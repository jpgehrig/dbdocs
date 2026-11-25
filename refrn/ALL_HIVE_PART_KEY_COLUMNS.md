## 2.217 ALL_HIVE_PART_KEY_COLUMNS

`ALL_HIVE_PART_KEY_COLUMNS` provides information about all Hive table partition columns accessible to the current user in the database.

### Related Views

- `DBA_HIVE_PART_KEY_COLUMNS` provides information about all Hive table partition columns in the database.

- `USER_HIVE_PART_KEY_COLUMNS` provides information about all Hive table partition columns owned by the current user in the database.

| Column               | Datatype         | NULL | Description                                                   |
|:---------------------|:-----------------|:-----|:--------------------------------------------------------------|
| `CLUSTER_ID`         | `VARCHAR2(4000)` |      | Hadoop cluster name                                           |
| `DATABASE_NAME`      | `VARCHAR2(4000)` |      | Hive database where the Hive table resides                    |
| `TABLE_NAME`         | `VARCHAR2(4000)` |      | Hive table name                                               |
| `OWNER`              | `VARCHAR2(4000)` |      | Owner of the Hive table                                       |
| `COLUMN_NAME`        | `VARCHAR2(4000)` |      | Partition column name                                         |
| `COLUMN_TYPE`        | `VARCHAR2(4000)` |      | Partition column type                                         |
| `COLUMN_POSITION`    | `NUMBER`         |      | Partition column position in the Hive partition specification |
| `ORACLE_COLUMN_TYPE` | `VARCHAR2(4000)` |      | Equivalent Oracle data type of the Hive column                |

**See Also:**

- "[DBA_HIVE_PART_KEY_COLUMNS](DBA_HIVE_PART_KEY_COLUMNS.md)"

- "[USER_HIVE_PART_KEY_COLUMNS](USER_HIVE_PART_KEY_COLUMNS.md)"
