## 6.244 STMT_AUDIT_OPTION_MAP

`STMT_AUDIT_OPTION_MAP` describes auditing option type codes. This table can be used to map auditing option type numbers to type names.

**Note:**

This view is populated in any Oracle Database where auditing is enabled, regardless of whether pre-Oracle Database 12c auditing or unified auditing is enabled for the database.

- See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- See [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.

**Note:**

The mapping explained in this view is valid for audit configuration from the `DBA_STMT_AUDIT_OPTS` view only, and such audit configurations can be made when unified auditing is not enabled.

| Column     | Datatype       | NULL       | Description                          |
|:-----------|:---------------|:-----------|:-------------------------------------|
| `OPTION#`  | `NUMBER`       | `NOT NULL` | Numeric auditing option type code    |
| `NAME`     | `VARCHAR2(40)` | `NOT NULL` | Name of the type of auditing option  |
| `PROPERTY` | `NUMBER`       | `NOT NULL` | Property flag of the auditing option |

**See Also:**

"[DBA_STMT_AUDIT_OPTS](DBA_STMT_AUDIT_OPTS.md)"
