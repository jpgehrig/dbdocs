This manual describes the Oracle Database Gateway for ODBC, which enables Oracle client applications to access non-Oracle systems data through Structured Query Language (SQL). The gateway, with the Oracle database, creates the appearance that all data resides on a local Oracle database, even though the data can be widely distributed.

### Audience

This manual is intended for Oracle database administrators who perform the following tasks:

- Installing and configuring the Oracle Database Gateway for ODBC

- Diagnosing gateway errors

- Using the gateway to access non-Oracle system data

  **Note:**

  You should understand the fundamentals of Oracle Database Gateways and the UNIX based platform before using this guide to install or administer the gateway.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

For more information, see the following documents:

- [Oracle Database New Features Guide](../newft/index.md)

- [Oracle Call Interface Programmer's Guide](../lnoci/index.md)

- [Oracle Database Administrator's Guide](../admin/index.md)

- [Oracle Database Development Guide](../adfns/index.md)

- [Oracle Database Concepts](../cncpt/index.md)

- [Oracle Database Performance Tuning Guide](../tgdba/index.md)

- [Oracle Database Error Messages](../errmg/index.md)

- [Oracle Database Globalization Support Guide](../nlspg/index.md)

- [Oracle Database Reference](../refrn/index.md)

- [Oracle Database SQL Language Reference](../sqlrf/index.md)

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

- [SQL\*Plus User's Guide and Reference](../sqpug/index.md)

- [Oracle Database Heterogeneous Connectivity User's Guide](../heter/index.md)

- [Oracle Database Security Guide](../dbseg/index.md)

Many of the examples in this book use the sample schemas of the seed database, which is installed by default when you install Oracle. Refer to [Oracle Database Sample Schemas](../comsc/index.md) for information on how these schemas were created and how you can use them yourself.

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
