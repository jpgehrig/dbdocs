## 3.31 ALL_REWRITE_EQUIVALENCES

`ALL_REWRITE_EQUIVALENCES` describes the rewrite equivalences accessible to the current user.

### Related Views

- `DBA_REWRITE_EQUIVALENCES` describes all rewrite equivalences in the database.

- `USER_REWRITE_EQUIVALENCES` describes the rewrite equivalences owned by the current user.

| Column             | Datatype        | NULL       | Description                                                                                                |
|:-------------------|:----------------|:-----------|:-----------------------------------------------------------------------------------------------------------|
| `OWNER`            | `VARCHAR2(128)` | `NOT NULL` | Owner of the rewrite equivalence                                                                           |
| `NAME`             | `VARCHAR2(128)` | `NOT NULL` | Name of the rewrite equivalence                                                                            |
| `SOURCE_STMT`      | `CLOB`          |            | Source statement of the rewrite equivalence                                                                |
| `DESTINATION_STMT` | `CLOB`          |            | Destination of the rewrite equivalence                                                                     |
| `REWRITE_MODE`     | `VARCHAR2(10)`  |            | Rewrite mode of the rewrite equivalence:<br>• `DISABLED`<br>• `TEXT_MATCH`<br>• `GENERAL`<br>• `RECURSIVE` |

**See Also:**

- "[DBA_REWRITE_EQUIVALENCES](DBA_REWRITE_EQUIVALENCES.md)"

- "[USER_REWRITE_EQUIVALENCES](USER_REWRITE_EQUIVALENCES.md)"
