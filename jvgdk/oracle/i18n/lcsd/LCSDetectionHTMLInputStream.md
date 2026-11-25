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

- Prev Class
- [Next Class](LCSDetectionHTMLReader.md)

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

## Class LCSDetectionHTMLInputStream

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.io.InputStream](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)

  - - [java.io.FilterInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

    - - [oracle.i18n.lcsd.LCSDetectionInputStream](LCSDetectionInputStream.md)

      - - oracle.i18n.lcsd.LCSDetectionHTMLInputStream

<!-- -->

- All Implemented Interfaces:
  [Closeable](http://docs.oracle.com/javase/8/docs/api/java/io/Closeable.html?is-external=true), [AutoCloseable](http://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true)

  ------------------------------------------------------------------------



      public class LCSDetectionHTMLInputStream
      extends LCSDetectionInputStream

  The `LCSDetectionHTMLInputStream` class extends the [`LCSDetectionInputStream`](LCSDetectionInputStream.md) class to support the language/encoding detection for input in HTML format.
  The detection sampling length indicates how many bytes of plain text on which the detection feature will perform. The default sampling length is 1K. Generally, LCSD handles the language/encoding detection, and you do not need to set this value. By allowing changes to this value, you can control the detection sampling length.

  You can get the detection results from the [`LCSDResultSet`](LCSDResultSet.md) class if needed.

  Any `read` method returns `UTFDataFormatException` if the source is UTF-8 data and an invalid UTF-8 sequence is found.

  Since:
  10.2

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.i18n.lcsd.[LCSDetectionInputStream](LCSDetectionInputStream.md)

      [`DEFAULT_SAMPLING_SIZE`](LCSDetectionInputStream.md)

    <!-- -->

    - ### Fields inherited from class java.io.[FilterInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

      [`in`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#in)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LCSDetectionHTMLInputStream``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in)`<br>Creates an `LCSDetectionHTMLInputStream` object.                                                                                                                                                                                |
    | `LCSDetectionHTMLInputStream``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int len)`<br>Creates an `LCSDetectionStream` object with the specified sampling length.                                                                                                                                             |
    | `LCSDetectionHTMLInputStream``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in)`<br>Creates an `LCSDetectionStream` object with the specified profile for detection.                                            |
    | `LCSDetectionHTMLInputStream``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int len)`<br>Creates an `LCSDetectionStream` object with the specified sampling length and the specified profile for detection. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.i18n.lcsd.[LCSDetectionInputStream](LCSDetectionInputStream.md)

      [`getResult`](LCSDetectionInputStream.md)`, `[`read`](LCSDetectionInputStream.md)`, `[`read`](LCSDetectionInputStream.md)`, `[`read`](LCSDetectionInputStream.md)

    <!-- -->

    - ### Methods inherited from class java.io.[FilterInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

      [`available`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#available--)`, `[`close`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#close--)`, `[`mark`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#mark-int-)`, `[`markSupported`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#markSupported--)`, `[`reset`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#reset--)`, `[`skip`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#skip-long-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Constructor Detail

    - #### LCSDetectionHTMLInputStream

          public LCSDetectionHTMLInputStream(InputStream in)
                                      throws IOException,
                                             UTFDataFormatException

      Creates an `LCSDetectionHTMLInputStream` object. Use the default sampling length and default profile for detection.
      Parameters:
      `in` - input stream that you want to detect

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data

    <!-- -->

    - #### LCSDetectionHTMLInputStream

          public LCSDetectionHTMLInputStream(String name,
                                             InputStream in)
                                      throws IOException,
                                             UTFDataFormatException

      Creates an `LCSDetectionStream` object with the specified profile for detection. Use the default sampling length.
      Parameters:
      `name` - the profile name

      `in` - input stream that you want to detect

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data

    <!-- -->

    - #### LCSDetectionHTMLInputStream

          public LCSDetectionHTMLInputStream(InputStream in,
                                             int len)
                                      throws IOException,
                                             UTFDataFormatException

      Creates an `LCSDetectionStream` object with the specified sampling length. Use the default profile for detection.
      Parameters:
      `in` - input stream that you want to detect

      `len` - the sampling length

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data

    <!-- -->

    - #### LCSDetectionHTMLInputStream

          public LCSDetectionHTMLInputStream(String name,
                                             InputStream in,
                                             int len)
                                      throws IOException,
                                             UTFDataFormatException

      Creates an `LCSDetectionStream` object with the specified sampling length and the specified profile for detection.
      Parameters:
      `name` - the profile name

      `in` - input stream that you want to detect

      `len` - the sampling length

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

- Prev Class
- [Next Class](LCSDetectionHTMLReader.md)

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
