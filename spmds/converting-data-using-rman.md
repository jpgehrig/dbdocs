When you use the RMAN `CONVERT` command to convert data, you can either convert the data on the source platform after running Data Pump export, or you can convert the data on the target platform before running Data Pump import. In either case, you must transfer the data files from the source system to the target system.

You can convert data with the following RMAN `CONVERT` commands:

- `CONVERT` `DATAFILE`

- `CONVERT` `TABLESPACE`

- `CONVERT` `DATABASE`

**Note:**

- Datatype restrictions apply to the RMAN `CONVERT` command.

- RMAN `CONVERT` commands do not support conversion of data files between different endian formats for data files having undo segments.

<!-- -->

- Converting Tablespaces on the Source System After Export
  An example illustrates how to use the RMAN `CONVERT` `TABLESPACE` command to convert tablespaces to a different platform.
- Converting Data Files on the Target System Before Import
  An example illustrates how to use the RMAN `CONVERT` `DATAFILE` command to convert data files to a different platform.

**See Also:**

- [Oracle Database Backup and Recovery Reference](../rcmrf/CONVERT.md)

- [Oracle Database Backup and Recovery User's Guide](../bradv/rman-transporting-data-across-platforms.md)

**Parent topic:** [Converting Data to the Endian Format of the Target Operating System](converting-data-files.md)

### Converting Tablespaces on the Source System After Export

An example illustrates how to use the RMAN `CONVERT` `TABLESPACE` command to convert tablespaces to a different platform.

The example makes the following assumptions:

- The `sales_1` and `sales_2` tablespaces are being transported to a different platform.

- The endianness of the source platform is different from the endianness of the target platform.

- You want to convert the data on the source system, before transporting the tablespace set to the target system.

- You have completed the Data Pump export on the source database.

Complete the following steps to convert the tablespaces on the source system:

1.  At a command prompt, start RMAN and connect to the source database:
        $ RMAN TARGET /

        Recovery Manager: Release 12.1.0.1.0 - Production

        Copyright (c) 1982, 2012, Oracle and/or its affiliates.  All rights reserved.

        connected to target database: salesdb (DBID=3295731590)
2.  Use the RMAN `CONVERT` `TABLESPACE` command to convert the data files into a temporary location on the source platform.
    In this example, assume that the temporary location, directory `/tmp`, has already been created. The converted data files are assigned names by the system.

        RMAN> CONVERT TABLESPACE sales_1,sales_2
        2> TO PLATFORM 'Microsoft Windows IA (32-bit)'
        3> FORMAT '/tmp/%U';

        Starting conversion at source at 30-SEP-08
        using channel ORA_DISK_1
        channel ORA_DISK_1: starting datafile conversion
        input datafile file number=00007 name=/u01/app/oracle/oradata/salesdb/sales_101.dbf
        converted datafile=/tmp/data_D-SALESDB_I-1192614013_TS-SALES_1_FNO-7_03jru08s
        channel ORA_DISK_1: datafile conversion complete, elapsed time: 00:00:45
        channel ORA_DISK_1: starting datafile conversion
        input datafile file number=00008 name=/u01/app/oracle/oradata/salesdb/sales_201.dbf
        converted datafile=/tmp/data_D-SALESDB_I-1192614013_TS-SALES_2_FNO-8_04jru0aa
        channel ORA_DISK_1: datafile conversion complete, elapsed time: 00:00:25
        Finished conversion at source at 30-SEP-08

    **See Also:**

    [Oracle Database Backup and Recovery Reference](../rcmrf/CONVERT.md) for a description of the RMAN `CONVERT` command
3.  Exit Recovery Manager:
        RMAN> exit
        Recovery Manager complete.
4.  Transfer the data files to the target system.

**Parent topic:** Converting Data Between Platforms Using RMAN

### Converting Data Files on the Target System Before Import

An example illustrates how to use the RMAN `CONVERT` `DATAFILE` command to convert data files to a different platform.

During the conversion, you identify the data files by file name, not by tablespace name. Until the tablespace metadata is imported, the target instance has no way of knowing the desired tablespace names.

The example makes the following assumptions:

- You have not yet converted the data files for the tablespaces being transported.

  If you used the `DBMS_FILE_TRANSFER` package to transfer the data files to the target system, then the data files were converted automatically during the file transfer. See "[Converting Data Between Platforms Using the DBMS_FILE_TRANSFER Package](converting-data-using-the-dbms-file-transfer-package.md)".

- The following data files are being transported to a different platform:

  - C:\Temp\sales_101.dbf

  - C:\Temp\sales_201.dbf

- The endianness of the source platform is different from the endianness of the target platform.

- You want to convert the data on the target system, before performing the Data Pump import.

- The converted data files are placed in C:\app\orauser\oradata\orawin\\ which is the location of the existing data files for the target system:

Complete the following steps to convert the tablespaces on the target system:

1.  If you are in SQL\*Plus, then return to the host system:
        SQL> HOST
2.  Use the RMAN `CONVERT` `DATAFILE` command to convert the data files on the target platform:
        C:\>RMAN TARGET /

        Recovery Manager: Release 12.1.0.1.0 - Production

        Copyright (c) 1982, 2012, Oracle and/or its affiliates.  All rights reserved.

        connected to target database: ORAWIN (DBID=3462152886)

        RMAN> CONVERT DATAFILE
        2>'C:\Temp\sales_101.dbf',
        3>'C:\Temp\sales_201.dbf'
        4>TO PLATFORM="Microsoft Windows IA (32-bit)"
        5>FROM PLATFORM="Solaris[tm] OE (32-bit)"
        6>DB_FILE_NAME_CONVERT=
        7>'C:\Temp\', 'C:\app\orauser\oradata\orawin\'
        8> PARALLELISM=4;

    If the source location, the target location, or both do not use Oracle Automatic Storage Management (Oracle ASM), then the source and target platforms are optional. RMAN determines the source platform by examining the data file, and the target platform defaults to the platform of the host running the conversion.

    If both the source and target locations use Oracle ASM, then you must specify the source and target platforms in the `DB_FILE_NAME_CONVERT` clause.

    **See Also:**

    [Oracle Database Backup and Recovery Reference](../rcmrf/CONVERT.md) for a description of the RMAN `CONVERT` command
3.  Exit Recovery Manager:
        RMAN> exit
        Recovery Manager complete.

**Parent topic:** Converting Data Between Platforms Using RMAN
