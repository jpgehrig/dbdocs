## 3.106 ALL_TAB_COMMENTS

`ALL_TAB_COMMENTS` displays comments on the tables and views accessible to the current user.

### Related Views

- `DBA_TAB_COMMENTS` displays comments on all tables and views in the database.

- `USER_TAB_COMMENTS` displays comments on the tables and views owned by the current user. This view does not display the `OWNER` column.

| Column          | Datatype         | NULL       | Description                                                                                                                                                                                                                                                                                           |
|:----------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`         | `VARCHAR2(128)`  | `NOT NULL` | Owner of the object                                                                                                                                                                                                                                                                                   |
| `TABLE_NAME`    | `VARCHAR2(128)`  | `NOT NULL` | Name of the object                                                                                                                                                                                                                                                                                    |
| `TABLE_TYPE`    | `VARCHAR2(11)`   |            | Type of the object                                                                                                                                                                                                                                                                                    |
| `COMMENTS`      | `VARCHAR2(4000)` |            | Comment on the object                                                                                                                                                                                                                                                                                 |
| `ORIGIN_CON_ID` | `NUMBER`         |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs<br>• n: This value is used for rows containing data that originate in the container with the ID n (n=1 if the data originates in root) |

**See Also:**

- "[DBA_TAB_COMMENTS](DBA_TAB_COMMENTS.md)"

- "[USER_TAB_COMMENTS](USER_TAB_COMMENTS.md)"
