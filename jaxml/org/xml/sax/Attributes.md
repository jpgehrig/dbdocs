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

- **[Prev Class](AttributeList.md)**
- **[Next Class](ContentHandler.md)**

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

**org.xml.sax**

## **Interface Attributes**

- **All Known Implementing Classes:**
  **[AttributesImpl](helpers/AttributesImpl.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Attributes

  **Interface for a list of XML attributes.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This interface allows access to a list of attributes in three different ways:**

  1.  **by attribute index;**
  2.  **by Namespace-qualified name; or**
  3.  **by qualified (prefixed) name.**

  **The list will not contain attributes that were declared \#IMPLIED but not specified in the start tag. It will also not contain attributes used as Namespace declarations (xmlns\*) unless the `http://xml.org/sax/features/namespace-prefixes` feature is set to `true` (it is `false` by default).**

  **If the namespace-prefixes feature (see above) is `false`, access by qualified name may not be available; if the `http://xml.org/sax/features/namespaces` feature is `false`, access by Namespace-qualified names may not be available.**

  **This interface replaces the now-deprecated SAX1 [`AttributeList`](AttributeList.md) interface, which does not contain Namespace support. In addition to Namespace support, it adds the `getIndex` methods (below).**

  **The order of attributes in the list is unspecified, and will vary from implementation to implementation.**

  **Since:**
  **SAX 2.0**

  **See Also:**
  **[`AttributeListImpl`](helpers/AttributeListImpl.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                 |
    |--------------------|------------------------------------------------------------------------------------------------------------------------|
    | `int`              | `getIndex``(java.lang.String qName)`<br>Look up the index of an attribute by XML 1.0 qualified name.                   |
    | `int`              | `getIndex``(java.lang.String uri, java.lang.String localName)`<br>Look up the index of an attribute by Namespace name. |
    | `int`              | `getLength``()`<br>Return the number of attributes in the list.                                                        |
    | `java.lang.String` | `getLocalName``(int index)`<br>Look up an attribute's local name by index.                                             |
    | `java.lang.String` | `getQName``(int index)`<br>Look up an attribute's XML 1.0 qualified name by index.                                     |
    | `java.lang.String` | `getType``(int index)`<br>Look up an attribute's type by index.                                                        |
    | `java.lang.String` | `getType``(java.lang.String qName)`<br>Look up an attribute's type by XML 1.0 qualified name.                          |
    | `java.lang.String` | `getType``(java.lang.String uri, java.lang.String localName)`<br>Look up an attribute's type by Namespace name.        |
    | `java.lang.String` | `getURI``(int index)`<br>Look up an attribute's Namespace URI by index.                                                |
    | `java.lang.String` | `getValue``(int index)`<br>Look up an attribute's value by index.                                                      |
    | `java.lang.String` | `getValue``(java.lang.String qName)`<br>Look up an attribute's value by XML 1.0 qualified name.                        |
    | `java.lang.String` | `getValue``(java.lang.String uri, java.lang.String localName)`<br>Look up an attribute's value by Namespace name.      |

<!-- -->

- - ### Method Detail

    - #### getLength

          int getLength()

      Return the number of attributes in the list.
      Once you know the number of attributes, you can iterate through the list.

      Returns:
      The number of attributes in the list.

      See Also:
      `getURI(int)`, `getLocalName(int)`, `getQName(int)`, `getType(int)`, `getValue(int)`

    <!-- -->

    - #### getURI

          java.lang.String getURI(int index)

      Look up an attribute's Namespace URI by index.
      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      The Namespace URI, or the empty string if none is available, or null if the index is out of range.

      See Also:
      `getLength()`

    <!-- -->

    - #### getLocalName

          java.lang.String getLocalName(int index)

      Look up an attribute's local name by index.
      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      The local name, or the empty string if Namespace processing is not being performed, or null if the index is out of range.

      See Also:
      `getLength()`

    <!-- -->

    - #### getQName

          java.lang.String getQName(int index)

      Look up an attribute's XML 1.0 qualified name by index.
      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      The XML 1.0 qualified name, or the empty string if none is available, or null if the index is out of range.

      See Also:
      `getLength()`

    <!-- -->

    - #### getType

          java.lang.String getType(int index)

      Look up an attribute's type by index.
      The attribute type is one of the strings "CDATA", "ID", "IDREF", "IDREFS", "NMTOKEN", "NMTOKENS", "ENTITY", "ENTITIES", or "NOTATION" (always in upper case).

      If the parser has not read a declaration for the attribute, or if the parser does not report attribute types, then it must return the value "CDATA" as stated in the XML 1.0 Recommentation (clause 3.3.3, "Attribute-Value Normalization").

      For an enumerated attribute that is not a notation, the parser will report the type as "NMTOKEN".

      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      The attribute's type as a string, or null if the index is out of range.

      See Also:
      `getLength()`

    <!-- -->

    - #### getValue

          java.lang.String getValue(int index)

      Look up an attribute's value by index.
      If the attribute value is a list of tokens (IDREFS, ENTITIES, or NMTOKENS), the tokens will be concatenated into a single string with each token separated by a single space.

      Parameters:
      `index` - The attribute index (zero-based).

      Returns:
      The attribute's value as a string, or null if the index is out of range.

      See Also:
      `getLength()`

    <!-- -->

    - #### getIndex

          int getIndex(java.lang.String uri,
                       java.lang.String localName)

      Look up the index of an attribute by Namespace name.
      Parameters:
      `uri` - The Namespace URI, or the empty string if the name has no Namespace URI.

      `localName` - The attribute's local name.

      Returns:
      The index of the attribute, or -1 if it does not appear in the list.

    <!-- -->

    - #### getIndex

          int getIndex(java.lang.String qName)

      Look up the index of an attribute by XML 1.0 qualified name.
      Parameters:
      `qName` - The qualified (prefixed) name.

      Returns:
      The index of the attribute, or -1 if it does not appear in the list.

    <!-- -->

    - #### getType

          java.lang.String getType(java.lang.String uri,
                                   java.lang.String localName)

      Look up an attribute's type by Namespace name.
      See `getType(int)` for a description of the possible types.

      Parameters:
      `uri` - The Namespace URI, or the empty String if the name has no Namespace URI.

      `localName` - The local name of the attribute.

      Returns:
      The attribute type as a string, or null if the attribute is not in the list or if Namespace processing is not being performed.

    <!-- -->

    - #### getType

          java.lang.String getType(java.lang.String qName)

      Look up an attribute's type by XML 1.0 qualified name.
      See `getType(int)` for a description of the possible types.

      Parameters:
      `qName` - The XML 1.0 qualified name.

      Returns:
      The attribute type as a string, or null if the attribute is not in the list or if qualified names are not available.

    <!-- -->

    - #### getValue

          java.lang.String getValue(java.lang.String uri,
                                    java.lang.String localName)

      Look up an attribute's value by Namespace name.
      See `getValue(int)` for a description of the possible values.

      Parameters:
      `uri` - The Namespace URI, or the empty String if the name has no Namespace URI.

      `localName` - The local name of the attribute.

      Returns:
      The attribute value as a string, or null if the attribute is not in the list.

    <!-- -->

    - #### getValue

          java.lang.String getValue(java.lang.String qName)

      Look up an attribute's value by XML 1.0 qualified name.
      See `getValue(int)` for a description of the possible values.

      Parameters:
      `qName` - The XML 1.0 qualified name.

      Returns:
      The attribute value as a string, or null if the attribute is not in the list or if qualified names are not available.

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

- **[Prev Class](AttributeList.md)**
- **[Next Class](ContentHandler.md)**

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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
