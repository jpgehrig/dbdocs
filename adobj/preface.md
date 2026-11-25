Oracle Database Object-Relational Developer's Guide explains how to use the object-relational features of the Oracle Database, 12c release 2 (12.2.0.1). Information in this guide applies to versions of the Oracle Database that run on all platforms, and does not include system-specific information.

- Audience

- Documentation Accessibility

- Related Documents

- Conventions

### Audience

Oracle Database Object-Relational Developer's Guide is intended for programmers developing new applications or converting existing applications to run in the Oracle environment. The object-relational features are often used in content management, data warehousing, data/information integration, and similar applications that deal with complex structured data. The object views feature can be valuable when writing new C++, C#, Java, or XML applications on top of an existing relational schema.

This guide assumes that you have a working knowledge of application programming and that you are familiar with the use of Structured Query Language (SQL) to access information in relational databases. You should be familiar with the information in Oracle Database SQL Language Quick Reference, Oracle Database PL/SQL Language Reference, and Oracle Database 2 Day Developer's Guide, and with object-oriented programming techniques.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

For more information, see these Oracle resources:

- [Oracle Database Concepts](../cncpt/index.md) for information about basic Oracle concepts

- [Oracle Database SQL Language Reference ](../sqlrf/index.md)and [Oracle Database Administrator's Guide](../admin/index.md) for information about SQL

- [Oracle Database PL/SQL Language Reference ](../lnpls/index.md)for information about PL/SQL, the procedural language extension to Oracle SQL

- [Oracle Database Development Guide](../adfns/index.md) for general information about developing applications

- [Oracle Database JDBC Developer's Guide ](../jjdbc/index.md)and [Oracle Database Java Developer's Guide](../jjdev/index.md) for information about Oracle object-relational features through Java

- [Oracle Call Interface Programmer's Guide](../lnoci/index.md) and [Oracle C++ Call Interface Programmer's Guide](../lncpp/index.md) for information about using the Oracle Call Interface (OCI) and Oracle C++ Call Interface (OCCI) to build third-generation language (3GL) applications that interact with one or more the Oracle databases

- [Pro\*C/C++ Programmer's Guide](../lnpcc/index.md) for information about Oracle's Pro\* series of precompilers, which allow you to embed SQL and PL/SQL in 3GL application programs written in Ada, C, C++, COBOL, or FORTRAN

- [Oracle XML DB Developer's Guide ](../adxdb/index.md)and [Oracle XML Developer's Kit Programmer's Guide](../adxdk/index.md) for information about developing applications with XML

- [Oracle Database SecureFiles and Large Objects Developer's Guide ](../adlob/index.md)for information about Large Objects (LOBs)

- [Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/index.md)

- Oracle Developer Tools for Visual Studio Help

Many of the examples in this book use the sample schemas, which are installed by default when you select the Basic Installation option with an Oracle Database installation. Refer to [Oracle Database Sample Schemas](../comsc/index.md) for information on how these schemas were created and how you can use them yourself.

To download free release notes, installation documentation, white papers, or other collateral, please visit the Oracle Technology Network (OTN)

    http://www.oracle.com/technetwork/index.html

For the latest version of the Oracle documentation, including this guide, visit

    http://www.oracle.com/technetwork/documentation/index.html

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
