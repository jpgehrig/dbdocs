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

- **[Prev Class](Parser.md)**
- **[Next Class](SAXNotRecognizedException.md)**

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

**org.xml.sax**

## **Class SAXException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **org.xml.sax.SAXException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  <!-- -->

  **Direct Known Subclasses:**
  **[SAXNotRecognizedException](SAXNotRecognizedException.md), [SAXNotSupportedException](SAXNotSupportedException.md), [SAXParseException](SAXParseException.md)**

  ------------------------------------------------------------------------

  **
  **

      public class SAXException
      extends java.lang.Exception

  **Encapsulate a general SAX error or warning.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class can contain basic error or warning information from either the XML parser or the application: a parser writer or application writer can subclass it to provide additional functionality. SAX handlers may throw this exception or any exception subclassed from it.**

  **If the application needs to pass through other types of exceptions, it must wrap those exceptions in a SAXException or an exception derived from a SAXException.**

  **If the parser or application needs to include information about a specific location in an XML document, it should use the [`SAXParseException`](SAXParseException.md) subclass.**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`SAXParseException`](SAXParseException.md), [Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                |
    |----------------------------------------------------------------------------------------------------------------------------|
    | `SAXException``()`<br>Create a new SAXException.                                                                           |
    | `SAXException``(java.lang.Exception e)`<br>Create a new SAXException wrapping an existing exception.                       |
    | `SAXException``(java.lang.String message)`<br>Create a new SAXException.                                                   |
    | `SAXException``(java.lang.String message, java.lang.Exception e)`<br>Create a new SAXException from an existing exception. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                 |
    |-----------------------|------------------------------------------------------------------------|
    | `java.lang.Exception` | `getException``()`<br>Return the embedded exception, if any.           |
    | `java.lang.String`    | `getMessage``()`<br>Return a detail message for this exception.        |
    | `java.lang.String`    | `toString``()`<br>Override toString to pick up any embedded exception. |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SAXException

          public SAXException()

      Create a new SAXException.

    <!-- -->

    - #### SAXException

          public SAXException(java.lang.String message)

      Create a new SAXException.
      Parameters:
      `message` - The error or warning message.

      See Also:
      [`Parser.setLocale(java.util.Locale)`](Parser.md)

    <!-- -->

    - #### SAXException

          public SAXException(java.lang.Exception e)

      Create a new SAXException wrapping an existing exception.
      The existing exception will be embedded in the new one, and its message will become the default message for the SAXException.

      Parameters:
      `e` - The exception to be wrapped in a SAXException.

    <!-- -->

    - #### SAXException

          public SAXException(java.lang.String message,
                              java.lang.Exception e)

      Create a new SAXException from an existing exception.
      The existing exception will be embedded in the new one, but the new exception will have its own message.

      Parameters:
      `message` - The detail message.

      `e` - The exception to be wrapped in a SAXException.

      See Also:
      [`Parser.setLocale(java.util.Locale)`](Parser.md)

  <!-- -->

  - ### Method Detail

    - #### getMessage

          public java.lang.String getMessage()

      Return a detail message for this exception.
      If there is an embedded exception, and if the SAXException has no detail message of its own, this method will return the detail message from the embedded exception.

      Overrides:
      `getMessage` in class `java.lang.Throwable`

      Returns:
      The error or warning message.

      See Also:
      [`Parser.setLocale(java.util.Locale)`](Parser.md)

    <!-- -->

    - #### getException

          public java.lang.Exception getException()

      Return the embedded exception, if any.
      Returns:
      The embedded exception, or null if there is none.

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Override toString to pick up any embedded exception.
      Overrides:
      `toString` in class `java.lang.Throwable`

      Returns:
      A string representation of this exception.

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

- **[Prev Class](Parser.md)**
- **[Next Class](SAXNotRecognizedException.md)**

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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
