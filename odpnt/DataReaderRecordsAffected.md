This property gets the number of rows changed, inserted, or deleted by execution of the SQL statement.

### Declaration

    // C#
    public int RecordsAffected {get;}

### Property Value

The number of rows affected by execution of the SQL statement.

### Implements

`IDataReader`

### Remarks

Default = `0`

The value of `-1` is returned for `SELECT` statements.

`IsClosed` and `RecordsAffected` are the only two properties that are accessible after the `OracleDataReader` is closed.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
