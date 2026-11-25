## 6.251 SYSTEM_PRIVILEGE_MAP

`SYSTEM_PRIVILEGE_MAP` describes privilege (auditing option) type codes.

This table can be used to map privilege (auditing option) type numbers to type names.

| Column      | Datatype       | NULL       | Description                                                                                                                                                                                                        |
|:------------|:---------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PRIVILEGE` | `NUMBER`       | `NOT NULL` | Numeric privilege (auditing option) type code                                                                                                                                                                      |
| `NAME`      | `VARCHAR2(40)` | `NOT NULL` | Name of the type of privilege (auditing option).<br>See [Oracle Database SQL Language Reference](../sqlrf/GRANT.md) for a list of valid system privileges.                                                         |
| `PROPERTY`  | `NUMBER`       | `NOT NULL` | Property flag of the privilege (auditing option):<br>• `0` - Indicates a privilege that can be granted with a SQL GRANT statement<br>• `1` - Indicates a privilege that can only be granted using a PL/SQL package |
