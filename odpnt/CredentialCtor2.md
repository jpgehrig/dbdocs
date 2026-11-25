This constructor creates an `OracleCredential` object with the user id, the secured password, and the DBA privilege request.

### Declaration

    // C#
    public OracleCredential(string userId, SecureString password, OracleDBAPrivilege dbaprivilege)

### Exceptions

- `ArgumentNullException` is raised if any parameters are passed as null.

- `ArgumentException` is raised if “`/`” is passed for `userId` argument.

- `ArgumentException` is raised if the `SecureString` containing the password is not read-only.

- `InvalidOperationException` is raised when `OracleCredential` object is used with any of `user id`, `password`, `proxy user id`, `proxy password` and/or `dba privilege`connection string attribute(s) present in the connection string.

### Remarks

With this constructor, the specified `dbaprivilege` is for the DBA privilege when requesting for a connection.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)

- [OracleDBAPrivilege Enumeration](OracleDBAPrivilegeEnumeration.md)
