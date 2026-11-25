This method forcibly releases the lock on a session item in the database, if multiple attempts to retrieve the session item fail.

### Declaration

    // C#
    public override void ReleaseItemExclusive(HttpContext context, string id,
        Object lockId);

### Parameters

- `context`

  The `HttpContext` object for the current request.

- `id`

  The session ID for the current request.

- `lockId`

  The lock identifier for the current request.

### Exceptions

`ArgumentNullException` - The input parameter is null.

`OracleException` - An Oracle-related error has occurred.

### Remarks

This method is called by the session state service to release the lock on a session item in the database and update the expiration date. The `SessionStateModule` calls this method at the end of a request if the session values are unchanged or when the lock has exceeded the `HttpRuntimeSection.ExecutionTimeout` property value.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
