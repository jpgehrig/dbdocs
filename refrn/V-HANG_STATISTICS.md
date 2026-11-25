## 7.267 V\$HANG_STATISTICS

`V$HANG_STATISTICS` displays statistics about hangs found on the cluster.

| Column       | Datatype       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `STATISTIC#` | `NUMBER`       | Statistic number                                                                                                                                                                                                                                                                                                                                                                 |
| `NAME`       | `VARCHAR2(45)` | Name of the statistic                                                                                                                                                                                                                                                                                                                                                            |
| `VALUE`      | `NUMBER`       | Value associated with the statistic                                                                                                                                                                                                                                                                                                                                              |
| `CON_ID`     | `NUMBER`       | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[V\$HANG_INFO](V-HANG_INFO.md)"

- "[V\$HANG_SESSION_INFO](V-HANG_SESSION_INFO.md)"

- "[DBA_HANG_MANAGER_PARAMETERS](DBA_HANG_MANAGER_PARAMETERS.md)"
