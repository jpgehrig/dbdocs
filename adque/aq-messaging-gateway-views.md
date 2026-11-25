These topics describe the Oracle Database Advanced Queuing (AQ) administrative interface views and Oracle Messaging Gateway (MGW) views.

**Note:**

All views not detailed in the following sections are described in the [Oracle Database Reference](../refrn/index.md).

### Oracle AQ Views

- V\$AQ_MESSAGE_CACHE_STAT: Memory Management for Sharded Queues

- V\$AQ_SHARDED_SUBSCRIBER_STAT: Sharded Queue Subscriber Statistics

- V\$AQ_MESSAGE_CACHE_ADVICE: Simulated Metrics

- V\$AQ_REMOTE_DEQUEUE_AFFINITY: Dequeue Affinity Instance List

- DBA_QUEUE_TABLES: All Queue Tables in Database

- USER_QUEUE_TABLES: Queue Tables in User Schema

- ALL_QUEUE_TABLES: Queue Tables Accessible to the Current User

- DBA_QUEUES: All Queues in Database

- USER_QUEUES: Queues In User Schema

- ALL_QUEUES: Queues for Which User Has Any Privilege

- DBA_QUEUE_SCHEDULES: All Propagation Schedules

- USER_QUEUE_SCHEDULES: Propagation Schedules in User Schema

- QUEUE_PRIVILEGES: Queues for Which User Has Queue Privilege

- AQ\$\<Queue_Table_Name\>: Messages in Queue Table

- AQ\$\<Queue_Table_Name_S\>: Queue Subscribers

- AQ\$\<Queue_Table_Name_R\>: Queue Subscribers and Their Rules

- DBA_QUEUE_SUBSCRIBERS: All Queue Subscribers in Database

- USER_QUEUE_SUBSCRIBERS: Queue Subscribers in User Schema

- ALL_QUEUE_SUBSCRIBERS: Subscribers for Queues Where User Has Queue Privileges

- DBA_TRANSFORMATIONS: All Transformations

- DBA_ATTRIBUTE_TRANSFORMATIONS: All Transformation Functions

- USER_TRANSFORMATIONS: User Transformations

- USER_ATTRIBUTE_TRANSFORMATIONS: User Transformation Functions

- DBA_SUBSCR_REGISTRATIONS: All Subscription Registrations

- USER_SUBSCR_REGISTRATIONS: User Subscription Registrations

- AQ\$INTERNET_USERS: Oracle Database Advanced Queuing Agents Registered for Internet Access

- V\$AQ: Number of Messages in Different States in Database

- V\$BUFFERED_QUEUES: All Buffered Queues in the Instance.

- V\$BUFFERED_SUBSCRIBERS: Subscribers for All Buffered Queues in the Instance

- V\$BUFFERED_PUBLISHERS: All Buffered Publishers in the Instance

- V\$PERSISTENT_QUEUES: All Active Persistent Queues in the Instance

- V\$PERSISTENT_SUBSCRIBERS: All Active Subscribers of the Persistent Queues in the Instance

- V\$PERSISTENT_PUBLISHERS: All Active Publishers of the Persistent Queues in the Instance

- V\$PROPAGATION_SENDER: Buffer Queue Propagation Schedules on the Sending (Source) Side

- V\$PROPAGATION_RECEIVER: Buffer Queue Propagation Schedules on the Receiving (Destination) Side

- V\$SUBSCR_REGISTRATION_STATS: Diagnosability of Notifications

- V\$METRICGROUP: Information About the Metric Group

- V\$AQ_BACKGROUND_COORDINATOR: Performance Statistics for AQ's Master Background Coordinator Process (AQPC)

- V\$AQ_JOB_COORDINATOR: Performance Statistics per Coordinator

- V\$AQ_SERVER_POOL: Performance Statistics for all Servers

- V\$AQ_CROSS_INSTANCE_JOBS: Cross Process Jobs Description

- V\$AQ_IPC_ACTIVE_MSGS

- V\$AQ_IPC_MSG_STATS

- V\$AQ_IPC_PENDING_MSGS

- V\$AQ_NONDUR_REGISTRATIONS: Non-Durable Registrations

- V\$AQ_NOTIFICATION_CLIENTS: Secure OCI Client Connections

- V\$AQ_SUBSCRIBER_LOAD: Durable Subscribers

- V\$AQ_NONDUR_SUBSCRIBER: Non-Durable Subscribers

- V\$AQ_NONDUR_SUBSCRIBER_LWM: LWM of Non Durable Subscriber

- V\$AQ_MESSAGE_CACHE: Performance Statistics

### Oracle Messaging Gateway Views

- MGW_GATEWAY: Configuration and Status Information

- MGW_AGENT_OPTIONS: Supplemental Options and Properties

- MGW_LINKS: Names and Types of Messaging System Links

- MGW_MQSERIES_LINKS: WebSphere MQ Messaging System Links

- MGW_TIBRV_LINKS: TIB/Rendezvous Messaging System Links

- MGW_FOREIGN_QUEUES: Foreign Queues

- MGW_JOBS: Messaging Gateway Propagation Jobs

- MGW_SUBSCRIBERS: Information for Subscribers

- MGW_SCHEDULES: Information About Schedules

### DBA_QUEUE_TABLES: All Queue Tables in Database

This view contains information about the owner instance for a queue table.

A queue table can contain multiple queues. In this case, each queue in a queue table has the same owner instance as the queue table. The [`DBA_QUEUE_TABLES`](../refrn/DBA_QUEUE_TABLES.md) columns are the same as those in `ALL_QUEUE_TABLES`.

**See Also:**

[Oracle Database Reference](../refrn/DBA_QUEUE_TABLES.md) for more information about `DBA_QUEUE_TABLES`.

### USER_QUEUE_TABLES: Queue Tables in User Schema

This view is the same as `DBA_QUEUE_TABLES` with the exception that it only shows queue tables in the user's schema.

[`USER_QUEUE_TABLES`](../refrn/USER_QUEUE_TABLES.md) does not contain a column for `OWNER`.

**See Also:**

[Oracle Database Reference](../refrn/USER_QUEUE_TABLES.md) for more information about `USER_QUEUE_TABLES`.

### ALL_QUEUE_TABLES: Queue Tables Accessible to the Current User

This view describes queue tables accessible to the current user.

**See Also:**

[Oracle Database Reference](../refrn/ALL_QUEUE_TABLES.md) for more information about `ALL_QUEUE_TABLES`.

### DBA_QUEUES: All Queues in Database

The `DBA_QUEUES` view specifies operational characteristics for every queue in a database.

Its columns are the same as those [`ALL_QUEUES`](../refrn/ALL_QUEUES.md). Oracle Database 12c Release 1 (12.1) introduces a new column `SHARDED` with data type `VARCHAR2(5)`. The value for this column is `TRUE` for sharded queue, otherwise `FALSE`.

**See Also:**

[Oracle Database Reference](../refrn/DBA_QUEUES.md) for more information about `DBA_QUEUES`.

### USER_QUEUES: Queues In User Schema

The `USER_QUEUES` view is the same as `DBA_QUEUES` with the exception that it only shows queues in the user's schema.

Oracle Database 12c Release 1 (12.1) introduces a new column `SHARDED` with data type `VARCHAR2(5)`. The value for this column is `TRUE` for sharded queue, otherwise `FALSE`.

**See Also:**

[Oracle Database Reference](../refrn/USER_QUEUES.md) for more information about `USER_QUEUES`.

### ALL_QUEUES: Queues for Which User Has Any Privilege

The `ALL_QUEUES` view describes all queues on which the current user has enqueue or dequeue privileges.

If the user has any Advanced Queuing system privileges, like `MANAGE` `ANY` `QUEUE`, `ENQUEUE` `ANY` `QUEUE` or `DEQUEUE` `ANY` `QUEUE`, this view describes all queues in the database. Oracle Database 12c Release 1 (12.1) introduces a new column `SHARDED` with data type `VARCHAR2(5)`. The value for this column is `TRUE` for sharded queue, otherwise `FALSE`.

**See Also:**

[Oracle Database Reference](../refrn/ALL_QUEUES.md) for more information about `ALL_QUEUES`.

### DBA_QUEUE_SCHEDULES: All Propagation Schedules

The `DBA_QUEUE_SCHEDULES` view describes all the current schedules in the database for propagating messages.

**See Also:**

[Oracle Database Reference](../refrn/DBA_QUEUE_SCHEDULES.md) for more information about `DBA_QUEUE_SCHEDULES`.

### USER_QUEUE_SCHEDULES: Propagation Schedules in User Schema

The `USER_QUEUE_SCHEDULES` view is the same as `DBA_QUEUE_SCHEDULES` with the exception that it only shows queue schedules in the user's schema.

**See Also:**

[Oracle Database Reference](../refrn/USER_QUEUE_SCHEDULES.md) for more information about `USER_QUEUE_SCHEDULES`.

