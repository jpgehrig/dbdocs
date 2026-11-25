## Installing Oracle Grid Infrastructure for a Standalone Server for an Existing Database

Follow the high-level instructions in this section to install Oracle Grid Infrastructure and configure it for an existing Oracle database.

Oracle Restart can manage resources from the same release and releases up to one version lower than Oracle Restart. For this reason, you can install Oracle Restart to provide services only for Oracle Database 19c. However, previous release Oracle Databases can coexist on the same server without being managed by Oracle Restart.

To install Oracle Restart for a database that is already installed:

1.  On the same host computer as the database, install Oracle Restart, and select Configure Oracle Grid Infrastructure for a Standalone Server (Oracle Restart) as the installation option. See, Installing Oracle Restart with a New Database Installation in Oracle Database Installation Guide.

    The Oracle Restart components are installed in an Oracle Grid Infrastructure Oracle home (Grid home), which is in a different location from existing Oracle Database homes.

2.  If you have an existing Oracle Database, then register it for High Availability with Oracle Restart using the `srvctl` command:DRIVE_LETTER:\\ cd ORACLE_HOME\bin DRIVE_LETTER:\\ srvctl add database -db dbname -o oracle_home_path

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](install-configure-oracle-grid-infrastructure-standalone-server.md)
