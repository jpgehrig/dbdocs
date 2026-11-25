Understand the basic concepts of Oracle Data Mining.

- Mining Functions

- Algorithms

- Data Preparation

- In-Database Scoring

### 2.1 Mining Functions

Introduces the concept of data mining functions.

A basic understanding of data mining functions and algorithms is required for using Oracle Data Mining.

Each data mining **function** specifies a class of problems that can be modeled and solved. Data mining functions fall generally into two categories: **supervised** and **unsupervised**. Notions of supervised and unsupervised learning are derived from the science of machine learning, which has been called a sub-area of artificial intelligence.

Artificial intelligence refers to the implementation and study of systems that exhibit autonomous intelligence or behavior of their own. Machine learning deals with techniques that enable devices to learn from their own performance and modify their own functioning. Data mining applies machine learning concepts to data.

**Related Topics**

- Algorithms

#### 2.1.1 Supervised Data Mining

Supervised learning is also known as directed learning. The learning process is directed by a previously known dependent attribute or target. Directed data mining attempts to explain the behavior of the target as a function of a set of independent attributes or predictors.

Supervised learning generally results in predictive models. This is in contrast to unsupervised learning where the goal is pattern detection.

The building of a supervised model involves **training**, a process whereby the software analyzes many cases where the target value is already known. In the training process, the model "learns" the logic for making the prediction. For example, a model that seeks to identify the customers who are likely to respond to a promotion must be trained by analyzing the characteristics of many customers who are known to have responded or not responded to a promotion in the past.

##### 2.1.1.1 Supervised Learning: Testing

Separate data sets are required for building (training) and testing some predictive models. The build data (training data) and test data must have the same column structure. Typically, one large table or view is split into two data sets: one for building the model, and the other for testing the model.

The process of applying the model to test data helps to determine whether the model, built on one chosen sample, is generalizable to other data. In particular, it helps to avoid the phenomenon of overfitting, which can occur when the logic of the model fits the build data too well and therefore has little predictive power.

##### 2.1.1.2 Supervised Learning: Scoring

Apply data, also called scoring data, is the actual population to which a model is applied. For example, you might build a model that identifies the characteristics of customers who frequently buy a certain product. To obtain a list of customers who shop at a certain store and are likely to buy a related product, you might apply the model to the customer data for that store. In this case, the store customer data is the scoring data.

Most supervised learning can be applied to a population of interest. The principal supervised mining techniques, **Classification** and **Regression**, can both be used for scoring.

Oracle Data Mining does not support the scoring operation for **Attribute Importance**, another supervised function. Models of this type are built on a population of interest to obtain information about that population; they cannot be applied to separate data. An attribute importance model returns and ranks the attributes that are most important in predicting a target value.

Oracle Data Mining supports the supervised data mining functions described in the following table:

Table 2-1 Oracle Data Mining Supervised Functions

| Function             | Description                                                                        | Sample Problem                                                                                         |
|:---------------------|:-----------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------|
| Attribute Importance | Identifies the attributes that are most important in predicting a target attribute | Given customer response to an affinity card program, find the most significant predictors              |
| Classification       | Assigns items to discrete classes and predicts the class to which an item belongs  | Given demographic data about a set of customers, predict customer response to an affinity card program |
| Regression           | Approximates and forecasts continuous values                                       | Given demographic and purchasing data about a set of customers, predict customers' age                 |

#### 2.1.2 Unsupervised Data Mining

Unsupervised learning is non-directed. There is no distinction between dependent and independent attributes. There is no previously-known result to guide the algorithm in building the model.

Unsupervised learning can be used for **descriptive** purposes. It can also be used to make predictions.

##### 2.1.2.1 Unsupervised Learning: Scoring

Introduces unsupervised learning, supported scoring operations, and unsupervised Oracle Data Mining functions.

Although unsupervised data mining does not specify a target, most unsupervised learning can be applied to a population of interest. For example, clustering models use descriptive data mining techniques, but they can be applied to classify cases according to their cluster assignments. **Anomaly detection**, although unsupervised, is typically used to predict whether a data point is typical among a set of cases.

Oracle Data Mining supports the scoring operation for **Clustering** and **Feature Extraction**, both unsupervised mining functions. Oracle Data Mining does not support the scoring operation for **Association Rules**, another unsupervised function. Association models are built on a population of interest to obtain information about that population; they cannot be applied to separate data. An association model returns rules that explain how items or events are associated with each other. The association rules are returned with statistics that can be used to rank them according to their probability.

Oracle Data Mining supports the unsupervised functions described in the following table:

Table 2-2 Oracle Data Mining Unsupervised Functions

