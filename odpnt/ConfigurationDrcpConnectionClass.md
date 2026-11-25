This property specifies a logical name that identifies the DRCP connection pool that the ODP.NET connection will use. It will be used as a default if the `DRCPConnectionClass` property on the `OracleConnection` object is not set. It will be ignored for non-DRCP connections. Default value is `null`.

### Declaration

    // C#
    public static string DrcpConnectionClass { get; set; }

### Property Type

`System.String`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
