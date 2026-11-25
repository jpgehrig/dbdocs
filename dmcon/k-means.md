Learn how to use enhanced k-Means Clustering algorithm that the Oracle Data Mining supports.

- About k-Means

- k-Means Algorithm Configuration

- Data Preparation for k-Means

**Related Topics**

- [Clustering](clustering.md)

### 18.1 About k-Means

The k-Means algorithm is a distance-based clustering algorithm that partitions the data into a specified number of clusters.

Distance-based algorithms rely on a distance function to measure the similarity between cases. Cases are assigned to the nearest cluster according to the distance function used.

#### 18.1.1 Oracle Data Mining Enhanced k-Means

Oracle Data Mining implements an enhanced version of the k-Means algorithm with the following features:

- **Distance function**: The algorithm supports Euclidean and Cosine distance functions. The default is Euclidean.

- **Scalable Parallel Model build**: The algorithm uses a very efficient method of initialization based on Bahmani, Bahman, et al. "Scalable k-means++." Proceedings of the VLDB Endowment 5.7 (2012): 622-633.

- **Cluster properties**: For each cluster, the algorithm returns the centroid, a histogram for each attribute, and a rule describing the hyperbox that encloses the majority of the data assigned to the cluster. The centroid reports the mode for categorical attributes and the mean and variance for numerical attributes.

This approach to k-Means avoids the need for building multiple k-Means models and provides clustering results that are consistently superior to the traditional k-Means.

#### 18.1.2 Centroid

The **centroid** represents the most typical case in a cluster. For example, in a data set of customer ages and incomes, the centroid of each cluster would be a customer of average age and average income in that cluster. The centroid is a prototype. It does not necessarily describe any given case assigned to the cluster.

The attribute values for the centroid are the mean of the numerical attributes and the mode of the categorical attributes.

### 18.2 k-Means Algorithm Configuration

Learn about configuring k-means algorithm.

The Oracle Data Mining enhanced k-Means algorithm supports several build-time settings. All the settings have default values. There is no reason to override the defaults unless you want to influence the behavior of the algorithm in some specific way.

You can configure k-Means by specifying the following considerations:

- Number of clusters

- Distance Function. The default distance function is Euclidean.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)

### 18.3 Data Preparation for k-Means

Learn about preparing data for k-means algorithm.

Normalization is typically required by the k-Means algorithm. Automatic Data Preparation performs normalization for k-Means. If you do not use ADP, you must normalize numeric attributes before creating or applying the model.

When there are missing values in columns with simple data types (not nested), k-Means interprets them as missing at random. The algorithm replaces missing categorical values with the mode and missing numerical values with the mean.

When there are missing values in nested columns, k-Means interprets them as sparse. The algorithm replaces sparse numerical data with zeros and sparse categorical data with zero vectors.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING_TRANSFORM.md)
- [Preparing the Data](../dmprg/preparing-data.md)
- [Transforming the Data](../dmprg/transforming-data.md)
