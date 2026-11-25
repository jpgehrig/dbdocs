## 3.140 ALL_WARNING_SETTINGS

`ALL_WARNING_SETTINGS` displays information about the warning parameter settings for the objects accessible to the current user.

### Related Views

- `DBA_WARNING_SETTINGS` displays information about the warning parameter settings for all objects in the database.

- `USER_WARNING_SETTINGS` displays information about the warning parameter settings for the objects owned by the current user. This view does not display the `OWNER` column.

| Column        | Datatype        | NULL       | Description                                                                                                                         |
|:--------------|:----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`       | `VARCHAR2(128)` | `NOT NULL` | Owner of the object                                                                                                                 |
| `OBJECT_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the object                                                                                                                  |
| `OBJECT_ID`   | `NUMBER`        | `NOT NULL` | Object number of the object                                                                                                         |
| `OBJECT_TYPE` | `VARCHAR2(12)`  |            | Type of the object:<br>• `PROCEDURE`<br>• `FUNCTION`<br>• `PACKAGE`<br>• `PACKAGE BODY`<br>• `TRIGGER`<br>• `TYPE`<br>• `TYPE BODY` |
| `WARNING`     | `VARCHAR2(40)`  |            | Warning number or category:<br>• `INFORMATIONAL`<br>• `PERFORMANCE`<br>• `SEVERE`<br>• `ALL`                                        |
| `SETTING`     | `VARCHAR2(7)`   |            | Value of the warning setting:<br>• `DISABLE`<br>• `ENABLE`<br>• `ERROR`                                                             |

**See Also:**

- "[DBA_WARNING_SETTINGS](DBA_WARNING_SETTINGS.md)"

- "[USER_WARNING_SETTINGS](USER_WARNING_SETTINGS.md)"
