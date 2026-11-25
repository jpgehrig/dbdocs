## 5.16 DBA_HIST_OSSTAT_NAME

`DBA_HIST_OSSTAT_NAME` displays the names of the operating system statistics.

This view is used with `DBA_HIST_OSSTAT`.

| Column      | Datatype       | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:------------|:---------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBID`      | `NUMBER`       | `NOT NULL` | Database ID                                                                                                                                                                                                                                                                                                                                                                      |
| `STAT_ID`   | `NUMBER`       | `NOT NULL` | Statistic ID                                                                                                                                                                                                                                                                                                                                                                     |
| `STAT_NAME` | `VARCHAR2(64)` | `NOT NULL` | Statistic name                                                                                                                                                                                                                                                                                                                                                                   |
| `CON_DBID`  | `NUMBER`       |            | The database ID of the PDB for the sampled session                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`    | `NUMBER`       |            | The ID of the container that `CON_DBID` identifies. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[DBA_HIST_OSSTAT](DBA_HIST_OSSTAT.md)"
