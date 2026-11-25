## 6.254 TABLE_PRIVILEGE_MAP

`TABLE_PRIVILEGE_MAP` describes privilege (auditing option) type codes.

This table can be used to map privilege (auditing option) type numbers to type names.

| Column      | Datatype       | NULL       | Description                                     |
|:------------|:---------------|:-----------|:------------------------------------------------|
| `PRIVILEGE` | `NUMBER`       | `NOT NULL` | Numeric privilege (auditing option) type code   |
| `NAME `     | `VARCHAR2(40)` | `NOT NULL` | Name of the type of privilege (auditing option) |
