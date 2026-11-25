This method returns an array of objects that represent the underlying provider-specific values.

### Declaration

    // C#
    public override int GetProviderSpecificValues(object [ ] values);

### Parameters

- `values`

  An array of objects.

### Return Value

The number of `Object` instances in the array.

### Exceptions

`InvalidOperationException` - The reader is closed.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
