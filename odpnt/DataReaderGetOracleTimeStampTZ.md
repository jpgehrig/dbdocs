This method returns an `OracleTimeStampTZ` structure of the specified Oracle `TimeStamp` `WITH` `TIME` `ZONE` column.

### Declaration

    // C#
    public OracleTimeStampTZ GetOracleTimeStampTZ(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The `OracleTimeStampTZ` value of the column.

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

Used with the Oracle Type `TimeStamp` with Local Time Zone columns

`IsDBNull` should be called to check for `NULL` values before calling this method.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
