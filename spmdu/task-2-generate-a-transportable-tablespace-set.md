After ensuring that you have a self-contained set of tablespaces that you want to transport, generate a transportable tablespace set.

To generate a transportable tablespace set:

1.  Start SQL\*Plus and connect to the database as an administrator or as a user who has either the `ALTER` `TABLESPACE` or `MANAGE` `TABLESPACE` system privilege.
2.  Make all tablespaces in the set read-only.
        ALTER TABLESPACE sales_1 READ ONLY;

        ALTER TABLESPACE sales_2 READ ONLY;
3.  Run the Data Pump export utility as a user with `DATAPUMP_EXP_FULL_DATABASE` role and specify the tablespaces in the transportable set.
        SQL> HOST

        $ expdp user_name dumpfile=expdat.dmp directory=data_pump_dir
                transport_tablespaces=sales_1,sales_2 logfile=tts_export.log

        Password: password

    You must always specify `TRANSPORT_TABLESPACES`, which specifies that the transportable option is used. This example specifies the following additional Data Pump parameters:

    - The `DUMPFILE` parameter specifies the name of the structural information export dump file to be created, `expdat.dmp`.

    - The `DIRECTORY` parameter specifies the directory object that points to the operating system or Oracle Automatic Storage Management location of the dump file. You must create the `DIRECTORY` object before invoking Data Pump, and you must grant the `READ` and `WRITE` object privileges on the directory to the user running the Export utility.

      In a non-CDB, the directory object `DATA_PUMP_DIR` is created automatically. Read and write access to this directory is automatically granted to the `DBA` role, and thus to users `SYS` and `SYSTEM`.

      However, the directory object `DATA_PUMP_DIR` is not created automatically in a PDB. Therefore, when importing into a PDB, create a directory object in the PDB and specify the directory object when you run Data Pump.

    - The `LOGFILE` parameter specifies the log file to create for the export utility. In this example, the log file is created in the same directory as the dump file, but you can specify any other directory for storing the log file.

    - Triggers and indexes are included in the export operation by default.

    To perform a transport tablespace operation with a strict containment check, use the `TRANSPORT_FULL_CHECK` parameter, as shown in the following example:

        expdp use_name dumpfile=expdat.dmp directory=data_pump_dir
              transport_tablespaces=sales_1,sales_2 transport_full_check=y
              logfile=tts_export.log

    In this case, the Data Pump export utility verifies that there are no dependencies between the objects inside the transportable set and objects outside the transportable set. If the tablespace set being transported is not self-contained, then the export fails and indicates that the transportable set is not self-contained. You must resolve these violations and then run this task again.

    **Note:**

    In this example, the Data Pump utility is used to export only data dictionary structural information (metadata) for the tablespaces. No actual data is unloaded, so this operation goes relatively quickly even for large tablespace sets.
4.  The `expdp` utility displays the names and paths of the dump file and the data files on the command line as shown in the following example. These are the files that you need to transport to the target database. Also, check the log file for any errors.
        *****************************************************************************
        Dump file set for SYSTEM.SYS_EXPORT_TRANSPORTABLE_01 is:
          /u01/app/oracle/admin/salesdb/dpdump/expdat.dmp
        *****************************************************************************
        Datafiles required for transportable tablespace SALES_1:
          /u01/app/oracle/oradata/salesdb/sales_101.dbf
        Datafiles required for transportable tablespace SALES_2:
          /u01/app/oracle/oradata/salesdb/sales_201.dbf
5.  When the Data Pump export operation is completed, exit the `expdp` utility to return to SQL\*Plus:
        $ EXIT

    **See Also:**

    - [Oracle Database SQL Language Reference](../sqlrf/CREATE-DIRECTORY.md) for information on the `CREATE DIRECTORY` command

    - [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for information about the default directory when the `DIRECTORY` parameter is omitted

    - [Oracle Database Utilities ](../sutil/oracle-data-pump-export-utility.md)for information about using the Data Pump utility

    - [Oracle Multitenant Administrator's Guide](../multi/overview-of-managing-a-multitenant-environment.md) for more information about PDBs

**Parent topic:** [Migrating Oracle Database](migrating-oracle-database.md)
