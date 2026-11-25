## 5.67 DBA_HIST_SQLTEXT

`DBA_HIST_SQLTEXT` displays the text of SQL statements belonging to shared SQL cursors captured in the Workload Repository.

This view captures information from `V$SQL` and is used with the `DBA_HIST_SQLSTAT` view.

| Column         | Datatype       | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:---------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBID`         | `NUMBER`       | `NOT NULL` | Database ID                                                                                                                                                                                                                                                                                                                                                                      |
| `SQL_ID`       | `VARCHAR2(13)` | `NOT NULL` | SQL identifier of the parent cursor in the library cache                                                                                                                                                                                                                                                                                                                         |
| `SQL_TEXT`     | `CLOB`         |            | Full text for the SQL statement exposed as a CLOB column                                                                                                                                                                                                                                                                                                                         |
| `COMMAND_TYPE` | `NUMBER`       |            | Oracle command type definition                                                                                                                                                                                                                                                                                                                                                   |
| `CON_DBID`     | `NUMBER`       |            | The database ID of the PDB for the sampled session                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`       | `NUMBER`       |            | The ID of the container that `CON_DBID` identifies. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[V\$SQL](V-SQL.md)"

- "[DBA_HIST_SQLSTAT](DBA_HIST_SQLSTAT.md)"
