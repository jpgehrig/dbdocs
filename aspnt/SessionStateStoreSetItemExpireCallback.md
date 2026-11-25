This method returns a `false` value to indicate that callbacks for expired sessions are not supported.

### Declaration

    // C#
    public override bool SetItemExpireCallback(SessionStateItemExpireCallback
      expireCallback);

### Parameters

- `expireCallback`

  The delegate for the `Session_OnEnd` event defined in the `Global.asax` file.

### Return Value

A `false` value.

### Remarks

This method always returns a `false` value to indicate that callbacks for expired sessions are not supported.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
