Learn how to create and start an Oracle Database service.

To create and start an Oracle Database service:

1.  Run ORADIM from the command prompt:
        C:\> oradim -NEW -SID prod -STARTMODE manual
        -PFILE "C:\app\username\admin\prod\pfile\init.ora"

    Note that the previously created initialization parameter file is specified, with complete path, including drive name. You can check if the service is started in the Services window of the Control Panel. ORADIM automatically creates Oracle Database services under the Oracle Home User account. If the Oracle Home User account is a Windows Local User Account or a Windows Domain User Account, then ORADIM prompts for its password.
2.  Set the value of `ORACLE_SID` to `prod`. Note that there are no spaces around the equal sign (=) character:
        C:\> set ORACLE_SID=prod

**Parent topic:** [About Creating and Starting an Oracle Database Service](about-creating-and-starting-an-oracle-database-service.md)
