`OracleConfiguration` High Availability properties are listed in Table 6-35.

Table 6-35 OracleConfiguration High Availability Properties

| Property                                                                                 | Description                                                                                                                                                                                                      |
|:-----------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [DbNotificationAddress](ConfigurationDbNotificationAddress.md)                           | Specifies the address that the provider listens to for all notifications sent by the database for continuous query notification feature                                                                          |
| [DbNotificationPort](ConfigurationDbNotificationPort.md)                                 | Specifies the port number that the provider listens to for all notifications sent by the database for continuous query notification, Fast Connection Failover, and/or Runtime Connection Load Balancing features |
| [HAEvents](ConfigurationHAEvents.md)                                                     | Enables the application to receive Fast Connection Failover events for maintaining application high availability                                                                                                 |
| [OnsConfigFile](ConfigurationOnsConfigFile.md)                                           | Specifies the configuration file to define Oracle Notification Service (ONS) behavior                                                                                                                            |
| [OnsMode](ConfigurationOnsMode.md)                                                       | Specifies the ONS daemon mode as either `local` or `remote`                                                                                                                                                      |
| [OnsProtocol](ConfigurationOnsProtocol.md)                                               | Defines whether the ONS connection uses TCP/IP or TCP/IP with SSL/TLS                                                                                                                                            |
| [OnsWalletLocation](ConfigurationOnsWalletLocation.md)                                   | Specifies the directory location of the ONS wallets                                                                                                                                                              |
| [OracleOnsServers](ConfigurationOracleOnsServers.md)                                     | Returns a collection of logical ONS servers added through `OracleConfiguration`                                                                                                                                  |
| [ServiceRelocationConnectionTimeout](ConfigurationServiceRelocationConnectionTimeout.md) | Specifies the time to wait before retrying connecting to a service that becomes unavailable.                                                                                                                     |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
