This method adds or refreshes rows in the specified source table of the `DataSet` to match those in the provided `OracleRefCursor` object.

### Declaration

    // C#
    public int Fill(DataSet dataSet, string srcTable, OracleRefCursor
       refCursor);

### Parameters

- `dataSet`

  The `DataSet` object being populated.

- `srcTable`

  The name of the source table used in the table mapping.

- `refCursor`

  The `OracleRefCursor` that rows are being retrieved from.

### Return Value

Returns the number of rows added or refreshed into the `DataSet`.

### Exceptions

`ArgumentNullException` - The `dataSet` or `refCursor` parameter is null.

`InvalidOperationException` - The `OracleRefCursor` is already being used to fetch data or the source table name is invalid.

`NotSupportedException` - The `SafeMapping` type is not supported.

### Remarks

No schema or key information is provided, even if the `Fill` method is called with `MissingSchemaAction` set to `MissingSchemaAction.AddWithKey`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)

- "[OracleDataAdapter Requery Property](featRequery.md)"
