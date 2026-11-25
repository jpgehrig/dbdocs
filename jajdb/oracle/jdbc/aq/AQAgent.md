Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQAgent.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](AQDequeueOptions.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.jdbc.aq

## Interface AQAgent

-

  ------------------------------------------------------------------------



      public interface AQAgent

  An Agent represents and identifies a user of the queue, either producer or consumer of the message, either an end-user or an application. An Agent is identified by a name, an address and a protocol. The name can be either assigned by the application, or be the application itself. The address is determined in terms of the communication protocol. If the protocol is 0 (default), the address is of the form\[schema.\]queuename\[@dblink\], a database link.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                   |
    |-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getAddress``()`                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getName``()`                                                                                                                                                            |
    | `int`                                                                                           | `getProtocol``()`                                                                                                                                                        |
    | `void`                                                                                          | `setAddress``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` address)`<br>Protocol-specific address of the recipient. |
    | `void`                                                                                          | `setName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`                                                      |
    | `void`                                                                                          | `setProtocol``(int protocol)`<br>Protocol to interpret the address and propagate the message.                                                                            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toString``()`                                                                                                                                                           |

<!-- -->

- - ### Method Detail

    - #### setAddress

          void setAddress(String address)
                   throws SQLException

      Protocol-specific address of the recipient. If the protocol is 0 (default), the address is of the form \[schema.\]queue\[@dblink\].
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getAddress

          String getAddress()

    <!-- -->

    - #### setName

          void setName(String name)
                throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getName

          String getName()

    <!-- -->

    - #### setProtocol

          void setProtocol(int protocol)
                    throws SQLException

      Protocol to interpret the address and propagate the message. The default (and currently the only supported) value is 0. The only valid value is zero, which is also the default.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getProtocol

          int getProtocol()

    <!-- -->

    - #### toString

          String toString()

      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQAgent.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](AQDequeueOptions.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2008, 2022, Oracle and/or its affiliates.
