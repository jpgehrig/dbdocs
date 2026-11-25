## 4.24 DBA_ADVISOR_FDG_BREAKDOWN

`DBA_ADVISOR_FDG_BREAKDOWN` describes the contribution from the different instances to the findings for each ADDM task.

This view is populated only with ADDM tasks that are analyzing multiple instances (that is, the `ACTUAL_ANALYSIS` column in the task's row in `DBA_ADDM_TASKS` is set to `DATABASE` or `PARTIAL`).

### Related View

`USER_ADVISOR_FDG_BREAKDOWN` describes the contribution from the different instances to the findings for each ADDM task owned by the current user.

| Column            | Datatype        | NULL       | Description                                                                                                    |
|:------------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------|
| `TASK_ID`         | `NUMBER`        | `NOT NULL` | Unique identifier of the task (see `DBA_ADVISOR_TASKS` and `DBA_ADDM_TASKS`)                                   |
| `FINDING_ID`      | `NUMBER`        | `NOT NULL` | Identifier of the finding to which this breakdown applies (see `DBA_ADVISOR_FINDINGS` and `DBA_ADDM_FINDINGS`) |
| `INSTANCE_NUMBER` | `NUMBER`        | `NOT NULL` | The number of the instance for the breakdown                                                                   |
| `IMPACT`          | `NUMBER`        |            | The database time (in microseconds) of the finding in the instance                                             |
| `PERC_IMPACT`     | `NUMBER`        |            | Percentage of the contribution of the instance to the overall finding's impact                                 |
| `EXECUTION_NAME`  | `VARCHAR2(128)` |            | The name of the task execution with which this entry (row) is associated                                       |

**See Also:**

"[USER_ADVISOR_FDG_BREAKDOWN](USER_ADVISOR_FDG_BREAKDOWN.md)"
