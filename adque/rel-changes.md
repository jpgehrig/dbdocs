This preface contains:

- Changes in Oracle Database Advanced Queuing Release 19c, Version 19.2

- Changes in Oracle Database Advanced Queuing 12c Release 2 (12.2)

- Changes in Oracle Database Advanced Queuing 12c Release 1 (12.1.0.2)

- Changes in Oracle Database Advanced Queuing 12c Release 1 (12.1)

### Changes in Oracle Database Advanced Queuing Release 19c, Version 19.2

The following are changes in Oracle Database Advanced Queuing User's Guide for Oracle Database Release 19c, Version 19.2

#### New Features

The following feature is new in this release:

- Enhanced Key-based Messaging

  AQ sharded queues perform substantially better when compared to AQ classic (non-sharded) queues. This is achieved by sharding the queue, where each shard is owned by a specific instance of the database. By default, sharding is completely transparent to the user when it comes to enqueue and dequeue operations. AQ internally puts the message in the appropriate shard to get maximum performance and session level ordering as required by the JMS specification. Session level ordering ensures that no two messages will be dequeued in the reverse order of their enqueue order if both the messages are enqueued by the same session and have the same priority and delivery mode.

  In some cases, user applications want to control the sharding. The user application can choose the shard where a message is enqueued. The users can decide the way they plan to shard their messages in the sharded queue to support the application logic as needed. The performance and ordering benefits of AQ sharded queues are still maintained even if the sharding is under control of the user. Applications can control the following:

  - The number of shards of the queue

  - Key based enqueues: The enqueue session can choose the shard of the queue where the message will be enqueued by providing a key with the message at the time of enqueue. AQ server ensures that all the messages of a key are enqueued in the same shard. A shard can have messages of different keys.

  - Sticky dequeues: A shard can have only one active dequeue session for a single-consumer queue or JMS Queue. Similarly, a shard can have only one dequeue session per subscriber for a multi-consumer queue or JMS Topic. That dequeue session will stick to that shard of the queue for the session’s lifetime. Such functionality is also available for JMS listeners.

**See Also:**

[User Sharding](aq-performance-scalability.md)

#### Desupported Features

The following feature is desupported in this release:

- Desupport of Oracle Streams

  Starting in Oracle Database 19c, the Oracle Streams feature is desupported. Use Oracle GoldenGate to replace all replication features of Oracle Streams.

### Changes in Oracle Database Advanced Queuing 12c Release 2 (12.2.)

The following are changes in Oracle Database Advanced Queuing User's Guide for Oracle Database 12c Release 2 (12.2).

#### New Features

The following features are new in this release:

- PL/SQL enqueue and dequeue support for JMS and non-JMS (ADT or RAW) payload in Sharded Queues

  Oracle Database 12c Release 2 (12.2) extends and supports PL/SQL APIs to perform enqueue and dequeue operations for JMS, ADT, and RAW payload in sharded queues. The PL/SQL Array APIs also support sharded queues. Many existing non-JMS applications can now use sharded queues with little or no change.

  Starting from Oracle Database 12c Release 2 (12.2), JMS customers using sharded queues can make use of PL/SQL notification to register a PL/SQL procedure that gets automatically invoked by AQ Server on successful enqueue. PL/SQL notification can eliminate the need for clients to poll the queue for messages because messages can be automatically dequeued and processed at the server.

  See [Managing Sharded Queues](aq-administrative-interface.md) for more information.

- Sharded Queue Diagnosability and Manageability

  Starting from 12c Release 2 (12.2), AQ sharded queues provides an advisor, views, and automated management for its message cache to optimize `STREAMS_POOL` memory allocation and throughput.

  See [Sharded Queues Tuning](aq-performance-scalability.md) for more information.

- Longer Identifiers for Oracle Database Advanced Queuing

  Starting from 12c Release 2 (12.2), the maximum length of AQ queue names has been increased to 122 bytes. The maximum length of subscriber and recipient names is increased to 128 characters. For the AQ Rules Engine, the maximum length of rule names and rule set names is now 128 bytes.

