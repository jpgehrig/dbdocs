This property lists the host names and port numbers of the primary and alternate LDAP directory servers.

### Declaration

    // C#
    public static string DirectoryServers { get; set; }

### Property Type

`System.String`

Use the following format to list the host names and port numbers:

    <HOST>:<PORT>[:<TLS/SSL PORT>]

### Example

    // C#
    OracleConfiguration.DirectoryServers="(ldap-server1:389, ldap-server2:400:636)";

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
