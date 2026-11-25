Transport the data files of the tablespaces to a directory that is accessible to the target database.

In this example, transfer the following files from the source database to the target database:

- `sales_101.dbf`

- `sales_201.dbf`

If you are transporting the tablespace set to a platform different from the source platform, then determine if cross-platform tablespace transport is supported for both the source and target platforms, and determine the endianness of each platform. If both platforms have the same endianness, then no conversion is necessary. Otherwise, you must do the data conversion either at the source database or at the target database.

If you are transporting `sales_1` and `sales_2` to a different platform, then you can run the following query on each platform. If the query returns a row, the platform supports cross-platform tablespace transport.

    SELECT d.PLATFORM_NAME, ENDIAN_FORMAT
         FROM V$TRANSPORTABLE_PLATFORM tp, V$DATABASE d
         WHERE tp.PLATFORM_NAME = d.PLATFORM_NAME;

The following is the query result from the source platform:

    PLATFORM_NAME                      ENDIAN_FORMAT
    ---------------------------------- --------------
    Solaris[tm] OE (32-bit)            Big

The following is the result from the target platform:

    PLATFORM_NAME                      ENDIAN_FORMAT
    ---------------------------------- --------------
    Microsoft Windows IA (32-bit)      Little

In this example, you can see that the endian formats are different. Therefore, in this case, a conversion is necessary for transporting the database. Use either the `GET_FILE` or `PUT_FILE` procedure in the `DBMS_FILE_TRANSFER` package to transfer the data files. These procedures convert the data files to the target platform's endian format automatically. Transport the data files to the location of the existing data files of the target database. On the UNIX and Linux platforms, this location is typically /u01/app/oracle/oradata/dbname/ or +DISKGROUP/dbname/datafile/. Alternatively, you can use to convert the data files.

**Note:**

- If you use the RMAN `CONVERT` command, then conversion of data files between different endian formats is not supported for data files having undo segments.

- If no endianness conversion of the tablespaces is needed, then you can transfer the files using any file transfer method.

**Parent topic:** [Migrating Oracle Database](migrating-oracle-database.md)
