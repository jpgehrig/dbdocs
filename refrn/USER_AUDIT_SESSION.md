## 6.372 USER_AUDIT_SESSION

`USER_AUDIT_SESSION` displays the audit trail records concerning connections and disconnections of the current user. Its columns are the same as those in `DBA_AUDIT_SESSION`.

**Note:**

This view is populated only in an Oracle Database where unified auditing is not enabled. When unified auditing is enabled in Oracle Database, the audit records are populated in the new audit trail and can be viewed from `UNIFIED_AUDIT_TRAIL`.

- "[DBA_AUDIT_SESSION](DBA_AUDIT_SESSION.md)"

- See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- See [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.
