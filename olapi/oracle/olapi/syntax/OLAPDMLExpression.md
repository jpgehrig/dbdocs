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

- [Prev Class](OLAPDMLCommand.md)
- [Next Class](OLAPFunctionExpression.md)

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

## Class OLAPDMLExpression

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.TypedExpression](TypedExpression.md)

        - - oracle.olapi.syntax.OLAPDMLExpression

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class OLAPDMLExpression
      extends TypedExpression

  A `TypedExpression` that represents an Oracle OLAP DML expression. An application can use an instance of this class to make an OLAP DML program or formula the data source for an `MdmDerivedMeasure` in an analytic workspace. For information on creating OLAP DML objects, see *Oracle OLAP DML Reference*.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                               |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OLAPDMLExpression``(`[`TypedExpression`](TypedExpression.md)` olapDML, `[`DataType`](DataType.md)` datatype, java.util.List<`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)`> dimensions)`<br>Creates an `OLAPDMLExpression` with the specified Oracle OLAP DML expression and dimensionality.          |
    | `OLAPDMLExpression``(`[`TypedExpression`](TypedExpression.md)` olapDML, `[`DataType`](DataType.md)` datatype, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)`[] dimensions)`<br>Creates an `OLAPDMLExpression` with the specified Oracle OLAP DML expression.                                           |
    | `OLAPDMLExpression``(`[`TypedExpression`](TypedExpression.md)` olapDML, `[`SQLDataType`](SQLDataType.md)` SQLDataType, java.util.List<`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)`> dimensions)`<br>Creates an `OLAPDMLExpression` with the specified Oracle OLAP DML expression and dimensionality. |
    | `OLAPDMLExpression``(`[`TypedExpression`](TypedExpression.md)` olapDML, `[`SQLDataType`](SQLDataType.md)` SQLDataType, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)`[] dimensions)`<br>Creates an `OLAPDMLExpression` with the specified Oracle OLAP DML expression.                                  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                   | Method and Description                                                                                                                                                                                                                    |
    |---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)`[]` | `getDenseDimensions``()`<br>Gets the `MdmPrimaryDimension` objects that are specified as dense in the OLAP DML expression.                                                                                                                |
    | [`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)`[]` | `getDimensions``()`<br>Gets the `MdmPrimaryDimension` objects that are associated with this `OLAPDMLExpression`.                                                                                                                          |
    | [`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md)`[]`           | `getLoopByMeasures``()`<br>Gets the `MdmBaseMeasures` objects that are specified as measures to loop by in the OLAP DML expression.                                                                                                       |
    | [`TypedExpression`](TypedExpression.md)                             | `getOlapDML``()`<br>Gets the Oracle OLAP DML expression of this `OLAPDMLExpression`.                                                                                                                                                      |
    | [`SQLDataType`](SQLDataType.md)                                     | `getSQLDataType``()`<br>Gets the `SQLDataType` of the `OLAPDMLExpression`.                                                                                                                                                                |
    | `java.lang.Object`                                                  | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitOLAPDMLExpression` method of the `SyntaxObjectVisitor` and passes that method this `OLAPDMLExpression` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[TypedExpression](TypedExpression.md)

      [`abs`](TypedExpression.md)`, `[`acos`](TypedExpression.md)`, `[`addMonths`](TypedExpression.md)`, `[`addMonths`](TypedExpression.md)`, `[`ascii`](TypedExpression.md)`, `[`asciiStr`](TypedExpression.md)`, `[`asin`](TypedExpression.md)`, `[`atan`](TypedExpression.md)`, `[`atan2`](TypedExpression.md)`, `[`between`](TypedExpression.md)`, `[`binToNum`](TypedExpression.md)`, `[`bitAnd`](TypedExpression.md)`, `[`cast`](TypedExpression.md)`, `[`ceil`](TypedExpression.md)`, `[`charToROWID`](TypedExpression.md)`, `[`chr`](TypedExpression.md)`, `[`chr`](TypedExpression.md)`, `[`coalesce`](TypedExpression.md)`, `[`compose`](TypedExpression.md)`, `[`concat`](TypedExpression.md)`, `[`concat`](TypedExpression.md)`, `[`convert`](TypedExpression.md)`, `[`convert`](TypedExpression.md)`, `[`cos`](TypedExpression.md)`, `[`cosh`](TypedExpression.md)`, `[`currentDate`](TypedExpression.md)`, `[`currentTime`](TypedExpression.md)`, `[`dbTimeZone`](TypedExpression.md)`, `[`decode`](TypedExpression.md)`, `[`decompose`](TypedExpression.md)`, `[`deref`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`dump`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`exp`](TypedExpression.md)`, `[`extractDay`](TypedExpression.md)`, `[`extractHour`](TypedExpression.md)`, `[`extractMinute`](TypedExpression.md)`, `[`extractMonth`](TypedExpression.md)`, `[`extractSecond`](TypedExpression.md)`, `[`extractTimeZoneAbbr`](TypedExpression.md)`, `[`extractTimeZoneHour`](TypedExpression.md)`, `[`extractTimeZoneMinute`](TypedExpression.md)`, `[`extractTimeZoneRegion`](TypedExpression.md)`, `[`extractYear`](TypedExpression.md)`, `[`floor`](TypedExpression.md)`, `[`fromTZ`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`getDataType`](TypedExpression.md)`, `[`greatest`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`hexToRAW`](TypedExpression.md)`, `[`in`](TypedExpression.md)`, `[`initcap`](TypedExpression.md)`, `[`instr`](TypedExpression.md)`, `[`instr2`](TypedExpression.md)`, `[`instr4`](TypedExpression.md)`, `[`instrB`](TypedExpression.md)`, `[`instrC`](TypedExpression.md)`, `[`isInfinite`](TypedExpression.md)`, `[`isNAN`](TypedExpression.md)`, `[`isNotNull`](TypedExpression.md)`, `[`isNull`](TypedExpression.md)`, `[`lastDay`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`least`](TypedExpression.md)`, `[`length`](TypedExpression.md)`, `[`length2`](TypedExpression.md)`, `[`length4`](TypedExpression.md)`, `[`lengthB`](TypedExpression.md)`, `[`lengthC`](TypedExpression.md)`, `[`like`](TypedExpression.md)`, `[`like`](TypedExpression.md)`, `[`like2`](TypedExpression.md)`, `[`like4`](TypedExpression.md)`, `[`likeC`](TypedExpression.md)`, `[`ln`](TypedExpression.md)`, `[`localTimestamp`](TypedExpression.md)`, `[`log`](TypedExpression.md)`, `[`lower`](TypedExpression.md)`, `[`lpad`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`ltrim`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`mod`](TypedExpression.md)`, `[`monthsBetween`](TypedExpression.md)`, `[`nanvl`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`newTime`](TypedExpression.md)`, `[`nextDay`](TypedExpression.md)`, `[`nlsCharsetDeclLen`](TypedExpression.md)`, `[`nlsCharsetID`](TypedExpression.md)`, `[`nlsCharsetName`](TypedExpression.md)`, `[`nlsInitcap`](TypedExpression.md)`, `[`nlsLower`](TypedExpression.md)`, `[`nlsSort`](TypedExpression.md)`, `[`nlsUpper`](TypedExpression.md)`, `[`notIn`](TypedExpression.md)`, `[`nullIf`](TypedExpression.md)`, `[`numToDSInterval`](TypedExpression.md)`, `[`numToYMInterval`](TypedExpression.md)`, `[`nvl`](TypedExpression.md)`, `[`nvl2`](TypedExpression.md)`, `[`oraHash`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`power`](TypedExpression.md)`, `[`rawToHex`](TypedExpression.md)`, `[`rawToNHex`](TypedExpression.md)`, `[`regexpInstr`](TypedExpression.md)`, `[`regexpReplace`](TypedExpression.md)`, `[`regexpSubstr`](TypedExpression.md)`, `[`remainder`](TypedExpression.md)`, `[`replace`](TypedExpression.md)`, `[`round`](TypedExpression.md)`, `[`rowIDToChar`](TypedExpression.md)`, `[`rowIDToNChar`](TypedExpression.md)`, `[`rpad`](TypedExpression.md)`, `[`rtrim`](TypedExpression.md)`, `[`scnToTimestamp`](TypedExpression.md)`, `[`sessionTimeZone`](TypedExpression.md)`, `[`sign`](TypedExpression.md)`, `[`sin`](TypedExpression.md)`, `[`sinh`](TypedExpression.md)`, `[`soundex`](TypedExpression.md)`, `[`sqrt`](TypedExpression.md)`, `[`substr`](TypedExpression.md)`, `[`substr2`](TypedExpression.md)`, `[`substr4`](TypedExpression.md)`, `[`substrB`](TypedExpression.md)`, `[`substrC`](TypedExpression.md)`, `[`sysContext`](TypedExpression.md)`, `[`sysDate`](TypedExpression.md)`, `[`sysExtractUTC`](TypedExpression.md)`, `[`sysGUID`](TypedExpression.md)`, `[`sysTimestamp`](TypedExpression.md)`, `[`sysTypeID`](TypedExpression.md)`, `[`tan`](TypedExpression.md)`, `[`tanh`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`timestampToSCN`](TypedExpression.md)`, `[`toBinaryDouble`](TypedExpression.md)`, `[`toBinaryFloat`](TypedExpression.md)`, `[`toChar`](TypedExpression.md)`, `[`toChar`](TypedExpression.md)`, `[`toCLOB`](TypedExpression.md)`, `[`toDate`](TypedExpression.md)`, `[`toDate`](TypedExpression.md)`, `[`toDSInterval`](TypedExpression.md)`, `[`toLOB`](TypedExpression.md)`, `[`toMultiByte`](TypedExpression.md)`, `[`toNChar`](TypedExpression.md)`, `[`toNChar`](TypedExpression.md)`, `[`toNCLOB`](TypedExpression.md)`, `[`toNumber`](TypedExpression.md)`, `[`toNumber`](TypedExpression.md)`, `[`toNumber`](TypedExpression.md)`, `[`toSingleByte`](TypedExpression.md)`, `[`toTimestamp`](TypedExpression.md)`, `[`toTimestampTZ`](TypedExpression.md)`, `[`toYMInterval`](TypedExpression.md)`, `[`translate`](TypedExpression.md)`, `[`translateUsingCharCS`](TypedExpression.md)`, `[`translateUsingNCharCS`](TypedExpression.md)`, `[`treat`](TypedExpression.md)`, `[`trim`](TypedExpression.md)`, `[`trimLeading`](TypedExpression.md)`, `[`trimTrailing`](TypedExpression.md)`, `[`trunc`](TypedExpression.md)`, `[`tzOffset`](TypedExpression.md)`, `[`UID`](TypedExpression.md)`, `[`unistr`](TypedExpression.md)`, `[`upper`](TypedExpression.md)`, `[`USER`](TypedExpression.md)`, `[`userEnv`](TypedExpression.md)`, `[`vsize`](TypedExpression.md)`, `[`widthBucket`](TypedExpression.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### OLAPDMLExpression

          public OLAPDMLExpression(TypedExpression olapDML,
                                   DataType datatype,
                                   MdmPrimaryDimension[] dimensions)

      Creates an `OLAPDMLExpression` with the specified Oracle OLAP DML expression.
      Parameters:
      `olapDML` - A `TypedExpression` that evaluates to an OLAP DML expression.

      `datatype` - A `DataType` that specifies the data type of the OLAP DML expression.

      `dimensions` - An array of `MdmPrimaryDimension` objects.

    <!-- -->

    - #### OLAPDMLExpression

          public OLAPDMLExpression(TypedExpression olapDML,
                                   DataType datatype,
                                   java.util.List<MdmPrimaryDimension> dimensions)

      Creates an `OLAPDMLExpression` with the specified Oracle OLAP DML expression and dimensionality.
      Parameters:
      `olapDML` - A `TypedExpression` that evaluates to an OLAP DML expression.

      `datatype` - A `DataType` that specifies the data type of the OLAP DML expression.

      `dimensions` - A `List` of `MdmPrimaryDimension` objects.

    <!-- -->

    - #### OLAPDMLExpression

          public OLAPDMLExpression(TypedExpression olapDML,
                                   SQLDataType SQLDataType,
                                   MdmPrimaryDimension[] dimensions)

      Creates an `OLAPDMLExpression` with the specified Oracle OLAP DML expression.
      Parameters:
      `olapDML` - A `TypedExpression` that evaluates to an OLAP DML expression.

      `SQLDataType` - A `SQLDataType` that specifies the data type of the OLAP DML expression.

      `dimensions` - An array of `MdmPrimaryDimension` objects.

    <!-- -->

    - #### OLAPDMLExpression

          public OLAPDMLExpression(TypedExpression olapDML,
                                   SQLDataType SQLDataType,
                                   java.util.List<MdmPrimaryDimension> dimensions)

      Creates an `OLAPDMLExpression` with the specified Oracle OLAP DML expression and dimensionality.
      Parameters:
      `olapDML` - A `TypedExpression` that evaluates to an OLAP DML expression.

      `SQLDataType` - A `SQLDataType` that specifies the data type of the OLAP DML expression.

      `dimensions` - A `List` of `MdmPrimaryDimension` objects.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitOLAPDMLExpression` method of the `SyntaxObjectVisitor` and passes that method this `OLAPDMLExpression` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitOLAPDMLExpression` method.

    <!-- -->

    - #### getOlapDML

          public TypedExpression getOlapDML()

      Gets the Oracle OLAP DML expression of this `OLAPDMLExpression`.
      Returns:
      A `TypedExpression` that evaluates to the value of this `OLAPDMLExpression`.

    <!-- -->

    - #### getDimensions

          public MdmPrimaryDimension[] getDimensions()

      Gets the `MdmPrimaryDimension` objects that are associated with this `OLAPDMLExpression`.
      Returns:
      An array of the `MdmPrimaryDimension` objects of this `OLAPDMLExpression`.

    <!-- -->

    - #### getDenseDimensions

          public MdmPrimaryDimension[] getDenseDimensions()

      Gets the `MdmPrimaryDimension` objects that are specified as dense in the OLAP DML expression.
      Returns:
      An array of the `MdmPrimaryDimension` objects of this `OLAPDMLExpression`.

    <!-- -->

    - #### getLoopByMeasures

          public MdmBaseMeasure[] getLoopByMeasures()

      Gets the `MdmBaseMeasures` objects that are specified as measures to loop by in the OLAP DML expression.
      Returns:
      An array of the `MdmBaseMeasures` objects of this `OLAPDMLExpression`.

    <!-- -->

    - #### getSQLDataType

          public SQLDataType getSQLDataType()

      Gets the `SQLDataType` of the `OLAPDMLExpression`.
      Returns:
      A `SQLDataType` that specifies the data type of the `OLAPDMLExpression`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](OLAPDMLCommand.md)
- [Next Class](OLAPFunctionExpression.md)

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
