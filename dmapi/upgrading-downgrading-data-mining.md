Understand how to upgrade and downgrade Oracle Data Mining.

- Pre-Upgrade Steps

- Upgrading Oracle Data Mining

- Post Upgrade Steps

- Downgrading Oracle Data Mining

### 34.2.1 Pre-Upgrade Steps

Before upgrading, you must drop any data mining models that were created in Java and any mining activities that were created in Oracle Data Miner Classic (the earlier version of Oracle Data Miner).

**Caution:**

In Oracle Database 12c, Oracle Data Mining does not support a Java API, and Oracle Data Miner Classic cannot run against Oracle Database 12c .

#### 34.2.1.1 Dropping Models Created in Java

If your 10g or 11g database contains models created in Java, use the `DBMS_DATA_MINING.DROP_MODEL` routine to drop the models before upgrading the database.

#### 34.2.1.2 Dropping Mining Activities Created in Oracle Data Miner Classic

If your database contains mining activities from Oracle Data Miner Classic, delete the mining activities and drop the repository before upgrading the database. Follow these steps:

1.  Use the Data Miner Classic user interface to delete the mining activities.

2.  In SQL\*Plus or SQL Developer, drop these tables:

        DM4J$ACTIVITIES
        DM4J$RESULTS
        DM4J$TRANSFORMS

    and these views:

        DM4J$MODEL_RESULTS_V
        DM4J$RESULTS_STATE_V

There must be no tables or views with the prefix `DM4J$` in any schema in the database after you complete these steps.

### 34.2.2 Upgrading Oracle Data Mining

Learn how to upgrade Oracle Data Mining.

After you complete the "Pre-Upgrade Steps", all models and mining metadata are fully integrated with the Oracle Database upgrade process ­ whether you are upgrading from 11g or from 10g releases.

Upgraded models continue to work as they did in prior releases. Both upgraded models and new models that you create in the upgraded environment can make use of the new mining functionality introduced in the new release.

To upgrade a database, you can use Database Upgrade Assistant (DBUA) or you can perform a manual upgrade using export/import utilities.

**Related Topics**

- Pre-Upgrade Steps
- [Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md)

#### 34.2.2.1 Using Database Upgrade Assistant to Upgrade Oracle Data Mining

Oracle Database Upgrade Assistant provides a graphical user interface that guides you interactively through the upgrade process.

On Windows platforms, follow these steps to start the Upgrade Assistant:

1.  Go to the Windows Start menu and choose the Oracle home directory.

2.  Choose the Configuration and Migration Tools menu.

3.  Launch the Upgrade Assistant.

On Linux platforms, run the `DBUA` utility to upgrade Oracle Database.

##### 34.2.2.1.1 Upgrading from Release 10g

In Oracle Data Mining 10g, data mining metadata and PL/SQL packages are stored in the `DMSYS` schema. In Oracle Data Mining 11g and 12c, `DMSYS` no longer exists; data mining metadata objects are stored in `SYS`.

When Oracle Database 10g is upgraded to 12c, all data mining metadata objects and PL/SQL packages are migrated from `DMSYS` to `SYS`. The `DMSYS` schema and its associated objects are removed after a successful migration. When `DMSYS` is removed, the `SYS.DBA_REGISTRY` view no longer lists Oracle Data Mining as a component.

After upgrading to Oracle Database 12c, you can no longer switch to the Data Mining Scoring Engine (`DMSE`). The Scoring Engine does not exist in Oracle Database 11g or 12c.

##### 34.2.2.1.2 Upgrading from Release 11g

If you upgrade Oracle Database 11g to Oracle Database 12c, and the database was previously upgraded from Oracle Database 10g, then the`DMSYS` schema may still be present. If the upgrade process detects `DMSYS`, it displays a warning message and drops `DMSYS` during the upgrade.

#### 34.2.2.2 Using Export/Import to Upgrade Data Mining Models

If required, you can you can use a less automated approach to upgrading data mining models. You can export the models created in a previous version of Oracle Database and import them into an instance of Oracle Database 12c.

**Caution:**

Do not import data mining models that were created in Java. They are not supported in Oracle Database 12c.

