## 4.389 DBA_HIST_IOSTAT_FILETYPE_NAME

`DBA_HIST_IOSTAT_FILETYPE_NAME` displays historical I/O statistics for file type names.

This view contains snapshots of `V$IOSTAT_FILE`.

| Column          | Datatype       | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------|:---------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBID`          | `NUMBER`       | `NOT NULL` | Database ID for the snapshot                                                                                                                                                                                                                                                                                                                                                     |
| `FILETYPE_ID`   | `NUMBER`       | `NOT NULL` | Type of file (for example, log file, data file, and so on)                                                                                                                                                                                                                                                                                                                       |
| `FILETYPE_NAME` | `VARCHAR2(30)` | `NOT NULL` | Name of the file, in the case of a data file or temp file. For all other files, a corresponding string to be displayed (for example, `ARCHIVELOG`).                                                                                                                                                                                                                              |
| `CON_DBID`      | `NUMBER`       |            | The database ID of the PDB for the sampled session                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`        | `NUMBER`       |            | The ID of the container that `CON_DBID` identifies. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[V\$IOSTAT_FILE](V-IOSTAT_FILE.md)"
