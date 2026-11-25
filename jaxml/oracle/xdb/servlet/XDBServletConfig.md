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

- **[Prev Class](XDBPrincipal.md)**
- **[Next Class](XDBServletContainer.md)**

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

## **Class XDBServletConfig**

- **java.lang.Object**

- - **oracle.xdb.servlet.XDBServletConfig**

<!-- -->

- **All Implemented Interfaces:**
  **javax.servlet.ServletConfig**

  ------------------------------------------------------------------------

  **
  **

      public class XDBServletConfig
      extends java.lang.Object
      implements javax.servlet.ServletConfig

  **Servlet configuration parameters (from the XML configuration resource)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type              | Method and Description                                                                  |
    |--------------------------------|-----------------------------------------------------------------------------------------|
    | `java.lang.String[]`           | `get_paramnames``()`<br>Native method to get parameter names.                           |
    | `java.lang.String`             | `getInitParameter``(java.lang.String name)`<br>Native method to get the init parameter. |
    | `java.util.Enumeration`        | `getInitParameterNames``()`<br>Returns an enumeration of the param names.               |
    | `javax.servlet.ServletContext` | `getServletContext``()`<br>Return the servlet context.                                  |
    | `java.lang.String`             | `getServletName``()`<br>Return the name of this servlet.                                |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getInitParameter

          public java.lang.String getInitParameter(java.lang.String name)

      Native method to get the init parameter.
      Specified by:
      `getInitParameter` in interface `javax.servlet.ServletConfig`

      Parameters:
      `name` - The name.

      Returns:
      The init parameter.

    <!-- -->

    - #### get_paramnames

          public java.lang.String[] get_paramnames()

      Native method to get parameter names.
      Returns:
      an array of strings containing the parameter names.

    <!-- -->

    - #### getInitParameterNames

          public java.util.Enumeration getInitParameterNames()

      Returns an enumeration of the param names.
      Specified by:
      `getInitParameterNames` in interface `javax.servlet.ServletConfig`

      Returns:
      an enumeration of the param names.

    <!-- -->

    - #### getServletContext

          public javax.servlet.ServletContext getServletContext()

      Return the servlet context. If the servlet context is null, create a new one.
      Specified by:
      `getServletContext` in interface `javax.servlet.ServletConfig`

      Returns:
      as above.

    <!-- -->

    - #### getServletName

          public java.lang.String getServletName()

      Return the name of this servlet.
      Specified by:
      `getServletName` in interface `javax.servlet.ServletConfig`

      Returns:
      as above.

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

- **[Prev Class](XDBPrincipal.md)**
- **[Next Class](XDBServletContainer.md)**

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
