A  B  C  D  E  F  G  H  I  J  L  M  O  P  R  S  T  U  V  W  X  

------------------------------------------------------------------------

## A

- abandon connection timeout property [4.4.3](stale-ucp-connections.md)
- AbandonedConnectionTimeoutCallback [6.1](controlling-reclaimable-connection-behavior.md)
- admin package [2.3](get-started.md)
- affinity
  - transaction-based [9.4.1.1](connection-affinity.md)
  - web session [9.4.1](connection-affinity.md)
- API overview [2.3](get-started.md)
- application continuity
  - connection initialization callback [10.4](application-continuity-using-ucp.md)
  - connection labeling [10.3](application-continuity-using-ucp.md)
  - data source configuration [10.2](application-continuity-using-ucp.md)
- Application Continuity [10.1](application-continuity-using-ucp.md)
- applyConnectionLabel [5.4](applying-connection-labels.md)
- applying connection labels [5.4](applying-connection-labels.md)

------------------------------------------------------------------------

## B

- basic connection example [2.4](get-started.md)
- benefits of connection pools [1.2](intro.md)
- benefits of FCF [9.2.1](fast-connection-failover.md)
- benefits of run-time connection load balancing [9.3.1](run-time-connection-load-balancing.md)
- borrowing connections
  - basic steps [2.2](get-started.md)
  - conceptual architecture [1.3.1](intro.md)
  - labeled [5.5](borrowing-labeled-connections.md)
  - overview [3.1.1](borrowing-ucp-connections.md)
  - using JNDI [3.1.5](borrowing-ucp-connections.md)
  - using the pool-enabled data source [3.1.2](borrowing-ucp-connections.md)
  - using the pool-enabled XA data source [3.1.3](borrowing-ucp-connections.md)

------------------------------------------------------------------------

## C

- caching statements [4.6.1](caching-sql-statements.md)
- callback
  - connection affinity [9.4.2.1](connection-affinity.md)
  - labeling [5.2.1](implementing-labeling-ucp-connections.md)
- checking unmatched labels [5.6](checking-unmatched-labels.md)
- closing connections [3.4](returning-borrowed-connections.md)
- conceptual architecture [1.3.1](intro.md)
- configure method [5.2.2](implementing-labeling-ucp-connections.md)
- Configuring ONS [9.2.6](fast-connection-failover.md)
  - client-side daemon configuration [9.2.6.3](fast-connection-failover.md)
  - Remote Configuration [9.2.6.2](fast-connection-failover.md)
- connection affinity
  - create callback [9.4.2.1](connection-affinity.md)
  - overview [9.4.1](connection-affinity.md)
  - register callback [9.4.2.2](connection-affinity.md)
  - remove callback [9.4.2.3](connection-affinity.md)
  - setting up [9.4.2](connection-affinity.md)
  - statistics [12.3.3](viewing-Oracle-RAC-statistics.md)
  - transaction-based [9.4.1.1](connection-affinity.md)
  - web session [9.4.1](connection-affinity.md)
- ConnectionAffinityCallback interface [9.4.2.1](connection-affinity.md)
- connection factory [2.2](get-started.md)
  - conceptual architecture [1.3.1](intro.md)
  - requirements [2.1](get-started.md)
  - setting [3.1.2](borrowing-ucp-connections.md), [3.1.3](borrowing-ucp-connections.md)
- ConnectionLabelingCallback interface [5.1](overview-labeling-ucp-connections.md), [5.2.2](implementing-labeling-ucp-connections.md)
- connection labels
  - apply [5.4](applying-connection-labels.md)
  - check unmatched [5.6](checking-unmatched-labels.md)
  - implement callback [5.2.1](implementing-labeling-ucp-connections.md)
  - overview [5.1](overview-labeling-ucp-connections.md)
  - removing [5.7](removing-connection-labels.md)
