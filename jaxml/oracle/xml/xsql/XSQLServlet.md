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

- **[Prev Class](XSQLRequestObjectListener.md)**
- **[Next Class](XSQLServletPageRequest.md)**

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

**oracle.xml.xsql**

## **Class XSQLServlet**

- **java.lang.Object**

- - **javax.servlet.GenericServlet**

  - - **javax.servlet.http.HttpServlet**

    - - **oracle.xml.xsql.XSQLServlet**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, javax.servlet.Servlet, javax.servlet.ServletConfig**

  ------------------------------------------------------------------------

  **
  **

      public final class XSQLServlet
      extends javax.servlet.http.HttpServlet

  **Servlet to enable HTTP GET-ing of and POST-ing to XSQL Pages**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XSQLServlet``()`           |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                      |
    |--------------------|-------------------------------------------------------------------------------------------------------------|
    | `void`             | `destroy``()`                                                                                               |
    | `void`             | `doGet``(javax.servlet.http.HttpServletRequest request, javax.servlet.http.HttpServletResponse response)`   |
    | `void`             | `doPost``(javax.servlet.http.HttpServletRequest request, javax.servlet.http.HttpServletResponse response)`  |
    | `java.lang.String` | `getServletInfo``()`                                                                                        |
    | `void`             | `init``(javax.servlet.ServletConfig config)`                                                                |
    | `static boolean`   | `inJServ``()`                                                                                               |

    - ### Methods inherited from class javax.servlet.http.HttpServlet

      `service`

    <!-- -->

    - ### Methods inherited from class javax.servlet.GenericServlet

      `getInitParameter, getInitParameterNames, getServletConfig, getServletContext, getServletName, init, log, log`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSQLServlet

          public XSQLServlet()

  <!-- -->

  - ### Method Detail

    - #### init

          public void init(javax.servlet.ServletConfig config)
                    throws javax.servlet.ServletException

      Specified by:
      `init` in interface `javax.servlet.Servlet`

      Overrides:
      `init` in class `javax.servlet.GenericServlet`

      Throws:
      `javax.servlet.ServletException`

    <!-- -->

    - #### inJServ

          public static boolean inJServ()

    <!-- -->

    - #### doGet

          public void doGet(javax.servlet.http.HttpServletRequest request,
                            javax.servlet.http.HttpServletResponse response)
                     throws javax.servlet.ServletException,
                            java.io.IOException

      Overrides:
      `doGet` in class `javax.servlet.http.HttpServlet`

      Throws:
      `javax.servlet.ServletException`

      `java.io.IOException`

    <!-- -->

    - #### doPost

          public void doPost(javax.servlet.http.HttpServletRequest request,
                             javax.servlet.http.HttpServletResponse response)
                      throws javax.servlet.ServletException,
                             java.io.IOException

      Overrides:
      `doPost` in class `javax.servlet.http.HttpServlet`

      Throws:
      `javax.servlet.ServletException`

      `java.io.IOException`

    <!-- -->

    - #### getServletInfo

          public java.lang.String getServletInfo()

      Specified by:
      `getServletInfo` in interface `javax.servlet.Servlet`

      Overrides:
      `getServletInfo` in class `javax.servlet.GenericServlet`

    <!-- -->

    - #### destroy

          public void destroy()

      Specified by:
      `destroy` in interface `javax.servlet.Servlet`

      Overrides:
      `destroy` in class `javax.servlet.GenericServlet`

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

- **[Prev Class](XSQLRequestObjectListener.md)**
- **[Next Class](XSQLServletPageRequest.md)**

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
