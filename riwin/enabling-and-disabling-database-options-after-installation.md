## Enabling and Disabling Database Options After Installation

When you install Oracle Database, some options are enabled and the others disabled. You can view the enabled Oracle Database options by querying the `V$OPTION` view using SQL\*Plus.

If you need to enable or disable a particular database feature for an Oracle home, then use the `chopt` tool. The `chopt` tool is a command-line utility that is located in the `ORACLE_HOME``\bin` directory. The syntax for `chopt` is as follows:

    chopt [ enable | disable] db_option

The possible values for `db_option` are described in the following table:

Table 4-2 Database Options for Chopt Tool Command

| Value  | Description                     |
|:-------|:--------------------------------|
| `olap` | Oracle OLAP                     |
| `rat`  | Oracle Real Application Testing |

**Note:**

The Oracle Advanced Analytics (OAA) feature is enabled by default for Oracle Database. You cannot disable it using the `chopt` tool.

Example 4-3 Running the Chopt Tool

To enable the Oracle Real Application Testing option in your Oracle binary files:

1.  Shut down the database with `srvctl` or SQL\*Plus:

        srvctl stop database -d myDb

2.  Stop the database service, `OracleService``SID`, using the Services program in Control Panel.

3.  Run the following commands:

        cd ORACLE_HOME/bin
        chopt enable rat

4.  Start the database service, `OracleService``SID`, using the Services program in Control Panel.

5.  Start up the database:

        srvctl start database -d myDb

**Parent topic:** [Oracle Real Application Clusters Postinstallation Procedures](oracle-real-application-clusters-postinstallation-procedures.md)
