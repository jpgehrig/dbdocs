The `GET_*` interfaces are replaced by model views, and Oracle recommends that users leverage the views instead.

The following are the new model views:

Association:

- Model Detail Views for Association Rules

- Model Detail View for Frequent Itemsets

- Model Detail View for Transactional Itemsets

- Model Detail View for Transactional Rule

Classification, Regression, and Anomaly Detection:

- Model Detail Views for Classification Algorithms

- Model Detail Views for CUR Matrix Decomposition

- Model Detail Views for Decision Tree

- Model Detail Views for Generalized Linear Model

- Model Detail Views for Naive Bayes

- Model Detail Views for Neural Network

- Model Detail Views for Random Forest

- Model Detail View for Support Vector Machine

Clustering:

- Model Detail Views for Clustering Algorithms

- Model Detail Views for Expectation Maximization

- Model Detail Views for k-Means

- Model Detail Views for O-Cluster

Feature Extraction:

- Model Detail Views for Explicit Semantic Analysis

- Model Detail Views for Non-Negative Matrix Factorization

- Model Detail Views for Singular Value Decomposition

Feature Selection:

- Model Detail View for Minimum Description Length

Data Preparation and Other:

- Model Detail View for Binning

- Model Detail Views for Global Information

- Model Detail View for Normalization and Missing Value Handling

Time Series:

Model Detail Views for Exponential Smoothing Models

### 5.4.1 Model Detail Views for Association Rules

Model detail views for Association Rules describe the rule view for Association Rules. Oracle recommends that users leverage the model details views instead of the `GET_ASSOCIATION_RULES` function.

The rule view `DM$VR`model_name describes the generated rules for Association Rules. Depending on the settings of the model, the rule view has different set of columns. Settings `ODMS_ITEM_ID_COLUMN_NAME` and `ODMS_ITEM_VALUE_COLUMN_NAME` determine how each item is defined. If `ODMS_ITEM_ID_COLUMN_NAME` is set, the input format is called transactional input, otherwise, the input format is called 2-Dimensional input. With transactional input, if setting `ODMS_ITEM_VALUE_COLUMN_NAME` is not set, each item is defined by `ITEM_NAME`, otherwise, each item is defined by `ITEM_NAME` and `ITEM_VALUE`. With 2-Dimensional input, each item is defined by `ITEM_NAME`, `ITEM_SUBNAME` and `ITEM_VALUE`. Setting `ASSO_AGGREGATES` specifies the columns to aggregate, which is displayed in the view.

**Note:**

Setting `ASSO_AGGREGATES` is not allowed for 2-dimensional input.

The following shows the views with different settings.

#### Transactional Input Without ASSO_AGGREGATES Setting

When setting `ITEM_NAME` (`ODMS_ITEM_ID_COLUMN_NAME`) is set and `ITEM_VALUE` (`ODMS_ITEM_VALUE_COLUMN_NAME`) is not set, the following is the view. Here the consequent item is defined with only name field. If `ITEM_VALUE` setting is also set, the view will have one extra column `CONSEQUENT_VALUE` to specify the value field.

    Name                                      Type
     ----------------------------------------- ----------------------------
     PARTITION_NAME                            VARCHAR2(128)
     RULE_ID                                   NUMBER
     RULE_SUPPORT                              NUMBER
     RULE_CONFIDENCE                           NUMBER
     RULE_LIFT                                 NUMBER
     RULE_REVCONFIDENCE                        NUMBER
     ANTECEDENT_SUPPORT                        NUMBER
     NUMBER_OF_ITEMS                           NUMBER
     CONSEQUENT_SUPPORT                        NUMBER
     CONSEQUENT_NAME                           VARCHAR2(4000)
     ANTECEDENT                                SYS.XMLTYPE

Table 5-11 Rule View Columns for Transactional Inputs

| Column Name          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:---------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`     | A partition in a partitioned model to retrieve details                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `RULE_ID`            | Identifier of the rule                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `RULE_SUPPORT`       | The number of transactions that satisfy the rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `RULE_CONFIDENCE`    | The likelihood of a transaction satisfying the rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `RULE_LIFT`          | The degree of improvement in the prediction over random chance when the rule is satisfied.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `RULE_REVCONFIDENCE` | The number of transactions in which the rule occurs divided by the number of transactions in which the consequent occurs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `ANTECEDENT_SUPPORT` | The ratio of the number of transactions that satisfy the antecedent to the total number of transactions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `NUMBER_OF_ITEMS`    | The total number of attributes referenced in the antecedent and consequent of the rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `CONSEQUENT_SUPPORT` | The ratio of the number of transactions that satisfy the consequent to the total number of transactions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `CONSEQUENT_NAME`    | Name of the consequent                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `CONSEQUENT_VALUE`   | Value of the consequent when setting `Item_value` (`ODMS_ITEM_VALUE_COLUMN_NAME`) is set with `TYPE` as numerical, the view has a `CONSEQUENT_VALUE` column.<br>When setting `Item_value` (`ODMS_ITEM_VALUE_COLUMN_NAME`) is set with `TYPE` as categorical, the view has a `CONSEQUENT_VALUE` column.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `ANTECEDENT`         | The antecedent is described as an itemset. At the itemset level, it specifies the number of aggregates, and if not zero, the names of the columns to be aggregated (as well as the mapping to `ASSO_AGG`\*). The itemset contains `>= 1` items.<br>• When setting `ODMS_ITEM_VALUE_COLUMN_NAME` is not set, each item is defined by `item_name`. As an example, assume the antecedent contains one item B, it is represented as follows:<br>`<itemset NUMAGGR="0"><item><item_name>B</item_name></item></itemset>`<br>• As another example, assume the antecedent contains two items, A and C, it is represented as follows:<br>`<itemset NUMAGGR="0"><item><item_name>A</item_name></item><item><item_name>C</item_name></item></itemset>`<br>• When setting `ODMS_ITEM_VALUE_COLUMN_NAME` is set, each item is defined by `item_name` and `item_value`. As an example, assume the antecedent contains two items, (name A, value 1) and (name C, value 1), then it is represented as follows:<br>`<itemset NUMAGGR="0"><item><item_name>A</item_name><item_value>1</item_value></item><item><item_name>C</item_name><item_value>1</item_value></item></itemset>` |

#### Transactional Input With ASSO_AGGREGATES Setting

Similar to the view without aggregates setting, there are three cases:

- Rule view when `ODMS_ITEM_ID_COLUMN_NAME` is set and `Item_value` (`ODMS_ITEM_VALUE_COLUMN_NAME`) is not set.

- Rule view when `ODMS_ITEM_ID_COLUMN_NAME` is set and `Item_value` (`ODMS_ITEM_VALUE_COLUMN_NAME`) is set with `TYPE` as numerical, the view has a `CONSEQUENT_VALUE` column.

- Rule view when `ODMS_ITEM_ID_COLUMN_NAME` is set and `Item_value` (`ODMS_ITEM_VALUE_COLUMN_NAME`) is set with `TYPE` as categorical, the view has a `CONSEQUENT_VALUE` column.

For example, refer “[Example: Calculating Aggregates](../dmcon/apriori.md)” in Oracle Data Mining Concepts.

The view reports two sets of aggregates results:

1.  `ANT_RULE_PROFIT` refers to the total profit for the antecedent itemset with respect to the rule, the profit for each individual item of the antecedent itemset is shown in the `ANTECEDENT(XMLtype)` column, `CON_RULE_PROFIT` refers to the total profit for the consequent item with respect to the rule.

    In the example, for rule (A, B) =\> C, the rule itemset (A, B, C) occurs in the transactions of customer 1 and customer 3. The `ANT_RULE_PROFIT` is \$21.20, The `ANTECEDENT` is shown as follow, which tells that item A has profit 5.00 + 3.00 = \$8.00 and item B has profit 3.20 + 10.00 = \$13.20, which sum up to `ANT_RULE_PROFIT`.

        <itemset NUMAGGR="1" ASSO_AGG0="profit"><item><item_name>A</item_name><ASSO_AGG0>8.0E+000</ASSO_AGG0></item><item><item_name>B</item_name><ASSO_AGG0>1.32E+001</ASSO_AGG0></item></itemset>
        The CON_RULE_PROFIT is 12.00 + 14.00 = $26.00

2.  `ANT_PROFIT` refers to the total profit for the antecedent itemset, while `CON_PROFIT` refers to the total profit for the consequent item. The difference between `CON_PROFIT` and `CON_RULE_PROFIT` (the same applies to `ANT_PROFIT` and `ANT_RULE_PROFIT`) is that `CON_PROFIT` counts all profit for the consequent item across all transactions where the consequent occurs, while `CON_RULE_PROFIT` only counts across transactions where the rule itemset occurs.

    For example, item C occurs in transactions for customer 1, 2 and 3, `CON_PROFIT` is 12.00 + 4.20 + 14.00 = \$30.20, while `CON_RULE_PROFIT` only counts transactions for customer 1 and 3 where the rule itemset (A, B, C) occurs.

    Similarly, `ANT_PROFIT` counts all transactions where itemset (A, B) occurs, while `ANT_RULE_PROFIT` counts only transactions where the rule itemset (A, B, C) occurs. In this example, by coincidence, both count transactions for customer 1 and 3, and have the same value.

Example 5-13 Examples

The following example shows the view when setting `ASSO_AGGREGATES` specifies column profit and column sales to be aggregated. In this example, `ITEM_VALUE` column is not specified.

    Name                                      Type
     ----------------------------------------- ----------------------------
     PARTITION_NAME                            VARCHAR2(128)
     RULE_ID                                   NUMBER
     RULE_SUPPORT                              NUMBER
     RULE_CONFIDENCE                           NUMBER
     RULE_LIFT                                 NUMBER
     RULE_REVCONFIDENCE                        NUMBER
     ANTECEDENT_SUPPORT                        NUMBER
     NUMBER_OF_ITEMS                           NUMBER
     CONSEQUENT_SUPPORT                        NUMBER
     CONSEQUENT_NAME                           VARCHAR2(4000)
     ANTECEDENT                                SYS.XMLTYPE
     ANT_RULE_PROFIT                           BINARY_DOUBLE
     CON_RULE_PROFIT                           BINARY_DOUBLE
     ANT_PROFIT                                BINARY_DOUBLE
     CON_PROFIT                                BINARY_DOUBLE
     ANT_RULE_SALES                            BINARY_DOUBLE
     CON_RULE_SALES                            BINARY_DOUBLE
     ANT_SALES                                 BINARY_DOUBLE
     CON_SALES                                 BINARY_DOUBLE

Rule view when `ODMS_ITEM_ID_COLUMN_NAME` is set and `Item_value` (`ODMS_ITEM_VALUE_COLUMN_NAME`) is set with `TYPE` as numerical, the view has a `CONSEQUENT_VALUE` column.

Rule view when `ODMS_ITEM_ID_COLUMN_NAME` is set and `Item_value` (`ODMS_ITEM_VALUE_COLUMN_NAME`) is set with `TYPE` as categorical, the view has a `CONSEQUENT_VALUE` column.

#### 2-Dimensional Inputs

In Oracle Data Mining, association models can be built using either transactional or two-dimensional data formats. For two-dimensional input, each item is defined by three fields: `NAME`, `VALUE` and `SUBNAME`. The `NAME` field is the name of the column. The `VALUE` field is the content of the column. The `SUBNAME` field is used when input data table contains nested table. In such case, the `SUBNAME` is the name of the nested table's column. See, [Example: Creating a Nested Column for Market Basket Analysis](using-market-basket-data.md). In this example, there is a nested column. The `CONSEQUENT_SUBNAME` is the `ATTRIBUTE_NAME` part of the nested column. That is, `'O/S Documentation Set - English'` and `CONSEQUENT_VALUE` is the value part of the nested column, which is, 1.

The view uses three columns for consequent. The rule view has the following columns:

    Name                                      Type
     ----------------------- ---------------------
     PARTITION_NAME                            VARCHAR2(128)
     RULE_ID                                   NUMBER
     RULE_SUPPORT                              NUMBER
     RULE_CONFIDENCE                           NUMBER
     RULE_LIFT                                 NUMBER
     RULE_REVCONFIDENCE                        NUMBER
     ANTECEDENT_SUPPORT                        NUMBER
     NUMBER_OF_ITEMS                           NUMBER
     CONSEQUENT_SUPPORT                        NUMBER
     CONSEQUENT_NAME                           VARCHAR2(4000)
     CONSEQUENT_SUBNAME                        VARCHAR2(4000)
     CONSEQUENT_VALUE                          VARCHAR2(4000)
     ANTECEDENT                                SYS.XMLTYPE

**Note:**

All the types for three parts are `VARCHAR2`. `ASSO_AGGREGATES` is not applicable for 2-Dimensional input format.

The following table displays rule view columns for 2-Dimensional input with the descriptions of only the fields which are specific to 2-D inputs.

Table 5-12 Rule View for 2-Dimensional Input

| Column Name          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CONSEQUENT_SUBNAME` | For two-dimensional inputs, `CONSEQUENT_SUBNAME` is used for nested column in the input data table.                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `CONSEQUENT_VALUE`   | Value of the consequent when setting `Item_value` is set with `TYPE` as numerical, the view has a `CONSEQUENT_VALUE` column.<br>When setting `Item_value` is set with `TYPE` as categorical, the view has a `CONSEQUENT_VALUE` column.                                                                                                                                                                                                                                                                                                                   |
| `ANTECEDENT`         | The antecedent is described as an itemset. The itemset contains `>= 1` items. Each item is defined using `ITEM_NAME`, `ITEM_SUBNAME`, and `ITEM_VALUE`:<br>As an example, assuming that this is not a nested table input, and the antecedent contains one item: (name `ADDR`, value `MA`). The antecedent (XMLtype) is as follows:<br>`<itemset NUMAGGR="0"><item><item_name>ADDR</item_name><item_subname></item_subna`<br>`me><item_value>MA</item_value></item></itemset>`<br>For 2-Dimensional input with nested table, the subname field is filled. |

