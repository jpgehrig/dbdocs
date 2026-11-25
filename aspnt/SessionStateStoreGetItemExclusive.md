This method locks a session item and returns it from the database.

### Declaration

    // C#
    public override SessionStateStoreData GetItemExclusive(HttpContext context,
       string id, out bool locked, out TimeSpan lockAge, out Object lockId,
       out SessionStateActions actions);

### Parameters

- `context`

  The `HttpContext` object for the current request.

- `id`

  The session ID for the current request.

- `locked`

  A Boolean value that is `true` if the session item was successfully locked in the database; otherwise, it is `false`.

- `lockAge`

  A `TimeSpan` object that indicates the amount of time the session item has been locked in the database.

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

This method returns a `SessionStateStoreData` object from the database and updates the expiration date of the session item. This method is called only if the attribute in the page is set to the default value of true. The session item is retrieved only if no other requests are currently using it. The session item in the database is locked for the duration of the request.

If no session data is found, the `locked` out parameter is set to `false` and a null reference is returned. The session state service then calls the `CreateNewStoreData` method to create a `newsession` item in the database.

If the session data is locked in the database, then the `locked` parameter is set to `true`, the `lockAge` parameter is set to the amount of time the session item has been locked in the database, the `lockId` parameter is set to the lock identifier and a null reference is returned. The session state service then keeps calling this method at half-second intervals. If the `lockAge` value exceeds the `ExecutionTimeout` value, then the session state service calls the `ReleaseItemExclusive` method to release the lock. It then calls the `GetItemExclusive` method again.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
