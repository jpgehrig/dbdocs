## 6.96 DBA_USED_USERPRIVS_PATH

`DBA_USED_USERPRIVS_PATH` lists the user privileges that are used for the privilege analysis policies reported by the `DBMS_PRIVILEGE_CAPTURE.GENERATE_RESULT` procedure.

This view provides access to analyzed privilege records in `SYS` tables.

You must have the `CAPTURE_ADMIN` role to access this view.

| Column         | Datatype        | NULL       | Description                                                                                                                                                                                                                  |
|:---------------|:----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CAPTURE`      | `VARCHAR2(128)` | `NOT NULL` | Name of a privilege analysis policy                                                                                                                                                                                          |
| `SEQUENCE`     | `NUMBER`        | `NOT NULL` | The sequence number of the privilege analysis run during which the privilege was reported                                                                                                                                    |
| `OS_USER`      | `VARCHAR2(128)` |            | Operating system login username                                                                                                                                                                                              |
| `USERHOST`     | `VARCHAR2(128)` |            | Client host machine name                                                                                                                                                                                                     |
| `MODULE`       | `VARCHAR2(64)`  |            | Module name                                                                                                                                                                                                                  |
| `USERNAME`     | `VARCHAR2(128)` | `NOT NULL` | Name of the user whose privilege was reported                                                                                                                                                                                |
| `USED_ROLE`    | `VARCHAR2(128)` |            | Used role                                                                                                                                                                                                                    |
| `USER_PRIV`    | `VARCHAR2(25)`  |            | Used user privilege                                                                                                                                                                                                          |
| `ONUSER`       | `VARCHAR2(128)` |            | The user whose user privileges the grantee can exercise                                                                                                                                                                      |
| `GRANT_OPTION` | `NUMBER`        |            | Indicates whether the privilege is granted with the `GRANT` option:<br>• `0` - Indicates that the privilege is granted without the `GRANT` option<br>• `1` - Indicates that the privilege is granted with the `GRANT` option |
| `PATH`         | `GRANT_PATH`    |            | User privilege grant paths                                                                                                                                                                                                   |
| `RUN_NAME`     | `VARCHAR2(128)` |            | The name of the run during which the privilege was reported                                                                                                                                                                  |

**See Also:**

- [Oracle Database Security Guide](../dbseg/performing-privilege-analysis-identify-privilege-use.md) for more information about privilege analysis

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_PRIVILEGE_CAPTURE.md) for more information about the `DBMS_PRIVILEGE_CAPTURE.GENERATE_RESULT` procedure
