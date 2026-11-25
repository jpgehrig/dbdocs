Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../package-summary.md)
- [Next Package](../babelfish/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.jdbc.aq

This package is an Oracle JDBC extension that provides interfaces to access the Advanced Queuing feature of Oracle for enterprise messaging applications.

See: Description

- **Interface Summary**

  | Interface                                                   | Description                                                                                                                               |
  |-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
  | [AQAgent](AQAgent.md)                                       | An Agent represents and identifies a user of the queue, either producer or consumer of the message, either an end-user or an application. |
  | [AQMessage](AQMessage.md)                                   | A message is the unit that is enqueued or dequeued.                                                                                       |
  | [AQMessageProperties](AQMessageProperties.md)               | This interface contains the message properties such as Correlation, Sender, Delay and Expiration, Recipients, and Priority and Ordering.  |
  | [AQNotificationListener](AQNotificationListener.md)         | The listener interface for receiving AQ notification events.                                                                              |
  | [AQNotificationRegistration](AQNotificationRegistration.md) | This class represents your interest in being notified when a new message is enqueued in a particular queue.                               |

- **Class Summary**

  | Class                                         | Description                                                                                                                                                                     |
  |-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AQDequeueOptions](AQDequeueOptions.md)       | Specifies the options available for the dequeue operation.                                                                                                                      |
  | [AQEnqueueOptions](AQEnqueueOptions.md)       | Specifies the options available for the enqueue operation.                                                                                                                      |
  | [AQFactory](AQFactory.md)                     | Factory class for AQ.                                                                                                                                                           |
  | [AQNotificationEvent](AQNotificationEvent.md) | An AQNotificationEvent will be created whenever a new message is enqueued in a queue for which you have registered your interest (see OracleConnection.registerAQNotification). |

- **Enum Summary**

  | Enum                                                                                    | Description |
  |-----------------------------------------------------------------------------------------|-------------|
  | [AQDequeueOptions.DeliveryFilter](AQDequeueOptions.DeliveryFilter.md)                   |             |
  | [AQDequeueOptions.DequeueMode](AQDequeueOptions.DequeueMode.md)                         |             |
  | [AQDequeueOptions.NavigationOption](AQDequeueOptions.NavigationOption.md)               |             |
  | [AQDequeueOptions.VisibilityOption](AQDequeueOptions.VisibilityOption.md)               |             |
  | [AQEnqueueOptions.DeliveryMode](AQEnqueueOptions.DeliveryMode.md)                       |             |
  | [AQEnqueueOptions.SequenceDeviationOption](AQEnqueueOptions.SequenceDeviationOption.md) |             |
  | [AQEnqueueOptions.VisibilityOption](AQEnqueueOptions.VisibilityOption.md)               |             |
  | [AQMessageProperties.DeliveryMode](AQMessageProperties.DeliveryMode.md)                 |             |
  | [AQMessageProperties.MessageState](AQMessageProperties.MessageState.md)                 |             |
  | [AQNotificationEvent.AdditionalEventType](AQNotificationEvent.AdditionalEventType.md)   |             |
  | [AQNotificationEvent.EventType](AQNotificationEvent.EventType.md)                       |             |

## Package oracle.jdbc.aq Description

This package is an Oracle JDBC extension that provides interfaces to access the Advanced Queuing feature of Oracle for enterprise messaging applications. JDBC AQ supports only the operational interfaces and not the administrative interface, but administrative operations can be accessed through embedded PL/SQL calls.

Enqueuing refers to sending a message to a queue and dequeuing refers to receiving one. A client application can create a message, set the desired properties on it and enqueue it by storing the message in the queue, a table in the database. When dequeuing a message, an application can either dequeue it synchronously by calling the `dequeue` method on the connection, or asynchronously by waiting for a notification from the database (see the `registerAQNotification` method on the database).

Since:
9*i*

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../package-summary.md)
- [Next Package](../babelfish/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
