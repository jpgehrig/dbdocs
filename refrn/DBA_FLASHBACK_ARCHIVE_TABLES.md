## 4.304 DBA_FLASHBACK_ARCHIVE_TABLES

`DBA_FLASHBACK_ARCHIVE_TABLES` displays information about all tables in the database that are enabled for Flashback Archive.

### Related View

`USER_FLASHBACK_ARCHIVE_TABLES` displays information about the tables owned by the current user that are enabled for Flashback Archive.

| Column                   | Datatype        | NULL       | Description                                                                   |
|:-------------------------|:----------------|:-----------|:------------------------------------------------------------------------------|
| `TABLE_NAME`             | `VARCHAR2(128)` | `NOT NULL` | Name of the table enabled for Flashback Archive                               |
| `OWNER_NAME`             | `VARCHAR2(128)` | `NOT NULL` | Owner name of the table enabled for Flashback Archive                         |
| `FLASHBACK_ARCHIVE_NAME` | `VARCHAR2(255)` | `NOT NULL` | Name of the flashback archive                                                 |
| `ARCHIVE_TABLE_NAME`     | `VARCHAR2(53)`  |            | Name of the archive table containing the historical data for the user table   |
| `STATUS`                 | `VARCHAR2(13)`  |            | Status of whether flashback archive is enabled or being disabled on the table |

**See Also:**

"[USER_FLASHBACK_ARCHIVE_TABLES](USER_FLASHBACK_ARCHIVE_TABLES.md)"
