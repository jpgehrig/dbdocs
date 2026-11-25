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

- [Prev Class](LCSDetectionInputStream.md)
- [Next Class](LCSDetector.md)

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

## Class LCSDetectionReader

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.io.Reader](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

  - - oracle.i18n.lcsd.LCSDetectionReader

<!-- -->

- All Implemented Interfaces:
  [Closeable](http://docs.oracle.com/javase/8/docs/api/java/io/Closeable.html?is-external=true), [AutoCloseable](http://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true), [Readable](http://docs.oracle.com/javase/8/docs/api/java/lang/Readable.html?is-external=true)

  <!-- -->

  Direct Known Subclasses:
  [LCSDetectionHTMLReader](LCSDetectionHTMLReader.md)

  ------------------------------------------------------------------------



      public class LCSDetectionReader
      extends Reader

  The `LCSDetectionReader` class is the language and character detector (LCSD) reader class that transparently detects the character set and converts it to the Unicode data.
  The most common usage is for the `Reader` interface to read the text data as follows:

       InputStream in = file.getInputStream();
       Reader rdr = new LCSDetectionReader(in);
       char[] cbuf = new char[1024];
       for (int len = -1; (len = rdr.read(cbuf)) != -1;)
       {
         // do something with cbuf
         ...
       }


  The detection occurs only once by sampling the first chunk of data.
  Since:
  10.2

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type      | Field and Description                                                                             |
    |------------------------|---------------------------------------------------------------------------------------------------|
    | `protected static int` | `DEFAULT_SAMPLING_SIZE`<br>Default sampling byte length for language and character set detection. |

    - ### Fields inherited from class java.io.[Reader](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      [`lock`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#lock)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                          |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LCSDetectionReader``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in)`<br>Constructs the LCSD Reader instance with the character set determined by sampling initial data.                                                                                                                  |
    | `LCSDetectionReader``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int size)`<br>Constructs the LCSD Reader instance with the character set determined by sampling initial data.                                                                                                        |
    | `LCSDetectionReader``(`[`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader)`<br>Constructs the LCSD Reader instance over the input stream reader.                                                                                                                                                      |
    | `LCSDetectionReader``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` profile, `[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in)`<br>Constructs the LCSD Reader instance with the character set determined by sampling initial data.           |
    | `LCSDetectionReader``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` profile, `[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int size)`<br>Constructs the LCSD Reader instance with the character set determined by sampling initial data. |
    | `LCSDetectionReader``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` profile, `[`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader)`<br>Constructs the LCSD Reader instance over the reader.                                                            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                        |
    |-------------------------------------|-----------------------------------------------------------------------------------------------|
    | `void`                              | `close``()`<br>Closes the stream.                                                             |
    | [`LCSDResultSet`](LCSDResultSet.md) | `getResult``()`<br>Returns the result set of LCSD.                                            |
    | `void`                              | `mark``(int readAheadLimit)`<br>Marks the present position in the stream.                     |
    | `boolean`                           | `markSupported``()`<br>Tells whether this stream supports the `mark()` operation.             |
    | `int`                               | `read``()`<br>Reads a single character.                                                       |
    | `int`                               | `read``(char[] cbuf)`<br>Reads characters into an array.                                      |
    | `int`                               | `read``(char[] cbuf, int offset, int length)`<br>Reads characters into a portion of an array. |
    | `boolean`                           | `ready``()`<br>Tells whether this stream is ready to be read.                                 |
    | `void`                              | `reset``()`<br>Resets the stream.                                                             |

    - ### Methods inherited from class java.io.[Reader](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#read-java.nio.CharBuffer-)`, `[`skip`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#skip-long-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### DEFAULT_SAMPLING_SIZE

          protected static final int DEFAULT_SAMPLING_SIZE

      Default sampling byte length for language and character set detection.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### LCSDetectionReader

          public LCSDetectionReader(InputStream in)
                             throws IOException,
                                    UTFDataFormatException

      Constructs the LCSD Reader instance with the character set determined by sampling initial data.
      Parameters:
      `in` - the `InputStream` object including the text data

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

    <!-- -->

    - #### LCSDetectionReader

          public LCSDetectionReader(InputStream in,
                                    int size)
                             throws IOException,
                                    UTFDataFormatException

      Constructs the LCSD Reader instance with the character set determined by sampling initial data.
      Parameters:
      `in` - the `InputStream` object including the text data

      `size` - the sampling size

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is in UTF-8 encoding

    <!-- -->

    - #### LCSDetectionReader

          public LCSDetectionReader(String profile,
                                    InputStream in)
                             throws IOException,
                                    UTFDataFormatException

      Constructs the LCSD Reader instance with the character set determined by sampling initial data.
      Parameters:
      `profile` - the LCSD profile name. `null` is the default.

      `in` - the `InputStream` object including the text data

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is in UTF-8 encoding

    <!-- -->

    - #### LCSDetectionReader

          public LCSDetectionReader(String profile,
                                    InputStream in,
                                    int size)
                             throws IOException,
                                    UTFDataFormatException

      Constructs the LCSD Reader instance with the character set determined by sampling initial data.
      Parameters:
      `profile` - the LCSD profile name. `null` is the default

      `in` - the `InputStream` object including the text data

      `size` - the sampling size

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is in UTF-8 encoding

    <!-- -->

    - #### LCSDetectionReader

          public LCSDetectionReader(Reader reader)
                             throws IOException

      Constructs the LCSD Reader instance over the input stream reader.
      This constructor is used to detect the language from the reader object. The character set is always UTF-16.

      Parameters:
      `reader` - the `InputStreamReader` object

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

    <!-- -->

    - #### LCSDetectionReader

          public LCSDetectionReader(String profile,
                                    Reader reader)
                             throws IOException

      Constructs the LCSD Reader instance over the reader.
      This constructor is used to detect the language from the reader object. The character set is always UTF-16.

      Parameters:
      `profile` - the LCSD Profile name. `null` is the default

      `reader` - the reader including the text data

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

  <!-- -->

  - ### Method Detail

    - #### getResult

          public LCSDResultSet getResult()
                                  throws IOException,
                                         UTFDataFormatException

      Returns the result set of LCSD.
      If the language information is required in your application, call this method. The character set is implicitly used for the conversions, but if you need the name, call this method.

      Returns:
      the result set of LCSD

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if an invalid UTF-8 data sequence is detected. Note this occurs only if the source is in UTF-8 encoding

    <!-- -->

    - #### read

          public int read()
                   throws IOException,
                          UTFDataFormatException

      Reads a single character.
      Overrides:
      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#read--) in class [`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      Returns:
      the character read, or `-1` if the end of the stream has been reached

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if an I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

    <!-- -->

    - #### read

          public int read(char[] cbuf,
                          int offset,
                          int length)
                   throws IOException,
                          UTFDataFormatException

      Reads characters into a portion of an array.
      Specified by:
      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#read-char:A-int-int-) in class [`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      Parameters:
      `cbuf` - destination buffer

      `offset` - offset at which to start storing characters

      `length` - maximum number of characters to read

      Returns:
      the number of characters read, or `-1` if the end of the stream has been reached

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

    <!-- -->

    - #### close

          public void close()
                     throws IOException

      Closes the stream.
      Specified by:
      [`close`](http://docs.oracle.com/javase/8/docs/api/java/io/Closeable.html?is-external=true#close--) in interface [`Closeable`](http://docs.oracle.com/javase/8/docs/api/java/io/Closeable.html?is-external=true)

      Specified by:
      [`close`](http://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true#close--) in interface [`AutoCloseable`](http://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true)

      Specified by:
      [`close`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#close--) in class [`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if I/O error occurs

    <!-- -->

    - #### ready

          public boolean ready()
                        throws IOException

      Tells whether this stream is ready to be read.
      Overrides:
      [`ready`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#ready--) in class [`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      Returns:
      `true` if the next `read()` call is guaranteed not to block input, otherwise `false` is returned

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if I/O error occurs

    <!-- -->

    - #### markSupported

          public boolean markSupported()

      Tells whether this stream supports the `mark()` operation.
      Overrides:
      [`markSupported`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#markSupported--) in class [`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      Returns:
      `true` if this stream supports the `mark()` operation

    <!-- -->

    - #### mark

          public void mark(int readAheadLimit)
                    throws IOException

      Marks the present position in the stream.
      Overrides:
      [`mark`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#mark-int-) in class [`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      Parameters:
      `readAheadLimit` - limit on the number of characters that may be read while still preserving the mark. After reading the limited number of characters, attempting to reset the stream may fail.

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if the stream does not support the `mark()` operation, or if some other I/O error occurs

    <!-- -->

    - #### reset

          public void reset()
                     throws IOException

      Resets the stream.
      Overrides:
      [`reset`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#reset--) in class [`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if the stream has not been marked, or if the mark has been invalidated, or if the stream does not support the `reset()` operation, or if some other I/O error occurs

    <!-- -->

    - #### read

          public int read(char[] cbuf)
                   throws IOException,
                          UTFDataFormatException

      Reads characters into an array.
      Overrides:
      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#read-char:A-) in class [`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      Parameters:
      `cbuf` - destination buffer

      Returns:
      the number of characters read, or `-1` if the end of the stream has been reached

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if I/O error occurs

      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any invalid UTF-8 data sequence is detected. Note this occurs only if the source is UTF-8 data.

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

- [Prev Class](LCSDetectionInputStream.md)
- [Next Class](LCSDetector.md)

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
