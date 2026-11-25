## 6.369 USER_AUDIT_OBJECT

`USER_AUDIT_OBJECT` displays audit trail records for the objects accessible to the current user. Its columns are the same as those in `DBA_AUDIT_OBJECT`.

**Note:**

This view is populated only in an Oracle Database where unified auditing is not enabled. When unified auditing is enabled in Oracle Database, the audit records are populated in the new audit trail and can be viewed from `UNIFIED_AUDIT_TRAIL`.

- "[DBA_AUDIT_OBJECT](DBA_AUDIT_OBJECT.md)"

- See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- See [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.
