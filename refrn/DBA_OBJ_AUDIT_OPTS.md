## 5.208 DBA_OBJ_AUDIT_OPTS

`DBA_OBJ_AUDIT_OPTS` describes auditing options on all objects.

**Note:**

This view is populated only in an Oracle Database where unified auditing is not enabled. When unified auditing is enabled in Oracle Database, the audit records are populated in the new audit trail and can be viewed from `UNIFIED_AUDIT_TRAIL`.

- See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- See [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.

### Related View

`USER_OBJ_AUDIT_OPTS` describes auditing options on all objects owned by the current user. This view does not display the `OWNER` column.

| Column        | Datatype        | NULL | Description                                               |
|:--------------|:----------------|:-----|:----------------------------------------------------------|
| `OWNER `      | `VARCHAR2(128)` |      | Owner of the object                                       |
| `OBJECT_NAME` | `VARCHAR2(128)` |      | Name of the object                                        |
| `OBJECT_TYPE` | `VARCHAR2(23)`  |      | Type of the object                                        |
| `ALT `        | `VARCHAR2(3)`   |      | Auditing `ALTER WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`     |
| `AUD`         | `VARCHAR2(3)`   |      | Auditing `AUDIT WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`     |
| `COM`         | `VARCHAR2(3)`   |      | Auditing `COMMENT WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`   |
| `DEL`         | `VARCHAR2(3)`   |      | Auditing `DELETE WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`    |
| `GRA`         | `VARCHAR2(3)`   |      | Auditing `GRANT WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`     |
| `IND`         | `VARCHAR2(3)`   |      | Auditing `INDEX WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`     |
| `INS`         | `VARCHAR2(3)`   |      | Auditing `INSERT WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`    |
| `LOC`         | `VARCHAR2(3)`   |      | Auditing `LOCK WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`      |
| `REN`         | `VARCHAR2(3)`   |      | Auditing `RENAME WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`    |
| `SEL`         | `VARCHAR2(3)`   |      | Auditing `SELECT WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`    |
| `UPD`         | `VARCHAR2(3)`   |      | Auditing `UPDATE WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`    |
| `EXE`         | `VARCHAR2(3)`   |      | Auditing `EXECUTE WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`   |
| `CRE`         | `VARCHAR2(3)`   |      | Auditing `CREATE WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`    |
| `REA`         | `VARCHAR2(3)`   |      | Auditing `READ WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`      |
| `WRI`         | `VARCHAR2(3)`   |      | Auditing `WRITE WHENEVER SUCCESSFUL` / `UNSUCCESSFUL`     |
| `FBK`         | `VARCHAR2(3)`   |      | Auditing `FLASHBACK WHENEVER SUCCESSFUL` / `UNSUCCESSFUL` |

**See Also:**

- "[USER_OBJ_AUDIT_OPTS](USER_OBJ_AUDIT_OPTS.md)"

- [Oracle Database SQL Language Reference](../sqlrf/AUDIT-Unified-Auditing.md) for more information about the SQL `AUDIT` statement for unified auditing

- [Oracle Database SQL Language Reference](../sqlrf/AUDIT-Traditional-Auditing.md) for more information about the SQL` AUDIT` statement for traditional auditing

- [Oracle Database Security Guide](../dbseg/configuring-audit-policies.md) to learn how to find information about audited activities
