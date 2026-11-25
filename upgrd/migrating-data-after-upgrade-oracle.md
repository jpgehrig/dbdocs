## 9 Migrating Data Using Oracle Data Pump

Use the Export and Import utilities in Oracle Data Pump to migrate data from one database to another.

Oracle Data Pump provides high performance Export (`expdp`) and Import (`impdp`) utilities. These utilities facilitate upgrading to Oracle Database.

- Overview of Data Pump and Export/Import For Migrating Data
  Oracle provides Oracle Data Pump Export and Import to migrate (move) data from one Oracle Database instance to another.
- Migrating Data With Oracle Data Pump Before Upgrades
  Use this Oracle Data Pump procedure to export data from the source database before you install the new Oracle Database software. Then import the data into the target upgraded database.
- Importing a Full Oracle Database Using a Network Link
  This database export/import method is an alternative to Oracle Data Pump migrations that is helpful when you are migrating to a different storage system.
- Oracle Data Pump Requirements When Downgrading Oracle Database
  You can obtain a downward-compatible dump file by using Oracle Data Pump.

**See Also:**

[Oracle Database Utilities](../sutil/index.md) for detailed information about Data Pump and the Export and Import utilities

### Overview of Data Pump and Export/Import For Migrating Data

Oracle provides Oracle Data Pump Export and Import to migrate (move) data from one Oracle Database instance to another.

Migrating data by using Oracle Data Pump offers the following benefits:

- Supports filtering the metadata that is exported and imported based upon objects and object types, using `INCLUDE` and `EXCLUDE` parameters.

- Supports different modes for unloading/loading portions of the database including: full database mode, schema mode, table mode, tablespace mode, and transportable tablespace mode.

- Enables you to specify how partitioned tables should be handled during import operations, using the `PARTITION_OPTIONS` parameter.

- Provides support for the full range of data types.

`UTL_FIL_DIR` is desupported in Oracle Database 18c. Features using the `UTL_FILE` package to access a symbolic link fails in the new Oracle Database release. To avoid the issue, you must change the directory object and the file name, so that neither contains a symbolic link. This desupport can affect any feature from an earlier release using symbolic links, including (but not restricted to) Oracle Data Pump, BFILEs, and External Tables. If you attempt to use an affected feature after upgrade, where that feature used symbolic links, then you encounter `ORA-29283: invalid file operation: path traverses a symlink`.

**Related Topics**

- [The Export/Import Method for Migrating Data When Upgrading Oracle Database](choose-an-upgrade-method-for-oracle-database.md)

**See Also:**

[Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for an overview of Data Pump Export and Import

**Parent topic:** Migrating Data Using Oracle Data Pump

### Migrating Data With Oracle Data Pump Before Upgrades

Use this Oracle Data Pump procedure to export data from the source database before you install the new Oracle Database software. Then import the data into the target upgraded database.

1.  Install the new Oracle Database software, and ensure that it is updated to the most recent Release Update (RU) or Release Update Revision (RUR). Installation steps for Oracle Database are covered in your operating system-specific Oracle documentation.

2.  Export data from the current database using the Export utility shipped with the current database.

    The current database must not be available for updates during and after the export. If the current database is available to users for updates after the export, then before making the current database available, you must put procedures in place to copy the changes made in the current database to the new database after the import is complete.

    To obtain a consistent point from which you can update the exported database, use one of the following options:

    - Set `FLASHBACK_TIME=SYSTIMESTAMP` in your parameter file, so that the image you obtain of the data in the tables that you export represents the committed state of the table data at the same single point-in-time for all the tables that you are exporting.

    - Use `FLASHBACK_SCN` to select a specific system change number (SCN) that the Export can use to enable the Flashback Query utility.

    Using a flashback option increases UNDO usage and retention.

3.  Create the new database. If the new database is on the same server, and it has the same name as the current database, then shut down the current database before creating the new database.

    (Option) You can change the storage parameters from the source database. You can pre-create tablespaces, users, and tables in the new database to improve space usage by changing storage parameters. When you pre-create tables using SQL\*Plus, either run the database in the original database compatibility mode or make allowances for the specific data definition conversions that occur during import.

4.  Start SQL\*Plus in the new Oracle Database environment, and start an Oracle Database instance.

    For example:

        $ SQLPLUS / AS SYSDBA
        SQL> STARTUP

5.  If you have pre-created items, then specify the `TABLE_EXISTS_ACTION=APPEND` option for Data Pump Import.

    **Note:**

    If the new database is created on the same server as the source database, and you do not want to overwrite the source database data files, then you must pre-create the tablespaces and set the following parameter values for the Data pump import:

    - `REUSE_DATAFILES=N` for Data Pump Import

      (Option) You can use the `REMAP_DATAFILE, REMAP_TABLESPACE` and `REMAP_TABLE` options to remap references to export database names in the dump file set to new, non-colliding names in the importing database.

    - `DESTROY=N` for original Import.

6.  Import the objects exported from the current database by using the new database Import utility. To save the informational messages and error messages from the import session to a file, use the following parameters:

    - The `LOGFILE` parameter for Data Pump Import

    - The `LOG` parameter for original Import

7.  After the import, check the import log file for information about the imports of specific objects that completed successfully. If there were failures, check for information about any objects that failed.

8.  Use further Import scenarios, or use SQL scripts that create the database objects to clean up incomplete imports (or possibly to start an entirely new import).

    **Note:**

    If a Data Pump Export or Import job encounters an unrecoverable error, then the job can be restarted after the condition inducing the failure is corrected. The job continues automatically from the point of failure.

9.  If changes are made to the current database after the export, then make sure that those changes are propagated to the new database before making it available to users. Refer to step 1 in this procedure.

10. Complete required post-upgrade tasks for your upgrade as described in Chapter 4, “Post-Upgrade Tasks for Oracle Database.”

**Related Topics**

- [Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md)

**Parent topic:** Migrating Data Using Oracle Data Pump

### Importing a Full Oracle Database Using a Network Link

This database export/import method is an alternative to Oracle Data Pump migrations that is helpful when you are migrating to a different storage system.

Set up a database link and use the Data Pump Import utility (`impdp`) to perform a full database import from a source database to a destination database. Using this method to migrate data means that dump files are not written, so you do not have to copy over dump files. This method is of particular benefit when you use different storage systems. However, you must work within the limits imposed by the earlier release Oracle Data Pump software during the Oracle Database export.

**Note:**

To avoid interoperability errors, ensure that you have applied appropriate patchsets to the database you want to upgrade before you start the upgrade.

1.  Ensure that the exporting user at the source database has the `DATAPUMP_EXP_FULL_DATABASE` role.

    You must specify this exporting user when you create the database link.

2.  Ensure that the importing user at the destination database has the `DATAPUMP_IMP_FULL_DATABASE` role.

3.  Create and test a database link between the source and destination databases.

4.  Use the following command syntax to start a Data Pump export, where `import_user` is the username for the importing user, and `db_link` is the name of the database link owned by the exporting user:

        impdp import_user NETWORK_LINK=db_link FULL=Y NOLOGFILE=Y;

    **Note:**

    Running this command on the importing database implicitly triggers a Data Pump export operation (`expdp`) on the exporting Oracle Database.

5.  A log file for the import operation writes to the `DATA_PUMP_DIR` directory. You can discover the location of this directory by running the following command:

        SQL> select * from dba_directories where DIRECTORY_NAME like 'DATA_PUMP_DIR';

    In carrying out this command, be aware that the XDB repository is not moved in a full database export and import operation. LONG columns and NESTED columns are also not moved. However, user-created XML schemas are moved.

**Note:**

The import operation recreates users on the new destination server. The creation date for users in the `dba_users` table shows the actual import date. The expiration date is updated to the value of the `creation_date` plus the `password_life_time` columns. The creation dates in the `dba_users` table in the destination database are different from the values for the `dba_users` table in the source database.

**Related Topics**

- Migrating Data With Oracle Data Pump Before Upgrades

**See Also:**

[`http://support.oracle.com`](http://support.oracle.com) to obtain the latest patchsets

**Parent topic:** Migrating Data Using Oracle Data Pump

### Oracle Data Pump Requirements When Downgrading Oracle Database

You can obtain a downward-compatible dump file by using Oracle Data Pump.

When you use Oracle Data Pump with the downgrade process, the Oracle Database release to which you downgrade must be no more than one release earlier than the release from which you are downgrading.

Use one of the following Oracle Data Pump Export methods to obtain a downward-compatible dump file:

- Use the Oracle Data Pump Export utility included in the current release Oracle Database home, and set the VERSION parameter to the release of the earlier target to which you are downgrading.

  Oracle Data Pump Import cannot read dump file sets created by the version of Oracle Data Pump that is later than the current Oracle Database release, unless you created these dump file sets with the VERSION parameter set to the release number of the target database. For this reason, the best way to perform a downgrade is to use Oracle Data Pump Export with the VERSION parameter set to the release number of the target database to which you are downgrading.

- Use the Oracle Data Pump Export utility with `DOWNGRADE` using the `NETWORK_LINK` parameter with the `VERSION` parameter.

  If the compatibility level of the database to which you want to downgrade is earlier than the version of the export dump file sets you created, then you can still transfer data over a database link if the compatibility level of the Oracle Database from which you want to export is within two major release numbers. For example, if one database is Oracle Database 18c, then the other database must be 12c release 1 (12.1), or 12c release 2 (12.2). You can use Data Pump Export this way to recover from having the `VERSION` set to an incompatible value during a previous dump file export.

  **Note:**

  If you raise the compatibility level after you install the new release of Oracle Database, so that it uses features from the new release, then objects that use those new features cannot be downgraded. After the downgrade, when you try to import those objects, and the Oracle Data Pump Import utility attempts to recreate objects using features only available in later releases, you receive an error.

  **See Also:**

  [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for more information about using the VERSION parameter

**Parent topic:** Migrating Data Using Oracle Data Pump
