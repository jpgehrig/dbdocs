This method initializes the `OracleProfileProvider` instance with the property values specified in the ASP.NET application configuration file (`web.config`).

### Declaration

    // C#
    public override void Initialize(string name, NameValueCollection config);

### Parameters

- `name`

  The name of the `OracleProfileProvider` instance to initialize.

- `config`

  A collection of the name/value pairs representing the provider-specific attributes specified in the configuration for the provider.

### Exceptions

`ArgumentNullException` - The `config` parameter is a null reference.

`HttpException` - The current trust level is less than Low.

`InvalidOperationException` - An attempt is made to call the `Initialize` method on a provider that has already been initialized.

`ArgumentNullException` - The `config` parameter is a null.

`System.Configuration.Provider.ProviderException` - One of the following conditions is true in the application configuration file:

- The `connectionStringName` attribute is empty or does not exist in the application configuration file.

- The value of the connection string for the `connectionStringName` attribute is empty or the specified `connectionStringName` value does not exist in the application configuration file.

- The `applicationName` attribute value exceeds 256 characters.

- The application configuration file for this `OracleProfileProvider` instance contains an unrecognized attribute.

### Remarks

The `Initialize` method sets options and property values for the provider instance, including provider-specific values and options specified in the machine configuration file (`machine.config`) or the ASP.NET application configuration file (`web.config`).

The `Initialize` method is not intended to be called directly by the application.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
