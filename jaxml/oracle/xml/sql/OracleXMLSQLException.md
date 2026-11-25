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
- **[Next Class](OracleXMLSQLNoRowsException.md)**

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

## **Class OracleXMLSQLException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **java.lang.RuntimeException**

      - - **oracle.xml.sql.OracleXMLSQLException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  <!-- -->

  **Direct Known Subclasses:**
  **[OracleXMLSQLNoRowsException](OracleXMLSQLNoRowsException.md)**

  ------------------------------------------------------------------------

  **
  **

      public class OracleXMLSQLException
      extends java.lang.RuntimeException

  **The `OracleXMLSQLException` class is the generic runtime exception thrown by the XSU.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleXMLSQLException``(java.lang.Exception parentE)`<br>Constructor for the `OracleXMLSQLException` object.                                                      |
    | `OracleXMLSQLException``(java.lang.Exception parentE, java.lang.String errorTag)`<br>Constructor for the `OracleXMLSQLException` object.                           |
    | `OracleXMLSQLException``(java.lang.String message)`<br>Constructor for the `OracleXMLSQLException` object.                                                         |
    | `OracleXMLSQLException``(java.lang.String message, java.lang.Exception parentE)`<br>Constructor for the `OracleXMLSQLException` object.                            |
    | `OracleXMLSQLException``(java.lang.String message, java.lang.Exception parentE, boolean combine)`<br>Constructor for the `OracleXMLSQLException` object.           |
    | `OracleXMLSQLException``(java.lang.String message, java.lang.Exception parentE, java.lang.String errorTag)`<br>Constructor for the `OracleXMLSQLException` object. |
    | `OracleXMLSQLException``(java.lang.String message, int sqlErrorCode)`<br>Constructor for the `OracleXMLSQLException` object.                                       |
    | `OracleXMLSQLException``(java.lang.String message, int sqlErrorCode, java.lang.String errorTag)`<br>Constructor for the `OracleXMLSQLException` object.            |
    | `OracleXMLSQLException``(java.lang.String message, java.lang.String errorTag)`<br>Constructor for the `OracleXMLSQLException` object.                              |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                   |
    |-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                 | `getErrorCode``()`<br>This function gets the SQL error code                                                                                                                              |
    | `java.lang.Exception` | `getParentException``()`<br>Returns the original exception it if exists; otherwise, returns `null`.                                                                                      |
    | `java.lang.String`    | `getXMLErrorString``()`<br>Prints the XML error message and error tag name as a `String`.                                                                                                |
    | `java.lang.String`    | `getXMLSQLErrorString``()`<br>Prints the SQL error message and error parameters as a `String`.                                                                                           |
    | `void`                | `setErrorTag``(java.lang.String errorTag)`<br>Sets the error tag name that is subsequently used by `getXMLErrorString` and `getXMLSQLErrorString` methods to generate XML error reports. |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### OracleXMLSQLException

          public OracleXMLSQLException(java.lang.Exception parentE)

      Constructor for the `OracleXMLSQLException` object.
      Parameters:
      `parentE` - Parent exception

    <!-- -->

    - #### OracleXMLSQLException

          public OracleXMLSQLException(java.lang.Exception parentE,
                                       java.lang.String errorTag)

      Constructor for the `OracleXMLSQLException` object.
      Parameters:
      `parentE` - Parent exception

      `errorTag` - Name of error Tag

    <!-- -->

    - #### OracleXMLSQLException

          public OracleXMLSQLException(java.lang.String message,
                                       java.lang.Exception parentE,
                                       boolean combine)

      Constructor for the `OracleXMLSQLException` object.
      Parameters:
      `message` - The error message string

      `parentE` - Parent exception

      `combine` - combine the given message with the exception msg?

    <!-- -->

    - #### OracleXMLSQLException

          public OracleXMLSQLException(java.lang.String message,
                                       java.lang.Exception parentE)

      Constructor for the `OracleXMLSQLException` object.
      Parameters:
      `message` - The error message string

      `parentE` - Parent exception

    <!-- -->

    - #### OracleXMLSQLException

          public OracleXMLSQLException(java.lang.String message,
                                       java.lang.Exception parentE,
                                       java.lang.String errorTag)

      Constructor for the `OracleXMLSQLException` object.
      Parameters:
      `message` - The error message string

      `parentE` - Parent exception

      `errorTag` - The name of the error tag

    <!-- -->

    - #### OracleXMLSQLException

          public OracleXMLSQLException(java.lang.String message)

      Constructor for the `OracleXMLSQLException` object.
      Parameters:
      `message` - The error message string

    <!-- -->

    - #### OracleXMLSQLException

          public OracleXMLSQLException(java.lang.String message,
                                       java.lang.String errorTag)

      Constructor for the `OracleXMLSQLException` object.
      Parameters:
      `message` - The error message string

      `errorTag` - The name of the error tag

    <!-- -->

    - #### OracleXMLSQLException

          public OracleXMLSQLException(java.lang.String message,
                                       int sqlErrorCode)

      Constructor for the `OracleXMLSQLException` object.
      Parameters:
      `message` - The error message string

      `sqlErrorCode` - The SQL error code

    <!-- -->

    - #### OracleXMLSQLException

          public OracleXMLSQLException(java.lang.String message,
                                       int sqlErrorCode,
                                       java.lang.String errorTag)

      Constructor for the `OracleXMLSQLException` object.
      Parameters:
      `message` - The error message string

      `sqlErrorCode` - The SQL error code

      `errorTag` - The name of the error tag

  <!-- -->

  - ### Method Detail

    - #### getXMLErrorString

          public java.lang.String getXMLErrorString()

      Prints the XML error message and error tag name as a `String`.
      Returns:
      The Error as a string

    <!-- -->

    - #### getXMLSQLErrorString

          public java.lang.String getXMLSQLErrorString()

      Prints the SQL error message and error parameters as a `String`.
      Returns:
      The error massage and error parameters as a string

    <!-- -->

    - #### getParentException

          public java.lang.Exception getParentException()

      Returns the original exception it if exists; otherwise, returns `null`.
      Returns:
      The original exception, or NULL of one doesn't exist

    <!-- -->

    - #### setErrorTag

          public void setErrorTag(java.lang.String errorTag)

      Sets the error tag name that is subsequently used by `getXMLErrorString` and `getXMLSQLErrorString` methods to generate XML error reports.
      Parameters:
      `errorTag` - The name of the error tag.

    <!-- -->

    - #### getErrorCode

          public int getErrorCode()

      This function gets the SQL error code
      Returns:
      The SQL error code

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
- **[Next Class](OracleXMLSQLNoRowsException.md)**

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
