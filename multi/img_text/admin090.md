This illustration shows a CDB with a `CDB$ROOT` container, a `PDB$SEED` container plugged into the root, and several PDBs plugged into the root. One PDB is a new PDB. The illustration shows two options for creating the new PDB:

- A `CREATE` `PLUGGABLE` `DATABASE` `...` `USING` statement uses the unplugged PDB’s XML metadata file along with the unplugged PDB’s database files to create the new PDB.

- A `CREATE` `PLUGGABLE` `DATABASE` `...` `USING` statement uses a .PDB archive file to create the new PDB. The .PDB archive file contains the unplugged PDB’s database files and the unplugged PDB’s XML metadata file that are used to create the new PDB.
