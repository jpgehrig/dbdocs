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

- [Prev Class](IntervalExpression.md)
- [Next Class](IsCondition.md)

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

## Class IntervalLiteralExpression

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.TypedExpression](TypedExpression.md)

        - - [oracle.olapi.syntax.RowExpression](RowExpression.md)

          - - oracle.olapi.syntax.IntervalLiteralExpression

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class IntervalLiteralExpression
      extends RowExpression

  A `RowExpression` that represents an interval literal expression, which is similar to a SQL interval literal expression. An interval literal specifies a period of time. You can specify the time period in years and months, or in days, hours, minutes, and seconds.
  Oracle Database supports two types of interval literals, `YEAR TO MONTH` and `DAY TO SECOND`. Each type contains a leading period and a trailing period. The leading period defines the basic unit of date or time being measured. The trailing period defines the smallest increment of the basic unit being considered. For example, a `YEAR TO MONTH` interval considers an interval of years to the nearest month. A `DAY TO SECOND` interval literal can specify various combinations of intervals, such as `DAY TO MINUTE`, which considers an interval of days to the nearest minute.

  For all interval literals, the leading period must specify a larger time unit than time unit of the trailing period. If you have date data in numeric form, then you can use the `NUMTOYMINTERVAL` or `NUMTODSINTERVAL` conversion function to convert the numeric data into interval values. Interval literals are used primarily with analytic functions.

  For more information, see Interval Literals in *Oracle Database SQL Language Reference*.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                       |
    |---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `DAY`<br>A constant that represents a `DAY` period.                                                                                                                         |
    | `static int`              | `DEFAULT_FRACTIONAL_SECONDS_PRECISION`<br>A constant that represents a default value for the precision of the fractional seconds for a leading or trailing `SECOND` period. |
    | `static int`              | `DEFAULT_LEADING_PRECISION`<br>A constant that represents a default value for the precision of the leading period.                                                          |
    | `static java.lang.String` | `HOUR`<br>A constant that represents a `HOUR` period.                                                                                                                       |
    | `static java.lang.String` | `MINUTE`<br>A constant that represents a `MINUTE` period.                                                                                                                   |
    | `static java.lang.String` | `MONTH`<br>A constant that represents a `MONTH` period.                                                                                                                     |
    | `static java.lang.String` | `SECOND`<br>A constant that represents a `SECOND` period.                                                                                                                   |
    | `static java.lang.String` | `YEAR`<br>A constant that represents a `YEAR` period.                                                                                                                       |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `IntervalLiteralExpression``(java.lang.String value, java.lang.String leadingPeriod, int leadingPrecision, int leadingFractionalSecondsPrecision, java.lang.String trailingPeriod, int trailingFractionalSecondsPrecision)`<br>Creates an `IntervalLiteralExpression` that has the specified value, periods, and precisions. |
    | `IntervalLiteralExpression``(java.lang.String value, java.lang.String leadingPeriod, int leadingPrecision, java.lang.String trailingPeriod)`<br>Creates an `IntervalLiteralExpression` that has the specified value, periods, and precision.                                                                                 |
    | `IntervalLiteralExpression``(java.lang.String value, java.lang.String leadingPeriod, java.lang.String trailingPeriod)`<br>Creates an `IntervalLiteralExpression` that has the specified value and periods.                                                                                                                   |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                    |
    |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`              | `getLeadingFractionalSecondsPrecision``()`<br>Gets the fractional seconds precision for the value for the leading seconds period of this `IntervalLiteralExpression`.                                                                                     |
    | `java.lang.String` | `getLeadingPeriod``()`<br>Gets the type of the leading time period of this `IntervaLiterallExpression`.                                                                                                                                                   |
    | `int`              | `getLeadingPrecision``()`<br>Gets the precision for the value for the leading period of this `IntervalLiteralExpression`.                                                                                                                                 |
    | `int`              | `getTrailingFractionalSecondsPrecision``()`<br>Gets the fractional seconds precision of the value for the trailing seconds period of this `IntervalLiteralExpression`.                                                                                    |
    | `java.lang.String` | `getTrailingPeriod``()`<br>Gets the type of the trailing time period of this `IntervaLiterallExpression`.                                                                                                                                                 |
    | `java.lang.String` | `getValue``()`<br>Gets the values for the leading and trailing periods of this `IntervaLiterallExpression`.                                                                                                                                               |
    | `java.lang.Object` | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitIntervalLiteralExpression` method of the `SyntaxObjectVisitor` and passes that method this `IntervalLiteralExpression` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[RowExpression](RowExpression.md)

      [`isCompositeObject`](RowExpression.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[TypedExpression](TypedExpression.md)

      [`abs`](TypedExpression.md)`, `[`acos`](TypedExpression.md)`, `[`addMonths`](TypedExpression.md)`, `[`addMonths`](TypedExpression.md)`, `[`ascii`](TypedExpression.md)`, `[`asciiStr`](TypedExpression.md)`, `[`asin`](TypedExpression.md)`, `[`atan`](TypedExpression.md)`, `[`atan2`](TypedExpression.md)`, `[`between`](TypedExpression.md)`, `[`binToNum`](TypedExpression.md)`, `[`bitAnd`](TypedExpression.md)`, `[`cast`](TypedExpression.md)`, `[`ceil`](TypedExpression.md)`, `[`charToROWID`](TypedExpression.md)`, `[`chr`](TypedExpression.md)`, `[`chr`](TypedExpression.md)`, `[`coalesce`](TypedExpression.md)`, `[`compose`](TypedExpression.md)`, `[`concat`](TypedExpression.md)`, `[`concat`](TypedExpression.md)`, `[`convert`](TypedExpression.md)`, `[`convert`](TypedExpression.md)`, `[`cos`](TypedExpression.md)`, `[`cosh`](TypedExpression.md)`, `[`currentDate`](TypedExpression.md)`, `[`currentTime`](TypedExpression.md)`, `[`dbTimeZone`](TypedExpression.md)`, `[`decode`](TypedExpression.md)`, `[`decompose`](TypedExpression.md)`, `[`deref`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`div`](TypedExpression.md)`, `[`dump`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`eq`](TypedExpression.md)`, `[`exp`](TypedExpression.md)`, `[`extractDay`](TypedExpression.md)`, `[`extractHour`](TypedExpression.md)`, `[`extractMinute`](TypedExpression.md)`, `[`extractMonth`](TypedExpression.md)`, `[`extractSecond`](TypedExpression.md)`, `[`extractTimeZoneAbbr`](TypedExpression.md)`, `[`extractTimeZoneHour`](TypedExpression.md)`, `[`extractTimeZoneMinute`](TypedExpression.md)`, `[`extractTimeZoneRegion`](TypedExpression.md)`, `[`extractYear`](TypedExpression.md)`, `[`floor`](TypedExpression.md)`, `[`fromTZ`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`ge`](TypedExpression.md)`, `[`getDataType`](TypedExpression.md)`, `[`greatest`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`gt`](TypedExpression.md)`, `[`hexToRAW`](TypedExpression.md)`, `[`in`](TypedExpression.md)`, `[`initcap`](TypedExpression.md)`, `[`instr`](TypedExpression.md)`, `[`instr2`](TypedExpression.md)`, `[`instr4`](TypedExpression.md)`, `[`instrB`](TypedExpression.md)`, `[`instrC`](TypedExpression.md)`, `[`isInfinite`](TypedExpression.md)`, `[`isNAN`](TypedExpression.md)`, `[`isNotNull`](TypedExpression.md)`, `[`isNull`](TypedExpression.md)`, `[`lastDay`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`le`](TypedExpression.md)`, `[`least`](TypedExpression.md)`, `[`length`](TypedExpression.md)`, `[`length2`](TypedExpression.md)`, `[`length4`](TypedExpression.md)`, `[`lengthB`](TypedExpression.md)`, `[`lengthC`](TypedExpression.md)`, `[`like`](TypedExpression.md)`, `[`like`](TypedExpression.md)`, `[`like2`](TypedExpression.md)`, `[`like4`](TypedExpression.md)`, `[`likeC`](TypedExpression.md)`, `[`ln`](TypedExpression.md)`, `[`localTimestamp`](TypedExpression.md)`, `[`log`](TypedExpression.md)`, `[`lower`](TypedExpression.md)`, `[`lpad`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`lt`](TypedExpression.md)`, `[`ltrim`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`minus`](TypedExpression.md)`, `[`mod`](TypedExpression.md)`, `[`monthsBetween`](TypedExpression.md)`, `[`nanvl`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`ne`](TypedExpression.md)`, `[`newTime`](TypedExpression.md)`, `[`nextDay`](TypedExpression.md)`, `[`nlsCharsetDeclLen`](TypedExpression.md)`, `[`nlsCharsetID`](TypedExpression.md)`, `[`nlsCharsetName`](TypedExpression.md)`, `[`nlsInitcap`](TypedExpression.md)`, `[`nlsLower`](TypedExpression.md)`, `[`nlsSort`](TypedExpression.md)`, `[`nlsUpper`](TypedExpression.md)`, `[`notIn`](TypedExpression.md)`, `[`nullIf`](TypedExpression.md)`, `[`numToDSInterval`](TypedExpression.md)`, `[`numToYMInterval`](TypedExpression.md)`, `[`nvl`](TypedExpression.md)`, `[`nvl2`](TypedExpression.md)`, `[`oraHash`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`plus`](TypedExpression.md)`, `[`power`](TypedExpression.md)`, `[`rawToHex`](TypedExpression.md)`, `[`rawToNHex`](TypedExpression.md)`, `[`regexpInstr`](TypedExpression.md)`, `[`regexpReplace`](TypedExpression.md)`, `[`regexpSubstr`](TypedExpression.md)`, `[`remainder`](TypedExpression.md)`, `[`replace`](TypedExpression.md)`, `[`round`](TypedExpression.md)`, `[`rowIDToChar`](TypedExpression.md)`, `[`rowIDToNChar`](TypedExpression.md)`, `[`rpad`](TypedExpression.md)`, `[`rtrim`](TypedExpression.md)`, `[`scnToTimestamp`](TypedExpression.md)`, `[`sessionTimeZone`](TypedExpression.md)`, `[`sign`](TypedExpression.md)`, `[`sin`](TypedExpression.md)`, `[`sinh`](TypedExpression.md)`, `[`soundex`](TypedExpression.md)`, `[`sqrt`](TypedExpression.md)`, `[`substr`](TypedExpression.md)`, `[`substr2`](TypedExpression.md)`, `[`substr4`](TypedExpression.md)`, `[`substrB`](TypedExpression.md)`, `[`substrC`](TypedExpression.md)`, `[`sysContext`](TypedExpression.md)`, `[`sysDate`](TypedExpression.md)`, `[`sysExtractUTC`](TypedExpression.md)`, `[`sysGUID`](TypedExpression.md)`, `[`sysTimestamp`](TypedExpression.md)`, `[`sysTypeID`](TypedExpression.md)`, `[`tan`](TypedExpression.md)`, `[`tanh`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`times`](TypedExpression.md)`, `[`timestampToSCN`](TypedExpression.md)`, `[`toBinaryDouble`](TypedExpression.md)`, `[`toBinaryFloat`](TypedExpression.md)`, `[`toChar`](TypedExpression.md)`, `[`toChar`](TypedExpression.md)`, `[`toCLOB`](TypedExpression.md)`, `[`toDate`](TypedExpression.md)`, `[`toDate`](TypedExpression.md)`, `[`toDSInterval`](TypedExpression.md)`, `[`toLOB`](TypedExpression.md)`, `[`toMultiByte`](TypedExpression.md)`, `[`toNChar`](TypedExpression.md)`, `[`toNChar`](TypedExpression.md)`, `[`toNCLOB`](TypedExpression.md)`, `[`toNumber`](TypedExpression.md)`, `[`toNumber`](TypedExpression.md)`, `[`toNumber`](TypedExpression.md)`, `[`toSingleByte`](TypedExpression.md)`, `[`toTimestamp`](TypedExpression.md)`, `[`toTimestampTZ`](TypedExpression.md)`, `[`toYMInterval`](TypedExpression.md)`, `[`translate`](TypedExpression.md)`, `[`translateUsingCharCS`](TypedExpression.md)`, `[`translateUsingNCharCS`](TypedExpression.md)`, `[`treat`](TypedExpression.md)`, `[`trim`](TypedExpression.md)`, `[`trimLeading`](TypedExpression.md)`, `[`trimTrailing`](TypedExpression.md)`, `[`trunc`](TypedExpression.md)`, `[`tzOffset`](TypedExpression.md)`, `[`UID`](TypedExpression.md)`, `[`unistr`](TypedExpression.md)`, `[`upper`](TypedExpression.md)`, `[`USER`](TypedExpression.md)`, `[`userEnv`](TypedExpression.md)`, `[`vsize`](TypedExpression.md)`, `[`widthBucket`](TypedExpression.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DAY

          public static final java.lang.String DAY

      A constant that represents a `DAY` period.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### HOUR

          public static final java.lang.String HOUR

      A constant that represents a `HOUR` period.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MINUTE

          public static final java.lang.String MINUTE

      A constant that represents a `MINUTE` period.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SECOND

          public static final java.lang.String SECOND

      A constant that represents a `SECOND` period.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### YEAR

          public static final java.lang.String YEAR

      A constant that represents a `YEAR` period.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MONTH

          public static final java.lang.String MONTH

      A constant that represents a `MONTH` period.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEFAULT_LEADING_PRECISION

          public static final int DEFAULT_LEADING_PRECISION

      A constant that represents a default value for the precision of the leading period.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEFAULT_FRACTIONAL_SECONDS_PRECISION

          public static final int DEFAULT_FRACTIONAL_SECONDS_PRECISION

      A constant that represents a default value for the precision of the fractional seconds for a leading or trailing `SECOND` period.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### IntervalLiteralExpression

          public IntervalLiteralExpression(java.lang.String value,
                                           java.lang.String leadingPeriod,
                                           int leadingPrecision,
                                           int leadingFractionalSecondsPrecision,
                                           java.lang.String trailingPeriod,
                                           int trailingFractionalSecondsPrecision)

      Creates an `IntervalLiteralExpression` that has the specified value, periods, and precisions. The following are examples of using this constructor.
           IntervalLiteralExpression intLitExpr = new IntervalLiteralExpression(
                                                    "200 5:12:10:222",
                                                    IntervalLiteralExpression.DAY,
                                                    3,
                    IntervalLiteralExpression.DEFAULT_FRACTIONAL_SECONDS_PRECISION,
                                                  IntervalLiteralExpression.SECOND,
                                                    3);
           System.out.println("The syntax of intLitExpr is " +
                               intLitExpr.toSyntax());
           System.out.println("The data type of intLitExpr is " +
                               intLitExpr.getDataType().getName());

           IntervalLiteralExpression intLitExpr2 = new IntervalLiteralExpression(
                                                     "11:12:10.1234567",
                                                     IntervalLiteralExpression.HOUR,
                                IntervalLiteralExpression.DEFAULT_LEADING_PRECISION,
                     IntervalLiteralExpression.DEFAULT_FRACTIONAL_SECONDS_PRECISION,
                                                   IntervalLiteralExpression.SECOND,
                                                     7);
           System.out.println("The syntax of intLitExpr2 is " +
                               intLitExpr2.toSyntax());
           System.out.println("The data type of intLitExpr2 is " +
                               intLitExpr2.getDataType().getName());

      The output of the examples is the following.
           The syntax of intLitExpr is INTERVAL '200 5:12:10:222' DAY(3) TO SECOND (3)
           The data type of intLitExpr is INTERVAL DAY TO SECOND
           The syntax of intLitExpr2 is INTERVAL '11:12:10.1234567' HOUR TO SECOND (7)
           The data type of intLitExpr2 is INTERVAL DAY TO SECOND

      Parameters:
      `value` - A `String` that contains values for the leading and trailing time periods.

      `leadingPeriod` - One of the constants of this class that specifies the type of leading time period.

      `leadingPrecision` - An integer that specifies the precision of the value of the leading time period.

      `leadingFractionalSecondsPrecision` - An integer that specifies the precision of the value of the leading seconds time period.

      `trailingPeriod` - One of the constants of this class that specifies the type of trailing time period, which must be less significant than the leading period.

      `trailingFractionalSecondsPrecision` - An integer that specifies the precision of the value of the trailing seconds time period.

    <!-- -->

    - #### IntervalLiteralExpression

          public IntervalLiteralExpression(java.lang.String value,
                                           java.lang.String leadingPeriod,
                                           int leadingPrecision,
                                           java.lang.String trailingPeriod)

      Creates an `IntervalLiteralExpression` that has the specified value, periods, and precision. The following is an example of using this constructor.
           IntervalLiteralExpression intLitExpr3 = new IntervalLiteralExpression(
                                                    "123-2",
                                                    IntervalLiteralExpression.YEAR,
                                                    3,
                                                    IntervalLiteralExpression.MONTH);
           System.out.println("The syntax of intLitExpr3 is " +
                               intLitExpr3.toSyntax());
           System.out.println("The data type of intLitExpr3 is " +
                               intLitExpr3.getDataType().getName());

      The output of the example is the following.
           The syntax of intLitExpr3 is INTERVAL '123-2' YEAR(3) TO MONTH
           The data type of intLitExpr3 is INTERVAL YEAR TO MONTH

      Parameters:
      `value` - A `String` that contains values for the leading and trailing time periods.

      `leadingPeriod` - One of the constants of this class that specifies the type of leading time period.

      `trailingPeriod` - One of the constants of this class that specifies the type of trailing time period, which must be less significant than the leading period.

      `leadingPrecision` - An integer that specifies the precision of the value of the leading time period.

    <!-- -->

    - #### IntervalLiteralExpression

          public IntervalLiteralExpression(java.lang.String value,
                                           java.lang.String leadingPeriod,
                                           java.lang.String trailingPeriod)

      Creates an `IntervalLiteralExpression` that has the specified value and periods. The following are examples of using this constructor.
           IntervalLiteralExpression intLitExpr4 = new IntervalLiteralExpression(
                                                    IntervalLiteralExpression.YEAR,
                                                    IntervalLiteralExpression.MONTH,
                                                    "12-9");
           System.out.println("The syntax of intLitExpr4 is " +
                               intLitExpr4.toSyntax());
           System.out.println("The data type of intLitExpr4 is " +
                               intLitExpr4.getDataType().getName());

           IntervalLiteralExpression intLitExpr5 = new IntervalLiteralExpression(
                                                    IntervalLiteralExpression.MINUTE,
                                                    IntervalLiteralExpression.SECOND,
                                                    "10:22");
           System.out.println("The syntax of intLitExpr5 is " +
                               intLitExpr5.toSyntax());
           System.out.println("The data type of intLitExpr5 is " +
                              intLitExpr5.getDataType().getName());

      The output of the examples is the following.
           The syntax of intLitExpr4 is INTERVAL '12-9' YEAR TO MONTH
           The data type of intLitExpr4 is INTERVAL YEAR TO MONTH
           The syntax of intLitExpr5 is INTERVAL '10:22' MINUTE TO SECOND
           The data type of intLitExpr5 is INTERVAL DAY TO SECOND

      Parameters:
      `value` - A `String` that contains values for the leading and trailing time periods.

      `leadingPeriod` - One of the constants of this class that specifies the type of leading time period.

      `trailingPeriod` - One of the constants of this class that specifies the type of trailing time period, which must be less significant than the leading period.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitIntervalLiteralExpression` method of the `SyntaxObjectVisitor` and passes that method this `IntervalLiteralExpression` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitIntervalLiteralExpression` method.

    <!-- -->

    - #### getLeadingPeriod

          public java.lang.String getLeadingPeriod()

      Gets the type of the leading time period of this `IntervaLiterallExpression`.
      Returns:
      A `String` that contains the leading time period of this `IntervaLiterallExpression`, which is the value of one of the constants of this class.

    <!-- -->

    - #### getTrailingPeriod

          public java.lang.String getTrailingPeriod()

      Gets the type of the trailing time period of this `IntervaLiterallExpression`.
      Returns:
      A `String` that contains the trailing time period of this `IntervaLiterallExpression`, which is the value of one of the constants of this class.

    <!-- -->

    - #### getValue

          public java.lang.String getValue()

      Gets the values for the leading and trailing periods of this `IntervaLiterallExpression`. The values specify the number of units of the periods.
      Returns:
      A `String` that contains values that specify the number of units for the leading and trailing time periods.

    <!-- -->

    - #### getLeadingPrecision

          public int getLeadingPrecision()

      Gets the precision for the value for the leading period of this `IntervalLiteralExpression`.
      Returns:
      A `TypedExpression` that resolves to an integer value.

    <!-- -->

    - #### getLeadingFractionalSecondsPrecision

          public int getLeadingFractionalSecondsPrecision()

      Gets the fractional seconds precision for the value for the leading seconds period of this `IntervalLiteralExpression`.
      Returns:
      An integer that is the precision of the fractional seconds of the leading seconds time period.

    <!-- -->

    - #### getTrailingFractionalSecondsPrecision

          public int getTrailingFractionalSecondsPrecision()

      Gets the fractional seconds precision of the value for the trailing seconds period of this `IntervalLiteralExpression`.
      Returns:
      An integer that is the precision of the fractional seconds of the trailing seconds time period.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](IntervalExpression.md)
- [Next Class](IsCondition.md)

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
