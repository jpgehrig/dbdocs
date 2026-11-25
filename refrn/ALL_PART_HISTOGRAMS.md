## 3.2 ALL_PART_HISTOGRAMS

`ALL_PART_HISTOGRAMS` displays the histogram data (endpoints per histogram) for the histograms on the table partitions accessible to the current user.

### Related Views

- `DBA_PART_HISTOGRAMS` displays the histogram data for the histograms on all table partitions in the database.

- `USER_PART_HISTOGRAMS` displays the histogram data for the histograms on the table partitions owned by the current user. This view does not display the `OWNER` column.

**Note:**

These views are populated only if you collect statistics on the index using the `DBMS_STATS` package.

| Column                      | Datatype         | NULL | Description                                                                                              |
|:----------------------------|:-----------------|:-----|:---------------------------------------------------------------------------------------------------------|
| `OWNER`                     | `VARCHAR2(128)`  |      | Owner of the table                                                                                       |
| `TABLE_NAME`                | `VARCHAR2(128)`  |      | Name of the table                                                                                        |
| `PARTITION_NAME`            | `VARCHAR2(128)`  |      | Name of the table partition                                                                              |
| `COLUMN_NAME`               | `VARCHAR2(4000)` |      | Name of the column                                                                                       |
| `BUCKET_NUMBER`             | `NUMBER`         |      | Bucket number of the histogram                                                                           |
| `ENDPOINT_VALUE`            | `NUMBER`         |      | Normalized endpoint values for the bucket                                                                |
| `ENDPOINT_ACTUAL_VALUE`     | `VARCHAR2(4000)` |      | Actual (not normalized) string value of the endpoint for the bucket                                      |
| `ENDPOINT_ACTUAL_VALUE_RAW` | `RAW(1000)`      |      | Endpoint actual value in raw format                                                                      |
| `ENDPOINT_REPEAT_COUNT`     | `NUMBER`         |      | Frequency of the endpoint (applies only to hybrid histograms, and is set to 0 for other histogram types) |

**See Also:**

- "[DBA_PART_HISTOGRAMS](DBA_PART_HISTOGRAMS.md)"

- "[USER_PART_HISTOGRAMS](USER_PART_HISTOGRAMS.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md) for more information about the DBMS_STATS package
