## Product-Specific Postinstallation Tasks

You must complete postinstallation tasks before you can use some Oracle Database features.

- [Configuring Oracle Database Vault](configuring-oracle-database-vault.md)
  OUI installs Oracle Database Vault by default when you install the Oracle RAC software, but you must register Oracle Database Vault with the Oracle RAC database and create database user accounts before you can use it.
- [Configuring Oracle Database Security Settings](configuring-oracle-database-security-settings.md)
  Use Oracle Database Configuration Assistant (DBCA) commands to change security settings after installation.
- [Configuring Oracle Label Security](configuring-oracle-label-security.md)
  After installation, you must configure Oracle Label Security in a database before you use it.
- [Configuring Oracle XML DB](configuring-oracle-xml-db.md)
  Oracle XML DB is a required component of the Oracle Database installation. However, you must manually configure the FTP and HTTP ports for Oracle XML DB.
- [Configuring Storage for External Tables, Shared Files, or Directory Objects](configuring-storage-for-external-tables-shared-files-or-directory-objects.md)
  If your Oracle RAC database uses files that are external to the database, then locate the external files on shared storage that is accessible to all nodes. Each node should use the same mount point to access the file.

**Parent topic:** [Oracle Real Application Clusters Postinstallation Procedures](oracle-real-application-clusters-postinstallation-procedures.md)
