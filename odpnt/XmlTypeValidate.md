This methods validates whether or not the XML data in the `OracleXmlType` object conforms to the given XML schema.

### Declaration

    // C#
    public bool Validate(String schemaUrl);

### Parameters

- `schemaUrl`

  A string representing the [URL](glossary.md) in the database of the XML schema.

### Return Value

Returns true if the XML data conforms to the XML schema; otherwise, returns false.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentNullException` - The `schemaUrl` argument is null or an empty string.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
