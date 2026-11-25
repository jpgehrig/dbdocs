This method returns a read-only session item from the database.

### Declaration

    // C#
    public override SessionStateStoreData GetItem(HttpContext context, string id,
       out bool locked, out TimeSpan lockAge, out Object lockId,
       out SessionStateActions actions);

### Parameters

- `context`

  The `HttpContext` object for the current request.

- `id`

  The session ID for the current request.

- `locked`

  A Boolean value that is `true` if the session item is locked in the database; otherwise, it is `false`.

- `lockAge`

  A a `TimeSpan` object that indicates the amount of time the session item has been locked in the database.

- `lockId`

  A lock identifier object.

- `actions`

  A `SessionStateActions` enumeration value that indicates whether the session is uninitialized and cookieless.

### Return Value

A `SessionStateStoreData` object that contains session information from the database.

### Exceptions

`ArgumentNullException` - The input parameter is null.

`OracleException` - An Oracle-related error has occurred.

`System.Configuration.Provider.ProviderException` - The session state information is invalid and might be corrupted.

### Remarks

This method returns a read-only `SessionStateStoreData` object from the database and updates the expiration date of the session item. This method is called by the session state service at the beginning of a request. It is called only if the `EnableSessionState` attribute in the page is set to `ReadOnly`.

If no session data is found, then the `locked` out parameter is set to `false` and a null reference is returned. The session state service then calls the `CreateNewStoreData` method to create a new session item in the database.

If the session data is locked in the database, then the `locked` out parameter is set to `true`, the `lockAge` parameter is set to the amount of time the session item has been locked in the database, the `lockId` parameter is set to the lock identifier and a null reference is returned. The session state service then keeps calling this method at half-second intervals. If the `lockAge` value exceeds the `HttpRuntimeSection.ExecutionTimeout` value, then the session state service calls the `ReleaseItemExclusive` method to release the lock. It then calls the `GetItem` method again.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
