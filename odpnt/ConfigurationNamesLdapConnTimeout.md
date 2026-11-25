This property specifies the non-blocking connection timeout to the LDAP server.

### Declaration

    // C#
    public static Int32 NamesLdapConnTimeout { get; set; }

### Property Type

`System.Int32`

This property sets the time to wait (in seconds) for a LDAP server connection before a time out error can occur.

The minimum value is -1, which indicates no connection timeout. The default value is 15 seconds.

### Example

    // C#
    OracleConfiguration.NamesLdapConnTimeout = -1;

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
