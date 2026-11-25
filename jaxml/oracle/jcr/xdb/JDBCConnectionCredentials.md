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

- **Prev Class**
- **[Next Class](XDBRepositoryConfiguration.md)**

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

**oracle.jcr.xdb**

## **Class JDBCConnectionCredentials**

- **java.lang.Object**

- - **oracle.jcr.xdb.JDBCConnectionCredentials**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, [Credentials](../../../javax/jcr/Credentials.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **JDBCConnectionCredentials allows creation of a JCR session based on the user identity of an existing JDBC connection.**
  **The JCR session created from the JDBC connection will use that JDBC connection to access the XML DB repository.**

  **
  **

      public class JDBCConnectionCredentials
      extends java.lang.Object
      implements Credentials

  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                              |
    |--------------------------------------------------------------------------------------------------------------------------|
    | `JDBCConnectionCredentials``(java.sql.Connection connection)`<br>Deprecated. <br>Constructs a JDBCConnectionCredentials. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type     | Method and Description                                              |
    |-----------------------|---------------------------------------------------------------------|
    | `java.sql.Connection` | `getConnection``()`<br>Deprecated. <br>Returns the JDBC connection. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JDBCConnectionCredentials

          public JDBCConnectionCredentials(java.sql.Connection connection)
                                    throws RepositoryException

      Deprecated. 
      Constructs a JDBCConnectionCredentials.
      Parameters:
      `connection` - the connection; required; must not have been closed; must not auto-commit

      Throws:
      [`RepositoryException`](../../../javax/jcr/RepositoryException.md) - if the operation fails

  <!-- -->

  - ### Method Detail

    - #### getConnection

          public java.sql.Connection getConnection()

      Deprecated. 
      Returns the JDBC connection.
      Returns:
      the connection

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

- **Prev Class**
- **[Next Class](XDBRepositoryConfiguration.md)**

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
