## 2.96 ALL_ATTRIBUTE_DIM_ORD_ATRS_AE

`ALL_ATTRIBUTE_DIM_ORD_ATRS_AE` describes the order attributes of the attribute dimensions (across all editions) accessible to the current user.

### Related Views

- `DBA_ATTRIBUTE_DIM_ORD_ATRS_AE` describes the order attributes of all attribute dimensions (across all editions) in the database.

- `USER_ATTRIBUTE_DIM_ORD_ATRS_AE` describes the order attributes of the attribute dimensions (across all editions) owned by the current user. This view does not display the `OWNER` column.

| Column           | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                    |
|:-----------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the attribute dimension                                                                                                                                                                                                                                                                               |
| `DIMENSION_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the attribute dimension                                                                                                                                                                                                                                                                                |
| `LEVEL_NAME`     | `VARCHAR2(128)` |            | Name of the level to order or the name of the level that has the `ORDER` `BY` clause                                                                                                                                                                                                                           |
| `AGG_FUNC`       | `VARCHAR2(3)`   |            | Aggregation function of the `ORDER` `BY` clause:<br>• `MIN`<br>• `MAX`                                                                                                                                                                                                                                         |
| `ATTRIBUTE_NAME` | `VARCHAR2(128)` |            | Name of the order attribute                                                                                                                                                                                                                                                                                    |
| `ORDER_NUM`      | `NUMBER`        | `NOT NULL` | Order number of the attribute in the list of order attributes                                                                                                                                                                                                                                                  |
| `CRITERIA`       | `VARCHAR2(4)`   |            | Criteria of the ordering, either ascending or descending:<br>• `ASC`<br>• `DESC`                                                                                                                                                                                                                               |
| `NULLS_POSITION` | `VARCHAR2(5)`   |            | Position of `ORDER` `BY` values in the orderings:<br>• `FIRST`<br>• `LAST`                                                                                                                                                                                                                                     |
| `ORIGIN_CON_ID`  | `NUMBER`        |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root). |
| `EDITION_NAME`   | `VARCHAR2(128)` |            | Name of the application edition where the attribute dimension is defined                                                                                                                                                                                                                                       |

**Note:**

This view is available starting with Oracle Database 19c, Release Update 19.13.

**See Also:**

- "[DBA_ATTRIBUTE_DIM_ORD_ATRS_AE](DBA_ATTRIBUTE_DIM_ORD_ATRS_AE.md)"

- "[USER_ATTRIBUTE_DIM_ORD_ATRS_AE](USER_ATTRIBUTE_DIM_ORD_ATRS_AE.md)"
