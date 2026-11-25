## 3.8 ALL_PENDING_CONV_TABLES

`ALL_PENDING_CONV_TABLES` describes the pending conversion tables (tables which are not upgraded to the latest type version) accessible to the current user.

### Related Views

- `DBA_PENDING_CONV_TABLES` describes all pending conversion tables in the database.

- `USER_PENDING_CONV_TABLES` describes the pending conversion tables owned by the current user. This view does not display the `OWNER` column.

| Column       | Datatype        | NULL       | Description        |
|:-------------|:----------------|:-----------|:-------------------|
| `OWNER`      | `VARCHAR2(128)` | `NOT NULL` | Owner of the table |
| `TABLE_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the table  |

**See Also:**

- "[DBA_PENDING_CONV_TABLES](DBA_PENDING_CONV_TABLES.md)"

- "[USER_PENDING_CONV_TABLES](USER_PENDING_CONV_TABLES.md)"
