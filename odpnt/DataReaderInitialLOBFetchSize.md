This property specifies the amount that the `OracleDataReader` initially fetches for LOB columns.

### Declaration

    // C#
    public int InitialLOBFetchSize {get;}

### Property Value

The size of the chunk to retrieve.

### Exceptions

`InvalidOperationException` - The reader is closed.

### Remarks

The maximum value supported for `InitialLOBFetchSize` is 2 GB.

Default is the `OracleCommand.InitialLOBFetchSize`, from which this value is inherited.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)

- "[InitialLOBFetchSize](CommandInitialLOBFetchSize.md)" for further information on `OracleCommand.InitialLOBFetchSize`

- "[Obtaining LOB Data](featData.md)"
