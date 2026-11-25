This illustration shows a CDB with a `CDB$ROOT` container, a `PDB$SEED` container plugged into the root, and several PDBs plugged into the root. One PDB is being unplugged from the CDB. The illustration shows two ways to unplug the PDB:

- One way shows the database files and the XML metadata file of the unplugged PDB. An `ALTER` `PLUGGABLE` `DATABASE` `...` `UNPLUG` `INTO` statement unplugs the PDB.

- Another way shows the database files and the XML metadata file of the unplugged PDB in a single .PDB file. An `ALTER` `PLUGGABLE` `DATABASE` `...` `UNPLUG` `INTO` statement unplugs the PDB.
