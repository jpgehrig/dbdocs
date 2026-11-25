The following sections explain how to configure ODP.NET, Unmanaged Driver.

ODP.NET can be configured using an XML file named `web.config`, `app.config`, or `machine.config`. These config files contain sections specific to ODP.NET configuration.

For unmanaged ODP.NET, developers use either the traditional `<oracle.dataaccess.client>` section or the newer `<oracle.unmanageddataaccess.client>` section. Oracle recommends applications use `<oracle.unmanageddataaccess.client>` when possible. For managed ODP.NET, developers use `<oracle.manageddataaccess.client>`.

`<oracle.unmanageddataaccess.client>` is a superset of `<oracle.manageddataaccess.client>` as unmanaged ODP.NET supports some features not available in the managed driver. For features both providers have in common, they share the same structure, properties, and nearly all values. Programmers will find using either provider interchangeably or migrating between unmanaged and managed ODP.NET is easier with the shared format.

This documentation section covers unmanaged ODP.NET configuration settings in the Windows registry, `<oracle.dataaccess.client>`, or unique `<oracle.unmanageddataaccess.client>` settings. For shared settings with `<oracle.manageddataaccess.client>`.

**See Also:**

[Oracle Data Provider for .NET, Managed Driver Configuration](InstallManagedConfig.md)

### Supported Configuration Settings

ODP.NET, Unmanaged Driver supports the configuration of an attribute as follows:

- In the Windows registry.

- In an XML file.

- Through a different mechanism such as a connection string or programmatically through an ODP.NET class, if applicable.

Table 2-3 describes each configurable attribute that is supported by ODP.NET. In the table, the term Configuration Support is followed by the types of configuration support (Windows registry, XML file, and so on) that are available for that attribute.

The table describes valid values as well as the default for each attribute.

**Note:**

The default values shown are the values used for an attribute if the registry key does not exist or if it is not configured anywhere.

Table 2-3 Configuration Attributes

