## 2.155 ALL_DB_LINKS

`ALL_DB_LINKS` describes the database links accessible to the current user.

### Related Views

- `DBA_DB_LINKS` describes all database links in the database.

- `USER_DB_LINKS` describes the database links owned by the current user. This view does not display the `OWNER` column.

| Column                       | Datatype         | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                                  |
|:-----------------------------|:-----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`                      | `VARCHAR2(128)`  | `NOT NULL` | Owner of the database link                                                                                                                                                                                                                                                                                                                                                                   |
| `DB_LINK`                    | `VARCHAR2(128)`  | `NOT NULL` | Name of the database link                                                                                                                                                                                                                                                                                                                                                                    |
| `USERNAME`                   | `VARCHAR2(128)`  |            | Name of the user when logging in                                                                                                                                                                                                                                                                                                                                                             |
| `HOST`                       | `VARCHAR2(2000)` |            | Oracle Net connect string                                                                                                                                                                                                                                                                                                                                                                    |
| `CREATED`                    | `DATE`           | `NOT NULL` | Creation time of the database link                                                                                                                                                                                                                                                                                                                                                           |
| `HIDDEN`                     | `VARCHAR2(3)`    |            | For internal use only                                                                                                                                                                                                                                                                                                                                                                        |
| `SHARD_INTERNAL`             | `VARCHAR2(3)`    |            | Indicates whether the database link is used to support operations across sharded databases. Possible values:<br>• `YES`: The database link is used and managed for to support sharded databases<br>• `NO`: The database link is not used and managed to support sharded databases<br>Users should not alter or delete database links that are used and managed to support sharded databases. |
| `VALID`                      | `VARCHAR2(3)`    |            | Indicates whether the database link is valid and usable. Possible values:<br>• `YES`: The database link is valid and usable.<br>• `NO`: The database link is invalid and unusable.                                                                                                                                                                                                           |
| `INTRA_CDB`<sup>Foot 1</sup> | `VARCHAR2(3)`    |            | For internal use only                                                                                                                                                                                                                                                                                                                                                                        |

<sup>Footnote 1</sup> This column is available starting with Oracle Database 19c.

**See Also:**

- "[DBA_DB_LINKS](DBA_DB_LINKS.md)"

- "[USER_DB_LINKS](USER_DB_LINKS.md)"

- "[DBA_DB_LINK_SOURCES](DBA_DB_LINK_SOURCES.md)"

- "[DBA_EXTERNAL_SCN_ACTIVITY](DBA_EXTERNAL_SCN_ACTIVITY.md)"
