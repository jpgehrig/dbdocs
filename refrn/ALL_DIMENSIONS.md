## 2.165 ALL_DIMENSIONS

`ALL_DIMENSIONS` describes the dimension objects accessible to the current user.

### Related Views

- `DBA_DIMENSIONS` describes all dimensions in the database.

- `USER_DIMENSIONS` describes the dimensions in the current user's schema.

| Column           | Datatype        | NULL       | Description                                                                       |
|:-----------------|:----------------|:-----------|:----------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the dimension                                                            |
| `DIMENSION_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the dimension                                                             |
| `INVALID`        | `VARCHAR2(1)`   |            | Indicates whether the dimension is invalid (`Y`) or valid (`N`)                   |
| `COMPILE_STATE`  | `VARCHAR2(13)`  |            | Compile status of the dimension:<br>• `INVALID`<br>• `NEEDS_COMPILE`<br>• `ERROR` |
| `REVISION`       | `NUMBER`        |            | Dimension revision level                                                          |

**See Also:**

- "[DBA_DIMENSIONS](DBA_DIMENSIONS.md)"

- "[USER_DIMENSIONS](USER_DIMENSIONS.md)"
