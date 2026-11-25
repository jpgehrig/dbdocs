## 1.178 LOCK_SGA

`LOCK_SGA` locks the entire SGA into physical memory.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `false`        |
| Modifiable          | No             |
| Modifiable in a PDB | No             |
| Range of values     | `true | false` |
| Basic               | No             |

It is usually advisable to lock the SGA into real (physical) memory, especially if the use of virtual memory would include storing some of the SGA using disk space. This parameter is ignored on platforms that do not support it.

**See Also:**

[Oracle Database Performance Tuning Guide](../tgdba/tuning-system-global-area.md) for more information about using this parameter
