### ADP

See Automatic Data Preparation.

### aggregation

The process of consolidating data values into a smaller number of values. For example, sales data collected on a daily basis can be totaled to the week level.

### algorithm

A sequence of steps for solving a problem. See data mining algorithm. The Oracle Data Mining API supports the following algorithms: MDL, Apriori, Decision Tree, k-Means, Naive Bayes, GLM, O-Cluster, Support Vector Machines, Expectation Maximization, and Singular Value Decomposition.

### algorithm settings

The settings that specify algorithm-specific behavior for model building.

### anomaly detection

The detection of outliers or atypical cases. Oracle Data Mining implements Anomaly Detection as one-class SVM.

### apply

The data mining operation that scores data. Scoring is the process of applying a model to new data to predict results.

### Apriori

The algorithm that uses frequent itemsets to calculate associations.

### association

A machine learning technique that identifies relationships among items.

### association rules

A mining technique that captures co-occurrence of items among transactions. A typical rule is an implication of the form A -\> B, which means that the presence of itemset A implies the presence of itemset B with certain support and confidence. The support of the rule is the ratio of the number of transactions where the itemsets A and B are present to the total number of transactions. The confidence of the rule is the ratio of the number of transactions where the itemsets A and B are present to the number of transactions where itemset A is present. Oracle Data Mining uses the Apriori algorithm for association models.

### attribute

An attribute is a predictor in a predictive model or an item of descriptive information in a descriptive model. Data attributes are the columns of data that are used to build a model. Data attributes undergo transformations so that they can be used as categoricals or numericals by the model. Categoricals and numericals are model attributes. See also target.

### attribute importance

A mining technique that provides a measure of the importance of an attribute and predicts a specified target. The measure of different attributes of a training data table enables users to select the attributes that are found to be most relevant to a mining model. A smaller set of attributes results in a faster model build; the resulting model could be more accurate. Oracle Data Mining uses the Minimum Description Length to discover important attributes. Sometimes referred to as feature selection or key fields.

### Automatic Data Preparation

Mining models can be created with Automatic Data Preparation (ADP), which transforms the build data according to the requirements of the algorithm and embeds the transformation instructions in the model. The embedded transformations are executed whenever the model is applied to new data.

### bagging

Combine independently trained models on bootstrap samples (bagging is bootstrap aggregating).

### binning

See discretization.

### build data

Data used to build (train) a model. Also called training data.

### case

All the data collected about a specific transaction or related set of values. A data set is a collection of cases. Cases are also called records or examples. In the simplest situation, a case corresponds to a row in a table.

### case table

A table or view in single-record case format. All the data for each case is contained in a single row. The case table may include a case ID column that holds a unique identifier for each row. Mining data must be presented as a case table.

### categorical attribute

An attribute whose values correspond to discrete categories. For example, state is a categorical attribute with discrete values (CA, NY, MA). Categorical attributes are either non-ordered (nominal) like state or gender, or ordered (ordinal) such as high, medium, or low temperatures.

### centroid

See cluster centroid.

### classification

A mining technique for predicting categorical target values for new records using a model built from records with known target values. Oracle Data Mining supports the following algorithms for classification: Naive Bayes, Decision Tree, Generalized Linear Models, and Support Vector Machines.

### clipping

See trimming.

### cluster centroid

The vector that encodes, for each attribute, either the mean (if the attribute is numerical) or the mode (if the attribute is categorical) of the cases in the training data assigned to a cluster. A cluster centroid is often referred to as "the centroid."

### clustering

A mining technique for finding naturally occurring groupings in data. More precisely, given a set of data points, each having a set of attributes, and a similarity measure among them, clustering is the process of grouping the data points into different clusters such that data points in the same cluster are more similar to one another and data points in different clusters are less similar to one another. Oracle Data Mining supports three algorithms for clustering, k-Means, Orthogonal Partitioning Clustering, and Expectation Maximization.

### confusion matrix

