# Unsupervised learning: Clustering

`Unsupervised Learning` Involves `clustering` data. 

Clustering is the task of dividing a population or data points into several groups the aim is to, `segregate groups with similar traits and assign them into clusters.`




* Types of Clustering Models
    * Centroid
        * find the k cluster centers and assign the objects to the nearest cluster center such that the squared distances from the cluster are minimized.
    * Hierarchical 
        * Every point is a cluster, connect closest points in order to creat bigger clusters
    * Density
        * Area that meets threshold for density is considered a cluster, else an outlier 
        * Better for non-circular data, or data with many outliers
---
## Centroid

* Import code: 
    *       from sklearn.cluster import KMeans
* Instantiate KMean class
    *       km = KMeans(n_clusters=3, # how many clusters we expected   
            n_init=10, # how many initial runs
            random_state=0)

* Fit and predict the data with KM
    *       y_km = km.fit_predict(data)
      

## Hierarchical 

* Import code
    *       from sklearn.cluster import AgglomerativeClustering

* Instantiate obj from AGgCl class
    *       ac = AgglomerativeClustering(affinity='euclidean',
                             linkage='ward',
                             n_clusters = 3)
                            
* Fit and Predict
    *       y_hc = ac.fit_predict(X)


## Density 

* Import code
    *       from sklearn.cluster import DBSCAN

* Instantiate obj from AGgCl class
    *      db = DBSCAN(eps=0.5,
            min_samples=5,
            metric='euclidean')
                            
* Fit and Predict
    *       y_db = db.fit_predict(X)

---

## Elbow Rule
    def plot_distortion(X,max_clusters = 10):
    distortions = []
    for i in range(1, max_clusters +1):
        km = KMeans(n_clusters=i,
                    init='k-means++',
                    n_init=10,
                    random_state=0)
        km.fit(X)
        distortions.append(km.inertia_)

    plt.plot(range(1,max_clusters +1), distortions, marker='o')
    plt.xlabel('Number of clusters')
    plt.ylabel('Distortion')
    plt.show() 

---
## Dendrogram
    def plot_dendrogram(X,method ='ward'):
    dendrogram = sch.dendrogram(sch.linkage(X, method=method))
    plt.title("Dendrogram")
    plt.ylabel("Euclidean distances")
    plt.xlabel('Points')
    plt.show()

 ---

