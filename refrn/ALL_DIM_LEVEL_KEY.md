## 2.163 ALL_DIM_LEVEL_KEY

`ALL_DIM_LEVEL_KEY` describes a column of a dimension level accessible to the current user. The position of a column within a level is specified by `KEY_POSITION`.

### Related Views

- `DBA_DIM_LEVEL_KEY` describes all columns of dimension levels in the database.

- `USER_DIM_LEVEL_KEY` describes all columns of dimension levels owned by the current user.

| Column           | Datatype        | NULL       | Description                                         |
|:-----------------|:----------------|:-----------|:----------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the dimension                              |
| `DIMENSION_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the dimension                               |
| `LEVEL_NAME`     | `VARCHAR2(128)` |            | Name of the hierarchy level                         |
| `KEY_POSITION`   | `NUMBER`        | `NOT NULL` | Ordinal position of the key column within the level |
| `COLUMN_NAME`    | `VARCHAR2(128)` | `NOT NULL` | Name of the key column                              |

**See Also:**

- "[DBA_DIM_LEVEL_KEY](DBA_DIM_LEVEL_KEY.md)"

- "[USER_DIM_LEVEL_KEY](USER_DIM_LEVEL_KEY.md)"
