## 4.20 DBA_ADVISOR_DIR_TASK_INST

`DBA_ADVISOR_DIR_TASK_INST` provides information about all task directive instances.

### Related View

`USER_ADVISOR_DIR_TASK_INST` provides information about all task directive instances owned by the current user.

| Column          | Datatype        | NULL       | Description                                                                                               |
|:----------------|:----------------|:-----------|:----------------------------------------------------------------------------------------------------------|
| `DIRECTIVE_ID`  | `NUMBER`        | `NOT NULL` | Unique id for directive. The directive management engine automatically generates ID numbers.              |
| `SEQ_ID`        | `NUMBER`        | `NOT NULL` | Unique id for the directive instance. The directive management engine automatically generates ID numbers. |
| `INSTANCE_NAME` | `VARCHAR2(128)` | `NOT NULL` | A user-assigned name for the directive instance.                                                          |
| `USERNAME`      | `VARCHAR2(128)` | `NOT NULL` | Database user who owns the task instance.                                                                 |
| `TASK_ID`       | `NUMBER`        |            | An advisor task identifier to which the directive instance is associated                                  |
| `TASK_NAME`     | `VARCHAR2(128)` |            | An advisor task to which the directive instance is associated.                                            |
| `DATA`          | `CLOB`          | `NOT NULL` | An XML document that gives meaningful default values for all parts of the directive.                      |

**See Also:**

"[USER_ADVISOR_DIR_TASK_INST](USER_ADVISOR_DIR_TASK_INST.md)"
