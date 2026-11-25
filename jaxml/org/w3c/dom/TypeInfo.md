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

- **[Prev Class](Text.md)**
- **[Next Class](UserDataHandler.md)**

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

**org.w3c.dom**

## **Interface TypeInfo**

-

  ------------------------------------------------------------------------

  **
  **

      public interface TypeInfo

  **The `TypeInfo` interface represent a type referenced from `Element` or `Attr` nodes, specified in the schemas associated with the document. The type is a pair of a namespace URI and name properties, and depends on the document's schema.**
  **If the document's schema is an XML DTD \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\], the values are computed as follows:**

  - **If this type is referenced from an `Attr` node, `typeNamespace` is `null` and `typeName` represents the \[attribute type\] property in the \[[XML Information Set](http://www.w3.org/TR/2001/REC-xml-infoset-20011024/)\] . If there is no declaration for the attribute, `typeName` is `null`.**
  - If this type is referenced from an `Element` node, the `typeNamespace` and `typeName` are `null`.

  If the document's schema is an XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , the values are computed as follows using the post-schema-validation infoset contributions (also called PSVI contributions):

  - If the **\[validity\]** property exists AND is *"invalid"* or *"notKnown"*: the {target namespace} and {name} properties of the declared type if available, otherwise `null`.

    **Note:** At the time of writing, the XML Schema specification does not require exposing the declared type. Thus, DOM implementations might choose not to provide type information if validity is not valid.

  - If the **\[validity\]** property exists and is *"valid"*:
    1.  If **\[member type definition\]** exists:
        1.  If {name} is not absent, then expose {name} and {target namespace} properties of the **\[member type definition\]** property;
        2.  Otherwise, expose the namespace and local name of the corresponding anonymous type name.
    2.  If the **\[type definition\]** property exists:
        1.  If {name} is not absent, then expose {name} and {target namespace} properties of the **\[type definition\]** property;
        2.  Otherwise, expose the namespace and local name of the corresponding anonymous type name.
    3.  If the **\[member type definition anonymous\]** exists:
        1.  If it is false, then expose **\[member type definition name\]** and **\[member type definition namespace\]** properties;
        2.  Otherwise, expose the namespace and local name of the corresponding anonymous type name.
    4.  If the **\[type definition anonymous\]** exists:
        1.  If it is false, then expose **\[type definition name\]** and **\[type definition namespace\]** properties;
        2.  Otherwise, expose the namespace and local name of the corresponding anonymous type name.

  **Note:** Other schema languages are outside the scope of the W3C and therefore should define how to represent their type systems using `TypeInfo`.

  See also the [Document Object Model (DOM) Level 3 Core Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107).

  Since:
  DOM Level 3

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                                                                                                                                                                                                                                                                                           |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `DERIVATION_EXTENSION`<br>If the document's schema is an XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , this constant represents the derivation by [extension](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/#key-typeExtension) if complex types are involved.                                                                                                                                 |
    | `static int`      | `DERIVATION_LIST`<br>If the document's schema is an XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , this constant represents the [list](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/#element-list) if simple types are involved.                                                                                                                                                               |
    | `static int`      | `DERIVATION_RESTRICTION`<br>If the document's schema is an XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , this constant represents the derivation by [restriction](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/#key-typeRestriction) if complex types are involved, or a [restriction](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/#element-restriction) if simple types are involved. |
    | `static int`      | `DERIVATION_UNION`<br>If the document's schema is an XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , this constant represents the [union](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/#element-union) if simple types are involved.                                                                                                                                                            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                               |
    |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getTypeName``()`<br>The name of a type declared for the associated element or attribute, or `null` if unknown.                                                                                      |
    | `java.lang.String` | `getTypeNamespace``()`<br>The namespace of the type declared for the associated element or attribute or `null` if the element does not have declaration or if no namespace information is available. |
    | `boolean`          | `isDerivedFrom``(java.lang.String typeNamespaceArg, java.lang.String typeNameArg, int derivationMethod)`<br>The method checks if this `TypeInfo` derives from the specified ancestor type.           |

<!-- -->

- - ### Field Detail

    - #### DERIVATION_RESTRICTION

          static final int DERIVATION_RESTRICTION

      If the document's schema is an XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , this constant represents the derivation by [restriction](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/#key-typeRestriction) if complex types are involved, or a [restriction](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/#element-restriction) if simple types are involved.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DERIVATION_EXTENSION

          static final int DERIVATION_EXTENSION

      If the document's schema is an XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , this constant represents the derivation by [extension](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/#key-typeExtension) if complex types are involved.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DERIVATION_UNION

          static final int DERIVATION_UNION

      If the document's schema is an XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , this constant represents the [union](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/#element-union) if simple types are involved.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DERIVATION_LIST

          static final int DERIVATION_LIST

      If the document's schema is an XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , this constant represents the [list](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/#element-list) if simple types are involved.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getTypeName

          java.lang.String getTypeName()

      The name of a type declared for the associated element or attribute, or `null` if unknown.

    <!-- -->

    - #### getTypeNamespace

          java.lang.String getTypeNamespace()

      The namespace of the type declared for the associated element or attribute or `null` if the element does not have declaration or if no namespace information is available.

    <!-- -->

    - #### isDerivedFrom

          boolean isDerivedFrom(java.lang.String typeNamespaceArg,
                                java.lang.String typeNameArg,
                                int derivationMethod)

      The method checks if this `TypeInfo` derives from the specified ancestor type.
      Parameters:
      `typeNamespaceArg` - the namespace of the ancestor type.

      `typeNameArg` - the name of the ancestor type.

      `derivationMethod` - the type of derivation and conditions applied between two types, as described in the list of constants provided in this interface. Note that those constants:

      - are only defined if the document's schema is an XML Schema;
      - could be combined if XML Schema types are involved.
      - `TypeInfo.DERIVATION_EXTENSION` only applies to XML Schema complex types.

      The value `0x00000000` represents any kind of derivation method.

      Returns:
      `true` if the specified type is an ancestor according to the derivation parameter, `false` otherwise. If the document's schema is a DTD or no schema is associated with the document, this method will always return `false`.

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

- **[Prev Class](Text.md)**
- **[Next Class](UserDataHandler.md)**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
