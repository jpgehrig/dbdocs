This method extracts a subset from the XML data represented by the `OracleXmlType` object using the given XPath expression and a string parameter for namespace resolution.

### Declaration

    // C#
    public OracleXmlType Extract(string xpathExpr, string nsMap);

### Parameters

- `xpathExpr`

  The XPath expression.

- `nsMap`

  The string parameter used for namespace resolution of the XPath expression. `nsMap` has zero or more namespaces separated by spaces. `nsMap` can be null. For example:

       xmlns:nsi"=http://www.company1.com" xmlns:nsz="http://www.company2.com"

### Return Value

An `OracleXmlType` object.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`ArgumentNullException` - The `xpathExpr` is null or zero-length.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
