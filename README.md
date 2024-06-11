# document_clustering

**Overview:**

With the growing amount of digital content, oftentimes it is difficult to find relevant and hidden information in data we have. The primary idea of this project is to identify and cluster documents with similar content in terms of content or key ideas in the document. This clustering process will enable users to quickly locate and explore relevant information within large document collections. To simplify the process, we are dealing with the English language documents based on this project. By organizing these documents into meaningful clusters, the system will provide users with a powerful tool for knowledge discovery and information management.

**Implementation steps:**

1. Data cleaning (removing punctuation, numbers, stopwords etc.,)

2. Training Doc2vec embedding model.
   
3. Experiment Clustering with K-means, K-Center and Hierarchical algorithms.

4. Evaluation of cluster quality using Measures (Silhouette Score and NMI).

5. Compare the clustering results.

**Programming Language :** Python

**Dataset :** 20 NewsGroup http://qwone.com/~jason/20Newsgroups/ 
  
  Contains around 18,000 documents spread across 20 different newsgroups - Benchmark for text classification tasks.
  Document articles includes from topics politics, religion, science, and sports


<img width="843" alt="Screenshot 2024-06-10 at 4 40 10 PM" src="https://github.com/chethana613/document_clustering/assets/56347342/946b5509-f1ee-493a-ba08-3cd7d6b46bc9">


**Clustering Algorithms Experimented:**

1. K-Means

Begins by randomly initializing k cluster centroids, typically by selecting k random documents as initial centroids.
Each document is assigned to the nearest centroid based on a distance metric (e.g., Euclidean distance or cosine similarity) in the document vector space.
The centroids are updated by recalculating their positions as the mean of all the document vectors assigned to each cluster.


2. K-Center
   
The k-center problem is a fundamental optimization problem in computer science and operations research. Its objective is to find k centers in a given set of points such that the maximum distance from any point to its nearest center is minimized.
The algorithm starts by selecting a random data point(Document) as the first center and iteratively adds centers by choosing points that are farthest from the existing centers, ensuring the centers are well-distributed.

3. Hierarchical

Hierarchical clustering is an unsupervised learning technique for grouping similar objects into clusters. It aids in topic modeling, document organization, and information retrieval systems.
The algorithm starts by selecting a random data point as the first center and iteratively adds centers by choosing points that are farthest from the existing centers, ensuring the centers are well-distributed.

**Evaluation Metrics:**

1. Silhouette Score
   
This score is calculated by measuring each data point's similarity to the cluster it belongs to and how different it is from other clusters.
Silhouette score above 0.5 indicates a good clustering, a silhouette score below 0.25 indicates a poor clustering.

2. NMI (NORMALIZED MUTUAL INFORMATION)

Normalized Mutual Information (NMI) is a measure used to evaluate the similarity between two clusterings of data. It quantifies how much information is shared between the two clusterings, taking into account both the clustering assignments themselves and their agreement with some ground truth labels
normalization of the Mutual Information (MI) score to scale the results between 0 (no mutual information) and 1 (perfect correlation).

Results:

**K-Means:**

<img width="1010" alt="image" src="https://github.com/chethana613/document_clustering/assets/56347342/5d23304b-2fe3-4a63-8b0e-164fc5b68520">


**K-Center**

K center focuses on minimizing the maximum distance between any point to the center of its cluster. This leads to tight and well defined clusters (high Silhouette Score). But this method might not align well with the actual data distribution which leads to poor NMI scores. 


**Experimentation**


**Silhouette Score vs K :**
Experimentation is done with Silhouette Score vs K to find the optimal k value and corresponding Silhouette Scores and following are the results.

<img width="673" alt="image" src="https://github.com/chethana613/document_clustering/assets/56347342/62c57fcd-8dc4-49e8-92e7-86102a1cda4e">


**NMI Score vs K :**
We have taken another metrics NMI Score which is experimented on different k values and following are the results.

<img width="625" alt="image" src="https://github.com/chethana613/document_clustering/assets/56347342/64b5afe9-d773-409e-8b4a-d832fe2f8a6d">


**Observations & Results**
The 20 Newsgroups dataset is high-dimensional. The k-center algorithm, which minimizes the maximum distance to the nearest center, can perform well in high-dimensional spaces where the concept of "center" and "distance" can be quite different compared to lower-dimensional spaces.

Text data, like the 20 Newsgroups dataset, is often sparse. The k-center algorithm might effectively capture the separation between sparse clusters, leading to better-defined clusters.
For the 20 Newsgroups dataset, the clusters found by k-center are more compact and better separated



**Conclusion**
The k-center algorithm yielding a higher Silhouette Score on the 20 Newsgroups dataset is likely due to the specific characteristics of the data and the strengths of the k-center approach in such contexts. While k-center might not universally outperform other algorithms across all datasets, it appears particularly well-suited for this high-dimensional, text-based dataset.

**Hierarchical Clustering**

Hierarchical clustering is an unsupervised learning technique that groups similar objects into clusters, creating a hierarchy or tree-like structure of clusters. It can be performed using either agglomerative (bottom-up) or divisive (top-down) approaches. In agglomerative clustering, each data point starts as its cluster, and pairs of clusters are iteratively merged based on their similarity, forming a dendrogram that illustrates the merging process. Divisive clustering starts with all data points in one cluster and recursively splits them into smaller clusters. The choice of distance measure and linkage criterion (e.g., single, complete, or average linkage) significantly impacts the clustering results. 
Hierarchical clustering is used in various fields, including data mining, pattern recognition, and bioinformatics, to discover inherent structures in data and to organize data into meaningful clusters based on their similarities.

**Experimentation:**

In this work, document vectors are calculated by training a Doc2Vec model on a set of cleaned sentences. These vectors are then used to perform hierarchical clustering using the agglomerative method with Ward linkage. Clustering is done for various numbers of clusters, ranging from 15 to 25. The normalized mutual information (NMI) score, which measures the agreement between the clustering and the ground truth labels, and the silhouette score, which assesses the quality of the clustering, are computed for every number of clusters. Higher silhouette scores correspond to better-defined clusters. The silhouette scores measure the compactness and separation of the clustering. The NMI scores indicate how accurate the clustering is in comparison to the ground truth. The results are plotted to visualize how the silhouette scores vary with the number of clusters, helping to determine the optimal number of clusters for the given data.

**Results and observations:**
<img width="533" alt="Screenshot 2024-06-10 194754" src="https://github.com/chethana613/document_clustering/assets/89372870/9bb4e1e2-b6f0-4a69-a3ab-bd547998761f">


The experiment evaluated the clustering performance of a hierarchical clustering algorithm on a dataset for various numbers of clusters (K). The silhouette scores, which measure the cohesion and separation of the clusters, showed a decreasing trend as K increased. However, the silhouette scores for K=15 and K=16 were relatively stable and higher compared to other values, indicating well-defined clusters. The normalized mutual information (NMI) scores, which assess the clustering's alignment with ground truth labels, varied with different K values. The highest NMI score was observed for K=20, suggesting better agreement with the ground truth. Notably, for K=21 to K=25, the silhouette scores were negative, indicating poor clustering. Overall, while the optimal number of clusters was not definitive, the results suggested that K=20 could be a suitable choice, offering a balance between cluster quality and alignment with ground truth labels.


