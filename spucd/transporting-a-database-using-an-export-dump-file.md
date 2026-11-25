You can transport a database using an export dump file.

The following list of tasks summarizes the process of transporting a database using an export dump file. Details for each task are provided in the subsequent example.

1.  At the source database, configure each of the user-defined tablespaces in read-only mode and export the database.

    Ensure that the following parameters are set to the specified values:

    - `TRANSPORTABLE=ALWAYS`

    - `FULL=Y`

    If the source database is an Oracle Database 11g database (11.2.0.3 or later), then you must set the `VERSION` parameter to `12` or higher.

    If the source database contains any encrypted tablespaces or tablespaces containing tables with encrypted columns, then you must either specify `ENCRYPTION_PWD_PROMPT=YES`, or specify the `ENCRYPTION_PASSWORD` parameter.

    The export dump file includes the metadata for objects contained within the user-defined tablespaces and both the metadata and data for user-defined objects contained within the administrative tablespaces, such as `SYSTEM` and `SYSAUX`.

2.  Transport the export dump file.

    Copy the export dump file to a place that is accessible to the target database.

3.  Transport the data files for all of the user-defined tablespaces in the database.

    Copy the data files to a place that is accessible to the target database.

    If the source platform and target platform are different, then check the endian format of each platform by running the query on the `V$TRANSPORTABLE_PLATFORM` view in "[Transporting Data Across Platforms](transporting-data-across-platforms.md)".

    If the source platform's endian format is different from the target platform's endian format, then use one of the following methods to convert the data files:

    - Use the `GET_FILE` or `PUT_FILE` procedure in the `DBMS_FILE_TRANSFER` package to transfer the data files. These procedures convert the data files to the target platform's endian format automatically.

    - Use the RMAN `CONVERT` command to convert the data files to the target platform's endian format.

      **Note:**

      Conversion of data files between different endian formats is not supported for data files having undo segments.

    See "[Converting Data Between Platforms](converting-data-between-platforms.md)" for more information.

4.  (Optional) Restore the user-defined tablespaces to read/write mode on the source database.

5.  At the target database, import the database.

    When the import is complete, the user-defined tablespaces are in read/write mode.

### Example

The tasks for transporting a database are illustrated in detail in this example. This example assumes that the source platform is Solaris and the target platform is Microsoft Windows.

It also assumes that the source platform has the following data files and tablespaces:

| Tablespace | Type           | Data File                                 |
|:-----------|:---------------|:------------------------------------------|
| sales      | User-defined   | /u01/app/oracle/oradata/mydb/sales01.dbf  |
| customers  | User-defined   | /u01/app/oracle/oradata/mydb/cust01.dbf   |
| employees  | User-defined   | /u01/app/oracle/oradata/mydb/emp01.dbf    |
| SYSTEM     | Administrative | /u01/app/oracle/oradata/mydb/system01.dbf |
| SYSAUX     | Administrative | /u01/app/oracle/oradata/mydb/sysaux01.dbf |

This example makes the following additional assumptions:

- The target database is a new database that is being populated with the data from the source database. The name of the source database is `mydb`.

- Both the source database and the target database are Oracle Database 19c databases.

Complete the following tasks to transport the database using an export dump file:

Task 1   Generate the Export Dump File
Generate the export dump file by completing the following steps:

1.  Start SQL\*Plus and connect to the database as an administrator or as a user who has either the `ALTER` `TABLESPACE` or `MANAGE` `TABLESPACE` system privilege.

2.  Make all of the user-defined tablespaces in the database read-only.

        ALTER TABLESPACE sales READ ONLY;

        ALTER TABLESPACE customers READ ONLY;

        ALTER TABLESPACE employees READ ONLY;

