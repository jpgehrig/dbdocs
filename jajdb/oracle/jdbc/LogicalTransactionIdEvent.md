Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/LogicalTransactionIdEvent.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](LogicalTransactionId.md)
- [Next Class](LogicalTransactionIdEventListener.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.jdbc

## Class LogicalTransactionIdEvent

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.util.EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

  - - oracle.jdbc.LogicalTransactionIdEvent

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public abstract class LogicalTransactionIdEvent
      extends EventObject

  The event that corresponds to a new Logical Transaction Id. These events are sent by the database server and processed by the driver which notifies the registered listeners. See `LogicalTransactionIdEventListener`.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class java.util.[EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

      [`source`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true#source)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description                                                                                                              |
    |-------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected` | `LogicalTransactionIdEvent``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` source)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                            | Method and Description         |
    |--------------------------------------------------------------|--------------------------------|
    | `abstract `[`LogicalTransactionId`](LogicalTransactionId.md) | `getLogicalTransactionId``()`  |

    - ### Methods inherited from class java.util.[EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

      [`getSource`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true#getSource__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true#toString__)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### LogicalTransactionIdEvent

          protected LogicalTransactionIdEvent(Object source)

  <!-- -->

  - ### Method Detail

    - #### getLogicalTransactionId

          public abstract LogicalTransactionId getLogicalTransactionId()

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/LogicalTransactionIdEvent.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](LogicalTransactionId.md)
- [Next Class](LogicalTransactionIdEventListener.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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
