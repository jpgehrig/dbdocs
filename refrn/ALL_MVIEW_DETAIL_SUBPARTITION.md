## 2.276 ALL_MVIEW_DETAIL_SUBPARTITION

`ALL_MVIEW_DETAIL_SUBPARTITION` displays freshness information, with respect to partition change tracking (PCT) detail subpartitions, for the materialized views accessible to the current user.

### Related Views

- `DBA_MVIEW_DETAIL_SUBPARTITION` displays freshness information, with respect to PCT detail subpartitions, for all materialized views in the database.

- `USER_MVIEW_DETAIL_SUBPARTITION` displays freshness information, with respect to PCT detail subpartitions, for the materialized views owned by the current user.

| Column                         | Datatype        | NULL       | Description                                                            |
|:-------------------------------|:----------------|:-----------|:-----------------------------------------------------------------------|
| `OWNER`                        | `VARCHAR2(128)` | `NOT NULL` | Owner of the materialized view                                         |
| `MVIEW_NAME`                   | `VARCHAR2(128)` | `NOT NULL` | Name of the materialized view                                          |
| `DETAILOBJ_OWNER`              | `VARCHAR2(128)` | `NOT NULL` | Owner of the detail object                                             |
| `DETAILOBJ_NAME`               | `VARCHAR2(128)` | `NOT NULL` | Name of the detail object                                              |
| `DETAIL_PARTITION_NAME`        | `VARCHAR2(128)` |            | Name of the detail object partition                                    |
| `DETAIL_SUBPARTITION_NAME`     | `VARCHAR2(128)` |            | Name of the detail object subpartition                                 |
| `DETAIL_SUBPARTITION_POSITION` | `NUMBER`        |            | Position of the detail object subpartition                             |
| `FRESHNESS`                    | `CHAR(5)`       |            | Freshness state of the detail object subpartition (`FRESH` or `STALE`) |

**See Also:**

- "[DBA_MVIEW_DETAIL_SUBPARTITION](DBA_MVIEW_DETAIL_SUBPARTITION.md)"

- "[USER_MVIEW_DETAIL_SUBPARTITION](USER_MVIEW_DETAIL_SUBPARTITION.md)"
