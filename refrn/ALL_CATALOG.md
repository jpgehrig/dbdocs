## 2.115 ALL_CATALOG

`ALL_CATALOG` displays the tables, clusters, views, synonyms, and sequences accessible to the current user.

### Related Views

- `DBA_CATALOG` displays all tables, clusters, views, synonyms, and sequences in the entire database.

- `USER_CATALOG` displays the tables, clusters, views, synonyms, and sequences in the current user's schema. This view does not display the `OWNER` column.

| Column       | Datatype        | NULL       | Description                                                                    |
|:-------------|:----------------|:-----------|:-------------------------------------------------------------------------------|
| `OWNER`      | `VARCHAR2(128)` | `NOT NULL` | Owner of the `TABLE`, `CLUSTER`, `VIEW`, `SYNONYM`, `SEQUENCE`, or `UNDEFINED` |
| `TABLE_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the `TABLE`, `CLUSTER`, `VIEW`, `SYNONYM`, `SEQUENCE`, or `UNDEFINED`  |
| `TABLE_TYPE` | `VARCHAR2(11)`  |            | Type of the `TABLE`, `CLUSTER`, `VIEW`, `SYNONYM`, `SEQUENCE`, or `UNDEFINED`  |

**See Also:**

- "[DBA_CATALOG](DBA_CATALOG.md)"

- "[USER_CATALOG](USER_CATALOG.md)"
