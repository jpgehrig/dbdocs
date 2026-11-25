## 3.130 ALL_TYPE_VERSIONS

`ALL_TYPE_VERSIONS` describes the versions of the object types accessible to the current user.

### Related Views

- `DBA_TYPE_VERSIONS` describes the versions of all object types in the database.

- `USER_TYPE_VERSIONS` describes the versions of the object types owned by the current user. This view does not display the `OWNER` column.

| Column      | Datatype         | NULL       | Description                                                |
|:------------|:-----------------|:-----------|:-----------------------------------------------------------|
| `OWNER`     | `VARCHAR2(128)`  | `NOT NULL` | Owner of the type                                          |
| `TYPE_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Name of the type                                           |
| `VERSION#`  | `NUMBER`         | `NOT NULL` | Internal version number of the type                        |
| `TYPECODE`  | `VARCHAR2(128)`  |            | Typecode of the type                                       |
| `STATUS`    | `VARCHAR2(7)`    |            | Status of the type:<br>• `N/A`<br>• `VALID`<br>• `INVALID` |
| `LINE`      | `NUMBER`         | `NOT NULL` | Line number of the type's spec                             |
| `TEXT`      | `VARCHAR2(4000)` |            | Text of the type's spec                                    |
| `HASHCODE`  | `RAW(17)`        |            | Hashcode of the type                                       |

**See Also:**

- "[DBA_TYPE_VERSIONS](DBA_TYPE_VERSIONS.md)"

- "[USER_TYPE_VERSIONS](USER_TYPE_VERSIONS.md)"
