This preface introduces you to the Oracle Database SQLJ Developer's Guide, discussing the intended audience and conventions of this document. A list of related Oracle documents is also provided.

This preface covers the following topics:

- Audience

- Related Documents

- Conventions

### Audience

This manual is intended for anyone with an interest in SQLJ programming but assumes at least some prior knowledge of the following:

- Java

- SQL

- PL/SQL

- Oracle Database

Although general knowledge of SQL is sufficient, any knowledge of JDBC and Oracle-specific SQL features would be helpful as well.

### Related Documents

Also available from the Oracle Java Platform group are the following Oracle resources:

- [Oracle Database Java Developer's Guide ](../jjdev/Java-introduction.md)

  This book introduces the basic concepts of Java in Oracle Database and provides general information about server-side configuration and functionality. Information that pertains to Oracle Database Java environment in general, rather than to a particular product such as JDBC or SQLJ, is in this book.

  It also discusses Java stored procedures, which are programs that run directly in Oracle Database. With stored procedures, Java developers can implement business logic at the server level, thereby improving application performance, scalability, and security.

- [Oracle Database JDBC Developer's Guide ](../jjdev/Java-introduction.md)

  This book covers programming syntax and features of the Oracle implementation of the JDBC standard. This includes an overview of the Oracle JDBC drivers, details of the Oracle implementation of JDBC 1.22, 2.0, 3.0, and 4.0 features, and discussion of Oracle JDBC type extensions and performance extensions.

The following documents are from the Oracle Server Technologies group:

- [Oracle Database Development Guide ](../adfns/fundamentals.md)

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md)

- [Oracle Database Object-Relational Developer's Guide](../adobj/introduction-to-oracle-objects.md)

- [Oracle Database PL/SQL Packages and Types Reference ](../arpls/introduction-to-oracle-supplied-plsql-packages-and-types.md)

- [Oracle Database PL/SQL Language Reference ](../lnpls/overview.md)

- [Oracle Database SQL Language Reference ](../sqlrf/Introduction-to-Oracle-SQL.md)

- [Oracle Database Net Services Administrator's Guide ](../netag/part-I-understanding-oracle-net-services.md)

- [Oracle Database Advanced Security Guide ](../asoag/introduction-to-oracle-advanced-security.md)

- [Oracle Database Globalization Support Guide ](../nlspg/overview-of-globalization-support.md)

- [Oracle Database Reference ](../refrn/initialization-parameters.md)

- [Oracle Database Sample Schemas](../comsc/introduction-to-sample-schemas.md)

**Note:**

Oracle error message documentation is available on Oracle Technology Network. You can browse the error messages by range. Once you find the specific range, use the "find in page" feature of your browser to locate the specific message. When connected to the Internet, you can search for a specific error message using the error message search feature of the Oracle online documentation.

For documentation of SQLJ standard features and syntax, refer to the following specification:

Information Technology - Database Languages - SQL - Part 10: Object Language Bindings (SQL/OLB)

Throughout this manual, the term "ISO SQLJ standard" is used to refer to this standard.

You can obtain the ISO SQLJ standard from ANSI through the following Web site:

[`http://www.ansi.org/`](http://www.ansi.org/)

Click eStandards Store and search for the term "INCITS/ISO/IEC 9075-10".

You can also obtain the ISO SQLJ standard from ISO through their web store

[`http://www.iso.org/iso/store.htm`](http://www.iso.org/iso/store.htm)

Visit the preceding link and search for the term "ISO/IEC 9075-10".

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Conventions

This section describes the conventions used in the text and code examples of this documentation set. It describes:

- Conventions in Text

- Conventions in Code Examples

**Note:**

Also note that command-line examples are for a UNIX environment with a system prompt of "`%`". This is only by convention and can be adjusted as appropriate for your operating system.

#### Conventions in Text

There are various conventions in text to help you more quickly identify special terms. The following table describes those conventions and provides examples of their use.

| Convention                                      | Meaning                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Example                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Italics                                         | Italic typeface indicates book titles or emphasis, or terms that are defined in the text.                                                                                                                                                                                                                                                                                                                                                                                              | Oracle Database Concepts<br>Ensure that the recovery catalog and target database do not reside on the same disk.                                                                                                                                                                                                                                                                                                                  |
| `UPPERCASE monospace (fixed-width) font`        | Uppercase monospace typeface indicates elements supplied by the system. Such elements include parameters, privileges, data types, RMAN keywords, SQL keywords, SQL\*Plus or utility commands, packages and methods, as well as system-supplied column names, database objects and structures, usernames, and roles.                                                                                                                                                                    | You can specify this clause only for a `NUMBER` column.<br>You can back up the database by using the `BACKUP` command.<br>Query the `TABLE_NAME` column in the `USER_TABLES` data dictionary view.<br>Use the `DBMS_STATS`.`GENERATE_STATS` procedure.                                                                                                                                                                            |
| `lowercase monospace (fixed-width) font`        | Lowercase monospace typeface indicates executables, filenames, directory names, and sample user-supplied elements. Such elements include computer and database names, net service names, and connect identifiers, as well as user-supplied database objects and structures, column names, packages and classes, usernames and roles, program units, and parameter values.<br>Note: Some programmatic elements use a mixture of UPPERCASE and lowercase. Enter these elements as shown. | Enter `sqlplus` to open SQL\*Plus.<br>The password is specified in the `orapwd` file.<br>Back up the data files and control files in the `/disk1/oracle/dbs` directory.<br>The `department_id`, `department_name`, and `location_id` columns are in the `hr.departments` table.<br>Set the `QUERY_REWRITE_ENABLED` initialization parameter to `true.`<br>Connect as `oe` user.<br>The `JRepUtil` class implements these methods. |
| `lowercase italic monospace (fixed-width) font` | Lowercase italic monospace font represents place holders or variables.                                                                                                                                                                                                                                                                                                                                                                                                                 | You can specify the `parallel_clause`.<br>Run `old_release``.SQL` where `old_release`refers to the release you installed prior to upgrading.                                                                                                                                                                                                                                                                                      |

#### Conventions in Code Examples

Code examples illustrate SQL, PL/SQL, SQL\*Plus, or other command-line statements. They are displayed in a monospace (fixed-width) font and separated from standard text as shown in this example:

    SELECT username FROM dba_users WHERE username = 'MIGRATE';

The following table describes typographic conventions used in code examples and provides examples of their use.

Changed first row below to note this doc uses \*angle\* brackets for optional.

| Convention     | Meaning                                                                                                                                                                                                                                                                                                           | Example                                                                                                          |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------|
| \< \>          | In this document, angle brackets are used instead of regular brackets to enclose one or more optional items. Do not enter the angle brackets. (Regular brackets are not used due to SQLJ syntax considerations.)                                                                                                  | `DECIMAL (``digits`` < , ``precision`` >)`                                                                       |
| \|             | A vertical bar represents a choice of two or more options within brackets or braces. Enter one of the options. Do not enter the vertical bar.                                                                                                                                                                     | `{ENABLE | DISABLE}`<br>`[COMPRESS | NOCOMPRESS]`                                                                |
| `...`          | Horizontal ellipsis points indicate either:<br>• Omission of parts of the code that are not directly related to the example<br>• That you can repeat a portion of the code                                                                                                                                        | `CREATE TABLE ... AS ``subquery``;``SELECT ``col1``, ``col2``, ... , ``coln`` FROM employees;`                   |
| Other notation | You must enter symbols other than brackets, braces, vertical bars, and ellipsis points as shown.                                                                                                                                                                                                                  | ` acctbal NUMBER(11,2);`<br>` acct CONSTANT NUMBER(4) := 3;`                                                     |
| `Italics`      | Italicized text indicates place holders or variables for which you must supply particular values.                                                                                                                                                                                                                 | `CONNECT SYSTEM`<br>Enter password: password<br>`DB_NAME = ``database_name`                                      |
| `UPPERCASE`    | Uppercase typeface indicates elements supplied by the system. These terms are in uppercase to distinguish them from terms you define. Unless terms appear in brackets, enter them in the order and with the spelling shown. However, because these terms are not case-sensitive, you can enter them in lowercase. | `SELECT last_name, employee_id FROM employees;`<br>`SELECT * FROM USER_TABLES;`<br>`DROP TABLE hr.employees;`    |
| `lowercase`    | Lowercase typeface indicates programmatic elements that you supply. For example, lowercase indicates names of tables, columns, or files.<br>Note: Some programmatic elements use a mixture of UPPERCASE and lowercase. Enter these elements as shown.                                                             | `SELECT last_name, employee_id FROM employees;`<br>`sqlplus hr/hr`<br>`CREATE USER mjones IDENTIFIED BY ty3MU9;` |
