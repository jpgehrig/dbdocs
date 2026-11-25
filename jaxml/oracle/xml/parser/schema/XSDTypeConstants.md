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

- **[Prev Class](XSDSimpleType.md)**
- **[Next Class](XSDValidator.md)**

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

## **Interface XSDTypeConstants**

- **All Known Implementing Classes:**
  **[XSDAttribute](XSDAttribute.md), [XSDConstrainingFacet](XSDConstrainingFacet.md), [XSDDataValue](XSDDataValue.md), [XSDElement](XSDElement.md), [XSDSimpleType](XSDSimpleType.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XSDTypeConstants

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type           | Field and Description                                                     |
    |-----------------------------|---------------------------------------------------------------------------|
    | `static java.lang.String`   | `_atomic`                                                                 |
    | `static java.lang.String`   | `_base64`                                                                 |
    | `static java.lang.String`   | `_collapse`                                                               |
    | `static java.lang.String`   | `_hex`                                                                    |
    | `static java.lang.String`   | `_preserve`                                                               |
    | `static java.lang.String`   | `_replace`                                                                |
    | `static java.lang.String`   | `ANY_SIMPLE`                                                              |
    | `static java.lang.String`   | `ANY_URI`                                                                 |
    | `static java.lang.String`   | `BASE64_BINARY`                                                           |
    | `static java.lang.String`   | `BINARY`                                                                  |
    | `static java.lang.String`   | `BOOLEAN`                                                                 |
    | `static java.lang.String`   | `BYTE`                                                                    |
    | `static java.lang.String`   | `CDATA`                                                                   |
    | `static java.lang.String`   | `CENTURY`                                                                 |
    | `static java.lang.String`   | `DATE`                                                                    |
    | `static java.lang.String`   | `DATE_TIME`                                                               |
    | `static java.lang.String`   | `DAYTIME_DURATION`                                                        |
    | `static java.lang.String`   | `DECIMAL`                                                                 |
    | `static java.lang.String`   | `DOUBLE`                                                                  |
    | `static java.lang.String`   | `DURATION`                                                                |
    | `static java.lang.String`   | `ENCODING`                                                                |
    | `static java.lang.String`   | `ENTITIES`                                                                |
    | `static java.lang.String`   | `ENTITY`                                                                  |
    | `static java.lang.String`   | `ENUMERATION`                                                             |
    | `static int`                | `fDAYTIME`                                                                |
    | `static int`                | `fFINITE`                                                                 |
    | `static int`                | `fID`                                                                     |
    | `static int`                | `fIDREF`                                                                  |
    | `static int`                | `fINTEGER`                                                                |
    | `static java.lang.String`   | `FLOAT`                                                                   |
    | `static int`                | `fNUMERIC`<br>flags for foundamental Facet and other properties           |
    | `static int`                | `fORDERED`                                                                |
    | `static java.lang.String`   | `FRACTION_DIGITS`                                                         |
    | `static int`                | `fYEARMONTH`                                                              |
    | `static java.lang.String`   | `GDAY`                                                                    |
    | `static java.lang.String`   | `GMONTH`                                                                  |
    | `static java.lang.String`   | `GMONTH_DAY`                                                              |
    | `static java.lang.String`   | `GYEAR`                                                                   |
    | `static java.lang.String`   | `GYEAR_MONTH`                                                             |
    | `static java.lang.String`   | `HEX_BINARY`                                                              |
    | `static int`                | `iANY_SIMPLE`<br>Primitive datatypes const                                |
    | `static int`                | `iANY_URI`                                                                |
    | `static int`                | `iBASE64_BINARY`                                                          |
    | `static int`                | `iBOOLEAN`                                                                |
    | `static int`                | `iBYTE`                                                                   |
    | `static java.lang.String`   | `ID`                                                                      |
    | `static int`                | `iDATE`                                                                   |
    | `static int`                | `iDATE_TIME`                                                              |
    | `static int`                | `iDAYTIME_DURATION`                                                       |
    | `static int`                | `iDECIMAL`                                                                |
    | `static int`                | `iDOUBLE`                                                                 |
    | `static java.lang.String`   | `IDREF`                                                                   |
    | `static java.lang.String`   | `IDREFS`<br>Derived by List                                               |
    | `static int`                | `iDUMMY`<br>Contraining Facet IDs                                         |
    | `static int`                | `iDURATION`                                                               |
    | `static int`                | `iENTITIES`                                                               |
    | `static int`                | `iENTITY`                                                                 |
    | `static int`                | `iENUMERATION`                                                            |
    | `static int`                | `iFLOAT`                                                                  |
    | `static int`                | `iFRACTION_DIGITS`                                                        |
    | `static int`                | `iGDAY`                                                                   |
    | `static int`                | `iGMONTH`                                                                 |
    | `static int`                | `iGMONTH_DAY`                                                             |
    | `static int`                | `iGYEAR`                                                                  |
    | `static int`                | `iGYEAR_MONTH`                                                            |
    | `static int`                | `iHEX_BINARY`                                                             |
    | `static int`                | `iID`                                                                     |
    | `static int`                | `iIDREF`                                                                  |
    | `static int`                | `iIDREFS`                                                                 |
    | `static int`                | `iINT`                                                                    |
    | `static int`                | `iINTEGER`                                                                |
    | `static int`                | `iLANGUAGE`                                                               |
    | `static int`                | `iLENGTH`                                                                 |
    | `static int`                | `iLONG`                                                                   |
    | `static int`                | `iMAXEXCLUSIVE`                                                           |
    | `static int`                | `iMAXINCLUSIVE`                                                           |
    | `static int`                | `iMAXLENGTH`                                                              |
    | `static int`                | `iMINEXCLUSIVE`                                                           |
    | `static int`                | `iMININCLUSIVE`                                                           |
    | `static int`                | `iMINLENGTH`                                                              |
    | `static int`                | `iN_STRING`                                                               |
    | `static int`                | `iNAME`                                                                   |
    | `static int`                | `iNCNAME`                                                                 |
    | `static int`                | `iNEGATIVE_INTEGER`                                                       |
    | `static int`                | `iNMTOKEN`                                                                |
    | `static int`                | `iNMTOKENS`                                                               |
    | `static int`                | `iNON_NEGATIVE_INTEGER`                                                   |
    | `static int`                | `iNON_POSITIVE_INTEGER`                                                   |
    | `static int`                | `iNOTATION`                                                               |
    | `static java.lang.String`   | `INT`                                                                     |
    | `static java.lang.String`   | `INTEGER_STR`<br>Basic generated type derived from DECIMAL                |
    | `static int`                | `iPATTERN`                                                                |
    | `static int`                | `iPOSITIVE_INTEGER`                                                       |
    | `static int`                | `iQNAME`                                                                  |
    | `static int`                | `iSHORT`                                                                  |
    | `static int`                | `iSTRING`                                                                 |
    | `static int`                | `iTIME`                                                                   |
    | `static int`                | `iTOKEN`                                                                  |
    | `static int`                | `iTOTAL_DIGITS`                                                           |
    | `static int`                | `iUNSIGNED_BYTE`                                                          |
    | `static int`                | `iUNSIGNED_INT`                                                           |
    | `static int`                | `iUNSIGNED_LONG`                                                          |
    | `static int`                | `iUNSIGNED_SHORT`                                                         |
    | `static int`                | `iWHITESPACE`                                                             |
    | `static int`                | `iYEARMONTH_DURATION`                                                     |
    | `static java.lang.String`   | `LANGUAGE`                                                                |
    | `static java.lang.String`   | `LENGTH`                                                                  |
    | `static java.lang.String`   | `LONG`                                                                    |
    | `static java.lang.String`   | `MAXEXCLUSIVE`                                                            |
    | `static java.lang.String`   | `MAXINCLUSIVE`                                                            |
    | `static java.lang.String`   | `MAXLENGTH`                                                               |
    | `static java.lang.String`   | `MINEXCLUSIVE`                                                            |
    | `static java.lang.String`   | `MININCLUSIVE`                                                            |
    | `static java.lang.String`   | `MINLENGTH`                                                               |
    | `static java.lang.String`   | `MONTH`                                                                   |
    | `static java.lang.String`   | `N_STRING`<br>Basic generated type derived from STRING                    |
    | `static java.lang.String`   | `NAME`                                                                    |
    | `static int`                | `nBUILTIN`                                                                |
    | `static java.lang.String`   | `NCNAME`                                                                  |
    | `static java.lang.String`   | `NEGATIVE_INTEGER`                                                        |
    | `static int`                | `nFacets`                                                                 |
    | `static java.lang.String`   | `NMTOKEN`                                                                 |
    | `static java.lang.String`   | `NMTOKENS`                                                                |
    | `static java.lang.String`   | `NON_NEGATIVE_INTEGER`                                                    |
    | `static java.lang.String`   | `NON_POSITIVE_INTEGER`                                                    |
    | `static int`                | `nPRIMITIVE`                                                              |
    | `static java.lang.String`   | `PATTERN`                                                                 |
    | `static java.lang.String`   | `PERIOD`                                                                  |
    | `static java.lang.String`   | `POSITIVE_INTEGER`                                                        |
    | `static java.lang.String`   | `PRECISION`                                                               |
    | `static java.lang.String`   | `QNAME`                                                                   |
    | `static java.lang.String`   | `RECURRING_DATE`                                                          |
    | `static java.lang.String`   | `RECURRING_DAY`                                                           |
    | `static java.lang.String`   | `RECURRING_DURATION`                                                      |
    | `static java.lang.String`   | `SCALE`                                                                   |
    | `static java.lang.String[]` | `sFacets`<br>Array of facet strings, can be indexed using the above const |
    | `static java.lang.String`   | `SHORT`                                                                   |
    | `static java.lang.String`   | `SNOTATION`                                                               |
    | `static java.lang.String`   | `STRING`                                                                  |
    | `static java.lang.String[]` | `sTypes`<br>Array of types indexed by above consts                        |
    | `static java.lang.String`   | `TIME`                                                                    |
    | `static java.lang.String`   | `TIME_DURATION`                                                           |
    | `static java.lang.String`   | `TIME_INSTANT`                                                            |
    | `static java.lang.String`   | `TIME_PERIOD`                                                             |
    | `static java.lang.String`   | `TOKEN`                                                                   |
    | `static java.lang.String`   | `TOTAL_DIGITS`                                                            |
    | `static java.lang.String`   | `UNSIGNED_BYTE`                                                           |
    | `static java.lang.String`   | `UNSIGNED_INT`                                                            |
    | `static java.lang.String`   | `UNSIGNED_LONG`                                                           |
    | `static java.lang.String`   | `UNSIGNED_SHORT`                                                          |
    | `static java.lang.String`   | `UNTYPED_ATOMIC`                                                          |
    | `static java.lang.String`   | `URI_REFERENCE`                                                           |
    | `static java.lang.String`   | `WHITESPACE`                                                              |
    | `static java.lang.String`   | `YEAR`                                                                    |
    | `static java.lang.String`   | `YEARMONTH_DURATION`                                                      |

<!-- -->

-
  -

    ### **Field Detail**

    - #### **iANY_SIMPLE**

          static final int iANY_SIMPLE

      **Primitive datatypes const**
      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iSTRING**

          static final int iSTRING

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iBOOLEAN**

          static final int iBOOLEAN

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iFLOAT**

          static final int iFLOAT

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iDOUBLE**

          static final int iDOUBLE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iDECIMAL**

          static final int iDECIMAL

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iDURATION**

          static final int iDURATION

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iDATE_TIME**

          static final int iDATE_TIME

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iTIME**

          static final int iTIME

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iDATE**

          static final int iDATE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iGYEAR_MONTH**

          static final int iGYEAR_MONTH

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iGYEAR**

          static final int iGYEAR

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iGMONTH**

          static final int iGMONTH

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iGMONTH_DAY**

          static final int iGMONTH_DAY

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iGDAY**

          static final int iGDAY

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iHEX_BINARY**

          static final int iHEX_BINARY

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iBASE64_BINARY**

          static final int iBASE64_BINARY

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iANY_URI**

          static final int iANY_URI

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iQNAME**

          static final int iQNAME

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iNOTATION**

          static final int iNOTATION

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **nPRIMITIVE**

          static final int nPRIMITIVE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iYEARMONTH_DURATION**

          static final int iYEARMONTH_DURATION

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iDAYTIME_DURATION**

          static final int iDAYTIME_DURATION

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iINTEGER**

          static final int iINTEGER

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iNON_POSITIVE_INTEGER**

          static final int iNON_POSITIVE_INTEGER

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iLONG**

          static final int iLONG

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iNON_NEGATIVE_INTEGER**

          static final int iNON_NEGATIVE_INTEGER

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iNEGATIVE_INTEGER**

          static final int iNEGATIVE_INTEGER

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iINT**

          static final int iINT

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iSHORT**

          static final int iSHORT

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iBYTE**

          static final int iBYTE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iUNSIGNED_LONG**

          static final int iUNSIGNED_LONG

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iPOSITIVE_INTEGER**

          static final int iPOSITIVE_INTEGER

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iUNSIGNED_INT**

          static final int iUNSIGNED_INT

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iUNSIGNED_SHORT**

          static final int iUNSIGNED_SHORT

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iUNSIGNED_BYTE**

          static final int iUNSIGNED_BYTE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iN_STRING**

          static final int iN_STRING

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iTOKEN**

          static final int iTOKEN

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iLANGUAGE**

          static final int iLANGUAGE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iID**

          static final int iID

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iIDREF**

          static final int iIDREF

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iNMTOKEN**

          static final int iNMTOKEN

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iENTITY**

          static final int iENTITY

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iNAME**

          static final int iNAME

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iNCNAME**

          static final int iNCNAME

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iIDREFS**

          static final int iIDREFS

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iENTITIES**

          static final int iENTITIES

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iNMTOKENS**

          static final int iNMTOKENS

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **nBUILTIN**

          static final int nBUILTIN

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **sTypes**

          static final java.lang.String[] sTypes

      **Array of types indexed by above consts**

    - #### **ANY_SIMPLE**

          static final java.lang.String ANY_SIMPLE

    - #### **STRING**

          static final java.lang.String STRING

    - #### **BOOLEAN**

          static final java.lang.String BOOLEAN

    - #### **FLOAT**

          static final java.lang.String FLOAT

    - #### **DOUBLE**

          static final java.lang.String DOUBLE

    - #### **DECIMAL**

          static final java.lang.String DECIMAL

    - #### **DURATION**

          static final java.lang.String DURATION

    - #### **DATE_TIME**

          static final java.lang.String DATE_TIME

    - #### **TIME**

          static final java.lang.String TIME

    - #### **DATE**

          static final java.lang.String DATE

    - #### **GYEAR_MONTH**

          static final java.lang.String GYEAR_MONTH

    - #### **GYEAR**

          static final java.lang.String GYEAR

    - #### **GMONTH**

          static final java.lang.String GMONTH

    - #### **GMONTH_DAY**

          static final java.lang.String GMONTH_DAY

    - #### **GDAY**

          static final java.lang.String GDAY

    - #### **HEX_BINARY**

          static final java.lang.String HEX_BINARY

    - #### **BASE64_BINARY**

          static final java.lang.String BASE64_BINARY

    - #### **ANY_URI**

          static final java.lang.String ANY_URI

    - #### **QNAME**

          static final java.lang.String QNAME

    - #### **SNOTATION**

          static final java.lang.String SNOTATION

    - #### **N_STRING**

          static final java.lang.String N_STRING

      **Basic generated type derived from STRING**
      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **TOKEN**

          static final java.lang.String TOKEN

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **LANGUAGE**

          static final java.lang.String LANGUAGE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **ID**

          static final java.lang.String ID

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **IDREF**

          static final java.lang.String IDREF

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **NMTOKEN**

          static final java.lang.String NMTOKEN

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **ENTITY**

          static final java.lang.String ENTITY

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **NAME**

          static final java.lang.String NAME

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **NCNAME**

          static final java.lang.String NCNAME

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **IDREFS**

          static final java.lang.String IDREFS

      **Derived by List**
      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **ENTITIES**

          static final java.lang.String ENTITIES

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **NMTOKENS**

          static final java.lang.String NMTOKENS

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **INTEGER_STR**

          static final java.lang.String INTEGER_STR

      **Basic generated type derived from DECIMAL**
      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **NON_POSITIVE_INTEGER**

          static final java.lang.String NON_POSITIVE_INTEGER

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **LONG**

          static final java.lang.String LONG

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **NON_NEGATIVE_INTEGER**

          static final java.lang.String NON_NEGATIVE_INTEGER

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **NEGATIVE_INTEGER**

          static final java.lang.String NEGATIVE_INTEGER

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **INT**

          static final java.lang.String INT

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **SHORT**

          static final java.lang.String SHORT

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **BYTE**

          static final java.lang.String BYTE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **UNSIGNED_LONG**

          static final java.lang.String UNSIGNED_LONG

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **POSITIVE_INTEGER**

          static final java.lang.String POSITIVE_INTEGER

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **UNSIGNED_INT**

          static final java.lang.String UNSIGNED_INT

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **UNSIGNED_SHORT**

          static final java.lang.String UNSIGNED_SHORT

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **UNSIGNED_BYTE**

          static final java.lang.String UNSIGNED_BYTE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **YEARMONTH_DURATION**

          static final java.lang.String YEARMONTH_DURATION

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **DAYTIME_DURATION**

          static final java.lang.String DAYTIME_DURATION

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **UNTYPED_ATOMIC**

          static final java.lang.String UNTYPED_ATOMIC

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **CDATA**

          static final java.lang.String CDATA

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **URI_REFERENCE**

          static final java.lang.String URI_REFERENCE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **RECURRING_DURATION**

          static final java.lang.String RECURRING_DURATION

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **TIME_PERIOD**

          static final java.lang.String TIME_PERIOD

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **TIME_DURATION**

          static final java.lang.String TIME_DURATION

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **TIME_INSTANT**

          static final java.lang.String TIME_INSTANT

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **RECURRING_DATE**

          static final java.lang.String RECURRING_DATE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **RECURRING_DAY**

          static final java.lang.String RECURRING_DAY

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **CENTURY**

          static final java.lang.String CENTURY

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **YEAR**

          static final java.lang.String YEAR

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **MONTH**

          static final java.lang.String MONTH

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **BINARY**

          static final java.lang.String BINARY

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iDUMMY**

          static final int iDUMMY

      **Contraining Facet IDs**
      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iMININCLUSIVE**

          static final int iMININCLUSIVE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iMINEXCLUSIVE**

          static final int iMINEXCLUSIVE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iMAXINCLUSIVE**

          static final int iMAXINCLUSIVE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iMAXEXCLUSIVE**

          static final int iMAXEXCLUSIVE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iTOTAL_DIGITS**

          static final int iTOTAL_DIGITS

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iFRACTION_DIGITS**

          static final int iFRACTION_DIGITS

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iLENGTH**

          static final int iLENGTH

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iMAXLENGTH**

          static final int iMAXLENGTH

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iMINLENGTH**

          static final int iMINLENGTH

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iENUMERATION**

          static final int iENUMERATION

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iPATTERN**

          static final int iPATTERN

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **iWHITESPACE**

          static final int iWHITESPACE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **nFacets**

          static final int nFacets

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **fNUMERIC**

          static final int fNUMERIC

      **flags for foundamental Facet and other properties**
      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **fORDERED**

          static final int fORDERED

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **fFINITE**

          static final int fFINITE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **fID**

          static final int fID

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **fIDREF**

          static final int fIDREF

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **fINTEGER**

          static final int fINTEGER

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **fYEARMONTH**

          static final int fYEARMONTH

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **fDAYTIME**

          static final int fDAYTIME

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **sFacets**

          static final java.lang.String[] sFacets

      **Array of facet strings, can be indexed using the above const**

    - #### **MININCLUSIVE**

          static final java.lang.String MININCLUSIVE

    - #### **MINEXCLUSIVE**

          static final java.lang.String MINEXCLUSIVE

    - #### **MAXINCLUSIVE**

          static final java.lang.String MAXINCLUSIVE

    - #### **MAXEXCLUSIVE**

          static final java.lang.String MAXEXCLUSIVE

    - #### **TOTAL_DIGITS**

          static final java.lang.String TOTAL_DIGITS

    - #### **FRACTION_DIGITS**

          static final java.lang.String FRACTION_DIGITS

    - #### **LENGTH**

          static final java.lang.String LENGTH

    - #### **MAXLENGTH**

          static final java.lang.String MAXLENGTH

    - #### **MINLENGTH**

          static final java.lang.String MINLENGTH

    - #### **ENUMERATION**

          static final java.lang.String ENUMERATION

    - #### **PATTERN**

          static final java.lang.String PATTERN

    - #### **WHITESPACE**

          static final java.lang.String WHITESPACE

    - #### **ENCODING**

          static final java.lang.String ENCODING

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **PRECISION**

          static final java.lang.String PRECISION

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **SCALE**

          static final java.lang.String SCALE

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **PERIOD**

          static final java.lang.String PERIOD

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **\_atomic**

          static final java.lang.String _atomic

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **\_hex**

          static final java.lang.String _hex

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **\_base64**

          static final java.lang.String _base64

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **\_preserve**

          static final java.lang.String _preserve

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **\_collapse**

          static final java.lang.String _collapse

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **\_replace**

          static final java.lang.String _replace

      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

**Skip navigation links**

- **[Overview](../../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../../deprecated-list.md)**
- **[Index](../../../../index-all.md)**
- **[Help](../../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XSDSimpleType.md)**
- **[Next Class](XSDValidator.md)**

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
