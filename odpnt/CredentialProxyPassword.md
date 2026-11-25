This property returns the encrypted password of the proxy user.

### Declaration

    // C#
    SecureString ProxyUserPassword { get; }

### Property Value

The encrypted password of the proxy user.

### Remarks

`OracleCredential` does not support double quotes around a `SecureString` password. Double quotes can be used within a password, however.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCredential Class](OracleCredentialClass.md)

- [OracleCredential Members](CredentialMembers.md)