### QUEUE_PRIVILEGES: Queues for Which User Has Queue Privilege

The `QUEUE_PRIVILEGES` view describes queues for which the user is the grantor, grantee, or owner.

It also shows queues for which an enabled role on the queue is granted to `PUBLIC`.

**See Also:**

[Oracle Database Reference](../refrn/QUEUE_PRIVILEGES.md) for more information about `QUEUE_PRIVILEGES`.

### AQ\$\<Queue_Table_Name\>: Messages in Queue Table

The `AQ$``<Queue_Table_Name>` view describes the queue table in which message data is stored.

This view is automatically created with each queue table and should be used for querying the queue data. The dequeue history data (time, user identification and transaction identification) is only valid for single-consumer queues.

In a queue table that is created with the `compatible` parameter set to '8.1' or higher, messages that were not dequeued by the consumer are shown as "`UNDELIVERABLE`". You can dequeue these messages by `msgid`. If the Oracle Database Advanced Queuing queue process monitor is running, then the messages are eventually moved to an exception queue. You can dequeue these messages from the exception queue with an ordinary dequeue.

A multiconsumer queue table created without the `compatible` parameter, or with the `compatible` parameter set to '8.0', does not display the state of a message on a consumer basis, but only displays the global state of the message.

**Note:**

Queues created in a queue table with `compatible` set to `8.0` (referred to in this guide as 8.0-style queues) are deprecated in Oracle Database Advanced Queuing 10g Release 2 (10.2). Oracle recommends that any new queues you create be 8.1-style or newer and that you migrate existing 8.0-style queues at your earliest convenience.

When a message is dequeued using the `REMOVE` mode, `DEQ_TIME`, `DEQ_USER_ID`, and `DEQ_TXN_ID` are updated for the consumer that dequeued the message.

You can use `MSGID` and `ORIGINAL_MSGID` to chain propagated messages. When a message with message identifier `m1` is propagated to a remote queue, `m1` is stored in the `ORIGINAL_MSGID` column of the remote queue.

Beginning with Oracle Database 10g, `AQ$``Queue_Table_Name` includes buffered messages. For buffered messages, the value of `MSG_STATE` is one of the following:

- `IN MEMORY`

  Buffered messages enqueued by a user

- `DEFERRED`

  Buffered messages enqueued by a capture process

- `SPILLED`

  User-enqueued buffered messages that have been spilled to disk

- `DEFERRED SPILLED`

  Capture-enqueued buffered messages that have been spilled to disk

- `BUFFERED EXPIRED`

  Expired buffered messages

For JMS Sharded Queues, the columns `RETRY_COUNT`, `EXCEPTION_QUEUE_OWNER`, `EXCEPTION_QUEUE`, `PROPAGATED_MSGID`, `SENDER_NAME`, `SENDER_ADDRESS`, `SENDER_PROTOCOL`, `ORIGINAL_MSGID`, `ORIGINAL_QUEUE_NAME`, `ORIGINAL_QUEUE_OWNER`, `EXPIRATION_REASON` are always `NULL`.

For JMS Sharded Queues, this view shows messages only for durable subscribers because non durable subscribers are session specific. The view returns data from the in-memory Sharded Queue message cache if available, otherwise from the values on disk. A user is required to be one of the following in order to query from `AQ$<``queue_name``>` view for Sharded Queues:

- user is the owner

- user has "dequeue" privilege on queue

- user has "dequeue any queue" privilege

The view has the following difference for Sharded Queues for 12c and future releases:

- `MSG_PRIORITY` is defined as `NUMBER(38)`

- `MSG_STATE` in a queue table does not have `BUFFERED_EXPIRED` hence the max length of `UNDELIVERABLE` is taken as length got `MSG_STATE`.

- `EXPIRATION` is defined as `TIMESTAMP(6) WITH TIME ZONE` in a queue table.

- `USER_DATA` column is defined using a decode on `USERDATA_RAW` and `USERDATA_BLOB` with `UTL_RAW.CAST_TO_VARCHAR2`.

- `CONSUMER_NAME` is defined as `VARCHAR2(128)`

Table 9-1 AQ\$\<Queue_Table_Name\> View

| Column                            | Datatype         | NULL       | For JMS Sharded Queues 12c Release 1 (12.1) | Description                                                                                                                                                                                                                                                                         |
|:----------------------------------|:-----------------|:-----------|:--------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `QUEUE`                           | `VARCHAR2(30)`   | \-         |                                             | Queue name                                                                                                                                                                                                                                                                          |
| `SHARD_ID`                        | `NUMBER`         | \-         |                                             | `N/A `for 11g                                                                                                                                                                                                                                                                       |
| `SUBSHARD_ID`                     | `NUMBER`         | \-         |                                             | `N/A `for 11g                                                                                                                                                                                                                                                                       |
| `MSG_ID`                          | `RAW(16)`        | `NOT NULL` |                                             | Unique identifier of the message                                                                                                                                                                                                                                                    |
| `CORR_ID`                         | `VARCHAR2(128)`  | \-         |                                             | User-provided correlation identifier                                                                                                                                                                                                                                                |
| `MSG_PRIORITY`                    | `NUMBER`         | \-         | `NUMBER(38)`                                | Message priority                                                                                                                                                                                                                                                                    |
| `MSG_STATE`                       | `VARCHAR2(16)`   | \-         |                                             | Message state. 12c Release 1 (12.1) queue table doesnt have `BUFFERED_EXPIRED`. Hence for 12c Release 1 (12.1) the max length of `UNDELIVERABLE` is taken as length got `MSG_STATE`                                                                                                 |
| `DELAY`                           | `DATE`           | \-         |                                             | Time in date format at which the message in waiting state would become ready. Equals `ENQUEUE_TIME` + user specified `DELAY`                                                                                                                                                        |
| `DELAY_TIMESTAMP`                 | `TIMESTAMP`      | \-         |                                             | Time as a timestamp format at which the message in waiting state would become ready. Equals `ENQUEUE_TIMESTAMP` + user specified `DELAY`                                                                                                                                            |
| `EXPIRATION`                      | `NUMBER`         | \-         | `TIMESTAMP(6) WITH TIME ZONE`               | Number of seconds in which the message expires after being `READY`                                                                                                                                                                                                                  |
| `RETENTION_TIMESTAMP`             | `TIMESTAMP(6)`   | \-         |                                             | `N/A `for 11g                                                                                                                                                                                                                                                                       |
| `ENQ_TIME`                        | `DATE`           | \-         |                                             | Enqueue time                                                                                                                                                                                                                                                                        |
| `ENQ_TIMESTAMP`                   | `TIMESTAMP`      | \-         |                                             | Enqueue time                                                                                                                                                                                                                                                                        |
| `ENQ_USER_ID`                     | `NUMBER`         | \-         |                                             | Enqueue user ID                                                                                                                                                                                                                                                                     |
| `ENQ_USER_ID` (10.1 queue tables) | `VARCHAR2(30)`   | \-         |                                             | Enqueue user name                                                                                                                                                                                                                                                                   |
| `ENQ_TXN_ID`                      | `VARCHAR2(30)`   | \-         |                                             | Enqueue transaction ID                                                                                                                                                                                                                                                              |
| `DEQ_TIME`                        | `DATE`           | \-         |                                             | Dequeue time                                                                                                                                                                                                                                                                        |
| `DEQ_TIMESTAMP`                   | `TIMESTAMP`      | \-         |                                             | Dequeue time                                                                                                                                                                                                                                                                        |
| `DEQ_USER_ID`                     | `NUMBER`         | \-         |                                             | Dequeue user ID                                                                                                                                                                                                                                                                     |
| `DEQ_USER_ID` (10.1 queue tables) | `VARCHAR2(30)`   | \-         |                                             | Dequeue user name                                                                                                                                                                                                                                                                   |
| `DEQ_TXN_ID`                      | `VARCHAR2(30)`   | \-         |                                             | Dequeue transaction ID                                                                                                                                                                                                                                                              |
| `RETRY_COUNT`                     | `NUMBER`         | \-         | `NULL`                                      | Number of retries                                                                                                                                                                                                                                                                   |
| `EXCEPTION_QUEUE_OWNER`           | `VARCHAR2(30)`   | \-         | `NULL`                                      | Exception queue schema                                                                                                                                                                                                                                                              |
| `EXCEPTION_QUEUE`                 | `VARCHAR2(30)`   | \-         | `NULL`                                      | Exception queue name                                                                                                                                                                                                                                                                |
| `USER_DATA`                       | \-               | \-         |                                             | User data. `USER_DATA` column is defined using a decode on `USERDATA_RAW` and `USERDATA_BLOB` with `UTL_RAW.CAST_TO_VARCHAR2` for 12c Release 1 (12.1).                                                                                                                             |
| `SENDER_NAME`                     | `VARCHAR2(30)`   | \-         | `NULL`                                      | Name of the agent enqueuing the message (valid only for 8.1-compatible queue tables)                                                                                                                                                                                                |
| `SENDER_ADDRESS`                  | `VARCHAR2(1024)` | \-         | `NULL`                                      | Queue name and database name of the source (last propagating) queue (valid only for 8.1-compatible queue tables). The database name is not specified if the source queue is in the local database.                                                                                  |
| `SENDER_PROTOCOL`                 | `NUMBER`         | \-         | `NULL`                                      | Protocol for sender address (reserved for future use and valid only for 8.1-compatible queue tables)                                                                                                                                                                                |
| `ORIGINAL_MSGID`                  | `RAW(16)`        | \-         | `NULL`                                      | Message ID of the message in the source queue (valid only for 8.1-compatible queue tables)                                                                                                                                                                                          |
| `CONSUMER_NAME`                   | `VARCHAR2(30)`   | \-         | `VARCHAR2(128)`                             | Name of the agent receiving the message (valid only for 8.1-compatible multiconsumer queue tables)                                                                                                                                                                                  |
| `ADDRESS`                         | `VARCHAR2(1024)` | \-         |                                             | Queue name and database link name of the agent receiving the message.The database link name is not specified if the address is in the local database. The address is `NULL` if the receiving agent is local to the queue (valid only for 8.1-compatible multiconsumer queue tables) |
| `PROTOCOL`                        | `NUMBER`         | \-         |                                             | Protocol for address of receiving agent (valid only for 8.1-compatible queue tables)                                                                                                                                                                                                |
| `PROPAGATED_MSGID`                | `RAW(16)`        | \-         | `NULL`                                      | Message ID of the message in the queue of the receiving agent (valid only for 8.1-compatible queue tables)                                                                                                                                                                          |
| `ORIGINAL_QUEUE_NAME`             | `VARCHAR2(30)`   | \-         | `NULL`                                      | Name of the queue the message came from                                                                                                                                                                                                                                             |
| `ORIGINAL_QUEUE_OWNER`            | `VARCHAR2(30)`   | \-         | `NULL`                                      | Owner of the queue the message came from                                                                                                                                                                                                                                            |
| `EXPIRATION_REASON`               | `VARCHAR2(19)`   | \-         | `NULL`                                      | Reason the message came into exception queue. Possible values are `TIME_EXPIRATION` (message expired after the specified expired time), `MAX_RETRY_EXCEEDED` (maximum retry count exceeded), and `PROPAGATION_FAILURE` (message became undeliverable during propagation).           |

