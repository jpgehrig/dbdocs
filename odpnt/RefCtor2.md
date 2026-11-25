This constructor creates an instance of the `OracleRef` class using the specified `OracleConnection` object, user-defined type name, and an object table name.

### Declaration

    // C#
    public OracleRef(OracleConnection con, string udtTypeName, string objTabName);

### Parameters

- `con`

  An `OracleConnection` instance.

- `udtTypeName`

  A user-defined type name.

- `objTabName`

  An object table name.

### Exceptions

`ArgumentException` - The object type name or the object table name is not valid.

`ArgumentNullException` - The object type name or the table name is null.

`InvalidOperationException` - The `OracleConnection` object is not open.

### Remarks

When an `OracleRef` instance is created, this `OracleRef` instance is associated with the specific table in the database. In other words, it represents a persistent `REF`.

This constructor creates a reference to the object table. However, it does not cause any entries to be made in database tables until the object is flushed to the database, that is, until the `OracleRef.Flush` or the `OracleConnection.FlushCache` method is called on the `OracleRef` Connection. Therefore, any operation that attempts to operate on the database copy of the object before flushing the object, such as, lock the object or fetch the latest copy of the object from the database, results in an `OracleException`.

The connection must be opened explicitly by the application. `OracleRef` does not open the connection implicitly.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)

- [OracleRef Members](OracleRefMembers.md)

- "[FlushCache](ConnectionFlushCache.md)"