- Connection object [1.3.1](intro.md)
- connection pool
  - benefits [1.2](intro.md)
  - create explicitly [7.1.3.1](overview-using-ucp-manager.md)
  - create implicitly [2.2](get-started.md), [3.1.1](borrowing-ucp-connections.md)
  - destroy [7.1.3.4](overview-using-ucp-manager.md)
  - general overview [1.1](intro.md)
  - maintenance [7.1.4](overview-using-ucp-manager.md)
  - purge [7.1.4.3](overview-using-ucp-manager.md)
  - recycle [7.1.4.2](overview-using-ucp-manager.md)
  - refresh [7.1.4.1](overview-using-ucp-manager.md)
  - remove connection from [3.5](removing-connections.md)
  - start [7.1.3.2](overview-using-ucp-manager.md)
  - stop [7.1.3.3](overview-using-ucp-manager.md)
  - understanding lifecycle [7.1.3](overview-using-ucp-manager.md)
- connection pool manager
  - create [7.1.2](overview-using-ucp-manager.md)
  - create pool explicitly [7.1.3.1](overview-using-ucp-manager.md)
  - destroy pool [7.1.3.4](overview-using-ucp-manager.md)
  - overview [1.3.3](intro.md), [7.1.1](overview-using-ucp-manager.md)
  - purge pool [7.1.4.3](overview-using-ucp-manager.md)
  - recycle pool [7.1.4.2](overview-using-ucp-manager.md)
  - refresh pool [7.1.4.1](overview-using-ucp-manager.md)
  - start pool [7.1.3.2](overview-using-ucp-manager.md)
  - stop pool [7.1.3.3](overview-using-ucp-manager.md)
- connection pool properties
  - abandon connection timeout [4.4.3](stale-ucp-connections.md)
  - connection wait timeout [4.4.5](stale-ucp-connections.md)
  - harvest maximum count [4.5.4](harvesting-connections.md)
  - harvest trigger count [4.5.3](harvesting-connections.md)
  - inactive connection timeout [4.4.6](stale-ucp-connections.md)
  - initial pool size [4.2.1](controlling-pool-size.md)
  - maximum connection reuse count [4.4.1.2](stale-ucp-connections.md)
  - maximum connection reuse time [4.4.1.1](stale-ucp-connections.md)
  - maximum pool size [4.2.3](controlling-pool-size.md)
  - maximum statements [4.6.2](caching-sql-statements.md)
  - minimum pool size [4.2.2](controlling-pool-size.md)
  - optimizing [4.1](optimizing-connection-pools.md)
  - overview [1.3.2](intro.md)
  - setting [3.2](setting-ucp-properties.md), [4.1](optimizing-connection-pools.md)
  - timeout check interval [4.4.8](stale-ucp-connections.md)
  - time-to-live connection timeout [4.4.4](stale-ucp-connections.md)
  - validate on borrow [3.3.1](validating-ucp-connections.md)
- connection properties [3.1.4](borrowing-ucp-connections.md)
- connection reuse properties, setting [4.4.1](stale-ucp-connections.md)
- connections
  - basic steps [2.2](get-started.md)
  - borrowing [3.1.1](borrowing-ucp-connections.md)
  - borrowing labeled [5.5](borrowing-labeled-connections.md)
  - borrowing using JNDI [3.1.5](borrowing-ucp-connections.md)
  - checking if valid [3.3.3](validating-ucp-connections.md)
  - closing [3.4](returning-borrowed-connections.md)
  - controlling stale [4.4](stale-ucp-connections.md)
  - harvesting [4.5](harvesting-connections.md)
  - labeling [5.1](overview-labeling-ucp-connections.md)
  - removing from the pool [3.5](removing-connections.md)
  - run-time load balancing [9.3.1](run-time-connection-load-balancing.md)
  - using affinity [9.4.1](connection-affinity.md)
  - validate on borrow [3.3.1](validating-ucp-connections.md)
- connection steps, basic [2.2](get-started.md)
  - example [2.4](get-started.md)
- connection URL [9.2.7](fast-connection-failover.md)
- connection wait timeout property [4.4.5](stale-ucp-connections.md)
- cost method [5.2.2](implementing-labeling-ucp-connections.md)
- create connection pool
  - explicit [7.1.3.1](overview-using-ucp-manager.md)
  - implicit [2.2](get-started.md)

