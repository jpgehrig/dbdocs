## 3.184 DATABASE_EXPORT_OBJECTS

`DATABASE_EXPORT_OBJECTS` lists simple path names for some of the object types belonging to a full Data Pump export, which is invoked using the `FULL=Y` parameter on the `expdp` command.

Users of the Data Pump Export and Import utilities can query this view to determine valid values for the `EXCLUDE` and `INCLUDE` parameters.

| Column        | Datatype         | NULL       | Description                                                                                                                                             |
|:--------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OBJECT_PATH` | `VARCHAR2(200)`  | `NOT NULL` | Simple path name for the object type                                                                                                                    |
| `COMMENTS`    | `VARCHAR2(2000)` |            | Comment on the object type                                                                                                                              |
| `NAMED`       | `CHAR(1)`        |            | Do objects of this type have names? If yes (`Y`), then the name can be specified in the optional name_clause on the `EXCLUDE` and `INCLUDE` parameters. |

**See Also:**

- "[SCHEMA_EXPORT_OBJECTS](SCHEMA_EXPORT_OBJECTS.md)"

- "[TABLE_EXPORT_OBJECTS](TABLE_EXPORT_OBJECTS.md)"

- [Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md) for more information on performing a full Data Pump export using the `expdp` command
