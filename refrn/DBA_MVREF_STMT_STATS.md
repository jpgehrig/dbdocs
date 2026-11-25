## 5.203 DBA_MVREF_STMT_STATS

`DBA_MVREF_STMT_STATS` shows information associated with each refresh statement of a materialized view in a refresh run.

### Related View

`USER_MVREF_STMT_STATS` shows information associated with each refresh statement of a materialized view accessible to the current user in a refresh run.

| Column           | Datatype                 | NULL       | Description                                                                                                                                                       |
|:-----------------|:-------------------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MV_OWNER`       | `VARCHAR2(128)`          | `NOT NULL` | Owner of the materialized view                                                                                                                                    |
| `MV_NAME`        | `VARCHAR2(128)`          | `NOT NULL` | Name of the materialized view                                                                                                                                     |
| `REFRESH_ID`     | `NUMBER`                 | `NOT NULL` | The refresh ID of the refresh run                                                                                                                                 |
| `STEP`           | `NUMBER`                 | `NOT NULL` | A number indicating the step in the refresh process in which the statement is executed for the materialized view. Steps are numbered consecutively starting at 1. |
| `SQLID`          | `VARCHAR2(14)`           | `NOT NULL` | The SQL ID of the statement                                                                                                                                       |
| `STMT`           | `CLOB`                   | `NOT NULL` | The text of the SQL statement                                                                                                                                     |
| `EXECUTION_TIME` | `NUMBER`                 | `NOT NULL` | The time it took to execute the statement (in seconds)                                                                                                            |
| `EXECUTION_PLAN` | `XMLTYPE STORAGE BINARY` |            | For internal use only                                                                                                                                             |

**See Also:**

"[USER_MVREF_STMT_STATS](USER_MVREF_STMT_STATS.md)"
