## Simplified Upgrade of TIMESTAMP WITH TIME ZONE Data

Time zone files are upgraded when you install Oracle Real Application Clusters.

As part of an installation of Oracle Database 19c, time zone files are installed in the path `Oracle_home``\oracore\zoneinfo`. You can continue to use the current time zone file or upgrade to the latest version. Oracle recommends that you upgrade the server to the latest version of the time zone file. Upgrading to a new version of the time zone file may cause existing TIMESTAMP WITH TIME ZONE data to become stale. Using the newly provided DBMS_DST PL/SQL package, you can update the TIMESTAMP WITH TIME ZONE data transparently, with minimal manual procedures and system downtime.

All instances of an Oracle RAC database must use the same time zone. The Oracle RAC database time zone defaults to the time zone setting of the Grid user, unless an instance is started with SQL\*Plus. When you use SQL\*Plus, you must be sure to use the same time zone setting for the database instance that is used for Oracle Clusterware. You can change the time zone Oracle Clusterware uses for a database by using the following command, where time_zone is the time zone to which you want to change:

    srvctl setenv database -env "TZ=time_zone"

Time zone version files are also installed with Oracle Client installations. You do not have to upgrade Oracle Client time zone files immediately. Upgrades can be done at a time when it is most convenient to the system administrator. However, there could be a small performance penalty when client and server use different time zone versions.

**See Also:**

- [Oracle Database Upgrade Guide](../upgrd/using-preupgrade-information-tool-for-oracle-database.md) for information about preparing to upgrade TIMESTAMP WITH TIME ZONE data

- [Oracle Database Globalization Support Guide](../nlspg/datetime-data-types-and-time-zone-support.md) for information about how to upgrade the time zone file and TIMESTAMP WITH TIME ZONE data

- [Oracle Call Interface Programmer's Guide](../lnoci/index.md) for information about performance effects of clients and servers operating with different versions of time zone files

**Parent topic:** [Installing Oracle RAC and Oracle RAC One Node](installing-oracle-rac-and-oracle-rac-one-node.md)
