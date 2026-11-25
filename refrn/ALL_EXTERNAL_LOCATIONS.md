## 2.181 ALL_EXTERNAL_LOCATIONS

`ALL_EXTERNAL_LOCATIONS` describes the locations (data sources) of the external tables accessible to the current user.

### Related Views

- `DBA_EXTERNAL_LOCATIONS` describes the locations (data sources) of all external tables in the database.

- `USER_EXTERNAL_LOCATIONS` describes the locations (data sources) of the external tables owned by the current user. This view does not display the `OWNER` column.

| Column            | Datatype         | NULL       | Description                                                   |
|:------------------|:-----------------|:-----------|:--------------------------------------------------------------|
| `OWNER`           | `VARCHAR2(128)`  | `NOT NULL` | Owner of the external table location                          |
| `TABLE_NAME`      | `VARCHAR2(128)`  | `NOT NULL` | Name of the corresponding external table                      |
| `LOCATION`        | `VARCHAR2(4000)` |            | External table location clause                                |
| `DIRECTORY_OWNER` | `CHAR(3)`        |            | Owner of the directory containing the external table location |
| `DIRECTORY_NAME`  | `VARCHAR2(128)`  |            | Name of the directory containing the external table location  |

**See Also:**

- "[DBA_EXTERNAL_LOCATIONS](DBA_EXTERNAL_LOCATIONS.md)"

- "[USER_EXTERNAL_LOCATIONS](USER_EXTERNAL_LOCATIONS.md)"
