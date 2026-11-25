The `GetOutcome` method retrieves the transaction outcome from the database server. The method will determine whether the transaction committed and completed or not.

### Overload List:

- `GetOutcome(string` `constring`, `byte[]` `ltxid`, `out bool?` `bCommitted`, `out bool?` `bUserCallCompleted`)

  The application can use this static method to determine the outcome if the outcome was not known when the exception was raised.

  The application will need to obtain the connection string and `logical transaction id` from the `OracleException.OracleLogicalTransaction` object before calling this method.

  The supplied connection string will be used to establish a connection to the database to determine the outcome of the provided logical transaction id.

  ODP.NET implicitly calls `GetOutcome` under the following conditions:

  - Transaction Guard is enabled on the service

  - OracleException is raised

  - The exception is a recoverable error

  When all of the above is true, then the `OracleException.OracleLogicalTransaction` property will be non-null.

  If a connection is involved in a distributed transaction, then `GetOutcome` is not called implicitly and the `OracleException.OracleLogicalTransaction.LogicalTransactionId` property returns null.

**Note:**

Once one server round-trip is incurred for the `GetOutcome()` `invocation`, the PL/SQL `ForceOutcome` is never invoked again against the server for a given `OracleLogicalTransaction` object.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleLogicalTransaction Class](OracleLogicalTransactionClass.md)

- [OracleLogicalTransaction Members](LogicalTransactionMembers.md)
