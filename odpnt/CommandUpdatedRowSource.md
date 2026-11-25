This property specifies how query command results are applied to the row to be updated.

### Declaration

    // C#
    public override UpdateRowSource UpdatedRowSource {get; set;}

### Property Value

An `UpdateRowSource`.

### Implements

`IDbCommand`

### Exceptions

`ArgumentException` - The `UpdateRowSource` value specified is invalid.

### Remarks

Always returns UpdateRowSource,

Set accessor throws an `ArgumentException` if the value is other than `UpdateRowSource.None`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)
