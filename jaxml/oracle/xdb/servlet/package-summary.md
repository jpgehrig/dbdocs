Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../event/package-summary.md)**
- **[Next Package](../../xml/async/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

# **Package oracle.xdb.servlet**

**This package is the Oracle XML DB implementation of Java Servlet API - Version 2.2, with the following exceptions: All servlets must be distributable.**

**See: Description**

- **Interface Summary**

  | Interface                 | Description                                |
  |---------------------------|--------------------------------------------|
  | [XDBStream](XDBStream.md) | Interface for supporting native streaming. |

- **Class Summary**

  | Class                                         | Description                                                                         |
  |-----------------------------------------------|-------------------------------------------------------------------------------------|
  | [XDBCookie](XDBCookie.md)                     | XDB cookie accessor class.                                                          |
  | [XDBPrincipal](XDBPrincipal.md)               | Implementation of java.security.principal for database user.                        |
  | [XDBServletConfig](XDBServletConfig.md)       | Servlet configuration parameters (from the XML configuration resource)              |
  | [XDBServletContainer](XDBServletContainer.md) | XDB Servlet Container, called by the native HTTP server to handle servlet requests. |
  | [XDBServletContext](XDBServletContext.md)     | Servlet context for the current servlet.                                            |
  | [XDBServletRequest](XDBServletRequest.md)     | Servlet request object.                                                             |
  | [XDBServletResponse](XDBServletResponse.md)   | Servlet response object, providing access to the HTTP response.                     |

## **Package oracle.xdb.servlet Description**

**This package is the Oracle XML DB implementation of Java Servlet API - Version 2.2, with the following exceptions:**

- **All servlets must be distributable. They must expect to run in different VMs.**
- **WAR and web.xml files are not supported. Oracle XML DB supports a subset of the XML configurations in this file. An XSL style sheet can be applied to the web.xml to generate servlet definitions. An external tool must be used to create database roles for those defined in the web.xml file.**
- **JSP (Java Server Pages) support can be installed as a servlet and configured manually.**
- **HTTPSession and related classes are not supported.**
- **Only one servlet context (that is, one Web application) is supported.**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **Package**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../event/package-summary.md)**
- **[Next Package](../../xml/async/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
