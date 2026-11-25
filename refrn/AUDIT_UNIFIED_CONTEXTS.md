## 3.172 AUDIT_UNIFIED_CONTEXTS

`AUDIT_UNIFIED_CONTEXTS` describes the application context's attributes, which are configured to be captured in the audit trail.

**Note:**

This view is populated only in an Oracle Database where unified auditing is enabled.

- See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- See [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.

| Column      | Datatype        | NULL | Description                                                                                                           |
|:------------|:----------------|:-----|:----------------------------------------------------------------------------------------------------------------------|
| `NAMESPACE` | `VARCHAR2(128)` |      | Application context namespace                                                                                         |
| `ATTRIBUTE` | `VARCHAR2(128)` |      | Application context attribute                                                                                         |
| `USER_NAME` | `VARCHAR2(128)` |      | Username of database user for whom the application context's attribute is confiured to be captured in the audit trail |
