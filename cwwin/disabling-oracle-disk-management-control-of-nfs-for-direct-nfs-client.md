## Disabling Direct NFS Client

You disable Direct NFS Client by running the `disable_dnfs.bat` command.

1.  Shut down the Oracle Database instance.
2.  Remove the `oranfstab` configuration file from `ORACLE_HOME``\dbs`.
3.  Set ORACLE_HOME to Oracle home for which the Direct NFS Client must be disabled.
4.  Change directory to `ORACLE_HOME``\bin`.
5.  Run the batch file, `disable_dnfs.bat`.
6.  Restart the Oracle Database instance.

For Oracle RAC, repeat the above procedure on all nodes in the cluster.

**Parent topic:** [Configuring Direct NFS Client for Oracle RAC Data Files](configuring-direct-nfs-client-for-oracle-rac-data-files.md)
