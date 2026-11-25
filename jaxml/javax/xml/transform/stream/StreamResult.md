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

- **Prev Class**
- **[Next Class](StreamSource.md)**

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

## **Class StreamResult**

- **java.lang.Object**

- - **javax.xml.transform.stream.StreamResult**

<!-- -->

- **All Implemented Interfaces:**
  **[Result](../Result.md)**

  ------------------------------------------------------------------------

  **
  **

      public class StreamResult
      extends java.lang.Object
      implements Result

  **Acts as an holder for a transformation result, which may be XML, plain Text, HTML, or some other form of markup.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                                  |
    |---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `FEATURE`<br>If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the Transformer supports Result output of this type. |

    -

      ### **Fields inherited from interface javax.xml.transform.[Result](../Result.md)**

      **[`PI_DISABLE_OUTPUT_ESCAPING`](../Result.md)`, `[`PI_ENABLE_OUTPUT_ESCAPING`](../Result.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                         |
    |-----------------------------------------------------------------------------------------------------|
    | `StreamResult``()`<br>Zero-argument default constructor.                                            |
    | `StreamResult``(java.io.File f)`<br>Construct a StreamResult from a File.                           |
    | `StreamResult``(java.io.OutputStream outputStream)`<br>Construct a StreamResult from a byte stream. |
    | `StreamResult``(java.lang.String systemId)`<br>Construct a StreamResult from a URL.                 |
    | `StreamResult``(java.io.Writer writer)`<br>Construct a StreamResult from a character stream.        |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type      | Method and Description                                                                                                                                                                                             |
    |------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.io.OutputStream` | `getOutputStream``()`<br>Get the byte stream that was set with setOutputStream.                                                                                                                                    |
    | `java.lang.String`     | `getSystemId``()`<br>Get the system identifier that was set with setSystemId.                                                                                                                                      |
    | `java.io.Writer`       | `getWriter``()`<br>Get the character stream that was set with setWriter.                                                                                                                                           |
    | `void`                 | `setOutputStream``(java.io.OutputStream outputStream)`<br>Set the ByteStream that is to be written to.                                                                                                             |
    | `void`                 | `setSystemId``(java.io.File f)`<br>Set the system ID from a File reference.                                                                                                                                        |
    | `void`                 | `setSystemId``(java.lang.String systemId)`<br>Set the systemID that may be used in association with the byte or character stream, or, if neither is set, use this value as a writeable URI (probably a file name). |
    | `void`                 | `setWriter``(java.io.Writer writer)`<br>Set the writer that is to receive the result.                                                                                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### FEATURE

          public static final java.lang.String FEATURE

      If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the Transformer supports Result output of this type.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### StreamResult

          public StreamResult()

      Zero-argument default constructor.

    <!-- -->

    - #### StreamResult

          public StreamResult(java.io.OutputStream outputStream)

      Construct a StreamResult from a byte stream. Normally, a stream should be used rather than a reader, so that the transformer may use instructions contained in the transformation instructions to control the encoding.
      Parameters:
      `outputStream` - A valid OutputStream reference.

    <!-- -->

    - #### StreamResult

          public StreamResult(java.io.Writer writer)

      Construct a StreamResult from a character stream. Normally, a stream should be used rather than a reader, so that the transformer may use instructions contained in the transformation instructions to control the encoding. However, there are times when it is useful to write to a character stream, such as when using a StringWriter.
      Parameters:
      `writer` - A valid Writer reference.

    <!-- -->

    - #### StreamResult

          public StreamResult(java.lang.String systemId)

      Construct a StreamResult from a URL.
      Parameters:
      `systemId` - Must be a String that conforms to the URI syntax.

    <!-- -->

    - #### StreamResult

          public StreamResult(java.io.File f)

      Construct a StreamResult from a File.
      Parameters:
      `f` - Must a non-null File reference.

  <!-- -->

  - ### Method Detail

    - #### setOutputStream

          public void setOutputStream(java.io.OutputStream outputStream)

      Set the ByteStream that is to be written to. Normally, a stream should be used rather than a reader, so that the transformer may use instructions contained in the transformation instructions to control the encoding.
      Parameters:
      `outputStream` - A valid OutputStream reference.

    <!-- -->

    - #### getOutputStream

          public java.io.OutputStream getOutputStream()

      Get the byte stream that was set with setOutputStream.
      Returns:
      The byte stream that was set with setOutputStream, or null if setOutputStream or the ByteStream constructor was not called.

    <!-- -->

    - #### setWriter

          public void setWriter(java.io.Writer writer)

      Set the writer that is to receive the result. Normally, a stream should be used rather than a writer, so that the transformer may use instructions contained in the transformation instructions to control the encoding. However, there are times when it is useful to write to a writer, such as when using a StringWriter.
      Parameters:
      `writer` - A valid Writer reference.

    <!-- -->

    - #### getWriter

          public java.io.Writer getWriter()

      Get the character stream that was set with setWriter.
      Returns:
      The character stream that was set with setWriter, or null if setWriter or the Writer constructor was not called.

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.lang.String systemId)

      Set the systemID that may be used in association with the byte or character stream, or, if neither is set, use this value as a writeable URI (probably a file name).
      Specified by:
      [`setSystemId`](../Result.md) in interface [`Result`](../Result.md)

      Parameters:
      `systemId` - The system identifier as a URI string.

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.io.File f)

      Set the system ID from a File reference.
      Parameters:
      `f` - Must a non-null File reference.

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Get the system identifier that was set with setSystemId.
      Specified by:
      [`getSystemId`](../Result.md) in interface [`Result`](../Result.md)

      Returns:
      The system identifier that was set with setSystemId, or null if setSystemId was not called.

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

- **Prev Class**
- **[Next Class](StreamSource.md)**

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
