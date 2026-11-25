The `OracleWebEventProvider` class allows ASP.NET applications to store Web events in an Oracle database.

### Class Inheritance

`System.Object`

`  System.Configuration.Provider.ProviderBase`

`    System.Web.Management.WebEventProvider`

`      System.Web.Management.BufferedWebEventProvider`

`        Oracle.Web.Management.OracleWebEventProvider`

### Declaration

    // C#
    public class OracleWebEventProvider: BufferedWebEventProvider

### Thread Safety

All public static methods are thread-safe, although instance members are not guaranteed to be thread-safe.

### Remarks

This class allows ASP.NET applications to store Web event information in an Oracle database.

### Example

The following is a `web.config` example for an ASP.NET application that uses the `OracleWebEventProvider` class as the default provider. This configuration uses the connection string and default attribute values specified in the `machine.config` file.

Applications must provide any required configuration entries for event mapping, buffer modes, and rules in the `web.config` file, because the `machine.config` file does not provide these configuration entries. The following `web.config` file provides an example:

    <?xml version="1.0"?>
    <configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <system.web>
        <healthmonitoring enabled="true"/>
          <bufferModes>
            <add name="Notification"
                 maxBufferSize="1000"
                 maxFlushSize="200"
                 urgentFlushThreshold="500"
                 regularFlushInterval="00:00:6"
                 urgentFlushInterval="00:00:03"
                 maxBufferThreads="1"/>
          </bufferModes>
          <eventMappings>
            <add name="CustomEvent"
                 type="CustomEventSource.CustomEvent, CustomEventSource"/>
          </eventMappings>
          <rules>
            <add name="CustomRule"
                 eventName="CustomEvent"
                 provider="OracleWebEventProvider"
                 minInterval="00:00:00"/>
          </rules>
        </healthMonitoring>
      </system.web>
    </configuration>

The following is a `web.config` example for an ASP.NET application that uses an `OracleWebEventProvider` class as the default provider, using customized settings for the connection string name and application name, and an application-specific connection string, along with other configurations as described in the previous example:

    <?xml version="1.0"?>
    <configuration xmlns=
      "http://schemas.microsoft.com/.NetConfiguration/v2.0">
      <connectionStrings>
        <add name="my_webevent_app_con_string" connectionString=
          "User Id=scott;Password=tiger;Data Source=Oracle"/>
      </connectionStrings>
      <system.web>
        <!-- Enable and customize OracleWebEventProvider -->
        <healthMonitoring enabled="true">
          <providers>
            <add name="CustomOracleWebEventProvider"
                 type="Oracle.Web.Management.OracleWebEventProvider,
                       Oracle.Web, Version=2.112.2.0, Culture=neutral,
                       PublicKeyToken=89b483f429c47342"
                 connectionStringName="my_webevent_app_con_string"
                 bufferMode="CustomBufferMode">
          </providers>
          <bufferModes>
            <add name="CustomBufferMode"
                 maxBufferSize="1000"
                 maxFlushSize="200"
                 urgentFlushThreshold="500"
                 regularFlushInterval="00:00:06"
                 urgentFlushInterval="00:00:03"
                 maxBufferThreads="1"/>
          </bufferModes>
          <eventMappings>
            <add name="CustomEvent"
                 type="CustomEventSource.CustomEvent, CustomEventSource"/>
          </eventMappings>
          <rules>
            <add name="CustomRule"
                 eventName="CustomEvent"
                 provider="CustomOracleWebEventProvider"
                 minInterval="00:00:00"/>
          </rules>
        </healthMonitoring>
      </system.web>
    </configuration>

Note that the `applicationName` attribute should be set to a unique value for each ASP.NET application.

### Requirements

Namespace: `Oracle.Web.Management`

Assembly: `Oracle.Web.dll`

Oracle Providers for ASP.NET Version: Oracle Providers for ASP.NET 2.0 and Oracle Providers for ASP.NET 4

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleWebEventProvider Members](OracleWebEventProviderMembers.md)

- [OracleWebEventProvider Constructors](WebEventProviderConstructors.md)

- [OracleWebEventProvider Static Methods](WebEventProviderStaticMethods.md)

- [OracleWebEventProvider Public Properties](WebEventProviderPublicProperties.md)

- [OracleWebEventProvider Public Methods](WebEventProviderPublicMethods.md)
