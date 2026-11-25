## 4.36 DBA_ADVISOR_SQLA_WK_MAP

`DBA_ADVISOR_SQLA_WK_MAP` displays the workload references for all tasks in the database.

Workload references are necessary to allow the SQL Access Advisor to find required workload data.

### Related View

`USER_ADVISOR_SQLA_WK_MAP` displays the workload references for the tasks owned by the current user. This view does not display the `OWNER` column.

| Column          | Datatype        | NULL | Description                                                                       |
|:----------------|:----------------|:-----|:----------------------------------------------------------------------------------|
| `OWNER`         | `VARCHAR2(128)` |      | Owner of the task                                                                 |
| `TASK_ID`       | `NUMBER`        |      | Unique identifier of the task                                                     |
| `TASK_NAME`     | `VARCHAR2(128)` |      | Name of the task                                                                  |
| `WORKLOAD_ID`   | `NUMBER`        |      | Unique identifier of the workload object                                          |
| `WORKLOAD_NAME` | `VARCHAR2(128)` |      | Name of the workload                                                              |
| `IS_STS`        | `NUMBER`        |      | Type of workload source:<br>• `0` - SQL workload object<br>• `1` - SQL Tuning Set |

**See Also:**

"[USER_ADVISOR_SQLA_WK_MAP](USER_ADVISOR_SQLA_WK_MAP.md)"
