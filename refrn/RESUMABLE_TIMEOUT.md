## 1.318 RESUMABLE_TIMEOUT

`RESUMABLE_TIMEOUT` enables or disables resumable statements and specifies resumable timeout at the system level.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | Integer                                       |
| Default value       | `0` (seconds)                                 |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`               |
| Modifiable in a PDB | Yes                                           |
| Range of values     | `0` to 2<sup>31</sup> - 1 (in seconds)        |
| Basic               | No                                            |
| Oracle RAC          | Multiple instances can have different values. |

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-space-for-schema-objects.md) for more information about enabling resumable space allocation, what conditions are correctable, and what statements can be made resumable
