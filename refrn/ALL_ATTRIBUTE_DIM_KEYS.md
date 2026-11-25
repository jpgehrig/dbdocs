## 2.85 ALL_ATTRIBUTE_DIM_KEYS

`ALL_ATTRIBUTE_DIM_KEYS` describes the keys of the attribute dimensions accessible to the current user.

### Related Views

- `DBA_ATTRIBUTE_DIM_KEYS` describes the keys of all attribute dimensions in the database.

- `USER_ATTRIBUTE_DIM_KEYS` describes the keys of the attribute dimensions owned by the current user. This view does not display the `OWNER` column.

| Column           | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                    |
|:-----------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the attribute dimension                                                                                                                                                                                                                                                                               |
| `DIMENSION_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the attribute dimension                                                                                                                                                                                                                                                                                |
| `LEVEL_NAME`     | `VARCHAR2(128)` |            | Name of the level of the key                                                                                                                                                                                                                                                                                   |
| `IS_ALTERNATE`   | `VARCHAR2(1)`   |            | Indicates whether the attribute dimension key is an alternate key (`Y`) or not (`N`)                                                                                                                                                                                                                           |
| `ATTRIBUTE_NAME` | `VARCHAR2(128)` |            | Name of the key attribute                                                                                                                                                                                                                                                                                      |
| `ATTR_ORDER_NUM` | `NUMBER`        | `NOT NULL` | Order of the attribute in the list of attributes comprising the key                                                                                                                                                                                                                                            |
| `KEY_ORDER_NUM`  | `NUMBER`        | `NOT NULL` | Order of the key in the list of keys (if alternate keys are specified)                                                                                                                                                                                                                                         |
| `ORIGIN_CON_ID`  | `NUMBER`        |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root). |

**See Also:**

- "[DBA_ATTRIBUTE_DIM_KEYS](DBA_ATTRIBUTE_DIM_KEYS.md)"

- "[USER_ATTRIBUTE_DIM_KEYS](USER_ATTRIBUTE_DIM_KEYS.md)"
