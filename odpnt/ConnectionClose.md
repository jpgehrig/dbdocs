This method closes the connection to the database.

### Declaration

    // C#
    public override void Close();

### Implements

`IDbConnection`

### Remarks

Performs the following:

- Rolls back any pending local transactions that are not yet committed. Distributed transactions will rely on the distributed transaction coordinator on whether roll back is necessary.

- Places the connection to the connection pool if connection pooling is enabled. Even if connection pooling is enabled, the connection can be closed if it exceeds the connection lifetime specified in the connection string. If connection pooling is disabled, the connection is closed.

- Closes the connection to the database.

The connection can be reopened using `Open()`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
