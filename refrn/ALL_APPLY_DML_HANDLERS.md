## 2.58 ALL_APPLY_DML_HANDLERS

`ALL_APPLY_DML_HANDLERS` displays information about the DML handlers on the tables accessible to the current user.

### Related View

`DBA_APPLY_DML_HANDLERS` displays information about the DML handlers on all tables in the database.

| Column                | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                            |
|:----------------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OBJECT_OWNER`        | `VARCHAR2(128)` | `NOT NULL` | Owner of the object on which the DML handler is specified                                                                                                                                                                                                                              |
| `OBJECT_NAME`         | `VARCHAR2(128)` | `NOT NULL` | Name of the object on which the DML handler is specified                                                                                                                                                                                                                               |
| `OPERATION_NAME`      | `VARCHAR2(13)`  |            | Name of the DML operation for which the DML handler is used:<br>• `DEFAULT`<br>• `INSERT`<br>• `UPDATE`<br>• `DELETE`<br>• `LOB_UPDATE`<br>• `ASSEMBLE_LOBS`                                                                                                                           |
| `USER_PROCEDURE`      | `VARCHAR2(98)`  |            | Name of the user-specified DML handler, which handles row logical change records that contain the DML operation in the `OPERATION_NAME` column on the object                                                                                                                           |
| `ERROR_HANDLER`       | `VARCHAR2(1)`   |            | Indicates whether the DML handler handles only the relevant row logical change records that result in apply errors (`Y`) or all relevant row logical change records (`N`)                                                                                                              |
| `APPLY_DATABASE_LINK` | `VARCHAR2(128)` |            | Database link to which changes are applied. If null, then changes are applied to the local database.                                                                                                                                                                                   |
| `APPLY_NAME`          | `VARCHAR2(128)` |            | Name of the apply process for the given object                                                                                                                                                                                                                                         |
| `ASSEMBLE_LOBS`       | `VARCHAR2(1)`   |            | Indicates whether LOB assembly is used for LOB columns in logical change records (LCRs) processed by the handler (`Y`) or not (`N`)<br>LOB assembly combines multiple LCRs for a LOB column resulting from a single row change into one row LCR before passing the LCR to the handler. |
| `SET_BY`              | `VARCHAR2(10)`  |            | Entity that set up the handler. Possible values include:<br>• `GOLDENGATE`<br>• `USER`                                                                                                                                                                                                 |

**See Also:**

- "[DBA_APPLY_DML_HANDLERS](DBA_APPLY_DML_HANDLERS.md)"

- [Oracle Database XStream Guide](../xstrm/xstream-in-concepts.md) for more information about DML handlers in an Oracle XStream environment
