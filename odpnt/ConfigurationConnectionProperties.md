`OracleConfiguration` Connection properties are listed in Table 6-31.

Table 6-31 OracleConfiguration Connection Properties

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

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
