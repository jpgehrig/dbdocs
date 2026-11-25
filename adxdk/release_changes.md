This preface lists changes in Oracle XML Developer's Kit Programmer's Guide.

### Changes in Oracle XML Developer’s Kit Release 18c, Version 1

#### Deprecated Features

For Oracle Database Release 18c, Version 1, these features are deprecated, and may be desupported in a future release.

##### DBMS_XMLQUERY PL/SQL Package

PL/SQL Package `DBMS_XMLQUERY` is deprecated. Use package `DBMS_XMLGEN` instead.

##### DBMS_XMLSAVE PL/SQL Package

PL/SQL Package `DBMS_XMLSAVE` is deprecated. Use package `DBMS_XMLSTORE` instead.

### Changes in Oracle XML Developer’s Kit 12c Release 2 (12.2.0.1)

#### New Features

The following features are new in this release.

##### XSL 2.0 Support

XDK now provides complete support for the W3C XSL 2.0 standard.

##### XQuery 3.0 Support

XDK now provides limited support for the forthcoming XQuery 3.0 recommendation.

### Changes in Oracle XML Developer's Kit 12c Release 1 (12.1.0.1)

#### New Features

For Oracle Database 12c Release 1 (12.1.0.1), Oracle XML Developer's Kit Programmer's Guide documents these new features of XDK:

##### Oracle XQuery Processor for Java

XDK includes an XQuery 1.0 processor for Java, which lets Java applications query, transform, and update Extensible Markup Language (XML) directly in the Java Virtual Machine (JVM).

For more information, see [Using the XQuery Processor for Java](using-xquery-processor-for-Java.md).

##### XDK/J Support for Fast Infoset

XDK adds support for the Fast Infoset to XDK/J model. This support enables developers to use Fast Infoset techniques while working with XML content in Java. The Fast Infoset model is a popular technique for working with XML content in Java.

For more information, see [DOM Support for Fast Infoset](XML-parsing-for-Java.md).

##### XDK/J DOM Improvements

XDK adds support for World Wide Web Consortium (W3C) document object model (DOM) Level 3 Core application programming interfaces (APIs). This support lets developers maximize the benefits of the latest W3C APIs for XML processing, including the APIs that are defined as part of the DOM Level 3.0 Core specification.

For more information, see [XDK Java DOM Improvements](XML-parsing-for-Java.md).

##### XMLDiff Support for XDK Java

XDK supports a Java-based XMLDiff that is format-compatible with C and PL/SQL XMLDiff, which were introduced in Oracle Database 11g Release 1 (11.1). This support lets pure Java programs in the middle tier exchange XMLDiff output with C programs or with programs that use Oracle Database to perform XMLDiff operations.

For more information, see [Determining XML Differences Using Java](determining-XML-differences-using-Java.md).

#### Deprecated Features

For Oracle Database 12c Release 1 (12.1.0.1), these features are deprecated, and may be desupported in a future release.

##### XML Developer's Kit JavaBeans

For Oracle Database 12c Release 1 (12.1.0.1), these XDK JavaBeans are deprecated:

- DOMBuilder

- XSLTransformer

- DBAccess

- XMLDBAccess

- XMLDiff

- XMLCompress

- XSDValidator

For alternatives, see [Oracle XML Developer's Kit JavaBeans (Deprecated)](XDK-JavaBeans.md).

##### XML Developer's Kit for Java APIs

The XDK Java API packages and classes that correspond to deprecated XDK JavaBeans, are also deprecated, starting with Oracle Database 12c Release 1 (12.1.0.1).

These are the deprecated packages and classes:

- `oracle.xml.async`

- `oracle.xml.dbaccess`

- `oracle.xml.XMLDiff.BeanInfo`

- `oracle.xml.xmlcompl`

- `oracle.xml.xmldbaccess`

- `oracle.xml.schemavalidator`

For alternatives, see [Oracle Database XML Java API Reference](../jaxml/index.md).
