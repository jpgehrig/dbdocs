## 1.61 CREATE_BITMAP_AREA_SIZE

`CREATE_BITMAP_AREA_SIZE` specifies the amount of memory (in bytes) allocated for bitmap creation.

| Property            | Description                |
|:--------------------|:---------------------------|
| Parameter type      | Integer                    |
| Default value       | `0`                        |
| Modifiable          | No                         |
| Modifiable in a PDB | Yes                        |
| Range of values     | Operating system-dependent |
| Basic               | No                         |

This parameter is relevant only for systems containing bitmap indexes.

**Note:**

Oracle does not recommend using the `CREATE_BITMAP_AREA_SIZE` parameter unless the instance is configured with the shared server option. Oracle recommends that you enable automatic sizing of SQL working areas by setting `PGA_AGGREGATE_TARGET` instead. `CREATE_BITMAP_AREA_SIZE` is retained for backward compatibility.

A larger value may speed up index creation.

Cardinality is the number of unique values in a column in relation to the number of rows in the table. If cardinality is very small, you can set a small value for this parameter. For example, if cardinality is only 2, then the value can be in kilobytes rather than megabytes. As a general rule, the higher the cardinality, the more memory is needed for optimal performance.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/optimizer-access-paths.md) for more information on using bitmap indexes
