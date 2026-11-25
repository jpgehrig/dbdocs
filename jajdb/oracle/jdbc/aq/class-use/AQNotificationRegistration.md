Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AQNotificationRegistration.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

## Uses of Interface oracle.jdbc.aq.AQNotificationRegistration

- **Packages that use [AQNotificationRegistration](../AQNotificationRegistration.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |

- - ### Uses of [AQNotificationRegistration](../AQNotificationRegistration.md) in [oracle.jdbc](../../package-summary.md)

    **Methods in [oracle.jdbc](../../package-summary.md) that return [AQNotificationRegistration](../AQNotificationRegistration.md)**

    | Modifier and Type                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    |----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`AQNotificationRegistration`](../AQNotificationRegistration.md)`[]` | OracleConnection.[`registerAQNotification`](../../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] name, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)`[] options, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` globaloptions)`<br>Registers your interest into being notified when a message is enqueued in a particular queue (or array of queues). |
    | [`AQNotificationRegistration`](../AQNotificationRegistration.md)`[]` | OracleConnectionWrapper.[`registerAQNotification`](../../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] name, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)`[] options, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` globaloptions)`                                                                                                         |
    | [`AQNotificationRegistration`](../AQNotificationRegistration.md)`[]` | OracleConnectionWrapper.[`registerAQNotification`](../../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] name, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)`[] options, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` globaloptions)`                                                                                                         |
    | [`AQNotificationRegistration`](../AQNotificationRegistration.md)`[]` | OracleConnection.[`registerAQNotification`](../../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] name, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)`[] options, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` globaloptions)`<br>Registers your interest into being notified when a message is enqueued in a particular queue (or array of queues). |

    **Methods in [oracle.jdbc](../../package-summary.md) with parameters of type [AQNotificationRegistration](../AQNotificationRegistration.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                          |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OracleConnection.[`unregisterAQNotification`](../../OracleConnection.md)`(`[`AQNotificationRegistration`](../AQNotificationRegistration.md)` registration)`<br>Deletes a given AQ registration. |
    | `void`            | OracleConnectionWrapper.[`unregisterAQNotification`](../../OracleConnectionWrapper.md)`(`[`AQNotificationRegistration`](../AQNotificationRegistration.md)` registration)`                       |
    | `void`            | OracleConnectionWrapper.[`unregisterAQNotification`](../../OracleConnectionWrapper.md)`(`[`AQNotificationRegistration`](../AQNotificationRegistration.md)` registration)`                       |
    | `void`            | OracleConnection.[`unregisterAQNotification`](../../OracleConnection.md)`(`[`AQNotificationRegistration`](../AQNotificationRegistration.md)` registration)`<br>Deletes a given AQ registration. |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AQNotificationRegistration.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
