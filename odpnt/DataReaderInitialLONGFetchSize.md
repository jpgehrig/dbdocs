This property specifies the amount that the `OracleDataReader` initially fetches for `LONG` and `LONG` `RAW` columns.

### Declaration

    // C#
    public long InitialLONGFetchSize {get;}

### Property Value

The size of the chunk to retrieve. The default is `0`.

### Exceptions

`InvalidOperationException` - The reader is closed.

### Remarks

The maximum value supported for `InitialLONGFetchSize` is `32767`. If this property is set to a higher value, the provider resets it to `32767`.

Default is `OracleCommand.InitialLONGFetchSize`, from which this value is inherited.

This property is read-only for the `OracleDataReader`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)

- "[InitialLONGFetchSize](CommandInitialLONGFetchSize.md)" for further information on `OracleCommand.InitialLONGFetchSize`

- "[Obtaining LONG and LONG RAW Data](featData.md)"
