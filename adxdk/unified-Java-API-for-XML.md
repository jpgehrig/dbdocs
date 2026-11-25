The Unified Java application program interface (API) for Extensible Markup Language (XML) is presented. The APIs that are unified for Oracle XML DB and Oracle XML Developer's Kit (XDK) are described.

### 10.1 Overview of Unified Java API for XML

With the Unified Java API for XML, you can use the core Java DOM APIs required by both Oracle XML DB and XDK. You can also use the new Java classes that provide extra functionality that is built on top of the Java DOM API.

Unified Java API for XML combines the functionality required by both Oracle XML DB and XDK. Oracle XML DB implements the Java Document Object Model (DOM) API using the Java package `oracle.xdb.dom` and XDK implements it using the `oracle.xml.parser.v2` package.

You can use Unified Java API regardless of where your XML data resides (within the database or outside it), because Unified Java API uses a session pool model of connection management. If you do not specify the connection type as thick (which uses OCI APIs and is C-based) or thin (which uses Java Database Connectivity (JDBC) APIs and is purely Java-based), then a Java DOM API is used to connect to a local document object that resides outside the database.

**See Also:**

[Oracle Database XML Java API Reference](../jaxml/index.md) for information about the `oracle.xml.parser.v2` package

### 10.2 Component Unification

Some components that were supported only by the thick connection or only by the thin connection have been unified in Unified Java API for XML.

Those that were supported only by the thin connection and have been unified include the following:

- DOM Parser

- Java API for XML Processing (JAXP) Transformer

- XML SQL Utility (XSU)

- Extensible Stylesheet Language Transformation (XSLT)

### 10.3 About Moving to the Unified Java API

Unified Java API provides new Java classes that replace the old `oracle.xdb.dom` Java classes. All classes in the `oracle.xdb.dom` package are deprecated. If you are using deprecated classes, you must migrate to Unified Java API and use `oracle.xml.parser.v2` classes instead.

#### 10.3.1 Java DOM APIs for XMLType Classes

The Java DOM APIs for XMLType classes are listed, together with their deprecated equivalents.

Table 10-1 lists the `oracle.xdb.dom` package classes that were deprecated in Oracle Database 11g Release 1 (11.1) and their Unified Java API for XML equivalents.

Table 10-1 Deprecated XDB Package Classes and Their Unified Java API Equivalents

| Deprecated oracle.xdb.dom.\* Class | Equivalent oracle.xml.parser.v2 (Unified Java API) Class |
|:-----------------------------------|:---------------------------------------------------------|
| `XDBAttribute`                     | `XMLAttr`                                                |
| `XDBBinaryDocument`                | None                                                     |
| `XDBCData`                         | `XMLCDATA`                                               |
| `XDBCharData`                      | `CharData`                                               |
| `XDBComment`                       | `XMLComment`                                             |
| `XDBDocFragment`                   | `XMLDocumentFragment`                                    |
| `XDBDocument`                      | `XMLDocument`                                            |
| `XDBDocumentType`                  | `DTD`                                                    |
| `XDBDOMException`                  | `XMLDomException`                                        |
| `XDBDomImplementation`             | `XMLDomImplementation`                                   |
| `XDBDOMNotFoundErrException`       | None                                                     |
| `XDBElement`                       | `XMLElement`                                             |
| `XDBEntity`                        | `XMLEntity`                                              |
| `XDBEntityReference`               | `XMLEntityReference`                                     |
| `XDBNamedNodeMap`                  | `XMLAttrList`                                            |
| `XDBNode`                          | `XMLNode`                                                |
| `XDBNotation`                      | `XMLNotation`                                            |
| `XDBNotImplementedException`       | None                                                     |
| `XDBProcInst`                      | `XMLPI`                                                  |
| `XDBText`                          | `XMLText`                                                |

When you use the Java DOM API to retrieve XML data, you get either an `XMLDocument` instance (if the connection is thin) or an `XDBDocument` instance with method `getDOM()` and an `XMLDocument` instance with method `getDocument()`. Both `XMLDocument` and `XDBDocument` are instances of the World Wide Web Consortium (W3C) DOM interface. The `getDOM()` method and `XDBDocument` class have been deprecated in the Unified Java API for XML.

Table 10-2 lists the deprecated XMLType methods and their Unified Java API equivalents.

Table 10-2 Deprecated XMLType Methods and Their Unified Java API Equivalents

| Deprecated oracle.xdb.XMLType API | Equivalent oracle.xdb.XMLType (Unified Java) API                                                           |
|:----------------------------------|:-----------------------------------------------------------------------------------------------------------|
| `getDOM()`                        | `getDocument()`                                                                                            |
| `public XMLType createXML(...)`   | `public XMLType createXML(..., int kind)` where `kind` is either `XMLDocument.THICK` or `XMLDocument.THIN` |

#### 10.3.2 Extension APIs

