## 7.133 V\$CLIENT_STATS

`V$CLIENT_STATS` displays measures for all sessions that are active for the client identifier per instance.

The statistics available in this view are a subset of those available in `V$SESSTAT` and `V$SESS_TIME_MODEL`.

| Column              | Datatype       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CLIENT_IDENTIFIER` | `VARCHAR2(64)` | Client identifier                                                                                                                                                                                                                                                                                                                                                                |
| `STAT_ID`           | `NUMBER`       | Statistic identifier                                                                                                                                                                                                                                                                                                                                                             |
| `STAT_NAME`         | `VARCHAR2(64)` | Derived statistic name from `V$STATNAME` and `V$SESS_TIME_MODEL`                                                                                                                                                                                                                                                                                                                 |
| `VALUE`             | `NUMBER`       | Cumulative value (in microseconds)                                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`            | `NUMBER`       | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[V\$SESSTAT](V-SESSTAT.md)"

- "[V\$SESS_TIME_MODEL](V-SESS_TIME_MODEL.md)"
