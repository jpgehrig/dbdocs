Understand data transformation using Automatic Data Preparation (ADP).

Most algorithms require some form of data transformation. During the model build process, Oracle Data Mining can automatically perform the transformations required by the algorithm. You can choose to supplement the automatic transformations with additional transformations of your own, or you can choose to manage all the transformations yourself.

In calculating automatic transformations, Oracle Data Mining uses heuristics that address the common requirements of a given algorithm. This process results in reasonable model quality in most cases.

Binning and normalization are transformations that are commonly needed by data mining algorithms.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)

### 30.3.1 Binning

Binning, also called discretization, is a technique for reducing the cardinality of continuous and discrete data. Binning groups related values together in bins to reduce the number of distinct values.

Binning can improve resource utilization and model build response time dramatically without significant loss in model quality. Binning can improve model quality by strengthening the relationship between attributes.

Supervised binning is a form of intelligent binning in which important characteristics of the data are used to determine the bin boundaries. In supervised binning, the bin boundaries are identified by a single-predictor decision tree that takes into account the joint distribution with the target. Supervised binning can be used for both numerical and categorical attributes.

### 30.3.2 Normalization

Normalization is the most common technique for reducing the range of numerical data. Most normalization methods map the range of a single variable to another range (often 0,1).

### 30.3.3 How ADP Transforms the Data

The following table shows how ADP prepares the data for each algorithm.

Table 30-1 Oracle Data Mining Algorithms With ADP

| Algorithm                | Mining Function                                   | Treatment by ADP                                                                                                                                                                                              |
|:-------------------------|:--------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Apriori                  | Association Rules                                 | ADP has no effect on association rules.                                                                                                                                                                       |
| Decision Tree            | Classification                                    | ADP has no effect on Decision Tree. Data preparation is handled by the algorithm.                                                                                                                             |
| Expectation Maximization | Clustering                                        | Single-column (not nested) numerical columns that are modeled with Gaussian distributions are normalized. ADP has no effect on the other types of columns.                                                    |
| GLM                      | Classification and Regression                     | Numerical attributes are normalized.                                                                                                                                                                          |
| k-Means                  | Clustering                                        | Numerical attributes are normalized.                                                                                                                                                                          |
| MDL                      | Attribute Importance                              | All attributes are binned with supervised binning.                                                                                                                                                            |
| Naive Bayes              | Classification                                    | All attributes are binned with supervised binning.                                                                                                                                                            |
| NMF                      | Feature Extraction                                | Numerical attributes are normalized.                                                                                                                                                                          |
| O-Cluster                | Clustering                                        | Numerical attributes are binned with a specialized form of equi-width binning, which computes the number of bins per attribute automatically. Numerical columns with all nulls or a single value are removed. |
| SVD                      | Feature Extraction                                | Numerical attributes are normalized.                                                                                                                                                                          |
| SVM                      | Classification, Anomaly Detection, and Regression | Numerical attributes are normalized.                                                                                                                                                                          |

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING_TRANSFORM.md)

- Part III of [Oracle Data Mining Concepts](algorithms.md) for more information about algorithm-specific data preparation
