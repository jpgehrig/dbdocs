## 2.206 ALL_HIER_JOIN_PATHS

`ALL_HIER_JOIN_PATHS` describes the join paths for the hierarchies accessible to the current user.

### Related Views

- `DBA_HIER_JOIN_PATHS` describes the join paths for all hierarchies in the database.

- `USER_HIER_JOIN_PATHS` describes the join paths for the hierarchies owned by the current user. This view does not display the `OWNER` column.

| Column           | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                    |
|:-----------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the hierarchy                                                                                                                                                                                                                                                                                         |
| `HIER_NAME`      | `VARCHAR2(128)` | `NOT NULL` | Name of the hierarchy                                                                                                                                                                                                                                                                                          |
| `JOIN_PATH_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the join path                                                                                                                                                                                                                                                                                          |
| `ORDER_NUM`      | `NUMBER`        | `NOT NULL` | Order of the classification in the list of join paths associated with the hierarchy                                                                                                                                                                                                                            |
| `ORIGIN_CON_ID`  | `NUMBER`        |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root). |

**See Also:**

- "[DBA_HIER_JOIN_PATHS](DBA_HIER_JOIN_PATHS.md)"

- "[USER_HIER_JOIN_PATHS](USER_HIER_JOIN_PATHS.md)"