| Function           | Description                                                                                           | Sample Problem                                                                                                                       |
|:-------------------|:------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| Anomaly Detection  | Identifies items (outliers) that do not satisfy the characteristics of "normal" data                  | Given demographic data about a set of customers, identify customer purchasing behavior that is significantly different from the norm |
| Association Rules  | Finds items that tend to co-occur in the data and specifies the rules that govern their co-occurrence | Find the items that tend to be purchased together and specify their relationship                                                     |
| Clustering         | Finds natural groupings in the data                                                                   | Segment demographic data into clusters and rank the probability that an individual belongs to a given cluster                        |
| Feature Extraction | Creates new attributes (features) using linear combinations of the original attributes                | Given demographic data about a set of customers, group the attributes into general characteristics of the customers                  |

**Related Topics**

- [Mining Functions](mining-functions.md)
- In-Database Scoring

### 2.2 Algorithms

An algorithm is a mathematical procedure for solving a specific kind of problem. Oracle Data Mining supports at least one algorithm for each data mining function. For some functions, you can choose among several algorithms. For example, Oracle Data Mining supports four classification algorithms.

Each data mining model is produced by a specific algorithm. Some data mining problems can best be solved by using more than one algorithm. This necessitates the development of more than one model. For example, you might first use a feature extraction model to create an optimized set of predictors, then a classification model to make a prediction on the results.

#### 2.2.1 Oracle Data Mining Supervised Algorithms

Oracle Data Mining supports the supervised data mining algorithms described in the following table. The algorithm abbreviations are used throughout this manual.

Table 2-3 Oracle Data Mining Algorithms for Supervised Functions

| Algorithm                  | Function                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:---------------------------|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Decision Tree              | Classification                | Decision trees extract predictive information in the form of human-understandable rules. The rules are if-then-else expressions; they explain the decisions that lead to the prediction.                                                                                                                                                                                                                                     |
| Explicit Semantic Analysis | Classification                | Explicit Semantic Analysis (ESA) is designed to make predictions for text data. This algorithm can address use cases with hundreds of thousands of classes. In Oracle Database 12c Release 2, ESA was introduced as Feature Extraction algorithm.                                                                                                                                                                            |
| Exponential Smoothing      | Time Series                   | Exponential Smoothing (ESM) provides forecasts for time series data. Forecasts are made for each time period within a user-specified forecast window. ESM provides a total of 14 different time series models, including all the most popular estimates of trend and seasonal effects. Choice of model is controlled by user settings. ESM provides confidence bounds on its forecasts.                                      |
| Generalized Linear Models  | Classification and Regression | Generalized Linear Models (GLM) implement logistic regression for classification of binary targets and linear regression for continuous targets. GLM classification supports confidence bounds for prediction probabilities. GLM regression supports confidence bounds for predictions.                                                                                                                                      |
| Minimum Description Length | Attribute Importance          | Minimum Description Length (MDL) is an information theoretic model selection principle. MDL assumes that the simplest, most compact representation of data is the best and most probable explanation of the data.                                                                                                                                                                                                            |
| Naive Bayes                | Classification                | Naive Bayes makes predictions using Bayes' Theorem, which derives the probability of a prediction from the underlying evidence, as observed in the data.                                                                                                                                                                                                                                                                     |
| Neural Network             | Classification and Regression | Neural Network in Machine Learning is an artificial algorithm inspired from biological neural network and is used to estimate or approximate functions that depend on a large number of generally unknown inputs. Neural Network is designed for Classification and Regression.                                                                                                                                              |
| Random Forest              | Classification                | Random Forest is a powerful machine learning algorithm.Random Forest algorithm builds a number of decision tree models and predicts using the ensemble of trees.                                                                                                                                                                                                                                                             |
| Support Vector Machines    | Classification and Regression | Distinct versions of Support Vector Machines (SVM) use different kernel functions to handle different types of data sets. Linear and Gaussian (nonlinear) kernels are supported.<br>SVM classification attempts to separate the target classes with the widest possible margin.<br>SVM regression tries to find a continuous function such that the maximum number of data points lie within an epsilon-wide tube around it. |

#### 2.2.2 Oracle Data Mining Unsupervised Algorithms

Learn about unsupervised algorithms that Oracle Data Mining supports.

Oracle Data Mining supports the unsupervised data mining algorithms described in the following table. The algorithm abbreviations are used throughout this manual.

Table 2-4 Oracle Data Mining Algorithms for Unsupervised Functions

