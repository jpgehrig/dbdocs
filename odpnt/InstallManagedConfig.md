ODP.NET, Managed Driver supports .NET configuration file-based settings in `machine.config`, `app.config`, and `web.config`. It does not support Windows registry based configuration. ODP.NET, Managed Driver settings in .NET configuration files are similar to ODP.NET, Unmanaged Driver settings to make porting easier.

The ODP.NET, Managed Driver configuration file section name is `<oracle.manageddataaccess.client>`. The `<oracle.manageddataaccess.client>` settings and values are also supported in unmanaged ODP.NET configuration file: `<oracle.unmanageddataaccess.client>`. While this documentation section discusses managed ODP.NET configuration, it is also applicable to `<oracle.unmanageddataaccess.client>`. The `<oracle.unmanageddataaccess.client>` settings are actually a superset of `<oracle.manageddataaccess.client>`. The `<oracle.unmanageddataaccess.client>` settings not available in managed ODP.NET are documented in "[Oracle Data Provider for .NET, Unmanaged Driver Configuration](InstallUnmanagedConfig.md)". A typical .NET config that uses ODP.NET, Managed Driver has some or all of the following subsections nested within a `<version>` subsection under `<oracle.manageddataaccess.client>` section. Note the tag names are case sensitive, while the attribute names are case insensitive.

    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <oracle.manageddataaccess.client>
        <version number="*">
          <dataSources>
            ...
            ...
          </dataSources>
          <settings>
            ...
            ...
          </settings>
          <LDAPsettings>
            ...
            ...
          </LDAPsettings>
          <implicitRefCursor>
            ...
            ...
          </implicitRefCursor>
          <edmMappings>
            ...
            ...
          <edmMappings>
        </version>
        <version number="4.121.2.0">
          <dataSources>
            ...
            ...
          </dataSources>
          <settings>
            ...
            ...
          </settings>
          <LDAPsettings>
            ...
            ...
          </LDAPsettings>
          <implicitRefCursor>
            ...
            ...
          </implicitRefCursor>
          <edmMappings>
            ...
            ...
          <edmMappings>
        </version>
      </oracle.manageddataaccess.client>
    </configuration>

The ODP.NET, Managed Driver configuration and settings are described in the following sections. Many of the attributes are the same as ODP.NET, Unmanaged Driver. See [Table 2-3](InstallUnmanagedConfig.md) for detailed attribute descriptions.

### version Section

All the information required by an application should be grouped under the `version` subsections. Each` <version number="X">` section contains parameters applicable for version `X` of the ODP.NET, Managed Driver. For example, `<version number="4.121.2.0">` section parameters will be applicable only for those applications using ODP.NET, Managed Driver assembly 4.121.2.0.

Apart from version specific sections, there can also be a generic section `<version number="*">`. This section's parameters are applicable for all ODP.NET, Managed Driver versions. Parameters in the version specific section take precedence over the parameters of the generic section. The following is an example of a `version` section:

    <oracle.manageddataaccess.client>
      <version number="*">
         <settings>
              <setting name="TraceOption" value="1"/>
              <setting name="PerformanceCounters" value="0" />
         </settings>
      </version>
      <version number="4.121.2.0">
         <settings>
              <setting name="PerformanceCounters" value="4095" />
         </settings>
      </version>
    </oracle.manageddataaccess.client>

An application referencing ODP.NET, Managed Driver 4.121.2.0 has the following values set:

- `TraceOption = 1`

- `PerformanceCounters= 4095`

### dataSources Section

This section can appear only under a `<version>` section. The mapping between the different data source aliases and corresponding data descriptors should appear in this section. The following is an example.

    <dataSources>
      <dataSource alias="inst1" descriptor="(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)......)))"/>
      <dataSource alias="inst2" descriptor="(DESCRIPTION= ......)))"/>
    </dataSources>

**Note:**

The `data source` connection string attribute can alternatively be set to a full descriptor or Easy Connect syntax rather than a data source alias.

Requirements for connecting to a local database without specifying "data source" connection string attribute:

- The listener must be up and running.

- `ORACLE_SID` environment variable must be set appropriately.

**Note:**

When `data source` connection string attribute is not specified, protocol defaults to 'tcp' and port defaults to '1521'.

The ODP.NET managed driver reads and caches all the alias entries from the `app.config`, `web.config`, `machine.config`, and from a `tnsnames.ora` file that is found at application start-up time. However, aliases that are defined in LDAP servers are resolved and cached on demand. This means for each unique alias that is used by the application, an alias resolution query is executed against an LDAP server and the full descriptor associated with the alias will be cached once it is fetched.

