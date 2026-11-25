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

- Prev
-

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Hierarchy For Package javax.jms

Package Hierarchies:

- [All Packages](../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - javax.jms.[QueueRequestor](QueueRequestor.md)
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - javax.jms.[JMSException](JMSException.md)
        - javax.jms.[IllegalStateException](IllegalStateException.md)
        - javax.jms.[InvalidClientIDException](InvalidClientIDException.md)
        - javax.jms.[InvalidDestinationException](InvalidDestinationException.md)
        - javax.jms.[InvalidSelectorException](InvalidSelectorException.md)
        - javax.jms.[JMSSecurityException](JMSSecurityException.md)
        - javax.jms.[MessageEOFException](MessageEOFException.md)
        - javax.jms.[MessageFormatException](MessageFormatException.md)
        - javax.jms.[MessageNotReadableException](MessageNotReadableException.md)
        - javax.jms.[MessageNotWriteableException](MessageNotWriteableException.md)
        - javax.jms.[ResourceAllocationException](ResourceAllocationException.md)
        - javax.jms.[TransactionInProgressException](TransactionInProgressException.md)
        - javax.jms.[TransactionRolledBackException](TransactionRolledBackException.md)
  - javax.jms.[TopicRequestor](TopicRequestor.md)

## Interface Hierarchy

- javax.jms.[Connection](Connection.md)
  - javax.jms.[QueueConnection](QueueConnection.md)
    - javax.jms.[XAQueueConnection](XAQueueConnection.md) (also extends javax.jms.[QueueConnection](QueueConnection.md), javax.jms.[XAConnection](XAConnection.md))
  - javax.jms.[TopicConnection](TopicConnection.md)
    - javax.jms.[XATopicConnection](XATopicConnection.md) (also extends javax.jms.[TopicConnection](TopicConnection.md), javax.jms.[XAConnection](XAConnection.md))
  - javax.jms.[XAConnection](XAConnection.md)
    - javax.jms.[XAQueueConnection](XAQueueConnection.md) (also extends javax.jms.[QueueConnection](QueueConnection.md), javax.jms.[XAConnection](XAConnection.md))
    - javax.jms.[XATopicConnection](XATopicConnection.md) (also extends javax.jms.[TopicConnection](TopicConnection.md), javax.jms.[XAConnection](XAConnection.md))
- javax.jms.[ConnectionConsumer](ConnectionConsumer.md)
- javax.jms.[ConnectionFactory](ConnectionFactory.md)
  - javax.jms.[QueueConnectionFactory](QueueConnectionFactory.md)
    - javax.jms.[XAQueueConnectionFactory](XAQueueConnectionFactory.md) (also extends javax.jms.[QueueConnectionFactory](QueueConnectionFactory.md), javax.jms.[XAConnectionFactory](XAConnectionFactory.md))
  - javax.jms.[TopicConnectionFactory](TopicConnectionFactory.md)
    - javax.jms.[XATopicConnectionFactory](XATopicConnectionFactory.md) (also extends javax.jms.[TopicConnectionFactory](TopicConnectionFactory.md), javax.jms.[XAConnectionFactory](XAConnectionFactory.md))
- javax.jms.[ConnectionMetaData](ConnectionMetaData.md)
- javax.jms.[DeliveryMode](DeliveryMode.md)
- javax.jms.[Destination](Destination.md)
  - javax.jms.[Queue](Queue.md)
    - javax.jms.[TemporaryQueue](TemporaryQueue.md)
  - javax.jms.[Topic](Topic.md)
    - javax.jms.[TemporaryTopic](TemporaryTopic.md)
- javax.jms.[ExceptionListener](ExceptionListener.md)
- javax.jms.[Message](Message.md)
  - javax.jms.[BytesMessage](BytesMessage.md)
  - javax.jms.[MapMessage](MapMessage.md)
  - javax.jms.[ObjectMessage](ObjectMessage.md)
  - javax.jms.[StreamMessage](StreamMessage.md)
  - javax.jms.[TextMessage](TextMessage.md)
- javax.jms.[MessageConsumer](MessageConsumer.md)
  - javax.jms.[QueueReceiver](QueueReceiver.md)
  - javax.jms.[TopicSubscriber](TopicSubscriber.md)
- javax.jms.[MessageListener](MessageListener.md)
- javax.jms.[MessageProducer](MessageProducer.md)
  - javax.jms.[QueueSender](QueueSender.md)
  - javax.jms.[TopicPublisher](TopicPublisher.md)
- javax.jms.[QueueBrowser](QueueBrowser.md)
- java.lang.Runnable
  - javax.jms.[Session](Session.md)
    - javax.jms.[QueueSession](QueueSession.md)
    - javax.jms.[TopicSession](TopicSession.md)
    - javax.jms.[XASession](XASession.md)
      - javax.jms.[XAQueueSession](XAQueueSession.md)
      - javax.jms.[XATopicSession](XATopicSession.md)
- javax.jms.[ServerSession](ServerSession.md)
- javax.jms.[ServerSessionPool](ServerSessionPool.md)
- javax.jms.[XAConnectionFactory](XAConnectionFactory.md)
  - javax.jms.[XAQueueConnectionFactory](XAQueueConnectionFactory.md) (also extends javax.jms.[QueueConnectionFactory](QueueConnectionFactory.md), javax.jms.[XAConnectionFactory](XAConnectionFactory.md))
  - javax.jms.[XATopicConnectionFactory](XATopicConnectionFactory.md) (also extends javax.jms.[TopicConnectionFactory](TopicConnectionFactory.md), javax.jms.[XAConnectionFactory](XAConnectionFactory.md))

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

- Prev
-

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
