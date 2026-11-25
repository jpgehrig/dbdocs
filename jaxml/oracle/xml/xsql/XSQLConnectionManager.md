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

- **[Prev Class](XSQLConnection.md)**
- **[Next Class](XSQLConnectionManagerFactory.md)**

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

## **Interface XSQLConnectionManager**

- **All Known Implementing Classes:**
  **[XSQLDatasourceConnectionManager](XSQLDatasourceConnectionManager.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XSQLConnectionManager

  **One of two interfaces that must be implemented to override the built-in connection manager implementation. The XSQL Page Processor asks the XSQLConnectionManagerFactory associated with each request to create() an instance of an XSQLConnectionManager to service the current request.**
  **In multithreaded environments, the implementation of XSQLConnectionManager must insure that an XSQLConnection instance returned by getConnection() is not used by another thread until it has been released by the XSQL Page Processor after the call to releaseConnection().**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                     | Method and Description                                                                                                 |
    |---------------------------------------|------------------------------------------------------------------------------------------------------------------------|
    | [`XSQLConnection`](XSQLConnection.md) | `getConnection``(java.lang.String connName, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`                            |
    | `void`                                | `releaseConnection``(`[`XSQLConnection`](XSQLConnection.md)` theConn, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`  |

<!-- -->

- - ### Method Detail

    - #### getConnection

          XSQLConnection getConnection(java.lang.String connName,
                                       XSQLPageRequest env)
                                throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### releaseConnection

          void releaseConnection(XSQLConnection theConn,
                                 XSQLPageRequest env)

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

- **[Prev Class](XSQLConnection.md)**
- **[Next Class](XSQLConnectionManagerFactory.md)**

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
