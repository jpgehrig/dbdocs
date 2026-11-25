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

- **[Prev Class](LSLoadEvent.md)**
- **[Next Class](LSParser.md)**

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

## **Interface LSOutput**

-

  ------------------------------------------------------------------------

  **
  **

      public interface LSOutput

  **This interface represents an output destination for data.**
  **This interface allows an application to encapsulate information about an output destination in a single object, which may include a URI, a byte stream (possibly with a specified encoding), a base URI, and/or a character stream.**

  **The exact definitions of a byte stream and a character stream are binding dependent.**

  **The application is expected to provide objects that implement this interface whenever such objects are needed. The application can either provide its own objects that implement this interface, or it can use the generic factory method `DOMImplementationLS.createLSOutput()` to create objects that implement this interface.**

  **The `LSSerializer` will use the `LSOutput` object to determine where to serialize the output to. The `LSSerializer` will look at the different outputs specified in the `LSOutput` in the following order to know which one to output to, the first one that is not null and not an empty string will be used:**

  1.  **`LSOutput.characterStream`**
  2.  **`LSOutput.byteStream`**
  3.  **`LSOutput.systemId`**

  **`LSOutput` objects belong to the application. The DOM implementation will never modify them (though it may make copies and modify the copies, if necessary).**

  **See also the [Document Object Model (DOM) Level 3 Load and Save Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107).**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type      | Method and Description                                                                                                                                                                 |
    |------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.io.OutputStream` | `getByteStream``()`<br>An attribute of a language and binding dependent type that represents a writable stream of bytes.                                                               |
    | `java.io.Writer`       | `getCharacterStream``()`<br>An attribute of a language and binding dependent type that represents a writable stream to which 16-bit units can be output.                               |
    | `java.lang.String`     | `getEncoding``()`<br>The character encoding to use for the output.                                                                                                                     |
    | `java.lang.String`     | `getSystemId``()`<br>The system identifier, a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\], for this output destination.                                     |
    | `void`                 | `setByteStream``(java.io.OutputStream byteStream)`<br>An attribute of a language and binding dependent type that represents a writable stream of bytes.                                |
    | `void`                 | `setCharacterStream``(java.io.Writer characterStream)`<br>An attribute of a language and binding dependent type that represents a writable stream to which 16-bit units can be output. |
    | `void`                 | `setEncoding``(java.lang.String encoding)`<br>The character encoding to use for the output.                                                                                            |
    | `void`                 | `setSystemId``(java.lang.String systemId)`<br>The system identifier, a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\], for this output destination.            |

<!-- -->

- - ### Method Detail

    - #### getCharacterStream

          java.io.Writer getCharacterStream()

      An attribute of a language and binding dependent type that represents a writable stream to which 16-bit units can be output.

    <!-- -->

    - #### setCharacterStream

          void setCharacterStream(java.io.Writer characterStream)

      An attribute of a language and binding dependent type that represents a writable stream to which 16-bit units can be output.

    <!-- -->

    - #### getByteStream

          java.io.OutputStream getByteStream()

      An attribute of a language and binding dependent type that represents a writable stream of bytes.

    <!-- -->

    - #### setByteStream

          void setByteStream(java.io.OutputStream byteStream)

      An attribute of a language and binding dependent type that represents a writable stream of bytes.

    <!-- -->

    - #### getSystemId

          java.lang.String getSystemId()

      The system identifier, a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\], for this output destination.
      If the system ID is a relative URI reference (see section 5 in \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\]), the behavior is implementation dependent.

    <!-- -->

    - #### setSystemId

          void setSystemId(java.lang.String systemId)

      The system identifier, a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\], for this output destination.
      If the system ID is a relative URI reference (see section 5 in \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\]), the behavior is implementation dependent.

    <!-- -->

    - #### getEncoding

          java.lang.String getEncoding()

      The character encoding to use for the output. The encoding must be a string acceptable for an XML encoding declaration (\[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\] section 4.3.3 "Character Encoding in Entities"), it is recommended that character encodings registered (as charsets) with the Internet Assigned Numbers Authority \[IANA-CHARSETS\] should be referred to using their registered names.
      This attribute has no effect when outputting to a character stream.

    <!-- -->

    - #### setEncoding

          void setEncoding(java.lang.String encoding)

      The character encoding to use for the output. The encoding must be a string acceptable for an XML encoding declaration (\[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\] section 4.3.3 "Character Encoding in Entities"), it is recommended that character encodings registered (as charsets) with the Internet Assigned Numbers Authority \[IANA-CHARSETS\] should be referred to using their registered names.
      This attribute has no effect when outputting to a character stream.

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

- **[Prev Class](LSLoadEvent.md)**
- **[Next Class](LSParser.md)**

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
