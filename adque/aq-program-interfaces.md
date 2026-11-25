These topics describe the various language options and elements you must work with and issues to consider in preparing your Oracle Database Advanced Queuing (AQ) application environment.

**Note:**

Java package `oracle.AQ` was deprecated in 10g Release 1 (10.1). Oracle recommends that you migrate existing Java AQ applications to Oracle JMS (or other Java APIs) and use Oracle JMS (or other Java APIs) to design your future Java AQ applications.

Topics:

- Programmatic Interfaces for Accessing Oracle Database Advanced Queuing

- Using PL/SQL to Access Oracle Database Advanced Queuing

- Using OCI to Access Oracle Database Advanced Queuing

- Using OCCI to Access Oracle Database Advanced Queuing

- Using Oracle Java Message Service (Oracle JMS) to Access Oracle Database Advanced Queuing

- Using Oracle Database Advanced Queuing XML Servlet to Access Oracle Database Advanced Queuing

- Comparing Oracle Database Advanced Queuing Programmatic Interfaces

### Programmatic Interfaces for Accessing Oracle Database Advanced Queuing

The table lists Oracle Database Advanced Queuing programmatic interfaces, functions supported in each interface, and syntax references.

Table 3-1 Oracle Database Advanced Queuing Programmatic Interfaces

