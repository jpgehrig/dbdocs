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

- **[Prev Class](SAXNotSupportedException.md)**
- **[Next Class](XMLFilter.md)**

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

## **Class SAXParseException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[org.xml.sax.SAXException](SAXException.md)**

      - - **org.xml.sax.SAXParseException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  <!-- -->

  **Direct Known Subclasses:**
  **[XMLParseException](../../../oracle/xml/parser/v2/XMLParseException.md)**

  ------------------------------------------------------------------------

  **
  **

      public class SAXParseException
      extends SAXException

  **Encapsulate an XML parse error or warning.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This exception will include information for locating the error in the original XML document. Note that although the application will receive a SAXParseException as the argument to the handlers in the [`ErrorHandler`](ErrorHandler.md) interface, the application is not actually required to throw the exception; instead, it can simply read the information in it and take a different action.**

  **Since this exception is a subclass of [`SAXException`](SAXException.md), it inherits the ability to wrap another exception.**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`SAXException`](SAXException.md), [`Locator`](Locator.md), [`ErrorHandler`](ErrorHandler.md), [Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SAXParseException``(java.lang.String message, `[`Locator`](Locator.md)` locator)`<br>Create a new SAXParseException from a message and a Locator.                                                                           |
    | `SAXParseException``(java.lang.String message, `[`Locator`](Locator.md)` locator, java.lang.Exception e)`<br>Wrap an existing exception in a SAXParseException.                                                              |
    | `SAXParseException``(java.lang.String message, java.lang.String publicId, java.lang.String systemId, int lineNumber, int columnNumber)`<br>Create a new SAXParseException.                                                   |
    | `SAXParseException``(java.lang.String message, java.lang.String publicId, java.lang.String systemId, int lineNumber, int columnNumber, java.lang.Exception e)`<br>Create a new SAXParseException with an embedded exception. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                          |
    |--------------------|-------------------------------------------------------------------------------------------------|
    | `int`              | `getColumnNumber``()`<br>The column number of the end of the text where the exception occurred. |
    | `int`              | `getLineNumber``()`<br>The line number of the end of the text where the exception occurred.     |
    | `java.lang.String` | `getPublicId``()`<br>Get the public identifier of the entity where the exception occurred.      |
    | `java.lang.String` | `getSystemId``()`<br>Get the system identifier of the entity where the exception occurred.      |

    - ### Methods inherited from class org.xml.sax.[SAXException](SAXException.md)

      [`getException`](SAXException.md)`, `[`getMessage`](SAXException.md)`, `[`toString`](SAXException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SAXParseException

          public SAXParseException(java.lang.String message,
                                   Locator locator)

      Create a new SAXParseException from a message and a Locator.
      This constructor is especially useful when an application is creating its own exception from within a [`ContentHandler`](ContentHandler.md) callback.

      Parameters:
      `message` - The error or warning message.

      `locator` - The locator object for the error or warning (may be null).

      See Also:
      [`Locator`](Locator.md), [`Parser.setLocale(java.util.Locale)`](Parser.md)

    <!-- -->

    - #### SAXParseException

          public SAXParseException(java.lang.String message,
                                   Locator locator,
                                   java.lang.Exception e)

      Wrap an existing exception in a SAXParseException.
      This constructor is especially useful when an application is creating its own exception from within a [`ContentHandler`](ContentHandler.md) callback, and needs to wrap an existing exception that is not a subclass of [`SAXException`](SAXException.md).

      Parameters:
      `message` - The error or warning message, or null to use the message from the embedded exception.

      `locator` - The locator object for the error or warning (may be null).

      `e` - Any exception.

      See Also:
      [`Locator`](Locator.md), [`Parser.setLocale(java.util.Locale)`](Parser.md)

    <!-- -->

    - #### SAXParseException

          public SAXParseException(java.lang.String message,
                                   java.lang.String publicId,
                                   java.lang.String systemId,
                                   int lineNumber,
                                   int columnNumber)

      Create a new SAXParseException.
      This constructor is most useful for parser writers.

      If the system identifier is a URL, the parser must resolve it fully before creating the exception.

      Parameters:
      `message` - The error or warning message.

      `publicId` - The public identifer of the entity that generated the error or warning.

      `systemId` - The system identifer of the entity that generated the error or warning.

      `lineNumber` - The line number of the end of the text that caused the error or warning.

      `columnNumber` - The column number of the end of the text that cause the error or warning.

      See Also:
      [`Parser.setLocale(java.util.Locale)`](Parser.md)

    <!-- -->

    - #### SAXParseException

          public SAXParseException(java.lang.String message,
                                   java.lang.String publicId,
                                   java.lang.String systemId,
                                   int lineNumber,
                                   int columnNumber,
                                   java.lang.Exception e)

      Create a new SAXParseException with an embedded exception.
      This constructor is most useful for parser writers who need to wrap an exception that is not a subclass of [`SAXException`](SAXException.md).

      If the system identifier is a URL, the parser must resolve it fully before creating the exception.

      Parameters:
      `message` - The error or warning message, or null to use the message from the embedded exception.

      `publicId` - The public identifer of the entity that generated the error or warning.

      `systemId` - The system identifer of the entity that generated the error or warning.

      `lineNumber` - The line number of the end of the text that caused the error or warning.

      `columnNumber` - The column number of the end of the text that cause the error or warning.

      `e` - Another exception to embed in this one.

      See Also:
      [`Parser.setLocale(java.util.Locale)`](Parser.md)

  <!-- -->

  - ### Method Detail

    - #### getPublicId

          public java.lang.String getPublicId()

      Get the public identifier of the entity where the exception occurred.
      Returns:
      A string containing the public identifier, or null if none is available.

      See Also:
      [`Locator.getPublicId()`](Locator.md)

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Get the system identifier of the entity where the exception occurred.
      If the system identifier is a URL, it will be resolved fully.

      Returns:
      A string containing the system identifier, or null if none is available.

      See Also:
      [`Locator.getSystemId()`](Locator.md)

    <!-- -->

    - #### getLineNumber

          public int getLineNumber()

      The line number of the end of the text where the exception occurred.
      Returns:
      An integer representing the line number, or -1 if none is available.

      See Also:
      [`Locator.getLineNumber()`](Locator.md)

    <!-- -->

    - #### getColumnNumber

          public int getColumnNumber()

      The column number of the end of the text where the exception occurred.
      The first column in a line is position 1.

      Returns:
      An integer representing the column number, or -1 if none is available.

      See Also:
      [`Locator.getColumnNumber()`](Locator.md)

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

- **[Prev Class](SAXNotSupportedException.md)**
- **[Next Class](XMLFilter.md)**

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
