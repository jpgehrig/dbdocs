Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Package](../../javax/jms/package-summary.md)
- Next Package

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Package oracle.jms

This package is an Oracle implementation of JMS 1.1 standard on top of Oracle® Database Advanced Queuing.

See: Description

- **Interface Summary**

  | Interface                                       | Description                                                                                                                                                                                                  |
  |-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AdtMessage](AdtMessage.md)                     | Adds Oracle® Database Advanced Queuing extensions to `javax.jms.Message`.                                                                                                                                    |
  | [AQjmsQueueReceiver](AQjmsQueueReceiver.md)     | Adds Oracle® Database Advanced Queuing extensions to `javax.jms.QueueReceiver`.                                                                                                                              |
  | [AQjmsQueueSender](AQjmsQueueSender.md)         | Adds Oracle® Database Advanced Queuing extensions to `javax.jms.QueueSender`<br>Allows use of transformations                                                                                                |
  | [AQjmsTopicPublisher](AQjmsTopicPublisher.md)   | Adds Oracle® Database Advanced Queuing specific extensions to `javax.jms.TopicPublisher`<br>Allows point to point publishing and use of transformations.                                                     |
  | [AQjmsTopicReceiver](AQjmsTopicReceiver.md)     | Oracle Advanced Queueing allows messages to be sent to all subscribers of a topic (standard JMS behaviour) or to a set of specific recipients (These recipients may or may not be subscribers of the topic). |
  | [AQjmsTopicSubscriber](AQjmsTopicSubscriber.md) | Adds Oracle® Database Advanced Queuing extensions to javax.jms.TopicSubscriber<br>Allows use of navigation mode and methods to consume message without returning it to user.                                 |
  | [TopicBrowser](TopicBrowser.md)                 | Allows browsing of messages on a Topic.                                                                                                                                                                      |
  | [TopicReceiver](TopicReceiver.md)               | Extends `javax.jms.MessageConsumer` to allow point to multipoint communication, which is an Oracle® Database Advanced Queuing specific variation of publish subscribe                                        |

- **Class Summary**

  | Class                                                             | Description                                                                                                                                      |
  |-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AQjmsAdtMessage](AQjmsAdtMessage.md)                             | This is an Oracle class which implements `oracle.jms.AdtMessage`.                                                                                |
  | [AQjmsBytesMessage](AQjmsBytesMessage.md)                         | This is an Oracle class which implements `javax.jms.BytesMessage`.                                                                               |
  | [AQjmsConnection](AQjmsConnection.md)                             | This is an Oracle class which implements `javax.jms.QueueConnection` and `javax.jms.TopicConnection`.                                            |
  | [AQjmsConnectionFactory](AQjmsConnectionFactory.md)               | This is an Oracle class which implements `javax.jms.ConnectionFactory` and `javax.naming.spi.ObjectFactory`.                                     |
  | [AQjmsConnectionMetaData](AQjmsConnectionMetaData.md)             | This is an Oracle class which implements `javax.jms.ConnectionMetaData`.                                                                         |
  | [AQjmsConsumer](AQjmsConsumer.md)                                 | This is an Oracle class which implements `oracle.jms.AQjmsQueueReceiver`, `oracle.jms.AQjmsTopicSubscriber` and `oracle.jms.AQjmsTopicReceiver`. |
  | [AQjmsDestination](AQjmsDestination.md)                           | This is an Oracle class which implements `javax.jms.Queue`, `javax.jms.Topic` and `java.io.Serializable`.                                        |
  | [AQjmsDestinationFactory](AQjmsDestinationFactory.md)             | This is an Oracle class which implements `javax.naming.spi.ObjectFactory`.                                                                       |
  | [AQjmsDestinationProperty](AQjmsDestinationProperty.md)           | This is an Oracle class which extends `oracle.jms.AQQueueProperty`.                                                                              |
  | [AQjmsFactory](AQjmsFactory.md)                                   | Class `AQjmsFactory` is an adaptor for accessing Oracle JMS administered objects.                                                                |
  | [AQjmsMapMessage](AQjmsMapMessage.md)                             | This is an Oracle class which implements `javax.jms.MapMessage`.                                                                                 |
  | [AQjmsMessage](AQjmsMessage.md)                                   | This is an Oracle class which implements `javax.jms.Message`.                                                                                    |
  | [AQjmsObjectMessage](AQjmsObjectMessage.md)                       | This is an Oracle class which implements `javax.jms.ObjectMessage`.                                                                              |
  | [AQjmsProducer](AQjmsProducer.md)                                 | This is an Oracle class which implements `javax.jms.MessageProducer`.                                                                            |
  | [AQjmsQueueBrowser](AQjmsQueueBrowser.md)                         | This is an Oracle class which implements `javax.jms.QueueBrowser` and `java.util.Enumeration`.                                                   |
  | [AQjmsQueueConnectionFactory](AQjmsQueueConnectionFactory.md)     | This is an Oracle class which implements `javax.jms.QueueConnectionFactory`.                                                                     |
  | [AQjmsSession](AQjmsSession.md)                                   | This is an Oracle class which implements `javax.jms.Session`, `javax.jms.QueueSession` and `javax.jms.TopicSession`.                             |
  | [AQjmsStreamMessage](AQjmsStreamMessage.md)                       | Oracle class implementing javax.jms.StreamMessage                                                                                                |
  | [AQjmsTextMessage](AQjmsTextMessage.md)                           | This is an Oracle class which implements `javax.jms.TextMessage`.                                                                                |
  | [AQjmsTopicBrowser](AQjmsTopicBrowser.md)                         | This is an Oracle class which implements `javax.jms.TopicBrowser` and `java.util.Enumeration`.                                                   |
  | [AQjmsTopicConnectionFactory](AQjmsTopicConnectionFactory.md)     | This is an Oracle class which implements `javax.jms.TopicConnectionFactory`.                                                                     |
  | [AQjmsXAConnection](AQjmsXAConnection.md)                         | Oracle class implementing javax.jms.XAConnection, javax.jms.XAQueueConnection, javax.jms.XATopicConnection                                       |
  | [AQjmsXAConnectionFactory](AQjmsXAConnectionFactory.md)           | Oracle class implementing javax.jms.XAConnectionFactory                                                                                          |
  | [AQjmsXAQueueConnectionFactory](AQjmsXAQueueConnectionFactory.md) | Oracle class implementing `javax.jms.XAQueueConnectionFactory`                                                                                   |
  | [AQjmsXASession](AQjmsXASession.md)                               | This is an Oracle class which implements `javax.jms.XASession`, `javax.jms.XAQueueSession` and `javax.jms.XATopicSession`.                       |
  | [AQjmsXATopicConnectionFactory](AQjmsXATopicConnectionFactory.md) | Oracle class implementing `javax.jms.XATopicConnectionFactory`                                                                                   |

- **Exception Summary**

  | Exception                                     | Description                                                                                                           |
  |-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
  | [AQjmsException](AQjmsException.md)           | This is an Oracle class which extends `javax.jms.JMSException` and adds Oracle® Database Advanced Queuing extensions. |
  | [AQjmsParseException](AQjmsParseException.md) | This is an Oracle class which extends `javax.jms.JMSException`.                                                       |

## Package oracle.jms Description

This package is an Oracle implementation of JMS 1.1 standard on top of Oracle® Database Advanced Queuing. It also provides the API to extension messaging features of Oracle® Database Advanced Queuing.

Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Package](../../javax/jms/package-summary.md)
- Next Package

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
