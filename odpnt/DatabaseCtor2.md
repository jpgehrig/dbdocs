The `OracleDatabase` constructor instantiates a new instance of the `OracleDatabase` class using the supplied connection string and `OracleCredential` object.

### Declaration

    // C#
    public OracleDatabase(string connectionString, OracleCredential orclCredential)

### Parameters

- `connectionString`

  connection string that does not contain any of `user id`, `password`, `DBA Privilege`, `proxy user id`, nor `proxy password`.

- `orclCredential`

  `OracleCredential` object containing user credentials. If this parameter is passed as null then `OracleConnection`’s behavior will be same as `OracleConnection` with normal connection string.

### Exceptions

`InvalidOperationException` is raised when non-null `OracleCredential` object is used with a connection string containing any of `user id`, `password`, `DBA Privilege`, `proxy user id`, or `proxy password`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDatabase Class](OracleDatabaseClass.md)

- [OracleDatabase Members](DatabaseMembers.md)
