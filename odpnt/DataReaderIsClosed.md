This property indicates whether or not the data reader is closed.

### Declaration

    // C#
    public override bool IsClosed {get;}

### Property Value

If the `OracleDataReader` is in a closed state, returns `true`; otherwise, returns `false`.

### Implements

`IDataReader`

### Remarks

Default = `true`

`IsClosed` and `RecordsAffected` are the only two properties that are accessible after the `OracleDataReader` is closed.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
