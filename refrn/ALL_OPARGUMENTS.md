## 2.289 ALL_OPARGUMENTS

`ALL_OPARGUMENTS` describes arguments for each operator binding accessible to the current user.

### Related Views

- `DBA_OPARGUMENTS` describes arguments of all operator bindings in the database.

- `USER_OPARGUMENTS` describes arguments of all operator bindings owned by the current user.

| Column          | Datatype        | NULL       | Description                                      |
|:----------------|:----------------|:-----------|:-------------------------------------------------|
| `OWNER`         | `VARCHAR2(128)` | `NOT NULL` | Owner of the operator argument                   |
| `OPERATOR_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the operator argument                    |
| `BINDING#`      | `NUMBER`        | `NOT NULL` | Binding number of the operator argument          |
| `POSITION`      | `NUMBER`        | `NOT NULL` | Position of the operator argument (1, 2, 3, ...) |
| `ARGUMENT_TYPE` | `VARCHAR2(61)`  |            | Datatype of the operator argument                |

**See Also:**

- "[DBA_OPARGUMENTS](DBA_OPARGUMENTS.md)"

- "[USER_OPARGUMENTS](USER_OPARGUMENTS.md)"
