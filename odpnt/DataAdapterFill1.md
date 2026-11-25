This method adds or refreshes rows in the specified `DataTable` to match those in the provided `OracleRefCursor` object.

### Declaration

    // C#
    public int Fill(DataTable dataTable, OracleRefCursor refCursor);

### Parameters

- `dataTable`

  The `DataTable` object being populated.

- `refCursor`

  The `OracleRefCursor` that rows are being retrieved from.

### Return Value

The number of rows added to or refreshed in the `DataTable`.

### Exceptions

`ArgumentNullException` - The `dataTable` or `refCursor` parameter is null.

`InvalidOperationException` - The `OracleRefCursor` is already being used to fetch data.

`NotSupportedException` - The `SafeMapping` type is not supported.

### Remarks

No schema or key information is provided, even if the `Fill` method is called with `MissingSchemaAction` set to `MissingSchemaAction.AddWithKey`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)

- "[OracleDataAdapter Requery Property](featRequery.md)"
