## Oracle Net Services Configuration for Oracle RAC Databases

When connecting to an Oracle Database, you can use a connect descriptor or a net service name.

For Oracle RAC databases, you can also use the single client access name (SCAN) to connect to any available instance of the Oracle RAC database. Users can access an Oracle RAC database using a client/server configuration or through one or more middle tiers, with or without connection pooling.

- [Database Services for an Oracle RAC Database](database-services-for-an-oracle-rac-database.md)
  Each database is represented by one or more services. A service is identified by a service name, such as `sales.example.com`.
- [Naming Methods and Connect Descriptors](naming-methods-and-connect-descriptors.md)
  Each net service name is associated with a connect descriptor. A connect descriptor provides the location of the database and the name of the database service.
- [Easy Connect Naming Method](easy-connect-naming-method.md)
  The Easy Connect naming method eliminates the need to look up service names in the tnsnames.ora file or other repository for TCP/IP environments.
- [Understanding SCANs](understanding-scans.md)
  The SCAN is a domain name registered to at least one and up to three IP addresses, either in domain name service (DNS) or in Grid Naming Service (GNS).
- [About Connecting to an Oracle RAC Database Using SCANs](about-connecting-to-an-oracle-rac-database-using-scans.md)
  Oracle recommends that you configure Oracle RAC database clients to use the SCAN to connect to the database instead of configuring the `tnsnames.ora` file.
- [About Listener Configuration for an Oracle RAC Database](listener-configuration-for-an-oracle-rac-database.md)
  An Oracle RAC database uses multiple listeners to direct client requests to the available instances.
- [About Service Registration for an Oracle RAC Database](service-registration-for-an-oracle-rac-database.md)
  An Oracle Database 19c database service automatically registers with the listeners specified in the database initialization parameters `LOCAL_LISTENER` and `REMOTE_LISTENER`.
- [How Database Connections are Created When Using SCANs](how-database-connections-are-created-when-using-scans.md)
  Based on the environment, the following actions occur when you use a SCAN to connect to an Oracle RAC database using a service name.

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
