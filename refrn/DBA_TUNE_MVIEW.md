## 6.69 DBA_TUNE_MVIEW

`DBA_TUNE_MVIEW` displays the result of executing the `DBMS_ADVISOR.TUNE_MVIEW` procedure.

### Related View

`USER_TUNE_MVIEW` displays the result of executing the `DBMS_ADVISOR.TUNE_MVIEW` procedure. This view does not display the `OWNER` column.

| Column        | Datatype        | NULL       | Description                                           |
|:--------------|:----------------|:-----------|:------------------------------------------------------|
| `OWNER`       | `VARCHAR2(128)` |            | Owner of the task                                     |
| `TASK_NAME`   | `VARCHAR2(128)` |            | Name of the task                                      |
| `ACTION_ID`   | `NUMBER`        | `NOT NULL` | Identifier of the action                              |
| `SCRIPT_TYPE` | `VARCHAR2(14)`  |            | Type of the script:<br>• `IMPLEMENTATION`<br>• `UNDO` |
| `STATEMENT`   | `CLOB`          |            | Action statement                                      |

**See Also:**

- "[USER_TUNE_MVIEW](USER_TUNE_MVIEW.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ADVISOR.md) for more information about the `DBMS_ADVISOR.TUNE_MVIEW` procedure
