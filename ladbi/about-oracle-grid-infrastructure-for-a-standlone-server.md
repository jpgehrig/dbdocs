## About Oracle Grid Infrastructure for a Standalone Server

If you plan to use Oracle Automatic Storage Management (Oracle ASM), then you must install Oracle Restart before installing your database.

Oracle Grid Infrastructure for a standalone server is a version of Oracle Grid Infrastructure that supports single instance databases. This support includes volume management, file system, and automatic restart capabilities. Oracle Grid Infrastructure for a standalone server includes Oracle Restart and Oracle Automatic Storage Management. Oracle combined the two infrastructure products into a single set of binaries that is installed into an Oracle Restart home.

Oracle Restart is a feature provided as part of Oracle Grid Infrastructure. Oracle Restart monitors and can restart Oracle Database instances, Oracle Net Listeners, and Oracle ASM instances. Oracle Restart is currently restricted to manage single instance Oracle Databases and Oracle ASM instances only.

Oracle Automatic Storage Management is a volume manager and a file system for Oracle Database files that supports single-instance Oracle Database and Oracle Real Application Clusters (Oracle RAC) configurations. Oracle Automatic Storage Management also supports a general purpose file system for your application needs, including Oracle Database binaries. Oracle Automatic Storage Management is Oracle's recommended storage management solution that provides an alternative to conventional volume managers, and file systems.

Oracle Restart improves the availability of your Oracle database by providing the following services:

- When there is a hardware or a software failure, Oracle Restart automatically starts all Oracle components, including the Oracle database instance, Oracle Net Listener, database services, and Oracle ASM.

- Oracle Restart starts components in the proper order when the database host is restarted.

- Oracle Restart runs periodic checks to monitor the status of Oracle components. If a check operation fails for a component, then the component is shut down and restarted.

Note the following restrictions for using Oracle Restart:

- You can neither install Oracle Restart on an Oracle Grid Infrastructure cluster member node, nor add an Oracle Restart server to an Oracle Grid Infrastructure cluster member node. Oracle Restart supports single-instance databases on one server, while Oracle Grid Infrastructure for a Cluster supports single-instance or Oracle RAC databases on a cluster.

- If you want to use Oracle ASM or Oracle Restart, then you should install Oracle Grid Infrastructure for a standalone server before you install and create the database. Otherwise, you must install Oracle Restart, and then manually register the database with Oracle Restart.

- You can use the Oracle Restart implementation of Oracle Grid Infrastructure only in single-instance (nonclustered) environments. Use Oracle Grid Infrastructure with Oracle Clusterware for clustered environments.

**Parent topic:** [Supported Storage Options for Oracle Database and Oracle Grid Infrastructure](supported-storage-options-for-oracle-database-and-oracle-grid-infrastructure.md)
