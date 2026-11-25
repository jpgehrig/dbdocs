## 1.350 STANDBY_DB_PRESERVE_STATES

`STANDBY_DB_PRESERVE_STATES` controls whether user sessions, buffers, and other internal states of the instance are retained when a readable physical standby database is converted to a primary database. This parameter is meaningful on a physical standby database that is open in real-time query mode.

| Property            | Description                                                      |
|:--------------------|:-----------------------------------------------------------------|
| Parameter type      | String                                                           |
| Syntax              | `STANDBY_DB_PRESERVE_STATES = { NONE | SESSION | BUFFER | ALL }` |
| Default value       | `NONE`                                                           |
| Modifiable          | No                                                               |
| Modifiable in a PDB | No                                                               |
| Basic               | No                                                               |
| Oracle RAC          | The same value must be used on all instances.                    |

### Values

- `NONE`

  Nothing is retained. All sessions are disconnected and all buffers are flushed. This is the default value.

- `SESSION`

  The role transition waits 10 seconds for active sessions to finish the current statement or top-level PL/SQL call. The sessions that are still active after 10 seconds are terminated. The sessions that complete their work in this lap of time are retained, along with inactive sessions. If the database is reopened as the primary within 300 seconds, the retained sessions resume their operations as if nothing had happened. If the database (or individual PDB) is not opened in the primary role within 300 seconds, the sessions will be terminated.

- `BUFFER`

  All current buffers are retained. Media recovery buffers are converted to current buffers and retained, if possible. When the database is reopened as the primary, the retained buffers are available for use, which may enable queries to run faster during the first few minutes of operation. If the database (or an individual PDB) is not opened in the primary role, the buffers will be flushed.

- `ALL`

  This value is equivalent to setting both the `SESSION` and `BUFFER` values.

**Note:**

Sessions that have long running queries or are using database links will not be retained regardless of the setting of this parameter.

**See Also:**

- [Oracle Data Guard Concepts and Administration](../sbydb/managing-oracle-data-guard-physical-standby-databases.md) for more information about real-time query mode

- [Oracle Data Guard Concepts and Administration](../sbydb/managing-oracle-data-guard-role-transitions.md) for more information about preserving user sessions and buffers when a standby database is converted to a primary database