------------------------------------------------------------------------

## D

- database requirements [2.1](get-started.md)
- data source
  - PoolDataSource [1.3.1](intro.md), [3.1.2](borrowing-ucp-connections.md)
  - PoolXADataSource [1.3.1](intro.md), [3.1.3](borrowing-ucp-connections.md)
- destroyConnectionPool [7.1.3.4](overview-using-ucp-manager.md)
- destroying a connection pool [7.1.3.4](overview-using-ucp-manager.md)

------------------------------------------------------------------------

## E

- enable FCF property [9.2.5](fast-connection-failover.md)
- errors
  - connection pool layer messages [A.2](error-codes-reference.md)
  - general UCP message structure [A.1](error-codes-reference.md)
  - JDBC data sources and dynamic proxies messages [A.3](error-codes-reference.md)
- example
  - basic connection [2.4](get-started.md)
  - connection affinity callback [9.4.2.1](connection-affinity.md)
  - FCF [9.2.4](fast-connection-failover.md)
  - labeling callback [5.2.2.1](implementing-labeling-ucp-connections.md)

------------------------------------------------------------------------

## F

- fast connection failover
  - prerequisites [9.2.3](fast-connection-failover.md)
- Fast Connection Failover
  - See: FCF
- FCF
  - configure connection URL [9.2.7](fast-connection-failover.md)
  - configure ONS [9.2.6](fast-connection-failover.md)
  - enable [9.2.5](fast-connection-failover.md)
  - example [9.2.4](fast-connection-failover.md)
  - statistics [12.3.1](viewing-Oracle-RAC-statistics.md)

------------------------------------------------------------------------

## G

- GDS [9.5](global-data-services.md)
- getAffinityPolicy [9.4.2.1](connection-affinity.md)
- getConnection methods [3.1.2](borrowing-ucp-connections.md), [5.5](borrowing-labeled-connections.md)
- getPoolDataSource [3.1.2](borrowing-ucp-connections.md)
- getPoolXADataSource [3.1.3](borrowing-ucp-connections.md)
- getStatistics [12.3](viewing-Oracle-RAC-statistics.md)
- getting a connection [3.1.2](borrowing-ucp-connections.md)
- getting an XA connection [3.1.3](borrowing-ucp-connections.md)
- getUniversalConnectionPoolManager [7.1.2](overview-using-ucp-manager.md)
- getUnmatchedConnectionLabels [5.6](checking-unmatched-labels.md)
- getXAConnection methods [3.1.3](borrowing-ucp-connections.md)
- Global Data Services [9.5](global-data-services.md)

------------------------------------------------------------------------

## H

- HarvestableConnection interface [4.5.2](harvesting-connections.md)
- harvest connections [4.5](harvesting-connections.md)
- harvest maximum count property [4.5.4](harvesting-connections.md)
- harvest trigger count property [4.5.3](harvesting-connections.md)
- high availability [1.3.4](intro.md), [9.1](overview-Oracle-RAC-features.md)

------------------------------------------------------------------------

## I

- inactive connection timeout property [4.4.6](stale-ucp-connections.md)
- initial pool size property [4.2.1](controlling-pool-size.md)
- integration
  - third-party [3.6](third-party-integration.md)
- isValid [3.3.3](validating-ucp-connections.md)

------------------------------------------------------------------------

## J

- JDBC connection pool
  - See: UCP
- JDBC driver
  - connection properties [3.1.4](borrowing-ucp-connections.md)
  - requirements [2.1](get-started.md)
- jdbc package [2.3](get-started.md)
- JNDI [3.1.5](borrowing-ucp-connections.md)
- JRE requirements [2.1](get-started.md)

------------------------------------------------------------------------

## L

