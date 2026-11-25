## Oracle Net Services Configuration Files and Parameters

Networking elements for the Oracle Database server and clients are preconfigured for most environments.

The Easy Connect naming method is enabled by default and does not require a repository. If you use a naming method other than Easy Connect, then additional configuration of Oracle Net Services may be required.

- [Database Initialization Parameters for Database Service Registration](database-init-parameters-for-service-registration.md)
  An Oracle Database 19c database service automatically registers with the listeners specified in the `LOCAL_LISTENER` and `REMOTE_LISTENER` parameters.
- [Net Service Names and the tnsnames.ora File](net-service-names-and-the-tnsnames-ora-file.md)
  The installation process creates a `tnsnames.ora` file on each node.
- [Net Service Names Created by DBCA](net-service-names-created-by-dbca.md)
  Oracle Database Configuration Assistant creates net service names for connecting to the database instances.
- [Listener Configuration and the listener.ora File](listener-configuration-and-the-listener-ora-file.md)
  In Oracle RAC environments, Oracle recommends that you let the Oracle Agent manage Oracle listeners for Oracle Databases.
- [Net Services Profile File (sqlnet.ora)](net-services-profile-file-sqlnet-ora.md)
  Oracle Universal Installer starts Oracle Net Configuration Assistant (NETCA) after the database software is installed. NETCA creates the Oracle Net Services profile, or the `sqlnet.ora` file.

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
