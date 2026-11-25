## 2.176 ALL_ERRORS_AE

`ALL_ERRORS_AE` describes the current errors on the stored objects (across all editions) accessible to the current user.

### Related Views

- `DBA_ERRORS_AE` describes the current errors on all stored objects (across all editions) in the database.

- `USER_ERRORS_AE` describes the current errors on the stored objects (across all editions) owned by the current user. This view does not display the `OWNER` column.

| Column           | Datatype         | NULL       | Description                                                                                                                                                                                                                                                                                                                  |
|:-----------------|:-----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)`  | `NOT NULL` | Owner of the object                                                                                                                                                                                                                                                                                                          |
| `NAME`           | `VARCHAR2(128)`  | `NOT NULL` | Name of the object                                                                                                                                                                                                                                                                                                           |
| `TYPE`           | `VARCHAR2(12)`   |            | Type of the object:<br>• `ANALYTIC` `VIEW`<br>• `ASSEMBLY`<br>• `ATTRIBUTE` `DIMENSION`<br>• `DIMENSION`<br>• `FUNCTION`<br>• `HIERARCHY`<br>• `JAVA` `CLASS`<br>• `JAVA` `SOURCE`<br>• `LIBRARY`<br>• `PACKAGE`<br>• `PACKAGE` `BODY`<br>• `PROCEDURE`<br>• `QUEUE`<br>• `TRIGGER`<br>• `TYPE`<br>• `TYPE BODY`<br>• `VIEW` |
| `SEQUENCE`       | `NUMBER`         | `NOT NULL` | Sequence number (for ordering purposes)                                                                                                                                                                                                                                                                                      |
| `LINE`           | `NUMBER`         | `NOT NULL` | Line number at which this error occurred                                                                                                                                                                                                                                                                                     |
| `POSITION`       | `NUMBER`         | `NOT NULL` | Position in the line at which this error occurred                                                                                                                                                                                                                                                                            |
| `TEXT`           | `VARCHAR2(4000)` | `NOT NULL` | Text of the error                                                                                                                                                                                                                                                                                                            |
| `ATTRIBUTE`      | `VARCHAR2(9)`    |            | Indicates whether the error is an error (`ERROR`) or a warning (`WARNING`)                                                                                                                                                                                                                                                   |
| `MESSAGE_NUMBER` | `NUMBER`         |            | Numeric error number (without any prefix)                                                                                                                                                                                                                                                                                    |
| `EDITION_NAME`   | `VARCHAR2(128)`  |            | Name of the edition in which the object is actual                                                                                                                                                                                                                                                                            |

**See Also:**

- "[DBA_ERRORS_AE](DBA_ERRORS_AE.md)"

- "[USER_ERRORS_AE](USER_ERRORS_AE.md)"
