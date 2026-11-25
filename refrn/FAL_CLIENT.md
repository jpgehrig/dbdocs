## 1.126 FAL_CLIENT

`FAL_CLIENT` specifies the FAL (fetch archive log) client name that is used by the FAL service, configured through the `FAL_SERVER` initialization parameter, to refer to the FAL client.

| Property            | Description                |
|:--------------------|:---------------------------|
| Parameter type      | String                     |
| Syntax              | `FAL_CLIENT = ``string`    |
| Default value       | There is no default value. |
| Modifiable          | `ALTER SYSTEM`             |
| Modifiable in a PDB | No                         |
| Basic               | No                         |

The value is an Oracle Net service name, which is assumed to be configured properly on the FAL server system to point to the FAL client (standby database).

**See Also:**

[Oracle Data Guard Concepts and Administration](../sbydb/using-RMAN-in-oracle-data-guard-configurations.md) for more information about FAL server