Measures the correctness of predictions made by a model from a test task. The row indexes of a confusion matrix correspond to actual values observed and provided in the test data. The column indexes correspond to predicted values produced by applying the model to the test data. For any pair of actual/predicted indexes, the value indicates the number of records classified in that pairing.

When predicted value equals actual value, the model produces correct predictions. All other entries indicate errors.

### cost matrix

An n by n table that defines the cost associated with a prediction versus the actual value. A cost matrix is typically used in classification models, where n is the number of distinct values in the target, and the columns and rows are labeled with target values. The rows are the actual values; the columns are the predicted values.

### counterexample

Negative instance of a target. Counterexamples are required for classification models, except for one-class Support Vector Machines.

### data mining

Data mining is the practice of automatically searching large stores of data to discover patterns and trends that go beyond simple analysis. Data mining uses sophisticated mathematical algorithms to segment the data and evaluate the probability of future events. Data mining is also known as Knowledge Discovery in Data (KDD).

A data mining model implements a data mining algorithm to solve a given type of problem for a given set of data.

### data mining algorithm

A specific technique or procedure for producing a data mining model. An algorithm uses a specific data representation and a specific mining technique.

The algorithms supported by Oracle Data Mining are Naive Bayes, Support Vector Machines, Generalized Linear Model, and Decision Tree for classification; Support Vector Machines and Generalized Linear Model for regression; k-Means, O-Cluster and Expectation Maximization for clustering; Minimum Description Length for attribute importance; Non-Negative Matrix Factorization and Singular Value Decomposition for feature extraction; Apriori for associations, and one-class Support Vector Machines for anomaly detection.

### data mining server

The component of Oracle Database that implements the data mining engine and persistent metadata repository. You must connect to a data mining server before performing data mining tasks.

### data set

In general, a collection of data. A data set is a collection of cases.

### descriptive model

A descriptive model helps in understanding underlying processes or behavior. For example, an association model may describe consumer buying patterns. See also mining model.

### discretization

Discretization (binning) groups related values together under a single value (or bin). This reduces the number of distinct values in a column. Fewer bins result in models that build faster. Many Oracle Data Mining algorithms (for example NB) may benefit from input data that is discretized prior to model building, testing, computing lift, and applying (scoring). Different algorithms may require different types of binning. Oracle Data Mining supports supervised binning, top N frequency binning for categorical attributes and equi-width binning and quantile binning for numerical attributes.

### distance-based (clustering algorithm)

Distance-based algorithms rely on a distance metric (function) to measure the similarity between data points. Data points are assigned to the nearest cluster according to the distance metric used.

### Decision Tree

A decision tree is a representation of a classification system or supervised model. The tree is structured as a sequence of questions; the answers to the questions trace a path down the tree to a leaf, which yields the prediction.

Decision trees are a way of representing a series of questions that lead to a class or value. The top node of a decision tree is called the root node; terminal nodes are called leaf nodes. Decision trees are grown through an iterative splitting of data into discrete groups, where the goal is to maximize the distance between groups at each split.

An important characteristic of the decision tree models is that they are transparent; that is, there are rules that explain the classification.

See also rule .

### equi-width binning

Equi-width binning determines bins for numerical attributes by dividing the range of values into a specified number of bins of equal size.

### Expectation Maximization

Expectation Maximization is a probabilistic clustering algorithm that creates a density model of the data. The density model allows for an improved approach to combining data originating in different domains (for example, sales transactions and customer demographics, or structured data and text or other unstructured data).

### explode

For a categorical attribute, replace a multi-value categorical column with several binary categorical columns. To explode the attribute, create a new binary column for each distinct value that the attribute takes on. In the new columns, 1 indicates that the value of the attribute takes on the value of the column; 0, that it does not. For example, suppose that a categorical attribute takes on the values {1, 2, 3}. To explode this attribute, create three new columns, `col_1`, `col_2`, and `col_3`. If the attribute takes on the value 1, the value in `col_1` is 1; the values in the other two columns is 0.

### feature

A combination of attributes in the data that is of special interest and that captures important characteristics of the data. See feature extraction.

