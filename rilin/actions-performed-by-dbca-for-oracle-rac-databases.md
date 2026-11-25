## Actions Performed By DBCA for Oracle RAC Databases

Review this information to understand about DBCA actions during Oracle RAC database creation.

After you respond to DBCA prompts, review the Summary dialog information and click OK, DBCA does the following:

- Creates an Oracle RAC database, and its instances

- Creates the Oracle RAC data dictionary views

- Starts the CRS (Cluster Ready Service) resource for the database

**Caution:**

After you have created the Oracle RAC database, if you decide to install additional Oracle Database products in the Oracle RAC database you have created, then before you attempt to install the products, you must stop all processes running in the Oracle RAC database homes.

You must stop all processes running in the Oracle RAC homes so that Oracle Universal Installer can relink certain executables and libraries.

**Parent topic:** [Selecting DBCA Options to Create an Oracle RAC or Oracle RAC One Node Database](creating-an-oracle-rac-or-oracle-rac-one-node-database-with-dbca.md)
