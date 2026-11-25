## 9.56 V\$SQL_MONITOR_SESSTAT

`V$SQL_MONITOR_SESSTAT` displays information about statistics that are exposed in `V$SESSTAT`.

| Column       | Datatype | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------|:---------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CON_ID`     | `NUMBER` | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |
| `KEY`        | `NUMBER` | Artificial join key to efficiently join with other database operation views                                                                                                                                                                                                                                                                                                      |
| `STATISTIC#` | `NUMBER` | Statistic number                                                                                                                                                                                                                                                                                                                                                                 |
| `VALUE`      | `NUMBER` | Value associated with the statistic                                                                                                                                                                                                                                                                                                                                              |

**See Also:**

"[V\$SESSTAT](V-SESSTAT.md)"
