## 2.273 ALL_MVIEW_COMMENTS

`ALL_MVIEW_COMMENTS` displays comments on the materialized views accessible to the current user.

### Related Views

- `DBA_MVIEW_COMMENTS` displays comments on the materialized views in the database.

- `USER_MVIEW_COMMENTS` displays comments on the materialized views owned by the current user. This view does not display the `OWNER` column.

| Column       | Datatype         | NULL       | Description                      |
|:-------------|:-----------------|:-----------|:---------------------------------|
| `OWNER`      | `VARCHAR2(128)`  | `NOT NULL` | Owner of the materialized view   |
| `MVIEW_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Name of the materialized view    |
| `COMMENTS`   | `VARCHAR2(4000)` |            | Comment on the materialized view |

**See Also:**

- "[DBA_MVIEW_COMMENTS](DBA_MVIEW_COMMENTS.md)"

- "[USER_MVIEW_COMMENTS](USER_MVIEW_COMMENTS.md)"
