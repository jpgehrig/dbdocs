## Provisioning a Pluggable Database

You can provision a pluggable database (PDB) on an existing container database (CDB) running in a provisioned database working copy.

After you create a working copy of a gold image, provision that working copy to a target, and create a database as a multitenant CDB, you can add a PDB to the CDB using the `rhpctl addpdb database` command.

- The following command example creates a PDB called `pdb19c` on a CDB called `raccdb19c`, which is on a working copy called `wc_db19c`:
      $ rhpctl addpdb database -workingcopy wc_db19c -cdbname raccdb19c -pdbname pdb19c
- Use the `rhpctl deletepdb database` command to delete a PDB from an existing CDB on a working copy.
  The following command example deletes a PDB called `pdb19c` on a CDB called `raccdb19c`, which is on a working copy called `wc_db19c`:
      $ rhpctl deletepdb database -workingcopy wc_db19c -cdbname raccdb19c -pdbname pdb19c

**Parent topic:** [Oracle Fleet Patching and Provisioning Use Cases](fleet-patching-provisioning-use-cases.md)
