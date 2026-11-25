## 9.95 V\$SYSMETRIC

`V$SYSMETRIC` displays the system metric values captured for the most current time interval for both the long duration (60-second) and short duration (15-second) system metrics.

| Column         | Datatype       | Description                                                                                                                                                                                                                                                                                  |
|:---------------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BEGIN_TIME`   | `DATE`         | Begin time of the interval                                                                                                                                                                                                                                                                   |
| `END_TIME`     | `DATE`         | End time of the interval                                                                                                                                                                                                                                                                     |
| `INTSIZE_CSEC` | `NUMBER`       | Interval size (in hundredths of a second)                                                                                                                                                                                                                                                    |
| `GROUP_ID`     | `NUMBER`       | Metric group ID                                                                                                                                                                                                                                                                              |
| `METRIC_ID`    | `NUMBER`       | Metric ID                                                                                                                                                                                                                                                                                    |
| `METRIC_NAME`  | `VARCHAR2(64)` | Metric name                                                                                                                                                                                                                                                                                  |
| `VALUE`        | `NUMBER`       | Metric value                                                                                                                                                                                                                                                                                 |
| `METRIC_UNIT`  | `VARCHAR2(64)` | Metric unit description                                                                                                                                                                                                                                                                      |
| `CON_ID`       | `NUMBER`       | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[DBA_HIST_SYS_TIME_MODEL](DBA_HIST_SYS_TIME_MODEL.md)"

- "[V\$CON_SYSMETRIC](V-CON_SYSMETRIC.md)"

- "[DBA_HIST_CON_SYS_TIME_MODEL](DBA_HIST_CON_SYS_TIME_MODEL.md)"
