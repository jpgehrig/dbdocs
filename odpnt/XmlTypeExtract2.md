This public method extracts a subset from the XML data represented by the `OracleXmlType` object, using the given XPath expression and a .NET `XmlNameSpaceManager` object for namespace resolution.

### Declaration

    // C#
    public OracleXmlType Extract(string xpathExpr, XmlNameSpaceManager nsMgr);

### Parameters

- `xpathExpr`

  The XPath expression.

- `nsMgr`

  The .NET `XmlNameSpaceManager` object used for namespace resolution of the XPath expression. `nsMgr` can be null.

### Return Value

An `OracleXmlType`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`ArgumentNullException` - The `xpathExpr` is null or zero-length.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The default namespace is ignored if its value is an empty string.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
