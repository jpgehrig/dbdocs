## 2.147 ALL_CUBE_HIER_VIEWS

`ALL_CUBE_HIER_VIEWS` describes the hierarchies for the OLAP cube dimensions accessible to the current user.

### Related Views

- `DBA_CUBE_HIER_VIEWS` describes the hierarchies for all OLAP cube dimensions in the database.

- `USER_CUBE_HIER_VIEWS` describes the hierarchies for the OLAP cube dimensions owned by the current user. This view does not display the `OWNER` column.

| Column           | Datatype        | NULL       | Description                                                    |
|:-----------------|:----------------|:-----------|:---------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the cube dimension                                    |
| `DIMENSION_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of a cube dimension, such as `TIME`                       |
| `HIERARCHY_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of a hierarchy for the cube dimension, such as `CALENDAR` |
| `VIEW_NAME`      | `VARCHAR2(128)` | `NOT NULL` | Name of a view of the hierarchy, such as `TIME_CALENDAR_VIEW`  |

**See Also:**

- "[DBA_CUBE_HIER_VIEWS](DBA_CUBE_HIER_VIEWS.md)"

- "[USER_CUBE_HIER_VIEWS](USER_CUBE_HIER_VIEWS.md)"
