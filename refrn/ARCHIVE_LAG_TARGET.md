## 1.17 ARCHIVE_LAG_TARGET

`ARCHIVE_LAG_TARGET` forces a log switch after the specified amount of time elapses.

| Property            | Description                                  |
|:--------------------|:---------------------------------------------|
| Parameter type      | Integer                                      |
| Default value       | `0` (disabled)                               |
| Modifiable          | `ALTER SYSTEM`                               |
| Modifiable in a PDB | No                                           |
| Range of values     | 0 or any integer in \[60, 7200\]             |
| Basic               | No                                           |
| Oracle RAC          | Multiple instances should use the same value |

A 0 value disables the time-based thread advance feature; otherwise, the value represents the number of seconds. Values larger than 7200 seconds are not of much use in maintaining a reasonable lag in the standby database. The typical, or recommended value is 1800 (30 minutes). Extremely low values can result in frequent log switches, which could degrade performance; such values can also make the archiver process too busy to archive the continuously generated logs.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-the-redo-log.md) for more information about setting this parameter
