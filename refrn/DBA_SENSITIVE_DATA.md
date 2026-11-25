## 5.353 DBA_SENSITIVE_DATA

`DBA_SENSITIVE_DATA` describes the sensitive columns in the database.

| Column           | Datatype         | NULL       | Description                                                        |
|:-----------------|:-----------------|:-----------|:-------------------------------------------------------------------|
| `SENSITIVE#`     | `NUMBER`         | `NOT NULL` | Dictionary ID for the sensitive data                               |
| `SCHEMA_NAME`    | `VARCHAR2(128)`  | `NOT NULL` | The schema containing the sensitive data                           |
| `TABLE_NAME`     | `VARCHAR2(128)`  | `NOT NULL` | The table containing the sensitive data                            |
| `COLUMN_NAME`    | `VARCHAR2(128)`  | `NOT NULL` | The name of the column identified as sensitive                     |
| `SENSITIVE_TYPE` | `VARCHAR2(128)`  |            | The sensitive column type of the data                              |
| `SOURCE_NAME`    | `VARCHAR2(128)`  |            | The name of the discovery source for the sensitive data            |
| `USER_COMMENT`   | `VARCHAR2(4000)` |            | User comment on the sensitive data                                 |
| `TS`             | `TIMESTAMP(6)`   |            | The time when the data was identified as sensitive in the database |

**See Also:**

[Oracle Database Security Guide](../dbseg/using-transparent-sensitive-data-protection.md) for more information about transparent sensitive data protection
