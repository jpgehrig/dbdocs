Using backup sets to perform active database duplication is also known as the pull-based method of active database duplication.

In this method, RMAN connects as TARGET to the source database and as AUXILIARY to the auxiliary instance. The auxiliary instance then connects to the source database through Oracle Net Services and retrieves the required database files, over the network, from the source database.

Using backup sets for active database duplication provides the following advantages:

- RMAN can use unused block compression, thus reducing the size of backups that must be transported over the network.

- Backup sets can be created in parallel, on the source database, by using multisection backups.

- Backup sets created on the source database can be encrypted.

**Parent topic:** [Migrating and Upgrading Oracle Database](migrating-and-upgrading-oracle-database.md)
