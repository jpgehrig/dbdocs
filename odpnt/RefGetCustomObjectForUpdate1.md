This method locks the specified `REF` in the database and returns the object that the specified `REF` references, as a custom type, using the specified wait option.

### Declaration

    // C#
    public object GetCustomObjectForUpdate(bool bWait);

### Parameters

- `bWait`

  Specifies if the `REF` is to be locked with the no-wait option. If wait is set to `true`, this method invocation does not return until the `REF` is locked.

### Return Value

A custom object that represents the object that the specified `REF` references.

### Exceptions

`InvalidOperationException` - The specified connection is not open, or a valid custom type has not been registered for type of the referenced object.

`OracleException` - `bWait` is set to `false`, and the lock cannot be acquired.

### Remarks

This method returns the latest copy of the referenced object, as a custom type, determined by the custom types registered on the `OracleRef` connection.

To be able to release the lock on the `REF` appropriately after flushing the `REF` using the `Flush` method on the `OracleRef` or `FlushCache` method on the `OracleConnection`, the application must commit or rollback the transaction. Therefore, it is required that, before invoking this method, a transaction is explicitly started by executing the `BeginTransaction` method on the `OracleConnection` object.

This method makes a network round-trip to lock the `REF` in the database. After this call, programmers can modify the associated row object exclusively. Then a call to the `Flush` method on the `OracleRef` or `FlushCache` method on the `OracleConnection` flushes the changes to the database.

If `true` is passed, this method blocks until the lock can be acquired. If `false` is passed, this method immediately returns. If the lock cannot be acquired, an `OracleException` is thrown.

The connection must be opened explicitly by the application. This method does not open the connection implicitly.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)

- [OracleRef Members](OracleRefMembers.md)
