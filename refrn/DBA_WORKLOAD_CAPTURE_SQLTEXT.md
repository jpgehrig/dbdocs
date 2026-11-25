## 6.116 DBA_WORKLOAD_CAPTURE_SQLTEXT

`DBA_WORKLOAD_CAPTURE_SQLTEXT` displays all the SQL statements that have been recorded in a workload capture. For those SQL statements whose length exceeds 1000 characters, the full statements can be loaded to the `DBA_WORKLOAD_LONG_SQLTEXT` view using the `DBMS_WORKLOAD_REPLAY.LOAD_LONG_SQLTEXT` procedure.

| Column              | Datatype         | NULL       | Description                                                                                                                                                                                                                                                                   |
|:--------------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CAPTURE_ID`        | `NUMBER(38)`     | `NOT NULL` | Internal key for the workload capture                                                                                                                                                                                                                                         |
| `SQL_ID`            | `VARCHAR2(13)`   | `NOT NULL` | SQL identifier of the parent cursor in the library cache                                                                                                                                                                                                                      |
| `SQL_TYPE`          | `VARCHAR2(64)`   |            | Type of the SQL statement, which can include values such as `INSERT`, `SELECT`, and `CREATE INDEX`                                                                                                                                                                            |
| `SQL_TEXT`          | `VARCHAR2(1000)` |            | First thousand characters of the SQL text for the current cursor                                                                                                                                                                                                              |
| `SQL_LENGTH`        | `NUMBER(38)`     |            | The length of the SQL statement                                                                                                                                                                                                                                               |
| `SQL_TEXT_COMPLETE` | `CHAR(1)`        |            | Indicates whether the `SQL_TEXT` column includes the full text of the SQL statement. Possible values:<br>• `Y`: The column `SQL_TEXT` includes the full text of the SQL statement<br>• `N`: The column `SQL_TEXT` contains only the first thousand characters of the SQL text |

**See Also:**

- "[DBA_WORKLOAD_LONG_SQLTEXT](DBA_WORKLOAD_LONG_SQLTEXT.md)"

- "[DBA_RAT_CAPTURE_SCHEMA_INFO](DBA_RAT_CAPTURE_SCHEMA_INFO.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_WORKLOAD_REPLAY.md) for information about the `DBMS_WORKLOAD_REPLAY` package
