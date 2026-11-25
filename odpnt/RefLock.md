This instance method locks the `REF` in the database.

### Declaration

    // C#
    public bool Lock(bool bWait);

### Parameters

- `bWait`

  Specifies if the lock is set to the no-wait option. If `bWait` is set to `true`, the method invocation does not return until the `REF` is locked.

### Return Value

A boolean value that indicates whether or not the lock has been acquired.

### Exceptions

`InvalidOperationException` - The associated connection is not open.

`ObjectDisposedException` - The object is already disposed.

### Remarks

In order for the application to release the lock on the `REF` appropriately after the `Flush` invocation on the `OracleRef` or `FlushCache` methods, the application must commit or rollback the transaction. Therefore, it is required that, before invoking a lock on an `OracleRef` object, a transaction is explicitly started by executing the `BeginTransaction` method on the `OracleConnection` object.

This instance method makes a network round-trip to lock the `REF` in the database. After this call, programmers can modify the attribute values of the associated row object exclusively. Then a call to the `Flush` instance method on the `OracleRef` or `FlushCache` method on the `OracleConnection` flushes the changes to the database.

If `true` is passed, this method blocks, that is, does not return, until the lock is acquired. Consequently, the return value is always `true`.

If `false` is passed, this method immediately returns. The return value indicates `true` if the lock is acquired, and `false` if it is not.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)

- [OracleRef Members](OracleRefMembers.md)
