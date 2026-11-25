## 9.6 V\$SERV_MOD_ACT_STATS

`V$SERV_MOD_ACT_STATS` displays the same set of performance statistics as `V$SERVICE_STATS` except for a specific combination of service/module/action names.

When aggregation is enabled for the service name, module, and action name, then this view provides the timing and work done for calls issued for the business transaction.

| Column             | Datatype       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AGGREGATION_TYPE` | `VARCHAR2(21)` | Aggregation statistic type:<br>• `SERVICE_MODULE` - Action value is NULL and the entry is an aggregate for all actions within a given module<br>• `SERVICE_MODULE_ACTION` - Action value is NULL only for an empty action, and the aggregation is on the level of service/module/action                                                                                          |
| `SERVICE_NAME`     | `VARCHAR2(64)` | Service name from `V$SERVICES`                                                                                                                                                                                                                                                                                                                                                   |
| `MODULE`           | `VARCHAR2(65)` | Module name from `DBA_ENABLED_AGGREGATIONS`                                                                                                                                                                                                                                                                                                                                      |
| `ACTION`           | `VARCHAR2(65)` | Action name from `DBA_ENABLED_AGGREGATIONS`                                                                                                                                                                                                                                                                                                                                      |
| `STAT_ID`          | `NUMBER`       | Statistic identifier                                                                                                                                                                                                                                                                                                                                                             |
| `STAT_NAME`        | `VARCHAR2(64)` | Derived statistic name from `V$STATNAME` and `V$SESS_TIME_MODEL`                                                                                                                                                                                                                                                                                                                 |
| `VALUE`            | `NUMBER`       | Cumulative value (in microseconds)                                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`           | `NUMBER`       | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[V\$SERVICE_STATS](V-SERVICE_STATS.md)"

- "[V\$STATNAME](V-STATNAME.md)"

- "[V\$SESS_TIME_MODEL](V-SESS_TIME_MODEL.md)"
