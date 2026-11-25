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

- [Prev Class](ListComparisonCondition.md)
- [Next Class](LoadCommand.md)

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

## Class LiteralExpression

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.TypedExpression](TypedExpression.md)

        - - oracle.olapi.syntax.LiteralExpression

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  <!-- -->

  Direct Known Subclasses:
  [DateExpression](DateExpression.md), [NullExpression](NullExpression.md), [NumberExpression](NumberExpression.md), [StringExpression](StringExpression.md)

  ------------------------------------------------------------------------



      public abstract class LiteralExpression
      extends TypedExpression

  A `TypedExpression` that is the abstract base for classes that represent a literal expression.

<!-- -->

- - ### Method Summary

    - ### Methods inherited from class oracle.olapi.syntax.[TypedExpression](TypedExpression.md)

      [`abs`](TypedExpression.md)`, `[`acos`](TypedExpression.md)`, `[`addMonths`](TypedExpression.md)`, `[`addMonths`](TypedExpression.md)`, `[`ascii`](TypedExpression.md)`, `[`asciiStr`](TypedExpression.md)`, `[`asin`](TypedExpression.md)`, `[`atan`](TypedExpression.md)`, `[`atan2`](TypedExpression.md)`, `[`between`](TypedExpression.md)`, `[`binToNum`](TypedExpression.md)`, `[`bitAnd`](TypedExpression.md)`, `[`cast`](TypedExpression.md)`, `[`ceil`](TypedExpression.md)`, `[`charToROWID`](TypedExpression.md)`, `[`chr`](TypedExpression.md)`, `[`chr`](TypedExpression.md)`, `[`coalesce`](TypedExpression.md)`, `[`compose`](TypedExpression.md)`, `[`concat`](TypedExpression.md)`, `[`concat`](TypedExpression.md)`, `[`convert`](TypedExpression.md)`, `[`convert`](TypedExpression.md)`, `[`cos`](TypedExpression.md)`, `[`cosh`](TypedExpression.md)`, `[`currentDate`](TypedExpression.md)`, `[`currentTime`](TypedExpression.md)`, `[`dbTimeZone`](TypedExpression.md)`, `[`decode`](TypedExpression.md)`, `[`decompose`](TypedExpression.md)`, `[`deref`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`dump`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`exp`](TypedExpression.md)`, `[`extractDay`](TypedExpression.md)`, `[`extractHour`](TypedExpression.md)`, `[`extractMinute`](TypedExpression.md)`, `[`extractMonth`](TypedExpression.md)`, `[`extractSecond`](TypedExpression.md)`, `[`extractTimeZoneAbbr`](TypedExpression.md)`, `[`extractTimeZoneHour`](TypedExpression.md)`, `[`extractTimeZoneMinute`](TypedExpression.md)`, `[`extractTimeZoneRegion`](TypedExpression.md)`, `[`extractYear`](TypedExpression.md)`, `[`floor`](TypedExpression.md)`, `[`fromTZ`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`getDataType`](TypedExpression.md)`, `[`greatest`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`hexToRAW`](TypedExpression.md)`, `[`in`](TypedExpression.md)`, `[`initcap`](TypedExpression.md)`, `[`instr`](TypedExpression.md)`, `[`instr2`](TypedExpression.md)`, `[`instr4`](TypedExpression.md)`, `[`instrB`](TypedExpression.md)`, `[`instrC`](TypedExpression.md)`, `[`isInfinite`](TypedExpression.md)`, `[`isNAN`](TypedExpression.md)`, `[`isNotNull`](TypedExpression.md)`, `[`isNull`](TypedExpression.md)`, `[`lastDay`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`least`](TypedExpression.md)`, `[`length`](TypedExpression.md)`, `[`length2`](TypedExpression.md)`, `[`length4`](TypedExpression.md)`, `[`lengthB`](TypedExpression.md)`, `[`lengthC`](TypedExpression.md)`, `[`like`](TypedExpression.md)`, `[`like`](TypedExpression.md)`, `[`like2`](TypedExpression.md)`, `[`like4`](TypedExpression.md)`, `[`likeC`](TypedExpression.md)`, `[`ln`](TypedExpression.md)`, `[`localTimestamp`](TypedExpression.md)`, `[`log`](TypedExpression.md)`, `[`lower`](TypedExpression.md)`, `[`lpad`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`ltrim`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`mod`](TypedExpression.md)`, `[`monthsBetween`](TypedExpression.md)`, `[`nanvl`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`newTime`](TypedExpression.md)`, `[`nextDay`](TypedExpression.md)`, `[`nlsCharsetDeclLen`](TypedExpression.md)`, `[`nlsCharsetID`](TypedExpression.md)`, `[`nlsCharsetName`](TypedExpression.md)`, `[`nlsInitcap`](TypedExpression.md)`, `[`nlsLower`](TypedExpression.md)`, `[`nlsSort`](TypedExpression.md)`, `[`nlsUpper`](TypedExpression.md)`, `[`notIn`](TypedExpression.md)`, `[`nullIf`](TypedExpression.md)`, `[`numToDSInterval`](TypedExpression.md)`, `[`numToYMInterval`](TypedExpression.md)`, `[`nvl`](TypedExpression.md)`, `[`nvl2`](TypedExpression.md)`, `[`oraHash`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`power`](TypedExpression.md)`, `[`rawToHex`](TypedExpression.md)`, `[`rawToNHex`](TypedExpression.md)`, `[`regexpInstr`](TypedExpression.md)`, `[`regexpReplace`](TypedExpression.md)`, `[`regexpSubstr`](TypedExpression.md)`, `[`remainder`](TypedExpression.md)`, `[`replace`](TypedExpression.md)`, `[`round`](TypedExpression.md)`, `[`rowIDToChar`](TypedExpression.md)`, `[`rowIDToNChar`](TypedExpression.md)`, `[`rpad`](TypedExpression.md)`, `[`rtrim`](TypedExpression.md)`, `[`scnToTimestamp`](TypedExpression.md)`, `[`sessionTimeZone`](TypedExpression.md)`, `[`sign`](TypedExpression.md)`, `[`sin`](TypedExpression.md)`, `[`sinh`](TypedExpression.md)`, `[`soundex`](TypedExpression.md)`, `[`sqrt`](TypedExpression.md)`, `[`substr`](TypedExpression.md)`, `[`substr2`](TypedExpression.md)`, `[`substr4`](TypedExpression.md)`, `[`substrB`](TypedExpression.md)`, `[`substrC`](TypedExpression.md)`, `[`sysContext`](TypedExpression.md)`, `[`sysDate`](TypedExpression.md)`, `[`sysExtractUTC`](TypedExpression.md)`, `[`sysGUID`](TypedExpression.md)`, `[`sysTimestamp`](TypedExpression.md)`, `[`sysTypeID`](TypedExpression.md)`, `[`tan`](TypedExpression.md)`, `[`tanh`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`timestampToSCN`](TypedExpression.md)`, `[`toBinaryDouble`](TypedExpression.md)`, `[`toBinaryFloat`](TypedExpression.md)`, `[`toChar`](TypedExpression.md)`, `[`toChar`](TypedExpression.md)`, `[`toCLOB`](TypedExpression.md)`, `[`toDate`](TypedExpression.md)`, `[`toDate`](TypedExpression.md)`, `[`toDSInterval`](TypedExpression.md)`, `[`toLOB`](TypedExpression.md)`, `[`toMultiByte`](TypedExpression.md)`, `[`toNChar`](TypedExpression.md)`, `[`toNChar`](TypedExpression.md)`, `[`toNCLOB`](TypedExpression.md)`, `[`toNumber`](TypedExpression.md)`, `[`toNumber`](TypedExpression.md)`, `[`toNumber`](TypedExpression.md)`, `[`toSingleByte`](TypedExpression.md)`, `[`toTimestamp`](TypedExpression.md)`, `[`toTimestampTZ`](TypedExpression.md)`, `[`toYMInterval`](TypedExpression.md)`, `[`translate`](TypedExpression.md)`, `[`translateUsingCharCS`](TypedExpression.md)`, `[`translateUsingNCharCS`](TypedExpression.md)`, `[`treat`](TypedExpression.md)`, `[`trim`](TypedExpression.md)`, `[`trimLeading`](TypedExpression.md)`, `[`trimTrailing`](TypedExpression.md)`, `[`trunc`](TypedExpression.md)`, `[`tzOffset`](TypedExpression.md)`, `[`UID`](TypedExpression.md)`, `[`unistr`](TypedExpression.md)`, `[`upper`](TypedExpression.md)`, `[`USER`](TypedExpression.md)`, `[`userEnv`](TypedExpression.md)`, `[`vsize`](TypedExpression.md)`, `[`widthBucket`](TypedExpression.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`visit`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ListComparisonCondition.md)
- [Next Class](LoadCommand.md)

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