#### Global Detail for Association Rules

A single global detail is produced by an Association model. The following table describes a global detail returned for Association Rules model.

Table 5-13 Global Detail for Association Rules

| Name                | Description                                            |
|:--------------------|:-------------------------------------------------------|
| `ITEMSET_COUNT`     | The number of itemsets generated                       |
| `MAX_SUPPORT`       | The maximum support                                    |
| `NUM_ROWS`          | The total number of rows used in the build             |
| `RULE_COUNT`        | The number of association rules in the model generated |
| `TRANSACTION_COUNT` | The number of the transactions in input data           |

### 5.4.2 Model Detail View for Frequent Itemsets

Model detail view for Frequent Itemsets describes the frequent itemsets view. Oracle recommends that you leverage model details view instead of the `GET_FREQUENT_ITEMSETS` function.

The frequent itemsets view `DM$VI`model_name has the following schema:

    Name                  Type
     ------------- ------------------
     PARTITION_NAME   VARCHAR2 (128)
     ITEMSET_ID       NUMBER
     SUPPORT          NUMBER
     NUMBER_OF_ITEMS  NUMBER
     ITEMSET          SYS.XMLTYPE

Table 5-14 Frequent Itemsets View

| Column Name       | Description                                                                                                                                |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`  | A partition in a partitioned model                                                                                                         |
| `ITEMSET_ID`      | Itemset identifier                                                                                                                         |
| `SUPPORT`         | Support of the itemset                                                                                                                     |
| `NUMBER_OF_ITEMS` | Number of items in the itemset                                                                                                             |
| `ITEMSET`         | Frequent itemset<br>The structure of the `SYS.XMLTYPE` column itemset is the same as the corresponding Antecedent column of the rule view. |

### 5.4.3 Model Detail View for Transactional Itemsets

Model detail view for Transactional Itemsets describes the transactional itemsets view. Oracle recommends that users leverage the model details views.

For the very common case of transactional data without aggregates, `DM$VT`model_name view provides the itemsets information in transactional format. This view can help improve performance for some queries as compared to the view with the XML column. The transactional itemsets view has the following schema:

    Name                    Type
     ----------------- -----------------
     PARTITION_NAME      VARCHAR2(128)
     ITEMSET_ID          NUMBER
     ITEM_ID             NUMBER
     SUPPORT             NUMBER
     NUMBER_OF_ITEMS     NUMBER
     ITEM_NAME           VARCHAR2(4000)

Table 5-15 Transactional Itemsets View

| Column Name       | Description                        |
|:------------------|:-----------------------------------|
| `PARTITION_NAME`  | A partition in a partitioned model |
| `ITEMSET_ID`      | Itemset identifier                 |
| `ITEM_ID`         | Item identifier                    |
| `SUPPORT`         | Support of the itemset             |
| `NUMBER_OF_ITEMS` | Number of items in the itemset     |
| `ITEM_NAME`       | The name of the item               |

### 5.4.4 Model Detail View for Transactional Rule

Model detail view for Transactional Rule describes the transactional rule view and transactional itemsets view. Oracle recommends that you leverage model details views.

Transactional data without aggregates also has a transactional rule view `DM$VA`model_name. This view can improve performance for some queries as compared to the view with the XML column. The transactional rule view has the following schema:

    Name                                      Type
     ----------------------------------------- ----------------------------
     PARTITION_NAME                            VARCHAR2(128)
     RULE_ID                                   NUMBER
     ANTECEDENT_PREDICATE                      VARCHAR2(4000)
     CONSEQUENT_PREDICATE                      VARCHAR2(4000)
     RULE_SUPPORT                              NUMBER
     RULE_CONFIDENCE                           NUMBER
     RULE_LIFT                                 NUMBER
     RULE_REVCONFIDENCE                        NUMBER
     RULE_ITEMSET_ID                           NUMBER
     ANTECEDENT_SUPPORT                        NUMBER
     CONSEQUENT_SUPPORT                        NUMBER
     NUMBER_OF_ITEMS                           NUMBER

Table 5-16 Transactional Rule View

| Column Name            | Description                                                                                                              |
|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`       | A partition in a partitioned model                                                                                       |
| `RULE_ID`              | Rule identifier                                                                                                          |
| `ANTECEDENT_PREDICATE` | Name of the Antecedent item.                                                                                             |
| `CONSEQUENT_PREDICATE` | Name of the Consequent item                                                                                              |
| `RULE_SUPPORT`         | Support of the rule                                                                                                      |
| `RULE_CONFIDENCE`      | The likelihood a transaction satisfies the rule when it contains the Antecedent.                                         |
| `RULE_LIFT`            | The degree of improvement in the prediction over random chance when the rule is satisfied                                |
| `RULE_REVCONFIDENCE`   | The number of transactions in which the rule occurs divided by the number of transactions in which the consequent occurs |
| `RULE_ITEMSET_ID`      | Itemset identifier                                                                                                       |
| `ANTECEDENT_SUPPORT`   | The ratio of the number of transactions that satisfy the antecedent to the total number of transactions                  |
| `CONSEQUENT_SUPPORT`   | The ratio of the number of transactions that satisfy the consequent to the total number of transactions                  |
| `NUMBER_OF_ITEMS`      | Number of items in the rule                                                                                              |

### 5.4.5 Model Detail Views for Classification Algorithms

Model detail view for Classification algorithms describe target map view and scoring cost view which are applicable to all Classification algorithms. Oracle recommends that users leverage the model details views instead of the `GET_*` function.

The target map view `DM$VT`model_name describes the target distribution for Classification models. The view has the following schema:

    Name                                      Type
     ----------------------------------------- ----------------------------
     PARTITION_NAME                            VARCHAR2(128)
     TARGET_VALUE                              NUMBER/VARCHAR2
     TARGET_COUNT                              NUMBER
     TARGET_WEIGHT                             NUMBER

Table 5-17 Target Map View

| Column Name      | Description                               |
|:-----------------|:------------------------------------------|
| `PARTITION_NAME` | Partition name in a partitioned model     |
| `TARGET_VALUE`   | Target value, numerical or categorical    |
| `TARGET_COUNT`   | Number of rows for a given `TARGET_VALUE` |
| `TARGET_WEIGHT`  | Weight for a given `TARGET_VALUE`         |

The scoring cost view `DM$VC`model_name describes the scoring cost matrix for Classification models. The view has the following schema:

    Name                                       Type
     ----------------------------------------- --------------------------------
     PARTITION_NAME                            VARCHAR2(128)
     ACTUAL_TARGET_VALUE                       NUMBER/VARCHAR2
     PREDICTED_TARGET_VALUE                    NUMBER/VARCHAR2
     COST                                      NUMBER

Table 5-18 Scoring Cost View

| Column Name              | Description                                                    |
|:-------------------------|:---------------------------------------------------------------|
| `PARTITION_NAME`         | Partition name in a partitioned model                          |
| `ACTUAL_TARGET_VALUE`    | A valid target value                                           |
| `PREDICTED_TARGET_VALUE` | Predicted target value                                         |
| `COST`                   | Associated cost for the actual and predicted target value pair |

### 5.4.6 Model Detail Views for CUR Matrix Decomposition

Model Detail Views for CUR Matrix Decomposition describe scores and ranks of attributes and rows.

CUR Matrix Decomposition algorithm has the following views:

Attribute importance and rank: `DM$VC`model_name

Row importance and rank: `DM$VR`model_name

Global statistics: `DM$VG`

The Attribute Importance and Rank view `DM$VC`model_name has the following schema:

    Name                            Type
    -----------------              -----------------
    PARTITION_NAME                 VARCHAR2(128)
    ATTRIBUTE_NAME                 VARCHAR2(128)
    ATTRIBUTE_SUBNAME              VARCHAR2(4000)
    ATTRIBUTE_VALUE                VARCHAR2(4000)
    ATTRIBUTE_IMPORTANCE           NUMBER
    ATTRIBUTE_RANK                 NUMBER

Table 5-19 Attribute Importance and Rank View

| Column Name            | Description                                                  |
|:-----------------------|:-------------------------------------------------------------|
| `PARTITION_NAME`       | Partition name in a partitioned model                        |
| `ATTRIBUTE_NAME`       | Attribute name                                               |
| `ATTRIBUTE_SUBNAME`    | Attribute subname. The value is null for non-nested columns. |
| `ATTRIBUTE_VALUE`      | Value of the attribute                                       |
| `ATTRIBUTE_IMPORTANCE` | Attribute leverage score                                     |
| `ATTRIBUTE_RANK`       | Attribute rank based on leverage score                       |

The view `DM$VR`model_name exposes the leverage scores and ranks of all selected rows through a view. This view is created when users decide to perform row importance and the `CASE_ID` column is present. The view has the following schema:

    Name                      Type
    ---------------------    ------------------------
    PARTITION_NAME            VARCHAR2(128)
    CASE_ID               Original cid data types,
                              including NUMBER, VARCHAR2,
                              DATE, TIMESTAMP,
                              TIMESTAMP WITH TIME ZONE,
                              TIMESTAMP WITH LOCAL TIME ZONE
    ROW_IMPORTANCE        NUMBER
    ROW_RANK                  NUMBER

Table 5-20 Row Importance and Rank View

