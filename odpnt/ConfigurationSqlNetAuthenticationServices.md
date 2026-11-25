This property enables one or more authentication services, such as TCP/IP with SSL.

### Declaration

    // C#
    public static string SqlNetAuthenticationServices { get; set; }

### Property Type

`System.String`

Valid Values: `NTS`, `TCPS`, or `NONE`.

### Example

    //C#
    OracleConfiguration.SqlNetAuthenticationServices = "(nts, tcps)";

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
