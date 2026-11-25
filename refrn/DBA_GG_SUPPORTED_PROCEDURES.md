## 4.317 DBA_GG_SUPPORTED_PROCEDURES

`DBA_GG_SUPPORTED_PROCEDURES` provides details about all procedures that are supported for Oracle GoldenGate replication.

| Column                  | Datatype        | NULL | Description                                                                                                                                                        |
|:------------------------|:----------------|:-----|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`                 | `VARCHAR2(128)` |      | Procedure package owner                                                                                                                                            |
| `PACKAGE_NAME`          | `VARCHAR2(128)` |      | Procedure package name                                                                                                                                             |
| `PROCEDURE_NAME`        | `VARCHAR2(128)` |      | Procedure name                                                                                                                                                     |
| `MIN_DB_VERSION`        | `VARCHAR2(100)` |      | Minimum database version for the procedure                                                                                                                         |
| `MAX_DB_VERSION`        | `VARCHAR2(100)` |      | Maximum database version for the procedure                                                                                                                         |
| `MIN_REDO_COMPAT_LEVEL` | `VARCHAR2(100)` |      | Minimum redo compatibility for the procedure                                                                                                                       |
| `MAX_REDO_COMPAT_LEVEL` | `VARCHAR2(100)` |      | Maximum redo compatibility for the procedure                                                                                                                       |
| `SUPPORTED_MODE`        | `VARCHAR2(100)` |      | Supported mode for the procedure: `ALWAYS` or `DBMS_ROLLING`                                                                                                       |
| `EXCLUSION_RULE_EXISTS` | `VARCHAR2(3)`   |      | Specifies whether an exclusion rule exists for the procedure (`YES`) or not (`NO`).<br>See Also: "[DBA_GG_PROC_OBJECT_EXCLUSION](DBA_GG_PROC_OBJECT_EXCLUSION.md)" |
