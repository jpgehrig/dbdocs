## Disabling Direct NFS Client

Complete the following steps to disable the Direct NFS Client:

1.  Log in as the Oracle Grid Infrastructure software owner.
2.  Set `ORACLE_HOME` to Oracle home for which the Direct NFS Client must be disabled.
3.  Change directory to `ORACLE_HOME\``bin`.
4.  Shut down the Oracle database.
5.  Run the batch file, `disable_dnfs.bat` to delete `ORACLE_HOME``\rdbms\lib\odm\oranfsodm18.dll`.
6.  Remove the `oranfstab` file.

**Note:**

If you remove an NFS path that an Oracle Database is using, then you must restart the database for the change to take effect.

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-oracle-database.md)
