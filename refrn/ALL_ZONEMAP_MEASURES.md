## 3.169 ALL_ZONEMAP_MEASURES

`ALL_ZONEMAP_MEASURES` describes the measures for all zone maps accessible to the user.

### Related Views

- `DBA_ZONEMAP_MEASURES` describes the measures for all the zone maps in the database.

- `USER_ZONEMAP_MEASURES` describes the measures for all the zone maps owned by the user.

| Column               | Datatype        | NULL       | Description                                                                                |
|:---------------------|:----------------|:-----------|:-------------------------------------------------------------------------------------------|
| `OWNER`              | `VARCHAR2(128)` | `NOT NULL` | Owner of the zone map                                                                      |
| `ZONEMAP_NAME`       | `VARCHAR2(128)` | `NOT NULL` | Name of the zone map                                                                       |
| `MEASURE`            | `LONG`          |            | Column whose `MIN/``MAX` value is computed                                                 |
| `POSITION_IN_SELECT` | `NUMBER`        | `NOT NULL` | Original position of the mesaure aggregate on the `SELECT` list of zone map defining query |
| `AGG_FUNCTION`       | `VARCHAR2(13)`  |            | Name of aggregate in zone map table                                                        |
| `AGG_COLUMN_NAME`    | `VARCHAR2(128)` | `NOT NULL` | Name of the column whose `MIN``/MAX` per zone maintained                                   |

**Note:**

This view is intended for use with Oracle Exadata release 12.1.2.1.1 or later.

**See Also:**

- "[DBA_ZONEMAP_MEASURES](DBA_ZONEMAP_MEASURES.md)"

- "[USER_ZONEMAP_MEASURES](USER_ZONEMAP_MEASURES.md)"

- [Oracle Database Data Warehousing Guide](../dwhsg/using-zone-maps.md) for more information about zone maps
