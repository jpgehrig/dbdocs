## 2.177 ALL_EVALUATION_CONTEXT_TABLES

`ALL_EVALUATION_CONTEXT_TABLES` describes the tables in the rule evaluation contexts accessible to the current user.

### Related Views

- `DBA_EVALUATION_CONTEXT_TABLES` describes the tables in all rule evaluation contexts in the database.

- `USER_EVALUATION_CONTEXT_TABLES` describes the tables in the rule evaluation contexts owned by the current user. This view does not display the `EVALUATION_CONTEXT_OWNER` column.

| Column                     | Datatype         | NULL       | Description                                      |
|:---------------------------|:-----------------|:-----------|:-------------------------------------------------|
| `EVALUATION_CONTEXT_OWNER` | `VARCHAR2(128)`  | `NOT NULL` | Owner of the evaluation context                  |
| `EVALUATION_CONTEXT_NAME`  | `VARCHAR2(128)`  | `NOT NULL` | Name of the evaluation context                   |
| `TABLE_ALIAS`              | `VARCHAR2(128)`  |            | Alias for a table in the evaluation context      |
| `TABLE_NAME`               | `VARCHAR2(4000)` |            | Name of the table referred to by the table alias |

**See Also:**

- "[DBA_EVALUATION_CONTEXT_TABLES](DBA_EVALUATION_CONTEXT_TABLES.md)"

- "[USER_EVALUATION_CONTEXT_TABLES](USER_EVALUATION_CONTEXT_TABLES.md)"
