This method returns the name of the specified column.

### Declaration

    // C#
    public override string GetName(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The name of the column.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The reader is closed.

`IndexOutOfRangeException` - The column index is invalid.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
