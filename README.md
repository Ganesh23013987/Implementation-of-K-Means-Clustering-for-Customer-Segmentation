# Ex 10 - Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary libraries.
2. Read the dataset/analyze the data.
3. Preprocessing the data.
4. Split the x,y Training/Testing data.
5. Import model to fit.
6. Use the model to predict on the test data.
7. Evaluate the metrices.
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by:   GANESH D
RegisterNumber: 212223240035
*/
```

```
import pandas as pd
import matplotlib.pyplot as plt
```

```
data = pd.read_csv("/content/Mall_Customers.csv")
data.head()
```
<img width="850" alt="image" src="https://github.com/user-attachments/assets/e0c7f6fe-10be-4821-b085-bf883a2a3664">

```
data.info()
```
<img width="850" alt="image" src="https://github.com/user-attachments/assets/14276aee-d3c4-437f-8d2c-46d745766d8d">

```
data.isnull().sum()
```
<img width="850" alt="image" src="https://github.com/user-attachments/assets/2ffd1a84-b5e6-4e39-933a-f62915630dc5">

```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No.of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```

<img width="1250" alt="image" src="https://github.com/user-attachments/assets/db8b27af-0672-4371-bf41-a8db408b9ee4">

```
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
KMeans(n_clusters=5)
y_pred=km.predict(data.iloc[:,3:])
y_pred
```
<img width="950" alt="image" src="https://github.com/user-attachments/assets/a0561a10-e229-4f66-8113-f0b53efd3d65">

```
data["cluster"]=y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
```

```
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"], color = "gold")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"], color = "pink")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"], color = "green")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"], color = "blue")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"], color = "red")
plt.show()
```
<img width="850" alt="image" src="https://github.com/user-attachments/assets/8049fb92-6396-4b66-9c83-8ce64bab40d9">
 
## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
