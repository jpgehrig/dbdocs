## 3.7 ALL_PARTIAL_DROP_TABS

`ALL_PARTIAL_DROP_TABS` describes tables accessible to the current user that have partially completed `DROP COLUMN` operations. Such operations might have been interrupted by the user or by a system crash.

### Related Views

- `DBA_PARTIAL_DROP_TABS` describes all tables in the database that have partially completed `DROP COLUMN` operations.

- `USER_PARTIAL_DROP_TABS` describes tables in the schema of the current user that have partially completed `DROP COLUMN` operations. This view does not display the `OWNER` column.

| Column       | Datatype        | NULL       | Description         |
|:-------------|:----------------|:-----------|:--------------------|
| `OWNER`      | `VARCHAR2(128)` | `NOT NULL` | Owner of the object |
| `TABLE_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the table   |

**See Also:**

- "[DBA_PARTIAL_DROP_TABS](DBA_PARTIAL_DROP_TABS.md)"

- "[USER_PARTIAL_DROP_TABS](USER_PARTIAL_DROP_TABS.md)"
