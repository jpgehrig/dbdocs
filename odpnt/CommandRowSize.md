This property specifies the amount of memory needed by the `OracleDataReader` internal cache to store one row of data.

### Declaration

    // C#
    public long RowSize {get;}

### Property Value

A `long` that indicates the amount of memory (in bytes) that an `OracleDataReader` needs to store one row of data for the executed query.

### Remarks

Default value = `0`

The `RowSize` property is set to a nonzero value after the execution of a command that returns a result set. This property can be used at design time or dynamically during runtime, to set the `FetchSize`, based on number of rows. For example, to enable the `OracleDataReader` to fetch `N` rows for each database round-trip, the `OracleDataReader` `FetchSize` property can be set dynamically to `RowSize * N`. Note that for the `FetchSize` to take effect appropriately, it must be set after `OracleCommand.ExecuteReader()` but before `OracleDataReader.Read()`.

ODP.NET now supports values up to 32K for `VARCHAR2`, `NVARCHAR2` or `RAW` type columns in its calculation of `RowSize` value.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- `OracleDataReader` "[FetchSize](CommandFetchSize.md)"
