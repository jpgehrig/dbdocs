Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AQMessage.md)
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

## Uses of Interface oracle.jdbc.aq.AQMessage

- **Packages that use [AQMessage](../AQMessage.md)**

  | Package        | Description                                                                                                                                               |
  |----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc    | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                                                         |
  | oracle.jdbc.aq | This package is an Oracle JDBC extension that provides interfaces to access the Advanced Queuing feature of Oracle for enterprise messaging applications. |

- - ### Uses of [AQMessage](../AQMessage.md) in [oracle.jdbc](../../package-summary.md)

    **Methods in [oracle.jdbc](../../package-summary.md) that return [AQMessage](../AQMessage.md)**

    | Modifier and Type              | Method and Description                                                                                                                                                                                                                                                                                                                                                                                 |
    |--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`AQMessage`](../AQMessage.md) | OracleConnection.[`dequeue`](../../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, byte[] tdo)`<br>Dequeues an AQ message from the queue specified by its name.                                                                                                 |
    | [`AQMessage`](../AQMessage.md) | OracleConnectionWrapper.[`dequeue`](../../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, byte[] tdo)`                                                                                                                                                   |
    | [`AQMessage`](../AQMessage.md) | OracleConnectionWrapper.[`dequeue`](../../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, byte[] tdo)`                                                                                                                                                   |
    | [`AQMessage`](../AQMessage.md) | OracleConnection.[`dequeue`](../../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, byte[] tdo)`<br>Dequeues an AQ message from the queue specified by its name.                                                                                                 |
    | [`AQMessage`](../AQMessage.md) | OracleConnection.[`dequeue`](../../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, byte[] tdo, int version)`<br>Dequeues an AQ message from the queue specified by its name.                                                                                    |
    | [`AQMessage`](../AQMessage.md) | OracleConnectionWrapper.[`dequeue`](../../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, byte[] tdo, int version)`                                                                                                                                      |
    | [`AQMessage`](../AQMessage.md) | OracleConnectionWrapper.[`dequeue`](../../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, byte[] tdo, int version)`                                                                                                                                      |
    | [`AQMessage`](../AQMessage.md) | OracleConnection.[`dequeue`](../../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, byte[] tdo, int version)`<br>Dequeues an AQ message from the queue specified by its name.                                                                                    |
    | [`AQMessage`](../AQMessage.md) | OracleConnection.[`dequeue`](../../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`<br>Dequeues an AQ message from the queue specified by its name. |
    | [`AQMessage`](../AQMessage.md) | OracleConnectionWrapper.[`dequeue`](../../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`                                                   |
    | [`AQMessage`](../AQMessage.md) | OracleConnectionWrapper.[`dequeue`](../../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`                                                   |
    | [`AQMessage`](../AQMessage.md) | OracleConnection.[`dequeue`](../../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](../AQDequeueOptions.md)` opt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`<br>Dequeues an AQ message from the queue specified by its name. |

    **Methods in [oracle.jdbc](../../package-summary.md) with parameters of type [AQMessage](../AQMessage.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                                 |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OracleConnection.[`enqueue`](../../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQEnqueueOptions`](../AQEnqueueOptions.md)` opt, `[`AQMessage`](../AQMessage.md)` mesg)`<br>Enqueues the given AQ message to the queue specified by its name. |
    | `void`            | OracleConnectionWrapper.[`enqueue`](../../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQEnqueueOptions`](../AQEnqueueOptions.md)` opt, `[`AQMessage`](../AQMessage.md)` mesg)`                                                        |
    | `void`            | OracleConnectionWrapper.[`enqueue`](../../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQEnqueueOptions`](../AQEnqueueOptions.md)` opt, `[`AQMessage`](../AQMessage.md)` mesg)`                                                        |
    | `void`            | OracleConnection.[`enqueue`](../../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQEnqueueOptions`](../AQEnqueueOptions.md)` opt, `[`AQMessage`](../AQMessage.md)` mesg)`<br>Enqueues the given AQ message to the queue specified by its name. |

  - ### Uses of [AQMessage](../AQMessage.md) in [oracle.jdbc.aq](../package-summary.md)

    **Methods in [oracle.jdbc.aq](../package-summary.md) that return [AQMessage](../AQMessage.md)**

    | Modifier and Type                       | Method and Description                                                                                                                                                |
    |-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`AQMessage`](../AQMessage.md) | AQFactory.[`createAQMessage`](../AQFactory.md)`(`[`AQMessageProperties`](../AQMessageProperties.md)` prop)`<br>Constructs a new AQMessage with given mess properties. |
    | `static `[`AQMessage`](../AQMessage.md) | AQFactory.[`createAQMessage`](../AQFactory.md)`(`[`AQMessageProperties`](../AQMessageProperties.md)` prop)`<br>Constructs a new AQMessage with given mess properties. |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AQMessage.md)
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
