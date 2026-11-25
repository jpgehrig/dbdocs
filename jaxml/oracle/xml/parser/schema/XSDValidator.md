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

- **[Prev Class](XSDTypeConstants.md)**
- **Next Class**

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

## **Class XSDValidator**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLMultiHandler](../v2/XMLMultiHandler.md)**

  - - **oracle.xml.parser.schema.XSDValidator**

<!-- -->

- **All Implemented Interfaces:**
  **[XSDConstantValues](XSDConstantValues.md), [ContentHandler](../../../../org/xml/sax/ContentHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XSDValidator
      extends XMLMultiHandler
      implements XSDConstantValues

  **XSDValidator validates instance XML document against an XMLSchema. When registered an XSDValidator object is inserted as a pipe-line node between XMLParser and XMLDocument events handler (SAXHandler or DOMBuilder). It works with three events: startElement, characters and endElement. If defined, default element and default attribute values are added to the events contents (as XMLSchema additions to infoset) and are propagated up. As far as XSDValidator is concerned the XMLSchema object is a set/group of element declaratioms whith following structure: \[element(name)\] -\> \[shode(min/maxOccurs)\] -\> \[type(group/simpleType)\] XSDValidator is implemented as stack based state machine. Each state represents element type - group or simpleType. XMLSchema object(as a group) is loaded as a first state. Current element(event startElement) is matched against current state group elements. If matched the element type element name and snode info are loaded as new state. In a case of group a vector of counters(int) is allocated in a parallel stack. This vector is used to count element occurances. State status could be: - NEW_STATE: just loaded and not tryed. - ACCEPTED: minOccurs satisfied. Could still accept element occurances. - DONE: maxOccurs satisfied. Doesn't accept element occurances. Text element contents(event characters) is matched against simpleType (method validateValue). End element (event endElement) is matched against last named state. XMLSchema attributes are represented as a group (attrName -\> attrType) forming the contents of special element: \<\_attrTag\> \<attrName\> attrType \</attrName\> ... \</\_attrTag\> SMLParser converts attributes (event startElement) accordingly. (see method startElement) XSDAny objects are used as Namespace frame descriptors (see XMLSchema definition of 'any' element). Fake states are loaded in a case of error or when wildcard('any') contents is skipped.**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface oracle.xml.parser.schema.[XSDConstantValues](XSDConstantValues.md)**

      **[`_abstract`](XSDConstantValues.md)`, `[`_all`](XSDConstantValues.md)`, `[`_annotation`](XSDConstantValues.md)`, `[`_any`](XSDConstantValues.md)`, `[`_anyAttribute`](XSDConstantValues.md)`, `[`_anySimpleType`](XSDConstantValues.md)`, `[`_anyType`](XSDConstantValues.md)`, `[`_appinfo`](XSDConstantValues.md)`, `[`_attrFormDefault`](XSDConstantValues.md)`, `[`_attribute`](XSDConstantValues.md)`, `[`_attributeGroup`](XSDConstantValues.md)`, `[`_attrTag`](XSDConstantValues.md)`, `[`_base`](XSDConstantValues.md)`, `[`_block`](XSDConstantValues.md)`, `[`_blockDefault`](XSDConstantValues.md)`, `[`_choice`](XSDConstantValues.md)`, `[`_complexContent`](XSDConstantValues.md)`, `[`_complexType`](XSDConstantValues.md)`, `[`_content`](XSDConstantValues.md)`, `[`_default`](XSDConstantValues.md)`, `[`_derivedBy`](XSDConstantValues.md)`, `[`_documentation`](XSDConstantValues.md)`, `[`_element`](XSDConstantValues.md)`, `[`_elementOnly`](XSDConstantValues.md)`, `[`_elemFormDefault`](XSDConstantValues.md)`, `[`_empty`](XSDConstantValues.md)`, `[`_enumeration`](XSDConstantValues.md)`, `[`_equivClass`](XSDConstantValues.md)`, `[`_extension`](XSDConstantValues.md)`, `[`_false`](XSDConstantValues.md)`, `[`_field`](XSDConstantValues.md)`, `[`_final`](XSDConstantValues.md)`, `[`_finalDefault`](XSDConstantValues.md)`, `[`_fixed`](XSDConstantValues.md)`, `[`_form`](XSDConstantValues.md)`, `[`_group`](XSDConstantValues.md)`, `[`_id`](XSDConstantValues.md)`, `[`_import`](XSDConstantValues.md)`, `[`_include`](XSDConstantValues.md)`, `[`_itemType`](XSDConstantValues.md)`, `[`_key`](XSDConstantValues.md)`, `[`_keyref`](XSDConstantValues.md)`, `[`_lax`](XSDConstantValues.md)`, `[`_list`](XSDConstantValues.md)`, `[`_maxOccurs`](XSDConstantValues.md)`, `[`_memberTypes`](XSDConstantValues.md)`, `[`_minOccurs`](XSDConstantValues.md)`, `[`_mixed`](XSDConstantValues.md)`, `[`_nall`](XSDConstantValues.md)`, `[`_name`](XSDConstantValues.md)`, `[`_namespace`](XSDConstantValues.md)`, `[`_nil`](XSDConstantValues.md)`, `[`_nillable`](XSDConstantValues.md)`, `[`_nnany`](XSDConstantValues.md)`, `[`_nnlist`](XSDConstantValues.md)`, `[`_nnlocal`](XSDConstantValues.md)`, `[`_nnother`](XSDConstantValues.md)`, `[`_nntargetNS`](XSDConstantValues.md)`, `[`_noNSSchemaLocation`](XSDConstantValues.md)`, `[`_notation`](XSDConstantValues.md)`, `[`_null`](XSDConstantValues.md)`, `[`_nullable`](XSDConstantValues.md)`, `[`_optional`](XSDConstantValues.md)`, `[`_pattern`](XSDConstantValues.md)`, `[`_processContents`](XSDConstantValues.md)`, `[`_prohibited`](XSDConstantValues.md)`, `[`_publicid`](XSDConstantValues.md)`, `[`_qualified`](XSDConstantValues.md)`, `[`_redefine`](XSDConstantValues.md)`, `[`_ref`](XSDConstantValues.md)`, `[`_refer`](XSDConstantValues.md)`, `[`_required`](XSDConstantValues.md)`, `[`_restriction`](XSDConstantValues.md)`, `[`_restrictions`](XSDConstantValues.md)`, `[`_schemaLocation`](XSDConstantValues.md)`, `[`_selector`](XSDConstantValues.md)`, `[`_sequence`](XSDConstantValues.md)`, `[`_simpleContent`](XSDConstantValues.md)`, `[`_simpleType`](XSDConstantValues.md)`, `[`_skip`](XSDConstantValues.md)`, `[`_strict`](XSDConstantValues.md)`, `[`_substitution`](XSDConstantValues.md)`, `[`_substitutionGrp`](XSDConstantValues.md)`, `[`_systemid`](XSDConstantValues.md)`, `[`_targetNS`](XSDConstantValues.md)`, `[`_textOnly`](XSDConstantValues.md)`, `[`_this`](XSDConstantValues.md)`, `[`_true`](XSDConstantValues.md)`, `[`_type`](XSDConstantValues.md)`, `[`_undef`](XSDConstantValues.md)`, `[`_union`](XSDConstantValues.md)`, `[`_unique`](XSDConstantValues.md)`, `[`_unqualified`](XSDConstantValues.md)`, `[`_use`](XSDConstantValues.md)`, `[`_value`](XSDConstantValues.md)`, `[`_version`](XSDConstantValues.md)`, `[`_xmlns`](XSDConstantValues.md)`, `[`ABSENT_NS`](XSDConstantValues.md)`, `[`ACCEPTED`](XSDConstantValues.md)`, `[`ALL`](XSDConstantValues.md)`, `[`ANNOTATION`](XSDConstantValues.md)`, `[`ANY`](XSDConstantValues.md)`, `[`ANY_ATTRIBUTE`](XSDConstantValues.md)`, `[`ANY_NODE`](XSDConstantValues.md)`, `[`ATTRIBUTE`](XSDConstantValues.md)`, `[`ATTRIBUTE_GROUP`](XSDConstantValues.md)`, `[`AUTO_VALIDATION`](XSDConstantValues.md)`, `[`BASE_RESOLVED`](XSDConstantValues.md)`, `[`BASE_UNRESOLVED`](XSDConstantValues.md)`, `[`BASE_URL`](XSDConstantValues.md)`, `[`BUILD_FAIL`](XSDConstantValues.md)`, `[`CHOICE`](XSDConstantValues.md)`, `[`CIRCULAR_SUBST`](XSDConstantValues.md)`, `[`CONFLICIT_FACET`](XSDConstantValues.md)`, `[`constName`](XSDConstantValues.md)`, `[`DATATYPE`](XSDConstantValues.md)`, `[`DEEP_VALIDATION`](XSDConstantValues.md)`, `[`derivationBlock`](XSDConstantValues.md)`, `[`DONE`](XSDConstantValues.md)`, `[`DUPLICATE_DEF`](XSDConstantValues.md)`, `[`duplicateId`](XSDConstantValues.md)`, `[`ELEMENT`](XSDConstantValues.md)`, `[`ELEMENT_CHILD`](XSDConstantValues.md)`, `[`ELEMENT_ONLY`](XSDConstantValues.md)`, `[`elemNotNullable`](XSDConstantValues.md)`, `[`EMPTY`](XSDConstantValues.md)`, `[`ENTITY_RESOLVER`](XSDConstantValues.md)`, `[`EQUIV_RESOLVED`](XSDConstantValues.md)`, `[`EQUIV_UNRESOLVED`](XSDConstantValues.md)`, `[`ERROR`](XSDConstantValues.md)`, `[`EXTENTION`](XSDConstantValues.md)`, `[`FACET_CHILD`](XSDConstantValues.md)`, `[`FAKE_ATTR`](XSDConstantValues.md)`, `[`FAKE_NODE`](XSDConstantValues.md)`, `[`FIXED_SCHEMA`](XSDConstantValues.md)`, `[`GROUP`](XSDConstantValues.md)`, `[`IABSTRACT`](XSDConstantValues.md)`, `[`IBLOCKEXT`](XSDConstantValues.md)`, `[`IBLOCKRST`](XSDConstantValues.md)`, `[`IBLOCKSUB`](XSDConstantValues.md)`, `[`IDENTITY_ERROR`](XSDConstantValues.md)`, `[`IDENTITY_KEY`](XSDConstantValues.md)`, `[`IDENTITY_KEYREF`](XSDConstantValues.md)`, `[`IDENTITY_UNIQUE`](XSDConstantValues.md)`, `[`IFINALEXT`](XSDConstantValues.md)`, `[`IFINALLIST`](XSDConstantValues.md)`, `[`IFINALRST`](XSDConstantValues.md)`, `[`IFINALUNION`](XSDConstantValues.md)`, `[`IMPORT`](XSDConstantValues.md)`, `[`INCLUDE`](XSDConstantValues.md)`, `[`INCORRECT_ATTR`](XSDConstantValues.md)`, `[`INCORRECT_ELEM`](XSDConstantValues.md)`, `[`INFINITY`](XSDConstantValues.md)`, `[`INTERNAL_ERROR`](XSDConstantValues.md)`, `[`INVALID_DATE`](XSDConstantValues.md)`, `[`INVALID_DATETIME`](XSDConstantValues.md)`, `[`INVALID_DERIVATION`](XSDConstantValues.md)`, `[`INVALID_FACET`](XSDConstantValues.md)`, `[`INVALID_FACET_VALUE`](XSDConstantValues.md)`, `[`INVALID_NOTATION`](XSDConstantValues.md)`, `[`INVALID_REGEX`](XSDConstantValues.md)`, `[`INVALID_SCHEMA_NS`](XSDConstantValues.md)`, `[`INVALID_TIME`](XSDConstantValues.md)`, `[`INVALID_TYPE_VALUE`](XSDConstantValues.md)`, `[`invalidAttr`](XSDConstantValues.md)`, `[`invalidAttrVal`](XSDConstantValues.md)`, `[`invalidChars`](XSDConstantValues.md)`, `[`invalidElem`](XSDConstantValues.md)`, `[`invalidFixedChars`](XSDConstantValues.md)`, `[`invalidNS`](XSDConstantValues.md)`, `[`invalidPrefix`](XSDConstantValues.md)`, `[`invalidProperty`](XSDConstantValues.md)`, `[`invalidRef`](XSDConstantValues.md)`, `[`invalidSubstitution`](XSDConstantValues.md)`, `[`invalidTargetNS`](XSDConstantValues.md)`, `[`LAX_VALIDATION`](XSDConstantValues.md)`, `[`MISSING_NS`](XSDConstantValues.md)`, `[`missingAttr`](XSDConstantValues.md)`, `[`MIXED`](XSDConstantValues.md)`, `[`NEW_STATE`](XSDConstantValues.md)`, `[`NO_CHILD`](XSDConstantValues.md)`, `[`noDefinition`](XSDConstantValues.md)`, `[`NOT_DONE`](XSDConstantValues.md)`, `[`NOTATION`](XSDConstantValues.md)`, `[`notComplete`](XSDConstantValues.md)`, `[`notSubstitutable`](XSDConstantValues.md)`, `[`notSubTypeOf`](XSDConstantValues.md)`, `[`NS_CONFLICT`](XSDConstantValues.md)`, `[`NS_DIF_SPECIFIED`](XSDConstantValues.md)`, `[`NS_NOT_ALLOWED`](XSDConstantValues.md)`, `[`NS_NOT_EXPECTED`](XSDConstantValues.md)`, `[`NS_NOT_SAME`](XSDConstantValues.md)`, `[`NS_RESOLVER`](XSDConstantValues.md)`, `[`REDEFINE`](XSDConstantValues.md)`, `[`REF_RESOLVED`](XSDConstantValues.md)`, `[`REF_UNRESOLVED`](XSDConstantValues.md)`, `[`RESTRICTION`](XSDConstantValues.md)`, `[`ROOT_ELEMENT`](XSDConstantValues.md)`, `[`ROOT_NODE`](XSDConstantValues.md)`, `[`ROOT_TYPE`](XSDConstantValues.md)`, `[`SCHEMA_NS`](XSDConstantValues.md)`, `[`SCHEMA_RESOLVER`](XSDConstantValues.md)`, `[`SEQ`](XSDConstantValues.md)`, `[`STRICT_VALIDATION`](XSDConstantValues.md)`, `[`TEXT_ONLY`](XSDConstantValues.md)`, `[`TOP_LEVEL`](XSDConstantValues.md)`, `[`TYPE`](XSDConstantValues.md)`, `[`TYPE_RESOLVED`](XSDConstantValues.md)`, `[`TYPE_UNRESOLVED`](XSDConstantValues.md)`, `[`UNDEF`](XSDConstantValues.md)`, `[`unexpectedAttr`](XSDConstantValues.md)`, `[`unexpectedElem`](XSDConstantValues.md)`, `[`VALIDATION_MODE`](XSDConstantValues.md)`, `[`VIOLATE_FACET`](XSDConstantValues.md)`, `[`XSDRECNS`](XSDConstantValues.md)`, `[`XSDRECTYPENS`](XSDConstantValues.md)`, `[`XSIRECNS`](XSDConstantValues.md)`, `[`XSITYPE_ABSENT`](XSDConstantValues.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                     |
    |-------------------------------------------------|
    | `XSDValidator``()`<br>XSDValidator constructor. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type             | Method and Description                                                                                                                                                                                                    |
    |-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                        | `characters``(char[] ch, int start, int length)`<br>Propagate notification of character data inside an element.                                                                                                           |
    | `boolean`                     | `elementNilled``()`<br>Check if current element's content is nilled                                                                                                                                                       |
    | `void`                        | `endElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName)`<br>Receive notification of the end of an element.                                                                       |
    | `java.lang.String`            | `getCurrentMode``()`<br>Get the current validation mode                                                                                                                                                                   |
    | [`XSDElement`](XSDElement.md) | `getElementDeclaration``()`<br>Get the current element declaration                                                                                                                                                        |
    | [`XSDElement`](XSDElement.md) | `getParentDeclaration``()`<br>Get the parent element declaration                                                                                                                                                          |
    | [`XSDNode`](XSDNode.md)       | `getTypeDefinition``()`<br>Get the current XSD type                                                                                                                                                                       |
    | `java.lang.Object`            | `getXMLProperty``(java.lang.String name)`                                                                                                                                                                                 |
    | `void`                        | `reset``()`<br>Reset the validator, prepare for next validation                                                                                                                                                           |
    | `void`                        | `setDocumentLocator``(`[`Locator`](../../../../org/xml/sax/Locator.md)` locator)`<br>Propagates Locator object for document events.                                                                                       |
    | `void`                        | `setError``(`[`XMLError`](../v2/XMLError.md)` he)`<br>Sets an XMLError object as current err.                                                                                                                             |
    | `java.lang.Object`            | `setXMLProperty``(java.lang.String name, java.lang.Object value)`<br>Set a property.                                                                                                                                      |
    | `void`                        | `setXMLSchema``(`[`XMLSchema`](XMLSchema.md)` s)`<br>Deprecated.                                                                                                                                                          |
    | `void`                        | `startDocument``()`<br>Receive notification of the beginning of the document.                                                                                                                                             |
    | `void`                        | `startElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName, `[`Attributes`](../../../../org/xml/sax/Attributes.md)` atts)`<br>Receive notification of the beginning of an element. |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLMultiHandler](../v2/XMLMultiHandler.md)

      [`addContentHandler`](../v2/XMLMultiHandler.md)`, `[`endDocument`](../v2/XMLMultiHandler.md)`, `[`endPrefixMapping`](../v2/XMLMultiHandler.md)`, `[`getContentHandlers`](../v2/XMLMultiHandler.md)`, `[`getNumContentHandlers`](../v2/XMLMultiHandler.md)`, `[`ignorableWhitespace`](../v2/XMLMultiHandler.md)`, `[`processingInstruction`](../v2/XMLMultiHandler.md)`, `[`removeContentHandler`](../v2/XMLMultiHandler.md)`, `[`skippedEntity`](../v2/XMLMultiHandler.md)`, `[`startPrefixMapping`](../v2/XMLMultiHandler.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSDValidator

          public XSDValidator()
                       throws XSDException

      XSDValidator constructor.
      Throws:
      [`XSDException`](XSDException.md)

  <!-- -->

  - ### Method Detail

    - #### reset

          public void reset()

      Reset the validator, prepare for next validation

    <!-- -->

    - #### setError

          public void setError(XMLError he)
                        throws SAXException

      Sets an XMLError object as current err.
      Parameters:
      `he` - XMLError object

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - A `SAXException` could be thrown.

    <!-- -->

    - #### setXMLSchema

          public void setXMLSchema(XMLSchema s)
                            throws SAXException

      Deprecated. 
      Sets an XMLSchema object as current schema.
      Parameters:
      `s` - XMLSchema object

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - A `SAXException` could be thrown.

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

    <!-- -->

    - #### getCurrentMode

          public java.lang.String getCurrentMode()

      Get the current validation mode
      Returns:
      a `_strict`, `_lax`, `_skip`, or `_error`

    <!-- -->

    - #### getTypeDefinition

          public XSDNode getTypeDefinition()

      Get the current XSD type
      Returns:
      `XSDComplexType` node or `XSDSimpleType<code/> node`

    <!-- -->

    - #### `getElementDeclaration`

          public XSDElement getElementDeclaration()

      `Get the current element declaration`
      `Returns:`
      `XSDElement`` node`

    <!-- -->

    - #### getParentDeclaration

          public XSDElement getParentDeclaration()

      Get the parent element declaration
      Returns:
      `XSDElement` node

    <!-- -->

    - #### elementNilled

          public boolean elementNilled()

      Check if current element's content is nilled
      Returns:
      `boolean` true if current element is nilled, false otherwise

    <!-- -->

    - #### startDocument

          public void startDocument()
                             throws SAXException

      Receive notification of the beginning of the document.
      Specified by:
      [`startDocument`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`startDocument`](../v2/XMLMultiHandler.md) in class [`XMLMultiHandler`](../v2/XMLMultiHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.startDocument()`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### startElement

          public void startElement(java.lang.String namespaceURI,
                                   java.lang.String localName,
                                   java.lang.String qName,
                                   Attributes atts)
                            throws SAXException

      Receive notification of the beginning of an element.
      Specified by:
      [`startElement`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`startElement`](../v2/XMLMultiHandler.md) in class [`XMLMultiHandler`](../v2/XMLMultiHandler.md)

      Parameters:
      `namespaceURI` - The Namespace URI, or the empty string if the element has no Namespace URI or if Namespace processing is not being performed.

      `localName` - The local name(without prefix), or the empty string if Namespace processing is not being performed.

      `qName` - The qualified name (with prefix), or the empty string if qualified names are not available.

      `atts` - The attributes attached to the element. If there are no attributes, it shall be an empty Attributes object.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `endElement(java.lang.String, java.lang.String, java.lang.String)`, [`Attributes`](../../../../org/xml/sax/Attributes.md)

    <!-- -->

    - #### endElement

          public void endElement(java.lang.String namespaceURI,
                                 java.lang.String localName,
                                 java.lang.String qName)
                          throws SAXException

      Receive notification of the end of an element.
      Specified by:
      [`endElement`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`endElement`](../v2/XMLMultiHandler.md) in class [`XMLMultiHandler`](../v2/XMLMultiHandler.md)

      Parameters:
      `namespaceURI` - The Namespace URI, or the empty string if the element has no Namespace URI or if Namespace processing is not being performed.

      `localName` - The local name (without prefix), or the empty string if Namespace processing is not being performed.

      `qName` - The qualified XML 1.0 name (with prefix), or the empty string if qualified names are not available.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### characters

          public void characters(char[] ch,
                                 int start,
                                 int length)
                          throws SAXException

      Propagate notification of character data inside an element.
      Specified by:
      [`characters`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`characters`](../v2/XMLMultiHandler.md) in class [`XMLMultiHandler`](../v2/XMLMultiHandler.md)

      Parameters:
      `ch` - The characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.characters(char[], int, int)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### setDocumentLocator

          public void setDocumentLocator(Locator locator)

      Propagates Locator object for document events.
      Specified by:
      [`setDocumentLocator`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`setDocumentLocator`](../v2/XMLMultiHandler.md) in class [`XMLMultiHandler`](../v2/XMLMultiHandler.md)

      Parameters:
      `locator` - A locator for all SAX document events.

      See Also:
      [`DocumentHandler.setDocumentLocator(org.xml.sax.Locator)`](../../../../org/xml/sax/DocumentHandler.md), [`Locator`](../../../../org/xml/sax/Locator.md)

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

- **[Prev Class](XSDTypeConstants.md)**
- **Next Class**

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
