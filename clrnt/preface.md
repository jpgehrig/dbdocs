This document describes the features of Oracle Database for Windows software installed on Windows 2003, Windows 2000, and Windows XP Professional operating systems.

This guide describes Oracle Database Extensions for .NET, which provides a Common Language Runtime (CLR) host for Oracle Database and data access through Oracle Data Provider for .NET (ODP.NET) classes.

This preface contains these topics:

- Audience

- Documentation Accessibility

- Related Documents

- Passwords in Code Examples

- Conventions

### Audience

Oracle Database Extensions for .NET Developer's Guide is intended for programmers who are developing applications to access an Oracle Database using Oracle Database Extensions for .NET. This documentation is also valuable to systems analysts, project managers, and others interested in the development of database applications.

To use this document, you must be familiar with Microsoft .NET Framework classes and ADO.NET and have a working knowledge of application programming using Microsoft C#, Visual Basic, or another .NET language.

Users should also be familiar with the use of Structured Query Language (SQL) to access information in relational database systems.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

For more information, see these Oracle resources:

- Oracle Developer Tools for Visual Studio Help

- [Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/index.md)

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md)

- [Oracle Database SQL Language Reference](../sqlrf/index.md)

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md)

- [Oracle Database Release Notes for Microsoft Windows](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/clrnt&id=NTDBN)

- [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/index.md)

- [Oracle Database New Features Guide](../newft/index.md)

- [Oracle Database Net Services Reference ](../netrf/index.md)

Many of the examples in this book use the sample schemas, which are installed by default when you select the Basic Installation option with an Oracle Database installation. Refer to [Oracle Database Sample Schemas](../comsc/index.md) for information on how these schemas were created and how you can use them yourself.

To download free release notes, installation documentation, white papers, or other collateral, please visit the Oracle Technology Network (OTN). You must register online before using OTN; registration is free and can be done at

    http://www.oracle.com/technetwork/index.html

If you already have a username and password for OTN, then you can go directly to the documentation section of the OTN Web site at

    http://www.oracle.com/technetwork/documentation/index.html

### Passwords in Code Examples

For simplicity in demonstrating this product, code examples do not perform the password management techniques that a deployed system normally uses. In a production environment, follow the Oracle Database password management guidelines, and disable any sample accounts. See [Oracle Database Security Guide](../dbseg/managing-security-for-application-developers.md) for password management guidelines and other security recommendations.

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
