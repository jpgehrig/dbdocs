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

- **Prev Class**
- **[Next Class](AttributesImpl.md)**

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

## **Class AttributeListImpl**

- **java.lang.Object**

- - **org.xml.sax.helpers.AttributeListImpl**

<!-- -->

- **All Implemented Interfaces:**
  **[AttributeList](../AttributeList.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **This class implements a deprecated interface, [`AttributeList`](../AttributeList.md); that interface has been replaced by [`Attributes`](../Attributes.md), which is implemented in the [`AttributesImpl`](AttributesImpl.md) helper class.**
  **
  **

      public class AttributeListImpl
      extends java.lang.Object
      implements AttributeList

  **Default implementation for AttributeList.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **AttributeList implements the deprecated SAX1 [`AttributeList`](../AttributeList.md) interface, and has been replaced by the new SAX2 [`AttributesImpl`](AttributesImpl.md) interface.**

  **This class provides a convenience implementation of the SAX [`AttributeList`](../AttributeList.md) interface. This implementation is useful both for SAX parser writers, who can use it to provide attributes to the application, and for SAX application writers, who can use it to create a persistent copy of an element's attribute specifications:**

       private AttributeList myatts;

       public void startElement (String name, AttributeList atts)
       {
                    // create a persistent copy of the attribute list
                    // for use outside this method
         myatts = new AttributeListImpl(atts);
         [...]
       }


  **Please note that SAX parsers are not required to use this class to provide an implementation of AttributeList; it is supplied only as an optional convenience. In particular, parser writers are encouraged to invent more efficient implementations.**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`AttributeList`](../AttributeList.md), [`DocumentHandler.startElement(java.lang.String, org.xml.sax.AttributeList)`](../DocumentHandler.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                        |
    |----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `AttributeListImpl``()`<br>Deprecated. <br>Create an empty attribute list.                                                                         |
    | `AttributeListImpl``(`[`AttributeList`](../AttributeList.md)` atts)`<br>Deprecated. <br>Construct a persistent copy of an existing attribute list. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type  | Method and Description                                                                                                                           |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `addAttribute``(java.lang.String name, java.lang.String type, java.lang.String value)`<br>Deprecated. <br>Add an attribute to an attribute list. |
    | `void`             | `clear``()`<br>Deprecated. <br>Clear the attribute list.                                                                                         |
    | `int`              | `getLength``()`<br>Deprecated. <br>Return the number of attributes in the list.                                                                  |
    | `java.lang.String` | `getName``(int i)`<br>Deprecated. <br>Get the name of an attribute (by position).                                                                |
    | `java.lang.String` | `getType``(int i)`<br>Deprecated. <br>Get the type of an attribute (by position).                                                                |
    | `java.lang.String` | `getType``(java.lang.String name)`<br>Deprecated. <br>Get the type of an attribute (by name).                                                    |
    | `java.lang.String` | `getValue``(int i)`<br>Deprecated. <br>Get the value of an attribute (by position).                                                              |
    | `java.lang.String` | `getValue``(java.lang.String name)`<br>Deprecated. <br>Get the value of an attribute (by name).                                                  |
    | `void`             | `removeAttribute``(java.lang.String name)`<br>Deprecated. <br>Remove an attribute from the list.                                                 |
    | `void`             | `setAttributeList``(`[`AttributeList`](../AttributeList.md)` atts)`<br>Deprecated. <br>Set the attribute list, discarding previous contents.     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AttributeListImpl

          public AttributeListImpl()

      Deprecated. 
      Create an empty attribute list.
      This constructor is most useful for parser writers, who will use it to create a single, reusable attribute list that can be reset with the clear method between elements.

      See Also:
      `addAttribute(java.lang.String, java.lang.String, java.lang.String)`, `clear()`

    <!-- -->

    - #### AttributeListImpl

          public AttributeListImpl(AttributeList atts)

      Deprecated. 
      Construct a persistent copy of an existing attribute list.
      This constructor is most useful for application writers, who will use it to create a persistent copy of an existing attribute list.

      Parameters:
      `atts` - The attribute list to copy

      See Also:
      [`DocumentHandler.startElement(java.lang.String, org.xml.sax.AttributeList)`](../DocumentHandler.md)

  <!-- -->

  - ### Method Detail

    - #### setAttributeList

          public void setAttributeList(AttributeList atts)

      Deprecated. 
      Set the attribute list, discarding previous contents.
      This method allows an application writer to reuse an attribute list easily.

      Parameters:
      `atts` - The attribute list to copy.

    <!-- -->

    - #### addAttribute

          public void addAttribute(java.lang.String name,
                                   java.lang.String type,
                                   java.lang.String value)

      Deprecated. 
      Add an attribute to an attribute list.
      This method is provided for SAX parser writers, to allow them to build up an attribute list incrementally before delivering it to the application.

      Parameters:
      `name` - The attribute name.

      `type` - The attribute type ("NMTOKEN" for an enumeration).

      `value` - The attribute value (must not be null).

      See Also:
      `removeAttribute(java.lang.String)`, [`DocumentHandler.startElement(java.lang.String, org.xml.sax.AttributeList)`](../DocumentHandler.md)

    <!-- -->

    - #### removeAttribute

          public void removeAttribute(java.lang.String name)

      Deprecated. 
      Remove an attribute from the list.
      SAX application writers can use this method to filter an attribute out of an AttributeList. Note that invoking this method will change the length of the attribute list and some of the attribute's indices.

      If the requested attribute is not in the list, this is a no-op.

      Parameters:
      `name` - The attribute name.

      See Also:
      `addAttribute(java.lang.String, java.lang.String, java.lang.String)`

    <!-- -->

    - #### clear

          public void clear()

      Deprecated. 
      Clear the attribute list.
      SAX parser writers can use this method to reset the attribute list between DocumentHandler.startElement events. Normally, it will make sense to reuse the same AttributeListImpl object rather than allocating a new one each time.

      See Also:
      [`DocumentHandler.startElement(java.lang.String, org.xml.sax.AttributeList)`](../DocumentHandler.md)

    <!-- -->

    - #### getLength

          public int getLength()

      Deprecated. 
      Return the number of attributes in the list.
      Specified by:
      [`getLength`](../AttributeList.md) in interface [`AttributeList`](../AttributeList.md)

      Returns:
      The number of attributes in the list.

      See Also:
      [`AttributeList.getLength()`](../AttributeList.md)

    <!-- -->

    - #### getName

          public java.lang.String getName(int i)

      Deprecated. 
      Get the name of an attribute (by position).
      Specified by:
      [`getName`](../AttributeList.md) in interface [`AttributeList`](../AttributeList.md)

      Parameters:
      `i` - The position of the attribute in the list.

      Returns:
      The attribute name as a string, or null if there is no attribute at that position.

      See Also:
      [`AttributeList.getName(int)`](../AttributeList.md)

    <!-- -->

    - #### getType

          public java.lang.String getType(int i)

      Deprecated. 
      Get the type of an attribute (by position).
      Specified by:
      [`getType`](../AttributeList.md) in interface [`AttributeList`](../AttributeList.md)

      Parameters:
      `i` - The position of the attribute in the list.

      Returns:
      The attribute type as a string ("NMTOKEN" for an enumeration, and "CDATA" if no declaration was read), or null if there is no attribute at that position.

      See Also:
      [`AttributeList.getType(int)`](../AttributeList.md)

    <!-- -->

    - #### getValue

          public java.lang.String getValue(int i)

      Deprecated. 
      Get the value of an attribute (by position).
      Specified by:
      [`getValue`](../AttributeList.md) in interface [`AttributeList`](../AttributeList.md)

      Parameters:
      `i` - The position of the attribute in the list.

      Returns:
      The attribute value as a string, or null if there is no attribute at that position.

      See Also:
      [`AttributeList.getValue(int)`](../AttributeList.md)

    <!-- -->

    - #### getType

          public java.lang.String getType(java.lang.String name)

      Deprecated. 
      Get the type of an attribute (by name).
      Specified by:
      [`getType`](../AttributeList.md) in interface [`AttributeList`](../AttributeList.md)

      Parameters:
      `name` - The attribute name.

      Returns:
      The attribute type as a string ("NMTOKEN" for an enumeration, and "CDATA" if no declaration was read).

      See Also:
      [`AttributeList.getType(java.lang.String)`](../AttributeList.md)

    <!-- -->

    - #### getValue

          public java.lang.String getValue(java.lang.String name)

      Deprecated. 
      Get the value of an attribute (by name).
      Specified by:
      [`getValue`](../AttributeList.md) in interface [`AttributeList`](../AttributeList.md)

      Parameters:
      `name` - The attribute name.

      Returns:
      The attribute value as a string, or null if no such attribute exists.

      See Also:
      [`AttributeList.getValue(java.lang.String)`](../AttributeList.md)

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

- **Prev Class**
- **[Next Class](AttributesImpl.md)**

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
