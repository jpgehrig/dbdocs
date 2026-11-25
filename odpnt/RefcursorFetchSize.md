This property specifies the size that the `OracleDataReader` internal cache needs to store result set data.

### Declaration

    // C#
    public long FetchSize {get; set;}

### Property Value

A `long` that specifies the size (in bytes) of the `OracleRefCursor` internal cache.

### Exceptions

`ArgumentException` - The `FetchSize` value specified is invalid.

### Remarks

Default = `131072`.

The `FetchSize` property value is inherited by the `OracleCommand` that created the `OracleRefCursor` object. The `FetchSize` property on the `OracleDataReader` object determines the amount of data the `OracleRefCursor` fetches into its internal cache for each database round-trip.

This property is useful if the `OracleRefCursor` is explicitly used to fill the `DataSet` or `DataTable` through the `OracleDataAdapter`, because it can provide control on how the data of the `REF` `CURSOR` is fetched.

If an `OracleDataReader` object is created from the `OracleRefCursor`, the resulting `OracleDataReader` object inherits the `FetchSize` value of the `OracleDataReader` object. However, the inherited value can be overridden, if it is set before the first invocation of the `OracleDataReader` `Read` method for the given result set, by setting the `OracleDataReader` `FetchSize` property.

The `RowSize` and `FetchSize` properties handle UDT and `XMLType` data differently than other scalar data types. Because only a reference to the UDT and `XMLType` data is stored in the ODP.NET's internal cache, the `RowSize` property accounts for only the memory needed for the reference (which is very small) and not the actual size of the UDT and `XMLType` data. Thus, applications can inadvertently fetch a large number of UDT or `XMLType` instances from the database in a single database round-trip. This is because the actual size of UDT and `XMLType` data does not count against the `FetchSize,` and it would require numerous UDT and `XMLType` references to fill up the default cache size of 131072 bytes. Therefore, when fetching UDT or `XMLType` data, the `FetchSize` property must be appropriately configured to control the number of UDT and `XMLType` instances that are to be fetched, rather than the amount of the actual UDT and `XMLType` data to be fetched.

NOTE: For LOB and `LONG` data types, only the sizes specified in the `InitialLOBFetchSize` and `InitialLONGFetchSize` properties are accounted for by the `RowSize` property in addition to the metadata and reference information that is maintained by the cache for each LOB in the select list.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRefCursor Class](OracleRefCursorClass.md)

- [OracleRefCursor Members](RefCursorMembers.md)
