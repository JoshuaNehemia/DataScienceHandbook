# K-Means Clustering

K-Means is the "Hello World" of clustering algorithms. It is popular because it is fast, conceptually simple, and works well on many standard datasets. It falls under the **Centroid Model** category: it assumes that a cluster is defined by a central point (the centroid) and that data points gravitate toward the nearest center.

## The Core Concept

The name "K-Means" reveals exactly what it does:

* **"K"**: K must tell the algorithm how many clusters to find (e.g., $k=3$ means there are 3 clusters).
* **"Means"**: The center of a cluster is the arithmetic *mean* (average) of all the points belonging to that cluster.

## The Algorithm: Step-by-Step

The process is an iterative loop. It repeats the same steps over and over until the clusters stop changing (convergent).

### 1. Initialization (The Starting Line)

First, define $k$ (the number of clusters). The algorithm then randomly selects $k$ points from the dataset (or random locations in the data space) to serve as the initial **centroids**.

>[!WARNING] 
> Starting point is important. If starting points is bad, k-means might get a bad result.

### 2. The Assignment Step (Choosing Sides)

The algorithm looks at every single data point in your dataset and asks: *"Which centroid am I closest to?"*

* It calculates the distance/similarity (usually **Euclidean distance**, [learn more about distance](../../../Similarity_Measures/SimilarityMeasures(Distance).md)) between the data point and every centroid.
* The data point is assigned to the cluster of the nearest centroid.
* *Result:* The data space is partitioned into regions (Voronoi cells).

### 3. The Update Step (Moving the Center)

Now that every point has picked a team, the algorithm re-evaluates the centers.

* It looks at all the points currently assigned to "Cluster 1."
* It calculates the average (mean) position of all those points.
* It moves the centroid to this new, true center.
* This is repeated for every cluster.

### 4. Convergence (The Finish Line)

Steps 2 and 3 are repeated.

* Points are re-assigned to the nearest (newly moved) centroid.
* Centroids are moved again to the center of their new members.
* **Stop Condition:** The loop stops when the centroids stop moving (or move very little), meaning the clusters have stabilized.

## Critical Limitations

While powerful, K-Means has specific blind spots:

* **You must guess $k$:** The algorithm cannot figure out how many clusters exist; it must be inputted manually. However, there is a tool in clustering called **Elbow Method** to help define how many $k$ is appropriate for the datasets if applied a clustering model.
* **Spherical assumption:** It assumes clusters are round blobs. It fails miserably on complex shapes (like concentric circles or crescent moons).
* **Sensitivity to outliers:** A single outlier far away can pull the centroid "mean" toward it, skewing the entire cluster.
