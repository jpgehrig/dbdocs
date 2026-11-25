This constructor instantiates a new `OracleConnection` class instance using the provided connection string and `OracleCredential` class.

### Declaration

    // C#
    public OracleConnection(string connectionString, OracleCredential orclCredential);

### Parameters

- `connectionString`

  connection string that does not contain any of `user id`, `password`, `DBA Privilege`, `proxy user id`, nor `proxy password`.

- `orclCredential`

  `OracleCredential` object containing user credentials. If this parameter is passed as null then the behavior of `OracleConnection` will be same as `OracleConnection` with normal connection string.

### Remarks

Use this constructor to create a new `OracleConnection` object with an `OracleCredential` object containing user credentials and a connection string that does not contain any of `user id`, `password`, `DBA Privilege`, `proxy user id`, nor `proxy password`.

### Exceptions

`InvalidOperationException` is raised when non-null `OracleCredential` object is used with a connection string containing any of `user id`, `password`, `DBA Privilege`, `proxy user id`, or `proxy password`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
