## 1.121 ENABLE_PLUGGABLE_DATABASE

`ENABLE_PLUGGABLE_DATABASE` is a bootstrap initialization parameter to create a CDB.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `false`        |
| Modifiable          | No             |
| Modifiable in a PDB | No             |
| Range of values     | `true | false` |
| Basic               | No             |

This parameter enables a database in `NOMOUNT` startup mode to know that it is a CDB.

This parameter must be set in `init.ora` before creating a CDB.

**Note:**

See [Oracle Multitenant Administrator's Guide](../multi/introduction-to-the-multitenant-architecture.md) for more information about CDBs and PDBs.
