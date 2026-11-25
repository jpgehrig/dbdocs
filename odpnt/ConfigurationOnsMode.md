This property specifies the ONS daemon mode as either "local" or "remote".

For local configuration, configure and make available ONS on the node where ODP.NET is running so that ODP.NET can receive events directly from the local ONS daemon.

Remote configuration is used when the application directly receives ONS events from the ONS daemons running on remote machines. One of the advantages of this configuration is that no ONS daemon is needed on the client end and; therefore, there is no need to manage this process.

### Declaration

    // C#
    public static OnsConfigMode OnsMode { get; set; }

### Property Type

`System.String`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
