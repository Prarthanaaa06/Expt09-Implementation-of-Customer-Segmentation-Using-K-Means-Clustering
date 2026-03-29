# BLENDED LEARNING
# Implementation of Customer Segmentation Using K-Means Clustering

## AIM:
To implement customer segmentation using K-Means clustering on the Mall Customers dataset to group customers based on purchasing habits.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1. **Start**

2. **Import Libraries**

   * Import required libraries:

     * `pandas`
     * `matplotlib`, `seaborn`
     * `KMeans`
     * `StandardScaler`
     * `silhouette_score`

3. **Load Dataset**

   * Read dataset `CustomerData.csv` into a DataFrame
   * Display:

     * First few rows (`head()`)
     * Column names

4. **Select Features**

   * Choose relevant features:

     * `Age`
     * `Annual Income (k$)`
     * `Spending Score (1-100)`
   * Store in variable `X`

---

### **Data Preprocessing**

5. **Feature Scaling**

   * Initialize `StandardScaler`
   * Transform features to scaled values
   * Store as `X_scaled`

---

### **Find Optimal Number of Clusters (Elbow Method)**

6. **Initialize WCSS List**

   * Create empty list `wcss`

7. **Compute WCSS for Different Clusters**

   * For `i` from 1 to 10:

     * Apply KMeans with `n_clusters = i`
     * Fit model on `X_scaled`
     * Store inertia (WCSS) in list

8. **Plot Elbow Graph**

   * Plot number of clusters vs WCSS
   * Identify optimal number of clusters (elbow point)

---

### **Model Training**

9. **Choose Optimal Clusters**

   * Set number of clusters (e.g., 4)

10. **Apply K-Means**

* Initialize KMeans with chosen clusters
* Fit model on `X_scaled`

11. **Assign Cluster Labels**

* Add cluster labels to dataset as new column `Cluster`

---

### **Model Evaluation**

12. **Calculate Silhouette Score**

* Compute silhouette score to evaluate clustering quality
* Display score

---

### **Visualization**

13. **Plot Clusters**

* Create scatter plot:

  * X-axis → Annual Income
  * Y-axis → Spending Score
  * Color → Cluster labels
* Add title, labels, and legend

14. **Display Plot**

15. **End**

---

## Program:
```
/*
Program to implement customer segmentation using K-Means clustering on the Mall Customers dataset.
Developed by: PRARTHANA D
RegisterNumber: 212225230213
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import silhouette_score


data = pd.read_csv("CustomerData.csv")


print(data.head())
print(data.columns)


features = ['Age', 'Annual Income (k$)', 'Spending Score (1-100)']
X = data[features]


scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)


wcss = [] 
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, random_state=42)
    kmeans.fit(X_scaled)
    wcss.append(kmeans.inertia_)


plt.figure(figsize=(8, 4))
plt.plot(range(1, 11), wcss, marker='o', linestyle='--')
plt.xlabel('Number of Clusters')
plt.ylabel('WCSS')
plt.title('Elbow Method for Optimal Number of Clusters')
plt.show()


optimal_clusters = 4
kmeans = KMeans(n_clusters=optimal_clusters, random_state=42)
kmeans.fit(X_scaled)


data['Cluster'] = kmeans.labels_


sil_score = silhouette_score(X_scaled, kmeans.labels_)
print(f"Silhouette Score: {sil_score}")

plt.figure(figsize=(10, 6))
sns.scatterplot(data=data, x='Annual Income (k$)', y='Spending Score (1-100)', hue='Cluster', palette='viridis', s=100, alpha=0.7)
plt.title('Customer Segmentation based on Annual Income and Spending Score')
plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.legend(title='Cluster')
plt.show()
*/
```

## Output:
<img width="1051" height="226" alt="image" src="https://github.com/user-attachments/assets/79313e65-c4db-4637-9082-439e50d420f5" />
<img width="1011" height="438" alt="image" src="https://github.com/user-attachments/assets/145e3185-0957-4e1d-a721-f2690924fee7" />

<img width="1235" height="424" alt="image" src="https://github.com/user-attachments/assets/8318f3b6-f812-4f13-8c18-a1e133570856" />


## Result:
Thus, customer segmentation was successfully implemented using K-Means clustering, grouping customers into distinct segments based on their annual income and spending score. 
