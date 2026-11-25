This method opens a new connection with the new password.

### Declaration

    // C#
    public void OpenWithNewPassword(SecureString newSecurePassword)

### Parameters

- `newSecurePassword`

  The `SecureString` object that contains the new password for a user id.

### Remarks

Use this method to change the password for a user id. This method can only be used if an `OracleCredential` instance was passed using the `OracleConnection` constructor or through the `OracleConnection Credential` property.

This method will also update the password in the `OracleCredential` instance that was passed using the `OracleConnection` constructor or through the `OracleConnection Credential` property.

`OracleCredential` does not support double quotes around a `SecureString` password. Double quotes can be used within a password, however.

### Exceptions

`ArgumentNullException` is raised if `newSecurePassword` is NULL or is not read only.

`InvalidOperationException` is raised if `OracleCredential` is not already set on the `OracleConnection` either through the `OracleConnection` constructor or through the `Credential` property of the `OracleConnection`.

`InvalidOperationException` is raised if the `OracleConnection` is already in the open state.

`InvalidOperationException` is raised of the connection string is NULL or of length 0.

`InvalidOperationException` is raised if the user id, proxy user id, password, proxy password, DBA privilege is set using the connection string.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- "[Password Expiration](featConnecting.md)"
