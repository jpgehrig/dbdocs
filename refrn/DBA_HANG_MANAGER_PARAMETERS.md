## 4.324 DBA_HANG_MANAGER_PARAMETERS

`DBA_HANG_MANAGER_PARAMETERS` shows the available user tunable Hang Manager parameters and their values.

| Column           | Datatype       | NULL       | Description                                                           |
|:-----------------|:---------------|:-----------|:----------------------------------------------------------------------|
| `NAME`           | `VARCHAR2(40)` | `NOT NULL` | String representation of the parameter names                          |
| `CURRENT_VALUE`  | `VARCHAR2(20)` |            | String representation of the parameter values                         |
| `CURRENT_TIME`   | `DATE`         |            | Time when the current value was set                                   |
| `PREVIOUS_VALUE` | `VARCHAR2(20)` |            | String representation of the parameter value from the previous update |
| `PREVIOUS_TIME`  | `DATE`         |            | Time when the previous value was set                                  |

**Note:**

- "[V\$HANG_INFO](V-HANG_INFO.md)"

- "[V\$HANG_SESSION_INFO](V-HANG_SESSION_INFO.md)"

- "[V\$HANG_STATISTICS](V-HANG_STATISTICS.md)"
