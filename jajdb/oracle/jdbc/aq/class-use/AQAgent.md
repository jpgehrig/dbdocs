Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AQAgent.md)
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

## Uses of Interface oracle.jdbc.aq.AQAgent

- **Packages that use [AQAgent](../AQAgent.md)**

  | Package        | Description                                                                                                                                               |
  |----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc.aq | This package is an Oracle JDBC extension that provides interfaces to access the Advanced Queuing feature of Oracle for enterprise messaging applications. |

- - ### Uses of [AQAgent](../AQAgent.md) in [oracle.jdbc.aq](../package-summary.md)

    **Methods in [oracle.jdbc.aq](../package-summary.md) that return [AQAgent](../AQAgent.md)**

    | Modifier and Type                   | Method and Description                                                         |
    |-------------------------------------|--------------------------------------------------------------------------------|
    | `static `[`AQAgent`](../AQAgent.md) | AQFactory.[`createAQAgent`](../AQFactory.md)`()`<br>Constructs a new AQ agent. |
    | `static `[`AQAgent`](../AQAgent.md) | AQFactory.[`createAQAgent`](../AQFactory.md)`()`<br>Constructs a new AQ agent. |
    | [`AQAgent`](../AQAgent.md)`[]`      | AQMessageProperties.[`getRecipientList`](../AQMessageProperties.md)`()`        |
    | [`AQAgent`](../AQAgent.md)`[]`      | AQMessageProperties.[`getRecipientList`](../AQMessageProperties.md)`()`        |
    | [`AQAgent`](../AQAgent.md)          | AQMessageProperties.[`getSender`](../AQMessageProperties.md)`()`               |
    | [`AQAgent`](../AQAgent.md)          | AQMessageProperties.[`getSender`](../AQMessageProperties.md)`()`               |

    **Methods in [oracle.jdbc.aq](../package-summary.md) with parameters of type [AQAgent](../AQAgent.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                  |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | AQMessageProperties.[`setRecipientList`](../AQMessageProperties.md)`(`[`AQAgent`](../AQAgent.md)`[] agents)`<br>This parameter is only valid for queues which allow multiple consumers. |
    | `void`            | AQMessageProperties.[`setRecipientList`](../AQMessageProperties.md)`(`[`AQAgent`](../AQAgent.md)`[] agents)`<br>This parameter is only valid for queues which allow multiple consumers. |
    | `void`            | AQMessageProperties.[`setSender`](../AQMessageProperties.md)`(`[`AQAgent`](../AQAgent.md)` sender)`<br>Identifies the original sender of a message.                                     |
    | `void`            | AQMessageProperties.[`setSender`](../AQMessageProperties.md)`(`[`AQAgent`](../AQAgent.md)` sender)`<br>Identifies the original sender of a message.                                     |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AQAgent.md)
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
