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

- **[Prev Class](XSQLConnectionManagerFactory.md)**
- **[Next Class](XSQLDiagnostic.md)**

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

## **Class XSQLDatasourceConnectionManager**

- **java.lang.Object**

- - **oracle.xml.xsql.XSQLDatasourceConnectionManager**

<!-- -->

- **All Implemented Interfaces:**
  **[XSQLConnectionManager](XSQLConnectionManager.md), [XSQLConnectionManagerFactory](XSQLConnectionManagerFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XSQLDatasourceConnectionManager
      extends java.lang.Object
      implements XSQLConnectionManager, XSQLConnectionManagerFactory

  **Generic implementation of XSQLConnectionManager that uses JNDI to lookup a JDBC datasource from the container in which the XSQL servlet is running.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description            |
    |----------------------------------------|
    | `XSQLDatasourceConnectionManager``()`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                       |
    |-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XSQLConnectionManager`](XSQLConnectionManager.md) | `create``()`<br>Needed to implement XSQLConnectionManagerFactory interface                                                                                                   |
    | [`XSQLConnection`](XSQLConnection.md)               | `getConnection``(java.lang.String connName, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`<br>Needed to implement XSQLConnectionManager interface                           |
    | `void`                                              | `releaseConnection``(`[`XSQLConnection`](XSQLConnection.md)` theConn, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`<br>Needed to implement XSQLConnectionManager interface |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSQLDatasourceConnectionManager

          public XSQLDatasourceConnectionManager()

  <!-- -->

  - ### Method Detail

    - #### getConnection

          public XSQLConnection getConnection(java.lang.String connName,
                                              XSQLPageRequest env)
                                       throws java.sql.SQLException

      Needed to implement XSQLConnectionManager interface
      Specified by:
      [`getConnection`](XSQLConnectionManager.md) in interface [`XSQLConnectionManager`](XSQLConnectionManager.md)

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### releaseConnection

          public void releaseConnection(XSQLConnection theConn,
                                        XSQLPageRequest env)

      Needed to implement XSQLConnectionManager interface
      Specified by:
      [`releaseConnection`](XSQLConnectionManager.md) in interface [`XSQLConnectionManager`](XSQLConnectionManager.md)

    <!-- -->

    - #### create

          public XSQLConnectionManager create()

      Needed to implement XSQLConnectionManagerFactory interface
      Specified by:
      [`create`](XSQLConnectionManagerFactory.md) in interface [`XSQLConnectionManagerFactory`](XSQLConnectionManagerFactory.md)

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

- **[Prev Class](XSQLConnectionManagerFactory.md)**
- **[Next Class](XSQLDiagnostic.md)**

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
