This method creates a new `SessionStateStoreData` object for the current request.

### Declaration

    // C#
    public override SessionStateStoreData CreateNewStoreData(HttpContext context,
       int timeout);

### Parameters

- `context`

  The `HttpContext` object for the current request.

- `timeout`

  The timeout value for the `SessionStateStoreData` object that is created.

### Return Value

A new `SessionStateStoreData` object for the current request.

### Remarks

This method creates a new `SessionStateStoreData` object for the current request based on the `HttpContext` and timeout values. The `SessionStateModule` calls this method at the beginning of a request for an ASP.NET page, if the request does not contain a session ID or if the request contains a session ID for a session that is not found in the database. This method creates a new `SessionStateStoreData` object with an empty `ISessionStateItemCollection` object, an `HttpStaticObjectsCollection` collection, and the specified timeout value.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