For developers that need to change or add alias settings while developing applications, one may consider using `OracleDataSourceEnumerator.GetDataSources()` rather than restarting the application. Invoking this method will first wipe out existing cache entries that were read from the `tnsnames.ora` file and all aliases obtained from the LDAP Server. Then, the `tnsnames.ora` is re-parsed and all its entries will be cached again. Please note that the `app.config`, `web.config`, and `machine.config` entries are read only once at application start-up time and thus their contents are maintained and not re-parsed even if `OracleDataSourceEnumerator.GetDataSources()` is invoked.

The `OracleDataSourceEnumerator.GetDataSources()` method invocation has an impact on the connection pool. This is because a connection pool, which is created for each unique connection string, will cache the resolved full descriptor information after the first connection is created for a given connection pool. After that, the connection pool uses the cached full descriptor information for all subsequent connection creations. Thus, for applications that have their `tnsnames.ora` or LDAP entries modified during the execution of an application where an alias points to a different database than before, one should call the `OracleDataSourceEnumerator.GetDataSources()` method to remove old cached entries. This should be followed by the invocation of the `ClearPool(OracleConnection)` instance method or the `ClearAllPools() `static method to remove existing connections and also have it obtain a new full descriptor value that was read by the invocation of `OracleDataSourceEnumerator.GetDataSources()`. Following this scheme will assure that all the connections in the connection pool uses the new full descriptor that is now associated with the alias and all connections in a connection pool is established to the same database.

The following keywords are supported within the descriptor setting:

- `ADDRESS`

- `ADDRESS_LIST` (Note: only failover supported)

  Oracle recommends using SCAN listener and Runtime Load Balancing to balance the load when connecting to an Oracle RAC database.

- `DESCRIPTION`

- `DESCRIPTION_LIST` (Note: Failover supported; `Address_list` load balancing not supported)

- `HOST` (Note: \<hostname\>, \<IPv6 literal\>, and \<IPv4 literal\> are supported)

- `HTTPS_PROXY`

- `HTTPS_PROXY_PORT`

- `IP` (Note: "loopback" is supported)

- `PROTOCOL` (Note: tcp and tcps are supported)

- `RETRY_COUNT`: Specifies the number of times an `ADDRESS` list is traversed before the connection attempt is terminated and times out.

- `RETRY_DELAY`: Specifies the delay in seconds between subsequent retries for a connection.

  `RETRY_COUNT` and `RETRY_DELAY` are timeout parameters that work at the Oracle networking layer. They are intended to be used in conjunction with each other. When these parameters are used, ODP.NET will attempt to connect with one of the addresses in the `ADDRESS_LIST`. If there is no successful connection after going through the entire list, then ODP.NET will wait for the number of seconds specified by `RETRY_DELAY` before traversing the address list again. It will repeat this behavior until there is a successful connection or the `RETRY_COUNT` limit is hit.

  For example, let's assume `RETRY_COUNT=2` and `RETRY_DELAY=4` when ODP.NET cannot successfully connect to any address on the list. The following sequence is triggered:

  1.  Traverse address list to connect.

  2.  Wait four seconds for next set of retry attempts.

  3.  Traverse the address list again. This is first set of retry attempts.

  4.  Wait four seconds for the next retry attempt.

  5.  Traverse the address list again. This is the second and final set of retry attempts.

  6.  Timeout

  These timeout parameters function independent of ODP.NET application timeouts, such as the `Connection Timeout` connection string attribute. If the `Connection Timeout` is set to a low value, then it may trigger before the `RETRY_COUNT` and `RETRY_DELAY` attempt cycle completes.

- `SDU` (Note: `256` to `65536` are supported)

- `SECURITY: SSL_VERSION `(Note: overrides sqlnet.ora:ssl_version)

- `TRANSPORT_CONNECT_TIMEOUT` (Note: overrides tcp.connect_timeout)

**Note:**

- SSL is now supported via method MCS and FILE.

- Both Kerberos5 and NTS authentication are supported. RADIUS is not supported.

- Only NTS authentication is supported. No RADIUS nor Kerberos5 authentication.

- Only Net Services, Easy Connect naming, and LDAP (namely, Active Directory and Oracle Internet Directory) are supported.

- No bequeath (`beq`) support. Default address is instead TCP loopback with port 1521 and Oracle service name from environment (`ORACLE_SID`)

**See Also:**

[Oracle Database Net Services Reference](../netrf/index.md) for a detailed description of the attributes.

Though managed ODP.NET does not support TNS descriptor based load balancing, it does support failover through both an `ADDRESS_LIST` and `DESCRIPTION_LIST`.

Note that you need not specify either the `LOAD_BALANCE` or the `FAILOVER` directive, because only failover is supported. The directives are ignored.

