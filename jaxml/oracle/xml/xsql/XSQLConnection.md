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

- **[Prev Class](XSQLCommandLine.md)**
- **[Next Class](XSQLConnectionManager.md)**

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

## **Class XSQLConnection**

- **java.lang.Object**

- - **oracle.xml.xsql.XSQLConnection**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class XSQLConnection
      extends java.lang.Object

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                |
    |------------------------------------------------------------------------------------------------------------|
    | `XSQLConnection``(java.sql.Connection connection, java.lang.String connName)`                              |
    | `XSQLConnection``(java.sql.Connection connection, java.lang.String connName, boolean isOracleConnection)`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description   |
    |-----------------------|--------------------------|
    | `void`                | `close``()`              |
    | `java.lang.String`    | `getConnectionName``()`  |
    | `java.sql.Connection` | `getJDBCConnection``()`  |
    | `long`                | `getLastUsed``()`        |
    | `boolean`             | `isOracleDriver``()`     |
    | `void`                | `updateLastUsed``()`     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSQLConnection

          public XSQLConnection(java.sql.Connection connection,
                                java.lang.String connName)

    <!-- -->

    - #### XSQLConnection

          public XSQLConnection(java.sql.Connection connection,
                                java.lang.String connName,
                                boolean isOracleConnection)

  <!-- -->

  - ### Method Detail

    - #### isOracleDriver

          public boolean isOracleDriver()

    <!-- -->

    - #### getJDBCConnection

          public java.sql.Connection getJDBCConnection()

    <!-- -->

    - #### getConnectionName

          public java.lang.String getConnectionName()

    <!-- -->

    - #### getLastUsed

          public long getLastUsed()

    <!-- -->

    - #### updateLastUsed

          public void updateLastUsed()

    <!-- -->

    - #### close

          public void close()

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

- **[Prev Class](XSQLCommandLine.md)**
- **[Next Class](XSQLConnectionManager.md)**

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
