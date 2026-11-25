This constructor creates an `OracleCredential` object with the user id and the secured password for the end user, as well as the user id and the secured password for the proxy user.

### Declaration

    // C#
    public OracleCredential(string userId, SecureString password, string proxyUserId, SecureString proxyPassword)

### Exceptions

- `ArgumentNullException` is raised if any parameters are passed as null.

- `ArgumentException` is raised if “`/`” is passed for `userId` argument.

- `ArgumentException` is raised if the `SecureString` containing the password is not read-only.

- `InvalidOperationException` is raised when `OracleCredential` object is used with any of `user id`, `password`, `proxy user id`, `proxy password` and/or `dba privilege`connection string attribute(s) present in the connection string.

### Remarks

With this constructor, `OracleDBAPrivilege.None` is for the DBA privilege when requesting for a connection.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCredential Class](OracleCredentialClass.md)

- [OracleCredential Members](CredentialMembers.md)
