## 3.101 ALL_SYNC_CAPTURE_TABLES

`ALL_SYNC_CAPTURE_TABLES` displays information about the tables accessible to the current user that are captured by synchronous captures.

### Related View

`DBA_SYNC_CAPTURE_TABLES` displays information about all tables in the database that are captured by synchronous captures.

| Column        | Datatype        | NULL | Description                                                                          |
|:--------------|:----------------|:-----|:-------------------------------------------------------------------------------------|
| `TABLE_OWNER` | `VARCHAR2(128)` |      | Owner of the synchronous capture table                                               |
| `TABLE_NAME`  | `VARCHAR2(128)` |      | Name of the synchronous capture table                                                |
| `ENABLED`     | `VARCHAR2(3)`   |      | Indicates whether synchronous capture is enabled for the table (`YES`) or not (`NO`) |

**See Also:**

"[DBA_SYNC_CAPTURE_TABLES](DBA_SYNC_CAPTURE_TABLES.md)"
