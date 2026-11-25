This property specifies the crypto-checksum algorithms the client can use.

### Declaration

    // C#
    public static string SqlNetCryptoChecksumTypesClient { get; set; }

### Property Type

`System.String`

Valid Values:

- `SHA1`

- `SHA256`

- `SHA384`

- `SHA512`

### Example

    C#
    OracleConfiguration.SqlNetCryptoChecksumTypesClient = "(SHA1, SHA256, SHA512)";

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
