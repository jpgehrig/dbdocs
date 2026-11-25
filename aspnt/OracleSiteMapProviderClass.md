This class allows ASP.NET applications to retrieve site map information from an Oracle database.

### Class Inheritance

`System.Object`

`  System.Configuration.Provider.ProviderBase`

`    System.Web.SiteMapProvider`

`      System.Web.StaticSiteMapProvider`

`        Oracle.Web.SiteMap.OracleSiteMapProvider`

### Declaration

    // C#
    Public class OracleSiteMapProvider: StaticSiteMapProvider, IDisposable

### Thread Safety

All public static methods are thread-safe, although instance members are not guaranteed to be thread-safe.

### Remarks

This class allows ASP.NET applications to read and load site map information from an Oracle database.

### Examples

The following is a `web.config` example for an ASP.NET application that uses `OracleSiteMapProvider` as the default provider. This configuration uses the connection string and default attribute values specified in the `machine.config` file.

    <?xml version="1.0"?>
    <configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <system.web>
        <siteMap defaultProvider="OracleSiteMapProvider"/>
      </system.web>
    </configuration>

The following is a `web.config` example for an ASP.NET application that uses `OracleSiteMapProvider` as the default provider, with customized settings and an application-specific connection string:

    <?xml version="1.0"?>
    <configuration xmlns=
      "http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <connectionStrings>
        <add name="my_sitemap_app_con_string" connectionString=
          "User Id=scott;Password=tiger;Data Source=Oracle"/>
      </connectionStrings>
      <system.web>
        <!-- Enable and customize OracleSiteMapProvider -->
        <siteMap defaultProvider="CustomOracleSiteMapProvider">
          <providers>
            <add name="CustomOracleSiteMapProvider"
                 type="Oracle.Web.SiteMap.OracleSiteMapProvider,
                       Oracle.Web, Version=2.112.2.0, Culture=neutral,
                       PublicKeyToken=89b483f429c47342"
                 connectionStringName="my_sitemap_app_con_string"
                 applicationName="my_sitemap_app"
                 securityTrimmingEnabled="false"/>
          </providers>
        </siteMap>
      </system.web>
    </configuration>

Note that the `applicationName` attribute should be set to a unique value for each ASP.NET application.

### Requirements

Namespace: `Oracle.Web.SiteMap`

Assembly: `Oracle.Web.dll`

Oracle Providers for ASP.NET Version: Oracle Providers for ASP.NET 2.0 and Oracle Providers for ASP.NET 4

`OracleSiteMapProvider` requires the Change Notification privilege with Oracle Database 10g release 2 (10.2)and later.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSiteMapProvider Members](OracleSiteMapProviderMembers.md)

- [OracleSiteMapProvider Constructors](SiteMapProviderConstructors.md)

- [OracleSiteMapProvider Public Properties](SiteMapProviderPublicProperties.md)

- [OracleSiteMapProvider Public Methods](SiteMapProviderPublicMethods.md)