See also text feature.

### feature extraction

Creates a new set of features by decomposing the original data. Feature extraction lets you describe the data with a number of features that is usually far smaller than the number of original attributes. See also Non-Negative Matrix Factorization and Singular Value Decomposition.

### Generalized Linear Model

A statistical technique for linear modeling. Generalized linear models (GLM) include and extend the class of simple linear models. Oracle Data Mining supports logistic regression for GLM classification and linear regression for GLM regression.

### GLM

See Generalized Linear Model.

### k-Means

A distance-based clustering algorithm that partitions the data into a predetermined number of clusters (provided there are enough distinct cases). Distance-based algorithms rely on a distance metric (function) to measure the similarity between data points. Data points are assigned to the nearest cluster according to the distance metric used. Oracle Data Mining provides an enhanced version of k-Means.

### lift

A measure of how much better prediction results are using a model than could be obtained by chance. For example, suppose that 2% of the customers mailed a catalog make a purchase; suppose also that when you use a model to select catalog recipients, 10% make a purchase. Then the lift for the model is 10/2 or 5. Lift may also be used as a measure to compare different data mining models. Since lift is computed using a data table with actual outcomes, lift compares how well a model performs with respect to this data on predicted outcomes. Lift indicates how well the model improved the predictions over a random selection given actual results. Lift allows a user to infer how a model performs on new data.

### lineage

The sequence of transformations performed on a data set during the data preparation phase of the model build process.

### linear regression

The GLM regression algorithm supported by Oracle Data Mining.

### logistic regression

The GLM classification algorithm supported by Oracle Data Mining.

### MDL

See Minimum Description Length.

### min-max normalization

Normalizes numerical attributes using this transformation:

     x_new = (x_old-min) / (max-min)

### Minimum Description Length

Given a sample of data and an effective enumeration of the appropriate alternative theories to explain the data, the best theory is the one that minimizes the sum of

- The length, in bits, of the description of the theory

- The length, in bits, of the data when encoded with the help of the theory

The Minimum Description Length principle is used to select the attributes that most influence target value discrimination in attribute importance.

### mining technique

A major subdomain of data mining that shares common high level characteristics. The Oracle Data Mining API supports the following mining techniques: classification , regression, attribute importance, feature extraction, clustering, and anomaly detection.

### mining model

A first-class schema object that specifies a data mining model in Oracle Database.

### missing value

A data value that is missing at random. The value could be missing because it is unavailable, unknown, or because it was lost. Oracle Data Mining interprets missing values in columns with simple data types (not nested) as missing at random. Oracle Data Mining interprets missing values in nested columns as sparsity.

Data mining algorithms vary in the way they treat missing values. There are several typical ways to treat them: ignore them, omit any records containing missing values, replace missing values with the mode or mean, or infer missing values from existing values. See also sparse data.

### model

A model uses an algorithm to implement a given mining technique. A model can be a supervised model or an unsupervised model. A model can be used for direct inspection, for example, to examine the rules produced from an association model, or to score data (predict an outcome). In Oracle Database, data mining models are implemented as mining model schema objects.

### multi-record case

Each case in the data table is stored in multiple rows. Also known as transactional data. See also single-record case.

### Naive Bayes

An algorithm for classification that is based on Bayes's theorem. Naive Bayes makes the assumption that each attribute is conditionally independent of the others: given a particular value of the target, the distribution of each predictor is independent of the other predictors.

### nested data

Oracle Data Mining supports transactional data in nested columns of name/value pairs. Multidimensional data that expresses a one-to-many relationship can be loaded into a nested column and mined along with single-record case data in a case table.

### NMF

See Non-Negative Matrix Factorization.

### Non-Negative Matrix Factorization

A feature extraction algorithm that decomposes multivariate data by creating a user-defined number of features, which results in a reduced representation of the original data.

### normalization

