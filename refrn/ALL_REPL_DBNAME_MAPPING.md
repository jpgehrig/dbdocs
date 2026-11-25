## 3.29 ALL_REPL_DBNAME_MAPPING

`ALL_REPL_DBNAME_MAPPING` provides details about the database name mapping in replication for the current user.

### Related View

`DBA_REPL_DBNAME_MAPPING` provides details about the database name mapping in replication.

| Column                  | Datatype        | NULL | Description                                                                                                        |
|:------------------------|:----------------|:-----|:-------------------------------------------------------------------------------------------------------------------|
| `SOURCE_ROOT_NAME`      | `VARCHAR2(128)` |      | The fully qualified global name of the root in a multitenant container database (CDB) where the changes originated |
| `SOURCE_DATABASE_NAME`  | `VARCHAR2(128)` |      | The fully qualified global name of the pluggable database (PDB) where the changes originated                       |
| `SOURCE_CONTAINER_NAME` | `VARCHAR2(128)` |      | The container name of the database where the changes originated                                                    |

**See Also:**

"[DBA_REPL_DBNAME_MAPPING](DBA_REPL_DBNAME_MAPPING.md)"
