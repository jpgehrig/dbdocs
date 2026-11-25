## 4.391 DBA_HIST_IOSTAT_FUNCTION_NAME

`DBA_HIST_IOSTAT_FUNCTION_NAME` displays historical I/O statistics by function names.

This view contains snapshots of `V$IOSTAT_FUNCTION`.

| Column          | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBID`          | `NUMBER`        | `NOT NULL` | Database ID for the snapshot                                                                                                                                                                                                                                                                                                                                                     |
| `FUNCTION_ID`   | `NUMBER`        | `NOT NULL` | Function ID                                                                                                                                                                                                                                                                                                                                                                      |
| `FUNCTION_NAME` | `VARCHAR2(128)` | `NOT NULL` | Function name                                                                                                                                                                                                                                                                                                                                                                    |
| `CON_DBID`      | `NUMBER`        |            | The database ID of the PDB for the sampled session                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`        | `NUMBER`        |            | The ID of the container that `CON_DBID` identifies. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[V\$IOSTAT_FUNCTION](V-IOSTAT_FUNCTION.md)"
