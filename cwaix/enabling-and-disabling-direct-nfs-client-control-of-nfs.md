Use these commands to enable or disable Direct NFS Client Oracle Disk Manager Control of NFS.

By default, Direct NFS Client is installed in an enabled state. However, if Direct NFS Client is disabled and you want to enable it, complete the following steps on each node. If you use a shared Grid home for the cluster, then complete the following steps in the shared Grid home:

1.  Log in as the Oracle Grid Infrastructure installation owner.
2.  Change directory to `Grid_home``/rdbms/lib`.
3.  Enter the following command:
        $ make -f ins_rdbms.mk dnfs_on

**Note:**

If you remove an NFS path that an Oracle Database is using, then you must restart the database for the change to take effect.

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-grid-infrastructure.md)
