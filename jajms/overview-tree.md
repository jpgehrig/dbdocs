Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Tree
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Hierarchy For All Packages

Package Hierarchies:

- [javax.jms](javax/jms/package-tree.md),
- [oracle.jms](oracle/jms/package-tree.md)

## Class Hierarchy

- java.lang.Object
  - oracle.jms.[AQjmsConnectionFactory](oracle/jms/AQjmsConnectionFactory.md) (implements javax.jms.[ConnectionFactory](javax/jms/ConnectionFactory.md), javax.naming.spi.ObjectFactory, java.io.Serializable)
    - oracle.jms.[AQjmsQueueConnectionFactory](oracle/jms/AQjmsQueueConnectionFactory.md) (implements javax.jms.[QueueConnectionFactory](javax/jms/QueueConnectionFactory.md), java.io.Serializable)
      - oracle.jms.[AQjmsXAQueueConnectionFactory](oracle/jms/AQjmsXAQueueConnectionFactory.md) (implements javax.jms.[XAQueueConnectionFactory](javax/jms/XAQueueConnectionFactory.md))
    - oracle.jms.[AQjmsTopicConnectionFactory](oracle/jms/AQjmsTopicConnectionFactory.md) (implements java.io.Serializable, javax.jms.[TopicConnectionFactory](javax/jms/TopicConnectionFactory.md))
      - oracle.jms.[AQjmsXATopicConnectionFactory](oracle/jms/AQjmsXATopicConnectionFactory.md) (implements javax.jms.[XATopicConnectionFactory](javax/jms/XATopicConnectionFactory.md))
    - oracle.jms.[AQjmsXAConnectionFactory](oracle/jms/AQjmsXAConnectionFactory.md) (implements javax.jms.[XAConnectionFactory](javax/jms/XAConnectionFactory.md))
  - oracle.jms.[AQjmsConnectionMetaData](oracle/jms/AQjmsConnectionMetaData.md) (implements javax.jms.[ConnectionMetaData](javax/jms/ConnectionMetaData.md))
  - oracle.jms.[AQjmsDestination](oracle/jms/AQjmsDestination.md) (implements javax.jms.[Queue](javax/jms/Queue.md), java.io.Serializable, javax.jms.[TemporaryQueue](javax/jms/TemporaryQueue.md), javax.jms.[TemporaryTopic](javax/jms/TemporaryTopic.md), javax.jms.[Topic](javax/jms/Topic.md))
  - oracle.jms.[AQjmsDestinationFactory](oracle/jms/AQjmsDestinationFactory.md) (implements javax.naming.spi.ObjectFactory)
  - oracle.jms.[AQjmsFactory](oracle/jms/AQjmsFactory.md)
  - oracle.jms.[AQjmsMessage](oracle/jms/AQjmsMessage.md) (implements javax.jms.[Message](javax/jms/Message.md))
    - oracle.jms.[AQjmsAdtMessage](oracle/jms/AQjmsAdtMessage.md) (implements oracle.jms.[AdtMessage](oracle/jms/AdtMessage.md))
    - oracle.jms.[AQjmsBytesMessage](oracle/jms/AQjmsBytesMessage.md) (implements javax.jms.[BytesMessage](javax/jms/BytesMessage.md))
    - oracle.jms.[AQjmsMapMessage](oracle/jms/AQjmsMapMessage.md) (implements javax.jms.[MapMessage](javax/jms/MapMessage.md))
    - oracle.jms.[AQjmsObjectMessage](oracle/jms/AQjmsObjectMessage.md) (implements javax.jms.[ObjectMessage](javax/jms/ObjectMessage.md))
    - oracle.jms.[AQjmsStreamMessage](oracle/jms/AQjmsStreamMessage.md) (implements javax.jms.[StreamMessage](javax/jms/StreamMessage.md))
    - oracle.jms.[AQjmsTextMessage](oracle/jms/AQjmsTextMessage.md) (implements javax.jms.[TextMessage](javax/jms/TextMessage.md))
  - oracle.jms.AQjmsObject
    - oracle.jms.[AQjmsConnection](oracle/jms/AQjmsConnection.md) (implements javax.jms.[QueueConnection](javax/jms/QueueConnection.md), javax.jms.[TopicConnection](javax/jms/TopicConnection.md))
      - oracle.jms.[AQjmsXAConnection](oracle/jms/AQjmsXAConnection.md) (implements javax.jms.[XAConnection](javax/jms/XAConnection.md), javax.jms.[XAQueueConnection](javax/jms/XAQueueConnection.md), javax.jms.[XATopicConnection](javax/jms/XATopicConnection.md))
    - oracle.jms.[AQjmsConsumer](oracle/jms/AQjmsConsumer.md) (implements oracle.jms.[AQjmsQueueReceiver](oracle/jms/AQjmsQueueReceiver.md), oracle.jms.[AQjmsTopicReceiver](oracle/jms/AQjmsTopicReceiver.md), oracle.jms.[AQjmsTopicSubscriber](oracle/jms/AQjmsTopicSubscriber.md))
    - oracle.jms.[AQjmsProducer](oracle/jms/AQjmsProducer.md) (implements javax.jms.[MessageProducer](javax/jms/MessageProducer.md))
    - oracle.jms.[AQjmsQueueBrowser](oracle/jms/AQjmsQueueBrowser.md) (implements java.util.Enumeration, javax.jms.[QueueBrowser](javax/jms/QueueBrowser.md))
    - oracle.jms.[AQjmsSession](oracle/jms/AQjmsSession.md) (implements javax.jms.[QueueSession](javax/jms/QueueSession.md), javax.jms.[TopicSession](javax/jms/TopicSession.md))
      - oracle.jms.[AQjmsXASession](oracle/jms/AQjmsXASession.md) (implements javax.jms.[XAQueueSession](javax/jms/XAQueueSession.md), javax.jms.[XASession](javax/jms/XASession.md), javax.jms.[XATopicSession](javax/jms/XATopicSession.md))
    - oracle.jms.[AQjmsTopicBrowser](oracle/jms/AQjmsTopicBrowser.md) (implements java.util.Enumeration, oracle.jms.[TopicBrowser](oracle/jms/TopicBrowser.md))
  - oracle.AQ.AQQueueProperty (implements java.io.Serializable)
    - oracle.jms.[AQjmsDestinationProperty](oracle/jms/AQjmsDestinationProperty.md)
  - javax.jms.[QueueRequestor](javax/jms/QueueRequestor.md)
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - javax.jms.[JMSException](javax/jms/JMSException.md)
        - oracle.jms.[AQjmsException](oracle/jms/AQjmsException.md)
        - oracle.jms.[AQjmsParseException](oracle/jms/AQjmsParseException.md)
        - javax.jms.[IllegalStateException](javax/jms/IllegalStateException.md)
        - javax.jms.[InvalidClientIDException](javax/jms/InvalidClientIDException.md)
        - javax.jms.[InvalidDestinationException](javax/jms/InvalidDestinationException.md)
        - javax.jms.[InvalidSelectorException](javax/jms/InvalidSelectorException.md)
        - javax.jms.[JMSSecurityException](javax/jms/JMSSecurityException.md)
        - javax.jms.[MessageEOFException](javax/jms/MessageEOFException.md)
        - javax.jms.[MessageFormatException](javax/jms/MessageFormatException.md)
        - javax.jms.[MessageNotReadableException](javax/jms/MessageNotReadableException.md)
        - javax.jms.[MessageNotWriteableException](javax/jms/MessageNotWriteableException.md)
        - javax.jms.[ResourceAllocationException](javax/jms/ResourceAllocationException.md)
        - javax.jms.[TransactionInProgressException](javax/jms/TransactionInProgressException.md)
        - javax.jms.[TransactionRolledBackException](javax/jms/TransactionRolledBackException.md)
  - javax.jms.[TopicRequestor](javax/jms/TopicRequestor.md)

