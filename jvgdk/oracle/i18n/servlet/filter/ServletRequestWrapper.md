Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](ServletFilter.md)
- [Next Class](ServletResponseWrapper.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.i18n.servlet.filter

## Class ServletRequestWrapper

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [javax.servlet.ServletRequestWrapper](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true)

  - - [javax.servlet.http.HttpServletRequestWrapper](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true)

    - - oracle.i18n.servlet.filter.ServletRequestWrapper

<!-- -->

- All Implemented Interfaces:
  [HttpServletRequest](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true), [ServletRequest](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true)

  ------------------------------------------------------------------------



      public class ServletRequestWrapper
      extends HttpServletRequestWrapper

  The `ServletRequestWrapper` class is an HTTP request class that detects the current user locale and makes it available for the application.
  Since:
  10.1.0.2

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.servlet.http.[HttpServletRequest](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true)

      [`BASIC_AUTH`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true#BASIC_AUTH)`, `[`CLIENT_CERT_AUTH`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true#CLIENT_CERT_AUTH)`, `[`DIGEST_AUTH`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true#DIGEST_AUTH)`, `[`FORM_AUTH`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true#FORM_AUTH)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ServletRequestWrapper``(`[`HttpServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true)` request)`<br>Constructs a ServletRequestWrapper object for the GDK framework. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                     | Method and Description                                                                                                                                                                                                                                                         |
    |-------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)           | `getCharacterEncoding``()`<br>Returns the name of the character encoding used in the body of this request, or returns `null` if the request does not specify character encoding.                                                                                               |
    | [`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)           | `getLocale``()`<br>Returns the current locale derived from the locale detection mechanism.                                                                                                                                                                                     |
    | [`Enumeration`](http://docs.oracle.com/javase/8/docs/api/java/util/Enumeration.html?is-external=true) | `getLocales``()`<br>Returns the `Enumeration` object that includes the current locales derived from the locale detection mechanism.                                                                                                                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)           | `getParameter``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>Returns the parameter value corresponding to the key.                                                                                                   |
    | [`Map`](http://docs.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)                 | `getParameterMap``()`<br>Returns a `java.util.Map` object of the parameters of this request.                                                                                                                                                                                   |
    | [`Enumeration`](http://docs.oracle.com/javase/8/docs/api/java/util/Enumeration.html?is-external=true) | `getParameterNames``()`<br>Returns an `Enumeration` of `String` objects containing the names of the parameters in this request.                                                                                                                                                |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`       | `getParameterValues``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>Returns an array of `String` objects containing all the values of the given request parameter, or returns `null` if the parameter does not exist. |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)           | `getRawParameter``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>Returns the raw value of the parameter corresponding to the key.                                                                                     |
    | `void`                                                                                                | `setCharacterEncoding``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` env)`<br>Sets the character set of the input stream.                                                                                                     |

    - ### Methods inherited from class javax.servlet.http.[HttpServletRequestWrapper](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true)

      [`getAuthType`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getAuthType--)`, `[`getContextPath`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getContextPath--)`, `[`getCookies`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getCookies--)`, `[`getDateHeader`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getDateHeader-java.lang.String-)`, `[`getHeader`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getHeader-java.lang.String-)`, `[`getHeaderNames`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getHeaderNames--)`, `[`getHeaders`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getHeaders-java.lang.String-)`, `[`getIntHeader`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getIntHeader-java.lang.String-)`, `[`getMethod`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getMethod--)`, `[`getPathInfo`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getPathInfo--)`, `[`getPathTranslated`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getPathTranslated--)`, `[`getQueryString`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getQueryString--)`, `[`getRemoteUser`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getRemoteUser--)`, `[`getRequestedSessionId`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getRequestedSessionId--)`, `[`getRequestURI`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getRequestURI--)`, `[`getRequestURL`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getRequestURL--)`, `[`getServletPath`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getServletPath--)`, `[`getSession`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getSession--)`, `[`getSession`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getSession-boolean-)`, `[`getUserPrincipal`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#getUserPrincipal--)`, `[`isRequestedSessionIdFromCookie`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#isRequestedSessionIdFromCookie--)`, `[`isRequestedSessionIdFromUrl`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#isRequestedSessionIdFromUrl--)`, `[`isRequestedSessionIdFromURL`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#isRequestedSessionIdFromURL--)`, `[`isRequestedSessionIdValid`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#isRequestedSessionIdValid--)`, `[`isUserInRole`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true#isUserInRole-java.lang.String-)

    <!-- -->

    - ### Methods inherited from class javax.servlet.[ServletRequestWrapper](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true)

      [`getAttribute`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getAttribute-java.lang.String-)`, `[`getAttributeNames`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getAttributeNames--)`, `[`getContentLength`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getContentLength--)`, `[`getContentType`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getContentType--)`, `[`getInputStream`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getInputStream--)`, `[`getProtocol`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getProtocol--)`, `[`getReader`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getReader--)`, `[`getRealPath`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getRealPath-java.lang.String-)`, `[`getRemoteAddr`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getRemoteAddr--)`, `[`getRemoteHost`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getRemoteHost--)`, `[`getRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getRequest--)`, `[`getRequestDispatcher`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getRequestDispatcher-java.lang.String-)`, `[`getScheme`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getScheme--)`, `[`getServerName`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getServerName--)`, `[`getServerPort`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getServerPort--)`, `[`isSecure`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#isSecure--)`, `[`removeAttribute`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#removeAttribute-java.lang.String-)`, `[`setAttribute`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#setAttribute-java.lang.String-java.lang.Object-)`, `[`setRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#setRequest-javax.servlet.ServletRequest-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

    <!-- -->

    - ### Methods inherited from interface javax.servlet.[ServletRequest](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true)

      [`getAttribute`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getAttribute-java.lang.String-)`, `[`getAttributeNames`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getAttributeNames--)`, `[`getContentLength`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getContentLength--)`, `[`getContentType`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getContentType--)`, `[`getInputStream`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getInputStream--)`, `[`getProtocol`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getProtocol--)`, `[`getReader`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getReader--)`, `[`getRealPath`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getRealPath-java.lang.String-)`, `[`getRemoteAddr`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getRemoteAddr--)`, `[`getRemoteHost`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getRemoteHost--)`, `[`getRequestDispatcher`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getRequestDispatcher-java.lang.String-)`, `[`getScheme`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getScheme--)`, `[`getServerName`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getServerName--)`, `[`getServerPort`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getServerPort--)`, `[`isSecure`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#isSecure--)`, `[`removeAttribute`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#removeAttribute-java.lang.String-)`, `[`setAttribute`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#setAttribute-java.lang.String-java.lang.Object-)

<!-- -->

- - ### Constructor Detail

    - #### ServletRequestWrapper

          public ServletRequestWrapper(HttpServletRequest request)
                                throws IOException

      Constructs a ServletRequestWrapper object for the GDK framework.
      Parameters:
      `request` - a default `HttpServletRequest` object

      Throws:
      [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if I/O exception occurs

  <!-- -->

  - ### Method Detail

    - #### getLocale

          public Locale getLocale()

      Returns the current locale derived from the locale detection mechanism.
      Specified by:
      [`getLocale`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getLocale--) in interface [`ServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true)

      Overrides:
      [`getLocale`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getLocale--) in class [`ServletRequestWrapper`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true)

      Returns:
      `Locale` object

    <!-- -->

    - #### getLocales

          public Enumeration getLocales()

      Returns the `Enumeration` object that includes the current locales derived from the locale detection mechanism.
      Specified by:
      [`getLocales`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getLocales--) in interface [`ServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true)

      Overrides:
      [`getLocales`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getLocales--) in class [`ServletRequestWrapper`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true)

      Returns:
      `Enumeration` object

    <!-- -->

    - #### getCharacterEncoding

          public String getCharacterEncoding()

      Returns the name of the character encoding used in the body of this request, or returns `null` if the request does not specify character encoding.
      Specified by:
      [`getCharacterEncoding`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getCharacterEncoding--) in interface [`ServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true)

      Overrides:
      [`getCharacterEncoding`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getCharacterEncoding--) in class [`ServletRequestWrapper`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true)

      Returns:
      a `String` containing the name of the character encoding, or returns `null` if the request does not specify character encoding

    <!-- -->

    - #### getRawParameter

          public String getRawParameter(String key)

      Returns the raw value of the parameter corresponding to the key. This method does not perform character set conversion on the returned parameter.
      Parameters:
      `key` - the key string

      Returns:
      a `String` value corresponding to the `key`

    <!-- -->

    - #### getParameter

          public String getParameter(String key)

      Returns the parameter value corresponding to the key.
      Specified by:
      [`getParameter`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getParameter-java.lang.String-) in interface [`ServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true)

      Overrides:
      [`getParameter`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getParameter-java.lang.String-) in class [`ServletRequestWrapper`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true)

      Parameters:
      `key` - the key string

      Returns:
      a `String` value corresponding to the `key`

    <!-- -->

    - #### getParameterValues

          public String[] getParameterValues(String key)

      Returns an array of `String` objects containing all the values of the given request parameter, or returns `null` if the parameter does not exist.
      Specified by:
      [`getParameterValues`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getParameterValues-java.lang.String-) in interface [`ServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true)

      Overrides:
      [`getParameterValues`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getParameterValues-java.lang.String-) in class [`ServletRequestWrapper`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true)

      Parameters:
      `key` - a parameter name

      Returns:
      an array of `String` objects containing the parameter values corresponding to the `key`

    <!-- -->

    - #### getParameterMap

          public Map getParameterMap()

      Returns a `java.util.Map` object of the parameters of this request. For HTTP servlets, parameters are contained in the query string or posted form data.
      Specified by:
      [`getParameterMap`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getParameterMap--) in interface [`ServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true)

      Overrides:
      [`getParameterMap`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getParameterMap--) in class [`ServletRequestWrapper`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true)

      Returns:
      a `java.util.Map` object containing parameter names as keys and parameter values as map values

    <!-- -->

    - #### getParameterNames

          public Enumeration getParameterNames()

      Returns an `Enumeration` of `String` objects containing the names of the parameters in this request. If the request has no parameters, the method returns an empty `Enumeration` object.
      Specified by:
      [`getParameterNames`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#getParameterNames--) in interface [`ServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true)

      Overrides:
      [`getParameterNames`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#getParameterNames--) in class [`ServletRequestWrapper`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true)

      Returns:
      a `java.util.Enumeration` object containing parameter names

    <!-- -->

    - #### setCharacterEncoding

          public void setCharacterEncoding(String env)
                                    throws UnsupportedEncodingException

      Sets the character set of the input stream. By default, GDK determines the input character set based on the application configuration file. Use this method only if it is necessary to explicitly specify the character set.
      Specified by:
      [`setCharacterEncoding`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true#setCharacterEncoding-java.lang.String-) in interface [`ServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true)

      Overrides:
      [`setCharacterEncoding`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true#setCharacterEncoding-java.lang.String-) in class [`ServletRequestWrapper`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true)

      Parameters:
      `env` - an IANA character set name

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the given character set name is invalid

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](ServletFilter.md)
- [Next Class](ServletResponseWrapper.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
