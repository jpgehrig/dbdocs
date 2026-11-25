## 2.63 ALL_APPLY_HANDLE_COLLISIONS

`ALL_APPLY_HANDLE_COLLISIONS` provides details about apply handlers for collisions on objects visible to the user at the table level.

### Related View

`DBA_APPLY_HANDLE_COLLISIONS` provides details about apply handlers for collisions at the table level.

| Column                | Datatype        | NULL       | Description                                                        |
|:----------------------|:----------------|:-----------|:-------------------------------------------------------------------|
| `APPLY_NAME`          | `VARCHAR2(128)` | `NOT NULL` | Name of the apply process                                          |
| `OBJECT_OWNER`        | `VARCHAR2(128)` | `NOT NULL` | Owner of the target object                                         |
| `OBJECT_NAME`         | `VARCHAR2(128)` | `NOT NULL` | Name of the target object                                          |
| `SOURCE_OBJECT_OWNER` | `VARCHAR2(128)` | `NOT NULL` | Source database owner of the object                                |
| `SOURCE_OBJECT_NAME`  | `VARCHAR2(128)` | `NOT NULL` | Source database name of the object                                 |
| `ENABLED`             | `VARCHAR2(1)`   | `NOT NULL` | State of the collision handlers: `Y` for enabled, `N` for disabled |
| `SET_BY`              | `VARCHAR2(10)`  |            | Entity that set up the handler:<br>• `USER`<br>• `GOLDENGATE`      |

**See Also:**

"[DBA_APPLY_HANDLE_COLLISIONS](DBA_APPLY_HANDLE_COLLISIONS.md)"
