## 6.149 DBA_XS_ENABLED_AUDIT_POLICIES

`DBA_XS_ENABLED_AUDIT_POLICIES` describes all the audit policies specific to Oracle Database Real Application Security that are enabled to users.

**Note:**

This view was known as `DBA_XS_ENB_AUDIT_POLICIES` in Oracle Database 12c Release 1. It was renamed to `DBA_XS_ENABLED_AUDIT_POLICIES` in Oracle Database 12c Release 2 (12.2.0.1).

| Column           | Datatype        | NULL | Description                                                                                                                                                                                                                                                                                   |
|:-----------------|:----------------|:-----|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`    | `VARCHAR2(128)` |      | Name of the audit policy                                                                                                                                                                                                                                                                      |
| `ENABLED_OPTION` | `VARCHAR2(15)`  |      | Enabled option of the audit policy. Possible values:<br>• `BY USER`: For policies that are enabled on users<br>• `EXCEPT USERS`: For policies that are enabled on users<br>• `BY GRANTED ROLE`: For policies that are enabled on roles<br>• `INVALID`: For policies that are enabled on roles |
| `ENTITY_NAME`    | `VARCHAR2(128)` |      | Database entity (user name or role name) on which the audit policy is enabled                                                                                                                                                                                                                 |
| `ENTITY_TYPE`    | `VARCHAR2(7)`   |      | Database entity type. Possible values:<br>• `USER`: Indicates that the policy is enabled on a user or users.<br>• `ROLE`: Indicates that the policy is enabled on a role or roles.                                                                                                            |
| `SUCCESS`        | `VARCHAR2(3)`   |      | Indicates whether the audit policy is enabled for auditing successful events (`YES`) or not (`NO`)                                                                                                                                                                                            |
| `FAILURE`        | `VARCHAR2(3)`   |      | Indicates whether the audit policy is enabled for auditing unsuccessful events (`YES`) or not (`NO`)                                                                                                                                                                                          |

**See Also:**

[Oracle Database Security Guide](../dbseg/part_6.md) for more information about auditing
