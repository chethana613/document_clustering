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
