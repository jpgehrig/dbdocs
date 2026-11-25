## 2.172 ALL_EDITIONS

`ALL_EDITIONS` describes the editions accessible to the current user.

### Related View

`DBA_EDITIONS` describes all editions in the database.

| Column                | Datatype        | NULL       | Description                                                        |
|:----------------------|:----------------|:-----------|:-------------------------------------------------------------------|
| `EDITION_NAME`        | `VARCHAR2(128)` | `NOT NULL` | Name of the edition                                                |
| `PARENT_EDITION_NAME` | `VARCHAR2(128)` |            | Name of the parent edition for this edition                        |
| `USABLE`              | `VARCHAR2(3)`   |            | Indicates whether the edition is usable (`YES`) or unusable (`NO`) |

**See Also:**

- "[DBA_EDITIONS](DBA_EDITIONS.md)"

- [Oracle Database Development Guide](../adfns/editions.md) for more information about editions
