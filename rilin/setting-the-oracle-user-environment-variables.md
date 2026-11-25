## Setting the Oracle User Environment Variables

On each node, in the installation owner user profile file, set the environment variables `ORACLE_BASE` and `ORACLE_HOME`, and `ORACLE_SID`; also add `ORACLE_HOME/bin` to the path environment variable.

Set environment variables as shown, in the following example:

    export ORACLE_BASE=/u01/app/oracle
    export ORACLE_HOME=/u01/app/oracle/product/19.0.0/dbhome_1
    export PATH=$PATH:$ORACLE_HOME/bin
    export ORACLE_SID=sales1

If the environment variables `ORACLE_HOME` and `ORACLE_SID` are not set, and you try to use SQL\*Plus or other tools, then you receive an error message requesting that you set these variables.

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
