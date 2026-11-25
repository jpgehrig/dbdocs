This property indicates the minimum amount of time that the `Open` method can take to obtain a pooled connection before the request is terminated.

### Declaration

    // C#
    public override int ConnectionTimeout {get;}

### Property Value

The minimum time allowed for a pooled connection request, in seconds.

### Implements

`IDbConnection`

### Remarks

This property indicates the connection timeout that has been set using the `ConnectionString` attribute `Connection` `TimeOut`.

This property is read-only.

### Remarks (.NET Stored Procedure)

There is no connection string specified by the application and a connection on the implicit database is always available, therefore, this property is set to `0`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
