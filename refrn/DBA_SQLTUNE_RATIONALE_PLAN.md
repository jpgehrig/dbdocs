## 5.379 DBA_SQLTUNE_RATIONALE_PLAN

`DBA_SQLTUNE_RATIONALE_PLAN` displays the association between rationales and operations in the execution plan of all SQL statements in the database.

### Related View

`USER_SQLTUNE_RATIONALE_PLAN` displays the association between rationales and operations in the execution plan of the SQL statements owned by the current user.

| Column           | Datatype        | NULL       | Description                                                                                                                                                                                                                                                           |
|:-----------------|:----------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TASK_ID`        | `NUMBER(38)`    | `NOT NULL` | Tuning task identifier                                                                                                                                                                                                                                                |
| `EXECUTION_NAME` | `VARCHAR2(128)` | `NOT NULL` | The name of the task execution with which this entry (row) is associated                                                                                                                                                                                              |
| `RATIONALE_ID`   | `NUMBER(38)`    | `NOT NULL` | Rationale identifier                                                                                                                                                                                                                                                  |
| `OBJECT_ID`      | `NUMBER(38)`    | `NOT NULL` | Advisor framework object identifier                                                                                                                                                                                                                                   |
| `OPERATION_ID`   | `NUMBER(38)`    | `NOT NULL` | Operation identifier                                                                                                                                                                                                                                                  |
| `PLAN_ATTRIBUTE` | `VARCHAR2(34)`  |            | Type of the execution plan:<br>• `Original` - Original plan of the query<br>• `Original with adjusted cost` - Same as `Original` but with adjusted cost<br>• `Using SQL profile` - Plan with SQL profile applied<br>• `Using new indices` - Plan with indexes applied |

**See Also:**

"[USER_SQLTUNE_RATIONALE_PLAN](USER_SQLTUNE_RATIONALE_PLAN.md)"
