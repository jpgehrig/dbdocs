This property specifies the value for the XML element that identifies a row of data in an XML document.

### Declaration

    // C#
    public string RowTag {get; set;}

### Property Value

An XML element name.

### Remarks

The default value is `ROW`.

Each element in the XML document identifies one row in a table or view.

If `RowTag` is set to `""` or `null`, no row tag is used in the XML document. In this case, the XML document is assumed to contain only one row.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleXmlSaveProperties Class](OracleXmlSavePropertiesClass.md)

- [OracleXmlSaveProperties Members](XmlSavePropertiesMembers.md)
