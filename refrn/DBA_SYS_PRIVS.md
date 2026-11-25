## 6.29 DBA_SYS_PRIVS

`DBA_SYS_PRIVS` describes system privileges granted to users and roles.

| Column         | Datatype        | NULL | Description                                                                                                                                                                                                  |
|:---------------|:----------------|:-----|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `GRANTEE`      | `VARCHAR2(128)` |      | Grantee name, user, or role receiving the grant                                                                                                                                                              |
| `PRIVILEGE`    | `VARCHAR2(40)`  |      | System privilege                                                                                                                                                                                             |
| `ADMIN_OPTION` | `VARCHAR2(3)`   |      | Indicates whether the grant was with the `ADMIN` option (`YES`) or not (`NO`)                                                                                                                                |
| `COMMON`       | `VARCHAR2(3)`   |      | Indicates how the grant was made. Possible values:<br>• `YES` if the privilege was granted commonly (`CONTAINER=ALL` was used)<br>• `NO` if the privilege was granted locally (`CONTAINER=ALL` was not used) |
| `INHERITED`    | `VARCHAR2(3)`   |      | Indicates whether the grant was inherited from another container (`YES`) or not (`NO`)                                                                                                                       |

**See Also:**

"[USER_SYS_PRIVS](USER_SYS_PRIVS.md)"
