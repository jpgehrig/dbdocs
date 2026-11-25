## 9.30 V\$SESSTAT

`V$SESSTAT` displays user session statistics. To find the name of the statistic associated with each statistic number (`STATISTIC#`), query the `V$STATNAME` view.

| Column       | Datatype | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------|:---------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SID`        | `NUMBER` | Session identifier                                                                                                                                                                                                                                                                                                                                                               |
| `STATISTIC#` | `NUMBER` | Statistic number<br>Note: Statistics numbers are not guaranteed to remain constant from one release to another. Therefore, you should rely on the statistics name rather than its number in your applications.                                                                                                                                                                   |
| `VALUE`      | `NUMBER` | Statistic value                                                                                                                                                                                                                                                                                                                                                                  |
| `CON_ID`     | `NUMBER` | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[V\$STATNAME](V-STATNAME.md)" and "[Statistics Descriptions](statistics-descriptions.md)"
