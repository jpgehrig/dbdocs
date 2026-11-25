Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AQMessageProperties.md)
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

## Uses of Interface oracle.jdbc.aq.AQMessageProperties

- **Packages that use [AQMessageProperties](../AQMessageProperties.md)**

  | Package        | Description                                                                                                                                               |
  |----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc.aq | This package is an Oracle JDBC extension that provides interfaces to access the Advanced Queuing feature of Oracle for enterprise messaging applications. |

- - ### Uses of [AQMessageProperties](../AQMessageProperties.md) in [oracle.jdbc.aq](../package-summary.md)

    **Methods in [oracle.jdbc.aq](../package-summary.md) that return [AQMessageProperties](../AQMessageProperties.md)**

    | Modifier and Type                                             | Method and Description                                                                                                      |
    |---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
    | `static `[`AQMessageProperties`](../AQMessageProperties.md)   | AQFactory.[`createAQMessageProperties`](../AQFactory.md)`()`<br>Constructs a new instance of AQMessageProperties.           |
    | `static `[`AQMessageProperties`](../AQMessageProperties.md)   | AQFactory.[`createAQMessageProperties`](../AQFactory.md)`()`<br>Constructs a new instance of AQMessageProperties.           |
    | [`AQMessageProperties`](../AQMessageProperties.md)            | AQMessage.[`getMessageProperties`](../AQMessage.md)`()`<br>Gets the AQMessageProperties that goes with this AQMessage.      |
    | `abstract `[`AQMessageProperties`](../AQMessageProperties.md) | AQNotificationEvent.[`getMessageProperties`](../AQNotificationEvent.md)`()`<br>Retrieves the properties of the new message. |
    | `abstract `[`AQMessageProperties`](../AQMessageProperties.md) | AQNotificationEvent.[`getMessageProperties`](../AQNotificationEvent.md)`()`<br>Retrieves the properties of the new message. |
    | [`AQMessageProperties`](../AQMessageProperties.md)            | AQMessage.[`getMessageProperties`](../AQMessage.md)`()`<br>Gets the AQMessageProperties that goes with this AQMessage.      |

    **Methods in [oracle.jdbc.aq](../package-summary.md) with parameters of type [AQMessageProperties](../AQMessageProperties.md)**

    | Modifier and Type                       | Method and Description                                                                                                                                                |
    |-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`AQMessage`](../AQMessage.md) | AQFactory.[`createAQMessage`](../AQFactory.md)`(`[`AQMessageProperties`](../AQMessageProperties.md)` prop)`<br>Constructs a new AQMessage with given mess properties. |
    | `static `[`AQMessage`](../AQMessage.md) | AQFactory.[`createAQMessage`](../AQFactory.md)`(`[`AQMessageProperties`](../AQMessageProperties.md)` prop)`<br>Constructs a new AQMessage with given mess properties. |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../AQMessageProperties.md)
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
