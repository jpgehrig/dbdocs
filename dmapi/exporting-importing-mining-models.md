You can export data mining models to flat files to back up work in progress or to move models to a different instance of Oracle Database Enterprise Edition (such as from a development database to a test database).

All methods for exporting and importing models are based on Oracle Data Pump technology.

The `DBMS_DATA_MINING` package includes the `EXPORT_MODEL` and `IMPORT_MODEL` procedures for exporting and importing individual mining models. `EXPORT_MODEL` and `IMPORT_MODEL` use the export and import facilities of Oracle Data Pump.

- About Oracle Data Pump

- Options for Exporting and Importing Mining Models

- Directory Objects for EXPORT_MODEL and IMPORT_MODEL

- Using EXPORT_MODEL and IMPORT_MODEL

- EXPORT and IMPORT Serialized Models

- Importing From PMML

**Related Topics**

- [`EXPORT_MODEL`](DBMS_DATA_MINING.md)
- [`IMPORT_MODEL`](DBMS_DATA_MINING.md)

### 34.3.1 About Oracle Data Pump

Oracle Data Pump consists of two command-line clients and two PL/SQL packages. The command-line clients, `expdp` and `impdp`, provide an easy-to-use interface to the Data Pump export and import utilities. You can use `expdp` and `impdp` to export and import entire schemas or databases.

The Data Pump export utility writes the schema objects, including the tables and metadata that constitute mining models, to a dump file set. The Data Pump import utility retrieves the schema objects, including the model tables and metadata, from the dump file set and restores them in the target database.

`expdp` and `impdp` cannot be used to export/import individual mining models.

**See Also:**

[Oracle Database Utilities](../sutil/oracle-data-pump.md) for information about Oracle Data Pump and the `expdp` and `impdp` utilities

### 34.3.2 Options for Exporting and Importing Mining Models

Lists options for exporting and importing mining models.

Options for exporting and importing mining models are described in the following table.

Table 34-1 Export and Import Options for Oracle Data Mining

| Task                                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:----------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Export or import a full database                                | (DBA only) Use `expdp` to export a full database and `impdp` to import a full database. All mining models in the database are included.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Export or import a schema                                       | Use `expdp` to export a schema and `impdp` to import a schema. All mining models in the schema are included.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Export or import individual models within a database            | Use `DBMS_DATA_MINING.EXPORT_MODEL` to export individual models and `DBMS_DATA_MINING.IMPORT_MODEL` to import individual models. These procedures can export and import a single mining model, all mining models, or mining models that match specific criteria.<br>By default, `IMPORT_MODEL` imports models back into the schema from which they were exported. You can specify the `schema_remap` parameter to import models into a different schema. You can specify `tablespace_remap` with `schema_remap` to import models into a schema that uses a different tablespace.<br>You may need special privileges in the database to import models into a different schema. These privileges are granted by the `EXP_FULL_DATABASE` and `IMP_FULL_DATABASE` roles, which are only available to privileged users (such as `SYS` or a user with the `DBA` role). You do not need these roles to export or import models within your own schema.<br>To import models, you must have the same database privileges as the user who created the dump file set. Otherwise, a DBA with full system privileges must import the models. |
| Export or import individual models to or from a remote database | Use a database link to export individual models to a remote database or import individual models from a remote database. A database link is a schema object in one database that enables access to objects in a different database. The link must be created before you execute `EXPORT_MODEL` or `IMPORT_MODEL`.<br>To create a private database link, you must have the `CREATE DATABASE LINK` system privilege. To create a public database link, you must have the `CREATE PUBLIC DATABASE LINK` system privilege. Also, you must have the `CREATE SESSION` system privilege on the remote Oracle Database. Oracle Net must be installed on both the local and remote Oracle Databases.                                                                                                                                                                                                                                                                                                                                                                                                                                     |

**Related Topics**

- [IMPORT_MODEL Procedure](../arpls/DBMS_DATA_MINING.md)
- [EXPORT_MODEL Procedure](../arpls/DBMS_DATA_MINING.md)
- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DATABASE-LINK.md)

### 34.3.3 Directory Objects for EXPORT_MODEL and IMPORT_MODEL

Learn how to use directory objects to identify the location of the dump file set.

`EXPORT_MODEL` and `IMPORT_MODEL` use a directory object to identify the location of the dump file set. A directory object is a logical name in the database for a physical directory on the host computer.

To export data mining models, you must have write access to the directory object and to the file system directory that it represents. To import data mining models, you must have read access to the directory object and to the file system directory. Also, the database itself must have access to file system directory. You must have the `CREATE ANY DIRECTORY` privilege to create directory objects.

The following SQL command creates a directory object named `dmuser_dir`. The file system directory that it represents must already exist and have shared read/write access rights granted by the operating system.

    CREATE OR REPLACE DIRECTORY dmuser_dir AS '/dm_path/dm_mining';

The following SQL command gives user `dmuser` both read and write access to `dmuser_dir`.

    GRANT READ,WRITE ON DIRECTORY dmuser_dir TO dmuser;

**Related Topics**

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DIRECTORY.md)

### 34.3.4 Using EXPORT_MODEL and IMPORT_MODEL

The examples illustrate various export and import scenarios with `EXPORT_MODEL` and `IMPORT_MODEL`.

