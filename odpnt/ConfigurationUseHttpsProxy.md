This property enables forward HTTP proxy tunneling client connections.

### Declaration

    // C#
    public static String UseHttpsProxy { get; set; }

### Property Type

`System.String`

### Values

Valid values are on, off, 0, or 1. Default is off.

### Usage Notes

If turned on, ODP.NET can tunnel secure connections over forward HTTP proxy using HTTP CONNECT method. This helps in accessing the public cloud database service as it eliminates the requirement to open an outbound port on a client side firewall.

This parameter is applicable with Oracle Connection Manager on the server side.

### Example

    //C#
    SQLNET.USE_HTTPS_PROXY=on

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
