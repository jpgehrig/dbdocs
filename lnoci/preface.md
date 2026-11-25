Oracle Call Interface (OCI) is an application programming interface (API) that lets applications written in C or C++ interact with Oracle Database. OCI gives your programs the capability to perform the full range of database operations that are possible with Oracle Database, including SQL statement processing and object manipulation.

### Audience

This guide is intended for programmers developing new applications or converting existing applications to run in the Oracle Database environment. This comprehensive treatment of OCI is also valuable to systems analysts, project managers, and others interested in the development of database applications.

This guide assumes that you have a working knowledge of application programming using C. Readers should also be familiar with the use of structured query language (SQL) to access information in relational database systems. In addition, some sections of this guide assume knowledge of the basic concepts of object-oriented programming.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/index.md)and[Oracle Database Administrator’s Guide](../admin/index.md) for information about SQL

- [Oracle Database Concepts](../cncpt/index.md)

- [Oracle Database New Features Guide](../newft/index.md) for information about the differences between the Standard Edition and the Enterprise Edition and all the features and options that are available to you

- [Oracle C++ Call Interface Programmer's Guide](../lncpp/index.md) for more information about OCI functionality for C++ that enables programmers to manipulate database objects of user-defined types as C++ objects

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

Many of the examples in this book use the sample schemas, which are installed by default when you select the Basic Installation option with an Oracle Database installation. See [Oracle Database Sample Schemas](../comsc/index.md) for information about how these schemas were created and how you can use them.

To download free release notes, installation documentation, white papers, or other collateral, visit the Oracle Technology Network (OTN). You must register online before using OTN; registration is free and can be done at

    http://www.oracle.com/technetwork/community/join/overview/

If you have a user name and password for OTN, then you can go directly to the documentation section of the OTN Web site at

    http://www.oracle.com/technetwork/indexes/documentation/

Oracle Call Interface Programmer's Guide does not contain all information that describes the features and functionality of OCI in the Oracle Database Standard Edition and Enterprise Edition products. Explore the following documents for additional information about OCI.

- [Oracle Database Data Cartridge Developer's Guide](../addci/index.md) provides information about cartridge services and OCI calls pertaining to development of data cartridges.

- [Oracle Database Globalization Support Guide](../nlspg/index.md) explains OCI calls pertaining to NLS settings and globalization support.

- [Oracle Database Advanced Queuing User's Guide](../adque/index.md) supplies information about OCI calls pertaining to Advanced Queuing.

- [Oracle Database Development Guide](../adfns/index.md) explains how to use OCI with the XA library.

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/index.md) provides information about using OCI calls to manipulate LOBs, including code examples.

- [Oracle Database Object-Relational Developer's Guide](../adobj/index.md) offers a detailed explanation of object types.

For additional information about Oracle Database, consult the following documents:

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

- [Oracle Database New Features Guide](../newft/index.md)

- [Oracle Database Concepts](../cncpt/index.md)

- [Oracle Database Reference](../refrn/index.md)

- [Oracle Database Error Messages Reference](../errmg/index.md)

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
