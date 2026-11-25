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

- [Prev Class](LCSDetectionHTMLReader.md)
- [Next Class](LCSDetectionReader.md)

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

## Class LCSDetectionInputStream

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.io.InputStream](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)

  - - [java.io.FilterInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

    - - oracle.i18n.lcsd.LCSDetectionInputStream

<!-- -->

- All Implemented Interfaces:
  [Closeable](http://docs.oracle.com/javase/8/docs/api/java/io/Closeable.html?is-external=true), [AutoCloseable](http://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true)

  <!-- -->

  Direct Known Subclasses:
  [LCSDetectionHTMLInputStream](LCSDetectionHTMLInputStream.md)

  ------------------------------------------------------------------------



      public class LCSDetectionInputStream
      extends FilterInputStream

  The `LCSDetectionInputStream` class is the language and character detector stream class that transparently detects the language and character set for the stream object.
  The output of `read` methods are the original contents of the input stream in its original state. If the character set conversion using the detected character set is needed, use the [`LCSDetectionReader`](LCSDetectionReader.md) class. If the input stream includes the HTML contents, use the [`LCSDetectionHTMLInputStream`](LCSDetectionHTMLInputStream.md) class or the [`LCSDetectionHTMLReader`](LCSDetectionHTMLReader.md) class. The `LCSDetectionInputStream` class is used to determine the language and character set information used in the content.

  Since:
  10.2

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type      | Field and Description                                                       |
    |------------------------|-----------------------------------------------------------------------------|
    | `protected static int` | `DEFAULT_SAMPLING_SIZE`<br>Default buffer size for the dual stream objects. |

    - ### Fields inherited from class java.io.[FilterInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

      [`in`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#in)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                           |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LCSDetectionInputStream``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in)`<br>Constructs the default LCS Detector input stream object.                                                                                                                                                                                     |
    | `LCSDetectionInputStream``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int size)`<br>Constructs the default LCS Detector input stream object with the sampling length.                                                                                                                                                  |
    | `LCSDetectionInputStream``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` profile, `[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in)`<br>Constructs the LCS Detector input stream object using the specified LCSD profile.                                                     |
    | `LCSDetectionInputStream``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` profile, `[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int size)`<br>Constructs the LCS Detector input stream object using the specified LCSD profile, input stream object, and sampling length. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                |
    |-------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | [`LCSDResultSet`](LCSDResultSet.md) | `getResult``()`<br>Returns the result set of LCSD.                                                                    |
    | `int`                               | `read``()`<br>Reads the next byte of data from the input stream.                                                      |
    | `int`                               | `read``(byte[] b)`<br>Reads some number of bytes from the input stream and stores them into the buffer array `b`.     |
    | `int`                               | `read``(byte[] b, int off, int len)`<br>Reads up to `len` bytes of data from the input stream into an array of bytes. |

    - ### Methods inherited from class java.io.[FilterInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

      [`available`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#available--)`, `[`close`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#close--)`, `[`mark`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#mark-int-)`, `[`markSupported`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#markSupported--)`, `[`reset`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#reset--)`, `[`skip`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#skip-long-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### DEFAULT_SAMPLING_SIZE

          protected static final int DEFAULT_SAMPLING_SIZE

      Default buffer size for the dual stream objects.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### LCSDetectionInputStream

          public LCSDetectionInputStream(InputStream in)
                                  throws IOException,
                                         UTFDataFormatException

      Constructs the default LCS Detector input stream object.
      Parameters:
      `in` - the input stream to be sampled by the detector

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

    <!-- -->

    - #### LCSDetectionInputStream

          public LCSDetectionInputStream(InputStream in,
                                         int size)
                                  throws IOException,
                                         UTFDataFormatException

      Constructs the default LCS Detector input stream object with the sampling length.
      Parameters:
      `in` - the input stream to be sampled by the detector

      `size` - the sampling size

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

    <!-- -->

    - #### LCSDetectionInputStream

          public LCSDetectionInputStream(String profile,
                                         InputStream in)
                                  throws IOException,
                                         UTFDataFormatException

      Constructs the LCS Detector input stream object using the specified LCSD profile.
      Parameters:
      `profile` - the LCSD profile name. Specify `null` for the default profile.

      `in` - the input stream to be sampled by the detector

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

    <!-- -->

    - #### LCSDetectionInputStream

          public LCSDetectionInputStream(String profile,
                                         InputStream in,
                                         int size)
                                  throws IOException,
                                         UTFDataFormatException

      Constructs the LCS Detector input stream object using the specified LCSD profile, input stream object, and sampling length.
      The sampling is performed for the specified length. The detection result does not change until the read operation exceeds the specified length. Each minimum data length will be sampled afterwards.

      Parameters:
      `profile` - the LCSD profile name. Specify `null` for the default profile.

      `in` - the input stream to be sampled by the detector

      `size` - the sampling length

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

  <!-- -->

  - ### Method Detail

    - #### getResult

          public LCSDResultSet getResult()
                                  throws IOException,
                                         EOFException,
                                         UTFDataFormatException

      Returns the result set of LCSD.
      If your application requires information about the language, the character set, or both, call this method.

      Returns:
      The result set of LCSD.

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if an I/O error occurs

      [`EOFException`](http://docs.oracle.com/javase/8/docs/api/java/io/EOFException.html?is-external=true) - if the stream ends unexpectedly

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

    <!-- -->

    - #### read

          public int read()
                   throws IOException,
                          UTFDataFormatException

      Reads the next byte of data from the input stream.
      Overrides:
      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#read--) in class [`FilterInputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

      Returns:
      The next byte of data, or `-1` if the end of the stream is reached.

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if an I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

    <!-- -->

    - #### read

          public int read(byte[] b)
                   throws IOException,
                          UTFDataFormatException

      Reads some number of bytes from the input stream and stores them into the buffer array `b`.
      Overrides:
      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#read-byte:A-) in class [`FilterInputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

      Parameters:
      `b` - the buffer into which the data is read

      Returns:
      The total number of bytes read into the buffer, or `-1` if there is no more data because the end of the stream has been reached.

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if an I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

    <!-- -->

    - #### read

          public int read(byte[] b,
                          int off,
                          int len)
                   throws IOException,
                          UTFDataFormatException

      Reads up to `len` bytes of data from the input stream into an array of bytes.
      Overrides:
      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#read-byte:A-int-int-) in class [`FilterInputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

      Parameters:
      `b` - the buffer into which the data is read

      `off` - the start offset in array `b` to where the data is written

      `len` - the maximum number of bytes to read

      Returns:
      The total number of bytes read into the buffer, or `-1` if there is no more data because the end of the stream has been reached.

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if an I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

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

- [Prev Class](LCSDetectionHTMLReader.md)
- [Next Class](LCSDetectionReader.md)

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
