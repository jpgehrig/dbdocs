## 2.113 ALL_CAPTURE_PREPARED_SCHEMAS

`ALL_CAPTURE_PREPARED_SCHEMAS` displays information about the schemas prepared for instantiation that are accessible to the current user at the local database.

### Related View

`DBA_CAPTURE_PREPARED_SCHEMAS` displays information about all schemas prepared for instantiation at the local database.

| Column                      | Datatype        | NULL       | Description                                                                                                 |
|:----------------------------|:----------------|:-----------|:------------------------------------------------------------------------------------------------------------|
| `SCHEMA_NAME`               | `VARCHAR2(128)` | `NOT NULL` | Name of the schema that is ready to be instantiated                                                         |
| `TIMESTAMP`                 | `DATE`          |            | Date and time at which the schema was ready to be instantiated                                              |
| `SUPPLEMENTAL_LOG_DATA_PK`  | `VARCHAR2(8)`   |            | Status of schema-level PRIMARY KEY COLUMNS supplemental logging:<br>• `IMPLICIT`<br>• `EXPLICIT`<br>• `NO`  |
| `SUPPLEMENTAL_LOG_DATA_UI`  | `VARCHAR2(8)`   |            | Status of schema-level UNIQUE INDEX COLUMNS supplemental logging:<br>• `IMPLICIT`<br>• `EXPLICIT`<br>• `NO` |
| `SUPPLEMENTAL_LOG_DATA_FK`  | `VARCHAR2(8)`   |            | Status of schema-level FOREIGN KEY COLUMNS supplemental logging:<br>• `IMPLICIT`<br>• `EXPLICIT`<br>• `NO`  |
| `SUPPLEMENTAL_LOG_DATA_ALL` | `VARCHAR2(8)`   |            | Status of schema-level ALL COLUMNS supplemental logging:<br>• `IMPLICIT`<br>• `EXPLICIT`<br>• `NO`          |

**See Also:**

"[DBA_CAPTURE_PREPARED_SCHEMAS](DBA_CAPTURE_PREPARED_SCHEMAS.md)"