Normalization consists of transforming numerical values into a specific range, such as \[–1.0,1.0\] or \[0.0,1.0\] such that `x_new = (x_old-shift)/scale`. Normalization applies only to numerical attributes. Oracle Data Mining provides transformations that perform min-max normalization, scale normalization, and z-score normalization.

### numerical attribute

An attribute whose values are numbers. The numeric value can be either an integer or a real number. Numerical attribute values can be manipulated as continuous values. See also categorical attribute.

### O-Cluster

See Orthogonal Partitioning Clustering.

### one-class Support Vector Machines

The version of Support Vector Machines used to solve anomaly detection problems. The algorithm performs classification without a target.

### Orthogonal Partitioning Clustering

An Oracle proprietary clustering algorithm that creates a hierarchical grid-based clustering model, that is, it creates axis-parallel (orthogonal) partitions in the input attribute space. The algorithm operates recursively. The resulting hierarchical structure represents an irregular grid that tessellates the attribute space into clusters.

### outlier

A data value that does not come from the typical population of data or extreme values. In a normal distribution, outliers are typically at least three standard deviations from the mean.

### positive target value

In binary classification problems, you may designate one of the two classes (target values) as positive, the other as negative. When Oracle Data Mining computes a model's lift, it calculates the density of positive target values among a set of test instances for which the model predicts positive values with a given degree of confidence.

### predictive model

A predictive model is an equation or set of rules that makes it possible to predict an unseen or unmeasured value (the dependent variable or output) from other, known values (independent variables or input). The form of the equation or rules is suggested by mining data collected from the process under study. Some training or estimation technique is used to estimate the parameters of the equation or rules. A predictive model is a supervised model.

### predictor

An attribute used as input to a supervised algorithm to build a model.

### prepared data

Data that is suitable for model building using a specified algorithm. Data preparation often accounts for much of the time spent in a data mining project. Automatic Data Preparation greatly simplifies model development and deployment by automatically preparing the data for the algorithm.

### Principal Component Analysis

Principal Component Analysis is implemented as a special scoring method for the Singular Value Decomposition algorithm.

### prior probabilities

The set of prior probabilities specifies the distribution of examples of the various classes in the original source data. Also referred to as priors, these could be different from the distribution observed in the data set provided for model build.

### priors

See prior probabilities.

### quantile binning

A numerical attribute is divided into bins such that each bin contains approximately the same number of cases.

### random sample

A sample in which every element of the data set has an equal chance of being selected.

### recode

Literally "change or rearrange the code." Recoding can be useful in preparing data according to the requirements of a given business problem, for example:

- Missing values treatment: Missing values may be indicated by something other than `NULL`, such as "0000" or "9999" or "NA" or some other string. One way to treat the missing value is to recode, for example, "0000" to `NULL`. Then the Oracle Data Mining algorithms and the database recognize the value as missing.

- Change data type of variable: For example, change "Y" or "Yes" to 1 and "N" or "No" to 0.

- Establish a cutoff value: For example, recode all incomes less than \$20,000 to the same value.

- Group items: For example, group individual US states into regions. The "New England region" might consist of ME, VT, NH, MA, CT, and RI; to implement this, recode the five states to, say, NE (for New England).

### record

See case.

### regression

A data mining technique for predicting continuous target values for new records using a model built from records with known target values. Oracle Data Mining supports linear regression (GLM) and Support Vector Machines algorithms for regression.

### rule

An expression of the general form if X, then Y. An output of certain algorithms, such as clustering, association, and decision tree. The predicate X may be a compound predicate.

### sample

See random sample.

### scale normalization

Normalize numerical attributes using this transformation:

     x_new = (x_old - 0) / (max(abs(max),abs(min)))

### schema

A collection of objects in an Oracle database, including logical structures such as tables, views, sequences, stored procedures, synonyms, indexes, clusters, and database links. A schema is associated with a specific database user.

### score

Scoring data means applying a data mining model to data to generate predictions.

### settings

Seealgorithm settings.

### single-record case

Each case in the data table is stored in one row. Contrast with multi-record case.

### Singular Value Decomposition

