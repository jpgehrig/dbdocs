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

- [Prev Class](CharEntityReference.Form.md)
- [Next Class](URLDecoder.md)

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

## Class MimeUtility

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.net.MimeUtility

<!-- -->

-

  ------------------------------------------------------------------------



      public class MimeUtility
      extends Object

  The `MimeUtility` contains encoder and decoder information for MIME header and body text. This is an alternative to the `javax.mail.internet.MimeUtility` class, but `MimeUtillity` allows you to use Oracle or IANA character set names.
  RFC 2047 specifies the MIME-safe header and body format. The mail header must be in the following US-ASCII character set encoding:

  `=? <charset> ? <encoding> ? <encoded-text> ?=`

  This output can be generated using the `MimeUtility.encodeHeader(String, String, String)` method. The receiver of the data is able to decode the data based on the included character set (for example, `iso-8859-1`) and encoding (`"B"` or `"Q"`) information using `MimeUtility.decodeHeader(String)`.

  Since:
  10.2.0.0

  See Also:
  [RFC 2045](http://www.ietf.org/rfc/rfc2045.txt), [RFC 2047](http://www.ietf.org/rfc/rfc2047.txt)

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                            |
    |------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `decodeHeader``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` srcstr)`<br>Decodes a MIME-safe form into a `String` object for MIME header as per RFC 2047.                                                                                                                                                                                                                        |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `decodeText``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` intext)`<br>Decode an input "Unstructured" headers which are defined in RFC 822.                                                                                                                                                                                                                                      |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `decodeText``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` intext, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Decode an input "Unstructured" headers which are defined in RFC 822.                                                                                                                               |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `decodeWord``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` eword)`<br>Decode an input encoded mail-safe form word token accoding to RFC 2047.                                                                                                                                                                                                                                    |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `decodeWord``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` eword, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Same as decodeWord(String), except that the specified charset is used and the one declared in the string is ignored.                                                                                |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `encodeHeader``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` srcstr, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` encoding)`<br>Encodes a `String` object into a MIME-safe form for MIME header as per RFC 2047.         |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `encodeText``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text)`<br>Deprecated. <br>As of 10.1.2, use encodeText(text, charset, encoding) instead.                                                                                                                                                                                                                              |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `encodeText``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` encoding)`<br>Encode an input RFC 822 text token into mail-safe form according to RFC 2047.                |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `encodeText``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` encoding, boolean bFold)`<br>Encode an input RFC 822 text token into mail-safe form according to RFC 2047. |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `encodeWord``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` word)`                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `encodeWord``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` word, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` encoding)`                                                                                                 |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getDefaultJavaCharset``()`<br>Query the system property `file.encoding` to get the default Java charset.                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `javaCharset``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Get the equivalent Java encoding name of a MIME charset.                                                                                                                                                                                                                                                |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `mimeCharset``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` encoding)`<br>Get the equivalent MIME charset name of a Java encoding.                                                                                                                                                                                                                                               |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Method Detail

    - #### encodeHeader

          public static String encodeHeader(String srcstr,
                                            String charset,
                                            String encoding)
                                     throws UnsupportedEncodingException

      Encodes a `String` object into a MIME-safe form for MIME header as per RFC 2047.
      Currently, AL16UTF16 (also known as UTF-16BE) is not supported.

      The output includes the character set and encoding (for example, base64 or quoted-printable) information in the following form:

      `=? <charset> ? <encoding> ? <encoded-text> ?=`

      Parameters:
      `srcstr` - a `String` object to be encoded

      `charset` - an Oracle or IANA character set name

      `encoding` - base64 ("B") or quoted-printable ("Q")

      Returns:
      an encoded `String` object

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the character set name is invalid or not supported

    <!-- -->

    - #### decodeHeader

          public static String decodeHeader(String srcstr)
                                     throws UnsupportedEncodingException

      Decodes a MIME-safe form into a `String` object for MIME header as per RFC 2047.
      The input is expected to include the character set and encoding (for example, base64 or quoted-printable) information in the following form:

      `=? <charset> ? <encoding> ? <encoded-text> ?=`

      Parameters:
      `srcstr` - a `String` object to be decoded.

      Returns:
      a decoded `String` object

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - - if the character set name is invalid or not supported

    <!-- -->

    - #### mimeCharset

          public static String mimeCharset(String encoding)

      Get the equivalent MIME charset name of a Java encoding.
      Parameters:
      `encoding` - a Java encoding

      Returns:
      the equivalent MIME/IANA charset name. Return the input encoding if no proper mapping.

    <!-- -->

    - #### javaCharset

          public static String javaCharset(String charset)

      Get the equivalent Java encoding name of a MIME charset.
      Parameters:
      `charset` - a MIME charset name

      Returns:
      the equivalent Java encoding. Return the input charset if no proper mapping.

    <!-- -->

    - #### getDefaultJavaCharset

          public static String getDefaultJavaCharset()

      Query the system property `file.encoding` to get the default Java charset. Before it, if the system property `mail.mime.charset` is set, a equivalent Java charset of this MIME charset will be returned.
      Returns:
      the default Java charset of the system's default locale.

    <!-- -->

    - #### decodeWord

          public static final String decodeWord(String eword,
                                                String charset)
                                         throws UnsupportedEncodingException

      Same as decodeWord(String), except that the specified charset is used and the one declared in the string is ignored.
      Parameters:
      `eword` - the possibly encoded value

      `charset` - MIME charset name

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the string is not an encoded-word according to RFC 2047 or the charset conversion failed.

    <!-- -->

    - #### decodeWord

          public static final String decodeWord(String eword)
                                         throws UnsupportedEncodingException

      Decode an input encoded mail-safe form word token accoding to RFC 2047. Firstly decode it while transferring the token, then convert it into Unicode. If the decoding or the character conversion fails, an UnsupportedEncodingException is thrown.
      Parameters:
      `eword` - the possibly encoded mail-safe form token

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the input word is not an encoded email token according to RFC 2047 or the charset conversion fails.

    <!-- -->

    - #### encodeText

          public static final String encodeText(String text)
                                         throws UnsupportedEncodingException

      Deprecated. As of 10.1.2, use encodeText(text, charset, encoding) instead.
      Encode an input RFC 822 text token into mail-safe form according to RFC 2047. Pure US-ASCII strings are returned as is. Strings containing non US-ASCII characters will first be encoded with the platform default character set and then encoded with either the 'B' or 'Q' transfer encoding (RFC 2045). The return Unicode string will therefore include only US-ASCII characters.
      Note that we should use this method to encode only "unstructured" RFC 822 headers. Folding behaviour can be specified by setting the system property mail.mime.foldencodedwords

      Parameters:
      `text` - mail header Unicode string

      Returns:
      encoded mail header Unicode string

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the encoding fails

    <!-- -->

    - #### encodeText

          public static final String encodeText(String text,
                                                String charset,
                                                String encoding,
                                                boolean bFold)
                                         throws UnsupportedEncodingException

      Encode an input RFC 822 text token into mail-safe form according to RFC 2047. Pure US-ASCII strings are returned as is. Strings containing non US-ASCII characters will first be encoded with the input character set and then encoded with either the 'B' or 'Q' transfer encoding (RFC 2045). The return Unicode string will therefore include only US-ASCII characters.
      Note that we should use this method to encode only "unstructured" RFC 822 headers. Folding behaviour can be specified by setting the system property mail.mime.foldencodedwords

      Parameters:
      `text` - mail header Unicode string

      `charset` - the character set used to encode the 'text'. Use the default platform charset if this parameter is null.

      `encoding` - the transfer encoding in RFC 2045. Now there are only "B" and "Q". If this parameter is null, use the 'Q' encoding if more than half of the characters to be encoded are ASCII, otherwise use the "B" encoding.

      `bFold` - if true the encoded word will be folded as per RFC 882, if false the encoded word will not be folded

      Returns:
      encoded mail header Unicode string

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the encoding fails

    <!-- -->

    - #### encodeText

          public static final String encodeText(String text,
                                                String charset,
                                                String encoding)
                                         throws UnsupportedEncodingException

      Encode an input RFC 822 text token into mail-safe form according to RFC 2047. Pure US-ASCII strings are returned as is. Strings containing non US-ASCII characters will first be encoded with the input character set and then encoded with either the 'B' or 'Q' transfer encoding (RFC 2045). The return Unicode string will therefore include only US-ASCII characters.
      Note that we should use this method to encode only "unstructured" RFC 822 headers. Folding behaviour can be specified by setting the system property mail.mime.foldencodedwords

      Parameters:
      `text` - mail header Unicode string

      `charset` - the character set used to encode the 'text'. Use the default platform charset if this parameter is null.

      `encoding` - the transfer encoding in RFC 2045. Now there are only "B" and "Q". If this parameter is null, use the 'Q' encoding if more than half of the characters to be encoded are ASCII, otherwise use the "B" encoding.

      Returns:
      encoded mail header Unicode string

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the encoding fails

    <!-- -->

    - #### decodeText

          public static final String decodeText(String intext)
                                         throws UnsupportedEncodingException

      Decode an input "Unstructured" headers which are defined in RFC 822.
      Decode the input string according to RFC 2047, Section 6.1.1. Invalid RFC 2047 style encoded headers are returned as is. If the decoding fails, an UnsupportedEncodingException is thrown.

      Parameters:
      `intext` - the possibly encoded string

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the decoding fails.

    <!-- -->

    - #### decodeText

          public static final String decodeText(String intext,
                                                String charset)
                                         throws UnsupportedEncodingException

      Decode an input "Unstructured" headers which are defined in RFC 822.
      Decode the input string according to RFC 2047, Section 6.1.1. Invalid RFC 2047 style encoded headers are returned as is. If the decoding fails, an UnsupportedEncodingException is thrown.

      Parameters:
      `intext` - the possibly encoded string

      `charset` - MIME charset of etext

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the decoding fails.

    <!-- -->

    - #### encodeWord

          public static final String encodeWord(String word)
                                         throws UnsupportedEncodingException

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true)

    <!-- -->

    - #### encodeWord

          public static String encodeWord(String word,
                                          String charset,
                                          String encoding)
                                   throws UnsupportedEncodingException

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true)

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

- [Prev Class](CharEntityReference.Form.md)
- [Next Class](URLDecoder.md)

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
