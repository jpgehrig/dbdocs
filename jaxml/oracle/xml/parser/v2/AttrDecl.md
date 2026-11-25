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
- **[Next Class](BinaryParser.md)**

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

## **Class AttrDecl**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **oracle.xml.parser.v2.AttrDecl**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  ------------------------------------------------------------------------

  **
  **

      public class AttrDecl
      extends XMLNode
      implements java.io.Externalizable

  **This class hold information about each attribute declared in an attribute list in the Document Type Definition.**
  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                   |
    |-------------------|---------------------------------------------------------|
    | `static int`      | `CDATA`<br>AttType - StringType - CDATA                 |
    | `static int`      | `DEFAULT`<br>Attribute presence - Default               |
    | `static int`      | `ENTITIES`<br>AttType - TokenizedType - Entities        |
    | `static int`      | `ENTITY`<br>AttType - TokenizedType - Entity            |
    | `static int`      | `ENUMERATION`<br>AttType - EnumeratedType - Enumeration |
    | `static int`      | `FIXED`<br>Attribute presence - Fixed                   |
    | `static int`      | `ID`<br>AttType - TokenizedType - ID                    |
    | `static int`      | `IDREF`<br>AttType - TokenizedType - ID reference       |
    | `static int`      | `IDREFS`<br>AttType - TokenizedType - ID references     |
    | `static int`      | `IMPLIED`<br>Attribute presence - Implied               |
    | `static int`      | `NMTOKEN`<br>AttType - TokenizedType - Name token       |
    | `static int`      | `NMTOKENS`<br>AttType - TokenizedType - Name tokens     |
    | `static int`      | `NOTATION`<br>AttType - EnumeratedType - Notation       |
    | `static int`      | `REQUIRED`<br>Attribute presence - Required             |

    -

      ### **Fields inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)**

      **[`ATTRDECL`](XMLNode.md)`, `[`Auto_Events`](XMLNode.md)`, `[`capturing`](XMLNode.md)`, `[`DOMAttrModified`](XMLNode.md)`, `[`DOMCharacterDataModified`](XMLNode.md)`, `[`DOMNodeInserted`](XMLNode.md)`, `[`DOMNodeInsertedIntoDocument`](XMLNode.md)`, `[`DOMNodeRemoved`](XMLNode.md)`, `[`DOMNodeRemovedFromDocument`](XMLNode.md)`, `[`DOMSubtreeModified`](XMLNode.md)`, `[`ELEMENTDECL`](XMLNode.md)`, `[`KEPT_NODE`](XMLNode.md)`, `[`NAMESPACE_NODE`](XMLNode.md)`, `[`noncapturing`](XMLNode.md)`, `[`RANGE_DELETE_EVENT`](XMLNode.md)`, `[`RANGE_DELETETEXT_EVENT`](XMLNode.md)`, `[`RANGE_INSERT_EVENT`](XMLNode.md)`, `[`RANGE_INSERTTEXT_EVENT`](XMLNode.md)`, `[`RANGE_REPLACE_EVENT`](XMLNode.md)`, `[`RANGE_SETTEXT_EVENT`](XMLNode.md)`, `[`TRAVERSAL_DELETE_EVENT`](XMLNode.md)`, `[`TRAVERSAL_REPLACE_EVENT`](XMLNode.md)`, `[`XMLDECL_NODE`](XMLNode.md)**

    <!-- -->

    -

      ### **Fields inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)**

      **[`ATTRIBUTE_NODE`](../../../../org/w3c/dom/Node.md)`, `[`CDATA_SECTION_NODE`](../../../../org/w3c/dom/Node.md)`, `[`COMMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_FRAGMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_TYPE_NODE`](../../../../org/w3c/dom/Node.md)`, `[`ELEMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`ENTITY_NODE`](../../../../org/w3c/dom/Node.md)`, `[`ENTITY_REFERENCE_NODE`](../../../../org/w3c/dom/Node.md)`, `[`NOTATION_NODE`](../../../../org/w3c/dom/Node.md)`, `[`PROCESSING_INSTRUCTION_NODE`](../../../../org/w3c/dom/Node.md)`, `[`TEXT_NODE`](../../../../org/w3c/dom/Node.md)**

    <!-- -->

    -

      ### **Fields inherited from interface org.w3c.dom.validation.[NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

      **[`VAL_FALSE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_INCOMPLETE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_NS_WF`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_SCHEMA`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_TRUE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_UNKNOWN`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_WF`](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description            |
    |----------------------------------------|
    | `AttrDecl``()`<br>Default constructor. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                             |
    |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`              | `getAttrPresence``()`<br>Gets attribute presence                                                                                                                                   |
    | `int`              | `getAttrType``()`<br>Gets attribute type                                                                                                                                           |
    | `java.lang.String` | `getDefaultValue``()`<br>Gets attribute default value                                                                                                                              |
    | `java.util.Vector` | `getEnumerationValues``()`<br>Gets attribute values                                                                                                                                |
    | `java.lang.String` | `getNodeName``()`<br>Gets the name of this node, depending on its type                                                                                                             |
    | `short`            | `getNodeType``()`<br>Gets a code representing the type of the underlying object                                                                                                    |
    | `void`             | `readExternal``(java.io.ObjectInput inArg)`<br>This method reads the information written in the compressed stream by writeExternal method and restores the object correspondingly. |
    | `void`             | `writeExternal``(java.io.ObjectOutput outArg)`<br>This method saves the state of the object by creating a binary compressed stream with information about this object.             |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`addText`](XMLNode.md)`, `[`appendChild`](XMLNode.md)`, `[`canAppendChild`](XMLNode.md)`, `[`canInsertBefore`](XMLNode.md)`, `[`canRemoveChild`](XMLNode.md)`, `[`canReplaceChild`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getAttributes`](XMLNode.md)`, `[`getChildNodes`](XMLNode.md)`, `[`getColumnNumber`](XMLNode.md)`, `[`getDebugMode`](XMLNode.md)`, `[`getEnumeratedValues`](XMLNode.md)`, `[`getFirstChild`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getLastChild`](XMLNode.md)`, `[`getLineNumber`](XMLNode.md)`, `[`getLocalName`](XMLNode.md)`, `[`getNamespaceURI`](XMLNode.md)`, `[`getNextSibling`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeValue`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getOwnerDocument`](XMLNode.md)`, `[`getParentNode`](XMLNode.md)`, `[`getPrefix`](XMLNode.md)`, `[`getPreviousSibling`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getSystemId`](XMLNode.md)`, `[`getText`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasAttributes`](XMLNode.md)`, `[`hasChildNodes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`insertBefore`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`nodeValidity`](XMLNode.md)`, `[`normalize`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`removeChild`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`replaceChild`](XMLNode.md)`, `[`reportSAXEvents`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValue`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setPrefix`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### CDATA

          public static final int CDATA

      AttType - StringType - CDATA
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ID

          public static final int ID

      AttType - TokenizedType - ID
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IDREF

          public static final int IDREF

      AttType - TokenizedType - ID reference
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IDREFS

          public static final int IDREFS

      AttType - TokenizedType - ID references
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ENTITY

          public static final int ENTITY

      AttType - TokenizedType - Entity
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ENTITIES

          public static final int ENTITIES

      AttType - TokenizedType - Entities
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NMTOKEN

          public static final int NMTOKEN

      AttType - TokenizedType - Name token
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NMTOKENS

          public static final int NMTOKENS

      AttType - TokenizedType - Name tokens
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NOTATION

          public static final int NOTATION

      AttType - EnumeratedType - Notation
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ENUMERATION

          public static final int ENUMERATION

      AttType - EnumeratedType - Enumeration
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DEFAULT

          public static final int DEFAULT

      Attribute presence - Default
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### REQUIRED

          public static final int REQUIRED

      Attribute presence - Required
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IMPLIED

          public static final int IMPLIED

      Attribute presence - Implied
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FIXED

          public static final int FIXED

      Attribute presence - Fixed
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### AttrDecl

          public AttrDecl()

      Default constructor. Note that this constructor is used only during deserialization/decompression of this DOM node. In order to deserialize this node to construct the DOM node from the serialized/ compressed stream, it is required to create a handle of the object.

  <!-- -->

  - ### Method Detail

    - #### getNodeType

          public short getNodeType()

      Gets a code representing the type of the underlying object
      Specified by:
      [`getNodeType`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNodeType`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      type of the node

    <!-- -->

    - #### getNodeName

          public java.lang.String getNodeName()

      Gets the name of this node, depending on its type
      Specified by:
      [`getNodeName`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNodeName`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      Name of this node

    <!-- -->

    - #### getAttrType

          public int getAttrType()

      Gets attribute type
      Returns:
      The type of the attribute

    <!-- -->

    - #### getAttrPresence

          public int getAttrPresence()

      Gets attribute presence
      Returns:
      The presence of the attribute

    <!-- -->

    - #### getDefaultValue

          public java.lang.String getDefaultValue()

      Gets attribute default value
      Specified by:
      [`getDefaultValue`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`getDefaultValue`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      The default value of the attribute

    <!-- -->

    - #### getEnumerationValues

          public java.util.Vector getEnumerationValues()

      Gets attribute values
      Returns:
      The values of the attribute as an `Enumeration`

    <!-- -->

    - #### writeExternal

          public void writeExternal(java.io.ObjectOutput outArg)
                             throws java.io.IOException

      This method saves the state of the object by creating a binary compressed stream with information about this object.
      Specified by:
      `writeExternal` in interface `java.io.Externalizable`

      Overrides:
      [`writeExternal`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `outArg` - The ObjectOutput stream used to write the serialized/ compressed stream.

      Throws:
      `java.io.IOException` - is thrown when there is an exception while writing the serialized/compressed stream.

    <!-- -->

    - #### readExternal

          public void readExternal(java.io.ObjectInput inArg)
                            throws java.io.IOException,
                                   java.lang.ClassNotFoundException

      This method reads the information written in the compressed stream by writeExternal method and restores the object correspondingly.
      Specified by:
      `readExternal` in interface `java.io.Externalizable`

      Overrides:
      [`readExternal`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `inArg` - the ObjectInput stream used for reading the compressed stream.

      Throws:
      `java.io.IOException` - is thrown when there is an error in reading the input stream.

      `java.lang.ClassNotFoundException` - is thrown when the class is not found

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
- **[Next Class](BinaryParser.md)**

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