**Note:**

A message is moved to an exception queue if `RETRY_COUNT` is greater than `MAX_RETRIES`. If a dequeue transaction fails because the server process dies (including `ALTER` `SYSTEM` `KILL` `SESSION`) or `SHUTDOWN` `ABORT` on the instance, then `RETRY_COUNT` is not incremented.

### AQ\$\<Queue_Table_Name_S\>: Queue Subscribers

The `AQ$``<Queue_Table_Name``_S>` view provides information about subscribers for all the queues in any given queue table.

It shows subscribers created by users with `DBMS_AQADM.ADD_SUBSCRIBER` and subscribers created for the apply process to apply user-created events. It also displays the [transformation](glossary.md) for the [subscriber](glossary.md), if it was created with one. It is generated when the queue table is created.

This view provides functionality that is equivalent to the `DBMS_AQADM.QUEUE_SUBSCRIBERS()` procedure. For these queues, Oracle recommends that the view be used instead of this procedure to view queue subscribers. This view is created only for 8.1-compatible queue tables.

Table 9-2 AQ\$\<Queue_Table_Name_S\> View

| Column           | Datatype         | NULL       | Description                                   |
|:-----------------|:-----------------|:-----------|:----------------------------------------------|
| `QUEUE`          | `VARCHAR2(30)`   | `NOT NULL` | Name of queue for which subscriber is defined |
| `NAME`           | `VARCHAR2(30)`   | \-         | Name of agent                                 |
| `ADDRESS`        | `VARCHAR2(1024)` | \-         | Address of agent                              |
| `PROTOCOL`       | `NUMBER`         | \-         | Protocol of agent                             |
| `TRANSFORMATION` | `VARCHAR2(61)`   | \-         | Name of the transformation (can be null)      |

### AQ\$\<Queue_Table_Name_R\>: Queue Subscribers and Their Rules

The `AQ$``<Queue_Table_Name``_R>` view displays only the subscribers based on rules for all queues in a given queue table, including the text of the rule defined by each subscriber.

It also displays the transformation for the subscriber, if one was specified. It is generated when the queue table is created.

This view is created only for 8.1-compatible queue tables.

Table 9-3 AQ\$\<Queue_Table_Name_R\> View

| Column           | Datatype         | NULL       | Description                                   |
|:-----------------|:-----------------|:-----------|:----------------------------------------------|
| `QUEUE`          | `VARCHAR2(30)`   | `NOT NULL` | Name of queue for which subscriber is defined |
| `NAME`           | `VARCHAR2(30)`   | \-         | Name of agent                                 |
| `ADDRESS`        | `VARCHAR2(1024)` | \-         | Address of agent                              |
| `PROTOCOL`       | `NUMBER`         | \-         | Protocol of agent                             |
| `RULE`           | `CLOB`           | \-         | Text of defined rule                          |
| `RULE_SET`       | `VARCHAR2(65)`   | \-         | Set of [rules](glossary.md)                   |
| `TRANSFORMATION` | `VARCHAR2(61)`   | \-         | Name of the transformation (can be null)      |

### AQ\$Queue_Name_R: Queue Subscribers and Their Rules for Multi-consumer Queue

This table shows queue subscribers and their rules for multi-consumer queue.

Table 9-4 AQ\$Queue_Name_R: Queue Subscribers and Their Rules for Multi-consumer Queue

| Column           | Datatype         | NULL       |
|:-----------------|:-----------------|:-----------|
| `QUEUE`          | `VARCHAR2(30)`   | `NOT NULL` |
| `NAME`           | `VARCHAR2(30)`   | \-         |
| `ADDRESS`        | `VARCHAR2(1024)` | \-         |
| `PROTOCOL`       | `NUMBER`         | \-         |
| `RULE`           | `CLOB`           | \-         |
| `RULE_SET`       | `VARCHAR2(65)`   | \-         |
| `TRANSFORMATION` | `VARCHAR2(65)`   | \-         |

### AQ\$Queue_Name_S: Queue Subscribers and Their Rules for Multi-consumer Queue

This table shows queue subscribers and their rules for multi-consumer queue.

Table 9-5 AQ\$Queue_Name_S: Queue Subscribers and Their Rules for Multi-consumer Queue

| Column           | Datatype         | NULL       |
|:-----------------|:-----------------|:-----------|
| `QUEUE`          | `VARCHAR2(30)`   | `NOT NULL` |
| `NAME`           | `VARCHAR2(30)`   | \-         |
| `ADDRESS`        | `VARCHAR2(1024)` | \-         |
| `PROTOCOL`       | `NUMBER`         | \-         |
| `TRANSFORMATION` | `VARCHAR2(65)`   | \-         |
| `QUEUE_TO_QUEUE` | `VARCHAR2(5)`    | \-         |

### DBA_QUEUE_SUBSCRIBERS: All Queue Subscribers in Database

The `DBA_QUEUE_SUBSCRIBERS` view returns a list of all subscribers on all queues in the database.

Its columns are the same as those in `ALL_QUEUE_SUBSCRIBERS`.

**See Also:**

[Oracle Database Reference](../refrn/DBA_QUEUE_SUBSCRIBERS.md) for more information about `DBA_QUEUE_SUBSCRIBERS`.

### USER_QUEUE_SUBSCRIBERS: Queue Subscribers in User Schema

The `USER_QUEUE_SUBSCRIBERS` view returns a list of subscribers on queues in the schema of the current user.

Its columns are the same as those in `ALL_QUEUE_SUBSCRIBERS` except that it does not contain the `OWNER` column.

**See Also:**

[Oracle Database Reference](../refrn/USER_QUEUE_SUBSCRIBERS.md) for more information about `USER_QUEUE_SUBSCRIBERS`.

### ALL_QUEUE_SUBSCRIBERS: Subscribers for Queues Where User Has Queue Privileges

The `ALL_QUEUE_SUBSCRIBERS` view returns a list of subscribers to queues that the current user has privileges to dequeue from.

**See Also:**

[Oracle Database Reference](../refrn/ALL_QUEUE_SUBSCRIBERS.md) for more information about `ALL_QUEUE_SUBSCRIBERS`.

### DBA_TRANSFORMATIONS: All Transformations

The `DBA_TRANSFORMATIONS `view displays all the transformations in the database.

These transformations can be specified with Advanced Queue operations like enqueue, dequeue and subscribe to automatically integrate transformations in messaging. This view is accessible only to users having DBA privileges.

**See Also:**

[Oracle Database Reference](../refrn/DBA_TRANSFORMATIONS.md) for more information about `DBA_TRANSFORMATIONS`.

### DBA_ATTRIBUTE_TRANSFORMATIONS: All Transformation Functions

