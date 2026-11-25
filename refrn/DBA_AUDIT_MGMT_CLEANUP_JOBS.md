## 4.156 DBA_AUDIT_MGMT_CLEANUP_JOBS

`DBA_AUDIT_MGMT_CLEANUP_JOBS` displays information about the configured audit trail purge jobs.

**Note:**

This view is populated in any Oracle Database where auditing is enabled, regardless of whether pre-Oracle Database 12c auditing or unified auditing is enabled for the database.

- See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- See [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.

| Column                       | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `JOB_NAME`                   | `VARCHAR2(100)` | `NOT NULL` | Name of the audit trail purge job                                                                                                                                                                                                                                                                                                                                                                                                |
| `JOB_STATUS`                 | `VARCHAR2(8)`   |            | Current status of the audit trail purge job (`ENABLED`) or (`DISABLED`)                                                                                                                                                                                                                                                                                                                                                          |
| `AUDIT_TRAIL`                | `VARCHAR2(28)`  |            | Audit trail for which the audit trail purge job is configured:<br>• `STANDARD AUDIT TRAIL`<br>• `FGA AUDIT TRAIL`<br>• `STANDARD AND FGA AUDIT TRAIL`<br>• `OS AUDIT TRAIL`<br>• `XML AUDIT TRAIL`<br>• `OS AND XML AUDIT TRAIL`<br>• `ALL AUDIT TRAILS`<br>• `UNIFIED AUDIT TRAIL`                                                                                                                                              |
| `JOB_FREQUENCY`              | `VARCHAR2(100)` |            | Frequency at which the audit trail purge job runs                                                                                                                                                                                                                                                                                                                                                                                |
| `USE_LAST_ARCHIVE_TIMESTAMP` | `VARCHAR2(3)`   |            | Indicates whether the audit trail purge job invocation uses the last archive timestamp. The last archive timestamp is shown in the `LAST_ARCHIVE_TS` column of the `DBA_AUDIT_MGMT_LAST_ARCH_TS` view. Possible values:<br>• `YES` - Indicates that the audit trail purge job invocation uses the last archive timestamp<br>• `NO` - Indicates that the audit trail purge job invocation does not use the last archive timestamp |
| `JOB_CONTAINER`              | `VARCHAR2(7)`   |            | In a CDB, indicates whether audit trail purge job will be performed only in the current container or in all the containers. Possible values:<br>• `CURRENT` - Indicates that audit trail purge job will be performed only in the current container<br>• `ALL` - Indicates that audit trail purge job will be performed in all the containers<br>In a non-CDB, the value in this column is always `CURRENT`.                      |

**See Also:**

"[DBA_AUDIT_MGMT_LAST_ARCH_TS](DBA_AUDIT_MGMT_LAST_ARCH_TS.md)"
