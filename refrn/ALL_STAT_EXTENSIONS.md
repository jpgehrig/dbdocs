## 3.85 ALL_STAT_EXTENSIONS

`ALL_STAT_EXTENSIONS` displays information about the optimizer statistics extensions accessible to the current user.

### Related Views

- `DBA_STAT_EXTENSIONS` displays information about all optimizer statistics extensions in the database.

- `USER_STAT_EXTENSIONS` displays information about the optimizer statistics extensions owned by the current user. This view does not display the `OWNER` column.

| Column           | Datatype        | NULL       | Description                                                                                               |
|:-----------------|:----------------|:-----------|:----------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the extension                                                                                    |
| `TABLE_NAME`     | `VARCHAR2(128)` | `NOT NULL` | Name of the table to which the extension belongs                                                          |
| `EXTENSION_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the statistics extension                                                                          |
| `EXTENSION`      | `CLOB`          |            | Extension (the expression or column group)                                                                |
| `CREATOR`        | `VARCHAR2(6)`   |            | Creator of the extension:<br>• `USER`<br>• `SYSTEM`                                                       |
| `DROPPABLE`      | `VARCHAR2(3)`   |            | Indicates whether the extension is droppable using `DBMS_STATS.DROP_EXTENDED_STATS` (`YES`) or not (`NO`) |

**See Also:**

- "[DBA_STAT_EXTENSIONS](DBA_STAT_EXTENSIONS.md)"

- "[USER_STAT_EXTENSIONS](USER_STAT_EXTENSIONS.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md) for more information about the `DBMS_STATS.DROP_EXTENDED_STATS` procedure
