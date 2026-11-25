This method returns the `type` of the specified column.

### Declaration

    // C#
    public override Type GetFieldType(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The `type` of the default .NET type of the column.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The reader is closed, or the specified column is a UDT but no registered custom type mapping exists for the UDT.

`IndexOutOfRangeException` - The column index is invalid.

### Remarks

`GetFieldType` returns a type that corresponds to the value that the application obtains after invoking the `GetValue` accessor or `Item` property on the `OracleDataReader`. For example, if the column is a string, this method returns a .NET Type object for a .NET string.

If the attribute is a UDT, this method may return either of the following:

- A .NET Type of the custom type if a custom type mapping exists for the Oracle object or collection.

- A .NET Type of string if the column is an Oracle `REF`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
