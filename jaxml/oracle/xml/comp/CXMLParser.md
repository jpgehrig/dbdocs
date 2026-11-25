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

- **[Prev Class](CXMLHandlerBase.md)**
- **Next Class**

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

**oracle.xml.comp**

## **Class CXMLParser**

- **java.lang.Object**

- - **oracle.xml.comp.CXMLParser**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class CXMLParser
      extends java.lang.Object

  **This class implements the re-generation of XML document from the compressed stream by generating the SAX events from them.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                            |
    |----------------------------------------------------------------------------------------|
    | `CXMLParser``()`<br>Creates a new XML Parser object for reading the compressed stream. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                          | Method and Description                                                                                                          |
    |------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | [`ContentHandler`](../../../org/xml/sax/ContentHandler.md) | `getContentHandler``()`<br>Get content handler                                                                                  |
    | [`ErrorHandler`](../../../org/xml/sax/ErrorHandler.md)     | `getErrorHandler``()`<br>Get the current error handler                                                                          |
    | `void`                                                     | `parse``(java.io.ObjectInput objIn)`<br>Parse the compressed stream and generates the SAX events.                               |
    | `void`                                                     | `parse``(java.lang.String inFile)`<br>Parse the compressed stream and generates the SAX events.                                 |
    | `void`                                                     | `setContentHandler``(`[`ContentHandler`](../../../org/xml/sax/ContentHandler.md)` handler)`<br>Register a content event handler |
    | `void`                                                     | `setErrorHandler``(`[`ErrorHandler`](../../../org/xml/sax/ErrorHandler.md)` handler)`<br>Register an error event handler        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### CXMLParser

          public CXMLParser()

      Creates a new XML Parser object for reading the compressed stream.

  <!-- -->

  - ### Method Detail

    - #### setContentHandler

          public void setContentHandler(ContentHandler handler)

      Register a content event handler
      Parameters:
      `handler` - The content handler

    <!-- -->

    - #### getContentHandler

          public ContentHandler getContentHandler()

      Get content handler
      Returns:
      The current content handler or null if none has been registered.

    <!-- -->

    - #### setErrorHandler

          public void setErrorHandler(ErrorHandler handler)

      Register an error event handler
      Parameters:
      `handler` - The error handler

    <!-- -->

    - #### getErrorHandler

          public ErrorHandler getErrorHandler()

      Get the current error handler
      Returns:
      The current error handler, or null if none has been registered

    <!-- -->

    - #### parse

          public void parse(java.lang.String inFile)
                     throws java.io.IOException,
                            SAXException

      Parse the compressed stream and generates the SAX events.
      Parameters:
      `inFile` - The input source which needs to be parsed to regenerate the SAX events.

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - any SAX exception

      `java.io.IOException` - an error due to I/O operations

    <!-- -->

    - #### parse

          public void parse(java.io.ObjectInput objIn)
                     throws java.io.IOException,
                            SAXException

      Parse the compressed stream and generates the SAX events.
      Parameters:
      `objIn` - The input source which needs to be parsed to regenerate the SAX events.

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - any SAX exception

      `java.io.IOException` - an error due to I/O operations

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

- **[Prev Class](CXMLHandlerBase.md)**
- **Next Class**

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
