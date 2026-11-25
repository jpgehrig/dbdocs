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

- **[Prev Class](AttributeListImpl.md)**
- **[Next Class](DefaultHandler.md)**

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

**org.xml.sax.helpers**

## **Class AttributesImpl**

- **java.lang.Object**

- - **org.xml.sax.helpers.AttributesImpl**

<!-- -->

- **All Implemented Interfaces:**
  **[Attributes](../Attributes.md)**

  ------------------------------------------------------------------------

  **
  **

      public class AttributesImpl
      extends java.lang.Object
      implements Attributes

  **Default implementation of the Attributes interface.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class provides a default implementation of the SAX2 [`Attributes`](../Attributes.md) interface, with the addition of manipulators so that the list can be modified or reused.**

  **There are two typical uses of this class:**

  1.  **to take a persistent snapshot of an Attributes object in a [`startElement`](../ContentHandler.md) event; or**
  2.  **to construct or modify an Attributes object in a SAX2 driver or filter.**

  **This class replaces the now-deprecated SAX1 [`AttributeListImpl`](AttributeListImpl.md) class; in addition to supporting the updated Attributes interface rather than the deprecated [`AttributeList`](../AttributeList.md) interface, it also includes a much more efficient implementation using a single array rather than a set of Vectors.**

  **Since:**
  **SAX 2.0**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                        |
    |----------------------------------------------------------------------------------------------------|
    | `AttributesImpl``()`<br>Construct a new, empty AttributesImpl object.                              |
    | `AttributesImpl``(`[`Attributes`](../Attributes.md)` atts)`<br>Copy an existing Attributes object. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                |
    |--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `addAttribute``(java.lang.String uri, java.lang.String localName, java.lang.String qName, java.lang.String type, java.lang.String value)`<br>Add an attribute to the end of the list. |
    | `void`             | `clear``()`<br>Clear the attribute list for reuse.                                                                                                                                    |
    | `int`              | `getIndex``(java.lang.String qName)`<br>Look up an attribute's index by qualified (prefixed) name.                                                                                    |
    | `int`              | `getIndex``(java.lang.String uri, java.lang.String localName)`<br>Look up an attribute's index by Namespace name.                                                                     |
    | `int`              | `getLength``()`<br>Return the number of attributes in the list.                                                                                                                       |
    | `java.lang.String` | `getLocalName``(int index)`<br>Return an attribute's local name.                                                                                                                      |
    | `java.lang.String` | `getQName``(int index)`<br>Return an attribute's qualified (prefixed) name.                                                                                                           |
    | `java.lang.String` | `getType``(int index)`<br>Return an attribute's type by index.                                                                                                                        |
    | `java.lang.String` | `getType``(java.lang.String qName)`<br>Look up an attribute's type by qualified (prefixed) name.                                                                                      |
    | `java.lang.String` | `getType``(java.lang.String uri, java.lang.String localName)`<br>Look up an attribute's type by Namespace-qualified name.                                                             |
    | `java.lang.String` | `getURI``(int index)`<br>Return an attribute's Namespace URI.                                                                                                                         |
    | `java.lang.String` | `getValue``(int index)`<br>Return an attribute's value by index.                                                                                                                      |
    | `java.lang.String` | `getValue``(java.lang.String qName)`<br>Look up an attribute's value by qualified (prefixed) name.                                                                                    |
    | `java.lang.String` | `getValue``(java.lang.String uri, java.lang.String localName)`<br>Look up an attribute's value by Namespace-qualified name.                                                           |
    | `void`             | `removeAttribute``(int index)`<br>Remove an attribute from the list.                                                                                                                  |
    | `void`             | `setAttribute``(int index, java.lang.String uri, java.lang.String localName, java.lang.String qName, java.lang.String type, java.lang.String value)`<br>Set an attribute in the list. |
    | `void`             | `setAttributes``(`[`Attributes`](../Attributes.md)` atts)`<br>Copy an entire Attributes object.                                                                                       |
    | `void`             | `setLocalName``(int index, java.lang.String localName)`<br>Set the local name of a specific attribute.                                                                                |
    | `void`             | `setQName``(int index, java.lang.String qName)`<br>Set the qualified name of a specific attribute.                                                                                    |
    | `void`             | `setType``(int index, java.lang.String type)`<br>Set the type of a specific attribute.                                                                                                |
    | `void`             | `setURI``(int index, java.lang.String uri)`<br>Set the Namespace URI of a specific attribute.                                                                                         |
    | `void`             | `setValue``(int index, java.lang.String value)`<br>Set the value of a specific attribute.                                                                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AttributesImpl

          public AttributesImpl()

      Construct a new, empty AttributesImpl object.

    <!-- -->

    - #### AttributesImpl

          public AttributesImpl(Attributes atts)

      Copy an existing Attributes object.
      This constructor is especially useful inside a [`startElement`](../ContentHandler.md) event.

      Parameters:
      `atts` - The existing Attributes object.

  <!-- -->

  - ### Method Detail

    - #### getLength

          public int getLength()

      Return the number of attributes in the list.
      Specified by:
      [`getLength`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Returns:
      The number of attributes in the list.

      See Also:
      [`Attributes.getLength()`](../Attributes.md)

    <!-- -->

    - #### getURI

          public java.lang.String getURI(int index)

      Return an attribute's Namespace URI.
      Specified by:
      [`getURI`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `index` - The attribute's index (zero-based).

      Returns:
      The Namespace URI, the empty string if none is available, or null if the index is out of range.

      See Also:
      [`Attributes.getURI(int)`](../Attributes.md)

    <!-- -->

    - #### getLocalName

          public java.lang.String getLocalName(int index)

      Return an attribute's local name.
      Specified by:
      [`getLocalName`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `index` - The attribute's index (zero-based).

      Returns:
      The attribute's local name, the empty string if none is available, or null if the index if out of range.

      See Also:
      [`Attributes.getLocalName(int)`](../Attributes.md)

    <!-- -->

    - #### getQName

          public java.lang.String getQName(int index)

      Return an attribute's qualified (prefixed) name.
      Specified by:
      [`getQName`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `index` - The attribute's index (zero-based).

      Returns:
      The attribute's qualified name, the empty string if none is available, or null if the index is out of bounds.

      See Also:
      [`Attributes.getQName(int)`](../Attributes.md)

    <!-- -->

    - #### getType

          public java.lang.String getType(int index)

      Return an attribute's type by index.
      Specified by:
      [`getType`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `index` - The attribute's index (zero-based).

      Returns:
      The attribute's type, "CDATA" if the type is unknown, or null if the index is out of bounds.

      See Also:
      [`Attributes.getType(int)`](../Attributes.md)

    <!-- -->

    - #### getValue

          public java.lang.String getValue(int index)

      Return an attribute's value by index.
      Specified by:
      [`getValue`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `index` - The attribute's index (zero-based).

      Returns:
      The attribute's value or null if the index is out of bounds.

      See Also:
      [`Attributes.getValue(int)`](../Attributes.md)

    <!-- -->

    - #### getIndex

          public int getIndex(java.lang.String uri,
                              java.lang.String localName)

      Look up an attribute's index by Namespace name.
      In many cases, it will be more efficient to look up the name once and use the index query methods rather than using the name query methods repeatedly.

      Specified by:
      [`getIndex`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `uri` - The attribute's Namespace URI, or the empty string if none is available.

      `localName` - The attribute's local name.

      Returns:
      The attribute's index, or -1 if none matches.

      See Also:
      [`Attributes.getIndex(java.lang.String,java.lang.String)`](../Attributes.md)

    <!-- -->

    - #### getIndex

          public int getIndex(java.lang.String qName)

      Look up an attribute's index by qualified (prefixed) name.
      Specified by:
      [`getIndex`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `qName` - The qualified name.

      Returns:
      The attribute's index, or -1 if none matches.

      See Also:
      [`Attributes.getIndex(java.lang.String)`](../Attributes.md)

    <!-- -->

    - #### getType

          public java.lang.String getType(java.lang.String uri,
                                          java.lang.String localName)

      Look up an attribute's type by Namespace-qualified name.
      Specified by:
      [`getType`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `uri` - The Namespace URI, or the empty string for a name with no explicit Namespace URI.

      `localName` - The local name.

      Returns:
      The attribute's type, or null if there is no matching attribute.

      See Also:
      [`Attributes.getType(java.lang.String,java.lang.String)`](../Attributes.md)

    <!-- -->

    - #### getType

          public java.lang.String getType(java.lang.String qName)

      Look up an attribute's type by qualified (prefixed) name.
      Specified by:
      [`getType`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `qName` - The qualified name.

      Returns:
      The attribute's type, or null if there is no matching attribute.

      See Also:
      [`Attributes.getType(java.lang.String)`](../Attributes.md)

    <!-- -->

    - #### getValue

          public java.lang.String getValue(java.lang.String uri,
                                           java.lang.String localName)

      Look up an attribute's value by Namespace-qualified name.
      Specified by:
      [`getValue`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `uri` - The Namespace URI, or the empty string for a name with no explicit Namespace URI.

      `localName` - The local name.

      Returns:
      The attribute's value, or null if there is no matching attribute.

      See Also:
      [`Attributes.getValue(java.lang.String,java.lang.String)`](../Attributes.md)

    <!-- -->

    - #### getValue

          public java.lang.String getValue(java.lang.String qName)

      Look up an attribute's value by qualified (prefixed) name.
      Specified by:
      [`getValue`](../Attributes.md) in interface [`Attributes`](../Attributes.md)

      Parameters:
      `qName` - The qualified name.

      Returns:
      The attribute's value, or null if there is no matching attribute.

      See Also:
      [`Attributes.getValue(java.lang.String)`](../Attributes.md)

    <!-- -->

    - #### clear

          public void clear()

      Clear the attribute list for reuse.
      Note that no memory is actually freed by this call: the current arrays are kept so that they can be reused.

    <!-- -->

    - #### setAttributes

          public void setAttributes(Attributes atts)

      Copy an entire Attributes object.
      It may be more efficient to reuse an existing object rather than constantly allocating new ones.

      Parameters:
      `atts` - The attributes to copy.

    <!-- -->

    - #### addAttribute

          public void addAttribute(java.lang.String uri,
                                   java.lang.String localName,
                                   java.lang.String qName,
                                   java.lang.String type,
                                   java.lang.String value)

      Add an attribute to the end of the list.
      For the sake of speed, this method does no checking to see if the attribute is already in the list: that is the responsibility of the application.

      Parameters:
      `uri` - The Namespace URI, or the empty string if none is available or Namespace processing is not being performed.

      `localName` - The local name, or the empty string if Namespace processing is not being performed.

      `qName` - The qualified (prefixed) name, or the empty string if qualified names are not available.

      `type` - The attribute type as a string.

      `value` - The attribute value.

    <!-- -->

    - #### setAttribute

          public void setAttribute(int index,
                                   java.lang.String uri,
                                   java.lang.String localName,
                                   java.lang.String qName,
                                   java.lang.String type,
                                   java.lang.String value)

      Set an attribute in the list.
      For the sake of speed, this method does no checking for name conflicts or well-formedness: such checks are the responsibility of the application.

      Parameters:
      `index` - The index of the attribute (zero-based).

      `uri` - The Namespace URI, or the empty string if none is available or Namespace processing is not being performed.

      `localName` - The local name, or the empty string if Namespace processing is not being performed.

      `qName` - The qualified name, or the empty string if qualified names are not available.

      `type` - The attribute type as a string.

      `value` - The attribute value.

      Throws:
      `java.lang.ArrayIndexOutOfBoundsException` - When the supplied index does not point to an attribute in the list.

    <!-- -->

    - #### removeAttribute

          public void removeAttribute(int index)

      Remove an attribute from the list.
      Parameters:
      `index` - The index of the attribute (zero-based).

      Throws:
      `java.lang.ArrayIndexOutOfBoundsException` - When the supplied index does not point to an attribute in the list.

    <!-- -->

    - #### setURI

          public void setURI(int index,
                             java.lang.String uri)

      Set the Namespace URI of a specific attribute.
      Parameters:
      `index` - The index of the attribute (zero-based).

      `uri` - The attribute's Namespace URI, or the empty string for none.

      Throws:
      `java.lang.ArrayIndexOutOfBoundsException` - When the supplied index does not point to an attribute in the list.

    <!-- -->

    - #### setLocalName

          public void setLocalName(int index,
                                   java.lang.String localName)

      Set the local name of a specific attribute.
      Parameters:
      `index` - The index of the attribute (zero-based).

      `localName` - The attribute's local name, or the empty string for none.

      Throws:
      `java.lang.ArrayIndexOutOfBoundsException` - When the supplied index does not point to an attribute in the list.

    <!-- -->

    - #### setQName

          public void setQName(int index,
                               java.lang.String qName)

      Set the qualified name of a specific attribute.
      Parameters:
      `index` - The index of the attribute (zero-based).

      `qName` - The attribute's qualified name, or the empty string for none.

      Throws:
      `java.lang.ArrayIndexOutOfBoundsException` - When the supplied index does not point to an attribute in the list.

    <!-- -->

    - #### setType

          public void setType(int index,
                              java.lang.String type)

      Set the type of a specific attribute.
      Parameters:
      `index` - The index of the attribute (zero-based).

      `type` - The attribute's type.

      Throws:
      `java.lang.ArrayIndexOutOfBoundsException` - When the supplied index does not point to an attribute in the list.

    <!-- -->

    - #### setValue

          public void setValue(int index,
                               java.lang.String value)

      Set the value of a specific attribute.
      Parameters:
      `index` - The index of the attribute (zero-based).

      `value` - The attribute's value.

      Throws:
      `java.lang.ArrayIndexOutOfBoundsException` - When the supplied index does not point to an attribute in the list.

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

- **[Prev Class](AttributeListImpl.md)**
- **[Next Class](DefaultHandler.md)**

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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
