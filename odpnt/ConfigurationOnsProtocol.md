This property defines whether the ONS connection uses TCP/IP or TCP/IP with SSL/TLS.

### Declaration

    // C#
    public static string OnsProtocol { get; set; }

### Property Type

`System.String`

### Usage Notes

Valid values are TCP or TCPS. Default value is TCP.

### Example

    OracleConfiguration.OnsProtocol=TCPS

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
