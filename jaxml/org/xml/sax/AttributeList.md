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

- **Prev Class**
- **[Next Class](Attributes.md)**

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

## **Interface AttributeList**

- **All Known Implementing Classes:**
  **[AttributeListImpl](helpers/AttributeListImpl.md), [SAXAttrList](../../../oracle/xml/parser/v2/SAXAttrList.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **This interface has been replaced by the SAX2 [`Attributes`](Attributes.md) interface, which includes Namespace support.**
  **
  **

      public interface AttributeList

  **Interface for an element's attribute specifications.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This is the original SAX1 interface for reporting an element's attributes. Unlike the new [`Attributes`](Attributes.md) interface, it does not support Namespace-related information.**

  **When an attribute list is supplied as part of a [`startElement`](DocumentHandler.md) event, the list will return valid results only during the scope of the event; once the event handler returns control to the parser, the attribute list is invalid. To save a persistent copy of the attribute list, use the SAX1 [`AttributeListImpl`](helpers/AttributeListImpl.md) helper class.**

  **An attribute list includes only attributes that have been specified or defaulted: \#IMPLIED attributes will not be included.**

  **There are two ways for the SAX application to obtain information from the AttributeList. First, it can iterate through the entire list:**

       public void startElement (String name, AttributeList atts) {
         for (int i = 0; i < atts.getLength(); i++) {
           String name = atts.getName(i);
           String type = atts.getType(i);
           String value = atts.getValue(i);
           [...]
         }
       }


  **(Note that the result of getLength() will be zero if there are no attributes.)**

  **As an alternative, the application can request the value or type of specific attributes:**

       public void startElement (String name, AttributeList atts) {
         String identifier = atts.getValue("id");
         String label = atts.getValue("label");
         [...]
       }


  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`startElement`](DocumentHandler.md), [`AttributeListImpl`](helpers/AttributeListImpl.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type  | Method and Description                                                                                         |
    |--------------------|----------------------------------------------------------------------------------------------------------------|
    | `int`              | `getLength``()`<br>Deprecated. <br>Return the number of attributes in this list.                               |
    | `java.lang.String` | `getName``(int i)`<br>Deprecated. <br>Return the name of an attribute in this list (by position).              |
    | `java.lang.String` | `getType``(int i)`<br>Deprecated. <br>Return the type of an attribute in the list (by position).               |
    | `java.lang.String` | `getType``(java.lang.String name)`<br>Deprecated. <br>Return the type of an attribute in the list (by name).   |
    | `java.lang.String` | `getValue``(int i)`<br>Deprecated. <br>Return the value of an attribute in the list (by position).             |
    | `java.lang.String` | `getValue``(java.lang.String name)`<br>Deprecated. <br>Return the value of an attribute in the list (by name). |

<!-- -->

- - ### Method Detail

    - #### getLength

          int getLength()

      Deprecated. 
      Return the number of attributes in this list.
      The SAX parser may provide attributes in any arbitrary order, regardless of the order in which they were declared or specified. The number of attributes may be zero.

      Returns:
      The number of attributes in the list.

    <!-- -->

    - #### getName

          java.lang.String getName(int i)

      Deprecated. 
      Return the name of an attribute in this list (by position).
      The names must be unique: the SAX parser shall not include the same attribute twice. Attributes without values (those declared \#IMPLIED without a value specified in the start tag) will be omitted from the list.

      If the attribute name has a namespace prefix, the prefix will still be attached.

      Parameters:
      `i` - The index of the attribute in the list (starting at 0).

      Returns:
      The name of the indexed attribute, or null if the index is out of range.

      See Also:
      `getLength()`

    <!-- -->

    - #### getType

          java.lang.String getType(int i)

      Deprecated. 
      Return the type of an attribute in the list (by position).
      The attribute type is one of the strings "CDATA", "ID", "IDREF", "IDREFS", "NMTOKEN", "NMTOKENS", "ENTITY", "ENTITIES", or "NOTATION" (always in upper case).

      If the parser has not read a declaration for the attribute, or if the parser does not report attribute types, then it must return the value "CDATA" as stated in the XML 1.0 Recommentation (clause 3.3.3, "Attribute-Value Normalization").

      For an enumerated attribute that is not a notation, the parser will report the type as "NMTOKEN".

      Parameters:
      `i` - The index of the attribute in the list (starting at 0).

      Returns:
      The attribute type as a string, or null if the index is out of range.

      See Also:
      `getLength()`, `getType(java.lang.String)`

    <!-- -->

    - #### getValue

          java.lang.String getValue(int i)

      Deprecated. 
      Return the value of an attribute in the list (by position).
      If the attribute value is a list of tokens (IDREFS, ENTITIES, or NMTOKENS), the tokens will be concatenated into a single string separated by whitespace.

      Parameters:
      `i` - The index of the attribute in the list (starting at 0).

      Returns:
      The attribute value as a string, or null if the index is out of range.

      See Also:
      `getLength()`, `getValue(java.lang.String)`

    <!-- -->

    - #### getType

          java.lang.String getType(java.lang.String name)

      Deprecated. 
      Return the type of an attribute in the list (by name).
      The return value is the same as the return value for getType(int).

      If the attribute name has a namespace prefix in the document, the application must include the prefix here.

      Parameters:
      `name` - The name of the attribute.

      Returns:
      The attribute type as a string, or null if no such attribute exists.

      See Also:
      `getType(int)`

    <!-- -->

    - #### getValue

          java.lang.String getValue(java.lang.String name)

      Deprecated. 
      Return the value of an attribute in the list (by name).
      The return value is the same as the return value for getValue(int).

      If the attribute name has a namespace prefix in the document, the application must include the prefix here.

      Parameters:
      `name` - The index of the attribute in the list.

      Returns:
      The attribute value as a string, or null if no such attribute exists.

      See Also:
      `getValue(int)`

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

- **Prev Class**
- **[Next Class](Attributes.md)**

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
