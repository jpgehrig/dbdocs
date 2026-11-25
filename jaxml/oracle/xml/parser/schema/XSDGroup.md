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

- **[Prev Class](XSDException.md)**
- **[Next Class](XSDIdentity.md)**

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

## **Class XSDGroup**

- **java.lang.Object**

- - **[oracle.xml.parser.schema.XSDNode](XSDNode.md)**

  - - **oracle.xml.parser.schema.XSDGroup**

<!-- -->

- **All Implemented Interfaces:**
  **[XSDConstantValues](XSDConstantValues.md), [XSDParticleNode](XSDParticleNode.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XSDGroup
      extends XSDNode
      implements XSDParticleNode

  **This class represents Schema model groups: \<xsd:group\>, \<xsd:all\>, \<xsd:sequence\>, and \<xsd:choice\>.**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface oracle.xml.parser.schema.[XSDConstantValues](XSDConstantValues.md)**

      **[`_abstract`](XSDConstantValues.md)`, `[`_all`](XSDConstantValues.md)`, `[`_annotation`](XSDConstantValues.md)`, `[`_any`](XSDConstantValues.md)`, `[`_anyAttribute`](XSDConstantValues.md)`, `[`_anySimpleType`](XSDConstantValues.md)`, `[`_anyType`](XSDConstantValues.md)`, `[`_appinfo`](XSDConstantValues.md)`, `[`_attrFormDefault`](XSDConstantValues.md)`, `[`_attribute`](XSDConstantValues.md)`, `[`_attributeGroup`](XSDConstantValues.md)`, `[`_attrTag`](XSDConstantValues.md)`, `[`_base`](XSDConstantValues.md)`, `[`_block`](XSDConstantValues.md)`, `[`_blockDefault`](XSDConstantValues.md)`, `[`_choice`](XSDConstantValues.md)`, `[`_complexContent`](XSDConstantValues.md)`, `[`_complexType`](XSDConstantValues.md)`, `[`_content`](XSDConstantValues.md)`, `[`_default`](XSDConstantValues.md)`, `[`_derivedBy`](XSDConstantValues.md)`, `[`_documentation`](XSDConstantValues.md)`, `[`_element`](XSDConstantValues.md)`, `[`_elementOnly`](XSDConstantValues.md)`, `[`_elemFormDefault`](XSDConstantValues.md)`, `[`_empty`](XSDConstantValues.md)`, `[`_enumeration`](XSDConstantValues.md)`, `[`_equivClass`](XSDConstantValues.md)`, `[`_extension`](XSDConstantValues.md)`, `[`_false`](XSDConstantValues.md)`, `[`_field`](XSDConstantValues.md)`, `[`_final`](XSDConstantValues.md)`, `[`_finalDefault`](XSDConstantValues.md)`, `[`_fixed`](XSDConstantValues.md)`, `[`_form`](XSDConstantValues.md)`, `[`_group`](XSDConstantValues.md)`, `[`_id`](XSDConstantValues.md)`, `[`_import`](XSDConstantValues.md)`, `[`_include`](XSDConstantValues.md)`, `[`_itemType`](XSDConstantValues.md)`, `[`_key`](XSDConstantValues.md)`, `[`_keyref`](XSDConstantValues.md)`, `[`_lax`](XSDConstantValues.md)`, `[`_list`](XSDConstantValues.md)`, `[`_maxOccurs`](XSDConstantValues.md)`, `[`_memberTypes`](XSDConstantValues.md)`, `[`_minOccurs`](XSDConstantValues.md)`, `[`_mixed`](XSDConstantValues.md)`, `[`_nall`](XSDConstantValues.md)`, `[`_name`](XSDConstantValues.md)`, `[`_namespace`](XSDConstantValues.md)`, `[`_nil`](XSDConstantValues.md)`, `[`_nillable`](XSDConstantValues.md)`, `[`_nnany`](XSDConstantValues.md)`, `[`_nnlist`](XSDConstantValues.md)`, `[`_nnlocal`](XSDConstantValues.md)`, `[`_nnother`](XSDConstantValues.md)`, `[`_nntargetNS`](XSDConstantValues.md)`, `[`_noNSSchemaLocation`](XSDConstantValues.md)`, `[`_notation`](XSDConstantValues.md)`, `[`_null`](XSDConstantValues.md)`, `[`_nullable`](XSDConstantValues.md)`, `[`_optional`](XSDConstantValues.md)`, `[`_pattern`](XSDConstantValues.md)`, `[`_processContents`](XSDConstantValues.md)`, `[`_prohibited`](XSDConstantValues.md)`, `[`_publicid`](XSDConstantValues.md)`, `[`_qualified`](XSDConstantValues.md)`, `[`_redefine`](XSDConstantValues.md)`, `[`_ref`](XSDConstantValues.md)`, `[`_refer`](XSDConstantValues.md)`, `[`_required`](XSDConstantValues.md)`, `[`_restriction`](XSDConstantValues.md)`, `[`_restrictions`](XSDConstantValues.md)`, `[`_schemaLocation`](XSDConstantValues.md)`, `[`_selector`](XSDConstantValues.md)`, `[`_sequence`](XSDConstantValues.md)`, `[`_simpleContent`](XSDConstantValues.md)`, `[`_simpleType`](XSDConstantValues.md)`, `[`_skip`](XSDConstantValues.md)`, `[`_strict`](XSDConstantValues.md)`, `[`_substitution`](XSDConstantValues.md)`, `[`_substitutionGrp`](XSDConstantValues.md)`, `[`_systemid`](XSDConstantValues.md)`, `[`_targetNS`](XSDConstantValues.md)`, `[`_textOnly`](XSDConstantValues.md)`, `[`_this`](XSDConstantValues.md)`, `[`_true`](XSDConstantValues.md)`, `[`_type`](XSDConstantValues.md)`, `[`_undef`](XSDConstantValues.md)`, `[`_union`](XSDConstantValues.md)`, `[`_unique`](XSDConstantValues.md)`, `[`_unqualified`](XSDConstantValues.md)`, `[`_use`](XSDConstantValues.md)`, `[`_value`](XSDConstantValues.md)`, `[`_version`](XSDConstantValues.md)`, `[`_xmlns`](XSDConstantValues.md)`, `[`ABSENT_NS`](XSDConstantValues.md)`, `[`ACCEPTED`](XSDConstantValues.md)`, `[`ALL`](XSDConstantValues.md)`, `[`ANNOTATION`](XSDConstantValues.md)`, `[`ANY`](XSDConstantValues.md)`, `[`ANY_ATTRIBUTE`](XSDConstantValues.md)`, `[`ANY_NODE`](XSDConstantValues.md)`, `[`ATTRIBUTE`](XSDConstantValues.md)`, `[`ATTRIBUTE_GROUP`](XSDConstantValues.md)`, `[`AUTO_VALIDATION`](XSDConstantValues.md)`, `[`BASE_RESOLVED`](XSDConstantValues.md)`, `[`BASE_UNRESOLVED`](XSDConstantValues.md)`, `[`BASE_URL`](XSDConstantValues.md)`, `[`BUILD_FAIL`](XSDConstantValues.md)`, `[`CHOICE`](XSDConstantValues.md)`, `[`CIRCULAR_SUBST`](XSDConstantValues.md)`, `[`CONFLICIT_FACET`](XSDConstantValues.md)`, `[`constName`](XSDConstantValues.md)`, `[`DATATYPE`](XSDConstantValues.md)`, `[`DEEP_VALIDATION`](XSDConstantValues.md)`, `[`derivationBlock`](XSDConstantValues.md)`, `[`DONE`](XSDConstantValues.md)`, `[`DUPLICATE_DEF`](XSDConstantValues.md)`, `[`duplicateId`](XSDConstantValues.md)`, `[`ELEMENT`](XSDConstantValues.md)`, `[`ELEMENT_CHILD`](XSDConstantValues.md)`, `[`ELEMENT_ONLY`](XSDConstantValues.md)`, `[`elemNotNullable`](XSDConstantValues.md)`, `[`EMPTY`](XSDConstantValues.md)`, `[`ENTITY_RESOLVER`](XSDConstantValues.md)`, `[`EQUIV_RESOLVED`](XSDConstantValues.md)`, `[`EQUIV_UNRESOLVED`](XSDConstantValues.md)`, `[`ERROR`](XSDConstantValues.md)`, `[`EXTENTION`](XSDConstantValues.md)`, `[`FACET_CHILD`](XSDConstantValues.md)`, `[`FAKE_ATTR`](XSDConstantValues.md)`, `[`FAKE_NODE`](XSDConstantValues.md)`, `[`FIXED_SCHEMA`](XSDConstantValues.md)`, `[`GROUP`](XSDConstantValues.md)`, `[`IABSTRACT`](XSDConstantValues.md)`, `[`IBLOCKEXT`](XSDConstantValues.md)`, `[`IBLOCKRST`](XSDConstantValues.md)`, `[`IBLOCKSUB`](XSDConstantValues.md)`, `[`IDENTITY_ERROR`](XSDConstantValues.md)`, `[`IDENTITY_KEY`](XSDConstantValues.md)`, `[`IDENTITY_KEYREF`](XSDConstantValues.md)`, `[`IDENTITY_UNIQUE`](XSDConstantValues.md)`, `[`IFINALEXT`](XSDConstantValues.md)`, `[`IFINALLIST`](XSDConstantValues.md)`, `[`IFINALRST`](XSDConstantValues.md)`, `[`IFINALUNION`](XSDConstantValues.md)`, `[`IMPORT`](XSDConstantValues.md)`, `[`INCLUDE`](XSDConstantValues.md)`, `[`INCORRECT_ATTR`](XSDConstantValues.md)`, `[`INCORRECT_ELEM`](XSDConstantValues.md)`, `[`INFINITY`](XSDConstantValues.md)`, `[`INTERNAL_ERROR`](XSDConstantValues.md)`, `[`INVALID_DATE`](XSDConstantValues.md)`, `[`INVALID_DATETIME`](XSDConstantValues.md)`, `[`INVALID_DERIVATION`](XSDConstantValues.md)`, `[`INVALID_FACET`](XSDConstantValues.md)`, `[`INVALID_FACET_VALUE`](XSDConstantValues.md)`, `[`INVALID_NOTATION`](XSDConstantValues.md)`, `[`INVALID_REGEX`](XSDConstantValues.md)`, `[`INVALID_SCHEMA_NS`](XSDConstantValues.md)`, `[`INVALID_TIME`](XSDConstantValues.md)`, `[`INVALID_TYPE_VALUE`](XSDConstantValues.md)`, `[`invalidAttr`](XSDConstantValues.md)`, `[`invalidAttrVal`](XSDConstantValues.md)`, `[`invalidChars`](XSDConstantValues.md)`, `[`invalidElem`](XSDConstantValues.md)`, `[`invalidFixedChars`](XSDConstantValues.md)`, `[`invalidNS`](XSDConstantValues.md)`, `[`invalidPrefix`](XSDConstantValues.md)`, `[`invalidProperty`](XSDConstantValues.md)`, `[`invalidRef`](XSDConstantValues.md)`, `[`invalidSubstitution`](XSDConstantValues.md)`, `[`invalidTargetNS`](XSDConstantValues.md)`, `[`LAX_VALIDATION`](XSDConstantValues.md)`, `[`MISSING_NS`](XSDConstantValues.md)`, `[`missingAttr`](XSDConstantValues.md)`, `[`MIXED`](XSDConstantValues.md)`, `[`NEW_STATE`](XSDConstantValues.md)`, `[`NO_CHILD`](XSDConstantValues.md)`, `[`noDefinition`](XSDConstantValues.md)`, `[`NOT_DONE`](XSDConstantValues.md)`, `[`NOTATION`](XSDConstantValues.md)`, `[`notComplete`](XSDConstantValues.md)`, `[`notSubstitutable`](XSDConstantValues.md)`, `[`notSubTypeOf`](XSDConstantValues.md)`, `[`NS_CONFLICT`](XSDConstantValues.md)`, `[`NS_DIF_SPECIFIED`](XSDConstantValues.md)`, `[`NS_NOT_ALLOWED`](XSDConstantValues.md)`, `[`NS_NOT_EXPECTED`](XSDConstantValues.md)`, `[`NS_NOT_SAME`](XSDConstantValues.md)`, `[`NS_RESOLVER`](XSDConstantValues.md)`, `[`REDEFINE`](XSDConstantValues.md)`, `[`REF_RESOLVED`](XSDConstantValues.md)`, `[`REF_UNRESOLVED`](XSDConstantValues.md)`, `[`RESTRICTION`](XSDConstantValues.md)`, `[`ROOT_ELEMENT`](XSDConstantValues.md)`, `[`ROOT_NODE`](XSDConstantValues.md)`, `[`ROOT_TYPE`](XSDConstantValues.md)`, `[`SCHEMA_NS`](XSDConstantValues.md)`, `[`SCHEMA_RESOLVER`](XSDConstantValues.md)`, `[`SEQ`](XSDConstantValues.md)`, `[`STRICT_VALIDATION`](XSDConstantValues.md)`, `[`TEXT_ONLY`](XSDConstantValues.md)`, `[`TOP_LEVEL`](XSDConstantValues.md)`, `[`TYPE`](XSDConstantValues.md)`, `[`TYPE_RESOLVED`](XSDConstantValues.md)`, `[`TYPE_UNRESOLVED`](XSDConstantValues.md)`, `[`UNDEF`](XSDConstantValues.md)`, `[`unexpectedAttr`](XSDConstantValues.md)`, `[`unexpectedElem`](XSDConstantValues.md)`, `[`VALIDATION_MODE`](XSDConstantValues.md)`, `[`VIOLATE_FACET`](XSDConstantValues.md)`, `[`XSDRECNS`](XSDConstantValues.md)`, `[`XSDRECTYPENS`](XSDConstantValues.md)`, `[`XSIRECNS`](XSDConstantValues.md)`, `[`XSITYPE_ABSENT`](XSDConstantValues.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                             |
    |--------------------|----------------------------------------------------------------------------------------------------|
    | `int`              | `getMaxOccurs``()`<br>Get the maxOccurs maximum occurrence for this content particle.              |
    | `int`              | `getMinOccurs``()`<br>Get the minOccurs min occurrence for this content particle.                  |
    | `java.util.Vector` | `getNodeVector``()`<br>Get the particles of the group stored in nodeVector                         |
    | `int`              | `getOrder``()`<br>Get the composite type - ALL, SEQUENCE, CHOICE                                   |
    | `java.lang.String` | `getRefLocalname``()`<br>Get the refernce local name of the node                                   |
    | `java.lang.String` | `getRefNamespace``()`<br>Get the refernce namespace of the node                                    |
    | `boolean`          | `isEmptiable``()`                                                                                  |
    | `void`             | `setMaxOccurs``(int maxOccurs)`<br>Set the maxOccurs maximum occurrence for this content particle. |
    | `void`             | `setMinOccurs``(int minOccurs)`<br>Set the minOccurs min occurrence for this content particle.     |

    - ### Methods inherited from class oracle.xml.parser.schema.[XSDNode](XSDNode.md)

      [`getName`](XSDNode.md)`, `[`getNodeType`](XSDNode.md)`, `[`getOwnerSchema`](XSDNode.md)`, `[`getTargetNS`](XSDNode.md)`, `[`isNodeType`](XSDNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getRefNamespace

          public java.lang.String getRefNamespace()

      Get the refernce namespace of the node

    <!-- -->

    - #### getRefLocalname

          public java.lang.String getRefLocalname()

      Get the refernce local name of the node
      Overrides:
      [`getRefLocalname`](XSDNode.md) in class [`XSDNode`](XSDNode.md)

    <!-- -->

    - #### getNodeVector

          public java.util.Vector getNodeVector()

      Get the particles of the group stored in nodeVector
      Returns:
      nodeVector

    <!-- -->

    - #### getMinOccurs

          public int getMinOccurs()

      Get the minOccurs min occurrence for this content particle. Valid values are from 0 to AS_UNBOUNDED.
      Specified by:
      [`getMinOccurs`](XSDParticleNode.md) in interface [`XSDParticleNode`](XSDParticleNode.md)

    <!-- -->

    - #### getMaxOccurs

          public int getMaxOccurs()

      Get the maxOccurs maximum occurrence for this content particle. Valid values are from 0 to AS_UNBOUNDED.
      Specified by:
      [`getMaxOccurs`](XSDParticleNode.md) in interface [`XSDParticleNode`](XSDParticleNode.md)

    <!-- -->

    - #### setMinOccurs

          public void setMinOccurs(int minOccurs)

      Set the minOccurs min occurrence for this content particle. Valid values are from 0 to AS_UNBOUNDED.
      Specified by:
      [`setMinOccurs`](XSDParticleNode.md) in interface [`XSDParticleNode`](XSDParticleNode.md)

    <!-- -->

    - #### setMaxOccurs

          public void setMaxOccurs(int maxOccurs)

      Set the maxOccurs maximum occurrence for this content particle. Valid values are from 0 to AS_UNBOUNDED.
      Specified by:
      [`setMaxOccurs`](XSDParticleNode.md) in interface [`XSDParticleNode`](XSDParticleNode.md)

    <!-- -->

    - #### getOrder

          public int getOrder()

      Get the composite type - ALL, SEQUENCE, CHOICE
      Returns:
      order

    <!-- -->

    - #### isEmptiable

          public boolean isEmptiable()

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

- **[Prev Class](XSDException.md)**
- **[Next Class](XSDIdentity.md)**

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