- LabelableConnection interface [5.1](overview-labeling-ucp-connections.md), [5.4](applying-connection-labels.md)
- labeled connections
  - apply label [5.4](applying-connection-labels.md)
  - borrowing [5.5](borrowing-labeled-connections.md)
  - check unmatched [5.6](checking-unmatched-labels.md)
  - implement callback [5.2.1](implementing-labeling-ucp-connections.md)
  - overview [5.1](overview-labeling-ucp-connections.md)
  - remove label [5.7](removing-connection-labels.md)
- labeling callback
  - create [5.2.2](implementing-labeling-ucp-connections.md)
  - example [5.2.2.1](implementing-labeling-ucp-connections.md)
  - register [5.2.3](implementing-labeling-ucp-connections.md)
  - removing [5.2.4](implementing-labeling-ucp-connections.md)
  - run-time algorithm [5.2.2](implementing-labeling-ucp-connections.md)
- lifecycle of connection pools [7.1.3](overview-using-ucp-manager.md)
- lifecycle states [7.1.3](overview-using-ucp-manager.md)
- Load Balance Advisory [9.3.1](run-time-connection-load-balancing.md)
- load balancing [9.2.7](fast-connection-failover.md), [9.3.1](run-time-connection-load-balancing.md)
- logging [12.4](logging-in-ucp.md)
- logging configuration
  - programmatically [12.4.2](logging-in-ucp.md)
  - properties file [12.4.1](logging-in-ucp.md)
- logging levels [12.4.5](logging-in-ucp.md)

------------------------------------------------------------------------

## M

- manager, connection pool [7.1.1](overview-using-ucp-manager.md)
- maximum connection reuse count property [4.4.1.2](stale-ucp-connections.md)
- maximum connection reuse time property [4.4.1.1](stale-ucp-connections.md)
- maximum pool size property [4.2.3](controlling-pool-size.md)
- maximum statements property [4.6.2](caching-sql-statements.md)
- method [3.1.3](borrowing-ucp-connections.md)
- minimum pool size property [4.2.2](controlling-pool-size.md)

------------------------------------------------------------------------

## O

- ONS [9.2.6](fast-connection-failover.md)
- ons.config file [9.2.6](fast-connection-failover.md)
- optimizing a connection pool [4.1](optimizing-connection-pools.md)
- Oracle Client software [9.2.6](fast-connection-failover.md)
- Oracle Client software requirements [2.1](get-started.md)
- Oracle Notification Service
  - See: ONS
- Oracle RAC
  - connection affinity [9.4.1](connection-affinity.md)
  - features overview [9.1](overview-Oracle-RAC-features.md)
  - run-time connection load balancing [9.3.1](run-time-connection-load-balancing.md)
  - statistics [12.3](viewing-Oracle-RAC-statistics.md)
- Oracle RAC Load Balance Advisory [9.3.1](run-time-connection-load-balancing.md)
- overview
  - API [2.3](get-started.md)
  - connection pool manager [7.1.1](overview-using-ucp-manager.md)
  - connection pool properties [4.1](optimizing-connection-pools.md)
  - connection pools, general [1.1](intro.md)
  - connection steps [2.2](get-started.md)
  - high availability and performance features [1.3.4](intro.md)
  - labeling connections [5.1](overview-labeling-ucp-connections.md)
  - Oracle RAC features [9.1](overview-Oracle-RAC-features.md)
  - UCP [1.3](intro.md)

------------------------------------------------------------------------

## P

- password [2.2](get-started.md), [3.1.2](borrowing-ucp-connections.md), [3.1.3](borrowing-ucp-connections.md)
- PoolDataSourceFactory class [3.1.2](borrowing-ucp-connections.md), [3.1.3](borrowing-ucp-connections.md)
- PoolDataSourceImpl [3.6](third-party-integration.md)
- PoolDataSource interface [1.3.1](intro.md), [3.1.2](borrowing-ucp-connections.md)
- pool-enabled data source
  - create instance [3.1.2](borrowing-ucp-connections.md)
- pool-enabled XA data source
  - create instance [3.1.3](borrowing-ucp-connections.md)
- pool manager
  - See: connection pool manager