| Column Name      | Description                                                                                           |
|:-----------------|:------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME` | Partition name in a partitioned model                                                                 |
| `CASE_ID`        | Case ID. The supported case ID types are the same as that supported for GLM, SVD, and ESA algorithms. |
| `ROW_IMPORTANCE` | Row leverage score                                                                                    |
| `ROW_RANK`       | Row rank based on leverage score                                                                      |

The following table describes global statistics for CUR Matrix Decomposition.

Table 5-21 CUR Matrix Decomposition Statistics Information In Model Global View.

| Name             | Description                            |
|:-----------------|:---------------------------------------|
| `NUM_COMPONENTS` | Number of SVD components (SVD rank)    |
| `NUM_ROWS`       | Number of rows used in the model build |

### 5.4.7 Model Detail Views for Decision Tree

Model detail view for Decision Tree describes the split information view, node statistics view, node description view, and the cost matrix view. Oracle recommends that users leverage the model details views instead of `GET_MODEL_DETAILS_XML` function.

The split information view `DM$VP`model_name describes the decision tree hierarchy and the split information for each level in the Decision Tree. The view has the following schema:

    Name                                Type
     ---------------------------------- ---------------------------
     PARTITION_NAME                     VARCHAR2(128)
     PARENT                             NUMBER
     SPLIT_TYPE                         VARCHAR2
     NODE                               NUMBER
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     OPERATOR                           VARCHAR2
     VALUE                              SYS.XMLTYPE

Table 5-22 Split Information View

| Column Name         | Description                                                                                                                                                          |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                                                                                                                                |
| `PARENT`            | Node ID of the parent                                                                                                                                                |
| `SPLIT_TYPE`        | The main or surrogate split                                                                                                                                          |
| `NODE`              | The node ID                                                                                                                                                          |
| `ATTRIBUTE_NAME`    | The attribute used as the splitting criterion at the parent node to produce this node.                                                                               |
| `ATTRIBUTE_SUBNAME` | Split attribute subname. The value is null for non-nested columns.                                                                                                   |
| `OPERATOR`          | Split operator                                                                                                                                                       |
| `VALUE`             | Value used as the splitting criterion. This is an XML element described using the `<Element>` tag.<br>For example, `<Element>Windy</Element><Element>Hot</Element>`. |

The node statistics view `DM$VI`model_name describes the statistics associated with individual tree nodes. The statistics include a target histogram for the data in the node. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     NODE                               NUMBER
     NODE_SUPPORT                       NUMBER
     PREDICTED_TARGET_VALUE             NUMBER/VARCHAR2
     TARGET_VALUE                       NUMBER/VARCHAR2
     TARGET_SUPPORT                     NUMBER

Table 5-23 Node Statistics View

| Parameter                | Description                                                                                             |
|:-------------------------|:--------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`         | Partition name in a partitioned model                                                                   |
| `NODE`                   | The node ID                                                                                             |
| `NODE_SUPPORT`           | Number of records in the training set that belong to the node                                           |
| `PREDICTED_TARGET_VALUE` | Predicted Target value                                                                                  |
| `TARGET_VALUE`           | A target value seen in the training data                                                                |
| `TARGET_SUPPORT`         | The number of records that belong to the node and have the value specified in the `TARGET_VALUE` column |

Higher level node description can be found in `DM$VO`model_name view. The `DM$VO`model_name has the following schema:

    ame                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     NODE                               NUMBER
     NODE_SUPPORT                       NUMBER
     PREDICTED_TARGET_VALUE             NUMBER/VARCHAR2
     PARENT                             NUMBER
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     OPERATOR                           VARCHAR2
     VALUE                              SYS.XMLTYPE

Table 5-24 Node Description View

| Parameter                | Description                                                                                                                                                            |
|:-------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`         | Partition name in a partitioned model                                                                                                                                  |
| `NODE`                   | The node ID                                                                                                                                                            |
| `NODE_SUPPORT`           | Number of records in the training set that belong to the node                                                                                                          |
| `PREDICTED_TARGET_VALUE` | Predicted Target value                                                                                                                                                 |
| `PARENT`                 | The ID of the parent                                                                                                                                                   |
| `ATTRIBUTE_NAME`         | Specifies the attribute name                                                                                                                                           |
| `ATTRIBUTE_SUBNAME`      | Specifies the attribute subname                                                                                                                                        |
| `OPERATOR`               | Attribute predicate operator - a conditional operator taking the following values:<br>IN, = , \<\>, \< , \>, \<=, and \>=                                              |
| `VALUE`                  | Value used as the description criterion. This is an XML element described using the `<Element>` tag.<br>For example, `<Element>Windy</Element><Element>Hot</Element>`. |

The `DM$VM`model_name view describes the cost matrix used by the Decision Tree build. The `DM$VM`model_name view has the following schema:

    Name                                       Type
     ----------------------------------------- --------------------------------
     PARTITION_NAME                            VARCHAR2(128)
     ACTUAL_TARGET_VALUE                       NUMBER/VARCHAR2
     PREDICTED_TARGET_VALUE                    NUMBER/VARCHAR2
     COST                                      NUMBER

Table 5-25 Cost Matrix View

| Parameter                | Description                                                    |
|:-------------------------|:---------------------------------------------------------------|
| `PARTITION_NAME`         | Partition name in a partitioned model                          |
| `ACTUAL_TARGET_VALUE`    | Valid target value                                             |
| `PREDICTED_TARGET_VALUE` | Predicted Target value                                         |
| `COST`                   | Associated cost for the actual and predicted target value pair |

The following table describes the global view for Decision Tree.

Table 5-26 Decision Tree Statistics Information In Model Global View

| Name       | Description                                |
|:-----------|:-------------------------------------------|
| `NUM_ROWS` | The total number of rows used in the build |

### 5.4.8 Model Detail Views for Generalized Linear Model

Model details views for Generalized Linear Model (GLM) describes the model details view and row diagnostic view for Linear and Logistic Regression. Oracle recommends that users leverage model details views than the `GET_MODEL_DETAILS_GLM` function.

The model details view `DM$VD`model_name describes the final model information for both Linear Regression models and Logistic Regression models.

For Linear Regression, the view `DM$VD`model_name has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     ATTRIBUTE_VALUE                    VARCHAR2(4000)
     FEATURE_EXPRESSION                 VARCHAR2(4000)
     COEFFICIENT                        BINARY_DOUBLE
     STD_ERROR                          BINARY_DOUBLE
     TEST_STATISTIC                     BINARY_DOUBLE
     P_VALUE                            BINARY_DOUBLE
     VIF                                BINARY_DOUBLE
     STD_COEFFICIENT                    BINARY_DOUBLE
     LOWER_COEFF_LIMIT                  BINARY_DOUBLE
     UPPER_COEFF_LIMIT                  BINARY_DOUBLE

For Logistic Regression, the view `DM$VD`model_name has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     TARGET_VALUE                       NUMBER/VARCHAR2
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     ATTRIBUTE_VALUE                    VARCHAR2(4000)
     FEATURE_EXPRESSION                 VARCHAR2(4000)
     COEFFICIENT                        BINARY_DOUBLE
     STD_ERROR                          BINARY_DOUBLE
     TEST_STATISTIC                     BINARY_DOUBLE
     P_VALUE                            BINARY_DOUBLE
     STD_COEFFICIENT                    BINARY_DOUBLE
     LOWER_COEFF_LIMIT                  BINARY_DOUBLE
     UPPER_COEFF_LIMIT                  BINARY_DOUBLE
     EXP_COEFFICIENT                    BINARY_DOUBLE
     EXP_LOWER_COEFF_LIMIT              BINARY_DOUBLE
     EXP_UPPER_COEFF_LIMIT              BINARY_DOUBLE

Table 5-27 Model View for Linear and Logistic Regression Models

| Column Name             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`        | The name of a feature in the model                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TARGET_VALUE`          | Valid target value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `ATTRIBUTE_NAME`        | The attribute name when there is no subname, or first part of the attribute name when there is a subname. `ATTRIBUTE_NAME` is the name of a column in the source table or view. If the column is a non-nested, numeric column, then `ATTRIBUTE_NAME` is the name of the mining attribute. For the intercept, `ATTRIBUTE_NAME` is null. Intercepts are equivalent to the bias term in SVM models.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `ATTRIBUTE_SUBNAME`     | Nested column subname. The value is null for non-nested columns.<br>When the nested column is numeric, the mining attribute is identified by the combination `ATTRIBUTE_NAME - ATTRIBUTE_SUBNAME`. If the column is not nested, `ATTRIBUTE_SUBNAME` is null. If the attribute is an intercept, both the `ATTRIBUTE_NAME` and the `ATTRIBUTE_SUBNAME` are null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `ATTRIBUTE_VALUE`       | A unique value that can be assumed by a categorical column or nested categorical column. For categorical columns, a mining attribute is identified by a unique `ATTRIBUTE_NAME.ATTRIBUTE_VALUE` pair. For nested categorical columns, a mining attribute is identified by the combination: `ATTRIBUTE_NAME.ATTRIBUTE_SUBNAME.ATTRIBUTE_VALUE`. For numerical attributes, `ATTRIBUTE_VALUE` is null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `FEATURE_EXPRESSION`    | The feature name constructed by the algorithm when feature selection is enabled. If feature selection is not enabled, the feature name is simply the fully-qualified attribute name (attribute_name.attribute_subname if the attribute is in a nested column). For categorical attributes, the algorithm constructs a feature name that has the following form:<br>fully-qualified_attribute_name.attribute_value<br>When feature generation is enabled, a term in the model can be a single mining attribute or the product of up to 3 mining attributes. Component mining attributes can be repeated within a single term. If feature generation is not enabled or, if feature generation is enabled, but no multiple component terms are discovered by the `CREATE` model process, then `FEATURE_EXPRESSION` is null.<br>**Note:**<br>In 12c Release 2, the algorithm does not subtract the mean from numerical components. |
| `COEFFICIENT`           | The estimated coefficient.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `STD_ERROR`             | Standard error of the coefficient estimate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `TEST_STATISTIC`        | For Linear Regression, the t-value of the coefficient estimate.<br>For Logistic Regression, the Wald chi-square value of the coefficient estimate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `P_VALUE`               | Probability of the `TEST_STATISTIC` under the (NULL) hypothesis that the term in the model is not statistically significant. A low probability indicates that the term is significant, while a high probability indicates that the term can be better discarded. Used to analyze the significance of specific attributes in the model.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `VIF`                   | Variance Inflation Factor. The value is zero for the intercept. For Logistic Regression, `VIF` is null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `STD_COEFFICIENT`       | Standardized estimate of the coefficient.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `LOWER_COEFF_LIMIT`     | Lower confidence bound of the coefficient.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `UPPER_COEFF_LIMIT`     | Upper confidence bound of the coefficient.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `EXP_COEFFICIENT`       | Exponentiated coefficient for Logistic Regression. For linear<br>regression, `EXP_COEFFICIENT` is null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `EXP_LOWER_COEFF_LIMIT` | Exponentiated coefficient for lower confidence bound of the coefficient for Logistic Regression. For Linear Regression, `EXP_LOWER_COEFF_LIMIT` is null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `EXP_UPPER_COEFF_LIMIT` | Exponentiated coefficient for upper confidence bound of the coefficient for Logistic Regression. For Linear Regression, `EXP_UPPER_COEFF_LIMIT` is null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

The row diagnostic view `DM$VA`model_name describes row level information for both Linear Regression models and Logistic Regression models. For Linear Regression, the view `DM$VA`model_name has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     CASE_ID                            NUMBER/VARHCAR2, DATE, TIMESTAMP,
                                        TIMESTAMP WITH TIME ZONE,
                                        TIMESTAMP WITH LOCAL TIME ZONE
     TARGET_VALUE                       BINARY_DOUBLE
     PREDICTED_TARGET_VALUE             BINARY_DOUBLE
     Hat                                BINARY_DOUBLE
     RESIDUAL                           BINARY_DOUBLE
     STD_ERR_RESIDUAL                   BINARY_DOUBLE
     STUDENTIZED_RESIDUAL               BINARY_DOUBLE
     PRED_RES                           BINARY_DOUBLE
     COOKS_D                            BINARY_DOUBLE

Table 5-28 Row Diagnostic View for Linear Regression

| Column Name              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:-------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`         | Partition name in a partitioned model                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `CASE_ID`                | Name of the case identifier                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `TARGET_VALUE`           | The actual target value as taken from the input row                                                                                                                                                                                                                                                                                                                                                                                                                |
| `PREDICTED_TARGET_VALUE` | The model predicted target value for the row                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `HAT`                    | The diagonal element of the n\*n (n=number of rows) that the Hat matrix identifies with a specific input row. The model predictions for the input data are the product of the Hat matrix and vector of input target values. The diagonal elements (Hat values) represent the influence of the i<sup>th</sup> row on the i<sup>th</sup> fitted value. Large Hat values are indicators that the i<sup>th</sup> row is a point of high leverage, a potential outlier. |
| `RESIDUAL`               | The difference between the predicted and actual target value for a specific input row.                                                                                                                                                                                                                                                                                                                                                                             |
| `STD_ERR_RESIDUAL`       | The standard error residual, sometimes called the Studentized residual, re-scales the residual to have constant variance across all input rows in an effort to make the input row residuals comparable. The process multiplies the residual by square root of the row weight divided by the product of the model mean square error and 1 minus the Hat value.                                                                                                      |
| `STUDENTIZED_RESIDUAL`   | Studentized deletion residual adjusts the standard error residual for the influence of the current row.                                                                                                                                                                                                                                                                                                                                                            |
| `PRED_RES`               | The predictive residual is the weighted square of the deletion residuals, computed as the row weight multiplied by the square of the residual divided by 1 minus the Hat value.                                                                                                                                                                                                                                                                                    |
| `COOKS_D`                | Cook's distance is a measure of the combined impact of the i<sup>th</sup> case on all of the estimated regression coefficients.                                                                                                                                                                                                                                                                                                                                    |

