## 1.116 ENABLE_AUTOMATIC_MAINTENANCE_PDB

`ENABLE_AUTOMATIC_MAINTENANCE_PDB` can be used to enable or disable the running of automated maintenance tasks for all the PDBs in a CDB or for individual PDBs in a CDB.

| Property            | Description                                      |
|:--------------------|:-------------------------------------------------|
| Parameter type      | Boolean                                          |
| Default value       | `true`                                           |
| Modifiable          | `ALTER SYSTEM`                                   |
| Modifiable in a PDB | Yes                                              |
| Range of values     | `true | false`                                   |
| Basic               | No                                               |
| Oracle RAC          | The same value should be used for all instances. |

**Note:**

The value of this parameter in CDB\$ROOT (the root of a CDB) has no effect in the root. Automated maintenance tasks are always run in the root, regardless of the setting of this parameter.

By default, the value of `ENABLE_AUTOMATIC_MAINTENANCE_PDB` is `true` in CDB\$ROOT (the root container in the CDB) and in the individual PDBs in a CDB. This means that by default, automated maintenance tasks are run for the CDB root and all the PDBs in the CDB.

When you change the value of `ENABLE_AUTOMATIC_MAINTENANCE_PDB` in the CDB root, the new value takes effect in the root and in all the PDBs in the CDB.

Therefore, if you change the value of `ENABLE_AUTOMATIC_MAINTENANCE_PDB` in the CDB root to `false`, the value of `ENABLE_AUTOMATIC_MAINTENANCE_PDB` is also changed to `false` in all of the PDBs in the CDB.

You can also change the value of `ENABLE_AUTOMATIC_MAINTENANCE_PDB` in any of the individual PDBs in a CDB, and the value that is set for each individual PDB will be honored. This enables you to enable or disable automated maintenance tasks for individual PDBs.

**See Also:**

- "[AUTOTASK_MAX_ACTIVE_PDBS](AUTOTASK_MAX_ACTIVE_PDBS.md)" for information about specifying the maximum number of PDBs that can schedule automated maintenance tasks at the same time

- [Oracle Database Administrator’s Guide](../admin/managing-automated-database-maintenance-tasks.md) for more information about managing automated database maintenance tasks
