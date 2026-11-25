This property specifies the isolation level for the transaction.

### Declaration

    // C#
    public override IsolationLevel IsolationLevel {get;}

### Property Value

`IsolationLevel`

### Implements

`IDbTransaction`

### Exceptions

`InvalidOperationException` - The transaction has already completed.

### Remarks

Default = `IsolationLevel.ReadCommitted`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleTransaction Class](OracleTransactionClass.md)

- [OracleTransaction Members](TransactionMembers.md)
