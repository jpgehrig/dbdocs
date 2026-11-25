## 6.91 DBA_USED_PRIVS

`DBA_USED_PRIVS` lists the privileges that are used for the privilege analysis policies reported by the `DBMS_PRIVILEGE_CAPTURE.GENERATE_RESULT` procedure.

This view provides access to analyzed privilege records in `SYS` tables.

You must have the `CAPTURE_ADMIN` role to access this view.

| Column         | Datatype        | NULL       | Description                                                                                                                                                                                                              |
|:---------------|:----------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CAPTURE`      | `VARCHAR2(128)` | `NOT NULL` | Name of a privilege analysis policy                                                                                                                                                                                      |
| `SEQUENCE`     | `NUMBER`        | `NOT NULL` | The sequence number of the privilege analysis run during which the privilege was reported                                                                                                                                |
| `OS_USER`      | `VARCHAR2(128)` |            | Operating system login username                                                                                                                                                                                          |
| `USERHOST`     | `VARCHAR2(128)` |            | Client host machine name                                                                                                                                                                                                 |
| `MODULE`       | `VARCHAR2(64)`  |            | Module name                                                                                                                                                                                                              |
| `USERNAME`     | `VARCHAR2(128)` | `NOT NULL` | Name of the user whose privilege was reported                                                                                                                                                                            |
| `USED_ROLE`    | `VARCHAR2(128)` |            | Used role                                                                                                                                                                                                                |
| `SYS_PRIV`     | `VARCHAR2(40)`  |            | Used system privilege                                                                                                                                                                                                    |
| `OBJ_PRIV`     | `VARCHAR2(40)`  |            | Used object privilege                                                                                                                                                                                                    |
| `USER_PRIV`    | `VARCHAR2(25)`  |            | Used user privilege                                                                                                                                                                                                      |
| `OBJECT_OWNER` | `VARCHAR2(128)` |            | Object owner                                                                                                                                                                                                             |
| `OBJECT_NAME`  | `VARCHAR2(128)` |            | Name of the object or user that `OBJ_PRIV` or `USER_PRIV` is used to access                                                                                                                                              |
| `OBJECT_TYPE`  | `VARCHAR2(23)`  |            | Type of the object or user that `OBJ_PRIV` or `USER_PRIV` is used to access                                                                                                                                              |
| `COLUMN_NAME`  | `VARCHAR2(128)` |            | Name of the column that `OBJ_PRIV` is used to access                                                                                                                                                                     |
| `OPTION$`      | `NUMBER`        |            | Indicates whether the `GRANT` option or the `ADMIN` option was used:<br>• `0` - Indicates that the `GRANT` option or `ADMIN` option was not used<br>• `1` - Indicates that the `GRANT` option or `ADMIN` option was used |
| `PATH`         | `GRANT_PATH`    |            | Used privilege grant paths                                                                                                                                                                                               |
| `RUN_NAME`     | `VARCHAR2(128)` |            | The name of the run during which the privilege was reported                                                                                                                                                              |

**See Also:**

- "[DBA_UNUSED_PRIVS](DBA_UNUSED_PRIVS.md)"

- [Oracle Database Security Guide](../dbseg/performing-privilege-analysis-identify-privilege-use.md) for more information about privilege analysis

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_PRIVILEGE_CAPTURE.md) for more information about the `DBMS_PRIVILEGE_CAPTURE.GENERATE_RESULT` procedure
