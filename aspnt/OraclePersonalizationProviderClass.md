The `OraclePersonalizationProvider` class enables ASP.NET developers to store Web parts personalization information in an Oracle database.

### Class Inheritance

`System.Object`

`  System.Configuration.Provider.ProviderBase`

`    System.Web.UI.WebControls.WebParts.PersonalizationProvider`

`      Oracle.Web.Personalization.OraclePersonalizationProvider`

### Declaration

    // C#
    public class OraclePersonalizationProvider: PersonalizationProvider

### Thread Safety

All public static methods are thread-safe, although instance members are not guaranteed to be thread-safe.

### Remarks

This class allows ASP.NET applications to store and manage personalization information in an Oracle database.

### Example

The following is a `web.config` example for an ASP.NET application that uses an `OraclePersonalizationProvider` as the default provider. This configuration uses the connection string and default attribute values specified in the `machine.config` file.

    <?xml version="1.0"?>
    <configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <system.web>
        <webParts>
          <personalization defaultProvider="OraclePersonalizationProvider"/>
        </webParts>
      </system.web>
    </configuration>

The following is a `web.config` example for an ASP.NET application that uses an `OraclePersonalizationProvider` as the default provider, with customized settings and an application-specific connection string:

    <?xml version="1.0"?>
    <configuration xmlns=
      "http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <connectionStrings>
        <add name="my_personalization_app_con_string" connectionString=
          "User Id=scott;Password=tiger;Data Source=Oracle"/>
      </connectionStrings>
      <system.web>
        <webParts>
          <!-- Enable and customize OraclePersonalizationProvider -->
          <personalization defaultProvider="CustomOraclePersonalizationProvider">
            <providers>
              <add name="CustomOraclePersonalizationProvider"
                   type="Oracle.Web.Personalization.OraclePersonalizationProvider,
                         Oracle.Web, Version=2.112.2.0, Culture=neutral,
                         PublicKeyToken=89b483f429c47342"
                   connectionStringName="my_personalization_app_con_string"
                   applicationName="my_personalization_app"/>
            </providers>
          </personalization>
        </webParts>
      </system.web>
    </configuration>

Note that the `applicationName` attribute should be set to a unique value for each ASP.NET application.

### Requirements

Namespace: `Oracle.Web.Personalization`

Assembly: `Oracle.Web.dll`

Oracle Providers for ASP.NET Version: Oracle Providers for ASP.NET 2.0 and Oracle Providers for ASP.NET 4

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OraclePersonalizationProvider Members](OraclePersonalizationProviderMembers.md)

- [OraclePersonalizationProvider Constructors](PersonalizationProviderConstructors.md)

- [OraclePersonalizationProvider Static Methods](PersonalizationProviderStaticMethods.md)

- [OraclePersonalizationProvider Public Properties](PersonalizationProviderPublicProperties.md)

- [OraclePersonalizationProvider Public Methods](PersonalizationProviderPublicMethods.md)
