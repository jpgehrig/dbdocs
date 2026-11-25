This method adds or refreshes rows in a specified range in the `DataSet` to match rows in the provided `OracleRefCursor` object.

### Declaration

    // C#
    public int Fill(DataSet dataSet, int startRecord, int maxRecords,
       string srcTable, OracleRefCursor refCursor);

### Parameters

- `dataSet`

  The `DataSet` object being populated.

- `startRecord`

  The record number to start with.

- `maxRecords`

  The maximum number of records to obtain.

- `srcTable`

  The name of the source table used in the table mapping.

- `refCursor`

  The `OracleRefCursor` that rows are being retrieved from.

### Return Value

This method returns the number of rows added or refreshed in the `DataSet`. This does not include rows affected by statements that do not return rows.

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
