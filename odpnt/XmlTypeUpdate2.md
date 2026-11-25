This method updates the XML nodes identified by the given XPath expression with the given string value and a .NET `XmlNameSpaceManager` object for namespace resolution.

### Declaration

    // C#
    public void Update(string xpathExpr, XmlNameSpaceManager nsMgr, string
      value);

### Parameters

- `xpathExpr`

  The XPath expression that identifies the nodes to update.

- `nsMgr`

  The .NET `XmlNameSpaceManager` object used for namespace resolution of the XPath expression. `nsMgr` can be null.

- `value`

  The new value as a `string`.

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
