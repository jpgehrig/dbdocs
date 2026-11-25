Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XDBServletRequest.md)**
- **[Next Class](XDBStream.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xdb.servlet**

## **Class XDBServletResponse**

- **java.lang.Object**

- - **java.io.OutputStream**

  - - **javax.servlet.ServletOutputStream**

    - - **oracle.xdb.servlet.XDBServletResponse**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Closeable, java.io.Flushable, java.lang.AutoCloseable, javax.servlet.http.HttpServletResponse, javax.servlet.ServletResponse, [XDBStream](XDBStream.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XDBServletResponse
      extends javax.servlet.ServletOutputStream
      implements javax.servlet.http.HttpServletResponse, XDBStream

  **Servlet response object, providing access to the HTTP response.**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface javax.servlet.http.HttpServletResponse**

      **`SC_ACCEPTED, SC_BAD_GATEWAY, SC_BAD_REQUEST, SC_CONFLICT, SC_CONTINUE, SC_CREATED, SC_EXPECTATION_FAILED, SC_FORBIDDEN, SC_GATEWAY_TIMEOUT, SC_GONE, SC_HTTP_VERSION_NOT_SUPPORTED, SC_INTERNAL_SERVER_ERROR, SC_LENGTH_REQUIRED, SC_METHOD_NOT_ALLOWED, SC_MOVED_PERMANENTLY, SC_MOVED_TEMPORARILY, SC_MULTIPLE_CHOICES, SC_NO_CONTENT, SC_NON_AUTHORITATIVE_INFORMATION, SC_NOT_ACCEPTABLE, SC_NOT_FOUND, SC_NOT_IMPLEMENTED, SC_NOT_MODIFIED, SC_OK, SC_PARTIAL_CONTENT, SC_PAYMENT_REQUIRED, SC_PRECONDITION_FAILED, SC_PROXY_AUTHENTICATION_REQUIRED, SC_REQUEST_ENTITY_TOO_LARGE, SC_REQUEST_TIMEOUT, SC_REQUEST_URI_TOO_LONG, SC_REQUESTED_RANGE_NOT_SATISFIABLE, SC_RESET_CONTENT, SC_SEE_OTHER, SC_SERVICE_UNAVAILABLE, SC_SWITCHING_PROTOCOLS, SC_UNAUTHORIZED, SC_UNSUPPORTED_MEDIA_TYPE, SC_USE_PROXY`**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                   | Method and Description                                                                           |
    |-------------------------------------|--------------------------------------------------------------------------------------------------|
    | `void`                              | `addCookie``(javax.servlet.http.Cookie cookie)`<br>Add a cookie                                  |
    | `void`                              | `addDateHeader``(java.lang.String name, long date)`<br>Add header whose value is a date.         |
    | `void`                              | `addHeader``(java.lang.String name, java.lang.String value)`<br>Add header.                      |
    | `void`                              | `addIntHeader``(java.lang.String name, int value)`<br>Add header whose value is an int.          |
    | `void`                              | `close``()`<br>Close this response.                                                              |
    | `boolean`                           | `containsHeader``(java.lang.String name)`<br>Is this header present?                             |
    | `java.lang.String`                  | `encodeRedirectUrl``(java.lang.String url)`<br>Deprecated.                                       |
    | `java.lang.String`                  | `encodeRedirectURL``(java.lang.String url)`<br>Encode URL.                                       |
    | `java.lang.String`                  | `encodeUrl``(java.lang.String url)`<br>Deprecated.                                               |
    | `java.lang.String`                  | `encodeURL``(java.lang.String url)`<br>Encode URL.                                               |
    | `void`                              | `flush``()`<br>Flush the contents.                                                               |
    | `void`                              | `flushBuffer``()`<br>Flush the buffer.                                                           |
    | `int`                               | `getBufferSize``()`<br>Get buffer size.                                                          |
    | `java.lang.String`                  | `getCharacterEncoding``()`<br>Get character encoding.                                            |
    | `java.util.Locale`                  | `getLocale``()`<br>Get locale.                                                                   |
    | `javax.servlet.ServletOutputStream` | `getOutputStream``()`<br>Get output stream.                                                      |
    | `java.io.PrintWriter`               | `getWriter``()`<br>Get print writer                                                              |
    | `boolean`                           | `isCommitted``()`<br>Is this response committed?                                                 |
    | `void`                              | `print``(java.lang.String s)`<br>Print given string to writer.                                   |
    | `void`                              | `println``(java.lang.String s)`<br>Print given string to writer with a newline.                  |
    | `void`                              | `reset``()`<br>Reset this response.                                                              |
    | `void`                              | `sendError``(int sc)`<br>Send error with null message.                                           |
    | `void`                              | `sendError``(int sc, java.lang.String msg)`<br>Send error message.                               |
    | `void`                              | `sendRedirect``(java.lang.String location)`<br>Send redirect to location.                        |
    | `void`                              | `setBufferSize``(int size)`<br>Set buffer size                                                   |
    | `void`                              | `setContentLength``(int len)`<br>Set content length                                              |
    | `void`                              | `setContentType``(java.lang.String type)`<br>Set content type                                    |
    | `void`                              | `setDateHeader``(java.lang.String name, long date)`<br>Set header whose value is a date.         |
    | `void`                              | `setHeader``(java.lang.String name, java.lang.String value)`<br>Set header.                      |
    | `void`                              | `setIntHeader``(java.lang.String name, int value)`<br>Set header whose value is an int.          |
    | `void`                              | `setLocale``(java.util.Locale loc)`<br>Set Locale                                                |
    | `void`                              | `setStatus``(int sc)`<br>Set status code                                                         |
    | `void`                              | `setStatus``(int sc, java.lang.String ms)`<br>Deprecated.                                        |
    | `void`                              | `write``(byte[] b)`<br>Write data                                                                |
    | `void`                              | `write``(byte[] b, int off, int len)`<br>Write data                                              |
    | `void`                              | `write``(int b)`<br>Write data                                                                   |
    | `void`                              | `writeXMLNative``(long xobCState, java.lang.String encoding, short indent)`<br>Write native XML. |

    - ### Methods inherited from class javax.servlet.ServletOutputStream

      `print, print, print, print, print, print, println, println, println, println, println, println, println`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### close

          public void close()
                     throws java.io.IOException

      Close this response.
      Specified by:
      `close` in interface `java.io.Closeable`

      Specified by:
      `close` in interface `java.lang.AutoCloseable`

      Overrides:
      `close` in class `java.io.OutputStream`

      Throws:
      `java.io.IOException` - if there is an error in the IO.

    <!-- -->

    - #### print

          public final void print(java.lang.String s)
                           throws java.io.IOException

      Print given string to writer.
      Overrides:
      `print` in class `javax.servlet.ServletOutputStream`

      Parameters:
      `s` - String to be printed.

      Throws:
      `java.io.IOException` - if there is an IO error.

    <!-- -->

    - #### println

          public void println(java.lang.String s)
                       throws java.io.IOException

      Print given string to writer with a newline.
      Overrides:
      `println` in class `javax.servlet.ServletOutputStream`

      Parameters:
      `s` - String to be printed.

      Throws:
      `java.io.IOException` - if there is an IO error.

    <!-- -->

    - #### write

          public final void write(byte[] b)
                           throws java.io.IOException

      Write data
      Overrides:
      `write` in class `java.io.OutputStream`

      Parameters:
      `b` - The array of bytes to write.

      Throws:
      `java.io.IOException` - if there is an IO error.

    <!-- -->

    - #### write

          public void write(byte[] b,
                            int off,
                            int len)
                     throws java.io.IOException

      Write data
      Overrides:
      `write` in class `java.io.OutputStream`

      Parameters:
      `b` - The array of bytes to write.

      `off` - The offset.

      `len` - The length.

      Throws:
      `java.io.IOException` - if there is an IO error.

    <!-- -->

    - #### writeXMLNative

          public final void writeXMLNative(long xobCState,
                                           java.lang.String encoding,
                                           short indent)
                                    throws java.io.IOException

      Write native XML.
      Specified by:
      [`writeXMLNative`](XDBStream.md) in interface [`XDBStream`](XDBStream.md)

      Parameters:
      `xobCState` - The pointer to the xob in C.

      `encoding` - The character encoding to be used when writing.

      `indent` - The indentation to be used.

      Throws:
      `java.io.IOException` - if there is an IO error.

    <!-- -->

    - #### write

          public final void write(int b)
                           throws java.io.IOException

      Write data
      Specified by:
      `write` in class `java.io.OutputStream`

      Parameters:
      `b` - The number of bytes to write.

      Throws:
      `java.io.IOException` - if there is an IO error.

    <!-- -->

    - #### flush

          public void flush()
                     throws java.io.IOException

      Flush the contents.
      Specified by:
      `flush` in interface `java.io.Flushable`

      Overrides:
      `flush` in class `java.io.OutputStream`

      Throws:
      `java.io.IOException` - if there is an error in the IO.

    <!-- -->

    - #### flushBuffer

          public void flushBuffer()
                           throws java.io.IOException

      Flush the buffer.
      Specified by:
      `flushBuffer` in interface `javax.servlet.ServletResponse`

      Throws:
      `java.io.IOException` - if there is an error in the IO.

    <!-- -->

    - #### getBufferSize

          public final int getBufferSize()

      Get buffer size.
      Specified by:
      `getBufferSize` in interface `javax.servlet.ServletResponse`

    <!-- -->

    - #### getCharacterEncoding

          public final java.lang.String getCharacterEncoding()

      Get character encoding.
      Specified by:
      `getCharacterEncoding` in interface `javax.servlet.ServletResponse`

    <!-- -->

    - #### getLocale

          public final java.util.Locale getLocale()

      Get locale.
      Specified by:
      `getLocale` in interface `javax.servlet.ServletResponse`

    <!-- -->

    - #### getOutputStream

          public final javax.servlet.ServletOutputStream getOutputStream()

      Get output stream.
      Specified by:
      `getOutputStream` in interface `javax.servlet.ServletResponse`

    <!-- -->

    - #### getWriter

          public final java.io.PrintWriter getWriter()
                                              throws java.io.IOException

      Get print writer
      Specified by:
      `getWriter` in interface `javax.servlet.ServletResponse`

      Throws:
      `java.io.IOException` - if there is an error in the IO.

    <!-- -->

    - #### isCommitted

          public boolean isCommitted()

      Is this response committed?
      Specified by:
      `isCommitted` in interface `javax.servlet.ServletResponse`

    <!-- -->

    - #### reset

          public final void reset()

      Reset this response.
      Specified by:
      `reset` in interface `javax.servlet.ServletResponse`

    <!-- -->

    - #### setBufferSize

          public final void setBufferSize(int size)

      Set buffer size
      Specified by:
      `setBufferSize` in interface `javax.servlet.ServletResponse`

      Parameters:
      `size` - new size.

    <!-- -->

    - #### setContentType

          public final void setContentType(java.lang.String type)

      Set content type
      Specified by:
      `setContentType` in interface `javax.servlet.ServletResponse`

      Parameters:
      `type` - the content type

    <!-- -->

    - #### setContentLength

          public final void setContentLength(int len)

      Set content length
      Specified by:
      `setContentLength` in interface `javax.servlet.ServletResponse`

      Parameters:
      `len` - content length

    <!-- -->

    - #### setLocale

          public final void setLocale(java.util.Locale loc)

      Set Locale
      Specified by:
      `setLocale` in interface `javax.servlet.ServletResponse`

      Parameters:
      `loc` - locale

    <!-- -->

    - #### addCookie

          public final void addCookie(javax.servlet.http.Cookie cookie)

      Add a cookie
      Specified by:
      `addCookie` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `cookie` - The cookie to be added.

    <!-- -->

    - #### addHeader

          public final void addHeader(java.lang.String name,
                                      java.lang.String value)

      Add header.
      Specified by:
      `addHeader` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `name` - The name of the header.

      `value` - The value of the header.

    <!-- -->

    - #### addDateHeader

          public final void addDateHeader(java.lang.String name,
                                          long date)

      Add header whose value is a date.
      Specified by:
      `addDateHeader` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `name` - The name of the header.

      `date` - The date value of the header.

    <!-- -->

    - #### addIntHeader

          public final void addIntHeader(java.lang.String name,
                                         int value)

      Add header whose value is an int.
      Specified by:
      `addIntHeader` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `name` - The name of the header.

      `value` - The int value of the header.

    <!-- -->

    - #### containsHeader

          public final boolean containsHeader(java.lang.String name)

      Is this header present?
      Specified by:
      `containsHeader` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `name` - The name of the header.

      Returns:
      true if this header is present, false otherwise.

    <!-- -->

    - #### encodeRedirectUrl

          public final java.lang.String encodeRedirectUrl(java.lang.String url)

      Deprecated. 
      Specified by:
      `encodeRedirectUrl` in interface `javax.servlet.http.HttpServletResponse`

    <!-- -->

    - #### encodeRedirectURL

          public final java.lang.String encodeRedirectURL(java.lang.String url)

      Encode URL.
      Specified by:
      `encodeRedirectURL` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `url` - The URL to be encoded.

      Returns:
      The above parameter as it is.

    <!-- -->

    - #### encodeUrl

          public final java.lang.String encodeUrl(java.lang.String url)

      Deprecated. 
      Specified by:
      `encodeUrl` in interface `javax.servlet.http.HttpServletResponse`

    <!-- -->

    - #### encodeURL

          public final java.lang.String encodeURL(java.lang.String url)

      Encode URL.
      Specified by:
      `encodeURL` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `url` - The URL to be encoded.

      Returns:
      The above parameter as it is.

    <!-- -->

    - #### sendError

          public final void sendError(int sc)

      Send error with null message.
      Specified by:
      `sendError` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `sc` - Status code of the error.

    <!-- -->

    - #### sendError

          public final void sendError(int sc,
                                      java.lang.String msg)

      Send error message.
      Specified by:
      `sendError` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `sc` - Status code of the error.

      `msg` - The error message.

    <!-- -->

    - #### sendRedirect

          public final void sendRedirect(java.lang.String location)
                                  throws java.io.IOException

      Send redirect to location.
      Specified by:
      `sendRedirect` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `location` - The location to which to redirect.

      Throws:
      `java.io.IOException` - if there is an error in the IO.

    <!-- -->

    - #### setDateHeader

          public final void setDateHeader(java.lang.String name,
                                          long date)

      Set header whose value is a date.
      Specified by:
      `setDateHeader` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `name` - The name of the header.

      `date` - The date value of the header.

    <!-- -->

    - #### setHeader

          public final void setHeader(java.lang.String name,
                                      java.lang.String value)

      Set header.
      Specified by:
      `setHeader` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `name` - The name of the header.

      `value` - The value of the header.

    <!-- -->

    - #### setIntHeader

          public final void setIntHeader(java.lang.String name,
                                         int value)

      Set header whose value is an int.
      Specified by:
      `setIntHeader` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `name` - The name of the header.

      `value` - The int value of the header.

    <!-- -->

    - #### setStatus

          public final void setStatus(int sc)

      Set status code
      Specified by:
      `setStatus` in interface `javax.servlet.http.HttpServletResponse`

      Parameters:
      `sc` - status code.

    <!-- -->

    - #### setStatus

          public final void setStatus(int sc,
                                      java.lang.String ms)

      Deprecated. 
      Specified by:
      `setStatus` in interface `javax.servlet.http.HttpServletResponse`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XDBServletRequest.md)**
- **[Next Class](XDBStream.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
