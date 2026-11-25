## 3.166 ALL_XTERNAL_PART_TABLES

`ALL_XTERNAL_PART_TABLES` describes object-level information for partitioned external tables accessible to the current user.

### Related Views

- `DBA_XTERNAL_PART_TABLES` describes object-level information for partitioned external tables in the database

- `USER_XTERNAL_PART_TABLES` describes object-level information for partitioned external tables owned by the current user. This view does not display the `OWNER` column.

| Column                    | Datatype        | NULL       | Description                                                           |
|:--------------------------|:----------------|:-----------|:----------------------------------------------------------------------|
| `OWNER`                   | `VARCHAR2(128)` | `NOT NULL` | Owner of the partitioned external table                               |
| `TABLE_NAME`              | `VARCHAR2(128)` | `NOT NULL` | Name of the partitioned external table                                |
| `TYPE_OWNER`              | `CHAR(3)`       |            | Owner of the implementation type for the external table access driver |
| `TYPE_NAME`               | `VARCHAR2(128)` |            | Name of the implementation type for the external table access driver  |
| `DEFAULT_DIRECTORY_OWNER` | `CHAR(3)`       |            | Owner of the default directory for the external table                 |
| `DEFAULT_DIRECTORY_NAME`  | `VARCHAR2(128)` |            | Name of the default directory for the external table                  |
| `REJECT_LIMIT`            | `VARCHAR2(40)`  |            | Reject limit for the external table, or `UNLIMITED`                   |
| `ACCESS_TYPE`             | `VARCHAR2(7)`   |            | Type of access parameters for the external table (`BLOB`, `CLOB`)     |
| `ACCESS_PARAMETERS`       | `CLOB`          |            | Access parameters for the external table                              |
| `PROPERTY`                | `VARCHAR2(10)`  |            | Property of the external table (`REFERENCED`, `ALL`)                  |

**See Also:**

- "[DBA_XTERNAL_PART_TABLES](DBA_XTERNAL_PART_TABLES.md)"

- "[USER_XTERNAL_PART_TABLES](USER_XTERNAL_PART_TABLES.md)"
