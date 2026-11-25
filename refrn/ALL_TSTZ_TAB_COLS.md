## 3.126 ALL_TSTZ_TAB_COLS

`ALL_TSTZ_TAB_COLS` displays information about the columns of the tables accessible to the current user, which have columns defined on `TIMESTAMP WITH TIME ZONE` data types or object types containing attributes of `TIMESTAMP WITH TIME ZONE` data types.

### Related Views

- `DBA_TSTZ_TAB_COLS` displays information about the columns of all tables in the database, which have columns defined on `TIMESTAMP WITH TIME ZONE` data types or object types containing attributes of `TIMESTAMP WITH TIME ZONE` data types. This view does not display the `COLUMN_NAME`, `NESTED`, and `VIRTUAL_COLUMN` columns.

- `USER_TSTZ_TAB_COLS` displays information about the columns of the tables owned by the current user, which have columns defined on `TIMESTAMP WITH TIME ZONE` data types or object types containing attributes of `TIMESTAMP WITH TIME ZONE` data types. This view does not display the `OWNER`, `COLUMN_NAME`, `NESTED`, and `VIRTUAL_COLUMN` columns.

| Column               | Datatype         | NULL       | Description                                                         |
|:---------------------|:-----------------|:-----------|:--------------------------------------------------------------------|
| `OWNER`              | `VARCHAR2(128)`  | `NOT NULL` | Owner of the table                                                  |
| `TABLE_NAME`         | `VARCHAR2(128)`  | `NOT NULL` | Name of the table                                                   |
| `COLUMN_NAME`        | `VARCHAR2(128)`  | `NOT NULL` | Column name                                                         |
| `QUALIFIED_COL_NAME` | `VARCHAR2(4000)` |            | Qualified column name                                               |
| `NESTED`             | `NUMBER`         |            | Indicates whether the column is a nested table (`1`) or not (`0`)   |
| `VIRTUAL_COLUMN`     | `NUMBER`         |            | Indicates whether the column is a virtual column (`1`) or not (`0`) |
| `SCALAR_COLUMN`      | `NUMBER`         |            | Indicates whether the column is a scalar column (`1`) or not (`0`)  |
| `UNUSED_COLUMN`      | `NUMBER`         |            | Indicates whether the column is an unused column (`1`) or not (`0`) |

**See Also:**

- "[DBA_TSTZ_TAB_COLS](DBA_TSTZ_TAB_COLS.md)"

- "[USER_TSTZ_TAB_COLS](USER_TSTZ_TAB_COLS.md)"
