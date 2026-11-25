This method initializes the `OracleRoleProvider` instance with the property values specified in the ASP.NET application configuration file (`web.config`).

### Declaration

    // C#
    public override void Initialize(string name, NameValueCollection config);

### Parameters

- `name`

  The name of the `OracleRoleProvider` instance to initialize.

- `config`

  A `Systems.Collections.Specialized.NameValueCollection` object that contains the names and values of configuration options for the role provider.

### Exceptions

`System.Web.HttpException` - ASP.NET is not running at medium trust or higher.

`ArgumentNullException` - The `config` parameter is null.

`System.Configuration.Provider.ProviderException` - The `connectionStringName` attribute is empty or does not exist in the configuration file, the `applicationName` attribute exceeds 256 characters, or the configuration file contains an invalid attribute.

### Remarks

The `Initialize` method is not intended to be called directly by the application.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
