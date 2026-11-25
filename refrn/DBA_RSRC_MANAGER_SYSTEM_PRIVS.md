## 5.306 DBA_RSRC_MANAGER_SYSTEM_PRIVS

`DBA_RSRC_MANAGER_SYSTEM_PRIVS` displays information about all the users and roles that have been granted the `ADMINISTER_RESOURCE_MANAGER` system privilege, which is granted using the `DBMS_RESOURCE_MANAGER_PRIVS` package.

This privilege is not granted through the `GRANT` SQL statement.

### Related View

`USER_RSRC_MANAGER_SYSTEM_PRIVS` displays information about the users who are granted system privileges for the `DBMS_RESOURCE_MANAGER` package. This view does not display the `GRANTEE` column.

| Column         | Datatype        | NULL       | Description                                                                   |
|:---------------|:----------------|:-----------|:------------------------------------------------------------------------------|
| `GRANTEE`      | `VARCHAR2(128)` | `NOT NULL` | User or role receiving the grant                                              |
| `PRIVILEGE`    | `VARCHAR2(40)`  | `NOT NULL` | Name of the system privilege                                                  |
| `ADMIN_OPTION` | `VARCHAR2(3)`   |            | Indicates whether the grant was with the `ADMIN` option (`YES`) or not (`NO`) |

**See Also:**

- "[USER_RSRC_MANAGER_SYSTEM_PRIVS](USER_RSRC_MANAGER_SYSTEM_PRIVS.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md) for more information about the `DBMS_RESOURCE_MANAGER` package
