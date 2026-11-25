## 3.133 ALL_UNUSED_COL_TABS

`ALL_UNUSED_COL_TABS` describes the tables accessible to the current user that contain unused columns.

### Related Views

- `DBA_UNUSED_COL_TABS` describes all tables in the database that contain unused columns.

- `USER_UNUSED_COL_TABS` describes the tables owned by the current user that contain unused columns. This view does not display the `OWNER` column.

| Column       | Datatype        | NULL       | Description              |
|:-------------|:----------------|:-----------|:-------------------------|
| `OWNER`      | `VARCHAR2(128)` | `NOT NULL` | Owner of the table       |
| `TABLE_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the table        |
| `COUNT`      | `NUMBER`        |            | Number of unused columns |

**See Also:**

- "[DBA_UNUSED_COL_TABS](DBA_UNUSED_COL_TABS.md)"

- "[USER_UNUSED_COL_TABS](USER_UNUSED_COL_TABS.md)"
