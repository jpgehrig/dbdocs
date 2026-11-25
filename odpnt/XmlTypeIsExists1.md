This method checks for the existence of a particular set of nodes identified by the XPath expression in the XML data represented by the current `OracleXmlType` instance using a string parameter for namespace resolution.

### Declaration

    // C#
    public bool IsExists(string xpathExpr, string nsMap);

### Parameters

- `xpathExpr`

  The XPath expression.

- `nsMap`

  The string parameter used for namespace resolution of the XPath expression. `nsMap` has zero or more namespaces separated by spaces. `nsMap` can be null.

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
