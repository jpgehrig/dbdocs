## 2.112 ALL_CAPTURE_PREPARED_DATABASE

`ALL_CAPTURE_PREPARED_DATABASE` displays information about when the local database was prepared for instantiation. If the local database was not prepared for instantiation, then this view contains no rows.

### Related View

`DBA_CAPTURE_PREPARED_DATABASE` displays information about when the local database was prepared for instantiation.

| Column                      | Datatype      | NULL | Description                                                                                                   |
|:----------------------------|:--------------|:-----|:--------------------------------------------------------------------------------------------------------------|
| `TIMESTAMP`                 | `DATE`        |      | Date and time at which the local database was ready to be instantiated                                        |
| `SUPPLEMENTAL_LOG_DATA_PK`  | `VARCHAR2(8)` |      | Status of database-level PRIMARY KEY COLUMNS supplemental logging:<br>• `IMPLICIT`<br>• `EXPLICIT`<br>• `NO`  |
| `SUPPLEMENTAL_LOG_DATA_UI`  | `VARCHAR2(8)` |      | Status of database-level UNIQUE INDEX COLUMNS supplemental logging:<br>• `IMPLICIT`<br>• `EXPLICIT`<br>• `NO` |
| `SUPPLEMENTAL_LOG_DATA_FK`  | `VARCHAR2(8)` |      | Status of database-level FOREIGN KEY COLUMNS supplemental logging:<br>• `IMPLICIT`<br>• `EXPLICIT`<br>• `NO`  |
| `SUPPLEMENTAL_LOG_DATA_ALL` | `VARCHAR2(8)` |      | Status of database-level ALL COLUMNS supplemental logging:<br>• `IMPLICIT`<br>• `EXPLICIT`<br>• `NO`          |

**See Also:**

"[DBA_CAPTURE_PREPARED_DATABASE](DBA_CAPTURE_PREPARED_DATABASE.md)"
