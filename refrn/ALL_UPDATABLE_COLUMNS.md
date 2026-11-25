## 3.134 ALL_UPDATABLE_COLUMNS

`ALL_UPDATABLE_COLUMNS` describes all columns in a join view that are updatable by the current user, subject to appropriate privileges.

### Related Views

- `DBA_UPDATABLE_COLUMNS` describes all columns in a join view that are updatable by the database administrator, subject to appropriate privileges.

- `USER_UPDATABLE_COLUMNS` describes all columns owned by the current user that are in a join view and are updatable by the current user, subject to appropriate privileges.

| Column        | Datatype        | NULL       | Description                                                      |
|:--------------|:----------------|:-----------|:-----------------------------------------------------------------|
| `OWNER`       | `VARCHAR2(128)` | `NOT NULL` | Owner of the table                                               |
| `TABLE_NAME`  | `VARCHAR2(128)` | `NOT NULL` | Name of the table                                                |
| `COLUMN_NAME` | `VARCHAR2(128)` | `NOT NULL` | Column name                                                      |
| `UPDATABLE`   | `VARCHAR2(3)`   |            | Indicates whether the column is updatable (`YES`) or not (`NO`)  |
| `INSERTABLE ` | `VARCHAR2(3)`   |            | Indicates whether the column is insertable (`YES`) or not (`NO`) |
| `DELETABLE`   | `VARCHAR2(3)`   |            | Indicates whether the column is deletable (`YES`) or not (`NO`)  |

**Note:**

The values shown in the `UPDATABLE`, `INSERTABLE`, and `DELETABLE` columns are not instantly updated when a DDL operation that would affect these attributes occurs on one of the tables referenced in the `FROM` clause of the view definition. For example, these columns are not instantly updated when a primary key or unique constraint is added to or removed from the non-key-preserved table. To remedy this situation, recompile the view using the `ALTER` `VIEW` `COMPILE` statement to ensure that the latest information is displayed.

**See Also:**

- "[DBA_UPDATABLE_COLUMNS](DBA_UPDATABLE_COLUMNS.md)"

- "[USER_UPDATABLE_COLUMNS](USER_UPDATABLE_COLUMNS.md)"

- [Oracle Database Concepts](../cncpt/partitions-views-and-other-schema-objects.md) for information on updatable join views
