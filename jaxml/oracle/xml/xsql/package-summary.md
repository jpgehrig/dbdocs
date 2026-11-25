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

- **[Prev Package](../xquery/xqjdb/package-summary.md)**
- **[Next Package](../../../org/w3c/dom/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

# **Package oracle.xml.xsql**

**Provides APIs for Oracle XSQL Pages and XSQL Servlet.**

**See: Description**

- **Interface Summary**

  | Interface                                                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
  |-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [XSQLActionHandler](XSQLActionHandler.md)                       | Interface that must be implemented by all XSQL Action Element Handlers Upon encountering an XSQL Action Element of the form \<xsql:xxxx\> in an XSQL page, the XSQL Page Processor invokes the associated XSQL Action Handler by: Constructing an instance of the handler using the no-args constructor Invoking the XSQL Action Handler's init() method Invoking the XSQL Action Handler's handleAction() method **NOTE**: conn parameter can be null if no connection specified for the XSQL page being processed. |
  | [XSQLConnectionManager](XSQLConnectionManager.md)               | One of two interfaces that must be implemented to override the built-in connection manager implementation.                                                                                                                                                                                                                                                                                                                                                                                                           |
  | [XSQLConnectionManagerFactory](XSQLConnectionManagerFactory.md) | One of two interfaces that must be implemented to override the built-in connection manager implementation.                                                                                                                                                                                                                                                                                                                                                                                                           |
  | [XSQLDocumentSerializer](XSQLDocumentSerializer.md)             | Interface that must be implemented by all XSQL Serializers which serialize an XSQL data page as an XML Document to a PrintWriter.                                                                                                                                                                                                                                                                                                                                                                                    |
  | [XSQLErrorHandler](XSQLErrorHandler.md)                         | Any custom XSQL Error Handler must implement this interface in order to perform custom processing when an XSQL page processing engine fatal error occurs.                                                                                                                                                                                                                                                                                                                                                            |
  | [XSQLLogger](XSQLLogger.md)                                     | One of two interfaces that must be implemented to provide a custom logging implementation.                                                                                                                                                                                                                                                                                                                                                                                                                           |
  | [XSQLLoggerFactory](XSQLLoggerFactory.md)                       | One of two interfaces that must be implemented to provide a custom logging implementation.                                                                                                                                                                                                                                                                                                                                                                                                                           |
  | [XSQLPageRequest](XSQLPageRequest.md)                           | Interface representing a request for an XSQL Page                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
  | [XSQLRequestObjectListener](XSQLRequestObjectListener.md)       | Objects that implement this interface and which are added to the current request context using setRequestObject() will be notified when the page processing of the outermost page is completed.                                                                                                                                                                                                                                                                                                                      |

- **Class Summary**

  | Class                                                                 | Description                                                                                                                                         |
  |-----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
  | [XSQLActionHandlerImpl](XSQLActionHandlerImpl.md)                     | Base Implementation of XSQLActionHandler that can be extended to create your own custom handlers.                                                   |
  | [XSQLCommandLine](XSQLCommandLine.md)                                 | Command-line Utility to process XSQL Pages.                                                                                                         |
  | [XSQLConnection](XSQLConnection.md)                                   |                                                                                                                                                     |
  | [XSQLDatasourceConnectionManager](XSQLDatasourceConnectionManager.md) | Generic implementation of XSQLConnectionManager that uses JNDI to lookup a JDBC datasource from the container in which the XSQL servlet is running. |
  | [XSQLDiagnostic](XSQLDiagnostic.md)                                   |                                                                                                                                                     |
  | [XSQLError](XSQLError.md)                                             | Represents a fatal error in the XSQL page processing engine.                                                                                        |
  | [XSQLErrorWriter](XSQLErrorWriter.md)                                 |                                                                                                                                                     |
  | [XSQLHttpUtil](XSQLHttpUtil.md)                                       |                                                                                                                                                     |
  | [XSQLNamedConnection](XSQLNamedConnection.md)                         |                                                                                                                                                     |
  | [XSQLNamedConnectionManager](XSQLNamedConnectionManager.md)           |                                                                                                                                                     |
  | [XSQLPageRequestImpl](XSQLPageRequestImpl.md)                         | Base implementation of the XSQLPageRequest interface that case be used to derive new kinds of page request implementations.                         |
  | [XSQLParserHelper](XSQLParserHelper.md)                               | Common XML Parsing Routines                                                                                                                         |
  | [XSQLRequest](XSQLRequest.md)                                         | Programmatically process a request for an XSQL Page.                                                                                                |
  | [XSQLServlet](XSQLServlet.md)                                         | Servlet to enable HTTP GET-ing of and POST-ing to XSQL Pages                                                                                        |
  | [XSQLServletPageRequest](XSQLServletPageRequest.md)                   |                                                                                                                                                     |
  | [XSQLStylesheetProcessor](XSQLStylesheetProcessor.md)                 | XSLT Stylesheet Processing Engine                                                                                                                   |
  | [XSQLUtil](XSQLUtil.md)                                               |                                                                                                                                                     |

## Package oracle.xml.xsql Description

Provides APIs for Oracle XSQL Pages and XSQL Servlet.

## Related Documentation

For overviews, tutorials, examples, guides, and tool documentation, please see:

- https://www.oracle.com/database/technologies/appdev/xmldb.html

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

- **[Prev Package](../xquery/xqjdb/package-summary.md)**
- **[Next Package](../../../org/w3c/dom/package-summary.md)**

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
