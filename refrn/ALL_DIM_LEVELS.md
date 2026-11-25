## 2.164 ALL_DIM_LEVELS

`ALL_DIM_LEVELS` describes the dimension levels accessible to the current user. All columns of a dimension level must come from the same relation.

### Related Views

- `DBA_DIM_LEVELS` describes all dimension levels in the database.

- `USER_DIM_LEVELS` describes the levels of all dimensions owned by the current user.

| Column            | Datatype        | NULL       | Description                                                                                 |
|:------------------|:----------------|:-----------|:--------------------------------------------------------------------------------------------|
| `OWNER`           | `VARCHAR2(128)` | `NOT NULL` | Owner of the dimension                                                                      |
| `DIMENSION_NAME`  | `VARCHAR2(128)` | `NOT NULL` | Name of the dimension                                                                       |
| `LEVEL_NAME`      | `VARCHAR2(128)` |            | Unique within a dimension                                                                   |
| `NUM_COLUMNS`     | `NUMBER`        |            | Number of columns in the level definition                                                   |
| `DETAILOBJ_OWNER` | `VARCHAR2(128)` | `NOT NULL` | Owner of the detail object that the keys of this level come from                            |
| `DETAILOBJ_NAME`  | `VARCHAR2(128)` | `NOT NULL` | Name of the table that the keys of this level come from                                     |
| `SKIP_WHEN_NULL`  | `VARCHAR2(1)`   |            | Indicates whether the level is declared with the `SKIP WHEN NULL` clause (`Y`) or not (`N`) |

**See Also:**

- "[DBA_DIM_LEVELS](DBA_DIM_LEVELS.md)"

- "[USER_DIM_LEVELS](USER_DIM_LEVELS.md)"
