This appendix briefly discusses the general structure of Universal Connection Pool (UCP) error messages, UCP error messages for the connection pool layer, and UCP error messages for JDBC data sources and dynamic proxies. The appendix is organized as follows:

- General Structure of UCP Error Messages

- Connection Pool Layer Error Messages

- JDBC Data Sources and Dynamic Proxies Error Messages

Both the message lists are sorted by the error message number.

### A.1 General Structure of UCP Error Messages

The general UCP error message structure enables run-time information to be appended to the end of a message, following a colon, as follows:

    <error_message>:<extra_info>

For example, a `closed statement` error might be displayed as follows:

    Closed Statement:next

This indicates that the exception was thrown during a call to the `next` method (of a result set object).

In some cases, the user can find the same information in a stack trace.

### A.2 Connection Pool Layer Error Messages

This section lists UCP error messages for the connection pool layer.

Table A-1 Connection Pool Layer Error Messages

| Error Message Number | Message                                                                                                                                                               |
|:---------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| UCP-45001            | Universal Connection Pool internal error                                                                                                                              |
| UCP-45002            | No available connections in the Universal Connection Pool                                                                                                             |
| UCP-45003            | Universal Connection Pool already exists                                                                                                                              |
| UCP-45004            | Invalid connection retrieval information                                                                                                                              |
| UCP-45005            | Callback already registered                                                                                                                                           |
| UCP-45006            | Invalid Universal Connection Pool configuration                                                                                                                       |
| UCP-45051            | Inactive connection timeout timer scheduling failed                                                                                                                   |
| UCP-45052            | Abandoned connection timeout timer scheduling failed                                                                                                                  |
| UCP-45053            | Time-to-live connection timeout timer scheduling failed                                                                                                               |
| UCP-45054            | The Universal Connection Pool cannot be null                                                                                                                          |
| UCP-45055            | Error when removing an available connection                                                                                                                           |
| UCP-45057            | The `AvailableConnections` object cannot be null                                                                                                                      |
| UCP-45058            | The `Failoverable` object cannot be null                                                                                                                              |
| UCP-45059            | `MaxPoolsize` is set to 0. There are no connections to return                                                                                                         |
| UCP-45060            | Invalid life cycle state. Check the status of the Universal Connection Pool                                                                                           |
| UCP-45061            | Universal Connection Pool is not started. Start the Universal Connection Pool before accessing                                                                        |
| UCP-45062            | The collection of available connections can only be set when the Universal Connection Pool is in the initialization state                                             |
| UCP-45063            | Universal Connection Pool has been shutdown while attempting to get a connection                                                                                      |
| UCP-45064            | All connections in the Universal Connection Pool are in use                                                                                                           |
| UCP-45065            | Connection borrowing returned null                                                                                                                                    |
| UCP-45091            | Connection labeling callback already registered                                                                                                                       |
| UCP-45092            | Borrowing labeled connection with no labeling callback registered                                                                                                     |
| UCP-45093            | Requested no-label connection but borrowing labeled connection                                                                                                        |
| UCP-45097            | Connection harvesting timer scheduling failed                                                                                                                         |
| UCP-45100            | `ConnectionFactoryAdapter` returned null                                                                                                                              |
| UCP-45103            | `ConnectionFactoryAdapter` must be an instance of `DataSourceConnectionFactoryAdapter`                                                                                |
| UCP-45104            | `ConnectionFactoryAdapter` object cannot be null                                                                                                                      |
| UCP-45105            | `ConnectionFactoryAdapter` must be an instance of `ConnectionPoolDataSourceConnectionFactoryAdapter`                                                                  |
| UCP-45106            | `ConnectionFactoryAdapter` must be an instance of `XADataSourceConnectionFactoryAdapter`                                                                              |
| UCP-45150            | `UniversalPooledConnection` cannot be null                                                                                                                            |
| UCP-45152            | `UniversalPooledConnectionStatus` object cannot be null                                                                                                               |
| UCP-45153            | The connection label key cannot be null or an empty string                                                                                                            |
| UCP-45154            | The connection labeling operation cannot be invoked on closed connections                                                                                             |
| UCP-45155            | Connection harvesting callback already registered                                                                                                                     |
| UCP-45156            | Abandoned connection timeout callback already registered                                                                                                              |
| UCP-45157            | Time-to-live connection timeout callback already registered                                                                                                           |
| UCP-45201            | The connection label key cannot be null or an empty string                                                                                                            |
| UCP-45202            | The cloning of the `ConnectionRetrievalInfo` object failed                                                                                                            |
| UCP-45203            | The Connection Request Info is null                                                                                                                                   |
| UCP-45251            | `ConnectionPoolDataSource` cannot be null                                                                                                                             |
| UCP-45252            | Invalid `ConnectionRetrievalInfo` object                                                                                                                              |
| UCP-45253            | SQLException occurred while getting `PooledConnection` from `ConnectionPoolDataSource`                                                                                |
| UCP-45254            | Invalid connection type. Must be a `javax.sql.PooledConnection`                                                                                                       |
| UCP-45255            | SQLException while closing `PooledConnection`                                                                                                                         |
| UCP-45256            | Data source cannot be null                                                                                                                                            |
| UCP-45257            | Cannot get Connection from Data source                                                                                                                                |
| UCP-45258            | Invalid connection type. Must be a `java.sql.Connection`                                                                                                              |
| UCP-45259            | The connection to proxy must be an instance of `java.sql.Connection`                                                                                                  |
| UCP-45260            | `XADatasource` cannot be null                                                                                                                                         |
| UCP-45261            | `SQLException` occurred while getting `XAConnection` from `XADataSource`                                                                                              |
| UCP-45262            | Invalid connection type. Must be a `javax.sql.XAConnection`                                                                                                           |
| UCP-45263            | `SQLException` occurred while closing `XAConnection`                                                                                                                  |
| UCP-45264            | The connection cannot be null                                                                                                                                         |
| UCP-45265            | The connection to proxy must be an instance of `java.sql.Statement`                                                                                                   |
| UCP-45266            | The statement to proxy must be an instance of `java.sql.ResultSet`                                                                                                    |
| UCP-45267            | The connection to proxy must be an instance of `javax.sql.XAConnection`                                                                                               |
| UCP-45268            | The Driver argument cannot be null                                                                                                                                    |
| UCP-45269            | The URL argument cannot be null                                                                                                                                       |
| UCP-45301            | Unable to get a connection for failover information                                                                                                                   |
| UCP-45302            | Unable to execute SQL query to get failover information                                                                                                               |
| UCP-45303            | SQLException occurred while getting failover information                                                                                                              |
| UCP-45304            | The event type cannot be null                                                                                                                                         |
| UCP-45305            | The event type is invalid. Event type must be `database/event/host or database/event/service`                                                                         |
| UCP-45306            | The failover event type is invalid. It must be an `OracleFailoverEvent`                                                                                               |
| UCP-45307            | The affinity context is invalid. It must be an `OracleConnectionAffinityContext`                                                                                      |
| UCP-45308            | Exception occurred while enabling failover with remote ONS subscription                                                                                               |
| UCP-45350            | Universal Connection Pool already exists in the Universal Connection Pool Manager. Universal Connection Pool cannot be added to the Universal Connection Pool Manager |
| UCP-45351            | Universal Connection Pool not found in Universal Connection Pool Manager. Register the Universal Connection Pool with Universal Connection Pool Manager               |
| UCP-45352            | Cannot get Universal Connection Pool Manager instance                                                                                                                 |
| UCP-45353            | Cannot get Universal Connection Pool Manager MBean instance                                                                                                           |
| UCP-45354            | MBean `ObjectName` is not in the right format. Use the right format to construct `ObjectName` for MBean                                                               |
| UCP-45355            | MBean exception occurred while registering or unregistering the MBean                                                                                                 |
| UCP-45356            | MBean already exits in the MBeanServer. Use a different name to register MBean                                                                                        |
| UCP-45357            | Exception occurred when trying to register an object in the MBean server that is not a JMX compliant MBean                                                            |
| UCP-45358            | The specified MBean does not exist in the repository                                                                                                                  |
| UCP-45359            | Invalid target object type is specified. Check the managed resource                                                                                                   |
| UCP-45360            | Invalid MBean Descriptor is specified. Check the Universal Connection Pool Manager MBean Descriptor                                                                   |
| UCP-45361            | Runtime exception occurred while building MBeanInfo for Universal Connection Pool Manager MBean                                                                       |
| UCP-45362            | Runtime exception occurred while building constructors information for Universal Connection Pool Manager MBean                                                        |
| UCP-45363            | Runtime exception occurred while building attributes information for Universal Connection Pool Manager MBean                                                          |
| UCP-45364            | Runtime exception occurred while building operations information for Universal Connection Pool Manager MBean                                                          |
| UCP-45365            | Universal Connection Pool must be an instance of `ConnectionConnectionPool` or `OracleConnectionConnectionPool`                                                       |
| UCP-45366            | Invalid MBean Descriptor is specified. Check the JDBC Universal Connection Pool MBean Descriptor                                                                      |
| UCP-45367            | Runtime exception occurred while building `MBeanInfo` for JDBC Universal Connection Pool MBean                                                                        |
| UCP-45368            | Runtime exception occurred while building constructors information for JDBC Universal Connection Pool MBean                                                           |
| UCP-45369            | Runtime exception occurred while building attributes information for JDBC Universal Connection Pool MBean                                                             |
| UCP-45370            | Runtime exception occurred while building operations information for JDBC Universal Connection Pool MBean                                                             |
| UCP-45371            | Runtime exception occurred while building attributes information for Universal Connection Pool MBean                                                                  |
| UCP-45372            | Runtime exception occurred while building operations information for Universal Connection Pool MBean                                                                  |
| UCP-45373            | Invalid MBean Descriptor is specified. Check the Universal Connection Pool MBean Descriptor                                                                           |
| UCP-45374            | Runtime exception occurred while building `MBeanInfo` for Universal Connection Pool MBean                                                                             |
| UCP-45375            | Cannot stop the UCP metric collection. Exception occurred while trying to stop the metric collection or while destroying the nouns or sensors.                        |
| UCP-45376            | Metrics update timer task scheduling failed                                                                                                                           |
| UCP-45377            | Problem occurred while updating UCP metric sensors                                                                                                                    |
| UCP-45378            | Universal Connection Pool is not an instance of `OracleJDBCConnectionPool` and cannot access `ONSConfiguration` property                                              |
| UCP-45379            | Cannot set the connection pool name in Universal Connection Pool MBean. Check the connection pool name to avoid duplicates                                            |
| UCP-45380            | MBean object is null                                                                                                                                                  |
| UCP-45381            | MBean object name is null                                                                                                                                             |
| UCP-45382            | MBean display name is null                                                                                                                                            |
| UCP-45383            | Invalid adapter for pool creation in Universal Connection Pool Manager                                                                                                |
| UCP-45384            | Invalid adapter for pool creation in Universal Connection Pool Manager MBean                                                                                          |
| UCP-45385            | Error during pool creation in Universal Connection Pool Manager                                                                                                       |
| UCP-45386            | Error during pool creation in Universal Connection Pool Manager MBean                                                                                                 |
| UCP-45401            | Waiting threads LO watermark cannot be negative                                                                                                                       |
| UCP-45402            | Waiting threads HI watermark cannot be negative                                                                                                                       |
| UCP-45403            | Total worker threads limit cannot be negative                                                                                                                         |
| UCP-45404            | Queue poll timeout cannot be negative                                                                                                                                 |
| UCP-45405            | The waiting threads HI watermark cannot be lower than the LO watermark                                                                                                |
| UCP-45406            | The limit of total worker threads cannot be higher than the limit of waiting threads                                                                                  |
| UCP-45407            | The error number is out of range                                                                                                                                      |
| UCP-45408            | Invalid operation because the logger is null                                                                                                                          |

