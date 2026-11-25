This property specifies the root element of the result XML document.

### Declaration

    // C#
    public string RootTag {get; set;}

### Property Value

The root element of the result XML document.

### Remarks

The default root tag is `ROWSET`.

To indicate that no root tag is be used in the result XML document, set this property to `null` or `""` or `String.Empty`.

If both `RootTag` and `RowTag` are set to `null`, an XML document is returned only if the result set returns one row and one column.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleXmlQueryProperties Class](OracleXmlQueryPropertiesClass.md)

- [OracleXmlQueryProperties Members](XmlQueryPropertiesMembers.md)
