Explains the preparation steps before creating a model.

Models are database schema objects that perform data mining. The `DBMS_DATA_MINING` PL/SQL package is the API for creating, configuring, evaluating, and querying mining models (model details).

Before you create a model, you must decide what you want the model to do. You must identify the training data and determine if transformations are required. You can specify model settings to influence the behavior of the model behavior. The preparation steps are summarized in the following table.

Table 31-1 Preparation for Creating a Mining Model

| Preparation Step                                  | Description                                                               |
|:--------------------------------------------------|:--------------------------------------------------------------------------|
| Choose the mining function                        | See "[Choosing the Mining Function](CREATE_MODEL-procedure.md)"           |
| Choose the algorithm                              | See "[Choosing the Algorithm](CREATE_MODEL-procedure.md)"                 |
| Identify the build (training) data                | See "[Preparing the Data](preparing-data.md)"                             |
| For classification models, identify the test data | See "[Data Sets for Classification and Regression](data-requirements.md)" |
| Determine your data transformation strategy       | See " [Transforming the Data](transforming-data.md)"                      |
| Create and populate a settings tables (if needed) | See "[Specifying Model Settings](specifying-model-settings.md)"           |

**Related Topics**

- [About Mining Models](mining-models.md)
- [DBMS_DATA_MINING](data-mining-PL-SQL-packages.md)
