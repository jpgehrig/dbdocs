The `OracleMembershipProvider` class enables ASP.NET developers to store Web site user account information in an Oracle database.

### Class Inheritance

`System.Object`

`  System.Configuration.Provider.ProviderBase`

`    System.Web.Security.MembershipProvider`

`      Oracle.Web.Security.OracleMembershipProvider`

### Declaration

    // C#
    public class OracleMembershipProvider: MembershipProvider

### Thread Safety

All public static methods are thread-safe, although instance members are not guaranteed to be thread-safe.

### Remarks

This class allows ASP.NET applications to store and manage user information in an Oracle database. Note that the term user in this chapter refers to an application or user, not a database user. Thus, the user information that this provider manages is application or user information, not database user information.

### Example

The following code example shows a `web.config` file for an ASP.NET application configured to use `OracleMembershipProvider` as the default provider. This configuration uses the connection string and default attribute values specified in the `machine.config` file.

    <?xml version="1.0"?>
    <configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <system.web>
        <membership defaultProvider="OracleMembershipProvider"/>
      </system.web>
    </configuration>

The following is a `web.config` example for an ASP.NET application that uses an `OracleMembershipProvider` with customized settings and an application-specific connection string:

    <?xml version="1.0"?>
    <configuration xmlns=
      "http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <connectionStrings>
        <add name="my_membership_app_con_string" connectionString=
          "User Id=scott;Password=tiger;Data Source=Oracle"/>
      </connectionStrings>
      <system.web>
        <!-- Enable and customize OracleMembershipProvider settings -->
        <membership defaultProvider="MyOracleMembershipProvider">
          <providers>
            <add name="MyOracleMembershipProvider"
                 type="Oracle.Web.Security.OracleMembershipProvider,
                 Oracle.Web, Version=2.112.2.0, Culture=neutral,
                 PublicKeyToken=89b483f429c47342"
                 connectionStringName="my_membership_app_con_string"
                 applicationName="my_membership_app"
                 enablePasswordRetrieval="false"
                 enablePasswordReset="true"
                 requiresQuestionAndAnswer="true"
                 requiresUniqueEmail="true"
                 passwordFormat="Hashed"
                 maxInvalidPasswordAttempts="4"
                 minRequiredPasswordLength="9"
                 passwordAttemptWindow="8"/>
          </providers>
        </membership>
      </system.web>
    </configuration>

Note that the `applicationName` attribute should be set to a unique value for each ASP.NET application.

### Requirements

Namespace: `Oracle.Web.Security`

Assembly: `Oracle.Web.dll`

Oracle Providers for ASP.NET Version: Oracle Providers for ASP.NET 2.0 and Oracle Providers for ASP.NET 4

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)

- [OracleMembershipProvider Constructors](MembershipProviderConstructors.md)

- [OracleMembershipProvider Static Methods](MembershipProviderStaticMethods.md)

- [OracleMembershipProvider Public Properties](MembershipProviderPublicProperties.md)

- [OracleMembershipProvider Public Methods](MembershipProviderPublicMethods.md)

- [OracleMembershipProvider Public Events](MembershipProviderPublicEvents.md)
