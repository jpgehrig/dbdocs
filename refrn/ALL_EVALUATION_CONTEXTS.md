## 2.179 ALL_EVALUATION_CONTEXTS

`ALL_EVALUATION_CONTEXTS` describes the rule evaluation contexts accessible to the current user.

### Related Views

- `DBA_EVALUATION_CONTEXTS` describes all rule evaluation contexts in the database.

- `USER_EVALUATION_CONTEXTS` describes the rule evaluation contexts owned by the current user. This view does not display the `EVALUATION_CONTEXT_OWNER` column.

| Column                       | Datatype         | NULL       | Description                                                        |
|:-----------------------------|:-----------------|:-----------|:-------------------------------------------------------------------|
| `EVALUATION_CONTEXT_OWNER`   | `VARCHAR2(128)`  | `NOT NULL` | Owner of the evaluation context                                    |
| `EVALUATION_CONTEXT_NAME`    | `VARCHAR2(128)`  | `NOT NULL` | Name of the evaluation context                                     |
| `EVALUATION_FUNCTION`        | `VARCHAR2(4000)` |            | Evaluation function associated with the evaluation context, if any |
| `EVALUATION_CONTEXT_COMMENT` | `VARCHAR2(4000)` |            | Comment specified with the evaluation context, if any              |

**See Also:**

- "[DBA_EVALUATION_CONTEXTS](DBA_EVALUATION_CONTEXTS.md)"

- "[USER_EVALUATION_CONTEXTS](USER_EVALUATION_CONTEXTS.md)"
