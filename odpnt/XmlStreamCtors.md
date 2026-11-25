This constructor creates an instance of an `OracleXmlStream` object which provides a `Stream` representation of the XML data stored in an `OracleXmlType` object.

### Declaration

    // C#
    public OracleXmlStream(OracleXmlType xmlType);

### Parameters

- `xmlType`

  The `OracleXmlType` object.

### Remarks

The `OracleXmlStream` implicitly uses the `OracleConnection` object from the `OracleXmlType` object from which it was constructed.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlStream Class](OracleXmlStreamClass.md)

- [OracleXmlStream Members](XmlStreamMembers.md)