- pool properties
  - See: connection pool properties
- pool size, controlling
  - initial size [4.2.1](controlling-pool-size.md)
  - maximum [4.2.3](controlling-pool-size.md)
  - minimum [4.2.2](controlling-pool-size.md)
- PoolXADataSourceImpl [3.6](third-party-integration.md)
- PoolXADataSource interface [1.3.1](intro.md), [3.1.3](borrowing-ucp-connections.md)
- purgeConnectionPool [7.1.4.3](overview-using-ucp-manager.md)
- purging a connection pool [7.1.4.3](overview-using-ucp-manager.md)

------------------------------------------------------------------------

## R

- Real Application Clusters
  - See Oracle RAC [1.3](intro.md)
- recycleConnectionPool [7.1.4.2](overview-using-ucp-manager.md)
- recycling a connection pool [7.1.4.2](overview-using-ucp-manager.md)
- refreshConnectionPool [7.1.4.1](overview-using-ucp-manager.md)
- refreshing a connection pool [7.1.4.1](overview-using-ucp-manager.md)
- registerConnectionAffinityCallback [9.4.2.2](connection-affinity.md)
- registerConnectionLabelingCallback [5.2.3](implementing-labeling-ucp-connections.md)
- removeConnectionAffinityCallback [9.4.2.3](connection-affinity.md)
- removeConnectionLabel [5.7](removing-connection-labels.md)
- removeConnectionLabelingCallback [5.2.4](implementing-labeling-ucp-connections.md)
- removing connection labels [5.7](removing-connection-labels.md)
- removing connections from the pool [3.5](removing-connections.md)
- reuse properites
  - maximum count [4.4.1.2](stale-ucp-connections.md)
- reuse properties
  - maximum time [4.4.1.1](stale-ucp-connections.md)
- run-time connection load balancing
  - overview [9.3.1](run-time-connection-load-balancing.md)
  - setting up [9.3.2](run-time-connection-load-balancing.md)
  - statistics [12.3.2](viewing-Oracle-RAC-statistics.md)

------------------------------------------------------------------------

## S

- SERVICE_TIME [9.3.2](run-time-connection-load-balancing.md)
- setAbandonedConnectionTimeout [4.4.3](stale-ucp-connections.md)
- setAffinityPolicy [9.4.2.1](connection-affinity.md)
- setConnectionAffinityContext [9.4.2.1](connection-affinity.md)
- setConnectionFactoryClassName [3.1.2](borrowing-ucp-connections.md), [3.1.3](borrowing-ucp-connections.md)
- setConnectionHarvestable [4.5.2](harvesting-connections.md)
- setConnectionHarvestMaxCount [4.5.4](harvesting-connections.md)
- setConnectionHarvestTriggerCount [4.5.3](harvesting-connections.md)
- setConnectionProperties [3.1.4](borrowing-ucp-connections.md)
- setConnectionWaitTimeout [4.4.5](stale-ucp-connections.md)
- setFastConnectionFailoverEnabled [9.2.5](fast-connection-failover.md)
- setInactiveConnectionTimeout [4.4.6](stale-ucp-connections.md)
- setInitialPoolSize [4.2.1](controlling-pool-size.md)
- setInvalid [3.3.3](validating-ucp-connections.md), [3.5](removing-connections.md)
- setMaxConnectionReuseCount [4.4.1.2](stale-ucp-connections.md)
- setMaxConnectionReuseTime [4.4.1.1](stale-ucp-connections.md)
- setMaxPoolSize [4.2.3](controlling-pool-size.md)
- setMaxStatements [4.6.2](caching-sql-statements.md)
- setMinPoolSize [4.2.2](controlling-pool-size.md)
- setONSConfiguration [9.2.6](fast-connection-failover.md)
- setPassword [3.1.2](borrowing-ucp-connections.md), [3.1.3](borrowing-ucp-connections.md)
- setSQLForValidateConnection [3.3.1](validating-ucp-connections.md)
- setTimeoutCheckInterval [4.4.8](stale-ucp-connections.md)
- setTimeToLiveConnectionTimeout [4.4.4](stale-ucp-connections.md)
- setURL [3.1.2](borrowing-ucp-connections.md), [3.1.3](borrowing-ucp-connections.md)
- setUser [3.1.2](borrowing-ucp-connections.md), [3.1.3](borrowing-ucp-connections.md)
- setValidateConnectionOnBorrow [3.3.1](validating-ucp-connections.md)
- SHORT [9.3.2](run-time-connection-load-balancing.md)
- SQL statement caching [4.6.1](caching-sql-statements.md)
- stale connections [4.4](stale-ucp-connections.md)
- startConnectionPool [7.1.3.2](overview-using-ucp-manager.md)
- starting a connection pool [7.1.3.2](overview-using-ucp-manager.md)
- statement caching [4.6.1](caching-sql-statements.md)
- statistics
  - connection affinity [12.3.3](viewing-Oracle-RAC-statistics.md)
  - FCF [12.3.1](viewing-Oracle-RAC-statistics.md)
  - Oracle RAC [12.3](viewing-Oracle-RAC-statistics.md)
  - run-time connection load balancing [12.3.2](viewing-Oracle-RAC-statistics.md)