## Interface Hierarchy

- javax.jms.[Connection](javax/jms/Connection.md)
  - javax.jms.[QueueConnection](javax/jms/QueueConnection.md)
    - javax.jms.[XAQueueConnection](javax/jms/XAQueueConnection.md) (also extends javax.jms.[QueueConnection](javax/jms/QueueConnection.md), javax.jms.[XAConnection](javax/jms/XAConnection.md))
  - javax.jms.[TopicConnection](javax/jms/TopicConnection.md)
    - javax.jms.[XATopicConnection](javax/jms/XATopicConnection.md) (also extends javax.jms.[TopicConnection](javax/jms/TopicConnection.md), javax.jms.[XAConnection](javax/jms/XAConnection.md))
  - javax.jms.[XAConnection](javax/jms/XAConnection.md)
    - javax.jms.[XAQueueConnection](javax/jms/XAQueueConnection.md) (also extends javax.jms.[QueueConnection](javax/jms/QueueConnection.md), javax.jms.[XAConnection](javax/jms/XAConnection.md))
    - javax.jms.[XATopicConnection](javax/jms/XATopicConnection.md) (also extends javax.jms.[TopicConnection](javax/jms/TopicConnection.md), javax.jms.[XAConnection](javax/jms/XAConnection.md))
  - javax.jms.[XAQueueConnection](javax/jms/XAQueueConnection.md) (also extends javax.jms.[QueueConnection](javax/jms/QueueConnection.md), javax.jms.[XAConnection](javax/jms/XAConnection.md))
  - javax.jms.[XATopicConnection](javax/jms/XATopicConnection.md) (also extends javax.jms.[TopicConnection](javax/jms/TopicConnection.md), javax.jms.[XAConnection](javax/jms/XAConnection.md))
