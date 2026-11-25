## 6.373 USER_AUDIT_STATEMENT

`USER_AUDIT_STATEMENT` displays audit trail entries for the `GRANT`, `REVOKE`, `AUDIT`, `NOAUDIT`, and `ALTER SYSTEM` statements issued by the current user.

Its columns are the same as those in "[DBA_AUDIT_STATEMENT](DBA_AUDIT_STATEMENT.md)".

**Note:**

This view is populated only in an Oracle Database where unified auditing is not enabled. When unified auditing is enabled in Oracle Database, the audit records are populated in the new audit trail and can be viewed from `UNIFIED_AUDIT_TRAIL`.

- See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- See [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.