The `DBA_ATTRIBUTE_TRANSFORMATIONS` view displays the transformation functions for all the transformations in the database.

**See Also:**

[Oracle Database Reference](../refrn/DBA_ATTRIBUTE_TRANSFORMATIONS.md) for more information about `DBA_ATTRIBUTE_TRANSFORMATIONS`.

### USER_TRANSFORMATIONS: User Transformations

The `USER_TRANSFORMATIONS `view displays all the transformations owned by the user.

To view the transformation definition, query `USER_ATTRIBUTE_TRANSFORMATIONS`.

**See Also:**

[Oracle Database Reference](../refrn/USER_TRANSFORMATIONS.md) for more information about `USER_TRANSFORMATIONS`.

### USER_ATTRIBUTE_TRANSFORMATIONS: User Transformation Functions

The `USER_ATTRIBUTE_TRANSFORMATIONS` view displays the transformation functions for all the transformations of the user.

**See Also:**

[Oracle Database Reference](../refrn/USER_ATTRIBUTE_TRANSFORMATIONS.md) for more information about `USER_ATTRIBUTE_TRANSFORMATIONS`.

### DBA_SUBSCR_REGISTRATIONS: All Subscription Registrations

The `DBA_SUBSCR_REGISTRATIONS` view lists all the subscription registrations in the database.

**See Also:**

[Oracle Database Reference](../refrn/DBA_SUBSCR_REGISTRATIONS.md) for more information about `DBA_SUBSCR_REGISTRATIONS`.

### USER_SUBSCR_REGISTRATIONS: User Subscription Registrations

The `USER_SUBSCR_REGISTRATIONS `view lists the subscription registrations in the database for the current user.

Its columns are the same as those in `DBA_SUBSCR_REGISTRATIONS`.

**See Also:**

[Oracle Database Reference](../refrn/USER_SUBSCR_REGISTRATIONS.md) for more information about `USER_SUBSCR_REGISTRATIONS`.

### AQ\$INTERNET_USERS: Oracle Database Advanced Queuing Agents Registered for Internet Access

The `AQ$INTERNET_USERS` view provides information about the agents registered for Internet access to Oracle Database Advanced Queuing. It also provides the list of database users that each Internet agent maps to.

Table 9-6 AQ\$INTERNET_USERS View

| Column         | Datatype       | NULL | Description                                                                                                                     |
|:---------------|:---------------|:-----|:--------------------------------------------------------------------------------------------------------------------------------|
| `AGENT_NAME`   | `VARCHAR2(30)` | \-   | Name of the Oracle Database Advanced Queuing Internet agent                                                                     |
| `DB_USERNAME`  | `VARCHAR2(30)` | \-   | Name of database user that this Internet agent maps to                                                                          |
| `HTTP_ENABLED` | `VARCHAR2(4)`  | \-   | Indicates whether this agent is allowed to access Oracle Database Advanced Queuing through HTTP (`YES` or `NO`)                 |
| `FTP_ENABLED`  | `VARCHAR2(4)`  | \-   | Indicates whether this agent is allowed to access Oracle Database Advanced Queuing through FTP (always `NO` in current release) |

### V\$AQ: Number of Messages in Different States in Database

The `V$AQ `view provides information about the number of messages in different states for the whole database.

In a Oracle Real Application Clusters environment, each instance keeps its own Oracle Database Advanced Queuing statistics information in its own System Global Area (SGA), and does not have knowledge of the statistics gathered by other instances. When a `GV$AQ` view is queried by an instance, all other instances funnel their Oracle Database Advanced Queuing statistics information to the instance issuing the query.

**See Also:**

[Oracle Database Reference](../refrn/V-AQ.md) for more information about `V$AQ`.

### V\$BUFFERED_QUEUES: All Buffered Queues in the Instance

The `V$BUFFERED_QUEUES `view displays information about all buffered queues in the instance. There is one row per queue.

**See Also:**

[Oracle Database Reference](../refrn/V-BUFFERED_QUEUES.md) for more information about `V$BUFFERED_QUEUES`.

### V\$BUFFERED_SUBSCRIBERS: Subscribers for All Buffered Queues in the Instance

The `V$BUFFERED_SUBSCRIBERS` view displays information about the subscribers for all buffered queues in the instance. There is one row per subscriber per queue.

**See Also:**

[Oracle Database Reference](../refrn/V-BUFFERED_SUBSCRIBERS.md) for more information about `V$BUFFERED_SUBSCRIBERS`.

### V\$BUFFERED_PUBLISHERS: All Buffered Publishers in the Instance

The `V$BUFFERED_PUBLISHERS` view displays information about all buffered publishers in the instance.

There is one row per queue per sender. The values are reset to zero when the database (or instance in an Oracle RAC environment) restarts.

**See Also:**

[Oracle Database Reference](../refrn/V-BUFFERED_PUBLISHERS.md) for more information about `V$BUFFERED_PUBLISHERS`.

### V\$PERSISTENT_QUEUES: All Active Persistent Queues in the Instance

The `V$PERSISTENT_QUEUES` view displays information about all active persistent queues in the database since the queues' first activity time.

There is one row per queue. The rows are deleted when the database (or instance in an Oracle RAC environment) restarts.

**See Also:**

[Oracle Database Reference](../refrn/V-PERSISTENT_QUEUES.md) for more information about `V$PERSISTENT_QUEUES`.

### V\$PERSISTENT_QMN_CACHE: Performance Statistics on Background Tasks for Persistent Queues

The `V$PERSISTENT_QMN_CACHE` view displays detailed statistics about all background activities relating to all queue tables in the database.

There is one row per queue table. The values are reset when the database (or instance in an Oracle RAC environment) restarts.

**See Also:**

[Oracle Database Reference](../refrn/V-PERSISTENT_QMN_CACHE.md) for more information about `V$PERSISTENT_QMN_CACHE`.

### V\$PERSISTENT_SUBSCRIBERS: All Active Subscribers of the Persistent Queues in the Instance

The `V$PERSISTENT_SUBSCRIBERS` view displays information about all active subscribers of the persistent queues in the database.

There is one row per instance per queue per subscriber. The rows are deleted when the database (or instance in an Oracle RAC environment) restarts.

**See Also:**

[Oracle Database Reference](../refrn/V-PERSISTENT_SUBSCRIBERS.md) for more information about [`V$PERSISTENT_SUBSCRIBERS`](../refrn/V-PERSISTENT_SUBSCRIBERS.md).

### V\$PERSISTENT_PUBLISHERS: All Active Publishers of the Persistent Queues in the Instance

The `V$PERSISTENT_PUBLISHERS` view displays information about all active publishers of the persistent queues in the database.

There is one row per instance per queue per publisher. The rows are deleted when the database (or instance in an Oracle RAC environment) restarts.

**See Also:**

[Oracle Database Reference](../refrn/V-PERSISTENT_PUBLISHERS.md) for more information about V\$PERSISTENT_PUBLISHERS.

### V\$PROPAGATION_SENDER: Buffer Queue Propagation Schedules on the Sending (Source) Side

The `V$PROPAGATION_SENDER` view displays information about buffer queue propagation schedules on the sending (source) side.

The values are reset to zero when the database (or instance in a Oracle Real Application Clusters (Oracle RAC) environment) restarts, when propagation migrates to another instance, or when an unscheduled propagation is attempted.

**See Also:**

[Oracle Database Reference](../refrn/V-PROPAGATION_SENDER.md) for more information about `V$PROPAGATION_SENDER` .

### V\$PROPAGATION_RECEIVER: Buffer Queue Propagation Schedules on the Receiving (Destination) Side

The `V$PROPAGATION_RECEIVER` view displays information about buffer queue propagation schedules on the receiving (destination) side.

The values are reset to zero when the database (or instance in a Oracle Real Application Clusters (Oracle RAC) environment) restarts, when propagation migrates to another instance, or when an unscheduled propagation is attempted.

**See Also:**

[Oracle Database Reference](../refrn/V-PROPAGATION_RECEIVER.md) for more information about `V$PROPAGATION_RECEIVER`.

### V\$SUBSCR_REGISTRATION_STATS: Diagnosability of Notifications

The `V$SUBSCR_REGISTRATION_STATS` view provides information for diagnosability of notifications.

**See Also:**

[Oracle Database Reference](../refrn/V-SUBSCR_REGISTRATION_STATS.md) for more information about `V$SUBSCR_REGISTRATION_STATS`.

### V\$METRICGROUP: Information About the Metric Group

This `V$METRICGROUP` view displays information about the metric group for each of the four major Streams components: capture, propagation, apply, and queue.

**See Also:**

[Oracle Database Reference](../refrn/V-METRICGROUP.md) for more information about `V$METRICGROUP`.

### V\$AQ_MESSAGE_CACHE_STAT: Memory Management for Sharded Queues

