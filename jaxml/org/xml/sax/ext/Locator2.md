Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](LexicalHandler.md)**
- **[Next Class](Locator2Impl.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**org.xml.sax.ext**

## **Interface Locator2**

- **All Superinterfaces:**
  **[Locator](../Locator.md)**

  <!-- -->

  **All Known Subinterfaces:**
  **[XMLLocator](../../../../oracle/xml/parser/v2/XMLLocator.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[Locator2Impl](Locator2Impl.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Locator2
      extends Locator

  **SAX2 extension to augment the entity information provided though a [`Locator`](../Locator.md). If an implementation supports this extension, the Locator provided in [`ContentHandler.setDocumentLocator()`](../ContentHandler.md) will implement this interface, and the *http://xml.org/sax/features/use-locator2* feature flag will have the value *true*.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **XMLReader implementations are not required to support this information, and it is not part of core-only SAX2 distributions.**

  **Since:**
  **SAX 2.0 (extensions 1.1 alpha)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                          |
    |--------------------|---------------------------------------------------------------------------------|
    | `java.lang.String` | `getEncoding``()`<br>Returns the name of the character encoding for the entity. |
    | `java.lang.String` | `getXMLVersion``()`<br>Returns the version of XML used for the entity.          |

    - ### Methods inherited from interface org.xml.sax.[Locator](../Locator.md)

      [`getColumnNumber`](../Locator.md)`, `[`getLineNumber`](../Locator.md)`, `[`getPublicId`](../Locator.md)`, `[`getSystemId`](../Locator.md)

<!-- -->

- - ### Method Detail

    - #### getXMLVersion

          java.lang.String getXMLVersion()

      Returns the version of XML used for the entity. This will normally be the identifier from the current entity's *\<?xml version='...' ...?\>* declaration, or be defaulted by the parser.
      Returns:
      Identifier for the XML version being used to interpret the entity's text, or null if that information is not yet available in the current parsing state.

    <!-- -->

    - #### getEncoding

          java.lang.String getEncoding()

      Returns the name of the character encoding for the entity. If the encoding was declared externally (for example, in a MIME Content-Type header), that will be the name returned. Else if there was an *\<?xml ...encoding='...'?\>* declaration at the start of the document, that encoding name will be returned. Otherwise the encoding will been inferred (normally to be UTF-8, or some UTF-16 variant), and that inferred name will be returned.
      When an [`InputSource`](../InputSource.md) is used to provide an entity's character stream, this method returns the encoding provided in that input stream.

      Note that some recent W3C specifications require that text in some encodings be normalized, using Unicode Normalization Form C, before processing. Such normalization must be performed by applications, and would normally be triggered based on the value returned by this method.

      Encoding names may be those used by the underlying JVM, and comparisons should be case-insensitive.

      Returns:
      Name of the character encoding being used to interpret \* the entity's text, or null if this was not provided for a \* character stream passed through an InputSource or is otherwise not yet available in the current parsing state.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](LexicalHandler.md)**
- **[Next Class](Locator2Impl.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
