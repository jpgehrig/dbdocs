This method transforms the current `OracleXmlType` instance into another `OracleXmlType` instance using the given XSL document and a string of XSLT parameters.

### Declaration

    // C#
    public OracleXmlType Transform(string xsldoc, string paramMap);

### Parameters

- `xsldoc`

  The XSL document to be used for XSLT.

- `paramMap`

  A string which provides the parameters for the XSL document.

  For this release, `paramMap` is ignored.

### Return Value

An `OracleXmlType` object containing the transformed XML document.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`ArgumentNullException` - The `xsldoc` parameter is null.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
