## 1.32 BACKGROUND_DUMP_DEST

`BACKGROUND_DUMP_DEST` specifies the pathname (directory or disc) where debugging trace files for the background processes (LGWR, DBWn, and so on) are written during Oracle operations.

| Property            | Description                                               |
|:--------------------|:----------------------------------------------------------|
| Parameter type      | String                                                    |
| Syntax              | `BACKGROUND_DUMP_DEST = { ``pathname`` | ``directory`` }` |
| Default value       | Operating system-dependent                                |
| Modifiable          | `ALTER SYSTEM`                                            |
| Modifiable in a PDB | No                                                        |
| Range of values     | Any valid local path, directory, or disk                  |
| Basic               | No                                                        |

**Note:**

The `BACKGROUND_DUMP_DEST` parameter is deprecated in Oracle Database 12c Release 1 (12.1.0.1).

An alert log in the directory specified by `BACKGROUND_DUMP_DEST` logs significant database events and messages. Anything that affects the database instance or global database is recorded here. The alert log is a normal text file. Its file name is operating system-dependent. For platforms that support multiple instances, it takes the form `alert_``sid``.log`, where sid is the system identifier. This file grows slowly, but without limit, so you might want to delete it periodically. You can delete the file even when the database is running.

**Note:**

This parameter is ignored by the diagnosability infrastructure introduced in Oracle Database 11g Release 1 (11.1), which places trace and core files in a location controlled by the `DIAGNOSTIC_DEST` initialization parameter.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/diagnosing-and-resolving-problems.md) for more information on the DIAGNOSTIC_DEST initialization parameter

- "[USER_DUMP_DEST](USER_DUMP_DEST.md)" for information on setting a destination for server process trace files
