## 6.262 USABLE_EDITIONS

`USABLE_EDITIONS` describes the usable editions of the current user.

| Column                | Datatype        | NULL       | Description                                 |
|:----------------------|:----------------|:-----------|:--------------------------------------------|
| `EDITION_NAME`        | `VARCHAR2(128)` | `NOT NULL` | Name of the edition                         |
| `PARENT_EDITION_NAME` | `VARCHAR2(128)` |            | Name of the parent edition for this edition |

**See Also:**

[Oracle Database Development Guide](../adfns/editions.md) for more information about editions
