This method initializes the provider with the property values specified in the ASP.NET application configuration file (`web.config`).

### Declaration

    // C#
    public override void Initialize(string name, NameValueCollection config);

### Parameters

- `name`

  The name of the provider instance to initialize.

- `config`

  A `Systems.Collections.Specialized.NameValueCollection` object that contains the names and values of configuration options for the provider.

### Exceptions

`ArgumentNullException` - The `config` parameter is null.

`System.Configuration.Provider.ProviderException` - The `connectionStringName` attribute is empty or does not exist in the configuration file, or an invalid attribute is found in the configuration file.

### Remarks

The `Initialize` method is not intended to be called directly by the application.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
