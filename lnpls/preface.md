## Preface

Oracle Database PL/SQL Language Reference describes and explains how to use PL/SQL, the Oracle procedural extension of SQL.

### Topics

- Audience

- Documentation Accessibility

- Related Documents

- Conventions

- Syntax Descriptions

### Audience

Oracle Database PL/SQL Language Reference is intended for anyone who is developing PL/SQL-based applications for either an Oracle Database or an Oracle TimesTen In-Memory Database, including:

- Programmers

- Systems analysts

- Project managers

- Database administrators

To use this document effectively, you need a working knowledge of:

- Oracle Database

- Structured Query Language (SQL)

- Basic programming concepts such as `IF-THEN` statements, loops, procedures, and functions

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at [http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc](https://docs.oracle.com/pls/topic/lookup?ctx=acc&id=docacc).

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit [http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info](https://docs.oracle.com/pls/topic/lookup?ctx=acc&id=info) or visit [http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs](https://docs.oracle.com/pls/topic/lookup?ctx=acc&id=trs) if you are hearing impaired.

### Related Documents

For more information, see these documents in the Oracle Database documentation set:

- [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md)

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/introduction-to-oracle-supplied-plsql-packages-and-types.md)

- [Oracle Database JSON Developer’s Guide](../adjsn/intro-to-json-data-and-oracle-database.md)

- [Oracle Database SODA for PL/SQL Developer's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnpls&id=ADSDP-GUID-4F518E19-7B01-4C89-AFD7-56D9A4FC8779)

- [Oracle Database Development Guide](../adfns/fundamentals.md)

- [Oracle Database Administrator's Guide](../admin/basic-database-administration.md)

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/getting-started.md)

- [Oracle Database Object-Relational Developer's Guide](../adobj/introduction-to-oracle-objects.md)

- [Oracle Database Concepts](../cncpt/introduction-to-oracle-database.md)

  [Oracle Database Sample Schemas](../comsc/introduction-to-sample-schemas.md)

**See Also:**

[`http://www.oracle.com/technetwork/database/features/plsql/index.html`](http://www.oracle.com/technetwork/database/features/plsql/index.html)

### Conventions

This document uses these text conventions:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
| {A\|B\|C}   | Choose either A, B, or C.                                                                                                              |

Also:

- `*_``view` means all static data dictionary views whose names end with `view`. For example, `*_ERRORS` means `ALL_ERRORS`, `DBA_ERRORS`, and `USER_ERRORS`. For more information about any static data dictionary view, or about static dictionary views in general, see [Oracle Database Reference](../refrn/about-static-data-dictionary-views.md).

- Table names not qualified with schema names are in the sample schema `HR`. For information about the sample schemas, see [Oracle Database Sample Schemas](../comsc/index.md).

### Syntax Descriptions

Syntax descriptions are provided in this book for various SQL, PL/SQL, or other command-line constructs in graphic form or Backus Naur Form (BNF). See [Oracle Database SQL Language Reference](../sqlrf/How-to-Read-Syntax-Diagrams.md) for information about how to interpret these descriptions.
