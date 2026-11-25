## 4.267 DBA_DML_LOCKS

`DBA_DML_LOCKS` lists all DML locks held in the database and all outstanding requests for a DML lock.

| Column            | Datatype        | NULL       | Description                                                                                                                                                                                                                                             |
|:------------------|:----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SESSION_ID`      | `NUMBER`        |            | Session holding or acquiring the lock                                                                                                                                                                                                                   |
| `OWNER`           | `VARCHAR2(128)` | `NOT NULL` | Owner of the lock                                                                                                                                                                                                                                       |
| `NAME`            | `VARCHAR2(128)` | `NOT NULL` | Name of the lock                                                                                                                                                                                                                                        |
| `MODE_HELD`       | `VARCHAR2(13)`  |            | The type of lock held. The values are:<br>• `ROWS_S` (`SS`): row share lock<br>• `ROW-X` (`SX`): row exclusive lock<br>• `SHARE` (`S`): share lock<br>• `S/ROW-X` (`SSX`): exclusive lock<br>• `NONE`: lock requested but not yet obtained              |
| `MODE_REQUESTED`  | `VARCHAR2(13)`  |            | Lock request type. The values are:<br>• `ROWS_S` (`SS`): row share lock<br>• `ROW-X` (`SX`): row exclusive lock<br>• `SHARE` (`S`): share lock<br>• `S/ROW-X` (`SSX`): exclusive lock<br>• `NONE`: Lock identifier obtained; lock not held or requested |
| `LAST_CONVERT`    | `NUMBER`        |            | Time since current mode was granted                                                                                                                                                                                                                     |
| `BLOCKING_OTHERS` | `VARCHAR2(40)`  |            | Blocking others                                                                                                                                                                                                                                         |

**See Also:**

[Oracle Database Concepts](../cncpt/data-concurrency-and-consistency.md) for more information about lock modes for table locks
