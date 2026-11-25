This property creates a mapping between column names in the result set to .NET types that represent column values in the `DataSet`, to preserve the data.

### Declaration

    // C#
    public Hashtable SafeMapping {get; set;}

### Property Value

A hash table.

### Remarks

Default = `null`

The `SafeMapping` property is used, when necessary, to preserve data in the following types:

- `DATE`

- `TimeStamp` (refers to all `TimeStamp` objects)

- `INTERVAL` `DAY` `TO` `SECOND`

- `NUMBER`

### Example

See the example in "[OracleDataAdapter Safe Type Mapping](featSafeType.md)".

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)

- "[OracleDataAdapter Safe Type Mapping](featSafeType.md)"
