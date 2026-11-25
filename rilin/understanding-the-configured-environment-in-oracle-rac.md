## Understanding the Configured Environment in Oracle RAC

Oracle Net Configuration Assistant (NETCA) and Database Configuration Assistant (DBCA) configure your environment to meet the requirements for database creation and Oracle Enterprise Manager discovery of Oracle RAC databases.

**Note:**

Configuration files are created on each node in your cluster database.

Avoid changing host names after you complete your Oracle RAC installation, including adding or deleting domain qualifications. Node names are created from the host names during an Oracle Clusterware installation and are used extensively with database processes. Nodes with changed host names must be deleted from the cluster and added back with the new host names.

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
