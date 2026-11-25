Before you run the Pre-Upgrade Information Tool, in preparation for your non-CDB upgrade, set up the user environment variables for the Oracle user that runs the tool.

You must set up the user environment variables for the Pre-Upgrade information tool. This example shows how to use shell commands to set up user environment variables to point to an earlier release Oracle home.

In this example, the operating system is Linux or UNIX, the system identifier is `sales01`, and the earlier release Oracle home path is `/u01/app/oracle/product/12.1.0/dbhome_1`

1.  Log in as the Oracle installation owner (`oracle`).
2.  Set up the user environment variables to point to the earlier release Oracle home that you want to upgrade.
    For example:

        $ export ORACLE_HOME=/u01/app/oracle/product/12.1.0/dbhome_1
        $ export ORACLE_BASE=/u01/app/oracle
        $ export ORACLE_SID=sales01
        $ export PATH=.:$ORACLE_HOME/bin:$PATH

**Parent topic:** [Using the Pre-Upgrade Information Tool for Oracle Database](using-the-pre-upgrade-information-tool-for-oracle-db.md)
