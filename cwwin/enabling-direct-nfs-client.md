## Enabling Direct NFS Client

You enable Direct NFS Client by running the `enable_dnfs.bat` command

1.  Shut down the Oracle Database instance.
2.  Create and configure an `oranfstab` file in `ORACLE_HOME``\dbs`.
3.  Set `ORACLE_HOME` to Oracle home for which the Direct NFS Client must be enabled.
4.  Change directory to `ORACLE_HOME``\bin`.
5.  Run the batch file `enable_dnfs.bat`.
6.  Restart the Oracle Database instance.

For Oracle RAC, repeat the above procedure on all nodes in the cluster.

**Related Topics**

- [Creating an oranfstab File for Direct NFS Client](creating-an-oranfstab-file-for-direct-nfs-client.md)

**Parent topic:** [Configuring Direct NFS Client for Oracle RAC Data Files](configuring-direct-nfs-client-for-oracle-rac-data-files.md)