### A.3 JDBC Data Sources and Dynamic Proxies Error Messages

This section lists UCP error messages for JDBC data sources and dynamic proxies error messages.

Table A-2 JDBC Data Sources and Dynamic Proxies Error Messages

| Error Message Number | Message                                                                                          |
|:---------------------|:-------------------------------------------------------------------------------------------------|
| SQL-0                | Unable to start the Universal Connection Pool                                                    |
| SQL-1                | Unable to build the Universal Connection Pool                                                    |
| SQL-2                | Invalid minimum pool size                                                                        |
| SQL-3                | Invalid maximum pool size                                                                        |
| SQL-4                | Invalid inactive connection timeout                                                              |
| SQL-5                | Invalid connection wait timeout                                                                  |
| SQL-6                | Invalid time-to-live connection timeout                                                          |
| SQL-7                | Invalid abandoned connection timeout                                                             |
| SQL-8                | Invalid timeout check interval                                                                   |
| SQL-9                | Failed to enable Failover                                                                        |
| SQL-10               | Failed to set the `maxStatements` value                                                          |
| SQL-11               | Failed to set the SQL string for validation                                                      |
| SQL-12               | Invalid connection harvest trigger count                                                         |
| SQL-13               | Invalid connection harvest max count                                                             |
| SQL-14               | Universal Connection Pool is created already. Can not create the Universal Connection Pool again |
| SQL-15               | Exception occurred while destroying the Universal Connection Pool                                |
| SQL-16               | Operation only applies to Oracle connection pools                                                |
| SQL-17               | Exception occurred while setting ONS configuration string                                        |
| SQL-18               | Failed to register labeling callback                                                             |
| SQL-19               | Failed to remove labeling callback                                                               |
| SQL-20               | Failed to register affinity callback                                                             |
| SQL-21               | Failed to remove affinity callback                                                               |
| SQL-22               | Invalid Universal Connection Pool configuration                                                  |
| SQL-23               | Unable to create factory class instance with provided factory class name                         |
| SQL-24               | Unable to set the User                                                                           |
| SQL-25               | Unable to set the Password                                                                       |
| SQL-26               | Unable to set the URL                                                                            |
| SQL-27               | The factory class must be an instance of `DataSource`                                            |
| SQL-28               | Cannot create connections. There are no available connections                                    |
| SQL-29               | Exception occurred while getting connection                                                      |
| SQL-30               | Universal Connection Pool is not started                                                         |
| SQL-31               | The connection is closed                                                                         |
| SQL-32               | Error occurred when applying label                                                               |
| SQL-33               | Error occurred when removing the connection label                                                |
| SQL-34               | Error occurred when getting labels                                                               |
| SQL-35               | Error occurred when getting unmatched labels                                                     |
| SQL-36               | Error occurred when setting connection harvestable                                               |
| SQL-37               | Error occurred when registering harvesting callback                                              |
| SQL-38               | Error occurred when removing harvesting callback                                                 |
| SQL-39               | Error occurred when registering abandoned-connection callback                                    |
| SQL-40               | Error occurred when removing abandoned-connection callback                                       |
| SQL-41               | Error occurred when registering time-to-live-connection callback                                 |
| SQL-42               | Error occurred when removing time-to-live-connection callback                                    |
| SQL-43               | The result set is closed                                                                         |
| SQL-44               | The statement is closed                                                                          |
| SQL-45               | Cannot set the connection pool name. Check the connection pool name to avoid duplicates          |
| SQL-46               | The SQL string is null                                                                           |
| SQL-47               | Error occurred when setting connection to be invalid                                             |
| SQL-48               | Unable to set the Connection properties                                                          |
| SQL-49               | Unable to set the Database server name                                                           |
| SQL-50               | Unable to set the Database port number                                                           |
| SQL-51               | Unable to set the Database name                                                                  |
| SQL-52               | Unable to set the data source name                                                               |
| SQL-53               | Unable to set the data source description                                                        |
| SQL-54               | Unable to set the data source network protocol                                                   |
| SQL-55               | Unable to set the data source role name                                                          |
| SQL-56               | Invalid max connection reuse time                                                                |
| SQL-57               | Invalid max connection reuse count                                                               |
| SQL-58               | The method is disabled                                                                           |
| SQL-59               | Unable to set the connection factory properties                                                  |