A feature extraction algorithm that uses orthogonal linear projections to capture the underlying variance of the data. Singular Value Decomposition scales well to very large data sizes (both rows and attributes), and has a powerful data compression capability.

See Singular Value Decomposition.

### sparse data

Data for which only a small fraction of the attributes are non-zero or non-null in any given case. Market basket data and unstructured text data are typically sparse. Oracle Data Mining interprets nested data as sparse. See also missing value.

### split

Divide a data set into several disjoint subsets. For example, in a classification problem, a data set is often divided in to a training data set and a test data set.

### stratified sample

Divide the data set into disjoint subsets (strata) and then take a random sample from each of the subsets. This technique is used when the distribution of target values is skewed greatly. For example, response to a marketing campaign may have a positive target value 1% of the time or less. A stratified sample provides the data mining algorithms with enough positive examples to learn the factors that differentiate positive from negative target values. See also random sample.

### supervised binning

A form of intelligent binning wherein bin boundaries are derived from important characteristics of the data. Supervised binning builds a single-predictor decision tree to find the interesting bin boundaries with respect to a target. Supervised binning can be used for numerical or categorical attributes.

### supervised learning

See supervised model.

### supervised model

A data mining model that is built using a known dependent variable, also referred to as the target. Classification and regression techniques are examples of supervised mining. See unsupervised model. Also referred to as predictive model.

### Support Vector Machines

An algorithm that uses machine learning theory to maximize predictive accuracy while automatically avoiding over-fit to the data. Support Vector Machines can make predictions with sparse data, that is, in domains that have a large number of predictor columns and relatively few rows, as is the case with bioinformatics data. Support Vector Machines can be used for classification, regression, and anomaly detection.

### SVM

See Support Vector Machines.

### target

In supervised learning, the identified attribute that is to be predicted. Sometimes called target value or target attribute. See also attribute.

### text feature

A combination of words that captures important attributes of a document or class of documents. Text features are usually keywords, frequencies of words, or other document-derived features. A document typically contains a large number of words and a much smaller number of features.

### text mining

Conventional data mining done using text features. Text features are usually keywords, frequencies of words, or other document-derived features. Once you derive text features, you mine them just as you would any other data. Both Oracle Data Mining and Oracle Text support text mining.

### top N frequency binning

This type of binning bins categorical attributes. The bin definition for each attribute is computed based on the occurrence frequency of values that are computed from the data. The user specifies a particular number of bins, say N. Each of the bins bin_1,..., bin_N corresponds to the values with top frequencies. The bin bin_N+1 corresponds to all remaining values.

### training data

See build data.

### transactional data

The data for one case is contained in several rows. An example is market basket data, in which a case represents one basket that contains multiple items. Oracle Data Mining supports transactional data in nested columns of attribute name/value pairs. See also nested data, multi-record case, and single-record case.

### transformation

A function applied to data resulting in a new representation of the data. For example, discretization and normalization are transformations on data.

### trimming

A technique for minimizing the impact of outliers. Trimming removes values in the tails of a distribution in the sense that trimmed values are ignored in further computations. Trimming is achieved by setting the tails to `NULL`.

### unstructured data

Images, audio, video, geospatial mapping data, and documents or text data are collectively known as unstructured data. Oracle Data Mining supports the mining of unstructured text data.

### unsupervised learning

See unsupervised model.

### unsupervised model

A data mining model built without the guidance (supervision) of a known, correct result. In supervised learning, this correct result is provided in the target attribute. Unsupervised learning has no such target attribute. Clustering and association are examples of unsupervised mining techniques. See supervised model.

### winsorizing

A technique for minimizing the impact of outliers. Winsorizing involves setting the tail values of an particular attribute to some specified value. For example, for a 90% Winsorization, the bottom 5% of values are set equal to the minimum value in the 6th percentile, while the upper 5% are set equal to the maximum value in the 95th percentile.

### z-score normalization

Normalize numerical attributes using this transformation:

    x_new = (x_old-mean) / standard_deviation
