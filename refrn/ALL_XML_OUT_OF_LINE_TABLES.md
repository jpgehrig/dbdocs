## 3.143 ALL_XML_OUT_OF_LINE_TABLES

`ALL_XML_OUT_OF_LINE_TABLES` descibes all the out of line tables connected to a given root table for the same schema accessible to the current user.

### Related Views

- `DBA_XML_OUT_OF_LINE_TABLES` describes all the out of line tables connected to a given root table for the same schema in the database.

- `USER_XML_OUT_OF_LINE_TABLES` describes all the out of line tables connected to a given root table for the same schema owned by the current user. This view does not display the `TABLE_OWNER` column.

| Column         | Datatype        | NULL | Description                                                                                                                                                                              |
|:---------------|:----------------|:-----|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SCHEMA_URL`   | `VARCHAR2(700)` |      | The URL of the schema within which the out of line table is defined<br>Refer to the See Also note below for links to more information about the `schemaurl` attribute for an XML schema. |
| `SCHEMA_OWNER` | `VARCHAR2(128)` |      | Owner of the schema                                                                                                                                                                      |
| `TABLE_NAME`   | `VARCHAR2(128)` |      | Name of the out of line table                                                                                                                                                            |
| `TABLE_OWNER`  | `VARCHAR2(128)` |      | Owner of the out of line table                                                                                                                                                           |

**See Also:**

- "[DBA_XML_OUT_OF_LINE_TABLES](DBA_XML_OUT_OF_LINE_TABLES.md)"

- "[USER_XML_OUT_OF_LINE_TABLES](USER_XML_OUT_OF_LINE_TABLES.md)"

- [Oracle XML DB Developer’s Guide](../adxdb/XML-Schema-and-query-basic.md) for information about registering an XML schema with Oracle XML DB

- [Oracle XML DB Developer’s Guide](../adxdb/XML-DB-restrictions.md) for information about restrictions for an XML schema URL
