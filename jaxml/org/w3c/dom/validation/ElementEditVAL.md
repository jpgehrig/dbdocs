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

- **[Prev Class](DocumentEditVAL.md)**
- **[Next Class](ExceptionVAL.md)**

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

**org.w3c.dom.validation**

## **Interface ElementEditVAL**

- **All Superinterfaces:**
  **[NodeEditVAL](NodeEditVAL.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[XMLDocument](../../../../oracle/xml/parser/v2/XMLDocument.md), [XMLDocumentFragment](../../../../oracle/xml/parser/v2/XMLDocumentFragment.md), [XMLElement](../../../../oracle/xml/parser/v2/XMLElement.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface ElementEditVAL
      extends NodeEditVAL

  **This interface extends the `NodeEditVAL` interface with additional methods for guided document editing. An object implementing this interface must also implement the `Element` interface.**
  **This interface also has attributes that are a `NameList` of elements or attributes which can appear in the specified context. Some schema languages, i.e., [XML Schema](http://www.w3.org/TR/xmlschema-1/#Wildcards), define wildcards which provide for validation of attribute and element information items dependent on their namespace names but independent of their local names.**

  **To expose wildcards, the `NameList` returns the values that represent the [namespace constraint](http://www.w3.org/TR/xmlschema-1/#namespace_constraint):**

  - **`{namespaceURI, name}` is `{null, ##any}` if *any*;**
  - **`{namespaceURI, name}` is `{namespace_a, ##other}` if *not and a namespace name (namespace_a)*;**
  - **`{namespaceURI, name}` is `{null, ##other}` if *not and absent*;**
  - **Pairs of `{namespaceURI, name}` with values `{a_namespaceURI | null, ##other}` if *a set whose members are either namespace names or absent*.**

  **See also the [Document Object Model (DOM) Level 3 Validation Specification](https://www.w3.org/TR/DOM-Level-3-Val/validation.html).**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                                                                                                                             |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static short`    | `VAL_ANY_CONTENTTYPE`<br>The content model contains unordered child information item(s), i.e., element, processing instruction, unexpanded entity reference, character, and comment information items as defined in the [XML Information Set](http://www.w3.org/TR/xml-infoset/). |
    | `static short`    | `VAL_ELEMENTS_CONTENTTYPE`<br>The content model contains a sequence of [ele ment information items](http://www.w3.org/TR/xml-infoset/#infoitem.element) optionally separated by whitespace.                                                                                       |
    | `static short`    | `VAL_EMPTY_CONTENTTYPE`<br>The content model does not allow any [content](http://www.w3.org/TR/REC-xml#dt-content).                                                                                                                                                               |
    | `static short`    | `VAL_MIXED_CONTENTTYPE`<br>The content model contains a sequence of ordered [ele ment information items](http://www.w3.org/TR/xml-infoset/#infoitem.element) optionally interspersed with character data.                                                                         |
    | `static short`    | `VAL_SIMPLE_CONTENTTYPE`<br>The content model contains [character information items](http://www.w3.org/TR/xml-infoset/#infoitem.character).                                                                                                                                       |

    -

      ### **Fields inherited from interface org.w3c.dom.validation.[NodeEditVAL](NodeEditVAL.md)**

      **[`VAL_FALSE`](NodeEditVAL.md)`, `[`VAL_INCOMPLETE`](NodeEditVAL.md)`, `[`VAL_NS_WF`](NodeEditVAL.md)`, `[`VAL_SCHEMA`](NodeEditVAL.md)`, `[`VAL_TRUE`](NodeEditVAL.md)`, `[`VAL_UNKNOWN`](NodeEditVAL.md)`, `[`VAL_WF`](NodeEditVAL.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type            | Method and Description                                                                                                                                                                                                                                                                                               |
    |------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `short`                      | `canRemoveAttribute``(java.lang.String attrname)`<br>Verifies if an attribute by the given name can be removed.                                                                                                                                                                                                      |
    | `short`                      | `canRemoveAttributeNode``(`[`Node`](../Node.md)` attrNode)`<br>Determines if an attribute node can be removed.                                                                                                                                                                                                       |
    | `short`                      | `canRemoveAttributeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Verifies if an attribute by the given local name and namespace can be removed.                                                                                                                                                |
    | `short`                      | `canSetAttribute``(java.lang.String attrname, java.lang.String attrval)`<br>Determines if the value for specified attribute can be set.                                                                                                                                                                              |
    | `short`                      | `canSetAttributeNode``(`[`Attr`](../Attr.md)` attrNode)`<br>Determines if an attribute node can be added.                                                                                                                                                                                                            |
    | `short`                      | `canSetAttributeNS``(java.lang.String namespaceURI, java.lang.String qualifiedName, java.lang.String value)`<br>Determines if the attribute with given namespace and qualified name can be created if not already present in the attribute list of the element.                                                      |
    | [`NameList`](../NameList.md) | `getAllowedAttributes``()`<br>A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible attribute information items or wildcards that can appear as attributes of this element, or `null` if this element has no context or schema.             |
    | [`NameList`](../NameList.md) | `getAllowedChildren``()`<br>A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as children of this element, or `null` if this element has no context or schema.                   |
    | [`NameList`](../NameList.md) | `getAllowedFirstChildElements``()`<br>A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a first child of this element, or `null` if this element has no context or schema.    |
    | [`NameList`](../NameList.md) | `getAllowedNextSiblings``()`<br>A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a next sibling of this element, or `null` if this element has no context or schema.         |
    | [`NameList`](../NameList.md) | `getAllowedParents``()`<br>A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items that can appear as a parent this element, or `null` if this element has no context or schema.                                    |
    | [`NameList`](../NameList.md) | `getAllowedPreviousSiblings``()`<br>A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a previous sibling of this element, or `null` if this element has no context or schema. |
    | `short`                      | `getContentType``()`<br>The content type of an element.                                                                                                                                                                                                                                                              |
    | [`NameList`](../NameList.md) | `getRequiredAttributes``()`<br>A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of required attribute information items that must appear on this element, or `null` if this element has no context or schema.                                          |
    | `short`                      | `isElementDefined``(java.lang.String name)`<br>Determines if `name` is defined in the schema.                                                                                                                                                                                                                        |
    | `short`                      | `isElementDefinedNS``(java.lang.String namespaceURI, java.lang.String name)`<br>Determines if `name` in this namespace is defined in the current context.                                                                                                                                                            |

    - ### Methods inherited from interface org.w3c.dom.validation.[NodeEditVAL](NodeEditVAL.md)

      [`canAppendChild`](NodeEditVAL.md)`, `[`canInsertBefore`](NodeEditVAL.md)`, `[`canRemoveChild`](NodeEditVAL.md)`, `[`canReplaceChild`](NodeEditVAL.md)`, `[`getDefaultValue`](NodeEditVAL.md)`, `[`getEnumeratedValues`](NodeEditVAL.md)`, `[`nodeValidity`](NodeEditVAL.md)

<!-- -->

- - ### Field Detail

    - #### VAL_EMPTY_CONTENTTYPE

          static final short VAL_EMPTY_CONTENTTYPE

      The content model does not allow any [content](http://www.w3.org/TR/REC-xml#dt-content). If the schema is an XML Schema, this corresponds to the `empty` content type; and if the schema is a DTD, this corresponds to the `EMPTY` content model.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VAL_ANY_CONTENTTYPE

          static final short VAL_ANY_CONTENTTYPE

      The content model contains unordered child information item(s), i.e., element, processing instruction, unexpanded entity reference, character, and comment information items as defined in the [XML Information Set](http://www.w3.org/TR/xml-infoset/). If the schema is a DTD, this corresponds to the `ANY` content model.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VAL_MIXED_CONTENTTYPE

          static final short VAL_MIXED_CONTENTTYPE

      The content model contains a sequence of ordered [ele ment information items](http://www.w3.org/TR/xml-infoset/#infoitem.element) optionally interspersed with character data. If the schema is an XML Schema, this corresponds to the `mixed` content type.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VAL_ELEMENTS_CONTENTTYPE

          static final short VAL_ELEMENTS_CONTENTTYPE

      The content model contains a sequence of [ele ment information items](http://www.w3.org/TR/xml-infoset/#infoitem.element) optionally separated by whitespace. If the schema is a DTD, this is the `element content` content model; and if the schema is an XML Schema, this is the `element-only` content type.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VAL_SIMPLE_CONTENTTYPE

          static final short VAL_SIMPLE_CONTENTTYPE

      The content model contains [character information items](http://www.w3.org/TR/xml-infoset/#infoitem.character). If the schema is an XML Schema, this corresponds to the `simple type definition`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getAllowedChildren

          NameList getAllowedChildren()

      A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as children of this element, or `null` if this element has no context or schema. Duplicate pairs of {namespaceURI, name} are eliminated.

    <!-- -->

    - #### getAllowedFirstChildElements

          NameList getAllowedFirstChildElements()

      A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a first child of this element, or `null` if this element has no context or schema. Duplicate pairs of {namespaceURI, name} are eliminated.

    <!-- -->

    - #### getAllowedParents

          NameList getAllowedParents()

      A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items that can appear as a parent this element, or `null` if this element has no context or schema.

    <!-- -->

    - #### getAllowedNextSiblings

          NameList getAllowedNextSiblings()

      A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a next sibling of this element, or `null` if this element has no context or schema. Duplicate pairs of {namespaceURI, name} are eliminated.

    <!-- -->

    - #### getAllowedPreviousSiblings

          NameList getAllowedPreviousSiblings()

      A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a previous sibling of this element, or `null` if this element has no context or schema.

    <!-- -->

    - #### getAllowedAttributes

          NameList getAllowedAttributes()

      A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible attribute information items or wildcards that can appear as attributes of this element, or `null` if this element has no context or schema. Duplicate pairs of {namespaceURI, name} are eliminated.

    <!-- -->

    - #### getRequiredAttributes

          NameList getRequiredAttributes()

      A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of required attribute information items that must appear on this element, or `null` if this element has no context or schema. Duplicate pairs of {namespaceURI, name} are eliminated.

    <!-- -->

    - #### getContentType

          short getContentType()

      The content type of an element.

    <!-- -->

    - #### canSetAttribute

          short canSetAttribute(java.lang.String attrname,
                                java.lang.String attrval)

      Determines if the value for specified attribute can be set.
      Parameters:
      `attrname` - Name of attribute.

      `attrval` - Value to be assigned to the attribute.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canSetAttributeNode

          short canSetAttributeNode(Attr attrNode)

      Determines if an attribute node can be added.
      Parameters:
      `attrNode` - `Node` in which the attribute can possibly be set.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canSetAttributeNS

          short canSetAttributeNS(java.lang.String namespaceURI,
                                  java.lang.String qualifiedName,
                                  java.lang.String value)

      Determines if the attribute with given namespace and qualified name can be created if not already present in the attribute list of the element. If the attribute with the same qualified name and namespaceURI is already present in the element's attribute list, it tests whether the value of the attribute and its prefix can be set to the new value. See DOM core `setAttributeNS`.
      Parameters:
      `namespaceURI` - `namespaceURI` of namespace.

      `qualifiedName` - Qualified name of attribute.

      `value` - Value to be assigned to the attribute.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canRemoveAttribute

          short canRemoveAttribute(java.lang.String attrname)

      Verifies if an attribute by the given name can be removed.
      Parameters:
      `attrname` - Name of attribute.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canRemoveAttributeNS

          short canRemoveAttributeNS(java.lang.String namespaceURI,
                                     java.lang.String localName)

      Verifies if an attribute by the given local name and namespace can be removed.
      Parameters:
      `namespaceURI` - The namespace URI of the attribute to remove.

      `localName` - Local name of the attribute to be removed.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canRemoveAttributeNode

          short canRemoveAttributeNode(Node attrNode)

      Determines if an attribute node can be removed.
      Parameters:
      `attrNode` - The `Attr` node to remove from the attribute list.

      Returns:
      A validation state constant.

    <!-- -->

    - #### isElementDefined

          short isElementDefined(java.lang.String name)

      Determines if `name` is defined in the schema. This only applies to global declarations.
      Parameters:
      `name` - Name of element.

      Returns:
      A validation state constant.

    <!-- -->

    - #### isElementDefinedNS

          short isElementDefinedNS(java.lang.String namespaceURI,
                                   java.lang.String name)

      Determines if `name` in this namespace is defined in the current context. Thus not only does this apply to global declarations . but depending on the content, this may also apply to local definitions.
      Parameters:
      `namespaceURI` - `namespaceURI` of namespace.

      `name` - Name of element.

      Returns:
      A validation state constant.

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

- **[Prev Class](DocumentEditVAL.md)**
- **[Next Class](ExceptionVAL.md)**

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

**[Copyright](http://www.w3.org/Consortium/Legal/ipr-notice#Copyright) ©2004 [W3C](http://www.w3.org/)® ([MIT](http://www.csail.mit.edu/), [ERCIM](http://www.ercim.org/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [trademark](http://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks), [document use](http://www.w3.org/Consortium/Legal/copyright-documents) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software) rules apply. The latest version is at [http://www.w3.org/TR/DOM-Level-3-Val](http://www.w3.org/TR/DOM-Level-3-Val/).**
