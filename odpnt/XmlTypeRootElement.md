This property represents the name of the top-level or root element of the schema-based XML data contained in the `OracleXmlType`.

### Declaration

    // C#
    public string RootElement{get;}

### Property Value

A string that represents the name of the top-level or root element of the XML data contained in the `OracleXmlType`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

If the `OracleXmlType` instance contains non-schema based XML data, this property returns an empty string.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
