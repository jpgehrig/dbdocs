## 3.73 ALL_SOURCE

`ALL_SOURCE` describes the text source of the stored objects accessible to the current user.

### Related Views

- `DBA_SOURCE` describes the text source of all stored objects in the database.

- `USER_SOURCE` describes the text source of the stored objects owned by the current user. This view does not display the `OWNER` column.

| Column          | Datatype         | NULL       | Description                                                                                                                                                                                                                                                                                                   |
|:----------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`         | `VARCHAR2(128)`  | `NOT NULL` | Owner of the object                                                                                                                                                                                                                                                                                           |
| `NAME`          | `VARCHAR2(128)`  | `NOT NULL` | Name of the object                                                                                                                                                                                                                                                                                            |
| `TYPE`          | `VARCHAR2(12)`   |            | Type of object:<br>• `ASSEMBLEY`<br>• `FUNCTION`<br>• `LIBRARY`<br>• `PACKAGE`<br>• `PACKAGE` `BODY`<br>• `PROCEDURE`<br>• `TRIGGER`<br>• `TYPE`<br>• `TYPE` `BODY`                                                                                                                                           |
| `LINE`          | `NUMBER`         | `NOT NULL` | Line number of this line of source                                                                                                                                                                                                                                                                            |
| `TEXT`          | `VARCHAR2(4000)` |            | Text source of the stored object                                                                                                                                                                                                                                                                              |
| `ORIGIN_CON_ID` | `VARCHAR2(256)`  |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root) |

**See Also:**

- "[DBA_SOURCE](DBA_SOURCE.md)"

- "[USER_SOURCE](USER_SOURCE.md)"
