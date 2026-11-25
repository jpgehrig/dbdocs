## 4.224 DBA_CQ_NOTIFICATION_QUERIES

`DBA_CQ_NOTIFICATION_QUERIES` describes the registered queries for all CQ notifications in the database.

### Related View

`USER_CQ_NOTIFICATION_QUERIES` describes the registered queries for the CQ notifications owned by the current user. This view does not display the `USERNAME` column.

| Column      | Datatype       | NULL | Description                                       |
|:------------|:---------------|:-----|:--------------------------------------------------|
| `QUERYID`   | `NUMBER`       |      | ID of the query                                   |
| `QUERYTEXT` | `CLOB`         |      | Text of the query                                 |
| `REGID`     | `NUMBER`       |      | Registration ID that the query is registered with |
| `USERNAME`  | `VARCHAR2(31)` |      | Name of the user who registered the query         |

**See Also:**

"[USER_CQ_NOTIFICATION_QUERIES](USER_CQ_NOTIFICATION_QUERIES.md)"
