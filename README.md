### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 19.09.25
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

### Program 1:
```
import pandas as pd
df=pd.read_csv("/content/clustervisitor.csv")
df
cluster={"Young":(df['Age']<=30),"Middle":((df['Age']>30) & (df['Age']<=50)),"Old":(df['Age']>50)}
print(cluster)
count=[]
for g,c in cluster.items():
  visitors=df[c]
  count.append(len(visitors))
  print(f"visitors in {g} Group")
  print(visitors)
  print(count)
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.bar(cluster.keys(),count, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:
<img width="896" height="675" alt="Screenshot 2025-09-19 112524" src="https://github.com/user-attachments/assets/6f11a8ad-04fd-444d-b70f-230b964462a2" />


## Program2:
```
df=pd.read_csv("/content/clustervisitor (Salary).csv")
df1=df['Age']
df2=df['Salary']
df3=pd.concat([df1,df2],axis=1)
df3
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
sc=StandardScaler()
scaleddata=sc.fit_transform(df3)
scaleddata
kmeans_model = KMeans(n_clusters=3, random_state=42)
df3['cluster'] = kmeans_model.fit_predict(df3[['Age', 'Salary']])
df3
plt.scatter(df3['Age'],df3['Salary'],c=df3['cluster'])
plt.xlabel("Age")
plt.ylabel("Income in thousands")
plt.show()
```
## Output:
<img width="788" height="594" alt="Screenshot 2025-09-19 112004" src="https://github.com/user-attachments/assets/062a1dcb-5752-4c75-a907-8d85b054c251" />


### Result:
 Thus the implementation of Cluster and Visitor Segmentation for Navigation patterns in Python were successfully done.
