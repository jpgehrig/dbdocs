This method performs any per-request initializations that the `OracleSessionStateStore` provider requires.

### Declaration

    // C#
    public override void InitializeRequest(HttpContext context);

### Parameters

- `context`

  The `HttpContext` object for the current request.

### Exceptions

`ArgumentNullException` - The `context` parameter is null.

### Remarks

This method is called by the session state service before calling any other methods.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
