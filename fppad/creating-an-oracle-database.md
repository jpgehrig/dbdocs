## Creating an Oracle Database

Create an Oracle Database on a working copy.

The Oracle Fleet Patching and Provisioning Server can add a database on a working copy that is on the Oracle Fleet Patching and Provisioning Server, itself, an Oracle Fleet Patching and Provisioning Client, or an `rhpclient`-less target. An Oracle Fleet Patching and Provisioning Client can create a database on a working copy that is running on the Oracle Fleet Patching and Provisioning Client, itself.

- After you create a working copy of a gold image and provision that working copy to an `rhpclient`-less target, you can create an Oracle Database on the working copy using the `rhpctl add database` command, similar to the following command example, which creates an Oracle Real Application Clusters (Oracle RAC) database called `db12201` on a working copy called `wc_db122_1`:
      $ rhpctl add database –workingcopy wc_db122_1 –dbname db12201 -node client_007_node1,client_007_node2 -dbtype RAC -datafileDestination DATA007_DG

The preceding example creates an administrator-managed Oracle RAC database on two nodes in a client cluster. The data file destination is an Oracle ASM disk group that was created prior to running the command. Additionally, you can create Oracle RAC One Node and non-cluster databases.

**Note:**

When you create a database using Oracle Fleet Patching and Provisioning, the feature uses random passwords for both the SYS and SYSTEM schemas in the database and you cannot retrieve these passwords. A user with the DBA or operator role must connect to the database, locally, on the node where it is running and reset the passwords to these two accounts.

**Parent topic:** [Patching and Upgrading Oracle Database](patching-and-upgrading-oracle-database.md)
