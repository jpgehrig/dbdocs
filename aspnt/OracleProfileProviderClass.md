`OracleProfileProvider` enables ASP.NET developers to easily store Web site user profile information in an Oracle database.

### Class Inheritance

`System.Object`

`  System.Configuration.Provider.ProviderBase`

`    System.Configuration.SettingsProvider`

`      System.Web.Profile.ProfileProvider`

`       Oracle.Web.Profile.OracleProfileProvider`

### Declaration

    // C#
    public class OracleProfileProvider: ProfileProvider

### Thread Safety

All public static methods are thread-safe, although instance members are not guaranteed to be thread-safe.

### Remarks

This class allows ASP.NET applications to store and manage profile information in an Oracle database.

### Example

The following is a `web.config` file example for an ASP.NET application that uses `OracleProfileProvider` as the default provider. This configuration uses the connection string and default attribute values specified in the `machine.config` file. Profile properties are specified in the properties section. This example also enables anonymous identification and allows anonymous users to set properties.

    <?xml version="1.0"?>
    <configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <system.web>
        <anonymousIdentification enabled="true"/>
        <profile enabled="true" defaultProvider="OracleProfileProvider">
          <!-- Profile properties -->
          <properties>
            <add name="hire_date" allowAnonymous="true" type="DateTime"/>
            <add name="location" allowAnonymous="true"
                                defaultValue="Redwood Shores"/>
            <add name="experience" allowAnonymous="true" type="int"/>
          </properties>
        </profile>
      </system.web>
    </configuration>

The following is a `web.config` file example for an ASP.NET application that uses an `OracleProfileProvider` with customized settings and an application-specific connection string. Profile properties are specified in the properties section. This example also enables anonymous identification and allows anonymous users to set properties.

    <?xml version="1.0"?>
    <configuration xmlns=
      "http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <connectionStrings>
        <add name="my_profile_app_con_string" connectionString=
           "User Id=scott;Password=tiger;Data Source=Oracle"/>
      </connectionStrings>
      <system.web>
        <!-- Enable and customize OracleProfileProvider settings -->
        <anonymousIdentification enabled="true"/>
        <profile enabled="true" defaultProvider="MyOracleProfileProvider">
          <providers>
            <add name="MyOracleProfileProvider"
                 type="Oracle.Web.Profile.OracleProfileProvider,
                 Oracle.Web, Version=2.112.2.0, Culture=neutral,
                 PublicKeyToken=89b483f429c47342"
                 connectionStringName="my_profile_app_con_string"
                 applicationName="my_profile_app"/>
          </providers>
          <!-- Profile properties -->
          <properties>
            <add name="hire_date" allowAnonymous="true" type="DateTime"/>
            <add name="location" allowAnonymous="true"
                      defaultValue="Redwood Shores"/>
            <add name="experience" allowAnonymous="true" type="int"/>
          </properties>
        </profile>
      </system.web>
    </configuration>

Note that the `applicationName` attribute should be set to a unique value for each ASP.NET application.

### Requirements

Namespace: `Oracle.Web.Profile`

Assembly: `Oracle.Web.dll`

Oracle Providers for ASP.NET Version: Oracle Providers for ASP.NET 2.0 and Oracle Providers for ASP.NET 4

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)

- [OracleProfileProvider Constructors](ProfileProviderConstructors.md)

- [OracleProfileProvider Static Methods](ProfileProviderStaticMethods.md)

- [OracleProfileProvider Public Properties](ProfileProviderPublicProperties.md)

- [OracleProfileProvider Public Methods](ProfileProviderPublicMethods.md)
