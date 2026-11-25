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

- **[Prev Class](XSQLHttpUtil.md)**
- **[Next Class](XSQLLoggerFactory.md)**

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

**oracle.xml.xsql**

## **Interface XSQLLogger**

-

  ------------------------------------------------------------------------

  **
  **

      public interface XSQLLogger

  **One of two interfaces that must be implemented to provide a custom logging implementation. The XSQL Page Processor asks the XSQLLoggerFactory associated with each request to create() an instance of an XSQLLogger to service the current request. If the factory implementation returns the same XSQLLogger instance to multiple requests, the logger implementation needs to be aware of this and synchronize access to any resources used for logging as necessary.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                             |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `logRequestEnd``(`[`XSQLPageRequest`](XSQLPageRequest.md)` env)`<br>Event handler method invoked by the XSQL page processing engine at the end of the page request processing.     |
    | `void`            | `logRequestStart``(`[`XSQLPageRequest`](XSQLPageRequest.md)` env)`<br>Event handler method invoked by the XSQL page processing engine at the start of the page request processing. |

<!-- -->

- - ### Method Detail

    - #### logRequestStart

          void logRequestStart(XSQLPageRequest env)

      Event handler method invoked by the XSQL page processing engine at the start of the page request processing. The event only fires for the top-level page request.

    <!-- -->

    - #### logRequestEnd

          void logRequestEnd(XSQLPageRequest env)

      Event handler method invoked by the XSQL page processing engine at the end of the page request processing.

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

- **[Prev Class](XSQLHttpUtil.md)**
- **[Next Class](XSQLLoggerFactory.md)**

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
