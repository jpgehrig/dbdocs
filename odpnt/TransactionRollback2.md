This method rolls back a database transaction to a [savepoint](glossary.md) within the current transaction.

### Declaration

    // C#
    public override void Rollback(string savepointName);

### Parameters

- `savepointName`

  The name of the savepoint to rollback to, in the current transaction.

### Exceptions

`InvalidOperationException` - The transaction has already been completed successfully, has been rolled back, or the associated connection is closed.

### Remarks

After a rollback to a savepoint, the current transaction remains active and can be used for further operations.

The `savepointName` specified does not have to match the case of the `savepointName` created using the `Save` method, since savepoints are created in the database in a case-insensitive manner.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleTransaction Class](OracleTransactionClass.md)

- [OracleTransaction Members](TransactionMembers.md)
