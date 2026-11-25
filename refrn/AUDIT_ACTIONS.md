## 3.171 AUDIT_ACTIONS

`AUDIT_ACTIONS` describes audit trail action type codes. This table can be used to map action type numbers to action type names.

**Note:**

The mapping explained in this view is valid for audit trail records from the following views only, and such audit records are generated only when unified auditing is not enabled:

- `DBA_AUDIT_TRAIL`

- `DBA_COMMON_AUDIT_TRAIL`

- `DBA_FGA_AUDIT_TRAIL`

- `USER_AUDIT_TRAIL`

- `V$XML_AUDIT_TRAIL`

**See Also:**

- [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.

| Column   | Datatype       | NULL       | Description                            |
|:---------|:---------------|:-----------|:---------------------------------------|
| `ACTION` | `NUMBER`       | `NOT NULL` | Numeric audit trail action type code.  |
| `NAME`   | `VARCHAR2(28)` | `NOT NULL` | Name of the type of audit trail action |
