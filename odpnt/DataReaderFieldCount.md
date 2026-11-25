This property returns the number of columns in the result set.

### Declaration

    // C#
    public override int FieldCount {get;}

### Property Value

The number of columns in the result set if one exists, otherwise `0`.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The reader is closed.

### Remarks

Default = `0`

This property has a value of 0 for queries that do not return result sets.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
