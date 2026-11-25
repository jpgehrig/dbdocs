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

- [Prev Class](LCSDetectionReader.md)
- [Next Class](LCSDResultSet.md)

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

## Class LCSDetector

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.lcsd.LCSDetector

<!-- -->

-

  ------------------------------------------------------------------------



      public class LCSDetector
      extends Object

  The `LCSDetector` class contains methods to automatically detect and recognize language, encoding, or both based on text input.
  To use the `LCSDetector` class, call the `getInstance()` method to obtain an instance of the `LCSDetector` class. You can specify a profile by calling the `getInstance(profile)` method, or simply call the `getInstance()` method to use the standard profile depending on the content of the text you plan to sample. Certain profiles may yield more accurate results. For example, if you are sampling medical journals, you many want to use a profile that is built using mainly medical journals. If you are sampling computer related white papers, a profile built with similar documents improves the accuracy of the detection. Currently, we only provide one standard profile which is for general purpose detection.

  The detection process begins by calling the `LCSDetector.detect(byte[])` method. Statistics are cumulated every time a `LCSDetector.detect(byte[])` method is called. When you are ready for the result, call the `LCSDetector.getResult()` method to retrieve an [`LCSDResultSet`](LCSDResultSet.md) instance. To begin a new detection using the same `LCSDetector` instance, call the `LCSDetector.reset()` method to remove the cumulated statistics.

  Since:
  10.1.0.2

  See Also:
  `LCSDResultSet`

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                              |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LCSDetector``()`<br>Constructor which uses the standard default profile.                                                                                                                                                |
    | `LCSDetector``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Constructor which takes a profile name and allows you to choose a profile other than the default. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                                                                                                                                                                       |
    |-------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                              | `detect``(byte[] input)`<br>Statistical data is cumulated in an internal structure when the `detect()` methods are called.                                                                                                                                                                   |
    | `int`                               | `detect``(byte[] input, int offset, int length)`<br>Statistical data is cumulated in an internal structure when the `detect()` methods are called.                                                                                                                                           |
    | `void`                              | `detect``(char[] input)`<br>Statistical data is cumulated in an internal structure when the `detect()` methods are called.                                                                                                                                                                   |
    | `int`                               | `detect``(char[] input, int offset, int length)`<br>Statistical data is cumulated in an internal structure when the `detect()` methods are called.                                                                                                                                           |
    | `void`                              | `detect``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` input)`<br>Statistical data is cumulated in an internal structure when the `detect()` methods are called.                                                                    |
    | `int`                               | `detect``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` input, int length)`<br>Statistical data is cumulated in an internal structure when the `detect()` methods are called.                                                        |
    | `void`                              | `detect``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` input)`<br>Statistical data is cumulated in an internal structure when the `detect()` methods are called.                                                                            |
    | `int`                               | `detect``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` input, int length)`<br>Statistical data is cumulated in an internal structure when the `detect()` methods are called.                                                                |
    | [`LCSDResultSet`](LCSDResultSet.md) | `getResult``()`<br>Determines the top ranking language/character set pairs from the cumulated statistical data.                                                                                                                                                                              |
    | `static boolean`                    | `isCharsetSupported``(int charsettype, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Check whether the given character set that is equivalent to the Oracle, IANA, or Java Character Set is supported by the detection feature. |
    | `void`                              | `reset``()`<br>To reset statistical data for all pairs to `0`.                                                                                                                                                                                                                               |
    | `void`                              | `setCharacterSetFilter``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Sets the character set filter if you know the character set of the input data.                                                                           |
    | `void`                              | `setLanguageFilter``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language)`<br>Sets the language filter if you know the language of the input data.                                                                                        |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Constructor Detail

    - #### LCSDetector

          public LCSDetector()

      Constructor which uses the standard default profile.

    <!-- -->

    - #### LCSDetector

          public LCSDetector(String name)

      Constructor which takes a profile name and allows you to choose a profile other than the default.
      Parameters:
      `name` - name of profile to use

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if an invalid profile name is specified

  <!-- -->

  - ### Method Detail

    - #### setCharacterSetFilter

          public void setCharacterSetFilter(String charset)

      Sets the character set filter if you know the character set of the input data. The default value is none. If both the language filter and character set filter are set, they are ignored. If an invalid IANA character set name is passed in, it is ignored.
      Parameters:
      `charset` - IANA character set name

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if an invalid character set is specified

    <!-- -->

    - #### setLanguageFilter

          public void setLanguageFilter(String language)

      Sets the language filter if you know the language of the input data. The default value is none. If both the language filter and character set filter are set, they are ignored. If an invalid language name is passed in, it is ignored.
      Parameters:
      `language` - ISO language name.

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if an invalida language is specified

    <!-- -->

    - #### detect

          public void detect(byte[] input)

      Statistical data is cumulated in an internal structure when the `detect()` methods are called. Use the `LCSDetector.reset()` method to clear the cumulated statistics.
      Parameters:
      `input` - the bytes to be sampled by the `detect` method

    <!-- -->

    - #### detect

          public int detect(byte[] input,
                            int offset,
                            int length)

      Statistical data is cumulated in an internal structure when the `detect()` methods are called. Use the `LCSDetector.reset()` method to clear the cumulated statistics. Only the specified length of bytes is sampled.
      Parameters:
      `input` - the bytes to be sampled by the `detect` method

      `offset` - the index of the first byte to sample

      `length` - the number of bytes to sample

      Returns:
      the number of bytes sampled, or `-1` if the end of the array reached

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - call the `reset` method

    <!-- -->

    - #### detect

          public void detect(InputStream input)
                      throws IOException

      Statistical data is cumulated in an internal structure when the `detect()` methods are called. Use the `LCSDetector.reset()` method to clear the cumulated statistics. The entire stream is sampled by the `detect()` method.
      Parameters:
      `input` - `InputStream` to be sampled by the `detect` method

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if error occurs while doing operation on stream

      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - call the `reset` method

    <!-- -->

    - #### detect

          public int detect(InputStream input,
                            int length)
                     throws IOException

      Statistical data is cumulated in an internal structure when the `detect()` methods are called. Use the `LCSDetector.reset()` method to clear the cumulated statistics. Only the specified length of bytes will be sampled.
      Parameters:
      `input` - `InputStream` to be sampled by the `detect()` method

      `length` - the number of bytes to sample

      Returns:
      the number of bytes sampled, or `-1` if the end of the stream is reached

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if error occurs while doing operation on stream

      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - call `reset` method

    <!-- -->

    - #### detect

          public void detect(String input)

      Statistical data is cumulated in an internal structure when the `detect()` methods are called. Use the `LCSDetector.reset()` method to clear the cumulated statistics. The entire string is sampled by the `detect()` method.
      Parameters:
      `input` - to be sampled by the `detect` method

    <!-- -->

    - #### detect

          public int detect(String input,
                            int length)

      Statistical data is cumulated in an internal structure when the `detect()` methods are called. Use the `LCSDetector.reset()` method to clear the cumulated statistics. Only the specified length of characters will be sampled.
      Parameters:
      `input` - a string to be sampled by the `detect()` method

      `length` - the number of characters to sample

      Returns:
      the number of characters sampled, or `-1` if the end of the string is reached

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - call `reset` method

    <!-- -->

    - #### detect

          public void detect(char[] input)

      Statistical data is cumulated in an internal structure when the `detect()` methods are called. Use the `LCSDetector.reset()` method to clear the cumulated statistics. The entire array is sampled by the `detect()` method.
      Parameters:
      `input` - the characters to be sampled by the `detect` method

    <!-- -->

    - #### detect

          public int detect(char[] input,
                            int offset,
                            int length)

      Statistical data is cumulated in an internal structure when the `detect()` methods are called. Use the `LCSDetector.reset()` method to clear the cumulated statistics. Only the specified length of characters will be sampled.
      Parameters:
      `input` - the `char` array to be sampled by the `detect()` method

      `offset` - the index of the first character to sample

      `length` - the number of characters to sample

      Returns:
      the number of characters sampled, or `-1` if the end of the array reached.

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - call `reset` method

    <!-- -->

    - #### getResult

          public LCSDResultSet getResult()

      Determines the top ranking language/character set pairs from the cumulated statistical data.
      Returns:
      An [`LCSDResultSet`](LCSDResultSet.md) object which contains the result

    <!-- -->

    - #### isCharsetSupported

          public static boolean isCharsetSupported(int charsettype,
                                                   String charset)

      Check whether the given character set that is equivalent to the Oracle, IANA, or Java Character Set is supported by the detection feature.
      See [`LocaleMapper`](../util/LocaleMapper.md) for the parameter `ORACLE`, `IANA`, or `JAVA`.

      Parameters:
      `charsettype` - can be `ORACLE`, `IANA`, or `JAVA`.

      `charset` - the given character set

      Returns:
      `true` if the given character set is supported by the detection feature, or `false` if not

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if an invalid profile is specified

    <!-- -->

    - #### reset

          public void reset()

      To reset statistical data for all pairs to `0`.

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

- [Prev Class](LCSDetectionReader.md)
- [Next Class](LCSDResultSet.md)

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
