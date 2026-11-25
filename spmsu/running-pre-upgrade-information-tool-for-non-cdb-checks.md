To check your system and database to see if it is ready for upgrade, use the Pre-Upgrade Information Tool (`preupgrade.jar`)

The Pre-Upgrade Information Tool is in the new release Oracle home, in the file path `ORACLE_HOME/rdbms/admin/preupgrade.jar`. Oracle has configured it with the system checks necessary for the new Oracle Database release. However, the checks that the tool performs are carried out on the earlier release Oracle Database home. Set up the Oracle user environment variables so that they point to the earlier release Oracle home.

Run the Pre-Upgrade Information Tool by using the Java version in your earlier release Oracle home. For multitenant architecture (CDB and PDB) upgrades, open up all the PDBs that you want the tool to analyze before you run the tool.

Set the environment variables for your user account to point to the earlier release ORACLE_HOME, ORACLE_BASE, and ORACLE_SID.

### Pre-Upgrade Information Tool Location

The `preupgrade.jar` file is located in the new Oracle home:

    New_release_Oracle_home/rdbms/admin/preupgrade.jar

You can also copy the `preupgrade.jar` binaries to a path of your choosing. For example:

`/tmp/preupgrade.jar`

### Pre-Upgrade Information Tool Syntax

    $Earlier_release_Oracle_home/jdk/bin/java -jar $New_release_Oracle_home
    /rdbms/admin/preupgrade.jar [FILE|TERMINAL] [TEXT|XML] [DIR output_dir]

Example 8-4 Non-CDB In the Source Oracle Home Example

1.  Set your user environment variables to point to the earlier release Oracle home.

        $ export ORACLE_HOME=/u01/app/oracle/product/12.1.0/dbhome_1
        $ export ORACLE_BASE=/u01/app/oracle
        $ export ORACLE_SID=sales01
        $ export PATH=.:$ORACLE_HOME/bin:$PATH

2.  Run the new release Oracle Database Pre-Upgrade Information Tool on the earlier release Oracle Database server, using the environment settings you have set to the earlier release Oracle home.

        $ORACLE_HOME/jdk/bin/java -jar /u01/app/oracle/product/18.0.0/dbhome_1/rdbms/admin/preupgrade.jar TERMINAL TEXT

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/using-preupgrade-information-tool-for-oracle-database.md)

**Parent topic:** [Using the Pre-Upgrade Information Tool for Oracle Database](using-the-pre-upgrade-information-tool-for-oracle-db.md)
