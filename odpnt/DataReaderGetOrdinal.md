This method returns the `0`-based ordinal (or index) of the specified column name.

### Declaration

    // C#
    public override int GetOrdinal(string name);

### Parameters

- `name`

  The specified column name.

### Return Value

The index of the column.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The reader is closed.

`IndexOutOfRangeException` - The column index is invalid.

### Remarks

A case-sensitive search is made to locate the specified column by its name. If this fails, then a case-insensitive search is made.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
