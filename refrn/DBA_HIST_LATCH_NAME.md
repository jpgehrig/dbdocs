## 5.4 DBA_HIST_LATCH_NAME

`DBA_HIST_LATCH_NAME` displays information about decoded latch names for the latches shown in `DBA_HIST_LATCH`.

This view contains a snapshot of `V$LATCHNAME`.

| Column       | Datatype       | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------|:---------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBID`       | `NUMBER`       | `NOT NULL` | Database ID                                                                                                                                                                                                                                                                                                                                                                      |
| `LATCH_HASH` | `NUMBER`       | `NOT NULL` | Latch hash                                                                                                                                                                                                                                                                                                                                                                       |
| `LATCH_NAME` | `VARCHAR2(64)` | `NOT NULL` | Latch name                                                                                                                                                                                                                                                                                                                                                                       |
| `CON_DBID`   | `NUMBER`       |            | The database ID of the PDB for the sampled session                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`     | `NUMBER`       |            | The ID of the container that `CON_DBID` identifies. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[DBA_HIST_LATCH](DBA_HIST_LATCH.md)"

- "[V\$LATCHNAME](V-LATCHNAME.md)"
