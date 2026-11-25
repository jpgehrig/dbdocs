Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](SAXAttrList.md)**
- **[Next Class](XMLAttr.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xml.parser.v2**

## **Class SAXParser**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLParser](XMLParser.md)**

  - - **oracle.xml.parser.v2.SAXParser**

<!-- -->

- **All Implemented Interfaces:**
  **[Parser](../../../../org/xml/sax/Parser.md), [XMLReader](../../../../org/xml/sax/XMLReader.md)**

  ------------------------------------------------------------------------

  **
  **

      public class SAXParser
      extends XMLParser
      implements XMLReader, Parser

  **This class implements an eXtensible Markup Language (XML) 1.0 SAX parser according to the World Wide Web Consortium (W3C) [recommendation](http://www.w3.org/TR/1998/REC-xml-19980210). Applications can register a [SAX](http://www.megginson.com/SAX/index.html) handler to receive notification of various parser events.**
  **XMLReader is the interface that an XML parser's SAX2 driver must implement. This interface allows an application to set and query features and properties in the parser, to register event handlers for document processing, and to initiate a document parse.**

  **All SAX interfaces are assumed to be synchronous: the parse methods must not return until parsing is complete, and readers must wait for an event-handler callback to return before reporting the next event.**

  **This interface replaces the (now deprecated) SAX 1.0 Parser interface. The XMLReader interface contains two important enhancements over the old Parser interface:**

  1.  **it adds a standard way to query and set features and properties; and**
  2.  **it adds Namespace support, which is required for many higher-level XML standards.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                 |
    |---------------------------|-------------------------------------------------------|
    | `static java.lang.String` | `REPORT_CHARS_CHUNKS`<br>Report characters in chunks. |

    -

      ### **Fields inherited from class oracle.xml.parser.v2.[XMLParser](XMLParser.md)**

      **[`BASE_URL`](XMLParser.md)`, `[`BASE_URL_ID`](XMLParser.md)`, `[`CONTENT_MODEL_DETERMINISTIC`](XMLParser.md)`, `[`DEFAULT_ENTITY_EXPANSION_DEPTH`](XMLParser.md)`, `[`DEFAULT_ENTITY_EXPANSION_DEPTH_SECURE`](XMLParser.md)`, `[`DTD_OBJECT`](XMLParser.md)`, `[`DTD_OBJECT_ID`](XMLParser.md)`, `[`ENTITY_EXPANSION_DEPTH`](XMLParser.md)`, `[`ENTITY_EXPANSION_DEPTH_ID`](XMLParser.md)`, `[`EXPAND_ENTITYREF`](XMLParser.md)`, `[`EXPAND_ENTITYREF_ID`](XMLParser.md)`, `[`IGNORE_DUPLICATE_ID`](XMLParser.md)`, `[`PARSER`](XMLParser.md)`, `[`PARSER_CDATA`](XMLParser.md)`, `[`PARSER_DTD`](XMLParser.md)`, `[`RESOLVE_ENTITY_DEFAULT`](XMLParser.md)`, `[`RESOLVE_ENTITY_DEFAULT_ID`](XMLParser.md)`, `[`SCHEMA_LANGUAGE`](XMLParser.md)`, `[`SCHEMA_LANGUAGE_ID`](XMLParser.md)`, `[`SCHEMA_OBJECT`](XMLParser.md)`, `[`SCHEMA_OBJECT_ID`](XMLParser.md)`, `[`SCHEMA_SOURCE`](XMLParser.md)`, `[`SCHEMA_SOURCE_ID`](XMLParser.md)`, `[`STANDALONE`](XMLParser.md)`, `[`STANDALONE_ID`](XMLParser.md)`, `[`USE_DTD_ONLY_FOR_VALIDATION`](XMLParser.md)`, `[`USE_DTD_ONLY_FOR_VALIDATION_ID`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_DEFAULT`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_ID`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_SECURE`](XMLParser.md)`, `[`XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING`](XMLParser.md)`, `[`XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING_ID`](XMLParser.md)`, `[`XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC`](XMLParser.md)`, `[`XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC_ID`](XMLParser.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                     |
    |-------------------------------------------------|
    | `SAXParser``()`<br>Creates a new parser object. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                             | Method and Description                                                                                                                                            |
    |---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md) | `getContentHandler``()`<br>Return the current content handler.                                                                                                    |
    | [`DTDHandler`](../../../../org/xml/sax/DTDHandler.md)         | `getDTDHandler``()`<br>Return the current DTD handler.                                                                                                            |
    | `boolean`                                                     | `getFeature``(java.lang.String name)`<br>Look up the value of a feature.                                                                                          |
    | `java.lang.Object`                                            | `getProperty``(java.lang.String name)`<br>Look up the value of a property.                                                                                        |
    | `void`                                                        | `setContentHandler``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` handler)`<br>Allow an application to register a content event handler.       |
    | `void`                                                        | `setDocumentHandler``(`[`DocumentHandler`](../../../../org/xml/sax/DocumentHandler.md)` handler)`<br>Deprecated. <br>as of SAX2.0 - Replaced by setContentHandler |
    | `void`                                                        | `setDTDHandler``(`[`DTDHandler`](../../../../org/xml/sax/DTDHandler.md)` handler)`<br>Allow an application to register a DTD event handler.                       |
    | `void`                                                        | `setFeature``(java.lang.String name, boolean value)`<br>Set the state of a feature.                                                                               |
    | `void`                                                        | `setProperty``(java.lang.String name, java.lang.Object value)`<br>Set the value of a property.                                                                    |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLParser](XMLParser.md)

      [`getAttribute`](XMLParser.md)`, `[`getBaseURL`](XMLParser.md)`, `[`getEntityResolver`](XMLParser.md)`, `[`getErrorHandler`](XMLParser.md)`, `[`getReleaseVersion`](XMLParser.md)`, `[`getValidationMode`](XMLParser.md)`, `[`getValidationModeValue`](XMLParser.md)`, `[`getXMLProperty`](XMLParser.md)`, `[`isXMLPropertyReadOnly`](XMLParser.md)`, `[`isXMLPropertySupported`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`reset`](XMLParser.md)`, `[`setAttribute`](XMLParser.md)`, `[`setAttribute`](XMLParser.md)`, `[`setBaseURL`](XMLParser.md)`, `[`setDoctype`](XMLParser.md)`, `[`setEntityResolver`](XMLParser.md)`, `[`setErrorHandler`](XMLParser.md)`, `[`setLocale`](XMLParser.md)`, `[`setPreserveWhitespace`](XMLParser.md)`, `[`setSchemaValidationMode`](XMLParser.md)`, `[`setSchemaValidatorProperty`](XMLParser.md)`, `[`setSecureProcessing`](XMLParser.md)`, `[`setValidationMode`](XMLParser.md)`, `[`setValidationMode`](XMLParser.md)`, `[`setXMLProperty`](XMLParser.md)`, `[`setXMLSchema`](XMLParser.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[XMLReader](../../../../org/xml/sax/XMLReader.md)

      [`getEntityResolver`](../../../../org/xml/sax/XMLReader.md)`, `[`getErrorHandler`](../../../../org/xml/sax/XMLReader.md)`, `[`parse`](../../../../org/xml/sax/XMLReader.md)`, `[`parse`](../../../../org/xml/sax/XMLReader.md)`, `[`setEntityResolver`](../../../../org/xml/sax/XMLReader.md)`, `[`setErrorHandler`](../../../../org/xml/sax/XMLReader.md)

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[Parser](../../../../org/xml/sax/Parser.md)

      [`parse`](../../../../org/xml/sax/Parser.md)`, `[`parse`](../../../../org/xml/sax/Parser.md)`, `[`setEntityResolver`](../../../../org/xml/sax/Parser.md)`, `[`setErrorHandler`](../../../../org/xml/sax/Parser.md)`, `[`setLocale`](../../../../org/xml/sax/Parser.md)

<!-- -->

- - ### Field Detail

    - #### REPORT_CHARS_CHUNKS

          public static final java.lang.String REPORT_CHARS_CHUNKS

      Report characters in chunks. If this property is set to TRUE the parser reports characters in multiple call, if the data is large.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### SAXParser

          public SAXParser()

      Creates a new parser object.

  <!-- -->

  - ### Method Detail

    - #### setDocumentHandler

          public void setDocumentHandler(DocumentHandler handler)

      Deprecated. as of SAX2.0 - Replaced by setContentHandler
      SAX applications can use this to register a new document event handler.
      Specified by:
      [`setDocumentHandler`](../../../../org/xml/sax/Parser.md) in interface [`Parser`](../../../../org/xml/sax/Parser.md)

      Parameters:
      `handler` - `DocumentHandler` being registered

      See Also:
      [`Parser.setDocumentHandler(org.xml.sax.DocumentHandler)`](../../../../org/xml/sax/Parser.md), [`DocumentHandler`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### getFeature

          public boolean getFeature(java.lang.String name)
                             throws SAXNotRecognizedException,
                                    SAXNotSupportedException

      Look up the value of a feature.
      The feature name is any fully-qualified URI. It is possible for an XMLReader to recognize a feature name but to be unable to return its value; this is especially true in the case of an adapter for a SAX1 Parser, which has no way of knowing whether the underlying parser is performing validation or expanding external entities.

      All XMLReaders are required to recognize the http://xml.org/sax/features/namespaces and the http://xml.org/sax/features/namespace-prefixes feature names.

      Some feature values may be available only in specific contexts, such as before, during, or after a parse.

      Typical usage is something like this:

           XMLReader r = new MySAXDriver();

                                   // try to activate validation
           try {
             r.setFeature("http://xml.org/sax/features/validation", true);
           } catch (SAXException e) {
             System.err.println("Cannot activate validation.");
           }

                                   // register event handlers
           r.setContentHandler(new MyContentHandler());
           r.setErrorHandler(new MyErrorHandler());

                                   // parse the first document
           try {
             r.parse("http://www.foo.com/mydoc.xml");
           } catch (IOException e) {
             System.err.println("I/O exception reading XML document");
           } catch (SAXException e) {
             System.err.println("XML exception reading document.");
           }


      The feature "http://xml.org/sax/features/validation" due to its binary input value only controls DTD validation. The value true sets DTD validation to TRUE. This feature cannot be used to control XML Schema based validation

      Implementors are free (and encouraged) to invent their own features, using names built on their own URIs.

      Specified by:
      [`getFeature`](../../../../org/xml/sax/XMLReader.md) in interface [`XMLReader`](../../../../org/xml/sax/XMLReader.md)

      Parameters:
      `name` - The feature name, which is a fully-qualified URI.

      Returns:
      The current state of the feature (true or false).

      Throws:
      [`SAXNotRecognizedException`](../../../../org/xml/sax/SAXNotRecognizedException.md) - When the XMLReader does not recognize the feature name.

      [`SAXNotSupportedException`](../../../../org/xml/sax/SAXNotSupportedException.md) - When the XMLReader recognizes the feature name but cannot determine its value at this time.

      See Also:
      `setFeature(java.lang.String, boolean)`

    <!-- -->

    - #### setFeature

          public void setFeature(java.lang.String name,
                                 boolean value)
                          throws SAXNotRecognizedException,
                                 SAXNotSupportedException

      Set the state of a feature.
      The feature name is any fully-qualified URI. It is possible for an XMLReader to recognize a feature name but to be unable to set its value; this is especially true in the case of an adapter for a SAX1 [`Parser`](../../../../org/xml/sax/Parser.md), which has no way of affecting whether the underlying parser is validating, for example.

      All XMLReaders are required to support setting http://xml.org/sax/features/namespaces to true and http://xml.org/sax/features/namespace-prefixes to false.

      Some feature values may be immutable or mutable only in specific contexts, such as before, during, or after a parse.

      The feature "http://xml.org/sax/features/validation" due to its binary input value only controls DTD validation. The value true sets DTD validation to TRUE. This feature cannot be used to control XML Schema based validation

      Specified by:
      [`setFeature`](../../../../org/xml/sax/XMLReader.md) in interface [`XMLReader`](../../../../org/xml/sax/XMLReader.md)

      Parameters:
      `name` - The feature name, which is a fully-qualified URI.

      `value` - The requested value of the feature (true or false).

      Throws:
      [`SAXNotRecognizedException`](../../../../org/xml/sax/SAXNotRecognizedException.md) - When the XMLReader does not recognize the feature name.

      [`SAXNotSupportedException`](../../../../org/xml/sax/SAXNotSupportedException.md) - When the XMLReader recognizes the feature name but cannot set the requested value.

      See Also:
      `getFeature(java.lang.String)`

    <!-- -->

    - #### getProperty

          public java.lang.Object getProperty(java.lang.String name)
                                       throws SAXNotRecognizedException,
                                              SAXNotSupportedException

      Look up the value of a property.
      The property name is any fully-qualified URI. It is possible for an XMLReader to recognize a property name but to be unable to return its state; this is especially true in the case of an adapter for a SAX1 [`Parser`](../../../../org/xml/sax/Parser.md).

      XMLReaders are not required to recognize any specific property names, though an initial core set is documented for SAX2.

      Some property values may be available only in specific contexts, such as before, during, or after a parse.

      Implementors are free (and encouraged) to invent their own properties, using names built on their own URIs.

      Specified by:
      [`getProperty`](../../../../org/xml/sax/XMLReader.md) in interface [`XMLReader`](../../../../org/xml/sax/XMLReader.md)

      Parameters:
      `name` - The property name, which is a fully-qualified URI.

      Returns:
      The current value of the property.

      Throws:
      [`SAXNotRecognizedException`](../../../../org/xml/sax/SAXNotRecognizedException.md) - When the XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](../../../../org/xml/sax/SAXNotSupportedException.md) - When the XMLReader recognizes the property name but cannot determine its value at this time.

      See Also:
      `setProperty(java.lang.String, java.lang.Object)`

    <!-- -->

    - #### setProperty

          public void setProperty(java.lang.String name,
                                  java.lang.Object value)
                           throws SAXNotRecognizedException,
                                  SAXNotSupportedException

      Set the value of a property.
      The property name is any fully-qualified URI. It is possible for an XMLReader to recognize a property name but to be unable to set its value; this is especially true in the case of an adapter for a SAX1 [`Parser`](../../../../org/xml/sax/Parser.md).

      XMLReaders are not required to recognize setting any specific property names, though a core set is provided with SAX2.

      Some property values may be immutable or mutable only in specific contexts, such as before, during, or after a parse.

      This method is also the standard mechanism for setting extended handlers.

      Specified by:
      [`setProperty`](../../../../org/xml/sax/XMLReader.md) in interface [`XMLReader`](../../../../org/xml/sax/XMLReader.md)

      Parameters:
      `name` - The property name, which is a fully-qualified URI.

      `value` - The requested value for the property.

      Throws:
      [`SAXNotRecognizedException`](../../../../org/xml/sax/SAXNotRecognizedException.md) - When the XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](../../../../org/xml/sax/SAXNotSupportedException.md) - When the XMLReader recognizes the property name but cannot set the requested value.

    <!-- -->

    - #### setDTDHandler

          public void setDTDHandler(DTDHandler handler)

      Allow an application to register a DTD event handler.
      If the application does not register a DTD handler, all DTD events reported by the SAX parser will be silently ignored.

      Applications may register a new or different handler in the middle of a parse, and the SAX parser must begin using the new handler immediately.

      Specified by:
      [`setDTDHandler`](../../../../org/xml/sax/Parser.md) in interface [`Parser`](../../../../org/xml/sax/Parser.md)

      Specified by:
      [`setDTDHandler`](../../../../org/xml/sax/XMLReader.md) in interface [`XMLReader`](../../../../org/xml/sax/XMLReader.md)

      Parameters:
      `handler` - The DTD handler.

      Throws:
      `java.lang.NullPointerException` - If the handler argument is null.

      See Also:
      `getDTDHandler()`

    <!-- -->

    - #### getDTDHandler

          public DTDHandler getDTDHandler()

      Return the current DTD handler.
      Specified by:
      [`getDTDHandler`](../../../../org/xml/sax/XMLReader.md) in interface [`XMLReader`](../../../../org/xml/sax/XMLReader.md)

      Returns:
      The current DTD handler, or null if none has been registered.

      Since:
      SAX 2.0

      See Also:
      `setDTDHandler(org.xml.sax.DTDHandler)`

    <!-- -->

    - #### setContentHandler

          public void setContentHandler(ContentHandler handler)

      Allow an application to register a content event handler.
      If the application does not register a content handler, all content events reported by the SAX parser will be silently ignored.

      Applications may register a new or different handler in the middle of a parse, and the SAX parser must begin using the new handler immediately.

      Specified by:
      [`setContentHandler`](../../../../org/xml/sax/XMLReader.md) in interface [`XMLReader`](../../../../org/xml/sax/XMLReader.md)

      Parameters:
      `handler` - The content handler.

      Throws:
      `java.lang.NullPointerException` - If the handler argument is null.

      Since:
      SAX 2.0

      See Also:
      `getContentHandler()`

    <!-- -->

    - #### getContentHandler

          public ContentHandler getContentHandler()

      Return the current content handler.
      Specified by:
      [`getContentHandler`](../../../../org/xml/sax/XMLReader.md) in interface [`XMLReader`](../../../../org/xml/sax/XMLReader.md)

      Returns:
      The current content handler, or null if none has been registered.

      Since:
      SAX 2.0

      See Also:
      `setContentHandler(org.xml.sax.ContentHandler)`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](SAXAttrList.md)**
- **[Next Class](XMLAttr.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
