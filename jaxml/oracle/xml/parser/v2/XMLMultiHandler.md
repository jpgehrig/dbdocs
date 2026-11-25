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

- **[Prev Class](XMLLocator.md)**
- **[Next Class](XMLNode.md)**

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

**oracle.xml.parser.v2**

## **Class XMLMultiHandler**

- **java.lang.Object**

- - **oracle.xml.parser.v2.XMLMultiHandler**

<!-- -->

- **All Implemented Interfaces:**
  **[ContentHandler](../../../../org/xml/sax/ContentHandler.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[XSDValidator](../schema/XSDValidator.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLMultiHandler
      extends java.lang.Object
      implements ContentHandler

  **This utility class allow multiple content handlers registered and send all the events to the registered content handlers.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XMLMultiHandler``()`       |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                 | Method and Description                                                                                                                                                                                                    |
    |-------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                            | `addContentHandler``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` cntHandler)`<br>Add the next level ContentHandler the order in which the handler are called is not defined.                          |
    | `void`                                                            | `characters``(char[] ch, int start, int length)`<br>Receive notification of character data.                                                                                                                               |
    | `void`                                                            | `endDocument``()`<br>Receive notification of the end of a document.                                                                                                                                                       |
    | `void`                                                            | `endElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName)`<br>Receive notification of the end of an element.                                                                       |
    | `void`                                                            | `endPrefixMapping``(java.lang.String prefix)`<br>End the scope of a prefix-URI mapping.                                                                                                                                   |
    | [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)`[]` | `getContentHandlers``()`<br>Return the next level of ContentHandlers                                                                                                                                                      |
    | `int`                                                             | `getNumContentHandlers``()`<br>Return the number of ContentHandlers                                                                                                                                                       |
    | `void`                                                            | `ignorableWhitespace``(char[] ch, int start, int length)`<br>Receive notification of ignorable whitespace in element content.                                                                                             |
    | `void`                                                            | `processingInstruction``(java.lang.String target, java.lang.String data)`<br>Receive notification of a processing instruction.                                                                                            |
    | `boolean`                                                         | `removeContentHandler``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` cntHandler)`<br>Remove a content handler                                                                                          |
    | `void`                                                            | `setDocumentLocator``(`[`Locator`](../../../../org/xml/sax/Locator.md)` locator)`<br>Receive an object for locating the origin of SAX document events.                                                                    |
    | `void`                                                            | `skippedEntity``(java.lang.String name)`<br>Receive notification of a skipped entity.                                                                                                                                     |
    | `void`                                                            | `startDocument``()`<br>Receive notification of the beginning of a document.                                                                                                                                               |
    | `void`                                                            | `startElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName, `[`Attributes`](../../../../org/xml/sax/Attributes.md)` atts)`<br>Receive notification of the beginning of an element. |
    | `void`                                                            | `startPrefixMapping``(java.lang.String prefix, java.lang.String uri)`<br>Begin the scope of a prefix-URI Namespace mapping.                                                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLMultiHandler

          public XMLMultiHandler()

  <!-- -->

  - ### Method Detail

    - #### setDocumentLocator

          public void setDocumentLocator(Locator locator)

      Receive an object for locating the origin of SAX document events.
      Specified by:
      [`setDocumentLocator`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Parameters:
      `locator` - An object that can return the location of any SAX document event.

      See Also:
      [`Locator`](../../../../org/xml/sax/Locator.md)

    <!-- -->

    - #### startDocument

          public void startDocument()
                             throws SAXException

      Receive notification of the beginning of a document.
      Specified by:
      [`startDocument`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `endDocument()`

    <!-- -->

    - #### endDocument

          public void endDocument()
                           throws SAXException

      Receive notification of the end of a document.
      Specified by:
      [`endDocument`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `startDocument()`

    <!-- -->

    - #### startPrefixMapping

          public void startPrefixMapping(java.lang.String prefix,
                                         java.lang.String uri)
                                  throws SAXException

      Begin the scope of a prefix-URI Namespace mapping.
      Specified by:
      [`startPrefixMapping`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Parameters:
      `prefix` - The Namespace prefix being declared.

      `uri` - The Namespace URI the prefix is mapped to.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The client may throw an exception during processing.

      See Also:
      `endPrefixMapping(java.lang.String)`, `startElement(java.lang.String, java.lang.String, java.lang.String, org.xml.sax.Attributes)`

    <!-- -->

    - #### endPrefixMapping

          public void endPrefixMapping(java.lang.String prefix)
                                throws SAXException

      End the scope of a prefix-URI mapping.
      Specified by:
      [`endPrefixMapping`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Parameters:
      `prefix` - The prefix that was being mapping.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The client may throw an exception during processing.

      See Also:
      `startPrefixMapping(java.lang.String, java.lang.String)`, `endElement(java.lang.String, java.lang.String, java.lang.String)`

    <!-- -->

    - #### startElement

          public void startElement(java.lang.String namespaceURI,
                                   java.lang.String localName,
                                   java.lang.String qName,
                                   Attributes atts)
                            throws SAXException

      Receive notification of the beginning of an element.
      Specified by:
      [`startElement`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Parameters:
      `namespaceURI` - The Namespace URI, or the empty string if the element has no Namespace URI or if Namespace processing is not being performed.

      `localName` - The local name (without prefix), or the empty string if Namespace processing is not being performed.

      `qName` - The qualified name (with prefix), or the empty string if qualified names are not available.

      `atts` - The attributes attached to the element. If there are no attributes, it shall be an empty Attributes object.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `endElement(java.lang.String, java.lang.String, java.lang.String)`, [`Attributes`](../../../../org/xml/sax/Attributes.md)

    <!-- -->

    - #### endElement

          public void endElement(java.lang.String namespaceURI,
                                 java.lang.String localName,
                                 java.lang.String qName)
                          throws SAXException

      Receive notification of the end of an element.
      Specified by:
      [`endElement`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Parameters:
      `namespaceURI` - The Namespace URI, or the empty string if the element has no Namespace URI or if Namespace processing is not being performed.

      `localName` - The local name (without prefix), or the empty string if Namespace processing is not being performed.

      `qName` - The qualified XML 1.0 name (with prefix), or the empty string if qualified names are not available.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### characters

          public void characters(char[] ch,
                                 int start,
                                 int length)
                          throws SAXException

      Receive notification of character data.
      Specified by:
      [`characters`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Parameters:
      `ch` - The characters from the XML document.

      `start` - The start position in the array.

      `length` - The number of characters to read from the array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `ignorableWhitespace(char[], int, int)`, [`Locator`](../../../../org/xml/sax/Locator.md)

    <!-- -->

    - #### ignorableWhitespace

          public void ignorableWhitespace(char[] ch,
                                          int start,
                                          int length)
                                   throws SAXException

      Receive notification of ignorable whitespace in element content.
      Specified by:
      [`ignorableWhitespace`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Parameters:
      `ch` - The characters from the XML document.

      `start` - The start position in the array.

      `length` - The number of characters to read from the array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `characters(char[], int, int)`

    <!-- -->

    - #### processingInstruction

          public void processingInstruction(java.lang.String target,
                                            java.lang.String data)
                                     throws SAXException

      Receive notification of a processing instruction.
      Specified by:
      [`processingInstruction`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Parameters:
      `target` - The processing instruction target.

      `data` - The processing instruction data, or null if none was supplied. The data does not include any whitespace separating it from the target.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### skippedEntity

          public void skippedEntity(java.lang.String name)
                             throws SAXException

      Receive notification of a skipped entity.
      Specified by:
      [`skippedEntity`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Parameters:
      `name` - The name of the skipped entity. If it is a parameter entity, the name will begin with '%', and if it is the external DTD subset, it will be the string "\[dtd\]".

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### addContentHandler

          public void addContentHandler(ContentHandler cntHandler)

      Add the next level ContentHandler the order in which the handler are called is not defined.
      Parameters:
      `cntHandler` - - ContentHandler

    <!-- -->

    - #### getContentHandlers

          public ContentHandler[] getContentHandlers()

      Return the next level of ContentHandlers
      Returns:
      ContentHandler Array

    <!-- -->

    - #### getNumContentHandlers

          public int getNumContentHandlers()

      Return the number of ContentHandlers
      Returns:
      count of ContentHandler

    <!-- -->

    - #### removeContentHandler

          public boolean removeContentHandler(ContentHandler cntHandler)

      Remove a content handler
      Parameters:
      `cntHandler` - content handler to be removed

      Returns:
      boolean TRUE if removed, false if not found

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

- **[Prev Class](XMLLocator.md)**
- **[Next Class](XMLNode.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