The `V$AQ_MESSAGE_CACHE_STAT` view displays statistics about memory management for sharded queues in `streams_pool` within the System Global Area (SGA). Sharded queue uses `streams_pool` in units of subshards. Thus columns of this view shows statistics at subshard level irrespective of the queue. This view shows statistics across all sharded queues.

Table 9-7 V\$AQ_MESSAGE_CACHE_STAT View

| Column              | Datatype | Description                                                                                                                                                                                                                                                                                                                                                                        |
|:--------------------|:---------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `INST_ID`           | `NUMBER` | The instance id of the sharded queue                                                                                                                                                                                                                                                                                                                                               |
| `NUM_EVICTED`       | `NUMBER` | Number of evicted subshards across all sharded queues                                                                                                                                                                                                                                                                                                                              |
| `NUM_PREFETCHED`    | `NUMBER` | Number of subshards pre-fetched by AQ background Process                                                                                                                                                                                                                                                                                                                           |
| `NUM_UNEVICTION`    | `NUMBER` | Number of subshards un-evicted by foreground process. (like dequeue process)                                                                                                                                                                                                                                                                                                       |
| `NUM_UNCACHED`      | `NUMBER` | Number of subshards stored as uncached.                                                                                                                                                                                                                                                                                                                                            |
| `NUM_TRACKED`       | `NUMBER` | Number of subshards which are actively tracking dequeue rates                                                                                                                                                                                                                                                                                                                      |
| `NUM_CACHED `       | `NUMBER` | Number of subshards stored cached in memory                                                                                                                                                                                                                                                                                                                                        |
| `MAX_SUBSH_SIZE`    | `NUMBER` | Maximum subshard size seen till now, in terms of number of messages per subshard                                                                                                                                                                                                                                                                                                   |
| `MIN_SUBSH_SIZE `   | `NUMBER` | Minimum subshard size seen till now, in terms of number of messages per subshard                                                                                                                                                                                                                                                                                                   |
| `MEAN_SUBSH_SIZE`   | `NUMBER` | Mean subshard size seen till now, in terms of number of messages per subshard                                                                                                                                                                                                                                                                                                      |
| `AVG_EVICTION_RATE` | `NUMBER` | Average number of subshard evicted per second                                                                                                                                                                                                                                                                                                                                      |
| `AVG_LOAD_RATE`     | `NUMBER` | Average number of subshards pre-fetched or un-evicted per second                                                                                                                                                                                                                                                                                                                   |
| `AVG_EVICTION_TIME` | `NUMBER` | Average time taken to evict one subshard (in milliseconds)                                                                                                                                                                                                                                                                                                                         |
| `AVG_LOAD_TIME`     | `NUMBER` | Average time taken to un-evict one subshard (in milliseconds)                                                                                                                                                                                                                                                                                                                      |
| `AVG_MISS_RATIO`    | `NUMBER` | Average ratio of number of foreground un-evictions versus background pre-fetch                                                                                                                                                                                                                                                                                                     |
| `AVG_THRASH_RATIO`  | `NUMBER` | Average ratio of number of subshard pre-fetched by background without dequeue attempt versus total number of subshards prefetched                                                                                                                                                                                                                                                  |
| `CON_ID`            | `NUMBER` | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• `n`: Where n is the applicable container ID for the rows containing data |

**Note:**

Some of the above mentioned columns will be used by sharded queue memory advisor during analysis.

### V\$AQ_SHARDED_SUBSCRIBER_STAT: Sharded Queue Subscriber Statistics

The `V$AQ_SHARDED_SUBSCRIBER_STAT` view displays statistical information about the subscribers of sharded queues. This statistics is used by the memory advisor.

Table 9-8 V\$AQ_SHARDED_SUBSCRIBER_STAT View

| Column                      | Datatype | Description                                                                                                                                         |
|:----------------------------|:---------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| `INST_ID`                   | `NUMBER` | Instance Identifier                                                                                                                                 |
| `QUEUE_ID`                  | `NUMBER` | Queue Identifier                                                                                                                                    |
| `SUBSCRIBER_ID`             | `NUMBER` | Subscriber Identifier                                                                                                                               |
| `SHARD_ID`                  | `NUMBER` | Shard Identifier                                                                                                                                    |
| `PRIORITY`                  | `NUMBER` | Priority value of the shard                                                                                                                         |
| `DEQUEUE_SUBSHARD`          | `NUMBER` | Last known dequeue position in this shard                                                                                                           |
| `ENQUEUED_MSGS`             | `NUMBER` | Number of enqueued messages                                                                                                                         |
| `DEQUEUED_MSGS`             | `NUMBER` | Number of dequeued messages                                                                                                                         |
| `ELAPSED_DEQUEUE_TIME`      | `NUMBER` | Amount of time spent performing dequeues (in seconds)                                                                                               |
| `CPU_DEQUEUE_TIME`          | `NUMBER` | Actual amount of CPU time spent performing dequeues (in seconds)                                                                                    |
| `DEQUEUE_RATE`              | `NUMBER` | Number of messages dequeued per second                                                                                                              |
| `TIME_SINCE_LAST_DEQUEUE`   | `NUMBER` | Time since last dequeue activity (in seconds)                                                                                                       |
| `ESTD_TIME_TO_DRAIN`        | `NUMBER` | Estimated amount of time to drain the shard (in seconds) with current enqueue and dequeue rates. Null, if enqueue rate is greater than dequeue rate |
| `ESTD_TIME_TO_DRAIN_NO_ENQ` | `NUMBER` | Estimated amount of time to drain the shard (in seconds) with no new enqueues                                                                       |
| `CON_ID`                    | `NUMBER` | The ID of the container to which the data pertains.                                                                                                 |

### V\$AQ_MESSAGE_CACHE_ADVICE: Simulated Metrics

The `V$AQ_MESSAGE_CACHE_ADVICE` view shows simulated metrics for a range of potential message cache sizes. This view assists in cache sizing by providing information in form of metrics as described below.

Table 9-9 V\$AQ_MESSAGE_CACHE_ADVICE View

| Column                    | Datatype   | Description                                                                                                                                                                                                                                                                                    |
|:--------------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `INST_ID`                 | `NUMBER`   | Instance id                                                                                                                                                                                                                                                                                    |
| `SIZE_FOR_ESTIMATE`       | `NUMBER`   | Cache size for simulation (in megabytes)                                                                                                                                                                                                                                                       |
| `SIZE_FACTOR`             | `NUMBER`   | Size factor with respect to the current cache size (in %)                                                                                                                                                                                                                                      |
| `ESTD_SIZE_TYPE`          | `VARCHAR2` | This column can have one of the following values:<br>• `MINIMUM` - This cache size is required to have all dequeues in-memory (no uncached)<br>• `CURRENT` - This is current size of message cache<br>• `MAXIMUM` - This cache size is required to have zero evictions<br>• `Null` - otherwise |
| `ESTD_CACHED_SUBSHARDS`   | `NUMBER`   | Estimated number of cached subshards for this size                                                                                                                                                                                                                                             |
| `ESTD_UNCACHED_SUBSHARDS` | `NUMBER`   | Estimated number of uncached subshards for this size                                                                                                                                                                                                                                           |
| `ESTD_EVICTIONS`          | `NUMBER`   | Estimated number of subshards evicted for this size                                                                                                                                                                                                                                            |
| `ESTD_EVICTION_RATE`      | `NUMBER`   | Estimated number of subshards getting evicted per minute                                                                                                                                                                                                                                       |
| `ESTD_FG_UNEVICTIONS`     | `NUMBER`   | Estimated number of subshards unevicted by foreground processes                                                                                                                                                                                                                                |
| `ESTD_FG_UNEVICTION_RATE` | `NUMBER`   | Estimated number of subshards getting unevicted by foreground processes                                                                                                                                                                                                                        |
| `ESTD_BG_UNEVICTIONS`     | `NUMBER`   | Estimated number of subshards unevicted by background processes                                                                                                                                                                                                                                |
| `ESTD_BG_UNEVICTION_RATE` | `NUMBER`   | Estimated number of subshards getting unevicted by background processes                                                                                                                                                                                                                        |
| `ESTD_BG_PROCESSES `      | `NUMBER`   | Estimated number of background processes required for this size                                                                                                                                                                                                                                |
| `TOTAL_ENQUEUE_RATE`      | `NUMBER`   | Simulated number of messages being enqueued per second                                                                                                                                                                                                                                         |
| `TOTAL_DEQUEUE_RATE`      | `NUMBER`   | Simulated number of messages being dequeued per second                                                                                                                                                                                                                                         |
| `AVG_SUBSHARD_SIZE`       | `NUMBER`   | Simulated average number of messages per cached subshard                                                                                                                                                                                                                                       |
| `AVG_SUBSHARD_MEMORY`     | `NUMBER`   | Simulated average memory per cached subshard (in megabytes)                                                                                                                                                                                                                                    |
| `AVG_EVICTION_TIME`       | `NUMBER`   | Simulated average time to evict a cached subshard (in milliseconds)                                                                                                                                                                                                                            |
| `AVG_UNEVICTION_TIME`     | `NUMBER`   | Simulated average time to unevict a cached subshard (in milliseconds)                                                                                                                                                                                                                          |
| `FLAGS`                   | `NUMBER`   | Reserved for internal and future use                                                                                                                                                                                                                                                           |
| `SIMULATION_TIME`         | `NUMBER`   | Amount of time that was simulated for (in minutes)                                                                                                                                                                                                                                             |
| `CON_ID`                  | `NUMBER`   | The ID of the container to which the data pertains.                                                                                                                                                                                                                                            |

