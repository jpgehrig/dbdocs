## 3.150 ALL_XML_SCHEMA_SUBSTGRP_MBRS

`ALL_XML_SCHEMA_SUBSTGRP_MBRS` describes all members of substitution groups accessible to the current user.

### Related Views

- `DBA_XML_SCHEMA_SUBSTGRP_MBRS` describes all members of substitution groups.

- `USER_XML_SCHEMA_SUBSTGRP_MBRS` describes all members of substitution groups owned by the current user. This view does not display the `OWNER` column.

| Column                  | Datatype                                                                           | NULL | Description                                                                                                                                                                    |
|:------------------------|:-----------------------------------------------------------------------------------|:-----|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`                 | `VARCHAR2(128)`                                                                    |      | The user who owns the element                                                                                                                                                  |
| `SCHEMA_URL`            | `VARCHAR2(700)`                                                                    |      | The URL of the schema within which the element is defined<br>Refer to the See Also note below for links to more information about the `schemaurl` attribute for an XML schema. |
| `TARGET_NAMESPACE`      | `VARCHAR2(2000)`                                                                   |      | The namespace of the element                                                                                                                                                   |
| `ELEMENT_NAME`          | `VARCHAR2(256)`                                                                    |      | Name of the element                                                                                                                                                            |
| `ELEMENT`               | `XMLTYPE(XMLSchema "http://xmlns.oracle.com/xdb/XDBSchema.xsd" Element "element")` |      | The actual XML fragment of the element                                                                                                                                         |
| `HEAD_OWNER`            | `VARCHAR2(128)`                                                                    |      | The user who owns the head element for the current element                                                                                                                     |
| `HEAD_SCHEMA_URL`       | `VARCHAR2(700)`                                                                    |      | The URL of the schema within which the head element exists                                                                                                                     |
| `HEAD_TARGET_NAMESPACE` | `VARCHAR2(2000)`                                                                   |      | The namespace of the head element                                                                                                                                              |
| `HEAD_ELEMENT_NAME`     | `VARCHAR2(256)`                                                                    |      | Name of the head element                                                                                                                                                       |
| `HEAD_ELEMENT`          | `XMLTYPE(XMLSchema "http://xmlns.oracle.com/xdb/XDBSchema.xsd" Element "element")` |      | The actual XMLType of the head element                                                                                                                                         |

**See Also:**

- "[DBA_XML_SCHEMA_SUBSTGRP_MBRS](DBA_XML_SCHEMA_SUBSTGRP_MBRS.md)"

- "[USER_XML_SCHEMA_SUBSTGRP_MBRS](USER_XML_SCHEMA_SUBSTGRP_MBRS.md)"

- [Oracle XML DB Developer’s Guide](../adxdb/XML-Schema-and-query-basic.md) for information about registering an XML schema with Oracle XML DB

- [Oracle XML DB Developer’s Guide](../adxdb/XML-DB-restrictions.md) for information about restrictions for an XML schema URL
