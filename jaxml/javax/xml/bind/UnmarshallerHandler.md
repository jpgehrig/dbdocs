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

- **[Prev Class](Unmarshaller.md)**
- **[Next Class](ValidationEvent.md)**

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

**javax.xml.bind**

## **Interface UnmarshallerHandler**

- **All Superinterfaces:**
  **[ContentHandler](../../../org/xml/sax/ContentHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface UnmarshallerHandler
      extends ContentHandler

  **Unmarshaller implemented as SAX ContentHandler.**
  **Application can use this interface to use JAXB provider as a component in an XML pipeline.**

  **This interface is reusable: even if the user fails to unmarshal an object, s/he can still start a new round of unmarshalling.**

  **Since:**
  **JAXB1.0**

  **See Also:**
  **[`Unmarshaller.getUnmarshallerHandler()`](Unmarshaller.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                              |
    |--------------------|-----------------------------------------------------|
    | `java.lang.Object` | `getResult``()`<br>Obtains the unmarshalled result. |

    - ### Methods inherited from interface org.xml.sax.[ContentHandler](../../../org/xml/sax/ContentHandler.md)

      [`characters`](../../../org/xml/sax/ContentHandler.md)`, `[`endDocument`](../../../org/xml/sax/ContentHandler.md)`, `[`endElement`](../../../org/xml/sax/ContentHandler.md)`, `[`endPrefixMapping`](../../../org/xml/sax/ContentHandler.md)`, `[`ignorableWhitespace`](../../../org/xml/sax/ContentHandler.md)`, `[`processingInstruction`](../../../org/xml/sax/ContentHandler.md)`, `[`setDocumentLocator`](../../../org/xml/sax/ContentHandler.md)`, `[`skippedEntity`](../../../org/xml/sax/ContentHandler.md)`, `[`startDocument`](../../../org/xml/sax/ContentHandler.md)`, `[`startElement`](../../../org/xml/sax/ContentHandler.md)`, `[`startPrefixMapping`](../../../org/xml/sax/ContentHandler.md)

<!-- -->

- - ### Method Detail

    - #### getResult

          java.lang.Object getResult()
                              throws JAXBException,
                                     java.lang.IllegalStateException

      Obtains the unmarshalled result. This method can be called only after this handler receives the endDocument SAX event.
      Returns:
      always return a non-null valid object which was unmarshalled.

      Throws:
      `java.lang.IllegalStateException` - if this method is called before this handler receives the endDocument event.

      [`JAXBException`](JAXBException.md) - if there is any unmarshalling error. Note that the implementation is allowed to throw SAXException during the parsing when it finds an error.

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

- **[Prev Class](Unmarshaller.md)**
- **[Next Class](ValidationEvent.md)**

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