The following examples demonstrate TNS descriptors utilizing failover:

    (DESCRIPTION=
       (ADDRESS_LIST=
         (ADDRESS=(PROTOCOL=tcp)(HOST=host1)(PORT=1630))
         (ADDRESS=(PROTOCOL=tcp)(HOST=host2)(PORT=1630))
         (ADDRESS=(PROTOCOL=tcp)(HOST=host3)(PORT=1521)))
       (CONNECT_DATA=(SERVICE_NAME=Sales.us.example.com)))

    (DESCRIPTION_LIST=
     (DESCRIPTION=
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales1a-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales1b-svr)(PORT=1521)))
      (CONNECT_DATA=(SERVICE_NAME=sales1.example.com)))
     (DESCRIPTION=
      (ADDRESS_LIST=
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales2a-svr)(PORT=1521))
       (ADDRESS=(PROTOCOL=tcp)(HOST=sales2b-svr)(PORT=1521)))
      (CONNECT_DATA=(SERVICE_NAME=sales2.us.example.com))))

### settings section

This section can appear only under a `<version>` section. Any ODP.NET, Managed Driver specific settings should appear in this section. The following is an example of a `settings` section:

    <settings>
      <setting name="TraceLevel" value="7" />
      <setting name="TraceOption" value="1"/>
      <setting name="TNS_ADMIN" value="C:\oracle\work"/>
    </settings>

A new default behavior has been introduced for ODP.NET Release 12.1.0.2 and later when `InitialLobFetchSize` is set to `-1`. The new default value is `LegacyEntireLOBFetch = 0`. To use the old behavior, set `LegacyEntireLobFetch = 1` in the ODP.NET configuration. Refer to "[Setting InitialLONGFetchSize to -1](featData.md)" for more information.

ODP.NET, Managed Driver configuration settings that are supported:

- `BindByName`

- `CPVersion`: Determines whether ODP.NET, Unmanaged Driver uses the traditional connection pool implementation (`Default=1.0`) or the more modern connection pool implementation with better high availability support (`2.0`). In addition, the more modern connection pool (`2.0`) is required if the application uses Database Resident Connection Pooling (DRCP), or hosts multiple pluggable databases or editions in the same pool. Possible values: `1.0` or `2.0`.

  ODP.NET, Managed Driver only uses the more modern connection pool implementation. This setting can only be used for ODP.NET, Unmanaged Driver for .NET Framework 4 and higher. It cannot be used for earlier versions of unmanaged ODP.NET, which will always use the traditional connection pool implementation.

  If `CPVersion` is set explicitly, then that setting will be used across processes for all connection strings.

  If `CPVersion` is left unmodified (or contains an invalid value) and an application's first unmanaged ODP.NET established connection for a given connection string uses DRCP, pluggable databases, or editions by modifying one these features' properties or configuration settings, then `CPVersion` will be implicitly modified to use the newer connection pool implementation (`2.0`).

  If a `CPVersion 1.0` pool attempts to use DRCP, pluggable database, or edition settings, then ODP.NET will raise an exception when the application attempts to open a connection.

  When `CPVersion 2.0` is used explicitly or implicitly and the "proxy user id" is not specified in the connection string, then a proxy connection will not be created, even if "proxy password" is supplied.

  When `CPVersion 2.0` is used by ODP.NET, Unmanaged Driver, the connection pool behavior will be the same as the more modern connection pool as implementation that ODP.NET, Managed Driver uses.

- `DbNotificationPort`

- `DemandOraclePermission`

- `Disable_Oob`: Interrupts database query execution via either TCP/IP urgent data or normal TCP/IP data, called out of band data (default) or in band data, respectively. (Default=`off`).

  All Oracle database clients support interrupting database query execution, such as through an ODP.NET command timeout. Windows-based database servers only support in band breaks, whereas all other (predominantly UNIX-based) database servers can support out of band (OOB) or in band breaks. ODP.NET, Managed Driver uses OOB breaks by default with database servers that support it. For certain network topologies, the routers or firewalls involved in the route to the database may have been configured to drop urgent data or in band the data. If the routers or firewalls can not be changed to handle urgent data appropriately, then the ODP.NET, Managed Driver can be configured to utilize in band breaks by setting the .NET configuration parameter `Disable_Oob` to `on`.

- `DRCPConnectionClass`: Specifies a logical name that identifies the DRCP connection pool that the ODP.NET connection will use. It will be used as a default if the `DRCPConnectionClass` property on the `OracleConnection` object is not set. It will be ignored for non-DRCP connections.

  Valid Values: the connection class name is string at max 1024 characters. The default is null.

- `FetchSize`

