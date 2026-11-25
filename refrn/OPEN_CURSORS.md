## 1.240 OPEN_CURSORS

`OPEN_CURSORS` specifies the maximum number of open cursors (handles to private SQL areas) a session can have at once. You can use this parameter to prevent a session from opening an excessive number of cursors.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Integer        |
| Default value       | `50`           |
| Modifiable          | `ALTER SYSTEM` |
| Modifiable in a PDB | Yes            |
| Range of values     | 0 to 65535     |
| Basic               | Yes            |

It is important to set the value of `OPEN_CURSORS` high enough to prevent your application from running out of open cursors. The number will vary from one application to another. Assuming that a session does not open the number of cursors specified by `OPEN_CURSORS`, there is no added overhead to setting this value higher than actually needed.

**See Also:**

- [Oracle Database Performance Tuning Guide](../tgdba/tuning-shared-pool-and-large-pool.md) for more information on setting this parameter

- Your operating system-specific Oracle documentation for the range of values
