This property gets a value indicating the depth of nesting for the current row.

### Declaration

    // C#
    public override int Depth {get;}

### Property Value

The depth of nesting for the current row.

### Implements

`IDataReader`

### Exceptions

`InvalidOperationException` - The reader is closed.

### Remarks

Default = `0`

This property always returns zero because Oracle does not support nesting.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
