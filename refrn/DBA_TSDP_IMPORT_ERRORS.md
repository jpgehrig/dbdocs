## 6.59 DBA_TSDP_IMPORT_ERRORS

`DBA_TSDP_IMPORT_ERRORS` shows information about the errors encountered during import of the Transparent Sensitive Data Protection discovery result.

This error information corresponds to the last import of the discovery result done using the `DBMS_TSDP_MANAGE.IMPORT_DISCOVERY_RESULT` API.

| Column           | Datatype        | NULL       | Description                                   |
|:-----------------|:----------------|:-----------|:----------------------------------------------|
| `ERROR_CODE`     | `NUMBER`        | `NOT NULL` | The ORA error code of the error encountered   |
| `SCHEMA_NAME`    | `VARCHAR2(128)` |            | The schema corresponding to the error         |
| `TABLE_NAME`     | `VARCHAR2(128)` |            | The table corresponding to the error          |
| `COLUMN_NAME`    | `VARCHAR2(128)` |            | The column corresponding to the error         |
| `SENSITIVE_TYPE` | `VARCHAR2(128)` |            | The sensitive type corresponding to the error |

**See Also:**

- [Oracle Database Security Guide](../dbseg/using-transparent-sensitive-data-protection.md) for more information about using Transparent Sensitive Data Protection

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_TSDP_MANAGE.md) for more information about the `DBMS_TSDP_MANAGE.IMPORT_DISCOVERY_RESULT` procedure
