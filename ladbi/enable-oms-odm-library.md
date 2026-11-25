## Enabling the OMS ODM Library

Oracle routes I/O requests to the Oracle Memory Speed (OMS) file system through the Oracle Disk Manager (ODM) library.

1.  To enable the OMS ODM library:
        $ cd $ORACLE_HOME/rdbms/lib
        $ make -f ins_rdbms.mk oms_on
2.  Start the instance. Verify that the Oracle instance is using the OMS file system by searching for the following message in the alert log:
        Oracle instance running with ODM: OMS (Oracle memory speed)
        ODM Library, Version: 2.0

Oracle creates files that have a path prefix starting with `/oracle/omsfs_1` and `/oracle/omsfs_2` in the OMS file system.

**Parent topic:** [Deploying Oracle Database with Oracle Memory Speed](deploying-database-oms.md)
