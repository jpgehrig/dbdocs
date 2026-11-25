The `CREATE_MODEL` procedure in the `DBMS_DATA_MINING` package uses the specified data to create a mining model with the specified name and mining function. The model can be created with configuration settings and user-specified transformations.

    PROCEDURE CREATE_MODEL(
                      model_name            IN VARCHAR2,
                      mining_function       IN VARCHAR2,
                      data_table_name       IN VARCHAR2,
                      case_id_column_name   IN VARCHAR2,
                      target_column_name    IN VARCHAR2 DEFAULT NULL,
                      settings_table_name   IN VARCHAR2 DEFAULT NULL,
                      data_schema_name      IN VARCHAR2 DEFAULT NULL,
                      settings_schema_name  IN VARCHAR2 DEFAULT NULL,
                      xform_list            IN TRANSFORM_LIST DEFAULT NULL);

### 31.2.1 Choosing the Mining Function

Explains about providing mining function to `CREATE_MODEL`.

The mining function is a required argument to the `CREATE_MODEL` procedure. A data mining function specifies a class of problems that can be modeled and solved.

Data mining functions implement either **supervised** or **unsupervised** learning. Supervised learning uses a set of independent attributes to predict the value of a dependent attribute or **target**. Unsupervised learning does not distinguish between dependent and independent attributes. Supervised functions are predictive. Unsupervised functions are descriptive.

**Note:**

In data mining terminology, a **function** is a general type of problem to be solved by a given approach to data mining. In SQL language terminology, a **function** is an operator that returns a value.

In Oracle Data Mining documentation, the term **function**, or **mining function** refers to a data mining function; the term **SQL function** or **SQL Data Mining function** refers to a SQL function for scoring (applying data mining models).

You can specify any of the values in the following table for the `mining_function` parameter to `CREATE_MODEL`.

Table 31-2 Mining Model Functions

