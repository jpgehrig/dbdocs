Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Uses of Package oracle.jdbc.aq

- **Packages that use [oracle.jdbc.aq](package-summary.md)**

  | Package        | Description                                                                                                                                               |
  |----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc    | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                                                         |
  | oracle.jdbc.aq | This package is an Oracle JDBC extension that provides interfaces to access the Advanced Queuing feature of Oracle for enterprise messaging applications. |

- **Classes in [oracle.jdbc.aq](package-summary.md) used by [oracle.jdbc](../package-summary.md)**

  | Class and Description                                                                                                                                                                |
  |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AQDequeueOptions](class-use/AQDequeueOptions.md)<br>Specifies the options available for the dequeue operation.                                                                      |
  | [AQEnqueueOptions](class-use/AQEnqueueOptions.md)<br>Specifies the options available for the enqueue operation.                                                                      |
  | [AQMessage](class-use/AQMessage.md)<br>A message is the unit that is enqueued or dequeued.                                                                                           |
  | [AQNotificationRegistration](class-use/AQNotificationRegistration.md)<br>This class represents your interest in being notified when a new message is enqueued in a particular queue. |

- **Classes in [oracle.jdbc.aq](package-summary.md) used by [oracle.jdbc.aq](package-summary.md)**

  | Class and Description                                                                                                                                                                                                                      |
  |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AQAgent](class-use/AQAgent.md)<br>An Agent represents and identifies a user of the queue, either producer or consumer of the message, either an end-user or an application.                                                               |
  | [AQDequeueOptions.DeliveryFilter](class-use/AQDequeueOptions.DeliveryFilter.md)                                                                                                                                                            |
  | [AQDequeueOptions.DequeueMode](class-use/AQDequeueOptions.DequeueMode.md)                                                                                                                                                                  |
  | [AQDequeueOptions.NavigationOption](class-use/AQDequeueOptions.NavigationOption.md)                                                                                                                                                        |
  | [AQDequeueOptions.VisibilityOption](class-use/AQDequeueOptions.VisibilityOption.md)                                                                                                                                                        |
  | [AQEnqueueOptions.DeliveryMode](class-use/AQEnqueueOptions.DeliveryMode.md)                                                                                                                                                                |
  | [AQEnqueueOptions.SequenceDeviationOption](class-use/AQEnqueueOptions.SequenceDeviationOption.md)                                                                                                                                          |
  | [AQEnqueueOptions.VisibilityOption](class-use/AQEnqueueOptions.VisibilityOption.md)                                                                                                                                                        |
  | [AQMessage](class-use/AQMessage.md)<br>A message is the unit that is enqueued or dequeued.                                                                                                                                                 |
  | [AQMessageProperties](class-use/AQMessageProperties.md)<br>This interface contains the message properties such as Correlation, Sender, Delay and Expiration, Recipients, and Priority and Ordering.                                        |
  | [AQMessageProperties.DeliveryMode](class-use/AQMessageProperties.DeliveryMode.md)                                                                                                                                                          |
  | [AQMessageProperties.MessageState](class-use/AQMessageProperties.MessageState.md)                                                                                                                                                          |
  | [AQNotificationEvent](class-use/AQNotificationEvent.md)<br>An AQNotificationEvent will be created whenever a new message is enqueued in a queue for which you have registered your interest (see OracleConnection.registerAQNotification). |
  | [AQNotificationEvent.AdditionalEventType](class-use/AQNotificationEvent.AdditionalEventType.md)                                                                                                                                            |
  | [AQNotificationEvent.EventType](class-use/AQNotificationEvent.EventType.md)                                                                                                                                                                |
  | [AQNotificationListener](class-use/AQNotificationListener.md)<br>The listener interface for receiving AQ notification events.                                                                                                              |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
