## 5.377 DBA_SQLTUNE_BINDS

`DBA_SQLTUNE_BINDS` displays the bind values associated with all tuned SQL statements in the database.

### Related View

`USER_SQLTUNE_BINDS` displays the bind values associated with the tuned SQL statements owned by the current user.

| Column      | Datatype     | NULL       | Description                                              |
|:------------|:-------------|:-----------|:---------------------------------------------------------|
| `TASK_ID`   | `NUMBER(38)` | `NOT NULL` | Tuning task identifier                                   |
| `OBJECT_ID` | `NUMBER(38)` | `NOT NULL` | Advisor framework object identifier                      |
| `POSITION`  | `NUMBER(38)` | `NOT NULL` | Bind position                                            |
| `VALUE`     | `ANYDATA`    |            | Bind value. This column is `NULL` for PL/SQL bind types. |

**See Also:**

"[USER_SQLTUNE_BINDS](USER_SQLTUNE_BINDS.md)"
