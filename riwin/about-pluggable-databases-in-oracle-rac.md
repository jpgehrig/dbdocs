## About Pluggable Databases in Oracle RAC

A pluggable database (PDB) is a portable collection of schemas, schema objects, and nonschema objects that appears to an Oracle Net client as a non-CDB.

PDBs can be plugged into to CDBs. A CDB can contain multiple PDBs. Each PDB appears on the network as a separate database.

Starting in Oracle Database 12c, you must create a database as either a multitenant container database (CDB) or as an Oracle database that is non-CDB. This also applies to Oracle RAC databases. The only difference to the installation process is to choose whether to create the Oracle RAC database as a CDB or a non-CDB.

If you create an Oracle RAC database as a CDB and plug one or more PDBs into the CDB, then, by default, a PDB is not started automatically on any instance of the Oracle RAC CDB. With the first dynamic database service assigned to the PDB (other than the default database service which has the same name as the database name), the PDB is made available on those instances on which the service runs.

Whether a PDB is available on more than one instance of an Oracle RAC CDB is typically managed by the services running on the PDB. You can manually enable PDB access on each instance of an Oracle RAC CDB by starting the PDB manually on that instance.

**See Also:**

- [Oracle Database Concepts](../multi/introduction-to-the-multitenant-architecture.md) for more information about PDBs

- [Oracle Database Administrator's Guide](../multi/managing-a-multitenant-environment.md) for more information about managing PDBs

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/administering-database-instances-and-cluster-databases.md) for information specific to the administration of Oracle RAC CDBs

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
