## 3.168 ALL_XTERNAL_TAB_SUBPARTITIONS

`ALL_XTERNAL_TAB_SUBPARTITIONS` describes subpartition-level information for partitioned external tables accessible to the current user.

### Related Views

- `DBA_XTERNAL_TAB_SUBPARTITIONS` describes subpartition-level information for partitioned external tables in the database.

- `USER_XTERNAL_TAB_SUBPARTITIONS` describes subpartition-level information for partitioned external tables owned by the current user. This view does not display the `TABLE_OWNER` column.

| Column                    | Datatype        | NULL       | Description                                                     |
|:--------------------------|:----------------|:-----------|:----------------------------------------------------------------|
| `TABLE_OWNER`             | `VARCHAR2(128)` | `NOT NULL` | Owner of the partitioned external table                         |
| `TABLE_NAME`              | `VARCHAR2(128)` | `NOT NULL` | Name of the partitioned external table                          |
| `PARTITION_NAME`          | `VARCHAR2(128)` |            | Name of the partition                                           |
| `SUBPARTITION_NAME`       | `VARCHAR2(128)` |            | Name of the subpartition                                        |
| `DEFAULT_DIRECTORY_OWNER` | `CHAR(3)`       |            | Owner of the default directory for the external table partition |
| `DEFAULT_DIRECTORY_NAME`  | `VARCHAR2(128)` |            | Name of the default directory for the external table partition  |
| `ACCESS_TYPE`             | `VARCHAR2(7)`   |            | Type of access parameters for the partition (`BLOB`, `CLOB`)    |
| `ACCESS_PARAMETERS`       | `CLOB`          |            | Access parameters for the external table partition              |

**See Also:**

- "[DBA_XTERNAL_TAB_SUBPARTITIONS](DBA_XTERNAL_TAB_SUBPARTITIONS.md)"

- "[USER_XTERNAL_TAB_SUBPARTITIONS](USER_XTERNAL_TAB_SUBPARTITIONS.md)"
