This property refers to the `OracleConnection` used to fetch the `REF` `CURSOR` data.

### Declaration

    // C#
    public OracleConnection Connection {get;}

### Property Value

An `OracleConnection.`

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

This property is bound to a `REF` `CURSOR` once it is set. After the `OracleRefCursor` object is created by the constructor, this property is initially `null`. An `OracleRefCursor` object can be bound to a `REF` `CURSOR` after a command execution.

If the connection is closed or returned to the connection pool, the `OracleRefCursor` is placed in an uninitialized state and no operation can be carried out from it. However, the uninitialized `OracleRefCursor` can be reassigned to another `REF` `CURSOR`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRefCursor Class](OracleRefCursorClass.md)

- [OracleRefCursor Members](RefCursorMembers.md)
