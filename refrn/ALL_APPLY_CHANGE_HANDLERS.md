## 2.55 ALL_APPLY_CHANGE_HANDLERS

`ALL_APPLY_CHANGE_HANDLERS` displays information about the change handlers on the tables accessible to the current user.

### Related View

`DBA_APPLY_CHANGE_HANDLERS` displays information about the change handlers on all tables in the database.

| Column               | Datatype        | NULL | Description                                                                                                                           |
|:---------------------|:----------------|:-----|:--------------------------------------------------------------------------------------------------------------------------------------|
| `CHANGE_TABLE_OWNER` | `VARCHAR2(128)` |      | Owner of the change table                                                                                                             |
| `CHANGE_TABLE_NAME`  | `VARCHAR2(128)` |      | Name of the change table                                                                                                              |
| `SOURCE_TABLE_OWNER` | `VARCHAR2(128)` |      | Owner of the source table                                                                                                             |
| `SOURCE_TABLE_NAME`  | `VARCHAR2(128)` |      | Name of the source table                                                                                                              |
| `HANDLER_NAME`       | `VARCHAR2(128)` |      | Name of the statement-based change handler                                                                                            |
| `CAPTURE_VALUES`     | `VARCHAR2(3)`   |      | Indicates whether to capture the old (`OLD`), new (`NEW`), or both (`*`) values                                                       |
| `APPLY_NAME`         | `VARCHAR2(128)` |      | Name of the apply process                                                                                                             |
| `OPERATION_NAME`     | `VARCHAR2(10)`  |      | Name of the DML operation to which the DML handler is set:<br>• `DEFAULT`<br>• `INSERT`<br>• `UPDATE`<br>• `DELETE`<br>• `LOB_UPDATE` |
| `CREATION_TIME`      | `TIMESTAMP(6)`  |      | Change handler creation time                                                                                                          |
| `MODIFICATION_TIME`  | `TIMESTAMP(6)`  |      | Change handler modification time                                                                                                      |

**See Also:**

"[DBA_APPLY_CHANGE_HANDLERS](DBA_APPLY_CHANGE_HANDLERS.md)"
