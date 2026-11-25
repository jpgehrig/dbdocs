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

- **[Prev Class](OXQDataSource.md)**
- **[Next Class](OXQDecimalFormat.md)**

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

## **Class OXQDebugListener**

- **java.lang.Object**

- - **oracle.xml.xquery.OXQDebugListener**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public abstract class OXQDebugListener
      extends java.lang.Object

  **An event listener for implementing an XQuery debugger client.**
  **Since:**
  **12.1**

  **See Also:**
  **[`OXQDynamicContext.setDebugListener(OXQDebugListener)`](OXQDynamicContext.md), [`OXQDataSource.DEBUG_MODE`](OXQDataSource.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                 |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract void`   | `enter``(`[`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md)` element)`<br>Invoked when the processor enters a function or the main query.      |
    | `abstract void`   | `exit``(`[`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md)` element)`<br>Invoked when the processor exits a function or the main query.        |
    | `abstract void`   | `step``(`[`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md)` element)`<br>Invoked before a line of XQuery source code is about to be processed. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### enter

          public abstract void enter(XQStackTraceElement element)
                              throws XQException

      Invoked when the processor enters a function or the main query.
      Parameters:
      `element` - Contains only information about the function declaration. [`XQStackTraceElement.getVariables()`](../../../javax/xml/xquery/XQStackTraceElement.md) and [`OXQStackTraceElement.getStaticContext()`](OXQStackTraceElement.md) return `null`.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md)

      See Also:
      [`OXQView.getStackTraceElement(javax.xml.xquery.XQStackTraceElement)`](OXQView.md)

    <!-- -->

    - #### exit

          public abstract void exit(XQStackTraceElement element)
                             throws XQException

      Invoked when the processor exits a function or the main query.
      Parameters:
      `element` - Contains only information about the function declaration. [`XQStackTraceElement.getVariables()`](../../../javax/xml/xquery/XQStackTraceElement.md) and [`OXQStackTraceElement.getStaticContext()`](OXQStackTraceElement.md) return `null`.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md)

      See Also:
      [`OXQView.getStackTraceElement(javax.xml.xquery.XQStackTraceElement)`](OXQView.md)

    <!-- -->

    - #### step

          public abstract void step(XQStackTraceElement element)
                             throws XQException

      Invoked before a line of XQuery source code is about to be processed.
      Parameters:
      `element` - Contains information about the line.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md)

      See Also:
      [`OXQView.getStackTraceElement(javax.xml.xquery.XQStackTraceElement)`](OXQView.md)

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

- **[Prev Class](OXQDataSource.md)**
- **[Next Class](OXQDecimalFormat.md)**

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
