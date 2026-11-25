This method deletes the referenced object from the database.

### Declaration

    // C#
    public void Delete(bool bFlush);

### Parameters

- `bFlush`

  A `bool` that specifies whether or not the `REF` is flushed immediately.

### Remarks

This method marks the specified `REF` for deletion.

Depending on whether the value of `bFlush` is set to `true` or `false`, the following occurs:

- `True`

  The object referenced by the specified `REF` is deleted immediately from the database.

  Before flushing objects, it is required that the application has explicitly started a transaction by executing the `BeginTransaction` method on the `OracleConnection` object. This is because if the object being flushed has not already been locked by the application, an exclusive lock is obtained implicitly for the object. The lock is only released when the transaction commits or rollbacks.

- `False`

  The object referenced by the `REF` is not deleted immediately from the database, but only when a subsequent `Flush` method is invoked for the specified `REF` or the `FlushCache` method is invoked on the `OracleRef` or the `FlushCache` method is invoked on the `OracleRef` connection.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)

- [OracleRef Members](OracleRefMembers.md)

- OracleConnection "[FlushCache](ConnectionFlushCache.md)"
