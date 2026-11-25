## 2.236 ALL_JAVA_COMPILER_OPTIONS

`ALL_JAVA_COMPILER_OPTIONS` displays information about the native compiler options accessible to the current user.

### Related Views

- `DBA_JAVA_COMPILER_OPTIONS` displays information about all native compiler options in the database.

- `USER_JAVA_COMPILER_OPTIONS` displays information about the native compiler options owned by the current user. This view does not display the `OWNER` column.

| Column        | Datatype         | NULL       | Description                         |
|:--------------|:-----------------|:-----------|:------------------------------------|
| `OWNER`       | `VARCHAR2(128)`  | `NOT NULL` | Owner of the native compiler option |
| `OPTION_NAME` | `VARCHAR2(64)`   |            | Name of the native compiler option  |
| `VALUE`       | `VARCHAR2(4000)` |            | Value of the native compiler option |

**See Also:**

- "[DBA_JAVA_COMPILER_OPTIONS](DBA_JAVA_COMPILER_OPTIONS.md)"

- "[USER_JAVA_COMPILER_OPTIONS](USER_JAVA_COMPILER_OPTIONS.md)"