For Logistic Regression, the view `DM$VA`model_name has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     CASE_ID                            NUMBER/VARHCAR2, DATE, TIMESTAMP,
                                        TIMESTAMP WITH TIME ZONE,
                                        TIMESTAMP WITH LOCAL TIME ZONE
     TARGET_VALUE                       NUMBER/VARCHAR2
     TARGET_VALUE_PROB                  BINARY_DOUBLE
     Hat                                BINARY_DOUBLE
     WORKING_RESIDUAL                   BINARY_DOUBLE
     PEARSON_RESIDUAL                   BINARY_DOUBLE
     DEVIANCE_RESIDUAL                  BINARY_DOUBLE
     C                                  BINARY_DOUBLE
     CBAR                               BINARY_DOUBLE
     DIFDEV                             BINARY_DOUBLE
     DIFCHISQ                           BINARY_DOUBLE

Table 5-29 Row Diagnostic View for Logistic Regression

| Column Name         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `CASE_ID`           | Name of the case identifier                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `TARGET_VALUE`      | The actual target value as taken from the input row                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `TARGET_VALUE_PROB` | Model estimate of the probability of the predicted target value.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `Hat`               | The Hat value concept from Linear Regression is extended to Logistic Regression by multiplying the Linear Regression Hat value by the variance function for Logistic Regression, the predicted probability multiplied by 1 minus the predicted probability.                                                                                                                                                                                                                                         |
| `WORKING_RESIDUAL`  | The working residual is the residual of the working response. The working response is the response on the linearized scale. For Logistic Regression it has the form: the i<sup>th</sup> row residual divided by the variance of the i<sup>th</sup> row prediction. The variance of the prediction is the predicted probability multiplied by 1 minus the predicted probability.<br>`WORKING_RESIDUAL` is the difference between the working response and the linear predictor at convergence.       |
| `PEARSON_RESIDUAL`  | The Pearson residual is a re-scaled version of the working residual, accounting for the weight. For Logistic Regression, the Pearson residual multiplies the residual by a factor that is computed as square root of the weight divided by the variance of the predicted probability for the i<sup>th</sup> row.<br>`RESIDUAL` is 1 minus the predicted probability of the actual target value for the row.                                                                                         |
| `DEVIANCE_RESIDUAL` | The `DEVIANCE_RESIDUAL` is the contribution to the model deviance of the i<sup>th</sup> observation. For Logistic Regression it has the form the square root of 2 times the `log(1 + e^eta) - eta` for the non-reference class and -square root of 2 time the `log (1 + eta)` for the reference class, where `eta` is the linear prediction (the prediction as if the model were a Linear Regression).                                                                                              |
| `C`                 | Measures the overall change in the fitted logits due to the deletion of the i<sup>th</sup> observation for all points including the one deleted (the i<sup>th</sup> point). It is computed as the square of the Pearson residual multiplied by the Hat value divided by the square of 1 minus the Hat value.<br>Confidence interval displacement diagnostics that provides scalar measure of the influence of individual observations.                                                              |
| `CBAR`              | `C` and `CBAR` are extensions of Cooks’ distance for Logistic Regression. `CBAR` measures the overall change in the fitted logits due to the deletion of the i<sup>th</sup> observation for all points excluding the one deleted (the i<sup>th</sup> point). It is computed as the square of the Pearson residual multiplied by the Hat value divided by (1 minus the Hat value)<br>Confidence interval displacement diagnostic which measures the influence of deleting an individual observation. |
| `DIFDEV`            | A statistic that measures the change in deviance that occurs when an observation is deleted from the input. It is computed as the square of the deviance residual plus `CBAR`.                                                                                                                                                                                                                                                                                                                      |
| `DIFCHISQ`          | A statistic that measures the change in the Pearson chi-square statistic that occurs when an observation is deleted from the input. It is computed as `CBAR` divided by the Hat value.                                                                                                                                                                                                                                                                                                              |

#### Global Details for GLM: Linear Regression

The following table describes global details returned by a Linear Regression model.

Table 5-30 Global Details for Linear Regression

| Name                 | Description                                                                                                                                 |
|:---------------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `ADJUSTED_R_SQUARE`  | Adjusted R-Square                                                                                                                           |
| `AIC`                | Akaike's information criterion                                                                                                              |
| `COEFF_VAR`          | Coefficient of variation                                                                                                                    |
| `CONVERGED`          | Indicates whether the model build process has converged to specified tolerance. The following are the possible values:<br>• `YES`<br>• `NO` |
| `CORRECTED_TOTAL_DF` | Corrected total degrees of freedom                                                                                                          |
| `CORRECTED_TOT_SS`   | Corrected total sum of squares                                                                                                              |
| `DEPENDENT_MEAN`     | Dependent mean                                                                                                                              |
| `ERROR_DF`           | Error degrees of freedom                                                                                                                    |
| `ERROR_MEAN_SQUARE`  | Error mean square                                                                                                                           |
| `ERROR_SUM_SQUARES`  | Error sum of squares                                                                                                                        |
| `F_VALUE`            | Model F value statistic                                                                                                                     |
| `GMSEP`              | Estimated mean square error of the prediction, assuming multivariate normality                                                              |
| `HOCKING_SP`         | Hocking Sp statistic                                                                                                                        |
| `ITERATIONS`         | Tracks the number of SGD iterations. Applicable only when the solver is SGD.                                                                |
| `J_P`                | JP statistic (the final prediction error)                                                                                                   |
| `MODEL_DF`           | Model degrees of freedom                                                                                                                    |
| `MODEL_F_P_VALUE`    | Model F value probability                                                                                                                   |
| `MODEL_MEAN_SQUARE`  | Model mean square error                                                                                                                     |
| `MODEL_SUM_SQUARES`  | Model sum of square errors                                                                                                                  |
| `NUM_PARAMS`         | Number of parameters (the number of coefficients, including the intercept)                                                                  |
| `NUM_ROWS`           | Number of rows                                                                                                                              |
| `R_SQ`               | R-Square                                                                                                                                    |
| `RANK_DEFICIENCY`    | The number of predictors excluded from the model due to multi-collinearity                                                                  |
| `ROOT_MEAN_SQ`       | Root mean square error                                                                                                                      |
| `SBIC`               | Schwarz's Bayesian information criterion                                                                                                    |

#### Global Details for GLM: Logistic Regression

The following table returns global details returned by a Logistic Regression model.

Table 5-31 Global Details for Logistic Regression

| Name                | Description                                                                                                                                 |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `AIC_INTERCEPT`     | Akaike's criterion for the fit of the baseline, intercept-only, model                                                                       |
| `AIC_MODEL`         | Akaike's criterion for the fit of the intercept and the covariates (predictors) mode                                                        |
| `CONVERGED`         | Indicates whether the model build process has converged to specified tolerance. The following are the possible values:<br>• `YES`<br>• `NO` |
| `DEPENDENT_MEAN`    | Dependent mean                                                                                                                              |
| `ITERATIONS`        | Tracks the number of SGD iterations (number of IRLS iterations). Applicable only when the solver is SGD.                                    |
| `LR_DF`             | Likelihood ratio degrees of freedom                                                                                                         |
| `LR_CHI_SQ`         | Likelihood ratio chi-square value                                                                                                           |
| `LR_CHI_SQ_P_VALUE` | Likelihood ratio chi-square probability value                                                                                               |
| `NEG2_LL_INTERCEPT` | -2 log likelihood of the baseline, intercept-only, model                                                                                    |
| `NEG2_LL_MODEL`     | -2 log likelihood of the model                                                                                                              |
| `NUM_PARAMS`        | Number of parameters (the number of coefficients, including the intercept)                                                                  |
| `NUM_ROWS`          | Number of rows                                                                                                                              |
| `PCT_CORRECT`       | Percent of correct predictions                                                                                                              |
| `PCT_INCORRECT`     | Percent of incorrectly predicted rows                                                                                                       |
| `PCT_TIED`          | Percent of cases where the estimated probabilities are equal for both target classes                                                        |
| `PSEUDO_R_SQ_CS`    | Pseudo R-square Cox and Snell                                                                                                               |
| `PSEUDO_R_SQ_N`     | Pseudo R-square Nagelkerke                                                                                                                  |
| `RANK_DEFICIENCY`   | The number of predictors excluded from the model due to multi-collinearity                                                                  |
| `SC_INTERCEPT`      | Schwarz's Criterion for the fit of the baseline, intercept-only, model                                                                      |
| `SC_MODEL`          | Schwarz's Criterion for the fit of the intercept and the covariates (predictors) model                                                      |

**Note:**

- When Ridge Regression is enabled, fewer global details are returned. For information about ridge, see [Oracle Data Mining Concepts](../dmapi/generalized-linear-models.md).

- When the value is `NULL` for a partitioned model, an exception is thrown. When the value is not null, it must contain the desired partition name.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)
- Model Detail Views for Global Information

### 5.4.9 Model Detail Views for Naive Bayes

Model Detail Views for Naive Bayes describes prior view and result view. Oracle recommends that users leverage the model details views instead of the `GET_MODEL_DETAILS_NB` function.

The prior view `DM$VP`model_name describes the priors of the targets for Naïve Bayes. The view has the following schema:

    Name                                       Type
     ----------------------------------------- ----------------------------
     PARTITION_NAME                            VARCHAR2(128)
     TARGET_NAME                               VARCHAR2(128)
     TARGET_VALUE                              NUMBER/VARCHAR2
     PRIOR_PROBABILITY                         BINARY_DOUBLE
     COUNT                                     NUMBER

Table 5-32 Prior View for Naive Bayes

