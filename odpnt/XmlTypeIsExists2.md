This method checks the existence of a particular set of nodes identified by the XPath expression in the XML document represented by the current `OracleXmlType` instance using a .NET `XmlNameSpaceManager` object for namespace resolution.

### Declaration

    // C#
    public bool IsExists(string xpathExpr, XmlNameSpaceManager nsMgr);

### Parameters

- `xpathExpr`

  The XPath expression.

- `nsMgr`

  The .NET `XmlNameSpaceManager` object used for namespace resolution of the XPath expression. `nsMgr` can be null.

### Return Value

Returns `true` if the required set of nodes exists; otherwise, returns `false`.

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