- `LDAP_ADMIN`: Specifies the `ldap.ora` location. The `LDAP_ADMIN` setting works in conjunction with the `TNS_ADMIN` setting to set `ldap.ora` search order.

  `ldap.ora` is searched in the following order:

  - `TNS_ADMIN` in `app.config` or `web.config`

  - `LDAP_ADMIN` in `app.config` or `web.config`

  - current working directory

  - `%ORACLE_HOME%\network\admin`

  - `%ORACLE_HOME%\ldap\admin`

- `LegacyEntireLOBFetch`

- `MaxStatementCacheSize`

- `MetaDataXml`

- `NAMES.DIRECTORY_PATH`: The default search order is `TNSNAMES` and `EZCONNECT`. `TNSNAMES`, `LDAP`, and `EZCONNECT` are the only name resolution methods supported, but their order of precedence can be modified.

- `NAMES.LDAP_AUTHENTICATE_BIND`

- `NAMES.LDAP_CONN_TIMEOUT`

- `NODELAY`

- `ORA_DEBUG_JDWP`: Allows Oracle PL/SQL Debugger and database to connect automatically without application code changes. Value is set as `host=<``IP_address or host_name``>;port=<``debugging port number``>`. Ex. `host=localhost;port=1234`

- `ORACLE_SID`

- `PerformanceCounters`

- `RECEIVE_BUF_SIZE`: Sets TCP `SO_RECVBUF`, the total buffer space associated with the local side of a TCP socket

- `SelfTuning`

- `SEND_BUF_SIZE`: Sets TCP `SO_SENDBUF`, the total buffer space associated with the local side of a TCP socket

- `ServiceRelocationConnectionTimeout`

  In seconds. (`Default` = `90`).

  Whenever a database service becomes unavailable, such as due to a service being relocated, an application can encounter numerous connectivity errors during this time. To avoid unnecessary connection attempts to an unavailable service which will result in an error, ODP.NET, Managed and Unmanaged Drivers block any connection attempts until the service is up or until this property's specified time limit expires from the time when the service DOWN event was received, whichever comes first. Once the specified time elapses, all the connection attempts to the specific service which is known to be down will no longer be blocked. Those requests will be sent to the server. `ServiceRelocationConnectionTimeout` is only operational in conjunction with Oracle Fast Connection Failover (`HA Events` = `true`). Once Fast Connection Failover is enabled for the .NET application, Service Relocation Connection Timeout is automatically enabled. It will use its default value if no `ServiceRelocationConnectionTimeout` value has been explicitly set. It works with planned and unplanned outages.

  When connecting to Oracle Data Guard in Oracle Database 12c Release 2 or later, database administrators can set their own timeout value, `drain_timeout`, to indicate the number of seconds allowed for resource draining to be completed. This setting can be optionally used by the ODP.NET `ServiceRelocationConnectionTimeout` value as the intent behind `drain_timeout `and `ServiceRelocationConnectionTimeout` are the same.

  If `ServiceRelocationConnectionTimeout` and `drain_timeout` are not set, then the default `ServiceRelocationConnectionTimeout` value is used (90 seconds). If only `drain_timeout` is set, then that value will be used for the service relocation connection timeout. If only `drain_timeout` is set and is set to 0, then also default `ServiceRelocationConnectionTimeout` value is used (90 seconds). If both are set, then the value of `ServiceRelocationConnectionTimeout` will override the value of `drain_timeout`.

  `ServiceRelocationConnectionTimeout` itself can be set based upon the value of `drain_timeout`. For example, if ODP.NET administrators desire the service relocation connection timeout to be `drain_timeout` plus 50 seconds, then they would set `ServiceRelocationConnectionTimeout` in the following manner:

      <setting name="ServiceRelocationConnectionTimeout" value="drain_timeout + 50"/>

  Service Relocation Connection Timeout is not supported in pools that connect to more than one pluggable database.

- `SQLNET.AUTHENTICATION_SERVICES`: Supported values are `Kerberos5`, `NTS`, `TCPS`, or `NONE`.

  Managed ODP.NET supports `NTS`, `Kerberos5`, and `TCPS` external authentication methods. This setting should be set based on the desired database authentication method. If internal database authentication is desired, then the setting should be set to `NONE`. Default value is `NONE`. The value(s) must be enclosed in parentheses. Example settings made in `sqlnet.ora` are:

      SQLNET.AUTHENTICATION_SERVICES = (TCPS)
      SQLNET.AUTHENTICATION_SERVICES = (NTS)
      SQLNET.AUTHENTICATION_SERVICES = (Kerberos5, NTS)
      SQLNET.AUTHENTICATION_SERVICES = (NONE)

  **Note:**

  The `NTS` external authentication methodology is only supported on a Windows-based client and server.

  `SQLNET.AUTHENTICATION_SERVICES` default values are different for managed ODP.NET and unmanaged ODP.NET. Managed ODP.NET defaults to `NONE` and unmanaged defaults to `ALL` when no value is set.

