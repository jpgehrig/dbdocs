This method adds a new session state item to the database.

### Declaration

    // C#
    public override void CreateUninitializedItem(HttpContext context, string id,
      int timeout);

### Parameters

- `context`

  The `HttpContext` object for the current request.

- `id`

  The session ID for the current request.

- `timeout`

  The timeout value for the current request.

### Exceptions

`ArgumentNullException` - The input parameter is null.

`OracleException` - An Oracle-related error has occurred.

### Remarks

This method adds an uninitialized session state entry into the database and is called when the `cookieless` and `regenerateExpiredId` attributes are both set to `true`.

After a new session ID is created, this method is called to store an uninitialized entry with this new session ID in the database. The browser is redirected to the URL containing the new session ID. The new session ID exists in the database, so there is no conflict with an expired session ID.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
