You can export machine learning models to move models to a different Oracle Database instance, such as from a development database to a production database.

The `DBMS_DATA_MINING` package includes procedures for migrating machine learning models between database instances.

`EXPORT_MODEL` exports a single model or list of models to a dump file so it can be imported, queried, and scored in a separate Oracle Machine Learning database instance.

`IMPORT_MODEL` takes the dump file and creates the model in the destination database.

`EXPORT_SERMODEL` exports a single model to a serialized `BLOB` so it can be imported and scored in a separate Oracle Data Mining database instance or to OML Services.

`IMPORT_SERMODEL` takes the serialized `BLOB` and creates the model in the destination database.

- About Exporting Models

- About Oracle Data Pump

- Options for Exporting and Importing Mining Models

- Directory Objects for EXPORT_MODEL and IMPORT_MODEL

- Using EXPORT_MODEL and IMPORT_MODEL

- EXPORT and IMPORT Serialized Models

- Importing From PMML

**Related Topics**

- [`EXPORT_MODEL`](../arpls/DBMS_DATA_MINING.md)
- [`IMPORT_MODEL`](../arpls/DBMS_DATA_MINING.md)
- [`EXPORT_SERMODEL`](../arpls/DBMS_DATA_MINING.md)
- [`IMPORT_SERMODEL`](../arpls/DBMS_DATA_MINING.md)

### 8.3.1 About Exporting Models

As a result of building models, each model has a set of model detail views that provide information about the model, such as model statistics for evaluation. The user can query these model detail views. With serialized models, only the model data and metadata required for scoring are available in the serialized model. This is more compact and transfers faster to the destination environment than dump files produced by the `EXPORT_MODEL` procedure.

To retain complete model details, use the `DMBS_DATA_MINING.EXPORT_MODEL` procedure and the `DBMS_DATA_MINING.IMPORT_MODEL` procedure. Serialized model export only works with models that produce scores. Specifically, it doesn't support Attribute Importance, Association Rules, Exponential Smoothing, or O-Cluster (although O-Cluster does allow scoring). Use `EXPORT_MODEL` to export these models and scenarios when full model details are needed.

[EXPORT_MODEL Procedure](../arpls/DBMS_DATA_MINING.md)

[IMPORT_MODEL Procedure](../arpls/DBMS_DATA_MINING.md)

### 8.3.2 About Oracle Data Pump

Use the command-line clients of Oracle Data Pump to export and import schemas or databases.

Oracle Data Pump consists of two command-line clients and two PL/SQL packages. The command-line clients, `expdp` and `impdp`, provide an easy-to-use interface to the Data Pump export and import utilities. You can use `expdp` and `impdp` to export and import entire schemas or databases respectively.

The Data Pump export utility writes the schema objects, including the tables and metadata that constitute data mining models, to a dump file set. The Data Pump import utility retrieves the schema objects, including the model tables and metadata, from the dump file set and restores them in the target database.

`expdp` and `impdp` cannot be used to export/import individual data mining models.

**See Also:**

[Oracle Database Utilities](../sutil/oracle-data-pump.md) for information about Oracle Data Pump and the `expdp` and `impdp` utilities

### 8.3.3 Options for Exporting and Importing Mining Models

Lists options for exporting and importing mining models.

Options for exporting and importing mining models are described in the following table.

Table 8-1 Export and Import Options for Oracle Data Mining for SQL

