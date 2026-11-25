Welcome to the Oracle Database Enterprise User Security Administrator's Guide for Oracle Database release 18c, version 18.1.

Oracle Database contains a comprehensive suite of security features that protect your data. These features include database privileges, roles, and integration with the Oracle Identity Management infrastructure for identity management services. Identity management refers to the process by which the complete security lifecycle—account creation, suspension, modification, and deletion—for network entities is managed by an organization.

The Oracle Database Enterprise User Security Administrator's Guide describes how to implement, configure, and administer Oracle Database users in Oracle Internet Directory, a directory service provided by the Oracle Identity Management platform.

This preface contains these topics:

- Intended Audience

- Documentation Accessibility

- Related Documents

- Conventions

### Intended Audience

The Oracle Database Enterprise User Security Administrator's Guide is intended for security administrators, DBAs, and application developers who perform one or more of the following tasks:

- Manage database users and privileges

- Provision database users

- Develop PL/SQL applications for enterprise users

To use this document, you need a working knowledge of SQL and Oracle fundamentals. You should also be familiar with Oracle security features described in "Related Documents".

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

For more information, see these Oracle resources:

- [Oracle Fusion Middleware Administrator's Guide for Oracle Internet Directory](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/dbimi&id=OIDAG)

- [Oracle Fusion Middleware Reference for Oracle Identity Management](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/dbimi&id=OIMUR)

- [Oracle Database Advanced Security Guide](../asoag/index.md)

- [Oracle Database 2 Day DBA](../admqs/index.md)

- [Oracle Database Administrator’s Guide](../admin/index.md)

- [Oracle Database Security Guide](../dbseg/index.md)

- [Oracle Database Development Guide](../adfns/index.md)

- [Oracle Database SQL Language Reference](../sqlrf/index.md)

- [SQL\*Plus Quick Reference](../sqlqr/index.md)

- [Oracle Database Error Messages Reference](../errmg/index.md)

- [Oracle Database Reference](../refrn/index.md)

- [Oracle Database Heterogeneous Connectivity User's Guide](../heter/index.md)

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

Many of the examples in this book use the sample schemas, which are installed by default when you select the Basic Installation option with an Oracle Database installation. Refer to [Oracle Database Sample Schemas](../comsc/index.md) for information on how these schemas were created and how you can use them yourself.

To download free release notes, installation documentation, white papers, or other collateral, please visit the Oracle Technology Network (OTN). You must register online before using OTN; registration is free and can be done at

    Community - Get Started

If you already have a user name and password for OTN, then you can go directly to the documentation section of the OTN Web site at

    Oracle Documentation

For conceptual information about the security technologies supported by Enterprise User Security, you can refer to the following third-party publications:

- Oracle Database 12c Security by Scott Gaetjen, David Knox, and William Maroulis. McGraw-Hill Education (Publisher), 2015.

- Oracle Database 12c Security Cookbook by Zorin Pavlovic and Maja Veselica. Birmingham, UK. Packet Publishing Ltd., 2016.

- Applied Oracle Security: Developing Secure Database and Middleware Environments by David Knox, Scott Gaetjen, Hamza Jahangir, Tyler Muth, Patrick Sack, Richard Wark, and Byran Wise. McGraw-Hill Companies Inc., 2010.

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
