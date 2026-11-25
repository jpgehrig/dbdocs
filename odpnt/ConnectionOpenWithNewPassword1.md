This method opens a new connection with the new password.

### Declaration

    // C#
    public void OpenWithNewPassword(string newPassword);

### Parameters

- `newPassword`

  A string that contains the new password.

### Remarks

This method uses the `ConnectionString` property settings to establish a new connection. The old password must be provided in the connection string as the `Password` attribute value.

This method can only be called on an `OracleConnection` in the closed state.

### Remarks (.NET Stored Procedure)

This method is not supported in a .NET stored procedure for context connection.

**Note:**

If connection pooling is enabled, then invoking the `OpenWithNewPassword` method also clears the connection pool. This closes all idle connections created with the old password.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- "[Password Expiration](featConnecting.md)"
