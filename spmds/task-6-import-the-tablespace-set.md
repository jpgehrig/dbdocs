To complete the transportable tablespaces operation, import the tablespace set.

To import the tablespace set:

1.  Run the Data Pump import utility as a user with `DATAPUMP_IMP_FULL_DATABASE` role and import the tablespace metadata.
        impdp user_name dumpfile=expdat.dmp directory=data_pump_dir
           transport_datafiles=
           'c:\app\orauser\oradata\orawin\sales_101.dbf',
           'c:\app\orauser\oradata\orawin\sales_201.dbf'
           remap_schema=sales1:crm1  remap_schema=sales2:crm2
           logfile=tts_import.log

        Password: password

    This example specifies the following Data Pump parameters:

    - The `DUMPFILE` parameter specifies the exported file containing the metadata for the tablespaces to be imported.

    - The `DIRECTORY` parameter specifies the directory object that identifies the location of the export dump file. You must create the `DIRECTORY` object before running Data Pump, and you must grant the `READ` and `WRITE` object privileges on the directory to the user running the Import utility. See [Oracle Database SQL Language Reference](../sqlrf/CREATE-DIRECTORY.md) for information on the `CREATE` `DIRECTORY` command.

      In a non-CDB, the database creates the directory object `DATA_PUMP_DIR` automatically. Read and write access to this directory is automatically granted to the `DBA` role, and thus to users `SYS` and `SYSTEM`.

      However, the database does not create the directory object `DATA_PUMP_DIR` automatically in a PDB. Therefore, when importing into a PDB, create a directory object in the PDB and specify the directory object when you run Data Pump.

      **See Also:**

      - [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for information about the default directory when the `DIRECTORY` parameter is omitted

      - [Oracle Multitenant Administrator's Guide](../multi/overview-of-managing-a-multitenant-environment.md) for more information about PDBs

    - The `TRANSPORT_DATAFILES` parameter identifies all of the data files containing the tablespaces to be imported.

      You can specify the `TRANSPORT_DATAFILES` parameter multiple times in a parameter file specified with the `PARFILE` parameter if there are many data files.

    - The `REMAP_SCHEMA` parameter changes the ownership of database objects. If you do not specify `REMAP_SCHEMA`, then all database objects (such as tables and indexes) are created in the same user schema as in the source database, and those users must already exist in the target database. If they do not exist, then the import utility returns an error. In this example, objects in the tablespace set owned by `sales1` in the source database will be owned by `crm1` in the target database after the tablespace set is imported. Similarly, objects owned by `sales2` in the source database will be owned by `crm2` in the target database. In this case, the target database is not required to have users `sales1` and `sales2`, but must have users `crm1` and `crm2`.

      Starting with Oracle Database 12c Release 2 (12.2), the Recovery Manager (RMAN) `RECOVER` command can move tables to a different schema while remapping a table. See [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-recovering-tables-partitions.md) for more information.

    - The `LOGFILE` parameter specifies the file name of the log file to be written by the import utility. In this example, the log file is written to the directory from which the dump file is read, but it can be written to a different location.

    After this statement runs successfully, all tablespaces in the set being copied remain in read-only mode. Check the import log file to ensure that no error has occurred.

    When dealing with a large number of data files, specifying the list of data file names in the statement line can be a laborious process as the data file list can even exceed the statement line limit. In this situation, you can use an import parameter file. For example, you can run the Data Pump import utility as follows:

        impdp user_name parfile='par.f'

    The `par.f` parameter file contains the following:

        DUMPFILE=expdat.dmp
        DIRECTORY=data_pump_dir
        TRANSPORT_DATAFILES=
        'C:\app\orauser\oradata\orawin\sales_101.dbf',
        'C:\app\orauser\oradata\orawin\sales_201.dbf'
        REMAP_SCHEMA=sales1:crm1  REMAP_SCHEMA=sales2:crm2
        LOGFILE=tts_import.log

    **See Also:**

    [Oracle Database Utilities](../sutil/datapump-import-utility.md) for information about using the import utility
2.  If required, put the tablespaces into read/write mode on the target database.

**Parent topic:** [Migrating Oracle Database](migrating-oracle-database.md)
