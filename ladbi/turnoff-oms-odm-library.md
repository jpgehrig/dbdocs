## Turning-Off the OMS ODM Library

Learn how to turn off the ODM library.

1.  To turn off the ODM library:
        $ cd $ORACLE_HOME/rdbms/lib
        $ make -f ins_rdbms.mk oms_off
2.  Recycle the instance and ensure that the following message is not present in the alert log after instance startup
        Oracle instance running with ODM: OMS (Oracle memory speed)
        ODM Library, Version: 2.0

**Parent topic:** [Deploying Oracle Database with Oracle Memory Speed](deploying-database-oms.md)
