## 1.34 BITMAP_MERGE_AREA_SIZE

`BITMAP_MERGE_AREA_SIZE` specifies the amount of memory Oracle uses to merge bitmaps retrieved from a range scan of the index.

| Property            | Description                |
|:--------------------|:---------------------------|
| Parameter type      | Integer                    |
| Default value       | `1048576` (1 MB)           |
| Modifiable          | No                         |
| Modifiable in a PDB | Yes                        |
| Range of values     | Operating system-dependent |
| Basic               | No                         |

**Note:**

Oracle does not recommend using the `BITMAP_MERGE_AREA_SIZE` parameter unless the instance is configured with the shared server option. Oracle recommends that you enable automatic sizing of SQL working areas by setting `PGA_AGGREGATE_TARGET` instead. `BITMAP_MERGE_AREA_SIZE` is retained for backward compatibility.

`BITMAP_MERGE_AREA_SIZE` is relevant only for systems containing bitmap indexes. A larger value usually improves performance, because the bitmap segments must be sorted before being merged into a single bitmap.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/optimizer-access-paths.md) for more information on using bitmap indexes for performance
