## Using DBCA to Generate Installation Scripts for Oracle RAC

Review this topic to generate scripts to create an Oracle RAC database, create a database using the generated scripts, and prepare the database for use.

Complete the following steps:

1.  Start DBCA and select your preferred options to build the Oracle RAC database.
    On the Creation Options page of your DBCA session, deselect Create Database and select Generate Database Creation Scripts before you click Finish. You can accept the default destination directory for the scripts, or browse for a different location. In either case, note the path name for use in the next step.
2.  Go to the directory where DBCA created the scripts, and review the SQL scripts to ensure that they contain the statements to build a database with the characteristics you require. If they do not, then Oracle recommends that you rerun DBCA to create scripts with the desired configuration rather than editing the scripts yourself.
3.  On each cluster node you identified during your DBCA session, run the script `sid``.sh`, where `sid` is the SID prefix that you entered on the DBCA Database Name page.
4.  Set the initialization parameter, `cluster_database`, to the value `TRUE` in your SPFILE by running an `ALTER SYSTEM` statement in SQL\*Plus, or by uncommenting the parameter in the SPFILE for each instance.
5.  Configure Oracle Net Services to support your new database and instances.
6.  Set the `REMOTE_LISTENER` parameter to the SCAN (using the Easy Connect Naming syntax `scanname:scanport`) in your SPFILE by entering an `ALTER SYSTEM` statement in SQL\*Plus, or by uncommenting the parameter in the PFILE for each instance.
7.  Run the Server Control Utility (SRVCTL) to configure and start database and instance applications as described in the following document:
    [Oracle Real Application Clusters Administration and Deployment Guide](../racad/index.md)

**Related Topics**

- [Understanding the Configured Environment in Oracle RAC](understanding-the-configured-environment-in-oracle-rac.md)

**Parent topic:** [Using Scripts or Response Files to Create Oracle RAC Databases](using-scripts-or-response-files-to-create-oracle-rac-databases.md)