The examples use the directory object `dmdir` shown in Example 34-1 and two schemas, `dm1` and `dm2`. Both schemas have data mining privileges. `dm1` has two models. `dm2` has one model.

    SELECT owner, model_name, mining_function, algorithm FROM all_mining_models;

    OWNER      MODEL_NAME           MINING_FUNCTION      ALGORITHM
    ---------- -------------------- -------------------- --------------------------
    DM1        EM_SH_CLUS_SAMPLE    CLUSTERING           EXPECTATION_MAXIMIZATION
    DM1        DT_SH_CLAS_SAMPLE    CLASSIFICATION       DECISION_TREE
    DM2        SVD_SH_SAMPLE        FEATURE_EXTRACTION   SINGULAR_VALUE_DECOMP

Example 34-1 Creating the Directory Object

    -- connect as system user
    CREATE OR REPLACE DIRECTORY dmdir AS '/scratch/dmuser/expimp';
    GRANT READ,WRITE ON DIRECTORY dmdir TO dm1;
    GRANT READ,WRITE ON DIRECTORY dmdir TO dm2;
    SELECT * FROM all_directories WHERE directory_name IN 'DMDIR';

    OWNER      DIRECTORY_NAME             DIRECTORY_PATH
    ---------- -------------------------- ----------------------------------------
    SYS        DMDIR                      /scratch/dmuser/expimp

Example 34-2 Exporting All Models From DM1

    -- connect as dm1
    BEGIN
      dbms_data_mining.export_model (
                       filename =>   'all_dm1',
                       directory =>  'dmdir');
    END;
    /


A log file and a dump file are created in `/scratch/dmuser/expimp`, the physical directory associated with `dmdir`. The name of the log file is `dm1_exp_11.log`. The name of the dump file is `all_dm101.dmp`.

Example 34-3 Importing the Models Back Into DM1

The models that were exported in Example 34-2 still exist in `dm1`. Since an import does not overwrite models with the same name, you must drop the models before importing them back into the same schema.

    BEGIN
      dbms_data_mining.drop_model('EM_SH_CLUS_SAMPLE');
      dbms_data_mining.drop_model('DT_SH_CLAS_SAMPLE');
      dbms_data_mining.import_model(
                       filename => 'all_dm101.dmp',
                       directory => 'DMDIR');
    END;
    /
    SELECT model_name FROM user_mining_models;

    MODEL_NAME
    ------------------------------
    DT_SH_CLAS_SAMPLE
    EM_SH_CLUS_SAMPLE

Example 34-4 Importing Models Into a Different Schema

In this example, the models that were exported from `dm1` in Example 34-2 are imported into `dm2`. The `dm1` schema uses the `example` tablespace; the `dm2` schema uses the `sysaux` tablespace.

    -- CONNECT as sysdba
    BEGIN
      dbms_data_mining.import_model (
                       filename => 'all_d101.dmp',
                       directory => 'DMDIR',
                       schema_remap => 'DM1:DM2',
                       tablespace_remap => 'EXAMPLE:SYSAUX');
    END;
    /
    -- CONNECT as dm2
    SELECT model_name from user_mining_models;

    MODEL_NAME
    --------------------------------------------------------------------------------
    SVD_SH_SAMPLE
    EM_SH_CLUS_SAMPLE
    DT_SH_CLAS_SAMPLE

Example 34-5 Exporting Specific Models

You can export a single model, a list of models, or a group of models that share certain characteristics.

    -- Export the model named dt_sh_clas_sample
    EXECUTE dbms_data_mining.export_model (
                 filename => 'one_model',
                 directory =>'DMDIR',
                 model_filter => 'name in (''DT_SH_CLAS_SAMPLE'')');
    -- one_model01.dmp and dm1_exp_37.log are created in /scratch/dmuser/expimp

    -- Export Decision Tree models
    EXECUTE dbms_data_mining.export_model(
                 filename => 'algo_models',
                 directory => 'DMDIR',
                 model_filter => 'ALGORITHM_NAME IN (''DECISION_TREE'')');
    -- algo_model01.dmp and dm1_exp_410.log are created in /scratch/dmuser/expimp

    -- Export clustering models
    EXECUTE dbms_data_mining.export_model(
                 filename =>'func_models',
                 directory => 'DMDIR',
                 model_filter => 'FUNCTION_NAME = ''CLUSTERING''');
    -- func_model01.dmp and dm1_exp_513.log are created in /scratch/dmuser/expimp

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](DBMS_DATA_MINING.md)

### 34.3.5 EXPORT and IMPORT Serialized Models

From Oracle Database Release 18c onwards, `EXPORT_SERMODEL` and `IMPORT_SERMODEL` procedures are available to export and import serialized models.

The serialized format allows the models to be moved to another platform (outside the database) for scoring. The model is exported in a `BLOB` that can be saved in a `BFILE`. The import routine takes the serialized content in the `BLOB` and the name of the model to be created with the content.

**Related Topics**

- [EXPORT_SERMODEL Procedure](../arpls/DBMS_DATA_MINING.md)
- [IMPORT_SERMODEL Procedure](../arpls/DBMS_DATA_MINING.md)

### 34.3.6 Importing From PMML

You can import Regression models represented in Predictive Model Markup Language (PMML).

PMML is an XML-based standard specified by the Data Mining Group ([`http://www.dmg.org`](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/dmapi&id=dmg)). Applications that are PMML-compliant can deploy PMML-compliant models that were created by any vendor. Oracle Data Mining supports the core features of PMML 3.1 for regression models.

You can import regression models represented in PMML. The models must be of type `RegressionModel`, either linear regression or binary logistic regression.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](DBMS_DATA_MINING.md)
