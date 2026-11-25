This method removes the specified session item from the database.

### Declaration

    // C#
    public override void RemoveItem(HttpContext context, string id, Object lockId,
       SessionStateStoreData item);

### Parameters

- `context`

  The `HttpContext` object for the current request.

- `id`

  The session ID for the current request.

- `lockId`

  The lock identifier for the current request.

- `item`

  The session item to remove from the database.

### Exceptions

`ArgumentNullException` - The input parameter is null.

`OracleException` - An Oracle-related error has occurred.

### Remarks

The session state service calls this method to remove the specified session item from the database. An application can call the `Session.Abandon` method to cancel a session.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
