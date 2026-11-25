A description is given of the Oracle XML Developer's Kit (XDK) standards.

### 34.1 XML Standards Supported by XDK

Topics here include XML and Java standards supported by XDK.

#### 34.1.1 Summary of XML Standards Supported by XDK

The XML standards supported by XDK components are described.

Table 34-1 Summary of XML Standards Supported by Oracle XML Developer's Kit

| Standard                                                                                                                                                                                      | Java                                                   | C                     | C++                      |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------|:----------------------|:-------------------------|
| [Document Object Model (DOM) Level 1 Specification](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_dom_level_1)                         | Full                                                   | Full                  | Full                     |
| [Document Object Model Core](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_dom_level2_core) (2.0)                                         | Full                                                   | Full                  | Full                     |
| [Document Object Model (DOM) Level 2 Events Specification](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_dom_level2_events)               | Full                                                   | Full                  | Full                     |
| [Document Object Model (DOM) Level 2 Traversal and Range Specification](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_dom_level2_t_range) | Full                                                   | Full                  | Full                     |
| [Document Object Model (DOM) Level 3 Core Specification](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_dom_level_3)                    | Full                                                   | N/A                   | N/A                      |
| [Document Object Model (DOM) Level 3 Load and Save Specification](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_dom_level3_lod_sav)       | Partial<sup>Foot 1</sup>                               | None                  | None                     |
| [Document Object Model (DOM) Level 3 Validation Specification](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_dom_level3_valid8n)          | Full<sup>Foot 2</sup>                                  | None                  | None                     |
| [JAXP 1.1 and 1.2](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=otn_java) (JSR Standard)                                                        | Full                                                   | N/A                   | N/A                      |
| [SAX Project](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=sax_project_org), 1.0, 2.0 core, and 2.0 extension                                   | Full                                                   | Full                  | Full                     |
| [Extensible Markup Language (XML) 1.0 (Fifth Edition)](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_rec_xml)                          | Full                                                   | Full                  | Full                     |
| [XML Base (Second Edition)](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xmlbase)                                                     | Only in XSLT                                           | None                  | None                     |
| [Namespaces in XML 1.0 (Third Edition)](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_rec_xml_names)                                      | Full                                                   | Full                  | Full                     |
| [XML Pipeline Definition Language Version 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xml_pipeline)                                | Partial<sup>Foot 3</sup>                               | None                  | None                     |
| [XML Schema Part 0: Primer Second Edition](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xschema0_primer)                              | Full                                                   | Full<sup>Foot 4</sup> | Full<sup>Footref 4</sup> |
| [XML Path Language (XPath) Version 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xpath)                                           | Full                                                   | Full                  | Full                     |
| [XML Path Language (XPath) 2.0 (Second Edition)](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xpath_2_0)                              | Full                                                   | None                  | None                     |
| [XML Path Language (XPath) 3.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xpath_3_0)                                               | Full                                                   | None                  | None                     |
| [XQuery 1.0: An XML Query Language (Second Edition)](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xquery)                             | Full                                                   | None                  | None                     |
| [XQuery and XPath Data Model 3.1](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xpath_datamodel)                                       | Full                                                   | None                  | None                     |
| [XPath and XQuery Functions and Operators 3.1](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xpath_functions)                          | Full                                                   | None                  | None                     |
| [XQuery 3.0: An XML Query Language](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xquery_30)                                              | Full                                                   | None                  | None                     |
| [XQuery and XPath Data Model 3.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xpath_datamodel_30)                                       | Full                                                   | None                  | None                     |
| [XPath and XQuery Functions and Operators 3.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xpath_fns_30)                             | Full                                                   | None                  | None                     |
| [XQuery Update Facility 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xquery_update10)                                            | Full                                                   | None                  | None                     |
| [XQueryX 3.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xqueryx_30)                                                                   | Full                                                   | None                  | None                     |
| [JSR-000225 XQuery API for Java](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=jcp_org_jsr225)                                                   | Full                                                   | None                  | None                     |
| [XSL Transformations (XSLT) Version 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xslt)                                           | Full                                                   | Full                  | Full                     |
| XSL Transformations (XSLT) Version 2.0, [Basic XSLT Processor](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xslt20basicconform)          | Conformance as a basic XSLT processor<sup>Foot 5</sup> | None                  | None                     |

<sup>Footnote 1</sup>

DOM Level 3 Load and Save describes the relationship between DOM 3.0 Core and Load and Save.

<sup>Footnote 2</sup>

DOM 3.0 Validation describes the relationship between DOM 3.0 Core and Validation.

<sup>Footnote 3</sup>

Pipeline Definition Language Standard for XDK for Java describes the parts of the standard that are not supported.

<sup>Footnote 4</sup>

The Schema processor fully supports the functionality stated in the specification plus [XML Schema 1.0 Specification Errata](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xmlschema_errata).

<sup>Footnote 5</sup> See XSLT Standard for XDK for Java for details

#### 34.1.2 XML Standards for XDK for Java

Topics here include XDK standards for DOM, XSLT, JAXB, and Pipeline Definition Language.

##### 34.1.2.1 DOM Standard for XDK for Java

The DOM APIs include support for candidate recommendations of DOM Level 3 Validation and DOM Level 3 Load and Save.

**Note:**

