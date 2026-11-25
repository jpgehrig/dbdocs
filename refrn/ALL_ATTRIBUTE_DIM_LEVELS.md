## 2.88 ALL_ATTRIBUTE_DIM_LEVELS

`ALL_ATTRIBUTE_DIM_LEVELS` describes the levels of the attribute dimensions accessible to the current user.

### Related Views

- `DBA_ATTRIBUTE_DIM_LEVELS` describes the levels of all attribute dimensions in the database.

- `USER_ATTRIBUTE_DIM_LEVELS` describes the levels of the attribute dimensions owned by the current user. This view does not display the `OWNER` column.

| Column                    | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                    |
|:--------------------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`                   | `VARCHAR2(128)` | `NOT NULL` | Owner of the attribute dimension                                                                                                                                                                                                                                                                               |
| `DIMENSION_NAME`          | `VARCHAR2(128)` | `NOT NULL` | Name of the attribute dimension                                                                                                                                                                                                                                                                                |
| `LEVEL_NAME`              | `VARCHAR2(128)` |            | Name of the attribute dimension level                                                                                                                                                                                                                                                                          |
| `SKIP_WHEN_NULL`          | `VARCHAR2(1)`   |            | Indicates whether to skip the level when the key is NULL; the value can be `Y` or `N`.                                                                                                                                                                                                                         |
| `LEVEL_TYPE`              | `VARCHAR2(10)`  |            | Type of attribute dimension level                                                                                                                                                                                                                                                                              |
| `MEMBER_NAME_EXPR`        | `CLOB`          | `NOT NULL` | Expression representing the level member name                                                                                                                                                                                                                                                                  |
| `MEMBER_CAPTION_EXPR`     | `CLOB`          |            | Expression representing the level member caption, or NULL if not specified                                                                                                                                                                                                                                     |
| `MEMBER_DESCRIPTION_EXPR` | `CLOB`          |            | Expression representing the level member description, or NULL if not specified                                                                                                                                                                                                                                 |
| `ORDER_NUM`               | `NUMBER`        | `NOT NULL` | Order of the level in the list of attribute dimension levels                                                                                                                                                                                                                                                   |
| `ORIGIN_CON_ID`           | `NUMBER`        |            | The ID of the container where the data originates. Possible values include:<br>• `0`: This value is used for rows in non-CDBs. This value is not used for CDBs.<br>• n: This value is used for rows containing data that originate in the container with container ID n (n = 1 if the row originates in root). |

**See Also:**

- "[DBA_ATTRIBUTE_DIM_LEVELS](DBA_ATTRIBUTE_DIM_LEVELS.md)"

- "[USER_ATTRIBUTE_DIM_LEVELS](USER_ATTRIBUTE_DIM_LEVELS.md)"
