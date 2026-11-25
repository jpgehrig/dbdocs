This method returns the provider-specific type of the specified column.

### Declaration

    // C#public override Type GetProviderSpecificFieldType(int index);

### Parameters

- `index`

  A zero-based column index.

### Return Value

The provider-specific type of the specified column. This is a member of the `Oracle.DataAccess.Types` namespace.

### Exceptions

`IndexOutOfRangeException` - The column index is invalid.

`InvalidOperationException` - The reader is closed, or the specified column is a UDT but no registered custom type mapping exists for the UDT.

### Remarks

`GetProviderSpecficFieldType` returns a type that corresponds to the value the application obtains after invoking the `GetProviderSpecificValue` accessor on the `OracleDataReader`. For example, if the column is a string, this method returns a .NET Type object for an `OracleString`.

If the attribute is a UDT, this method may return any of the following:

- A .NET Type of the custom type, if the column is an Oracle object or Oracle collection column and a custom type mapping exists.

- A .NET Type of `OracleRef` if the column is an Oracle `REF`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
