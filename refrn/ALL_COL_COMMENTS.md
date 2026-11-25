## 2.124 ALL_COL_COMMENTS

`ALL_COL_COMMENTS` displays comments on the columns of the tables and views accessible to the current user.

### Related Views

- `DBA_COL_COMMENTS` displays comments on the columns of all tables and views in the database.

- `USER_COL_COMMENTS` displays comments on the columns of the tables and views owned by the current user. This view does not display the `OWNER` column.

| Column          | Datatype         | NULL       | Description                                                                                                                                                                                                                                                                                           |
|:----------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`         | `VARCHAR2(128)`  | `NOT NULL` | Owner of the object                                                                                                                                                                                                                                                                                   |
| `TABLE_NAME`    | `VARCHAR2(128)`  | `NOT NULL` | Name of the object                                                                                                                                                                                                                                                                                    |
| `COLUMN_NAME`   | `VARCHAR2(128)`  | `NOT NULL` | Name of the column                                                                                                                                                                                                                                                                                    |
| `COMMENTS`      | `VARCHAR2(4000)` |            | Comment on the column                                                                                                                                                                                                                                                                                 |
| `ORIGIN_CON_ID` | `NUMBER`         |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs<br>• n: This value is used for rows containing data that originate in the container with the ID n (n=1 if the data originates in root) |

**See Also:**

- "[DBA_COL_COMMENTS](DBA_COL_COMMENTS.md)"

- "[USER_COL_COMMENTS](USER_COL_COMMENTS.md)"
