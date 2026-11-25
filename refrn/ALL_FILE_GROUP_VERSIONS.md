## 2.187 ALL_FILE_GROUP_VERSIONS

`ALL_FILE_GROUP_VERSIONS` shows top-level version information for the file groups accessible to the current user.

### Related Views

- `DBA_FILE_GROUP_VERSIONS` shows top-level version information for all file groups in the database.

- `USER_FILE_GROUP_VERSIONS` shows top-level version information for all file groups owned by the current user. This view does not display the `FILE_GROUP_OWNER` column.

| Column              | Datatype                      | NULL       | Description                                             |
|:--------------------|:------------------------------|:-----------|:--------------------------------------------------------|
| `FILE_GROUP_OWNER`  | `VARCHAR2(128)`               | `NOT NULL` | Owner of the file group                                 |
| `FILE_GROUP_NAME`   | `VARCHAR2(128)`               | `NOT NULL` | Name of the file group                                  |
| `VERSION_NAME`      | `VARCHAR2(128)`               | `NOT NULL` | User-specified name for the version                     |
| `VERSION`           | `NUMBER`                      | `NOT NULL` | Internal version number                                 |
| `CREATOR`           | `VARCHAR2(128)`               | `NOT NULL` | User who created the version                            |
| `CREATED`           | `TIMESTAMP(6) WITH TIME ZONE` | `NOT NULL` | Time at which the version was created                   |
| `COMMENTS`          | `VARCHAR2(4000)`              |            | Comments about the file group                           |
| `DEFAULT_DIRECTORY` | `VARCHAR2(128)`               |            | Default directory object for this version, if specified |

**See Also:**

- "[DBA_FILE_GROUP_VERSIONS](DBA_FILE_GROUP_VERSIONS.md)"

- "[USER_FILE_GROUP_VERSIONS](USER_FILE_GROUP_VERSIONS.md)"
