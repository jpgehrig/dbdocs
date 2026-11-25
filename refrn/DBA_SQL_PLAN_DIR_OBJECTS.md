## 5.364 DBA_SQL_PLAN_DIR_OBJECTS

`DBA_SQL_PLAN_DIR_OBJECTS` displays the objects created in the SQL plan directive.

| Column           | Datatype        | NULL | Description                                                               |
|:-----------------|:----------------|:-----|:--------------------------------------------------------------------------|
| `DIRECTIVE_ID`   | `NUMBER`        |      | The identifier of the SQL plan directive                                  |
| `OWNER`          | `VARCHAR2(128)` |      | The username of the owner of the object in the SQL plan directive         |
| `OBJECT_NAME`    | `VARCHAR2(128)` |      | The name of the object in the SQL plan directive                          |
| `SUBOBJECT_NAME` | `VARCHAR2(128)` |      | The name of the subobject (for example, column) in the SQL plan directive |
| `OBJECT_TYPE`    | `VARCHAR2(6)`   |      | The type of the subobject in the SQL plan directive                       |
| `NUM_ROWS`       | `NUMBER`        |      | The number of rows in the object when the directive is created            |
| `NOTES`          | `XMLTYPE`       |      | Other notes about the object                                              |

**See Also:**

- "[DBA_SQL_PLAN_DIRECTIVES](DBA_SQL_PLAN_DIRECTIVES.md)"

- [Oracle Database SQL Tuning Guide](../tgsql/optimizer-statistics-concepts.md) for more information about SQL plan directives
