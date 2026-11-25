## 3.148 ALL_XML_SCHEMA_SIMPLE_TYPES

`ALL_XML_SCHEMA_SIMPLE_TYPES` describes all simple types accessible to the current user.

### Related Views

- `DBA_XML_SCHEMA_SIMPLE_TYPES` describes all simple types.

- `USER_XML_SCHEMA_SIMPLE_TYPES` describes all simple types owned by the current user. This view does not display the `OWNER` column.

| Column             | Datatype                                                                              | NULL | Description                                                                                                                                                                 |
|:-------------------|:--------------------------------------------------------------------------------------|:-----|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`            | `VARCHAR2(128)`                                                                       |      | The user who owns the type                                                                                                                                                  |
| `SCHEMA_URL`       | `VARCHAR2(700)`                                                                       |      | The URL of the schema within which the type is defined<br>Refer to the See Also note below for links to more information about the `schemaurl` attribute for an XML schema. |
| `TARGET_NAMESPACE` | `VARCHAR2(2000)`                                                                      |      | The namespace of the type                                                                                                                                                   |
| `SIMPLE_TYPE_NAME` | `VARCHAR2(256)`                                                                       |      | Name of the simple type                                                                                                                                                     |
| `SIMPLE_TYPE`      | `XMLTYPE(XMLSchema "http://xmlns.oracle.com/xdb/XDBSchema.xsd" Element "simpleType")` |      | The actual XMLType of the type                                                                                                                                              |

**See Also:**

- "[DBA_XML_SCHEMA_SIMPLE_TYPES](DBA_XML_SCHEMA_SIMPLE_TYPES.md)"

- "[USER_XML_SCHEMA_SIMPLE_TYPES](USER_XML_SCHEMA_SIMPLE_TYPES.md)"

- [Oracle XML DB Developer’s Guide](../adxdb/XML-Schema-and-query-basic.md) for information about registering an XML schema with Oracle XML DB

- [Oracle XML DB Developer’s Guide](../adxdb/XML-DB-restrictions.md) for information about restrictions for an XML schema URL
