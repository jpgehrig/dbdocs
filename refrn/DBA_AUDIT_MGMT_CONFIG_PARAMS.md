## 4.157 DBA_AUDIT_MGMT_CONFIG_PARAMS

`DBA_AUDIT_MGMT_CONFIG_PARAMS` displays information about the currently configured audit trail properties that are used by the `DBMS_AUDIT_MGMT` PL/SQL package.

**Note:**

This view is populated in any Oracle Database where auditing is enabled, regardless of whether pre-Oracle Database 12c auditing or unified auditing is enabled for the database.

- See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- See [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.

| Column            | Datatype         | NULL       | Description                                                                                                                                                                                                                                                             |
|:------------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARAMETER_NAME`  | `VARCHAR2(1024)` | `NOT NULL` | Name of the property                                                                                                                                                                                                                                                    |
| `PARAMETER_VALUE` | `VARCHAR2(4000)` |            | Value of the property                                                                                                                                                                                                                                                   |
| `AUDIT_TRAIL`     | `VARCHAR2(28)`   |            | Audit trails for which the property is configured:<br>• `STANDARD AUDIT TRAIL`<br>• `FGA AUDIT TRAIL`<br>• `STANDARD AND FGA AUDIT TRAIL`<br>• `OS AUDIT TRAIL`<br>• `XML AUDIT TRAIL`<br>• `OS AND XML AUDIT TRAIL`<br>• `ALL AUDIT TRAILS`<br>• `UNIFIED AUDIT TRAIL` |

**Note:**

In a read-only database, including an Oracle Active Data Guard physical standby database, this view is not populated when the `DBMS_AUDIT_MGMT.SET_AUDIT_TRAIL` PL/SQL procedure is invoked. If the procedure was used when the database was in read-only mode, use `DBMS_AUDIT_MGMT.GET_AUDIT_TRAIL` to check the value of the property.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_AUDIT_MGMT.md) for more information about the parameters specified with the `DBMS_AUDIT_MGMT.SET_AUDIT_TRAIL_PROPERTY` procedure
