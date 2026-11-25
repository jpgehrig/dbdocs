This document is your primary source of introductory, installation, postinstallation configuration, and usage information for Oracle Data Provider for .NET.

Oracle Data Provider for .NET is an implementation of the Microsoft ADO.NET interface.

This Preface contains these topics:

- Audience

- Documentation Accessibility

- Related Documents

- Passwords in Code Examples

- Conventions

### Audience

Oracle Data Provider for .NET Developer's Guide is intended for programmers who are developing applications to access an Oracle database using Oracle Data Provider for .NET. This documentation is also valuable to systems analysts, project managers, and others interested in the development of database applications.

To use this document, you must be familiar with Microsoft .NET Framework classes and ADO.NET and have a working knowledge of application programming using Microsoft C#, Visual Basic .NET, or another .NET language.

Although the examples in the documentation and the samples in the sample directory are written in C#, developers can use these examples as models for writing code in other .NET languages.

Users should also be familiar with the use of Structured Query Language (SQL) to access information in relational database systems.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

For more information, see these Oracle resources:

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md)

- [Oracle Database Release Notes for Microsoft Windows](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=NTDBN)

- [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/index.md)

- [Oracle Database Administrator's Guide](../admin/index.md)

- [Oracle Database Development Guide](../adfns/index.md)

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/index.md)

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/index.md)

- [Oracle Database New Features Guide](../newft/index.md)

- [Oracle Database Concepts](../cncpt/index.md)

- [Oracle Database Reference](../refrn/index.md)

- [Oracle Database Extensions for .NET Developer's Guide for Microsoft Windows](../clrnt/index.md)

- [Oracle Database Object-Relational Developer's Guide](../adobj/index.md)

- [Oracle Database SQL Language Reference](../sqlrf/index.md)

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

- [Oracle Database Net Services Reference ](../netrf/index.md)

- [Oracle Call Interface Programmer's Guide](../lnoci/index.md)

- [Oracle Services for Microsoft Transaction Server Developer's Guide for Microsoft Windows](../ntmts/index.md)

- [Oracle Database Globalization Support Guide](../nlspg/index.md)

- [Oracle XML DB Developer's Guide](../adxdb/index.md)

- [Oracle XML Developer's Kit Programmer's Guide](../adxdk/index.md)

- [Oracle Database Security Guide](../dbseg/index.md)

- [Oracle Spatial Developer's Guide](../spatl/index.md)

- [Oracle Data Guard Concepts and Administration](../sbydb/index.md)

Many of the examples in this book use the sample schemas, which are installed by default when you select the Basic Installation option with an Oracle Database installation. Refer to [Oracle Database Sample Schemas](../comsc/index.md) for information on how these schemas were created and how you can use them yourself.

To download free release notes, installation documentation, white papers, or other collateral, please visit the Oracle Technology Network (OTN). You must register online before using OTN; registration is free and can be done at

    http://www.oracle.com/technetwork/index.html

If you already have a username and password for OTN, then you can go directly to the documentation section of the OTN Web site at

    http://docs.oracle.com/database/122/index.htm

For additional information, see:

    https://msdn.microsoft.com/en-us/default.aspx

and

    http://msdn.microsoft.com/library

### Passwords in Code Examples

For simplicity in demonstrating this product, code examples do not perform the password management techniques that a deployed system normally uses. In a production environment, follow the Oracle Database password management guidelines, and disable any sample accounts. See [Oracle Database Security Guide](../dbseg/managing-security-for-application-developers.md) for password management guidelines and other security recommendations.

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
