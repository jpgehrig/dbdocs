## 2.245 ALL_JAVA_THROWS

`ALL_JAVA_THROWS` displays information about exceptions thrown from methods of the Java classes accessible to the current user.

### Related Views

- `DBA_JAVA_THROWS` displays information about exceptions thrown from methods of all Java classes in the database.

- `USER_JAVA_THROWS` displays information about exceptions thrown from methods of the Java classes owned by the current user. This view does not display the `OWNER` column.

| Column            | Datatype         | NULL       | Description                                   |
|:------------------|:-----------------|:-----------|:----------------------------------------------|
| `OWNER`           | `VARCHAR2(128)`  | `NOT NULL` | Owner of the Java class                       |
| `NAME`            | `VARCHAR2(4000)` |            | Name of the Java class                        |
| `METHOD_INDEX`    | `NUMBER`         |            | Index of the throwing method of the exception |
| `METHOD_NAME`     | `VARCHAR2(4000)` |            | Name of the throwing method of the exception  |
| `EXCEPTION_INDEX` | `NUMBER`         |            | Index of the exception                        |
| `EXCEPTION_CLASS` | `VARCHAR2(4000)` |            | Class of the exception                        |

**See Also:**

- "[DBA_JAVA_THROWS](DBA_JAVA_THROWS.md)"

- "[USER_JAVA_THROWS](USER_JAVA_THROWS.md)"
