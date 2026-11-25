Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XQConnection.md)**
- **[Next Class](XQConnectionEventListener.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.xml.xquery**

## **Class XQConnectionEvent**

- **java.lang.Object**

- - **java.util.EventObject**

  - - **javax.xml.xquery.XQConnectionEvent**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class XQConnectionEvent
      extends java.util.EventObject

  **An event object that provides information about the source of a connection-related event. `XQConnectionEvent` objects are generated when an application closes a pooled connection and when an error occurs. The `XQConnectionEvent` object contains the folowing information:**
  - **The pooled connection closed by the application**
  - **In the case of an error, the `XQException` to be thrown to the application**

  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                   |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XQConnectionEvent``(`[`PooledXQConnection`](PooledXQConnection.md)` con)`<br>Constructs an `XQConnectionEvent` object initialized with the given `PooledXQConnection` object.                                                                |
    | `XQConnectionEvent``(`[`PooledXQConnection`](PooledXQConnection.md)` con, `[`XQException`](XQException.md)` ex)`<br>Constructs an `XQConnectionEvent` object initialized with the given `PooledXQConnection` object and `XQException` object. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                   |
    |---------------------------------|------------------------------------------------------------------------------------------|
    | [`XQException`](XQException.md) | `getXQException``()`<br>Retrieves the `XQException` for this `XQConnectionEvent` object. |

    - ### Methods inherited from class java.util.EventObject

      `getSource, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XQConnectionEvent

          public XQConnectionEvent(PooledXQConnection con)

      Constructs an `XQConnectionEvent` object initialized with the given `PooledXQConnection` object. `XQException` defaults to `null`.
      Parameters:
      `con` - the pooled connection that is the source of the event

    <!-- -->

    - #### XQConnectionEvent

          public XQConnectionEvent(PooledXQConnection con,
                                   XQException ex)

      Constructs an `XQConnectionEvent` object initialized with the given `PooledXQConnection` object and `XQException` object.
      Parameters:
      `con` - the pooled connection that is the source of the event

      `ex` - the XQException to be thrown to the application

  <!-- -->

  - ### Method Detail

    - #### getXQException

          public XQException getXQException()

      Retrieves the `XQException` for this `XQConnectionEvent` object.
      Returns:
      the `XQException` to be thrown or `null`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XQConnection.md)**
- **[Next Class](XQConnectionEventListener.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
