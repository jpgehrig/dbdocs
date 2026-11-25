### attribute

A property of an element that consists of a name and a value separated by an equal sign and contained within the start-tags after the element name.

In this example, `<Price units='USD'>5</Price>`, units is the attribute and USD is its value, which must be in single or double quotation marks. Attributes can reside in the document or document type definition (DTD). Elements may have many attributes but their retrieval order is not defined.

### binary XML

An Extensible Markup Language (XML) representation that uses a compact, XML schema-aware format.

### callback

A programmatic technique in which one process starts another and then continues. The second process then invokes the first as a result of an action, value, or other event. This technique is used in most programs that have a user interface to allow continuous interaction.

### cartridge

A stored program in Java or Procedural Language/Structured Query Language (PL/SQL) that adds the necessary functionality for the database to understand and manipulate a new data type.

Cartridges interface through the Extensibility Framework within the Oracle XML Developer's Kit (XDK) implementation of the Java Architecture for XML Binding (JAXB) specification version 8 or later. Oracle Text is such a cartridge, adding support for reading, writing, and searching text documents stored within the database.

See also Oracle Text.

### Cascading Style Sheets (CSS)

See CSS.

### CDATA

Character data. Text in a document that must not be parsed is included within a `CDATA` section. This allows for the inclusion of characters that would otherwise have special functions, such as `&`, `<`, and `>`. `CDATA` sections can be used in the content of an element or in attributes.

### character data (CDATA)

See CDATA.

### child element

An element that is wholly contained within another, which is referred to as its parent element. For example `<Parent><Child></Child></Parent>` shows a child element nested within its parent element.

See also parent element.

### class generator

A class generator accepts an input file and creates a set of output classes that have corresponding functionality. For the XML class generator, the input file is a DTD or XML schema, and the output is a series of classes that can be used to create conforming XML documents.

### CLASSPATH

The operating system environment variable that the Java virtual machine (JVM) uses to find the classes required to run applications.

### Common Oracle Runtime Environment (CORE)

See CORE.

### CORE

Common Oracle Runtime Environment. The library of functions written in C that enables developers to create code that can be easily ported to virtually any platform and operating system.

### CSS

Cascading Style Sheets. A simple mechanism for adding style (fonts, colors, spacing, and so on) to web documents.

### data definition language (DDL)

See DDL.

### datagram

A text fragment, possibly in XML format, that is returned to the requester embedded in an HTML page from a SQL query processed by the XSQL servlet.

### DDL

Data definition language. Statements that define or change a data structure.

### DOCTYPE

The term used as the tag name designating the DTD or its reference within an XML document. For example, `<!DOCTYPE person SYSTEM "person.dtd">` declares the root element name as person and an external DTD as person.dtd in the file system. Internal DTDs are declared within the DOCTYPE declaration.

### Document Object Model (DOM)

See DOM.

### document type definition (DTD)

See DTD.

### DOM

Document Object Model. An in-memory, tree-based object representation of an XML document that enables programmatic access to its elements and attributes.

The Document Object Model (DOM) object and its interface is a World Wide Web Consortium (W3C) recommendation that specifies the DOM of an XML document, including the application programming interfaces (APIs) for programmatic access. DOM views the parsed document as a tree of objects.

### DTD

Document type definition. A set of rules that defines the valid structure of an XML document. DTDs are text files that derive their format from SGML. A DTD can be included in an XML document by using the `DOCTYPE` element or by using an external file through a `DOCTYPE` reference.

**See Also:**

- XML

- SGML

- WML

### element

The basic logical unit of an XML document that can serve as a container for other elements, such as children, data, attributes, and their values. Elements are identified by start-tags, such as `<name>`, and end-tags, such as `</name>`, or for empty elements, `<name/>`.

### empty element

An element without text content or child elements. It can contain only attributes and their values. Empty elements are of the form `<name/>` or `<name></name>`, where there is no space between the tags.

### entity

A string of characters that can represent either another string of characters or special characters that are not part of the document character set. Entities and the text that is substituted for them by the parser are declared in the DTD.

### epilog

The closing part of an XML document. The epilog is optional.

### Extensible Markup Language (XML)

See XML.

### Extensible Stylesheet Language (XSL)

