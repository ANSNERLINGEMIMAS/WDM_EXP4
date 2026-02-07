### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
``
## Program 1
```
cluster = {"Young":(df['Age']<=30),"Middle":((df['Age']>30)&(df['Age']<=50)),"Old":(df['Age']>50)}
count=[]
for group,condition in cluster.items():
  visitors=df[condition]
  count.append(len(visitors))
  print(f"The visitors on {group} age are")
  print(visitors)
  print("count=",len(visitors))
```
 ### Output

<img width="484" height="684" alt="Screenshot 2026-02-07 142946" src="https://github.com/user-attachments/assets/681b66af-1003-4b01-a535-b2bdcd163667" />

### Visualization:
```
import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.bar(['Young','Middle','Old'],count,color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Number of Visitors by Age Group')
plt.show()
```



### Output:

<img width="873" height="571" alt="Screenshot 2026-02-07 142501" src="https://github.com/user-attachments/assets/1c42c739-7b0d-4001-a5dc-7b7b743bd0f9" />


### Program 2:
```
from sklearn .preprocessing import StandardScaler
from sklearn.cluster import KMeans
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=4,random_state=55)
df3['cluster']=k.fit_predict(newdf)
df3
```
### Output:
<img width="246" height="661" alt="Screenshot 2026-02-07 142802" src="https://github.com/user-attachments/assets/e44dfa7d-e359-49ec-a67a-6af38a05c9c9" />

## Visualiaztion:
```
import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.scatter(x=df3['Age'],y=df3['Income'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title('Visitor Distribution in Different Clusters')
plt.show()
```



### Output:

<img width="771" height="550" alt="Screenshot 2026-02-07 142906" src="https://github.com/user-attachments/assets/c733b7cb-27f0-4050-9684-d14c9ac1f52a" />


### Result:

Thus Implementation of Cluster and Visitor Segmentation for Navigation patterns is implemented successfully.