### V\$AQ_REMOTE_DEQUEUE_AFFINITY: Dequeue Affinity Instance List

The `V$AQ_REMOTE_DEQUEUE_AFFINITY` view lists the dequeue affinity instance of the subscribers not dequeuing locally from the shard's owner instance. Cross instance message forwarding is used for these subscribers.

Table 9-10 V\$AQ_REMOTE_DEQUEUE_AFFINITY View

| Column            | Datatype   | Description                                                                                                           |
|:------------------|:-----------|:----------------------------------------------------------------------------------------------------------------------|
| `QUEUE_ID`        | `NUMBER`   | Queue Identifier                                                                                                      |
| `QUEUE_SCHEMA`    | `VARCHAR2` | Queue schema name                                                                                                     |
| `QUEUE_NAME`      | `VARCHAR2` | Queue name                                                                                                            |
| `SUBSCRIBER_ID`   | `NUMBER`   | Subscriber identifier                                                                                                 |
| `SHARD_ID`        | `NUMBER`   | Shard identifier which is being forwarded from `SOURCE_INSTANCE` to `INST_ID` for the subscriber                      |
| `SOURCE_INSTANCE` | `NUMBER`   | Owner instance from where the shard is being forwarded                                                                |
| `INST_ID`         | `NUMBER`   | Dequeue instance id of the subscriber for the shard. Destination instance where shard is forwarded for the subscriber |

####

**See Also:**

[Oracle Database Reference](../refrn/V-AQ_REMOTE_DEQUEUE_AFFINITY.md) for more information about `V$AQ_REMOTE_DEQUEUE_AFFINITY`.

### V\$AQ_BACKGROUND_COORDINATOR: Performance Statistics for AQ's Master Background Coordinator Process (AQPC)

The `V$AQ_BACKGROUND_COORDINATOR` view is applicable for Oracle Database 12c Release 1 (12.1) onwards.

This view lists performance statistics for the Oracle Database Advanced Queuing master background coordinator process (AQPC).

**See Also:**

[Oracle Database Reference](../refrn/V-AQ_BACKGROUND_COORDINATOR.md) for more information about `V$AQ_BACKGROUND_COORDINATOR`.

### V\$AQ_JOB_COORDINATOR: Performance Statistics per Coordinator

The `V$AQ_JOB_COORDINATOR` view is applicable for Oracle Database 12c Release 1 (12.1) onwards.

This view lists performance statistics per coordinator, for every AQ coordinator controlled by the AQ's Master coordinator.

**See Also::**

[Oracle Database Reference](../refrn/V-AQ_JOB_COORDINATOR.md) for more information about `V$AQ_JOB_COORDINATOR`.

### V\$AQ_SERVER_POOL: Performance Statistics for all Servers

The `V$AQ_SERVER_POOL` view is applicable for Oracle Database 12c Release 1 (12.1) onwards. This view lists performance statistics for all the servers in the pool.

**See Also::**

[Oracle Database Reference](../refrn/V-AQ_SERVER_POOL.md) for more information about `V$AQ_SERVER_POOL`.

### V\$AQ_CROSS_INSTANCE_JOBS: Cross Process Jobs Description

The `V$AQ_CROSS_INSTANCE_JOBS` view is applicable for Oracle Database 12c Release 1 (12.1) onwards. This view describes each of the cross process jobs.

Each job serves for forwarding messages for a shard from source instance to destination instance for a set of subscribers.

**See Also::**

[Oracle Database Reference](../refrn/V-AQ_CROSS_INSTANCE_JOBS.md) for more information about `V$AQ_CROSS_INSTANCE_JOBS`.

### V\$AQ_IPC_ACTIVE_MSGS

`V$AQ_IPC_ACTIVE_MSGS` displays information about long and priority messages being processed by slaves and the short message being processed by the master.

**See Also:**

[Oracle Database Reference](../refrn/V-AQ_IPC_ACTIVE_MSGS.md) for more information about `V$AQ_IPC_ACTIVE_MSGS`.

### V\$AQ_IPC_MSG_STATS

V\$AQ_IPC_MSG_STATS displays cumulative statistics for each message class, for example., cumulative calls, average pending/processing time, and last failure.

**See Also:**

[Oracle Database Reference](../refrn/V-AQ_IPC_MSG_STATS.md) for more information about `V$AQ_IPC_MSG_STATS`.

### V\$AQ_IPC_PENDING_MSGS

V\$AQ_IPC_PENDING_MSGS displays information about pending messages, present in the local master context.

**See Also:**

[Oracle Database Reference](../refrn/V-AQ_IPC_PENDING_MSGS.md) for more information about `V$AQ_IPC_PENDING_MSGS`.

### V\$AQ_NONDUR_REGISTRATIONS: Non-Durable Registrations

The `V$AQ_NONDUR_REGISTRATIONS` view is applicable for Oracle Database 12c Release 1 (12.1) onwards. This view provides information about non-durable subscriptions.

**See Also::**

[Oracle Database Reference](../refrn/V-AQ_NONDUR_REGISTRATIONS.md) for more information about `V$AQ_NONDUR_REGISTRATIONS`.

### V\$AQ_NOTIFICATION_CLIENTS: Secure OCI Client Connections

The `V$AQ_NOTIFICATION_CLIENTS` view is applicable for Oracle Database 12c Release 1 (12.1) onwards. This view displays performance statistics for secure OCI client connections.

**See Also::**

[Oracle Database Reference](../refrn/V-AQ_NOTIFICATION_CLIENTS.md) for more information about `V$AQ_NOTIFICATION_CLIENTS`.

### V\$AQ_SUBSCRIBER_LOAD: Durable Subscribers

The `V$AQ_SUBSCRIBER_LOAD` view is applicable for Oracle Database 12c Release 1 (12.1) onwards. This view describes the load of all subscribers of sharded queues in terms of latency at every instance in an Oracle RAC environment.

Latency denotes the predicted amount of time (in seconds) required from the current time to drain all the messages for that subscriber at each respective instance. The latency calculation considers past enqueue/dequeue rates and future enqueue/dequeue rates based on history.

**See Also::**

[Oracle Database Reference](../refrn/V-AQ_SUBSCRIBER_LOAD.md) for more information about `V$AQ_SUBSCRIBER_LOAD`.

### V\$AQ_NONDUR_SUBSCRIBER: Non-Durable Subscribers

The `V$AQ_NONDUR_SUBSCRIBER` view is applicable for Oracle Database 12c Release 1 (12.1) onwards. `V$AQ_NONDUR_SUBSCRIBER` provides information about non-durable subscribers on sharded queues.

**See Also::**

[Oracle Database Reference](../refrn/V-AQ_NONDUR_SUBSCRIBER.md) for more information about `V$AQ_NONDUR_SUBSCRIBER`.

### V\$AQ_NONDUR_SUBSCRIBER_LWM: LWM of Non Durable Subscriber

The `V$AQ_NONDUR_SUBSCRIBER_LWM` view is applicable for Oracle Database 12c Release 1 (12.1) onwards. The LWM of a non durable subscriber is a combination of shard, priority and LWM (sub-shard).

**See Also::**

[Oracle Database Reference](../refrn/V-AQ_NONDUR_SUBSCRIBER_LWM.md) for more information about `V$AQ_NONDUR_SUBSCRIBER_LWM`.

### V\$AQ_MESSAGE_CACHE: Performance Statistics

The `V$AQ_MESSAGE_CACHE` view provides performance statistics of the message cache for sharded queues at the subshard level in the instance.

**See Also::**

[Oracle Database Reference](../refrn/V-AQ_MESSAGE_CACHE.md) for more information about `V$AQ_MESSAGE_CACHE`.

### MGW_GATEWAY: Configuration and Status Information

This view lists configuration and status information for Messaging Gateway.

Table 9-11 MGW_GATEWAY View Properties

