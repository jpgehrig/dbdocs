![Only in Oracle on-premises](img/only-or-onprem.png) This topic applies only to Oracle on-premises.

Learn how to build an analytics model and score in R. The R extensible algorithms are enhanced to support and register additional algorithms for users who use SQL and graphical user interface.

- Oracle Data Mining with R Extensibility

- Scoring with R

- About Algorithm Meta Data Registration

### 24.1 Oracle Data Mining with R Extensibility

Learn how you can use Oracle Data Mining to build, score, and view Oracle Data Mining models as well as R models.

The Oracle Data Mining framework is enhanced extending the data mining algorithm set with algorithms from the open source R ecosystem. Oracle Data Mining is implemented in the Oracle Database kernel. The mining models are Database schema objects. With the extensibility enhancement, the data mining framework can build, score, and view both Oracle Data Mining models and R models.

#### Registration of R scripts

The R engine on the database server executes the R scripts to build, score, and view R models. These R scripts must be registered with the database beforehand by a privileged user with rqAdmin role. You must first install Oracle R Enterprise to register the R scripts.

#### Functions of Oracle Data Mining with R Model

The following functions are supported for an R model:

- Oracle Data Mining `DBMS_DATA_MINING` package is enhanced to support R model. For example, `CREATE_MODEL` and `DROP_MODEL`.

- `MODEL VIEW` to get the R model details about a single model and a partitioned model.

- Oracle Data Mining SQL functions are enhanced to operate with the R model functions. For example, `PREDICTION` and `CLUSTER_ID`.

R model extensibility supports the following data mining techniques:

- Association

- Attribute Importance

- Regression

- Classification

- Clustering

- Feature Extraction

### 24.2 Scoring with R

Learn how to build and score with R Mining model.

####

For more information, see [Oracle Data Mining User’s Guide](../dmprg/specifying-model-settings.md)

### 24.3 About Algorithm Meta Data Registration

Algorithm Meta Data Registration allows for a uniform and consistent approach of registering new algorithm techniques and their settings.

Users have the ability to add new R-based algorithms through the registration process. The new algorithms appear as available within Oracle R Enterprise and within the appropriate mining techniques. Based on the registration meta data, the settings page is dynamically rendered. The advantages are as follows:

- Manage R-based algorithms more easily

- Easy to specify R-based algorithm for model build

- Clean individual properties in JSON structure

- Share R-based algorithm across user

Algorithm meta data registration extends the mining model capability of Oracle Data Mining.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)
- [FETCH_JSON_SCHEMA Procedure](../arpls/DBMS_DATA_MINING.md)
- [REGISTER_ALGORITHM Procedure](../arpls/DBMS_DATA_MINING.md)
- [JSON Schema for R Extensible Algorithm](../arpls/DBMS_DATA_MINING.md)
