## 5.68 DBA_HIST_STAT_NAME

`DBA_HIST_STAT_NAME` displays decoded statistic names for the statistics captured in the Workload Repository.

This includes OLAP statisitics and OLAP timed events. This view captures information from `V$STATNAME` and is used with `DBA_HIST_SYSSTAT` and `DBA_HIST_SYS_TIME_MODEL`.

| Column      | Datatype       | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:------------|:---------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBID`      | `NUMBER`       | `NOT NULL` | Database ID                                                                                                                                                                                                                                                                                                                                                                      |
| `STAT_ID`   | `NUMBER`       | `NOT NULL` | Statistic identifier                                                                                                                                                                                                                                                                                                                                                             |
| `STAT_NAME` | `VARCHAR2(64)` | `NOT NULL` | Statistic name                                                                                                                                                                                                                                                                                                                                                                   |
| `CON_DBID`  | `NUMBER`       |            | The database ID of the PDB for the sampled session                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`    | `NUMBER`       |            | The ID of the container that `CON_DBID` identifies. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[V\$STATNAME](V-STATNAME.md)"

- "[DBA_HIST_SYSSTAT](DBA_HIST_SYSSTAT.md)"

- "[DBA_HIST_SYS_TIME_MODEL](DBA_HIST_SYS_TIME_MODEL.md)"
