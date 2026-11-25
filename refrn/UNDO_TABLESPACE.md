## 1.371 UNDO_TABLESPACE

`UNDO_TABLESPACE` specifies the undo tablespace to be used when an instance starts. If this parameter is specified when the instance is in manual undo management mode, then an error will occur and startup will fail.

| Property            | Description                                                                |
|:--------------------|:---------------------------------------------------------------------------|
| Parameter type      | String                                                                     |
| Syntax              | `UNDO_TABLESPACE = ``undoname`                                             |
| Default value       | The first available undo tablespace in the database.                       |
| Modifiable          | `ALTER SYSTEM`                                                             |
| Modifiable in a PDB | Yes                                                                        |
| Range of values     | Legal name of an existing undo tablespace                                  |
| Basic               | Yes                                                                        |
| Oracle RAC          | Each instance must have a unique value for this parameter, when it is set. |

If the `UNDO_TABLESPACE` parameter is omitted, the first available undo tablespace in the database is chosen. If no undo tablespace is available, the instance will start without an undo tablespace. In such cases, user transactions will be executed using the `SYSTEM` rollback segment. You should avoid running in this mode under normal circumstances.

You can replace an undo tablespace with another undo tablespace while the instance is running.

**Note:**

When you update this parameter on the primary database in an Oracle Data Guard configuration, you must also update it on all the physical standby databases in the configuration. This ensures that the standby databases can find the undo tablespace when they become the primary database.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLESPACE.md) for information about creating undo tablespaces
