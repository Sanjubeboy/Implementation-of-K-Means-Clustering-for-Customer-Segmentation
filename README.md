# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the dataset and print dataset info
2. Check for null values
3. Import kmeans and fit it to dataset
4. Plot the graph using elbow method
5. Print the predicted array values
6. Plot the customer segments graph

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: SANJAY KUMAR P
RegisterNumber:  212220040144
*/

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("/content/Mall_Customers (1).csv")
print('1) data.head()')
data.head()
print('2) data.info()')
data.info()
print('3) data.isnull().sum()')
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
print('3) ')
for i in range(1,11):
  kmeans = KMeans(n_clusters = i,init = "k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
print('4) ')
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow method")
plt.show()
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title('Customer Segments')
plt.show()

```

## Output:
![1](images/1.png)\
![2](images/2.png)\
![3](images/3.png)\
![4](images/4.png)\
![5](images/5.png)\
![6](images/6.png)\
![7](images/7.png)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.