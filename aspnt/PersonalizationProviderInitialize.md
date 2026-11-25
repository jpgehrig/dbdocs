This method initializes the `OraclePersonalizationProvider` with the property values specified in the ASP.NET application configuration file (`web.config`).

### Declaration

    // C#
    public override void Initialize(string name, NameValueCollection config);

### Parameters

- `name`

  The friendly name of the provider.

- `config`

  A collection of the name/value pairs configuration options for this provider.

### Exceptions

`HttpException` - The current trust level is less than Low.

`InvalidOperationException` - An attempt is made to call the `Initialize` method on a provider that has already been initialized.

`ArgumentNullException` - The `config` parameter is a null reference.

`System.Configuration.Provider.ProviderException` - One of the following conditions exists in the application configuration file:

- The `connectionStringName` attribute is empty or does not exist in the application configuration file.

- The value of the connection string for the `connectionStringName` attribute value is empty, or the specified `connectionStringName` attribute does not exist in the application configuration file.

- The `applicationName` attribute value exceeds 256 characters.

- The application configuration file for this `OraclePersonalizationProvider` instance contains an unrecognized attribute.

### Remarks

The `Initialize` method is not intended to be called directly by the application.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OraclePersonalizationProvider Class](OraclePersonalizationProviderClass.md)

- [OraclePersonalizationProvider Members](OraclePersonalizationProviderMembers.md)
