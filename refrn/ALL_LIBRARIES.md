## 2.251 ALL_LIBRARIES

`ALL_LIBRARIES` describes the libraries accessible to the current user.

### Related Views

- `DBA_LIBRARIES` describes all libraries in the database.

- `USER_LIBRARIES` describes the libraries owned by the current user. This view does not display the `OWNER` column.

| Column          | Datatype         | NULL       | Description                                                                                                                                                                                                                                                                                                   |
|:----------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`         | `VARCHAR2(128)`  | `NOT NULL` | Owner of the library                                                                                                                                                                                                                                                                                          |
| `LIBRARY_NAME`  | `VARCHAR2(128)`  | `NOT NULL` | Library name                                                                                                                                                                                                                                                                                                  |
| `FILE_SPEC`     | `VARCHAR2(2000)` |            | Operating system file specification associated with the library                                                                                                                                                                                                                                               |
| `DYNAMIC`       | `VARCHAR2(1)`    |            | Indicates whether the library is dynamically loadable (`Y`) or not (`N`)                                                                                                                                                                                                                                      |
| `STATUS`        | `VARCHAR2(7)`    |            | Status of the library:<br>• `N/A`<br>• `VALID`<br>• `INVALID`                                                                                                                                                                                                                                                 |
| `AGENT`         | `VARCHAR2(128)`  |            | Agent of the library                                                                                                                                                                                                                                                                                          |
| `LEAF_FILENAME` | `VARCHAR2(2000)` |            | Leaf filename of the library                                                                                                                                                                                                                                                                                  |
| `ORIGIN_CON_ID` | `VARCHAR2(256)`  |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root) |

**See Also:**

- "[DBA_LIBRARIES](DBA_LIBRARIES.md)"

- "[USER_LIBRARIES](USER_LIBRARIES.md)"
