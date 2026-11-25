This property specifies the directory server type used, such as Oracle Internet Directory or Microsoft Active Directory.

### Declaration

    // C#
    public static string DirectoryType { get; set; }

### Property Type

`System.String`

### Values

- `oid` for Oracle Internet Directory

- `ad` for Microsoft Active Directory

### Example

    // C#
    OracleConfiguration.DefaultAdminContext=@"oid";

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
