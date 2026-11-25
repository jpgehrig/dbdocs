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

- **[Prev Class](TransformerFactory.md)**
- **[Next Class](URIResolver.md)**

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

**javax.xml.transform**

## **Class TransformerFactoryConfigurationError**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Error**

    - - **javax.xml.transform.TransformerFactoryConfigurationError**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class TransformerFactoryConfigurationError
      extends java.lang.Error

  **Thrown when a problem with configuration with the Transformer Factories exists. This error will typically be thrown when the class of a transformation factory specified in the system properties cannot be found or instantiated.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                            |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TransformerFactoryConfigurationError``()`<br>Create a new `TransformerFactoryConfigurationError` with no detail mesage.                                                                               |
    | `TransformerFactoryConfigurationError``(java.lang.Exception e)`<br>Create a new `TransformerFactoryConfigurationError` with a given `Exception` base cause of the error.                               |
    | `TransformerFactoryConfigurationError``(java.lang.Exception e, java.lang.String msg)`<br>Create a new `TransformerFactoryConfigurationError` with the given `Exception` base cause and detail message. |
    | `TransformerFactoryConfigurationError``(java.lang.String msg)`<br>Create a new `TransformerFactoryConfigurationError` with the `String` specified as an error message.                                 |

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

    - #### TransformerFactoryConfigurationError

          public TransformerFactoryConfigurationError()

      Create a new `TransformerFactoryConfigurationError` with no detail mesage.

    <!-- -->

    - #### TransformerFactoryConfigurationError

          public TransformerFactoryConfigurationError(java.lang.String msg)

      Create a new `TransformerFactoryConfigurationError` with the `String` specified as an error message.
      Parameters:
      `msg` - The error message for the exception.

    <!-- -->

    - #### TransformerFactoryConfigurationError

          public TransformerFactoryConfigurationError(java.lang.Exception e)

      Create a new `TransformerFactoryConfigurationError` with a given `Exception` base cause of the error.
      Parameters:
      `e` - The exception to be encapsulated in a TransformerFactoryConfigurationError.

    <!-- -->

    - #### TransformerFactoryConfigurationError

          public TransformerFactoryConfigurationError(java.lang.Exception e,
                                                      java.lang.String msg)

      Create a new `TransformerFactoryConfigurationError` with the given `Exception` base cause and detail message.
      Parameters:
      `msg` - The detail message.

      `e` - The exception to be wrapped in a TransformerFactoryConfigurationError

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

- **[Prev Class](TransformerFactory.md)**
- **[Next Class](URIResolver.md)**

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
