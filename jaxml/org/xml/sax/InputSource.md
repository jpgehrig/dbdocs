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

- **[Prev Class](HandlerBase.md)**
- **[Next Class](Locator.md)**

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

## **Class InputSource**

- **java.lang.Object**

- - **org.xml.sax.InputSource**

<!-- -->

- **Direct Known Subclasses:**
  **[XSDInputSource](../../../oracle/xml/parser/schema/XSDInputSource.md)**

  ------------------------------------------------------------------------

  **
  **

      public class InputSource
      extends java.lang.Object

  **A single input source for an XML entity.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class allows a SAX application to encapsulate information about an input source in a single object, which may include a public identifier, a system identifier, a byte stream (possibly with a specified encoding), and/or a character stream.**

  **There are two places that the application will deliver this input source to the parser: as the argument to the Parser.parse method, or as the return value of the EntityResolver.resolveEntity method.**

  **The SAX parser will use the InputSource object to determine how to read XML input. If there is a character stream available, the parser will read that stream directly; if not, the parser will use a byte stream, if available; if neither a character stream nor a byte stream is available, the parser will attempt to open a URI connection to the resource identified by the system identifier.**

  **An InputSource object belongs to the application: the SAX parser shall never modify it in any way (it may modify a copy if necessary).**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`Parser.parse(org.xml.sax.InputSource)`](Parser.md), [`EntityResolver.resolveEntity(java.lang.String, java.lang.String)`](EntityResolver.md), `InputStream`, `Reader`**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                           |
    |-------------------------------------------------------------------------------------------------------|
    | `InputSource``()`<br>Zero-argument default constructor.                                               |
    | `InputSource``(java.io.InputStream byteStream)`<br>Create a new input source with a byte stream.      |
    | `InputSource``(java.io.Reader characterStream)`<br>Create a new input source with a character stream. |
    | `InputSource``(java.lang.String systemId)`<br>Create a new input source with a system identifier.     |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                    |
    |-----------------------|-----------------------------------------------------------------------------------------------------------|
    | `java.io.InputStream` | `getByteStream``()`<br>Get the byte stream for this input source.                                         |
    | `java.io.Reader`      | `getCharacterStream``()`<br>Get the character stream for this input source.                               |
    | `java.lang.String`    | `getEncoding``()`<br>Get the character encoding for a byte stream or URI.                                 |
    | `java.lang.String`    | `getPublicId``()`<br>Get the public identifier for this input source.                                     |
    | `java.lang.String`    | `getSystemId``()`<br>Get the system identifier for this input source.                                     |
    | `void`                | `setByteStream``(java.io.InputStream byteStream)`<br>Set the byte stream for this input source.           |
    | `void`                | `setCharacterStream``(java.io.Reader characterStream)`<br>Set the character stream for this input source. |
    | `void`                | `setEncoding``(java.lang.String encoding)`<br>Set the character encoding, if known.                       |
    | `void`                | `setPublicId``(java.lang.String publicId)`<br>Set the public identifier for this input source.            |
    | `void`                | `setSystemId``(java.lang.String systemId)`<br>Set the system identifier for this input source.            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### InputSource

          public InputSource()

      Zero-argument default constructor.
      See Also:
      `setPublicId(java.lang.String)`, `setSystemId(java.lang.String)`, `setByteStream(java.io.InputStream)`, `setCharacterStream(java.io.Reader)`, `setEncoding(java.lang.String)`

    <!-- -->

    - #### InputSource

          public InputSource(java.lang.String systemId)

      Create a new input source with a system identifier.
      Applications may use setPublicId to include a public identifier as well, or setEncoding to specify the character encoding, if known.

      If the system identifier is a URL, it must be full resolved.

      Parameters:
      `systemId` - The system identifier (URI).

      See Also:
      `setPublicId(java.lang.String)`, `setSystemId(java.lang.String)`, `setByteStream(java.io.InputStream)`, `setEncoding(java.lang.String)`, `setCharacterStream(java.io.Reader)`

    <!-- -->

    - #### InputSource

          public InputSource(java.io.InputStream byteStream)

      Create a new input source with a byte stream.
      Application writers may use setSystemId to provide a base for resolving relative URIs, setPublicId to include a public identifier, and/or setEncoding to specify the object's character encoding.

      Parameters:
      `byteStream` - The raw byte stream containing the document.

      See Also:
      `setPublicId(java.lang.String)`, `setSystemId(java.lang.String)`, `setEncoding(java.lang.String)`, `setByteStream(java.io.InputStream)`, `setCharacterStream(java.io.Reader)`

    <!-- -->

    - #### InputSource

          public InputSource(java.io.Reader characterStream)

      Create a new input source with a character stream.
      Application writers may use setSystemId() to provide a base for resolving relative URIs, and setPublicId to include a public identifier.

      The character stream shall not include a byte order mark.

      See Also:
      `setPublicId(java.lang.String)`, `setSystemId(java.lang.String)`, `setByteStream(java.io.InputStream)`, `setCharacterStream(java.io.Reader)`

  <!-- -->

  - ### Method Detail

    - #### setPublicId

          public void setPublicId(java.lang.String publicId)

      Set the public identifier for this input source.
      The public identifier is always optional: if the application writer includes one, it will be provided as part of the location information.

      Parameters:
      `publicId` - The public identifier as a string.

      See Also:
      `getPublicId()`, [`Locator.getPublicId()`](Locator.md), [`SAXParseException.getPublicId()`](SAXParseException.md)

    <!-- -->

    - #### getPublicId

          public java.lang.String getPublicId()

      Get the public identifier for this input source.
      Returns:
      The public identifier, or null if none was supplied.

      See Also:
      `setPublicId(java.lang.String)`

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.lang.String systemId)

      Set the system identifier for this input source.
      The system identifier is optional if there is a byte stream or a character stream, but it is still useful to provide one, since the application can use it to resolve relative URIs and can include it in error messages and warnings (the parser will attempt to open a connection to the URI only if there is no byte stream or character stream specified).

      If the application knows the character encoding of the object pointed to by the system identifier, it can register the encoding using the setEncoding method.

      If the system ID is a URL, it must be fully resolved.

      Parameters:
      `systemId` - The system identifier as a string.

      See Also:
      `setEncoding(java.lang.String)`, `getSystemId()`, [`Locator.getSystemId()`](Locator.md), [`SAXParseException.getSystemId()`](SAXParseException.md)

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Get the system identifier for this input source.
      The getEncoding method will return the character encoding of the object pointed to, or null if unknown.

      If the system ID is a URL, it will be fully resolved.

      Returns:
      The system identifier, or null if none was supplied.

      See Also:
      `setSystemId(java.lang.String)`, `getEncoding()`

    <!-- -->

    - #### setByteStream

          public void setByteStream(java.io.InputStream byteStream)

      Set the byte stream for this input source.
      The SAX parser will ignore this if there is also a character stream specified, but it will use a byte stream in preference to opening a URI connection itself.

      If the application knows the character encoding of the byte stream, it should set it with the setEncoding method.

      Parameters:
      `byteStream` - A byte stream containing an XML document or other entity.

      See Also:
      `setEncoding(java.lang.String)`, `getByteStream()`, `getEncoding()`, `InputStream`

    <!-- -->

    - #### getByteStream

          public java.io.InputStream getByteStream()

      Get the byte stream for this input source.
      The getEncoding method will return the character encoding for this byte stream, or null if unknown.

      Returns:
      The byte stream, or null if none was supplied.

      See Also:
      `getEncoding()`, `setByteStream(java.io.InputStream)`

    <!-- -->

    - #### setEncoding

          public void setEncoding(java.lang.String encoding)

      Set the character encoding, if known.
      The encoding must be a string acceptable for an XML encoding declaration (see section 4.3.3 of the XML 1.0 recommendation).

      This method has no effect when the application provides a character stream.

      Parameters:
      `encoding` - A string describing the character encoding.

      See Also:
      `setSystemId(java.lang.String)`, `setByteStream(java.io.InputStream)`, `getEncoding()`

    <!-- -->

    - #### getEncoding

          public java.lang.String getEncoding()

      Get the character encoding for a byte stream or URI.
      Returns:
      The encoding, or null if none was supplied.

      See Also:
      `setByteStream(java.io.InputStream)`, `getSystemId()`, `getByteStream()`

    <!-- -->

    - #### setCharacterStream

          public void setCharacterStream(java.io.Reader characterStream)

      Set the character stream for this input source.
      If there is a character stream specified, the SAX parser will ignore any byte stream and will not attempt to open a URI connection to the system identifier.

      Parameters:
      `characterStream` - The character stream containing the XML document or other entity.

      See Also:
      `getCharacterStream()`, `Reader`

    <!-- -->

    - #### getCharacterStream

          public java.io.Reader getCharacterStream()

      Get the character stream for this input source.
      Returns:
      The character stream, or null if none was supplied.

      See Also:
      `setCharacterStream(java.io.Reader)`

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

- **[Prev Class](HandlerBase.md)**
- **[Next Class](Locator.md)**

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
