This method updates the object referenced by the specified `REF` in the database using the specified custom object.

### Declaration

    // C#
    public void Update(object customObject, bool bFlush);

### Parameters

- `customObject`

  The custom object used to update the referenced object.

- `bFlush`

  A boolean that specifies if the changes must be flushed immediately. If `bFlush` is set to true, this method invocation flushes the changes immediately.

### Exceptions

`InvalidOperationException` - The specified connection is not open or the custom object does not map to the type of referenced object.

### Remarks

This method marks the specified `REF` for update. Depending on whether the value of `bFlush` is set to true or false, the following occurs:

- True

  The object referenced by the specified `REF` is updated immediately in the database.

  Before flushing objects, it is required that the application has explicitly started a transaction by executing the `BeginTransaction` method on the `OracleConnection` object. This is because if the object being flushed has not already been locked by the application, an exclusive lock is obtained implicitly for the object. The lock is only released when the transaction commits or rollbacks.

- False

  The object referenced by the `REF` is not updated immediately in the database, but only when a subsequent `Flush` method is invoked for the specified `REF` or the `FlushCache` method is invoked for the specified connection.

The connection must be opened explicitly by the application. This method does not open the connection implicitly.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)

- [OracleRef Members](OracleRefMembers.md)
