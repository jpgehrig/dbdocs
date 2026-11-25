## 2.152 ALL_CUBE_VIEW_COLUMNS

`ALL_CUBE_VIEW_COLUMNS` describes the columns of the relational views of the OLAP cubes accessible to the current user.

### Related Views

- `DBA_CUBE_VIEW_COLUMNS` describes the columns of relational views of all OLAP cubes in the database.

- `USER_CUBE_VIEW_COLUMNS` describes the columns of relational views of OLAP cubes owned by the current user. This view does not display the `OWNER` column.

| Column        | Datatype        | NULL | Description                                                     |
|:--------------|:----------------|:-----|:----------------------------------------------------------------|
| `OWNER`       | `VARCHAR2(128)` |      | Owner of the cube                                               |
| `CUBE_NAME`   | `VARCHAR2(128)` |      | Name of a cube, such as `UNITS_CUBE`                            |
| `VIEW_NAME`   | `VARCHAR2(128)` |      | Name of a view of the cube, such as `PRODUCT_VIEW`              |
| `COLUMN_NAME` | `VARCHAR2(128)` |      | Name of a column in the view, such as `DIM_KEY` or `LEVEL_NAME` |
| `COLUMN_TYPE` | `VARCHAR2(7)`   |      | Type of the column:<br>• `MEASURE`<br>• `KEY`                   |
| `OBJECT_NAME` | `VARCHAR2(128)` |      | Name of the measure or dimension represented in the column      |

**See Also:**

- "[DBA_CUBE_VIEW_COLUMNS](DBA_CUBE_VIEW_COLUMNS.md)"

- "[USER_CUBE_VIEW_COLUMNS](USER_CUBE_VIEW_COLUMNS.md)"
