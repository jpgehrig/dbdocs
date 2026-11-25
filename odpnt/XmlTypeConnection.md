This property indicates the `OracleConnection` that is used to retrieve and store XML data in the `OracleXmlType`.

### Declaration

    // C#
    public OracleConnection Connection {get;}

### Property Value

An `OracleConnection` object.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The connection must explicitly be opened by the user before creating or using `OracleXmlType`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
