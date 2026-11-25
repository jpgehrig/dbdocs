Oracle Data Mining distinguishes between **sparse data** and data that contains **random missing values**. The latter means that some attribute values are unknown. Sparse data, on the other hand, contains values that are assumed to be known, although they are not represented in the data.

A typical example of sparse data is market basket data. Out of hundreds or thousands of available items, only a few are present in an individual case (the basket or transaction). All the item values are known, but they are not all included in the basket. Present values have a quantity, while the items that are not represented are sparse (with a known quantity of zero).

Oracle Data Mining interprets missing data as follows:

- Missing at random: Missing values in columns with a simple data type (not nested) are assumed to be missing at random.

- Sparse: Missing values in nested columns indicate sparsity.

### 3.6.1 Examples: Missing Values or Sparse Data?

The examples in this section illustrate how Oracle Data Mining identifies data as either sparse or missing at random.

#### 3.6.1.1 Sparsity in a Sales Table

A sales table contains point-of-sale data for a group of products that are sold in several stores to different customers over a period of time. A particular customer buys only a few of the products. The products that the customer does not buy do not appear as rows in the sales table.

If you were to figure out the amount of money a customer has spent for each product, the unpurchased products have an inferred amount of zero. The value is not random or unknown; it is zero, even though no row appears in the table.

Note that the sales data is dimensioned (by product, stores, customers, and time) and are often represented as nested data for mining.

Since missing values in a nested column always indicate sparsity, you must ensure that this interpretation is appropriate for the data that you want to mine. For example, when trying to mine a multi-record case data set containing movie ratings from users of a large movie database, the missing ratings are unknown (missing at random), but Oracle Data Mining treats the data as sparse and infer a rating of zero for the missing value.

#### 3.6.1.2 Missing Values in a Table of Customer Data

A table of customer data contains demographic data about customers. The case ID column is the customer ID. The attributes are age, education, profession, gender, house-hold size, and so on. Not all the data is available for each customer. Any missing values are considered to be missing at random. For example, if the age of customer 1 and the profession of customer 2 are not present in the data, that information is simply unknown. It does not indicate sparsity.

Note that the customer data is not dimensioned. There is a one-to-one mapping between the case and each of its attributes. None of the attributes are nested.

### 3.6.2 Missing Value Treatment in Oracle Data Mining

Missing value treatment depends on the algorithm and on the nature of the data (categorical or numerical, sparse or missing at random). Missing value treatment is summarized in the following table.

**Note:**

Oracle Data Mining performs the same missing value treatment whether or not Automatic Data Preparation is being used.

Table 3-3 Missing Value Treatment by Algorithm

| Missing Data                  | EM, GLM, NMF, k-Means, SVD, SVM                                                                                                                                                                                                                                                                                                                                    | DT, MDL, NB, OC                                                                                                                                                                                             | Apriori                                              |
|:------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------|
| NUMERICAL missing at random   | The algorithm replaces missing numerical values with the mean.<br>For Expectation Maximization (EM), the replacement only occurs in columns that are modeled with Gaussian distributions.                                                                                                                                                                          | The algorithm handles missing values naturally as missing at random.                                                                                                                                        | The algorithm interprets all missing data as sparse. |
| CATEGORICAL missing at random | Genelized Linear Models (GLM), Non-Negative Matrix Factorization (NMF), k-Means, and Support Vector Machine (SVM) replaces missing categorical values with the mode.<br>Singular Value Decomposition (SVD) does not support categorical data.<br>EM does not replace missing categorical values. EM treats NULLs as a distinct value with its own frequency count. | The algorithm handles missing values naturally as missing random.                                                                                                                                           | The algorithm interprets all missing data as sparse. |
| NUMERICAL sparse              | The algorithm replaces sparse numerical data with zeros.                                                                                                                                                                                                                                                                                                           | O-Cluster does not support nested data and therefore does not support sparse data. Decision Tree (DT), Minimum Description Length (MDL), and Naive Bayes (NB) and replace sparse numerical data with zeros. | The algorithm handles sparse data.                   |
| CATEGORICAL sparse            | All algorithms except SVD replace sparse categorical data with zero vectors. SVD does not support categorical data.                                                                                                                                                                                                                                                | O-Cluster does not support nested data and therefore does not support sparse data. DT, MDL, and NB replace sparse categorical data with the special value `DM$SPARSE`.                                      | The algorithm handles sparse data.                   |

### 3.6.3 Changing the Missing Value Treatment

Transform the missing data as sparse or missing at random.

If you want Oracle Data Mining to treat missing data as sparse instead of missing at random or missing at random instead of sparse, transform it before building the model.

If you want missing values to be treated as sparse, but Oracle Data Mining interprets them as missing at random, you can use a SQL function like `NVL` to replace the nulls with a value such as "NA". Oracle Data Mining does not perform missing value treatment when there is a specified value.

If you want missing nested attributes to be treated as missing at random, you can transform the nested rows into physical attributes in separate columns — as long as the case table stays within the 1000 column limitation imposed by the Database. Fill in all of the possible attribute names, and specify them as null. Alternatively, insert rows in the nested column for all the items that are not present and assign a value such as the mean or mode to each one.

**Related Topics**

- [Oracle Database SQL Language Reference](../sqlrf/NVL.md)
