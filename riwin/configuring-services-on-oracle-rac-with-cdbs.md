## Configuring Services on Oracle RAC with CDBs

During installation, if you select a multitenant container database (CDB), and configure pluggable databases (PDBs), then Oracle recommends that you add services to the PDBs after installation.

If you do not add services to PDBs, and then the Oracle RAC One Node CDB fails over to another node, or you manually relocate the CDB to another node, then by default, all PDBs associated with that CDB that do not have registered services are restarted in `MOUNTED` state.

PDBs are opened in Read Write mode after failover or relocation only after you have configured the PDBs to have associated services. If you have not associated services to PDBs, then the PDBs remains in `MOUNTED` state when the CDB instance restarts.

- Use the following `srvctl` command syntax, where cdbname is the name of the CDB, service_name is the name of the service, and pdbname is the name of the PDB:
      srvctl add service -d cdbname -s service_name -pdb pdbname

After you add services to your PDBs, if you relocate the CDB with which the PDBs are associated, or the CDB fails over, then the PDBs associated with that CDB automatically open in `Read Write` state.

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