| Algorithm                                                     | Function             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:--------------------------------------------------------------|:---------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Apriori                                                       | Association          | Apriori performs market basket analysis by identifying co-occurring items (frequent itemsets) within a set. Apriori finds rules with support greater than a specified minimum support and confidence greater than a specified minimum confidence.                                                                                                                                                                                                                                                                                                         |
| CUR matrix decomposition                                      | Attribute Importance | CUR matrix decomposition is an alternative to Support Vector Machines(SVM) and Principal Component Analysis (PCA) and an important tool for exploratory data analysis. This algorithm performs analytical processing and singles out important columns and rows.                                                                                                                                                                                                                                                                                          |
| Expectation Maximization                                      | Clustering           | Expectation Maximization (EM) is a density estimation algorithm that performs probabilistic clustering. In density estimation, the goal is to construct a density function that captures how a given population is distributed. The density estimate is based on observed data that represents a sample of the population.<br>Oracle Data Mining supports probabilistic clustering and data frequency estimates and other applications of Expectation Maximization.                                                                                       |
| Explicit Semantic Analysis                                    | Feature Extraction   | Explicit Semantic Analysis (ESA) uses existing knowledge base as features. An attribute vector represents each feature or a concept. ESA creates a reverse index that maps every attribute to the knowledge base concepts or the concept-attribute association vector value.                                                                                                                                                                                                                                                                              |
| k-Means                                                       | Clustering           | k-Means is a distance-based clustering algorithm that partitions the data into a predetermined number of clusters. Each cluster has a centroid (center of gravity). Cases (individuals within the population) that are in a cluster are close to the centroid.<br>Oracle Data Mining supports an enhanced version of k-Means. It goes beyond the classical implementation by defining a hierarchical parent-child relationship of clusters.                                                                                                               |
| Non-Negative Matrix Factorization                             | Feature Extraction   | Non-Negative Matrix Factorization (NMF) generates new attributes using linear combinations of the original attributes. The coefficients of the linear combinations are non-negative. During model apply, an NMF model maps the original data into the new set of attributes (features) discovered by the model.                                                                                                                                                                                                                                           |
| One Class Support Vector Machines                             | Anomaly Detection    | One-class SVM builds a profile of one class. When the model is applied, it identifies cases that are somehow different from that profile. This allows for the detection of rare cases that are not necessarily related to each other.                                                                                                                                                                                                                                                                                                                     |
| Orthogonal Partitioning Clustering                            | Clustering           | Orthogonal Partitioning Clustering (o-cluster) creates a hierarchical, grid-based clustering model. The algorithm creates clusters that define dense areas in the attribute space. A sensitivity parameter defines the baseline density level.                                                                                                                                                                                                                                                                                                            |
| Singular Value Decomposition and Principal Component Analysis | Feature Extraction   | Singular Value Decomposition (SVD) and Principal Component Analysis (PCA) are orthogonal linear transformations that are optimal at capturing the underlying variance of the data. This property is extremely useful for reducing the dimensionality of high-dimensional data and for supporting meaningful data visualization.<br>In addition to dimensionality reduction, SVD and PCA have a number of other important applications, such as data de-noising (smoothing), data compression, matrix inversion, and solving a system of linear equations. |

**Related Topics**

- [Algorithms](algorithms.md)

### 2.3 Data Preparation

The quality of a model depends to a large extent on the quality of the data used to build (train) it. Much of the time spent in any given data mining project is devoted to data preparation. The data must be carefully inspected, cleansed, and transformed, and algorithm-appropriate data preparation methods must be applied.

The process of data preparation is further complicated by the fact that any data to which a model is applied, whether for testing or for scoring, must undergo the same transformations as the data used to train the model.

#### 2.3.1 Oracle Data Mining Simplifies Data Preparation

Oracle Data Mining offers several features that significantly simplify the process of data preparation:

- Embedded data preparation: The transformations used in training the model are embedded in the model and automatically executed whenever the model is applied to new data. If you specify transformations for the model, you only have to specify them once.

- Automatic Data Preparation (ADP): Oracle Data Mining supports an automated data preparation mode. When ADP is active, Oracle Data Mining automatically performs the data transformations required by the algorithm. The transformation instructions are embedded in the model along with any user-specified transformation instructions.

- Automatic management of missing values and sparse data: Oracle Data Mining uses consistent methodology across mining algorithms to handle sparsity and missing values.

- Transparency: Oracle Data Mining provides model details, which are a view of the attributes that are internal to the model. This insight into the inner details of the model is possible because of reverse transformations, which map the transformed attribute values to a form that can be interpreted by a user. Where possible, attribute values are reversed to the original column values. Reverse transformations are also applied to the target of a supervised model, thus the results of scoring are in the same units as the units of the original target.

- Tools for custom data preparation: Oracle Data Mining provides many common transformation routines in the `DBMS_DATA_MINING_TRANSFORM` PL/SQL package. You can use these routines, or develop your own routines in SQL, or both. The SQL language is well suited for implementing transformations in the database. You can use custom transformation instructions along with ADP or instead of ADP.

#### 2.3.2 Case Data

Most data mining algorithms act on single-record case data, where the information for each case is stored in a separate row. The data attributes for the cases are stored in the columns.

When the data is organized in transactions, the data for one case (one transaction) is stored in many rows. An example of transactional data is market basket data. With the single exception of Association Rules, which can operate on native transactional data, Oracle Data Mining algorithms require single-record case organization.

