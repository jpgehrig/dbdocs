## 5.119 DBA_INMEMORY_AIMTASKDETAILS

`DBA_INMEMORY_AIMTASKDETAILS` displays details for an Automatic In-Memory management task.

| Column           | Datatype        | NULL | Description                                                                          |
|:-----------------|:----------------|:-----|:-------------------------------------------------------------------------------------|
| `TASK_ID`        | `NUMBER`        |      | Number that uniquely identifies a specific automatic IM column store management task |
| `OBJECT_OWNER`   | `VARCHAR2(128)` |      | Owner of the object subject to automatic IM column store management task action      |
| `OBJECT_NAME`    | `VARCHAR2(128)` |      | Name of the object subject to automatic IM column store management task action       |
| `SUBOBJECT_NAME` | `VARCHAR2(128)` |      | Name of the subobject subject to automatic IM column store management task action    |
| `ACTION`         | `VARCHAR2(16)`  |      | Action taken on the object                                                           |
| `STATE`          | `VARCHAR2(10)`  |      | Status of the action on the object                                                   |

**See Also:**

[Oracle Database In-Memory Guide](../inmem/configuring-memory-management.md) for more information about configuring the Automatic In-Memory feature
