This constructor creates a new instance of the `OracleRowsCopiedEventArgs` object.

### Declaration

    // C#
    public OracleRowsCopiedEventArgs(long rowsCopied);

### Parameters

- `rowsCopied`

  An `Int64` value that indicates the number of rows copied during the current bulk copy operation.

### Remarks

The value in the `rowsCopied` parameter is reset by each call to a `WriteToServer` method.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleRowsCopiedEventArgs Class](OracleRowsCopiedEventArgsClass.md)

- [OracleRowsCopiedEventArgs Members](OracleRowsCopiedEventArgsMembers.md)
