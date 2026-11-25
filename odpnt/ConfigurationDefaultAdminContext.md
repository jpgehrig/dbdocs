This property specifies the default directory entry that contains a LDAP Oracle Context from which connect identifiers can be created, modified, or looked up.

### Declaration

    // C#
    public static string DefaultAdminContext { get; set; }

### Property Type

`System.String`

### Values

Valid distinguished name

### Example

    // C#
    OracleConfiguration.DefaultAdminContext=@"o=OracleSoftware,c=US";

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
