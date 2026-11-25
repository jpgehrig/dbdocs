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

- [Prev Class](OraUnicodeProperty.md)
- [Next Class](UTF8ValidationFilter.ValidationBehavior.md)

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

oracle.i18n.text

## Class UTF8ValidationFilter

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.io.InputStream](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)

  - - [java.io.FilterInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

    - - [java.io.BufferedInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true)

      - - oracle.i18n.text.UTF8ValidationFilter

<!-- -->

- All Implemented Interfaces:
  [Closeable](http://docs.oracle.com/javase/8/docs/api/java/io/Closeable.html?is-external=true), [AutoCloseable](http://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true)

  ------------------------------------------------------------------------



      public class UTF8ValidationFilter
      extends BufferedInputStream

  The `UTF8ValidationFilter` class is used to check the illegal UTF-8 byte sequence to replace with the replacement character U+FFFD or raise an exception.
  The validation occurs transparently for the users. The output has the same contents as the input if an invalid UTF-8 sequence is not found. If an invalid UTF-8 sequence is found and [`UTF8ValidationFilter.ValidationBehavior.REPLACE`](UTF8ValidationFilter.ValidationBehavior.md) is specified as the conversion behavior, the output will include U+FFFD, or 0xef, 0xbf, 0xbd in UTF-8 encoding where the problem occurs. By default, the illegal UTF-8 sequence is reported by the exception `UTFDataFormatException`.

  Since:
  10.2

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                                                                                               |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`UTF8ValidationFilter.ValidationBehavior`](UTF8ValidationFilter.ValidationBehavior.md)<br>The `ValidationBehavior` class is the class used to determine the behavior in case the conversion fails. |

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from class java.io.[BufferedInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true)

      [`buf`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#buf)`, `[`count`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#count)`, `[`marklimit`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#marklimit)`, `[`markpos`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#markpos)`, `[`pos`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#pos)

    <!-- -->

    - ### Fields inherited from class java.io.[FilterInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

      [`in`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#in)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                             |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `UTF8ValidationFilter``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in)`<br>Constructs the object with the `InputStream` object.                                                                                                                                                              |
    | `UTF8ValidationFilter``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int size)`<br>Constructs the object with the `InputStream` object with the buffer size.                                                                                                                               |
    | `UTF8ValidationFilter``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` in, int size, `[`UTF8ValidationFilter.ValidationBehavior`](UTF8ValidationFilter.ValidationBehavior.md)` action)`<br>Constructs the object with the `InputStream` object with the buffer size and the validation behavior. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                        |
    |-------------------|---------------------------------------------------------------|
    | `int`             | `read``()`<br>Reads one byte.                                 |
    | `int`             | `read``(byte[] b, int off, int len)`<br>Reads the byte array. |

    - ### Methods inherited from class java.io.[BufferedInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true)

      [`available`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#available--)`, `[`close`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#close--)`, `[`mark`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#mark-int-)`, `[`markSupported`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#markSupported--)`, `[`reset`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#reset--)`, `[`skip`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#skip-long-)

    <!-- -->

    - ### Methods inherited from class java.io.[FilterInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)

      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true#read-byte:A-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Constructor Detail

    - #### UTF8ValidationFilter

          public UTF8ValidationFilter(InputStream in)

      Constructs the object with the `InputStream` object.
      Parameters:
      `in` - the `InputStream` object

    <!-- -->

    - #### UTF8ValidationFilter

          public UTF8ValidationFilter(InputStream in,
                                      int size)

      Constructs the object with the `InputStream` object with the buffer size.
      Parameters:
      `in` - the `InputStream` object

      `size` - the buffer size

    <!-- -->

    - #### UTF8ValidationFilter

          public UTF8ValidationFilter(InputStream in,
                                      int size,
                                      UTF8ValidationFilter.ValidationBehavior action)

      Constructs the object with the `InputStream` object with the buffer size and the validation behavior.
      Parameters:
      `in` - the `InputStream` object

      `size` - the buffer size

      `action` - specifies the error action to be either `REPLACE` or `REPORT`

  <!-- -->

  - ### Method Detail

    - #### read

          public int read()
                   throws UTFDataFormatException,
                          IOException

      Reads one byte.
      Overrides:
      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#read--) in class [`BufferedInputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true)

      Returns:
      a byte from the input stream

      Throws:
      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any illegal UTF-8 sequence is found

      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any other I/O error occurs

    <!-- -->

    - #### read

          public int read(byte[] b,
                          int off,
                          int len)
                   throws UTFDataFormatException,
                          IOException

      Reads the byte array.
      Overrides:
      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true#read-byte:A-int-int-) in class [`BufferedInputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true)

      Parameters:
      `b` - buffer

      `off` - offset

      `len` - length

      Returns:
      the number of bytes copied

      Throws:
      [`UTFDataFormatException`](http://docs.oracle.com/javase/8/docs/api/java/io/UTFDataFormatException.html?is-external=true) - if any illegal UTF-8 sequence is found

      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any other I/O error occurs

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

- [Prev Class](OraUnicodeProperty.md)
- [Next Class](UTF8ValidationFilter.ValidationBehavior.md)

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
