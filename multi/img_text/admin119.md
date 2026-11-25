This illustration shows a CDB with a `CDB$ROOT` container, a `PDB$SEED` container plugged into the root, and several PDBs plugged into the root. There is an application container plugged into the CDB root. The application container has an application seed and several application PDBs plugged into it. One application PDB is being unplugged from the application container. The illustration shows two ways to unplug the application PDB:

- One way shows the database files and the XML metadata file of the unplugged application PDB. An `ALTER` `PLUGGABLE` `DATABASE` `...` `UNPLUG` `INTO` statement unplugs the application PDB.

- Another way shows the database files and the XML metadata file of the unplugged application PDB in a single .PDB file. An `ALTER` `PLUGGABLE` `DATABASE` `...` `UNPLUG` `INTO` statement unplugs the application PDB.
