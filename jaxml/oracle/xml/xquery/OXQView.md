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

- **[Prev Class](OXQStaticContext.md)**
- **[Next Class](OXQView.OXQViewAccessor.md)**

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

**oracle.xml.xquery**

## **Class OXQView**

- **java.lang.Object**

- - **oracle.xml.xquery.OXQView**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class OXQView
      extends java.lang.Object

  **This class provides methods to access Oracle's XQJ extensions (OXQJ) and extensions to other classes returned by the XQJ implementation.**
  **OXQJ extension classes are named after their XQJ counterparts as follows:**

  |                                                                             |                                                     |                                               |                                                                 |
  |-----------------------------------------------------------------------------|-----------------------------------------------------|-----------------------------------------------|-----------------------------------------------------------------|
  | XQJ Interface                                                               | OXQJ Extension                                      | Accessor Method (XQ to OXQ)                   | Inverse Accessor Method (OXQ to XQ)                             |
  | [`XQConnection`](../../../javax/xml/xquery/XQConnection.md)                 | [`OXQConnection`](OXQConnection.md)                 | `getConnection(XQConnection)`                 | [`OXQConnection.getXQView()`](OXQConnection.md)                 |
  | [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md)               | [`OXQDataFactory`](OXQDataFactory.md)               | `getDataFactory(XQDataFactory)`               | [`OXQDataFactory.getXQView()`](OXQDataFactory.md)               |
  | [`XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md)         | [`OXQDynamicContext`](OXQDynamicContext.md)         | `getDynamicContext(XQDynamicContext)`         | [`OXQDynamicContext.getXQView()`](OXQDynamicContext.md)         |
  | [`XQExpression`](../../../javax/xml/xquery/XQExpression.md)                 | [`OXQExpression`](OXQExpression.md)                 | `getExpression(XQExpression)`                 | [`OXQExpression.getXQView()`](OXQExpression.md)                 |
  | [`XQItem`](../../../javax/xml/xquery/XQItem.md)                             | [`OXQItem`](OXQItem.md)                             | `getItem(XQItem)`                             | [`OXQItem.getXQView()`](OXQItem.md)                             |
  | [`XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md)             | [`OXQItemAccessor`](OXQItemAccessor.md)             | `getItemAccessor(XQItemAccessor)`             | [`OXQItemAccessor.getXQView()`](OXQItemAccessor.md)             |
  | [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) | [`OXQPreparedExpression`](OXQPreparedExpression.md) | `getPreparedExpression(XQPreparedExpression)` | [`OXQPreparedExpression.getXQView()`](OXQPreparedExpression.md) |
  | [`XQSequence`](../../../javax/xml/xquery/XQSequence.md)                     | [`OXQSequence`](OXQSequence.md)                     | `getSequence(XQSequence)`                     | [`OXQSequence.getXQView()`](OXQSequence.md)                     |
  | [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md)           | [`OXQStaticContext`](OXQStaticContext.md)           | `getStaticContext(XQStaticContext)`           | [`OXQStaticContext.getXQView()`](OXQStaticContext.md)           |
  | [`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md)   | [`OXQStackTraceElement`](OXQStackTraceElement.md)   | `getStackTraceElement(XQStackTraceElement)`   | [`OXQStackTraceElement.getXQView()`](OXQStackTraceElement.md)   |
  | [`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md) | [`OXQStackTraceVariable`](OXQStackTraceVariable.md) | `getStackTraceVariable(XQStackTraceVariable)` | [`OXQStackTraceVariable.getXQView()`](OXQStackTraceVariable.md) |

  **Accessor methods return an OXQJ view over an XQJ object. Reverse navigation (OXQJ-\>XQJ) is provided by the `getXQView()` method of each OXQJ interface.**
  **In addition to XQJ API extensions, this class also provides access to the [`OXQCloseable`](OXQCloseable.md) extension of an `InputStream` instance returned by [`OXQItemAccessor.getItemAsInputStream(Properties)`](OXQItemAccessor.md) and an `XMLStreamReader` instance returned by [`XQItemAccessor.getItemAsStream()`](../../../javax/xml/xquery/XQItemAccessor.md).**

  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Nested Class Summary**

    **Nested Classes**

    | Modifier and Type   | Class and Description                                                                                                                                    |
    |---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static interface ` | [`OXQView.OXQViewAccessor`](OXQView.OXQViewAccessor.md)<br>Generic interface implemented by all XQJ objects which are capable of providing an OXQJ view. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                            | Method and Description                                                                                                                                                                                                                           |
    |--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`OXQCloseable`](OXQCloseable.md)                   | `getCloseable``(java.io.InputStream inputStream)`<br>Provides the OXQJ view of the closeable object.                                                                                                                                             |
    | `static `[`OXQCloseable`](OXQCloseable.md)                   | `getCloseable``(javax.xml.stream.XMLStreamReader reader)`<br>Provides the OXQJ view of the closeable object.                                                                                                                                     |
    | `static `[`OXQCloseable`](OXQCloseable.md)                   | `getCloseable``(`[`XQSequence`](../../../javax/xml/xquery/XQSequence.md)` sequence)`<br>Provides the OXQJ view of the closeable object.                                                                                                          |
    | `static `[`OXQConnection`](OXQConnection.md)                 | `getConnection``(`[`XQConnection`](../../../javax/xml/xquery/XQConnection.md)` connection)`<br>Provides the OXQJ view of the [`XQConnection`](../../../javax/xml/xquery/XQConnection.md) object.                                                 |
    | `static `[`OXQDataFactory`](OXQDataFactory.md)               | `getDataFactory``(`[`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md)` dataFactory)`<br>Provides the OXQJ view of the [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md) object.                                           |
    | `static `[`OXQDynamicContext`](OXQDynamicContext.md)         | `getDynamicContext``(`[`XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md)` dynamicContext)`<br>Provides the OXQJ view of the [`XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md) object.                         |
    | `static `[`OXQExpression`](OXQExpression.md)                 | `getExpression``(`[`XQExpression`](../../../javax/xml/xquery/XQExpression.md)` expression)`<br>Provides the OXQJ view of the [`XQExpression`](../../../javax/xml/xquery/XQExpression.md) object.                                                 |
    | `static `[`OXQItem`](OXQItem.md)                             | `getItem``(`[`XQItem`](../../../javax/xml/xquery/XQItem.md)` item)`<br>Provides the OXQJ view of the [`XQItem`](../../../javax/xml/xquery/XQItem.md) object.                                                                                     |
    | `static `[`OXQItemAccessor`](OXQItemAccessor.md)             | `getItemAccessor``(`[`XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md)` itemAccessor)`<br>Provides the OXQJ view of the [`XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md) object.                                     |
    | `static `[`OXQPreparedExpression`](OXQPreparedExpression.md) | `getPreparedExpression``(`[`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md)` preparedExpression)`<br>Provides the OXQJ view of the [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) object. |
    | `static `[`OXQSequence`](OXQSequence.md)                     | `getSequence``(`[`XQSequence`](../../../javax/xml/xquery/XQSequence.md)` sequence)`<br>Provides the OXQJ view of the [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) object.                                                             |
    | `static `[`OXQStackTraceElement`](OXQStackTraceElement.md)   | `getStackTraceElement``(`[`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md)` element)`<br>Provides the OXQJ view of the [`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md) object.                 |
    | `static `[`OXQStackTraceVariable`](OXQStackTraceVariable.md) | `getStackTraceVariable``(`[`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md)` variable)`<br>Provides the OXQJ view of the [`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md) object.           |
    | `static `[`OXQStaticContext`](OXQStaticContext.md)           | `getStaticContext``(`[`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md)` staticContext)`<br>Provides the OXQJ view of the [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md) object.                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getConnection

          public static OXQConnection getConnection(XQConnection connection)

      Provides the OXQJ view of the [`XQConnection`](../../../javax/xml/xquery/XQConnection.md) object.
      Parameters:
      `connection` - [`XQConnection`](../../../javax/xml/xquery/XQConnection.md) instance constructed by [`OXQDataSource`](OXQDataSource.md)

      Returns:
      view object implementing [`OXQConnection`](OXQConnection.md) interface

    <!-- -->

    - #### getDataFactory

          public static OXQDataFactory getDataFactory(XQDataFactory dataFactory)

      Provides the OXQJ view of the [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md) object.
      Parameters:
      `dataFactory` - [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md) instance constructed by [`OXQDataSource`](OXQDataSource.md)

      Returns:
      view object implementing [`OXQDataFactory`](OXQDataFactory.md) interface

    <!-- -->

    - #### getDynamicContext

          public static OXQDynamicContext getDynamicContext(XQDynamicContext dynamicContext)

      Provides the OXQJ view of the [`XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md) object.
      Parameters:
      `dynamicContext` - [`XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md) instance originated from [`OXQDataSource`](OXQDataSource.md)

      Returns:
      view object implementing [`OXQDynamicContext`](OXQDynamicContext.md) interface

    <!-- -->

    - #### getExpression

          public static OXQExpression getExpression(XQExpression expression)

      Provides the OXQJ view of the [`XQExpression`](../../../javax/xml/xquery/XQExpression.md) object.
      Parameters:
      `expression` - [`XQExpression`](../../../javax/xml/xquery/XQExpression.md) instance originated from [`OXQDataSource`](OXQDataSource.md)

      Returns:
      view object implementing [`OXQExpression`](OXQExpression.md) interface

    <!-- -->

    - #### getItem

          public static OXQItem getItem(XQItem item)

      Provides the OXQJ view of the [`XQItem`](../../../javax/xml/xquery/XQItem.md) object.
      Parameters:
      `item` - [`XQItem`](../../../javax/xml/xquery/XQItem.md) instance originated from [`OXQDataSource`](OXQDataSource.md)

      Returns:
      view object implementing [`OXQItem`](OXQItem.md) interface

    <!-- -->

    - #### getItemAccessor

          public static OXQItemAccessor getItemAccessor(XQItemAccessor itemAccessor)

      Provides the OXQJ view of the [`XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md) object.
      Parameters:
      `itemAccessor` - [`XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md) instance originated from [`OXQDataSource`](OXQDataSource.md)

      Returns:
      view object implementing [`OXQItemAccessor`](OXQItemAccessor.md) interface

    <!-- -->

    - #### getPreparedExpression

          public static OXQPreparedExpression getPreparedExpression(XQPreparedExpression preparedExpression)

      Provides the OXQJ view of the [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) object.
      Parameters:
      `preparedExpression` - [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) instance originated from [`OXQDataSource`](OXQDataSource.md)

      Returns:
      view object implementing [`OXQPreparedExpression`](OXQPreparedExpression.md) interface

    <!-- -->

    - #### getSequence

          public static OXQSequence getSequence(XQSequence sequence)

      Provides the OXQJ view of the [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) object.
      Parameters:
      `sequence` - [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) instance originated from [`OXQDataSource`](OXQDataSource.md)

      Returns:
      view object implementing [`OXQSequence`](OXQSequence.md) interface

    <!-- -->

    - #### getStaticContext

          public static OXQStaticContext getStaticContext(XQStaticContext staticContext)

      Provides the OXQJ view of the [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md) object.
      Parameters:
      `staticContext` - [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md) instance originated from [`OXQDataSource`](OXQDataSource.md)

      Returns:
      view object implementing [`OXQStaticContext`](OXQStaticContext.md) interface

    <!-- -->

    - #### getStackTraceElement

          public static OXQStackTraceElement getStackTraceElement(XQStackTraceElement element)

      Provides the OXQJ view of the [`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md) object. This method only applies to [`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md) instances exposed by [`OXQDebugListener`](OXQDebugListener.md).
      Parameters:
      `element` - [`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md) passed to one of the [`OXQDebugListener`](OXQDebugListener.md) methods

      Returns:
      view object implementing [`OXQStackTraceElement`](OXQStackTraceElement.md) interface

    <!-- -->

    - #### getStackTraceVariable

          public static OXQStackTraceVariable getStackTraceVariable(XQStackTraceVariable variable)

      Provides the OXQJ view of the [`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md) object. This method only applies to [`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md) instances from [`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md)s exposed by [`OXQDebugListener`](OXQDebugListener.md).
      Parameters:
      `variable` - [`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md) passed to one of the [`OXQDebugListener`](OXQDebugListener.md) methods

      Returns:
      view object implementing [`OXQStackTraceVariable`](OXQStackTraceVariable.md) interface

    <!-- -->

    - #### getCloseable

          public static OXQCloseable getCloseable(XQSequence sequence)

      Provides the OXQJ view of the closeable object.
      Parameters:
      `sequence` - [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) instance originated from [`OXQDataSource`](OXQDataSource.md)

      Returns:
      view object implementing [`OXQCloseable`](OXQCloseable.md) interface.

    <!-- -->

    - #### getCloseable

          public static OXQCloseable getCloseable(javax.xml.stream.XMLStreamReader reader)

      Provides the OXQJ view of the closeable object.
      Parameters:
      `reader` - `XMLStreamReader` constructed by [`XQItemAccessor.getItemAsStream()`](../../../javax/xml/xquery/XQItemAccessor.md)

      Returns:
      view object implementing [`OXQCloseable`](OXQCloseable.md) interface

    <!-- -->

    - #### getCloseable

          public static OXQCloseable getCloseable(java.io.InputStream inputStream)

      Provides the OXQJ view of the closeable object.
      Parameters:
      `inputStream` - `InputStream` constructed by [`OXQItemAccessor.getItemAsInputStream(Properties)`](OXQItemAccessor.md)

      Returns:
      view object implementing [`OXQCloseable`](OXQCloseable.md) interface

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

- **[Prev Class](OXQStaticContext.md)**
- **[Next Class](OXQView.OXQViewAccessor.md)**

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