| Name               | Type        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:-------------------|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AGENT_DATABASE`   | `VARCHAR2`  | The database connect string used by the Messaging Gateway agent. `NULL` indicates that a local connection is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `AGENT_INSTANCE`   | `NUMBER`    | The database instance on which the Messaging Gateway agent is currently running. This should be `NULL` if the agent is not running.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `AGENT_JOB`        | `NUMBER`    | \[Deprecated\] Job number of the queued job used to start the Messaging Gateway agent process. The job number is set when Messaging Gateway is started and cleared when it shuts down.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `AGENT_NAME`       | `VARCHAR2`  | Name of the Messaging Gateway agent                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `AGENT_PING`       | `VARCHAR2`  | Gateway agent ping status. Values:<br>• `NULL` means no ping attempt was made.<br>• `REACHABLE` means ping attempt was successful.<br>• `UNREACHABLE` means ping attempt failed.<br>`AGENT_PING` attempts to contact the Messaging Gateway agent. There is a short delay (up to 5 seconds) if the ping attempt fails. No ping is attempted if the `AGENT_STATUS` is `NOT_STARTED` or `START_SCHEDULED`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `AGENT_START_TIME` | `TIMESTAMP` | The time when the Messaging Gateway agent job currently running was started. This should be `NULL` if the agent is not running.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `AGENT_STATUS`     | `VARCHAR2`  | Status of the Messaging Gateway agent. Values:<br>• `NOT_STARTED` means the Messaging Gateway agent has not been started<br>• `START_SCHEDULED` means Messaging Gateway agent has been scheduled to start. That is, Messaging Gateway has been started using `DBMS_MGWADM.STARTUP`, but the queued job used to start the Messaging Gateway agent has not yet run.<br>• `STARTING` means Messaging Gateway agent is starting. That is, Messaging Gateway has been started using `DBMS_MGWADM.STARTUP`, the queued job has run, and the Messaging Gateway agent is starting up.<br>• `INITIALIZING` means the Messaging Gateway agent has started and is initializing<br>• `RUNNING` means the Messaging Gateway agent is running<br>• `SHUTTING_DOWN` means the Messaging Gateway agent is shutting down<br>• `BROKEN` means an unexpected condition has been encountered that prevents the Messaging Gateway agent from starting. `DBMS_MGWADM.CLEANUP_GATEWAY` must be called before the agent can be started. |
| `AGENT_USER`       | `VARCHAR2`  | Database user name used by the Messaging Gateway agent to connect to the database                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `COMMENTS`         | `VARCHAR2`  | Comments for the agent                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `CONNTYPE`         | `VARCHAR2`  | Connection type used by the agent:<br>• `JDBC_OCI` if the JDBC OCI driver is used<br>• `JDBC_THIN` if the JDBC Thin driver is used                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `INITFILE`         | `VARCHAR2`  | Name of the Messaging Gateway initialization file used by the agent. `NULL` indicates that the default initialization file is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `LAST_ERROR_DATE`  | `DATE`      | Date of last Messaging Gateway agent error. The last error information is cleared when Messaging Gateway is started. It is set if the Messaging Gateway agent fails to start or terminates due to an abnormal condition.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `LAST_ERROR_MSG`   | `VARCHAR2`  | Message for last Messaging Gateway agent error                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `LAST_ERROR_TIME`  | `VARCHAR2`  | Time of last Messaging Gateway agent error                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `MAX_CONNECTIONS`  | `NUMBER`    | \[Deprecated\] Maximum number of messaging connections to Oracle Database                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `MAX_MEMORY`       | `NUMBER`    | Maximum heap size used by the Messaging Gateway agent (in MB)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `MAX_THREADS`      | `NUMBER`    | Maximum number of messaging threads created by the Messaging Gateway agent                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `SERVICE`          | `VARCHAR2`  | Name of the database service that is associated with an Oracle Scheduler job class used by the agent                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

### MGW_AGENT_OPTIONS: Supplemental Options and Properties

This view lists supplemental options and properties for a Messaging Gateway agent.

Table 9-12 MGW_AGENT_OPTIONS View

| Column       | Type       | Description                                                                                                                                       |
|:-------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| `AGENT_NAME` | `VARCHAR2` | Name of the Messaging Gateway agent                                                                                                               |
| `ENCRYPTED`  | `VARCHAR2` | Indicates whether the value is stored as encrypted:<br>• `TRUE` if the value is stored encrypted<br>• `FALSE` if the value is stored as cleartext |
| `NAME`       | `VARCHAR2` | Name of the option                                                                                                                                |
| `TYPE`       | `VARCHAR2` | Option type or usage: `JAVA_SYSTEM_PROP` if the option is used to set a Java System property                                                      |
| `VALUE`      | `VARCHAR2` | Value for the option. This will be \<\<`ENCRYPTED`\>\> if the value is stored in an encrypted form.                                               |

### MGW_LINKS: Names and Types of Messaging System Links

This view lists the names and types of messaging system links currently defined.

Table 9-13 MGW_LINKS View Properties

| Name           | Type       | Description                                                                                                                |
|:---------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------|
| `AGENT_NAME`   | `VARCHAR2` | Name of the Messaging Gateway agent that will process propagation jobs for this link                                       |
| `LINK_COMMENT` | `VARCHAR2` | User comment for the link                                                                                                  |
| `LINK_NAME`    | `VARCHAR2` | Name of the messaging system link                                                                                          |
| `LINK_TYPE`    | `VARCHAR2` | Type of messaging system link. Values<br>• `MQSERIES` is for WebSphere MQ links.<br>• `TIBRV` is for TIB/Rendezvous links. |

### MGW_MQSERIES_LINKS: WebSphere MQ Messaging System Links

This view lists information for the WebSphere MQ messaging system links. The view includes most of the messaging system properties specified when the link is created.

Table 9-14 MGW_MQSERIES_LINKS View Properties

| Name                 | Type                 | Description                                                                                                                                                                                                                                                                                                                  |
|:---------------------|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AGENT_NAME`         | `VARCHAR2`           | Name of the Messaging Gateway agent that will process propagation jobs for this link                                                                                                                                                                                                                                         |
| `CHANNEL`            | `VARCHAR2`           | Connection channel                                                                                                                                                                                                                                                                                                           |
| `HOSTNAME`           | `VARCHAR2`           | Name of the WebSphere MQ host                                                                                                                                                                                                                                                                                                |
| `INBOUND_LOG_QUEUE`  | `VARCHAR2`           | Inbound propagation log queue                                                                                                                                                                                                                                                                                                |
| `INTERFACE_TYPE`     | `VARCHAR2`           | Messaging interface type. Values:<br>• `BASE_JAVA` is for WebSphere MQ Base Java interface<br>• `JMS_CONNECTION` is for WebSphere MQ JMS unified, domain-independent connections<br>• `JMS_QUEUE_CONNECTION` is for WebSphere MQ JMS queue connections<br>• `JMS_TOPIC_CONNECTION` is for WebSphere MQ JMS topic connections |
| `LINK_COMMENT`       | `VARCHAR2`           | User comment for the link                                                                                                                                                                                                                                                                                                    |
| `LINK_NAME`          | `VARCHAR2`           | Name of the messaging system link                                                                                                                                                                                                                                                                                            |
| `MAX_CONNECTIONS`    | `NUMBER`             | Maximum number of messaging connections                                                                                                                                                                                                                                                                                      |
| `OPTIONS`            | `SYS.MGW_PROPERTIES` | Link options                                                                                                                                                                                                                                                                                                                 |
| `OUTBOUND_LOG_QUEUE` | `VARCHAR2`           | Outbound propagation log queue                                                                                                                                                                                                                                                                                               |
| `PORT`               | `NUMBER`             | Port number                                                                                                                                                                                                                                                                                                                  |
| `QUEUE_MANAGER`      | `VARCHAR2`           | Name of the WebSphere MQ queue manager                                                                                                                                                                                                                                                                                       |

### MGW_TIBRV_LINKS: TIB/Rendezvous Messaging System Links

This view lists information for TIB/Rendezvous messaging system links. The view includes most of the messaging system properties specified when the link was created.

Table 9-15 MGW_TIBRV_LINKS View Properties

| Property Name  | Type                 | Description                                                                          |
|:---------------|:---------------------|:-------------------------------------------------------------------------------------|
| `AGENT_NAME`   | `VARCHAR2`           | Name of the Messaging Gateway agent that will process propagation jobs for this link |
| `CM_LEDGER`    | `VARCHAR2`           | TIB/Rendezvous CM ledger file name                                                   |
| `CM_NAME`      | `VARCHAR2`           | TIB/Rendezvous CM correspondent name                                                 |
| `DAEMON`       | `VARCHAR2`           | TIB/Rendezvous daemon parameter for RVD transport                                    |
| `LINK_COMMENT` | `VARCHAR2`           | User comment for the link                                                            |
| `LINK_NAME`    | `VARCHAR2`           | Name of the messaging system link                                                    |
| `NETWORK`      | `VARCHAR2`           | TIB/Rendezvous network parameter for rvd transport                                   |
| `OPTIONS`      | `SYS.MGW_PROPERTIES` | Link options                                                                         |
| `SERVICE`      | `VARCHAR2`           | TIB/Rendezvous service parameter for rvd transport                                   |

### MGW_FOREIGN_QUEUES: Foreign Queues

This view lists information for foreign queues. The view includes most of the queue properties specified when the queue is registered.

Table 9-16 MGW_FOREIGN_QUEUES View Properties

