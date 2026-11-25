This property specifies the value of the XML element which identifies a row of data from the result set in an XML document.

### Declaration

    // C#
    public string RowTag {get; set;}

### Property Value

The value of the XML element.

### Remarks

The default is `ROW`.

To indicate that no row tag is be used in the result XML document, set this property to `null` or `""` or `String.Empty`.

If both `RootTag` and `RowTag` are set to `null`, an XML document is returned only if the result set returns one row and one column.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleXmlQueryProperties Class](OracleXmlQueryPropertiesClass.md)

- [OracleXmlQueryProperties Members](XmlQueryPropertiesMembers.md)