See XSL.

### Extensible Stylesheet Language Formatting Objects (XSL-FO)

See XSL-FO.

### Extensible Stylesheet Language Transformations (XSLT)

See XSLT.

### FOP

Formatting Objects Processor: a print formatter driven by XSL-FO. FOP is a Java application that reads a formatting object tree and renders the resulting pages. The supported output are PDF, PCL, PS, SVG, XML (area tree representation), print, AWT, MIF, and TXT. The primary output target is PDF.

### Formatting Objects Processor (FOP)

See FOP.

### HTTP

Hypertext Transport Protocol. The set of rules for exchanging files on the World Wide Web. Relative to the TCP/IP suite of protocols, HTTP is an application protocol.

### HTTPS

Hypertext Transport Protocol, Secure. The use of Secure Sockets Layer (SSL) as a sublayer under the regular HTTP application layer.

### Hypertext Transport Protocol (HTTP)

See HTTP.

### Hypertext Transport Protocol, Secure (HTTPS)

See HTTPS.

### IDE

Integrated Development Environment. A set of programs designed to aid in the development of software run from a user interface. Oracle JDeveloper is an IDE for Java development that includes an editor, a compiler, a debugger, a syntax checker, and a help system.

### infoset

XML Information Set, an abstract data set consisting of several information items. It has at least one information item: the document node, but the infoset is not necessarily valid XML.

