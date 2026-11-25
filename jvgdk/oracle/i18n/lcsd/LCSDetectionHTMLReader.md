Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](LCSDetectionHTMLInputStream.md)
- [Next Class](LCSDetectionInputStream.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.i18n.lcsd

## Class LCSDetectionHTMLReader

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.io.Reader](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

  - - [oracle.i18n.lcsd.LCSDetectionReader](LCSDetectionReader.md)

    - - oracle.i18n.lcsd.LCSDetectionHTMLReader

<!-- -->

- All Implemented Interfaces:
  [Closeable](http://docs.oracle.com/javase/8/docs/api/java/io/Closeable.html?is-external=true), [AutoCloseable](http://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true), [Readable](http://docs.oracle.com/javase/8/docs/api/java/lang/Readable.html?is-external=true)

  ------------------------------------------------------------------------



      public class LCSDetectionHTMLReader
      extends LCSDetectionReader

  The `LCSDetectionHTMLReader` class extends the [`LCSDetectionReader`](LCSDetectionReader.md) class to support the language/encoding detection for input in HTML format.
  You can choose the character set of the HTML meta value or the detected character set value as the input character set with the flag `METAVAL` or `DETECTVAL`. The default flag value is `DETECTVAL`.

  The detection sampling length indicates how many bytes of plain text on which the detection feature will perform. The default sampling length is 1K. Generally, LCSD handles the language/encoding detection, and you do not need to set this value. By allowing changes to this value, you can control the detection sampling length.

  You can get the detection results from the [`LCSDResultSet`](LCSDResultSet.md) class if needed.

  Any `read` method returns `UTFDataFormatException` if the source is UTF-8 data and an invalid UTF-8 sequence is found.

  Since:
  10.2

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                        |
    |-------------------|--------------------------------------------------------------|
    | `static int`      | `DETECTVAL`<br>Constant value to represent `DETECTVAL` flag. |
    | `static int`      | `METAVAL`<br>Constant value to represent `METAVAL` flag.     |

    - ### Fields inherited from class oracle.i18n.lcsd.[LCSDetectionReader](LCSDetectionReader.md)

      [`DEFAULT_SAMPLING_SIZE`](LCSDetectionReader.md)

    <!-- -->

    - ### Fields inherited from class java.io.[Reader](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      [`lock`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#lock)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                            |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LCSDetectionHTMLReader``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in)`<br>Creates an `LCSDetectionHTMLReader` object.                    |
    | `LCSDetectionHTMLReader``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int len)`<br>Creates an `LCSDetectionHTMLReader` object.           |
    | `LCSDetectionHTMLReader``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int len, int flag)`<br>Creates an `LCSDetectionHTMLReader` object. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.i18n.lcsd.[LCSDetectionReader](LCSDetectionReader.md)

      [`close`](LCSDetectionReader.md)`, `[`getResult`](LCSDetectionReader.md)`, `[`mark`](LCSDetectionReader.md)`, `[`markSupported`](LCSDetectionReader.md)`, `[`read`](LCSDetectionReader.md)`, `[`read`](LCSDetectionReader.md)`, `[`read`](LCSDetectionReader.md)`, `[`ready`](LCSDetectionReader.md)`, `[`reset`](LCSDetectionReader.md)

    <!-- -->

    - ### Methods inherited from class java.io.[Reader](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#read-java.nio.CharBuffer-)`, `[`skip`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#skip-long-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### METAVAL

          public static final int METAVAL

      Constant value to represent `METAVAL` flag.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DETECTVAL

          public static final int DETECTVAL

      Constant value to represent `DETECTVAL` flag.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### LCSDetectionHTMLReader

          public LCSDetectionHTMLReader(InputStream in)
                                 throws IOException,
                                        UTFDataFormatException

      Creates an `LCSDetectionHTMLReader` object. Use the default sampling length and default profile for detection. The detected character set is used for conversion.
      Parameters:
      `in` - input stream that you want to detect

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data

    <!-- -->

    - #### LCSDetectionHTMLReader

          public LCSDetectionHTMLReader(InputStream in,
                                        int len)
                                 throws IOException,
                                        UTFDataFormatException

      Creates an `LCSDetectionHTMLReader` object. Use the specified sampling length and default profile for detection. The detected character set is used for conversion.
      Parameters:
      `in` - input stream that you want to detect

      `len` - the sampling length

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data

    <!-- -->

    - #### LCSDetectionHTMLReader

          public LCSDetectionHTMLReader(InputStream in,
                                        int len,
                                        int flag)
                                 throws IOException,
                                        UTFDataFormatException

      Creates an `LCSDetectionHTMLReader` object. Use the specified sampling length and default profile for detection. The detected character set is used for conversion if the flag is `DETECTVAL` or the meta value of the character set is used for conversion if the flag is `METAVAL`.
      Parameters:
      `in` - input stream that you want to detect

      `len` - the sampling length

      `flag` - `METAVAL` or `DETECTVAL`

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](LCSDetectionHTMLInputStream.md)
- [Next Class](LCSDetectionInputStream.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
