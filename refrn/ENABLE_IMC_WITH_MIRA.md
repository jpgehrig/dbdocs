## 1.120 ENABLE_IMC_WITH_MIRA

`ENABLE_IMC_WITH_MIRA` enables or disables the In-Memory Column Store and Oracle Data Guard Multi-Instance Redo Apply, at the same time, on an Active Data Guard standby database.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | Boolean                                       |
| Default value       | `false`                                       |
| Modifiable          | `ALTER SYSTEM`                                |
| Modifiable in a PDB | No                                            |
| Range of values     | `true | false`                                |
| Basic               | No                                            |
| Oracle RAC          | Different instances can use different values. |

The value of this parameter is relevant only on the instance where MRP0 is spawned at the start of Redo Apply on a standby database.

**Note:**

This parameter is available starting with Oracle Database 19c.
