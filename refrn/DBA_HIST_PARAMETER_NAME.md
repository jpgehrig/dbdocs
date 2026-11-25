## 5.18 DBA_HIST_PARAMETER_NAME

`DBA_HIST_PARAMETER_NAME` displays information about the parameter names captured in the workload repository.

This view is used with the `DBA_HIST_PARAMETER` view.

| Column           | Datatype       | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------|:---------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBID`           | `NUMBER`       | `NOT NULL` | Database ID                                                                                                                                                                                                                                                                                                                                                                      |
| `PARAMETER_HASH` | `NUMBER`       | `NOT NULL` | Parameter hash                                                                                                                                                                                                                                                                                                                                                                   |
| `PARAMETER_NAME` | `VARCHAR2(64)` | `NOT NULL` | Name of the parameter                                                                                                                                                                                                                                                                                                                                                            |
| `CON_DBID`       | `NUMBER`       |            | The database ID of the PDB for the sampled session                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`         | `NUMBER`       |            | The ID of the container that `CON_DBID` identifies. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[DBA_HIST_PARAMETER](DBA_HIST_PARAMETER.md)"