| Attribute/Setting Name             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CheckConStatus`                   | Specifies whether the status of the connection is checked or not before putting the connection back into the connection pool. This registry entry is not created by the installation of ODP.NET. However, the default value `1` is used.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>`1`: Check the status of the connection.<br>`0`: Do not check the status of the connection.<br>Default: `1`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `DbNotificationPort`               | Specifies the port number which ODP.NET listens to, for all notifications sent by the database for change notification, HA, or RLB features. ODP.NET does not throw any errors if an invalid or used port number is specified. The port can also be set to override the Windows registry and XML configuration file by setting the `OracleDependency.Port` static field.<br>Configuration Support:<br>XML file, and ODP.NET class<br>Valid Values:<br>`-1`: Open a random unused port to listen to.<br>`n` `>` `=` `0`: Listen on port `n`.<br>Default: `-1`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `DemandOraclePermission`           | Specifies whether ODP.NET demands `OraclePermission` from the .NET application that is trying to access the database using ODP.NET.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>0: Disables demands for `OraclePermission`.<br>1: Enables demands for `OraclePermission`<br>Default: 0                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `DllPath`                          | Specifies the location where dependent unmanaged Oracle Client binaries load from.<br>Configuration Support: Windows Registry and XML file<br>Valid Values:<br>The path where dependent unmanaged Oracle Client binaries reside.<br>Default: `ORACLE_BASE\\ORACLE_HOME``\bin`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `DynamicEnlistment`                | Due to a behavior change with the ODAC 12c Release 3 version of ODP.NET connection string attribute `enlist=dynamic`, `DynamicEnlistment` has no operation now.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `FetchSize`                        | Specifies the total memory size, in bytes, that ODP.NET allocates to cache the data fetched from a database round-trip. This value can be set on the `OracleCommand` and the `OracleDataReader` `FetchSize` property as well.<br>Configuration Support:<br>Windows Registry, XML file, and ODP.NET class<br>Valid Values:<br>`0 <=` `n` `<= int.MaxValue`: `n` is the size of the cache in bytes.<br>Default: `131072`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `LegacyEntireLobFetch`             | Returns either `OracleBlob` and `OracleClob` types or `OracleBinary` and `OracleString` types from Oracle Database `BLOB` and `CLOB` columns. This setting only applies when `InitialLobFetchSize` is set to `-1`.<br>Valid Values:<br>`0`: Returns `OracleBlob` and `OracleClob`<br>`1`: Returns `OracleBinary` and `OracleString`<br>Default: `0`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `LegacyTransactionBindingBehavior` | Specifies when a database connection detaches from a `System.Transactions` transaction. By default, connections detach from a transaction only when explicitly unbound as is the case when the connection closes or implicitly unbound when the transaction is disposed. Alternatively, this attribute can be set so that the connection detaches whenever the transaction ends (commits, aborts, or times out), the connection closes, or the transaction is disposed.<br>In ODP.NET 11.2.0.3.20 and earlier releases, the latter was the default behavior. Oracle recommends using the current default behavior.<br>In the earlier default behavior, when the timeout elapses before the transaction completes, the connection unbinds itself from the transaction and all subsequent executions on this connection execute in `AutoCommit` mode. Any operations prior to the timeout roll back, but operations performed after the timeout commit.<br>In the current default setting, users receive an exception when the transaction times out and additional operations execute on the connection.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>`0:` Connections detach from transaction when the connection closes or the transaction is disposed.<br>`1`: Connections detach from transaction when the connection closes, the transaction is disposed, or the transaction completes (commits, rolls back, times out).<br>Default: `0` |
| `MaxStatementCacheSize`            | Specifies the maximum number of statements that can be cached when self-tuning is enabled.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>0 to `System.Int32.MaxValue`.<br>Default: `OPEN_CURSORS` setting value of the database                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `MetaDataXml`                      | Specifies the name of the XML file that customizes the queries to obtain the metadata the ADO.NET 2.0 `GetSchema` method returns. `MetaDataXml` can only be set in a configuration file.<br>Configuration Support:<br>XML file only<br>Valid Values:<br>A complete file name for the XML file.<br>Default: none                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `PerformanceCounters`              | Enables or disables publishing performance counters for connection pooling. Multiple performance counters can be obtained by adding the valid values.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>`0`: Not Enabled<br>`1`: Number of sessions being established with Oracle Database every second.<br>`2`: Number of sessions being severed from Oracle Database every second.<br>`4`: Number of active connections originating from connection pools every second.<br>`8`: Number of active connections going back to the connection pool every second.<br>`16`: Total number of active connections.<br>`32`: Number of inactive connection pools.<br>`64`: Total number of connections in use.<br>`128`: Total number of connections available for use in all the connection pools.<br>`256`: Total number of pooled active and free connections.<br>`512`: Number of non-pooled active connections<br>`1024`: Number of connections which were garbage-collected implicitly.<br>`2048`: Number of connections that will be soon available in the pool. User has closed these connections, but they are currently awaiting actions, such transaction completion, before they can be placed back into the pool as free connections.<br>`4095`: All the above<br>Default: `0`                                                                                                                                                               |
| `PromotableTransaction`            | Specifies the type of transaction to use when the first connection participates in the `TransactionScope` object.<br>Configuration Support:<br>Windows Registry, XML file, and promotable transaction connection string attribute<br>Valid Values:<br>`local`: The first connection opened in the `TransactionScope` object uses a local transaction.<br>`promotable`: The first connection and all subsequent connections opened in the same `TransactionScope` object enlist in the same distributed transaction.<br>Default: `promotable`<br>This property has been deprecated in 12.2.0.1. It will be desupported in a future release.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `SelfTuning`                       | Specifies whether self-tuning is enabled for an ODP.NET application.<br>Configuration Support:<br>Windows Registry, XML file, and `Self Tuning` connection string attribute<br>Valid Values:<br>0: Self Tuning is disabled. Used in the registry or XML file.<br>`false`: Self Tuning is disabled. Used for the `Self Tuning` connection string attribute.<br>1: Self Tuning is enabled. Used in the registry or XML file.<br>`true`: Self Tuning is enabled. Used for the `Self Tuning` connection string attribute.<br>Default: 1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `StatementCacheSize`               | Specifies the number of cursors or statements to be cached on the database for each connection. This setting corresponds to Statement Cache Size attribute in the connection string. A value greater than zero also enables statement caching.<br>Configuration Support:<br>Windows Registry, XML file, and Statement Cache Size connection string attribute<br>Valid Values:<br>`0 <=` `n` `<=` the value of `OPEN_CURSORS` parameter set in `init.ora` database config file.<br>`n` is the number to set.<br>Default: `0`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `StatementCacheWithUdts`           | Specifies whether or not Oracle UDTs retrieved by executing a `SELECT` statement are cached along with the statement in the statement cache. This setting affects the memory usage and performance of the application.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>`0`: Oracle UDTs are not cached with statements.<br>`1`: Oracle UDTs are cached along with statements.<br>Default: `1`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `ThreadPoolMaxSize`                | Specifies the default maximum size of worker threads for each available processor in a process. This value may affect the performance of ODP.NET connection creation, command execution timeout, and external procedures (`extproc`) that use the thread pool. However, unnecessarily increasing thread pool maximum size can also cause performance problems.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>`0 <=` `n` `<= int.MaxValue`: Allows ODP.NET to reset thread pool maximum size with the value `n`. The ODP.NET reset operation may be ignored if the value is invalid. For example, if n is less than the number of available processors of the system. In this case, the result is the same as the value `-1`.<br>`-1`: Leave the thread pool max size as is.<br>Default: `-1` (this registry entry is not created by default)<br>Note that prior to ODAC 2007 or version 11.1.0.6.20, ODP.NET resets the thread pool maximum size to `int.MaxValue` when the `OracleCommand.CommandTimeout` property is set to a value greater than 0. This erroneous behavior has been corrected. `OracleCommand.CommandTimeout` does not change thread pool maximum size.                                                                                                                                                                                                                                                                    |
| `TraceFileName`                    | Specifies the file name to be used for logging trace information.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>Any valid directory location and file name.<br>Default: `c:\odpnet2.trc` (for .NET Framework 2.0)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TraceLevel`                       | Specifies the level of tracing in ODP.NET. Because tracing all the entry and exit calls for all the objects can be excessive, `TraceLevel` is provided to limit tracing to certain areas of the provider. Each valid value indicates a possible tracing level. Compounded tracing levels can be obtained by adding the valid values.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>`0`: None<br>`1`: Entry, exit, and SQL statement information<br>`2`: Connection pooling statistics<br>`4`: Distributed transactions (enlistment and delistment)<br>`8`: User-mode dump creation upon unmanaged exception<br>`16`: HA Event Information<br>`32`: Load Balancing Information<br>`64`: Self Tuning Information<br>`127`: All the above<br>Default: 0<br>Note: ODP.NET does bit-wise checking on the value. When tracing is enabled, logging to the trace file can affect ODP.NET performance.<br>Note: The user-mode dump creation requires `dbghelp.dll` version 5.1.2600.0 or later.                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `TraceOption`                      | Specifies whether to log trace information in single or multiple files for different threads. If a single trace file is specified, the file name specified in `TraceFileName` is used. If the multiple trace files option is requested, a Thread ID is appended to the file name provided to create a trace file for each thread.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>`0`: Single trace file<br>`1`: Multiple trace files<br>Default: `0`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `UdtCacheSize`                     | Specifies the size of the object cache for each connection in kilobytes (KB) that ODP.NET uses to retrieve and manipulate Oracle UDTs.<br>Configuration Support:<br>Windows Registry and XML file<br>Valid Values:<br>`0 <=` `n` `<= 4194303`, `n` is the number to set.<br>Default: `4096`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `UDT Mapping`                      | Specifies a mapping between a custom type and an Oracle UDT in the database. The mappings can be specified in configuration files and custom type factories. However, if the mapping is specified in both places, mappings specified in the configuration files takes precedence over mappings specified using custom type factories.<br>Configuration Support:<br>XML file and Custom Type Factory Classes<br>Valid Values:<br>Any valid mapping.<br>Default: none                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