- javax.jms.[ConnectionConsumer](javax/jms/ConnectionConsumer.md)
- javax.jms.[ConnectionFactory](javax/jms/ConnectionFactory.md)
  - javax.jms.[QueueConnectionFactory](javax/jms/QueueConnectionFactory.md)
    - javax.jms.[XAQueueConnectionFactory](javax/jms/XAQueueConnectionFactory.md) (also extends javax.jms.[QueueConnectionFactory](javax/jms/QueueConnectionFactory.md), javax.jms.[XAConnectionFactory](javax/jms/XAConnectionFactory.md))
  - javax.jms.[TopicConnectionFactory](javax/jms/TopicConnectionFactory.md)
    - javax.jms.[XATopicConnectionFactory](javax/jms/XATopicConnectionFactory.md) (also extends javax.jms.[TopicConnectionFactory](javax/jms/TopicConnectionFactory.md), javax.jms.[XAConnectionFactory](javax/jms/XAConnectionFactory.md))
  - javax.jms.[XAQueueConnectionFactory](javax/jms/XAQueueConnectionFactory.md) (also extends javax.jms.[QueueConnectionFactory](javax/jms/QueueConnectionFactory.md), javax.jms.[XAConnectionFactory](javax/jms/XAConnectionFactory.md))
  - javax.jms.[XATopicConnectionFactory](javax/jms/XATopicConnectionFactory.md) (also extends javax.jms.[TopicConnectionFactory](javax/jms/TopicConnectionFactory.md), javax.jms.[XAConnectionFactory](javax/jms/XAConnectionFactory.md))
- javax.jms.[ConnectionMetaData](javax/jms/ConnectionMetaData.md)
- javax.jms.[DeliveryMode](javax/jms/DeliveryMode.md)
- javax.jms.[Destination](javax/jms/Destination.md)
  - javax.jms.[Queue](javax/jms/Queue.md)
    - javax.jms.[TemporaryQueue](javax/jms/TemporaryQueue.md)
  - javax.jms.[TemporaryQueue](javax/jms/TemporaryQueue.md)
  - javax.jms.[TemporaryTopic](javax/jms/TemporaryTopic.md)
  - javax.jms.[Topic](javax/jms/Topic.md)
    - javax.jms.[TemporaryTopic](javax/jms/TemporaryTopic.md)
