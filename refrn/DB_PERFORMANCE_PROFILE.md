## 1.92 DB_PERFORMANCE_PROFILE

`DB_PERFORMANCE_PROFILE` specifies the performance profile for a database or a pluggable database (PDB).

| Property            | Description                                    |
|:--------------------|:-----------------------------------------------|
| Parameter type      | String                                         |
| Syntax              | `DB_PERFORMANCE_PROFILE =` `string`            |
| Default value       | There is no default value.                     |
| Modifiable          | No                                             |
| Modifiable in a PDB | Yes                                            |
| Basic               | No                                             |
| Oracle RAC          | The same value should be set on all instances. |

A performance profile supports easier management for hundreds of databases or PDBs.

On Oracle Exadata, the performance profile for the regular database or CDB is pushed down to the Exadata storage cells. The performance profile is used for the management of Exadata I/O Resource Manager.

A CDB resource plan can specify different resource controls for a performance profile using the `DBMS_RESOURCE_MANAGER.CREATE_CDB_PROFILE_DIRECTIVE` procedure. A PDB with a matching performance profile will use the specified controls.

The value of `DB_PERFORMANCE_PROFILE` can be up to 30 characters and is not case sensitive.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md) for information about the `DBMS_RESOURCE_MANAGER.CREATE_CDB_PROFILE_DIRECTIVE` procedure.
