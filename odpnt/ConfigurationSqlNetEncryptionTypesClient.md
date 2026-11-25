This property specifies encryption algorithms that the client can use.

### Declaration

    // C#
    public static string SqlNetEncryptionTypesClient { get; set; }

### Property Type

`System.String`

Valid Values:

- `AES128`

- `AES192`

- `AES256`

- `3DES112`

- `3DES168`

### Example

    C#
    OracleConfiguration.SqlNetEncryptionTypesClient = "(aes128, aes192)";

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
