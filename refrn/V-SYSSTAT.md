## 9.98 V\$SYSSTAT

`V$SYSSTAT` displays system statistics. To find the name of the statistic associated with each statistic number (`STATISTIC#`), query the `V$STATNAME` view.

| Column       | Datatype       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `STATISTIC#` | `NUMBER`       | Statistic number<br>Note: Statistics numbers are not guaranteed to remain constant from one release to another. Therefore, you should rely on the statistics name rather than its number in your applications.                                                                                                                                                                   |
| `NAME`       | `VARCHAR2(64)` | Statistic name. You can get a complete listing of statistic names by querying the `V$STATNAME` view.                                                                                                                                                                                                                                                                             |
| `CLASS`      | `NUMBER`       | A number representing one or more statistics class. The following class numbers are additive:<br>• `1` - User<br>• `2` - Redo<br>• `4` - Enqueue<br>• `8` - Cache<br>• `16` - OS<br>• `32` - Real Application Clusters<br>• `64` - SQL<br>• `128` - Debug                                                                                                                        |
| `VALUE`      | `NUMBER`       | Statistic value                                                                                                                                                                                                                                                                                                                                                                  |
| `STAT_ID`    | `NUMBER`       | Identifier of the statistic                                                                                                                                                                                                                                                                                                                                                      |
| `CON_ID`     | `NUMBER`       | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**Note:**

This view returns instance-wide data and a value of `0` in the `CON_ID` column when queried from the root of a CDB.

**See Also:**

"[V\$STATNAME](V-STATNAME.md)" and "[Statistics Descriptions](statistics-descriptions.md)"
