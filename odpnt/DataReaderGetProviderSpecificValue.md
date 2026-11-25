This method returns an object that represents the underlying provider-specific value of the specified ordinal.

### Declaration

    // C#
    public override object GetProviderSpecificValue (int index);

### Parameters

`index`

A zero-based column index.

### Return Value

An `Object` that is a representation of the underlying provider-specific field type.

### Exceptions

`IndexOutOfRangeException` - The column index is invalid.

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called or all rows have been read.

### Remarks

If the column is an Oracle object or collection column, and a custom type mapping exists, a custom type is returned.

If the column is an Oracle `REF` column, an `OracleRef` is returned.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
