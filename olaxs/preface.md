The OLAP expression syntax includes analytic functions, arithmetic operators, and single-row functions. The OLAP syntax is an extension of the SQL syntax. If you have used SQL analytic functions or single-row functions, then this syntax is familiar to you.

This preface contains these topics:

- Audience

- Documentation Accessibility

- Related Documents

- Conventions

- Backus-Naur Form Syntax

### Audience

This document is intended for anyone who wants to create calculated measures or transform the data stored in relational tables for use in dimensional database objects such as cubes, cube dimensions, and measures.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

For more information, see these documents in the Oracle Database 11.2 documentation set:

\<xref cid="1l1qda" format="html" href="olink:OLAUG" scope="external"\>\<i\>Oracle OLAP User's Guide\</i\>\</xref\>

- [Oracle OLAP User's Guide](../olaug/index.md)

  Explains how SQL applications can extend their analytic processing capabilities and manage summary data by using the OLAP option of Oracle Database.

- [Oracle OLAP DML Reference](../oladm/index.md)

  Contains a complete description of the OLAP Data Manipulation Language (OLAP DML), which is used to define and manipulate analytic workspace objects.

- [Oracle Database Reference](../refrn/index.md)

  Contains full descriptions of the data dictionary views for cubes, cube dimensions, and other dimensional objects.

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md)

  Contains full descriptions of several PL/SQL packages for managing cubes.

- [Oracle OLAP Java API Developer's Guide](../olaap/index.md)

  Introduces the Oracle OLAP API, a Java application programming interface for Oracle OLAP, which is used for defining, building, and querying dimensional objects in the database.

- [Oracle OLAP Java API Reference](../olapi/index.md)

  Describes the classes and methods in the Oracle OLAP Java API for defining, building, and querying dimensional objects in the database.

### Conventions

These text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |

### Backus-Naur Form Syntax

The syntax in this reference is presented in a simple variation of Backus-Naur Form (BNF) that uses the following symbols and conventions:

| Symbol or Convention | Description                                                                                                                                                                                                                                  |
|:---------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \[ \]                | Brackets enclose optional items.                                                                                                                                                                                                             |
| { }                  | Braces enclose a choice of items, only one of which is required.                                                                                                                                                                             |
| \|                   | A vertical bar separates alternatives within brackets or braces.                                                                                                                                                                             |
| ...                  | Ellipses indicate that the preceding syntactic element can be repeated.                                                                                                                                                                      |
| delimiters           | Delimiters other than brackets, braces, and vertical bars must be entered as shown.                                                                                                                                                          |
| boldface             | Words appearing in boldface are keywords. They must be typed as shown. (Keywords are case-sensitive in some, but not all, operating systems.) Words that are not in boldface are placeholders for which you must substitute a name or value. |
