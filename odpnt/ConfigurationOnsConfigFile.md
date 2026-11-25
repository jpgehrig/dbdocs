This property specifies the configuration file to define Oracle Notification Service (ONS) behavior. The file specified should contain the same local port and remote port values as specified in the ons.config file used by the local ONS daemon. This will enable the application to receive events from the local ONS daemon.

### Declaration

    // C#
    public static string OnsConfigFile { get; set; }

### Property Type

`System.String`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
