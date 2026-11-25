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

- **[Prev Class](DocumentBuilderFactory.md)**
- **[Next Class](ParserConfigurationException.md)**

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

**javax.xml.parsers**

## **Class FactoryConfigurationError**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Error**

    - - **javax.xml.parsers.FactoryConfigurationError**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class FactoryConfigurationError
      extends java.lang.Error

  **Thrown when a problem with configuration with the Parser Factories exists. This error will typically be thrown when the class of a parser factory specified in the system properties cannot be found or instantiated.**
  **Since:**
  **JAXP 1.0**

  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FactoryConfigurationError``()`<br>Create a new `FactoryConfigurationError` with no detail mesage.                                                                               |
    | `FactoryConfigurationError``(java.lang.Exception e)`<br>Create a new `FactoryConfigurationError` with a given `Exception` base cause of the error.                               |
    | `FactoryConfigurationError``(java.lang.Exception e, java.lang.String msg)`<br>Create a new `FactoryConfigurationError` with the given `Exception` base cause and detail message. |
    | `FactoryConfigurationError``(java.lang.String msg)`<br>Create a new `FactoryConfigurationError` with the `String` specified as an error message.                                 |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                              |
    |-----------------------|-----------------------------------------------------------------------------------------------------|
    | `java.lang.Exception` | `getException``()`<br>Return the actual exception (if any) that caused this exception to be raised. |
    | `java.lang.String`    | `getMessage``()`<br>Return the message (if any) for this error .                                    |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FactoryConfigurationError

          public FactoryConfigurationError()

      Create a new `FactoryConfigurationError` with no detail mesage.

    <!-- -->

    - #### FactoryConfigurationError

          public FactoryConfigurationError(java.lang.String msg)

      Create a new `FactoryConfigurationError` with the `String` specified as an error message.
      Parameters:
      `msg` - The error message for the exception.

    <!-- -->

    - #### FactoryConfigurationError

          public FactoryConfigurationError(java.lang.Exception e)

      Create a new `FactoryConfigurationError` with a given `Exception` base cause of the error.
      Parameters:
      `e` - The exception to be encapsulated in a FactoryConfigurationError.

    <!-- -->

    - #### FactoryConfigurationError

          public FactoryConfigurationError(java.lang.Exception e,
                                           java.lang.String msg)

      Create a new `FactoryConfigurationError` with the given `Exception` base cause and detail message.
      Parameters:
      `msg` - The detail message.

      `e` - The exception to be wrapped in a FactoryConfigurationError

  <!-- -->

  - ### Method Detail

    - #### getMessage

          public java.lang.String getMessage()

      Return the message (if any) for this error . If there is no message for the exception and there is an encapsulated exception then the message of that exception will be returned.
      Overrides:
      `getMessage` in class `java.lang.Throwable`

      Returns:
      The error message.

    <!-- -->

    - #### getException

          public java.lang.Exception getException()

      Return the actual exception (if any) that caused this exception to be raised.
      Returns:
      The encapsulated exception, or null if there is none.

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

- **[Prev Class](DocumentBuilderFactory.md)**
- **[Next Class](ParserConfigurationException.md)**

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
