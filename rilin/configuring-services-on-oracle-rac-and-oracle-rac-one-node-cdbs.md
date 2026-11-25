## Configuring Services on Oracle RAC and Oracle RAC One Node CDBs

During installation, if you select a multitenant container database (CDB), and configure pluggable databases (PDBs), then you must add services to the PDBs after installation.

If you do not add services to PDBs, and then the Oracle RAC One Node CDB fails over to another node, or you manually relocate the CDB to another node, then by default, all PDBs associated with the CDB that do not have registered services are restarted in `MOUNTED` state.

PDBs are opened in Read-Write mode after failover, in case of Oracle RAC One Node database, or relocation in case of any Oracle RAC database, only after you have configured the PDBs to have associated services. If you have not associated services to PDBs, then the PDBs remains in `MOUNTED` state when the CDB instance restarts.

To add services to a PDB, use the following `srvctl` command syntax, where `cdbname` is the name of the CDB, `service_name` is the name of the service, and `pdbname` is the name of the PDB:

    srvctl add service -d cdbname -s service_name -pdb pdbname

After you add services to your PDBs, if you relocate the CDB with which the PDBs are associated, or the CDB fails over for Oracle RAC One Node databases, then the PDBs associated with that CDB automatically open in Read-Write state.

**See Also:**

[Oracle Database Concepts](../multi/overview-of-the-multitenant-architecture.md) and [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md) for more information about PDBs and adding services

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
