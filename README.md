# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Load and clean the customer data for analysis.

2. Select relevant features such as income or spending score.

3. Determine the optimal number of clusters (K) using the Elbow Method.

4. Apply the K-Means algorithm to group customers into K clusters.

5. Assign each customer to the nearest cluster based on centroids.

6. Visualize the clusters and interpret the customer segments.
 

## Program and Output:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: DHIRAVIYA S
RegisterNumber:  212223040041
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt

data = pd.read_csv(r"C:\Users\admin\OneDrive\Desktop\Folders\ML\DATASET-20250226\Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/998253bc-c0b3-400a-8fcf-3eaa7822f63b)

```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters=i, init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No. of clusters")
plt.ylabel("wcss")
plt.title("Elbow method")
```
![image](https://github.com/user-attachments/assets/39355323-8326-4eb9-8449-f13dec34d0e9)

```
km = KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
```
![image](https://github.com/user-attachments/assets/0c6f53e4-0bda-4f5e-804b-15317b41064a)

```
y_pred = km.predict(data.iloc[:,3:])
y_pred
```
![image](https://github.com/user-attachments/assets/cff2987a-d060-4861-b663-c49d66e8537e)

```
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster 0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster 1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster 2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster 3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster 4")

plt.legend()
plt.title("customer segmentation")
```
![image](https://github.com/user-attachments/assets/eb606967-f923-4cec-9abc-f1cea4ffdfc0)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
