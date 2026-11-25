Active database duplication does not require backups of the source database. It duplicates the live source database to the destination host by copying the database files over the network to the auxiliary instance. RMAN can copy the required files as image copies or backup sets.

For active database duplication, the duplication technique used determines which channel performs the principal work. When active database duplication is performed using backup sets, the principal work of duplication is performed by the auxiliary channels. When image copies are used, the primary work is performed by the target channels.

To perform active database duplication, a connection to the target database is required. Oracle recommends that you use active database duplication in general, unless network bandwidth between the source host and the destination host is a constraint. Active database duplication requires minimal setup and is simpler to perform.

**Note:**

For active database duplication, the source database must use a server parameter file.

Some of the scenarios in which active database duplication using backup sets may be preferred over using image copies are:

- You want to use multisection backups, compression, or encryption while duplicating your database.

- The source database does not have sufficient network resources to transfer the required database files to the duplicate database.

- You want to minimize the resources used by the duplication process.

  Active database duplication with backup sets uses minimal resources on the source database.

**Parent topic:** [Migrating and Upgrading Oracle Database](migrating-and-upgrading-oracle-database.md)
