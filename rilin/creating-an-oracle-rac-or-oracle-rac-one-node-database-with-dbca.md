## Selecting DBCA Options to Create an Oracle RAC or Oracle RAC One Node Database

Review this information to use Database Configuration Assistant (DBCA) to create Oracle RAC or Oracle RAC One Node Database.

**Note:**

You can no longer set up email notification for Oracle RAC databases either from DBCA or Oracle Universal Installer (OUI).

- [Starting DBCA](starting-dbca.md)
  To start DBCA, connect as the installation owner account (for example, `oracle`) to one of your nodes where Oracle RAC is installed, load SSH keys into memory, and enter the command `dbca` from the `$ORACLE_HOME/bin` directory.
- [Cluster Detection and Node Selection when Using DBCA](cluster-detection-and-node-selection-when-using-dbca.md)
  When you start DBCA, it automatically shows Oracle RAC options if it detects from the central Oracle Inventory that the Oracle home is enabled for Oracle RAC.
- [Using DBCA to Select Storage to Use With any Oracle RAC Database](using-dbca-to-select-storage-to-use-with-any-oracle-rac-database.md)
  You can choose to use either Oracle ASM disk groups or a supported cluster file system as storage.
- [Selecting Server Pool Option with DBCA](selecting-server-pool-option-in-dbca.md)
  When creating a database using Database Configuration Assistant (DBCA), you can choose the server pools to host policy-managed databases.
- [Using DBCA to Specify Database Initialization Parameters for Oracle RAC](using-dbca-to-specify-database-initialization-parameters-for-oracle-rac.md)
  Specify initialization parameters if you intend to add more nodes in your cluster.
- [Actions Performed By DBCA for Oracle RAC Databases](actions-performed-by-dbca-for-oracle-rac-databases.md)
  Review this information to understand about DBCA actions during Oracle RAC database creation.

**Parent topic:** [Creating Oracle RAC or Oracle RAC One Node Databases with Oracle DBCA](selecting-dbca-options-to-create-oracle-rac-or-oracle-rac-one-node-databases-with-dbca.md)
