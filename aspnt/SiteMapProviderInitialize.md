This method initializes the `OracleSiteMapProvider` instance with the property values specified in the ASP.NET application configuration file (`web.config`).

### Declaration

    // C#
    Public override void Initialize(string name, NameValueCollection config);

### Parameters

- `name`

  The name of the `OracleSiteMapProvider` instance to initialize.

- `config`

  A `Systems.Collections.Specialized.NameValueCollection` object that contains the names and values of configuration options for the site map provider.

### Exceptions

`ArgumentNullException` - The `config` parameter is null.

`InvalidOperationException` - A `SiteMapProvider` is already initialized.

`ProviderException` - One of the following exists:

- The `connectionStringName` attribute is null or empty in the configuration file.

- The connection string corresponding to the value of the `connectionStringName` attribute is null or empty.

- The configuration file contains an unrecognized attribute.

- An error occurred during initialization of the provider.

### Remarks

The `Initialize` method is not intended to be called directly by the application.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSiteMapProvider Class](OracleSiteMapProviderClass.md)

- [OracleSiteMapProvider Members](OracleSiteMapProviderMembers.md)
