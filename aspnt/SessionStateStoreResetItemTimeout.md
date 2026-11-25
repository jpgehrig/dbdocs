This method resets the expiration date and timeout for a session item in the database.

### Declaration

    // C#
    public override void ResetItemTimeout(HttpContext context, string id);

### Parameters

- `context`

  The `HttpContext` object for the current request.

- `id`

  The session ID for the current request.

### Exceptions

`ArgumentNullException` - The input parameter is null.

`OracleException` - An Oracle-related error has occurred.

### Remarks

The session state service calls this method to reset the expiration date and timeout for a session item in the database, to the current date and time.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
