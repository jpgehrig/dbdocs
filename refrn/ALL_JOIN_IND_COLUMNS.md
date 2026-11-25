## 2.247 ALL_JOIN_IND_COLUMNS

`ALL_JOIN_IND_COLUMNS` describes the join conditions of bitmap join indexes accessible to the current user. Bitmap join indexes are indexes built on a child table with an index key containing columns from associated parent tables, where all of the tables are connected through join conditions. There is one row for each join condition.

### Related Views

- `DBA_JOIN_IND_COLUMNS` describes all join conditions in the database.

- `USER_JOIN_IND_COLUMNS` describes the join conditions owned by the current user. This view does not display the `INDEX_OWNER` column.

| Column               | Datatype        | NULL       | Description                             |
|:---------------------|:----------------|:-----------|:----------------------------------------|
| `INDEX_OWNER`        | `VARCHAR2(128)` | `NOT NULL` | Owner of the bitmap join index          |
| `INDEX_NAME`         | `VARCHAR2(128)` | `NOT NULL` | Name of the bitmap join index           |
| `INNER_TABLE_OWNER`  | `VARCHAR2(128)` | `NOT NULL` | Owner of the fact table                 |
| `INNER_TABLE_NAME`   | `VARCHAR2(128)` | `NOT NULL` | Name of the fact table                  |
| `INNER_TABLE_COLUMN` | `VARCHAR2(128)` | `NOT NULL` | Name of the fact table join column      |
| `OUTER_TABLE_OWNER`  | `VARCHAR2(128)` | `NOT NULL` | Owner of the dimension table            |
| `OUTER_TABLE_NAME`   | `VARCHAR2(128)` | `NOT NULL` | Name of the dimension table             |
| `OUTER_TABLE_COLUMN` | `VARCHAR2(128)` | `NOT NULL` | Name of the dimension table join column |

**See Also:**

- "[DBA_JOIN_IND_COLUMNS](DBA_JOIN_IND_COLUMNS.md)"

- "[USER_JOIN_IND_COLUMNS](USER_JOIN_IND_COLUMNS.md)"
