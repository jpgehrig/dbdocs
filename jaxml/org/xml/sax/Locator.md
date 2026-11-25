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

- **[Prev Class](InputSource.md)**
- **[Next Class](Parser.md)**

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

## **Interface Locator**

- **All Known Subinterfaces:**
  **[Locator2](ext/Locator2.md), [XMLLocator](../../../oracle/xml/parser/v2/XMLLocator.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[Locator2Impl](ext/Locator2Impl.md), [LocatorImpl](helpers/LocatorImpl.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Locator

  **Interface for associating a SAX event with a document location.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **If a SAX parser provides location information to the SAX application, it does so by implementing this interface and then passing an instance to the application using the content handler's [`setDocumentLocator`](ContentHandler.md) method. The application can use the object to obtain the location of any other content handler event in the XML source document.**

  **Note that the results returned by the object will be valid only during the scope of each content handler method: the application will receive unpredictable results if it attempts to use the locator at any other time.**

  **SAX parsers are not required to supply a locator, but they are very strongly encouraged to do so. If the parser supplies a locator, it must do so before reporting any other document events. If no locator has been set by the time the application receives the [`startDocument`](ContentHandler.md) event, the application should assume that a locator is not available.**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`ContentHandler.setDocumentLocator(org.xml.sax.Locator)`](ContentHandler.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                   |
    |--------------------|------------------------------------------------------------------------------------------|
    | `int`              | `getColumnNumber``()`<br>Return the column number where the current document event ends. |
    | `int`              | `getLineNumber``()`<br>Return the line number where the current document event ends.     |
    | `java.lang.String` | `getPublicId``()`<br>Return the public identifier for the current document event.        |
    | `java.lang.String` | `getSystemId``()`<br>Return the system identifier for the current document event.        |

<!-- -->

- - ### Method Detail

    - #### getPublicId

          java.lang.String getPublicId()

      Return the public identifier for the current document event.
      The return value is the public identifier of the document entity or of the external parsed entity in which the markup triggering the event appears.

      Returns:
      A string containing the public identifier, or null if none is available.

      See Also:
      `getSystemId()`

    <!-- -->

    - #### getSystemId

          java.lang.String getSystemId()

      Return the system identifier for the current document event.
      The return value is the system identifier of the document entity or of the external parsed entity in which the markup triggering the event appears.

      If the system identifier is a URL, the parser must resolve it fully before passing it to the application.

      Returns:
      A string containing the system identifier, or null if none is available.

      See Also:
      `getPublicId()`

    <!-- -->

    - #### getLineNumber

          int getLineNumber()

      Return the line number where the current document event ends.
      **Warning:** The return value from the method is intended only as an approximation for the sake of error reporting; it is not intended to provide sufficient information to edit the character content of the original XML document.

      The return value is an approximation of the line number in the document entity or external parsed entity where the markup triggering the event appears.

      If possible, the SAX driver should provide the line position of the first character after the text associated with the document event. The first line in the document is line 1.

      Returns:
      The line number, or -1 if none is available.

      See Also:
      `getColumnNumber()`

    <!-- -->

    - #### getColumnNumber

          int getColumnNumber()

      Return the column number where the current document event ends.
      **Warning:** The return value from the method is intended only as an approximation for the sake of error reporting; it is not intended to provide sufficient information to edit the character content of the original XML document.

      The return value is an approximation of the column number in the document entity or external parsed entity where the markup triggering the event appears.

      If possible, the SAX driver should provide the line position of the first character after the text associated with the document event.

      If possible, the SAX driver should provide the line position of the first character after the text associated with the document event. The first column in each line is column 1.

      Returns:
      The column number, or -1 if none is available.

      See Also:
      `getLineNumber()`

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

- **[Prev Class](InputSource.md)**
- **[Next Class](Parser.md)**

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
