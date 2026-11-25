## 2.126 ALL_COL_PRIVS

`ALL_COL_PRIVS` describes the following types of grants:

- Column object grants for which the current user is the object owner, grantor, or grantee

- Column object grants for which an enabled role or `PUBLIC` is the grantee

### Related Views

- `DBA_COL_PRIVS` describes all column object grants in the database.

- `USER_COL_PRIVS` describes the column object grants for which the current user is the object owner, grantor, or grantee.

| Column         | Datatype        | NULL | Description                                                                                                                                                                                                  |
|:---------------|:----------------|:-----|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `GRANTOR`      | `VARCHAR2(128)` |      | Name of the user who performed the grant                                                                                                                                                                     |
| `GRANTEE`      | `VARCHAR2(128)` |      | Name of the user or role to whom access was granted                                                                                                                                                          |
| `TABLE_SCHEMA` | `VARCHAR2(128)` |      | Schema of the object                                                                                                                                                                                         |
| `TABLE_NAME`   | `VARCHAR2(128)` |      | Name of the object                                                                                                                                                                                           |
| `COLUMN_NAME`  | `VARCHAR2(128)` |      | Name of the column                                                                                                                                                                                           |
| `PRIVILEGE`    | `VARCHAR2(40)`  |      | Privilege on the column:<br>• `INSERT`<br>• `REFERENCES`<br>• `UPDATE`                                                                                                                                       |
| `GRANTABLE`    | `VARCHAR2(3)`   |      | Indicates whether the privilege was granted with the `GRANT OPTION` (`YES`) or not (`NO`)                                                                                                                    |
| `COMMON`       | `VARCHAR2(3)`   |      | Indicates how the grant was made. Possible values:<br>• `YES` if the privilege was granted commonly (`CONTAINER=ALL` was used)<br>• `NO` if the privilege was granted locally (`CONTAINER=ALL` was not used) |
| `INHERITED`    | `VARCHAR2(3)`   |      | Indicates whether the privilege grant was inherited from another container (`YES`) or not (`NO`)                                                                                                             |

**See Also:**

- "[DBA_COL_PRIVS](DBA_COL_PRIVS.md)"

- "[USER_COL_PRIVS](USER_COL_PRIVS.md)"