### Changes in Oracle Database Advanced Queuing 12c Release 1 (12.1.0.2)

The following are changes in Oracle Database Advanced Queuing User's Guide for Oracle Database 12c Release 1 (12.1.0.2).

#### New Features

The following feature is new in this release:

- JMS Streaming

  In Oracle Database 12c Release 1 (12.1.0.2), Advanced Queuing introduces JMS Streaming with enqueue and dequeue for sharded queues through `AQjmsBytesMessage` and `AQjmsStreamMessage`, for the applications interested in sending and receiving large message data or payload.

  See "[JMS Streaming](jms-introduction.md)" for more information.

### Changes in Oracle Database Advanced Queuing 12c Release 1 (12.1)

The following are changes in Oracle Database Advanced Queuing User's Guide for Oracle Database 12c Release 1 (12.1).

#### New Features

The following features are new in this release:

- JMS Sharded Queues

  In Oracle Database 12c Release 1 (12.1), Advanced Queuing introduces high performing and scalable sharded JMS Queues. A sharded queue is a single logical queue that is divided into multiple, independent, physical queues through system-maintained partitioning. A [sharded queue](glossary.md) increases enqueue-dequeue throughput, especially across Oracle RAC instances, because ordering between two messages on different queue shards is best effort. Each shard is ordered based on enqueue time within a session. Sharded queues automatically manage table partitions so that enqueuers and dequeuers do not contend among themselves. In addition, sharded queues use an in-memory message cache to optimize performance and reduce the disk and CPU overhead of AQ-JMS enqueues and dequeues. Sharded queues are the preferred JMS queues for queues used across Oracle RAC instances, for queues with high enqueue or dequeue rates, or for queues with many subscribers.

  In 12.2, Sharded Queues have been enhanced to support more than JMS. See [Sharded Queues](aq-performance-scalability.md) for more information.

- Result Cache Enhancement

  In Oracle Database 12c Release 1 (12.1), the Rules Engine introduces a [result cache](glossary.md) to improve the performance of many commonly used rules. The result cache will bypass the evaluation phase if an expression with the same attributes has already been evaluated earlier. Not all rule results are cached, such as when rule results are potentially non-deterministic or when not all rules are evaluated or when attributes include non-scalar data types. For Advanced Queues, the cache is most useful when subscriptions and their dequeue sessions are long-lived.

- `LONG VARCHAR` Support

  The `LONG VARCHAR` data type is supported by Oracle Database Advanced Queuing in Oracle Database 12c Release 1 (12.1).

- 3-Tier Background Architecture

  Oracle Database 12c Release 1 (12.1) introduces the AQ background process architecture with a new a 3-tier design.

  See "[AQ Background Architecture](aq-basic-components.md)" for more information.

- Support for Data Guard Database Rolling Upgrade

  Databases that use Oracle Database Advanced Queuing can now be upgraded to new Oracle database releases and patch sets in rolling fashion using Data Guard database rolling upgrades (transient logical standby database only). Rolling upgrades are supported beginning in Oracle Database 12c Release 1 (12.1).

  Data Guard database rolling upgrades reduce planned downtime by enabling the upgrade to new database releases or patch sets in rolling fashion. Total database downtime for such an upgrade is limited to the small amount of time required to execute a Data Guard switchover.

  The following packages will have support for rolling upgrade using logical standby:

  - `DBMS_AQ`

  - `DBMS_AQJMS`

  - `DBMS_AQADM`, except for the following procedures:

    - `SCHECULE_PROPAGATION`

    - `UNSCHEDULE_PROPAGATION`

    - `ALTER_PROPAGATION_SCHEDULE`

    - `ENABLE_PROPAGATION_SCHEDULE`

    - `DISABLE_PROPAGATION_SCHEDULE`

  **See Also:**

  - [Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md) for more information on the Oracle Database AQ packages
