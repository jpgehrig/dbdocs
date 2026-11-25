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

- **[Prev Class](XSDAttribute.md)**
- **[Next Class](XSDComplexType.md)**

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

**oracle.xml.parser.schema**

## **Class XSDBuilder**

- **java.lang.Object**

- - **oracle.xml.parser.schema.XSDBuilder**

<!-- -->

- **All Implemented Interfaces:**
  **[XSDConstantValues](XSDConstantValues.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XSDBuilder
      extends java.lang.Object
      implements XSDConstantValues

  **Builds an XMLSchema object from XMLSchema document. XMLSchema object is a set of objects (Infoset items) corresponding to top-level schema declarations and definitions. The Schema document is parsed as XML and converted to a DOM tree. This schema DOM tree is 'Schema' parsed in the following order: \<import\> (if any) builds a schema object and makes it visible. \<include\> (if any) is replaced by corresponding DOM tree. Top-level declarations and definitions are registered as the current schema infoset items. Finally, top-level tree elements (infoset items) are 'Schema' parsed. Those include \<element\>, \<simpleType\>, \<complexType\>, \<annotation\>, \<group\>, \<attribute\>, \<attributeGroup\>, \<notation\>, etc. The result XMLSchema object is a set (infoset) of objects (top-level input elements). Object's contents is a tree with nodes corresponding to low-level element/group decls/refs preceded by node/object of type XSDNode containg cardinality info (minOccurs/maxOccurs).**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description   |
    |---------------------------|-------------------------|
    | `static java.lang.String` | `ANNOTATION_CONTEXT`    |
    | `static java.lang.String` | `IGNORE_DUPLICATE`      |
    | `static java.lang.String` | `IGNORE_DUPLICATES`     |
    | `static java.lang.String` | `IMPORT_INCLUDE_ERROR`  |
    | `static java.lang.String` | `INCREMENTAL_BUILD`     |
    | `static java.lang.String` | `KEEP_DOM_NODE`         |
    | `static java.lang.String` | `NAMESPACE_CONTEXT`     |
    | `static java.lang.String` | `SCHEMA_ANNOTATION`     |
    | `static java.lang.String` | `SORT_SCHEMA_IMPORTS`   |
    | `static java.lang.String` | `SQL_OFFLINE_SIZE`      |
    | `static java.lang.String` | `XDB_SQLINLINE`         |

    -

      ### **Fields inherited from interface oracle.xml.parser.schema.[XSDConstantValues](XSDConstantValues.md)**

      **[`_abstract`](XSDConstantValues.md)`, `[`_all`](XSDConstantValues.md)`, `[`_annotation`](XSDConstantValues.md)`, `[`_any`](XSDConstantValues.md)`, `[`_anyAttribute`](XSDConstantValues.md)`, `[`_anySimpleType`](XSDConstantValues.md)`, `[`_anyType`](XSDConstantValues.md)`, `[`_appinfo`](XSDConstantValues.md)`, `[`_attrFormDefault`](XSDConstantValues.md)`, `[`_attribute`](XSDConstantValues.md)`, `[`_attributeGroup`](XSDConstantValues.md)`, `[`_attrTag`](XSDConstantValues.md)`, `[`_base`](XSDConstantValues.md)`, `[`_block`](XSDConstantValues.md)`, `[`_blockDefault`](XSDConstantValues.md)`, `[`_choice`](XSDConstantValues.md)`, `[`_complexContent`](XSDConstantValues.md)`, `[`_complexType`](XSDConstantValues.md)`, `[`_content`](XSDConstantValues.md)`, `[`_default`](XSDConstantValues.md)`, `[`_derivedBy`](XSDConstantValues.md)`, `[`_documentation`](XSDConstantValues.md)`, `[`_element`](XSDConstantValues.md)`, `[`_elementOnly`](XSDConstantValues.md)`, `[`_elemFormDefault`](XSDConstantValues.md)`, `[`_empty`](XSDConstantValues.md)`, `[`_enumeration`](XSDConstantValues.md)`, `[`_equivClass`](XSDConstantValues.md)`, `[`_extension`](XSDConstantValues.md)`, `[`_false`](XSDConstantValues.md)`, `[`_field`](XSDConstantValues.md)`, `[`_final`](XSDConstantValues.md)`, `[`_finalDefault`](XSDConstantValues.md)`, `[`_fixed`](XSDConstantValues.md)`, `[`_form`](XSDConstantValues.md)`, `[`_group`](XSDConstantValues.md)`, `[`_id`](XSDConstantValues.md)`, `[`_import`](XSDConstantValues.md)`, `[`_include`](XSDConstantValues.md)`, `[`_itemType`](XSDConstantValues.md)`, `[`_key`](XSDConstantValues.md)`, `[`_keyref`](XSDConstantValues.md)`, `[`_lax`](XSDConstantValues.md)`, `[`_list`](XSDConstantValues.md)`, `[`_maxOccurs`](XSDConstantValues.md)`, `[`_memberTypes`](XSDConstantValues.md)`, `[`_minOccurs`](XSDConstantValues.md)`, `[`_mixed`](XSDConstantValues.md)`, `[`_nall`](XSDConstantValues.md)`, `[`_name`](XSDConstantValues.md)`, `[`_namespace`](XSDConstantValues.md)`, `[`_nil`](XSDConstantValues.md)`, `[`_nillable`](XSDConstantValues.md)`, `[`_nnany`](XSDConstantValues.md)`, `[`_nnlist`](XSDConstantValues.md)`, `[`_nnlocal`](XSDConstantValues.md)`, `[`_nnother`](XSDConstantValues.md)`, `[`_nntargetNS`](XSDConstantValues.md)`, `[`_noNSSchemaLocation`](XSDConstantValues.md)`, `[`_notation`](XSDConstantValues.md)`, `[`_null`](XSDConstantValues.md)`, `[`_nullable`](XSDConstantValues.md)`, `[`_optional`](XSDConstantValues.md)`, `[`_pattern`](XSDConstantValues.md)`, `[`_processContents`](XSDConstantValues.md)`, `[`_prohibited`](XSDConstantValues.md)`, `[`_publicid`](XSDConstantValues.md)`, `[`_qualified`](XSDConstantValues.md)`, `[`_redefine`](XSDConstantValues.md)`, `[`_ref`](XSDConstantValues.md)`, `[`_refer`](XSDConstantValues.md)`, `[`_required`](XSDConstantValues.md)`, `[`_restriction`](XSDConstantValues.md)`, `[`_restrictions`](XSDConstantValues.md)`, `[`_schemaLocation`](XSDConstantValues.md)`, `[`_selector`](XSDConstantValues.md)`, `[`_sequence`](XSDConstantValues.md)`, `[`_simpleContent`](XSDConstantValues.md)`, `[`_simpleType`](XSDConstantValues.md)`, `[`_skip`](XSDConstantValues.md)`, `[`_strict`](XSDConstantValues.md)`, `[`_substitution`](XSDConstantValues.md)`, `[`_substitutionGrp`](XSDConstantValues.md)`, `[`_systemid`](XSDConstantValues.md)`, `[`_targetNS`](XSDConstantValues.md)`, `[`_textOnly`](XSDConstantValues.md)`, `[`_this`](XSDConstantValues.md)`, `[`_true`](XSDConstantValues.md)`, `[`_type`](XSDConstantValues.md)`, `[`_undef`](XSDConstantValues.md)`, `[`_union`](XSDConstantValues.md)`, `[`_unique`](XSDConstantValues.md)`, `[`_unqualified`](XSDConstantValues.md)`, `[`_use`](XSDConstantValues.md)`, `[`_value`](XSDConstantValues.md)`, `[`_version`](XSDConstantValues.md)`, `[`_xmlns`](XSDConstantValues.md)`, `[`ABSENT_NS`](XSDConstantValues.md)`, `[`ACCEPTED`](XSDConstantValues.md)`, `[`ALL`](XSDConstantValues.md)`, `[`ANNOTATION`](XSDConstantValues.md)`, `[`ANY`](XSDConstantValues.md)`, `[`ANY_ATTRIBUTE`](XSDConstantValues.md)`, `[`ANY_NODE`](XSDConstantValues.md)`, `[`ATTRIBUTE`](XSDConstantValues.md)`, `[`ATTRIBUTE_GROUP`](XSDConstantValues.md)`, `[`AUTO_VALIDATION`](XSDConstantValues.md)`, `[`BASE_RESOLVED`](XSDConstantValues.md)`, `[`BASE_UNRESOLVED`](XSDConstantValues.md)`, `[`BASE_URL`](XSDConstantValues.md)`, `[`BUILD_FAIL`](XSDConstantValues.md)`, `[`CHOICE`](XSDConstantValues.md)`, `[`CIRCULAR_SUBST`](XSDConstantValues.md)`, `[`CONFLICIT_FACET`](XSDConstantValues.md)`, `[`constName`](XSDConstantValues.md)`, `[`DATATYPE`](XSDConstantValues.md)`, `[`DEEP_VALIDATION`](XSDConstantValues.md)`, `[`derivationBlock`](XSDConstantValues.md)`, `[`DONE`](XSDConstantValues.md)`, `[`DUPLICATE_DEF`](XSDConstantValues.md)`, `[`duplicateId`](XSDConstantValues.md)`, `[`ELEMENT`](XSDConstantValues.md)`, `[`ELEMENT_CHILD`](XSDConstantValues.md)`, `[`ELEMENT_ONLY`](XSDConstantValues.md)`, `[`elemNotNullable`](XSDConstantValues.md)`, `[`EMPTY`](XSDConstantValues.md)`, `[`ENTITY_RESOLVER`](XSDConstantValues.md)`, `[`EQUIV_RESOLVED`](XSDConstantValues.md)`, `[`EQUIV_UNRESOLVED`](XSDConstantValues.md)`, `[`ERROR`](XSDConstantValues.md)`, `[`EXTENTION`](XSDConstantValues.md)`, `[`FACET_CHILD`](XSDConstantValues.md)`, `[`FAKE_ATTR`](XSDConstantValues.md)`, `[`FAKE_NODE`](XSDConstantValues.md)`, `[`FIXED_SCHEMA`](XSDConstantValues.md)`, `[`GROUP`](XSDConstantValues.md)`, `[`IABSTRACT`](XSDConstantValues.md)`, `[`IBLOCKEXT`](XSDConstantValues.md)`, `[`IBLOCKRST`](XSDConstantValues.md)`, `[`IBLOCKSUB`](XSDConstantValues.md)`, `[`IDENTITY_ERROR`](XSDConstantValues.md)`, `[`IDENTITY_KEY`](XSDConstantValues.md)`, `[`IDENTITY_KEYREF`](XSDConstantValues.md)`, `[`IDENTITY_UNIQUE`](XSDConstantValues.md)`, `[`IFINALEXT`](XSDConstantValues.md)`, `[`IFINALLIST`](XSDConstantValues.md)`, `[`IFINALRST`](XSDConstantValues.md)`, `[`IFINALUNION`](XSDConstantValues.md)`, `[`IMPORT`](XSDConstantValues.md)`, `[`INCLUDE`](XSDConstantValues.md)`, `[`INCORRECT_ATTR`](XSDConstantValues.md)`, `[`INCORRECT_ELEM`](XSDConstantValues.md)`, `[`INFINITY`](XSDConstantValues.md)`, `[`INTERNAL_ERROR`](XSDConstantValues.md)`, `[`INVALID_DATE`](XSDConstantValues.md)`, `[`INVALID_DATETIME`](XSDConstantValues.md)`, `[`INVALID_DERIVATION`](XSDConstantValues.md)`, `[`INVALID_FACET`](XSDConstantValues.md)`, `[`INVALID_FACET_VALUE`](XSDConstantValues.md)`, `[`INVALID_NOTATION`](XSDConstantValues.md)`, `[`INVALID_REGEX`](XSDConstantValues.md)`, `[`INVALID_SCHEMA_NS`](XSDConstantValues.md)`, `[`INVALID_TIME`](XSDConstantValues.md)`, `[`INVALID_TYPE_VALUE`](XSDConstantValues.md)`, `[`invalidAttr`](XSDConstantValues.md)`, `[`invalidAttrVal`](XSDConstantValues.md)`, `[`invalidChars`](XSDConstantValues.md)`, `[`invalidElem`](XSDConstantValues.md)`, `[`invalidFixedChars`](XSDConstantValues.md)`, `[`invalidNS`](XSDConstantValues.md)`, `[`invalidPrefix`](XSDConstantValues.md)`, `[`invalidProperty`](XSDConstantValues.md)`, `[`invalidRef`](XSDConstantValues.md)`, `[`invalidSubstitution`](XSDConstantValues.md)`, `[`invalidTargetNS`](XSDConstantValues.md)`, `[`LAX_VALIDATION`](XSDConstantValues.md)`, `[`MISSING_NS`](XSDConstantValues.md)`, `[`missingAttr`](XSDConstantValues.md)`, `[`MIXED`](XSDConstantValues.md)`, `[`NEW_STATE`](XSDConstantValues.md)`, `[`NO_CHILD`](XSDConstantValues.md)`, `[`noDefinition`](XSDConstantValues.md)`, `[`NOT_DONE`](XSDConstantValues.md)`, `[`NOTATION`](XSDConstantValues.md)`, `[`notComplete`](XSDConstantValues.md)`, `[`notSubstitutable`](XSDConstantValues.md)`, `[`notSubTypeOf`](XSDConstantValues.md)`, `[`NS_CONFLICT`](XSDConstantValues.md)`, `[`NS_DIF_SPECIFIED`](XSDConstantValues.md)`, `[`NS_NOT_ALLOWED`](XSDConstantValues.md)`, `[`NS_NOT_EXPECTED`](XSDConstantValues.md)`, `[`NS_NOT_SAME`](XSDConstantValues.md)`, `[`NS_RESOLVER`](XSDConstantValues.md)`, `[`REDEFINE`](XSDConstantValues.md)`, `[`REF_RESOLVED`](XSDConstantValues.md)`, `[`REF_UNRESOLVED`](XSDConstantValues.md)`, `[`RESTRICTION`](XSDConstantValues.md)`, `[`ROOT_ELEMENT`](XSDConstantValues.md)`, `[`ROOT_NODE`](XSDConstantValues.md)`, `[`ROOT_TYPE`](XSDConstantValues.md)`, `[`SCHEMA_NS`](XSDConstantValues.md)`, `[`SCHEMA_RESOLVER`](XSDConstantValues.md)`, `[`SEQ`](XSDConstantValues.md)`, `[`STRICT_VALIDATION`](XSDConstantValues.md)`, `[`TEXT_ONLY`](XSDConstantValues.md)`, `[`TOP_LEVEL`](XSDConstantValues.md)`, `[`TYPE`](XSDConstantValues.md)`, `[`TYPE_RESOLVED`](XSDConstantValues.md)`, `[`TYPE_UNRESOLVED`](XSDConstantValues.md)`, `[`UNDEF`](XSDConstantValues.md)`, `[`unexpectedAttr`](XSDConstantValues.md)`, `[`unexpectedElem`](XSDConstantValues.md)`, `[`VALIDATION_MODE`](XSDConstantValues.md)`, `[`VIOLATE_FACET`](XSDConstantValues.md)`, `[`XSDRECNS`](XSDConstantValues.md)`, `[`XSDRECTYPENS`](XSDConstantValues.md)`, `[`XSIRECNS`](XSDConstantValues.md)`, `[`XSITYPE_ABSENT`](XSDConstantValues.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                |
    |--------------------------------------------|
    | `XSDBuilder``()`<br>XSDBuilder constructor |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                |
    |-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XMLSchema`](XMLSchema.md) | `build``(`[`InputSource`](../../../../org/xml/sax/InputSource.md)` source)`<br>Build an XMLSchema object                                                              |
    | [`XMLSchema`](XMLSchema.md) | `build``(java.io.InputStream in, java.net.URL baseurl)`<br>Build an XMLSchema object                                                                                  |
    | [`XMLSchema`](XMLSchema.md) | `build``(java.io.Reader r, java.net.URL baseurl)`<br>Build an XMLSchema object                                                                                        |
    | [`XMLSchema`](XMLSchema.md) | `build``(java.lang.String sysId)`<br>Build an XMLSchema object                                                                                                        |
    | [`XMLSchema`](XMLSchema.md) | `build``(java.lang.String ns, java.lang.String sysid)`<br>Build an XMLSchema object                                                                                   |
    | [`XMLSchema`](XMLSchema.md) | `build``(java.lang.String ns, java.net.URL sysid)`<br>Build an XMLSchema object                                                                                       |
    | [`XMLSchema`](XMLSchema.md) | `build``(java.net.URL schemaurl)`<br>Build an XMLSchema object                                                                                                        |
    | [`XMLSchema`](XMLSchema.md) | `build``(`[`XMLDocument`](../v2/XMLDocument.md)`[] schemaDoc)`<br>Build XMLSchema from a set of XML documents The system id of each document is used as the based uri |
    | [`XMLSchema`](XMLSchema.md) | `build``(`[`XMLDocument`](../v2/XMLDocument.md)`[] schemaDoc, java.net.URL baseurl)`<br>Build XMLSchema from a set of XML documents                                   |
    | [`XMLSchema`](XMLSchema.md) | `build``(`[`XMLDocument`](../v2/XMLDocument.md)` doc, java.lang.String fragment, java.lang.String ns, java.net.URL baseurl)`<br>Build an XMLSchema object             |
    | [`XMLSchema`](XMLSchema.md) | `build``(`[`XMLDocument`](../v2/XMLDocument.md)` schemaDoc, java.net.URL baseurl)`<br>Build XMLSchema from XML document                                               |
    | [`XMLSchema`](XMLSchema.md) | `build``(`[`XMLElement`](../v2/XMLElement.md)`[] schemaDoc, java.net.URL baseurl)`<br>Build XMLSchema from a set of XMLElements                                       |
    | `java.lang.Object`          | `getObject``()`<br>Returns the schema object.                                                                                                                         |
    | `java.util.HashSet`         | `getSchemaCircle``()`                                                                                                                                                 |
    | `void`                      | `setDebugMode``(boolean mode)`<br>Sets debug mode.                                                                                                                    |
    | `void`                      | `setEntityResolver``(`[`EntityResolver`](../../../../org/xml/sax/EntityResolver.md)` entResolver)`<br>Set an EntityResolver for resolving imports/include             |
    | `void`                      | `setError``(`[`XMLError`](../v2/XMLError.md)` er)`<br>Sets XMLError object.                                                                                           |
    | `void`                      | `setJAXP``(boolean jaxp)`<br>Set JAXP mode, in this mode, only resolved URI will be sent to entityResolver.                                                           |
    | `void`                      | `setLocale``(java.util.Locale locale)`<br>Sets locale for error reporting.                                                                                            |
    | `void`                      | `setXMLProperty``(java.lang.String name, java.lang.Object value)`                                                                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### SCHEMA_ANNOTATION

          public static final java.lang.String SCHEMA_ANNOTATION

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XDB_SQLINLINE

          public static final java.lang.String XDB_SQLINLINE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SQL_OFFLINE_SIZE

          public static final java.lang.String SQL_OFFLINE_SIZE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SORT_SCHEMA_IMPORTS

          public static final java.lang.String SORT_SCHEMA_IMPORTS

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ANNOTATION_CONTEXT

          public static final java.lang.String ANNOTATION_CONTEXT

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### KEEP_DOM_NODE

          public static final java.lang.String KEEP_DOM_NODE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### INCREMENTAL_BUILD

          public static final java.lang.String INCREMENTAL_BUILD

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NAMESPACE_CONTEXT

          public static final java.lang.String NAMESPACE_CONTEXT

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IMPORT_INCLUDE_ERROR

          public static final java.lang.String IMPORT_INCLUDE_ERROR

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IGNORE_DUPLICATES

          public static final java.lang.String IGNORE_DUPLICATES

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IGNORE_DUPLICATE

          public static final java.lang.String IGNORE_DUPLICATE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XSDBuilder

          public XSDBuilder()
                     throws XSDException

      XSDBuilder constructor
      Throws:
      [`XSDException`](XSDException.md)

  <!-- -->

  - ### Method Detail

    - #### setError

          public void setError(XMLError er)

      Sets XMLError object.
      Parameters:
      `er` - XMLError object

    <!-- -->

    - #### setDebugMode

          public void setDebugMode(boolean mode)

      Sets debug mode.
      Parameters:
      `mode` - boolean

    <!-- -->

    - #### setLocale

          public void setLocale(java.util.Locale locale)

      Sets locale for error reporting.
      Parameters:
      `locale` - Locale object

    <!-- -->

    - #### setEntityResolver

          public void setEntityResolver(EntityResolver entResolver)

      Set an EntityResolver for resolving imports/include
      Parameters:
      `entResolver` - EntityResolver

      See Also:
      [`EntityResolver`](../../../../org/xml/sax/EntityResolver.md)

    <!-- -->

    - #### setJAXP

          public void setJAXP(boolean jaxp)

      Set JAXP mode, in this mode, only resolved URI will be sent to entityResolver.
      Parameters:
      `jaxp` - - true for JAXP mode

    <!-- -->

    - #### setXMLProperty

          public void setXMLProperty(java.lang.String name,
                                     java.lang.Object value)
                              throws java.lang.IllegalArgumentException

      Throws:
      `java.lang.IllegalArgumentException`

    <!-- -->

    - #### getSchemaCircle

          public java.util.HashSet getSchemaCircle()

    <!-- -->

    - #### getObject

          public java.lang.Object getObject()

      Returns the schema object.
      Returns:
      XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(java.lang.String sysId)
                          throws XSDException

      Build an XMLSchema object
      Parameters:
      `sysId` - Schema location

      Returns:
      Object - XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(java.io.InputStream in,
                                 java.net.URL baseurl)
                          throws XSDException

      Build an XMLSchema object
      Parameters:
      `in` - Inputstream of Schema

      `baseurl` - URL used to resolve any relative refs.

      Returns:
      Object - XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(java.io.Reader r,
                                 java.net.URL baseurl)
                          throws XSDException

      Build an XMLSchema object
      Parameters:
      `r` - Reader of Schema

      `baseurl` - URL used to resolve any relative refs.

      Returns:
      Object - XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(java.net.URL schemaurl)
                          throws XSDException

      Build an XMLSchema object
      Parameters:
      `schemaurl` - - URL of Schema

      Returns:
      Object - XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(InputSource source)
                          throws XSDException

      Build an XMLSchema object
      Parameters:
      `source` - - InputSource of Schema

      Returns:
      Object - XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(XMLDocument schemaDoc,
                                 java.net.URL baseurl)
                          throws XSDException

      Build XMLSchema from XML document
      Parameters:
      `schemaDoc` - XMLDocument

      `baseurl` - base URL to be use for any import/include in document

      Returns:
      Object - XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(XMLDocument[] schemaDoc,
                                 java.net.URL baseurl)
                          throws XSDException

      Build XMLSchema from a set of XML documents
      Parameters:
      `schemaDoc` - Array of XMLDocument

      `baseurl` - base URL to be use for any import/include in document

      Returns:
      Object - XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(XMLDocument[] schemaDoc)
                          throws XSDException

      Build XMLSchema from a set of XML documents The system id of each document is used as the based uri
      Parameters:
      `schemaDoc` - Array of XMLDocument

      Returns:
      Object - XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(XMLElement[] schemaDoc,
                                 java.net.URL baseurl)
                          throws XSDException

      Build XMLSchema from a set of XMLElements
      Parameters:
      `schemaDoc` - Array of XMLElement

      `baseurl` - base URL to be use for any import/include in document

      Returns:
      Object - XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(XMLDocument doc,
                                 java.lang.String fragment,
                                 java.lang.String ns,
                                 java.net.URL baseurl)
                          throws XSDException

      Build an XMLSchema object
      Parameters:
      `doc` - XMLdocument contain the schema element

      `fragment` - Fragment ID of the schema element

      `ns` - Schema target namespace used to validate targetNamespace

      `baseurl` - Schema location

      Returns:
      Object XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(java.lang.String ns,
                                 java.lang.String sysid)
                          throws XSDException

      Build an XMLSchema object
      Parameters:
      `ns` - Schema target namespace used to validate targetNamespace

      `sysid` - Schema location

      Returns:
      Object XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

    <!-- -->

    - #### build

          public XMLSchema build(java.lang.String ns,
                                 java.net.URL sysid)
                          throws XSDException

      Build an XMLSchema object
      Parameters:
      `ns` - Schema target namespace used to validate targetNamespace

      `sysid` - URL Schema location

      Returns:
      Object XMLSchema

      Throws:
      [`XSDException`](XSDException.md) - An `XSDException` is thrown if Builder fails to build an XMLSchema object.

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

- **[Prev Class](XSDAttribute.md)**
- **[Next Class](XSDComplexType.md)**

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
