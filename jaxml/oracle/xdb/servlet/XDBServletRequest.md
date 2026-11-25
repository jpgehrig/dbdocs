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

- **[Prev Class](XDBServletContext.md)**
- **[Next Class](XDBServletResponse.md)**

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

## **Class XDBServletRequest**

- **java.lang.Object**

- - **oracle.xdb.servlet.XDBServletRequest**

<!-- -->

- **All Implemented Interfaces:**
  **javax.servlet.http.HttpServletRequest, javax.servlet.ServletRequest**

  ------------------------------------------------------------------------

  **
  **

      public class XDBServletRequest
      extends java.lang.Object
      implements javax.servlet.http.HttpServletRequest

  **Servlet request object. Provides access to the request data parsed by the HTTP server.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XDBServletRequest``()`     |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                  | Method and Description                                                                                |
    |------------------------------------|-------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                 | `getAttribute``(java.lang.String name)`<br>Get the attribute given the name.                          |
    | `java.util.Enumeration`            | `getAttributeNames``()`<br>Get all attribute names.                                                   |
    | `java.lang.String`                 | `getAuthType``()`<br>Native method to get authentication type.                                        |
    | `java.lang.String`                 | `getCharacterEncoding``()`<br>Native method to get character encoding.                                |
    | `int`                              | `getContentLength``()`<br>Native method to get content length.                                        |
    | `java.lang.String`                 | `getContentType``()`<br>Native method to get content type.                                            |
    | `java.lang.String`                 | `getContextPath``()`<br>Native method to get context path.                                            |
    | `javax.servlet.http.Cookie[]`      | `getCookies``()`<br>Get cookies.                                                                      |
    | `long`                             | `getDateHeader``(java.lang.String name)`<br>Native method to get date header.                         |
    | `java.lang.String`                 | `getHeader``(java.lang.String name)`<br>Native method to get header.                                  |
    | `java.util.Enumeration`            | `getHeaderNames``()`<br>Get all header names.                                                         |
    | `java.util.Enumeration`            | `getHeaders``(java.lang.String name)`<br>Get all headers                                              |
    | `javax.servlet.ServletInputStream` | `getInputStream``()`<br>Get an input stream.                                                          |
    | `int`                              | `getIntHeader``(java.lang.String name)`<br>Native method to get int header.                           |
    | `java.util.Locale`                 | `getLocale``()`<br>Get locale.                                                                        |
    | `java.util.Enumeration`            | `getLocales``()`<br>Get all locales.                                                                  |
    | `java.lang.String`                 | `getMethod``()`<br>Native method to get method.                                                       |
    | `java.lang.String`                 | `getParameter``(java.lang.String name)`<br>Native method to get parameter                             |
    | `java.util.Enumeration`            | `getParameterNames``()`<br>Get all parameter names.                                                   |
    | `java.lang.String[]`               | `getParameterValues``(java.lang.String name)`<br>Native method to get parameter values.               |
    | `java.lang.String`                 | `getPathInfo``()`<br>Native method to get path info.                                                  |
    | `java.lang.String`                 | `getPathTranslated``()`<br>Native method to get path translated.                                      |
    | `java.lang.String`                 | `getProtocol``()`<br>Native method to get protocol.                                                   |
    | `java.lang.String`                 | `getQueryString``()`<br>Native method to get query string.                                            |
    | `java.io.BufferedReader`           | `getReader``()`<br>Get a buffered reader over the request stream.                                     |
    | `java.lang.String`                 | `getRealPath``(java.lang.String path)`<br>Deprecated.                                                 |
    | `java.lang.String`                 | `getRemoteAddr``()`<br>Native method to get remote address.                                           |
    | `java.lang.String`                 | `getRemoteHost``()`<br>Native method to get remote host.                                              |
    | `java.lang.String`                 | `getRemoteUser``()`<br>Native method to get remote user.                                              |
    | `javax.servlet.RequestDispatcher`  | `getRequestDispatcher``(java.lang.String path)`<br>Get request dispatcher.                            |
    | `java.lang.String`                 | `getRequestedSessionId``()`<br>Native method to get session id.                                       |
    | `java.lang.String`                 | `getRequestURI``()`<br>Native method to get request URI.                                              |
    | `java.lang.String`                 | `getScheme``()`<br>Native method to get scheme.                                                       |
    | `java.lang.String`                 | `getServerName``()`<br>Native method to get server name.                                              |
    | `int`                              | `getServerPort``()`<br>Native method to get server port.                                              |
    | `java.lang.String`                 | `getServletPath``()`<br>Native method to get servlet path.                                            |
    | `javax.servlet.http.HttpSession`   | `getSession``()`<br>Get HTTP session.                                                                 |
    | `javax.servlet.http.HttpSession`   | `getSession``(boolean create)`<br>Get HTTP session.                                                   |
    | `java.security.Principal`          | `getUserPrincipal``()`<br>Get user's security principal.                                              |
    | `boolean`                          | `isRequestedSessionIdFromCookie``()`<br>Native method to find if requested session id is from cookie. |
    | `boolean`                          | `isRequestedSessionIdFromUrl``()`<br>Deprecated.                                                      |
    | `boolean`                          | `isRequestedSessionIdFromURL``()`<br>Native method to find if requested session id is from URL.       |
    | `boolean`                          | `isRequestedSessionIdValid``()`<br>Is requested session id valid?                                     |
    | `boolean`                          | `isSecure``()`<br>Is this request secure?                                                             |
    | `boolean`                          | `isUserInRole``(java.lang.String role)`<br>Native method to find if user is in given role.            |
    | `void`                             | `removeAttribute``(java.lang.String name)`<br>Remove the given attribute.                             |
    | `void`                             | `setAttribute``(java.lang.String name, java.lang.Object o)`<br>Set attribute for object.              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XDBServletRequest

          public XDBServletRequest()

  <!-- -->

  - ### Method Detail

    - #### getAttribute

          public java.lang.Object getAttribute(java.lang.String name)

      Get the attribute given the name.
      Specified by:
      `getAttribute` in interface `javax.servlet.ServletRequest`

      Parameters:
      `name` - The name.

      Returns:
      The object corresponding to the attribute.

    <!-- -->

    - #### getAttributeNames

          public java.util.Enumeration getAttributeNames()

      Get all attribute names.
      Specified by:
      `getAttributeNames` in interface `javax.servlet.ServletRequest`

      Returns:
      An enumeration containing all the attribute names.

    <!-- -->

    - #### getCharacterEncoding

          public java.lang.String getCharacterEncoding()

      Native method to get character encoding.
      Specified by:
      `getCharacterEncoding` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getContentLength

          public int getContentLength()

      Native method to get content length.
      Specified by:
      `getContentLength` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getContentType

          public java.lang.String getContentType()

      Native method to get content type.
      Specified by:
      `getContentType` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getInputStream

          public javax.servlet.ServletInputStream getInputStream()

      Get an input stream.
      Specified by:
      `getInputStream` in interface `javax.servlet.ServletRequest`

      Returns:
      a servelet input stream.

    <!-- -->

    - #### getLocale

          public java.util.Locale getLocale()

      Get locale.
      Specified by:
      `getLocale` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getLocales

          public java.util.Enumeration getLocales()

      Get all locales.
      Specified by:
      `getLocales` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getParameter

          public java.lang.String getParameter(java.lang.String name)

      Native method to get parameter
      Specified by:
      `getParameter` in interface `javax.servlet.ServletRequest`

      Parameters:
      `name` - The name of the param.

    <!-- -->

    - #### getParameterNames

          public java.util.Enumeration getParameterNames()

      Get all parameter names.
      Specified by:
      `getParameterNames` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getParameterValues

          public java.lang.String[] getParameterValues(java.lang.String name)

      Native method to get parameter values.
      Specified by:
      `getParameterValues` in interface `javax.servlet.ServletRequest`

      Parameters:
      `name` - The name of the param.

    <!-- -->

    - #### getProtocol

          public java.lang.String getProtocol()

      Native method to get protocol.
      Specified by:
      `getProtocol` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getRealPath

          public java.lang.String getRealPath(java.lang.String path)

      Deprecated. 
      Specified by:
      `getRealPath` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getReader

          public java.io.BufferedReader getReader()
                                           throws java.io.IOException

      Get a buffered reader over the request stream.
      Specified by:
      `getReader` in interface `javax.servlet.ServletRequest`

      Throws:
      `java.io.IOException` - if there is an I/O error.

    <!-- -->

    - #### getRemoteAddr

          public java.lang.String getRemoteAddr()

      Native method to get remote address.
      Specified by:
      `getRemoteAddr` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getRemoteHost

          public java.lang.String getRemoteHost()

      Native method to get remote host.
      Specified by:
      `getRemoteHost` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getRequestDispatcher

          public javax.servlet.RequestDispatcher getRequestDispatcher(java.lang.String path)

      Get request dispatcher.
      Specified by:
      `getRequestDispatcher` in interface `javax.servlet.ServletRequest`

      Parameters:
      `path` - The path.

    <!-- -->

    - #### getScheme

          public java.lang.String getScheme()

      Native method to get scheme.
      Specified by:
      `getScheme` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getServerName

          public java.lang.String getServerName()

      Native method to get server name.
      Specified by:
      `getServerName` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### getServerPort

          public int getServerPort()

      Native method to get server port.
      Specified by:
      `getServerPort` in interface `javax.servlet.ServletRequest`

    <!-- -->

    - #### isSecure

          public boolean isSecure()

      Is this request secure?
      Specified by:
      `isSecure` in interface `javax.servlet.ServletRequest`

      Returns:
      true if scheme is https, false otherwise.

    <!-- -->

    - #### removeAttribute

          public void removeAttribute(java.lang.String name)

      Remove the given attribute.
      Specified by:
      `removeAttribute` in interface `javax.servlet.ServletRequest`

      Parameters:
      `name` - Given attribute.

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.Object o)

      Set attribute for object.
      Specified by:
      `setAttribute` in interface `javax.servlet.ServletRequest`

      Parameters:
      `name` - Attribute.

      `o` - Object.

    <!-- -->

    - #### getAuthType

          public java.lang.String getAuthType()

      Native method to get authentication type.
      Specified by:
      `getAuthType` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getContextPath

          public java.lang.String getContextPath()

      Native method to get context path.
      Specified by:
      `getContextPath` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getCookies

          public javax.servlet.http.Cookie[] getCookies()

      Get cookies.
      Specified by:
      `getCookies` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getDateHeader

          public long getDateHeader(java.lang.String name)

      Native method to get date header.
      Specified by:
      `getDateHeader` in interface `javax.servlet.http.HttpServletRequest`

      Parameters:
      `name` - The name.

    <!-- -->

    - #### getHeader

          public java.lang.String getHeader(java.lang.String name)

      Native method to get header.
      Specified by:
      `getHeader` in interface `javax.servlet.http.HttpServletRequest`

      Parameters:
      `name` - The name.

    <!-- -->

    - #### getHeaderNames

          public java.util.Enumeration getHeaderNames()

      Get all header names.
      Specified by:
      `getHeaderNames` in interface `javax.servlet.http.HttpServletRequest`

      Returns:
      An enumeration containing all the header names.

    <!-- -->

    - #### getHeaders

          public java.util.Enumeration getHeaders(java.lang.String name)

      Get all headers
      Specified by:
      `getHeaders` in interface `javax.servlet.http.HttpServletRequest`

      Returns:
      An enumeration containing all the headers.

    <!-- -->

    - #### getIntHeader

          public int getIntHeader(java.lang.String name)

      Native method to get int header.
      Specified by:
      `getIntHeader` in interface `javax.servlet.http.HttpServletRequest`

      Parameters:
      `name` - The name.

    <!-- -->

    - #### getMethod

          public java.lang.String getMethod()

      Native method to get method.
      Specified by:
      `getMethod` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getPathInfo

          public java.lang.String getPathInfo()

      Native method to get path info.
      Specified by:
      `getPathInfo` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getPathTranslated

          public java.lang.String getPathTranslated()

      Native method to get path translated.
      Specified by:
      `getPathTranslated` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getQueryString

          public java.lang.String getQueryString()

      Native method to get query string.
      Specified by:
      `getQueryString` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getRemoteUser

          public java.lang.String getRemoteUser()

      Native method to get remote user.
      Specified by:
      `getRemoteUser` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getRequestedSessionId

          public java.lang.String getRequestedSessionId()

      Native method to get session id.
      Specified by:
      `getRequestedSessionId` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getRequestURI

          public java.lang.String getRequestURI()

      Native method to get request URI.
      Specified by:
      `getRequestURI` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getServletPath

          public java.lang.String getServletPath()

      Native method to get servlet path.
      Specified by:
      `getServletPath` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getSession

          public javax.servlet.http.HttpSession getSession()

      Get HTTP session. Returns null.
      Specified by:
      `getSession` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### getSession

          public javax.servlet.http.HttpSession getSession(boolean create)

      Get HTTP session. Returns null.
      Specified by:
      `getSession` in interface `javax.servlet.http.HttpServletRequest`

      Parameters:
      `create` - not used.

    <!-- -->

    - #### getUserPrincipal

          public java.security.Principal getUserPrincipal()

      Get user's security principal.
      Specified by:
      `getUserPrincipal` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### isRequestedSessionIdFromCookie

          public boolean isRequestedSessionIdFromCookie()

      Native method to find if requested session id is from cookie.
      Specified by:
      `isRequestedSessionIdFromCookie` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### isRequestedSessionIdFromUrl

          public boolean isRequestedSessionIdFromUrl()

      Deprecated. 
      Specified by:
      `isRequestedSessionIdFromUrl` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### isRequestedSessionIdFromURL

          public boolean isRequestedSessionIdFromURL()

      Native method to find if requested session id is from URL.
      Specified by:
      `isRequestedSessionIdFromURL` in interface `javax.servlet.http.HttpServletRequest`

    <!-- -->

    - #### isRequestedSessionIdValid

          public boolean isRequestedSessionIdValid()

      Is requested session id valid?
      Specified by:
      `isRequestedSessionIdValid` in interface `javax.servlet.http.HttpServletRequest`

      Returns:
      true always.

    <!-- -->

    - #### isUserInRole

          public boolean isUserInRole(java.lang.String role)

      Native method to find if user is in given role.
      Specified by:
      `isUserInRole` in interface `javax.servlet.http.HttpServletRequest`

      Parameters:
      `role` - The given role.

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

- **[Prev Class](XDBServletContext.md)**
- **[Next Class](XDBServletResponse.md)**

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