| Column Name         | Description                                  |
|:--------------------|:---------------------------------------------|
| `PARTITION_NAME`    | The name of a feature in the model           |
| `TARGET_NAME`       | Name of the target column                    |
| `TARGET_VALUE`      | Target value, numerical or categorical       |
| `PRIOR_PROBABILITY` | Prior probability for a given `TARGET_VALUE` |
| `COUNT`             | Number of rows for a given `TARGET_VALUE`    |

The Naïve Bayes result view `DM$VV`model_view describes the conditional probabilities of the Naïve Bayes model. The view has the following schema:

    Name                                       Type
     ----------------------------------------- ----------------------------
     PARTITION_NAME                            VARCHAR2(128)
     TARGET_NAME                               VARCHAR2(128)
     TARGET_VALUE                              NUMBER/VARCHAR2
     ATTRIBUTE_NAME                            VARCHAR2(128)
     ATTRIBUTE_SUBNAME                         VARCHAR2(4000)
     ATTRIBUTE_VALUE                           VARCHAR2(4000)
     CONDITIONAL_PROBABILITY                   BINARY_DOUBLE
     COUNT                                     NUMBER

Table 5-33 Result View for Naive Bayes

| Column Name               | Description                                                                                               |
|:--------------------------|:----------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`          | The name of a feature in the model                                                                        |
| `TARGET_NAME`             | Name of the target column                                                                                 |
| `TARGET_VALUE`            | Target value, numerical or categorical                                                                    |
| `ATTRIBUTE_NAME`          | Column name                                                                                               |
| `ATTRIBUTE_SUBNAME`       | Nested column subname. The value is null for non-nested columns.                                          |
| `ATTRIBUTE_VALUE`         | Mining attribute value for the column `ATTRIBUTE_NAME` or the nested column `ATTRIBUTE_SUBNAME` (if any). |
| `CONDITIONAL_PROBABILITY` | Conditional probability of a mining attribute for a given target                                          |
| `COUNT`                   | Number of rows for a given mining attribute and a given target                                            |

The following table describes the global view for Naive Bayes.

Table 5-34 Naive Bayes Statistics Information In Model Global View

| Name       | Description                                |
|:-----------|:-------------------------------------------|
| `NUM_ROWS` | The total number of rows used in the build |

### 5.4.10 Model Detail Views for Neural Network

Model Detail Views for Neural Network describes the weights of the neurons: input layer and hidden layers. Oracle recommends that users leverage the model details views.

Neural Network algorithm has the following views:

Weights: `DM$VA`model_name

The view `DM$VA`model_name has the following schema:

    Name                           Type
    ---------------------- -----------------------
    PARTITION_NAME                VARCHAR2(128)
    LAYER                         NUMBER
    IDX_FROM                      NUMBER
    ATTRIBUTE_NAME                VARCHAR2(128)
    ATTRIBUTE_SUBNAME             VARCHAR2(4000)
    ATTRIBUTE_VALUE               VARCHAR2(4000)
    IDX_TO                        NUMBER
    TARGET_VALUE                  NUMBER/VARCHAR2
    WEIGHT                        BINARY_DOUBLE

Table 5-35 Weights View

| Column Name         | Description                                                             |
|:--------------------|:------------------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                                   |
| `LAYER`             | Layer ID, 0 as an input layer                                           |
| `IDX_FROM`          | Node index that the weight connects from (attribute id for input layer) |
| `ATTRIBUTE_NAME`    | Attribute name (only for the input layer)                               |
| `ATTRIBUTE_SUBNAME` | Attribute subname. The value is null for non-nested columns.            |
| `ATTRIBUTE_VALUE`   | Categorical attribute value                                             |
| `IDX_TO`            | Node index that the weights connects to                                 |
| `TARGET_VALUE`      | Target value. The value is null for regression.                         |
| `WEIGHT`            | Value of the weight                                                     |

The view `DM$VG`model_name is a pre-existing view. The following name-value pairs are added to the view.

Table 5-36 Neural Networks Statistics Information In Model Global View

| Name         | Description                                                                                                                                 |
|:-------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `CONVERGED`  | Indicates whether the model build process has converged to specified tolerance. The following are the possible values:<br>• `YES`<br>• `NO` |
| `ITERATIONS` | Number of iterations                                                                                                                        |
| `LOSS_VALUE` | Loss function value (if it is with `NNET_REGULARIZER_HELDASIDE` regularization, it is the loss function value on test data)                 |
| `NUM_ROWS`   | Number of rows in the model (or partitioned model)                                                                                          |

### 5.4.11 Model Detail Views for Random Forest

Model Detail Views for Random Forest describes variable importance measures and statistics in global view. Oracle recommends that users leverage the model details views.

Random Forest algorithm has the following statistics views:

- Variable importance statistics `DM$VA`model_name

- Random Forest statistics in model global view `DM$VG`model_name

One of the important outputs from the Random Forest model build is a ranking of attributes based on their relative importance. This is measured using Mean Decrease Gini. The view `DM$VA`model_name has the following schema:

    Name                                Type
    ------------------------          ---------------
    PARTITION_NAME                     VARCHAR2(128)
    ATTRIBUTE_NAME                     VARCHAR2(128)
    ATTRIBUTE_SUBNAME                  VARCHAR2(128)
    ATTRIBUTE_IMPORTANCE               BINARY_DOUBLE

Table 5-37 Variable Importance Model View

| Column Name            | Description                                                                     |
|:-----------------------|:--------------------------------------------------------------------------------|
| `PARTITION_NAME`       | Partition name. The value is null for models which are not partitioned.         |
| `ATTRIBUTE_NAME`       | Column name                                                                     |
| `ATTRIBUTE_SUBNAME`    | Nested column subname. The value is null for non-nested columns.                |
| `ATTRIBUTE_IMPORTANCE` | Measure of importance for an attribute in the forest (mean Decrease Gini value) |

The view `DM$VG`model_name is a pre-existing view. The following name-value pairs are added to the view.

Table 5-38 Random Forest Statistics Information In Model Global View

| Name            | Description                                |
|:----------------|:-------------------------------------------|
| `AVG_DEPTH`     | Average depth of the trees in the forest   |
| `AVG_NODECOUNT` | Average number of nodes per tree           |
| `MAX_DEPTH`     | Maximum depth of the trees in the forest   |
| `MAX_NODECOUNT` | Maximum number of nodes per tree           |
| `MIN_DEPTH`     | Minimum depth of the trees in the forest   |
| `MIN_NODECOUNT` | Minimum number of nodes per tree           |
| `NUM_ROWS`      | The total number of rows used in the build |

### 5.4.12 Model Detail View for Support Vector Machine

Model Detail View for Support Vector Machine describes linear coefficient view. Oracle recommends that users leverage the model details views instead of the `GET_MODEL_DETAILS_SVM` function.

The linear coefficient view `DM$VL`model_name describes the coefficients of a linear SVM algorithm. The target_value field in the view is present only for Classification and has the type of the target. Regression models do not have a target_value field.

The reversed_coefficient field shows the value of the coefficient after reversing the automatic data preparation transformations. If data preparation is disabled, then coefficient and reversed_coefficient have the same value. The view has the following schema:

    Name                                       Type
     ----------------------------------------- --------------------------------
     PARTITION_NAME                            VARCHAR2(128)
     TARGET_VALUE                              NUMBER/VARCHAR2
     ATTRIBUTE_NAME                            VARCHAR2(128)
     ATTRIBUTE_SUBNAME                         VARCHAR2(4000)
     ATTRIBUTE_VALUE                           VARCHAR2(4000)
     COEFFICIENT                               BINARY_DOUBLE
     REVERSED_COEFFICIENT                      BINARY_DOUBLE

Table 5-39 Linear Coefficient View for Support Vector Machine

| Column Name            | Description                                                      |
|:-----------------------|:-----------------------------------------------------------------|
| `PARTITION_NAME`       | Partition name in a partitioned model                            |
| `TARGET_VALUE`         | Target value, numerical or categorical                           |
| `ATTRIBUTE_NAME`       | Column name                                                      |
| `ATTRIBUTE_SUBNAME`    | Nested column subname. The value is null for non-nested columns. |
| `ATTRIBUTE_VALUE`      | Value of a categorical attribute                                 |
| `COEFFICIENT`          | Projection coefficient value                                     |
| `REVERSED_COEFFICIENT` | Coefficient transformed on the original scale                    |

The following table describes the Support Vector statistics global view.

Table 5-40 Support Vector Statistics Information In Model Global View

| Name                     | Description                                                                                          |
|:-------------------------|:-----------------------------------------------------------------------------------------------------|
| `CONVERGED `             | Indicates whether the model build process has converged to specified tolerance:<br>• `YES`<br>• `NO` |
| `ITERATIONS`             | Number of iterations performed during build                                                          |
| `NUM_ROWS`               | Number of rows used for the build                                                                    |
| `REMOVED_ROWS_ZERO_NORM` | Number of rows removed due to 0 norm. This applies to one-class linear models only.                  |

### 5.4.13 Model Detail Views for Clustering Algorithms

Oracle Data Mining supports these clustering algorithms: Expectation Maximization, k-Means, and Orthogonal Partitioning Clustering (O-Cluster).

All clustering algorithms share the following views:

- Cluster description `DM$VD`model_name

- Attribute statistics `DM$VA`model_name

- Histogram statistics `DM$VH`model_name

- Rule statistics `DM$VR`model_name

The cluster description view `DM$VD`model_name describes cluster level information about a clustering model. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     CLUSTER_ID                         NUMBER
     CLUSTER_NAME                       NUMBER/VARCHAR2
     RECORD_COUNT                       NUMBER
     PARENT                             NUMBER
     TREE_LEVEL                         NUMBER
     LEFT_CHILD_ID                      NUMBER
     RIGHT_CHILD_ID                     NUMBER

Table 5-41 Cluster Description View for Clustering Algorithm

| Column Name      | Description                                                |
|:-----------------|:-----------------------------------------------------------|
| `PARTITION_NAME` | Partition name in a partitioned model                      |
| `CLUSTER_ID`     | The ID of a cluster in the model                           |
| `CLUSTER_NAME`   | Specifies the label of the cluster                         |
| `RECORD_COUNT`   | Specifies the number of records                            |
| `PARENT`         | The ID of the parent                                       |
| `TREE_LEVEL`     | Specifies the number of splits from the root               |
| `LEFT_CHILD_ID`  | The ID of the child cluster on the left side of the split  |
| `RIGHT_CHILD_ID` | The ID of the child cluster on the right side of the split |

The attribute view `DM$VA`model_name describes attribute level information about a Clustering model. The values of the mean, variance, and mode for a particular cluster can be obtained from this view. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     CLUSTER_ID                         NUMBER
     CLUSTER_NAME                       NUMBER/VARCHAR2
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     MEAN                               BINARY_DOUBLE
     VARIANCE                           BINARY_DOUBLE
     MODE_VALUE                         VARCHAR2(4000)

Table 5-42 Attribute View for Clustering Algorithm

| Column Name         | Description                                                    |
|:--------------------|:---------------------------------------------------------------|
| `PARTITION_NAME`    | A partition in a partitioned model                             |
| `CLUSTER_ID`        | The ID of a cluster in the model                               |
| `CLUSTER_NAME`      | Specifies the label of the cluster                             |
| `ATTRIBUTE_NAME`    | Specifies the attribute name                                   |
| `ATTRIBUTE_SUBNAME` | Specifies the attribute subname                                |
| `MEAN`              | The field returns the average value of a numeric attribute     |
| `VARIANCE`          | The variance of a numeric attribute                            |
| `MODE_VALUE`        | The mode is the most frequent value of a categorical attribute |

The histogram view `DM$VH`model_name describes histogram level information about a Clustering model. The bin information as well as bin counts can be obtained from this view. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     CLUSTER_ID                         NUMBER
     CLUSTER_NAME                       NUMBER/VARCHAR2
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     BIN_ID                             NUMBER
     LOWER_BIN_BOUNDARY                 BINARY_DOUBLE
     UPPER_BIN_BOUNDARY                 BINARY_DOUBLE
     ATTRIBUTE_VALUE                    VARCHAR2(4000)
     COUNT                              NUMBER

Table 5-43 Histogram View for Clustering Algorithm

| Column Name          | Description                        |
|:---------------------|:-----------------------------------|
| `PARTITION_NAME`     | A partition in a partitioned model |
| `CLUSTER_ID`         | The ID of a cluster in the model   |
| `CLUSTER_NAME`       | Specifies the label of the cluster |
| `ATTRIBUTE_NAME`     | Specifies the attribute name       |
| `ATTRIBUTE_SUBNAME`  | Specifies the attribute subname    |
| `BIN_ID`             | Bin ID                             |
| `LOWER_BIN_BOUNDARY` | Numeric lower bin boundary         |
| `UPPER_BIN_BOUNDARY` | Numeric upper bin boundary         |
| `ATTRIBUTE_VALUE`    | Categorical attribute value        |
| `COUNT`              | Histogram count                    |

The rule view `DM$VR`model_name describes the rule level information about a Clustering model. The information is provided at attribute predicate level. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     CLUSTER_ID                         NUMBER
     CLUSTER_NAME                       NUMBER/VARCHAR2
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     OPERATOR                           VARCHAR2(2)
     NUMERIC_VALUE                      NUMBER
     ATTRIBUTE_VALUE                    VARCHAR2(4000)
     SUPPORT                            NUMBER
     CONFIDENCE                         BINARY_DOUBLE
     RULE_SUPPORT                       NUMBER
     RULE_CONFIDENCE                    BINARY_DOUBLE

Table 5-44 Rule View for Clustering Algorithm

| Column Name         | Description                                                                                                            |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`    | A partition in a partitioned model                                                                                     |
| `CLUSTER_ID`        | The ID of a cluster in the model                                                                                       |
| `CLUSTER_NAME`      | Specifies the label of the cluster                                                                                     |
| `ATTRIBUTE_NAME`    | Specifies the attribute name                                                                                           |
| `ATTRIBUTE_SUBNAME` | Specifies the attribute subname                                                                                        |
| `OPERATOR`          | Attribute predicate operator - a conditional operator taking the following values: IN, = , \<\>, \< , \>, \<=, and \>= |
| `NUMERIC_VALUE`     | Numeric lower bin boundary                                                                                             |
| `ATTRIBUTE_VALUE`   | Categorical attribute value                                                                                            |
| `SUPPORT`           | Attribute predicate support                                                                                            |
| `CONFIDENCE`        | Attribute predicate confidence                                                                                         |
| `RULE_SUPPORT`      | Rule level support                                                                                                     |
| `RULE_CONFIDENCE`   | Rule level confidence                                                                                                  |

