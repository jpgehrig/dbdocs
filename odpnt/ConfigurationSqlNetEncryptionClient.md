This property specifies the encryption client behavior.

### Declaration

    // C#
    public static string SqlNetEncryptionClient { get; set; }

### Property Type

`System.String`

Default value is `accepted`.

Valid Values:

- `accepted` - to enable the security service if required or requested by the database.

- `rejected` - to disable the security service, even if required by the database.

- `requested` - to enable the security service if the database allows it.

- `required` - to enable the security service and disallow the connection if the database is not enabled for the security service.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