- `SQLNET.CRYPTO_CHECKSUM_CLIENT`: Specifies the desired data integrity behavior when this client connects to a server. Supported values are `accepted`, `rejected`, `requested`, or `required`. Default = `accepted`.

- `SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT`: Specifies the data integrity algorithms that this client uses. Supported values are `SHA512`, `SHA384`, `SHA256`, and `SHA1`.

- `SQLNET.USE_HTTPS_PROXY`

- `StatementCacheSize`

- `SSL_SERVER_DN_MATCH`: To enforce the distinguished name (DN) for the database server matches its service name. (Default=`no`).

  If you enforce the match verification, then SSL/TLS ensures that the certificate is from the server. If you select to not enforce the match verification, then SSL/TLS performs the check but allows the connection, regardless if there is a match. Not enforcing the match allows the server to potentially fake its identify.

  Supported values: `yes` \| `on` \| `true` to enforce a match.

  Supported values: `no` \| `off` \| `false` to not enforce a match.

  `SSL_SERVER_DN_MATCH` is often used together with `SSL_SERVER_CERT_DN`. `SSL_SERVER_CERT_DN` specifies the distinguished name (DN) of the database server. It can be set in the connect descriptor.

      net_service_name=
        (DESCRIPTION=
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
          (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521))
          (CONNECT_DATA=
            (SERVICE_NAME=sales.us.acme.com))
            (SECURITY=
             (SSL_SERVER_CERT_DN="cn=sales,cn=OracleContext,dc=us,dc=acme,dc=com")))

  The client uses this information to obtain the list of DNs it expects for each of the servers, enforcing the database server DN to match its service name. Use this parameter with `SSL_SERVER_DN_MATCH` to enable server DN matching.

- `SSL_VERSION`: Sets the version of the SSL/TLS connection. By default, all supported versions are enabled, in the order 3.0, 1.0, 1.1, and 1.2.

  The client and server negotiate to the highest version among the common conversions specified in their configurations. The versions from lowest to highest are: 3.0 (lowest), 1.0, 1.1, and 1.2 (highest).

- `TNS_ADMIN`: Location where either one or more of `tnsnames.ora`, `ldap.ora`, and `sqlnet.ora` are located. Locations can consist of either absolute or relative directory paths.

- `TraceFileLocation`: Trace file destination directory, for example, `D:\traces`. The default `TraceFileLocation` is `<Windows user temporary folder>``\ODP.NET\managed\trace`.

- `TraceLevel`: `1` = public APIs; `2` = private APIs; `4` = network APIs/data. These values can be `OR`ed. To enable everything, set `TraceLevel` to `7`. Errors will always be traced.

- `TraceOption`

- `TCP.CONNECT_TIMEOUT`

- `WALLET_LOCATION`: Microsoft Certificate Store (MCS) and file system wallets are supported.

- `SQLNET.ENCRYPTION_CLIENT` = Negotiates whether to turn on encryption. Supported values are accepted, rejected, requested, or required.

- `SQLNET.ENCRYPTION_TYPES_CLIENT` = Encryption algorithm(s) to use.

The following table lists the valid encryption algorithms for ODP.NET, Managed Driver.

Table 2-4 Encryption Algorithms for ODP.NET, Managed Driver

| Algorithm Name  | Legal Value |
|:----------------|:------------|
| AES 128-bit key | AES128      |
| AES 192-bit key | AES192      |
| AES 256-bit key | AES256      |
| 2-key 3DES      | 3DES112     |
| 3-key 3DES      | 3DES168     |

For more information on data encryption settings, refer to the [Oracle Database Security Guide](../dbseg/configuring-network-data-encryption-and-integrity.md).

**See Also:**

[Oracle Database Net Services Reference](../netrf/index.md)

### LDAPsettings section

This section can appear only under a `<version>` section. Any ODP.NET, Managed Driver specific LDAP settings should appear in this section. The following is an example of a `<LDAPsetting>` subsection under the `<LDAPsettings>` section:

    <LDAPsettings>
      <LDAPsetting name="DIRECTORY_TYPE" value="AD" />
      <LDAPsetting name="DEFAULT_ADMIN_CONTEXT" value="dc=Oracle,dc=com"/>
    </LDAPsettings>

### Lightweight Directory Access Protocol

