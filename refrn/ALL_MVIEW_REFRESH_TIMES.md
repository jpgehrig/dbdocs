## 2.280 ALL_MVIEW_REFRESH_TIMES

`ALL_MVIEW_REFRESH_TIMES` describes refresh times of the materialized views accessible to the current user.

### Related Views

- `DBA_MVIEW_REFRESH_TIMES` describes refresh times of all materialized views in the database.

- `USER_MVIEW_REFRESH_TIMES` describes refresh times of the materialized views owned by the current user.

| Column         | Datatype        | NULL       | Description                                                    |
|:---------------|:----------------|:-----------|:---------------------------------------------------------------|
| `OWNER`        | `VARCHAR2(128)` | `NOT NULL` | Owner of the materialized view                                 |
| `NAME`         | `VARCHAR2(128)` | `NOT NULL` | Name of the materialized view                                  |
| `MASTER_OWNER` | `VARCHAR2(128)` |            | Owner of the master table                                      |
| `MASTER`       | `VARCHAR2(128)` |            | Name of the master table                                       |
| `LAST_REFRESH` | `DATE`          |            | `SYSDATE` from the master site at the time of the last refresh |

**See Also:**

- "[DBA_MVIEW_REFRESH_TIMES](DBA_MVIEW_REFRESH_TIMES.md)"

- "[USER_MVIEW_REFRESH_TIMES](USER_MVIEW_REFRESH_TIMES.md)"
