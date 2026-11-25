This manual describes Oracle XML DB, and how you can use it to store, generate, manipulate, manage, and query XML data in the database.

After introducing you to the heart of Oracle XML DB, namely the `XMLType` framework and Oracle XML DB Repository, the manual provides a brief introduction to design criteria to consider when planning your Oracle XML DB application. It provides examples of how and where you can use Oracle XML DB.

The manual then describes ways you can store and retrieve XML data using Oracle XML DB, APIs for manipulating `XMLType` data, and ways you can view, generate, transform, and search on existing XML data. The remainder of the manual discusses how to use Oracle XML DB Repository, including versioning and security, how to access and manipulate repository resources using protocols, SQL, PL/SQL, or Java, and how to manage your Oracle XML DB application using Oracle Enterprise Manager. It also introduces you to XML messaging and Oracle Database Advanced Queuing `XMLType` support.

- Audience
  Oracle XML DB Developer's Guide is intended for developers building XML Oracle Database applications.
- Documentation Accessibility
- Related Documents
- Conventions
- Code Examples
  The code examples in this book are for illustration only. In many cases, however, you can copy and paste parts of examples and run them in your environment.
- Syntax Descriptions
  Syntax descriptions are provided for various SQL, PL/SQL, or other command-line constructs in graphic form or Backus Naur Form (BNF).

### Audience

Oracle XML DB Developer's Guide is intended for developers building XML Oracle Database applications.

An understanding of XML, XML Schema, XQuery, XPath, and XSL is helpful when using this manual.

Many examples provided here are in SQL, PL/SQL, Java, or C. A working knowledge of one of these languages is presumed.

**Parent topic:** Preface

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

**Parent topic:** Preface

### Related Documents

For more information, see these Oracle resources:

- [Oracle Database XML Java API Reference](../jaxml/index.md)

- [Oracle XML Developer's Kit Programmer's Guide](../adxdk/index.md)

- [Oracle Database Error Messages](../errmg/index.md)

