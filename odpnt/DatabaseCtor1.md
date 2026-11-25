The `OracleDatabase` constructor instantiates a new instance of the `OracleDatabase` class using the supplied connection string.

### Declaration

    // C#
    public OracleDatabase(string connetionString);

### Parameters

- `connectionString`

  The connection information used to connect to the Oracle Database instance.

### Remarks

The `connectionString` follows the same format used by the `OracleConnection` object. However, the `OracleDatabase` constructor accepts only the `user id`, `password`, `data source`, and `dba privilege` connection string attributes. All other attribute values are ignored. The supplied `connectionString` must contain the `dba privilege` connection string attribute that is set to either `SYSDBA` or `SYSOPER`.

The `OracleDatabase` object creates a connection upon construction and remains connected throughout its lifetime. The connection is destroyed when the OracleDatabase object is disposed. This connection is not pooled to be used by another `OracleDatabase` object.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDatabase Class](OracleDatabaseClass.md)

- [OracleDatabase Members](DatabaseMembers.md)
