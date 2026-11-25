The PL/SQL interface to Oracle Data Mining is implemented in three packages.

The following table displays the PL/SQL packages.

Table 28-2 Data Mining PL/SQL Packages

| Package Name                 | Description                                      |
|:-----------------------------|:-------------------------------------------------|
| `DBMS_DATA_MINING`           | Routines for creating and managing mining models |
| `DBMS_DATA_MINING_TRANSFORM` | Routines for transforming the data for mining    |
| `DBMS_PREDICTIVE_ANALYTICS`  | Routines that perform predictive analytics       |

**Related Topics**

- [DBMS_DATA_MINING](../arpls/DBMS_DATA_MINING.md)
- [DBMS_DATA_MINING_TRANSFORM](../arpls/DBMS_DATA_MINING_TRANSFORM.md)
- [DBMS_PREDICTIVE_ANALYTICS](../arpls/DBMS_PREDICTIVE_ANALYTICS.md)

### 28.3.1 DBMS_DATA_MINING

Understand the routines of `DBMS_DATA_MINING` package.

The `DBMS_DATA_MINING` package contains routines for creating mining models, for performing operations on mining models, and for querying mining models. The package includes routines for:

- Creating, dropping, and performing other DDL operations on mining models

- Obtaining detailed information about model attributes, rules, and other information internal to the model (model details)

- Computing test metrics for classification models

- Specifying costs for classification models

- Exporting and importing models

- Building models using Oracle's native algorithms as well as algorithms written in R

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)

### 28.3.2 DBMS_DATA_MINING_TRANSFORM

Understand the routines of `DBMS_DATA_MINING_TRANSFORM` package.

The `DBMS_DATA_MINING_TRANSFORM` package contains routines that perform data transformations such as binning, normalization, and outlier treatment. The package includes routines for:

- Specifying transformations in a format that can be embedded in a mining model.

- Specifying transformations as relational views (external to mining model objects).

- Specifying distinct properties for columns in the build data. For example, you can specify that the column must be interpreted as unstructured text, or that the column must be excluded from Automatic Data Preparation.

**Related Topics**

- [Transforming the Data](transforming-data.md)
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING_TRANSFORM.md)

#### 28.3.2.1 Transformation Methods in DBMS_DATA_MINING_TRANSFORM

Summarizes the methods for transforming data in DBMS_DATA_MINING_TRANSFORM package.

Table 28-3 DBMS_DATA_MINING_TRANSFORM Transformation Methods

| Transformation Method | Description                                                                               |
|:----------------------|:------------------------------------------------------------------------------------------|
| `XFORM` interface     | `CREATE`, `INSERT`, and `XFORM` routines specify transformations in external views        |
| `STACK` interface     | `CREATE`, `INSERT`, and `XFORM` routines specify transformations for embedding in a model |
| `SET_TRANSFORM`       | Specifies transformations for embedding in a model                                        |

The statements in the following example create an Support Vector Machine (SVM) Classification model called `T_SVM_Clas_sample` with an embedded transformation that causes the comments attribute to be treated as unstructured text data.

Example 28-7 Sample Embedded Transformation

    DECLARE
      xformlist dbms_data_mining_transform.TRANSFORM_LIST;
    BEGIN
      dbms_data_mining_transform.SET_TRANSFORM(
        xformlist, 'comments', null, 'comments', null, 'TEXT');
      DBMS_DATA_MINING.CREATE_MODEL(
        model_name          => 'T_SVM_Clas_sample',
        mining_function     => dbms_data_mining.classification,
        data_table_name     => 'mining_build_text',
        case_id_column_name => 'cust_id',
        target_column_name  => 'affinity_card',
        settings_table_name => 't_svmc_sample_settings',
        xform_list => xformlist);
    END;
    /

### 28.3.3 DBMS_PREDICTIVE_ANALYTICS

Understand the routines of `DBMS_PREDICTIVE_ANALYTICS` package.

The `DBMS_PREDICTIVE_ANALYTICS` package contains routines that perform an automated form of data mining known as predictive analytics. With predictive analytics, you do not need to be aware of model building or scoring. All mining activities are handled internally by the procedure. The `DBMS_PREDICTIVE_ANALYTICS` package includes these routines:

- **`EXPLAIN`** ranks attributes in order of influence in explaining a target column.

- **`PREDICT`** predicts the value of a target column based on values in the input data.

- **`PROFILE`** generates rules that describe the cases from the input data.

The `EXPLAIN` statement in the following example lists attributes in the view `mining_data_build_v` in order of their importance in predicting `affinity_card`.

Example 28-8 Sample EXPLAIN Statement

    BEGIN
        DBMS_PREDICTIVE_ANALYTICS.EXPLAIN(
            data_table_name      => 'mining_data_build_v',
            explain_column_name  => 'affinity_card',
            result_table_name    => 'explain_results');
    END;
    /

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_PREDICTIVE_ANALYTICS.md)
