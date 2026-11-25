## 2.291 ALL_OPERATOR_COMMENTS

`ALL_OPERATOR_COMMENTS` displays comments for the user-defined operators accessible to the current user.

### Related Views

- `DBA_OPERATOR_COMMENTS` displays comments for all user-defined operators in the database.

- `USER_OPERATOR_COMMENTS` displays comments for the user-defined operators owned by the current user.

| Column          | Datatype         | NULL       | Description                           |
|:----------------|:-----------------|:-----------|:--------------------------------------|
| `OWNER`         | `VARCHAR2(128)`  | `NOT NULL` | Owner of the user-defined operator    |
| `OPERATOR_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Name of the user-defined operator     |
| `COMMENTS`      | `VARCHAR2(4000)` |            | Comment for the user-defined operator |

**See Also:**

- "[DBA_OPERATOR_COMMENTS](DBA_OPERATOR_COMMENTS.md)"

- "[USER_OPERATOR_COMMENTS](USER_OPERATOR_COMMENTS.md)"
