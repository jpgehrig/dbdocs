## 2.161 ALL_DIM_HIERARCHIES

`ALL_DIM_HIERARCHIES` describes all dimension hierarchies accessible to the current user.

### Related Views

- `DBA_DIM_HIERARCHIES` describes all such hierarchies in the database.

- `USER_DIM_HIERARCHIES` describes all such hierarchies owned by the current user.

| Column           | Datatype        | NULL       | Description            |
|:-----------------|:----------------|:-----------|:-----------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the dimension |
| `DIMENSION_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the dimension  |
| `HIERARCHY_NAME` | `VARCHAR2(128)` |            | Hierarchy name         |

**See Also:**

- "[DBA_DIM_HIERARCHIES](DBA_DIM_HIERARCHIES.md)"

- "[USER_DIM_HIERARCHIES](USER_DIM_HIERARCHIES.md)"
