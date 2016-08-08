# K-Nearest Neighbor
```
def __calculate_dist(z, bag, k=KNN_K):
    dist = distance.cdist(bag, [z])[:,0]
    r = np.sort(dist)[:k].sum()
    return r
```
