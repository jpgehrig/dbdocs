This property gets the amount of memory the internal cache of the `OracleDataReader` needs to store one row of data.

### Declaration

    // C#
    public long RowSize {get;}

### Property Value

A `long` that indicates the amount of memory (in bytes) that an `OracleDataReader` needs to store one row of data for the executed query.

### Remarks

The `RowSize` property is set to a nonzero value when the `OracleDataReader` object is created. This property can be used at design time or dynamically during runtime, to set the `FetchSize` property, based on the number of rows. For example, to enable the `OracleDataReader` object to fetch `N` rows for each database round-trip, the `OracleDataReader` `FetchSize` property can be set dynamically to `RowSize` `*` `N`. Note that for the `FetchSize` property to take effect appropriately, it must be set before the first invocation of `OracleDataReader.Read()` for the particular result set.

ODP.NET now supports values up to 32K for `VARCHAR2`, `NVARCHAR2` or `RAW` type columns in its calculation of `RowSize` value

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)

- "[FetchSize](DataReaderFetchSize.md)"