| Task                                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Export or import a full database                                | (DBA only) Use `expdp` to export a full database and `impdp` to import a full database. All data mining models in the database are included.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Export or import a schema                                       | Use `expdp` to export a schema and `impdp` to import a schema. All data mining models in the schema are included.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Export or import models within a database or between databases  | Use `DBMS_DATA_MINING.EXPORT_MODEL` to export one or more models and `DBMS_DATA_MINING.IMPORT_MODEL` to import one or more models. These procedures can export and import a single data mining model, all data mining models, or data mining models that match specific criteria.<br>To import models, you must have the `CREATE TABLE`, `CREATE VIEW`, and `CREATE MINING MODEL` privileges.                                                                                                                                                                                                                                                                                           |
| Export or import individual models to or from a remote database | Use a database link to export individual models to a remote database or import individual models from a remote database. A database link is a schema object in one database that enables access to objects in a different database. The link must be created before you run `EXPORT_MODEL` or `IMPORT_MODEL`.<br>To create a private database link, you must have the `CREATE DATABASE LINK` system privilege. To create a public database link, you must have the `CREATE PUBLIC DATABASE LINK` system privilege. Also, you must have the `CREATE SESSION` system privilege on the remote Oracle Database. Oracle Net must be installed on both the local and remote Oracle Databases. |
| Serialized model export and import                              | Starting from Oracle Database 18c, the serialized model format was introduced as a lightweight approach to support scoring. The `DBMS_DATA_MINING.EXPORT_SERMODEL` procedure exports a single model to a serialized `BLOB` so it can be imported and scored in a separate Oracle Data Mining database instance. `DBMS_DATA_MINING.IMPORT_SERMODEL` takes the serialized `BLOB` and creates the model in the target database.                                                                                                                                                                                                                                                            |

**Related Topics**

- [IMPORT_MODEL Procedure](../arpls/DBMS_DATA_MINING.md)
- [EXPORT_MODEL Procedure](../arpls/DBMS_DATA_MINING.md)
- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DATABASE-LINK.md)

### 8.3.4 Directory Objects for EXPORT_MODEL and IMPORT_MODEL

Learn how to use directory objects to identify the location of the dump file set containing the models.

`EXPORT_MODEL` and `IMPORT_MODEL` use a directory object to identify the location of the dump file set. A directory object is a logical name in the database for a physical directory on the host computer.

To export data mining models, you must have write access to the directory object and to the file system directory that it represents. To import data mining models, you must have read access to the directory object and to the file system directory. Also, the database itself must have access to file system directory. You must have the `CREATE ANY DIRECTORY` privilege to create directory objects.

The following SQL command creates a directory object named `dmdir`. The file system directory that it represents must already exist and have shared read/write access rights granted by the operating system. For example, if the directory path is `/home/dmuser`, the command is:

    CREATE OR REPLACE DIRECTORY dmdir AS '/home/dmuser';

The following SQL command gives user `dmuser` both read and write access to `dmuser_dir`.

    GRANT READ,WRITE ON DIRECTORY dmdir TO dmuser;

**Related Topics**

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DIRECTORY.md)

### 8.3.5 Using EXPORT_MODEL and IMPORT_MODEL

The examples illustrate various export and import scenarios with `EXPORT_MODEL` and `IMPORT_MODEL`.

The examples use the directory object `dmdir` shown in Example 8-1 and two schemas, `dm1` and `dm2`. Both schemas have data mining privileges. `dm1` has two models. `dm2` has one model.

    SELECT owner, model_name, mining_function, algorithm FROM all_mining_models where OWNER='DM1';

The output is as follows:

    OWNER      MODEL_NAME           MINING_FUNCTION      ALGORITHM
    ---------- -------------------- -------------------- --------------------------
    DM1        EM_SH_CLUS_SAMPLE    CLUSTERING           EXPECTATION_MAXIMIZATION
    DM1        DT_SH_CLAS_SAMPLE    CLASSIFICATION       DECISION_TREE
    DM2        SVD_SH_SAMPLE        FEATURE_EXTRACTION   SINGULAR_VALUE_DECOMP

Example 8-1 Creating the Directory Object

    -- connect as system user
    CREATE OR REPLACE DIRECTORY OMLDIR AS '/home/oracle';
    GRANT READ, WRITE ON DIRECTORY OMLDIR TO DM1;
    GRANT READ, WRITE ON DIRECTORY OMLDIR TO DM2;
    SELECT * FROM all_directories WHERE directory_name = 'DMDIR';

The output is as follows:

    OWNER      DIRECTORY_NAME             DIRECTORY_PATH
    ---------- -------------------------- ----------------------------------------
    SYS        DMDIR                      /home/dmuser

