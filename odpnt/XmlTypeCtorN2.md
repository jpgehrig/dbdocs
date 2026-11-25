This constructor creates an instance of the `OracleXmlType` class using the XML data contained in the .NET `String`.

### Declaration

    // C#
    public OracleXmlType(OracleConnection con, string xmlData);

### Parameters

- `con`

  An `OracleConnection` object.

- `xmlData`

  A string containing the XML data.

### Exceptions

`ArgumentNullException - `The `OracleConnection` object is null.

`ArgumentException - `The `xmlData` argument is an empty string.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The new `OracleXmlType` uses the given `OracleConnection` object to store data for the current instance.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
