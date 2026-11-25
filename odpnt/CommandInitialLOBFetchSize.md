This property specifies the amount of data that the `OracleDataReader` initially fetches for LOB columns.

### Declaration

    // C#
    public int InitialLOBFetchSize {get; set;}

### Property Value

An `int` specifying the number of characters or bytes to fetch initially.

### Exceptions

`ArgumentException` - The `InitialLOBFetchSize` value specified is invalid.

### Remarks

The value of `InitialLOBFetchSize` specifies the initial amount of LOB data that is immediately fetched by the `OracleDataReader`. The property value specifies the number of characters for `CLOB` and `NCLOB` data, and the number of bytes for `BLOB` data.

The `InitialLOBFetchSize` value is used to determine the length of the LOB column data to fetch, if the LOB column is in the select list. If the select list does not contain a LOB column, the `InitialLOBFetchSize` value is ignored.

When `InitialLOBFetchSize` is set to `-1`, the entire LOB data is prefetched and stored in the fetch array.

Default = 0.

The maximum value supported for `InitialLOBFetchSize` is 2 GB.

`GetOracleBlob` and `GetOracleClob` methods can be used to retrieve any LOBs no matter the `InitialLOBFetchSize` value.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- "[Obtaining LOB Data](featData.md)" for more information on setting `InitialLOBFetchSize` values
