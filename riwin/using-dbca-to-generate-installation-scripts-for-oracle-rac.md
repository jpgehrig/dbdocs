## Using DBCA to Generate Installation Scripts for Oracle RAC

You can generate scripts that create an Oracle RAC database and prepare the database for use.

1.  Start Oracle Database Configuration Assistant (DBCA) and select your preferred options to build the Oracle RAC database.
    1.  On the Creation Options page of your DBCA session, deselect Create Database.
    2.  Select Generate Database Creation Scripts.
    3.  Click Finish.

    You can accept the default destination directory for the scripts, or browse for a different location. In either case, note the path name for use in the next step.
2.  Go to the directory where DBCA created the scripts, and review the SQL scripts to ensure that they contain the statements to build a database with the characteristics you require.
    If the scripts do not contain the statements for the specific database characteristics you need, then Oracle recommends that you rerun DBCA to create scripts with the desired configuration rather than editing the scripts yourself.
3.  On each cluster node you identified during your DBCA session, run the script `sid``.bat`, where sid is the SID prefix that you entered on the DBCA Database Name page.
4.  Set the initialization parameter, `cluster_database`, to the value `TRUE` in your SPFILE by entering an `ALTER SYSTEM` statement in SQL\*Plus, or by uncommenting the parameter in the PFILE for each instance.
5.  Configure Oracle Net Services to support your new database and instances.
6.  Set the `REMOTE_LISTENER` parameter to the SCAN (using the Easy Connect Naming syntax scanname:scanport) in your SPFILE by entering an `ALTER SYSTEM` statement in SQL\*Plus, or by uncommenting the parameter in the PFILE for each instance.
7.  Run the Server Control Utility (SRVCTL) to configure and start database and instance applications as described in Oracle Real Application Clusters Administration and Deployment Guide.

**See Also:**

- "[Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)"

- "[Selecting DBCA Options to Create an Oracle RAC or Oracle RAC One Node Database](creating-an-oracle-rac-or-oracle-rac-one-node-database-with-dbca.md)" for additional information about running a DBCA session.

**Parent topic:** [Using Scripts or Response Files to Create Oracle RAC Databases](using-scripts-or-response-files-to-create-oracle-rac-databases.md)
