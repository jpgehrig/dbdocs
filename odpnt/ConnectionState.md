This property specifies the current state of the connection.

### Declaration

    // C#
    public override ConnectionState State {get;}

### Property Value

The `ConnectionState` of the connection.

### Implements

`IDbConnection`

### Remarks

ODP.NET supports `ConnectionState.Closed` and `ConnectionState.Open` for this property. The default value is `ConnectionState.Closed`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
