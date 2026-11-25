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

- **[Prev Class](PrintDriver.md)**
- **[Next Class](SAXParser.md)**

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

## **Class SAXAttrList**

- **java.lang.Object**

- - **oracle.xml.parser.v2.SAXAttrList**

<!-- -->

- **All Implemented Interfaces:**
  **[AttributeList](../../../../org/xml/sax/AttributeList.md)**

  ------------------------------------------------------------------------

  **
  **

      public class SAXAttrList
      extends java.lang.Object
      implements AttributeList

  **This class implements the SAX `AttributeList` interface and also provides Namespace support. Applications that require Namespace support can explicitly cast any attribute list returned by an Oracle parser class to `SAXAttrList` and use the methods described here. It also implements Attributes (SAX 2.0) interface**
  **This interface allows access to a list of attributes in three different ways:**

  1.  **by attribute index;**
  2.  **by Namespace-qualified name; or**
  3.  **by qualified (prefixed) name.**

  **The list will not contain attributes that were declared \#IMPLIED but not specified in the start tag. It will also not contain attributes used as Namespace declarations (xmlns\*) unless the `http://xml.org/sax/features/namespace-prefixes` feature is set to `true` (it is `false` by default).**

  **If the namespace-prefixes feature (see above) is `false`, access by qualified name may not be available; if the `http://xml.org/sax/features/namespaces` feature is `false`, access by Namespace-qualified names may not be available.**

  **This interface replaces the now-deprecated SAX1 interface, which does not contain Namespace support. In addition to Namespace support, it adds the `getIndex` methods (below).**

  **The order of attributes in the list is unspecified, and will vary from implementation to implementation.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `SAXAttrList``(int elems)`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                 |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `addAttr``(java.lang.String pfx, java.lang.String lname, java.lang.String tag, java.lang.String value, boolean spec, int type)`<br>Add an attribute to the parent element node.                        |
    | `void`             | `addAttr``(java.lang.String pfx, java.lang.String lname, java.lang.String tag, java.lang.String value, boolean spec, int type, java.lang.String nmsp)`<br>Add an attribute to the parent element node. |
    | `java.lang.String` | `getExpandedName``(int i)`<br>Get the expanded name for an attribute in the list (by position)                                                                                                         |
    | `int`              | `getIndex``(java.lang.String qName)`<br>Look up the index of an attribute by XML 1.0 qualified name.                                                                                                   |
    | `int`              | `getIndex``(java.lang.String uri, java.lang.String localPart)`<br>Look up the index of an attribute by Namespace name.                                                                                 |
    | `int`              | `getLength``()`<br>Return the number of attributes in this list.                                                                                                                                       |
    | `java.lang.String` | `getLocalName``(int index)`<br>Look up an attribute's local name by index.                                                                                                                             |
    | `java.lang.String` | `getName``(int i)`<br>Deprecated. <br>as of SAX2 - Replaced by getLocalName(int i)                                                                                                                     |
    | `java.lang.String` | `getNamespace``(int i)`<br>Deprecated. <br>as of SAX2 - Replaced by getURI(int i)                                                                                                                      |
    | `java.lang.String` | `getPrefix``(int i)`<br>Get the namespace prefix for an attribute in the list (by position)                                                                                                            |
    | `java.lang.String` | `getQName``(int index)`<br>Look up an attribute's XML 1.0 qualified name by index.                                                                                                                     |
    | `java.lang.String` | `getQualifiedName``(int i)`<br>Deprecated. <br>as of SAX2 - Replaced by getQName(int i)                                                                                                                |
    | `java.lang.String` | `getType``(int index)`<br>Look up an attribute's type by index.                                                                                                                                        |
    | `java.lang.String` | `getType``(java.lang.String qName)`<br>Look up an attribute's type by XML 1.0 qualified name.                                                                                                          |
    | `java.lang.String` | `getType``(java.lang.String uri, java.lang.String localName)`<br>Look up an attribute's type by Namespace name.                                                                                        |
    | `java.lang.String` | `getURI``(int index)`<br>Look up an attribute's Namespace URI by index.                                                                                                                                |
    | `java.lang.String` | `getValue``(int index)`<br>Look up an attribute's value by index.                                                                                                                                      |
    | `java.lang.String` | `getValue``(java.lang.String qName)`<br>Look up an attribute's value by XML 1.0 qualified name.                                                                                                        |
    | `java.lang.String` | `getValue``(java.lang.String uri, java.lang.String localName)`<br>Look up an attribute's value by Namespace name.                                                                                      |
    | `boolean`          | `isSpecified``(int index)`<br>Look up if an attribute is specified by index.                                                                                                                           |
    | `void`             | `reset``()`<br>Resets the SAXAttrList                                                                                                                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SAXAttrList

          public SAXAttrList(int elems)

  <!-- -->

  - ### Method Detail

    - #### reset

          public void reset()

      Resets the SAXAttrList

    <!-- -->

    - #### addAttr

          public void addAttr(java.lang.String pfx,
                              java.lang.String lname,
                              java.lang.String tag,
                              java.lang.String value,
                              boolean spec,
                              int type)

      Add an attribute to the parent element node.
      Parameters:
      `pfx` - the prefix of the attribute

      `lname` - the local name of the attribute

      `tag` - the qname of the attribute

      `value` - the attribute value

      `spec` - the specified flag

      `type` - the attribute type

    <!-- -->

    - #### addAttr

          public void addAttr(java.lang.String pfx,
                              java.lang.String lname,
                              java.lang.String tag,
                              java.lang.String value,
                              boolean spec,
                              int type,
                              java.lang.String nmsp)

      Add an attribute to the parent element node.
      Parameters:
      `pfx` - the prefix of the attribute

      `lname` - the local name of the attribute

      `tag` - the qname of the attribute

      `value` - the attribute value

      `spec` - the specified flag

      `type` - the attribute type \#param nmsp the namespace of the attribute

    <!-- -->

    - #### getLength

          public int getLength()

      Return the number of attributes in this list.
      The SAX parser may provide attributes in any arbitrary order, regardless of the order in which they were declared or specified. The number of attributes may be zero.

      Specified by:
      [`getLength`](../../../../org/xml/sax/AttributeList.md) in interface [`AttributeList`](../../../../org/xml/sax/AttributeList.md)

      Returns:
      The number of attributes in the list.

    <!-- -->

    - #### getName

          public java.lang.String getName(int i)

      Deprecated. as of SAX2 - Replaced by getLocalName(int i)
      Return the name of an attribute in this list (by position).
      The names must be unique: the SAX parser shall not include the same attribute twice. Attributes without values (those declared \#IMPLIED without a value specified in the start tag) will be omitted from the list.

      If the attribute name has a namespace prefix, the prefix will still be attached.

      Specified by:
      [`getName`](../../../../org/xml/sax/AttributeList.md) in interface [`AttributeList`](../../../../org/xml/sax/AttributeList.md)

      Parameters:
      `i` - The index of the attribute in the list (starting at 0).

      Returns:
      The name of the indexed attribute, or null if the index is out of range.

      See Also:
      `getLength()`

    <!-- -->

    - #### getPrefix

          public java.lang.String getPrefix(int i)

      Get the namespace prefix for an attribute in the list (by position)
      Parameters:
      `i` - The index of the attribute in the list.

      Returns:
      The namespace prefix for the attribute

    <!-- -->

    - #### getQualifiedName

          public java.lang.String getQualifiedName(int i)

      Deprecated. as of SAX2 - Replaced by getQName(int i)
      Get the qualified name for an attribute in the list (by position)
      Parameters:
      `i` - The index of the attribute in the list.

      Returns:
      The qualified name for the attribute

    <!-- -->

    - #### getNamespace

          public java.lang.String getNamespace(int i)

      Deprecated. as of SAX2 - Replaced by getURI(int i)
      Get the resolved namespace for an attribute in the list (by position)
      Parameters:
      `i` - The index of the attribute in the list.

      Returns:
      The resolved namespace for the attribute

    <!-- -->

    - #### getExpandedName

          public java.lang.String getExpandedName(int i)

      Get the expanded name for an attribute in the list (by position)
      Parameters:
      `i` - The index of the attribute in the list.

      Returns:
      The expanded name for the attribute

    <!-- -->

    - #### getURI

          public java.lang.String getURI(int index)

      Look up an attribute's Namespace URI by index.
      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      The Namespace URI, or the empty string if none is available, or null if the index is out of range.

      Since:
      SAX2

      See Also:
      `getLength()`

    <!-- -->

    - #### getLocalName

          public java.lang.String getLocalName(int index)

      Look up an attribute's local name by index.
      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      The local name, or the empty string if Namespace processing is not being performed, or null if the index is out of range.

      Since:
      SAX2

      See Also:
      `getLength()`

    <!-- -->

    - #### getQName

          public java.lang.String getQName(int index)

      Look up an attribute's XML 1.0 qualified name by index.
      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      The XML 1.0 qualified name, or the empty string if none is available, or null if the index is out of range.

      Since:
      SAX2

      See Also:
      `getLength()`

    <!-- -->

    - #### getType

          public java.lang.String getType(int index)

      Look up an attribute's type by index.
      The attribute type is one of the strings "CDATA", "ID", "IDREF", "IDREFS", "NMTOKEN", "NMTOKENS", "ENTITY", "ENTITIES", or "NOTATION" (always in upper case).

      If the parser has not read a declaration for the attribute, or if the parser does not report attribute types, then it must return the value "CDATA" as stated in the XML 1.0 Recommentation (clause 3.3.3, "Attribute-Value Normalization").

      For an enumerated attribute that is not a notation, the parser will report the type as "NMTOKEN".

      Specified by:
      [`getType`](../../../../org/xml/sax/AttributeList.md) in interface [`AttributeList`](../../../../org/xml/sax/AttributeList.md)

      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      The attribute's type as a string, or null if the index is out of range.

      See Also:
      `getLength()`

    <!-- -->

    - #### isSpecified

          public boolean isSpecified(int index)

      Look up if an attribute is specified by index.
      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      True is the attribute is specified, else false Returns false if index is out of range.

      See Also:
      `getLength()`

    <!-- -->

    - #### getValue

          public java.lang.String getValue(int index)

      Look up an attribute's value by index.
      If the attribute value is a list of tokens (IDREFS, ENTITIES, or NMTOKENS), the tokens will be concatenated into a single string with each token separated by a single space.

      Specified by:
      [`getValue`](../../../../org/xml/sax/AttributeList.md) in interface [`AttributeList`](../../../../org/xml/sax/AttributeList.md)

      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      The attribute's value as a string, or null if the index is out of range.

      See Also:
      `getLength()`

    <!-- -->

    - #### getIndex

          public int getIndex(java.lang.String uri,
                              java.lang.String localPart)

      Look up the index of an attribute by Namespace name.
      Parameters:
      `uri` - The Namespace URI, or the empty string if the name has no Namespace URI.

      `localPart` - The attribute's local name.

      Returns:
      The index of the attribute, or -1 if it does not appear in the list.

      Since:
      SAX2

    <!-- -->

    - #### getIndex

          public int getIndex(java.lang.String qName)

      Look up the index of an attribute by XML 1.0 qualified name.
      Parameters:
      `qName` - The qualified (prefixed) name.

      Returns:
      The index of the attribute, or -1 if it does not appear in the list.

    <!-- -->

    - #### getType

          public java.lang.String getType(java.lang.String uri,
                                          java.lang.String localName)

      Look up an attribute's type by Namespace name.
      See `getType(int)` for a description of the possible types.

      Parameters:
      `uri` - The Namespace URI, or the empty String if the name has no Namespace URI.

      `localName` - The local name of the attribute.

      Returns:
      The attribute type as a string, or null if the attribute is not in the list or if Namespace processing is not being performed.

      Since:
      SAX2

    <!-- -->

    - #### getType

          public java.lang.String getType(java.lang.String qName)

      Look up an attribute's type by XML 1.0 qualified name.
      See `getType(int)` for a description of the possible types.

      Specified by:
      [`getType`](../../../../org/xml/sax/AttributeList.md) in interface [`AttributeList`](../../../../org/xml/sax/AttributeList.md)

      Parameters:
      `qName` - The XML 1.0 qualified name.

      Returns:
      The attribute type as a string, or null if the attribute is not in the list or if qualified names are not available.

      See Also:
      [`AttributeList.getType(int)`](../../../../org/xml/sax/AttributeList.md)

    <!-- -->

    - #### getValue

          public java.lang.String getValue(java.lang.String uri,
                                           java.lang.String localName)

      Look up an attribute's value by Namespace name.
      See `getValue(int)` for a description of the possible values.

      Parameters:
      `uri` - The Namespace URI, or the empty String if the name has no Namespace URI.

      `localName` - The local name of the attribute.

      Returns:
      The attribute value as a string, or null if the attribute is not in the list.

      Since:
      SAX2

    <!-- -->

    - #### getValue

          public java.lang.String getValue(java.lang.String qName)

      Look up an attribute's value by XML 1.0 qualified name.
      See `getValue(int)` for a description of the possible values.

      Specified by:
      [`getValue`](../../../../org/xml/sax/AttributeList.md) in interface [`AttributeList`](../../../../org/xml/sax/AttributeList.md)

      Parameters:
      `qName` - The XML 1.0 qualified name.

      Returns:
      The attribute value as a string, or null if the attribute is not in the list or if qualified names are not available.

      See Also:
      [`AttributeList.getValue(int)`](../../../../org/xml/sax/AttributeList.md)

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

- **[Prev Class](PrintDriver.md)**
- **[Next Class](SAXParser.md)**

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
