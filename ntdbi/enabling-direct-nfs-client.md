## Enabling Direct NFS Client

To enable Direct NFS Client, you must add an `oranfstab` file to the `Oracle_home``\dbs` directory and modify the related DLL files used by the Oracle Database software.

1.  Create an `oranfstab` file.
2.  Replace the standard ODM library, `oraodm19.dll`, with the ODM NFS library
    Oracle Database uses the ODM library, `oranfsodm19.dll`, to enable Direct NFS Client. To replace the ODM library, complete the following steps:
    1.  Change directory to `Oracle_home``\bin`.
    2.  Shut down the Oracle Database instance on a node using the Server Control Utility (SRVCTL).
    3.  Enter the following commands:
            copy oraodm19.dll oraodm19.dll.orig
            copy /Y oranfsodm19.dll oraodm19.dll
    4.  Restart the Oracle Database instance using SRVCTL.
    5.  Repeat Step 2.a to Step 2.d for each node in the cluster.

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-oracle-database.md)
