This method frees the resources used by the `OracleTransaction` object.

### Declaration

    // C#
    public void Dispose();

### Implements

`IDisposable`

### Remarks

This method releases both the managed and unmanaged resources held by the `OracleTransaction` object. If the transaction is not in a completed state, an attempt to rollback the transaction is made.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleTransaction Class](OracleTransactionClass.md)

- [OracleTransaction Members](TransactionMembers.md)
