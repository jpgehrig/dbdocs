## Locating the Server Parameter File

The starter database contains one database initialization response file. The initialization response file, `init.ora`.xxxxx, must exist for an instance to start.

A response file is a text file that contains a list of instance configuration parameters. The starter database `init.ora` file has preconfigured parameters. You must not edit this file to use the starter database.

The server parameter file (SPFILE) is created from the initialization response file, then the initialization response file is renamed. The SPFILE file name is `spfile``SID``.ora` and is located in the `ORACLE_HOME``\database` directory.

To use EM Express to view the location of the server parameter file and list the initialization parameters, see the "Viewing and Modifying Initialization Parameters" section in Oracle Database 2 Day DBA.

**See Also:**

[Oracle Database 2 Day DBA](../admqs/managing-the-oracle-instance.md)

**Parent topic:** [Getting Started with Oracle Database](getting-started-with-oracle-database.md)
