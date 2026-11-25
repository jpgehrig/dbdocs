This method advances the data reader to the next result set.

### Declaration

    // C#
    public override bool NextResult();

### Return Value

Returns `true` if another result set exists; otherwise, returns `false`.

### Implements

`IDataReader`

### Exceptions

`InvalidOperationException` - The connection is closed or the reader is closed.

### Remarks

`NextResult` is used when reading results from stored procedure execution that return more than one result set.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
