## 3.75 ALL_SQL_TRANSLATION_PROFILES

`ALL_SQL_TRANSLATION_PROFILES` describes all SQL translation profiles accessible to the user.

### Related Views

- `DBA_SQL_TRANSLATION_PROFILES` describes all SQL translation profiles in the database.

- `USER_SQL_TRANSLATION_PROFILES` describes all SQL translation profiles owned by the user. This view does not display the `OWNER` column.

| Column                    | Datatype        | NULL       | Description                                                                                                                     |
|:--------------------------|:----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`                   | `VARCHAR2(128)` | `NOT NULL` | Owner of the SQL translation profile                                                                                            |
| `PROFILE_NAME`            | `VARCHAR2(128)` | `NOT NULL` | Name of the SQL translation profile                                                                                             |
| `TRANSLATOR`              | `VARCHAR2(261)` |            | The translator package                                                                                                          |
| `FOREIGN_SQL_SYNTAX`      | `VARCHAR2(5)`   |            | Indicates whether the SQL syntax is foreign.<br>Possible values:<br>• `TRUE`<br>• `FALSE`                                       |
| `TRANSLATE_NEW_SQL`       | `VARCHAR2(5)`   |            | Indicates whether to translate new SQL statements and errors using the translator.<br>Possible values:<br>• `TRUE`<br>• `FALSE` |
| `RAISE_TRANSLATION_ERROR` | `VARCHAR2(5)`   |            | Indicates whether to raise translation error.<br>Possible values:<br>• `TRUE`<br>• `FALSE`                                      |
| `LOG_TRANSLATION_ERROR`   | `VARCHAR2(5)`   |            | Indicates whether to log translation error.<br>Possible values:<br>• `TRUE`<br>• `FALSE`                                        |
| `TRACE_TRANSLATION`       | `VARCHAR2(5)`   |            | Indicates whether to trace translation.<br>Possible values:<br>• `TRUE`<br>• `FALSE`                                            |
| `LOG_ERRORS`              | `VARCHAR2(5)`   |            | Indicates whether there are log errors (`TRUE`) or not (`FALSE`)                                                                |

**See Also:**

- "[DBA_SQL_TRANSLATION_PROFILES](DBA_SQL_TRANSLATION_PROFILES.md)"

- "[USER_SQL_TRANSLATION_PROFILES](USER_SQL_TRANSLATION_PROFILES.md)"
