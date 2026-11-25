## 1.127 FAL_SERVER

`FAL_SERVER` specifies the FAL (fetch archive log) server for a standby database.

| Property            | Description                |
|:--------------------|:---------------------------|
| Parameter type      | String                     |
| Syntax              | `FAL_SERVER = ``string`    |
| Default value       | There is no default value. |
| Modifiable          | `ALTER SYSTEM`             |
| Modifiable in a PDB | No                         |
| Basic               | No                         |

The value is an Oracle Net service name, which is assumed to be configured properly on the standby database system to point to the desired FAL server.

**See Also:**

[Oracle Data Guard Concepts and Administration](../sbydb/using-RMAN-in-oracle-data-guard-configurations.md) for more information about FAL server
