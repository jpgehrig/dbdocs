## 3.147 ALL_XML_SCHEMA_NAMESPACES

`ALL_XML_SCHEMA_NAMESPACES` describes all the available namespaces accessible to the current user.

### Related Views

- `DBA_XML_SCHEMA_NAMESPACES` describes all the available namespaces.

- `USER_XML_SCHEMA_NAMESPACES` describes all the available namespaces owned by the current user. This view does not display the `OWNER` column.

| Column             | Datatype         | NULL | Description                                                                                                                                |
|:-------------------|:-----------------|:-----|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`            | `VARCHAR2(128)`  |      | User who owns the namespace                                                                                                                |
| `TARGET_NAMESPACE` | `VARCHAR2(2000)` |      | The target namespace                                                                                                                       |
| `SCHEMA_URL`       | `VARCHAR2(700)`  |      | The URL of the schema<br>Refer to the See Also note below for links to more information about the `schemaurl` attribute for an XML schema. |

**See Also:**

- "[DBA_XML_SCHEMA_NAMESPACES](DBA_XML_SCHEMA_NAMESPACES.md)"

- "[USER_XML_SCHEMA_NAMESPACES](USER_XML_SCHEMA_NAMESPACES.md)"

- [Oracle XML DB Developer’s Guide](../adxdb/XML-Schema-and-query-basic.md) for information about registering an XML schema with Oracle XML DB

- [Oracle XML DB Developer’s Guide](../adxdb/XML-DB-restrictions.md) for information about restrictions for an XML schema URL
