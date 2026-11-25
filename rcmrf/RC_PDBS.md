## 5.35 RC_PDBS

This view provides information about the pluggable databases (PDBs) registered in the recovery catalog. It corresponds to the `V$PDBS` view.

| Column             | Data Type  | Description                                                                                                                                       |
|:-------------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| `PDB_KEY`          | `NUMBER`   | The primary key for this PDB in the recovery catalog.                                                                                             |
| `DB_KEY`           | `NUMBER`   | The primary key for the multitenant container database (CDB) in the recovery catalog. Use this column to join with almost any other catalog view. |
| `NAME`             | `VARCHAR2` | Name of the PDB.                                                                                                                                  |
| `CON_ID`           | `NUMBER`   | Unique identifier of the CDB.                                                                                                                     |
| `DBID`             | `NUMBER`   | Unique identifier of the PDB.                                                                                                                     |
| `GUID`             | `RAW(16)`  | Globally unique identifier (GUID) of this PDB.                                                                                                    |
| `CREATION_CHANGE#` | `NUMBER`   | SCN at which the PDB was created.                                                                                                                 |
