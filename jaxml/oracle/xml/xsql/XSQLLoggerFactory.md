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

- **[Prev Class](XSQLLogger.md)**
- **[Next Class](XSQLNamedConnection.md)**

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

## **Interface XSQLLoggerFactory**

-

  ------------------------------------------------------------------------

  **
  **

      public interface XSQLLoggerFactory

  **One of two interfaces that must be implemented to provide a custom logging implementation. The XSQL Page Processor asks the XSQLLoggerFactory associated with each request to create() an instance of an XSQLLogger to service the current request. If the factory implementation returns the same XSQLLogger instance to multiple requests, it needs to worry about synchronizing access to the logger object as necessary. Each page request has a unique XSQLPageRequest instance.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                          |
    |-------------------------------|-----------------------------------------------------------------------------------------------------------------|
    | [`XSQLLogger`](XSQLLogger.md) | `create``(`[`XSQLPageRequest`](XSQLPageRequest.md)` req)`<br>Returns a new or existing instance of XSQL logger. |

<!-- -->

- - ### Method Detail

    - #### create

          XSQLLogger create(XSQLPageRequest req)

      Returns a new or existing instance of XSQL logger. The XSQL page processing engine will hold a reference to the XSQLLogger object returned by this method for the duration of a single page request.

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

- **[Prev Class](XSQLLogger.md)**
- **[Next Class](XSQLNamedConnection.md)**

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
