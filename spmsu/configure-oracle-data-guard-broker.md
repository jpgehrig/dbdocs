InitialConnectIdentifier is replaced by DGConnectIdentifier, which affects upgrades from Oracle Database 10g.

The value of `DGConnectIdentifier` is used for all Data Guard network traffic, all of the time. If you are upgrading an Oracle Database release 10g configuration, which requires you to first upgrade to Oracle Database 11g, then the value that exists for `InitialConnectIdentifier` is retained as the new value for `DGConnectIdentifier` for the database. When upgrading an Oracle Real Application Clusters (Oracle RAC) database, database administrators must ensure that the value for the `InitialConnectIdentifier` property reaches all instances.

In a migration, you need to perform this step only for the standby database.

**Parent topic:** [Recommended and Best Practices to Complete After Upgrading Oracle Database](recommended-and-best-practices-complete-upgrading-oracle-database.md)