##### 34.2.2.2.1 Export/Import Release 10g Data Mining Models

Follow the instructions for exporting and importing Data Mining models.

To export models from an instance of Oracle Database 10g to a dump file, follow the instructions in "Exporting and Importing Mining Models". Before importing the models from the dump file, run the `DMEIDMSYS` script to create the `DMSYS` schema in Oracle Database 12c.

    SQL>CONNECT / as sysdba;
    SQL>@ORACLE_HOME\RDBMS\admin\dmeidmsys.sql
    SQL>EXIT;

**Note:**

The `TEMP` tablespace must already exist in the Oracle Database 12g database. The `DMEIDMSYS` script uses the `TEMP` and `SYSAUX` tablespaces to create the `DMSYS` schema.

To import the dump file into the Oracle Database 12c database:

    %ORACLE_HOME\bin\impdp system\<password>
           dumpfile=<dumpfile_name>
           directory=<directory_name>
           logfile=<logfile_name> .....
    SQL>CONNECT / as sysdba;
    SQL>EXECUTE dmp_sys.upgrade_models();
    SQL>ALTER SYSTEM FLUSH SHARED_POOL;
    SQL>ALTER SYSTEM FLUSH BUFFER_CACHE;
    SQL>EXIT;

The `upgrade_models` script migrates all data mining metadata objects and PL/SQL packages from `DMSYS` to `SYS` and then drops `DMSYS` before upgrading the models.

##### ALTER SYSTEM Statement

You can flush the Database Smart Flash Cache by issuing an `ALTER SYSTEM FLUSH FLASH_CACHE` statement. Flushing the Database Smart Flash Cache can be useful if you need to measure the performance of rewritten queries or a suite of queries from identical starting points.

**Related Topics**

- [Exporting and Importing Mining Models](exporting-importing-mining-models.md)

##### 34.2.2.2.2 Export/Import Release 11g Data Mining Models

To export models from an instance of Oracle Database 11g to a dump file, follow the instructions in [Exporting and Importing Mining Models](exporting-importing-mining-models.md).

**Caution:**

Do not import data mining models that were created in Java. They are not supported in Oracle Database 12c.

To import the dump file into the Oracle Database 12c database:

    %ORACLE_HOME\bin\impdp system\<password>
           dumpfile=<dumpfile_name>
           directory=<directory_name>
           logfile=<logfile_name> .....
    SQL>CONNECT / as sysdba;
    SQL>EXECUTE dmp_sys.upgrade_models();
    SQL>ALTER SYSTEM flush shared_pool;
    SQL>ALTER SYSTEM flush buffer_cache;
    SQL>EXIT;

##### ALTER SYSTEM Statement

You can flush the Database Smart Flash Cache by issuing an `ALTER SYSTEM FLUSH FLASH_CACHE` statement. Flushing the Database Smart Flash Cache can be useful if you need to measure the performance of rewritten queries or a suite of queries from identical starting points.

### 34.2.3 Post Upgrade Steps

Perform steps to view the upgraded database.

After upgrading the database, check the `DBA_MINING_MODELS` view in the upgraded database. The newly upgraded mining models must be listed in this view.

After you have verified the upgrade and confirmed that there is no need to downgrade, you must set the initialization parameter `COMPATIBLE` to `12.1`.

**Note:**

The `CREATE MINING MODEL` privilege must be granted to Data Mining user accounts that are used to create mining models.

**Related Topics**

- [Creating a Data Mining User](controlling-access-mining-models-data.md)
- [Controlling Access to Mining Models and Data](controlling-access-mining-models-data.md)

### 34.2.4 Downgrading Oracle Data Mining

Before downgrading the Oracle Database 12c database back to the previous version, ensure that no Singular Value Decomposition models or Expectation Maximization models are present. These algorithms are only available in Oracle Database 12c. Use the `DBMS_DATA_MINING.DROP_MODEL` routine to drop these models before downgrading. If you do not do this, the database downgrade process terminates.

Issue the following SQL statement in `SYS` to verify the downgrade:

    SQL>SELECT o.name FROM sys.model$ m, sys.obj$ o
                      WHERE m.obj#=o.obj# AND m.version=2;
