## 9.83 V\$STATNAME

`V$STATNAME` displays decoded statistic names for the statistics shown in the `V$SESSTAT` and `V$SYSSTAT` tables.

On some platforms, the `NAME` and `CLASS` columns contain additional operating system-specific statistics.

| Column         | Datatype       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `STATISTIC#`   | `NUMBER`       | Statistic number<br>Note: Statistics numbers are not guaranteed to remain constant from one release to another. Therefore, you should rely on the statistics name rather than its number in your applications.                                                                                                                                                                   |
| `NAME`         | `VARCHAR2(64)` | Statistic name. Names that appear in this column remain stable across Oracle Database releases, and they can be relied on by customer scripts.                                                                                                                                                                                                                                   |
| `CLASS`        | `NUMBER`       | A number representing one or more statistics classes. The following class numbers are additive:<br>• `1` - User<br>• `2` - Redo<br>• `4` - Enqueue<br>• `8` - Cache<br>• `16` - OS<br>• `32` - Real Application Clusters<br>• `64` - SQL<br>• `128` - Debug                                                                                                                      |
| `STAT_ID`      | `NUMBER`       | Identifier of the statistic                                                                                                                                                                                                                                                                                                                                                      |
| `DISPLAY_NAME` | `VARCHAR2(64)` | A clearer and more descriptive name for the statistic that appears in the `NAME` column. Names that appear in the `DISPLAY_NAME` column can change across Oracle Database releases, therefore customer scripts should not rely on names that appear in the `DISPLAY_NAME` column across releases.                                                                                |
| `CON_ID`       | `NUMBER`       | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[V\$SESSTAT](V-SESSTAT.md)" and "[V\$SYSSTAT](V-SYSSTAT.md)"

- "[Statistics Descriptions](statistics-descriptions.md)" for statistic descriptions

- Your operating system-specific Oracle documentation
