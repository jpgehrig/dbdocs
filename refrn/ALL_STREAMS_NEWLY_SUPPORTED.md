## 3.90 ALL_STREAMS_NEWLY_SUPPORTED

`ALL_STREAMS_NEWLY_SUPPORTED` displays information about the tables accessible to the current user that are newly supported by capture processes.

### Related View

`DBA_STREAMS_NEWLY_SUPPORTED` displays information about all tables in the database that are newly supported by capture processes.

| Column       | Datatype        | NULL | Description                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-------------|:----------------|:-----|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`      | `VARCHAR2(128)` |      | Owner of the table                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `TABLE_NAME` | `VARCHAR2(128)` |      | Name of the table                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `REASON`     | `VARCHAR2(39)`  |      | Reason why the table was not supported in a previous release:<br>• `IOT`<br>• `column with user-defined type`<br>• `unsupported column exists`<br>• `object table`<br>• `AQ queue table`<br>• `temporary table`<br>• `sub object`<br>• `external table`<br>• `materialized view`<br>• `FILE column exists`<br>• `materialized view log`<br>• `materialized view container table`<br>• `streams unsupported object`<br>• `domain index` |
| `COMPATIBLE` | `CHAR(4)`       |      | Minimum database compatibility for capture processes to support the database object                                                                                                                                                                                                                                                                                                                                                    |

**See Also:**

"[DBA_STREAMS_NEWLY_SUPPORTED](DBA_STREAMS_NEWLY_SUPPORTED.md)"