##### 2.3.2.1 Nested Data

Oracle Data Mining supports attributes in nested columns. A transactional table can be cast as a nested column and included in a table of single-record case data. Similarly, star schemas can be cast as nested columns. With nested data transformations, Oracle Data Mining can effectively mine data originating from multiple sources and configurations.

#### 2.3.3 Text Data

Prepare and transform unstructured text data for data mining.

Oracle Data Mining interprets `CLOB` columns and long `VARCHAR2` columns automatically as unstructured text. Additionally, you can specify columns of short `VARCHAR2`, `CHAR`, `BLOB`, and `BFILE` as unstructured text. Unstructured text includes data items such as web pages, document libraries, Power Point presentations, product specifications, emails, comment fields in reports, and call center notes.

Oracle Data Mining uses Oracle Text utilities and term weighting strategies to transform unstructured text for mining. In text transformation, text terms are extracted and given numeric values in a text index. The text transformation process is configurable for the model and for individual attributes. Once transformed, the text can by mined with a data mining algorithm.

**Related Topics**

- [Preparing the Data](../dmprg/preparing-data.md)
- [Transforming the Data](../dmprg/transforming-data.md)
- [Mining Unstructured Text](../dmprg/mining-unstructured-text.md)

### 2.4 In-Database Scoring

Scoring is the application of a data mining algorithm to new data. In traditional data mining, models are built using specialized software on a remote system and deployed to another system for scoring. This is a cumbersome, error-prone process open to security violations and difficulties in data synchronization.

With Oracle Data Mining, scoring is easy and secure. The scoring engine and the data both reside within the database. Scoring is an extension to the SQL language, so the results of mining can easily be incorporated into applications and reporting systems.

#### 2.4.1 Parallel Execution and Ease of Administration

All Oracle Data Mining scoring routines support parallel execution for scoring large data sets.

In-database scoring provides performance advantages. All Oracle Data Mining scoring routines support parallel execution, which significantly reduces the time required for executing complex queries and scoring large data sets.

In-database mining minimizes the IT effort needed to support data mining initiatives. Using standard database techniques, models can easily be refreshed (re-created) on more recent data and redeployed. The deployment is immediate since the scoring query remains the same; only the underlying model is replaced in the database.

**Related Topics**

- [Oracle Database VLDB and Partitioning Guide](../vldbg/using-parallel.md)

#### 2.4.2 SQL Functions for Model Apply and Dynamic Scoring

In Oracle Data Mining, scoring is performed by SQL language functions. Understand the different ways involved in SQL function scoring.

The functions perform prediction, clustering, and feature extraction. The functions can be invoked in two different ways: By applying a mining model object (Example 2-1), or by executing an analytic clause that computes the mining analysis dynamically and applies it to the data (Example 2-2). Dynamic scoring, which eliminates the need for a model, can supplement, or even replace, the more traditional data mining methodology described in "The Data Mining Process".

In Example 2-1, the `PREDICTION_PROBABILITY` function applies the model svmc_sh_clas_sample, created in [Example 1-1](introduction-to-oracle-data-mining.md), to score the data in `mining_data_apply_v`. The function returns the ten customers in Italy who are most likely to use an affinity card.

In Example 2-2, the functions `PREDICTION` and `PREDICTION_PROBABILITY` use the analytic syntax (the `OVER` () clause) to dynamically score the data in `mining_data_apply_v`. The query returns the customers who currently do not have an affinity card with the probability that they are likely to use.

Example 2-1 Applying a Mining Model to Score Data

    SELECT cust_id FROM
      (SELECT cust_id,
            rank() over (order by PREDICTION_PROBABILITY(svmc_sh_clas_sample, 1
                         USING *) DESC, cust_id) rnk
       FROM mining_data_apply_v
       WHERE country_name = 'Italy')
    WHERE rnk <= 10
    ORDER BY rnk;

       CUST_ID
    ----------
        101445
        100179
        100662
        100733
        100554
        100081
        100344
        100324
        100185
        101345

Example 2-2 Executing an Analytic Function to Score Data

    SELECT cust_id, pred_prob FROM
      (SELECT cust_id, affinity_card,
        PREDICTION(FOR TO_CHAR(affinity_card) USING *) OVER () pred_card,
        PREDICTION_PROBABILITY(FOR TO_CHAR(affinity_card),1 USING *) OVER () pred_prob
       FROM mining_data_build_v)
    WHERE affinity_card = 0
    AND pred_card = 1
    ORDER BY pred_prob DESC;

       CUST_ID PRED_PROB
    ---------- ---------
        102434       .96
        102365       .96
        102330       .96
        101733       .95
        102615       .94
        102686       .94
        102749       .93
        .
        .
        .
        101656       .51
