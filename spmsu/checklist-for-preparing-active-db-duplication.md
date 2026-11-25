Ensure that you prepare source and target databases before using RMAN to carry out active database duplication.

Source Oracle Database:

- To migrate the source database, you need the database name, database unique name, listener port, service name, database home patch level, and the password for SYS.

- If you have configured source database with Transparent Data Encryption (TDE), then you need a backup of the wallet and the wallet password to allow database duplication with encrypted data.

- The source database can be either in the open or in the mount state.

  - If the source database is open, then it must be in archivelog mode.

    The source database remains fully accessible to users while you are performing the database duplication. Be prepared to take a slight hit on CPU usage and network bandwidth consumption during datafile duplication.

  - If the source database is in the mount state, then shut it down cleanly before bringing it up to the mount state.

    **Note:**

    If you choose to maintain the source database in mount state, then the users cannot access the database.

Target Oracle Database:

- A target database system that supports the same database edition as the source database edition.

- Ensure that you have the target database name, database unique name, auxiliary service name, and applied current database home patch level.

- A free TCP port in the target database to setup the auxiliary instance.

**Parent topic:** [Preparing Servers and Network for Database Duplication](preparing-servers-and-network-for-db-duplication.md)
