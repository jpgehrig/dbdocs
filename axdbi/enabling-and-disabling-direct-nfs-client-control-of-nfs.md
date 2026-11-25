By default, Direct NFS Client is installed in a disabled state with single-instance Oracle Database installations. Before enabling Direct NFS, you must configure an `oranfstab` file.

Use these procedures to enable or disable Direct NFS Client Oracle Disk Manager Control of NFS

### Enabling Direct NFS Client Control of NFS

1.  Change the directory to `$ORACLE_HOME/rdbms/lib`.

2.  Enter the following command:

        make -f ins_rdbms.mk dnfs_on

### Disabling Direct NFS Client Control of NFS

1.  Log in as the Oracle software installation owner, and disable Direct NFS Client using the following commands:

        cd $ORACLE_HOME/rdbms/lib
        make -f ins_rdbms.mk dnfs_off

2.  Remove the `oranfstab` file.

**Note:**

If you remove an NFS path that an Oracle Database is using, then you must restart the database for the change to take effect.

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-database.md)
