Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev](../../javax/jms/package-tree.md)
- Next

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Hierarchy For Package oracle.jms

Package Hierarchies:

- [All Packages](../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - oracle.jms.[AQjmsConnectionFactory](AQjmsConnectionFactory.md) (implements javax.jms.[ConnectionFactory](../../javax/jms/ConnectionFactory.md), javax.naming.spi.ObjectFactory, java.io.Serializable)
    - oracle.jms.[AQjmsQueueConnectionFactory](AQjmsQueueConnectionFactory.md) (implements javax.jms.[QueueConnectionFactory](../../javax/jms/QueueConnectionFactory.md), java.io.Serializable)
      - oracle.jms.[AQjmsXAQueueConnectionFactory](AQjmsXAQueueConnectionFactory.md) (implements javax.jms.[XAQueueConnectionFactory](../../javax/jms/XAQueueConnectionFactory.md))
    - oracle.jms.[AQjmsTopicConnectionFactory](AQjmsTopicConnectionFactory.md) (implements java.io.Serializable, javax.jms.[TopicConnectionFactory](../../javax/jms/TopicConnectionFactory.md))
      - oracle.jms.[AQjmsXATopicConnectionFactory](AQjmsXATopicConnectionFactory.md) (implements javax.jms.[XATopicConnectionFactory](../../javax/jms/XATopicConnectionFactory.md))
    - oracle.jms.[AQjmsXAConnectionFactory](AQjmsXAConnectionFactory.md) (implements javax.jms.[XAConnectionFactory](../../javax/jms/XAConnectionFactory.md))
  - oracle.jms.[AQjmsConnectionMetaData](AQjmsConnectionMetaData.md) (implements javax.jms.[ConnectionMetaData](../../javax/jms/ConnectionMetaData.md))
  - oracle.jms.[AQjmsDestination](AQjmsDestination.md) (implements javax.jms.[Queue](../../javax/jms/Queue.md), java.io.Serializable, javax.jms.[TemporaryQueue](../../javax/jms/TemporaryQueue.md), javax.jms.[TemporaryTopic](../../javax/jms/TemporaryTopic.md), javax.jms.[Topic](../../javax/jms/Topic.md))
  - oracle.jms.[AQjmsDestinationFactory](AQjmsDestinationFactory.md) (implements javax.naming.spi.ObjectFactory)
  - oracle.jms.[AQjmsFactory](AQjmsFactory.md)
  - oracle.jms.[AQjmsMessage](AQjmsMessage.md) (implements javax.jms.[Message](../../javax/jms/Message.md))
    - oracle.jms.[AQjmsAdtMessage](AQjmsAdtMessage.md) (implements oracle.jms.[AdtMessage](AdtMessage.md))
    - oracle.jms.[AQjmsBytesMessage](AQjmsBytesMessage.md) (implements javax.jms.[BytesMessage](../../javax/jms/BytesMessage.md))
    - oracle.jms.[AQjmsMapMessage](AQjmsMapMessage.md) (implements javax.jms.[MapMessage](../../javax/jms/MapMessage.md))
    - oracle.jms.[AQjmsObjectMessage](AQjmsObjectMessage.md) (implements javax.jms.[ObjectMessage](../../javax/jms/ObjectMessage.md))
    - oracle.jms.[AQjmsStreamMessage](AQjmsStreamMessage.md) (implements javax.jms.[StreamMessage](../../javax/jms/StreamMessage.md))
    - oracle.jms.[AQjmsTextMessage](AQjmsTextMessage.md) (implements javax.jms.[TextMessage](../../javax/jms/TextMessage.md))
  - oracle.jms.AQjmsObject
    - oracle.jms.[AQjmsConnection](AQjmsConnection.md) (implements javax.jms.[QueueConnection](../../javax/jms/QueueConnection.md), javax.jms.[TopicConnection](../../javax/jms/TopicConnection.md))
      - oracle.jms.[AQjmsXAConnection](AQjmsXAConnection.md) (implements javax.jms.[XAConnection](../../javax/jms/XAConnection.md), javax.jms.[XAQueueConnection](../../javax/jms/XAQueueConnection.md), javax.jms.[XATopicConnection](../../javax/jms/XATopicConnection.md))
    - oracle.jms.[AQjmsConsumer](AQjmsConsumer.md) (implements oracle.jms.[AQjmsQueueReceiver](AQjmsQueueReceiver.md), oracle.jms.[AQjmsTopicReceiver](AQjmsTopicReceiver.md), oracle.jms.[AQjmsTopicSubscriber](AQjmsTopicSubscriber.md))
    - oracle.jms.[AQjmsProducer](AQjmsProducer.md) (implements javax.jms.[MessageProducer](../../javax/jms/MessageProducer.md))
    - oracle.jms.[AQjmsQueueBrowser](AQjmsQueueBrowser.md) (implements java.util.Enumeration, javax.jms.[QueueBrowser](../../javax/jms/QueueBrowser.md))
    - oracle.jms.[AQjmsSession](AQjmsSession.md) (implements javax.jms.[QueueSession](../../javax/jms/QueueSession.md), javax.jms.[TopicSession](../../javax/jms/TopicSession.md))
      - oracle.jms.[AQjmsXASession](AQjmsXASession.md) (implements javax.jms.[XAQueueSession](../../javax/jms/XAQueueSession.md), javax.jms.[XASession](../../javax/jms/XASession.md), javax.jms.[XATopicSession](../../javax/jms/XATopicSession.md))
    - oracle.jms.[AQjmsTopicBrowser](AQjmsTopicBrowser.md) (implements java.util.Enumeration, oracle.jms.[TopicBrowser](TopicBrowser.md))
  - oracle.AQ.AQQueueProperty (implements java.io.Serializable)
    - oracle.jms.[AQjmsDestinationProperty](AQjmsDestinationProperty.md)
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - javax.jms.[JMSException](../../javax/jms/JMSException.md)
        - oracle.jms.[AQjmsException](AQjmsException.md)
        - oracle.jms.[AQjmsParseException](AQjmsParseException.md)

## Interface Hierarchy

- javax.jms.[Message](../../javax/jms/Message.md)
  - oracle.jms.[AdtMessage](AdtMessage.md)
- javax.jms.[MessageConsumer](../../javax/jms/MessageConsumer.md)
  - javax.jms.[QueueReceiver](../../javax/jms/QueueReceiver.md)
    - oracle.jms.[AQjmsQueueReceiver](AQjmsQueueReceiver.md)
  - oracle.jms.[TopicReceiver](TopicReceiver.md)
    - oracle.jms.[AQjmsTopicReceiver](AQjmsTopicReceiver.md)
  - javax.jms.[TopicSubscriber](../../javax/jms/TopicSubscriber.md)
    - oracle.jms.[AQjmsTopicSubscriber](AQjmsTopicSubscriber.md)
- javax.jms.[MessageProducer](../../javax/jms/MessageProducer.md)
  - javax.jms.[QueueSender](../../javax/jms/QueueSender.md)
    - oracle.jms.[AQjmsQueueSender](AQjmsQueueSender.md)
  - javax.jms.[TopicPublisher](../../javax/jms/TopicPublisher.md)
    - oracle.jms.[AQjmsTopicPublisher](AQjmsTopicPublisher.md)
- oracle.jms.[TopicBrowser](TopicBrowser.md)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev](../../javax/jms/package-tree.md)
- Next

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