ODP.NET, Managed Driver supports TNS alias resolution through a LDAP server/service, specifically Microsoft Active Directory and Oracle Internet Directory (OID). TNS alias resolution occurs when using the `LDAPsettings` section or `ldap.ora` file settings. The `LDAPsettings` section settings take precedence over `ldap.ora` settings.

For Active Directory, only the `DIRECTORY_TYPE` and `DEFAULT_ADMIN_CONTEXT` parameters are required in `ldap.ora`. When the `DIRECTORY_SERVERS` parameter is missing or has no value, the default LDAP server for the current domain will be used.

For OID, all `ldap.ora` parameters must be set with valid values to complete configuration.

ODP.NET, Managed Driver and ODP.NET, Unmanaged Driver support the same level of security when using LDAP for name resolution.

Table 2-5 Microsoft Active Directory: Encryption Types and Authentication Credentials For Connecting and Binding

| No Encryption              | SSL Encryption             |
|:---------------------------|:---------------------------|
| Anonymous authentication   | Anonymous authentication   |
| Domain User authentication | Domain User authentication |

Table 2-6 Oracle Internet Directory: Encryption Types and Authentication Credentials For Connecting and Binding

| No Encryption            | SSL Encryption                                                                                                                   |
|:-------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| Anonymous authentication | Anonymous authentication                                                                                                         |
| \-                       | Wallet based authentication<br>Note: Wallet based authentication for Oracle Internet Directory is not supported for this release |

**See Also:**

- [Oracle Database Net Services Reference](../netrf/index.md) for more information on Directory Usage Parameters.

