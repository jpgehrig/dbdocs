This method updates the session time information in the database with the specified session item, and releases the lock.

### Declaration

    // C#
    public override void SetAndReleaseItemExclusive(HttpContext context, string id,
       SessionStateStoreDataItem item, Object lockId, bool newItem);

### Parameters

- `context`

  The `HttpContext` object for the current request.

- `id`

  The session ID for the current request.

- `item`

  The session item containing new values to update the session item in the database with.

- `LockId`

  The lock identifier for the current request.

- `newItem`

  A Boolean value that indicates whether the session item is new in the database. A `false` value indicates an existing item.

### Exceptions

`ArgumentNullException` - The input parameter is null.

`OracleException` - An Oracle-related error has occurred.

### Remarks

If the session items have been modified, the session state service calls this method at the end of a request, to either create a new item or update an existing session item in the database with the provided session values. This method also updates the expiration time for the session item and releases the lock on the session data.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
