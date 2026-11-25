You can use the `GET_FILE` or `PUT_FILE` procedure of the `DBMS_FILE_TRANSFER` package to convert data between platforms during a data file transfer.

When you use one of these procedures to move data files between the source platform and the target platform, each block in each data file is converted to the target platform's endianness.

This section uses an example to describe how to use the `DBMS_FILE_TRANSFER` package to convert a data file to a different platform. The example makes the following assumptions:

- The `GET_FILE` procedure will transfer the data file.

- The `mytable.342.123456789` data file is being transferred to a different platform.

- The endianness of the source platform is different from the endianness of the target platform.

- The global name of the source database is `dbsa.example.com`.

- Both the source database and the target database use Oracle Automatic Storage Management (Oracle ASM).

**Note:**

You can also use the `DBMS_FILE_TRANSFER` package to transfer data files between platforms with the same endianness.

Complete the following steps to convert the data file by transferring it with the `GET_FILE` procedure:

1.  Use SQL\*Plus to connect to the source database as an administrative user who can create directory objects.
2.  Create a directory object to store the data files that you want to transfer to the target database.
    For example, to create a directory object named `sales_dir_source` for the `+data/dbsa/datafile` directory, execute the following SQL statement:

        CREATE OR REPLACE DIRECTORY sales_dir_source
           AS '+data/dbsa/datafile';

    The specified file system directory must exist when you create the directory object.
3.  Use SQL\*Plus to connect to the target database as an administrative user who can create database links, create directory objects, and run the procedures in the `DBMS_FILE_TRANSFER` package.
4.  Create a database link from the target database to the source database.
    The connected user at the source database must have read privileges on the directory object that you created in Step 2.
5.  Create a directory object to store the data files that you want to transfer from the source database.
    The user at the local database who will run the procedure in the `DBMS_FILE_TRANSFER` package must have write privileges on the directory object.

    For example, to create a directory object named `sales_dir_target` for the `+data/dbsb/datafile` directory, run the following SQL statement:

        CREATE OR REPLACE DIRECTORY sales_dir_target
          AS '+data/dbsb/datafile';
6.  Run the `GET_FILE` procedure in the `DBMS_FILE_TRANSFER` package to transfer the data file.
    For example, run the following procedure to transfer the `mytable.342.123456789` data file from the source database to the target database using the database link you created in Step 4:

        BEGIN
          DBMS_FILE_TRANSFER.GET_FILE(
            source_directory_object      => 'sales_dir_source',
            source_file_name             => 'mytable.342.123456789',
            source_database              => 'dbsa.example.com',
            destination_directory_object => 'sales_dir_target',
            destination_file_name        => 'mytable');
        END;
        /

**Note:**

In this example, the destination data file name is `mytable`. Oracle ASM does not allow a fully qualified file name form in the `destination_file_name` parameter of the `GET_FILE` procedure.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_FILE_TRANSFER.md) for more information about using the `DBMS_FILE_TRANSFER` package

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-files-directories-templates.md) for information about fully qualified file name forms in ASM

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DATABASE-LINK.md) for information about how to create a database link

**Parent topic:** [Converting Data to the Endian Format of the Target Operating System](converting-data-files.md)