- [Oracle Database Net Services Administrator's Guide](../netag/managing-network-address-information.md) for more information on Managing Network Address.

### implicitRefCursor section

This section can appear only under a` <version>` section. Any information about `REF CURSOR` parameters that need to be bound implicitly should appear in this section. The following is an example of an `<implicitRefCursor>` section:

    <implicitRefCursor>
      <storedProcedure schema="USERREFCUR" name="TestProc1">
        <refCursor name="Param3">
         <bindInfo mode="Output"/>
         <metadata columnOrdinal="0" columnName="DEPTNO" baseColumnName="DEPTNO" baseSchemaName="USERREFCUR" baseTableName="DEPT" nativeDataType="number" providerType="Int32" dataType="System.Int16" columnSize="2" allowDBNull="true" />
         <metadata columnOrdinal="1" columnName="DNAME" baseColumnName="DNAME" baseSchemaName="USERREFCUR" baseTableName="DEPT" nativeDataType="varchar2" providerDBType="String" columnSize="30" />
        </refCursor>
        <refCursor name="param2">
          <bindInfo mode="Output"/>
          <metadata columnOrdinal="0" columnName="EMPNO" baseColumnName="EMPNO" baseSchemaName="USERREFCUR" baseTableName="EMP" nativeDataType="number" providerType="Int32" dataType="System.Int16" columnSize="4" allowDBNull="false" />
        </refCursor>
       </storedProcedure>

       <!--Next stored procedure information-->
       <storedProcedure name="TestProc2">
          ...
          ...
       </storedProcedure>
    </implicitRefCursor>

### distributedTransaction section

This section can appear only under a `<version>` section. Any information about distributed transactions should appear in this section. The following is an example of a `distributedTransaction` section:

    <distributedTransaction>
      <setting name="OMTSRECO_IP_ADDRESS" value="my-pc" />
      <setting name="OMTSRECO_PORT" value="2040" />
      <setting name="ORAMTS_SESS_TXNTIMETOLIVE" value="240" />
    </distributedTransaction>

- `OMTSRECO_IP_ADDRESS`: Specifies the machine name (or IP address) that the OraMTS Recovery service will be running on to resolve database in-doubt transactions. The default is the local machine name.

- `OMTSRECO_PORT`: Specifies the port that the OraMTS Recovery service will be listening on to resolve database in-doubt transactions. The default is 2030.

- `ORAMTS_SESS_TXNTIMETOLIVE` : Specifies the time in seconds that the transaction can remain inactive after it has been detached or delisted from the database. Once this time expires, the transaction is automatically terminated by the provider. The default is 120 seconds.

- `UseManagedDTC`: When set to `false` and using .NET Framework 4.5.2 or higher, ODP.NET uses .NET Framework for distributed transaction support. In all other instances, ODP.NET uses Oracle Services for Microsoft Transaction Server to support distributed transactions. Boolean (`Default = false`) for ODP.NET, Managed Driver only.

- `UseOraMTSManaged`: When set to `true` and using .NET Framework 4.5.2 or higher, ODP.NET uses managed code for distributed transactions. If set to `true`, but .NET 4.5.1 or lower is used, an exception will be thrown. If set to `false`, ODP.NET uses Oracle Services for Microsoft Transaction Server to support distributed transactions. Boolean (`Default = false`) for ODP.NET, Unmanaged Driver only.

### connectionPools section

This section can appear only under a `<version>` section. This section allows setting a string identifier for each set of monitored connection counters. Refer to [Connection Performance Counters](featConnecting.md) documentation section for more details.

### edmMappings section

This section can appear only under a `<version>` section. Any information related to EDM mappings should appear in this section. Refer to [Oracle Number Default Data Type Mapping and Customization](entityDataTypeMapping.md) for more examples on `edmMappings` section.

### onsConfig section

Oracle Notification Service (ONS) can be configured using either local or remote configuration. Remote configuration is the preferred configuration for standalone client applications. For releases earlier than Oracle Database 12c, this section is mandatory for ODP.NET to receive ONS notifications. With Oracle Database 12c and later, this section is optional and the information about the ONS daemons is received from the server itself. However, ODP.NET will also listen for events from any `<host:port>` pairs that is provided by the user in this section in addition to the `<host:port>` pairs received from the server.

For local configuration, please ensure that ONS is configured and available on the node where ODP.NET is running, so that ODP.NET can receive events directly from the local ONS daemon. The following is a sample format for the local configuration:

    <onsConfig configFile="C:\temp\test.config" mode="local">
    </onsConfig>

**Note:**

The `configFile` specified in .NET config should contain the same `localport` and `remoteport` values as specified in the `ons.config` used by the local ONS daemon. This will enable the application to receive events from the local ONS daemon.

Remote configuration is used in scenarios where the application directly receives ONS events from the ONS daemons running on remote machines. One of the advantages of this configuration is that no ONS daemon is needed on the client end and, therefore, there is no need to manage this process.

The following is a sample format for remote configuration:

      <onsConfig mode="remote">
            <ons database="db1">
              <add name="nodeList" value="racnode1:4100, racnode2:4200" />
            </ons>
            <ons database="db2">
              <add name="nodeList" value=" racnode3:4100, racnode4:4200" />
            </ons>
          </onsConfig>

In case of remote configuration, the application has to specify the `<host>:<port>` values for every potential database that it can connect to. The `<host>:<port>` value pairs represent the ports on the the different Oracle RAC nodes where the ONS daemons are talking to their remote clients.

**See Also:**

Client Side ONS Daemon Configurationfor information about client side ONS daemon configuration

### ONS TCPS and Wallets

ODP.NET enables ONS communications to occur over TCP/IP with SSL/TLS (TCPS), which is more secure than just TCP/IP. As TCPS requires using a wallet for storing keys and certificates, ODP.NET can use one wallet for both ONS and ODP.NET connections or have separate wallets for each.

TCPS provides more secure ONS communication, gives administrators flexibility in how to configure their wallets, and enables cloud database connections.

`oracle.manageddataaccess.client` configuration section sample

    <oracle.manageddataaccess.client>
        <version number="*">
          <onsConfig mode="remote">
            <settings>
              <setting name="Protocol" value="TCPS" />
              <setting name="WALLET_LOCATION" value="D:\user\ONS_SSLWallet" />
            </settings>
            <ons database="acdb183">
              <add name="nodeList" value="slcai611:6205,slcai610:6205,slcai612:6205" />
            </ons>
          </onsConfig>
          <settings>
            <setting name="WALLET_LOCATION" value=" D:\user\DBWallet" />
          </settings>
        </version>
    </oracle.manageddataaccess.client>

The protocol and wallet location properties are often used together.

If an ONS wallet location is set, ODP.NET will use the wallet for ONS to connect via TCP/IP with SSL/TLS regardless of the protocol setting.

If the protocol is set to “TCPS”, ODP.NET first tries to use the wallet in the ONS configuration wallet location to connect via TCP/IP with SSL/TLS. If no wallet is present, ODP.NET next tries to use the wallet from the database wallet location. If no wallet is found, the connection fails.

Administrators can choose between having the ONS connection use its own independent wallet or share the database’s wallet for ease of use.

If the protocol is set to “TCP” and no ONS wallet location is set, ODP.NET ONS will connect with TCP/IP.

ODP.NET ONS TCPS works with any Oracle Database version that supports ONS TCPS on the server side.

### Client Side ONS Daemon Configuration

ONS configuration is controlled by the ONS configuration file, `ORACLE_HOME``/opmn/conf/ons.config`. This file tells the ONS daemon how it should behave. The `SRVCTL` utility can be used to start and stop the ONS daemon. It is installed on each node by default during server install.

Configuration information within ons.config is defined in simple name and value pairs. An example of `ONS.config` is given below

    # This is an example ons.config file
    #
    # The first three values are required
    localport=4100
    remoteport=4200
    nodes=racnode1.example.com:4200,racnode2.example.com:4200

Some parameters in the ons.config file are required and some are optional. Table Table 2-7 lists the required ONS configuration parameters and Table 2-8 lists the optional ONS configuration parameters.

Table 2-7 Required ONS Configuration Parameters

| Parameter    | Explanation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:-------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `localport`  | The port that ONS binds to on the local host interface to talk to local clients.<br>For example, `localport=4100`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `remoteport` | The port that ONS binds to on all interfaces for talking to other ONS daemons.<br>For example, `remoteport=4200`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `nodes`      | A list of other ONS daemons to talk to. Node values are given as a comma-delimited list of either host names or IP addresses plus ports. The port value that is given is the remote port that each ONS instance is listening on. In order to maintain an identical file on all nodes, the `host:port` of the current ONS node can also be listed in the nodes list. It will be ignored when reading the list.<br>For example, `nodes=myhost.example.com:4200,123.123.123.123:4200`<br>The nodes listed in the nodes line correspond to the individual nodes in the Oracle RAC instance. Listing the nodes ensures that the middle-tier node can communicate with the Oracle RAC nodes. At least one middle-tier node and one node in the Oracle RAC instance must be configured to see one another. As long as one node on each side is aware of the other, all nodes are visible. You need not list every single cluster and middle-tier node in the ONS configuration file of each Oracle RAC node. In particular, if one ONS configuration file cluster node is aware of the middle tier, then all nodes in the cluster are aware of it. |

Table 2-8 Optional ONS Configuration Parameters

| Parameter    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `loglevel`   | The level of messages that should be logged by ONS. This value is an integer that ranges from 1, which indicates least messages logged, to 9, which indicates most messages logged. The default value is 3.<br>For example, `loglevel=3`                                                                                                                                                                                                                                                                                                                                                      |
| `logfile`    | A log file that ONS should use for logging messages. The default value for log file is `$ORACLE_HOME/opmn/logs/ons.log`.<br>For example, `logfile=C:\app\user\product\12.1.0\opmn\logs\myons.log`                                                                                                                                                                                                                                                                                                                                                                                             |
| `walletfile` | The wallet file used by the Oracle Secure Sockets Layer (SSL) to store SSL certificates. If a wallet file is specified to ONS, then it uses SSL when communicating with other ONS instances and require SSL certificate authentication from all ONS instances that try to connect to it. This means that if you want to turn on SSL for one ONS instance, then you must turn it on for all instances that are connected. This value should point to the directory where your `ewallet.p12` file is located.<br>For example, `walletfile=C:\app\user\product\12.1.0\opmn\conf\ssl.wlt\default` |
| `useocr`     | The value, reserved for use on the server-side, to indicate ONS whether it should store all Oracle RAC nodes and port numbers in Oracle Cluster Registry (OCR) instead of the ONS configuration file or not. A value of `useocr=on` is used to store all Oracle RAC nodes and port numbers in Oracle Cluster Registry (OCR).<br>Do not use this option on the client-side.                                                                                                                                                                                                                    |

The `ons.config` file allows blank lines and comments on lines that begin with the number sign (#).

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/index.md) for more information about the `SRVCTL` utility.

### Relative Windows Path and Windows Environment Variable Configuration Settings

The following managed ODP.NET configuration settings support relative Windows path and environment variables:

- `TraceFileLocation`

- `WALLET_LOCATION`

File locations for the above config parameters can now be set using relative Windows paths. The "`.`" notation informs ODP.NET to use the current working directory. Sub-directories can be added by appending them. For example, `.\mydir` refers to the sub-directory `mydir` in the current working directory. To navigate to a parent directory, use the "`..`" notation.

For web applications, the current working directory is the application directory. For Windows applications, the `.EXE` location is the current working directory.

Windows paths can also be set using Windows environment variable names within "`%`" characters.

For example, `%tns_admin%`, `c:\%dir%\my_app_location`, `c:\%top_level_dir%\%bottom_level_dir%` etc.

**Note:**

- If the environment variable that is used by the configuration parameter is not set to anything, then an exception will be thrown.

- A directory name cannot partially be using an environment variable. For example, `c:\my_app_%id%`

- Multiple variables can used in given directory location. For example, `c:\%top_level_dir%\%bottom_level_dir%`.

**See Also:**

[Oracle Database Net Services Reference](../netrf/index.md) chapters covering `sqlnet.ora` parameters, `tnsnames.ora` local naming parameters, and `listener.ora` Oracle Net Listener parameters, for more information about these Oracle client settings.
