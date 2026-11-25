## 5.120 DBA_INMEMORY_AIMTASKS

`DBA_INMEMORY_AIMTASKS` displays information about Automatic In-Memory management tasks.

| Column          | Datatype       | NULL | Description                                                                          |
|:----------------|:---------------|:-----|:-------------------------------------------------------------------------------------|
| `TASK_ID`       | `NUMBER`       |      | Number that uniquely identifies a specific automatic IM column store management task |
| `CREATION_TIME` | `TIMESTAMP(6)` |      | Creation time of the task                                                            |
| `STATE`         | `VARCHAR2(7)`  |      | State of the task                                                                    |

**See Also:**

[Oracle Database In-Memory Guide](../inmem/configuring-memory-management.md) for more information about configuring the Automatic In-Memory feature
