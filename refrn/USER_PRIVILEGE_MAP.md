## 6.608 USER_PRIVILEGE_MAP

`USER_PRIVILEGE_MAP` shows privilege (auditing option) type codes for object privileges that can be granted on a user.

This table can be used to map privilege type numbers to type names.

| Column      | Datatype       | NULL       | Description                                     |
|:------------|:---------------|:-----------|:------------------------------------------------|
| `PRIVILEGE` | `NUMBER`       | `NOT NULL` | A numeric privilege (auditing option) type code |
| `NAME`      | `VARCHAR2(40)` | `NOT NULL` | Name of the type of privilege (auditing option) |
