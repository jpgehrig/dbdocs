## 3.4 ALL_PART_KEY_COLUMNS

`ALL_PART_KEY_COLUMNS` describes the partitioning key columns for the partitioned objects accessible to the current user.

### Related Views

- `DBA_PART_KEY_COLUMNS` describes the partitioning key columns for all partitioned objects in the database.

- `USER_PART_KEY_COLUMNS` describes the partitioning key columns for the partitioned objects owned by the current user. This view does not display the `OWNER` column.

| Column               | Datatype         | NULL | Description                                                                               |
|:---------------------|:-----------------|:-----|:------------------------------------------------------------------------------------------|
| `OWNER`              | `VARCHAR2(128)`  |      | Owner of the partitioned table or index                                                   |
| `NAME`               | `VARCHAR2(128)`  |      | Name of the partitioned table or index                                                    |
| `OBJECT_TYPE`        | `CHAR(5)`        |      | Object type:<br>• `TABLE`<br>• `INDEX`                                                    |
| `COLUMN_NAME`        | `VARCHAR2(4000)` |      | Name of the column                                                                        |
| `COLUMN_POSITION`    | `NUMBER`         |      | Position of the column within the partitioning key                                        |
| `COLLATED_COLUMN_ID` | `NUMBER`         |      | Internal sequence number of the column for which this column provides linguistic ordering |

**See Also:**

- "[DBA_PART_KEY_COLUMNS](DBA_PART_KEY_COLUMNS.md)"

- "[USER_PART_KEY_COLUMNS](USER_PART_KEY_COLUMNS.md)"
