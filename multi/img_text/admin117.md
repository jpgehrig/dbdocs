This illustration shows a CDB with a `CDB$ROOT` container, a `PDB$SEED` container plugged into the CDB root, an application container plugged into the CDB root, and several PDBs plugged into the CDB root. The application container has an application root, an application seed plugged into the application root, and several application PDBs plugged into the application root. One PDB is a new application PDB that is plugged into the application root. The illustration shows two options for creating the new PDB:

- A `CREATE` `PLUGGABLE` `DATABASE` `...` `USING` statement uses the unplugged PDB’s XML metadata file along with the unplugged PDB’s database files to create the new application PDB.

- A `CREATE` `PLUGGABLE` `DATABASE` `...` `USING` statement uses a .PDB archive file to create the new application PDB. The .PDB archive file contains the unplugged PDB’s database files and the unplugged PDB’s XML metadata file that are used to create the new PDB.
