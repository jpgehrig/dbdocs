Learn how to use Random Forest as a classification algorithm.

- About Random Forest

- Building a Random Forest

- Scoring with Random Forest

**Related Topics**

- [Feature Selection and Extraction](feature-selection-extraction.md)

### 24.1 About Random Forest

Random Forest is a classification algorithm used by Oracle Data Mining. The algorithm builds an **ensemble** (also called **forest**) of trees.

The algorithm builds a number of decision tree models and predicts using the ensemble. An individual decision tree is built by choosing a random sample from the training data set as the input. At each node of the tree, only a random sample of predictors is chosen for computing the split point. This introduces variation in the data used by the different trees in the forest. The parameters `RFOR_SAMPLING_RATIO` and `RFOR_MTRY` are used to specify the sample size and number of predictors chosen at each node. Users can use `ODMS_RANDOM_SEED` to set the random seed value before running the algorithm.

**Related Topics**

- [Decision Tree](decision-tree.md)
- [Splitting](decision-tree.md)
- [Data Preparation for Decision Tree](decision-tree.md)

### 24.2 Building a Random Forest

The Random Forest is built upon existing infrastructure and Application Programming Interfaces (APIs) of Oracle Data Mining.

The model is built by specifying parameters in the existing APIs. The scoring is performed using the same SQL queries and APIs as the existing Classification algorithms. Oracle Data Mining implements a variant of Classical Random Forest algorithm. This implementation supports big data sets. The implementation of the algorithm differs in the following ways:

- Oracle Data Mining does not support bagging and instead provides sampling without replacement

- Users have the ability to specify the depth of the tree. Trees are not built to maximum depth.

Example 24-1 Example

In this example you will understand how to build a Random Forest. When the settings table is created and populated, insert a row in the settings table to specify the algorithm and the variant.

`INSERT INTO SETTINGS_TABLE (setting_name, setting_value) VALUES ('ALGO_NAME', 'ALGO_RANDOM_FOREST');`

Build the model as follows:

    BEGIN   DBMS_DATA_MINING.CREATE_MODEL(
    model_name          => ‘model-name',
    mining_function     => dbms_data_mining.classification,
    data_table_name     => 'test_table',
    case_id_column_name => '',
    target_column_name  => 'test_target',
    settings_table_name => 'settings_table');
    END;
    /

### 24.3 Scoring with Random Forest

Learn to score with Random Forest.

Scoring with Random Forest is the same as any other Classification algorithm. The following functions are supported: `PREDICTION`, `PREDICTION_PROBABILITY`, `PREDICTION_COST`, `PREDICTION_SET`, and `PREDICTION_DETAILS`.

**Related Topics**

- [Oracle Database SQL Language Reference](../sqlrf/Single-Row-Functions.md)
