## 2.239 ALL_JAVA_IMPLEMENTS

`ALL_JAVA_IMPLEMENTS` describes interfaces implemented by the stored Java classes accessible to the current user.

### Related Views

- `DBA_JAVA_IMPLEMENTS` describes interfaces implemented by all stored Java classes in the database.

- `USER_JAVA_IMPLEMENTS` describes interfaces implemented by the stored Java classes owned by the current user. This view does not display the `OWNER` column.

| Column            | Datatype         | NULL       | Description                                                      |
|:------------------|:-----------------|:-----------|:-----------------------------------------------------------------|
| `OWNER`           | `VARCHAR2(128)`  | `NOT NULL` | Owner of the Java class                                          |
| `NAME`            | `VARCHAR2(4000)` |            | Name of the Java class                                           |
| `INTERFACE_INDEX` | `NUMBER`         |            | Index of the interfaces implemented by the Java class            |
| `INTERFACE_NAME`  | `VARCHAR2(4000)` |            | Name of the interface identified by the `INTERFACE_INDEX` column |

**See Also:**

- "[DBA_JAVA_IMPLEMENTS](DBA_JAVA_IMPLEMENTS.md)"

- "[USER_JAVA_IMPLEMENTS](USER_JAVA_IMPLEMENTS.md)"
