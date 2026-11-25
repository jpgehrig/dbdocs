This method begins a local transaction.

### Declaration

    // C#
    public OracleTransaction BeginTransaction();

### Return Value

An `OracleTransaction` object representing the new transaction.

### Implements

`IDbConnection`

### Exceptions

`InvalidOperationException` - A transaction has already been started.

### Remarks

The transaction is created with its isolation level set to its default value of `IsolationLevel.ReadCommitted`. All further operations related to the transaction must be performed on the returned `OracleTransaction` object.

### Remarks (.NET Stored Procedure)

Using this method in a .NET stored procedure for context connection causes a Not Supported exception.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