### 5.4.14 Model Detail Views for Expectation Maximization

Model detail views for Expectation Maximization (EM) describes the differences in the views for EM against those of Clustering views. Oracle recommends that user leverage the model details views instead of the `GET_MODEL_DETAILS_EM` function.

The following views are the differences in the views for Expectation Maximization against Clustering views. For an overview of the different Clustering views, refer to "Model Detail Views for Clustering Algorithms".

The component view `DM$VO`model_name describes the EM components. The component view contains information about their prior probabilities and what cluster they map to. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     COMPONENT_ID                       NUMBER
     CLUSTER_ID                         NUMBER
     PRIOR_PROBABILITY                  BINARY_DOUBLE

Table 5-45 Component View

| Column Name         | Description                           |
|:--------------------|:--------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model |
| `COMPONENT_ID`      | Unique identifier of a component      |
| `CLUSTER_ID`        | The ID of a cluster in the model      |
| `PRIOR_PROBABILITY` | Component prior probability           |

The mean and variance component view `DM$VM`model_name provides information about the mean and variance parameters for the attributes by Gaussian distribution models. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     COMPONENT_ID                       NUMBER
     ATTRIBUTE_NAME                     VARCHAR2(4000)
     MEAN                               BINARY_DOUBLE
     VARIANCE                           BINARY_DOUBLE

The frequency component view `DM$VF`model_name provides information about the parameters of the multi-valued Bernoulli distributions used by the EM model. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     COMPONENT_ID                       NUMBER
     ATTRIBUTE_NAME                     VARCHAR2(4000)
     ATTRIBUTE_VALUE                    VARCHAR2(4000)
     FREQUENCY                          BINARY_DOUBLE

Table 5-46 Frequency Component View

