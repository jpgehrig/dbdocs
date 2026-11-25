## 2.268 ALL_MINING_MODEL_VIEWS

`ALL_MINING_MODEL_VIEWS` provides a description of all the model views accessible to the user.

### Related Views

- `DBA_MINING_MODEL_VIEWS` provides a description of all the model views in the database.

- `USER_MINING_MODEL_VIEWS` provides a description of the user's own model views. This view does not display the `OWNER` column.

| Column       | Datatype        | NULL       | Description                                    |
|:-------------|:----------------|:-----------|:-----------------------------------------------|
| `OWNER`      | `VARCHAR2(128)` | `NOT NULL` | Owner of the model view                        |
| `MODEL_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the model to which model views belongs |
| `VIEW_NAME`  | `VARCHAR2(128)` | `NOT NULL` | Name of the model view                         |
| `VIEW_TYPE`  | `VARCHAR2(128)` | –          | Type of the model view                         |

**See Also:**

"[ALL_MINING_MODEL_VIEWS](../dmprg/data-mining-data-dictionary-vews.md)" in Oracle Data Mining User’s Guide
