This property specifies a logical name that identifies the DRCP connection pool that the ODP.NET connection will use.

### Declaration

    // C#
    public string DRCPConnectionClass {get; set;}

### Property Value

The string to be used that uniquely identifies the DRCP server side connection pool for the ODP.NET application to use.

### Exceptions

- `InvalidOperationException()` - if `CPVersion=1.0` and the `DRCPConnectionClass` is set to a non-null / non-empty string. Applies to unmanaged ODP.NET only.

- `InvalidOperationException()` -  if the `DRCPConnectionClass` is set to a non-null / non-empty string after opening a connection.

- `InvalidOperationException()` -  if DRCP is not enabled and the `DRCPConnectionClass` is set to a non-null / non-empty string.

### Remarks

If an application will share the a DRCP connection pool across multiple middle tier servers, then the application will have the option to set the `DRCPConnectionClass` property to a string value that uniquely identifies the server pool. If a DRCP connection is opened with this property populated, ODP.NET will direct DRCP to use a connection from that specific server pool.

The default value is null. The character limit is 1024 minus the number of characters in the user id.

If this property is used, it must be set prior to opening the connection.

Only supported for .NET Framework 4 and higher.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
