The `OracleSessionStateStore` class allows ASP.NET applications to store session information in an Oracle database.

### Class Inheritance

`System.Object`

`  System.Configuration.Provider.ProviderBase`

`    System.Web.SessionState.SessionStateStoreProviderBase`

`      Oracle.Web.SessionState`

### Declaration

    // C#
    public class OracleSessionStateStore : SessionStateStoreProviderBase

### Thread Safety

All public static methods are thread-safe, although instance members are not guaranteed to be thread-safe.

### Remarks

This class allows ASP.NET applications to store and manage session state information in an Oracle database.Note that the session information that this provider manages is application session information, not database session information.

Expired session data is periodically deleted from the database.

### Example

The following is a `web.config` example for an ASP.NET application that uses `OracleSessionStateStore` as the default provider with customized settings and an application-specific connection string:

    <?xml version="1.0"?>
    <configuration xmlns=
      "http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <connectionStrings>
        <add name="my_sessionstate_app_con_string" connectionString=
          "User Id=scott;Password=tiger;Data Source=Oracle"/>
      </connectionStrings>
      <system.web>
        <!-- Enable and customize OracleSessionStateProvider -->
        <sessionState mode="Custom" customProvider="MyOracleSessionStateStore">
          <providers>
            <add name="MyOracleSessionStateStore"
                 type="Oracle.Web.SessionState.OracleSessionStateStore,
                 Oracle.Web, Version=2.112.2.0, Culture=neutral,
                 PublicKeyToken=89b483f429c47342"
                 connectionStringName="my_sessionstate_app_con_string"/>
          </providers>
        </sessionState>
      </system.web>
    </configuration>

### Requirements

Namespace: `Oracle.Web.SessionState`

Assembly: `Oracle.Web.dll`

Oracle Providers for ASP.NET Version: Oracle Providers for ASP.NET 2.0 and Oracle Providers for ASP.NET 4

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)

- [OracleSessionStateStore Constructors](OracleSessionStateStoreConstructors.md)

- [OracleSessionStateStore Public Methods](SessionStateStorePublicMethods.md)

- [OracleSessionStateStore Public Properties](SessionStateStorePublicProperties.md)