### Windows Registry

Upon installation, ODP.NET creates entries for configuration and tracing within the Windows Registry. Configuration and tracing registry values apply across all ODP.NET applications running in that Oracle client installation. Individual ODP.NET applications can override some of these values by configuring them within the ODP.NET application itself (for example, `FetchSize`). Applications can also use the .NET configuration files to override some of the ODP.NET Windows Registry values.

The ODP.NET registry values are located under `HKEY_LOCAL_MACHINE\Software\Oracle\ODP.NET\``version``\`. There is one key for .NET Framework 3.5, and one key for .NET Framework 4 and later.

**Note:**

32-bit applications running on an x64-based version of Windows use the registry subkey, `HKEY_LOCAL_MACHINE\Software\WOW6432node` in place of `HKEY_LOCAL_MACHINE\Software`. If such applications use Oracle Data Provider for .NET (32-bit), then the ODP.NET registry values are located under `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Oracle\ODP.NET\version\`.

### Configuration File Support

For customers who have numerous applications on a computer that depends on a single version of ODP.NET, the Windows Registry settings for a given version of ODP.NET may not necessarily be applicable for all applications that use that version of ODP.NET. To provide more granular control, ODP.NET Configuration File Support allows developers to specify ODP.NET configuration settings in an application config, `web.config`, or a `machine.config` file.

If a computer does not require granular control beyond configuration settings at the ODP.NET version level, there is no need to specify ODP.NET configuration settings through configuration files.

The following is an example of a `web.config` file for .NET Framework 2.0 and later:

    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <oracle.dataaccess.client>
        <settings>
          <add name="DllPath"               value="C:\oracle\bin"/>
          <add name="FetchSize"             value="131072"/>
          <add name="StatementCacheSize"    value="10"/>
          <add name="TraceFileName"         value="D:\odpnet2.trc"/>
          <add name="TraceLevel"            value="63"/>
          <add name="TraceOption"           value="1"/>
        </settings>
      </oracle.dataaccess.client>
    </configuration>

The following is an example of `app.config` for ODP.NET, Unmanaged Driver using .NET Framework 2.0, which sets some additional attributes as well as two UDT type mappings:

    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <oracle.dataaccess.client>
       <settings>
         <add name="DbNotificationPort" value="-1"/>
         <add name="DllPath" value="C:\app\user\product\11.1.0\client_1\bin"/>
         <add name="DynamicEnlistment" value="0"/>
         <add name="FetchSize" value="131072"/>
         <add name="MetaDataXml" value="CustomMetaData.xml"/>
         <add name="PerformanceCounters" value="4095"/>
         <add name="StatementCacheSize" value="50"/>
         <add name="ThreadPoolMaxSize" value="30"/>
         <add name="TraceFileName" value="D:\odpnet2.trc"/>
         <add name="TraceLevel" value="0"/>
         <add name="TraceOption" value="0"/>
         <add name="Person" value="udtMapping factoryName='PersonFactory, Sample,
           Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' typeName='PERSON'
           schemaName='SCOTT' dataSource='oracle'"/>
         <add name="Student" value="udtMapping factoryName='StudentFactory, Sample,
           Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' typeName='STUDENT'
           schemaName='SCOTT'"/>
       </settings>
     </oracle.dataaccess.client>
    </configuration>

ODP.NET, Unmanaged Driver now has the option of using the same configuration file format as ODP.NET, Managed Driver. The format simplifies configuration by using a single unified scheme. To utilize this format, the existing unmanaged ODP.NET configuration section should be renamed from `<oracle.dataaccess.client>` to `<oracle.unmanageddataaccess.client>`. The existing unmanaged ODP.NET elements and values are supported within the new section using the same format as with ODP.NET, Managed Driver. To see how to set the elements and values, see "[Oracle Data Provider for .NET, Managed Driver Configuration](InstallManagedConfig.md)" for more information.

For example, converting the `FetchSize` element and value from the traditional to the new format would be done as follows:

    <oracle.dataaccess.client>
       <settings>
         <add name="FetchSize" value="131072" />
       </settings>
    </oracle.dataaccess.client>

    <oracle.unmanageddataaccess.client>
       <version number="*">
         <settings>
           <setting name="FetchSize" value="131072" />
         </settings>
       </version>
    </oracle.unmanageddataaccess.client>

The traditional ODP.NET, Unmanaged Driver configuration file format will continue to be supported.

#### SQL Translation Framework Configuration

##### Configuring the SQL Translation Profile

The default SQL Translation Profile can be set in the .NET config file, either for all connections across the application, or it is also possible to limit the scope of a profile based on optional `dataSource` and `userId` XML attributes. Please note that these `dataSource` and `userId` XML attributes directly correspond to the `Data Source` and `User Id` attributes in the connection string used to open a database connection.

**Note:**

SQL Translation Profile settings are only supported in the `<oracle.unmanageddataaccess.client>` section. It is not supported in the \<`oracle.dataaccess.client>` section nor the `<oracle.manageddataaccess.client>` section.

This would be used for all connections to the `Data Source`s and `User Id`s.

This would be used for all connections to the specified `Data Source`.

This would be used for all connections to the specified `User Id`.

This would be used for all connections to the specified `Data Source` and `User Id`.

It is possible to configure multiple default profile entries which allow configuring default profiles for different `dataSource` and `userId` attributes, but while selecting a profile, the profile with maximum matching attributes will be selected.

In case there are 2 matching entries, one with `dataSource` only and the other with `userId` only then the entry with matching the `userId` would be given priority over the entry with matching `dataSource`.

With the above configuration, if we try to connect with a connection string which has `stf_ds` for `Data Source` and `stf_user` for `User Id` attributes, then both the entries given above will match and in such cases, we will give priority to the entry with a matching `User Id` attribute which means `profile_user` will be selected as the default profile.

##### Configuring the Error Mapping

Applications can configure the connection related error mapping in their application configuration file. The error mapping can also be scoped based on `Data Source` name, `User Id` and the profile name itself.

Here is an example of providing error mapping with all three attributes.

    <configuration>
      <oracle.unmanageddataaccess.client>
       <version number="*">
       <sqlTranslation>
         <defaultProfiles>
          <defaultProfile dataSource="stf_ds" userId="stf_user" profile=" Profile4"/>
         </defaultProfiles>
         <ErrorMappings>
            <ErrorMapping dataSource="stf_ds" userId="stf_user" profile="Profile4">
              <add oracleErrorNumber="1017" translatedErrorCode="222" />
              <add oracleErrorNumber="1005" translatedErrorCode="888" />
            </ErrorMapping>
         </ErrorMappings>
        </sqlTranslation>
       </version>
      </oracle.unmanageddataaccess.client>
    </configuration>

Please note that `dataSource` and `userId` attributes are optional but can be used to scope the mapping.

It is also possible to provide an error mapping which could be used for all profiles. Here is an example:

    <ErrorMappings>
      <ErrorMapping profile="*">
        <add oracleErrorNumber="1017" translatedErrorCode="222" />
        <add oracleErrorNumber="1018" translatedErrorCode="888" />
      </ErrorMapping>
    </ErrorMappings>

##### Configuring the Default Error Mapping Profile

The default error mapping profile can be configured through the `defaultErrorMappingProfile` setting. This is to be used to specify the default error mapping profile, especially in scenarios when the default profile is not specified through the .NET configuration file, but specified on the server side. In this case, if connectivity related errors occur, then ODP.NET will be able to properly use error mappings specified in the .NET configuration file for the profile specified by the `defaultErrorMappingProfile` setting.

Here is an example to configure the default error mapping profile:

    <sqlTranslation>
      <settings>
        <add name="defaultErrorMappingProfile" value="error_mapping_profile" />
      <settings>
    </sqlTranslation>

##### Configuring the SQL Translation Framework Statement Cache Size

Client can configure the number of translated statements that ODP.NET can cache internally to avoid translations, which can be an expensive operation.

Here is an example to configure default error mapping profile:

    <sqlTranslation>
        <settings>
          <add name="translatedStatementCacheSize" value="50" />
          <settings>
    </sqlTranslation>

##### Sample SQL Translation Framework configuration file

Here is a sample configuration file with all possible elements that can be used:

    <sqlTranslation>
      <settings>
        <add name="translatedStatementCacheSize" value="50" />
        <add name="defaultErrorMappingProfile" value="def_Profile" />
      <settings>
      <defaultProfiles>
        <defaultProfile profile="STF.NO_DS_NO_USERID"/>
        <defaultProfile userId="stf" profile="STF_NO_DS"/>
        <defaultProfile dataSource="stf_inst" profile="STF_NO_USERID"/>
        <defaultProfile dataSource="stf_inst" userId="stf" profile="STF.STF_X"/>
      </defaultProfiles>
      <ErrorMappings>
        <ErrorMapping profile="def_profile">
          <add oracleErrorNumber="1017" translatedErrorCode="444" />
        </ErrorMapping>
        <ErrorMapping dataSource="stf_inst" userId="stf" profile=" STF.STF_X ">
          <add oracleErrorNumber="1018" translatedErrorCode="88888" />
        </ErrorMapping>
      </ErrorMappings>
    </sqlTranslation>

Example 2-1 Setting the profile which could be used for all connections

    <configuration>
      <oracle.unmanageddataaccess.client>
       <version number="*">
        <sqlTranslation>
         <defaultProfiles>
           <defaultProfile profile="Profile1"/>
          </defaultProfiles>
         </sqlTranslation>
       </version>
      </oracle.unmanageddataaccess.client>
    </configuration>

Example 2-2 Setting the Profile for a Specific Data Source

    <defaultProfiles>
      <defaultProfile dataSource="stf_ds" profile="Profile2"/>
    </defaultProfiles>

Example 2-3 Setting the Profile for a Specific User Id

    <defaultProfiles>
      <defaultProfile userId="stf_user" profile="Profile3"/>
    </defaultProfiles>

Example 2-4 Setting the Profile for a Specific Data Source and User Id'

    <defaultProfiles>
      <defaultProfile dataSource="stf_ds" userId="stf_user" profile="Profile4"/>
    </defaultProfiles>

Example 2-5 Configuring Multiple Default Profile Entries

    <defaultProfiles>
      <defaultProfile dataSource="stf_ds" profile="profile_ds"/>
      <defaultProfile userId="stf_user" profile="profile_user"/>
    </defaultProfiles>

#### Specifying UDT Mappings with Unified Configuration for Unmanaged ODP.NET

As UDT mapping is not currently supported by ODP.NET, Managed Driver, a new section within the `<version>` section is used to support custom UDT mappings for unmanaged ODP.NET in the unified configuration format. This new section is identified as `<udtmappings>` and each mapping is identified using a `<udtmapping>` element. The following attributes may be specified for each `udtMapping` element:

- `typeName` (required)

- `factoryName` (required)

- `dataSource` (optional)

- `schemaName` (optional)

These elements retain the same name and meaning as when used with the traditional configuration format.

Example of converting traditional format to unified format:

    <configuration>
       <oracle.dataaccess.client>
         <settings>
           <add name="Person" value="udtMapping factoryName='PersonFactory, Sample, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' typeName='PERSON' schemaName='SCOTT' dataSource='oracle'" />
         </settings>
       </oracle.dataaccess.client>
    </configuration>

    <configuration>
       <oracle.unmanageddataaccess.client>
         <udtmappings>
           <udtmapping typename="PERSON" factoryname="PersonFactory, Sample, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" schemaname="SCOTT" datasource="oracle" />
         </udtmappings>
       </oracle.unmanageddataaccess.client>
    </configuration>

**See Also:**

[Oracle User-Defined Types (UDTs) and .NET Custom Types](featUDTs.md)
