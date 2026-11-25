## 6.122 DBA_WORKLOAD_LONG_SQLTEXT

`DBA_WORKLOAD_LONG_SQLTEXT` displays the captured SQL statements that are longer than 1000 characters. You can load SQL statements longer than 1000 characters to the `DBA_WORKLOAD_LONG_SQLTEXT` view using the `DBMS_WORKLOAD_REPLAY.LOAD_LONG_SQLTEXT` procedure.

| Column         | Datatype       | NULL       | Description                                              |
|:---------------|:---------------|:-----------|:---------------------------------------------------------|
| `CAPTURE_ID`   | `NUMBER(38)`   | `NOT NULL` | Internal key for the workload capture                    |
| `SQL_ID`       | `VARCHAR2(13)` | `NOT NULL` | SQL identifier of the parent cursor in the library cache |
| `SQL_FULLTEXT` | `CLOB`         |            | Full text for the SQL statement exposed as a CLOB column |

**See Also:**

- "[DBA_WORKLOAD_CAPTURE_SQLTEXT](DBA_WORKLOAD_CAPTURE_SQLTEXT.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_WORKLOAD_REPLAY.md) for information about the `DBMS_WORKLOAD_REPLAY` package
