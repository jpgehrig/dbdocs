This property determines if the `Fill` method returns ODP.NET-specific values or .NET common language specification compliant values.

### Declaration

    // C#
    public Boolean ReturnProviderSpecificTypes {get; set;}


### Property Value

A value that indicates whether or not the `Fill` method returns ODP.NET-specific values.

Starting with ODP.NET 12.1.0.2, when set to `true` and `LegacyEntireLOBFetch = 0` (default), BLOB and CLOB column values are represented in the `DataTable` as `OracleBlob` and `OracleClob`, respectively.

A value of `false` indicates that the `Fill` method returns .NET common language specification compliant values. The default is `false`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)
