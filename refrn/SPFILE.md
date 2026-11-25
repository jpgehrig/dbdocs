## 1.346 SPFILE

The value of this parameter is the name of the current server parameter file (`SPFILE`) in use.

| Property            | Description                                  |
|:--------------------|:---------------------------------------------|
| Parameter type      | String                                       |
| Syntax              | `SPFILE = ``spfile_name`                     |
| Default value       | `ORACLE_HOME``/dbs/spfile.ora`               |
| Modifiable          | No                                           |
| Modifiable in a PDB | No                                           |
| Range of values     | Any valid `SPFILE`                           |
| Basic               | No                                           |
| Oracle RAC          | Multiple instances must have the same value. |

This parameter can be defined in a client side PFILE to indicate the name of the server parameter file to use.

When the default server parameter file is used by the server, the value of `SPFILE` is internally set by the server.

The `SPFILE` resides in the `ORACLE_HOME``/dbs` directory; however, users can place it anywhere on their system as long as it is specified in an initialization parameter file.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for more information about creating the server parameter file
