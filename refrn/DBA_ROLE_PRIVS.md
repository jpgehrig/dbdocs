## 5.291 DBA_ROLE_PRIVS

`DBA_ROLE_PRIVS` describes the roles granted to all users and roles in the database.

### Related View

`USER_ROLE_PRIVS` describes the roles granted to the current user.

| Column            | Datatype        | NULL | Description                                                                                                                                                                                        |
|:------------------|:----------------|:-----|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `GRANTEE`         | `VARCHAR2(128)` |      | Name of the user or role receiving the grant                                                                                                                                                       |
| `GRANTED_ROLE`    | `VARCHAR2(128)` |      | Granted role name                                                                                                                                                                                  |
| `ADMIN_OPTION`    | `VARCHAR2(3)`   |      | Indicates whether the grant was with the `ADMIN OPTION` (`YES`) or not (`NO`)                                                                                                                      |
| `DELEGATE_OPTION` | `VARCHAR2(3)`   |      | Indicates whether the grant was with the `DELEGATE OPTION` (`YES`) or not (`NO`)                                                                                                                   |
| `DEFAULT_ROLE `   | `VARCHAR2(3)`   |      | Indicates whether the role is designated as a `DEFAULT ROLE` for the user (`YES`) or not (`NO`)                                                                                                    |
| `COMMON`          | `VARCHAR2(3)`   |      | Indicates how the grant was made. Possible values:<br>• `YES` if the role was granted commonly (`CONTAINER=ALL` was used)<br>• `NO` if the role was granted locally (`CONTAINER=ALL` was not used) |
| `INHERITED`       | `VARCHAR2(3)`   |      | Indicates whether the role grant was inherited from another container (`YES`) or not (`NO`)                                                                                                        |

**See Also:**

"[USER_ROLE_PRIVS](USER_ROLE_PRIVS.md)"
