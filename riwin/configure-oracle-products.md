## Product-Specific Postinstallation Tasks

Many Oracle products and options must be configured before you use them for the first time.

Before using individual Oracle Database 19c products or options, refer to the appropriate manual in the product documentation library, which is available online at: [http://docs.oracle.com](http://docs.oracle.com/).

Refer to the following topics for information about configuring various products and features after installation.

- [Configuring Oracle Database Vault](configuring-oracle-database-vault.md)
  Oracle Universal Installer (OUI) installs Oracle Database Vault by default when you install the Oracle RAC software, but requires additional configuration steps.
- [Configuring Oracle Label Security](configuring-oracle-label-security.md)
  After installation, you must configure Oracle Label Security in a database before you use it.
- [Configuring the OraClrAgnt Service for Oracle Database Extensions for .NET](configuring-the-oraclragnt-service-for-db-extensions-for-net.md)
  Oracle Database Extensions (ODE) for .NET depends on a Windows service to operate properly. This service is called the OraClrAgnt service.
- [Configuring Oracle XML DB](configuring-oracle-xml-db.md)
  Oracle XML DB is a required component of the Oracle Database installation. However, you must manually configure the FTP and HTTP ports for Oracle XML DB.
- [Configure Storage for External Tables, Shared Files, or Directory Objects](configure-storage-for-externall-tables-or-directory-objects.md)
  If your Oracle RAC database uses files that are external to the database, then the external files must be located on shared storage that is accessible to all nodes.

**Parent topic:** [Oracle Real Application Clusters Postinstallation Procedures](oracle-real-application-clusters-postinstallation-procedures.md)
