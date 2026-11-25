## 2.166 ALL_DIRECTORIES

`ALL_DIRECTORIES` describes all directories accessible to the current user.

### Related View

`DBA_DIRECTORIES` describes all directories in the database.

| Column           | Datatype         | NULL       | Description                                                                                                                                                                                                                                                                                                   |
|:-----------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)`  | `NOT NULL` | Owner of the directory (always `SYS`)                                                                                                                                                                                                                                                                         |
| `DIRECTORY_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Name of the directory                                                                                                                                                                                                                                                                                         |
| `DIRECTORY_PATH` | `VARCHAR2(4000)` |            | Operating system pathname for the directory                                                                                                                                                                                                                                                                   |
| `ORIGIN_CON_ID`  | `VARCHAR2(256)`  |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root) |

**See Also:**

"[DBA_DIRECTORIES](DBA_DIRECTORIES.md)"
