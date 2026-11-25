This property specifies the version number of the Oracle database to which the `OracleConnection` has established a connection.

### Declaration

    // C#
    public override string ServerVersion {get;}

### Property Value

The version of the Oracle database.

### Exceptions

`InvalidOperationException` - The connection is closed.

### Remarks

The default is an empty string.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
