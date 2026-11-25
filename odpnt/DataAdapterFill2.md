This method adds or refreshes rows in the `DataSet` to match those in the provided `OracleRefCursor` object.

### Declaration

    // C#
    public int Fill(DataSet dataSet, OracleRefCursor refCursor);

### Parameters

- `dataSet`

  The `DataSet` object being populated.

- `refCursor`

  The `OracleRefCursor` that rows are being retrieved from.

### Return Value

Returns the number of rows added or refreshed in the `DataSet`.

### Exceptions

`ArgumentNullException` - The `dataSet` or `refCursor` parameter is null.

`InvalidOperationException` - The `OracleRefCursor` is already being used to fetch data.

`InvalidOperationException` - The `OracleRefCursor` is ready to fetch data.

`NotSupportedException` - The `SafeMapping` type is not supported.

### Remarks

If there is no `DataTable` to refresh, a new `DataTable` named `Table` is created and populated using the provided `OracleRefCursor` object.

No schema or key information is provided, even if the `Fill` method is called with `MissingSchemaAction` set to `MissingSchemaAction.AddWithKey`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)

- "[OracleDataAdapter Requery Property](featRequery.md)"
