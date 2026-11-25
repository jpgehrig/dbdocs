## 2.167 ALL_EDITION_COMMENTS

`ALL_EDITION_COMMENTS` describes the comments on the editions accessible to the current user.

### Related View

`DBA_EDITION_COMMENTS` describes the comments on all editions in the database.

| Column         | Datatype         | NULL       | Description         |
|:---------------|:-----------------|:-----------|:--------------------|
| `EDITION_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Name of the edition |
| `COMMENTS`     | `VARCHAR2(4000)` |            | Edition comments    |

**See Also:**

"[DBA_EDITION_COMMENTS](DBA_EDITION_COMMENTS.md)"