The W3C recommendation is at [`http://www.w3.org/TR/xml-infoset/`](http://www.w3.org/TR/xml-infoset/).

### instance document

An XML document validated against an XML schema. If the instance document conforms to the rules of the schema, it is said to be valid.

### instantiate

A term used in object-based languages, such as Java and C++, to refer to the creation of an object of a specific class.

### Integrated Development Environment (IDE)

See IDE.

### Java EE

Java Platform, Enterprise Edition. The Java platform that defines multitier enterprise computing.

### Java

A high-level programming language where applications run in a virtual machine known as a Java Virtual Machine (JVM). The JVM is responsible for all interfaces to the operating system. This architecture lets developers create Java applications that can run on any operating system or platform that has a JVM.

**See Also:**

JVM.

### Java Platform, Enterprise Edition (Java EE)

See Java EE.

### Java API for XML Processing (JAXP)

See JAXP

### Java Architecture for XML Binding (JAXB)

See JAXB.

### Java Database Connectivity (JDBC)

See JDBC.

### Java Developer's Kit (JDK)

See JDK.

### Java Naming and Directory Interface (JNDI)

See JNDI.

### Java Specification Request (JSR)

See JSR.

### Java Virtual Machine (JVM)

See JVM.

### JavaBeans

An independent program module that runs within a Java Virtual Machine (JVM). It is typically used to create user interfaces on a client.

**See Also:**

JVM

### JAXB

Java Architecture for XML Binding. An API and tools that map to and from XML documents and Java objects. JAXB is a JSR-31 recommendation.

### JAXP

Java API for XML Processing. A programming tool that enables applications to parse and transform XML documents using an API that is independent of a particular XML processor implementation.

### JDBC

Java Database Connectivity. The programming API that enables Java applications to access a database through SQL. JDBC drivers are written in Java for platform independence, but are specific to each database.

### JDK

Java Developer's Kit. The collection of Java classes, runtime, compiler, debugger, and usually source code for a version of Java that makes up a Java development environment. JDKs are designated by versions.

### JNDI

Java Naming and Directory Interface. A programming interface for connecting Java programs to naming and directory services such as DNS, LDAP, and NDS.

### JSR

Java Specification Request. A recommendation of the Java Community Process organization (JCP), such as JAXB and XQJ.

### JVM

Java Virtual Machine. The Java interpreter that converts the compiled Java bytecode into the machine language of the platform and runs it. JVMs can run on a client, in a browser, in a middle tier, on an intranet, on an application server, or on a database server.

### listener

A separate application process that monitors the input process.

### marshalling

The process of traversing a Java content tree and writing an XML document that reflects the content of the tree. It is the inverse of unmarshalling.

See also unmarshalling.

### node

In XML, the term used to denote each addressable entity in a DOM tree.

### notation attribute declaration

In XML, the declaration of a content type that is not part of those understood by the parser. These types include audio, video, and other multimedia.

### OASIS

Organization for the Advancement of Structured Information Standards. An organization whose members are chartered with promoting public information standards through conferences, seminars, exhibits, and other educational events. XML and SGML are standards that OASIS is actively promoting.

**See Also:**

- SGML

- XML

### Oracle JDeveloper

Oracle JDeveloper is a Java IDE that enables application, applet, and servlet development and includes an editor, compiler, debugger, syntax checker, help system, integrated UML class modeler, and more. It supports XML-based development by including the XDK for Java components in its editor.

### Oracle Text

An Oracle tool that provides full-text indexing of documents and the capability to do SQL queries over documents, along with XPath-like searching.

### Oracle WebLogic Server

A product that integrates all the core services and features required for building, deploying, and managing high-performance, n-tier, transaction-oriented web applications within an open standards framework.

### XDK

Oracle XML Developer's Kit. The set of libraries, components, and utilities that provide software developers with the standards-based functionality to XML-enable their applications. In the Java components of XDK, the kit contains an XML parser, an XSLT processor, the XML class generator, the JavaBeans, and the XSQL servlet.

### Oracle XML DB

A high-performance XML storage and retrieval technology provided with Oracle Database. It is based on the W3C XML data model.

### Oracle XML Developer's Kit (XDK)

See XDK.

### ORACLE_HOME

The operating system environment variable that identifies the location for the installation of Oracle components.

### Organization for the Advancement of Structured Information Standards (OASIS)

See OASIS.

### parent element

An element that surrounds another element, which is referred to as its child element. For example, `<Parent><Child></Child></Parent>` shows a parent element wrapping its child element.

**See Also:**

child element

### parsed character data (PCDATA)

See PCDATA.

### path name

The name of a resource that reflects its location in the repository hierarchy.

A path name is composed of a root element (the first `/`), element separators (`/`), and various subelements (or path elements). A path element can be composed of any character in the database character set except the slash (`/`) or the backslash (`\`). These characters have a special meaning for Oracle XML DB. The slash is the default name separator in a path name; the backslash can be used to escape characters.

### PCDATA

Parsed character data. The element content consisting of text that must be parsed but is not part of a tag or nonparsed data.

See also tag.

### prolog

The opening part of an XML document containing the XML declaration and any DTD or other declarations needed to process the document. The prolog is optional.

### repository

The set of database objects, in any schema, that are mapped to path names. There is one root to the repository (/), which contains a set of resources, each with a path name.

**See Also:**

path name

### resource

An object in the repository hierarchy.

### resource name

The name of a resource within its parent folder. Resource names must be unique (potentially subject to case-insensitivity) within a folder. Resource names are always in the UTF-8 character set (`NVARCHAR2`).

### result set

The output of a SQL query consisting of one or more rows of data.

### root element

The element that encloses all the other elements in an XML document and is between the optional prolog and epilog. An XML document is permitted to have only one root element.

**See Also:**

- prolog

- epilog

### SAX

Simple API for XML. An XML standard interface provided by XML parsers and used by event-based applications.

### schema

The definition of the structure and data types within a database. It can also refer to an XML document that supports the XML Schema W3C recommendation.

### servlet

A Java application that runs in a server, typically a web server or an application server, and performs processing on that server. Servlets are the Java equivalent to CGI scripts.

### SGML

Standard Generalized Markup Language. An ISO standard for defining the format of a text document implemented using markup and DTDs.

### Simple API for XML (SAX)

See SAX.

### Simple Object Access Protocol (SOAP)

See SOAP.

### SOAP

Simple Object Access Protocol. An XML-based protocol for exchanging information in a decentralized, distributed environment.

### SQL

Structured Query Language. The standard language used to access and process data in a relational database.

### SQL/XML

An ANSI specification for representing XML in SQL. Oracle SQL includes SQL/XML functions that query XML: ANSI/ISO/IEC 9075-14:2011, Information technology—Database languages—SQL—Part 14: XML-Related Specifications (SQL/XML).

### Standard Generalized Markup Language (SGML)

See SGML.

### StAX

Streaming API for XML.

### Streaming API for XML (StAX)

See StAX.

### Structured Query Language (SQL)

See SQL.

### stylesheet

An XML document that consists of XSL processing instructions used by an XSLT processor to transform or format an input XML document into an output XML document.

### tag

A single piece of XML markup that delimits the start or end of an element. Tags start with `<` and end with `>`. XML includes start-tags (`<``name``>`), end-tags (`</``name``>`), and empty tags (`<``name``/>`), where `name` is the tag name.

### TransX Utility

A Java API that simplifies the loading of translated seed data and messages into a database.

### Uniform Resource Identifier (URI)

See URI.

### Uniform Resource Locator (URL)

See URL.

### unmarshalling

The process of reading an XML document and constructing a tree of Java content objects. Each content object corresponds directly to an instance in the input document of the corresponding schema component.

See also marshalling.

### URI

Uniform Resource Identifier. The address syntax that is used to create URLs and XPaths.

### URL

Uniform Resource Locator. The address that defines the location and route to a file on the Internet. URLs are used by browsers to navigate the World Wide Web and consist of a protocol prefix, port number, domain name, directory and subdirectory names, and a file name.

### valid

The term used to refer to an XML document when its structure and element content is consistent with that declared in its associated DTD or XML schema.

### W3C

World Wide Web Consortium. An international industry consortium started in 1994 to develop standards for the World Wide Web. The W3C Web site is located at `http://www.w3c.org`.

See also WWW.

### well-formed

An XML document that conforms to the syntax of the XML version declared in its XML declaration. This includes having a single root element and properly nested tags.

### Wireless Markup Language (WML)

See WML.

### WML

Wireless Markup Language. A tag-based markup language developed for the small display size, reduced memory, and limited processing power of cell phones and other devices that implement the Wireless Application Protocol (WAP) specification. WML documents are XML documents that validate against the WML DTD.

See also DTD.

### Working Group (WG)

A W3C committee that is made up of industry members who implement the recommendation process in specific Internet technology areas.

### World Wide Web (WWW)

See WWW.

See also W3C.

### World Wide Web Consortium (W3C)

See W3C.

See also WWW.

### WWW

World Wide Web. A worldwide hypertext system that uses the Internet and the HTTP protocol.

See also W3C.

### XDM

The W3C XQuery 1.0 and XPath 2.0 Data Model. A query data model that supports the most XQuery features. The main exceptions are the query prolog, element and attribute constructors, full `FLWOR` syntax, and the typeswitch expression.

### XLink

XML Linking Language. It consists of rules that govern the use of hyperlinks in XML documents. The rules are defined by the XML Linking Group, under the W3C recommendation process. This is one of the three languages (XLink, XPointer, and XPath) that XML supports to manage document presentation and hyperlinks.

**See Also:**

- XPath

- XPointer

### XML

Extensible Markup Language. An open standard for describing data developed by the World Wide Web Consortium (W3C) using a subset of the SGML syntax and designed for Internet use.

**See Also:**

- SGML

- W3C

### XML Base

A W3C recommendation that describes the use of the `xml:base` attribute, which can be inserted in an XML document to specify a base `URI` other than the base URI of the document or external entity. The `URI`s in the document are resolved by the given base.

### XML Information Set

See infoset.

### XML Linking Language (XLink)

See XLink.

### XML Namespaces

Related element names or attributes within an XML document. Namespace syntax and usage are defined by a W3C recommendation. For example, element `<xsl:apply-templates/>` is identified as part of the XSL namespace. Namespaces are declared in an XML document or a DTD before they are used, using this attribute syntax: `xmlns:xsl="http://www.w3.org/TR/WD-xsl".`

### XML parser

A software program that receives an XML document and determines whether it is well-formed and, optionally, valid. The Oracle XML parser supports both SAX and DOM interfaces.

**See Also:**

well-formed

### XML Path Language (XPath)

See XPath.

### XML Pipeline Definition Language

A W3C recommendation that enables you to describe the processing relations between XML resources.

### XML Pointer Language (XPointer)

See XPointer.

### XML processor

A software program that reads an XML document and processes it, that is, performs actions on the document based on a set of rules. Validity checkers and XML editors are examples of processors.

### XML Query (XQuery)

See XQuery.

### XML schema

A document written in the XML Schema language.

### XML Schema

See XML Schema language.

### XML Schema Definition

Equivalent to XML Schema language.

### XML Schema language

The XML Schema language, also called XML Schema, is a W3C recommendation for the use of simple data types and complex structures within an XML document. It addresses areas currently lacking in DTDs, including the definition and validation of data types.

### XML Schema processor

A software program that automatically ensures the validity of XML documents and data used in e-business applications, including online exchanges. It adds simple and complex data types to XML documents, and replaces DTD functionality with an XML schema definition XML document.

### XMLSchema-instance namespace

The namespace declaration attribute used to identify an instance document as a member of the class defined by a particular XML schema. You must declare the XMLSchema-instance namespace by adding a namespace declaration to the root element of the instance document. For example: `xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance`.

### XML SQL Utility (XSU)

See XSU.

### XMLType

An Oracle data type that stores XML data using object-relational columns or a binary format within a table or view.

### XMLType views

A mechanism provided by Oracle XML DB to wrap existing relational and object-relational data in XML format. This is especially useful if, for example, your legacy data is not in XML but you must migrate it to an XML format.

### XPath

XML Path Language. The open standard syntax for addressing elements within a document used by XSL and XPointer. XPath is a W3C recommendation. It specifies the data model and grammar for navigating an XML document used by XSLT, XLink, and XML Query.

**See Also:**

- XLink

- XPointer

- XQuery

### XPointer

XML Pointer Language. The term and W3C recommendation to describe a reference to an XML document fragment. An XPointer can be used at the end of an XPath-formatted URI. It specifies the identification of individual entities or fragments within an XML document using XPath navigation.

**See Also:**

- XLink

- XPath

### XQJ

XQuery API for Java.

### XQSX

XQuery Scripting Extension.

### XQuery

XML Query. The ongoing effort of W3C to create a standard for the language and syntax to query XML documents.

### XQueryX

XML Syntax for XQuery. XQueryX is an XML representation of an XQuery. See JSR 225.

### XQUF

XQuery Update Facility.

### XQVM

Oracle XQuery Virtual Machine.

### XSL

Extensible Stylesheet Language. The language used within stylesheets to transform or render XML documents. Two W3C recommendations cover XSL stylesheets: XSL Transformations (XSLT) and XSL Formatting Objects (XSL-FO).

- XSLT is a language for transforming one XML document into another.

- XSL-FO is an XML vocabulary for specifying the presentation of an XML document.

An XSL stylesheet specifies the presentation of a class of XML documents by describing how an instance of the class is transformed into an XML document that uses the formatting vocabulary.

**See Also:**

- XSLT

- XSL-FO

### XSL-FO

XSL Formatting Objects. Also known as Extensible Stylesheet Language Formatting Objects, and XSLFO. The W3C standard specification that defines an XML vocabulary for specifying formatting semantics.

**See Also:**

FOP.

### XSL Formatting Objects (XSL-FO)

See XSL-FO.

### XSL Transformations (XSLT)

See XSLT.

### XSLT

Extensible Stylesheet Language Transformations. Also known as XSL-T. The XSL W3C standard specification that defines a transformation language to convert one XML document into another.

### XSLT Virtual Machine (XVM)

Also XSLT VM. See XVM.

### XSLTVM

Also XSLT VM. See XVM.

### XSQL pages

XML pages that contain instructions for the XSQL servlet.

### XSQL pages publishing framework

See XSQL servlet.

### XSQL servlet

A Java-based servlet that can dynamically generate XML documents from one or more SQL queries and optionally transform the documents in the server with an XSLT stylesheet.

### XSU

XML SQL Utility. An Oracle utility that can generate an XML document (string or DOM) when given a SQL query or a JDBC `ResultSet` object. XSU can also extract the data from an XML document, and then insert, update, or delete rows in a database table.

### XVM

XSLT Virtual Machine. Also known as XSLTVM and XSLT VM. The Oracle XSLT Virtual Machine is the software implementation of a CPU designed to run compiled XSLT code. The virtual machine concept assumes a compiler compiling XSLT stylesheets to a program of bytecodes, or machine instructions for the XSLT CPU.
