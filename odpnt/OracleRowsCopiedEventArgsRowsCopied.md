This property retrieves a value that represents the number of rows copied during the current bulk copy operation.

### Declaration

    // C#
    public long RowsCopied {get;}

### Property Value

An `Int64` value that returns the number of rows copied.

### Remarks

The value in the `RowsCopied` property is reset by each call to a `WriteToServer` method.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleRowsCopiedEventArgs Class](OracleRowsCopiedEventArgsClass.md)

- [OracleRowsCopiedEventArgs Members](OracleRowsCopiedEventArgsMembers.md)