| Mining_Function Value  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ASSOCIATION`          | Association is a descriptive mining function. An association model identifies relationships and the probability of their occurrence within a data set. (association rules)<br>Association models use the Apriori algorithm.                                                                                                                                                                                                                                                          |
| `ATTRIBUTE_IMPORTANCE` | Attribute Importance is a predictive mining function. An attribute importance model identifies the relative importance of attributes in predicting a given outcome.<br>Attribute Importance models use the Minimum Description Length algorithm and CUR Matrix Decomposition.                                                                                                                                                                                                        |
| `CLASSIFICATION`       | Classification is a predictive mining function. A classification model uses historical data to predict a categorical target.<br>Classification models can use Naive Bayes, Neural Network, Decision Tree, Logistic Regression, Random Forest, Support Vector Machines, or Explicit Semantic Analysis. The default is Naive Bayes.<br>The classification function can also be used for anomaly detection. In this case, the SVM algorithm with a null target is used (One-Class SVM). |
| `CLUSTERING`           | Clustering is a descriptive mining function. A clustering model identifies natural groupings within a data set.<br>Clustering models can use k-Means, O-Cluster, or Expectation Maximization. The default is k-Means.                                                                                                                                                                                                                                                                |
| `FEATURE_EXTRACTION`   | Feature Extraction is a descriptive mining function. A feature extraction model creates a set of optimized attributes.<br>Feature extraction models can use Non-Negative Matrix Factorization, Singular Value Decomposition (which can also be used for Principal Component Analysis) or Explicit Semantic Analysis. The default is Non-Negative Matrix Factorization.                                                                                                               |
| `REGRESSION`           | Regression is a predictive mining function. A regression model uses historical data to predict a numerical target.<br>Regression models can use Support Vector Machines or Linear Regression. The default is Support Vector Machine.                                                                                                                                                                                                                                                 |
| `TIME_SERIES`          | Time series is a predictive mining function. A time series model forecasts the future values of a time-ordered series of historical numeric data over a user-specified time window. Time series models use the Exponential Smoothing algorithm. The default is Exponential Smoothing.                                                                                                                                                                                                |

**Related Topics**

- [Oracle Data Mining Concepts](mining-functions.md)

### 31.2.2 Choosing the Algorithm

Learn about providing the algorithm settings for a model.

The `ALGO_NAME` setting specifies the algorithm for a model. If you use the default algorithm for the mining function, or if there is only one algorithm available for the mining function, you do not need to specify the `ALGO_NAME` setting. Instructions for specifying model settings are in "Specifying Model Settings".

Table 31-3 Data Mining Algorithms

| ALGO_NAME Value                  | Algorithm                                                                        | Default? | Mining Model Function                                                                                             |
|:---------------------------------|:---------------------------------------------------------------------------------|:---------|:------------------------------------------------------------------------------------------------------------------|
| `ALGO_AI_MDL`                    | Minimum Description Length                                                       | —        | attribute importance                                                                                              |
| `ALGO_APRIORI_ASSOCIATION_RULES` | Apriori                                                                          | —        | association                                                                                                       |
| `ALGO_CUR_DECOMPOSITION`         | CUR Decomposition                                                                |          | Attribute Importance                                                                                              |
| `ALGO_DECISION_TREE`             | Decision Tree                                                                    | —        | classification                                                                                                    |
| `ALGO_EXPECTATION_MAXIMIZATION`  | Expectation Maximization                                                         |          |                                                                                                                   |
| `ALGO_EXPLICIT_SEMANTIC_ANALYS`  | Explicit Semantic Analysis                                                       | —        | feature extraction<br>classification                                                                              |
| `ALGO_EXPONENTIAL_SMOOTHING`     | Exponential Smoothing                                                            | —        | time series                                                                                                       |
| `ALGO_EXTENSIBLE_LANG`           | Language used for extensible algorithm                                           | —        | All mining functions are supported                                                                                |
| `ALGO_GENERALIZED_LINEAR_MODEL`  | Generalized Linear Model                                                         | —        | classification and regression                                                                                     |
| `ALGO_KMEANS`                    | k-Means                                                                          | yes      | clustering                                                                                                        |
| `ALGO_NAIVE_BAYES`               | Naive Bayes                                                                      | yes      | classification                                                                                                    |
| `ALGO_NEURAL_NETWORK`            | Neural Network                                                                   | —        | classification                                                                                                    |
| `ALGO_NONNEGATIVE_MATRIX_FACTOR` | Non-Negative Matrix Factorization                                                | yes      | feature extraction                                                                                                |
| `ALGO_O_CLUSTER`                 | O-Cluster                                                                        | —        | clustering                                                                                                        |
| `ALGO_RANDOM_FOREST`             | Random Forest                                                                    | —        | classification                                                                                                    |
| `ALGO_SINGULAR_VALUE_DECOMP`     | Singular Value Decomposition (can also be used for Principal Component Analysis) | —        | feature extraction                                                                                                |
| `ALGO_SUPPORT_VECTOR_MACHINES`   | Support Vector Machine                                                           | yes      | default regression algorithm<br>regression, classification, and anomaly detection (classification with no target) |

**Related Topics**

- [Specifying Model Settings](specifying-model-settings.md)
- [Oracle Data Mining Concepts](algorithms.md)

### 31.2.3 Supplying Transformations

You can optionally specify transformations for the build data in the `xform_list` parameter to `CREATE_MODEL`. The transformation instructions are embedded in the model and reapplied whenever the model is applied to new data.

#### 31.2.3.1 Creating a Transformation List

The following are the ways to create a transformation list:

- The `STACK` interface in `DBMS_DATA_MINING_TRANSFORM`.

  The `STACK` interface offers a set of pre-defined transformations that you can apply to an attribute or to a group of attributes. For example, you can specify supervised binning for all categorical attributes.

- The `SET_TRANSFORM` procedure in `DBMS_DATA_MINING_TRANSFORM`.

  The `SET_TRANSFORM` procedure applies a specified SQL expression to a specified attribute. For example, the following statement appends a transformation instruction for `country_id` to a list of transformations called `my_xforms`. The transformation instruction divides `country_id` by 10 before algorithmic processing begins. The reverse transformation multiplies `country_id` by 10.

        dbms_data_mining_transform.SET_TRANSFORM (my_xforms,
           'country_id', NULL, 'country_id/10', 'country_id*10');

  The reverse transformation is applied in the model details. If `country_id` is the target of a supervised model, the reverse transformation is also applied to the scored target.

#### 31.2.3.2 Transformation List and Automatic Data Preparation

Understand the interaction between transformation list and Automatic Data Preparation (ADP).

The transformation list argument to `CREATE_MODEL` interacts with the `PREP_AUTO` setting, which controls ADP:

- When ADP is on and you specify a transformation list, your transformations are applied with the automatic transformations and embedded in the model. The transformations that you specify are executed before the automatic transformations.

- When ADP is off and you specify a transformation list, your transformations are applied and embedded in the model, but no system-generated transformations are performed.

- When ADP is on and you do not specify a transformation list, the system-generated transformations are applied and embedded in the model.

- When ADP is off and you do not specify a transformation list, no transformations are embedded in the model; you must separately prepare the data sets you use for building, testing, and scoring the model.

**Related Topics**

- [Embedding Transformations in a Model](embedding-transformations-model.md)
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING_TRANSFORM.md)