- javax.jms.[ExceptionListener](javax/jms/ExceptionListener.md)
- javax.jms.[Message](javax/jms/Message.md)
  - oracle.jms.[AdtMessage](oracle/jms/AdtMessage.md)
  - javax.jms.[BytesMessage](javax/jms/BytesMessage.md)
  - javax.jms.[MapMessage](javax/jms/MapMessage.md)
  - javax.jms.[ObjectMessage](javax/jms/ObjectMessage.md)
  - javax.jms.[StreamMessage](javax/jms/StreamMessage.md)
  - javax.jms.[TextMessage](javax/jms/TextMessage.md)
- javax.jms.[MessageConsumer](javax/jms/MessageConsumer.md)
  - oracle.jms.[AQjmsQueueReceiver](oracle/jms/AQjmsQueueReceiver.md)
  - oracle.jms.[AQjmsTopicReceiver](oracle/jms/AQjmsTopicReceiver.md)
  - oracle.jms.[AQjmsTopicSubscriber](oracle/jms/AQjmsTopicSubscriber.md)
  - javax.jms.[QueueReceiver](javax/jms/QueueReceiver.md)
    - oracle.jms.[AQjmsQueueReceiver](oracle/jms/AQjmsQueueReceiver.md)
  - oracle.jms.[TopicReceiver](oracle/jms/TopicReceiver.md)
    - oracle.jms.[AQjmsTopicReceiver](oracle/jms/AQjmsTopicReceiver.md)
  - javax.jms.[TopicSubscriber](javax/jms/TopicSubscriber.md)
    - oracle.jms.[AQjmsTopicSubscriber](oracle/jms/AQjmsTopicSubscriber.md)
- javax.jms.[MessageListener](javax/jms/MessageListener.md)
- javax.jms.[MessageProducer](javax/jms/MessageProducer.md)
  - oracle.jms.[AQjmsQueueSender](oracle/jms/AQjmsQueueSender.md)
  - oracle.jms.[AQjmsTopicPublisher](oracle/jms/AQjmsTopicPublisher.md)
  - javax.jms.[QueueSender](javax/jms/QueueSender.md)
    - oracle.jms.[AQjmsQueueSender](oracle/jms/AQjmsQueueSender.md)
  - javax.jms.[TopicPublisher](javax/jms/TopicPublisher.md)
    - oracle.jms.[AQjmsTopicPublisher](oracle/jms/AQjmsTopicPublisher.md)
- javax.jms.[QueueBrowser](javax/jms/QueueBrowser.md)
- java.lang.Runnable
  - javax.jms.[Session](javax/jms/Session.md)
    - javax.jms.[QueueSession](javax/jms/QueueSession.md)
    - javax.jms.[TopicSession](javax/jms/TopicSession.md)
    - javax.jms.[XAQueueSession](javax/jms/XAQueueSession.md)
    - javax.jms.[XASession](javax/jms/XASession.md)
      - javax.jms.[XAQueueSession](javax/jms/XAQueueSession.md)
      - javax.jms.[XATopicSession](javax/jms/XATopicSession.md)
    - javax.jms.[XATopicSession](javax/jms/XATopicSession.md)
- javax.jms.[ServerSession](javax/jms/ServerSession.md)
- javax.jms.[ServerSessionPool](javax/jms/ServerSessionPool.md)
- oracle.jms.[TopicBrowser](oracle/jms/TopicBrowser.md)
- javax.jms.[XAConnectionFactory](javax/jms/XAConnectionFactory.md)
  - javax.jms.[XAQueueConnectionFactory](javax/jms/XAQueueConnectionFactory.md) (also extends javax.jms.[QueueConnectionFactory](javax/jms/QueueConnectionFactory.md), javax.jms.[XAConnectionFactory](javax/jms/XAConnectionFactory.md))
  - javax.jms.[XATopicConnectionFactory](javax/jms/XATopicConnectionFactory.md) (also extends javax.jms.[TopicConnectionFactory](javax/jms/TopicConnectionFactory.md), javax.jms.[XAConnectionFactory](javax/jms/XAConnectionFactory.md))

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Tree
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
