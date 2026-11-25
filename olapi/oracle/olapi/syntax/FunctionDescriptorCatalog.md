Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](FunctionDescriptorArgument.md)
- [Next Class](FunctionDescriptorChoiceArgument.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.olapi.syntax

## Class FunctionDescriptorCatalog

- java.lang.Object

- - oracle.olapi.syntax.FunctionDescriptorCatalog

<!-- -->

-

  ------------------------------------------------------------------------



      public final class FunctionDescriptorCatalog
      extends java.lang.Object

  A catalog of functions that are represented by `Expression` objects. The `FunctionDescriptorCatalog` class has fields that represent `FunctionDescriptor` objects. When an application explicitly or implicitly creates an `Expression` for a function, Oracle OLAP creates a `FunctionDescriptor` for the function. The `FunctionDescriptor` has `FunctionDescriptorArgument` objects that describe the arguments of the function.
  The `FunctionDescriptorCatalog` class also has fields that represent categories of functions. For example, the `CHARACTER_CATEGORY` field represents functions that operate on objects with the data type such as `DataType.TEXT_CATEGORY` or `DataType.TEXT_LITERAL_CATEGORY`.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                      | Field and Description                                                                                                |
    |--------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ABS`<br>A static constant `FunctionDescriptor` representing the function `ABS`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ACOS`<br>A static constant `FunctionDescriptor` representing the function `ACOS`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ADD_MONTHS`<br>A static constant `FunctionDescriptor` representing the function `ADD_MONTHS`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `AGGREGATE`<br>A static constant `FunctionDescriptor` representing the function `AGGREGATE`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `AGGREGATION_AVG`<br>A static constant `FunctionDescriptor` representing the function `AVG`.                         |
    | `static java.lang.String`                              | `AGGREGATION_CATEGORY`<br>A static constant `String` for the AGGREGATION category of functions.                      |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `AGGREGATION_FIRST`<br>A static constant `FunctionDescriptor` representing the function `FIRST`.                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `AGGREGATION_LAST`<br>A static constant `FunctionDescriptor` representing the function `LAST`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `AGGREGATION_MAX`<br>A static constant `FunctionDescriptor` representing the function `MAX`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `AGGREGATION_MIN`<br>A static constant `FunctionDescriptor` representing the function `MIN`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `AGGREGATION_SUM`<br>A static constant `FunctionDescriptor` representing the function `SUM`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ASCII`<br>A static constant `FunctionDescriptor` representing the function `ASCII`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ASCIISTR`<br>A static constant `FunctionDescriptor` representing the function `ASCIISTR`.                           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ASIN`<br>A static constant `FunctionDescriptor` representing the function `ASIN`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ATAN`<br>A static constant `FunctionDescriptor` representing the function `ATAN`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ATAN2`<br>A static constant `FunctionDescriptor` representing the function `ATAN2`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `AVERAGE_RANK`<br>A static constant `FunctionDescriptor` representing the function `AVERAGE_RANK`.                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `BIN_TO_NUM`<br>A static constant `FunctionDescriptor` representing the function `BIN_TO_NUM`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `BITAND`<br>A static constant `FunctionDescriptor` representing the function `BITAND`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `CAST`<br>A static constant `FunctionDescriptor` representing the function `CAST`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `CEIL`<br>A static constant `FunctionDescriptor` representing the function `CEIL`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `CHAR_TO_CHAR`<br>A static constant `FunctionDescriptor` representing the function `TO_CHAR`.                        |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `CHAR_TO_NCHAR`<br>A static constant `FunctionDescriptor` representing the function `TO_NCHAR`.                      |
    | `static java.lang.String`                              | `CHARACTER_CATEGORY`<br>A static constant `String` for the CHARACTER category of functions.                          |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `CHARTOROWID`<br>A static constant `FunctionDescriptor` representing the function `CHARTOROWID`.                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `CHR`<br>A static constant `FunctionDescriptor` representing the function `CHR`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `COALESCE`<br>A static constant `FunctionDescriptor` representing the function `COALESCE`.                           |
    | `static java.lang.String`                              | `COMPARISON_CATEGORY`<br>A static constant `String` for the COMPARISON category of functions.                        |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `COMPOSE`<br>A static constant `FunctionDescriptor` representing the function `COMPOSE`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `CONCAT`<br>A static constant `FunctionDescriptor` representing the function `CONCAT`.                               |
    | `static java.lang.String`                              | `CONVERSION_CATEGORY`<br>A static constant `String` for the CONVERSION category of functions.                        |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `CONVERT`<br>A static constant `FunctionDescriptor` representing the function `CONVERT`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `COS`<br>A static constant `FunctionDescriptor` representing the function `COS`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `COSH`<br>A static constant `FunctionDescriptor` representing the function `COSH`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `CURRENT_DATE`<br>A static constant `FunctionDescriptor` representing the function `CURRENT_DATE`.                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `CURRENT_TIMESTAMP`<br>A static constant `FunctionDescriptor` representing the function `CURRENT_TIMESTAMP`.         |
    | `static java.lang.String`                              | `DATETIME_CATEGORY`<br>A static constant `String` for the DATETIME category of functions.                            |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `DATETIME_TO_CHAR`<br>A static constant `FunctionDescriptor` representing the function `TO_CHAR`.                    |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `DATETIME_TO_NCHAR`<br>A static constant `FunctionDescriptor` representing the function `TO_NCHAR`.                  |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `DBTIMEZONE`<br>A static constant `FunctionDescriptor` representing the function `DBTIMEZONE`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `DECODE`<br>A static constant `FunctionDescriptor` representing the function `DECODE`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `DECOMPOSE`<br>A static constant `FunctionDescriptor` representing the function `DECOMPOSE`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `DENSE_RANK`<br>A static constant `FunctionDescriptor` representing the function `DENSE_RANK`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `DUMP`<br>A static constant `FunctionDescriptor` representing the function `DUMP`.                                   |
    | `static java.lang.String`                              | `ENCODING_CATEGORY`<br>A static constant `String` for the ENCODING category of functions.                            |
    | `static java.lang.String`                              | `ENVIRONMENT_CATEGORY`<br>A static constant `String` for the ENVIRONMENT category of functions.                      |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `EXP`<br>A static constant `FunctionDescriptor` representing the function `EXP`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `EXTRACT_DATE`<br>A static constant `FunctionDescriptor` representing the function `EXTRACT`.                        |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `FLOOR`<br>A static constant `FunctionDescriptor` representing the function `FLOOR`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `FROM_TZ`<br>A static constant `FunctionDescriptor` representing the function `FROM_TZ`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `GREATEST`<br>A static constant `FunctionDescriptor` representing the function `GREATEST`.                           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HEXTORAW`<br>A static constant `FunctionDescriptor` representing the function `HEXTORAW`.                           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_ANCESTOR`<br>A static constant `FunctionDescriptor` representing the function `HIER_ANCESTOR`.                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_ANCESTORS`<br>A static constant `FunctionDescriptor` representing the function `HIER_ANCESTORS`.               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_AVG`<br>A static constant `FunctionDescriptor` representing the function `HIER_AVG`.                           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_CHILD_COUNT`<br>A static constant `FunctionDescriptor` representing the function `HIER_CHILD_COUNT`.           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_CHILDREN`<br>A static constant `FunctionDescriptor` representing the function `HIER_CHILDREN`.                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_DEPTH`<br>A static constant `FunctionDescriptor` representing the function `HIER_DEPTH`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_DESCENDANTS`<br>A static constant `FunctionDescriptor` representing the function `HIER_DESCENDANTS`.           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_FIRST`<br>A static constant `FunctionDescriptor` representing the function `HIER_FIRST`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_HAS_CHILDREN`<br>A static constant `FunctionDescriptor` representing the function `HIER_HAS_CHILDREN`.         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_LAST`<br>A static constant `FunctionDescriptor` representing the function `HIER_LAST`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_LEAF_DESCENDANTS`<br>A static constant `FunctionDescriptor` representing the function `HIER_LEAF_DESCENDANTS`. |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_LEVEL`<br>A static constant `FunctionDescriptor` representing the function `HIER_LEVEL`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_ORDER`<br>A static constant `FunctionDescriptor` representing the function `HIER_ORDER`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_PARENT`<br>A static constant `FunctionDescriptor` representing the function `HIER_PARENT`.                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_SIBLINGS`<br>A static constant `FunctionDescriptor` representing the function `HIER_SIBLINGS`.                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `HIER_TOP`<br>A static constant `FunctionDescriptor` representing the function `HIER_TOP`.                           |
    | `static java.lang.String`                              | `HIERARCHICAL_CATEGORY`<br>A static constant `String` for the HIERARCHICAL category of functions.                    |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `INITCAP`<br>A static constant `FunctionDescriptor` representing the function `INITCAP`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `INSTR`<br>A static constant `FunctionDescriptor` representing the function `INSTR`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `INSTR2`<br>A static constant `FunctionDescriptor` representing the function `INSTR2`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `INSTR4`<br>A static constant `FunctionDescriptor` representing the function `INSTR4`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `INSTRB`<br>A static constant `FunctionDescriptor` representing the function `INSTRB`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `INSTRC`<br>A static constant `FunctionDescriptor` representing the function `INSTRC`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `INTERVAL_TO_CHAR`<br>A static constant `FunctionDescriptor` representing the function `TO_CHAR`.                    |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `INTERVAL_TO_NCHAR`<br>A static constant `FunctionDescriptor` representing the function `TO_NCHAR`.                  |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LAG`<br>A static constant `FunctionDescriptor` representing the function `LAG`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LAG_VARIANCE`<br>A static constant `FunctionDescriptor` representing the function `LAG_VARIANCE`.                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LAG_VARIANCE_PERCENT`<br>A static constant `FunctionDescriptor` representing the function `LAG_VARIANCE_PERCENT`.   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LAST_DAY`<br>A static constant `FunctionDescriptor` representing the function `LAST_DAY`.                           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LEAD`<br>A static constant `FunctionDescriptor` representing the function `LEAD`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LEAD_VARIANCE`<br>A static constant `FunctionDescriptor` representing the function `LEAD_VARIANCE`.                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LEAD_VARIANCE_PERCENT`<br>A static constant `FunctionDescriptor` representing the function `LEAD_VARIANCE_PERCENT`. |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LEAST`<br>A static constant `FunctionDescriptor` representing the function `LEAST`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LENGTH`<br>A static constant `FunctionDescriptor` representing the function `LENGTH`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LENGTH2`<br>A static constant `FunctionDescriptor` representing the function `LENGTH2`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LENGTH4`<br>A static constant `FunctionDescriptor` representing the function `LENGTH4`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LENGTHB`<br>A static constant `FunctionDescriptor` representing the function `LENGTHB`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LENGTHC`<br>A static constant `FunctionDescriptor` representing the function `LENGTHC`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LN`<br>A static constant `FunctionDescriptor` representing the function `LN`.                                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LNNVL`<br>A static constant `FunctionDescriptor` representing the function `LNNVL`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LOCALTIMESTAMP`<br>A static constant `FunctionDescriptor` representing the function `LOCALTIMESTAMP`.               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LOG`<br>A static constant `FunctionDescriptor` representing the function `LOG`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LOWER`<br>A static constant `FunctionDescriptor` representing the function `LOWER`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LPAD`<br>A static constant `FunctionDescriptor` representing the function `LPAD`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `LTRIM`<br>A static constant `FunctionDescriptor` representing the function `LTRIM`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `MOD`<br>A static constant `FunctionDescriptor` representing the function `MOD`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `MONTHS_BETWEEN`<br>A static constant `FunctionDescriptor` representing the function `MONTHS_BETWEEN`.               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NANVL`<br>A static constant `FunctionDescriptor` representing the function `NANVL`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NEW_TIME`<br>A static constant `FunctionDescriptor` representing the function `NEW_TIME`.                           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NEXT_DAY`<br>A static constant `FunctionDescriptor` representing the function `NEXT_DAY`.                           |
    | `static java.lang.String`                              | `NLS_CATEGORY`<br>A static constant `String` for the NLS category of functions.                                      |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NLS_CHARSET_DECL_LEN`<br>A static constant `FunctionDescriptor` representing the function `NLS_CHARSET_DECL_LEN`.   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NLS_CHARSET_ID`<br>A static constant `FunctionDescriptor` representing the function `NLS_CHARSET_ID`.               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NLS_CHARSET_NAME`<br>A static constant `FunctionDescriptor` representing the function `NLS_CHARSET_NAME`.           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NLS_INITCAP`<br>A static constant `FunctionDescriptor` representing the function `NLS_INITCAP`.                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NLS_LOWER`<br>A static constant `FunctionDescriptor` representing the function `NLS_LOWER`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NLS_UPPER`<br>A static constant `FunctionDescriptor` representing the function `NLS_UPPER`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NLSSORT`<br>A static constant `FunctionDescriptor` representing the function `NLSSORT`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NO_AGGREGATE`<br>A static constant `FunctionDescriptor` representing the function `NO AGGREGATE`.                   |
    | `static java.lang.String`                              | `NULL_RELATED_CATEGORY`<br>A static constant `String` for the NULL RELATED category of functions.                    |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NULLIF`<br>A static constant `FunctionDescriptor` representing the function `NULLIF`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NUMBER_TO_CHAR`<br>A static constant `FunctionDescriptor` representing the function `TO_CHAR`.                      |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NUMBER_TO_NCHAR`<br>A static constant `FunctionDescriptor` representing the function `TO_NCHAR`.                    |
    | `static java.lang.String`                              | `NUMERIC_CATEGORY`<br>A static constant `String` for the NUMERIC category of functions.                              |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NUMTODSINTERVAL`<br>A static constant `FunctionDescriptor` representing the function `NUMTODSINTERVAL`.             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NUMTOYMINTERVAL`<br>A static constant `FunctionDescriptor` representing the function `NUMTOYMINTERVAL`.             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NVL`<br>A static constant `FunctionDescriptor` representing the function `NVL`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `NVL2`<br>A static constant `FunctionDescriptor` representing the function `NVL2`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `OLAP_AVG`<br>A static constant `FunctionDescriptor` representing the function `AVG`.                                |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `OLAP_COUNT`<br>A static constant `FunctionDescriptor` representing the function `COUNT`.                            |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `OLAP_MAX`<br>A static constant `FunctionDescriptor` representing the function `MAX`.                                |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `OLAP_MIN`<br>A static constant `FunctionDescriptor` representing the function `MIN`.                                |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `OLAP_SUM`<br>A static constant `FunctionDescriptor` representing the function `SUM`.                                |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ORA_HASH`<br>A static constant `FunctionDescriptor` representing the function `ORA_HASH`.                           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `POWER`<br>A static constant `FunctionDescriptor` representing the function `POWER`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `RANK`<br>A static constant `FunctionDescriptor` representing the function `RANK`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `RAWTOHEX`<br>A static constant `FunctionDescriptor` representing the function `RAWTOHEX`.                           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `RAWTONHEX`<br>A static constant `FunctionDescriptor` representing the function `RAWTONHEX`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `REGEXP_COUNT`<br>A static constant `FunctionDescriptor` representing the function `REGEXP_COUNT`.                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `REGEXP_INSTR`<br>A static constant `FunctionDescriptor` representing the function `REGEXP_INSTR`.                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `REGEXP_REPLACE`<br>A static constant `FunctionDescriptor` representing the function `REGEXP_REPLACE`.               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `REGEXP_SUBSTR`<br>A static constant `FunctionDescriptor` representing the function `REGEXP_SUBSTR`.                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `REMAINDER`<br>A static constant `FunctionDescriptor` representing the function `REMAINDER`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `REPLACE`<br>A static constant `FunctionDescriptor` representing the function `REPLACE`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ROUND_DATE`<br>A static constant `FunctionDescriptor` representing the function `ROUND`.                            |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ROUND_NUMBER`<br>A static constant `FunctionDescriptor` representing the function `ROUND`.                          |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ROW_NUMBER`<br>A static constant `FunctionDescriptor` representing the function `ROW_NUMBER`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ROWIDTOCHAR`<br>A static constant `FunctionDescriptor` representing the function `ROWIDTOCHAR`.                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `ROWIDTONCHAR`<br>A static constant `FunctionDescriptor` representing the function `ROWIDTONCHAR`.                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `RPAD`<br>A static constant `FunctionDescriptor` representing the function `RPAD`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `RTRIM`<br>A static constant `FunctionDescriptor` representing the function `RTRIM`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SCN_TO_TIMESTAMP`<br>A static constant `FunctionDescriptor` representing the function `SCN_TO_TIMESTAMP`.           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SESSIONTIMEZONE`<br>A static constant `FunctionDescriptor` representing the function `SESSIONTIMEZONE`.             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SHARE`<br>A static constant `FunctionDescriptor` representing the function `SHARE`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SIGN`<br>A static constant `FunctionDescriptor` representing the function `SIGN`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SIN`<br>A static constant `FunctionDescriptor` representing the function `SIN`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SINH`<br>A static constant `FunctionDescriptor` representing the function `SINH`.                                   |
    | `static java.lang.String`                              | `SOLVE_CATEGORY`<br>A static constant `String` for the SOLVE category of functions.                                  |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SOUNDEX`<br>A static constant `FunctionDescriptor` representing the function `SOUNDEX`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SQRT`<br>A static constant `FunctionDescriptor` representing the function `SQRT`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SUBSTR`<br>A static constant `FunctionDescriptor` representing the function `SUBSTR`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SUBSTR2`<br>A static constant `FunctionDescriptor` representing the function `SUBSTR2`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SUBSTR4`<br>A static constant `FunctionDescriptor` representing the function `SUBSTR4`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SUBSTRB`<br>A static constant `FunctionDescriptor` representing the function `SUBSTRB`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SUBSTRC`<br>A static constant `FunctionDescriptor` representing the function `SUBSTRC`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SYS_CONTEXT`<br>A static constant `FunctionDescriptor` representing the function `SYS_CONTEXT`.                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SYS_EXTRACT_UTC`<br>A static constant `FunctionDescriptor` representing the function `SYS_EXTRACT_UTC`.             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SYS_GUID`<br>A static constant `FunctionDescriptor` representing the function `SYS_GUID`.                           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SYS_TYPEID`<br>A static constant `FunctionDescriptor` representing the function `SYS_TYPEID`.                       |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SYSDATE`<br>A static constant `FunctionDescriptor` representing the function `SYSDATE`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `SYSTIMESTAMP`<br>A static constant `FunctionDescriptor` representing the function `SYSTIMESTAMP`.                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TAN`<br>A static constant `FunctionDescriptor` representing the function `TAN`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TANH`<br>A static constant `FunctionDescriptor` representing the function `TANH`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TIMESTAMP_TO_SCN`<br>A static constant `FunctionDescriptor` representing the function `TIMESTAMP_TO_SCN`.           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_BINARY_DOUBLE`<br>A static constant `FunctionDescriptor` representing the function `TO_BINARY_DOUBLE`.           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_BINARY_FLOAT`<br>A static constant `FunctionDescriptor` representing the function `TO_BINARY_FLOAT`.             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_CLOB`<br>A static constant `FunctionDescriptor` representing the function `TO_CLOB`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_DATE`<br>A static constant `FunctionDescriptor` representing the function `TO_DATE`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_DSINTERVAL`<br>A static constant `FunctionDescriptor` representing the function `TO_DSINTERVAL`.                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_LOB`<br>A static constant `FunctionDescriptor` representing the function `TO_LOB`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_MULTI_BYTE`<br>A static constant `FunctionDescriptor` representing the function `TO_MULTI_BYTE`.                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_NCLOB`<br>A static constant `FunctionDescriptor` representing the function `TO_NCLOB`.                           |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_NUMBER`<br>A static constant `FunctionDescriptor` representing the function `TO_NUMBER`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_SINGLE_BYTE`<br>A static constant `FunctionDescriptor` representing the function `TO_SINGLE_BYTE`.               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_TIMESTAMP`<br>A static constant `FunctionDescriptor` representing the function `TO_TIMESTAMP`.                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_TIMESTAMP_TZ`<br>A static constant `FunctionDescriptor` representing the function `TO_TIMESTAMP_TZ`.             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TO_YMINTERVAL`<br>A static constant `FunctionDescriptor` representing the function `TO_YMINTERVAL`.                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TRANSLATE`<br>A static constant `FunctionDescriptor` representing the function `TRANSLATE`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TRANSLATE_USING`<br>A static constant `FunctionDescriptor` representing the function `TRANSLATE`.                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TREAT`<br>A static constant `FunctionDescriptor` representing the function `TREAT`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TRIM`<br>A static constant `FunctionDescriptor` representing the function `TRIM`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TRUNC_DATE`<br>A static constant `FunctionDescriptor` representing the function `TRUNC`.                            |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TRUNC_NUMBER`<br>A static constant `FunctionDescriptor` representing the function `TRUNC`.                          |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `TZ_OFFSET`<br>A static constant `FunctionDescriptor` representing the function `TZ_OFFSET`.                         |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `UID`<br>A static constant `FunctionDescriptor` representing the function `UID`.                                     |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `UNISTR`<br>A static constant `FunctionDescriptor` representing the function `UNISTR`.                               |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `UPPER`<br>A static constant `FunctionDescriptor` representing the function `UPPER`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `USER`<br>A static constant `FunctionDescriptor` representing the function `USER`.                                   |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `USERENV`<br>A static constant `FunctionDescriptor` representing the function `USERENV`.                             |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `VSIZE`<br>A static constant `FunctionDescriptor` representing the function `VSIZE`.                                 |
    | `static `[`FunctionDescriptor`](FunctionDescriptor.md) | `WIDTH_BUCKET`<br>A static constant `FunctionDescriptor` representing the function `WIDTH_BUCKET`.                   |
    | `static java.lang.String`                              | `WINDOW_CATEGORY`<br>A static constant `String` for the WINDOW category of functions.                                |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### HIERARCHICAL_CATEGORY

          public static final java.lang.String HIERARCHICAL_CATEGORY

      A static constant `String` for the HIERARCHICAL category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### WINDOW_CATEGORY

          public static final java.lang.String WINDOW_CATEGORY

      A static constant `String` for the WINDOW category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NUMERIC_CATEGORY

          public static final java.lang.String NUMERIC_CATEGORY

      A static constant `String` for the NUMERIC category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CHARACTER_CATEGORY

          public static final java.lang.String CHARACTER_CATEGORY

      A static constant `String` for the CHARACTER category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NLS_CATEGORY

          public static final java.lang.String NLS_CATEGORY

      A static constant `String` for the NLS category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DATETIME_CATEGORY

          public static final java.lang.String DATETIME_CATEGORY

      A static constant `String` for the DATETIME category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPARISON_CATEGORY

          public static final java.lang.String COMPARISON_CATEGORY

      A static constant `String` for the COMPARISON category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONVERSION_CATEGORY

          public static final java.lang.String CONVERSION_CATEGORY

      A static constant `String` for the CONVERSION category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENCODING_CATEGORY

          public static final java.lang.String ENCODING_CATEGORY

      A static constant `String` for the ENCODING category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NULL_RELATED_CATEGORY

          public static final java.lang.String NULL_RELATED_CATEGORY

      A static constant `String` for the NULL RELATED category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENVIRONMENT_CATEGORY

          public static final java.lang.String ENVIRONMENT_CATEGORY

      A static constant `String` for the ENVIRONMENT category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SOLVE_CATEGORY

          public static final java.lang.String SOLVE_CATEGORY

      A static constant `String` for the SOLVE category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AGGREGATION_CATEGORY

          public static final java.lang.String AGGREGATION_CATEGORY

      A static constant `String` for the AGGREGATION category of functions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### HIER_PARENT

          public static final FunctionDescriptor HIER_PARENT

      A static constant `FunctionDescriptor` representing the function `HIER_PARENT`.

    <!-- -->

    - #### HIER_CHILD_COUNT

          public static final FunctionDescriptor HIER_CHILD_COUNT

      A static constant `FunctionDescriptor` representing the function `HIER_CHILD_COUNT`.

    <!-- -->

    - #### HIER_DEPTH

          public static final FunctionDescriptor HIER_DEPTH

      A static constant `FunctionDescriptor` representing the function `HIER_DEPTH`.

    <!-- -->

    - #### HIER_TOP

          public static final FunctionDescriptor HIER_TOP

      A static constant `FunctionDescriptor` representing the function `HIER_TOP`.

    <!-- -->

    - #### HIER_ORDER

          public static final FunctionDescriptor HIER_ORDER

      A static constant `FunctionDescriptor` representing the function `HIER_ORDER`.

    <!-- -->

    - #### HIER_HAS_CHILDREN

          public static final FunctionDescriptor HIER_HAS_CHILDREN

      A static constant `FunctionDescriptor` representing the function `HIER_HAS_CHILDREN`.

    <!-- -->

    - #### HIER_LEVEL

          public static final FunctionDescriptor HIER_LEVEL

      A static constant `FunctionDescriptor` representing the function `HIER_LEVEL`.

    <!-- -->

    - #### HIER_ANCESTOR

          public static final FunctionDescriptor HIER_ANCESTOR

      A static constant `FunctionDescriptor` representing the function `HIER_ANCESTOR`.

    <!-- -->

    - #### HIER_ANCESTORS

          public static final FunctionDescriptor HIER_ANCESTORS

      A static constant `FunctionDescriptor` representing the function `HIER_ANCESTORS`.

    <!-- -->

    - #### HIER_DESCENDANTS

          public static final FunctionDescriptor HIER_DESCENDANTS

      A static constant `FunctionDescriptor` representing the function `HIER_DESCENDANTS`.

    <!-- -->

    - #### HIER_LEAF_DESCENDANTS

          public static final FunctionDescriptor HIER_LEAF_DESCENDANTS

      A static constant `FunctionDescriptor` representing the function `HIER_LEAF_DESCENDANTS`.

    <!-- -->

    - #### HIER_CHILDREN

          public static final FunctionDescriptor HIER_CHILDREN

      A static constant `FunctionDescriptor` representing the function `HIER_CHILDREN`.

    <!-- -->

    - #### HIER_SIBLINGS

          public static final FunctionDescriptor HIER_SIBLINGS

      A static constant `FunctionDescriptor` representing the function `HIER_SIBLINGS`.

    <!-- -->

    - #### SHARE

          public static final FunctionDescriptor SHARE

      A static constant `FunctionDescriptor` representing the function `SHARE`.

    <!-- -->

    - #### LAG

          public static final FunctionDescriptor LAG

      A static constant `FunctionDescriptor` representing the function `LAG`.

    <!-- -->

    - #### LAG_VARIANCE_PERCENT

          public static final FunctionDescriptor LAG_VARIANCE_PERCENT

      A static constant `FunctionDescriptor` representing the function `LAG_VARIANCE_PERCENT`.

    <!-- -->

    - #### LAG_VARIANCE

          public static final FunctionDescriptor LAG_VARIANCE

      A static constant `FunctionDescriptor` representing the function `LAG_VARIANCE`.

    <!-- -->

    - #### LEAD

          public static final FunctionDescriptor LEAD

      A static constant `FunctionDescriptor` representing the function `LEAD`.

    <!-- -->

    - #### LEAD_VARIANCE_PERCENT

          public static final FunctionDescriptor LEAD_VARIANCE_PERCENT

      A static constant `FunctionDescriptor` representing the function `LEAD_VARIANCE_PERCENT`.

    <!-- -->

    - #### LEAD_VARIANCE

          public static final FunctionDescriptor LEAD_VARIANCE

      A static constant `FunctionDescriptor` representing the function `LEAD_VARIANCE`.

    <!-- -->

    - #### OLAP_SUM

          public static final FunctionDescriptor OLAP_SUM

      A static constant `FunctionDescriptor` representing the function `SUM`.

    <!-- -->

    - #### OLAP_AVG

          public static final FunctionDescriptor OLAP_AVG

      A static constant `FunctionDescriptor` representing the function `AVG`.

    <!-- -->

    - #### OLAP_MAX

          public static final FunctionDescriptor OLAP_MAX

      A static constant `FunctionDescriptor` representing the function `MAX`.

    <!-- -->

    - #### OLAP_MIN

          public static final FunctionDescriptor OLAP_MIN

      A static constant `FunctionDescriptor` representing the function `MIN`.

    <!-- -->

    - #### OLAP_COUNT

          public static final FunctionDescriptor OLAP_COUNT

      A static constant `FunctionDescriptor` representing the function `COUNT`.

    <!-- -->

    - #### RANK

          public static final FunctionDescriptor RANK

      A static constant `FunctionDescriptor` representing the function `RANK`.

    <!-- -->

    - #### DENSE_RANK

          public static final FunctionDescriptor DENSE_RANK

      A static constant `FunctionDescriptor` representing the function `DENSE_RANK`.

    <!-- -->

    - #### AVERAGE_RANK

          public static final FunctionDescriptor AVERAGE_RANK

      A static constant `FunctionDescriptor` representing the function `AVERAGE_RANK`.

    <!-- -->

    - #### ROW_NUMBER

          public static final FunctionDescriptor ROW_NUMBER

      A static constant `FunctionDescriptor` representing the function `ROW_NUMBER`.

    <!-- -->

    - #### ABS

          public static final FunctionDescriptor ABS

      A static constant `FunctionDescriptor` representing the function `ABS`.

    <!-- -->

    - #### ACOS

          public static final FunctionDescriptor ACOS

      A static constant `FunctionDescriptor` representing the function `ACOS`.

    <!-- -->

    - #### ASIN

          public static final FunctionDescriptor ASIN

      A static constant `FunctionDescriptor` representing the function `ASIN`.

    <!-- -->

    - #### ATAN

          public static final FunctionDescriptor ATAN

      A static constant `FunctionDescriptor` representing the function `ATAN`.

    <!-- -->

    - #### ATAN2

          public static final FunctionDescriptor ATAN2

      A static constant `FunctionDescriptor` representing the function `ATAN2`.

    <!-- -->

    - #### BITAND

          public static final FunctionDescriptor BITAND

      A static constant `FunctionDescriptor` representing the function `BITAND`.

    <!-- -->

    - #### CEIL

          public static final FunctionDescriptor CEIL

      A static constant `FunctionDescriptor` representing the function `CEIL`.

    <!-- -->

    - #### COS

          public static final FunctionDescriptor COS

      A static constant `FunctionDescriptor` representing the function `COS`.

    <!-- -->

    - #### COSH

          public static final FunctionDescriptor COSH

      A static constant `FunctionDescriptor` representing the function `COSH`.

    <!-- -->

    - #### EXP

          public static final FunctionDescriptor EXP

      A static constant `FunctionDescriptor` representing the function `EXP`.

    <!-- -->

    - #### FLOOR

          public static final FunctionDescriptor FLOOR

      A static constant `FunctionDescriptor` representing the function `FLOOR`.

    <!-- -->

    - #### LN

          public static final FunctionDescriptor LN

      A static constant `FunctionDescriptor` representing the function `LN`.

    <!-- -->

    - #### LOG

          public static final FunctionDescriptor LOG

      A static constant `FunctionDescriptor` representing the function `LOG`.

    <!-- -->

    - #### MOD

          public static final FunctionDescriptor MOD

      A static constant `FunctionDescriptor` representing the function `MOD`.

    <!-- -->

    - #### NANVL

          public static final FunctionDescriptor NANVL

      A static constant `FunctionDescriptor` representing the function `NANVL`.

    <!-- -->

    - #### POWER

          public static final FunctionDescriptor POWER

      A static constant `FunctionDescriptor` representing the function `POWER`.

    <!-- -->

    - #### REMAINDER

          public static final FunctionDescriptor REMAINDER

      A static constant `FunctionDescriptor` representing the function `REMAINDER`.

    <!-- -->

    - #### ROUND_NUMBER

          public static final FunctionDescriptor ROUND_NUMBER

      A static constant `FunctionDescriptor` representing the function `ROUND`.

    <!-- -->

    - #### SIGN

          public static final FunctionDescriptor SIGN

      A static constant `FunctionDescriptor` representing the function `SIGN`.

    <!-- -->

    - #### SIN

          public static final FunctionDescriptor SIN

      A static constant `FunctionDescriptor` representing the function `SIN`.

    <!-- -->

    - #### SINH

          public static final FunctionDescriptor SINH

      A static constant `FunctionDescriptor` representing the function `SINH`.

    <!-- -->

    - #### SQRT

          public static final FunctionDescriptor SQRT

      A static constant `FunctionDescriptor` representing the function `SQRT`.

    <!-- -->

    - #### TAN

          public static final FunctionDescriptor TAN

      A static constant `FunctionDescriptor` representing the function `TAN`.

    <!-- -->

    - #### TANH

          public static final FunctionDescriptor TANH

      A static constant `FunctionDescriptor` representing the function `TANH`.

    <!-- -->

    - #### TRUNC_NUMBER

          public static final FunctionDescriptor TRUNC_NUMBER

      A static constant `FunctionDescriptor` representing the function `TRUNC`.

    <!-- -->

    - #### WIDTH_BUCKET

          public static final FunctionDescriptor WIDTH_BUCKET

      A static constant `FunctionDescriptor` representing the function `WIDTH_BUCKET`.

    <!-- -->

    - #### ASCII

          public static final FunctionDescriptor ASCII

      A static constant `FunctionDescriptor` representing the function `ASCII`.

    <!-- -->

    - #### CHR

          public static final FunctionDescriptor CHR

      A static constant `FunctionDescriptor` representing the function `CHR`.

    <!-- -->

    - #### CONCAT

          public static final FunctionDescriptor CONCAT

      A static constant `FunctionDescriptor` representing the function `CONCAT`.

    <!-- -->

    - #### INITCAP

          public static final FunctionDescriptor INITCAP

      A static constant `FunctionDescriptor` representing the function `INITCAP`.

    <!-- -->

    - #### INSTR

          public static final FunctionDescriptor INSTR

      A static constant `FunctionDescriptor` representing the function `INSTR`.

    <!-- -->

    - #### INSTRB

          public static final FunctionDescriptor INSTRB

      A static constant `FunctionDescriptor` representing the function `INSTRB`.

    <!-- -->

    - #### INSTRC

          public static final FunctionDescriptor INSTRC

      A static constant `FunctionDescriptor` representing the function `INSTRC`.

    <!-- -->

    - #### INSTR2

          public static final FunctionDescriptor INSTR2

      A static constant `FunctionDescriptor` representing the function `INSTR2`.

    <!-- -->

    - #### INSTR4

          public static final FunctionDescriptor INSTR4

      A static constant `FunctionDescriptor` representing the function `INSTR4`.

    <!-- -->

    - #### LENGTH

          public static final FunctionDescriptor LENGTH

      A static constant `FunctionDescriptor` representing the function `LENGTH`.

    <!-- -->

    - #### LENGTHB

          public static final FunctionDescriptor LENGTHB

      A static constant `FunctionDescriptor` representing the function `LENGTHB`.

    <!-- -->

    - #### LENGTHC

          public static final FunctionDescriptor LENGTHC

      A static constant `FunctionDescriptor` representing the function `LENGTHC`.

    <!-- -->

    - #### LENGTH2

          public static final FunctionDescriptor LENGTH2

      A static constant `FunctionDescriptor` representing the function `LENGTH2`.

    <!-- -->

    - #### LENGTH4

          public static final FunctionDescriptor LENGTH4

      A static constant `FunctionDescriptor` representing the function `LENGTH4`.

    <!-- -->

    - #### LOWER

          public static final FunctionDescriptor LOWER

      A static constant `FunctionDescriptor` representing the function `LOWER`.

    <!-- -->

    - #### UPPER

          public static final FunctionDescriptor UPPER

      A static constant `FunctionDescriptor` representing the function `UPPER`.

    <!-- -->

    - #### LPAD

          public static final FunctionDescriptor LPAD

      A static constant `FunctionDescriptor` representing the function `LPAD`.

    <!-- -->

    - #### RPAD

          public static final FunctionDescriptor RPAD

      A static constant `FunctionDescriptor` representing the function `RPAD`.

    <!-- -->

    - #### LTRIM

          public static final FunctionDescriptor LTRIM

      A static constant `FunctionDescriptor` representing the function `LTRIM`.

    <!-- -->

    - #### RTRIM

          public static final FunctionDescriptor RTRIM

      A static constant `FunctionDescriptor` representing the function `RTRIM`.

    <!-- -->

    - #### NLS_INITCAP

          public static final FunctionDescriptor NLS_INITCAP

      A static constant `FunctionDescriptor` representing the function `NLS_INITCAP`.

    <!-- -->

    - #### NLSSORT

          public static final FunctionDescriptor NLSSORT

      A static constant `FunctionDescriptor` representing the function `NLSSORT`.

    <!-- -->

    - #### NLS_LOWER

          public static final FunctionDescriptor NLS_LOWER

      A static constant `FunctionDescriptor` representing the function `NLS_LOWER`.

    <!-- -->

    - #### NLS_UPPER

          public static final FunctionDescriptor NLS_UPPER

      A static constant `FunctionDescriptor` representing the function `NLS_UPPER`.

    <!-- -->

    - #### REGEXP_INSTR

          public static final FunctionDescriptor REGEXP_INSTR

      A static constant `FunctionDescriptor` representing the function `REGEXP_INSTR`.

    <!-- -->

    - #### REGEXP_COUNT

          public static final FunctionDescriptor REGEXP_COUNT

      A static constant `FunctionDescriptor` representing the function `REGEXP_COUNT`.

    <!-- -->

    - #### REGEXP_REPLACE

          public static final FunctionDescriptor REGEXP_REPLACE

      A static constant `FunctionDescriptor` representing the function `REGEXP_REPLACE`.

    <!-- -->

    - #### REGEXP_SUBSTR

          public static final FunctionDescriptor REGEXP_SUBSTR

      A static constant `FunctionDescriptor` representing the function `REGEXP_SUBSTR`.

    <!-- -->

    - #### REPLACE

          public static final FunctionDescriptor REPLACE

      A static constant `FunctionDescriptor` representing the function `REPLACE`.

    <!-- -->

    - #### SOUNDEX

          public static final FunctionDescriptor SOUNDEX

      A static constant `FunctionDescriptor` representing the function `SOUNDEX`.

    <!-- -->

    - #### SUBSTR

          public static final FunctionDescriptor SUBSTR

      A static constant `FunctionDescriptor` representing the function `SUBSTR`.

    <!-- -->

    - #### SUBSTRB

          public static final FunctionDescriptor SUBSTRB

      A static constant `FunctionDescriptor` representing the function `SUBSTRB`.

    <!-- -->

    - #### SUBSTRC

          public static final FunctionDescriptor SUBSTRC

      A static constant `FunctionDescriptor` representing the function `SUBSTRC`.

    <!-- -->

    - #### SUBSTR2

          public static final FunctionDescriptor SUBSTR2

      A static constant `FunctionDescriptor` representing the function `SUBSTR2`.

    <!-- -->

    - #### SUBSTR4

          public static final FunctionDescriptor SUBSTR4

      A static constant `FunctionDescriptor` representing the function `SUBSTR4`.

    <!-- -->

    - #### TRANSLATE

          public static final FunctionDescriptor TRANSLATE

      A static constant `FunctionDescriptor` representing the function `TRANSLATE`.

    <!-- -->

    - #### TREAT

          public static final FunctionDescriptor TREAT

      A static constant `FunctionDescriptor` representing the function `TREAT`.

    <!-- -->

    - #### TRIM

          public static final FunctionDescriptor TRIM

      A static constant `FunctionDescriptor` representing the function `TRIM`.

    <!-- -->

    - #### NLS_CHARSET_DECL_LEN

          public static final FunctionDescriptor NLS_CHARSET_DECL_LEN

      A static constant `FunctionDescriptor` representing the function `NLS_CHARSET_DECL_LEN`.

    <!-- -->

    - #### NLS_CHARSET_ID

          public static final FunctionDescriptor NLS_CHARSET_ID

      A static constant `FunctionDescriptor` representing the function `NLS_CHARSET_ID`.

    <!-- -->

    - #### NLS_CHARSET_NAME

          public static final FunctionDescriptor NLS_CHARSET_NAME

      A static constant `FunctionDescriptor` representing the function `NLS_CHARSET_NAME`.

    <!-- -->

    - #### ADD_MONTHS

          public static final FunctionDescriptor ADD_MONTHS

      A static constant `FunctionDescriptor` representing the function `ADD_MONTHS`.

    <!-- -->

    - #### CURRENT_DATE

          public static final FunctionDescriptor CURRENT_DATE

      A static constant `FunctionDescriptor` representing the function `CURRENT_DATE`.

    <!-- -->

    - #### CURRENT_TIMESTAMP

          public static final FunctionDescriptor CURRENT_TIMESTAMP

      A static constant `FunctionDescriptor` representing the function `CURRENT_TIMESTAMP`.

    <!-- -->

    - #### DBTIMEZONE

          public static final FunctionDescriptor DBTIMEZONE

      A static constant `FunctionDescriptor` representing the function `DBTIMEZONE`.

    <!-- -->

    - #### EXTRACT_DATE

          public static final FunctionDescriptor EXTRACT_DATE

      A static constant `FunctionDescriptor` representing the function `EXTRACT`.

    <!-- -->

    - #### FROM_TZ

          public static final FunctionDescriptor FROM_TZ

      A static constant `FunctionDescriptor` representing the function `FROM_TZ`.

    <!-- -->

    - #### LAST_DAY

          public static final FunctionDescriptor LAST_DAY

      A static constant `FunctionDescriptor` representing the function `LAST_DAY`.

    <!-- -->

    - #### LOCALTIMESTAMP

          public static final FunctionDescriptor LOCALTIMESTAMP

      A static constant `FunctionDescriptor` representing the function `LOCALTIMESTAMP`.

    <!-- -->

    - #### MONTHS_BETWEEN

          public static final FunctionDescriptor MONTHS_BETWEEN

      A static constant `FunctionDescriptor` representing the function `MONTHS_BETWEEN`.

    <!-- -->

    - #### NEW_TIME

          public static final FunctionDescriptor NEW_TIME

      A static constant `FunctionDescriptor` representing the function `NEW_TIME`.

    <!-- -->

    - #### NEXT_DAY

          public static final FunctionDescriptor NEXT_DAY

      A static constant `FunctionDescriptor` representing the function `NEXT_DAY`.

    <!-- -->

    - #### ROUND_DATE

          public static final FunctionDescriptor ROUND_DATE

      A static constant `FunctionDescriptor` representing the function `ROUND`.

    <!-- -->

    - #### TRUNC_DATE

          public static final FunctionDescriptor TRUNC_DATE

      A static constant `FunctionDescriptor` representing the function `TRUNC`.

    <!-- -->

    - #### SESSIONTIMEZONE

          public static final FunctionDescriptor SESSIONTIMEZONE

      A static constant `FunctionDescriptor` representing the function `SESSIONTIMEZONE`.

    <!-- -->

    - #### SYS_EXTRACT_UTC

          public static final FunctionDescriptor SYS_EXTRACT_UTC

      A static constant `FunctionDescriptor` representing the function `SYS_EXTRACT_UTC`.

    <!-- -->

    - #### SYSDATE

          public static final FunctionDescriptor SYSDATE

      A static constant `FunctionDescriptor` representing the function `SYSDATE`.

    <!-- -->

    - #### SYSTIMESTAMP

          public static final FunctionDescriptor SYSTIMESTAMP

      A static constant `FunctionDescriptor` representing the function `SYSTIMESTAMP`.

    <!-- -->

    - #### TO_DSINTERVAL

          public static final FunctionDescriptor TO_DSINTERVAL

      A static constant `FunctionDescriptor` representing the function `TO_DSINTERVAL`.

    <!-- -->

    - #### TO_TIMESTAMP

          public static final FunctionDescriptor TO_TIMESTAMP

      A static constant `FunctionDescriptor` representing the function `TO_TIMESTAMP`.

    <!-- -->

    - #### TO_TIMESTAMP_TZ

          public static final FunctionDescriptor TO_TIMESTAMP_TZ

      A static constant `FunctionDescriptor` representing the function `TO_TIMESTAMP_TZ`.

    <!-- -->

    - #### TO_YMINTERVAL

          public static final FunctionDescriptor TO_YMINTERVAL

      A static constant `FunctionDescriptor` representing the function `TO_YMINTERVAL`.

    <!-- -->

    - #### TZ_OFFSET

          public static final FunctionDescriptor TZ_OFFSET

      A static constant `FunctionDescriptor` representing the function `TZ_OFFSET`.

    <!-- -->

    - #### GREATEST

          public static final FunctionDescriptor GREATEST

      A static constant `FunctionDescriptor` representing the function `GREATEST`.

    <!-- -->

    - #### LEAST

          public static final FunctionDescriptor LEAST

      A static constant `FunctionDescriptor` representing the function `LEAST`.

    <!-- -->

    - #### ASCIISTR

          public static final FunctionDescriptor ASCIISTR

      A static constant `FunctionDescriptor` representing the function `ASCIISTR`.

    <!-- -->

    - #### BIN_TO_NUM

          public static final FunctionDescriptor BIN_TO_NUM

      A static constant `FunctionDescriptor` representing the function `BIN_TO_NUM`.

    <!-- -->

    - #### CAST

          public static final FunctionDescriptor CAST

      A static constant `FunctionDescriptor` representing the function `CAST`.

    <!-- -->

    - #### CHARTOROWID

          public static final FunctionDescriptor CHARTOROWID

      A static constant `FunctionDescriptor` representing the function `CHARTOROWID`.

    <!-- -->

    - #### COMPOSE

          public static final FunctionDescriptor COMPOSE

      A static constant `FunctionDescriptor` representing the function `COMPOSE`.

    <!-- -->

    - #### CONVERT

          public static final FunctionDescriptor CONVERT

      A static constant `FunctionDescriptor` representing the function `CONVERT`.

    <!-- -->

    - #### DECOMPOSE

          public static final FunctionDescriptor DECOMPOSE

      A static constant `FunctionDescriptor` representing the function `DECOMPOSE`.

    <!-- -->

    - #### HEXTORAW

          public static final FunctionDescriptor HEXTORAW

      A static constant `FunctionDescriptor` representing the function `HEXTORAW`.

    <!-- -->

    - #### NUMTODSINTERVAL

          public static final FunctionDescriptor NUMTODSINTERVAL

      A static constant `FunctionDescriptor` representing the function `NUMTODSINTERVAL`.

    <!-- -->

    - #### NUMTOYMINTERVAL

          public static final FunctionDescriptor NUMTOYMINTERVAL

      A static constant `FunctionDescriptor` representing the function `NUMTOYMINTERVAL`.

    <!-- -->

    - #### RAWTOHEX

          public static final FunctionDescriptor RAWTOHEX

      A static constant `FunctionDescriptor` representing the function `RAWTOHEX`.

    <!-- -->

    - #### RAWTONHEX

          public static final FunctionDescriptor RAWTONHEX

      A static constant `FunctionDescriptor` representing the function `RAWTONHEX`.

    <!-- -->

    - #### ROWIDTOCHAR

          public static final FunctionDescriptor ROWIDTOCHAR

      A static constant `FunctionDescriptor` representing the function `ROWIDTOCHAR`.

    <!-- -->

    - #### ROWIDTONCHAR

          public static final FunctionDescriptor ROWIDTONCHAR

      A static constant `FunctionDescriptor` representing the function `ROWIDTONCHAR`.

    <!-- -->

    - #### SCN_TO_TIMESTAMP

          public static final FunctionDescriptor SCN_TO_TIMESTAMP

      A static constant `FunctionDescriptor` representing the function `SCN_TO_TIMESTAMP`.

    <!-- -->

    - #### TIMESTAMP_TO_SCN

          public static final FunctionDescriptor TIMESTAMP_TO_SCN

      A static constant `FunctionDescriptor` representing the function `TIMESTAMP_TO_SCN`.

    <!-- -->

    - #### TO_BINARY_DOUBLE

          public static final FunctionDescriptor TO_BINARY_DOUBLE

      A static constant `FunctionDescriptor` representing the function `TO_BINARY_DOUBLE`.

    <!-- -->

    - #### TO_BINARY_FLOAT

          public static final FunctionDescriptor TO_BINARY_FLOAT

      A static constant `FunctionDescriptor` representing the function `TO_BINARY_FLOAT`.

    <!-- -->

    - #### CHAR_TO_CHAR

          public static final FunctionDescriptor CHAR_TO_CHAR

      A static constant `FunctionDescriptor` representing the function `TO_CHAR`.

    <!-- -->

    - #### NUMBER_TO_CHAR

          public static final FunctionDescriptor NUMBER_TO_CHAR

      A static constant `FunctionDescriptor` representing the function `TO_CHAR`.

    <!-- -->

    - #### DATETIME_TO_CHAR

          public static final FunctionDescriptor DATETIME_TO_CHAR

      A static constant `FunctionDescriptor` representing the function `TO_CHAR`.

    <!-- -->

    - #### INTERVAL_TO_CHAR

          public static final FunctionDescriptor INTERVAL_TO_CHAR

      A static constant `FunctionDescriptor` representing the function `TO_CHAR`.

    <!-- -->

    - #### TO_CLOB

          public static final FunctionDescriptor TO_CLOB

      A static constant `FunctionDescriptor` representing the function `TO_CLOB`.

    <!-- -->

    - #### TO_DATE

          public static final FunctionDescriptor TO_DATE

      A static constant `FunctionDescriptor` representing the function `TO_DATE`.

    <!-- -->

    - #### TO_LOB

          public static final FunctionDescriptor TO_LOB

      A static constant `FunctionDescriptor` representing the function `TO_LOB`.

    <!-- -->

    - #### TO_MULTI_BYTE

          public static final FunctionDescriptor TO_MULTI_BYTE

      A static constant `FunctionDescriptor` representing the function `TO_MULTI_BYTE`.

    <!-- -->

    - #### CHAR_TO_NCHAR

          public static final FunctionDescriptor CHAR_TO_NCHAR

      A static constant `FunctionDescriptor` representing the function `TO_NCHAR`.

    <!-- -->

    - #### NUMBER_TO_NCHAR

          public static final FunctionDescriptor NUMBER_TO_NCHAR

      A static constant `FunctionDescriptor` representing the function `TO_NCHAR`.

    <!-- -->

    - #### DATETIME_TO_NCHAR

          public static final FunctionDescriptor DATETIME_TO_NCHAR

      A static constant `FunctionDescriptor` representing the function `TO_NCHAR`.

    <!-- -->

    - #### INTERVAL_TO_NCHAR

          public static final FunctionDescriptor INTERVAL_TO_NCHAR

      A static constant `FunctionDescriptor` representing the function `TO_NCHAR`.

    <!-- -->

    - #### TO_NCLOB

          public static final FunctionDescriptor TO_NCLOB

      A static constant `FunctionDescriptor` representing the function `TO_NCLOB`.

    <!-- -->

    - #### TO_NUMBER

          public static final FunctionDescriptor TO_NUMBER

      A static constant `FunctionDescriptor` representing the function `TO_NUMBER`.

    <!-- -->

    - #### TO_SINGLE_BYTE

          public static final FunctionDescriptor TO_SINGLE_BYTE

      A static constant `FunctionDescriptor` representing the function `TO_SINGLE_BYTE`.

    <!-- -->

    - #### TRANSLATE_USING

          public static final FunctionDescriptor TRANSLATE_USING

      A static constant `FunctionDescriptor` representing the function `TRANSLATE`.

    <!-- -->

    - #### UNISTR

          public static final FunctionDescriptor UNISTR

      A static constant `FunctionDescriptor` representing the function `UNISTR`.

    <!-- -->

    - #### DECODE

          public static final FunctionDescriptor DECODE

      A static constant `FunctionDescriptor` representing the function `DECODE`.

    <!-- -->

    - #### ORA_HASH

          public static final FunctionDescriptor ORA_HASH

      A static constant `FunctionDescriptor` representing the function `ORA_HASH`.

    <!-- -->

    - #### DUMP

          public static final FunctionDescriptor DUMP

      A static constant `FunctionDescriptor` representing the function `DUMP`.

    <!-- -->

    - #### VSIZE

          public static final FunctionDescriptor VSIZE

      A static constant `FunctionDescriptor` representing the function `VSIZE`.

    <!-- -->

    - #### COALESCE

          public static final FunctionDescriptor COALESCE

      A static constant `FunctionDescriptor` representing the function `COALESCE`.

    <!-- -->

    - #### NULLIF

          public static final FunctionDescriptor NULLIF

      A static constant `FunctionDescriptor` representing the function `NULLIF`.

    <!-- -->

    - #### NVL

          public static final FunctionDescriptor NVL

      A static constant `FunctionDescriptor` representing the function `NVL`.

    <!-- -->

    - #### NVL2

          public static final FunctionDescriptor NVL2

      A static constant `FunctionDescriptor` representing the function `NVL2`.

    <!-- -->

    - #### LNNVL

          public static final FunctionDescriptor LNNVL

      A static constant `FunctionDescriptor` representing the function `LNNVL`.

    <!-- -->

    - #### SYS_CONTEXT

          public static final FunctionDescriptor SYS_CONTEXT

      A static constant `FunctionDescriptor` representing the function `SYS_CONTEXT`.

    <!-- -->

    - #### SYS_GUID

          public static final FunctionDescriptor SYS_GUID

      A static constant `FunctionDescriptor` representing the function `SYS_GUID`.

    <!-- -->

    - #### UID

          public static final FunctionDescriptor UID

      A static constant `FunctionDescriptor` representing the function `UID`.

    <!-- -->

    - #### USER

          public static final FunctionDescriptor USER

      A static constant `FunctionDescriptor` representing the function `USER`.

    <!-- -->

    - #### SYS_TYPEID

          public static final FunctionDescriptor SYS_TYPEID

      A static constant `FunctionDescriptor` representing the function `SYS_TYPEID`.

    <!-- -->

    - #### USERENV

          public static final FunctionDescriptor USERENV

      A static constant `FunctionDescriptor` representing the function `USERENV`.

    <!-- -->

    - #### NO_AGGREGATE

          public static final FunctionDescriptor NO_AGGREGATE

      A static constant `FunctionDescriptor` representing the function `NO AGGREGATE`.

    <!-- -->

    - #### AGGREGATION_SUM

          public static final FunctionDescriptor AGGREGATION_SUM

      A static constant `FunctionDescriptor` representing the function `SUM`.

    <!-- -->

    - #### AGGREGATION_AVG

          public static final FunctionDescriptor AGGREGATION_AVG

      A static constant `FunctionDescriptor` representing the function `AVG`.

    <!-- -->

    - #### HIER_AVG

          public static final FunctionDescriptor HIER_AVG

      A static constant `FunctionDescriptor` representing the function `HIER_AVG`.

    <!-- -->

    - #### AGGREGATION_FIRST

          public static final FunctionDescriptor AGGREGATION_FIRST

      A static constant `FunctionDescriptor` representing the function `FIRST`.

    <!-- -->

    - #### AGGREGATION_LAST

          public static final FunctionDescriptor AGGREGATION_LAST

      A static constant `FunctionDescriptor` representing the function `LAST`.

    <!-- -->

    - #### HIER_FIRST

          public static final FunctionDescriptor HIER_FIRST

      A static constant `FunctionDescriptor` representing the function `HIER_FIRST`.

    <!-- -->

    - #### HIER_LAST

          public static final FunctionDescriptor HIER_LAST

      A static constant `FunctionDescriptor` representing the function `HIER_LAST`.

    <!-- -->

    - #### AGGREGATION_MAX

          public static final FunctionDescriptor AGGREGATION_MAX

      A static constant `FunctionDescriptor` representing the function `MAX`.

    <!-- -->

    - #### AGGREGATION_MIN

          public static final FunctionDescriptor AGGREGATION_MIN

      A static constant `FunctionDescriptor` representing the function `MIN`.

    <!-- -->

    - #### AGGREGATE

          public static final FunctionDescriptor AGGREGATE

      A static constant `FunctionDescriptor` representing the function `AGGREGATE`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](FunctionDescriptorArgument.md)
- [Next Class](FunctionDescriptorChoiceArgument.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method
