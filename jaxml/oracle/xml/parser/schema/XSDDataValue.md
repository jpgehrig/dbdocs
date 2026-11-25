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

- **[Prev Class](XSDConstrainingFacet.md)**
- **[Next Class](XSDElement.md)**

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

## **Class XSDDataValue**

- **java.lang.Object**

- - **oracle.xml.parser.schema.XSDDataValue**

<!-- -->

- **All Implemented Interfaces:**
  **[XSDConstantValues](XSDConstantValues.md), [XSDTypeConstants](XSDTypeConstants.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XSDDataValue
      extends java.lang.Object
      implements XSDTypeConstants, XSDConstantValues

  **Class used to represent a value as per XML Schema Part 2, simple types.**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface oracle.xml.parser.schema.[XSDTypeConstants](XSDTypeConstants.md)**

      **[`_atomic`](XSDTypeConstants.md)`, `[`_base64`](XSDTypeConstants.md)`, `[`_collapse`](XSDTypeConstants.md)`, `[`_hex`](XSDTypeConstants.md)`, `[`_preserve`](XSDTypeConstants.md)`, `[`_replace`](XSDTypeConstants.md)`, `[`ANY_SIMPLE`](XSDTypeConstants.md)`, `[`ANY_URI`](XSDTypeConstants.md)`, `[`BASE64_BINARY`](XSDTypeConstants.md)`, `[`BINARY`](XSDTypeConstants.md)`, `[`BOOLEAN`](XSDTypeConstants.md)`, `[`BYTE`](XSDTypeConstants.md)`, `[`CDATA`](XSDTypeConstants.md)`, `[`CENTURY`](XSDTypeConstants.md)`, `[`DATE`](XSDTypeConstants.md)`, `[`DATE_TIME`](XSDTypeConstants.md)`, `[`DAYTIME_DURATION`](XSDTypeConstants.md)`, `[`DECIMAL`](XSDTypeConstants.md)`, `[`DOUBLE`](XSDTypeConstants.md)`, `[`DURATION`](XSDTypeConstants.md)`, `[`ENCODING`](XSDTypeConstants.md)`, `[`ENTITIES`](XSDTypeConstants.md)`, `[`ENTITY`](XSDTypeConstants.md)`, `[`ENUMERATION`](XSDTypeConstants.md)`, `[`fDAYTIME`](XSDTypeConstants.md)`, `[`fFINITE`](XSDTypeConstants.md)`, `[`fID`](XSDTypeConstants.md)`, `[`fIDREF`](XSDTypeConstants.md)`, `[`fINTEGER`](XSDTypeConstants.md)`, `[`FLOAT`](XSDTypeConstants.md)`, `[`fNUMERIC`](XSDTypeConstants.md)`, `[`fORDERED`](XSDTypeConstants.md)`, `[`FRACTION_DIGITS`](XSDTypeConstants.md)`, `[`fYEARMONTH`](XSDTypeConstants.md)`, `[`GDAY`](XSDTypeConstants.md)`, `[`GMONTH`](XSDTypeConstants.md)`, `[`GMONTH_DAY`](XSDTypeConstants.md)`, `[`GYEAR`](XSDTypeConstants.md)`, `[`GYEAR_MONTH`](XSDTypeConstants.md)`, `[`HEX_BINARY`](XSDTypeConstants.md)`, `[`iANY_SIMPLE`](XSDTypeConstants.md)`, `[`iANY_URI`](XSDTypeConstants.md)`, `[`iBASE64_BINARY`](XSDTypeConstants.md)`, `[`iBOOLEAN`](XSDTypeConstants.md)`, `[`iBYTE`](XSDTypeConstants.md)`, `[`ID`](XSDTypeConstants.md)`, `[`iDATE`](XSDTypeConstants.md)`, `[`iDATE_TIME`](XSDTypeConstants.md)`, `[`iDAYTIME_DURATION`](XSDTypeConstants.md)`, `[`iDECIMAL`](XSDTypeConstants.md)`, `[`iDOUBLE`](XSDTypeConstants.md)`, `[`IDREF`](XSDTypeConstants.md)`, `[`IDREFS`](XSDTypeConstants.md)`, `[`iDUMMY`](XSDTypeConstants.md)`, `[`iDURATION`](XSDTypeConstants.md)`, `[`iENTITIES`](XSDTypeConstants.md)`, `[`iENTITY`](XSDTypeConstants.md)`, `[`iENUMERATION`](XSDTypeConstants.md)`, `[`iFLOAT`](XSDTypeConstants.md)`, `[`iFRACTION_DIGITS`](XSDTypeConstants.md)`, `[`iGDAY`](XSDTypeConstants.md)`, `[`iGMONTH`](XSDTypeConstants.md)`, `[`iGMONTH_DAY`](XSDTypeConstants.md)`, `[`iGYEAR`](XSDTypeConstants.md)`, `[`iGYEAR_MONTH`](XSDTypeConstants.md)`, `[`iHEX_BINARY`](XSDTypeConstants.md)`, `[`iID`](XSDTypeConstants.md)`, `[`iIDREF`](XSDTypeConstants.md)`, `[`iIDREFS`](XSDTypeConstants.md)`, `[`iINT`](XSDTypeConstants.md)`, `[`iINTEGER`](XSDTypeConstants.md)`, `[`iLANGUAGE`](XSDTypeConstants.md)`, `[`iLENGTH`](XSDTypeConstants.md)`, `[`iLONG`](XSDTypeConstants.md)`, `[`iMAXEXCLUSIVE`](XSDTypeConstants.md)`, `[`iMAXINCLUSIVE`](XSDTypeConstants.md)`, `[`iMAXLENGTH`](XSDTypeConstants.md)`, `[`iMINEXCLUSIVE`](XSDTypeConstants.md)`, `[`iMININCLUSIVE`](XSDTypeConstants.md)`, `[`iMINLENGTH`](XSDTypeConstants.md)`, `[`iN_STRING`](XSDTypeConstants.md)`, `[`iNAME`](XSDTypeConstants.md)`, `[`iNCNAME`](XSDTypeConstants.md)`, `[`iNEGATIVE_INTEGER`](XSDTypeConstants.md)`, `[`iNMTOKEN`](XSDTypeConstants.md)`, `[`iNMTOKENS`](XSDTypeConstants.md)`, `[`iNON_NEGATIVE_INTEGER`](XSDTypeConstants.md)`, `[`iNON_POSITIVE_INTEGER`](XSDTypeConstants.md)`, `[`iNOTATION`](XSDTypeConstants.md)`, `[`INT`](XSDTypeConstants.md)`, `[`INTEGER_STR`](XSDTypeConstants.md)`, `[`iPATTERN`](XSDTypeConstants.md)`, `[`iPOSITIVE_INTEGER`](XSDTypeConstants.md)`, `[`iQNAME`](XSDTypeConstants.md)`, `[`iSHORT`](XSDTypeConstants.md)`, `[`iSTRING`](XSDTypeConstants.md)`, `[`iTIME`](XSDTypeConstants.md)`, `[`iTOKEN`](XSDTypeConstants.md)`, `[`iTOTAL_DIGITS`](XSDTypeConstants.md)`, `[`iUNSIGNED_BYTE`](XSDTypeConstants.md)`, `[`iUNSIGNED_INT`](XSDTypeConstants.md)`, `[`iUNSIGNED_LONG`](XSDTypeConstants.md)`, `[`iUNSIGNED_SHORT`](XSDTypeConstants.md)`, `[`iWHITESPACE`](XSDTypeConstants.md)`, `[`iYEARMONTH_DURATION`](XSDTypeConstants.md)`, `[`LANGUAGE`](XSDTypeConstants.md)`, `[`LENGTH`](XSDTypeConstants.md)`, `[`LONG`](XSDTypeConstants.md)`, `[`MAXEXCLUSIVE`](XSDTypeConstants.md)`, `[`MAXINCLUSIVE`](XSDTypeConstants.md)`, `[`MAXLENGTH`](XSDTypeConstants.md)`, `[`MINEXCLUSIVE`](XSDTypeConstants.md)`, `[`MININCLUSIVE`](XSDTypeConstants.md)`, `[`MINLENGTH`](XSDTypeConstants.md)`, `[`MONTH`](XSDTypeConstants.md)`, `[`N_STRING`](XSDTypeConstants.md)`, `[`NAME`](XSDTypeConstants.md)`, `[`nBUILTIN`](XSDTypeConstants.md)`, `[`NCNAME`](XSDTypeConstants.md)`, `[`NEGATIVE_INTEGER`](XSDTypeConstants.md)`, `[`nFacets`](XSDTypeConstants.md)`, `[`NMTOKEN`](XSDTypeConstants.md)`, `[`NMTOKENS`](XSDTypeConstants.md)`, `[`NON_NEGATIVE_INTEGER`](XSDTypeConstants.md)`, `[`NON_POSITIVE_INTEGER`](XSDTypeConstants.md)`, `[`nPRIMITIVE`](XSDTypeConstants.md)`, `[`PATTERN`](XSDTypeConstants.md)`, `[`PERIOD`](XSDTypeConstants.md)`, `[`POSITIVE_INTEGER`](XSDTypeConstants.md)`, `[`PRECISION`](XSDTypeConstants.md)`, `[`QNAME`](XSDTypeConstants.md)`, `[`RECURRING_DATE`](XSDTypeConstants.md)`, `[`RECURRING_DAY`](XSDTypeConstants.md)`, `[`RECURRING_DURATION`](XSDTypeConstants.md)`, `[`SCALE`](XSDTypeConstants.md)`, `[`sFacets`](XSDTypeConstants.md)`, `[`SHORT`](XSDTypeConstants.md)`, `[`SNOTATION`](XSDTypeConstants.md)`, `[`STRING`](XSDTypeConstants.md)`, `[`sTypes`](XSDTypeConstants.md)`, `[`TIME`](XSDTypeConstants.md)`, `[`TIME_DURATION`](XSDTypeConstants.md)`, `[`TIME_INSTANT`](XSDTypeConstants.md)`, `[`TIME_PERIOD`](XSDTypeConstants.md)`, `[`TOKEN`](XSDTypeConstants.md)`, `[`TOTAL_DIGITS`](XSDTypeConstants.md)`, `[`UNSIGNED_BYTE`](XSDTypeConstants.md)`, `[`UNSIGNED_INT`](XSDTypeConstants.md)`, `[`UNSIGNED_LONG`](XSDTypeConstants.md)`, `[`UNSIGNED_SHORT`](XSDTypeConstants.md)`, `[`UNTYPED_ATOMIC`](XSDTypeConstants.md)`, `[`URI_REFERENCE`](XSDTypeConstants.md)`, `[`WHITESPACE`](XSDTypeConstants.md)`, `[`YEAR`](XSDTypeConstants.md)`, `[`YEARMONTH_DURATION`](XSDTypeConstants.md)**

    <!-- -->

    -

      ### **Fields inherited from interface oracle.xml.parser.schema.[XSDConstantValues](XSDConstantValues.md)**

      **[`_abstract`](XSDConstantValues.md)`, `[`_all`](XSDConstantValues.md)`, `[`_annotation`](XSDConstantValues.md)`, `[`_any`](XSDConstantValues.md)`, `[`_anyAttribute`](XSDConstantValues.md)`, `[`_anySimpleType`](XSDConstantValues.md)`, `[`_anyType`](XSDConstantValues.md)`, `[`_appinfo`](XSDConstantValues.md)`, `[`_attrFormDefault`](XSDConstantValues.md)`, `[`_attribute`](XSDConstantValues.md)`, `[`_attributeGroup`](XSDConstantValues.md)`, `[`_attrTag`](XSDConstantValues.md)`, `[`_base`](XSDConstantValues.md)`, `[`_block`](XSDConstantValues.md)`, `[`_blockDefault`](XSDConstantValues.md)`, `[`_choice`](XSDConstantValues.md)`, `[`_complexContent`](XSDConstantValues.md)`, `[`_complexType`](XSDConstantValues.md)`, `[`_content`](XSDConstantValues.md)`, `[`_default`](XSDConstantValues.md)`, `[`_derivedBy`](XSDConstantValues.md)`, `[`_documentation`](XSDConstantValues.md)`, `[`_element`](XSDConstantValues.md)`, `[`_elementOnly`](XSDConstantValues.md)`, `[`_elemFormDefault`](XSDConstantValues.md)`, `[`_empty`](XSDConstantValues.md)`, `[`_enumeration`](XSDConstantValues.md)`, `[`_equivClass`](XSDConstantValues.md)`, `[`_extension`](XSDConstantValues.md)`, `[`_field`](XSDConstantValues.md)`, `[`_final`](XSDConstantValues.md)`, `[`_finalDefault`](XSDConstantValues.md)`, `[`_fixed`](XSDConstantValues.md)`, `[`_form`](XSDConstantValues.md)`, `[`_group`](XSDConstantValues.md)`, `[`_id`](XSDConstantValues.md)`, `[`_import`](XSDConstantValues.md)`, `[`_include`](XSDConstantValues.md)`, `[`_itemType`](XSDConstantValues.md)`, `[`_key`](XSDConstantValues.md)`, `[`_keyref`](XSDConstantValues.md)`, `[`_lax`](XSDConstantValues.md)`, `[`_list`](XSDConstantValues.md)`, `[`_maxOccurs`](XSDConstantValues.md)`, `[`_memberTypes`](XSDConstantValues.md)`, `[`_minOccurs`](XSDConstantValues.md)`, `[`_mixed`](XSDConstantValues.md)`, `[`_nall`](XSDConstantValues.md)`, `[`_name`](XSDConstantValues.md)`, `[`_namespace`](XSDConstantValues.md)`, `[`_nil`](XSDConstantValues.md)`, `[`_nillable`](XSDConstantValues.md)`, `[`_nnany`](XSDConstantValues.md)`, `[`_nnlist`](XSDConstantValues.md)`, `[`_nnlocal`](XSDConstantValues.md)`, `[`_nnother`](XSDConstantValues.md)`, `[`_nntargetNS`](XSDConstantValues.md)`, `[`_noNSSchemaLocation`](XSDConstantValues.md)`, `[`_notation`](XSDConstantValues.md)`, `[`_null`](XSDConstantValues.md)`, `[`_nullable`](XSDConstantValues.md)`, `[`_optional`](XSDConstantValues.md)`, `[`_pattern`](XSDConstantValues.md)`, `[`_processContents`](XSDConstantValues.md)`, `[`_prohibited`](XSDConstantValues.md)`, `[`_publicid`](XSDConstantValues.md)`, `[`_qualified`](XSDConstantValues.md)`, `[`_redefine`](XSDConstantValues.md)`, `[`_ref`](XSDConstantValues.md)`, `[`_refer`](XSDConstantValues.md)`, `[`_required`](XSDConstantValues.md)`, `[`_restriction`](XSDConstantValues.md)`, `[`_restrictions`](XSDConstantValues.md)`, `[`_schemaLocation`](XSDConstantValues.md)`, `[`_selector`](XSDConstantValues.md)`, `[`_sequence`](XSDConstantValues.md)`, `[`_simpleContent`](XSDConstantValues.md)`, `[`_simpleType`](XSDConstantValues.md)`, `[`_skip`](XSDConstantValues.md)`, `[`_strict`](XSDConstantValues.md)`, `[`_substitution`](XSDConstantValues.md)`, `[`_substitutionGrp`](XSDConstantValues.md)`, `[`_systemid`](XSDConstantValues.md)`, `[`_targetNS`](XSDConstantValues.md)`, `[`_textOnly`](XSDConstantValues.md)`, `[`_this`](XSDConstantValues.md)`, `[`_type`](XSDConstantValues.md)`, `[`_undef`](XSDConstantValues.md)`, `[`_union`](XSDConstantValues.md)`, `[`_unique`](XSDConstantValues.md)`, `[`_unqualified`](XSDConstantValues.md)`, `[`_use`](XSDConstantValues.md)`, `[`_value`](XSDConstantValues.md)`, `[`_version`](XSDConstantValues.md)`, `[`_xmlns`](XSDConstantValues.md)`, `[`ABSENT_NS`](XSDConstantValues.md)`, `[`ACCEPTED`](XSDConstantValues.md)`, `[`ALL`](XSDConstantValues.md)`, `[`ANNOTATION`](XSDConstantValues.md)`, `[`ANY`](XSDConstantValues.md)`, `[`ANY_ATTRIBUTE`](XSDConstantValues.md)`, `[`ANY_NODE`](XSDConstantValues.md)`, `[`ATTRIBUTE`](XSDConstantValues.md)`, `[`ATTRIBUTE_GROUP`](XSDConstantValues.md)`, `[`AUTO_VALIDATION`](XSDConstantValues.md)`, `[`BASE_RESOLVED`](XSDConstantValues.md)`, `[`BASE_UNRESOLVED`](XSDConstantValues.md)`, `[`BASE_URL`](XSDConstantValues.md)`, `[`BUILD_FAIL`](XSDConstantValues.md)`, `[`CHOICE`](XSDConstantValues.md)`, `[`CIRCULAR_SUBST`](XSDConstantValues.md)`, `[`CONFLICIT_FACET`](XSDConstantValues.md)`, `[`constName`](XSDConstantValues.md)`, `[`DATATYPE`](XSDConstantValues.md)`, `[`DEEP_VALIDATION`](XSDConstantValues.md)`, `[`derivationBlock`](XSDConstantValues.md)`, `[`DONE`](XSDConstantValues.md)`, `[`DUPLICATE_DEF`](XSDConstantValues.md)`, `[`duplicateId`](XSDConstantValues.md)`, `[`ELEMENT`](XSDConstantValues.md)`, `[`ELEMENT_CHILD`](XSDConstantValues.md)`, `[`ELEMENT_ONLY`](XSDConstantValues.md)`, `[`elemNotNullable`](XSDConstantValues.md)`, `[`EMPTY`](XSDConstantValues.md)`, `[`ENTITY_RESOLVER`](XSDConstantValues.md)`, `[`EQUIV_RESOLVED`](XSDConstantValues.md)`, `[`EQUIV_UNRESOLVED`](XSDConstantValues.md)`, `[`ERROR`](XSDConstantValues.md)`, `[`EXTENTION`](XSDConstantValues.md)`, `[`FACET_CHILD`](XSDConstantValues.md)`, `[`FAKE_ATTR`](XSDConstantValues.md)`, `[`FAKE_NODE`](XSDConstantValues.md)`, `[`FIXED_SCHEMA`](XSDConstantValues.md)`, `[`GROUP`](XSDConstantValues.md)`, `[`IABSTRACT`](XSDConstantValues.md)`, `[`IBLOCKEXT`](XSDConstantValues.md)`, `[`IBLOCKRST`](XSDConstantValues.md)`, `[`IBLOCKSUB`](XSDConstantValues.md)`, `[`IDENTITY_ERROR`](XSDConstantValues.md)`, `[`IDENTITY_KEY`](XSDConstantValues.md)`, `[`IDENTITY_KEYREF`](XSDConstantValues.md)`, `[`IDENTITY_UNIQUE`](XSDConstantValues.md)`, `[`IFINALEXT`](XSDConstantValues.md)`, `[`IFINALLIST`](XSDConstantValues.md)`, `[`IFINALRST`](XSDConstantValues.md)`, `[`IFINALUNION`](XSDConstantValues.md)`, `[`IMPORT`](XSDConstantValues.md)`, `[`INCLUDE`](XSDConstantValues.md)`, `[`INCORRECT_ATTR`](XSDConstantValues.md)`, `[`INCORRECT_ELEM`](XSDConstantValues.md)`, `[`INFINITY`](XSDConstantValues.md)`, `[`INTERNAL_ERROR`](XSDConstantValues.md)`, `[`INVALID_DATE`](XSDConstantValues.md)`, `[`INVALID_DATETIME`](XSDConstantValues.md)`, `[`INVALID_DERIVATION`](XSDConstantValues.md)`, `[`INVALID_FACET`](XSDConstantValues.md)`, `[`INVALID_FACET_VALUE`](XSDConstantValues.md)`, `[`INVALID_NOTATION`](XSDConstantValues.md)`, `[`INVALID_REGEX`](XSDConstantValues.md)`, `[`INVALID_SCHEMA_NS`](XSDConstantValues.md)`, `[`INVALID_TIME`](XSDConstantValues.md)`, `[`INVALID_TYPE_VALUE`](XSDConstantValues.md)`, `[`invalidAttr`](XSDConstantValues.md)`, `[`invalidAttrVal`](XSDConstantValues.md)`, `[`invalidChars`](XSDConstantValues.md)`, `[`invalidElem`](XSDConstantValues.md)`, `[`invalidFixedChars`](XSDConstantValues.md)`, `[`invalidNS`](XSDConstantValues.md)`, `[`invalidPrefix`](XSDConstantValues.md)`, `[`invalidProperty`](XSDConstantValues.md)`, `[`invalidRef`](XSDConstantValues.md)`, `[`invalidSubstitution`](XSDConstantValues.md)`, `[`invalidTargetNS`](XSDConstantValues.md)`, `[`LAX_VALIDATION`](XSDConstantValues.md)`, `[`MISSING_NS`](XSDConstantValues.md)`, `[`missingAttr`](XSDConstantValues.md)`, `[`MIXED`](XSDConstantValues.md)`, `[`NEW_STATE`](XSDConstantValues.md)`, `[`NO_CHILD`](XSDConstantValues.md)`, `[`noDefinition`](XSDConstantValues.md)`, `[`NOT_DONE`](XSDConstantValues.md)`, `[`NOTATION`](XSDConstantValues.md)`, `[`notComplete`](XSDConstantValues.md)`, `[`notSubstitutable`](XSDConstantValues.md)`, `[`notSubTypeOf`](XSDConstantValues.md)`, `[`NS_CONFLICT`](XSDConstantValues.md)`, `[`NS_DIF_SPECIFIED`](XSDConstantValues.md)`, `[`NS_NOT_ALLOWED`](XSDConstantValues.md)`, `[`NS_NOT_EXPECTED`](XSDConstantValues.md)`, `[`NS_NOT_SAME`](XSDConstantValues.md)`, `[`NS_RESOLVER`](XSDConstantValues.md)`, `[`REDEFINE`](XSDConstantValues.md)`, `[`REF_RESOLVED`](XSDConstantValues.md)`, `[`REF_UNRESOLVED`](XSDConstantValues.md)`, `[`RESTRICTION`](XSDConstantValues.md)`, `[`ROOT_ELEMENT`](XSDConstantValues.md)`, `[`ROOT_NODE`](XSDConstantValues.md)`, `[`ROOT_TYPE`](XSDConstantValues.md)`, `[`SCHEMA_NS`](XSDConstantValues.md)`, `[`SCHEMA_RESOLVER`](XSDConstantValues.md)`, `[`SEQ`](XSDConstantValues.md)`, `[`STRICT_VALIDATION`](XSDConstantValues.md)`, `[`TEXT_ONLY`](XSDConstantValues.md)`, `[`TOP_LEVEL`](XSDConstantValues.md)`, `[`TYPE`](XSDConstantValues.md)`, `[`TYPE_RESOLVED`](XSDConstantValues.md)`, `[`TYPE_UNRESOLVED`](XSDConstantValues.md)`, `[`UNDEF`](XSDConstantValues.md)`, `[`unexpectedAttr`](XSDConstantValues.md)`, `[`unexpectedElem`](XSDConstantValues.md)`, `[`VALIDATION_MODE`](XSDConstantValues.md)`, `[`VIOLATE_FACET`](XSDConstantValues.md)`, `[`XSDRECNS`](XSDConstantValues.md)`, `[`XSDRECTYPENS`](XSDConstantValues.md)`, `[`XSIRECNS`](XSDConstantValues.md)`, `[`XSITYPE_ABSENT`](XSDConstantValues.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                      |
    |------------------------------------------------------------------------------------------------------------------|
    | `XSDDataValue``(int type, java.lang.String lex)`<br>Construct a XSDDataValue based of the type and lexical value |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                   |
    |--------------------|----------------------------------------------------------------------------------------------------------|
    | `int`              | `compareTo``(XSDDataValue val)`<br>Compare two values return int -1 -- smaller, 0 -- equal, 1 -- greater |
    | `int`              | `getLength``()`<br>Gets the length of STRING/BINARY value return int length                              |
    | `java.lang.String` | `getLexicalValue``()`<br>Gets LEXICAL value from the XSDDataValue class return String value              |
    | `int`              | `getPrecision``()`<br>Gets the precision of decimal value return int precision                           |
    | `int`              | `getScale``()`<br>Gets the scale of decimal value return int scale                                       |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSDDataValue

          public XSDDataValue(int type,
                              java.lang.String lex)
                       throws XSDException

      Construct a XSDDataValue based of the type and lexical value
      Parameters:
      `type` - - Type as defined in XSDTypeConstants

      `lex` - - Lexical value of the type

      Throws:
      `XSDException,` - if the lexical value doesn't match the type

      [`XSDException`](XSDException.md)

  <!-- -->

  - ### Method Detail

    - #### getLength

          public int getLength()
                        throws XSDException

      Gets the length of STRING/BINARY value return int length
      Throws:
      [`XSDException`](XSDException.md) - if the data value is not of String/Binary type

    <!-- -->

    - #### getPrecision

          public int getPrecision()
                           throws XSDException

      Gets the precision of decimal value return int precision
      Throws:
      [`XSDException`](XSDException.md) - if the data value is not of decimal type

    <!-- -->

    - #### getScale

          public int getScale()
                       throws XSDException

      Gets the scale of decimal value return int scale
      Throws:
      [`XSDException`](XSDException.md) - if the data value is not decimal type

    <!-- -->

    - #### getLexicalValue

          public java.lang.String getLexicalValue()

      Gets LEXICAL value from the XSDDataValue class return String value

    <!-- -->

    - #### compareTo

          public int compareTo(XSDDataValue val)
                        throws XSDException

      Compare two values return int -1 -- smaller, 0 -- equal, 1 -- greater
      Throws:
      [`XSDException`](XSDException.md) - if the data values are not comparable

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

- **[Prev Class](XSDConstrainingFacet.md)**
- **[Next Class](XSDElement.md)**

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
