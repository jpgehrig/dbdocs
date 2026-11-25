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

- **[Prev Class](XMLParseException.md)**
- **[Next Class](XMLPI.md)**

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

## **Class XMLParser**

- **java.lang.Object**

- - **oracle.xml.parser.v2.XMLParser**

<!-- -->

- **Direct Known Subclasses:**
  **[BinaryParser](BinaryParser.md), [DOMParser](DOMParser.md), [SAXParser](SAXParser.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class XMLParser
      extends java.lang.Object

  **This class serves as a base class for the `DOMParser` and `SAXParser` classes. It contains methods to parse eXtensible Markup Language (XML) 1.0 documents according to the World Wide Web Consortium (W3C) [recommendation](http://www.w3.org/TR/1998/REC-xml-19980210). This class can not be instantiated (applications may use the DOM or SAX parser depending on their requirements).**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                                                                |
    |---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `BASE_URL`<br>Base URL used in parsing entities.                                                                                                                                                                                     |
    | `static int`              | `BASE_URL_ID`                                                                                                                                                                                                                        |
    | `static java.lang.String` | `CONTENT_MODEL_DETERMINISTIC`<br>Deprecated. <br>Replaced by XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC.                                                                                                                                |
    | `static int`              | `DEFAULT_ENTITY_EXPANSION_DEPTH`                                                                                                                                                                                                     |
    | `static int`              | `DEFAULT_ENTITY_EXPANSION_DEPTH_SECURE`                                                                                                                                                                                              |
    | `static java.lang.String` | `DTD_OBJECT`<br>DTD Object to be used for validation.                                                                                                                                                                                |
    | `static int`              | `DTD_OBJECT_ID`                                                                                                                                                                                                                      |
    | `static java.lang.String` | `ENTITY_EXPANSION_DEPTH`<br>Define the depth of entity expansion allowed.                                                                                                                                                            |
    | `static int`              | `ENTITY_EXPANSION_DEPTH_ID`                                                                                                                                                                                                          |
    | `static java.lang.String` | `EXPAND_ENTITYREF`<br>Expands entities when set to true, else report just the reference                                                                                                                                              |
    | `static int`              | `EXPAND_ENTITYREF_ID`                                                                                                                                                                                                                |
    | `static int`              | `IGNORE_DUPLICATE_ID`                                                                                                                                                                                                                |
    | `static java.lang.String` | `PARSER`                                                                                                                                                                                                                             |
    | `static java.lang.String` | `PARSER_CDATA`                                                                                                                                                                                                                       |
    | `static java.lang.String` | `PARSER_DTD`                                                                                                                                                                                                                         |
    | `static java.lang.String` | `RESOLVE_ENTITY_DEFAULT`<br>Resolve external entities when set to true, else raise error Can be override by entityResovler                                                                                                           |
    | `static int`              | `RESOLVE_ENTITY_DEFAULT_ID`                                                                                                                                                                                                          |
    | `static java.lang.String` | `SCHEMA_LANGUAGE`                                                                                                                                                                                                                    |
    | `static int`              | `SCHEMA_LANGUAGE_ID`                                                                                                                                                                                                                 |
    | `static java.lang.String` | `SCHEMA_OBJECT`<br>Schema Object to be used for validation.                                                                                                                                                                          |
    | `static int`              | `SCHEMA_OBJECT_ID`                                                                                                                                                                                                                   |
    | `static java.lang.String` | `SCHEMA_SOURCE`                                                                                                                                                                                                                      |
    | `static int`              | `SCHEMA_SOURCE_ID`                                                                                                                                                                                                                   |
    | `static java.lang.String` | `STANDALONE`<br>Sets the standalone property of the input files.                                                                                                                                                                     |
    | `static int`              | `STANDALONE_ID`                                                                                                                                                                                                                      |
    | `static java.lang.String` | `USE_DTD_ONLY_FOR_VALIDATION`<br>If true, DTD Object is used only for validation and is not added to the parser document (Boolean.TRUE or Boolean.FALSE) This property/attribute is only if setDoctype is called to use a fixed DTD. |
    | `static int`              | `USE_DTD_ONLY_FOR_VALIDATION_ID`                                                                                                                                                                                                     |
    | `static java.lang.String` | `XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT`<br>Defines the limit on the number of entity expansions.                                                                                                                                |
    | `static int`              | `XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_DEFAULT`                                                                                                                                                                                 |
    | `static int`              | `XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_ID`                                                                                                                                                                                      |
    | `static int`              | `XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_SECURE`                                                                                                                                                                                  |
    | `static java.lang.String` | `XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING`<br>This property can be set to true in order to allow the parser to tolerate certain illegal UTF-8 encodings.                                                                              |
    | `static int`              | `XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING_ID`                                                                                                                                                                                         |
    | `static java.lang.String` | `XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC`<br>Do not verify if the content model is deterministic if this property is set to false.                                                                                                   |
    | `static int`              | `XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC_ID`                                                                                                                                                                                         |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                             | Method and Description                                                                                                                                                                                                                                                                                      |
    |---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                            | `getAttribute``(java.lang.String name)`<br>Allows the user to retrieve specific attributes on the underlying implementation.                                                                                                                                                                                |
    | `java.net.URL`                                                | `getBaseURL``()`<br>Gets the base URL                                                                                                                                                                                                                                                                       |
    | [`EntityResolver`](../../../../org/xml/sax/EntityResolver.md) | `getEntityResolver``()`<br>Return the current entity resolver.                                                                                                                                                                                                                                              |
    | [`ErrorHandler`](../../../../org/xml/sax/ErrorHandler.md)     | `getErrorHandler``()`<br>Return the current error handler.                                                                                                                                                                                                                                                  |
    | `static java.lang.String`                                     | `getReleaseVersion``()`<br>Returns the release version of the Oracle XML Parser                                                                                                                                                                                                                             |
    | `boolean`                                                     | `getValidationMode``()`<br>Returns the validation mode                                                                                                                                                                                                                                                      |
    | `int`                                                         | `getValidationModeValue``()`<br>Returns the validation mode                                                                                                                                                                                                                                                 |
    | `java.lang.Object`                                            | `getXMLProperty``(java.lang.String name)`<br>Get a property.                                                                                                                                                                                                                                                |
    | `boolean`                                                     | `isXMLPropertyReadOnly``(java.lang.String name)`<br>Check is the property is read-only Returns true if the property is not supported                                                                                                                                                                        |
    | `boolean`                                                     | `isXMLPropertySupported``(java.lang.String name)`<br>Check is the property is supported                                                                                                                                                                                                                     |
    | `void`                                                        | `parse``(`[`InputSource`](../../../../org/xml/sax/InputSource.md)` in)`<br>Parses the XML from given input source                                                                                                                                                                                           |
    | `void`                                                        | `parse``(java.io.InputStream in)`<br>Parses the XML from given input stream.                                                                                                                                                                                                                                |
    | `void`                                                        | `parse``(java.io.Reader r)`<br>Parses the XML from given input stream.                                                                                                                                                                                                                                      |
    | `void`                                                        | `parse``(java.lang.String in)`<br>Parses the XML from the URL indicated                                                                                                                                                                                                                                     |
    | `void`                                                        | `parse``(java.net.URL url)`<br>Parses the XML document pointed to by the given URL and creates the corresponding XML document hierarchy.                                                                                                                                                                    |
    | `void`                                                        | `reset``()`<br>Resets the parser state                                                                                                                                                                                                                                                                      |
    | `void`                                                        | `setAttribute``(int id, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation.                                                                                                                                                                            |
    | `void`                                                        | `setAttribute``(java.lang.String name, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation.                                                                                                                                                             |
    | `void`                                                        | `setBaseURL``(java.net.URL url)`<br>Set the base URL for loading external enitites and DTDs.                                                                                                                                                                                                                |
    | `void`                                                        | `setDoctype``(`[`DTD`](DTD.md)` dtd)`<br>Set the DTD                                                                                                                                                                                                                                                        |
    | `void`                                                        | `setEntityResolver``(`[`EntityResolver`](../../../../org/xml/sax/EntityResolver.md)` resolver)`<br>Allow an application to register an entity resolver.                                                                                                                                                     |
    | `void`                                                        | `setErrorHandler``(`[`ErrorHandler`](../../../../org/xml/sax/ErrorHandler.md)` handler)`<br>Allow an application to register an error event handler.                                                                                                                                                        |
    | `void`                                                        | `setLocale``(java.util.Locale locale)`<br>Applications can use this to set the locale for error reporting.                                                                                                                                                                                                  |
    | `void`                                                        | `setPreserveWhitespace``(boolean flag)`<br>Set the white space preserving mode                                                                                                                                                                                                                              |
    | `void`                                                        | `setSchemaValidationMode``(boolean flag)`<br>Deprecated. <br>Replaced by setValidationMode(int).                                                                                                                                                                                                            |
    | `java.lang.Object`                                            | `setSchemaValidatorProperty``(java.lang.String name, java.lang.Object value)`<br>Set an XML property to schema validator.                                                                                                                                                                                   |
    | `void`                                                        | `setSecureProcessing``()`<br>This method provides aggregate configurations for secure parsing It can be used to replace equevalent calls of setAttribute() This make it easier to change the definition of secure processing and provide better performance when the setAttribute becomes too many entries. |
    | `void`                                                        | `setValidationMode``(boolean yes)`<br>Deprecated. <br>Replaced by setValidationMode(int).                                                                                                                                                                                                                   |
    | `void`                                                        | `setValidationMode``(int valMode)`<br>Set the validation mode This method sets the validation mode of the parser.                                                                                                                                                                                           |
    | `java.lang.Object`                                            | `setXMLProperty``(java.lang.String name, java.lang.Object value)`<br>Set a property.                                                                                                                                                                                                                        |
    | `void`                                                        | `setXMLSchema``(java.lang.Object schema)`<br>Set an XMLSchema for validating the instance document                                                                                                                                                                                                          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### PARSER

          public static final java.lang.String PARSER

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DTD_OBJECT

          public static final java.lang.String DTD_OBJECT

      DTD Object to be used for validation. Replaces XMLParser.setDoctype()
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DTD_OBJECT_ID

          public static final int DTD_OBJECT_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SCHEMA_OBJECT

          public static final java.lang.String SCHEMA_OBJECT

      Schema Object to be used for validation. Replaces XMLParser.setXMLSchema()
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SCHEMA_OBJECT_ID

          public static final int SCHEMA_OBJECT_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### PARSER_DTD

          public static final java.lang.String PARSER_DTD

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### PARSER_CDATA

          public static final java.lang.String PARSER_CDATA

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SCHEMA_SOURCE

          public static final java.lang.String SCHEMA_SOURCE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SCHEMA_SOURCE_ID

          public static final int SCHEMA_SOURCE_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SCHEMA_LANGUAGE

          public static final java.lang.String SCHEMA_LANGUAGE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SCHEMA_LANGUAGE_ID

          public static final int SCHEMA_LANGUAGE_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IGNORE_DUPLICATE_ID

          public static final int IGNORE_DUPLICATE_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### BASE_URL

          public static final java.lang.String BASE_URL

      Base URL used in parsing entities. Replaces setBaseURL(); Should be URL object
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### BASE_URL_ID

          public static final int BASE_URL_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### USE_DTD_ONLY_FOR_VALIDATION

          public static final java.lang.String USE_DTD_ONLY_FOR_VALIDATION

      If true, DTD Object is used only for validation and is not added to the parser document (Boolean.TRUE or Boolean.FALSE) This property/attribute is only if setDoctype is called to use a fixed DTD.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### USE_DTD_ONLY_FOR_VALIDATION_ID

          public static final int USE_DTD_ONLY_FOR_VALIDATION_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### STANDALONE

          public static final java.lang.String STANDALONE

      Sets the standalone property of the input files. If true the DTDs are not retrieved.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### STANDALONE_ID

          public static final int STANDALONE_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### EXPAND_ENTITYREF

          public static final java.lang.String EXPAND_ENTITYREF

      Expands entities when set to true, else report just the reference
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### EXPAND_ENTITYREF_ID

          public static final int EXPAND_ENTITYREF_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### RESOLVE_ENTITY_DEFAULT

          public static final java.lang.String RESOLVE_ENTITY_DEFAULT

      Resolve external entities when set to true, else raise error Can be override by entityResovler
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### RESOLVE_ENTITY_DEFAULT_ID

          public static final int RESOLVE_ENTITY_DEFAULT_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_EXPANSION_DEPTH

          public static final java.lang.String ENTITY_EXPANSION_DEPTH

      Define the depth of entity expansion allowed. Entity expansion depth cannot exceed the value for DEFAULT_ENTITY_EXPANSION_DEPTH. It defines the maximum.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_EXPANSION_DEPTH_ID

          public static final int ENTITY_EXPANSION_DEPTH_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC

          public static final java.lang.String XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC

      Do not verify if the content model is deterministic if this property is set to false.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC_ID

          public static final int XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING

          public static final java.lang.String XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING

      This property can be set to true in order to allow the parser to tolerate certain illegal UTF-8 encodings.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING_ID

          public static final int XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### CONTENT_MODEL_DETERMINISTIC

          public static final java.lang.String CONTENT_MODEL_DETERMINISTIC

      Deprecated. Replaced by XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT

          public static final java.lang.String XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT

      Defines the limit on the number of entity expansions. The number of (general) entity expansions required for a single parse of a single XML document may not exceed this value.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_ID

          public static final int XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_SECURE

          public static final int XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_SECURE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_DEFAULT

          public static final int XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_DEFAULT

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DEFAULT_ENTITY_EXPANSION_DEPTH_SECURE

          public static final int DEFAULT_ENTITY_EXPANSION_DEPTH_SECURE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DEFAULT_ENTITY_EXPANSION_DEPTH

          public static final int DEFAULT_ENTITY_EXPANSION_DEPTH

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### reset

          public void reset()

      Resets the parser state

    <!-- -->

    - #### parse

          public void parse(InputSource in)
                     throws XMLParseException,
                            SAXException,
                            java.io.IOException

      Parses the XML from given input source
      Parameters:
      `in` - the `org.xml.sax.InputSouce` to parse

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### parse

          public void parse(java.lang.String in)
                     throws XMLParseException,
                            SAXException,
                            java.io.IOException

      Parses the XML from the URL indicated
      Parameters:
      `in` - the `String` containing the URL to parse from

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### parse

          public final void parse(java.net.URL url)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Parses the XML document pointed to by the given URL and creates the corresponding XML document hierarchy.
      Parameters:
      `url` - the url points to the XML document to parse.

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### parse

          public final void parse(java.io.InputStream in)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Parses the XML from given input stream. The base URL should be set for resolving external entities and DTD.
      Parameters:
      `in` - the `InputStream` containing XML data to parse.

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

      See Also:
      `setBaseURL(java.net.URL)`

    <!-- -->

    - #### parse

          public final void parse(java.io.Reader r)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Parses the XML from given input stream. The base URL should be set for resolving external entities and DTD.
      Parameters:
      `r` - the `Reader` containing XML data to parse.

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

      See Also:
      `setBaseURL(java.net.URL)`

    <!-- -->

    - #### setSecureProcessing

          public void setSecureProcessing()

      This method provides aggregate configurations for secure parsing It can be used to replace equevalent calls of setAttribute() This make it easier to change the definition of secure processing and provide better performance when the setAttribute becomes too many entries.

    <!-- -->

    - #### setEntityResolver

          public void setEntityResolver(EntityResolver resolver)

      Allow an application to register an entity resolver.
      If the application does not register an entity resolver, the XMLReader will perform its own default resolution.

      Applications may register a new or different resolver in the middle of a parse, and the SAX parser must begin using the new resolver immediately.

      Parameters:
      `resolver` - The entity resolver.

      Throws:
      `java.lang.NullPointerException` - If the resolver argument is null.

      See Also:
      `getEntityResolver()`

    <!-- -->

    - #### getEntityResolver

          public EntityResolver getEntityResolver()

      Return the current entity resolver.
      Returns:
      The current entity resolver, or null if none has been registered.

      Since:
      SAX 2.0

      See Also:
      `setEntityResolver(org.xml.sax.EntityResolver)`

    <!-- -->

    - #### setErrorHandler

          public void setErrorHandler(ErrorHandler handler)

      Allow an application to register an error event handler.
      If the application does not register an error handler, all error events reported by the SAX parser will be silently ignored; however, normal processing may not continue. It is highly recommended that all SAX applications implement an error handler to avoid unexpected bugs.

      Applications may register a new or different handler in the middle of a parse, and the SAX parser must begin using the new handler immediately.

      Parameters:
      `handler` - The error handler.

      Throws:
      `java.lang.NullPointerException` - If the handler argument is null.

      See Also:
      `getErrorHandler()`

    <!-- -->

    - #### getErrorHandler

          public ErrorHandler getErrorHandler()

      Return the current error handler.
      Returns:
      The current error handler, or null if none has been registered.

      Since:
      SAX 2.0

      See Also:
      `setErrorHandler(org.xml.sax.ErrorHandler)`

    <!-- -->

    - #### setLocale

          public void setLocale(java.util.Locale locale)
                         throws SAXException

      Applications can use this to set the locale for error reporting.
      Parameters:
      `locale` - `Locale` to set

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - A `SAXException` could be thrown.

      See Also:
      [`Parser.setLocale(java.util.Locale)`](../../../../org/xml/sax/Parser.md)

    <!-- -->

    - #### setDoctype

          public void setDoctype(DTD dtd)

      Set the DTD
      Parameters:
      `dtd` - `DTD` to set and used while parsing

    <!-- -->

    - #### setSchemaValidationMode

          public void setSchemaValidationMode(boolean flag)

      Deprecated. Replaced by setValidationMode(int).
      Set the schema validation mode
      Parameters:
      `flag` - determines whether the XML parser should invoke schema validating

    <!-- -->

    - #### setValidationMode

          public void setValidationMode(boolean yes)

      Deprecated. Replaced by setValidationMode(int).
      Set the validation mode
      Parameters:
      `yes` - determines whether the XML parser should be validating

    <!-- -->

    - #### setValidationMode

          public void setValidationMode(int valMode)

      Set the validation mode This method sets the validation mode of the parser. Legal values are: NONVALIDATING, PARTIAL_VALIDATION, DTD_VALIDATION, SCHEMA_VALIDATION, SCHEMA_LAX_VALIDATION, and SCHEMA_STRICT_VALIDATION.
      Parameters:
      `valMode` - determines the type of the validation mode which the parser is set to

    <!-- -->

    - #### setSchemaValidatorProperty

          public java.lang.Object setSchemaValidatorProperty(java.lang.String name,
                                                             java.lang.Object value)

      Set an XML property to schema validator. The value of the property set is returned if successfully set, a null is returned if schema validation is not initiallized or the property cannot be set or not supported.
      Parameters:
      `name` - - name of the property

      `value` - - value of the property

      Returns:
      Object - the set property

    <!-- -->

    - #### setBaseURL

          public void setBaseURL(java.net.URL url)

      Set the base URL for loading external enitites and DTDs. This method should to be called if the parse(InputStream) is used to parse the XML Document
      Parameters:
      `url` - The base URL

    <!-- -->

    - #### getBaseURL

          public java.net.URL getBaseURL()

      Gets the base URL
      Returns:
      the base URL

    <!-- -->

    - #### setPreserveWhitespace

          public void setPreserveWhitespace(boolean flag)

      Set the white space preserving mode
      Parameters:
      `flag` - preserving mode

    <!-- -->

    - #### getValidationMode

          public boolean getValidationMode()

      Returns the validation mode
      Returns:
      `true` if the XML parser is validating `false` if not

    <!-- -->

    - #### getValidationModeValue

          public int getValidationModeValue()

      Returns the validation mode
      Returns:
      `0` if the XML parser is NONVALIDATING `1` if the XML parser is PARTIAL_VALIDATION `2` if the XML parser is DTD_VALIDATION `3` if the XML parser is SCHEMA_VALIDATION

    <!-- -->

    - #### getReleaseVersion

          public static java.lang.String getReleaseVersion()

      Returns the release version of the Oracle XML Parser
      Returns:
      the release version string

    <!-- -->

    - #### setXMLSchema

          public void setXMLSchema(java.lang.Object schema)

      Set an XMLSchema for validating the instance document
      Parameters:
      `schema` - The XMLSchema object

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.Object value)
                            throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation.
      Parameters:
      `name` - The name of the attribute.

      `value` - The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

    <!-- -->

    - #### setAttribute

          public void setAttribute(int id,
                                   java.lang.Object value)
                            throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation.
      Parameters:
      `id` - The id of the attribute.

      `value` - The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

    <!-- -->

    - #### getAttribute

          public java.lang.Object getAttribute(java.lang.String name)
                                        throws java.lang.IllegalArgumentException

      Allows the user to retrieve specific attributes on the underlying implementation.
      Parameters:
      `name` - The name of the attribute.

      Returns:
      value The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

    <!-- -->

    - #### setXMLProperty

          public java.lang.Object setXMLProperty(java.lang.String name,
                                                 java.lang.Object value)

      Set a property. The value of the property set is returned if successfully set, a null is returned if the property is read-only and cannot be set or is not supported.
      Parameters:
      `name` - - name of the property

      `value` - - value of the property

      Returns:
      Object - the set property

    <!-- -->

    - #### getXMLProperty

          public java.lang.Object getXMLProperty(java.lang.String name)

      Get a property. The property is returned if present and supported, else null is returned
      Parameters:
      `name` - - name of the property

      Returns:
      Object - value of the property

    <!-- -->

    - #### isXMLPropertySupported

          public boolean isXMLPropertySupported(java.lang.String name)

      Check is the property is supported
      Parameters:
      `name` - - name of the property

      Returns:
      boolean - TRUE is supported

    <!-- -->

    - #### isXMLPropertyReadOnly

          public boolean isXMLPropertyReadOnly(java.lang.String name)

      Check is the property is read-only Returns true if the property is not supported
      Parameters:
      `name` - - name of the property

      Returns:
      boolean - TRUE is read-only

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

- **[Prev Class](XMLParseException.md)**
- **[Next Class](XMLPI.md)**

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
