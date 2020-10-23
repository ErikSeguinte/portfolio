---
title: "DBSCAN"
date: 2020-10-22T18:52:00-07:00
draft: false

---

# DBSCAN

DBSCAN, or **Density-based Spatial Cluster of applications with noise** is a data clustering algorithm that groups together points that are closely packed together while marking outliers as noise. It is one of the most common clustering algorithms.

## Terms

* $\epsilon$ (eps)
  $\epsilon$, epsilon, or simply "eps" is the maximum distance between two points for those points to be considered neighbors.
* **Core Point**
  A core point is a point that has the required minimum number of neighbors.
* **Minimum Points**
  The minimum number of neighbors, including the point itself.
* **Reachable**
  A point $q$ is reachable from point $p$ if there exists a path such that $p_1, \ldots, p_n $ with $p_1 =  p$ and $p_n = q$ where each $p_{i+1}$ is reachable from $p_i$. In other words, there exists a path from point $p$ to point $q$ that can be traversed by going from one point to its neighbor, to that points neighbor, and so on.   
* **Cluster**
  If $p$ is a core point, then it forms a cluster with all points, core or non-core, that are reachable from it. Each cluster must contain at least one core point. Non-core points can be part of a cluster, but they form the edge as further points cannot be reached from them.
* **Noise**
  A point that is not reachable from any other point is considered to be an outlier or noise.

## Abstract Algorithm

The DBSCAN algorithm can be abstracted into the following steps:

1. Starting from an arbitrary point $p$, determine the number of neighbors within range $\epsilon$. If this number is greater than or equal to the minimum required, mark $p$ as a core point and assign it to the next available cluster.
2. For each point $p_i$ that is reachable from point $p$, mark $p_i$ as part of the same cluster as $p$. Determine the number of neighbors that are reachable from $p_1$. If neighbors $\geq$ minimum points, mark it as a core point. Mark each reachable point $p_{i+1}$ as part of the cluster and repeat this step with each $p_{i+1}$.
3. If point $p$ is not a core point, mark it as noise.
4. Choose a new point $p$ that is not already part of a cluster or marked as noise and repeat until all points are marked as part of a cluster or as noise.

## Implementation Notes

This algorithm lends itself well to a recursive approach, where for each point p, recurse into each of its neighbors until no additional points are reachable.

The greatest challenge for the DBSCAN implementation is determining the number of neighbors. A naïve application might use brute force, checking the distance between each point and every other point. This gives us a time complexity of $O(n^2)$. Using memoization and storing each distance in a hashtable can reduce the real world time by half, as it eliminates an expensive calculation when checking between 2 points whose distance was already calculated while processing the one of the nodes previously. While $O(\frac{n^2}{2}) \approx O(n^2)$ for large enough values of $n$, it can still be a noticeable improvement.

The algorithm can be further improved by using data structures. K-Dimensional trees (KD Trees) and range trees are similar to binary search trees extended into k-dimensional space. KD trees partition space in a way that large sections of space can be eliminated and avoid processing them. Range Trees are 1-dimensional BSTs that embed trees keys to the other dimensions at each node, such that a 2d range tree would have a BST keyed by the x coordinate, and each node would have 4 sub trees. 2 subtrees for the left and right in the X direction, and those same nodes in trees keyed in the y direction. 

These data structures can reduce the number of candidates that need to be checked as neighbors.

## Implementation



```python
from scipy.spatial import cKDTree


class DBSCAN:
    def __init__(self, min_pts = 4, distance=0.1, protocol=0):
        self.q = set()
        self.memo = {}
        self.visited = set()
        self.min_pts = min_pts
        self.distance = distance
        self.clusters = []
        self.points = []
        self.tree = None
        self.clusters_used = set()

    def range_query(self, i, eps, min, cluster):

        if i in self.visited:
            return
        self.visited.add(i)

        point = self.points[i]
        neighbors = self.tree.query_ball_point(x=point, r=eps, n_jobs=-1)

        if len(neighbors) < min and cluster not in self.clusters_used:
            # else:
            self.clusters[i] = 0
        else:
            self.clusters[i] = cluster
            self.clusters_used.add(cluster)

            if len(neighbors) >= min:
                for p in neighbors:
                    if p not in self.q:
                        self.q.add(p)
                        self.range_query(p, eps, min, cluster)

    def dbscan(self, eps, min):
        self.clusters = [0] * len(self.points)
        self.memo = {}
        self.clusters_used = set()
        self.visited = set()
        cluster = 1
        for i in range(len(self.points)):
            if i in self.visited:
                continue

            if cluster in self.clusters_used:
                cluster += 1
            self.range_query(i, eps, min, cluster)

    def fit(self, points):
        self.points = points
        self.tree = cKDTree(points)
        self.clusters = [0 * len(self.points)]
        self.memo = {}
        self.clusters_used = set()
        self.visited = set()
        self.dbscan(eps = self.distance, min = self.min_pts)

    def predict(self):
        return self.clusters


if __name__ == "__main__":
    import numpy as np
    import plotly.express as px
    import plotly
    from pathlib import Path

    np.random.seed(0)
    points = np.random.random((1500, 2))
    classifier = DBSCAN(6, 0.038)
    classifier.fit(points)
    results = classifier.predict()
    fig = px.scatter(x=points[:, 0], y=points[:, 1], color=[str(i) for i in classifier.clusters])
    fig.show()
    path = Path("plot")

    plotly.offline.plot(fig, filename=str(path))


```

