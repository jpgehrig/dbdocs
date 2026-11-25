This constructor creates an instance of the `OracleRef` class with a connection and a HEX string that represents an `REF` instance in the database.

### Declaration

    // C#
    public OracleRef(OracleConnection con, string hexStr);

### Parameters

- `con`

  An `OracleConnection` instance.

- `hexStr`

  A HEX string that represents an `REF` instance in the database.

### Exceptions

`ArgumentException` - The HEX string does not represent a valid `REF` in the database.

`ArgumentNullException` - The connection or HEX string is null.

`InvalidOperationException` - The `OracleConnection` object is not open.

### Remarks

When an `OracleRef` instance is created, it is referenced to a specific table in the database.

The connection must be opened explicitly by the application. `OracleRef` does not open the connection implicitly.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)

- [OracleRef Members](OracleRefMembers.md)
