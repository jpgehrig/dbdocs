## 3.145 ALL_XML_SCHEMA_COMPLEX_TYPES

`ALL_XML_SCHEMA_COMPLEX_TYPES` describes all complex types accessible to the current user.

### Related Views

- `DBA_XML_SCHEMA_COMPLEX_TYPES` describes all complex types in the database.

- `USER_XML_SCHEMA_COMPLEX_TYPES` describes all complex types owned by the current user. This view does not display the `OWNER` column.

| Column                  | Datatype                                                                               | NULL | Description                                                                                                                                                                 |
|:------------------------|:---------------------------------------------------------------------------------------|:-----|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`                 | `VARCHAR2(128)`                                                                        |      | The user who owns the type                                                                                                                                                  |
| `SCHEMA_URL`            | `VARCHAR2(700)`                                                                        |      | The URL of the schema within which the type is defined<br>Refer to the See Also note below for links to more information about the `schemaurl` attribute for an XML schema. |
| `TARGET_NAMESPACE`      | `VARCHAR2(2000)`                                                                       |      | The namespace of the type                                                                                                                                                   |
| `COMPLEX_TYPE_NAME`     | `VARCHAR2(256)`                                                                        |      | Name of the complex type                                                                                                                                                    |
| `COMPLEX_TYPE`          | `XMLTYPE(XMLSchema "http://xmlns.oracle.com/xdb/XDBSchema.xsd" Element "complexType")` |      | The actual XMLType of the type                                                                                                                                              |
| `BASE_NAME`             | `VARCHAR2(256)`                                                                        |      | Name of the base type to which the complex type refers                                                                                                                      |
| `BASE_SCHEMA_URL`       | `VARCHAR2(700)`                                                                        |      | The URL of the schema within which the complex type is defined                                                                                                              |
| `BASE_TARGET_NAMESPACE` | `VARCHAR2(2000)`                                                                       |      | The namespace of the type                                                                                                                                                   |
| `MAINTAIN_DOM`          | `RAW(1)`                                                                               |      | XDB annotation for maintainDOM                                                                                                                                              |
| `SQL_TYPE`              | `VARCHAR2(128)`                                                                        |      | XDB annotation for sqlType                                                                                                                                                  |
| `SQL_SCHEMA`            | `VARCHAR2(128)`                                                                        |      | XDB annotation for sqlSchema                                                                                                                                                |

**See Also:**

- "[DBA_XML_SCHEMA_COMPLEX_TYPES](DBA_XML_SCHEMA_COMPLEX_TYPES.md)"

- "[USER_XML_SCHEMA_COMPLEX_TYPES](USER_XML_SCHEMA_COMPLEX_TYPES.md)"

- [Oracle XML DB Developer’s Guide](../adxdb/XML-Schema-and-query-basic.md) for information about registering an XML schema with Oracle XML DB

- [Oracle XML DB Developer’s Guide](../adxdb/XML-DB-restrictions.md) for information about restrictions for an XML schema URL