- [Oracle Text Application Developer's Guide ](../ccapp/index.md)

- [Oracle Text Reference](../ccref/index.md)

- [Oracle Database Concepts](../cncpt/index.md)

- [Oracle Database Java Developer's Guide](../jjdev/index.md)

- [Oracle Database Development Guide](../adfns/index.md)

- [Oracle Database Advanced Queuing User's Guide](../adque/index.md)

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md)

Many of the examples in this book use the Oracle Database sample schemas. Refer to [Oracle Database Sample Schemas](../comsc/introduction-to-sample-schemas.md) for information about how these database schemas were created and how you can use them yourself.

To download free release notes, installation documentation, white papers, or other collateral, please visit the Oracle Technology Network (OTN). You must register online before using OTN; registration is free and can be done at [OTN Registration](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=otn_join_overview)

If you already have a user name and password for OTN, then you can go directly to the documentation section of the OTN website at [OTN Documentation](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=otn_documentation)

For additional information, see:

- [Extensible Markup Language (XML) 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xml)

- [XML Schema](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_xml_schema) and [XML Schema resources](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_2001_xmlschema)

- [XML Schema Part 0: Primer](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xschema0_primer)

- [XML Schema Part 1: Structures](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xschema1_struct)

- [XML Schema Part 2: Datatypes](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xschema2_types)

- [XML Schemas reference list](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=oasis_open_org_schemas)

- [XML and MIME Media-Types](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=xml_coverpages_mime_types)

- [XML Pointer Language (XPointer)](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xpointer)

- [XML Path Language (XPath) Version 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xpath)

- [XML Path Language (XPath) 2.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xpath_2_0)

- [XPath Tutorial](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=zvon_org_xpath_tut_egs)

- [Unicode in XML and other Markup Languages, Unicode Technical Report \#20](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_2002_unicodexml)

- [Namespaces in XML 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xml_names)

- [XML Information Set](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xml_infoset)

- [Document Object Model (DOM)](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_dom)

- [XSL Transformations (XSLT) Version 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xslt)

- [Extensible Stylesheet Language (XSL) Version 1.1](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_tr_xsl)

- [XSL references](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=oasis_open_org_xsl)

- [XSLT Tutorial](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=zvon_org_xsl_tutorial)

- [Web Services Activity](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_ws_activity)

- [FTP Protocol Specification, IETF RFC959](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=ietf_org_rfc959)

- ISO/IEC 13249-2:2000, Information technology - Database languages - SQL Multimedia and Application Packages - Part 2: Full-Text, International Organization For Standardization, 2000

**Note:**

Throughout this manual, **XML Schema** refers to the [XML Schema 1.0 recommendation](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdb&id=w3_org_xml_schema).

**Parent topic:** Preface

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |

**Parent topic:** Preface

### Code Examples

The code examples in this book are for illustration only. In many cases, however, you can copy and paste parts of examples and run them in your environment.

- Standard Database Schemas
  Many of the examples in this book use the standard database schemas that are included in your database. In particular, database schema `OE` contains XML purchase-order documents in `XMLType` table `purchaseorder`, and XML documents with warehouse information in `XMLType` column `warehouse_spec` of table `warehouses`.
- Pretty Printing of XML Data
  To promote readability, especially of lengthy or complex XML data, output is sometimes shown pretty-printed (formatted) in code examples.
- Execution Plans
  Some of the code examples in this book present execution plans. These are for illustration only. Running examples that are presented here in your environment is likely to result in different execution plans from those presented here.
- Reminder About Case Sensitivity
  SQL is case-insensitive. XML is case-sensitive. Keep this in mind when you mix SQL and XML.

**Parent topic:** Preface

#### Standard Database Schemas

Many of the examples in this book use the standard database schemas that are included in your database. In particular, database schema `OE` contains XML purchase-order documents in `XMLType` table `purchaseorder`, and XML documents with warehouse information in `XMLType` column `warehouse_spec` of table `warehouses`.

The purchase-order documents are also contained in Oracle XML DB Repository, under the repository path `/home/OE/PurchaseOrders/2002/`. The XML schema that governs these documents is file `purchaseorder.xsd`, at repository location `/home/OE/purchaseorder.xsd`. An XSLT stylesheet that is used in some examples to transform purchase-order documents is file `purchaseorder.xsl`, at repository location `/home/OE/purchaseorder.xsl`. This XML schema and stylesheet can also be found in [Oracle-Supplied XML Schemas and Examples](oracle-supplied-XML-schemas-and-examples.md).

**See Also:**

- [Oracle Database Sample Schemas](../comsc/introduction-to-sample-schemas.md) for information about database schema `HR`

- [Oracle Database Sample Schemas](../comsc/introduction-to-sample-schemas.md) for information about database schema `OE`

**Parent topic:** Code Examples

#### Pretty Printing of XML Data

To promote readability, especially of lengthy or complex XML data, output is sometimes shown pretty-printed (formatted) in code examples.

**Parent topic:** Code Examples

#### Execution Plans

Some of the code examples in this book present execution plans. These are for illustration only. Running examples that are presented here in your environment is likely to result in different execution plans from those presented here.

**Parent topic:** Code Examples

#### Reminder About Case Sensitivity

SQL is case-insensitive. XML is case-sensitive. Keep this in mind when you mix SQL and XML.

When examining the examples in this book, keep in mind the following:

- SQL is case-insensitive, but names in SQL code are implicitly uppercase, unless you enclose them in double quotation marks (`"`).

- XML is case-sensitive. You must refer to SQL names in XML code using the correct case: uppercase SQL names must be written as uppercase.

For example, if you create a table named `my_table` in SQL without using double quotation marks, then you must refer to it in XML code as "`MY_TABLE`".

**Parent topic:** Code Examples

### Syntax Descriptions

Syntax descriptions are provided for various SQL, PL/SQL, or other command-line constructs in graphic form or Backus Naur Form (BNF).

See [Oracle Database SQL Language Reference](../sqlrf/How-to-Read-Syntax-Diagrams.md) for information about how to interpret these descriptions.

**Parent topic:** Preface
