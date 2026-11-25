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

- [Prev Class](OraSimpleDateFormat.md)
- [Next Class](UTF8ValidationFilter.md)

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

## Class OraUnicodeProperty

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.text.OraUnicodeProperty

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class OraUnicodeProperty
      extends Object
      implements Serializable

  This `OraUnicodeProperty` class is used to access Unicode character property. Currently only display width information is provided.
  Since:
  Oracle 11

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                                                                                                     |
    |-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                       | `getDisplayWidth``(int codepoint, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charSet, boolean isReplacementOn)`<br>Get the display width of a Unicode `codepoint`.                                                                                      |
    | `int`                       | `getDisplayWidth``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charSet, boolean isReplacementOn)`<br>Get the display width of a Unicode string `str`. |
    | `static OraUnicodeProperty` | `getInstance``()`<br>Get an OraUnicodeProperty instance.                                                                                                                                                                                                                                                   |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Method Detail

    - #### getInstance

          public static OraUnicodeProperty getInstance()

      Get an OraUnicodeProperty instance. This class is a singleton. Two or more calls will get the same instance.
      Returns:
      an OraUnicodeProperty object

    <!-- -->

    - #### getDisplayWidth

          public int getDisplayWidth(int codepoint,
                                     String charSet,
                                     boolean isReplacementOn)
                              throws SQLException,
                                     UnsupportedEncodingException

      Get the display width of a Unicode `codepoint`. Display width classification is based on East Asia Width definition of Unicode Standard, and display width data are from Unicode version 4.0. Ambiguous characters can be sometimes narrow and sometimes wide, and target character set `charSet` is used to resolve their display width. In other words, if the display width of the Unicode `codepoint` is ambiguous, then return its display width in the target character set `charSet`. If its display width is not defined in the target character set, return 1 if it is a single byte character; return 2 otherwise(a multi-byte character).
      Example:
              OraUnicodeProperty oup = OraUnicodeProperty.getInstance();
              int width = oup.getDisplayWidth(0x1121, "EUC_JP", true);


      Parameters:
      `codepoint` - a Unicode codepoint

      `charSet` - a target JAVA character set name

      `isReplacementOn` - a flag indicating whether character replacement is allowed for conversion.

      Returns:
      display width. Possible values are 0, 1, and 2.

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the display width is ambiguous and the target character set name is invalid, or Oracle does not have a corresponding character set mapping, or the codepoint is an invalid surrogate.

      [`SQLException`](http://docs.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if character replacement is needed for conversion but the replacement flag is off.

    <!-- -->

    - #### getDisplayWidth

          public int getDisplayWidth(String str,
                                     String charSet,
                                     boolean isReplacementOn)
                              throws SQLException,
                                     UnsupportedEncodingException

      Get the display width of a Unicode string `str`. Display width classification is based on East Asia Width definition of Unicode Standard, and display width data are from Unicode version 4.0. Ambiguous characters can be sometimes narrow and sometimes wide, and target character set `charSet` is used to resolve their display width.
      Example:
              String str = "Hello, how are you?";
              OraUnicodeProperty oup = OraUnicodeProperty.getInstance();
              int width = oup.getDisplayWidth(str, "GBK", true);


      Parameters:
      `str` - a Unicode string

      `charSet` - a target JAVA character set name

      `isReplacementOn` - a flag indicating whether character replacement is allowed for conversion

      Returns:
      display width.

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the display width is ambiguous and the target character set name is invalid or Oracle does not have a corresponding character set mapping, or the string contains any invalid unicode surrogates.

      [`SQLException`](http://docs.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if character replacement is needed for conversion but the replacement flag is off.

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

- [Prev Class](OraSimpleDateFormat.md)
- [Next Class](UTF8ValidationFilter.md)

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
