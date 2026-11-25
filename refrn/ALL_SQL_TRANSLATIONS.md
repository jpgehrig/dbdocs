## 3.76 ALL_SQL_TRANSLATIONS

`ALL_SQL_TRANSLATIONS` describes all SQL translations accessible to the user.

### Related Views

- `DBA_SQL_TRANSLATIONS` describes all SQL translations in the database.

- `USER_SQL_TRANSLATIONS` describes all SQL translations owned by the user. This view does not display the `OWNER` column.

| Column               | Datatype         | NULL       | Description                                                                                                  |
|:---------------------|:-----------------|:-----------|:-------------------------------------------------------------------------------------------------------------|
| `OWNER`              | `VARCHAR2(128)`  | `NOT NULL` | Owner of the SQL translation profile                                                                         |
| `PROFILE_NAME`       | `VARCHAR2(128)`  | `NOT NULL` | Name of the SQL translation profile                                                                          |
| `SQL_TEXT`           | `CLOB`           | `NOT NULL` | The SQL statement                                                                                            |
| `TRANSLATED_TEXT`    | `CLOB`           |            | The translated SQL statement                                                                                 |
| `SQL_ID`             | `VARCHAR2(13)`   | `NOT NULL` | SQL identifier of the SQL statement                                                                          |
| `HASH_VALUE`         | `NUMBER`         | `NOT NULL` | Hash value of the SQL statement                                                                              |
| `ENABLED`            | `VARCHAR2(5)`    |            | Displays whether the translation is enabled. Possible values:<br>• `TRUE`<br>• `FALSE`                       |
| `REGISTRATION_TIME`  | `TIMESTAMP(6)`   |            | Time the translation was registered                                                                          |
| `CLIENT_INFO`        | `VARCHAR2(64)`   |            | Client information when the SQL was parsed and the translation was registered                                |
| `MODULE`             | `VARCHAR2(64)`   |            | Module when the SQL was parsed and the translation was registered                                            |
| `ACTION`             | `VARCHAR2(64)`   |            | Action when the SQL was parsed and the translation was registered                                            |
| `PARSING_USER_ID`    | `NUMBER`         |            | Current user ID when the SQL was parsed and the translation was registered                                   |
| `PARSING_SCHEMA_ID`  | `NUMBER`         |            | Current schema ID when the SQL was parsed and the translation was registered                                 |
| `COMMENTS`           | `VARCHAR2(4000)` |            | Comment on the translation                                                                                   |
| `ERROR_CODE`         | `NUMBER`         |            | Last error code when the SQL was run                                                                         |
| `ERROR_SOURCE`       | `VARCHAR2(9)`    |            | Source of the last error                                                                                     |
| `TRANSLATION_METHOD` | `VARCHAR2(10)`   |            | Method used to translate the SQL during the last error                                                       |
| `DICTIONARY_SQL_ID`  | `VARCHAR2(13)`   |            | SQL identifier of the SQL text in the translation dictionary used to translate the SQL during the last error |

**See Also:**

- "[DBA_SQL_TRANSLATIONS](DBA_SQL_TRANSLATIONS.md)"

- "[USER_SQL_TRANSLATIONS](USER_SQL_TRANSLATIONS.md)"
