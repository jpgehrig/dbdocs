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

- **[Prev Class](XSDParticleNode.md)**
- **[Next Class](XSDTypeConstants.md)**

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

## **Class XSDSimpleType**

- **java.lang.Object**

- - **[oracle.xml.parser.schema.XSDNode](XSDNode.md)**

  - - **oracle.xml.parser.schema.XSDSimpleType**

<!-- -->

- **All Implemented Interfaces:**
  **[XSDConstantValues](XSDConstantValues.md), [XSDParticleNode](XSDParticleNode.md), [XSDTypeConstants](XSDTypeConstants.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XSDSimpleType
      extends XSDNode
      implements XSDParticleNode, XSDTypeConstants

  **This class represents Schema simpleType definitions**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type      | Field and Description |
    |------------------------|-----------------------|
    | `static XSDSimpleType` | `dayTimeDuration`     |
    | `static XSDSimpleType` | `untypedAtomic`       |
    | `static XSDSimpleType` | `yearMonthDuration`   |

    -

      ### **Fields inherited from interface oracle.xml.parser.schema.[XSDTypeConstants](XSDTypeConstants.md)**

      **[`_atomic`](XSDTypeConstants.md)`, `[`_base64`](XSDTypeConstants.md)`, `[`_collapse`](XSDTypeConstants.md)`, `[`_hex`](XSDTypeConstants.md)`, `[`_preserve`](XSDTypeConstants.md)`, `[`_replace`](XSDTypeConstants.md)`, `[`ANY_SIMPLE`](XSDTypeConstants.md)`, `[`ANY_URI`](XSDTypeConstants.md)`, `[`BASE64_BINARY`](XSDTypeConstants.md)`, `[`BINARY`](XSDTypeConstants.md)`, `[`BOOLEAN`](XSDTypeConstants.md)`, `[`BYTE`](XSDTypeConstants.md)`, `[`CDATA`](XSDTypeConstants.md)`, `[`CENTURY`](XSDTypeConstants.md)`, `[`DATE`](XSDTypeConstants.md)`, `[`DATE_TIME`](XSDTypeConstants.md)`, `[`DAYTIME_DURATION`](XSDTypeConstants.md)`, `[`DECIMAL`](XSDTypeConstants.md)`, `[`DOUBLE`](XSDTypeConstants.md)`, `[`DURATION`](XSDTypeConstants.md)`, `[`ENCODING`](XSDTypeConstants.md)`, `[`ENTITIES`](XSDTypeConstants.md)`, `[`ENTITY`](XSDTypeConstants.md)`, `[`ENUMERATION`](XSDTypeConstants.md)`, `[`fDAYTIME`](XSDTypeConstants.md)`, `[`fFINITE`](XSDTypeConstants.md)`, `[`fID`](XSDTypeConstants.md)`, `[`fIDREF`](XSDTypeConstants.md)`, `[`fINTEGER`](XSDTypeConstants.md)`, `[`FLOAT`](XSDTypeConstants.md)`, `[`fNUMERIC`](XSDTypeConstants.md)`, `[`fORDERED`](XSDTypeConstants.md)`, `[`FRACTION_DIGITS`](XSDTypeConstants.md)`, `[`fYEARMONTH`](XSDTypeConstants.md)`, `[`GDAY`](XSDTypeConstants.md)`, `[`GMONTH`](XSDTypeConstants.md)`, `[`GMONTH_DAY`](XSDTypeConstants.md)`, `[`GYEAR`](XSDTypeConstants.md)`, `[`GYEAR_MONTH`](XSDTypeConstants.md)`, `[`HEX_BINARY`](XSDTypeConstants.md)`, `[`iANY_SIMPLE`](XSDTypeConstants.md)`, `[`iANY_URI`](XSDTypeConstants.md)`, `[`iBASE64_BINARY`](XSDTypeConstants.md)`, `[`iBOOLEAN`](XSDTypeConstants.md)`, `[`iBYTE`](XSDTypeConstants.md)`, `[`ID`](XSDTypeConstants.md)`, `[`iDATE`](XSDTypeConstants.md)`, `[`iDATE_TIME`](XSDTypeConstants.md)`, `[`iDAYTIME_DURATION`](XSDTypeConstants.md)`, `[`iDECIMAL`](XSDTypeConstants.md)`, `[`iDOUBLE`](XSDTypeConstants.md)`, `[`IDREF`](XSDTypeConstants.md)`, `[`IDREFS`](XSDTypeConstants.md)`, `[`iDUMMY`](XSDTypeConstants.md)`, `[`iDURATION`](XSDTypeConstants.md)`, `[`iENTITIES`](XSDTypeConstants.md)`, `[`iENTITY`](XSDTypeConstants.md)`, `[`iENUMERATION`](XSDTypeConstants.md)`, `[`iFLOAT`](XSDTypeConstants.md)`, `[`iFRACTION_DIGITS`](XSDTypeConstants.md)`, `[`iGDAY`](XSDTypeConstants.md)`, `[`iGMONTH`](XSDTypeConstants.md)`, `[`iGMONTH_DAY`](XSDTypeConstants.md)`, `[`iGYEAR`](XSDTypeConstants.md)`, `[`iGYEAR_MONTH`](XSDTypeConstants.md)`, `[`iHEX_BINARY`](XSDTypeConstants.md)`, `[`iID`](XSDTypeConstants.md)`, `[`iIDREF`](XSDTypeConstants.md)`, `[`iIDREFS`](XSDTypeConstants.md)`, `[`iINT`](XSDTypeConstants.md)`, `[`iINTEGER`](XSDTypeConstants.md)`, `[`iLANGUAGE`](XSDTypeConstants.md)`, `[`iLENGTH`](XSDTypeConstants.md)`, `[`iLONG`](XSDTypeConstants.md)`, `[`iMAXEXCLUSIVE`](XSDTypeConstants.md)`, `[`iMAXINCLUSIVE`](XSDTypeConstants.md)`, `[`iMAXLENGTH`](XSDTypeConstants.md)`, `[`iMINEXCLUSIVE`](XSDTypeConstants.md)`, `[`iMININCLUSIVE`](XSDTypeConstants.md)`, `[`iMINLENGTH`](XSDTypeConstants.md)`, `[`iN_STRING`](XSDTypeConstants.md)`, `[`iNAME`](XSDTypeConstants.md)`, `[`iNCNAME`](XSDTypeConstants.md)`, `[`iNEGATIVE_INTEGER`](XSDTypeConstants.md)`, `[`iNMTOKEN`](XSDTypeConstants.md)`, `[`iNMTOKENS`](XSDTypeConstants.md)`, `[`iNON_NEGATIVE_INTEGER`](XSDTypeConstants.md)`, `[`iNON_POSITIVE_INTEGER`](XSDTypeConstants.md)`, `[`iNOTATION`](XSDTypeConstants.md)`, `[`INT`](XSDTypeConstants.md)`, `[`INTEGER_STR`](XSDTypeConstants.md)`, `[`iPATTERN`](XSDTypeConstants.md)`, `[`iPOSITIVE_INTEGER`](XSDTypeConstants.md)`, `[`iQNAME`](XSDTypeConstants.md)`, `[`iSHORT`](XSDTypeConstants.md)`, `[`iSTRING`](XSDTypeConstants.md)`, `[`iTIME`](XSDTypeConstants.md)`, `[`iTOKEN`](XSDTypeConstants.md)`, `[`iTOTAL_DIGITS`](XSDTypeConstants.md)`, `[`iUNSIGNED_BYTE`](XSDTypeConstants.md)`, `[`iUNSIGNED_INT`](XSDTypeConstants.md)`, `[`iUNSIGNED_LONG`](XSDTypeConstants.md)`, `[`iUNSIGNED_SHORT`](XSDTypeConstants.md)`, `[`iWHITESPACE`](XSDTypeConstants.md)`, `[`iYEARMONTH_DURATION`](XSDTypeConstants.md)`, `[`LANGUAGE`](XSDTypeConstants.md)`, `[`LENGTH`](XSDTypeConstants.md)`, `[`LONG`](XSDTypeConstants.md)`, `[`MAXEXCLUSIVE`](XSDTypeConstants.md)`, `[`MAXINCLUSIVE`](XSDTypeConstants.md)`, `[`MAXLENGTH`](XSDTypeConstants.md)`, `[`MINEXCLUSIVE`](XSDTypeConstants.md)`, `[`MININCLUSIVE`](XSDTypeConstants.md)`, `[`MINLENGTH`](XSDTypeConstants.md)`, `[`MONTH`](XSDTypeConstants.md)`, `[`N_STRING`](XSDTypeConstants.md)`, `[`NAME`](XSDTypeConstants.md)`, `[`nBUILTIN`](XSDTypeConstants.md)`, `[`NCNAME`](XSDTypeConstants.md)`, `[`NEGATIVE_INTEGER`](XSDTypeConstants.md)`, `[`nFacets`](XSDTypeConstants.md)`, `[`NMTOKEN`](XSDTypeConstants.md)`, `[`NMTOKENS`](XSDTypeConstants.md)`, `[`NON_NEGATIVE_INTEGER`](XSDTypeConstants.md)`, `[`NON_POSITIVE_INTEGER`](XSDTypeConstants.md)`, `[`nPRIMITIVE`](XSDTypeConstants.md)`, `[`PATTERN`](XSDTypeConstants.md)`, `[`PERIOD`](XSDTypeConstants.md)`, `[`POSITIVE_INTEGER`](XSDTypeConstants.md)`, `[`PRECISION`](XSDTypeConstants.md)`, `[`QNAME`](XSDTypeConstants.md)`, `[`RECURRING_DATE`](XSDTypeConstants.md)`, `[`RECURRING_DAY`](XSDTypeConstants.md)`, `[`RECURRING_DURATION`](XSDTypeConstants.md)`, `[`SCALE`](XSDTypeConstants.md)`, `[`sFacets`](XSDTypeConstants.md)`, `[`SHORT`](XSDTypeConstants.md)`, `[`SNOTATION`](XSDTypeConstants.md)`, `[`STRING`](XSDTypeConstants.md)`, `[`sTypes`](XSDTypeConstants.md)`, `[`TIME`](XSDTypeConstants.md)`, `[`TIME_DURATION`](XSDTypeConstants.md)`, `[`TIME_INSTANT`](XSDTypeConstants.md)`, `[`TIME_PERIOD`](XSDTypeConstants.md)`, `[`TOKEN`](XSDTypeConstants.md)`, `[`TOTAL_DIGITS`](XSDTypeConstants.md)`, `[`UNSIGNED_BYTE`](XSDTypeConstants.md)`, `[`UNSIGNED_INT`](XSDTypeConstants.md)`, `[`UNSIGNED_LONG`](XSDTypeConstants.md)`, `[`UNSIGNED_SHORT`](XSDTypeConstants.md)`, `[`UNTYPED_ATOMIC`](XSDTypeConstants.md)`, `[`URI_REFERENCE`](XSDTypeConstants.md)`, `[`WHITESPACE`](XSDTypeConstants.md)`, `[`YEAR`](XSDTypeConstants.md)`, `[`YEARMONTH_DURATION`](XSDTypeConstants.md)**

    <!-- -->

    -

      ### **Fields inherited from interface oracle.xml.parser.schema.[XSDConstantValues](XSDConstantValues.md)**

      **[`_abstract`](XSDConstantValues.md)`, `[`_all`](XSDConstantValues.md)`, `[`_annotation`](XSDConstantValues.md)`, `[`_any`](XSDConstantValues.md)`, `[`_anyAttribute`](XSDConstantValues.md)`, `[`_anySimpleType`](XSDConstantValues.md)`, `[`_anyType`](XSDConstantValues.md)`, `[`_appinfo`](XSDConstantValues.md)`, `[`_attrFormDefault`](XSDConstantValues.md)`, `[`_attribute`](XSDConstantValues.md)`, `[`_attributeGroup`](XSDConstantValues.md)`, `[`_attrTag`](XSDConstantValues.md)`, `[`_base`](XSDConstantValues.md)`, `[`_block`](XSDConstantValues.md)`, `[`_blockDefault`](XSDConstantValues.md)`, `[`_choice`](XSDConstantValues.md)`, `[`_complexContent`](XSDConstantValues.md)`, `[`_complexType`](XSDConstantValues.md)`, `[`_content`](XSDConstantValues.md)`, `[`_default`](XSDConstantValues.md)`, `[`_derivedBy`](XSDConstantValues.md)`, `[`_documentation`](XSDConstantValues.md)`, `[`_element`](XSDConstantValues.md)`, `[`_elementOnly`](XSDConstantValues.md)`, `[`_elemFormDefault`](XSDConstantValues.md)`, `[`_empty`](XSDConstantValues.md)`, `[`_enumeration`](XSDConstantValues.md)`, `[`_equivClass`](XSDConstantValues.md)`, `[`_extension`](XSDConstantValues.md)`, `[`_false`](XSDConstantValues.md)`, `[`_field`](XSDConstantValues.md)`, `[`_final`](XSDConstantValues.md)`, `[`_finalDefault`](XSDConstantValues.md)`, `[`_fixed`](XSDConstantValues.md)`, `[`_form`](XSDConstantValues.md)`, `[`_group`](XSDConstantValues.md)`, `[`_id`](XSDConstantValues.md)`, `[`_import`](XSDConstantValues.md)`, `[`_include`](XSDConstantValues.md)`, `[`_itemType`](XSDConstantValues.md)`, `[`_key`](XSDConstantValues.md)`, `[`_keyref`](XSDConstantValues.md)`, `[`_lax`](XSDConstantValues.md)`, `[`_list`](XSDConstantValues.md)`, `[`_maxOccurs`](XSDConstantValues.md)`, `[`_memberTypes`](XSDConstantValues.md)`, `[`_minOccurs`](XSDConstantValues.md)`, `[`_mixed`](XSDConstantValues.md)`, `[`_nall`](XSDConstantValues.md)`, `[`_name`](XSDConstantValues.md)`, `[`_namespace`](XSDConstantValues.md)`, `[`_nil`](XSDConstantValues.md)`, `[`_nillable`](XSDConstantValues.md)`, `[`_nnany`](XSDConstantValues.md)`, `[`_nnlist`](XSDConstantValues.md)`, `[`_nnlocal`](XSDConstantValues.md)`, `[`_nnother`](XSDConstantValues.md)`, `[`_nntargetNS`](XSDConstantValues.md)`, `[`_noNSSchemaLocation`](XSDConstantValues.md)`, `[`_notation`](XSDConstantValues.md)`, `[`_null`](XSDConstantValues.md)`, `[`_nullable`](XSDConstantValues.md)`, `[`_optional`](XSDConstantValues.md)`, `[`_pattern`](XSDConstantValues.md)`, `[`_processContents`](XSDConstantValues.md)`, `[`_prohibited`](XSDConstantValues.md)`, `[`_publicid`](XSDConstantValues.md)`, `[`_qualified`](XSDConstantValues.md)`, `[`_redefine`](XSDConstantValues.md)`, `[`_ref`](XSDConstantValues.md)`, `[`_refer`](XSDConstantValues.md)`, `[`_required`](XSDConstantValues.md)`, `[`_restriction`](XSDConstantValues.md)`, `[`_restrictions`](XSDConstantValues.md)`, `[`_schemaLocation`](XSDConstantValues.md)`, `[`_selector`](XSDConstantValues.md)`, `[`_sequence`](XSDConstantValues.md)`, `[`_simpleContent`](XSDConstantValues.md)`, `[`_simpleType`](XSDConstantValues.md)`, `[`_skip`](XSDConstantValues.md)`, `[`_strict`](XSDConstantValues.md)`, `[`_substitution`](XSDConstantValues.md)`, `[`_substitutionGrp`](XSDConstantValues.md)`, `[`_systemid`](XSDConstantValues.md)`, `[`_targetNS`](XSDConstantValues.md)`, `[`_textOnly`](XSDConstantValues.md)`, `[`_this`](XSDConstantValues.md)`, `[`_true`](XSDConstantValues.md)`, `[`_type`](XSDConstantValues.md)`, `[`_undef`](XSDConstantValues.md)`, `[`_union`](XSDConstantValues.md)`, `[`_unique`](XSDConstantValues.md)`, `[`_unqualified`](XSDConstantValues.md)`, `[`_use`](XSDConstantValues.md)`, `[`_value`](XSDConstantValues.md)`, `[`_version`](XSDConstantValues.md)`, `[`_xmlns`](XSDConstantValues.md)`, `[`ABSENT_NS`](XSDConstantValues.md)`, `[`ACCEPTED`](XSDConstantValues.md)`, `[`ALL`](XSDConstantValues.md)`, `[`ANNOTATION`](XSDConstantValues.md)`, `[`ANY`](XSDConstantValues.md)`, `[`ANY_ATTRIBUTE`](XSDConstantValues.md)`, `[`ANY_NODE`](XSDConstantValues.md)`, `[`ATTRIBUTE`](XSDConstantValues.md)`, `[`ATTRIBUTE_GROUP`](XSDConstantValues.md)`, `[`AUTO_VALIDATION`](XSDConstantValues.md)`, `[`BASE_RESOLVED`](XSDConstantValues.md)`, `[`BASE_UNRESOLVED`](XSDConstantValues.md)`, `[`BASE_URL`](XSDConstantValues.md)`, `[`BUILD_FAIL`](XSDConstantValues.md)`, `[`CHOICE`](XSDConstantValues.md)`, `[`CIRCULAR_SUBST`](XSDConstantValues.md)`, `[`CONFLICIT_FACET`](XSDConstantValues.md)`, `[`constName`](XSDConstantValues.md)`, `[`DATATYPE`](XSDConstantValues.md)`, `[`DEEP_VALIDATION`](XSDConstantValues.md)`, `[`derivationBlock`](XSDConstantValues.md)`, `[`DONE`](XSDConstantValues.md)`, `[`DUPLICATE_DEF`](XSDConstantValues.md)`, `[`duplicateId`](XSDConstantValues.md)`, `[`ELEMENT`](XSDConstantValues.md)`, `[`ELEMENT_CHILD`](XSDConstantValues.md)`, `[`ELEMENT_ONLY`](XSDConstantValues.md)`, `[`elemNotNullable`](XSDConstantValues.md)`, `[`EMPTY`](XSDConstantValues.md)`, `[`ENTITY_RESOLVER`](XSDConstantValues.md)`, `[`EQUIV_RESOLVED`](XSDConstantValues.md)`, `[`EQUIV_UNRESOLVED`](XSDConstantValues.md)`, `[`ERROR`](XSDConstantValues.md)`, `[`EXTENTION`](XSDConstantValues.md)`, `[`FACET_CHILD`](XSDConstantValues.md)`, `[`FAKE_ATTR`](XSDConstantValues.md)`, `[`FAKE_NODE`](XSDConstantValues.md)`, `[`FIXED_SCHEMA`](XSDConstantValues.md)`, `[`GROUP`](XSDConstantValues.md)`, `[`IABSTRACT`](XSDConstantValues.md)`, `[`IBLOCKEXT`](XSDConstantValues.md)`, `[`IBLOCKRST`](XSDConstantValues.md)`, `[`IBLOCKSUB`](XSDConstantValues.md)`, `[`IDENTITY_ERROR`](XSDConstantValues.md)`, `[`IDENTITY_KEY`](XSDConstantValues.md)`, `[`IDENTITY_KEYREF`](XSDConstantValues.md)`, `[`IDENTITY_UNIQUE`](XSDConstantValues.md)`, `[`IFINALEXT`](XSDConstantValues.md)`, `[`IFINALLIST`](XSDConstantValues.md)`, `[`IFINALRST`](XSDConstantValues.md)`, `[`IFINALUNION`](XSDConstantValues.md)`, `[`IMPORT`](XSDConstantValues.md)`, `[`INCLUDE`](XSDConstantValues.md)`, `[`INCORRECT_ATTR`](XSDConstantValues.md)`, `[`INCORRECT_ELEM`](XSDConstantValues.md)`, `[`INFINITY`](XSDConstantValues.md)`, `[`INTERNAL_ERROR`](XSDConstantValues.md)`, `[`INVALID_DATE`](XSDConstantValues.md)`, `[`INVALID_DATETIME`](XSDConstantValues.md)`, `[`INVALID_DERIVATION`](XSDConstantValues.md)`, `[`INVALID_FACET`](XSDConstantValues.md)`, `[`INVALID_FACET_VALUE`](XSDConstantValues.md)`, `[`INVALID_NOTATION`](XSDConstantValues.md)`, `[`INVALID_REGEX`](XSDConstantValues.md)`, `[`INVALID_SCHEMA_NS`](XSDConstantValues.md)`, `[`INVALID_TIME`](XSDConstantValues.md)`, `[`INVALID_TYPE_VALUE`](XSDConstantValues.md)`, `[`invalidAttr`](XSDConstantValues.md)`, `[`invalidAttrVal`](XSDConstantValues.md)`, `[`invalidChars`](XSDConstantValues.md)`, `[`invalidElem`](XSDConstantValues.md)`, `[`invalidFixedChars`](XSDConstantValues.md)`, `[`invalidNS`](XSDConstantValues.md)`, `[`invalidPrefix`](XSDConstantValues.md)`, `[`invalidProperty`](XSDConstantValues.md)`, `[`invalidRef`](XSDConstantValues.md)`, `[`invalidSubstitution`](XSDConstantValues.md)`, `[`invalidTargetNS`](XSDConstantValues.md)`, `[`LAX_VALIDATION`](XSDConstantValues.md)`, `[`MISSING_NS`](XSDConstantValues.md)`, `[`missingAttr`](XSDConstantValues.md)`, `[`MIXED`](XSDConstantValues.md)`, `[`NEW_STATE`](XSDConstantValues.md)`, `[`NO_CHILD`](XSDConstantValues.md)`, `[`noDefinition`](XSDConstantValues.md)`, `[`NOT_DONE`](XSDConstantValues.md)`, `[`NOTATION`](XSDConstantValues.md)`, `[`notComplete`](XSDConstantValues.md)`, `[`notSubstitutable`](XSDConstantValues.md)`, `[`notSubTypeOf`](XSDConstantValues.md)`, `[`NS_CONFLICT`](XSDConstantValues.md)`, `[`NS_DIF_SPECIFIED`](XSDConstantValues.md)`, `[`NS_NOT_ALLOWED`](XSDConstantValues.md)`, `[`NS_NOT_EXPECTED`](XSDConstantValues.md)`, `[`NS_NOT_SAME`](XSDConstantValues.md)`, `[`NS_RESOLVER`](XSDConstantValues.md)`, `[`REDEFINE`](XSDConstantValues.md)`, `[`REF_RESOLVED`](XSDConstantValues.md)`, `[`REF_UNRESOLVED`](XSDConstantValues.md)`, `[`RESTRICTION`](XSDConstantValues.md)`, `[`ROOT_ELEMENT`](XSDConstantValues.md)`, `[`ROOT_NODE`](XSDConstantValues.md)`, `[`ROOT_TYPE`](XSDConstantValues.md)`, `[`SCHEMA_NS`](XSDConstantValues.md)`, `[`SCHEMA_RESOLVER`](XSDConstantValues.md)`, `[`SEQ`](XSDConstantValues.md)`, `[`STRICT_VALIDATION`](XSDConstantValues.md)`, `[`TEXT_ONLY`](XSDConstantValues.md)`, `[`TOP_LEVEL`](XSDConstantValues.md)`, `[`TYPE`](XSDConstantValues.md)`, `[`TYPE_RESOLVED`](XSDConstantValues.md)`, `[`TYPE_UNRESOLVED`](XSDConstantValues.md)`, `[`UNDEF`](XSDConstantValues.md)`, `[`unexpectedAttr`](XSDConstantValues.md)`, `[`unexpectedElem`](XSDConstantValues.md)`, `[`VALIDATION_MODE`](XSDConstantValues.md)`, `[`VIOLATE_FACET`](XSDConstantValues.md)`, `[`XSDRECNS`](XSDConstantValues.md)`, `[`XSDRECTYPENS`](XSDConstantValues.md)`, `[`XSIRECNS`](XSDConstantValues.md)`, `[`XSITYPE_ABSENT`](XSDConstantValues.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                         |
    |---------------------------------------------------------------------|
    | `XSDSimpleType``(int basic, java.lang.String tnm)`<br>Deprecated.   |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                     | Method and Description                                                                                      |
    |-------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
    | `int`                                                 | `compareValues``(java.lang.String str1, java.lang.String str2)`                                             |
    | `static XSDSimpleType`                                | `derivedFrom``(XSDSimpleType source, java.lang.String nm, java.lang.String var)`<br>Deprecated.             |
    | `XSDSimpleType`                                       | `getBase``()`                                                                                               |
    | `int`                                                 | `getBasicType``()`<br>Gets the basic type from which this type was derived.                                 |
    | `static int`                                          | `getBasicType``(int btype)`<br>Gets the basic type from which this type was derived.                        |
    | `static java.util.Hashtable`                          | `getBuiltInDatatypes``()`<br>Gets all built-in datatypes                                                    |
    | `static java.util.HashMap`                            | `getBuiltInDatatypesAsHashMap``()`<br>Gets all built-in datatypes, as a HashMap.                            |
    | `int`                                                 | `getBuiltInId``()`<br>Gets the id of builtIn type from which this type was derived.                         |
    | [`XSDConstrainingFacet`](XSDConstrainingFacet.md)`[]` | `getFacets``()`<br>Get the facets                                                                           |
    | `static XSDSimpleType`                                | `getPrimitiveType``(int itype)`<br>Get primitive type                                                       |
    | `java.lang.String`                                    | `getTargetNS``()`<br>Get target namespace                                                                   |
    | `java.lang.String`                                    | `getVariety``()`<br>Get the variety of the type                                                             |
    | `java.lang.String`                                    | `getWSFacetValue``()`<br>Get the value for the whitespace facet                                             |
    | `boolean`                                             | `hasFlag``(int flag)`<br>Check proprety indicated by the flag                                               |
    | `boolean`                                             | `isAbstract``()`                                                                                            |
    | `boolean`                                             | `isPrimitive``()`                                                                                           |
    | `void`                                                | `setFacet``(java.lang.String fname, java.lang.String value)`<br>Sets a facet for restriction                |
    | `void`                                                | `validateValue``(java.lang.String val)`<br>Validates the string value with the facets defined for this type |

    - ### Methods inherited from class oracle.xml.parser.schema.[XSDNode](XSDNode.md)

      [`getName`](XSDNode.md)`, `[`getNodeType`](XSDNode.md)`, `[`getOwnerSchema`](XSDNode.md)`, `[`getRefLocalname`](XSDNode.md)`, `[`isNodeType`](XSDNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.xml.parser.schema.[XSDParticleNode](XSDParticleNode.md)

      [`getMaxOccurs`](XSDParticleNode.md)`, `[`getMinOccurs`](XSDParticleNode.md)`, `[`setMaxOccurs`](XSDParticleNode.md)`, `[`setMinOccurs`](XSDParticleNode.md)

<!-- -->

- - ### Field Detail

    - #### yearMonthDuration

          public static final XSDSimpleType yearMonthDuration

    <!-- -->

    - #### dayTimeDuration

          public static final XSDSimpleType dayTimeDuration

    <!-- -->

    - #### untypedAtomic

          public static final XSDSimpleType untypedAtomic

  <!-- -->

  - ### Constructor Detail

    - #### XSDSimpleType

          public XSDSimpleType(int basic,
                               java.lang.String tnm)

      Deprecated. 
      Constructor for built-in types

  <!-- -->

  - ### Method Detail

    - #### hasFlag

          public boolean hasFlag(int flag)

      Check proprety indicated by the flag
      Parameters:
      `flag` - - the flag to be check

      Returns:
      true is the flag is set, false otherwise

    <!-- -->

    - #### getTargetNS

          public java.lang.String getTargetNS()

      Get target namespace
      Overrides:
      [`getTargetNS`](XSDNode.md) in class [`XSDNode`](XSDNode.md)

      Returns:
      tagetNS

    <!-- -->

    - #### isPrimitive

          public boolean isPrimitive()

    <!-- -->

    - #### getPrimitiveType

          public static XSDSimpleType getPrimitiveType(int itype)

      Get primitive type
      Parameters:
      `itype` - - the primitive id

      Returns:
      the primitive simple type

    <!-- -->

    - #### derivedFrom

          public static XSDSimpleType derivedFrom(XSDSimpleType source,
                                                  java.lang.String nm,
                                                  java.lang.String var)
                                           throws XSDException

      Deprecated. 
      Derive a type from the given base type
      Parameters:
      `source` - XSDSimpleType The base type

      `nm` - String The name of the new type

      `var` - String The method of derivation

      Throws:
      [`XSDException`](XSDException.md) - if new type can not be created.

    <!-- -->

    - #### getBasicType

          public int getBasicType()

      Gets the basic type from which this type was derived.
      Returns:
      basicType

    <!-- -->

    - #### getBasicType

          public static int getBasicType(int btype)

      Gets the basic type from which this type was derived.
      Returns:
      basicType

    <!-- -->

    - #### getBuiltInId

          public int getBuiltInId()

      Gets the id of builtIn type from which this type was derived.
      Returns:
      the buitIn type id this type belongs to

    <!-- -->

    - #### isAbstract

          public boolean isAbstract()

    <!-- -->

    - #### getBase

          public XSDSimpleType getBase()

    <!-- -->

    - #### getWSFacetValue

          public java.lang.String getWSFacetValue()

      Get the value for the whitespace facet
      Returns:
      one of preserve, replace or collapse, "" for anySimple

    <!-- -->

    - #### getFacets

          public XSDConstrainingFacet[] getFacets()

      Get the facets
      Returns:
      facets

    <!-- -->

    - #### getVariety

          public java.lang.String getVariety()

      Get the variety of the type
      Returns:
      variety

    <!-- -->

    - #### getBuiltInDatatypes

          public static java.util.Hashtable getBuiltInDatatypes()
                                                         throws XSDException

      Gets all built-in datatypes
      Throws:
      [`XSDException`](XSDException.md)

    <!-- -->

    - #### getBuiltInDatatypesAsHashMap

          public static java.util.HashMap getBuiltInDatatypesAsHashMap()
                                                                throws XSDException

      Gets all built-in datatypes, as a HashMap. This method is to be used internally, instead of getBuiltInDatatypes(). getBuiltInDatatypes() returns a Hashtable, which locks up under high memory use, and is kept to preserve backward compatibility for preexisting external users.
      Throws:
      [`XSDException`](XSDException.md)

    <!-- -->

    - #### validateValue

          public void validateValue(java.lang.String val)
                             throws java.lang.Exception

      Validates the string value with the facets defined for this type
      Parameters:
      `val` - value to be validated

      Throws:
      [`XSDException`](XSDException.md) - if the value is not valid

      `java.lang.Exception`

    <!-- -->

    - #### compareValues

          public int compareValues(java.lang.String str1,
                                   java.lang.String str2)

    <!-- -->

    - #### setFacet

          public void setFacet(java.lang.String fname,
                               java.lang.String value)
                        throws XSDException

      Sets a facet for restriction
      Parameters:
      `fname` - Name of the facet being set

      `value` - Value of the facet

      Throws:
      [`XSDException`](XSDException.md) - if the facet is invalid

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

- **[Prev Class](XSDParticleNode.md)**
- **[Next Class](XSDTypeConstants.md)**

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
