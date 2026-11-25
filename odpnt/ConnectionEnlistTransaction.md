This method enlists the connection to the specified transaction.

### Declaration

    // C#
    public override void EnlistTransaction(Transaction transaction)


### Parameters

- `transaction`

  A `System.Transactions.Transaction` object.

### Exceptions

`InvalidOperationException` - The connection is part of a local transaction or the connection is closed.

### Remarks

Invocation of this method immediately enlists the connection to a transaction that is specified by the provided transaction parameter.

If `OracleConnection` is still associated with a distributed transaction that has not completed from a previous `EnlistTransaction` method invocation, calling this method will cause an exception to be thrown.

In general, for transaction enlistments to succeed, the `"enlist"` connection string attribute must be set to `"true"` before invoking the `Open` method. Setting the `"enlist"` connection string attribute to `"true"` will implicitly enlist the connection when the `Open` method is called, if the connection is within a transaction context. The `"enlist"` attribute should be set to `"false"` or "`dynamic`" only if the connection will never enlist in a transaction.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- "[System.Transactions and Promotable Transactions](featOraCommand.md)"

- "[EnlistDistributedTransaction](ConnectionEnlistDistributedTransaction.md)"
