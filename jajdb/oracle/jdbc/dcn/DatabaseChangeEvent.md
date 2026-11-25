Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/DatabaseChangeEvent.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](DatabaseChangeEvent.AdditionalEventType.md)

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

oracle.jdbc.dcn

## Class DatabaseChangeEvent

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.util.EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

  - - oracle.jdbc.dcn.DatabaseChangeEvent

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public abstract class DatabaseChangeEvent
      extends EventObject

  Once you have registered your interest into certain objects in the database, you get notified when these objects change. An instance of DatabaseChangeEvent represents such a notification.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                    |
    |-------------------|------------------------------------------------------------------------------------------|
    | `static class `   | [`DatabaseChangeEvent.AdditionalEventType`](DatabaseChangeEvent.AdditionalEventType.md)  |
    | `static class `   | [`DatabaseChangeEvent.EventType`](DatabaseChangeEvent.EventType.md)                      |

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from class java.util.[EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

      [`source`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true#source)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description                                                                                                        |
    |-------------|------------------------------------------------------------------------------------------------------------------------------------|
    | `protected` | `DatabaseChangeEvent``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` source)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                          | Method and Description                                                                                                                                                                     |
    |------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`DatabaseChangeEvent.AdditionalEventType`](DatabaseChangeEvent.AdditionalEventType.md)         | `getAdditionalEventType``()`<br>Retrieve the additional event type.                                                                                                                        |
    | `abstract `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getConnectionInformation``()`<br>Retrieves a description of the TCP connection on which the notification was received.                                                                    |
    | `abstract `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getDatabaseName``()`<br>Retrieves the name of the database.                                                                                                                               |
    | `abstract `[`DatabaseChangeEvent.EventType`](DatabaseChangeEvent.EventType.md)                             | `getEventType``()`<br>Retrieve the event type.                                                                                                                                             |
    | `abstract `[`QueryChangeDescription`](QueryChangeDescription.md)`[]`                                       | `getQueryChangeDescription``()`<br>For query change (`EVENT_TYPE_QUERYCHANGE`) kind of events, this method returns the description of the changes for each query which result has changed. |
    | `abstract long`                                                                                            | `getRegId``()`<br>Retrieves the identification of the registration that generated this event on the server.                                                                                |
    | `abstract int`                                                                                             | `getRegistrationId``()`<br>Deprecated. <br>Use getRegId instead.                                                                                                                           |
    | `abstract `[`TableChangeDescription`](TableChangeDescription.md)`[]`                                       | `getTableChangeDescription``()`<br>For object change (`EVENT_TYPE_OBJCHANGE`) kind of events, this method returns the description of the changes for each table that was changed.          |
    | `abstract byte[]`                                                                                          | `getTransactionId``()`<br>Returns the id of the transaction (xid) that when committed was responsible for generating this event.                                                           |
    | `abstract `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getTransactionId``(boolean isLittleEndian)`<br>Returns the id of the transaction (xid) that when committed was responsible for generating this event.                                     |
    | `abstract `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toString``()`                                                                                                                                                                             |

    - ### Methods inherited from class java.util.[EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

      [`getSource`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true#getSource__)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### DatabaseChangeEvent

          protected DatabaseChangeEvent(Object source)

  <!-- -->

  - ### Method Detail

    - #### getEventType

          public abstract DatabaseChangeEvent.EventType getEventType()

      Retrieve the event type.

    <!-- -->

    - #### getAdditionalEventType

          public abstract DatabaseChangeEvent.AdditionalEventType getAdditionalEventType()

      Retrieve the additional event type.

    <!-- -->

    - #### getTableChangeDescription

          public abstract TableChangeDescription[] getTableChangeDescription()

      For object change (`EVENT_TYPE_OBJCHANGE`) kind of events, this method returns the description of the changes for each table that was changed.
      Returns `null` for other kinds of events.

    <!-- -->

    - #### getQueryChangeDescription

          public abstract QueryChangeDescription[] getQueryChangeDescription()

      For query change (`EVENT_TYPE_QUERYCHANGE`) kind of events, this method returns the description of the changes for each query which result has changed.
      Returns `null` for other kinds of events.

    <!-- -->

    - #### getConnectionInformation

          public abstract String getConnectionInformation()

      Retrieves a description of the TCP connection on which the notification was received.

    <!-- -->

    - #### getDatabaseName

          public abstract String getDatabaseName()

      Retrieves the name of the database.

    <!-- -->

    - #### getRegistrationId

          public abstract int getRegistrationId()

      Deprecated. Use getRegId instead.
      Retrieves the identification of the registration that generated this event on the server.

    <!-- -->

    - #### getRegId

          public abstract long getRegId()

      Retrieves the identification of the registration that generated this event on the server.

    <!-- -->

    - #### getTransactionId

          public abstract byte[] getTransactionId()

      Returns the id of the transaction (xid) that when committed was responsible for generating this event. This transaction id is in RAW format. It contains 8 bytes: the xid undo segment number (2 bytes), the xid slot number (2 bytes) and the xid sequence number (4 bytes). Each one of these numbers is in the server's machine endian-ness.
      For example: in a local transaction, you execute: `select dbms_transaction.local_transaction_id from dual` and you get back `17.9.2339`. You then commit this transaction which generates an event. Calling `getTransactionId()` on this event will return `0x11 0x00 0x09 0x00 0x23 0x09 0x00 0x00` if the server is running on a little endian platform and `0x00 0x11 0x00 0x09 0x00 0x00 0x09 0x23` if the server is big endian.
      See Also:
      `getTransactionId(boolean)`

    <!-- -->

    - #### getTransactionId

          public abstract String getTransactionId(boolean isLittleEndian)

      Returns the id of the transaction (xid) that when committed was responsible for generating this event. Assuming that you know the endian-ness of the server you can call this method to retrieve the xid in a `String` format. For example, this method returns `17.9.2339` which is the same value as what `select dbms_transaction.local_transaction_id from dual` would have returned from the transaction before it was committed.
      Parameters:
      `isLittleEndian` - the endian-ness of the server. `true` if the server is little endian and `false` otherwise.

      See Also:
      `getTransactionId`

    <!-- -->

    - #### toString

          public abstract String toString()

      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true#toString__) in class [`EventObject`](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/DatabaseChangeEvent.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](DatabaseChangeEvent.AdditionalEventType.md)

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
