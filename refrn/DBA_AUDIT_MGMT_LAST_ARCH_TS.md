## 4.158 DBA_AUDIT_MGMT_LAST_ARCH_TS

`DBA_AUDIT_MGMT_LAST_ARCH_TS` displays information about the last archive timestamps set for audit trail cleanup or purges.

**Note:**

This view is populated in any Oracle Database where auditing is enabled, regardless of whether pre-Oracle Database 12c auditing or unified auditing is enabled for the database.

- See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- See [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.

| Column            | Datatype                      | NULL       | Description                                                                                                                                                                          |
|:------------------|:------------------------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AUDIT_TRAIL`     | `VARCHAR2(20)`                |            | Audit trail for which the last archive timestamp applies:<br>• `STANDARD AUDIT TRAIL`<br>• `FGA AUDIT TRAIL`<br>• `OS AUDIT TRAIL`<br>• `XML AUDIT TRAIL`<br>• `UNIFIED AUDIT TRAIL` |
| `RAC_INSTANCE`    | `NUMBER`                      | `NOT NULL` | Oracle RAC instance number for which the last archive timestamp applies; `0` implies not applicable                                                                                  |
| `LAST_ARCHIVE_TS` | `TIMESTAMP(6) WITH TIME ZONE` |            | Timestamp of the last audit record or audit file that has been archived                                                                                                              |
| `DATABASE_ID`     | `NUMBER`                      | `NOT NULL` | Database ID of the audit records to clean up                                                                                                                                         |
| `CONTAINER_GUID`  | `VARCHAR2(33)`                | `NOT NULL` | GUID of the container of the audit records to clean up                                                                                                                               |

**Note:**

In a read-only database, including an Oracle Active Data Guard physical standby database, this view is not populated when `DBMS_AUDIT_MGMT.SET_LAST_ARCHIVE_TIMESTAMP` is invoked. In such a case, use `DBMS_AUDIT_MGMT.GET_LAST_ARCHIVE_TIMESTAMP` to check for the timestamp, if it was configured for the database instance.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_AUDIT_MGMT.md) for more information about `DBMS_AUDIT_MGMT` subprograms
