This method initializes the `OracleWebEventProvider` instance with the property values specified in the ASP.NET application configuration file (`web.config`).

### Declaration

    // C#
    public override void Initialize(string name, NameValueCollection config);

### Parameters

- `name`

  The name of the `OracleWebEventProvider` instance to initialize.

- `config`

  A `Systems.Collections.Specialized.NameValueCollection` object that contains the names and values of configuration options for the `OracleWebEventProvider`.

### Exceptions

`InvalidOperationException` - If the `OracleWebEventProvider` instance is already initialized.

`ProviderException` - One of the following conditions exists:

- The `connectionStringName` attribute in the configuration file is null or empty.

- The connection string corresponding to value of the `connectionStringName` attribute is null or empty.

- An unrecognized attribute is found in the configuration file.

- Another error occurs during initialization of the provider.

### Remarks

The `Initialize` method is not intended to be called directly by the application.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleWebEventProvider Class](OracleWebEventProviderClass.md)

- [OracleWebEventProvider Members](OracleWebEventProviderMembers.md)
