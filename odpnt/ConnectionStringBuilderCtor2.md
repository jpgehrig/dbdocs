This constructor instantiates a new instance of the `OracleConnectionStringBuilder` class with the provided connection string.

### Declaration

    // C#
    public OracleConnectionStringBuilder(string connectionString);

### Parameters

- `connectionString`

  The connection information.

### Exceptions

`ArgumentNullException` - The `connectionString` parameter is null.

`ArgumentException` - The `connectionString` parameter is invalid.

### Remarks

The `ConnectionString` property of this instance is set to the supplied connection string.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)

- [OracleConnectionStringBuilder Members](OracleConnectionStringBuilderMembers.md)
