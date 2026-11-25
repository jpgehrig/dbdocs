This constructor instantiates a new instance of the `OracleConnection` class with the provided connection string.

### Declaration

    // C#
    public OracleConnection(string connectionString);

### Parameters

- `connectionString`

  The connection information used to connect to the Oracle database.

### Remarks

The `ConnectionString` property is set to the supplied `connectionString`. The `ConnectionString` property is parsed and an exception is thrown if it contains invalid connection string attributes or attribute values.

The properties of the `OracleConnection` object default to the following values unless they are set by the connection string:

- `ConnectionString` = empty string

- `ConnectionTimeout` = `15` (default value of `0` is used for the implicit database connection)

- `DataSource` = empty string

- `ServerVersion` = empty string

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
