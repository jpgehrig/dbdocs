## 1.185 LOG_ARCHIVE_MAX_PROCESSES

`LOG_ARCHIVE_MAX_PROCESSES` specifies the maximum number of ARCn processes that can be created.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Integer        |
| Default value       | `4`            |
| Modifiable          | `ALTER SYSTEM` |
| Modifiable in a PDB | No             |
| Range of values     | `1` to `30`    |
| Basic               | No             |

**See Also:**

- "[Background Processes](background-processes.md)" for more information about ARCn processes

- [Oracle Database Administrator’s Guide](../admin/managing-archived-redo-log-files.md) for more information about `LOG_ARCHIVE_MAX_PROCESSES`
