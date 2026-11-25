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

- **[Prev Class](SAXResult.md)**
- **[Next Class](SAXTransformerFactory.md)**

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

**javax.xml.transform.sax**

## **Class SAXSource**

- **java.lang.Object**

- - **javax.xml.transform.sax.SAXSource**

<!-- -->

- **All Implemented Interfaces:**
  **[Source](../Source.md)**

  ------------------------------------------------------------------------

  **
  **

      public class SAXSource
      extends java.lang.Object
      implements Source

  **Acts as an holder for SAX-style Source.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                                 |
    |---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `FEATURE`<br>If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the Transformer supports Source input of this type. |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                                         |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SAXSource``()`<br>Zero-argument default constructor.                                                                                                                                                               |
    | `SAXSource``(`[`InputSource`](../../../../org/xml/sax/InputSource.md)` inputSource)`<br>Create a SAXSource, using a SAX InputSource.                                                                                |
    | `SAXSource``(`[`XMLReader`](../../../../org/xml/sax/XMLReader.md)` reader, `[`InputSource`](../../../../org/xml/sax/InputSource.md)` inputSource)`<br>Create a SAXSource, using an XMLReader and a SAX InputSource. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                | Method and Description                                                                                                                          |
    |------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`InputSource`](../../../../org/xml/sax/InputSource.md)          | `getInputSource``()`<br>Get the SAX InputSource to be used for the Source.                                                                      |
    | `java.lang.String`                                               | `getSystemId``()`<br>Get the base ID (URI or system ID) from where URIs will be resolved.                                                       |
    | [`XMLReader`](../../../../org/xml/sax/XMLReader.md)              | `getXMLReader``()`<br>Get the XMLReader to be used for the Source.                                                                              |
    | `void`                                                           | `setInputSource``(`[`InputSource`](../../../../org/xml/sax/InputSource.md)` inputSource)`<br>Set the SAX InputSource to be used for the Source. |
    | `void`                                                           | `setSystemId``(java.lang.String systemId)`<br>Set the system identifier for this Source.                                                        |
    | `void`                                                           | `setXMLReader``(`[`XMLReader`](../../../../org/xml/sax/XMLReader.md)` reader)`<br>Set the XMLReader to be used for the Source.                  |
    | `static `[`InputSource`](../../../../org/xml/sax/InputSource.md) | `sourceToInputSource``(`[`Source`](../Source.md)` source)`<br>Attempt to obtain a SAX InputSource object from a TrAX Source object.             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### FEATURE

          public static final java.lang.String FEATURE

      If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the Transformer supports Source input of this type.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### SAXSource

          public SAXSource()

      Zero-argument default constructor. If this constructor is used, and no other method is called, the Transformer assumes an empty input tree, with a default root node.

    <!-- -->

    - #### SAXSource

          public SAXSource(XMLReader reader,
                           InputSource inputSource)

      Create a SAXSource, using an XMLReader and a SAX InputSource. The Transformer or SAXTransformerFactory will set itself to be the reader's ContentHandler, and then will call reader.parse(inputSource).
      Parameters:
      `reader` - An XMLReader to be used for the parse.

      `inputSource` - A SAX input source reference that must be non-null and that will be passed to the reader parse method.

    <!-- -->

    - #### SAXSource

          public SAXSource(InputSource inputSource)

      Create a SAXSource, using a SAX InputSource. The Transformer or SAXTransformerFactory creates a reader via org.xml.sax.helpers.XMLReaderFactory (if setXMLReader is not used), sets itself as the reader's ContentHandler, and calls reader.parse(inputSource).
      Parameters:
      `inputSource` - An input source reference that must be non-null and that will be passed to the parse method of the reader.

  <!-- -->

  - ### Method Detail

    - #### setXMLReader

          public void setXMLReader(XMLReader reader)

      Set the XMLReader to be used for the Source.
      Parameters:
      `reader` - A valid XMLReader or XMLFilter reference.

    <!-- -->

    - #### getXMLReader

          public XMLReader getXMLReader()

      Get the XMLReader to be used for the Source.
      Returns:
      A valid XMLReader or XMLFilter reference, or null.

    <!-- -->

    - #### setInputSource

          public void setInputSource(InputSource inputSource)

      Set the SAX InputSource to be used for the Source.
      Parameters:
      `inputSource` - A valid InputSource reference.

    <!-- -->

    - #### getInputSource

          public InputSource getInputSource()

      Get the SAX InputSource to be used for the Source.
      Returns:
      A valid InputSource reference, or null.

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.lang.String systemId)

      Set the system identifier for this Source. If an input source has already been set, it will set the system ID or that input source, otherwise it will create a new input source.
      The system identifier is optional if there is a byte stream or a character stream, but it is still useful to provide one, since the application can use it to resolve relative URIs and can include it in error messages and warnings (the parser will attempt to open a connection to the URI only if no byte stream or character stream is specified).

      Specified by:
      [`setSystemId`](../Source.md) in interface [`Source`](../Source.md)

      Parameters:
      `systemId` - The system identifier as a URI string.

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Get the base ID (URI or system ID) from where URIs will be resolved.
      Specified by:
      [`getSystemId`](../Source.md) in interface [`Source`](../Source.md)

      Returns:
      Base URL for the Source, or null.

    <!-- -->

    - #### sourceToInputSource

          public static InputSource sourceToInputSource(Source source)

      Attempt to obtain a SAX InputSource object from a TrAX Source object.
      Parameters:
      `source` - Must be a non-null Source reference.

      Returns:
      An InputSource, or null if Source can not be converted.

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

- **[Prev Class](SAXResult.md)**
- **[Next Class](SAXTransformerFactory.md)**

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