In addition to the W3C Recommendation, the Unified Java API for XML implementation provides extension APIs that extend the W3C DOM APIs. You can use the Oracle-specific extension APIs for performing basic functions (like connecting to a database) and performance enhancement.

`XMLDocument` is a class that represents the DOM for the instantiated XML document. Retrieve the `XMLType` value from the XML document using the `XMLType` constructor that takes a `Document` argument. For example:

    XMLType createXML(Connection conn, Document domdoc)

To dereference a node manually—that is, to explicitly dereference a document fragment from the DOM tree—use the `freeNode()` extension API in the `oracle.xml.parser.v2` package (`XMLNode` class).

#### 10.3.3 Document Creation Java APIs

A Java API that creates an `XMLDocument` must create either a thin document or a thick document. Because a thick document needs a `Connection` object to establish communication with the database, each document creation API is extended to accept a `Connection` object.

For an `XMLType.createXML` API, you must specify a `Connection` type, which determines the type of object. Old document creation APIs (provided only for backward compatibility), create thin (pure Java) objects unless you specify otherwise.

Table 10-3 lists the `XMLDocument` output, based on `KIND` and `CONNECTION`.

Table 10-3 XMLDocument Output Based on KIND and CONNECTION

| XMLDocument.KIND    | XMLDocument.CONNECTION   | XMLDocument                                                                                                                                                     |
|:--------------------|:-------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `XMLDocument.THICK` | Thick or KPRB connection | Thick DOM                                                                                                                                                       |
| `XMLDocument.THICK` | Thin or no connection    | Exception                                                                                                                                                       |
| `XMLDocument.THIN`  | Any connection type      | Thin DOM                                                                                                                                                        |
| Not specified       | Any connection type      | Non-`XMLType` APIs: Thin DOM<br>`XMLType.createXML` APIs: Determined by connection type—Thick DOM for OCI or KPRB connection, and Thin DOM for Thin connection. |

These objects, methods, and classes are available for document creation in the unified Java API:

- `DOMParser` object and `parse()` method

  Use the `DOMParser` object and `parse()` method to parse XML documents. You must specify object type—thick or thin. For a thick object, you must also provide the `Connection` type, using the `DOMParser.setAttribute()` API. For example:

      DOMParser parser = new oracle.xml.parser.v2.DOMParser();
      parser.setAttribute(XMLDocument.KIND, XMLDocument.THICK);
      parser.setAttribute(XMLDocument.CONNECTION, conn);

- `DocumentBuilder` object and `DocumentBuilderFactory` class

  Use the `DocumentBuilder` object to parse XML documents using the Java-specific API, JAXP.

  You must create a DOM parser factory with the `DocumentBuilderFactory` class. `DocumentBuilder` builds DOM from input SAX events, taking the Connection from a property set on the `DocumentBuilderFactory`. For example:

      DocumentBuilderFactory.setAttribute(XMLDocument.CONNECTION, conn);
      DocumentBuilderFactory.setAttribute(XMLDocument.KIND,XMLDocument.THICK);

  `DocumentBuilderFactory` passes the connection to the `DOMParser` object that creates the document from these APIs:

      DocumentBuilder.newDocument()
      DocumentBuilder parse(InputStream)
      DocumentBuilder parse(InputStream, int)
      DocumentBuilder.parse(InputSource)

- XSU methods

  Each XSU method returns an `XMLDocument` to the user. You can specify whether the user wants a thick or thin object. For example:

      OracleXMLUtil util = new OracleXMLUtil(...);
      util.setAttribute(XMLDocument.KIND, XMLDocument.THICK);
      util.setAttribute(XMLDocument.CONNECTION, conn);
      Document doc = util.getXMLDOMFromStruct(struct, enc);

      OracleXMLQuery query = new OracleXMLQuery(...);
      query.setAttribute(XMLDocument.KIND, XMLDocument.THICK);
      query.setAttribute(XMLDocument.CONNECTION, conn);
      Document doc = query.getXMLDOM (root, meta);

      OracleXMLDocGenDOM dgd = new OracleXMLDocGenDOM(...);
      dgd.setAttribute(XMLDocument.KIND, XMLDocument.THICK);
      dgd.setAttribute(XMLDocument.CONNECTION, conn);
      Document doc = dgd.getXMLDocumentDOM(struct, enc);

- `XMLType` methods

  You can use the `XMLType.createXML` method to specify the type of the document (thin or thick) that you want the `getDocument()` method to get. In this example, the connection is inferred from `OPAQUE`:

      XMLType xt = XMLType.createXML(orset.getOPAQUE(1), XMLDocument.THICK);
      Document doc = xt.getDocument();

**Note:**

You cannot specify the type of an `XMLType` object returned by `ResultSet.getObject()`. The object type is determined by the `Connection` used in the JDBC call that fetches the `ResultSet` from the `XMLType` column.
