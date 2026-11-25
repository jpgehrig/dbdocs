## 3.118 ALL_TAB_STATS_HISTORY

`ALL_TAB_STATS_HISTORY` provides a history of table statistics modifications for all tables accessible to the current user.

### Related Views

- `DBA_TAB_STATS_HISTORY` provides a history of table statistics modifications for all tables in the database.

- `USER_TAB_STATS_HISTORY` provides a history of table statistics modifications for all tables owned by the current user.

| Column              | Datatype                      | NULL | Description                               |
|:--------------------|:------------------------------|:-----|:------------------------------------------|
| `OWNER`             | `VARCHAR2(128)`               |      | Owner of the object                       |
| `TABLE_NAME`        | `VARCHAR2(128)`               |      | Name of the table                         |
| `PARTITION_NAME`    | `VARCHAR2(128)`               |      | Name of the partition                     |
| `SUBPARTITION_NAME` | `VARCHAR2(128)`               |      | Name of the subpartition                  |
| `STATS_UPDATE_TIME` | `TIMESTAMP(6) WITH TIME ZONE` |      | Time at which the statistics were updated |

**See Also:**

- "[DBA_TAB_STATS_HISTORY](DBA_TAB_STATS_HISTORY.md)"

- "[USER_TAB_STATS_HISTORY](USER_TAB_STATS_HISTORY.md)"
