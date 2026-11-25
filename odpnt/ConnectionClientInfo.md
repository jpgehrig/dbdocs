This property specifies the client information for the connection.

### Declaration

    // C#
    public string ClientInfo {set;}

### Property Value

The string to be used as the client information.

### Remarks

The default value is `null`.

Using the `ClientInfo` property allows the application to set the client information in the application context for a given `OracleConnection` object.

In unmanaged ODP.NET, the `ClientInfo` property is reset to null when the `Close` or `Dispose` method is called on the `OracleConnection` object. In managed ODP.NET, it is reset to null (assuming no new value is assigned) upon the next database round trip following a `Close` or `Dispose` method call on the `OracleConnection` object.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- "[Client Identifier and End-to-End Tracing](featConnecting.md)"

- [Oracle Database Security Guide](../dbseg/using-application-contexts-to-retrieve-user-information.md)
