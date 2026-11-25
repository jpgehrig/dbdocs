If your Oracle Database uses Oracle Automatic Storage Management (Oracle ASM) for storage, then shut down the database before upgrading Oracle Restart.

1.  Log in as the Oracle Home user.
2.  Shut down the Oracle Database instance.
        C:\> Grid_home\bin\srvctl stop database –d database_unique_name
3.  Ensure that your Oracle Database instance is shut down.
        C:\> Grid_home\bin\srvctl status database –d database_unique_name
        Database is not running.

**Parent topic:** [Preparing to Upgrade Oracle Restart](preparing-to-upgrade-oracle-restart.md)
