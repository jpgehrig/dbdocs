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

- [Prev Class](MimeUtility.md)
- [Next Class](URLEncoder.md)

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

oracle.i18n.net

## Class URLDecoder

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.net.URLDecoder

<!-- -->

-

  ------------------------------------------------------------------------



      public class URLDecoder
      extends Object

  The `URLDecoder` contains a utility method for converting from a MIME format called `x-www-form-urlencoded` to a `String` object.
  To convert to a `String`, each character is examined in turn:

  - The ASCII characters '`a`' through '`z`', '`A`' through '`Z`', and '`0`' through '`9`' remain the same.
  - The plus sign '`+`' is converted into a space character '` `'.
  - The remaining characters are represented by 3-character strings which begin with the percent sign, "`%`*`xy`*", where *xy* is the two-digit hexadecimal representation of the lower 8-bits of the character.

  Since:
  10.1.0.2

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                                           |
    |------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `decode``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`<br>Decodes a `x-www-form-urlencoded` object to a `String` object using UTF-8 character set encoding.                                                                 |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `decode``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` enc)`<br>Decodes a `x-www-form-urlencoded` object to a `String` object. |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Method Detail

    - #### decode

          public static String decode(String s)

      Decodes a `x-www-form-urlencoded` object to a `String` object using UTF-8 character set encoding.
      Parameters:
      `s` - `String` object to be decoded

      Returns:
      the translated `String` object

    <!-- -->

    - #### decode

          public static String decode(String s,
                                      String enc)
                               throws UnsupportedEncodingException

      Decodes a `x-www-form-urlencoded` object to a `String` object.
      Currently, AL16UTF16 (also known as UTF-16BE) is not supported.

      Parameters:
      `s` - `String` object to be decoded

      `enc` - the name of Oracle or IANA character set

      Returns:
      the translated `String` object

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the character is not supported

      [`NumberFormatException`](http://docs.oracle.com/javase/8/docs/api/java/lang/NumberFormatException.html?is-external=true) - if invalid escape representation is detected

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

- [Prev Class](MimeUtility.md)
- [Next Class](URLEncoder.md)

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
