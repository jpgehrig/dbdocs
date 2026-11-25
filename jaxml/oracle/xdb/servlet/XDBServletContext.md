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

- **[Prev Class](XDBServletContainer.md)**
- **[Next Class](XDBServletRequest.md)**

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

## **Class XDBServletContext**

- **java.lang.Object**

- - **oracle.xdb.servlet.XDBServletContext**

<!-- -->

- **All Implemented Interfaces:**
  **javax.servlet.ServletContext**

  ------------------------------------------------------------------------

  **
  **

      public class XDBServletContext
      extends java.lang.Object
      implements javax.servlet.ServletContext

  **Servlet context for the current servlet.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                 | Method and Description                                                                                             |
    |-----------------------------------|--------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                | `getAttribute``(java.lang.String name)`<br>Get the attribute given the name.                                       |
    | `java.util.Enumeration`           | `getAttributeNames``()`<br>Get all attribute names.                                                                |
    | `javax.servlet.ServletContext`    | `getContext``(java.lang.String uripath)`<br>Get the Servlet Context.                                               |
    | `java.lang.String`                | `getInitParameter``(java.lang.String name)`<br>Get init parameter.                                                 |
    | `java.util.Enumeration`           | `getInitParameterNames``()`<br>Get all init parameter names.                                                       |
    | `int`                             | `getMajorVersion``()`<br>Get the major version.                                                                    |
    | `java.lang.String`                | `getMimeType``(java.lang.String file)`<br>Native method to get the mime type.                                      |
    | `int`                             | `getMinorVersion``()`<br>Get the minor version.                                                                    |
    | `javax.servlet.RequestDispatcher` | `getNamedDispatcher``(java.lang.String servletName)`<br>Get named dispatcher.                                      |
    | `java.lang.String`                | `getRealPath``(java.lang.String path)`<br>Get real path.                                                           |
    | `javax.servlet.RequestDispatcher` | `getRequestDispatcher``(java.lang.String path)`<br>Get request dispatcher.                                         |
    | `java.net.URL`                    | `getResource``(java.lang.String path)`<br>Get resource URL given the path.                                         |
    | `java.io.InputStream`             | `getResourceAsStream``(java.lang.String path)`<br>Get resource as an input stream given the path.                  |
    | `java.lang.String`                | `getServerInfo``()`<br>Native method to get the server info.                                                       |
    | `javax.servlet.Servlet`           | `getServlet``(java.lang.String name)`<br>Deprecated.                                                               |
    | `java.util.Enumeration`           | `getServletNames``()`<br>Deprecated.                                                                               |
    | `java.util.Enumeration`           | `getServlets``()`<br>Deprecated.                                                                                   |
    | `void`                            | `log``(java.lang.Exception e, java.lang.String msg)`<br>Deprecated.                                                |
    | `void`                            | `log``(java.lang.String msg)`<br>Log a message to system.out                                                       |
    | `void`                            | `log``(java.lang.String msg, java.lang.Throwable t)`<br>Log the given message to system.out and print stack trace. |
    | `void`                            | `removeAttribute``(java.lang.String name)`<br>Remove the given attribute.                                          |
    | `void`                            | `setAttribute``(java.lang.String name, java.lang.Object o)`<br>Set attribute for object.                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getMimeType

          public java.lang.String getMimeType(java.lang.String file)

      Native method to get the mime type.
      Specified by:
      `getMimeType` in interface `javax.servlet.ServletContext`

      Parameters:
      `file` - The file name.

      Returns:
      The mime type.

    <!-- -->

    - #### getServerInfo

          public java.lang.String getServerInfo()

      Native method to get the server info.
      Specified by:
      `getServerInfo` in interface `javax.servlet.ServletContext`

      Returns:
      Server Info.

    <!-- -->

    - #### getAttribute

          public java.lang.Object getAttribute(java.lang.String name)

      Get the attribute given the name.
      Specified by:
      `getAttribute` in interface `javax.servlet.ServletContext`

      Parameters:
      `name` - The name.

      Returns:
      The object corresponding to the attribute.

    <!-- -->

    - #### getAttributeNames

          public java.util.Enumeration getAttributeNames()

      Get all attribute names.
      Specified by:
      `getAttributeNames` in interface `javax.servlet.ServletContext`

      Returns:
      An enumeration containing all the attribute names.

    <!-- -->

    - #### getContext

          public javax.servlet.ServletContext getContext(java.lang.String uripath)

      Get the Servlet Context.
      Specified by:
      `getContext` in interface `javax.servlet.ServletContext`

      Parameters:
      `uripath` - The URI path.

      Returns:
      This servlet context.

    <!-- -->

    - #### getInitParameter

          public java.lang.String getInitParameter(java.lang.String name)

      Get init parameter.
      Specified by:
      `getInitParameter` in interface `javax.servlet.ServletContext`

      Parameters:
      `name` - The name of the parameter.

      Returns:
      Null.

    <!-- -->

    - #### getNamedDispatcher

          public javax.servlet.RequestDispatcher getNamedDispatcher(java.lang.String servletName)

      Get named dispatcher.
      Specified by:
      `getNamedDispatcher` in interface `javax.servlet.ServletContext`

      Parameters:
      `servletName` - The name of the servlet.

      Returns:
      Null

    <!-- -->

    - #### getInitParameterNames

          public java.util.Enumeration getInitParameterNames()

      Get all init parameter names.
      Specified by:
      `getInitParameterNames` in interface `javax.servlet.ServletContext`

      Returns:
      The parameter names.

    <!-- -->

    - #### getMajorVersion

          public int getMajorVersion()

      Get the major version.
      Specified by:
      `getMajorVersion` in interface `javax.servlet.ServletContext`

      Returns:
      The major version (2).

    <!-- -->

    - #### getMinorVersion

          public int getMinorVersion()

      Get the minor version.
      Specified by:
      `getMinorVersion` in interface `javax.servlet.ServletContext`

      Returns:
      The minor version (2).

    <!-- -->

    - #### getRealPath

          public java.lang.String getRealPath(java.lang.String path)

      Get real path.
      Specified by:
      `getRealPath` in interface `javax.servlet.ServletContext`

      Parameters:
      `path` - The path.

      Returns:
      The same path as specified in the above parameter.

    <!-- -->

    - #### getRequestDispatcher

          public javax.servlet.RequestDispatcher getRequestDispatcher(java.lang.String path)

      Get request dispatcher.
      Specified by:
      `getRequestDispatcher` in interface `javax.servlet.ServletContext`

      Parameters:
      `path` - The path.

      Returns:
      Null.

    <!-- -->

    - #### getResource

          public java.net.URL getResource(java.lang.String path)
                                   throws java.net.MalformedURLException

      Get resource URL given the path.
      Specified by:
      `getResource` in interface `javax.servlet.ServletContext`

      Parameters:
      `path` - The path.

      Returns:
      The resource URL.

      Throws:
      `MalformedURLException` - If the URL is malformed.

    <!-- -->

    - #### getResourceAsStream

          public java.io.InputStream getResourceAsStream(java.lang.String path)

      Get resource as an input stream given the path.
      Specified by:
      `getResourceAsStream` in interface `javax.servlet.ServletContext`

      Parameters:
      `path` - The path.

      Returns:
      The resource as an InputStream.

    <!-- -->

    - #### getServlet

          public javax.servlet.Servlet getServlet(java.lang.String name)

      Deprecated. 
      Specified by:
      `getServlet` in interface `javax.servlet.ServletContext`

    <!-- -->

    - #### getServletNames

          public java.util.Enumeration getServletNames()

      Deprecated. 
      Specified by:
      `getServletNames` in interface `javax.servlet.ServletContext`

    <!-- -->

    - #### getServlets

          public java.util.Enumeration getServlets()

      Deprecated. 
      Specified by:
      `getServlets` in interface `javax.servlet.ServletContext`

    <!-- -->

    - #### log

          public void log(java.lang.Exception e,
                          java.lang.String msg)

      Deprecated. 
      Specified by:
      `log` in interface `javax.servlet.ServletContext`

    <!-- -->

    - #### log

          public void log(java.lang.String msg)

      Log a message to system.out
      Specified by:
      `log` in interface `javax.servlet.ServletContext`

      Parameters:
      `msg` - The message.

    <!-- -->

    - #### log

          public void log(java.lang.String msg,
                          java.lang.Throwable t)

      Log the given message to system.out and print stack trace.
      Specified by:
      `log` in interface `javax.servlet.ServletContext`

      Parameters:
      `msg` - The message.

      `t` - The throwable object whose stack trace is to be printed.

    <!-- -->

    - #### removeAttribute

          public void removeAttribute(java.lang.String name)

      Remove the given attribute.
      Specified by:
      `removeAttribute` in interface `javax.servlet.ServletContext`

      Parameters:
      `name` - Given attribute.

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.Object o)

      Set attribute for object.
      Specified by:
      `setAttribute` in interface `javax.servlet.ServletContext`

      Parameters:
      `name` - Attribute.

      `o` - Object.

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

- **[Prev Class](XDBServletContainer.md)**
- **[Next Class](XDBServletRequest.md)**

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
