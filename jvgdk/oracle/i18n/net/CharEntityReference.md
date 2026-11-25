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
- [Next Class](CharEntityReference.Form.md)

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

## Class CharEntityReference

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.net.CharEntityReference

<!-- -->

-

  ------------------------------------------------------------------------



      public class CharEntityReference
      extends Object

  The `CharEntityReference` class is a utility class to escape or unescape a string into a character reference or an entity reference form.
  Character reference refers to a specific character in the ISO/IEC 10646 character set in the following representation:

        CharRef ::= '&#' [0-9]+ ';' | '&#x' [0-9a-fA-F]+ ';'


  Entity reference refers to the content of the named entity of the form `'&XXX;'`, where `XXX` represents the name of the entity. These names are defined in XML and HTML standards.
  In escape operations, the entities `'amp', lt', 'gt', 'apos',` and `'quot'` are used as `NAMED` entity references. `DECIMAL` or `HEXADECIMAL` character references are used for other characters.

  In unescape operations, `'amp', 'lt', 'gt', 'apos', 'quot'`, and all entity references defined in HTML 4.01 are recognized in order to convert back to the original characters.

  See Also:
  [HTML 4.01 Specification](http://www.w3.org/TR/REC-html40/), [Extensible Markup Language (XML) 1.0 (Second Edition)](http://www.w3.org/TR/REC-xml)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                              |
    |-------------------|--------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`CharEntityReference.Form`](CharEntityReference.Form.md)<br>Form parameter class that specifies the escaped form. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                     |
    |------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `escape``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` srcstr)`<br>Escapes a string into the character entity reference in the `NAMED_DECIMAL_NUMBER` form assuming the WE8ISO8859P1 character set.                                                                                                       |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `escape``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` srcstr, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dstCharset)`<br>Escapes a string into the character entity reference in the `NAMED_DECIMAL_NUMBER` form.                                     |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `escape``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` srcstr, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dstCharset, `[`CharEntityReference.Form`](CharEntityReference.Form.md)` form)`<br>Escapes a string into the character entity reference form. |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `unescape``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` srcstr)`<br>Converts an escaped string into a Unicode string.                                                                                                                                                                                    |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Method Detail

    - #### escape

          public static String escape(String srcstr)

      Escapes a string into the character entity reference in the `NAMED_DECIMAL_NUMBER` form assuming the WE8ISO8859P1 character set.
      Default character set is WE8ISO8859P1, and the default form is the `NAMED_DECIMAL_NUMBER` form. Some characters are escaped in the named entity, for example, `&lt;` for `'<'`. Other characters are escaped in the hexadecimal form if they are not supported by the given character set.

      Parameters:
      `srcstr` - a string to be escaped

      Returns:
      an escaped string

      Throws:
      [`IllegalStateException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalStateException.html?is-external=true) - if WE8ISO8859P1 is not supported

      See Also:
      `CharEntityReference.escape(String, String, CharEntityReference.Form)`

    <!-- -->

    - #### escape

          public static String escape(String srcstr,
                                      String dstCharset)
                               throws UnsupportedEncodingException

      Escapes a string into the character entity reference in the `NAMED_DECIMAL_NUMBER` form.
      The default form is the `NAMED_DECIMAL_NUMBER` form. Some characters are escaped in the named entity, for example, `&lt;` for `'<'`. Other characters are escaped in the hexadecimal form if they are not supported by the given character set.

      Parameters:
      `srcstr` - a string to be escaped

      `dstCharset` - an Oracle character set name

      Returns:
      an escaped string

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the `dstCharset` is a invalid character set name

      See Also:
      `CharEntityReference.escape(String, String, CharEntityReference.Form)`

    <!-- -->

    - #### escape

          public static String escape(String srcstr,
                                      String dstCharset,
                                      CharEntityReference.Form form)
                               throws UnsupportedEncodingException

      Escapes a string into the character entity reference form. Aside from characters not supported by the given character set in either the `DECIMAL_NUMBER` or `HEXADECIMAL_NUMBER` form, the following characters will be escaped in either the `NAMED`, `DECIMAL_NUMBER`, or `HEXADECIMAL_NUMBER` forms:
      - `<` - Less than sign (U+003C)
      - `>` - Greater than sign (U+003E)
      - `&` - Ampersand (U+0026)
      - `'` - Apostrophe (U+0027)
      - `"` - Quotation mark (U+0022)

      Parameters:
      `srcstr` - a string to be escaped

      `dstCharset` - an Oracle character set name

      `form` - a form of character entity reference

      Returns:
      an escaped string

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the `dstCharset` parameter is an invalid character set name

    <!-- -->

    - #### unescape

          public static String unescape(String srcstr)

      Converts an escaped string into a Unicode string.
      Parameters:
      `srcstr` - a string containing escaped characters

      Returns:
      a string representing the original data

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if unregistered character entity reference is used

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
- [Next Class](CharEntityReference.Form.md)

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
