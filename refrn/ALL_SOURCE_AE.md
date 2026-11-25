## 3.74 ALL_SOURCE_AE

`ALL_SOURCE_AE` describes the text source of the stored objects (across all editions) accessible to the current user.

### Related Views

- `DBA_SOURCE_AE` describes the text source of all stored objects (across all editions) in the database.

- `USER_SOURCE_AE` describes the text source of the stored objects (across all editions) owned by the current user. This view does not display the `OWNER` column.

| Column          | Datatype         | NULL | Description                                                                                                                                                                                                                                                                                                   |
|:----------------|:-----------------|:-----|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`         | `VARCHAR2(128)`  |      | Owner of the object                                                                                                                                                                                                                                                                                           |
| `NAME`          | `VARCHAR2(128)`  |      | Name of the object                                                                                                                                                                                                                                                                                            |
| `TYPE`          | `VARCHAR2(12)`   |      | Type of the object:<br>• `ASSEMBLEY`<br>• `FUNCTION`<br>• `LIBRARY`<br>• `PACKAGE`<br>• `PACKAGE` `BODY`<br>• `PROCEDURE`<br>• `TRIGGER`<br>• `TYPE`<br>• `TYPE` `BODY`                                                                                                                                       |
| `LINE`          | `NUMBER`         |      | Line number of this line of source                                                                                                                                                                                                                                                                            |
| `TEXT`          | `VARCHAR2(4000)` |      | Source text                                                                                                                                                                                                                                                                                                   |
| `EDITION_NAME`  | `VARCHAR2(128)`  |      | Name of the edition                                                                                                                                                                                                                                                                                           |
| `ORIGIN_CON_ID` | `NUMBER`         |      | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root) |

**See Also:**

- "[DBA_SOURCE_AE](DBA_SOURCE_AE.md)"

- "[USER_SOURCE_AE](USER_SOURCE_AE.md)"
