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

- **[Prev Class](StreamResult.md)**
- **Next Class**

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

**javax.xml.transform.stream**

## **Class StreamSource**

- **java.lang.Object**

- - **javax.xml.transform.stream.StreamSource**

<!-- -->

- **All Implemented Interfaces:**
  **[Source](../Source.md)**

  ------------------------------------------------------------------------

  **
  **

      public class StreamSource
      extends java.lang.Object
      implements Source

  **Acts as an holder for a transformation Source in the form of a stream of XML markup.**

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

    | Constructor and Description                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------|
    | `StreamSource``()`<br>Zero-argument default constructor.                                                                     |
    | `StreamSource``(java.io.File f)`<br>Construct a StreamSource from a File.                                                    |
    | `StreamSource``(java.io.InputStream inputStream)`<br>Construct a StreamSource from a byte stream.                            |
    | `StreamSource``(java.io.InputStream inputStream, java.lang.String systemId)`<br>Construct a StreamSource from a byte stream. |
    | `StreamSource``(java.io.Reader reader)`<br>Construct a StreamSource from a character reader.                                 |
    | `StreamSource``(java.io.Reader reader, java.lang.String systemId)`<br>Construct a StreamSource from a character reader.      |
    | `StreamSource``(java.lang.String systemId)`<br>Construct a StreamSource from a URL.                                          |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                          |
    |-----------------------|-------------------------------------------------------------------------------------------------|
    | `java.io.InputStream` | `getInputStream``()`<br>Get the byte stream that was set with setByteStream.                    |
    | `java.lang.String`    | `getPublicId``()`<br>Get the public identifier that was set with setPublicId.                   |
    | `java.io.Reader`      | `getReader``()`<br>Get the character stream that was set with setReader.                        |
    | `java.lang.String`    | `getSystemId``()`<br>Get the system identifier that was set with setSystemId.                   |
    | `void`                | `setInputStream``(java.io.InputStream inputStream)`<br>Set the byte stream to be used as input. |
    | `void`                | `setPublicId``(java.lang.String publicId)`<br>Set the public identifier for this Source.        |
    | `void`                | `setReader``(java.io.Reader reader)`<br>Set the input to be a character reader.                 |
    | `void`                | `setSystemId``(java.io.File f)`<br>Set the system ID from a File reference.                     |
    | `void`                | `setSystemId``(java.lang.String systemId)`<br>Set the system identifier for this Source.        |

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

    - #### StreamSource

          public StreamSource()

      Zero-argument default constructor. If this constructor is used, and no other method is called, the transformer will assume an empty input tree, with a default root node.

    <!-- -->

    - #### StreamSource

          public StreamSource(java.io.InputStream inputStream)

      Construct a StreamSource from a byte stream. Normally, a stream should be used rather than a reader, so the XML parser can resolve character encoding specified by the XML declaration.
      If this constructor is used to process a stylesheet, normally setSystemId should also be called, so that relative URI references can be resolved.

      Parameters:
      `inputStream` - A valid InputStream reference to an XML stream.

    <!-- -->

    - #### StreamSource

          public StreamSource(java.io.InputStream inputStream,
                              java.lang.String systemId)

      Construct a StreamSource from a byte stream. Normally, a stream should be used rather than a reader, so that the XML parser can resolve character encoding specified by the XML declaration.
      This constructor allows the systemID to be set in addition to the input stream, which allows relative URIs to be processed.

      Parameters:
      `inputStream` - A valid InputStream reference to an XML stream.

      `systemId` - Must be a String that conforms to the URI syntax.

    <!-- -->

    - #### StreamSource

          public StreamSource(java.io.Reader reader)

      Construct a StreamSource from a character reader. Normally, a stream should be used rather than a reader, so that the XML parser can resolve character encoding specified by the XML declaration. However, in many cases the encoding of the input stream is already resolved, as in the case of reading XML from a StringReader.
      Parameters:
      `reader` - A valid Reader reference to an XML character stream.

    <!-- -->

    - #### StreamSource

          public StreamSource(java.io.Reader reader,
                              java.lang.String systemId)

      Construct a StreamSource from a character reader. Normally, a stream should be used rather than a reader, so that the XML parser may resolve character encoding specified by the XML declaration. However, in many cases the encoding of the input stream is already resolved, as in the case of reading XML from a StringReader.
      Parameters:
      `reader` - A valid Reader reference to an XML character stream.

      `systemId` - Must be a String that conforms to the URI syntax.

    <!-- -->

    - #### StreamSource

          public StreamSource(java.lang.String systemId)

      Construct a StreamSource from a URL.
      Parameters:
      `systemId` - Must be a String that conforms to the URI syntax.

    <!-- -->

    - #### StreamSource

          public StreamSource(java.io.File f)

      Construct a StreamSource from a File.
      Parameters:
      `f` - Must a non-null File reference.

  <!-- -->

  - ### Method Detail

    - #### setInputStream

          public void setInputStream(java.io.InputStream inputStream)

      Set the byte stream to be used as input. Normally, a stream should be used rather than a reader, so that the XML parser can resolve character encoding specified by the XML declaration.
      If this Source object is used to process a stylesheet, normally setSystemId should also be called, so that relative URL references can be resolved.

      Parameters:
      `inputStream` - A valid InputStream reference to an XML stream.

    <!-- -->

    - #### getInputStream

          public java.io.InputStream getInputStream()

      Get the byte stream that was set with setByteStream.
      Returns:
      The byte stream that was set with setByteStream, or null if setByteStream or the ByteStream constructor was not called.

    <!-- -->

    - #### setReader

          public void setReader(java.io.Reader reader)

      Set the input to be a character reader. Normally, a stream should be used rather than a reader, so that the XML parser can resolve character encoding specified by the XML declaration. However, in many cases the encoding of the input stream is already resolved, as in the case of reading XML from a StringReader.
      Parameters:
      `reader` - A valid Reader reference to an XML CharacterStream.

    <!-- -->

    - #### getReader

          public java.io.Reader getReader()

      Get the character stream that was set with setReader.
      Returns:
      The character stream that was set with setReader, or null if setReader or the Reader constructor was not called.

    <!-- -->

    - #### setPublicId

          public void setPublicId(java.lang.String publicId)

      Set the public identifier for this Source.
      The public identifier is always optional: if the application writer includes one, it will be provided as part of the location information.

      Parameters:
      `publicId` - The public identifier as a string.

    <!-- -->

    - #### getPublicId

          public java.lang.String getPublicId()

      Get the public identifier that was set with setPublicId.
      Returns:
      The public identifier that was set with setPublicId, or null if setPublicId was not called.

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.lang.String systemId)

      Set the system identifier for this Source.
      The system identifier is optional if there is a byte stream or a character stream, but it is still useful to provide one, since the application can use it to resolve relative URIs and can include it in error messages and warnings (the parser will attempt to open a connection to the URI only if there is no byte stream or character stream specified).

      Specified by:
      [`setSystemId`](../Source.md) in interface [`Source`](../Source.md)

      Parameters:
      `systemId` - The system identifier as a URL string.

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Get the system identifier that was set with setSystemId.
      Specified by:
      [`getSystemId`](../Source.md) in interface [`Source`](../Source.md)

      Returns:
      The system identifier that was set with setSystemId, or null if setSystemId was not called.

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.io.File f)

      Set the system ID from a File reference.
      Parameters:
      `f` - Must a non-null File reference.

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

- **[Prev Class](StreamResult.md)**
- **Next Class**

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
