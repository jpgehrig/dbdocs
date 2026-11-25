## Oracle Net Services Configuration Files and Parameters

If you use a naming method other than Easy Connect, then additional configuration of Oracle Net Services may be required.

Networking elements for the Oracle Database server and clients are preconfigured for most environments. The Easy Connect naming method is enabled by default and does not require a repository.

Review these topics for information about the Oracle Net Services configuration files and parameters for an Oracle RAC database:

- [Database Initialization Parameters for Database Service Registration](database-initialization-parameters-for-database-service-registration.md)
  An Oracle Database 19c database service automatically registers with the listeners specified in the `LOCAL_LISTENER` and `REMOTE_LISTENER` parameters.
- [Net Service Names and the tnsnames.ora File](net-service-names-and-the-tnsnames-ora-file.md)
  The installation process creates a `tnsnames.ora` file on each node. This file acts as a repository of net service names. Each net service name is associated with a connect identifier. A connect identifier is an identifier that maps a user-defined name to a connect descriptor.
- [Net Service Names Created by DBCA](net-service-names-created-by-dbca.md)
  DBCA creates net service names for connections.
- [Listener Configuration and the listener.ora File](listener-configuration-and-the-listener-ora-file.md)
  In Oracle RAC environments, Oracle recommends that you let the Oracle Agent manage Oracle listeners for Oracle Databases.
- [Net Services Profile File (sqlnet.ora)](net-services-profile-file-sqlnet-ora.md)
  Use Oracle NETCA to create the Oracle Net Services profile, or the `sqlnet.ora` file.

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