3.  Invoke the Data Pump export utility as a user with `DATAPUMP_EXP_FULL_DATABASE` role and specify the full transportable export/import options.

        SQL> HOST

        $ expdp user_name full=y dumpfile=expdat.dmp directory=data_pump_dir
                transportable=always logfile=export.log

        Password: password

    You must always specify `TRANSPORTABLE=ALWAYS`, which determines whether the transportable option is used.

    This example specifies the following Data Pump parameters:

    - The `FULL` parameter specifies that the entire database is being exported.

    - The `DUMPFILE` parameter specifies the name of the structural information export dump file to be created, `expdat.dmp`.

    - The `DIRECTORY` parameter specifies the directory object that points to the operating system or Oracle Automatic Storage Management location of the dump file. You must create the `DIRECTORY` object before invoking Data Pump, and you must grant the `READ` and `WRITE` object privileges on the directory to the user running the Export utility. See [Oracle Database SQL Language Reference](../sqlrf/CREATE-DIRECTORY.md) for information on the `CREATE` `DIRECTORY` command.

      In a non-CDB, the directory object `DATA_PUMP_DIR` is created automatically. Read and write access to this directory is automatically granted to the `DBA` role, and thus to users `SYS` and `SYSTEM`.

      However, the directory object `DATA_PUMP_DIR` is not created automatically in a PDB. Therefore, when importing into a PDB, create a directory object in the PDB and specify the directory object when you run Data Pump.

      **See Also:**

      - [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for information about the default directory when the `DIRECTORY` parameter is omitted

      - [Oracle Multitenant Administrator's Guide](../multi/overview-of-managing-a-multitenant-environment.md) for more information about PDBs

    - The `LOGFILE` parameter specifies the file name of the log file to be written by the export utility. In this example, the log file is written to the same directory as the dump file, but it can be written to a different location.

    To perform a full transportable export on an Oracle Database 11g Release 2 (11.2.0.3) or later Oracle Database 11g database, use the `VERSION` parameter, as shown in the following example:

        expdp user_name full=y dumpfile=expdat.dmp directory=data_pump_dir
              transportable=always version=12 logfile=export.log

    Full transportable import is supported only for Oracle Database 12c and later databases.

    **Note:**

    In this example, the Data Pump utility is used to export only data dictionary structural information (metadata) for the user-defined tablespaces. Actual data is unloaded only for the administrative tablespaces (`SYSTEM` and `SYSAUX`), so this operation goes relatively quickly even for large user-defined tablespaces.

4.  Check the log file for errors, and take note of the dump file and data files that you must transport to the target database. `expdp` outputs the names and paths of these files in messages like these:

        ******************************************************************************
        Dump file set for SYSTEM.SYS_EXPORT_TRANSPORTABLE_01 is:
          /u01/app/oracle/admin/mydb/dpdump/expdat.dmp
        ******************************************************************************
        Datafiles required for transportable tablespace SALES:
          /u01/app/oracle/oradata/mydb/sales01.dbf
        Datafiles required for transportable tablespace CUSTOMERS:
          /u01/app/oracle/oradata/mydb/cust01.dbf
        Datafiles required for transportable tablespace EMPLOYEES:
          /u01/app/oracle/oradata/mydb/emp01.dbf

5.  When finished, exit back to SQL\*Plus:

        $ exit

**See Also:**

[Oracle Database Utilities ](../sutil/oracle-data-pump-export-utility.md)for information about using the Data Pump utility

Task 2   Transport the Export Dump File
Transport the dump file to the directory pointed to by the `DATA_PUMP_DIR` directory object, or to any other directory of your choosing. The new location must be accessible to the target database.

At the target database, run the following query to determine the location of `DATA_PUMP_DIR`:

    SELECT * FROM DBA_DIRECTORIES WHERE DIRECTORY_NAME = 'DATA_PUMP_DIR';

    OWNER      DIRECTORY_NAME   DIRECTORY_PATH
    ---------- ---------------- -----------------------------------
    SYS        DATA_PUMP_DIR    C:\app\orauser\admin\orawin\dpdump\

Task 3   Transport the Data Files for the User-Defined Tablespaces
Transport the data files of the user-defined tablespaces in the database to a place that is accessible to the target database.

In this example, transfer the following data files from the source database to the target database:

- `sales01.dbf`

- `cust01.dbf`

- `emp01.dbf`

If you are transporting the database to a platform different from the source platform, then determine if cross-platform database transport is supported for both the source and target platforms, and determine the endianness of each platform. If both platforms have the same endianness, then no conversion is necessary. Otherwise, you must do a conversion of each tablespace in the database, either at the source database or at the target database.

If you are transporting the database to a different platform, you can execute the following query on each platform. If the query returns a row, then the platform supports cross-platform tablespace transport.

    SELECT d.PLATFORM_NAME, ENDIAN_FORMAT
         FROM V$TRANSPORTABLE_PLATFORM tp, V$DATABASE d
         WHERE tp.PLATFORM_NAME = d.PLATFORM_NAME;

The following is the query result from the source platform:

    PLATFORM_NAME                      ENDIAN_FORMAT
    ---------------------------------- --------------
    Solaris[tm] OE (32-bit)            Big

The following is the query result from the target platform:

    PLATFORM_NAME                      ENDIAN_FORMAT
    ---------------------------------- --------------
    Microsoft Windows IA (32-bit)      Little

In this example, you can see that the endian formats are different. Therefore, in this case, a conversion is necessary for transporting the database. Use either the `GET_FILE` or `PUT_FILE` procedure in the `DBMS_FILE_TRANSFER` package to transfer the data files. These procedures convert the data files to the target platform's endian format automatically. Transport the data files to the location of the existing data files of the target database. On the UNIX and Linux platforms, this location is typically /u01/app/oracle/oradata/dbname/ or +DISKGROUP/dbname/datafile/. Alternatively, you can use the RMAN `CONVERT` command to convert the data files. See "[Converting Data Between Platforms](converting-data-between-platforms.md)" for more information.

**Note:**

If no endianness conversion of the tablespaces is needed, then you can transfer the files using any file transfer method.

Task 4   (Optional) Restore Tablespaces to Read/Write Mode
Make the transported tablespaces read/write again at the source database, as follows:

    ALTER TABLESPACE sales READ WRITE;
    ALTER TABLESPACE customers READ WRITE;
    ALTER TABLESPACE employees READ WRITE;

You can postpone this task to first ensure that the import process succeeds.

Task 5   At the Target Database, Import the Database
Invoke the Data Pump import utility as a user with `DATAPUMP_IMP_FULL_DATABASE` role and specify the full transportable export/import options.

    impdp user_name full=Y dumpfile=expdat.dmp directory=data_pump_dir
       transport_datafiles=
          '/u01/app/oracle/oradata/mydb/sales01.dbf',
          '/u01/app/oracle/oradata/mydb/cust01.dbf',
          '/u01/app/oracle/oradata/mydb/emp01.dbf'
       logfile=import.log

    Password: password

This example specifies the following Data Pump parameters:

- The `FULL` parameter specifies that the entire database is being imported in `FULL` mode.

- The `DUMPFILE` parameter specifies the exported file containing the metadata for the user-defined tablespaces and both the metadata and data for the administrative tablespaces to be imported.

- The `DIRECTORY` parameter specifies the directory object that identifies the location of the export dump file. You must create the `DIRECTORY` object before invoking Data Pump, and you must grant the `READ` and `WRITE` object privileges on the directory to the user running the Import utility. See [Oracle Database SQL Language Reference](../sqlrf/CREATE-DIRECTORY.md) for information on the `CREATE` `DIRECTORY` command.

  In a non-CDB, the directory object `DATA_PUMP_DIR` is created automatically. Read and write access to this directory is automatically granted to the `DBA` role, and thus to users `SYS` and `SYSTEM`.

  However, the directory object `DATA_PUMP_DIR` is not created automatically in a PDB. Therefore, when importing into a PDB, create a directory object in the PDB and specify the directory object when you run Data Pump.

  **See Also:**

  - [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for information about the default directory when the `DIRECTORY` parameter is omitted

  - [Oracle Multitenant Administrator's Guide](../multi/overview-of-managing-a-multitenant-environment.md) for more information about PDBs

- The `TRANSPORT_DATAFILES` parameter identifies all of the data files to be imported.

  You can specify the `TRANSPORT_DATAFILES` parameter multiple times in a parameter file specified with the `PARFILE` parameter if there are many data files.

- The `LOGFILE` parameter specifies the file name of the log file to be written by the import utility. In this example, the log file is written to the directory from which the dump file is read, but it can be written to a different location.

After this statement executes successfully, check the import log file to ensure that no unexpected error has occurred.

When dealing with a large number of data files, specifying the list of data file names in the statement line can be a laborious process. It can even exceed the statement line limit. In this situation, you can use an import parameter file. For example, you can invoke the Data Pump import utility as follows:

    impdp user_name parfile='par.f'

For example, `par.f` might contain the following lines:

    FULL=Y
    DUMPFILE=expdat.dmp
    DIRECTORY=data_pump_dir
    TRANSPORT_DATAFILES=
    '/u01/app/oracle/oradata/mydb/sales01.dbf',
    '/u01/app/oracle/oradata/mydb/cust01.dbf',
    '/u01/app/oracle/oradata/mydb/emp01.dbf'
    LOGFILE=import.log

**Note:**

- During the import, user-defined tablespaces might be temporarily made read/write for metadata loading. Ensure that no user changes are made to the data during the import. At the successful completion of the import, all user-defined tablespaces are made read/write.

- When performing a network database import, the `TRANSPORTABLE` parameter must be set to `always`.

- When you are importing into a PDB in a CDB, specify the connect identifier for the PDB after the user name. For example, if the connect identifier for the PDB is `hrpdb`, then enter the following when you run the Oracle Data Pump Import utility:

      impdp user_name@hrpdb ...

**See Also:**

- [Oracle Database Utilities](../sutil/datapump-import-utility.md) for information about using the import utility

- [Oracle Multitenant Administrator's Guide](../multi/managing-a-multitenant-environment.md)

**Parent topic:** [Migrating Oracle Database](migrating-oracle-database.md)