| Name             | Type                 | Description                                                                                                                                                                                                                     |
|:-----------------|:---------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DOMAIN`         | `VARCHAR2`           | Queue domain type. Values:<br>• `NULL` means the queue domain type is automatically determined by the messaging system<br>• `QUEUE` is for a queue (point-to-point) model<br>• `TOPIC` is for a topic (publish-subscribe) model |
| `LINK_NAME`      | `VARCHAR2`           | Name of the messaging system link                                                                                                                                                                                               |
| `NAME`           | `VARCHAR2`           | Name of the registered queue                                                                                                                                                                                                    |
| `OPTIONS`        | `SYS.MGW_PROPERTIES` | Optional queue properties                                                                                                                                                                                                       |
| `PROVIDER_QUEUE` | `VARCHAR2`           | Message provider (native) queue name                                                                                                                                                                                            |
| `QUEUE_COMMENT`  | `VARCHAR2`           | User comment for the foreign queue                                                                                                                                                                                              |

### MGW_JOBS: Messaging Gateway Propagation Jobs

This view lists information for Messaging Gateway propagation jobs. The view includes most of the job properties specified when the propagation job was created, as well as other status and statistical information.

Table 9-17 MGW_JOBS View

| Column             | Type                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:-------------------|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AGENT_NAME`       | `VARCHAR2`           | Name of the Messaging Gateway agent that processes this job                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `COMMENTS`         | `VARCHAR2`           | Comments for the propagation job                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `DESTINATION`      | `VARCHAR2`           | Destination queue to which messages are propagated                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `ENABLED`          | `VARCHAR2`           | Indicates whether the job is enabled or not:<br>• `TRUE` if the job is enabled<br>• `FALSE` if the job is disabled                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `EXCEPTION_QUEUE`  | `VARCHAR2`           | Exception queue used for propagation logging purposes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `EXCEPTIONQ_MSGS`  | `NUMBER`             | Option type or usage: `JAVA_SYSTEM_PROP` if the option is used to set a Java System property                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `FAILURES`         | `NUMBER`             | Number of messages moved to exception queue since the last time the agent was started                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `JOB_NAME`         | `VARCHAR2`           | Name of the propagation job                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `LAST_ERROR_MSG`   | `VARCHAR2`           | Message for the last propagation error                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `LAST_ERROR_DATE`  | `DATE`               | Date of the last propagation error                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `LAST_ERROR_TIME`  | `VARCHAR2`           | Time of the last propagation error                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `LINK_NAME`        | `VARCHAR2`           | Name of the Messaging Gateway link used by this job                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `OPTIONS`          | `SYS.MGW_PROPERTIES` | Job options                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `POLL_INTERVAL`    | `INTEGER`            | Propagation poll interval (in seconds)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `PROPAGATED_MSGS`  | `NUMBER`             | Number of messages propagated since the last time the agent was started                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `PROP_STYLE`       | `VARCHAR2`           | Message propagation style:<br>• `NATIVE` for native message propagation<br>• `JMS` for JMS message propagation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `PROPAGATION_TYPE` | `VARCHAR2`           | Propagation type:<br>• `OUTBOUND` is for Oracle Database AQ to non-Oracle propagation<br>• `INBOUND` is for non-Oracle to Oracle Database AQ propagation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `RULE`             | `VARCHAR2`           | Subscription rule used for the propagation source                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `SOURCE`           | `VARCHAR2`           | Source queue from which messages are propagated                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `STATUS`           | `VARCHAR2`           | Job status:<br>• `READY` means the job is ready for propagation. The job must be enabled and the Messaging Gateway agent running before messages are actually propagated.<br>• `RETRY` means the agent encountered errors when attempting to propagate messages for the job and will retry the operation<br>• `FAILED` means the job has failed and agent has stopped trying to propagate messages. Usually this is due to an unrecoverable error or the propagation failure limit being reached. The job must be reset before the agent will attempt to propagate messages. The job is automatically reset each time the agent is started and can be manually reset by `DBMS_MGWADM.RESET_JOB`.<br>• `DELETE_PENDING` means that job removal is pending. `DBMS_MGWADM.REMOVE_JOB` has been called but certain cleanup tasks for this job are still outstanding.<br>• `SUBSCRIBER_DELETE_PENDING` means that removal is pending for the subscriber associated with the job. `DBMS_MGWADM.REMOVE_SUBSCRIBER` has been called but certain cleanup tasks are still outstanding. |
| `TRANSFORMATION`   | `VARCHAR2`           | Transformation used for message conversion                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### MGW_SUBSCRIBERS: Information for Subscribers

This view lists configuration and status information for Messaging Gateway subscribers. The view includes most of the subscriber properties specified when the subscriber is added, as well as other status and statistical information.

Table 9-18 MGW_SUBSCRIBERS View Properties

| Name               | Type                 | Description                                                                                                                                                                                                                                                                        |
|:-------------------|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DESTINATION`      | `VARCHAR2`           | Destination queue to which messages are propagated                                                                                                                                                                                                                                 |
| `EXCEPTIONQ_MSGS`  | `NUMBER`             | Number of messages moved to the propagation exception queue since the last time the agent was started                                                                                                                                                                              |
| `EXCEPTION_QUEUE`  | `VARCHAR2`           | Exception queue used for logging purposes                                                                                                                                                                                                                                          |
| `FAILURES`         | `NUMBER`             | Number of propagation failures                                                                                                                                                                                                                                                     |
| `LAST_ERROR_DATE`  | `DATE`               | Date of last propagation error                                                                                                                                                                                                                                                     |
| `LAST_ERROR_MSG`   | `VARCHAR2`           | Message for last propagation error                                                                                                                                                                                                                                                 |
| `LAST_ERROR_TIME`  | `VARCHAR2`           | Time of last propagation error                                                                                                                                                                                                                                                     |
| `OPTIONS`          | `SYS.MGW_PROPERTIES` | Subscriber options                                                                                                                                                                                                                                                                 |
| `PROP_STYLE`       | `VARCHAR2`           | Message propagation style. Values:<br>• `NATIVE` is for native message propagation<br>• `JMS` is for JMS message propagation                                                                                                                                                       |
| `PROPAGATED_MSGS`  | `NUMBER`             | Number of messages propagated to the destination queue since the last time the agent was started                                                                                                                                                                                   |
| `PROPAGATION_TYPE` | `VARCHAR2`           | Propagation type. Values:<br>• `OUTBOUND` is for Oracle Database AQ to non-Oracle propagation<br>• `INBOUND` is for non-Oracle to Oracle Database AQ propagation                                                                                                                   |
| `QUEUE_NAME`       | `VARCHAR2`           | Subscriber source queue                                                                                                                                                                                                                                                            |
| `RULE`             | `VARCHAR2`           | Subscription rule                                                                                                                                                                                                                                                                  |
| `STATUS`           | `VARCHAR2`           | Subscriber status. Values:<br>• `ENABLED` means the subscriber is enabled<br>• `DELETE_PENDING` means subscriber removal is pending, usually because `DBMS_MGWADM.REMOVE_SUBSCRIBER` has been called but certain cleanup tasks pertaining to this subscriber are still outstanding |
| `SUBSCRIBER_ID`    | `VARCHAR2`           | Propagation subscriber identifier                                                                                                                                                                                                                                                  |
| `TRANSFORMATION`   | `VARCHAR2`           | Transformation used for message conversion                                                                                                                                                                                                                                         |

### MGW_SCHEDULES: Information About Schedules

This view lists configuration and status information for Messaging Gateway schedules. The view includes most of the schedule properties specified when the schedule is created, as well as other status information.

Table 9-19 MGW_SCHEDULES View Properties

| Name                 | Type       | Description                                                                                                                                                      |
|:---------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DESTINATION`        | `VARCHAR2` | Propagation destination                                                                                                                                          |
| `LATENCY`            | `NUMBER`   | Propagation window latency (in seconds)                                                                                                                          |
| `NEXT_TIME`          | `VARCHAR2` | Reserved for future use                                                                                                                                          |
| `PROPAGATION_TYPE`   | `VARCHAR2` | Propagation type. Values:<br>• `OUTBOUND` is for Oracle Database AQ to non-Oracle propagation<br>• `INBOUND` is for non-Oracle to Oracle Database AQ propagation |
| `PROPAGATION_WINDOW` | `NUMBER`   | Reserved for future use                                                                                                                                          |
| `SCHEDULE_DISABLED`  | `VARCHAR2` | Indicates whether the schedule is disabled. `Y` means the schedule is disabled. `N` means the schedule is enabled.                                               |
| `SCHEDULE_ID`        | `VARCHAR2` | Propagation schedule identifier                                                                                                                                  |
| `SOURCE`             | `VARCHAR2` | Propagation source                                                                                                                                               |
| `START_DATE`         | `DATE`     | Reserved for future use                                                                                                                                          |
| `START_TIME`         | `VARCHAR2` | Reserved for future use                                                                                                                                          |
