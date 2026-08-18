# AIM

To implement visitor segmentation using the K-Means clustering algorithm in Python based on the Age feature and visualize the clustered visitor groups using a scatter plot.

# ALGORITHM

1. Import the required Python libraries.
2. Read the visitor dataset (CSV file).
3. Load the dataset into a DataFrame.
4. Select the **Age** feature for clustering.
5. Set the number of clusters (**K = 3**).
6. Choose the first **K** age values as the initial centroids.
7. Calculate the distance of each visitor from every centroid.
8. Assign each visitor to the nearest centroid.
9. Compute the new centroid of each cluster by taking the average age.
10. Repeat the assignment and centroid update steps until the centroids do not change.
11. Display the cluster-wise visitor details.
12. Visualize the clusters using a scatter plot.
13. Analyze the clustered visitor groups.


# Program 
```python
import pandas as pd
import matplotlib.pyplot as plt

# Read CSV file
df = pd.read_csv("clustervisitor.csv")

# Select Age feature
X = df["Age"].tolist()

# Number of clusters
k = 3

# Step 1: Choose initial centroids
centroids = X[:k]

while True:

 # Step 2: Assign each data point to the nearest centroid
    clusters = [[] for _ in range(k)]

    for age in X:
        distances = [abs(age - c) for c in centroids]
        cluster = distances.index(min(distances))
        clusters[cluster].append(age)
  # Step 3: Calculate new centroids
    new_centroids = []
    for cluster in clusters:
        if cluster:
            new_centroids.append(sum(cluster) / len(cluster))
        else:
            new_centroids.append(0)

    if new_centroids == centroids:
        break

    centroids = new_centroids

# Step 4: Display cluster-wise output
print("Final Centroids:", centroids)

for i in range(k):
    print(f"\nCluster {i+1}:")
    print(clusters[i])


# Step 5: Visualize clusters
colors = ["red", "green", "blue"]
# Step 4: Display cluster-wise output
print("Final Centroids:", centroids)

for i in range(k):
    print(f"\nCluster {i+1}:")
    print(clusters[i])

for i in range(k):
    plt.scatter(
        clusters[i],
        [i + 1] * len(clusters[i]),
        color=colors[i],
        label=f"Cluster {i+1}"
    )

plt.xlabel("Age")
plt.ylabel("Cluster")
plt.title("Visitor Segmentation using K-Means")
plt.legend()
plt.grid(True)
plt.show()
```

# Output
<img width="648" height="212" alt="image_59" src="https://github.com/user-attachments/assets/1d98abdd-f3e8-42cc-bd02-aec8e3da2d40" />
<img width="684" height="535" alt="image" src="https://github.com/user-attachments/assets/e55a24a1-4d6b-41b6-b7bf-0a3a49d0547d" />


# RESULT:
Thus, the K-Means clustering algorithm was successfully implemented, and the visitors were grouped into different clusters and visualized using a scatter plot.








