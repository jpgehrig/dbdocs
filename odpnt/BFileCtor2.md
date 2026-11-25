This constructor creates an instance of the `OracleBFile` class with an `OracleConnection` object, the location of the `BFILE`, and the name of the `BFILE`.

### Declaration

    // C#
    public OracleBFile(OracleConnection con, string directoryName, string
       fileName);

### Parameters

- `con`

  The `OracleConnection` object.

- `directoryName`

  The directory alias created by the `CREATE` `DIRECTORY` SQL statement.

- `fileName`

  The name of the external LOB.

### Exceptions

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The `OracleConnection` must be opened explicitly by the application. `OracleBFile` does not open the connection implicitly.

To initialize a `BFILE` column using an `OracleBFile` instance as an input parameter of a SQL `INSERT` statement, `directoryName` and `fileName` must be properly set.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
