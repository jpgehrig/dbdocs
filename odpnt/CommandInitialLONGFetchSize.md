This property specifies the amount of data that the `OracleDataReader` initially fetches for `LONG` and `LONG` `RAW` columns.

### Declaration

    // C#
    public int InitialLONGFetchSize {get; set;}

### Property Value

An `int` specifying the amount.

### Exceptions

`ArgumentException` - The `InitialLONGFetchSize` value specified is invalid.

### Remarks

The maximum value supported for `InitialLONGFetchSize` is `32767`. If this property is set to a higher value, the provider resets it to `32767`.

The value of `InitialLONGFetchSize` specifies the initial amount of `LONG` or `LONG` `RAW` data that is immediately fetched by the `OracleDataReader`. The property value specifies the number of characters for `LONG` data and the number of bytes for `LONG` `RAW`. To fetch more than the specified `InitialLONGFetchSize` amount, one of the following must be in the select list:

- Primary key

- `ROWID`

- Unique columns - (defined as a set of columns on which a unique constraint has been defined or a unique index has been created, where at least one of the columns in the set has a `NOT` `NULL` constraint defined on it)

The `InitialLONGFetchSize` value is used to determine the length of the `LONG` and `LONG` `RAW` column data to fetch if one of the two is in the select list. If the select list does not contain a `LONG` or a `LONG` `RAW` column, the `InitialLONGFetchSize` value is ignored.

When `InitialLONGFetchSize` is set to `-1`, the entire `LONG` or `LONG` `RAW` data is prefetched and stored in the fetch array. Calls to `GetString`, `GetChars`, or `GetBytes` in `OracleDataReader` allow retrieving the entire data.

Default = `0`.

Setting this property to `0` defers the `LONG` and `LONG` `RAW` data retrieval entirely until the application specifically requests it.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- "[Obtaining LONG and LONG RAW Data](featData.md)" for further information
