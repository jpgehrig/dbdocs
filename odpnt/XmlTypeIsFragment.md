This property indicates whether the XML data is a collection of XML elements or a well-formed XML document.

### Declaration

    // C#
    public bool IsFragment {get;}

### Property Value

Returns `true` if the XML data contained in the `OracleXmlType` object is a collection of XML elements with no root element. Returns `false` otherwise.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
