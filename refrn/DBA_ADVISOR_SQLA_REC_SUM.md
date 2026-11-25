## 4.34 DBA_ADVISOR_SQLA_REC_SUM

`DBA_ADVISOR_SQLA_REC_SUM` displays recommendation rollup information for all workload objects in the database after an Access Advisor analysis operation.

### Related View

`USER_ADVISOR_SQLA_REC_SUM` displays recommendation rollup information for the workload objects owned by the current user. This view does not display the `OWNER` column.

| Column           | Datatype        | NULL | Description                                                                                                                              |
|:-----------------|:----------------|:-----|:-----------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` |      | Owner of the task                                                                                                                        |
| `TASK_ID`        | `NUMBER`        |      | Unique identifier of the task                                                                                                            |
| `TASK_NAME`      | `VARCHAR2(128)` |      | Name of the task                                                                                                                         |
| `REC_ID`         | `NUMBER`        |      | Identifier of the recommendation                                                                                                         |
| `TOTAL_STMTS`    | `NUMBER`        |      | Total number of statements processed during analysis                                                                                     |
| `TOTAL_PRECOST`  | `NUMBER`        |      | Total cost of executing the statements in which the recommended object will be used, before the recommendations                          |
| `TOTAL_POSTCOST` | `NUMBER`        |      | Total cost of executing the statements in which the recommended object will be utilized, after the recommendations have been implemented |

**See Also:**

"[USER_ADVISOR_SQLA_REC_SUM](USER_ADVISOR_SQLA_REC_SUM.md)"
