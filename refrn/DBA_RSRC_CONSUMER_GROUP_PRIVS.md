## 5.302 DBA_RSRC_CONSUMER_GROUP_PRIVS

`DBA_RSRC_CONSUMER_GROUP_PRIVS` displays information about all resource consumer groups and the users and roles assigned to them.

The grant referred to in this view and the related view is the grant of the `SWITCH_CONSUMER_GROUP` object privilege, which is granted using the `DBMS_RESOURCE_MANAGER_PRIVS` package. This privilege is not granted through the `GRANT` SQL statement.

### Related View

`USER_RSRC_CONSUMER_GROUP_PRIVS` displays information about the resource consumer groups to which the current user is assigned. This view does not display the `GRANTEE` column.

| Column          | Datatype        | NULL       | Description                                                                                                   |
|:----------------|:----------------|:-----------|:--------------------------------------------------------------------------------------------------------------|
| `GRANTEE`       | `VARCHAR2(128)` | `NOT NULL` | User or role receiving the grant                                                                              |
| `GRANTED_GROUP` | `VARCHAR2(128)` |            | Granted consumer group name                                                                                   |
| `GRANT_OPTION`  | `VARCHAR2(3)`   |            | Indicates whether the grant was with the `GRANT` option (`YES`) or not (`NO`)                                 |
| `INITIAL_GROUP` | `VARCHAR2(3)`   |            | Indicates whether the consumer group is designated as the default for this user or role (`YES`) or not (`NO`) |

**See Also:**

- "[USER_RSRC_CONSUMER_GROUP_PRIVS](USER_RSRC_CONSUMER_GROUP_PRIVS.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER_PRIVS.md) for more information about the `DBMS_RESOURCE_MANAGER_PRIVS` package
