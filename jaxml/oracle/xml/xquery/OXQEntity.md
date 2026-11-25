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

- **[Prev Class](OXQDynamicContext.md)**
- **[Next Class](OXQEntityKind.md)**

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

## **Class OXQEntity**

- **java.lang.Object**

- - **oracle.xml.xquery.OXQEntity**

<!-- -->

- **All Implemented Interfaces:**
  **java.lang.Cloneable, [OXQCloseable](OXQCloseable.md)**

  ------------------------------------------------------------------------

  **
  **

      public final class OXQEntity
      extends java.lang.Object
      implements OXQCloseable, java.lang.Cloneable

  **The entity returned by an [`OXQEntityResolver`](OXQEntityResolver.md). The entity is made up of a `data` object, a `media-type`, and a set of properties. The type of `data` depends on the kind of entity that is being resolved. The following sections describe what `data` is expected to be for the possible [`entity kinds`](OXQEntityKind.md).**
  #### **Schema Entities ([`OXQEntityKind.SCHEMA`](OXQEntityKind.md))**

  | Type of `data`                                                                                      | Description                                                                                              |
  |-----------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
  | `java.io.InputStream`<br>`java.io.Reader`<br>`java.lang.String`<br>`javax.xml.transform.Source`<br> | A schema will be obtained by parsing `data` as an XML Schema.                                            |
  | `javax.xml.xquery.XQItem`                                                                           | A schema will be obtained by treating `data` as a parsed XML Schema.                                     |
  | An array or `java.util.Collection` of any of the above types.                                       | One or more schemas will be obtained by treating each object in the array/collection as described above. |

  **The `media-type` is currently ignored for schemas but it may be used in future releases. All schemas returned must have the target namespace that was specified in the `OXQEntityLocator` instance passed to the [`entity resolver`](OXQEntityResolver.md).**

  #### **Module Entities ([`OXQEntityKind.MODULE`](OXQEntityKind.md))**

  | Type of `data`                                                                                      | Description                                                                                                                                                                                                                                                      |
  |-----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | `java.io.InputStream`<br>`java.io.Reader`<br>`java.lang.String`<br>`javax.xml.transform.Source`<br> | If the `media-type` is `application/xquery+xml` then `data` will be parsed as an XQueryX module. Otherwise, `data` will be parsed as an XQuery module.                                                                                                           |
  | `javax.xml.xquery.XQItem`                                                                           | If the `media-type` is `application/xquery+xml` then `data` will be will be treated as a parsed XQueryX module. Otherwise, `data` will be [serialized as text](http://www.w3.org/TR/xslt-xquery-serialization/#text_output) and then parsed as an XQuery module. |
  | An array or `java.util.Collection` of any of the above types.                                       | One or more modules will be obtained by treating each object in the array/collection as described above.                                                                                                                                                         |

  - **All modules returned must have the target namespace that given by the `OXQEntityLocator` instance passed to the [`entity resolver`](OXQEntityResolver.md).**
  - **An instance of `javax.xml.xquery.XQStaticContext` can be set on the returned entity using the property `PROPERTY_MODULE_STATIC_CONTEXT`. It specifies the following default values when compiling this module:**
    - **XQuery Static Context Components (such as statically known namespaces, construction mode, ordering mode, etc) as defined by [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md),**
    - **Module language as defined by [`XQStaticContext.getQueryLanguageTypeAndVersion()`](../../../javax/xml/xquery/XQStaticContext.md),**
    - **Extension components from [`OXQStaticContext`](OXQStaticContext.md): declared functions and variables, imported modules and schemas, entity resolver.**

    **The remaining settings from either [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md) or [`OXQStaticContext`](OXQStaticContext.md) are ignored.**

  #### **Document Entities ([`OXQEntityKind.DOCUMENT`](OXQEntityKind.md))**

  | Type of `data`                                                                                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
  |-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | `java.io.InputStream`<br>`java.io.Reader`<br>`java.lang.String`<br>`javax.xml.transform.Source`<br> | A document will be obtained by parsing `data`.<br>The following media-types are supported:<br><br>• `application/xml` - unparsed XML (default)<br>• `text/xml` - unparsed XML<br>• `application/vnd.oracle.xml+csx` - CSX binary XML<br>It is an error to specify a binary media-type in combination with character data (i.e. Reader or String). When parsing, external XML entities (if any exist) will be resolved by additional calls to the entity resolver using the `XML_ENTITY` kind. |
  | `javax.xml.xquery.XQSequence`                                                                       | The sequence must either be empty or contain a single document node. This will be used directly for the `fn:doc` or `fn:collection` function.                                                                                                                                                                                                                                                                                                                                                 |
  | `javax.xml.xquery.XQItem`                                                                           | The item must be a document node. This will be used directly for the `fn:doc` or `fn:collection` function. Note, `data` may be null to signify the empty sequence.                                                                                                                                                                                                                                                                                                                            |

  **See also:**
  - **`PROPERTY_INFOSET_COMMENTS`**
  - **`PROPERTY_INFOSET_SIGNIFICANT_WHITESPACE`**
  - **`PROPERTY_INFOSET_INSIGNIFICANT_WHITESPACE`**
  - **`PROPERTY_INFOSET_NAMESPACES`**
  - **`PROPERTY_XML_PARSER_VALIDATING`**
  - **`PROPERTY_DOCUMENT_PAGE_MANAGER`**

  #### **Document Type Entities ([`OXQEntityKind.DOCUMENT_TYPE`](OXQEntityKind.md))**

  **`data` must be an instance of `java.xml.xquery.XQItemType` that is a subtype of `document-node()`. The returned type will be used as the static type of the `fn:doc` function.**

  #### **Collection Entities ([`OXQEntityKind.COLLECTION`](OXQEntityKind.md))**

  **`data` must be an instance of `java.util.Iterator<java.net.URI>`. For each URI returned, the entity resolver will be called using the `DOCUMENT` entity kind to obtain a document node. The documents will be returned by the call to `fn:collection`.**

  **Each document URI returned by the `Iterator` must be unique or an error will be raised. This uniqueness check may be disabled by setting property `PROPERTY_COLLECTION_UNIQUE_CHECK` to `false` on the returned entity using method `setProperty(int, Object)`. Even if this check is disabled, the returned document URIs must still be unique or else the query results may be incorrect. Disabling the check may improve performance in cases where there are many document URIs.**

  #### **URI Collection Entities ([`URI_COLLECTION`](OXQEntityKind.md))**

  **`data` must be an instance of `java.util.Iterator<java.net.URI>`. The [`OXQEntityKind.URI_COLLECTION`](OXQEntityKind.md) kind is used to resolve the result of a call to the `fn:uri-collection` function. Unlike the [`OXQEntityKind.COLLECTION`](OXQEntityKind.md) kind, there is no requirement that the returned URI's are unique or that they identify documents. However, entity resolvers may be implemented such that the results of `fn:collection` and `fn:collection-uri` are consistent.**

  #### **External Function Entities ([`OXQEntityKind.EXTERNAL_FUNCTION`](OXQEntityKind.md))**

  | Type of `data`     | Description                                                                                                                   |
  |--------------------|-------------------------------------------------------------------------------------------------------------------------------|
  | `java.lang.Class`  | The class must extend [`OXQFunctionEvaluator`](OXQFunctionEvaluator.md).                                                      |
  | `java.lang.Method` | The method must be static with parameter and return types that can be mapped to XQuery types as defined by XQJ specification. |

  **The `media-type` is ignored in this case.**

  #### **XML Entities ([`OXQEntityKind.XML_ENTITY`](OXQEntityKind.md))**

  **`data` must be an instance of `java.io.InputStream`, `java.xml.stream.XMLStreamReader`, or `java.xml.stream.XMLEventReader`**

  **Note, this kind is only used when the query processor needs to resolve an external XML entity while parsing unparsed XML returned for other entity kinds such as `DOCUMENT`.**
  #### **`upd:put` Entities ([`OXQEntityKind.UPD_PUT`](OXQEntityKind.md))**

  **`data` must be a *class* that extends [`OXQFunctionEvaluator`](OXQFunctionEvaluator.md). The returned class will be instantiated and then the [`evaluate`](OXQFunctionEvaluator.md) method will be invoked. The first `XQSequence` argument provided is the node to store. The second `XQSequence` argument is an absolute URI (as xs:string) which is the location where the node should be stored. Each returned [`OXQFunctionEvaluator`](OXQFunctionEvaluator.md) may be instantiated once and reused multiple times.**

  **Note, at the time the evaluator is invoked all updates have been applied and will not be undone if the `evaluate` method raises an error.**
  #### **Parser Factory Entities ([`OXQEntityKind.XML_PARSER_FACTORY`](OXQEntityKind.md))**

  **`data` must be an instance of `javax.xml.stream.XMLInputFactory`.**

  **See also:**

  - **`PROPERTY_XML_PARSER_DOCUMENT_URI`**
  - **`PROPERTY_XML_PARSER_DETECT_ENCODING`**

  #### **DOM Factory Entities ([`OXQEntityKind.DOM_FACTORY`](OXQEntityKind.md))**

  **`data` must be an instance of `javax.xml.parsers.DocumentBuilderFactory`.**

  #### **Collation Entities ([`COLLATION`](OXQEntityKind.md))**

  **`data` must be an instance of `java.text.Collator` or `oracle.i18n.text.OraCollator`. When a `java.text.Collator` is returned, the functions `fn:contains`, `fn:starts-with`, `fn:ends-with`, `fn:substring-before`, `fn:substring-after` will raise an error unless the returned Collator is also a `java.text.RuleBasedCollator`.**

  #### **Text Entities ([`TEXT`](OXQEntityKind.md))**

  **`data` must be an instance of `java.io.InputStream`, `java.io.Reader`, or `java.lang.String`. The [`TEXT`](OXQEntityKind.md) kind is used to resolve the result of a call to the `fn:unparsed-text` function. In the case of `java.io.InputStream`, the bytes will be decoded as specified by the [XPath and XQuery Functions and Operators](http://www.w3.org/TR/xpath-functions-30/#func_unparsed_text).**

  #### **Environment Variables ([`ENVIRONMENT_VARIABLE`](OXQEntityKind.md))**

  **If requesting [`OXQEntityLocator.getSystemId()`](OXQEntityLocator.md) was `null` then `data` must be an instance of `java.util.Iterator<java.lang.String>` containing all environment variable names. If [`OXQEntityLocator.getSystemId()`](OXQEntityLocator.md) was not `null` then `data` must be an instance of `java.lang.String` containing the value of the requested environment variable or `null` if there is no such variable.**

  #### **Closing resources**

  **The entity returned by [`OXQEntityResolver`](OXQEntityResolver.md) can have closeable resources associated with it through [`OXQCloseable`](OXQCloseable.md) methods. The XQuery processor assumes ownership of these resources and guarantees that they are closed when the query execution finishes.**

  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                                            |
    |---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`              | `DOCUMENT_URI_HIDE`<br>A string value constant for `PROPERTY_XML_PARSER_DOCUMENT_URI`                                                                                                                            |
    | `static int`              | `DOCUMENT_URI_PASS`<br>A string value constant for `PROPERTY_XML_PARSER_DOCUMENT_URI`                                                                                                                            |
    | `static int`              | `DOCUMENT_URI_PASS_URL`<br>A string value constant for `PROPERTY_XML_PARSER_DOCUMENT_URI`                                                                                                                        |
    | `static java.lang.String` | `MEDIA_TYPE_APPLICATION_XML`<br>Media-type "application/xml"                                                                                                                                                     |
    | `static java.lang.String` | `MEDIA_TYPE_ORACLE_CSX`<br>Media-type "application/vnd.oracle.xml+csx"                                                                                                                                           |
    | `static java.lang.String` | `MEDIA_TYPE_ORACLE_XPATH`<br>Media-type "application/vnd.oracle.xml.xpath"                                                                                                                                       |
    | `static java.lang.String` | `MEDIA_TYPE_TEXT_XML`<br>Media-type "text/xml"                                                                                                                                                                   |
    | `static java.lang.String` | `MEDIA_TYPE_XQUERY`<br>Media-type "application/xquery"                                                                                                                                                           |
    | `static java.lang.String` | `MEDIA_TYPE_XQUERYX`<br>Media-type "application/xquery+xml"                                                                                                                                                      |
    | `static int`              | `PROPERTY_COLLECTION_UNIQUE_CHECK`<br>The property that specifies whether or not the XQuery processor will ensure that the document URIs returned by a [`COLLECTION`](OXQEntityKind.md) entity are unique.       |
    | `static int`              | `PROPERTY_DOCUMENT_PAGE_MANAGER`<br>The property that specifies an instance of [`PageManager`](../scalable/PageManager.md) that will be used to store a [`DOCUMENT`](OXQEntityKind.md) entity.                   |
    | `static int`              | `PROPERTY_INFOSET_COMMENTS`<br>The property that specifies whether comment nodes are preserved when converting XML to the XQuery data model.                                                                     |
    | `static int`              | `PROPERTY_INFOSET_INSIGNIFICANT_WHITESPACE`<br>The property that specifies whether insignificant whitespace in an XML document is preserved or ignored when converting XML to the XQuery data model.             |
    | `static int`              | `PROPERTY_INFOSET_NAMESPACES`<br>The property that specifies whether namespaces that are not known to be used are preserved when converting XML to the XQuery data model.                                        |
    | `static int`              | `PROPERTY_INFOSET_SIGNIFICANT_WHITESPACE`<br>The property that specifies whether significant whitespace in an XML document is preserved or ignored when converting XML to the XQuery data model.                 |
    | `static int`              | `PROPERTY_MODULE_STATIC_CONTEXT`<br>The property that specifies an instance of [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md) to be used with a returned [`MODULE`](OXQEntityKind.md) entity. |
    | `static int`              | `PROPERTY_XML_PARSER_DETECT_ENCODING`<br>The property that specifies whether the XML parser performs document encoding detection or the encoding is detected by the XQuery processor.                            |
    | `static int`              | `PROPERTY_XML_PARSER_DOCUMENT_URI`<br>The property that specifies whether the XQuery processor passes the document URI to the XML parser or not.                                                                 |
    | `static int`              | `PROPERTY_XML_PARSER_VALIDATING`<br>The property that specifies whether or not to use a validating XML parser (performing DTD validation).                                                                       |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                               |
    |-------------------------------------------------------------------------------------------|
    | `OXQEntity``(java.lang.Object data)`<br>Constructs an entity.                             |
    | `OXQEntity``(java.lang.Object data, java.lang.String mediaType)`<br>Constructs an entity. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                                                                                                      |
    |----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OXQEntity`          | `clone``()`<br>Standard override; no change in semantics.                                                                                                                   |
    | `void`               | `enlistCloseable``(java.io.Closeable closeable)`<br>Declares a `closeable` object that will be closed when this object is closed.                                           |
    | `void`               | `enlistCloseable``(javax.xml.stream.XMLStreamReader closeable)`<br>Declares an `XMLStreamReader` object that will be closed when this object is closed.                     |
    | `void`               | `enlistCloseable``(`[`XQSequence`](../../../javax/xml/xquery/XQSequence.md)` closeable)`<br>Declares an `XQSequence` object that will be closed when this object is closed. |
    | `java.lang.Object`   | `getData``()`<br>Returns the entity.                                                                                                                                        |
    | `java.lang.Object[]` | `getEnlistedCloseables``()`<br>Returns closeable resources associated with this entity.                                                                                     |
    | `java.lang.String`   | `getMediaType``()`<br>Returns the Media-Type of the entity                                                                                                                  |
    | `java.lang.Object`   | `getProperty``(int key)`<br>Returns the property value for the given property key.                                                                                          |
    | `void`               | `setData``(java.lang.Object data)`<br>Sets the entity.                                                                                                                      |
    | `void`               | `setMediaType``(java.lang.String mediaType)`<br>Sets the Media-Type of the entity.                                                                                          |
    | `void`               | `setProperty``(int key, java.lang.Object value)`<br>Sets additional processing options for this entity.                                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### MEDIA_TYPE_APPLICATION_XML

          public static final java.lang.String MEDIA_TYPE_APPLICATION_XML

      Media-type "application/xml"
      See Also:
      `setMediaType(String)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MEDIA_TYPE_TEXT_XML

          public static final java.lang.String MEDIA_TYPE_TEXT_XML

      Media-type "text/xml"
      See Also:
      `setMediaType(String)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MEDIA_TYPE_ORACLE_CSX

          public static final java.lang.String MEDIA_TYPE_ORACLE_CSX

      Media-type "application/vnd.oracle.xml+csx"
      See Also:
      `setMediaType(String)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MEDIA_TYPE_ORACLE_XPATH

          public static final java.lang.String MEDIA_TYPE_ORACLE_XPATH

      Media-type "application/vnd.oracle.xml.xpath"
      See Also:
      `setMediaType(String)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MEDIA_TYPE_XQUERY

          public static final java.lang.String MEDIA_TYPE_XQUERY

      Media-type "application/xquery"
      See Also:
      `setMediaType(String)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MEDIA_TYPE_XQUERYX

          public static final java.lang.String MEDIA_TYPE_XQUERYX

      Media-type "application/xquery+xml"
      See Also:
      `setMediaType(String)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_XML_PARSER_DOCUMENT_URI

          public static final int PROPERTY_XML_PARSER_DOCUMENT_URI

      The property that specifies whether the XQuery processor passes the document URI to the XML parser or not. Supported values are the following:
      - `DOCUMENT_URI_PASS` - document URI is passed to the XML parser,
      - `DOCUMENT_URI_HIDE` - document URI is not passed to the XML parser,
      - `DOCUMENT_URI_PASS_URL` - document URI is passed to the XML parser only if it's a valid `URL` (default)

      See Also:
      [`OXQEntityKind.XML_PARSER_FACTORY`](OXQEntityKind.md), [`OXQEntityKind.DOCUMENT`](OXQEntityKind.md), `setProperty(int, Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_XML_PARSER_DETECT_ENCODING

          public static final int PROPERTY_XML_PARSER_DETECT_ENCODING

      The property that specifies whether the XML parser performs document encoding detection or the encoding is detected by the XQuery processor. The property value must be an instance of `java.lang.Boolean`:
      - When `true`, the XML parser detects the document encoding (default),
      - When `false`, the XQuery processor detects the document encoding

      See Also:
      [`OXQEntityKind.XML_PARSER_FACTORY`](OXQEntityKind.md), `setProperty(int, Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_XML_PARSER_VALIDATING

          public static final int PROPERTY_XML_PARSER_VALIDATING

      The property that specifies whether or not to use a validating XML parser (performing DTD validation). If XML parser doesn't support DTD validation property `javax.xml.stream.XMLInputFactory.IS_VALIDATING` then this option is ignored. The property value must be an instance of `java.lang.Boolean`:
      - When `true`, validating (default),
      - When `false`, non-validating

      See Also:
      [`OXQEntityKind.DOCUMENT`](OXQEntityKind.md), `setProperty(int, Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_INFOSET_COMMENTS

          public static final int PROPERTY_INFOSET_COMMENTS

      The property that specifies whether comment nodes are preserved when converting XML to the XQuery data model. The property value must be an instance of `java.lang.Boolean`:
      - When `true`, comment nodes are preserved (default),
      - When `false`, comment nodes are ignored

      See Also:
      [`OXQEntityKind.DOCUMENT`](OXQEntityKind.md), `setProperty(int, Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_INFOSET_NAMESPACES

          public static final int PROPERTY_INFOSET_NAMESPACES

      The property that specifies whether namespaces that are not known to be used are preserved when converting XML to the XQuery data model. See [XDM : Element Nodes / Construction from Infoset](http://www.w3.org/TR/xpath-datamodel/#const-infoset-element) for more information. The property value must be an instance of `java.lang.Boolean`:
      - When `true`, document will contain all namespaces, even those that are not known as per the XDM specification (default),
      - When `false`, document will only those namespace that are known

      See Also:
      [`OXQEntityKind.DOCUMENT`](OXQEntityKind.md), `setProperty(int, Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_INFOSET_SIGNIFICANT_WHITESPACE

          public static final int PROPERTY_INFOSET_SIGNIFICANT_WHITESPACE

      The property that specifies whether significant whitespace in an XML document is preserved or ignored when converting XML to the XQuery data model. According to the XML specification, an XML parser can only detect whether whitespace in element content is significant or not if it's in validation mode (`PROPERTY_XML_PARSER_VALIDATING`). In non-validating mode the parser cannot make that decision and therefore will report all whitespace as significant. This option only controls significant whitespace handling. The property value must be an instance of `java.lang.Boolean`:
      - When `true`, the document will contain significant whitespace as reported by the XML parser (default),
      - When `false`, the document will not contain significant whitespace

      See Also:
      [`OXQEntityKind.DOCUMENT`](OXQEntityKind.md), `setProperty(int, Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_INFOSET_INSIGNIFICANT_WHITESPACE

          public static final int PROPERTY_INFOSET_INSIGNIFICANT_WHITESPACE

      The property that specifies whether insignificant whitespace in an XML document is preserved or ignored when converting XML to the XQuery data model. According to the XML specification an XML parser can detect whether whitespace in element content is significant or not if it's in validation mode (`PROPERTY_XML_PARSER_VALIDATING`). This option only controls insignificant whitespace handling (also called element content whitespace). The property value must be an instance of `java.lang.Boolean`:
      - When `true`, the document will contain insignificant whitespace as reported by the XML parser
      - When `false`, the document will not contain insignificant whitespace (default).

      See Also:
      [`OXQEntityKind.DOCUMENT`](OXQEntityKind.md), `setProperty(int, Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_COLLECTION_UNIQUE_CHECK

          public static final int PROPERTY_COLLECTION_UNIQUE_CHECK

      The property that specifies whether or not the XQuery processor will ensure that the document URIs returned by a [`COLLECTION`](OXQEntityKind.md) entity are unique. Even if this check is disabled, the returned document URIs must still be unique or else the query results may be incorrect. Disabling the check may improve performance in cases where there are many document URIs. The property value must be an instance of `java.lang.Boolean`:
      - When `true`, the XQuery processor will raise an error if the document URIs are not unique (default)
      - When `false`, the XQuery processor will not check that the document URIs are unique.

      See Also:
      [`OXQEntityKind.COLLECTION`](OXQEntityKind.md), `setProperty(int, Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_MODULE_STATIC_CONTEXT

          public static final int PROPERTY_MODULE_STATIC_CONTEXT

      The property that specifies an instance of [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md) to be used with a returned [`MODULE`](OXQEntityKind.md) entity. The property value must be an instance of [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md)
      See Also:
      [`OXQEntityKind.MODULE`](OXQEntityKind.md), `setProperty(int, Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_DOCUMENT_PAGE_MANAGER

          public static final int PROPERTY_DOCUMENT_PAGE_MANAGER

      The property that specifies an instance of [`PageManager`](../scalable/PageManager.md) that will be used to store a [`DOCUMENT`](OXQEntityKind.md) entity. The returned document will be copied into the `PageManager`. The pages will be released (deleted) when the query [`result`](../../../javax/xml/xquery/XQResultSequence.md) is closed. The property value must be an instance of [`PageManager`](../scalable/PageManager.md)
      See Also:
      [`OXQEntityKind.DOCUMENT`](OXQEntityKind.md), `setProperty(int, Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DOCUMENT_URI_PASS

          public static final int DOCUMENT_URI_PASS

      A string value constant for `PROPERTY_XML_PARSER_DOCUMENT_URI`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DOCUMENT_URI_HIDE

          public static final int DOCUMENT_URI_HIDE

      A string value constant for `PROPERTY_XML_PARSER_DOCUMENT_URI`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DOCUMENT_URI_PASS_URL

          public static final int DOCUMENT_URI_PASS_URL

      A string value constant for `PROPERTY_XML_PARSER_DOCUMENT_URI`
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OXQEntity

          public OXQEntity(java.lang.Object data)

      Constructs an entity.
      Parameters:
      `data` - The entity.

    <!-- -->

    - #### OXQEntity

          public OXQEntity(java.lang.Object data,
                           java.lang.String mediaType)

      Constructs an entity.
      Parameters:
      `data` - The entity.

      `mediaType` - Media-Type of the entity

  <!-- -->

  - ### Method Detail

    - #### setData

          public void setData(java.lang.Object data)

      Sets the entity.
      Parameters:
      `data` - the entity

    <!-- -->

    - #### getData

          public java.lang.Object getData()

      Returns the entity.
      Returns:
      the entity

    <!-- -->

    - #### setMediaType

          public void setMediaType(java.lang.String mediaType)

      Sets the Media-Type of the entity.
      Parameters:
      `mediaType` - the Media-Type

    <!-- -->

    - #### getMediaType

          public java.lang.String getMediaType()

      Returns the Media-Type of the entity
      Returns:
      the Media-Type

    <!-- -->

    - #### setProperty

          public void setProperty(int key,
                                  java.lang.Object value)

      Sets additional processing options for this entity.
      Parameters:
      `key` - the property key

      `value` - the property value

    <!-- -->

    - #### getProperty

          public java.lang.Object getProperty(int key)

      Returns the property value for the given property key.
      Returns:
      the property value

    <!-- -->

    - #### clone

          public OXQEntity clone()

      Standard override; no change in semantics.
      Overrides:
      `clone` in class `java.lang.Object`

    <!-- -->

    - #### enlistCloseable

          public void enlistCloseable(java.io.Closeable closeable)

      Description copied from interface: [`OXQCloseable`](OXQCloseable.md)
      Declares a `closeable` object that will be closed when this object is closed.
      Specified by:
      [`enlistCloseable`](OXQCloseable.md) in interface [`OXQCloseable`](OXQCloseable.md)

      Parameters:
      `closeable` - input streaming object that `close()` must be invoked on after `close()` is invoked on this object.

      See Also:
      [`Detailed description`](OXQCloseable.md)

    <!-- -->

    - #### enlistCloseable

          public void enlistCloseable(javax.xml.stream.XMLStreamReader closeable)

      Description copied from interface: [`OXQCloseable`](OXQCloseable.md)
      Declares an `XMLStreamReader` object that will be closed when this object is closed.
      Note: `XMLStreamReader` implementations don't usually conform to the thread-safety semantics defined above, so their use as resources is not recommended in multi-threaded environments.

      Specified by:
      [`enlistCloseable`](OXQCloseable.md) in interface [`OXQCloseable`](OXQCloseable.md)

      Parameters:
      `closeable` - object that `close()` must be invoked on after `close()` is invoked on this object.

      See Also:
      [`Detailed description`](OXQCloseable.md)

    <!-- -->

    - #### enlistCloseable

          public void enlistCloseable(XQSequence closeable)

      Description copied from interface: [`OXQCloseable`](OXQCloseable.md)
      Declares an `XQSequence` object that will be closed when this object is closed.
      Specified by:
      [`enlistCloseable`](OXQCloseable.md) in interface [`OXQCloseable`](OXQCloseable.md)

      Parameters:
      `closeable` - object that `close()` must be invoked on after `close()` is invoked on this object.

      See Also:
      [`Detailed description`](OXQCloseable.md)

    <!-- -->

    - #### getEnlistedCloseables

          public java.lang.Object[] getEnlistedCloseables()

      Returns closeable resources associated with this entity.
      Returns:
      array of closeable resources or `null` if no resources have been registered

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

- **[Prev Class](OXQDynamicContext.md)**
- **[Next Class](OXQEntityKind.md)**

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