- stopConnectionPool [7.1.3.3](overview-using-ucp-manager.md)
- stopping a connection pool [7.1.3.3](overview-using-ucp-manager.md)

------------------------------------------------------------------------

## T

- third-party integration [3.6](third-party-integration.md)
- THROUGHPUT [9.3.2](run-time-connection-load-balancing.md)
- timeout check interval property [4.4.8](stale-ucp-connections.md)
- timeout properties
  - abandon [4.4.3](stale-ucp-connections.md)
  - check interval [4.4.8](stale-ucp-connections.md)
  - inactive [4.4.6](stale-ucp-connections.md)
  - time-to-live [4.4.4](stale-ucp-connections.md)
  - wait [4.4.5](stale-ucp-connections.md)
- TimeToLiveConnectionTimeoutCallback [6.2](controlling-reclaimable-connection-behavior.md)
- time-to-live connection timeout property [4.4.4](stale-ucp-connections.md)
- transaction-based affinity [9.4.1.1](connection-affinity.md)

------------------------------------------------------------------------

## U

- UCP
  - API overview [2.3](get-started.md)
  - basic connection steps [2.2](get-started.md)
  - conceptual architecture [1.3.1](intro.md)
  - Oracle RAC features [9.1](overview-Oracle-RAC-features.md)
  - overview [1.3](intro.md)
  - software requirements [2.1](get-started.md)
- UCP for JDBC
  - connection pool properties [3.2](setting-ucp-properties.md), [4.1](optimizing-connection-pools.md)
- UCP manager
  - See: connection pool manager
- ucp package [2.3](get-started.md)
- universal connection pool
  - See: UCP
- UniversalConnectionPoolManagerImpl [7.1.2](overview-using-ucp-manager.md)
- UniversalConnectionPoolManager interface [7.1.2](overview-using-ucp-manager.md)
- unmatched labels [5.6](checking-unmatched-labels.md)
- URL [2.2](get-started.md), [3.1.2](borrowing-ucp-connections.md), [3.1.3](borrowing-ucp-connections.md), [9.2.7](fast-connection-failover.md)
- username [2.2](get-started.md), [3.1.2](borrowing-ucp-connections.md), [3.1.3](borrowing-ucp-connections.md)

------------------------------------------------------------------------

## V

- validate connections
  - on borrow [3.3.1](validating-ucp-connections.md)
  - programmatically [3.3.3](validating-ucp-connections.md)
- ValidConnection interface [3.3.3](validating-ucp-connections.md), [3.5](removing-connections.md)

------------------------------------------------------------------------

## W

- web session affinity [9.4.1](connection-affinity.md)

------------------------------------------------------------------------

## X

- XAConnection object [1.3.1](intro.md)
- XA connections [1.3.1](intro.md), [3.1.3](borrowing-ucp-connections.md)
