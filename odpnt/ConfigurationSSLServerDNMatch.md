This property enforces the database server distinguished name (DN) matches its service name. Default value is `false`.

### Declaration

    // C#
    public static bool SSLServerDNMatch { get; set; }

### Property Type

`System.Boolean`

Valid Values:

- `true` - to enforce a match. If the DN matches the service name, then the connection succeeds. If the DN does not match the service name, then the connection fails.

- `false` - to not enforce a match. If the DN does not match the service name, then the connection is successful, but an error is logged to the `sqlnet.log` file.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