| Column Name       | Description                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`  | Partition name in a partitioned model                                                                                                            |
| `COMPONENT_ID`    | Unique identifier of a component                                                                                                                 |
| `ATTRIBUTE_NAME`  | Column name                                                                                                                                      |
| `ATTRIBUTE_VALUE` | Categorical attribute value                                                                                                                      |
| `FREQUENCY`       | The frequency of the multivalued Bernoulli distribution for the attribute/value combination specified by `ATTRIBUTE_NAME` and `ATTRIBUTE_VALUE`. |

For 2-Dimensional columns, EM provides an attribute ranking similar to that of Attribute Importance. This ranking is based on a rank-weighted average over Kullback–Leibler divergence computed for pairs of columns. This unsupervised Attribute Importance is shown in the `DM$VI`model_name view and has the following schema:

    Name                                       Type
     ----------------------------------------- ----------------------------
     PARTITION_NAME                            VARCHAR2(128)
     ATTRIBUTE_NAME                            VARCHAR2(128)
     ATTRIBUTE_IMPORTANCE_VALUE                BINARY_DOUBLE
     ATTRIBUTE_RANK                            NUMBER

Table 5-47 2–Dimensional Attribute Ranking for Expectation Maximization

| Column Name                  | Description                                     |
|:-----------------------------|:------------------------------------------------|
| `PARTITION_NAME`             | Partition name in a partitioned model           |
| `ATTRIBUTE_NAME`             | Column name                                     |
| `ATTRIBUTE_IMPORTANCE_VALUE` | Importance value                                |
| `ATTRIBUTE_RANK`             | An attribute rank based on the importance value |

The `pairwise` Kullback–Leibler divergence is reported in the `DM$VB`model_name view. This metric evaluates how much the observed joint distribution of two attributes diverges from the expected distribution under the assumption of independence. That is, the higher the value, the more dependent the two attributes are. The dependency value is scaled based on the size of the grid used for each pairwise computation. That ensures that all values fall within the \[0; 1\] range and are comparable. The view has the following schema:

    Name                                       Type
     ----------------------------------------- ----------------------------
     PARTITION_NAME                            VARCHAR2(128)
     ATTRIBUTE_NAME_1                          VARCHAR2(128)
     ATTRIBUTE_NAME_2                          VARCHAR2(128)
     DEPENDENCY                                BINARY_DOUBLE

Table 5-48 Kullback-Leibler Divergence for Expectation Maximization

| Column Name        | Description                                 |
|:-------------------|:--------------------------------------------|
| `PARTITION_NAME`   | Partition name in a partitioned model       |
| `ATTRIBUTE_NAME_1` | Name of an attribute 1                      |
| `ATTRIBUTE_NAME_2` | Name of an attribute 2                      |
| `DEPENDENCY`       | Scaled pairwise Kullback-Leibler divergence |

The projection table `DM$VP`model_name shows the coefficients used by random projections to map nested columns to a lower dimensional space. The view has rows only when nested or text data is present in the build data. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     FEATURE_NAME                       VARCHAR2(4000)
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     ATTRIBUTE_VALUE                    VARCHAR2(4000)
     COEFFICIENT                        NUMBER

Table 5-49 Projection table for Expectation Maximization

| Column Name         | Description                                                                                        |
|:--------------------|:---------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                                                              |
| `FEATURE_NAME`      | Name of feature                                                                                    |
| `ATTRIBUTE_NAME`    | Column name                                                                                        |
| `ATTRIBUTE_SUBNAME` | Nested column subname. The value is null for non-nested columns.                                   |
| `ATTRIBUTE_VALUE`   | Categorical attribute value                                                                        |
| `COEFFICIENT`       | Projection coefficient. The representation is sparse; only the non-zero coefficients are returned. |

#### Global Details for Expectation Maximization

The following table describes global details for Expectation Maximization.

Table 5-50 Global Details for Expectation Maximization

| Name                 | Description                                                                                                                   |
|:---------------------|:------------------------------------------------------------------------------------------------------------------------------|
| `CONVERGED`          | Indicates whether the model build process has converged to specified tolerance. The possible values are:<br>• `YES`<br>• `NO` |
| `LOGLIKELIHOOD`      | Loglikelihood on the build data                                                                                               |
| `NUM_COMPONENTS`     | Number of components produced by the model                                                                                    |
| `NUM_CLUSTERS`       | Number of clusters produced by the model                                                                                      |
| `NUM_ROWS`           | Number of rows used in the build                                                                                              |
| `RANDOM_SEED`        | The random seed value used for the model build                                                                                |
| `REMOVED_COMPONENTS` | The number of empty components excluded from the model                                                                        |

**Related Topics**

- Model Detail Views for Clustering Algorithms

### 5.4.15 Model Detail Views for k-Means

Model detail views for k-Means (KM) describes cluster description view and scoring view. Oracle recommends that you leverage model details view instead of `GET_MODEL_DETAILS_KM` function.

This section describes the differences in the views for k-Means against the Clustering views. For an overview of the different views, refer to "Model Detail Views for Clustering Algorithms". For k-Means, the cluster description view `DM$VD`model_name has an additional column:

    Name                                Type
     ---------------------------------- ----------------------------
     DISPERSION                         BINARY_DOUBLE

Table 5-51 Cluster Description for k-Means

| Column Name  | Description                                                                                                              |
|:-------------|:-------------------------------------------------------------------------------------------------------------------------|
| `DISPERSION` | A measure used to quantify whether a set of observed occurrences are dispersed compared to a standard statistical model. |

The scoring view `DM$VC`model_name describes the centroid of each leaf clusters:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     CLUSTER_ID                         NUMBER
     CLUSTER_NAME                       NUMBER/VARCHAR2
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     ATTRIBUTE_VALUE                    VARCHAR2(4000)
     VALUE                              BINARY_DOUBLE

Table 5-52 Scoring View for k-Means

| Column Name         | Description                                                      |
|:--------------------|:-----------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                            |
| `CLUSTER_ID`        | The ID of a cluster in the model                                 |
| `CLUSTER_NAME`      | Specifies the label of the cluster                               |
| `ATTRIBUTE_NAME`    | Column name                                                      |
| `ATTRIBUTE_SUBNAME` | Nested column subname. The value is null for non-nested columns. |
| `ATTRIBUTE_VALUE`   | Categorical attribute value                                      |
| `VALUE`             | Specifies the centroid value                                     |

The following table describes global view for k–Means.

Table 5-53 k–Means Statistics Information In Model Global View

| Name                     | Description                                                                                                                                 |
|:-------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `CONVERGED`              | Indicates whether the model build process has converged to specified tolerance. The following are the possible values:<br>• `YES`<br>• `NO` |
| `NUM_ROWS`               | Number of rows used in the build                                                                                                            |
| `REMOVED_ROWS_ZERO_NORM` | Number of rows removed due to 0 norm. This applies only to models using cosine distance.                                                    |

**Related Topics**

- Model Detail Views for Clustering Algorithms

### 5.4.16 Model Detail Views for O-Cluster

Model Detail Views for O-Cluster describes the statistics views. Oracle recommends that user leverage the model details views instead of the `GET_MODEL_DETAILS_OC` function.

The following are the differences in the views for O-Cluster against Clustering views. For an overview of the different clustering views, refer to "Model Detail Views for Clustering Algorithms". The OC algorithm uses the same descriptive statistics views as Expectation Maximization (EM) and k-Means (KM). The following are the statistics views:

- Cluster description `DM$VD`model_name

- Attribute statistics `DM$VA`model_name

- Rule statistics `DM$VR`model_name

- Histogram statistics `DM$VH`model_name

The Cluster description view `DM$VD`model_name describes the O-Cluster components. The cluster description view has additional fields that specify the split predicate. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     OPERATOR                           VARCHAR2(2)
     VALUE                              SYS.XMLTYPE

Table 5-54 Description View

| Column Name         | Description                                                      |
|:--------------------|:-----------------------------------------------------------------|
| `ATTRIBUTE_NAME`    | Column name                                                      |
| `ATTRIBUTE_SUBNAME` | Nested column subname. The value is null for non-nested columns. |
| `OPERATOR`          | Split operator                                                   |
| `VALUE`             | List of split values                                             |

The structure of the `SYS.XMLTYPE` is as follows:

    <Element>splitval1</Element>

The OC algorithm uses a histogram view `DM$VH`model_name with a different schema than EM and k-Means (KM). The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITON_NAME                      VARCHAR2(128)
     CLUSTER_ID                         NUMBER
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     BIN_ID                             NUMBER
     LABEL                              VARCHAR2(4000)
     COUNT                              NUMBER

Table 5-55 Histogram Component View

| Column Name         | Description                                                      |
|:--------------------|:-----------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                            |
| `CLUSTER_ID`        | Unique identifier of a component                                 |
| `ATTRIBUTE_NAME`    | Column name                                                      |
| `ATTRIBUTE_SUBNAME` | Nested column subname. The value is null for non-nested columns. |
| `BIN_ID`            | Unique identifier                                                |
| `LABEL`             | Bin label                                                        |
| `COUNT`             | Bin histogram count                                              |

The following table describes the global view for O-Cluster.

Table 5-56 O-Cluster Statistics Information In Model Global View

| Name       | Description                                |
|:-----------|:-------------------------------------------|
| `NUM_ROWS` | The total number of rows used in the build |

**Related Topics**

- Model Detail Views for Clustering Algorithms

### 5.4.17 Model Detail Views for Explicit Semantic Analysis

Model Detail Views for Explicit Semantic Analysis (ESA) describes attribute statistics view and feature view. Oracle recommends that users leverage the model details view.

ESA algorithm has the following views:

- Explicit Semantic Analysis Matrix `DM$VA`model_name: This view has different schemas for Feature Extraction and Classification. For Feature Extraction, this view contains model attribute coefficients per feature. For Classification, this view contains model attribute coefficients per target class.

- Explicit Semantic Analysis Features `DM$VF`model_name: This view is applicable for only Feature Extraction.

The view `DM$VA`model_name has the following schema for Feature Extraction:

     PARTITION_NAME                     VARCHAR2(128)
     FEATURE_ID                         NUMBER/VARHCAR2, DATE, TIMESTAMP,
                                        TIMESTAMP WITH TIME ZONE,
                                        TIMESTAMP WITH LOCAL TIME ZONE
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     ATTRIBUTE_VALUE                    VARCHAR2(4000)
     COEFFICIENT                        BINARY_DOUBLE

Table 5-57 Explicit Semantic Analysis Matrix for Feature Extraction

| Column Name         | Description                                                          |
|:--------------------|:---------------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                                |
| `FEATURE_ID`        | Unique identifier of a feature as it appears in the training data    |
| `ATTRIBUTE_NAME`    | Column name                                                          |
| `ATTRIBUTE_SUBNAME` | Nested column subname. The value is null for non-nested columns.     |
| `ATTRIBUTE_VALUE`   | Categorical attribute value                                          |
| `COEFFICIENT`       | A measure of the weight of the attribute with respect to the feature |

The `DM$VA`model_name view comprises attribute coefficients for all target classes.

The view `DM$VA`model_name has the following schema for Classification:

    Name                                Type
    ---------------------------------- ----------------------------
    PARTITION_NAME                     VARCHAR2(128)
    TARGET_VALUE                       NUMBER/VARCHAR2
    ATTRIBUTE_NAME                     VARCHAR2(128)
    ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
    ATTRIBUTE_VALUE                    VARCHAR2(4000)
    COEFFICIENT                        BINARY_DOUBLE

Table 5-58 Explicit Semantic Analysis Matrix for Classification

| Column Name         | Description                                                          |
|:--------------------|:---------------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                                |
| `TARGET_VALUE`      | Value of the target                                                  |
| `ATTRIBUTE_NAME`    | Column name                                                          |
| `ATTRIBUTE_SUBNAME` | Nested column subname. The value is null for non-nested columns.     |
| `ATTRIBUTE_VALUE`   | Categorical attribute value                                          |
| `COEFFICIENT`       | A measure of the weight of the attribute with respect to the feature |

The view `DM$VF`model_name has a unique row for every feature in one view. This feature is helpful if the model was pre-built and the source training data are not available. The view has the following schema:

     Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     FEATURE_ID                         NUMBER/VARHCAR2, DATE, TIMESTAMP,
                                        TIMESTAMP WITH TIME ZONE,
                                        TIMESTAMP WITH LOCAL TIME ZONE

Table 5-59 Explicit Semantic Analysis Features for Explicit Semantic Analysis

| Column Name      | Description                                                       |
|:-----------------|:------------------------------------------------------------------|
| `PARTITION_NAME` | Partition name in a partitioned model                             |
| `FEATURE_ID`     | Unique identifier of a feature as it appears in the training data |

The following table describes the global view for Explicit Semantic Analysis.

Table 5-60 Explicit Semantic Analysis Statistics Information In Model Global View

| Name                      | Description                       |
|:--------------------------|:----------------------------------|
| `NUM_ROWS`                | The total number of input rows    |
| `REMOVED_ROWS_BY_FILTERS` | Number of rows removed by filters |

### 5.4.18 Model Detail Views for Non-Negative Matrix Factorization

Model detail views for Non-Negative Matrix Factorization (NMF) describes encoding H matrix view and H inverse matrix view. Oracle recommends that users leverage the model details views instead of the `GET_MODEL_DETAILS_NMF` function.

The NMF algorithm has two matrix content views:

- Encoding (H) matrix `DM$VE`model_name

- H inverse matrix `DM$VI`model_name

The view `DM$VE`model_name describes the encoding (H) matrix of an NMF model. The `FEATURE_NAME` column type may be either `NUMBER` or `VARCHAR2`. The view has the following schema definition.

     Name            Type
     ------------------- --------------------------
     PARTITION_NAME       VARCHAR2(128)
     FEATURE_ID           NUMBER
     FEATURE_NAME         NUMBER/VARCHAR2
     ATTRIBUTE_NAME       VARCHAR2(128)
     ATTRIBUTE_SUBNAME    VARCHAR2(4000)
     ATTRIBUTE_VALUE      VARCHAR2(4000)
     COEFFICIENT          BINARY_DOUBLE

Table 5-61 Encoding H Matrix View for Non-Negative Matrix Factorization

| Column Name         | Description                                                            |
|:--------------------|:-----------------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                                  |
| `FEATURE_ID`        | The ID of a feature in the model                                       |
| `FEATURE_NAME`      | The name of a feature in the model                                     |
| `ATTRIBUTE_NAME`    | Column name                                                            |
| `ATTRIBUTE_SUBNAME` | Nested column subname. The value is null for non-nested columns.       |
| `ATTRIBUTE_VALUE`   | Specifies the value of attribute                                       |
| `COEFFICIENT`       | The attribute encoding that represents its contribution to the feature |

The view `DM$VI`model_view describes the inverse H matrix of an NMF model. The `FEATURE_NAME` column type may be either `NUMBER` or `VARCHAR2`. The view has the following schema:

     Name              Type
     ----------------- ------------------------
     PARTITION_NAME     VARCHAR2(128)
     FEATURE_ID         NUMBER
     FEATURE_NAME       NUMBER/VARCHAR2
     ATTRIBUTE_NAME     VARCHAR2(128)
     ATTRIBUTE_SUBNAME  VARCHAR2(4000)
     ATTRIBUTE_VALUE    VARCHAR2(4000)
     COEFFICIENT        BINARY_DOUBLE

Table 5-62 Inverse H Matrix View for Non-Negative Matrix Factorization

| Column Name         | Description                                                            |
|:--------------------|:-----------------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                                  |
| `FEATURE_ID`        | The ID of a feature in the model                                       |
| `FEATURE_NAME`      | The name of a feature in the model                                     |
| `ATTRIBUTE_NAME`    | Column name                                                            |
| `ATTRIBUTE_SUBNAME` | Nested column subname. The value is null for non-nested columns.       |
| `ATTRIBUTE_VALUE`   | Specifies the value of attribute                                       |
| `COEFFICIENT`       | The attribute encoding that represents its contribution to the feature |

The following table describes the global statistics for Non-Negative Matrix Factorization.

Table 5-63 Non-Negative Matrix Factorization Statistics Information In Model Global View

| Name          | Description                                                                                                                                 |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `CONV_ERROR`  | Convergence error                                                                                                                           |
| `CONVERGED`   | Indicates whether the model build process has converged to specified tolerance. The following are the possible values:<br>• `YES`<br>• `NO` |
| `ITERATIONS`  | Number of iterations performed during build                                                                                                 |
| `NUM_ROWS`    | Number of rows used in the build input dataset                                                                                              |
| `SAMPLE_SIZE` | Number of rows used by the build                                                                                                            |

### 5.4.19 Model Detail Views for Singular Value Decomposition

Model detail views for Singular Value Decomposition (SVD) describes S Matrix view, right-singular vectors view, and left-singular vector view. Oracle recommends that users leverage the model details views instead of the `GET_MODEL_DETAILS_SVD` function.

The `DM$VE`model_name view leverages the fact that each singular value in the SVD model has a corresponding principal component in the associated Principal Components Analysis (PCA) model to relate a common set of information for both classes of models. For a SVD model, it describes the content of the S matrix. When PCA scoring is selected as a build setting, the variance and percentage cumulative variance for the corresponding principal components are shown as well. The view has the following schema:

     Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     FEATURE_ID                         NUMBER
     FEATURE_NAME                       NUMBER/VARCHAR2
     VALUE                              BINARY_DOUBLE
     VARIANCE                           BINARY_DOUBLE
     PCT_CUM_VARIANCE                   BINARY_DOUBLE

Table 5-64 S Matrix View

| Column Name        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARTITION_NAME`   | Partition name in a partitioned model                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `FEATURE_ID`       | The ID of a feature in the model                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `FEATURE_NAME`     | The name of a feature in the model                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `VALUE`            | The matrix entry value                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `VARIANCE`         | The variance explained by a component. This column is only present for SVD models with setting `dbms_data_mining.svds_scoring_mode` set to `dbms_data_mining.svds_scoring_pca`<br>This column is non-null only if the build data is centered, either manually or because of the following setting:`dbms_data_mining.prep_auto` is set to `dbms_data_mining.prep_auto_on`.                                                                                                            |
| `PCT_CUM_VARIANCE` | The percent cumulative variance explained by the components thus far. The components are ranked by the explained variance in descending order.<br>This column is only present for SVD models with setting `dbms_data_mining.svds_scoring_mode` set to `dbms_data_mining.svds_scoring_pca`<br>This column is non-null only if the build data is centered, either manually or because of the following setting:`dbms_data_mining.prep_auto` is set to `dbms_data_mining.prep_auto_on`. |

The SVD `DM$VV`model_view describes the right-singular vectors of SVD model. For a PCA model it describes the principal components (eigenvectors). The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     FEATURE_ID                         NUMBER
     FEATURE_NAME                       NUMBER/VARCHAR2
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     ATTRIBUTE_VALUE                    VARCHAR2(4000)
     VALUE                              BINARY_DOUBLE

