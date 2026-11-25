## 6.235 ROLE_SYS_PRIVS

`ROLE_SYS_PRIVS` describes system privileges granted to roles.

Information is provided only about roles to which the user has access.

| Column         | Datatype        | NULL | Description                                                                                                                                                                                                  |
|:---------------|:----------------|:-----|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ROLE`         | `VARCHAR2(128)` |      | Name of the role                                                                                                                                                                                             |
| `PRIVILEGE`    | `VARCHAR2(40)`  |      | System privilege granted to the role                                                                                                                                                                         |
| `ADMIN_OPTION` | `VARCHAR2(3)`   |      | Indicates whether the grant was with the `ADMIN` option (`YES`) or not (`NO`)                                                                                                                                |
| `COMMON`       | `VARCHAR2(3)`   |      | Indicates how the grant was made. Possible values:<br>• `YES` if the privilege was granted commonly (`CONTAINER=ALL` was used)<br>• `NO` if the privilege was granted locally (`CONTAINER=ALL` was not used) |
| `INHERITED`    | `VARCHAR2(3)`   |      | Indicates whether the role grant was inherited from another container (`YES`) or not (`NO`)                                                                                                                  |
