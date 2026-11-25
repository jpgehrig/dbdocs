## 2.92 ALL_ATTRIBUTE_DIM_LVL_CLASS

`ALL_ATTRIBUTE_DIM_LVL_CLASS` describes the level classifications of the attribute dimensions accessible to the current user.

### Related Views

- `DBA_ATTRIBUTE_DIM_LVL_CLASS` describes the level classifications of all attribute dimensions in the database.

- `USER_ATTRIBUTE_DIM_LVL_CLASS` describes the level classifications of the attribute dimensions owned by the current user. This view does not display the `OWNER` column.

| Column           | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                    |
|:-----------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the attribute dimension                                                                                                                                                                                                                                                                               |
| `DIMENSION_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the attribute dimension                                                                                                                                                                                                                                                                                |
| `LEVEL_NAME`     | `VARCHAR2(128)` |            | Name of the level                                                                                                                                                                                                                                                                                              |
| `CLASSIFICATION` | `VARCHAR2(128)` |            | Classification associated with the level                                                                                                                                                                                                                                                                       |
| `VALUE`          | `CLOB`          |            | Value of the classification, or NULL if not specified                                                                                                                                                                                                                                                          |
| `LANGUAGE`       | `VARCHAR2(64)`  |            | `NLS_LANGUAGE` value associated with the classification, or NULL if not specified                                                                                                                                                                                                                              |
| `ORDER_NUM`      | `NUMBER`        | `NOT NULL` | Order of the classification in the list of classifications associated with the level                                                                                                                                                                                                                           |
| `ORIGIN_CON_ID`  | `NUMBER`        |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root). |

**See Also:**

- "[DBA_ATTRIBUTE_DIM_LVL_CLASS](DBA_ATTRIBUTE_DIM_LVL_CLASS.md)"

- "[USER_ATTRIBUTE_DIM_LVL_CLASS](USER_ATTRIBUTE_DIM_LVL_CLASS.md)"
