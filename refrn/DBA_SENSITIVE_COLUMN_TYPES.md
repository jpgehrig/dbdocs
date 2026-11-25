## 5.352 DBA_SENSITIVE_COLUMN_TYPES

`DBA_SENSITIVE_COLUMN_TYPES` describes sensitive column types in the database.

| Column         | Datatype         | NULL | Description                                                                                        |
|:---------------|:-----------------|:-----|:---------------------------------------------------------------------------------------------------|
| `NAME`         | `VARCHAR2(128)`  |      | The name of the sensitive column type                                                              |
| `USER_COMMENT` | `VARCHAR2(4000)` |      | User comment on the sensitive column type                                                          |
| `SOURCE_NAME`  | `VARCHAR2(128)`  |      | The name of the discovery source for the sensitive column type                                     |
| `SOURCE_TYPE`  | `VARCHAR2(3)`    |      | The type of the discovery source:<br>• `ADM`: import from ADM<br>• `DB`: added within the database |

**See Also:**

[Oracle Database Security Guide](../dbseg/using-transparent-sensitive-data-protection.md) for more information about transparent sensitive data protection
