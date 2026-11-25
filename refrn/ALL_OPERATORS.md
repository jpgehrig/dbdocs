## 2.292 ALL_OPERATORS

`ALL_OPERATORS` describes the operators accessible to the current user.

### Related Views

- `DBA_OPERATORS` describes all operators in the database.

- `USER_OPERATORS` describes the operators owned by the current user.

| Column            | Datatype        | NULL       | Description                                     |
|:------------------|:----------------|:-----------|:------------------------------------------------|
| `OWNER`           | `VARCHAR2(128)` | `NOT NULL` | Owner of the operator                           |
| `OPERATOR_NAME`   | `VARCHAR2(128)` | `NOT NULL` | Name of the operator                            |
| `NUMBER_OF_BINDS` | `NUMBER`        | `NOT NULL` | Number of bindings associated with the operator |

**See Also:**

- "[DBA_OPERATORS](DBA_OPERATORS.md)"

- "[USER_OPERATORS](USER_OPERATORS.md)"
