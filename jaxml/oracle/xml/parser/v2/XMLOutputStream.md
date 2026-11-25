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

- **[Prev Class](XMLObjectInputStream.md)**
- **[Next Class](XMLParseException.md)**

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

## **Class XMLOutputStream**

- **java.lang.Object**

- - **oracle.xml.parser.v2.XMLOutputStream**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XMLOutputStream
      extends java.lang.Object

  **XMLOutputSteam -- writes output stream, can handle XML encoding It writes either to a character stream (e.g., java.io.Writer), or to a byte stream (e.g., java.io.OutputStream). If the caller uses a character stream, then the encoding is irrelevant and will be ignored, because the output already consists of characters, not bytes. So the XML encoding applies only to the case of a byte stream.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `COMPACT`             |
    | `static int`      | `DEFAULT`             |
    | `static int`      | `NO_REUSE`            |
    | `static int`      | `PRETTY`              |
    | `static int`      | `REUSE`               |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                   |
    |-------------------------------------------------------------------------------------------------------------------------------|
    | `XMLOutputStream``(java.io.OutputStream outs)`<br>Builds the ASCII output stream (as a byte stream)                           |
    | `XMLOutputStream``(java.io.Writer outw)`<br>Builds the output stream from a Writer (also PrintWriter) (as a character stream) |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                         |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `addIndent``(int offset)`<br>Set indenting level for output                                                                                    |
    | `void`            | `close``()`<br>Closes the output stream.                                                                                                       |
    | `void`            | `close``(int option)`<br>Closes the output stream based on the option.                                                                         |
    | `void`            | `flush``()`<br>Flushes the internal buffer by writing it to the output stream                                                                  |
    | `int`             | `getOutputStyle``()`<br>Gets the Current output style                                                                                          |
    | `void`            | `setEncoding``(java.lang.String encoding, boolean lendian, boolean useByteOrderMark)`<br>Sets the output character encoding for a byte stream. |
    | `void`            | `setEOLChars``(java.lang.String nl)`<br>Set newline characters                                                                                 |
    | `void`            | `setOutputStyle``(int style)`<br>Sets the Output the style                                                                                     |
    | `void`            | `write``(int c)`<br>Outputs character according to type of the output stream                                                                   |
    | `void`            | `writeChars``(java.lang.String str)`<br>Write string to the output                                                                             |
    | `void`            | `writeIndent``()`<br>Output the indentation                                                                                                    |
    | `void`            | `writeNewLine``()`<br>Newline writer                                                                                                           |
    | `void`            | `writeQuotedString``(java.lang.String str)`<br>Write string with surrounding quotes                                                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DEFAULT

          public static final int DEFAULT

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### PRETTY

          public static final int PRETTY

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPACT

          public static final int COMPACT

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### REUSE

          public static final int REUSE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NO_REUSE

          public static final int NO_REUSE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XMLOutputStream

          public XMLOutputStream(java.io.OutputStream outs)

      Builds the ASCII output stream (as a byte stream)
      Parameters:
      `outs` - - the output stream

    <!-- -->

    - #### XMLOutputStream

          public XMLOutputStream(java.io.Writer outw)

      Builds the output stream from a Writer (also PrintWriter) (as a character stream)
      Parameters:
      `outw` - - the Writer stream

  <!-- -->

  - ### Method Detail

    - #### setEOLChars

          public void setEOLChars(java.lang.String nl)

      Set newline characters

    <!-- -->

    - #### setEncoding

          public void setEncoding(java.lang.String encoding,
                                  boolean lendian,
                                  boolean useByteOrderMark)
                           throws java.io.IOException

      Sets the output character encoding for a byte stream. This only applies to a byte stream, not to a character stream. If called for a character stream, then this is a no-op.
      Parameters:
      `encoding` - the encoding of the (byte) stream

      `lendian` - flag to indicate if the encoding is of type little endian

      `useByteOrderMark` - flag for whether to write the byte order mark

      Throws:
      `java.io.IOException` - if an error is thrown in setting the encoding type

    <!-- -->

    - #### flush

          public void flush()
                     throws java.io.IOException

      Flushes the internal buffer by writing it to the output stream
      Throws:
      `java.io.IOException` - if there is any error in flushing the output stream

    <!-- -->

    - #### close

          public void close()
                     throws java.io.IOException

      Closes the output stream. Migrate to close(int option).
      Throws:
      `java.io.IOException` - if there is any error in closing the output stream

    <!-- -->

    - #### close

          public void close(int option)
                     throws java.io.IOException

      Closes the output stream based on the option. Legal values are: REUSE and NO_REUSE.
      Parameters:
      `option` - determines whether output stream has to be closed.

      Throws:
      `java.io.IOException` - if there is any error in closing the output stream.

    <!-- -->

    - #### write

          public void write(int c)
                     throws java.io.IOException

      Outputs character according to type of the output stream
      Parameters:
      `c` - the character that needs to be written. Note that c can be either a standard Unicode code point (i.e., using UTF-32 encoding); or it may be just one member of a surrogate pair, either a high surrogate or a low surrogate. I.e., for supplementary characters, which use surrogate pairs in UTF-16, we may have to call write() twice in order to write one logical character.

      Throws:
      `java.io.IOException` - if there is any error in writing the character

    <!-- -->

    - #### writeChars

          public void writeChars(java.lang.String str)
                          throws java.io.IOException

      Write string to the output
      Parameters:
      `str` - the string that is written to the output stream

      Throws:
      `java.io.IOException` - error thrown if there is any error in writing the string

    <!-- -->

    - #### writeQuotedString

          public void writeQuotedString(java.lang.String str)
                                 throws java.io.IOException

      Write string with surrounding quotes
      Parameters:
      `str` - the string that is written to the output stream

      Throws:
      `java.io.IOException` - error thrown if there is any error in writing the string

    <!-- -->

    - #### writeNewLine

          public void writeNewLine()
                            throws java.io.IOException

      Newline writer
      Throws:
      `java.io.IOException` - error thrown if there is any error in writing the string

    <!-- -->

    - #### addIndent

          public void addIndent(int offset)

      Set indenting level for output
      Parameters:
      `offset` - the indenting level

    <!-- -->

    - #### writeIndent

          public void writeIndent()
                           throws java.io.IOException

      Output the indentation
      Throws:
      `java.io.IOException` - error thrown if there is any error in writing the string

    <!-- -->

    - #### setOutputStyle

          public void setOutputStyle(int style)

      Sets the Output the style
      Parameters:
      `style` - the output style

    <!-- -->

    - #### getOutputStyle

          public int getOutputStyle()

      Gets the Current output style
      Returns:
      the output style

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

- **[Prev Class](XMLObjectInputStream.md)**
- **[Next Class](XMLParseException.md)**

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
