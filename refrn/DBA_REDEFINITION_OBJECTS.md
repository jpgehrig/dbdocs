## 5.270 DBA_REDEFINITION_OBJECTS

`DBA_REDEFINITION_OBJECTS` is an online redefinition view. It displays the objects involved in the current redefinitions.

| Column                 | Datatype         | NULL       | Description                                                                                                                                    |
|:-----------------------|:-----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| `OBJECT_TYPE`          | `VARCHAR2(12)`   |            | Type of the redefinition object:<br>• `TABLE`<br>• `INDEX`<br>• `CONSTRAINT`<br>• `TRIGGER`<br>• `NESTED TABLE`<br>• `PARTITION`<br>• `MV LOG` |
| `OBJECT_OWNER`         | `VARCHAR2(4000)` |            | Owner of the redefinition object                                                                                                               |
| `OBJECT_NAME`          | `VARCHAR2(128)`  | `NOT NULL` | Name of the redefinition object                                                                                                                |
| `BASE_TABLE_OWNER`     | `VARCHAR2(128)`  |            | Owner of the base table of the redefinition object                                                                                             |
| `BASE_TABLE_NAME`      | `VARCHAR2(128)`  |            | Name of the base table of the redefinition object                                                                                              |
| `INTERIM_OBJECT_OWNER` | `VARCHAR2(4000)` |            | Owner of the corresponding interim redefinition object                                                                                         |
| `INTERIM_OBJECT_NAME`  | `VARCHAR2(128)`  |            | Name of the corresponding interim redefinition object                                                                                          |
| `EDITION_NAME`         | `VARCHAR2(128)`  |            | Reserved for future use                                                                                                                        |

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-tables.md) for more information about online redefinition
