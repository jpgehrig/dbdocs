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

- [Prev Class](URLDecoder.md)
- Next Class

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

## Class URLEncoder

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.net.URLEncoder

<!-- -->

-

  ------------------------------------------------------------------------



      public class URLEncoder
      extends Object

  The `URLEncoder` contains a utility method for converting a `String` object into a MIME format called `x-www-form-urlencoded` format.
  To convert a `String` object, each character is examined in turn:

  - The ASCII characters '`a`' through '`z`', '`A`' through '`Z`', '`0`' through '`9`', and ".", "-", "", "\_" remain the same.
  - The space character '` `' is converted into a plus sign '`+`'.
  - All other characters are converted into the 3-character string "`%`*`xy`*", where *xy* is the two-digit hexadecimal representation of the lower 8-bits of the character.

  When you encode a full set of URL string, for example, `http://www.acme.com/`, it is troublesome to encode special meaning characters such as `':'` and `'/'`. To avoid encoding, you can set the parameter of `escResChar` to `false`. The following characters will not be encoded:

  - `;` - Semicolon (U+003B)
  - `/` - Forward slash (U+002F)
  - `?` - Question mark (U+003F)
  - `:` - Colon (U+003A)
  - `(` - At sign (U+0040)
  - `&` - Ampersand (U+0026)
  - `=` - Equal sign (U+002D)
  - `+` - Plus sign (U+002B)
  - `$` - Dollar sign (U+0024)
  - `,` - Comma (U+002C)

  By default, `escResChar` is `true`.

  For information about URL encode/decode, see RFC 1738.

  Since:
  10.1.0.2

  See Also:
  [RFC 1738](http://www.ietf.org/rfc/rfc1738.txt)

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                                                               |
    |------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `encode``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`<br>Encodes a `String` object into `x-www-form-urlencoded` format using UTF-8 character set encoding.                                                                                     |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `encode``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s, boolean escResChar)`<br>Encodes a `String` object into `x-www-form-urlencoded` format using UTF-8 character set encoding.                                                                 |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `encode``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s, boolean escResChar, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` enc)`<br>Encodes a `string` object into `x-www-form-urlencoded` format. |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Method Detail

    - #### encode

          public static String encode(String s)

      Encodes a `String` object into `x-www-form-urlencoded` format using UTF-8 character set encoding. Any reserved characters are encoded.
      Parameters:
      `s` - a `String` object to be encoded

      Returns:
      the translated `String` object

    <!-- -->

    - #### encode

          public static String encode(String s,
                                      boolean escResChar)

      Encodes a `String` object into `x-www-form-urlencoded` format using UTF-8 character set encoding. `escResChar` determines whether it encodes the reserved characters .
      Parameters:
      `s` - a `String` ojbect to be translated

      `escResChar` - determines whether to encode the reserved characters; `true` - encode (default), `false` - don't encode

      Returns:
      the translated `String` object

      Throws:
      [`IllegalStateException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalStateException.html?is-external=true) - if UTF-8 is not supported by JVM

    <!-- -->

    - #### encode

          public static String encode(String s,
                                      boolean escResChar,
                                      String enc)
                               throws UnsupportedEncodingException

      Encodes a `string` object into `x-www-form-urlencoded` format.
      Currently AL16UTF16(also known as UTF-16BE) is not supported.

      Parameters:
      `s` - a `String` object to be translated

      `escResChar` - determines whether to encode the reserved characters; `true` - encode (default), `false` - don't encode

      `enc` - the name of an Oracle or IANA character set

      Returns:
      the translated `String` object

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the character set is not supported

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

- [Prev Class](URLDecoder.md)
- Next Class

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
