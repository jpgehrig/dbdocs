`OracleConfiguration` members are listed in the following tables.

### OracleConfiguration Connection Properties

`OracleConfiguration` Connection properties are listed in Table 6-24.

Table 6-24 OracleConfiguration Connection Properties

| Property                                                                      | Description                                                                                                                                                        |
|:------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [DatabaseEditionName](ConfigurationDatabaseEditionName.md)                    | Specifies the Oracle edition name for the connection object                                                                                                        |
| [DisableOOB](ConfigurationDisableOOB.md)                                      | Specifies whether to enable Oracle Net Services to send or receive out-of-band break messages using urgent data provided by the underlying protocol                |
| [DrcpConnectionClass](ConfigurationDrcpConnectionClass.md)                    | Specifies a logical name that identifies the DRCP connection pool that the ODP.NET connection will use                                                             |
| [HostnameDefaultServiceIsHost](ConfigurationHostnameDefaultServicesIsHost.md) | Specifies whether to default the service name to the hostname in Oracle Easy Connect Naming so that the service name does not need to be specified                 |
| [NamesDirectoryPath](ConfigurationNamesDirectoryPath.md)                      | Specifies the naming method order used for client name resolution lookups                                                                                          |
| [OracleDataSources](ConfigurationOracleDataSources.md)                        | Returns a collection of TNS entries added through `OracleConfiguration`                                                                                            |
| [TcpConnectTimeout](ConfigurationTcpConnectTimeout.md)                        | Specifies the time, in seconds, for a client to establish a TCP connection (PROTOCOL=tcp in the TNS connect address) to the database server before it can time out |
| [TnsAdmin](ConfigurationTnsAdmin.md)                                          | Specifies the `tnsnames.ora` and/or `sqlnet.ora` directory location                                                                                                |

### OracleConfiguration Secure Connection Properties

`OracleConfiguration` Secure Connection Properties are listed in Table 6-25.

Table 6-25 OracleConfiguration Secure Connection Properties

| Property                                                                           | Description                                                                                                                                        |
|:-----------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| [HttpsProxy](ConfigurationHttpsProxy.md)                                           | Specifies HTTP proxy host name for tunneling SSL client connections                                                                                |
| [HttpsProxyPort](ConfigurationHttpsProxyPort.md)                                   | Specifies the forward HTTP proxy host port for tunneling TLS/SSL client connections                                                                |
| [SqlNetAuthenticationServices](ConfigurationSqlNetAuthenticationServices.md)       | Enables one or more authentication services, such as TCP/IP with SSL                                                                               |
| [SqlNetEncryptionClient](ConfigurationSqlNetEncryptionClient.md)                   | Specifies the encryption client behavior                                                                                                           |
| [SqlNetEncryptionTypesClient](ConfigurationSqlNetEncryptionTypesClient.md)         | Specifies encryption algorithms that the client can use                                                                                            |
| [SqlNetCryptoChecksumClient](ConfigurationSqlNetCryptoChecksumClient.md)           | Specifies the checksum client behavior                                                                                                             |
| [SqlNetCryptoChecksumTypesClient](ConfigurationSqlNetCryptoChecksumTypesClient.md) | Specifies the crypto-checksum algorithms the client can use                                                                                        |
| [SqlNetWalletOverride](ConfigurationSqlNetWalletOverride.md)                       | Specifies whether the client overrides the strong authentication credential with the stored wallet password credential for the database connection |
| [SSLServerDNMatch](ConfigurationSSLServerDNMatch.md)                               | Enforces the database server distinguished name (DN) matches its service name                                                                      |
| [SSLVersion](ConfigurationSSLVersion.md)                                           | Enforces the connection to use a specific SSL/TLS version                                                                                          |
| [UseHttpsProxy](ConfigurationUseHttpsProxy.md)                                     | Enables forward HTTP proxy tunneling client connections                                                                                            |
| [WalletLocation](ConfigurationWalletLocation.md)                                   | Specifies the location of wallets                                                                                                                  |

### OracleConfiguration Command Properties

`OracleConfiguration` Command properties are listed in Table 6-26.

Table 6-26 OracleConfiguration Command Properties

| Property                                         | Description                                                                                                          |
|:-------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------|
| [BindByName](ConfigurationBindByName.md)         | Specifies whether the binding method used for the parameter collection is by name or by position                     |
| [CommandTimeout](ConfigurationCommandTimeout.md) | Specifies the number of seconds the command is allowed to execute before terminating the execution with an exception |

### OracleConfiguration Directories Properties

`OracleConfiguration` Directories properties are listed in Table 6-27.

Table 6-27 OracleConfiguration Directories Properties

