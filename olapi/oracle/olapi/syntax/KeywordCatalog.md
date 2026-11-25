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

- [Prev Class](KeywordArgument.md)
- [Next Class](LikeCondition.md)

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

## Class KeywordCatalog

- java.lang.Object

- - oracle.olapi.syntax.KeywordCatalog

<!-- -->

-

  ------------------------------------------------------------------------



      public final class KeywordCatalog
      extends java.lang.Object

  A catalog of keywords that an application can use as arguments to `Expression` functions. The `KeywordCatalog` class has fields that represent `KeywordArgument` objects.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                | Field and Description                                                                                                                    |
    |--------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`KeywordArgument`](KeywordArgument.md) | `ANCESTOR`<br>A static constant `KeywordArgument` representing the keyword `ANCESTOR`.                                                   |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `AND`<br>A static constant `KeywordArgument` representing the keyword `AND`.                                                             |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `AS`<br>A static constant `KeywordArgument` representing the keyword `AS`.                                                               |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `ASC`<br>A static constant `KeywordArgument` representing the keyword `ASC`.                                                             |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `AT`<br>A static constant `KeywordArgument` representing the keyword `AT`.                                                               |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `BEGINNING`<br>A static constant `KeywordArgument` representing the keyword `BEGINNING`.                                                 |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `BETWEEN`<br>A static constant `KeywordArgument` representing the keyword `BETWEEN`.                                                     |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `BOTH`<br>A static constant `KeywordArgument` representing the keyword `BOTH`.                                                           |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `BY`<br>A static constant `KeywordArgument` representing the keyword `BY`.                                                               |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `CHAR_CS`<br>A static constant `KeywordArgument` representing the keyword `CHAR_CS`.                                                     |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `CLOSEST`<br>A static constant `KeywordArgument` representing the keyword `CLOSEST`.                                                     |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `CURRENT`<br>A static constant `KeywordArgument` representing the keyword `CURRENT`.                                                     |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `DAY`<br>A static constant `KeywordArgument` representing the keyword `DAY`.                                                             |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `DESC`<br>A static constant `KeywordArgument` representing the keyword `DESC`.                                                           |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `DIMENSION`<br>A static constant `KeywordArgument` representing the keyword `DIMENSION`.                                                 |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `END`<br>A static constant `KeywordArgument` representing the keyword `END`.                                                             |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `FIRST`<br>A static constant `KeywordArgument` representing the keyword `FIRST`.                                                         |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `FOLLOWING`<br>A static constant `KeywordArgument` representing the keyword `FOLLOWING`.                                                 |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `FORCE`<br>A static constant `KeywordArgument` representing the keyword `FORCE`.                                                         |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `FROM`<br>A static constant `KeywordArgument` representing the keyword `FROM`.                                                           |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `GREGORIAN`<br>A static constant `KeywordArgument` representing the keyword `GREGORIAN`.                                                 |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `HIERARCHY`<br>A static constant `KeywordArgument` representing the keyword `HIERARCHY`.                                                 |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `HOUR`<br>A static constant `KeywordArgument` representing the keyword `HOUR`.                                                           |
    | `static java.util.Map`                           | `KEYWORD_MAP`<br>A static constant `Map` that contains the keywords in this catalog as keys and has `KeywordArgument` objects as values. |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `LAST`<br>A static constant `KeywordArgument` representing the keyword `LAST`.                                                           |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `LEADING`<br>A static constant `KeywordArgument` representing the keyword `LEADING`.                                                     |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `LEVEL`<br>A static constant `KeywordArgument` representing the keyword `LEVEL`.                                                         |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `MEMBER`<br>A static constant `KeywordArgument` representing the keyword `MEMBER`.                                                       |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `MINUTE`<br>A static constant `KeywordArgument` representing the keyword `MINUTE`.                                                       |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `MONTH`<br>A static constant `KeywordArgument` representing the keyword `MONTH`.                                                         |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `NCHAR_CS`<br>A static constant `KeywordArgument` representing the keyword `NCHAR_CS`.                                                   |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `NO`<br>A static constant `KeywordArgument` representing the keyword `NO`.                                                               |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `NULLS`<br>A static constant `KeywordArgument` representing the keyword `NULLS`.                                                         |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `OF`<br>A static constant `KeywordArgument` representing the keyword `OF`.                                                               |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `OPTIMIZE`<br>A static constant `KeywordArgument` representing the keyword `OPTIMIZE`.                                                   |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `ORDER`<br>A static constant `KeywordArgument` representing the keyword `ORDER`.                                                         |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `PARENT`<br>A static constant `KeywordArgument` representing the keyword `PARENT`.                                                       |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `POSITION`<br>A static constant `KeywordArgument` representing the keyword `POSITION`.                                                   |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `PRECEDING`<br>A static constant `KeywordArgument` representing the keyword `PRECEDING`.                                                 |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `QUARTER`<br>A static constant `KeywordArgument` representing the keyword `QUARTER`.                                                     |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `REF`<br>A static constant `KeywordArgument` representing the keyword `REF`.                                                             |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `SCALEBY`<br>A static constant `KeywordArgument` representing the keyword `SCALEBY`.                                                     |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `SECOND`<br>A static constant `KeywordArgument` representing the keyword `SECOND`.                                                       |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `TIMEZONE_ABBR`<br>A static constant `KeywordArgument` representing the keyword `TIMEZONE_ABBR`.                                         |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `TIMEZONE_HOUR`<br>A static constant `KeywordArgument` representing the keyword `TIMEZONE_HOUR`.                                         |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `TIMEZONE_MINUTE`<br>A static constant `KeywordArgument` representing the keyword `TIMEZONE_MINUTE`.                                     |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `TIMEZONE_REGION`<br>A static constant `KeywordArgument` representing the keyword `TIMEZONE_REGION`.                                     |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `TOP`<br>A static constant `KeywordArgument` representing the keyword `TOP`.                                                             |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `TRAILING`<br>A static constant `KeywordArgument` representing the keyword `TRAILING`.                                                   |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `UNBOUNDED`<br>A static constant `KeywordArgument` representing the keyword `UNBOUNDED`.                                                 |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `USING`<br>A static constant `KeywordArgument` representing the keyword `USING`.                                                         |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `WEEK`<br>A static constant `KeywordArgument` representing the keyword `WEEK`.                                                           |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `WEIGHTBY`<br>A static constant `KeywordArgument` representing the keyword `WEIGHTBY`.                                                   |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `WITHIN`<br>A static constant `KeywordArgument` representing the keyword `WITHIN`.                                                       |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `YEAR`<br>A static constant `KeywordArgument` representing the keyword `YEAR`.                                                           |
    | `static `[`KeywordArgument`](KeywordArgument.md) | `YES`<br>A static constant `KeywordArgument` representing the keyword `YES`.                                                             |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `KeywordCatalog``()`        |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### KEYWORD_MAP

          public static final java.util.Map KEYWORD_MAP

      A static constant `Map` that contains the keywords in this catalog as keys and has `KeywordArgument` objects as values.

    <!-- -->

    - #### ANCESTOR

          public static final KeywordArgument ANCESTOR

      A static constant `KeywordArgument` representing the keyword `ANCESTOR`.

    <!-- -->

    - #### AND

          public static final KeywordArgument AND

      A static constant `KeywordArgument` representing the keyword `AND`.

    <!-- -->

    - #### AS

          public static final KeywordArgument AS

      A static constant `KeywordArgument` representing the keyword `AS`.

    <!-- -->

    - #### ASC

          public static final KeywordArgument ASC

      A static constant `KeywordArgument` representing the keyword `ASC`.

    <!-- -->

    - #### AT

          public static final KeywordArgument AT

      A static constant `KeywordArgument` representing the keyword `AT`.

    <!-- -->

    - #### BEGINNING

          public static final KeywordArgument BEGINNING

      A static constant `KeywordArgument` representing the keyword `BEGINNING`.

    <!-- -->

    - #### BETWEEN

          public static final KeywordArgument BETWEEN

      A static constant `KeywordArgument` representing the keyword `BETWEEN`.

    <!-- -->

    - #### BOTH

          public static final KeywordArgument BOTH

      A static constant `KeywordArgument` representing the keyword `BOTH`.

    <!-- -->

    - #### BY

          public static final KeywordArgument BY

      A static constant `KeywordArgument` representing the keyword `BY`.

    <!-- -->

    - #### CHAR_CS

          public static final KeywordArgument CHAR_CS

      A static constant `KeywordArgument` representing the keyword `CHAR_CS`.

    <!-- -->

    - #### CLOSEST

          public static final KeywordArgument CLOSEST

      A static constant `KeywordArgument` representing the keyword `CLOSEST`.

    <!-- -->

    - #### CURRENT

          public static final KeywordArgument CURRENT

      A static constant `KeywordArgument` representing the keyword `CURRENT`.

    <!-- -->

    - #### DAY

          public static final KeywordArgument DAY

      A static constant `KeywordArgument` representing the keyword `DAY`.

    <!-- -->

    - #### DESC

          public static final KeywordArgument DESC

      A static constant `KeywordArgument` representing the keyword `DESC`.

    <!-- -->

    - #### DIMENSION

          public static final KeywordArgument DIMENSION

      A static constant `KeywordArgument` representing the keyword `DIMENSION`.

    <!-- -->

    - #### END

          public static final KeywordArgument END

      A static constant `KeywordArgument` representing the keyword `END`.

    <!-- -->

    - #### FIRST

          public static final KeywordArgument FIRST

      A static constant `KeywordArgument` representing the keyword `FIRST`.

    <!-- -->

    - #### FOLLOWING

          public static final KeywordArgument FOLLOWING

      A static constant `KeywordArgument` representing the keyword `FOLLOWING`.

    <!-- -->

    - #### FORCE

          public static final KeywordArgument FORCE

      A static constant `KeywordArgument` representing the keyword `FORCE`.

    <!-- -->

    - #### FROM

          public static final KeywordArgument FROM

      A static constant `KeywordArgument` representing the keyword `FROM`.

    <!-- -->

    - #### GREGORIAN

          public static final KeywordArgument GREGORIAN

      A static constant `KeywordArgument` representing the keyword `GREGORIAN`.

    <!-- -->

    - #### HIERARCHY

          public static final KeywordArgument HIERARCHY

      A static constant `KeywordArgument` representing the keyword `HIERARCHY`.

    <!-- -->

    - #### HOUR

          public static final KeywordArgument HOUR

      A static constant `KeywordArgument` representing the keyword `HOUR`.

    <!-- -->

    - #### LAST

          public static final KeywordArgument LAST

      A static constant `KeywordArgument` representing the keyword `LAST`.

    <!-- -->

    - #### LEADING

          public static final KeywordArgument LEADING

      A static constant `KeywordArgument` representing the keyword `LEADING`.

    <!-- -->

    - #### LEVEL

          public static final KeywordArgument LEVEL

      A static constant `KeywordArgument` representing the keyword `LEVEL`.

    <!-- -->

    - #### MEMBER

          public static final KeywordArgument MEMBER

      A static constant `KeywordArgument` representing the keyword `MEMBER`.

    <!-- -->

    - #### MINUTE

          public static final KeywordArgument MINUTE

      A static constant `KeywordArgument` representing the keyword `MINUTE`.

    <!-- -->

    - #### MONTH

          public static final KeywordArgument MONTH

      A static constant `KeywordArgument` representing the keyword `MONTH`.

    <!-- -->

    - #### NCHAR_CS

          public static final KeywordArgument NCHAR_CS

      A static constant `KeywordArgument` representing the keyword `NCHAR_CS`.

    <!-- -->

    - #### NO

          public static final KeywordArgument NO

      A static constant `KeywordArgument` representing the keyword `NO`.

    <!-- -->

    - #### NULLS

          public static final KeywordArgument NULLS

      A static constant `KeywordArgument` representing the keyword `NULLS`.

    <!-- -->

    - #### OF

          public static final KeywordArgument OF

      A static constant `KeywordArgument` representing the keyword `OF`.

    <!-- -->

    - #### OPTIMIZE

          public static final KeywordArgument OPTIMIZE

      A static constant `KeywordArgument` representing the keyword `OPTIMIZE`.

    <!-- -->

    - #### ORDER

          public static final KeywordArgument ORDER

      A static constant `KeywordArgument` representing the keyword `ORDER`.

    <!-- -->

    - #### PARENT

          public static final KeywordArgument PARENT

      A static constant `KeywordArgument` representing the keyword `PARENT`.

    <!-- -->

    - #### POSITION

          public static final KeywordArgument POSITION

      A static constant `KeywordArgument` representing the keyword `POSITION`.

    <!-- -->

    - #### PRECEDING

          public static final KeywordArgument PRECEDING

      A static constant `KeywordArgument` representing the keyword `PRECEDING`.

    <!-- -->

    - #### QUARTER

          public static final KeywordArgument QUARTER

      A static constant `KeywordArgument` representing the keyword `QUARTER`.

    <!-- -->

    - #### REF

          public static final KeywordArgument REF

      A static constant `KeywordArgument` representing the keyword `REF`.

    <!-- -->

    - #### SCALEBY

          public static final KeywordArgument SCALEBY

      A static constant `KeywordArgument` representing the keyword `SCALEBY`.

    <!-- -->

    - #### SECOND

          public static final KeywordArgument SECOND

      A static constant `KeywordArgument` representing the keyword `SECOND`.

    <!-- -->

    - #### TIMEZONE_ABBR

          public static final KeywordArgument TIMEZONE_ABBR

      A static constant `KeywordArgument` representing the keyword `TIMEZONE_ABBR`.

    <!-- -->

    - #### TIMEZONE_HOUR

          public static final KeywordArgument TIMEZONE_HOUR

      A static constant `KeywordArgument` representing the keyword `TIMEZONE_HOUR`.

    <!-- -->

    - #### TIMEZONE_MINUTE

          public static final KeywordArgument TIMEZONE_MINUTE

      A static constant `KeywordArgument` representing the keyword `TIMEZONE_MINUTE`.

    <!-- -->

    - #### TIMEZONE_REGION

          public static final KeywordArgument TIMEZONE_REGION

      A static constant `KeywordArgument` representing the keyword `TIMEZONE_REGION`.

    <!-- -->

    - #### TOP

          public static final KeywordArgument TOP

      A static constant `KeywordArgument` representing the keyword `TOP`.

    <!-- -->

    - #### TRAILING

          public static final KeywordArgument TRAILING

      A static constant `KeywordArgument` representing the keyword `TRAILING`.

    <!-- -->

    - #### UNBOUNDED

          public static final KeywordArgument UNBOUNDED

      A static constant `KeywordArgument` representing the keyword `UNBOUNDED`.

    <!-- -->

    - #### USING

          public static final KeywordArgument USING

      A static constant `KeywordArgument` representing the keyword `USING`.

    <!-- -->

    - #### WEEK

          public static final KeywordArgument WEEK

      A static constant `KeywordArgument` representing the keyword `WEEK`.

    <!-- -->

    - #### WEIGHTBY

          public static final KeywordArgument WEIGHTBY

      A static constant `KeywordArgument` representing the keyword `WEIGHTBY`.

    <!-- -->

    - #### WITHIN

          public static final KeywordArgument WITHIN

      A static constant `KeywordArgument` representing the keyword `WITHIN`.

    <!-- -->

    - #### YEAR

          public static final KeywordArgument YEAR

      A static constant `KeywordArgument` representing the keyword `YEAR`.

    <!-- -->

    - #### YES

          public static final KeywordArgument YES

      A static constant `KeywordArgument` representing the keyword `YES`.

  <!-- -->

  - ### Constructor Detail

    - #### KeywordCatalog

          public KeywordCatalog()

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](KeywordArgument.md)
- [Next Class](LikeCondition.md)

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
