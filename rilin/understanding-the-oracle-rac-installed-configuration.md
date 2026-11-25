## 6  Understanding the Oracle RAC Installed Configuration

Understand the groups and environment settings for the Oracle Real Application Clusters (Oracle RAC) installed configuration.

- [Understanding the Configured Environment in Oracle RAC](understanding-the-configured-environment-in-oracle-rac.md)
  Oracle Net Configuration Assistant (NETCA) and Database Configuration Assistant (DBCA) configure your environment to meet the requirements for database creation and Oracle Enterprise Manager discovery of Oracle RAC databases.
- [Understanding Operating System Privileges Groups](understanding-operating-system-privileges-groups.md)
  Review this information for system privileges required for Oracle Database or Oracle Automatic Storage Management (Oracle ASM) administration.
- [Understanding Time Zone Settings on Cluster Nodes](understanding-time-zone-settings-on-cluster-nodes.md)
  Oracle RAC requires that all cluster nodes have the same time zone setting.
- [Understanding the Server Parameter File for Oracle RAC](understanding-the-server-parameter-file-for-oracle-rac.md)
  When you create the database, Oracle Database creates an SPFILE in the file location that you specify. This location can be either an Oracle ASM disk group or a cluster file system.
- [About ORATAB Configuration for Oracle RAC](about-oratab-configuration-for-oracle-rac.md)
  Oracle creates an entry for each Oracle RAC database in the `oratab` configuration file.
- [Database Components Created Using Database Configuration Assistant](database-components-created-using-database-configuration-assistant.md)
  Understand the database components that DBCA creates.
- [Managing Undo Tablespaces in Oracle RAC](managing-undo-tablespaces-in-oracle-rac.md)
  Oracle Database stores rollback or undo information in undo tablespaces. To manage undo tablespaces, Oracle recommends that you use Automatic Undo Management.
- [About Initialization Parameter Files](about-initialization-parameter-files.md)
  Oracle recommends using the server parameter file (SPFILE) for storing Oracle Database initialization parameters.
- [Oracle Net Services Configuration for Oracle RAC Databases](oracle-net-services-configuration-for-oracle-rac-databases.md)
  Users can access an Oracle RAC database using a client and server configuration or through one or more middle tiers, with or without connection pooling.
- [Performance Features of Oracle Net Services and Oracle RAC](performance-features-of-oracle-net-services-and-oracle-rac.md)
  Oracle RAC databases provide the important benefits of connection load balancing and failover.
- [Oracle Net Services Configuration Files and Parameters](oracle-net-services-configuration-files-and-parameters.md)
  If you use a naming method other than Easy Connect, then additional configuration of Oracle Net Services may be required.