In Oracle Database 10g Release 2, XDK for Java implements the candidate recommendation versions of Document Object Model (DOM) Level 3.0 Load and Save and Validation specifications. Oracle plans to produce a release or patch set that will include an implementation of DOM Level 3.0 Load and Save and Validation recommendations. To conform with the recommendations, Oracle might be forced to make changes that are not backward compatible. During this period Oracle does not guarantee backward compatibility with our DOM Load and Save, and Validation implementation. After XDK for Java is updated to conform with the recommendations, standard Oracle policies for backward compatibility will apply to the Oracle DOM Load and Save, and Validation implementation.

###### 34.1.2.1.1 DOM Level 3 Load and Save

The DOM Level 3 Load and Save module enables software developers to load and save Extensible Markup Language (XML) content inside conforming products.

The `charset-overrides-xml-encoding` configuration parameter is not supported by `LSParser`. Optional settings of these configuration parameters are not supported by `LSParser`:

- `disallow-doctype (true)`

- `ignore-unknown-character-denormalizations (false)`

- `namespaces (false)`

- `supported-media-types-only (true)`

The `discard-default-content` configuration parameter is not supported by `LSSerializer`. Optional settings of these configuration parameters are not supported by LSSerializer:

- `canonical-form (true)`

- `format-pretty-print (true)`

- `ignore-unknown-character-denormalizations (false)`

- `normalize-characters (true)`

###### 34.1.2.1.2 DOM 3.0 Validation

DOM 3.0 validation lets users retrieve metadata definitions from XML schemas, query the validity of DOM operations, and validate the DOM documents or subtrees against an XML schema. Because validation is based on a schema, you must convert a document type definition (DTD) to a schema before using these functions.

##### 34.1.2.2 XSLT Standard for XDK for Java

The XDK XSLT processor supports the current recommendations of XSLT 2.0, XPath 2.0, and the shared XPath/XQuery data model.

Oracle XML Development Kit (XDK) supports the XSLT 2.0 (W3C Recommendation, 23 January 2007) as a basic XSLT processor, with the following limitation: Support for `xsl:key` and `xsl:sort` behavior is at the XSLT 1.0 level.

**See Also:**

- [Basic XSLT Processor](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xslt20basicconform)

- [XSL Transformations (XSLT) Version 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xslt)

##### 34.1.2.3 JAXB Standard for XDK for Java

Features not supported by the XDK implementation of the Java Architecture for XML Binding (JAXB) specification are described.

The XDK implementation of the Java Architecture for XML Binding (JAXB) specification does not support these features:

- Javadoc generation

- XML Schema component `any` and substitution groups

##### 34.1.2.4 Pipeline Definition Language Standard for XDK for Java

Differences between the XML Pipeline processor and the W3C Note are presented.

The two differ as follows:

- The parser processes `DOMParserProcess` and `SAXParserProcess` are included in the XML pipeline (Section 1).

- Only the final target output is checked to see if it is up-to-date with the available pipeline inputs. The XML Pipeline processor does not determine whether the intermediate outputs of every process are up-to-date (Section 2.2).

- For the `select` attribute, anything in between double quotation marks ("...") is considered to be a string literal.

- The XML Pipeline processor throws an error if more that one process produces the same infoset (Section 2.4.2.3).

- The `<document>` element is not supported (Section 2.4.2.8).

### 34.2 Character Sets Supported by XDK

The character sets supported by XDK for Java and XDK for C are described.

#### 34.2.1 Character Sets Supported by XDK for Java

The character-set encodings supported by XDK for Java are described.

XML Schema processor for Java supports documents in these encodings:

- BIG

- EBCDIC-CP-\*

- EUC-JP

- EUC-KR

- GB2312

- ISO-2022-JP

- ISO-2022-KR

- ISO-8859-1to -9

- ISO-10646-UCS-2

- ISO-10646-UCS-4

- KOI8-R

- Shift_JIS

- US-ASCII

- UTF-8

- UTF-16

#### 34.2.2 Character Sets Supported by XDK for C

XDK for C supports over 300 Internet Assigned Numbers Authority (IANA) character sets.

These character sets include:

- UTF-8

- UTF-16

- UTF16-BE

- UTF16-LE

- US-ASCII

- ISO-10646-UCS-2

- ISO-8859-{1-9, 13-15}

- EUC-JP

- SHIFT_JIS

- BIG5

- GB2312

- GB_2312-80

- HZ-GB-2312

- KOI8-R

- KSC5601

- EUC-KR

- ISO-2022-CN

- ISO-2022-JP

- ISO-2022-KR

- WINDOWS-{1250-1258}

- EBCDIC-CP-{US,CA,NL,WT,DK,NO,FI,SE,IT,ES,GB,FR,HE,BE,CH,ROECE,YU,IS,AR}

- IBM{037, 273, 277, 278, 280, 284, 285, 297, 420, 424, 437, 500, 775, 850, 852, 855, 857, 858, 860, 861, 863, 865, 866, 869, 870, 871, 1026, 01140, 01141, 01142, 01143, 01144, 01145, 01146, 01147,01148}

You can use any alias of the preceding character sets. In addition, you can use any character set specified in [Oracle Database Globalization Support Guide](../nlspg/appendix-A-locale-data.md), except for IW7IS960.