| Property                                                               | Description                                                                                                                                                                        |
|:-----------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [DefaultAdminContext](ConfigurationDefaultAdminContext.md)             | Specifies the default directory entry that contains a LDAP Oracle Context from which connect identifiers can be created, modified, or looked up                                    |
| [DirectoryServers](ConfigurationDirectoryServers.md)                   | Lists the host names and port numbers of the primary and alternate LDAP directory servers                                                                                          |
| [DirectoryType](ConfigurationDirectoryType.md)                         | Specifies the directory server type used, such as Oracle Internet Directory or Microsoft Active Directory                                                                          |
| [LdapAdmin](ConfigurationLdapAdmin.md)                                 | Specifies the `ldap.ora` directory location                                                                                                                                        |
| [NamesLdapAuthenticateBind](ConfigurationNamesLdapAuthenticateBind.md) | Specifies whether the LDAP naming adapter should attempt to authenticate using a specified wallet when it connects to the LDAP directory to resolve the name in the connect string |
| [NamesLdapConnTimeout](ConfigurationNamesLdapConnTimeout.md)           | specifies the non-blocking connection timeout to the LDAP server                                                                                                                   |

### OracleConfiguration High Availability Properties

`OracleConfiguration` High Availability properties are listed in Table 6-28.

Table 6-28 OracleConfiguration High Availability Properties

| Property                                                                                 | Description                                                                                                                                                                                                      |
|:-----------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [DbNotificationAddress](ConfigurationDbNotificationAddress.md)                           | Specifies the address that the provider listens to for all notifications sent by the database for continuous query notification feature.                                                                         |
| [DbNotificationPort](ConfigurationDbNotificationPort.md)                                 | Specifies the port number that the provider listens to for all notifications sent by the database for continuous query notification, Fast Connection Failover, and/or Runtime Connection Load Balancing features |
| [HAEvents](ConfigurationHAEvents.md)                                                     | Enables the application to receive Fast Connection Failover events for maintaining application high availability                                                                                                 |
| [OnsConfigFile](ConfigurationOnsConfigFile.md)                                           | Specifies the configuration file to define Oracle Notification Service (ONS) behavior                                                                                                                            |
| [OnsMode](ConfigurationOnsMode.md)                                                       | Specifies the ONS daemon mode as either `local` or `remote`                                                                                                                                                      |
| [OnsProtocol](ConfigurationOnsProtocol.md)                                               | Defines whether the ONS connection uses TCP/IP or TCP/IP with SSL/TLS                                                                                                                                            |
| [OnsWalletLocation](ConfigurationOnsWalletLocation.md)                                   | Specifies the directory location of the ONS wallets                                                                                                                                                              |
| [OracleOnsServers](ConfigurationOracleOnsServers.md)                                     | Returns a collection of logical ONS servers added through `OracleConfiguration`                                                                                                                                  |
| [ServiceRelocationConnectionTimeout](ConfigurationServiceRelocationConnectionTimeout.md) | Specifies the time to wait before retrying connecting to a service that becomes unavailable.                                                                                                                     |

### OracleConfiguration Performance Properties

`OracleConfiguration` Performance properties are listed in Table 6-29.

Table 6-29 OracleConfiguration Performance Properties

| Property                                                       | Description                                                                                                             |
|:---------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------|
| [FetchSize](ConfigurationFetchSize.md)                         | Specifies the total memory size, in bytes, that the provider allocates to cache data fetched in one database round-trip |
| [LoadBalancing](ConfigurationLoadBalancing.md)                 | Enables the application to receive runtime connection load balancing information                                        |
| [MaxStatementCacheSize](ConfigurationMaxStatementCacheSize.md) | Specifies the maximum number of statements that can be cached when self-tuning is enabled                               |
| [PerformanceCounters](ConfigurationPerformanceCounters.md)     | Specifies the ODP.NET connection performance counters to publish so that they can be monitored                          |
| [ReceiveBufferSize](ConfigurationReceiveBufferSize.md)         | Specifies the buffer space limit for receive operations of sessions                                                     |
| [SelfTuning](ConfigurationSelfTuning.md)                       | Specifies whether self-tuning is enabled for an ODP.NET application                                                     |
| [SendBufferSize](ConfigurationSendBufferSize.md)               | Specifies the buffer space limit for send operations of sessions                                                        |
| [StatementCacheSize](ConfigurationStatementCacheSize.md)       | Specifies the number of cursors or statements to be cached for each database connection                                 |
| [TcpNoDelay](ConfigurationTcpNoDelay.md)                       | Preempts delays in buffer flushing within the TCP/IP protocol stack                                                     |

### OracleConfiguration Debug Tracing Properties

`OracleConfiguration` Debug Tracing properties are listed in Table 6-30.

Table 6-30 OracleConfiguration Debug Tracing Properties

| Property                                               | Description                                                                                              |
|:-------------------------------------------------------|:---------------------------------------------------------------------------------------------------------|
| [TraceFileLocation](ConfigurationTraceFileLocation.md) | Specifies the destination directory to output provider traces                                            |
| [TraceLevel](ConfigurationTraceLevel.md)               | Specifies the generated trace level to trace ODP.NET calls and diagnose provider issues                  |
| [TraceOption](ConfigurationTraceOption.md)             | Specifies whether to generate a single trace file or multiple trace files for multithreaded applications |
