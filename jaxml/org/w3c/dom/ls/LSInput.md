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

- **[Prev Class](DOMImplementationLS.md)**
- **[Next Class](LSLoadEvent.md)**

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

**org.w3c.dom.ls**

## **Interface LSInput**

-

  ------------------------------------------------------------------------

  **
  **

      public interface LSInput

  **This interface represents an input source for data.**
  **This interface allows an application to encapsulate information about an input source in a single object, which may include a public identifier, a system identifier, a byte stream (possibly with a specified encoding), a base URI, and/or a character stream.**

  **The exact definitions of a byte stream and a character stream are binding dependent.**

  **The application is expected to provide objects that implement this interface whenever such objects are needed. The application can either provide its own objects that implement this interface, or it can use the generic factory method `DOMImplementationLS.createLSInput()` to create objects that implement this interface.**

  **The `LSParser` will use the `LSInput` object to determine how to read data. The `LSParser` will look at the different inputs specified in the `LSInput` in the following order to know which one to read from, the first one that is not null and not an empty string will be used:**

  1.  **`LSInput.characterStream`**
  2.  **`LSInput.byteStream`**
  3.  **`LSInput.stringData`**
  4.  **`LSInput.systemId`**
  5.  **`LSInput.publicId`**

  **`LSInput` objects belong to the application. The DOM implementation will never modify them (though it may make copies and modify the copies, if necessary).**

  **See also the [Document Object Model (DOM) Level 3 Load and Save Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107).**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                                                                                        |
    |-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`    | `getBaseURI``()`<br>The base URI to be used (see section 5.1.4 in \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\]) for resolving a relative `systemId` to an absolute URI.                                                                           |
    | `java.io.InputStream` | `getByteStream``()`<br>An attribute of a language and binding dependent type that represents a stream of bytes.                                                                                                                                               |
    | `boolean`             | `getCertifiedText``()`<br>If set to true, assume that the input is certified (see section 2.13 in \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\]) when parsing \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\].                      |
    | `java.io.Reader`      | `getCharacterStream``()`<br>An attribute of a language and binding dependent type that represents a stream of 16-bit units.                                                                                                                                   |
    | `java.lang.String`    | `getEncoding``()`<br>The character encoding, if known.                                                                                                                                                                                                        |
    | `java.lang.String`    | `getPublicId``()`<br>The public identifier for this input source.                                                                                                                                                                                             |
    | `java.lang.String`    | `getStringData``()`<br>String data to parse.                                                                                                                                                                                                                  |
    | `java.lang.String`    | `getSystemId``()`<br>The system identifier, a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\], for this input source.                                                                                                                  |
    | `void`                | `setBaseURI``(java.lang.String baseURI)`<br>The base URI to be used (see section 5.1.4 in \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\]) for resolving a relative `systemId` to an absolute URI.                                                   |
    | `void`                | `setByteStream``(java.io.InputStream byteStream)`<br>An attribute of a language and binding dependent type that represents a stream of bytes.                                                                                                                 |
    | `void`                | `setCertifiedText``(boolean certifiedText)`<br>If set to true, assume that the input is certified (see section 2.13 in \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\]) when parsing \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\]. |
    | `void`                | `setCharacterStream``(java.io.Reader characterStream)`<br>An attribute of a language and binding dependent type that represents a stream of 16-bit units.                                                                                                     |
    | `void`                | `setEncoding``(java.lang.String encoding)`<br>The character encoding, if known.                                                                                                                                                                               |
    | `void`                | `setPublicId``(java.lang.String publicId)`<br>The public identifier for this input source.                                                                                                                                                                    |
    | `void`                | `setStringData``(java.lang.String stringData)`<br>String data to parse.                                                                                                                                                                                       |
    | `void`                | `setSystemId``(java.lang.String systemId)`<br>The system identifier, a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\], for this input source.                                                                                         |

<!-- -->

- - ### Method Detail

    - #### getCharacterStream

          java.io.Reader getCharacterStream()

      An attribute of a language and binding dependent type that represents a stream of 16-bit units. The application must encode the stream using UTF-16 (defined in \[Unicode\] and in \[ISO/IEC 10646\]).

    <!-- -->

    - #### setCharacterStream

          void setCharacterStream(java.io.Reader characterStream)

      An attribute of a language and binding dependent type that represents a stream of 16-bit units. The application must encode the stream using UTF-16 (defined in \[Unicode\] and in \[ISO/IEC 10646\]).

    <!-- -->

    - #### getByteStream

          java.io.InputStream getByteStream()

      An attribute of a language and binding dependent type that represents a stream of bytes.
      If the application knows the character encoding of the byte stream, it should set the encoding attribute. Setting the encoding in this way will override any encoding specified in an XML declaration in the data.

    <!-- -->

    - #### setByteStream

          void setByteStream(java.io.InputStream byteStream)

      An attribute of a language and binding dependent type that represents a stream of bytes.
      If the application knows the character encoding of the byte stream, it should set the encoding attribute. Setting the encoding in this way will override any encoding specified in an XML declaration in the data.

    <!-- -->

    - #### getStringData

          java.lang.String getStringData()

      String data to parse. If provided, this will always be treated as a sequence of 16-bit units (UTF-16 encoded characters).

    <!-- -->

    - #### setStringData

          void setStringData(java.lang.String stringData)

      String data to parse. If provided, this will always be treated as a sequence of 16-bit units (UTF-16 encoded characters).

    <!-- -->

    - #### getSystemId

          java.lang.String getSystemId()

      The system identifier, a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\], for this input source. The system identifier is optional if there is a byte stream, a character stream, or string data, but it is still useful to provide one, since the application will use it to resolve any relative URIs and can include it in error messages and warnings (the `LSParser` will only attempt to fetch the resource identified by the URI reference only if there is no other input available in the input source).
      If the application knows the character encoding of the object pointed to by the system identifier, it can set the encoding using the `encoding` attribute.
      If the system ID is a relative URI reference (see section 5 in \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\]), the DOM implementation will attempt to resolve the relative URI with the `baseURI` as the base, if that fails, the behavior is implementation dependent.

    <!-- -->

    - #### setSystemId

          void setSystemId(java.lang.String systemId)

      The system identifier, a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\], for this input source. The system identifier is optional if there is a byte stream, a character stream, or string data, but it is still useful to provide one, since the application will use it to resolve any relative URIs and can include it in error messages and warnings (the `LSParser` will only attempt to fetch the resource identified by the URI reference only if there is no other input available in the input source).
      If the application knows the character encoding of the object pointed to by the system identifier, it can set the encoding using the `encoding` attribute.
      If the system ID is a relative URI reference (see section 5 in \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\]), the DOM implementation will attempt to resolve the relative URI with the `baseURI` as the base, if that fails, the behavior is implementation dependent.

    <!-- -->

    - #### getPublicId

          java.lang.String getPublicId()

      The public identifier for this input source. This may be mapped to an input source using an implementation dependent mechanism (such as catalogues or other mappings). The public identifier, if specified, may also be reported as part of the location information when errors are reported.

    <!-- -->

    - #### setPublicId

          void setPublicId(java.lang.String publicId)

      The public identifier for this input source. This may be mapped to an input source using an implementation dependent mechanism (such as catalogues or other mappings). The public identifier, if specified, may also be reported as part of the location information when errors are reported.

    <!-- -->

    - #### getBaseURI

          java.lang.String getBaseURI()

      The base URI to be used (see section 5.1.4 in \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\]) for resolving a relative `systemId` to an absolute URI.
      If, when used, the base URI is itself a relative URI, an empty string, or null, the behavior is implementation dependent.

    <!-- -->

    - #### setBaseURI

          void setBaseURI(java.lang.String baseURI)

      The base URI to be used (see section 5.1.4 in \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\]) for resolving a relative `systemId` to an absolute URI.
      If, when used, the base URI is itself a relative URI, an empty string, or null, the behavior is implementation dependent.

    <!-- -->

    - #### getEncoding

          java.lang.String getEncoding()

      The character encoding, if known. The encoding must be a string acceptable for an XML encoding declaration (\[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\] section 4.3.3 "Character Encoding in Entities").
      This attribute has no effect when the application provides a character stream or string data. For other sources of input, an encoding specified by means of this attribute will override any encoding specified in the XML declaration or the Text declaration, or an encoding obtained from a higher level protocol, such as HTTP \[[IETF RFC 2616](http://www.ietf.org/rfc/rfc2616.txt)\].

    <!-- -->

    - #### setEncoding

          void setEncoding(java.lang.String encoding)

      The character encoding, if known. The encoding must be a string acceptable for an XML encoding declaration (\[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\] section 4.3.3 "Character Encoding in Entities").
      This attribute has no effect when the application provides a character stream or string data. For other sources of input, an encoding specified by means of this attribute will override any encoding specified in the XML declaration or the Text declaration, or an encoding obtained from a higher level protocol, such as HTTP \[[IETF RFC 2616](http://www.ietf.org/rfc/rfc2616.txt)\].

    <!-- -->

    - #### getCertifiedText

          boolean getCertifiedText()

      If set to true, assume that the input is certified (see section 2.13 in \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\]) when parsing \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\].

    <!-- -->

    - #### setCertifiedText

          void setCertifiedText(boolean certifiedText)

      If set to true, assume that the input is certified (see section 2.13 in \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\]) when parsing \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\].

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

- **[Prev Class](DOMImplementationLS.md)**
- **[Next Class](LSLoadEvent.md)**

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

**[Copyright](http://www.w3.org/Consortium/Legal/ipr-notice#Copyright) ©2004 [W3C](http://www.w3.org/)® ([MIT](http://www.csail.mit.edu/), [ERCIM](http://www.ercim.org/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [trademark](http://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks), [document use](http://www.w3.org/Consortium/Legal/copyright-documents) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software) rules apply. The latest version is at <http://www.w3.org/TR/DOM-Level-3-LS>.**