Example 8-2 Exporting All Models From DM1

    -- connect as DM1
    BEGIN
      dbms_data_mining.export_model (
                       filename =>   'all_DM1',
                       directory =>  'DMDIR');
    END;
    /


A log file and a dump file are created in `/home/dmuser`, the physical directory associated with `DMDIR`. The name of the log file is `dm1_exp_11.log`. The name of the dump file is `all_dm101.dmp`.

Example 8-3 Importing the Models Back Into DM1

The models that were exported in Example 8-2 still exist in `dm1`. Since an import does not overwrite models with the same name, you must drop the models before importing them back into the same schema.

    BEGIN
      dbms_data_mining.drop_model('EM_SH_CLUS_SAMPLE');
      dbms_data_mining.drop_model('DT_SH_CLAS_SAMPLE');
      dbms_data_mining.import_model(
                       filename => 'all_dm101.dmp',
                       directory => 'DMDIR');
    END;
    /
    SELECT model_name FROM user_mining_models;


The output is as follows:

    MODEL_NAME
    ------------------------------
    DT_SH_CLAS_SAMPLE
    EM_SH_CLUS_SAMPLE

Example 8-4 Importing Models Into a Different Schema

In this example, the models that were exported from `DM1` in Example 8-2 are imported into `DM2`. The `DM1` schema uses the `USER1` tablespace; the `DM2` schema uses the `USER2` tablespace.

    -- CONNECT as sysdba
    BEGIN
      dbms_data_mining.import_model (
                       filename => 'all_d101.dmp',
                       directory => 'DMDIR',
                       schema_remap => 'DM1:DM2',
                       tablespace_remap => 'USER1:USER2');
    END;
    /
    -- CONNECT as DM2
    SELECT model_name from user_mining_models;


    MODEL_NAME
    --------------------------------------------------------------------------------
    SVD_SH_SAMPLE
    EM_SH_CLUS_SAMPLE
    DT_SH_CLAS_SAMPLE

Example 8-5 Exporting Specific Models

You can export a single model, a list of models, or a group of models that share certain characteristics.

    -- Export the model named dt_sh_clas_sample
    EXECUTE dbms_data_mining.export_model (
                 filename => 'one_model',
                 directory =>'DMDIR',
                 model_filter => 'name in (''DT_SH_CLAS_SAMPLE'')');
    -- one_model01.dmp and dm1_exp_37.log are created in /home/dmuser

    -- Export Decision Tree models
    EXECUTE dbms_data_mining.export_model(
                 filename => 'algo_models',
                 directory => 'DMDIR',
                 model_filter => 'ALGORITHM_NAME IN (''DECISION_TREE'')');
    -- algo_model01.dmp and dm1_exp_410.log are created in /home/dmuser

    -- Export clustering models
    EXECUTE dbms_data_mining.export_model(
                 filename =>'func_models',
                 directory => 'DMDIR',
                 model_filter => 'FUNCTION_NAME = ''CLUSTERING''');
    -- func_model01.dmp and dm1_exp_513.log are created in /home/dmuser

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)

### 8.3.6 EXPORT and IMPORT Serialized Models

From Oracle Database Release 18c onwards, `EXPORT_SERMODEL` and `IMPORT_SERMODEL` procedures are available to export or import serialized models to or from a database.

The serialized format allows the models to be moved to another database instance or OML Services for scoring. The model is exported to a serialized `BLOB` . The import routine takes the serialized content in the `BLOB` and the name of the model to be created with the content.

**Related Topics**

- [EXPORT_SERMODEL Procedure](../arpls/DBMS_DATA_MINING.md)
- [IMPORT_SERMODEL Procedure](../arpls/DBMS_DATA_MINING.md)

### 8.3.7 Importing From PMML

You can import Regression models represented in Predictive Model Markup Language (PMML).

PMML is an XML-based standard specified by the Data Mining Group (<https://dmg.org/>). Applications that are PMML-compliant can deploy PMML-compliant models that were created by any vendor. Oracle Data Mining supports the core features of PMML 3.1 for regression models.

You can import regression models represented in PMML. The models must be of type `RegressionModel`, either linear regression or binary logistic regression.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)
