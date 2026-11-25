## 2.230 ALL_INDEXTYPE_COMMENTS

`ALL_INDEXTYPE_COMMENTS` displays comments for the user-defined indextypes accessible to the current user.

### Related Views

- `DBA_INDEXTYPE_COMMENTS` displays comments for all user-defined indextypes in the database.

- `USER_INDEXTYPE_COMMENTS` displays comments for the user-defined indextypes owned by the current user.

| Column           | Datatype         | NULL       | Description                            |
|:-----------------|:-----------------|:-----------|:---------------------------------------|
| `OWNER`          | `VARCHAR2(128)`  | `NOT NULL` | Owner of the user-defined indextype    |
| `INDEXTYPE_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Name of the user-defined indextype     |
| `COMMENTS`       | `VARCHAR2(4000)` |            | Comment for the user-defined indextype |

**See Also:**

- "[DBA_INDEXTYPE_COMMENTS](DBA_INDEXTYPE_COMMENTS.md)"

- "[USER_INDEXTYPE_COMMENTS](USER_INDEXTYPE_COMMENTS.md)"
