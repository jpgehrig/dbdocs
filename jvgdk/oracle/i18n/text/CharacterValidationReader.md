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
- [Next Class](OraCollationKey.md)

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

## Class CharacterValidationReader

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.io.Reader](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

  - - [java.io.FilterReader](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true)

    - - oracle.i18n.text.CharacterValidationReader

<!-- -->

- All Implemented Interfaces:
  [Closeable](http://docs.oracle.com/javase/8/docs/api/java/io/Closeable.html?is-external=true), [AutoCloseable](http://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true), [Readable](http://docs.oracle.com/javase/8/docs/api/java/lang/Readable.html?is-external=true)

  ------------------------------------------------------------------------



      public class CharacterValidationReader
      extends FilterReader

  The `CharacterValidationReader` class is the validator class that checks the conversion failure, and optionally checks the HTML.
  Do not use this validator class if the source is allowed to include `U+FFFD` since this validator cannot distinguish whether the `0xfffd` was given because of the conversion failure or intentionally being added.

  Since:
  10.2

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class java.io.[FilterReader](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true)

      [`in`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true#in)

    <!-- -->

    - ### Fields inherited from class java.io.[Reader](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      [`lock`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#lock)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `CharacterValidationReader``(`[`Reader`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` r)`<br>Constructs this object with the `Reader` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                  |
    |-------------------|-----------------------------------------------------------------------------------------|
    | `int`             | `read``()`<br>Reads a single character.                                                 |
    | `int`             | `read``(char[] cbuf, int off, int len)`<br>Reads characters into a portion of an array. |

    - ### Methods inherited from class java.io.[FilterReader](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true)

      [`close`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true#close--)`, `[`mark`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true#mark-int-)`, `[`markSupported`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true#markSupported--)`, `[`ready`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true#ready--)`, `[`reset`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true#reset--)`, `[`skip`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true#skip-long-)

    <!-- -->

    - ### Methods inherited from class java.io.[Reader](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)

      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#read-char:A-)`, `[`read`](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true#read-java.nio.CharBuffer-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Constructor Detail

    - #### CharacterValidationReader

          public CharacterValidationReader(Reader r)
                                    throws IOException

      Constructs this object with the `Reader` object.
      By default, HTML character and entity reference is not checked.

      Parameters:
      `r` - the input `Reader` object

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any I/O exception occurs

  <!-- -->

  - ### Method Detail

    - #### read

          public int read()
                   throws CharConversionException,
                          IOException

      Reads a single character.
      Overrides:
      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true#read--) in class [`FilterReader`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true)

      Returns:
      the character read, either as an integer in the range `0` to `65535` (`0x00-0xffff`), or `-1` if the end of the stream has been reached

      Throws:
      [`CharConversionException`](http://docs.oracle.com/javase/8/docs/api/java/io/CharConversionException.html?is-external=true) - if any invalid character is found

      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if any other I/O error occurs

    <!-- -->

    - #### read

          public int read(char[] cbuf,
                          int off,
                          int len)
                   throws CharConversionException,
                          IOException

      Reads characters into a portion of an array.
      Overrides:
      [`read`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true#read-char:A-int-int-) in class [`FilterReader`](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true)

      Parameters:
      `cbuf` - destination buffer

      `off` - offset at which to start storing characters

      `len` - maximum number of characters to read

      Returns:
      the number of characters read, or `-1` if the end of the stream has been reached

      Throws:
      [`CharConversionException`](http://docs.oracle.com/javase/8/docs/api/java/io/CharConversionException.html?is-external=true) - if any invalid character is found

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

- Prev Class
- [Next Class](OraCollationKey.md)

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
