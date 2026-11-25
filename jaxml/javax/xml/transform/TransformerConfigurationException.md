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

- **[Prev Class](Transformer.md)**
- **[Next Class](TransformerException.md)**

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

## **Class TransformerConfigurationException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[javax.xml.transform.TransformerException](TransformerException.md)**

      - - **javax.xml.transform.TransformerConfigurationException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class TransformerConfigurationException
      extends TransformerException

  **Indicates a serious configuration error.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TransformerConfigurationException``()`<br>Create a new `TransformerConfigurationException` with no detail mesage.                                                                                          |
    | `TransformerConfigurationException``(java.lang.String msg)`<br>Create a new `TransformerConfigurationException` with the `String` specified as an error message.                                            |
    | `TransformerConfigurationException``(java.lang.String message, `[`SourceLocator`](SourceLocator.md)` locator)`<br>Create a new TransformerConfigurationException from a message and a Locator.              |
    | `TransformerConfigurationException``(java.lang.String message, `[`SourceLocator`](SourceLocator.md)` locator, java.lang.Throwable e)`<br>Wrap an existing exception in a TransformerConfigurationException. |
    | `TransformerConfigurationException``(java.lang.String msg, java.lang.Throwable e)`<br>Create a new `TransformerConfigurationException` with the given `Exception` base cause and detail message.            |
    | `TransformerConfigurationException``(java.lang.Throwable e)`<br>Create a new `TransformerConfigurationException` with a given `Exception` base cause of the error.                                          |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class javax.xml.transform.[TransformerException](TransformerException.md)**

      **[`getCause`](TransformerException.md)`, `[`getException`](TransformerException.md)`, `[`getLocationAsString`](TransformerException.md)`, `[`getLocator`](TransformerException.md)`, `[`getMessageAndLocation`](TransformerException.md)`, `[`initCause`](TransformerException.md)`, `[`printStackTrace`](TransformerException.md)`, `[`printStackTrace`](TransformerException.md)`, `[`printStackTrace`](TransformerException.md)`, `[`setLocator`](TransformerException.md)**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Throwable**

      **`addSuppressed, fillInStackTrace, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, setStackTrace, toString`**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`**

<!-- -->

-
  -

    ### **Constructor Detail**

    - #### **TransformerConfigurationException**

          public TransformerConfigurationException()

      **Create a new `TransformerConfigurationException` with no detail mesage.**

    - #### **TransformerConfigurationException**

          public TransformerConfigurationException(java.lang.String msg)

      **Create a new `TransformerConfigurationException` with the `String` specified as an error message.**
      **Parameters:**
      **`msg` - The error message for the exception.**

    - #### **TransformerConfigurationException**

          public TransformerConfigurationException(java.lang.Throwable e)

      **Create a new `TransformerConfigurationException` with a given `Exception` base cause of the error.**
      **Parameters:**
      **`e` - The exception to be encapsulated in a TransformerConfigurationException.**

    - #### **TransformerConfigurationException**

          public TransformerConfigurationException(java.lang.String msg,
                                                   java.lang.Throwable e)

      **Create a new `TransformerConfigurationException` with the given `Exception` base cause and detail message.**
      **Parameters:**
      **`msg` - The detail message.**

      **`e` - The exception to be wrapped in a TransformerConfigurationException**

    - #### **TransformerConfigurationException**

          public TransformerConfigurationException(java.lang.String message,
                                                   SourceLocator locator)

      **Create a new TransformerConfigurationException from a message and a Locator.**
      **This constructor is especially useful when an application is creating its own exception from within a DocumentHandler callback.**

      **Parameters:**
      **`message` - The error or warning message.**

      **`locator` - The locator object for the error or warning.**

    - #### **TransformerConfigurationException**

          public TransformerConfigurationException(java.lang.String message,
                                                   SourceLocator locator,
                                                   java.lang.Throwable e)

      **Wrap an existing exception in a TransformerConfigurationException.**
      **Parameters:**
      **`message` - The error or warning message, or null to use the message from the embedded exception.**

      **`locator` - The locator object for the error or warning.**

      **`e` - Any exception.**

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

- **[Prev Class](Transformer.md)**
- **[Next Class](TransformerException.md)**

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
