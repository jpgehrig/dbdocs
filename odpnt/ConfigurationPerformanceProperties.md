`OracleConfiguration` Performance properties are listed in Table 6-36.

Table 6-36 OracleConfiguration Performance Properties

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

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
