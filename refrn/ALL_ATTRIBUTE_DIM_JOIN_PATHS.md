## 2.84 ALL_ATTRIBUTE_DIM_JOIN_PATHS

`ALL_ATTRIBUTE_DIM_JOIN_PATHS` describes the join paths for the attribute dimensions accessible to the current user.

### Related Views

- `DBA_ATTRIBUTE_DIM_JOIN_PATHS` describes the join paths for all attribute dimensions in the database.

- `USER_ATTRIBUTE_DIM_JOIN_PATHS` describes the join paths for the attribute dimensions owned by the current user. This view does not display the `OWNER` column.

| Column           | Datatype         | NULL       | Description                                                                                                                                                                                                                                                                                                    |
|:-----------------|:-----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)`  | `NOT NULL` | Owner of the attribute dimension                                                                                                                                                                                                                                                                               |
| `DIMENSION_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Name of the attribute dimension                                                                                                                                                                                                                                                                                |
| `JOIN_PATH_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Name of the join path                                                                                                                                                                                                                                                                                          |
| `ON_CONDITION`   | `VARCHAR2(4000)` |            | Join condition specified in the `ON` clause                                                                                                                                                                                                                                                                    |
| `ORDER_NUM`      | `NUMBER`         | `NOT NULL` | Order of the classification in the list of classifications associated with the attribute dimension                                                                                                                                                                                                             |
| `ORIGIN_CON_ID`  | `NUMBER`         |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root). |

**See Also:**

- "[DBA_ATTRIBUTE_DIM_JOIN_PATHS](DBA_ATTRIBUTE_DIM_JOIN_PATHS.md)"

- "[USER_ATTRIBUTE_DIM_JOIN_PATHS](USER_ATTRIBUTE_DIM_JOIN_PATHS.md)"
