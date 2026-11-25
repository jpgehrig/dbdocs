## 2.107 ALL_BASE_TABLE_MVIEWS

`ALL_BASE_TABLE_MVIEWS` describes the materialized views using materialized view logs accessible to the current user. A materialized view log can be created for a master, base table, or master materialized view. Query this view at the master site or the master materialized view site to show one row for each materialized view using a materialized view log.

### Related Views

- `DBA_BASE_TABLE_MVIEWS` describes all materialized views using materialized view logs in the database.

- `USER_BASE_TABLE_MVIEWS` describes the materialized views using materialized view logs owned by the current user.

| Column                    | Datatype        | NULL       | Description                                                                  |
|:--------------------------|:----------------|:-----------|:-----------------------------------------------------------------------------|
| `OWNER`                   | `VARCHAR2(128)` | `NOT NULL` | Schema in which the master table or the master materialized view was created |
| `MASTER`                  | `VARCHAR2(128)` | `NOT NULL` | Name of the master table or the master materialized view                     |
| `MVIEW_LAST_REFRESH_TIME` | `DATE`          | `NOT NULL` | Date when the materialized view based on the master was last refreshed       |
| `MVIEW_ID`                | `NUMBER(38)`    |            | Unique identifier of the materialized view that is based on the master       |

**See Also:**

- "[DBA_BASE_TABLE_MVIEWS](DBA_BASE_TABLE_MVIEWS.md)"

- "[USER_BASE_TABLE_MVIEWS](USER_BASE_TABLE_MVIEWS.md)"
