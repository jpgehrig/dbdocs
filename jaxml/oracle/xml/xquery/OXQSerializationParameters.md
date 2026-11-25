Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](OXQSequence.md)**
- **[Next Class](OXQStackTraceElement.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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

**oracle.xml.xquery**

## **Interface OXQSerializationParameters**

-

  ------------------------------------------------------------------------

  **
  **

      public interface OXQSerializationParameters

  **Models the supported [serialization parameters](http://www.w3.org/TR/xslt-xquery-serialization-30/#serparam). This can be used to create a `java.util.Properties` instance that can be passed to any standard XQJ method that accepts serialization parameters. For example:**
            OXQConnection connection = ...
            OXQSerializationParameters params = connection.createSerializationParameters();
            params.setMethod(OXQSerializationParameters.METHOD_XML);
            params.setIndent(true);
            params.setEncoding("UTF-16");
            XQSequence seq = ...;
            String xml = seq.getSequenceAsString(params.createProperties());


  **Since:**
  **12.1**

  **See Also:**
  **[XSLT 2.0 and XQuery 1.0 Serialization (Second Edition)](http://www.w3.org/TR/xslt-xquery-serialization-30/)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type                  | Field and Description                                                                                          |
    |------------------------------------|----------------------------------------------------------------------------------------------------------------|
    | `static javax.xml.namespace.QName` | `METHOD_HTML`<br>The [HTML Output Method](http://www.w3.org/TR/xslt-xquery-serialization-30/#html_output).     |
    | `static javax.xml.namespace.QName` | `METHOD_ORACLE_CSX`<br>The CSX Output Method.                                                                  |
    | `static javax.xml.namespace.QName` | `METHOD_TEXT`<br>The [Text Output Method](http://www.w3.org/TR/xslt-xquery-serialization/#text_output).        |
    | `static javax.xml.namespace.QName` | `METHOD_XHTML`<br>The [XHTML Output Method](https://www.w3.org/TR/xslt-xquery-serialization-30/#xhtml_output). |
    | `static javax.xml.namespace.QName` | `METHOD_XML`<br>The [XML Output Method](http://www.w3.org/TR/xslt-xquery-serialization/#xml_output).           |
    | `static int`                       | `STANDALONE_NO`<br>The value that indicates `standalone='no'` should appear in the document declaration.       |
    | `static int`                       | `STANDALONE_OMIT`<br>The value that indicates `standalone` will not appear in the document declaration.        |
    | `static int`                       | `STANDALONE_YES`<br>The value that indicates `standalone='yes'` should appear in the document declaration.     |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                                                                                           |
    |-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                        | `addCDATASectionElement``(javax.xml.namespace.QName elementName)`<br>Adds an element name to the `cdata-section-elements` parameter.                                             |
    | `void`                        | `addCharacterMapping``(int codepoint, java.lang.String replacement)`<br>Sets the `use-character-maps` parameter.                                                                 |
    | `void`                        | `addSuppressIndentation``(javax.xml.namespace.QName elementName)`<br>Adds an element name to the `suppress-indentation` parameter.                                               |
    | `java.util.Properties`        | `createProperties``()`<br>Exports the current parameters to a `java.util.Properties` object that may be used with any standard XQJ method that accepts serialization properties. |
    | `int`                         | `getBufferSize``()`<br>Gets the buffer size in bytes that will be used during serialization.                                                                                     |
    | `javax.xml.namespace.QName[]` | `getCDATASectionElements``()`<br>Gets the `cdata-section-elements` parameter.                                                                                                    |
    | `java.lang.String`            | `getCharacterMapping``(int codepoint)`<br>Gets the current character mapping for the specified character.                                                                        |
    | `int[]`                       | `getCharacterMappingCodepoints``()`<br>Gets an array of Unicode characters that are currently replaced by character mappings.                                                    |
    | `java.lang.String`            | `getDoctypePublic``()`<br>Gets the `doctype-public` parameter.                                                                                                                   |
    | `java.lang.String`            | `getDoctypeSystem``()`<br>Gets the `doctype-system` parameter.                                                                                                                   |
    | `java.nio.charset.Charset`    | `getEncoding``()`<br>Gets the value of the `encoding` parameter.                                                                                                                 |
    | `boolean`                     | `getEscapeUriAttributes``()`<br>Gets the value of the `escape-uri-attributes` parameter.                                                                                         |
    | `java.math.BigDecimal`        | `getHTMLVersion``()`<br>Gets the value of the `html-version` parameter.                                                                                                          |
    | `boolean`                     | `getIncludeContentType``()`<br>Gets the value of the `include-content-type` parameter.                                                                                           |
    | `java.lang.String`            | `getItemSeparator``()`<br>Gets the value of the `item-separator` parameter.                                                                                                      |
    | `javax.activation.MimeType`   | `getMediaType``()`<br>Gets the value of the `media-type` parameter.                                                                                                              |
    | `javax.xml.namespace.QName`   | `getMethod``()`<br>Gets the `method` parameter.                                                                                                                                  |
    | `java.text.Normalizer.Form`   | `getNormalizationForm``()`<br>Gets the `normalization-form` parameter.                                                                                                           |
    | `int`                         | `getStandalone``()`<br>Gets the `standalone` parameter.                                                                                                                          |
    | `javax.xml.namespace.QName[]` | `getSuppressIndentation``()`<br>Gets the `suppress-indentation` parameter.                                                                                                       |
    | `java.lang.String`            | `getVersion``()`<br>Gets the value of the `version` parameter.                                                                                                                   |
    | `boolean`                     | `isIndent``()`<br>Gets the value of the `indent` parameter.                                                                                                                      |
    | `boolean`                     | `isOmitXMLDeclaration``()`<br>Gets the `omit-xml-declaration` parameter value.                                                                                                   |
    | `boolean`                     | `removeCDATASectionElement``(javax.xml.namespace.QName elementName)`<br>Removes the element name from the `cdata-section-elements` parameter.                                    |
    | `boolean`                     | `removeSuppressIndentation``(javax.xml.namespace.QName elementName)`<br>Removes an element name from the `suppress-indentation` parameter.                                       |
    | `void`                        | `setBufferSize``(int buffer)`<br>Sets the buffer size that will be used during serialization.                                                                                    |
    | `void`                        | `setDoctypePublic``(java.lang.String doctypePublic)`<br>Sets the `doctype-public` parameter.                                                                                     |
    | `void`                        | `setDoctypeSystem``(java.lang.String doctypeSystem)`<br>Sets the `doctype-system` parameter.                                                                                     |
    | `void`                        | `setEncoding``(java.nio.charset.Charset encoding)`<br>Sets the `encoding` parameter.                                                                                             |
    | `void`                        | `setEncoding``(java.lang.String encoding)`<br>Sets the `encoding` parameter.                                                                                                     |
    | `void`                        | `setEscapeUriAttributes``(boolean escapeUriAttributes)`<br>Sets the `escape-uri-attributes` parameter.                                                                           |
    | `void`                        | `setHTMLVersion``(java.math.BigDecimal version)`<br>Sets the `html-version` parameter.                                                                                           |
    | `void`                        | `setIncludeContentType``(boolean includeContentType)`<br>Sets the `include-content-type` parameter.                                                                              |
    | `void`                        | `setIndent``(boolean indent)`<br>Sets the `indent` parameter.                                                                                                                    |
    | `void`                        | `setItemSeparator``(java.lang.String separator)`<br>Sets the `item-separator` parameter.                                                                                         |
    | `void`                        | `setMediaType``(javax.activation.MimeType mediaType)`<br>Sets the `media-type` parameter.                                                                                        |
    | `void`                        | `setMethod``(javax.xml.namespace.QName method)`<br>Sets the `method` parameter.                                                                                                  |
    | `void`                        | `setNormalizationForm``(java.text.Normalizer.Form form)`<br>Sets `normalization-form` parameter.                                                                                 |
    | `void`                        | `setOmitXMLDeclaration``(boolean omitXMLDeclaration)`<br>Sets the `omit-xml-declaration` parameter.                                                                              |
    | `void`                        | `setStandalone``(int standalone)`<br>Sets the `standalone` parameter which controls the standalone document declaration.                                                         |
    | `void`                        | `setVersion``(java.lang.String version)`<br>Sets the `version` parameter.                                                                                                        |

<!-- -->

- - ### Field Detail

    - #### METHOD_XML

          static final javax.xml.namespace.QName METHOD_XML

      The [XML Output Method](http://www.w3.org/TR/xslt-xquery-serialization/#xml_output).
      See Also:
      `setMethod(QName)`

    <!-- -->

    - #### METHOD_TEXT

          static final javax.xml.namespace.QName METHOD_TEXT

      The [Text Output Method](http://www.w3.org/TR/xslt-xquery-serialization/#text_output).
      See Also:
      `setMethod(QName)`

    <!-- -->

    - #### METHOD_HTML

          static final javax.xml.namespace.QName METHOD_HTML

      The [HTML Output Method](http://www.w3.org/TR/xslt-xquery-serialization-30/#html_output).
      See Also:
      `setMethod(QName)`

    <!-- -->

    - #### METHOD_XHTML

          static final javax.xml.namespace.QName METHOD_XHTML

      The [XHTML Output Method](https://www.w3.org/TR/xslt-xquery-serialization-30/#xhtml_output).
      See Also:
      `setMethod(QName)`

    <!-- -->

    - #### METHOD_ORACLE_CSX

          static final javax.xml.namespace.QName METHOD_ORACLE_CSX

      The CSX Output Method. Causes the XML to be output in CSX binary format. May not be specified in combination with any other parameter (e.g. "indent").
      See Also:
      `setMethod(QName)`

    <!-- -->

    - #### STANDALONE_YES

          static final int STANDALONE_YES

      The value that indicates `standalone='yes'` should appear in the document declaration.
      See Also:
      `setStandalone(int)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### STANDALONE_NO

          static final int STANDALONE_NO

      The value that indicates `standalone='no'` should appear in the document declaration.
      See Also:
      `setStandalone(int)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### STANDALONE_OMIT

          static final int STANDALONE_OMIT

      The value that indicates `standalone` will not appear in the document declaration.
      See Also:
      `setStandalone(int)`, [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### createProperties

          java.util.Properties createProperties()

      Exports the current parameters to a `java.util.Properties` object that may be used with any standard XQJ method that accepts serialization properties. This conversion requires the parameter values to be represented as strings. The following table describes this conversion. Note, if a parameter is currently set to the default value, it will not have an entry in the result.
      **Parameter Conversion**

      | Parameter                | String Conversion                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Setter                                  |
      |--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------|
      | `method`                 | `java.xml.namespace.QName.toString()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | `setMethod(QName)`                      |
      | `encoding`               | The `Charset` name. See `java.nio.Charset`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | `setEncoding(Charset)`                  |
      | `indent`                 | `true` maps to `"yes"` and `false` maps to `"no"`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | `setIndent(boolean)`                    |
      | `omit-xml-declaration`   | `true` maps to `"yes"` and `false` maps to `"no"`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | `setOmitXMLDeclaration(boolean)`        |
      | `standalone`             | `STANDALONE_OMIT` maps to `"omit"`, `STANDALONE_YES` maps to `"yes"`, and `STANDALONE_NO` maps to `"no"`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | `setStandalone(int)`                    |
      | `cdata-section-elements` | A semicolon separated list of QNames using `javax.xml.namespace.QName.toString()`.<br>For example:<br>   `"{http://example.org/ns1}one; two; {http://example.org/ns2}three"`<br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | `addCDATASectionElement(QName)`         |
      | `doctype-public`         | No conversion needed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | `setDoctypePublic(String)`              |
      | `doctype-system`         | No conversion needed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | `setDoctypeSystem(String)`              |
      | `normalization-form`     | `Normalizer.Form.toString().toLowerCase()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | `setNormalizationForm(Normalizer.Form)` |
      | `use-character-maps`     | A comma delimited list of mappings where a mapping is represented by a character followed by '=' followed by any string. More precisely:<br><br>`    Mapping ::= [Character] '=' [Character]* `<br>`    Value ::= ( Mapping ( ';' Mapping )* )?`<br>` `<br>Note, to use the ';' character in a mapping value, it must be escaped with the characters "\\"<br><br>For example:<br>   `"\u03A3=[SIGMA];A=;|=\\;"`<br>*This example string should be interpreted as a Java literal string. The Unicode character 0x03A3 is replaced with "\[SIGMA\]", the letter 'A' is replaced with the empty string, and the pipe ('\|') is replaced with a semicolon.* | `addCharacterMapping(int, String)`      |
      | `media-type`             | The media type (MIME content type). See `javax.activation.MimeType`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | `setMediaType(MimeType)`                |
      | `item-separator`         | No conversion needed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | `setItemSeparator(String)`              |
      | `html-version`           | No conversion needed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | `setHTMLVersion(BigDecimal)`            |
      | `include-content-type`   | `true` maps to `"yes"` and `false` maps to `"no"`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | `setIncludeContentType(boolean)`        |
      | `escape-uri-attributes`  | `true` maps to `"yes"` and `false` maps to `"no"`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | `setEscapeUriAttributes(boolean)`       |
      | `version`                | No conversion needed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | `setVersion(String)`                    |

      Returns:
      a `Properties` object that may be used with any XQJ serialization method

    <!-- -->

    - #### setMethod

          void setMethod(javax.xml.namespace.QName method)
                  throws XQException

      Sets the `method` parameter. Must be one of `METHOD_XML`, `METHOD_TEXT`, or `METHOD_ORACLE_CSX`. The default value is `METHOD_XML`.
      Parameters:
      `method` - the output method

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the specified method is not supported

    <!-- -->

    - #### getMethod

          javax.xml.namespace.QName getMethod()

      Gets the `method` parameter. The default value is `METHOD_XML`.
      Returns:
      the output method

      See Also:
      `setMethod(QName)`

    <!-- -->

    - #### setEncoding

          void setEncoding(java.lang.String encoding)
                    throws XQException

      Sets the `encoding` parameter. The default encoding is `"UTF-8"`.
      Parameters:
      `encoding` - the encoding to use. Cannot be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the specified encoding is not a valid `Charset` name. See `java.nio.Charset`

    <!-- -->

    - #### setEncoding

          void setEncoding(java.nio.charset.Charset encoding)

      Sets the `encoding` parameter. The default encoding is `UTF-8`.
      Parameters:
      `encoding` - the encoding to use. Cannot be `null`

    <!-- -->

    - #### getEncoding

          java.nio.charset.Charset getEncoding()

      Gets the value of the `encoding` parameter. The default encoding is `UTF-8`.
      Returns:
      the current encoding

    <!-- -->

    - #### setIndent

          void setIndent(boolean indent)

      Sets the `indent` parameter.
      When true, the serializer will format the output by inserting and removing whitespace adjacent to elements. For validated instances, the serializer will not modify whitespace in elements where the schema type indicates the content is mixed.

      This parameter only applies when the `xml` output `method` is used.

      The default value is `false`.
      Parameters:
      `indent` - the value for the `indent` parameter

      See Also:
      [XML Output Method: indent parameter](http://www.w3.org/TR/xslt-xquery-serialization/#xml_indent)

    <!-- -->

    - #### isIndent

          boolean isIndent()

      Gets the value of the `indent` parameter. The default value is `false`.
      Returns:
      the value of the `indent` parameter

    <!-- -->

    - #### setOmitXMLDeclaration

          void setOmitXMLDeclaration(boolean omitXMLDeclaration)

      Sets the `omit-xml-declaration` parameter. When set to `false`, the serializer will write an XML declaration. When set to `true`, an XML declaration will not be written. The default value is `true`.
      Parameters:
      `omitXMLDeclaration` - the value for the `omit-xml-declaration` parameter

    <!-- -->

    - #### isOmitXMLDeclaration

          boolean isOmitXMLDeclaration()

      Gets the `omit-xml-declaration` parameter value. The default value is `true`.
      Returns:
      the value of the `omit-xml-declaration` parameter

    <!-- -->

    - #### setStandalone

          void setStandalone(int standalone)
                      throws XQException

      Sets the `standalone` parameter which controls the standalone document declaration. Must be one of `STANDALONE_OMIT`, `STANDALONE_YES`, or `STANDALONE_NO`. The default value is `STANDALONE_OMIT`.
      Parameters:
      `standalone` - the `standalone` parameter

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the specified value is not valid

    <!-- -->

    - #### getStandalone

          int getStandalone()

      Gets the `standalone` parameter. The default value is `STANDALONE_OMIT`.
      Returns:
      the `standalone` parameter

    <!-- -->

    - #### setDoctypeSystem

          void setDoctypeSystem(java.lang.String doctypeSystem)
                         throws XQException

      Sets the `doctype-system` parameter. Setting this causes a document type declaration to be output with the specified system id. The instance being serialized must have a single top level element node and no top level text nodes.
      Parameters:
      `doctypeSystem` - may not include both an apostrophe (#x27) and a quotation mark (#x22) character. May be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the specified value is invalid

    <!-- -->

    - #### getDoctypeSystem

          java.lang.String getDoctypeSystem()

      Gets the `doctype-system` parameter.
      Returns:
      the `doctype-system` parameter or `null` if not set

    <!-- -->

    - #### setDoctypePublic

          void setDoctypePublic(java.lang.String doctypePublic)
                         throws XQException

      Sets the `doctype-public` parameter. Specifies the public id to be used in the document type declaration. This setting is ignored unless the `doctype-system` parameter is specified.
      Parameters:
      `doctypePublic` - [http://www.w3.org/TR/REC-xml/#NT-PubidChar](http://www.w3.org/TR/REC-xml/#NT_PubidChar)

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the specified value is not valid

    <!-- -->

    - #### getDoctypePublic

          java.lang.String getDoctypePublic()

      Gets the `doctype-public` parameter.
      Returns:
      the `doctype-public` parameter

    <!-- -->

    - #### setNormalizationForm

          void setNormalizationForm(java.text.Normalizer.Form form)

      Sets `normalization-form` parameter.
      Parameters:
      `form` - may be NFC, NFD, NFKC, NFKD, or null

    <!-- -->

    - #### getNormalizationForm

          java.text.Normalizer.Form getNormalizationForm()

      Gets the `normalization-form` parameter. A value of `null` indicates no normalization will be performed. The default value is `null`.
      Returns:
      may be NFC, NFD, NFKC, NFKD, or null for `"none"`

    <!-- -->

    - #### addCharacterMapping

          void addCharacterMapping(int codepoint,
                                   java.lang.String replacement)

      Sets the `use-character-maps` parameter. Specifies that a given Unicode character should be replaced with the corresponding string value. This only applies to attribute and text values. Note, the string value used in the replacement will be output "as is". Characters in the string will not be normalized, swapped out with character references, etc. This means that using a character mapping can potentially lead to the production invalid XML documents; for example, if the replacement string contains a mismatched end tag.
      Parameters:
      `codepoint` - the Unicode codepoint of the character to replace

      `replacement` - the replacement string. If `null` the mapping will be removed if it already exists

    <!-- -->

    - #### getCharacterMappingCodepoints

          int[] getCharacterMappingCodepoints()

      Gets an array of Unicode characters that are currently replaced by character mappings.
      Returns:
      the array of code points that are currently replaced by character mappings. Returns `null` if there are no mappings

      See Also:
      `addCharacterMapping(int, String)`

    <!-- -->

    - #### getCharacterMapping

          java.lang.String getCharacterMapping(int codepoint)

      Gets the current character mapping for the specified character.
      Parameters:
      `codepoint` - the Unicode character

      Returns:
      the replacement string for the specified character or `null` if no mapping exists

    <!-- -->

    - #### addCDATASectionElement

          void addCDATASectionElement(javax.xml.namespace.QName elementName)
                               throws XQException

      Adds an element name to the `cdata-section-elements` parameter. When the parent element of a text node has the specified QName, the text node will be output as a CDATA section.
      Parameters:
      `elementName` - the element name. Must not be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the local part and prefix of `elementName` are not valid as NCName

    <!-- -->

    - #### removeCDATASectionElement

          boolean removeCDATASectionElement(javax.xml.namespace.QName elementName)

      Removes the element name from the `cdata-section-elements` parameter.
      Parameters:
      `elementName` - the element name to remove. Must not be `null`

      Returns:
      `true` if the parameter contained the specified element and `false` otherwise

    <!-- -->

    - #### getCDATASectionElements

          javax.xml.namespace.QName[] getCDATASectionElements()

      Gets the `cdata-section-elements` parameter.
      Returns:
      a list of the element names or `null` if none are defined

    <!-- -->

    - #### setBufferSize

          void setBufferSize(int buffer)

      Sets the buffer size that will be used during serialization. Must be greater than 0.
      Parameters:
      `buffer` - the buffer size

    <!-- -->

    - #### getBufferSize

          int getBufferSize()

      Gets the buffer size in bytes that will be used during serialization.
      Returns:
      the buffer size

    <!-- -->

    - #### setMediaType

          void setMediaType(javax.activation.MimeType mediaType)
                     throws XQException

      Sets the `media-type` parameter. There's no default media type. Currently setting media type has no effect on any of the supported serialization methods.
      Parameters:
      `mediaType` - the media type. Must not be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the specified media type has 'charset' parameter.

      Since:
      12.2

    <!-- -->

    - #### getMediaType

          javax.activation.MimeType getMediaType()

      Gets the value of the `media-type` parameter. There's no default media type.
      Returns:
      the current media type or `null` if it's not defined.

      Since:
      12.2

    <!-- -->

    - #### setItemSeparator

          void setItemSeparator(java.lang.String separator)

      Sets the `item-separator` parameter. Use `null` to make this parameter absent during serialization.
      Parameters:
      `separator` - the item separator. May be `null`.

      Since:
      12.2

      See Also:
      [Sequence Normalization](http://www.w3.org/TR/xslt-xquery-serialization-30/#serdm)

    <!-- -->

    - #### getItemSeparator

          java.lang.String getItemSeparator()

      Gets the value of the `item-separator` parameter.
      Returns:
      the item separator or `null` if it's not defined.

      Since:
      12.2

      See Also:
      [Sequence Normalization](http://www.w3.org/TR/xslt-xquery-serialization-30/#serdm)

    <!-- -->

    - #### setHTMLVersion

          void setHTMLVersion(java.math.BigDecimal version)

      Sets the `html-version` parameter. Use `null` to make this parameter absent during serialization.
      Parameters:
      `version` - the version value. May be `null`.

      Since:
      12.2

      See Also:
      [HTML Output Method: the version and html-version Parameter](http://www.w3.org/TR/xslt-xquery-serialization-30/#req_html_ver)

    <!-- -->

    - #### getHTMLVersion

          java.math.BigDecimal getHTMLVersion()

      Gets the value of the `html-version` parameter.
      Returns:
      the requested HTML version for the serialization or `null` if it's not defined.

      Since:
      12.2

      See Also:
      [HTML Output Method: the version and html-version Parameter](http://www.w3.org/TR/xslt-xquery-serialization-30/#req_html_ver)

    <!-- -->

    - #### setIncludeContentType

          void setIncludeContentType(boolean includeContentType)

      Sets the `include-content-type` parameter.
      When true, if there is a head element the serializer will add a meta element as the first child of the head element specifying the character encoding. For example: `<META http-equiv="Content-Type" content="text/html; charset=EUC-JP">` If a meta element has been added to the head element as described above, then any existing meta element child of the head element having an http-equiv attribute with the value "Content-Type", making the comparison without regard to case after first stripping leading and trailing spaces from the value of the attribute solely for the purposes of comparison, will be discarded.

      This parameter is only applicable when the `XHTML` or `HTML` output `method` is used.

      The default value is `false`.
      Parameters:
      `includeContentType` - the value for the `include-content-type` parameter

      See Also:
      [HTML Output Method: the include-content-type Parameter](http://www.w3.org/TR/xslt-xquery-serialization-30/#HTML_INCLUDE_CONTENT_TYPE)

    <!-- -->

    - #### getIncludeContentType

          boolean getIncludeContentType()

      Gets the value of the `include-content-type` parameter. The default value is `false`.
      Returns:
      the value of the `include-content-type` parameter

    <!-- -->

    - #### setEscapeUriAttributes

          void setEscapeUriAttributes(boolean escapeUriAttributes)

      Sets the `escape-uri-attributes` parameter.
      When `true`, the serializer will apply URI escaping to URI attribute values, except that relative URIs will not be absolutized.

      This parameter is only applicable when the `XHTML` or `HTML` output `method` is used.

      The default value is `false`.
      Parameters:
      `escapeUriAttributes` - the value for the `escape-uri-attributes` parameter

      See Also:
      [HTML Output Method: the escape-uri-attributes Parameter](https://www.w3.org/TR/xslt-xquery-serialization-30/#HTML_ESCAPE_URI_ATTRIBUTES)

    <!-- -->

    - #### getEscapeUriAttributes

          boolean getEscapeUriAttributes()

      Gets the value of the `escape-uri-attributes` parameter. The default value is `false`.
      Returns:
      the value of the `escape-uri-attributes` parameter

    <!-- -->

    - #### setVersion

          void setVersion(java.lang.String version)

      Sets the `version` parameter. Use `null` to make this parameter absent during serialization.
      Parameters:
      `version` - the version value. May be `null`.

      Since:
      12.2

      See Also:
      [XML Output Method: the version Parameter](https://www.w3.org/TR/xslt-xquery-serialization-30/#XML_VERSION)

    <!-- -->

    - #### getVersion

          java.lang.String getVersion()

      Gets the value of the `version` parameter.
      Returns:
      the requested XML or HTML version for the serialization or 1.0 if it's not defined.

      Since:
      12.2

      See Also:
      [XML Output Method: the version Parameter](https://www.w3.org/TR/xslt-xquery-serialization-30/#XML_VERSION)

    <!-- -->

    - #### addSuppressIndentation

          void addSuppressIndentation(javax.xml.namespace.QName elementName)
                               throws XQException

      Adds an element name to the `suppress-indentation` parameter. When an element has the specified QName, it and its children will be output as if indent had a value of "no".
      Parameters:
      `elementName` - the element name. Must not be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the local part and prefix of `elementName` are not valid as NCName

      See Also:
      [XML Output Method: the indent and suppress-indentation Parameters](https://www.w3.org/TR/xslt-xquery-serialization-30/#xml_indent) or [XHTML Output Method: the indent and suppress-indentation Parameters](https://www.w3.org/TR/xslt-xquery-serialization-30/#XHTML_INDENT) or [HTML Output Method: the indent and suppress-indentation Parameters](https://www.w3.org/TR/xslt-xquery-serialization-30/#HTML_INDENT)

    <!-- -->

    - #### removeSuppressIndentation

          boolean removeSuppressIndentation(javax.xml.namespace.QName elementName)

      Removes an element name from the `suppress-indentation` parameter.
      Parameters:
      `elementName` - the element name to remove. Must not be `null`

      Returns:
      `true` if the parameter contained the specified element and `false` otherwise

      See Also:
      [XML Output Method: the indent and suppress-indentation Parameters](https://www.w3.org/TR/xslt-xquery-serialization-30/#xml_indent) or [XHTML Output Method: the indent and suppress-indentation Parameters](https://www.w3.org/TR/xslt-xquery-serialization-30/#XHTML_INDENT) or [HTML Output Method: the indent and suppress-indentation Parameters](https://www.w3.org/TR/xslt-xquery-serialization-30/#HTML_INDENT)

    <!-- -->

    - #### getSuppressIndentation

          javax.xml.namespace.QName[] getSuppressIndentation()

      Gets the `suppress-indentation` parameter.
      Returns:
      a list of the element names or `null` if none are defined

      See Also:
      [XML Output Method: the indent and suppress-indentation Parameters](https://www.w3.org/TR/xslt-xquery-serialization-30/#xml_indent) or [XHTML Output Method: the indent and suppress-indentation Parameters](https://www.w3.org/TR/xslt-xquery-serialization-30/#XHTML_INDENT) or [HTML Output Method: the indent and suppress-indentation Parameters](https://www.w3.org/TR/xslt-xquery-serialization-30/#HTML_INDENT)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](OXQSequence.md)**
- **[Next Class](OXQStackTraceElement.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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