Table 5-65 Right-singular Vectors of Singular Value Decomposition

| Column Name         | Description                                                                       |
|:--------------------|:----------------------------------------------------------------------------------|
| `PARTITION_NAME`    | Partition name in a partitioned model                                             |
| `FEATURE_ID`        | The ID of a feature in the model                                                  |
| `FEATURE_NAME`      | The name of a feature in the model                                                |
| `ATTRIBUTE_NAME`    | Column name                                                                       |
| `ATTRIBUTE_SUBNAME` | Nested column subname. The value is null for non-nested columns.                  |
| `ATTRIBUTE_VALUE`   | Categorical attribute value. For numerical attributes, `ATTRIBUTE_VALUE` is null. |
| `VALUE`             | The matrix entry value                                                            |

The view `DM$VU`model_name describes the left-singular vectors of a SVD model. For a PCA model, it describes the projection of the data in the principal components. This view does not exist unless the settings `dbms_data_mining.svds_u_matrix_output` is set to `dbms_data_mining.svds_u_matrix_enable`. The view has the following schema:

    Name                                Type
     ---------------------------------- ----------------------------
     PARTITION_NAME                     VARCHAR2(128)
     CASE_ID                            NUMBER/VARHCAR2, DATE, TIMESTAMP,
                                        TIMESTAMP WITH TIME ZONE,
                                        TIMESTAMP WITH LOCAL TIME ZONE
     FEATURE_ID                         NUMBER
     FEATURE_NAME                       NUMBER/VARCHAR2
     VALUE                              BINARY_DOUBLE

Table 5-66 Left-singular Vectors of Singular Value Decomposition or Projection Data in Principal Components

| Column Name      | Description                                                                           |
|:-----------------|:--------------------------------------------------------------------------------------|
| `PARTITION_NAME` | Partition name in a partitioned model                                                 |
| `CASE_ID`        | Unique identifier of the row in the build data described by the U matrix projection.  |
| `FEATURE_ID`     | The ID of a feature in the model                                                      |
| `FEATURE_NAME`   | The name of a feature in the model                                                    |
| `VALUE`          | The matrix entry value                                                                |

#### Global Details for Singular Value Decomposition

The following table describes a global detail for Singular Value Decomposition.

Table 5-67 Global Details for Singular Value Decomposition

| Name               | Description                                                                                                                                                                                                             |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NUM_COMPONENTS`   | Number of features (components) produced by the model                                                                                                                                                                   |
| `NUM_ROWS`         | The total number of rows used in the build                                                                                                                                                                              |
| `SUGGESTED_CUTOFF` | Suggested cutoff that indicates how many of the top computed features capture most of the variance in the model. Using only the features below this cutoff would be a reasonable strategy for dimensionality reduction. |

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)

### 5.4.20 Model Detail View for Minimum Description Length

Model detail view for Minimum Description Length (for calculating Attribute Importance) describes Attribute Importance view. Oracle recommends that users leverage the model details views instead of the `GET_MODEL_DETAILS_AI` function.

The Attribute Importance view `DM$VA`model_name describes the Attribute Importance as well as the Attribute Importance rank. The view has the following schema:

    Name                                       Type
     ----------------------------------------- ----------------------------
     PARTITION_NAME                            VARCHAR2(128)
     ATTRIBUTE_NAME                            VARCHAR2(128)
     ATTRIBUTE_SUBNAME                         VARCHAR2(4000)
     ATTRIBUTE_IMPORTANCE_VALUE                BINARY_DOUBLE
     ATTRIBUTE_RANK                            NUMBER

Table 5-68 Attribute Importance View for Minimum Description Length

| Column Name                  | Description                                                      |
|:-----------------------------|:-----------------------------------------------------------------|
| `PARTITION_NAME`             | Partition name in a partitioned model                            |
| `ATTRIBUTE_NAME`             | Column name                                                      |
| `ATTRIBUTE_SUBNAME`          | Nested column subname. The value is null for non-nested columns. |
| `ATTRIBUTE_IMPORTANCE_VALUE` | Importance value                                                 |
| `ATTRIBUTE_RANK`             | Rank based on importance                                         |

The following table describes the global view for Minimum Description Length.

Table 5-69 Minimum Description Length Statistics Information In Model Global View

| Name       | Description                                |
|:-----------|:-------------------------------------------|
| `NUM_ROWS` | The total number of rows used in the build |

### 5.4.21 Model Detail View for Binning

The binning view `DM$VB` describes the bin boundaries used in the automatic data preparation.

The view has the following schema:

    Name                                Type
     --------------------       --------------------
     PARTITION_NAME                     VARCHAR2(128)
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     BIN_ID                             NUMBER
     LOWER_BIN_BOUNDARY                 BINARY_DOUBLE
     UPPER_BIN_BOUNDARY                 BINARY_DOUBLE
     ATTRIBUTE_VALUE                    VARCHAR2(4000)

Table 5-70 Model Details View for Binning

| Column Name          | Description                           |
|:---------------------|:--------------------------------------|
| `PARTITION_NAME`     | Partition name in a partitioned model |
| `ATTRIBUTE_NAME`     | Specifies the attribute name          |
| `ATTRIBUTE_SUBNAME`  | Specifies the attribute subname       |
| `BIN_ID`             | Bin ID (or bin identifier)            |
| `LOWER_BIN_BOUNDARY` | Numeric lower bin boundary            |
| `UPPER_BIN_BOUNDARY` | Numeric upper bin boundary            |
| `ATTRIBUTE_VALUE`    | Categorical value                     |

### 5.4.22 Model Detail Views for Global Information

Model detail views for Global Information describes global statistics view, alert view, and computed settings view. Oracle recommends that users leverage the model details views instead of `GET_MODEL_DETAILS_GLOBAL` function.

The global statistics view `DM$VG`model_name describes global statistics related to the model build. Examples include the number of rows used in the build, the convergence status, and the model quality metrics. The view has the following schema:

    Name                                Type
     -------------------         --------------------
     PARTITION_NAME                     VARCHAR2(128)
     NAME                               VARCHAR2(30)
     NUMERIC_VALUE                      NUMBER
     STRING_VALUE                       VARCHAR2(4000)

Table 5-71 Global Statistics View

| Column Name      | Description                           |
|:-----------------|:--------------------------------------|
| `PARTITION_NAME` | Partition name in a partitioned model |
| `NAME`           | Name of the statistic                 |
| `NUMERIC_VALUE`  | Numeric value of the statistic        |
| `STRING_VALUE`   | Categorical value of the statistic    |

The alert view `DM$VW`model_name lists alerts issued during the model build. The view has the following schema:

    Name                                Type
     -------------------       ----------------------
     PARTITION_NAME                     VARCHAR2(128)
     ERROR_NUMBER                       BINARY_DOUBLE
     ERROR_TEXT                         VARCHAR2(4000)

Table 5-72 Alert View

| Column Name      | Description                              |
|:-----------------|:-----------------------------------------|
| `PARTITION_NAME` | Partition name in a partitioned model    |
| `ERROR_NUMBER`   | Error number (valid when event is Error) |
| `ERROR_TEXT`     | Error message                            |

The computed settings view `DM$VS`model_name lists the algorithm computed settings. The view has the following schema:

    Name                                Type
     -----------------          --------------------
     PARTITION_NAME                     VARCHAR2(128)
     SETTING_NAME                       VARCHAR2(30)
     SETTING_VALUE                      VARCHAR2(4000)

Table 5-73 Computed Settings View

| Column Name      | Description                           |
|:-----------------|:--------------------------------------|
| `PARTITION_NAME` | Partition name in a partitioned model |
| `SETTING_NAME`   | Name of the setting                   |
| `SETTING_VALUE`  | Value of the setting                  |

### 5.4.23 Model Detail View for Normalization and Missing Value Handling

The Normalization and Missing Value Handling View `DM$VN` describes the normalization parameters used in Automatic Data Preparation (ADP) and the missing value replacement when a `NULL` value is encountered. Missing value replacement applies only to the two­dimensional columns and does not apply to the nested columns.

The view has the following schema:

    Name                                Type
     ----------------------       -----------------------
     PARTITION_NAME                     VARCHAR2(128)
     ATTRIBUTE_NAME                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                  VARCHAR2(4000)
     NUMERIC_MISSING_VALUE              BINARY_DOUBLE
     CATEGORICAL_MISSING_VALUE          VARCHAR2(4000)
     NORMALIZATION_SHIFT                BINARY_DOUBLE
     NORMALIZATION_SCALE                BINARY_DOUBLE

Table 5-74 Normalization and Missing Value Handling View

| Column Name                 | Description                                                      |
|:----------------------------|:-----------------------------------------------------------------|
| `PARTITION_NAME`            | A partition in a partitioned model                               |
| `ATTRIBUTE_NAME`            | Column name                                                      |
| `ATTRIBUTE_SUBNAME`         | Nested column subname. The value is null for non-nested columns. |
| `NUMERIC_MISSING_VALUE`     | Numeric missing value replacement                                |
| `CATEGORICAL_MISSING_VALUE` | Categorical missing value replacement                            |
| `NORMALIZATION_SHIFT`       | Normalization shift value                                        |
| `NORMALIZATION_SCALE`       | Normalization scale value                                        |

### 5.4.24 Model Detail Views for Exponential Smoothing Models

Model Detail Views for Exponential Smoothing Model (ESM) describes the views for model output and global information. Oracle recommends that users leverage the model details views.

Exponential Smoothing Model algorithm has the following views:

Model output: `DM$VP`model_name

Model global information: `DM$VG`model_name

Model output: This view gives the result of ESM model. The output has a set of records such as partition, `CASE_ID`, value, prediction, lower, upper, and so on and ordered by partition and `CASE_ID` (time). Each partition has a separate smoothing model. For a given partition, for each time (`CASE_ID`) point that the input time series covers, the value is the observed or accumulated value at the time point, and the prediction is the one-step-ahead forecast at that time point. For each time point (future prediction) beyond the range of input time series, the value is `NULL`, and the prediction is the model forecast for that time point. Lower and upper are the lower bound and upper bound of the user specified confidence interval for the prediction.

Model global Information: This view gives the global information of the model along with the estimated smoothing constants, the estimated initial state, and global diagnostic measures.

Depending on the type of model, the global diagnostics include some or all of the following for Exponential Smoothing.

Table 5-75 Exponential Smoothing Model Statistics Information In Model Global View

| Name                | Description                                                                                        |
|:--------------------|:---------------------------------------------------------------------------------------------------|
| `–2 LOG-LIKELIHOOD` | Negative log-likelihood of model                                                                   |
| `ALPHA`             | Smoothing constant                                                                                 |
| `AIC`               | Akaike information criterion                                                                       |
| `AICC`              | Corrected Akaike information criterion                                                             |
| `AMSE`              | Average mean square error over user-specified time window                                          |
| `BETA`              | Trend smoothing constant                                                                           |
| `BIC`               | Bayesian information criterion                                                                     |
| `GAMMA`             | Seasonal smoothing constant                                                                        |
| `INITIAL LEVEL`     | Model estimate of value one time interval prior to start of observed series                        |
| `INITIAL SEASON i`  | Model estimate of seasonal effect for season i one time interval prior to start of observed series |
| `INITIAL TREND`     | Model estimate of trend one time interval prior to start of observed series                        |
| `MAE`               | Model mean absolute error                                                                          |
| `MSE`               | Model mean square error                                                                            |
| `PHI`               | Damping parameter                                                                                  |
| `STD`               | Model standard error                                                                               |
| `SIGMA`             | Model standard deviation of residuals                                                              |
