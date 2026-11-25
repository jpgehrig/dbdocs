## 2.123 ALL_CODE_ROLE_PRIVS

`ALL_CODE_ROLE_PRIVS` describes all the roles that are associated with program units owned or accessible by the current user.

### Related Views

- `DBA_CODE_ROLE_PRIVS` describes all the roles that are associated with program units in the database.

- `USER_CODE_ROLE_PRIVS` describes all the roles that are associated with program units owned by current user. This view does not display the `OWNER` column.

| Column        | Datatype        | NULL       | Description                         |
|:--------------|:----------------|:-----------|:------------------------------------|
| `OWNER`       | `VARCHAR2(128)` | `NOT NULL` | Username of the owner of the object |
| `OBJECT_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the object                  |
| `OBJECT_TYPE` | `VARCHAR2(9)`   |            | Type of the object                  |
| `ROLE`        | `VARCHAR2(128)` | `NOT NULL` | The role associated with the object |

**See Also:**

- "[DBA_CODE_ROLE_PRIVS](DBA_CODE_ROLE_PRIVS.md)"

- "[USER_CODE_ROLE_PRIVS](USER_CODE_ROLE_PRIVS.md)"

- [Oracle Database Security Guide](../dbseg/configuring-privilege-and-role-authorization.md) for more information about granting and revoking roles to and from program units
