This method allows the `OracleSessionStateStore` object to perform any cleanup that may be required for the current request.

### Declaration

    // C#
    public override void EndRequest(HttpContext context);

### Parameters

- `context`

  The `HttpContext` object for the current request.

### Remarks

This method is called by the `SessionStateModule` object at the end of a request.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
