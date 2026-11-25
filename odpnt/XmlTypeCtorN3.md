This constructor creates an instance of the `OracleXmlType` class using the contents of the .NET `XmlReader` object.

### Declaration

    // C#
    public OracleXmlType(OracleConnection con, XmlReader reader);

### Parameters

- `con`

  An `OracleConnection` object.

- `reader`

  An `XmlReader` object.

### Exceptions

`ArgumentNullException - `The `OracleConnection` object is null.

`ArgumentException` - The `reader` argument contains no data.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The new `OracleXMLType` uses the given `OracleConnection` object to store data for the current instance.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
