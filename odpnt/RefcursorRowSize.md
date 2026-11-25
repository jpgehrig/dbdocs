This property specifies the amount of memory the `OracleRefcursor` internal cache needs to store one row of data.

### Declaration

    // C#
    public long RowSize {get;}

### Property Value

A `long` that indicates the amount of memory (in bytes) that an `OracleRefcursor` needs to store one row of data for the executed query.

### Remarks

The `RowSize` property is set to a nonzero value when the `OracleRefcursor` object is created. This property can be used at design time or dynamically during run time, to set the `FetchSize`, based on number of rows. For example, to enable the `OracleRefcursor` to fetch `N` rows for each database round-trip, the `OracleRefcursor` `FetchSize` property can be set dynamically to `RowSize` `*` `N`. Note that for the `FetchSize` to take effect appropriately, it must be set before the it is used to fill the `DataSet`/`DataTable` using `OracleDataAdapter`.

If an `OracleDataReader` is obtained from the `OracleRefCursor` through the `GetDataReader` method, the resulting `OracleDataReader` will have its `FetchSize` property set to the `FetchSize` value of the `OracleRefCursor`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRefCursor Class](OracleRefCursorClass.md)

- [OracleRefCursor Members](RefCursorMembers.md)
