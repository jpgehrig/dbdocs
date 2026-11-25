## 4.35 DBA_ADVISOR_SQLA_TABLES

`DBA_ADVISOR_SQLA_TABLES` displays cross references between the workload statements and the tables referenced in the statement.

### Related View

`USER_ADVISOR_SQLA_TABLES` displays cross references between the workload statements and the tables referenced in the statement for the current user. This view does not display the `OWNER` column.

| Column        | Datatype        | NULL | Description                                              |
|:--------------|:----------------|:-----|:---------------------------------------------------------|
| `OWNER`       | `VARCHAR2(128)` |      | Owner of the workload object                             |
| `TASK_ID`     | `NUMBER`        |      | Unique identifier of the task                            |
| `TASK_NAME`   | `VARCHAR2(128)` |      | Name of the task                                         |
| `SQL_ID`      | `VARCHAR2(13)`  |      | SQL identifier of the parent cursor in the library cache |
| `STMT_ID`     | `NUMBER`        |      | Statement ID                                             |
| `TABLE_OWNER` | `VARCHAR2(128)` |      | Owner of the table                                       |
| `TABLE_NAME`  | `VARCHAR2(128)` |      | Table name                                               |

**See Also:**

"[USER_ADVISOR_SQLA_TABLES](USER_ADVISOR_SQLA_TABLES.md)"
