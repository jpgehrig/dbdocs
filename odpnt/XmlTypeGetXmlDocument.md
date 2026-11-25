This public method returns a `XmlDocument` object containing the XML data stored in this `OracleXmlType` instance.

### Declaration

    // C#
    public XmlDocument GetXmlDocument();

### Return Value

An `XmlDocument` object.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The XML data in the `XmlDocument` object is a copy of the XML data in the `OracleXmlType` instance and modifying it does not automatically modify the XML data in the `OracleXmlType` instance. The `XmlDocument` instance returned has the `PreserveWhitespace` property set to `true`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
