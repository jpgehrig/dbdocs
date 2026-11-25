The `OracleRoleProvider` class allows ASP.NET applications to store role and user information in an Oracle database.

### Class Inheritance

`System.Object`

`  System.Configuration.Provider.ProviderBase`

`    System.Web.Security.RoleProvider`

`      Oracle.Web.Security`

### Declaration

    // C#
    public class OracleRoleProvider : RoleProvider

### Thread Safety

All public static methods are thread-safe, although instance members are not guaranteed to be thread-safe.

### Remarks

This class allows ASP.NET applications to store and manage role information in an Oracle database.

Note that the role information that this provider manages are application roles and not database roles.

### Example

The following is a `web.config` example for an ASP.NET application that uses the `OracleRoleProvider` class as the default provider. This configuration uses the connection string and default attribute values specified in the `machine.config` file:

    <?xml version="1.0"?>
    <configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <system.web>
        <roleManager enabled="true" defaultProvider="OracleRoleProvider"/>
      </system.web>
    </configuration>

The following is a `web.config` example for an ASP.NET application that uses an `OracleRoleProvider` as the default provider with customized settings and an application-specific connection string.

    <?xml version="1.0"?>
    <configuration xmlns=
      "http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <connectionStrings>
        <add name="my_role_app_con_string" connectionString=
          "User Id=scott;Password=tiger;Data Source=Oracle"/>
      </connectionStrings>
      <system.web>
        <!-- Enable and customize OracleRoleProvider -->
        <roleManager enabled="true" defaultProvider="MyOracleRoleProvider">
          <providers>
            <add name="MyOracleRoleProvider"
                 type="Oracle.Web.Security.OracleRoleProvider,
                 Oracle.Web, Version=2.112.2.0, Culture=neutral,
                 PublicKeyToken=89b483f429c47342"
                 connectionStringName="my_role_app_con_string"
                 applicationName="my_role_app"/>
          </providers>
        </roleManager>
      </system.web>
    </configuration>

Note that the `applicationName` attribute should be set to a unique value for each ASP.NET application.

### Requirements

Namespace: `Oracle.Web.Security`

Assembly: `Oracle.Web.dll`

Oracle Providers for ASP.NET Version: Oracle Providers for ASP.NET 2.0 and Oracle Providers for ASP.NET 4

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)

- [OracleRoleProvider Constructors](RoleProviderConstructors.md)

- [OracleRoleProvider Static Methods](RoleProviderStaticMethods.md)

- [OracleRoleProvider Public Properties](RoleProviderPublicProperties.md)

- [OracleRoleProvider Public Methods](RoleProviderPublicMethods.md)
