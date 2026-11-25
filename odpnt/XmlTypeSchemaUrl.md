This property represents the XML schema in the database for the XML schema of the XML data contained in the `OracleXmlType`.

### Declaration

    // C#
    public string SchemaUrl {get;}

### Property Value

A string that represents the URL in the database for the XML schema of the XML data.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

If the `OracleXmlType` instance contains non-schema based XML data, this property returns an empty string.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
