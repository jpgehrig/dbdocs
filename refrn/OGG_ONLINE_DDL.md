## 1.237 OGG_ONLINE_DDL

Use `OGG_ONLINE_DDL` to enable or disable GoldenGate replication of online DDLs.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | Boolean                                       |
| Default value       | `false`                                       |
| Modifiable          | `ALTER SYSTEM ... SID='*'`                    |
| Modifiable in a PDB | Yes                                           |
| Range of values     | `true | false`                                |
| Basic               | No                                            |
| Oracle RAC          | The same value must be used on all instances. |

To enable GoldenGate replication of online DDLs, set this parameter to `true`; to disable GoldenGate replication of online DDLs, set this parameter to `false`.

Prior to the introduction of the `OGG_ONLINE_DDL` parameter, online DDLs were not allowed while using GoldenGate replication.

**Note:**

This parameter is available starting with Oracle Database 19c, Release Update 19.22.