| Language                      | Precompiler or Interface Program                        | Functions Supported            | Syntax References                                                                 |
|:------------------------------|:--------------------------------------------------------|:-------------------------------|:----------------------------------------------------------------------------------|
| PL/SQL                        | `DBMS_AQADM` and `DBMS_AQ` Packages                     | Administrative and operational | [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_AQ.md)        |
| C                             | [Oracle Call Interface](glossary.md) (OCI)              | Operational only               | [Oracle Call Interface Programmer's Guide](../lnoci/introduction.md)              |
| Java (JMS)                    | `oracle.JMS` package using JDBC [API](glossary.md)      | Administrative and operational | [Oracle Database Advanced Queuing Java API Reference](../jajms/index.md)          |
| AQ XML [servlet](glossary.md) | [Internet Data Access Presentation](glossary.md) (IDAP) | Operational only               | [Oracle XML DB Developer's Guide](../adxdb/XML-data-exchange-using-streams-AQ.md) |

### Using PL/SQL to Access Oracle Database Advanced Queuing

The PL/SQL packages `DBMS_AQADM` and `DBMS_AQ` support access to Oracle Database Advanced Queuing administrative and operational functions using the native Oracle Database Advanced Queuing interface.

These functions include:

- Create [queue](glossary.md), [queue table](glossary.md), [nonpersistent](glossary.md) queue, [sharded queue](glossary.md), multiconsumer queue/topic, RAW [message](glossary.md), or message with structured data

- Get queue table, queue, or multiconsumer queue/topic

- Alter queue table or queue/topic

- Drop queue/topic

- Start or stop queue/topic

- Grant and revoke privileges

- Add, remove, or alter [subscriber](glossary.md)

- Add, remove, or alter an Oracle Database Advanced Queuing Internet agent

- Grant or revoke privileges of database users to Oracle Database Advanced Queuing Internet agents

- Enable, disable, or alter [propagation](glossary.md) schedule

- Enqueue messages to single [consumer](glossary.md) queue (point-to-point model)

- Publish messages to multiconsumer queue/topic ([publish/subscribe](glossary.md) model)

- Subscribe for messages in multiconsumer queue

- Browse messages in a queue

- Receive messages from queue/topic

- Register to receive messages asynchronously

- Listen for messages on multiple queues/topics

- Post messages to anonymous subscriptions

- Bind or unbind agents in a [Lightweight Directory Access Protocol](glossary.md) (LDAP) server

- Add or remove aliases to Oracle Database Advanced Queuing objects in a LDAP server

Available PL/SQL `DBMS_AQADM` and `DBMS_AQ` functions are listed in detail in Table 3–2 through Table 3–9.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_AQ.md)for detailed documentation of `DBMS_AQADM` and `DBMS_AQ`, including syntax, parameters, parameter types, return values, and examples

### Using OCI and the Thin JDBC Driver to Access Oracle Database Advanced Queuing

An Oracle Call Interface (OCI) provides an interface to Oracle Database Advanced Queuing functions using the native Oracle Database Advanced Queuing interface.

An OCI client can perform the following actions:

- Enqueue messages

- Dequeue messages

- Listen for messages on sets of queues

- Register to receive message notifications

In addition, OCI clients can receive [asynchronous](glossary.md) notifications for new messages in a queue using `OCISubscriptionRegister`. Sharded queues do not support OCI clients.

#### Oracle Type Translator

For queues with user-defined payload types, the Oracle type translator must be used to generate the OCI/OCCI mapping for the Oracle type. The OCI client is responsible for freeing the memory of the Oracle Database Advanced Queuing descriptors and the message payload.

**See Also:**

"OCI and Advanced Queuing" and "Publish-Subscribe Notification" in [Oracle Call Interface Programmer's Guide](../lnoci/introduction.md) for syntax details

#### Comparing Oracle Database Advanced Queuing Programmatic Interfaces

These topics list and compare the Oracle Database Advanced Queuing Administrative Interfaces and the Oracle Database Advanced Queuing Operational Interfaces.

Available functions for the Oracle Database Advanced Queuing programmatic interfaces are listed by use case in Table 3-2 through Table 3-9. Use cases are described in [Oracle Database Advanced Queuing Administrative Interface](aq-administrative-interface.md) through [Oracle Database Advanced Queuing Operations Using PL/SQL](aq-operations-using-pl-sql.md) and [Oracle Java Message Service Basic Operations](jms-basic-operation.md) through [Oracle Java Message Service Shared Interfaces](jms-shared-interfaces.md).

##### Oracle Database Advanced Queuing Administrative Interfaces

The table lists the equivalent Oracle Database Advanced Queuing administrative functions for the PL/SQL and Java (JMS) programmatic interfaces.

Table 3-2 Comparison of Oracle Database Advanced Queuing Programmatic Interfaces: Administrative Interface

| Use Case                                                                                | PL/SQL                                          | Java (JMS)                                                                                       |
|:----------------------------------------------------------------------------------------|:------------------------------------------------|:-------------------------------------------------------------------------------------------------|
| Create a connection factory                                                             | N/A                                             | `AQjmsFactory.getQueue`<br>`ConnectionFactory`<br>`AQjmsFactory.getTopic`<br>`ConnectionFactory` |
| Register a [ConnectionFactory](glossary.md) in an LDAP server                           | N/A                                             | `AQjmsFactory.register`<br>`ConnectionFactory`                                                   |
| Create a queue table                                                                    | `DBMS_AQADM.CREATE_QUEUE_TABLE`                 | `AQjmsSession.createQueueTable`                                                                  |
| Get a queue table                                                                       | Use `schema`.`queue_table_name`                 | `AQjmsSession.getQueueTable`                                                                     |
| Alter a queue table                                                                     | `DBMS_AQADM.ALTER_QUEUE_TABLE`                  | `AQQueueTable.alter`                                                                             |
| Drop a queue table                                                                      | `DBMS_AQADM.DROP_QUEUE_TABLE`                   | `AQQueueTable.drop`                                                                              |
| Create a queue                                                                          | `DBMS_AQADM.CREATE_QUEUE`                       | `AQjmsSession.createQueue`                                                                       |
| Get a queue                                                                             | Use `schema.queue_name`                         | `AQjmsSession.getQueue`                                                                          |
| Create a multiconsumer queue/topic in a queue table with multiple consumers enabled     | `DBMS_AQADM.CREATE_QUEUE`                       | `AQjmsSession.createTopic`                                                                       |
| Get a multiconsumer queue/topic                                                         | Use `schema.queue_name`                         | `AQjmsSession.getTopic`                                                                          |
| Alter a queue/topic                                                                     | `DBMS_AQADM.ALTER_QUEUE`                        | `AQjmsDestination.alter`                                                                         |
| Start a queue/topic                                                                     | `DBMS_AQADM.START_QUEUE`                        | `AQjmsDestination.start`                                                                         |
| Stop a queue/topic                                                                      | `DBMS_AQADM.STOP_QUEUE`                         | `AQjmsDestination.stop`                                                                          |
| Drop a queue/topic                                                                      | `DBMS_AQADM.DROP_QUEUE`                         | `AQjmsDestination.drop`                                                                          |
| Create a sharded queue                                                                  | `DBMS_AQADM.CREATE_SHARDED_QUEUE `              | `AQjmsDestination.createJMSShardedQueue`                                                         |
| Drop a sharded queue                                                                    | `DBMS_AQADM.DROP_SHARDED_QUEUE `                | `AQjmsDestination.dropJMSShardedQueue`                                                           |
| Alter a sharded queue                                                                   | `DBMS_AQADM.ALTER_SHARDED_QUEUE `               | None. Use PL/SQL API.                                                                            |
| Grant system privileges                                                                 | `DBMS_AQADM.GRANT_SYSTEM_`<br>`PRIVILEGE`       | `AQjmsSession.grantSystem`<br>`Privilege`                                                        |
| Revoke system privileges                                                                | `DBMS_AQADM.REVOKE_SYSTEM_`<br>`PRIVILEGE`      | `AQjmsSession.revokeSystem`<br>`Privilege`                                                       |
| Grant a queue/topic privilege                                                           | `DBMS_AQADM.GRANT_QUEUE_`<br>`PRIVILEGE`        | `AQjmsDestination.grantQueue`<br>`Privilege`<br>`AQjmsDestination.grantTopic`<br>`Privilege`     |
| Revoke a queue/topic privilege                                                          | `DBMS_AQADM.REVOKE_QUEUE_`<br>`PRIVILEGE`       | `AQjmsDestination.revokeQueue`<br>`Privilege`<br>`AQjmsDestination.revokeTopic`<br>`Privilege`   |
| Verify a queue type                                                                     | `DBMS_AQADM.VERIFY_QUEUE_TYPES`                 | Not supported                                                                                    |
| Add a subscriber                                                                        | `DBMS_AQADM.ADD_SUBSCRIBER`                     | See Table 3-6                                                                                    |
| Alter a subscriber                                                                      | `DBMS_AQADM.ALTER_SUBSCRIBER`                   | See Table 3-6                                                                                    |
| Remove a subscriber                                                                     | `DBMS_AQADM.REMOVE_SUBSCRIBER`                  | See Table 3-6                                                                                    |
| Schedule propagation                                                                    | `DBMS_AQADM.SCHEDULE_PROPAGATION`               | `AQjmsDestination.schedule`<br>`Propagation`                                                     |
| Enable a propagation schedule                                                           | `DBMS_AQADM.ENABLE_PROPAGATION_`<br>`SCHEDULE`  | `AQjmsDestination.enable`<br>`PropagationSchedule`                                               |
| Alter a propagation schedule                                                            | `DBMS_AQADM.ALTER_PROPAGATION_`<br>`SCHEDULE`   | `AQjmsDestination.alter`<br>`PropagationSchedule`                                                |
| Disable a propagation schedule                                                          | `DBMS_AQADM.DISABLE_PROPAGATION_`<br>`SCHEDULE` | `AQjmsDestination.disable`<br>`PropagationSchedule`                                              |
| Unschedule a propagation                                                                | `DBMS_AQADM.UNSCHEDULE_`<br>`PROPAGATION`       | `AQjmsDestination.unschedule`<br>`Propagation`                                                   |
| Create an Oracle Database Advanced Queuing Internet Agent                               | `DBMS_AQADM.CREATE_AQ_AGENT`                    | Not supported                                                                                    |
| Alter an Oracle Database Advanced Queuing Internet Agent                                | `DBMS_AQADM.ALTER_AQ_AGENT`                     | Not supported                                                                                    |
| Drop an Oracle Database Advanced Queuing Internet Agent                                 | `DBMS_AQADM.DROP_AQ_AGENT`                      | Not supported                                                                                    |
| Grant database user privileges to an Oracle Database Advanced Queuing Internet Agent    | `DBMS_AQADM.ENABLE_AQ_AGENT`                    | Not supported                                                                                    |
| Revoke database user privileges from an Oracle Database Advanced Queuing Internet Agent | `DBMS_AQADM.DISABLE_AQ_AGENT`                   | Not supported                                                                                    |
| Add alias for queue, agent, ConnectionFactory in a LDAP server                          | `DBMS_AQADM.ADD_ALIAS_TO_LDAP`                  | Not supported                                                                                    |
| Delete alias for queue, agent, ConnectionFactory in a LDAP server                       | `DBMS_AQADM.DEL_ALIAS_FROM_LDAP`                | Not supported                                                                                    |

##### Oracle Database Advanced Queuing Operational Interfaces

These tables list equivalent Oracle Database Advanced Queuing operational functions for the programmatic interfaces PL/SQL, OCI, Oracle Database Advanced Queuing XML Servlet, and JMS, for various use cases.

Table 3-3 Comparison of Oracle Database Advanced Queuing Programmatic Interfaces: Operational Interface—Create Connection, Session, Message Use Cases

| Use Case                                 | PL/SQL                                                | OCI                                    | AQ XML Servlet                                                                                                                                                                                                                                                                                                                                                                               | JMS                                                                                                                                                                                            |
|:-----------------------------------------|:------------------------------------------------------|:---------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Create a connection                      | N/A                                                   | `OCIServer`<br>`Attach`                | Open an HTTP connection after authenticating with the Web server                                                                                                                                                                                                                                                                                                                             | `AQjmsQueueConnectionFactory`<br>`.createQueueConnection`<br>`AQjmsTopicConnectionFactory`<br>`.createTopicConnection`                                                                         |
| Create a session                         | N/A                                                   | `OCISession`<br>`Begin`                | An HTTP servlet session is automatically started with the first SOAP request                                                                                                                                                                                                                                                                                                                 | `QueueConnection.createQueue`<br>`Session`<br>`TopicConnection.createTopic`<br>`Session`                                                                                                       |
| Create a RAW message                     | Use SQL RAW type for message                          | Use OCIRaw for Message                 | Supply the hex representation of the message payload in the XML message. For example, `<raw>023f4523</raw>`                                                                                                                                                                                                                                                                                  | Not supported                                                                                                                                                                                  |
| Create a message with structured data    | Use SQL Oracle [object type](glossary.md) for message | Use SQL Oracle object type for message | For Oracle object type queues that are not JMS queues (that is, they are not type `AQ$_JMS_*`), the XML specified in `<message payload>` must map to the SQL type of the payload for the queue table.<br>For JMS queues, the XML specified in the `<message_payload>` must be one of the following: `<jms_text_message>`, `<jms_map_message>`, `<jms_bytes_message>`, `<jms_object_message>` | `Session.createTextMessage`<br>`Session.createObjectMessage`<br>`Session.createMapMessage`<br>`Session.createBytesMessage`<br>`Session.createStreamMessage`<br>`AQjmsSession.createAdtMessage` |
| Create a message [producer](glossary.md) | N/A                                                   | N/A                                    | N/A                                                                                                                                                                                                                                                                                                                                                                                          | `QueueSession.createSender`<br>`TopicSession.createPublisher`                                                                                                                                  |

Table 3-4 Comparison of Oracle Database Advanced Queuing Programmatic Interfaces: Operational Interface—Enqueue Messages to a Single-Consumer Queue, Point-to-Point Model Use Cases

| Use Case                                                                                                                             | PL/SQL                                                                                      | OCI                                                                                                                   | AQ XML Servlet                                                                                                             | JMS                                                                                                                                                                                              |
|:-------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Enqueue a message to a single-consumer queue                                                                                         | `DBMS_AQ.enqueue`                                                                           | `OCIAQEnq`                                                                                                            | `<AQXmlSend>`                                                                                                              | `QueueSender.send`                                                                                                                                                                               |
| Enqueue a message to a queue and specify visibility options                                                                          | `DBMS_AQ.enqueue`<br>Specify visibility in<br>`ENQUEUE_OPTIONS`                             | `OCIAQEnq`<br>Specify `OCI_ATTR_VISIBILITY `in `OCIAQEnqOptions`<br>`OCIAQEnqOptions`                                 | `<AQXmlSend>`<br>Specify `<visibility>` in<br>`<producer_options>`                                                         | Not supported                                                                                                                                                                                    |
| Enqueue a message to a single-consumer queue and specify message properties priority and expiration                                  | `DBMS_AQ.enqueue`<br>Specify priority, expiration in<br>`MESSAGE_PROPERTIES`                | `OCIAQEnq`<br>Specify `OCI_ATTR_PRIORITY`, `OCI_ATTR_EXPIRATION` in<br>`OCIAQMsgProperties`                           | `<AQXmlSend>`<br>Specify `<priority>`, `<expiration> `in<br>`<message_header>`                                             | Specify `priority` and `TimeToLive` during<br>`QueueSender.send`<br>or<br>`.setTimeToLive`<br>and<br>`MessageProducer.`<br>`setPriority`<br>followed by<br>`QueueSender.send`                    |
| Enqueue a message to a single-consumer queue and specify message properties correlationID, delay, and [exception queue](glossary.md) | `DBMS_AQ.enqueue`<br>Specify correlation, delay, exception_queue in<br>`MESSAGE_PROPERTIES` | `OCIAQEnq`<br>Specify `OCI_ATTR_CORRELATION`, `OCI_ATTR_DELAY`, `OCI_ATTR_EXCEPTION_QUEUE` in<br>`OCIAQMsgProperties` | `<AQXmlSend>`<br>Specify `<correlation_id>`, `<delay>`, `<exception_queue> `in<br>`<message_header>`                       | `Message.setJMS`<br>`CorrelationI`<br>Delay and exception queue specified as provider specific message properties<br>`JMS_OracleDelay`<br>`JMS_OracleExcpQ`<br>followed by<br>`QueueSender.send` |
| Enqueue a message to a single-consumer queue and specify user-defined message properties                                             | Not supported<br>Properties should be part of payload                                       | Not supported<br>Properties should be part of payload                                                                 | `<AQXmlSend>`<br>Specify `<name>` and `<int_value>`, `<string_value>`, `<long_value>,` and so on in<br>`<user_properties>` | `Message.setInt`<br>`Property`<br>`Message.setString`<br>`Property`<br>`Message.setBoolean`<br>`Property`<br>and so forth, followed by<br>`QueueSender.send`                                     |
| Enqueue a message to a single-consumer queue and specify message [transformation](glossary.md)                                       | `DBMS_AQ.enqueue`<br>Specify transformation in<br>`ENQUEUE_OPTIONS`                         | `OCIAQEnq`<br>Specify `OCI_ATTR_TRANSFORMATION` in<br>`OCIAQEnqOptions`                                               | `<AQXmlSend>`<br>Specify `<transformation>` in<br>`<producer_options>`                                                     | `AQjmsQueueSender.`<br>`setTransformation`<br>followed by<br>`QueueSender.send`                                                                                                                  |

Table 3-5 Comparison of Oracle Database Advanced Queuing Programmatic Interfaces: Operational Interface—Publish Messages to a Multiconsumer Queue/Topic, Publish/Subscribe Model Use Cases

| Use Case                                                                                                            | PL/SQL                                                                                        | OCI                                                                                                                   | AQ XML Servlet                                                                                                                | JMS                                                                                                                                                                                                                        |
|:--------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Publish a message to a multiconsumer queue/topic using default subscription list                                    | `DBMS_AQ.enqueue`<br>Set `recipient_list` to `NULL` in<br>`MESSAGE_PROPERTIES`                | `OCIAQEnq`<br>Set `OCI_ATTR_RECIPIENT_LIST` to `NULL` in<br>`OCIAQMsgProperties`                                      | `<AQXmlPublish>`                                                                                                              | `TopicPublisher.`<br>`publish`                                                                                                                                                                                             |
| Publish a message to a multiconsumer queue/topic using specific recipient list<br>See footnote-1                    | `DBMS_AQ.enqueue`<br>Specify recipient list in<br>`MESSAGE_PROPERTIES`                        | `OCIAQEnq`<br>Specify `OCI_ATTR_RECIPIENT_LIST` in<br>`OCIAQMsgProperties`                                            | `<AQXmlPublish>`<br>Specify `<recipient_list>` in<br>`<message_header>`                                                       | `AQjmsTopic`<br>`Publisher.publish`<br>Specify recipients as an array of `AQjmsAgent`                                                                                                                                      |
| Publish a message to a multiconsumer queue/topic and specify message properties priority and expiration             | `DBMS_AQ.enqueue`<br>Specify priority, expiration in<br>`MESSAGE_PROPERTIES`                  | `OCIAQEnq`<br>Specify `OCI_ATTR_PRIORITY`, `OCI_ATTR_EXPIRATION` in<br>`OCIAQMsgProperties`                           | `<AQXmlPublish>`<br>Specify `<priority>`, `<expiration>` in<br>`<message_header>`                                             | Specify `priority` and `TimeToLive` during<br>`TopicPublisher.`<br>`publish`<br>or<br>`MessageProducer.`<br>`setTimeToLive`<br>and<br>`MessageProducer.`<br>`setPriority`<br>followed by<br>`TopicPublisher.`<br>`publish` |
| Publish a message to a multiconsumer queue/topic and specify send options correlationID, delay, and exception queue | `DBMS_AQ.enqueue`<br>Specify correlation, delay, `exception_queue` in<br>`MESSAGE_PROPERTIES` | `OCIAQEnq`<br>Specify `OCI_ATTR_CORRELATION`, `OCI_ATTR_DELAY`, `OCI_ATTR_EXCEPTION_QUEUE` in<br>`OCIAQMsgProperties` | `<AQXmlPublish>`<br>Specify `<correlation_id>`, `<delay>`, `<exception_queue>` in<br>`<message_header>`                       | `Message.setJMS`<br>`CorrelationID`<br>Delay and exception queue specified as provider-specific message properties<br>`JMS_OracleDelay`<br>`JMS_OracleExcpQ`<br>followed by<br>`TopicPublisher.`<br>`publish`              |
| Publish a message to a topic and specify user-defined message properties                                            | Not supported<br>Properties should be part of payload                                         | Not supported<br>Properties should be part of payload                                                                 | `<AQXmlPublish>`<br>Specify `<name>` and `<int_value>`, `<string_value>`, `<long_value>,` and so on in<br>`<user_properties>` | `Message.setInt`<br>`Property`<br>`Message.setString`<br>`Property`<br>`Message.setBoolean`<br>`Property`<br>and so forth, followed by<br>`TopicPublisher.`<br>`publish`                                                   |
| Publish a message to a topic and specify message transformation                                                     | `DBMS_AQ.enqueue`<br>Specify transformation in<br>`ENQUEUE_OPTIONS`                           | `OCIAQEnq`<br>Specify `OCI_ATTR_TRANSFORMATION` in<br>`OCIAQEnqOptions`                                               | `<AQXmlPublish>`<br>Specify `<transformation>` in<br>`<producer_options>`                                                     | `AQjmsTopic`<br>`Publisher.set`<br>`Transformation`<br>followed by<br>`TopicPublisher.`<br>`publish`                                                                                                                       |

Table 3-6 Comparison of Oracle Database Advanced Queuing Programmatic Interfaces: Operational Interface—Subscribing for Messages in a Multiconsumer Queue/Topic, Publish/Subscribe Model Use Cases

| Use Case            | PL/SQL                        | OCI           | AQ XML Servlet | JMS                                                                                                                                |
|:--------------------|:------------------------------|:--------------|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| Add a subscriber    | See administrative interfaces | Not supported | Not supported  | `TopicSession.`<br>`createDurable`<br>`Subscriber`<br>`AQjmsSession.`<br>`createDurable`<br>`Subscriber`                           |
| Alter a subscriber  | See administrative interfaces | Not supported | Not supported  | `TopicSession.`<br>`createDurable`<br>`Subscriber`<br>`AQjmsSession.`<br>`createDurable`<br>`Subscriber`<br>using the new selector |
| Remove a subscriber | See administrative interfaces | Not supported | Not supported  | `AQjmsSession.`<br>`unsubscribe`                                                                                                   |

Table 3-7 Comparison of Oracle Database Advanced Queuing Programmatic Interfaces: Operational Interface—Browse Messages in a Queue Use Cases

| Use Case                                                          | PL/SQL                                                                            | OCI                                                                       | AQ XML Servlet                                                                   | JMS                                                                                                                                                                                                                    |
|:------------------------------------------------------------------|:----------------------------------------------------------------------------------|:--------------------------------------------------------------------------|:---------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Browse messages in a queue/topic                                  | `DBMS_AQ.`<br>`dequeue`<br>Set `dequeue_mode` to `BROWSE` in<br>`DEQUEUE_OPTIONS` | `OCIAQDeq`<br>Set `OCI_ATTR_DEQ_MODE` to `BROWSE` in<br>`OCIAQDeqOptions` | `<AQXmlReceive>`<br>Specify `<dequeue_mode>` `BROWSE` in<br>`<consumer_options>` | `QueueSession.createBrowser`<br>`QueueBrowser.getEnumeration`<br>Not supported on topics<br>`oracle.jms.AQjmsSession.`<br>`createBrowser`<br>`oracle.jms.TopicBrowser.`<br>`getEnumeration`                            |
| Browse messages in a queue/topic and lock messages while browsing | `DBMS_AQ.dequeue`<br>Set `dequeue_mode` to `LOCKED` in<br>`DEQUEUE_OPTIONS`       | `OCIAQDeq`<br>Set `OCI_ATTR_DEQ_MODE` to `LOCKED` in<br>`OCIAQDeqOptions` | `<AQXmlReceive>`<br>Specify `<dequeue_mode> LOCKED `in<br>`<consumer_options>`   | `AQjmsSession.createBrowser`<br>set `locked` to `TRUE`.<br>`QueueBrowser.getEnumeration`<br>Not supported on topics<br>`oracle.jms.AQjmsSession.`<br>`createBrowser`<br>`oracle.jms.TopicBrowser.`<br>`getEnumeration` |

Table 3-8 Comparison of Oracle Database Advanced Queuing Programmatic Interfaces: Operational Interface—Receive Messages from a Queue/Topic Use Cases

| Use Case                                                                   | PL/SQL                                                                                                                   | OCI                                                                                                                             | AQ XML Servlet                                                            | JMS                                                                                                                                                                                                                                                        |
|:---------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Start a connection for receiving messages                                  | N/A                                                                                                                      | N/A                                                                                                                             | N/A                                                                       | `Connection.start`                                                                                                                                                                                                                                         |
| Create a message consumer                                                  | N/A                                                                                                                      | N/A                                                                                                                             | N/A                                                                       | `QueueSession.`<br>`createQueueReceiver`<br>`TopicSession.create`<br>`DurableSubscriber `<br>`AQjmsSession.create`<br>`TopicReceiver`                                                                                                                      |
| Dequeue a message from a queue/topic and specify visibility                | `DBMS_AQ.dequeue`<br>Specify visibility in<br>`DEQUEUE_OPTIONS`                                                          | `OCIAQDeq`<br>Specify `OCI_ATTR_VISIBILITY` in<br>`OCIAQDeqOptions`                                                             | `<AQXmlReceive>`<br>Specify `<visibility> `in<br>`<consumer_options>`     | Not supported                                                                                                                                                                                                                                              |
| Dequeue a message from a queue/topic and specify transformation            | `DBMS_AQ.dequeue`<br>Specify transformation in<br>`DEQUEUE_OPTIONS`                                                      | `OCIAQDeq`<br>Specify `OCI_ATTR_TRANSFORMATION` in<br>`OCIAQDeqOptions`                                                         | `<AQXmlReceive>`<br>Specify `<transformation>` in<br>`<consumer_options>` | `AQjmsQueueReceiver.`<br>`setTransformation`<br>`AQjmsTopicSubscriber.`<br>`setTransformation`<br>`AQjmsTopicReceiver.`<br>`setTransformation`                                                                                                             |
| Dequeue a message from a queue/topic and specify navigation mode           | `DBMS_AQ.dequeue`<br>Specify navigation in<br>`DEQUEUE_OPTIONS`                                                          | `OCIAQDeq`<br>Specify `OCI_ATTR_NAVIGATION` in<br>`OCIAQDeqOptions`                                                             | `<AQXmlReceive>`<br>Specify `<navigation>` in<br>`<consumer_options>`     | `AQjmsQueueReceiver.`<br>`setNavigationMode`<br>`AQjmsTopicSubscriber.`<br>`setNavigationMode`<br>`AQjmsTopicReceiver.`<br>`setNavigationMode`                                                                                                             |
| Dequeue a message from a single-consumer queue                             | `DBMS_AQ.dequeue`<br>Set `dequeue_mode` to `REMOVE` in<br>`DEQUEUE_OPTIONS`                                              | `OCIAQDeq`<br>Set `OCI_ATTR_DEQ_MODE` to `REMOVE` in<br>`OCIAQDeqOptions`                                                       | `<AQXmlReceive>`                                                          | `QueueReceiver.receive`<br>or<br>`QueueReceiver.receive`<br>`NoWait`<br>or<br>`AQjmsQueueReceiver.`<br>`receiveNoData`                                                                                                                                     |
| Dequeue a message from a multiconsumer queue/topic using subscription name | `DBMS_AQ.dequeue`<br>Set `dequeue_mode` to `REMOVE` and set `consumer_name` to subscription name in<br>`DEQUEUE_OPTIONS` | `OCIAQDeq`<br>Set `OCI_ATTR_DEQ_MODE` to `REMOVE` and set `OCI_ATTR_CONSUMER_NAME` to subscription name in<br>`OCIAQDeqOptions` | `<AQXmlReceive>`<br>Specify `<consumer_name> `in<br>`<consumer_options>`  | Create a durable TopicSubscriber on the topic using the subscription name, then<br>`TopicSubscriber.`<br>`receive`<br>or<br>`TopicSubscriber.`<br>`receiveNoWait`<br>or<br>`AQjmsTopicSubscriber.`<br>`receiveNoData`                                      |
| Dequeue a message from a multiconsumer queue/topic using recipient name    | `DBMS_AQ.dequeue`<br>Set `dequeue_mode` to `REMOVE` and set `consumer_name` to recipient name in<br>`DEQUEUE_OPTIONS`    | `OCIAQDeq`<br>Set `OCI_ATTR_DEQ_MODE` to `REMOVE` and set `OCI_ATTR_CONSUMER_NAME` to recipient name in<br>`OCIAQDeqOptions`    | `<AQXmlReceive>`<br>Specify `<consumer_name>` in<br>`<consumer_options>`  | Create a `TopicReceiver` on the topic using the recipient name, then<br>`AQjmsSession.create`<br>`TopicReceiver`<br>`AQjmsTopicReceiver.`<br>`receive`<br>or<br>`AQjmsTopicReceiver.`<br>`receiveNoWait`<br>or<br>`AQjmsTopicReceiver.`<br>`receiveNoData` |

Table 3-9 Comparison of Oracle Database Advanced Queuing Programmatic Interfaces: Operational Interface—Register to Receive Messages Asynchronously from a Queue/Topic Use Cases

| Use Case                                                         | PL/SQL                                                                        | OCI                                                                                                                             | AQ XML Servlet                                                                                                                         | JMS                                                                                                                         |
|:-----------------------------------------------------------------|:------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------|
| Receive messages asynchronously from a single-consumer queue     | Define a PL/SQL callback procedure<br>Register it using<br>`DBMS_AQ.REGISTER` | `OCISubscription`<br>`Register`<br>Specify `queue_name` as subscription name<br>`OCISubscription`<br>`Enable`                   | `<AQXmlRegister>`<br>Specify queue name in `<destination>` and notification mechanism in<br>`<notify_url>`                             | Create a `QueueReceiver` on the queue, then<br>`QueueReceiver.set`<br>`MessageListener`                                     |
| Receive messages asynchronously from a multiconsumer queue/topic | Define a PL/SQL callback procedure<br>Register it using<br>`DBMS_AQ.REGISTER` | `OCISubscription`<br>`Register`<br>Specify `queue:OCI_ATTR_CONSUMER_NAME` as subscription name<br>`OCISubscription`<br>`Enable` | `<AQXmlRegister>`<br>Specify queue name in `<destination>`, consumer in `<consumer_name>` and notification mechanism in `<notify_url>` | Create a `TopicSubscriber` or `TopicReceiver` on the topic, then<br>`TopicSubscriber.`<br>`setMessageListener`              |
| Listen for messages on multiple queues/topics                    | \-                                                                            | \-                                                                                                                              | \-                                                                                                                                     | \-                                                                                                                          |
| Listen for messages on one (many) single-consumer queues         | `DBMS_AQ.LISTEN`<br>Use `agent_name` as `NULL` for all agents in `agent_list` | `OCIAQListen`<br>Use `agent_name` as `NULL` for all agents in `agent_list`                                                      | Not supported                                                                                                                          | Create multiple `QueueReceivers` on a `QueueSession`, then<br>`QueueSession.set`<br>`MessageListener`                       |
| Listen for messages on one (many) multiconsumer queues/Topics    | `DBMS_AQ.LISTEN`<br>Specify `agent_name` for all agents in `agent_list`       | `OCIAQListen`<br>Specify `agent_name` for all agents in `agent_list`                                                            | Not supported                                                                                                                          | Create multiple `TopicSubscribers` or `TopicReceivers` on a `TopicSession`, then<br>`TopicSession.set`<br>`MessageListener` |

### Using OCCI to Access Oracle Database Advanced Queuing

C++ applications can use OCCI, which has a set of Oracle Database Advanced Queuing interfaces that enable messaging clients to access Oracle Database Advanced Queuing.

OCCI AQ supports all the operational functions required to send/receive and publish/subscribe messages in a message-enabled database. Synchronous and asynchronous message consumption is available, based on a message selection rule. Sharded queues do not support OCCI clients.

**See Also:**

"Oracle Database Advanced Queuing" in [Oracle C++ Call Interface Programmer's Guide](../lncpp/object-type-translator-utility.md)

### Using Oracle Java Message Service (Oracle JMS) to Access Oracle Database Advanced Queuing

Java Message Service (JMS) is a messaging standard defined by Sun Microsystems, Oracle, IBM, and other vendors. JMS is a set of interfaces and associated semantics that define how a JMS client accesses the facilities of an enterprise messaging product. Oracle Java Message Service (Oracle JMS) provides a Java API for Oracle Database Advanced Queuing based on the JMS standard.

[Oracle Java Message Service](glossary.md) (Oracle JMS) supports the standard JMS interfaces and has extensions to support administrative operations and other features that are not a part of the standard.

Standard [Java Message Service](glossary.md)(JMS) features include:

- Point-to-point model of communication using queues

- Publish/subscribe model of communication using topics

- `ObjectMessage`, `StreamMessage`, `TextMessage`, `BytesMessage`, and `MapMessage` message types

- Asynchronous and [synchronous](glossary.md) delivery of messages

- Message selection based on message header fields or properties

Oracle JMS extensions include:

- Administrative API to create queue tables, queues and topics

- Point-to-multipoint communication using [recipient](glossary.md) lists for topics

- Message propagation between destinations, which allows the application to define remote subscribers

- Support for transactional sessions, enabling JMS and SQL operations in one transaction

- Message retention after messages have been dequeued

- Message delay, allowing messages to be made visible after a certain delay

- Exception handling, allowing messages to be moved to exception queues if they cannot be processed successfully

- Support for `AdtMessage`

  These are stored in the database as Oracle objects, so the payload of the message can be queried after it is enqueued. Subscriptions can be defined on the contents of these messages as opposed to just the message properties.

- Topic browsing

  This allows durable subscribers to browse through the messages in a publish/subscribe (topic) destination. It optionally allows these subscribers to purge the browsed messages, so they are no longer retained by Oracle Database Advanced Queuing for that subscriber.

  **See Also:**

  - Java Message Service Specification, version 1.1, March 18, 2002, Sun Microsystems, Inc.

  - [Oracle Database Advanced Queuing Java API Reference](../jajms/index.md)

#### Accessing Standard and Oracle JMS Applications

Standard JMS interfaces are in the `javax.jms` package. Oracle JMS interfaces are in the `oracle.jms` package. You must have `EXECUTE` privilege on the `DBMS_AQIN` and `DBMS_AQJMS` packages to use the Oracle JMS interfaces. You can also acquire these rights through the `AQ_USER_ROLE` or the `AQ_ADMINSTRATOR_ROLE`. You also need the appropriate system and queue or topic privileges to [send](glossary.md) or receive messages.

Because Oracle JMS uses [Java Database Connectivity](glossary.md) (JDBC) to connect to the database, its applications can run outside the database using the JDBC OCI driver or JDBC thin driver.

#### Using JDBC OCI Driver or JDBC Thin Driver

To use JMS with clients running outside the database, you must include the appropriate [JDBC driver](glossary.md), [Java Naming and Directory Interface](glossary.md) (JNDI) jar files, and Oracle Database Advanced Queuing jar files in your CLASSPATH.

Note that the Oracle Database does not support JDK 1.2, JDK 1.3, JDK 1.4, JDK5.n and all classes12\*.\* files. You need to use the `ojdbc6.jar `and ` ojbc7.jar` files with JDK 6.n and JDK 7.n, respectively. The following jar and zip files should be in the `CLASSPATH` based on the release of JDK you are using.

For JDK 1.5.x, the `CLASSPATH` must contain:

    ORACLE_HOME/jdbc/lib/ojdbc6.jar

For JDK 1.6.x, the `CLASSPATH` must contain:

    ORACLE_HOME/jdbc/lib/ojdbc7.jar

The following files are used for either JDK version:

    ORACLE_HOME/lib/jta.jar
    ORACLE_HOME/xdk/lib/xmlparserv2.jar
    ORACLE_HOME/rdbms/jlib/xdb.jar
    ORACLE_HOME/rdbms/jlib/aqapi.jar
    ORACLE_HOME/rdbms/jlib/jmscommon.jar

#### Using Oracle Server Driver in JServer

If your application is running inside the [JServer](glossary.md), then you should be able to access the Oracle JMS classes that have been automatically loaded when the JServer was installed. If these classes are not available, then you must load `jmscommon.jar` followed by `aqapi.jar` using the `$ORACLE_HOME/rdbms/admin/initjms` SQL script.

### Using Oracle Database Advanced Queuing XML Servlet to Access Oracle Database Advanced Queuing

You can use Oracle Database Advanced Queuing XML servlet to access Oracle Database Advanced Queuing over HTTP using Simple Object Access Protocol (SOAP) and an Oracle Database Advanced Queuing XML message format called Internet Data Access Presentation (IDAP).

Using the Oracle Database Advanced Queuing servlet, a client can perform the following actions:

- Send messages to single-consumer queues

- Publish messages to multiconsumer queues/topics

- Receive messages from queues

- Register to receive message notifications
