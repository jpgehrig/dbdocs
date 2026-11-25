RMAN uses an auxiliary instance to create the duplicate database. You must prepare the auxiliary instance before you begin the duplication.

- [Installing the Oracle Database Software on the Destination Host](installing-the-oracle-db-software-on-the-destination-host.md)
  When the source and destination host are different, you must install the Oracle Database software on the destination host, so that the auxiliary instance can be created.
- [Steps to Create an Initialization Parameter File for the Auxiliary Instance](steps-to-create-an-init-param-file-for-the-aux-instance.md)
  The initialization parameter file for the auxiliary instance must contain at least the `DB_NAME` and `DB_DOMAIN` initialization parameters. Additional parameters may be specified, if required. Ensure that the initialization parameter file is on the same host as the RMAN client that performs the duplication.
- [Copying the Server Parameter File from the Source Database](copying-the-server-param-file-from-the-source-db.md)
  If the source database uses a server parameter file, then including the `SPFILE` option in the `DUPLICATE` command directs RMAN to use the server parameter file from the source database for the auxiliary instance.
- [Creating a Password File for the Auxiliary Instance](creating-a-password-file-for-the-auxiliary-instance.md)
  Connections to the auxiliary instance can be established by using operating system authentication or password file authentication. For backup-based duplication, you can either create a password file or use operating system authentication to connect to the auxiliary instance. For active database duplication, you must use password file authentication.
- [Creating Directories for the Duplicate Database](creating-directories-for-the-duplicate-db.md)
  On the destination host, you must create the directories that RMAN uses to store the duplicate database files on the destination host.
- [Using the Same Names for Database Files in the Source Database and Duplicate Database](using-the-same-names-for-database-files.md)
  Certain conditions must be met to use the same names for files in the source and duplicate database.
- [Establishing Oracle Net Connectivity Between the Source Database and Auxiliary Instance](establish-oracle-net-connectivity.md)
  You must be able to establish a connection between the source database and auxiliary instance for certain forms of duplication.
- [Configuring the Network Between Source and Target Oracle Databases](configuring-the-network-between-source-and-target-dbs.md)
  In preparation for duplicating your Oracle Database, configure the network between your source and target Oracle Database instances.
- [Starting the Auxiliary Instance](starting-the-auxiliary-instance.md)
  The initialization parameter file that you create is used to start the auxiliary instance.
- [Making the Oracle Keystore Available to the Destination Host](making-the-oracle-Keystore-available-to-the-dest-host.md)
  If transparent encryption is configured on the source database, then you must ensure that the Oracle software keystore from the source database is available to the auxiliary instance. Manually copy the keystore from the source database to the destination host.
- [Starting RMAN and Connecting to Databases](starting-rman-and-connecting-to-dbs.md)
  You must start the RMAN client and connect to the database instances as required by the chosen duplication technique. The RMAN client can be located on any host so long as it can connect to the necessary databases over the network.
