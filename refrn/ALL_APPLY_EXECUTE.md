## 2.62 ALL_APPLY_EXECUTE

`ALL_APPLY_EXECUTE` displays information about the apply execute actions for the rules visible to the current user.

### Related View

`DBA_APPLY_EXECUTE` displays information about the apply execute actions for all rules in the database.

| Column          | Datatype        | NULL       | Description                                                 |
|:----------------|:----------------|:-----------|:------------------------------------------------------------|
| `RULE_OWNER`    | `VARCHAR2(128)` | `NOT NULL` | Owner of the rule                                           |
| `RULE_NAME`     | `VARCHAR2(128)` | `NOT NULL` | Name of the rule                                            |
| `EXECUTE_EVENT` | `VARCHAR2(2)`   |            | Indicates whether the event satisfying the rule is executed |

**See Also:**

"[DBA_APPLY_EXECUTE](DBA_APPLY_EXECUTE.md)"
