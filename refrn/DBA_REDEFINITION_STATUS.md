## 5.271 DBA_REDEFINITION_STATUS

`DBA_REDEFINITION_STATUS` is an online redefinition view. It provides information about the online redefinition status.

| Column                 | Datatype         | NULL       | Description                                                                                                                                   |
|:-----------------------|:-----------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `REDEFINITION_ID`      | `NUMBER(38)`     | `NOT NULL` | ID for the redefinition object                                                                                                                |
| `BASE_TABLE_OWNER`     | `VARCHAR2(128)`  |            | Owner of the base table of the redefinition object                                                                                            |
| `BASE_TABLE_NAME`      | `VARCHAR2(128)`  |            | Name of the base table of the redefinition object                                                                                             |
| `BASE_OBJECT_NAME`     | `VARCHAR2(128)`  | `NOT NULL` | Name of the base object of the redefinition object                                                                                            |
| `BASE_OBJECT_TYPE`     | `VARCHAR2(9)`    |            | Type of the base object of the redefinition object                                                                                            |
| `INTERIM_OBJECT_OWNER` | `VARCHAR2(128)`  |            | Owner of the interim object of the redefinition object                                                                                        |
| `INTERIM_OBJECT_NAME`  | `VARCHAR2(128)`  |            | Name of the interim object of the redefinition object                                                                                         |
| `OPERATION`            | `VARCHAR2(128)`  | `NOT NULL` | The current redefinition operation:<br>• `START_REDEF_TABLE`<br>• `SYNC_INTERIM_TABLE`<br>• `COPY_TABLE_DEPENDENTS`<br>• `FINISH_REDEF_TABLE` |
| `STATUS`               | `VARCHAR2(128)`  | `NOT NULL` | Status of the previous redefinition operation:<br>• `FAILURE`<br>• `SUCCESS`                                                                  |
| `RESTARTABLE`          | `VARCHAR2(1)`    | `NOT NULL` | Indicates whether the previous operation can be restarted                                                                                     |
| `ERR_TXT`              | `VARCHAR2(1000)` |            | The error message raised from the previous operation                                                                                          |
| `ACTION`               | `VARCHAR2(400)`  |            | The suggested action                                                                                                                          |
| `REFRESH_DEP_MVIEWS`   | `VARCHAR2(1)`    |            | Indicates whether the online redefinition will also refresh dependent materialized views when syncing the interim table (`Y`) or not (`N`)    |

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-tables.md) for more information about online redefinition
