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

- **[Prev Class](OracleXMLSQLException.md)**
- **Next Class**

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

**oracle.xml.sql**

## **Class OracleXMLSQLNoRowsException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **java.lang.RuntimeException**

      - - **[oracle.xml.sql.OracleXMLSQLException](OracleXMLSQLException.md)**

        - - **oracle.xml.sql.OracleXMLSQLNoRowsException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class OracleXMLSQLNoRowsException
      extends OracleXMLSQLException

  **The `OracleXMLSQLNoRowsException` class represents the runtime exception thrown when no rows are returned by a query when using the XSU.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------|
    | `OracleXMLSQLNoRowsException``()`<br>Constructor for the Oracle XMLSQLNoRowsException object                          |
    | `OracleXMLSQLNoRowsException``(java.lang.String errorTag)`<br>Constructor for the Oracle XMLSQLNoRowsException object |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class oracle.xml.sql.[OracleXMLSQLException](OracleXMLSQLException.md)**

      **[`getErrorCode`](OracleXMLSQLException.md)`, `[`getParentException`](OracleXMLSQLException.md)`, `[`getXMLErrorString`](OracleXMLSQLException.md)`, `[`getXMLSQLErrorString`](OracleXMLSQLException.md)`, `[`setErrorTag`](OracleXMLSQLException.md)**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Throwable**

      **`addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`**

<!-- -->

-
  -

    ### **Constructor Detail**

    - #### **OracleXMLSQLNoRowsException**

          public OracleXMLSQLNoRowsException()

      **Constructor for the Oracle XMLSQLNoRowsException object**

    - #### **OracleXMLSQLNoRowsException**

          public OracleXMLSQLNoRowsException(java.lang.String errorTag)

      **Constructor for the Oracle XMLSQLNoRowsException object**
      **Parameters:**
      **`errorTag` - The name of the error tag**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](OracleXMLSQLException.md)**
- **Next Class**

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
