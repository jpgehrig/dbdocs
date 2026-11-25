This instance property indicates whether or not the object referenced by the Oracle `REF` in the object cache has any changes that can be flushed to the database.

### Declaration

    // C#
    public bool HasChanges {get;}

### Property Value

Returns `true` if the object referenced by the Oracle `REF` in the object cache has any changes that can be flushed to the database; otherwise, returns `false`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

This property returns `true` if a copy of the referenced object in the object cache is updated or deleted.

If there is no copy of the referenced object in the object cache, the latest copy of the referenced object in the database is cached in the object cache and `false` is returned.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)

- [OracleRef Members](OracleRefMembers.md)
