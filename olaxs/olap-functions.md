The OLAP functions extend the syntax of the SQL analytic functions. This syntax is familiar to SQL developers and DBAs, so you can adopt it more easily than proprietary OLAP languages and APIs. Using the OLAP functions, you can create all standard calculated measures, including rank, share, prior and future periods, period-to-date, parallel period, moving aggregates, and cumulative aggregates.

This chapter describes the OLAP functions. It contains these topics:

- OLAP Functions in Alphabetical Order

- OLAP Functions By Category

### 2.1 OLAP Functions in Alphabetical Order

- AVERAGE_RANK
- AVG
- COUNT
- DENSE_RANK
- HIER_ANCESTOR
- HIER_CHILD_COUNT
- HIER_DEPTH
- HIER_LEVEL
- HIER_ORDER
- HIER_PARENT
- HIER_TOP
- LAG
- LAG_VARIANCE
- LAG_VARIANCE_PERCENT
- LEAD
- LEAD_VARIANCE
- LEAD_VARIANCE_PERCENT
- MAX
- MIN
- OLAP_DML_EXPRESSION
- RANK
- ROW_NUMBER
- SHARE
- SUM

### 2.2 OLAP Functions By Category

The OLAP functions are grouped into these categories:

- Aggregate Functions

- Analytic Functions

- Hierarchical Functions

- Lag Functions

- OLAP DML Functions

- Rank Functions

- Share Functions

- Window Functions

#### 2.2.1 Aggregate Functions

- AVERAGE_RANK
- AVG
- COUNT
- DENSE_RANK
- MAX
- MIN
- RANK
- SUM

#### 2.2.2 Analytic Functions

- AVERAGE_RANK
- AVG
- COUNT
- DENSE_RANK
- LAG
- LAG_VARIANCE
- LEAD_VARIANCE_PERCENT
- MAX
- MIN
- RANK
- ROW_NUMBER
- SUM

#### 2.2.3 Hierarchical Functions

- HIER_ANCESTOR
- HIER_CHILD_COUNT
- HIER_DEPTH
- HIER_LEVEL
- HIER_ORDER
- HIER_PARENT
- HIER_TOP

#### 2.2.4 Lag Functions

- LAG
- LAG_VARIANCE
- LAG_VARIANCE_PERCENT
- LEAD
- LEAD_VARIANCE
- LEAD_VARIANCE_PERCENT

#### 2.2.5 OLAP DML Functions

- OLAP_DML_EXPRESSION

#### 2.2.6 Rank Functions

- AVERAGE_RANK
- DENSE_RANK
- RANK
- ROW_NUMBER

#### 2.2.7 Share Functions

- SHARE

#### 2.2.8 Window Functions

- AVG
- COUNT
- MAX
- MIN
- SUM

### 2.3 AVERAGE_RANK

`AVERAGE_RANK` orders the members of a dimension based on the values of an expression. The function returns the sequence numbers of the dimension members.

`AVERAGE_RANK` assigns the same average rank to identical values. For example, `AVERAGE_RANK` may return 1, 2, 3.5, 3.5, 5 for a series of five dimension members.

#### Return Value

    NUMBER

#### Syntax

    AVERAGE_RANK ( ) OVER (rank_clause)

rank_clause::=

    { DIMENSION dimension_id | HIERARCHY hierarchy_id }
      ORDER BY order_by_clause [, order_by_clause]...
      [ WITHIN { LEVEL
               | PARENT
               | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                             | HIERARCHY LEVEL hier_level_id
                             }
               }
      ]

order_by_clause::=

    expression [ASC | DESC] [NULLS {FIRST | LAST}]

#### Arguments

dimension_id
The dimension over which the values are calculated using the default hierarchy.

hierarchy_id
The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

ORDER BY
Provides the basis for the ranking. You can provide additional `ORDER BY` clauses to break any ties in the order.

expression
Provides the values to use as the basis for the rankings.

ASC \| DESC
Sorts the ranking from smallest to largest (ascending) or from largest to smallest (descending).

NULLS {FIRST \| LAST}
Determines whether members with null values are listed first or last.

WITHIN
Selects a set of related dimension members to be ranked.

`LEVEL` ranks all members at the same level.

`PARENT` ranks members at the same level with the same parent.

`ANCESTOR` ranks all members at the same level and with the same ancestor at a specified level.

dim_level_id
The name of a level of `dimension_id`.

hier_level_id
The name of a level of `hierarchy_id`.

#### Example

This example ranks time periods within a calendar year by Unit Cost. Notice that no month is ranked 7, because two months (JAN-02 and JUL-02) have the same value and the same rank (6.5).

`AVERAGE_RANK() OVER (HIERARCHY TIME.CALENDAR ORDER BY PRICE_CUBE.UNIT_COST DESC NULLS LAST WITHIN ANCESTOR AT DIMENSION LEVEL TIME.CALENDAR_YEAR)`

| Product      | Time   | Cost  | Average Rank |
|:-------------|:-------|:------|:-------------|
| Deluxe Mouse | MAR-02 | 24.05 | 1            |
| Deluxe Mouse | APR-02 | 23.95 | 2            |
| Deluxe Mouse | FEB-02 | 23.94 | 3            |
| Deluxe Mouse | AUG-02 | 23.88 | 4            |
| Deluxe Mouse | MAY-02 | 23.84 | 5            |
| Deluxe Mouse | JAN-02 | 23.73 | 6.5          |
| Deluxe Mouse | JUL-02 | 23.73 | 6.5          |
| Deluxe Mouse | JUN-02 | 23.72 | 8            |
| Deluxe Mouse | SEP-02 | 23.71 | 9            |
| Deluxe Mouse | NOV-02 | 23.65 | 10           |
| Deluxe Mouse | DEC-02 | 23.62 | 11           |
| Deluxe Mouse | OCT-02 | 23.37 | 12           |

#### Related Topics

DENSE_RANK, RANK, ROW_NUMBER

### 2.4 AVG

`AVG` returns the average of a selection of values calculated over a Time dimension. Use this function to create cumulative averages and moving averages.

The `GREGORIAN` relations superimpose the Gregorian calendar on the Time dimension. These relations can be useful for calculations on fiscal and nonstandard hierarchies.

#### Return Value

    NUMBER

#### Syntax

    AVG (value_expr) OVER (window_clause)

window_clause::=

    [ { DIMENSION dimension_id | HIERARCHY hierarchy_id } ]
        BETWEEN preceding_boundary | following_boundary
         [WITHIN { LEVEL
                 | PARENT
                 | GREGORIAN {YEAR | QUARTER | MONTH | WEEK}
                 | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                               | HIERARCHY LEVEL hier_level_id
                               }
                 }
         ]

preceding_boundary::=

    {UNBOUNDED PRECEDING | expression PRECEDING} AND
       { CURRENT MEMBER
       | expression {PRECEDING | FOLLOWING}
       | UNBOUNDED FOLLOWING
       }

following_boundary::=

    {CURRENT MEMBER | expression FOLLOWING} AND
      { expression FOLLOWING
      | UNBOUNDED FOLLOWING
      }

#### Arguments

value_expr
A dimensional expression whose values you want to calculate.

dimension_id
The Time dimension over which the values are calculated using the default hierarchy.

hierarchy_id
The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

dim_level_id
The name of a level of `dimension_id`.

hier_level_id
The name of a level of `hierarchy_id`.

boundaries
The preceding_boundary and following_boundary identify a range of time periods within the group identified by the dimension or hierarchy.

`UNBOUNDED` starts with the first period or ends with the last period of the group.

`CURRENT MEMBER` starts or ends the calculation at the current time period.

expression
A numeric value identifying a period at a particular distance from the current time period that starts or ends the range.

WITHIN
Identifies the range of time periods used in the calculation. Following are descriptions of the keywords.

| Range               | Description                                                                              |
|:--------------------|:-----------------------------------------------------------------------------------------|
| `LEVEL`             | Calculates all time periods at the same level. (Default)                                 |
| `PARENT`            | Calculates time periods at the same level with the same parent.                          |
| `GREGORIAN YEAR`    | Calculates time periods within the same Gregorian year.                                  |
| `GREGORIAN QUARTER` | Calculates time periods within the same Gregorian quarter.                               |
| `GREGORIAN MONTH`   | Calculates time periods within the same Gregorian month.                                 |
| `GREGORIAN WEEK`    | Calculates time periods within the same Gregorian week.                                  |
| `ANCESTOR`          | Includes time periods at the same level and with the same ancestor at a specified level. |

#### Example

This example calculates a cumulative average within each parent. The selection of data shows the cumulative averages for quarters within the 2005 and 2006 calendar years.

`AVG(GLOBAL.UNITS_CUBE.UNITS) OVER (HIERARCHY GLOBAL.TIME.CALENDAR BETWEEN UNBOUNDED PRECEDING AND CURRENT MEMBER WITHIN PARENT)`

| TIME  | PARENT | UNITS  | AVERAGE |
|:------|:-------|:-------|:--------|
| Q1.05 | CY2005 | 143607 | 143607  |
| Q2.05 | CY2005 | 138096 | 140852  |
| Q3.05 | CY2005 | 138953 | 140219  |
| Q4.05 | CY2005 | 145062 | 141430  |
| Q1.06 | CY2006 | 146819 | 146819  |
| Q2.06 | CY2006 | 145233 | 146026  |
| Q3.06 | CY2006 | 143572 | 145208  |
| Q4.06 | CY2006 | 149305 | 146232  |

#### Related Topics

COUNT, MAX, MIN, SUM

### 2.5 COUNT

`COUNT` tallies the number of data values identified by a selection of members in a Time dimension.

The `GREGORIAN` relations superimpose the Gregorian calendar on the Time dimension. These relations can be useful for calculations on fiscal and nonstandard hierarchies.

#### Return Value

    NUMBER

#### Syntax

    COUNT (value_expr) OVER (window_clause)

window_clause::=

    { DIMENSION dimension_id | HIERARCHY hierarchy_id }
      BETWEEN preceding_boundary AND following_boundary
       [WITHIN { LEVEL
               | PARENT
               | GREGORIAN {YEAR | QUARTER | MONTH | WEEK}
               | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                             | HIERARCHY LEVEL hier_level_id
                             }
               }
       ]

preceding_boundary::=

    {UNBOUNDED PRECEDING | expression PRECEDING} AND
       { CURRENT MEMBER
       | expression {PRECEDING | FOLLOWING}
       | UNBOUNDED FOLLOWING
       }

following_boundary::=

    {CURRENT MEMBER | expression FOLLOWING} AND
      { expression FOLLOWING
      | UNBOUNDED FOLLOWING
      }

#### Arguments

value_expr
A dimensional expression whose values you want to calculate.

dimension_id
The Time dimension over which the values are calculated using the default hierarchy.

hierarchy_id
The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

dim_level_id
The name of a level of `dimension_id`.

hier_level_id
The name of a level of `hierarchy_id`.

boundaries
The preceding_boundary and following_boundary identify a range of time periods within the group identified by the dimension or hierarchy.

`UNBOUNDED` starts with the first period or ends with the last period of the group.

`CURRENT MEMBER` starts or ends the calculation at the current time period.

expression
A numeric value identifying a period at a particular distance from the current time period that starts or ends the range.

WITHIN subclause
Identifies the range of time periods used in the calculation. Following are descriptions of the keywords.

| Range               | Description                                                                              |
|:--------------------|:-----------------------------------------------------------------------------------------|
| `LEVEL`             | Calculates all time periods at the same level. (Default)                                 |
| `PARENT`            | Calculates time periods at the same level with the same parent.                          |
| `GREGORIAN YEAR`    | Calculates time periods within the same Gregorian year.                                  |
| `GREGORIAN QUARTER` | Calculates time periods within the same Gregorian quarter.                               |
| `GREGORIAN MONTH`   | Calculates time periods within the same Gregorian month.                                 |
| `GREGORIAN WEEK`    | Calculates time periods within the same Gregorian week.                                  |
| `ANCESTOR`          | Includes time periods at the same level and with the same ancestor at a specified level. |

#### Example

This example tallies the number of time periods at the same level and the same year up to and including the current time period. The selected data displays the number of each month in the year.

`COUNT(GLOBAL.UNITS_CUBE.UNITS) OVER (HIERARCHY GLOBAL.TIME.CALENDAR BETWEEN UNBOUNDED PRECEDING AND CURRENT MEMBER WITHIN ANCESTOR AT DIMENSION LEVEL GLOBAL.TIME.CALENDAR_YEAR)`

| TIME   | UNITS | COUNT |
|:-------|:------|:------|
| JAN-06 | 47776 | 1     |
| FEB-06 | 47695 | 2     |
| MAR-06 | 51348 | 3     |
| APR-06 | 47005 | 4     |
| MAY-06 | 52809 | 5     |
| JUN-06 | 45419 | 6     |
| JUL-06 | 48388 | 7     |
| AUG-06 | 48830 | 8     |
| SEP-06 | 46354 | 9     |
| OCT-06 | 47411 | 10    |
| NOV-06 | 46842 | 11    |
| DEC-06 | 55052 | 12    |

#### Related Topics

AVG, MAX, MIN, SUM

### 2.6 DENSE_RANK

`DENSE_RANK` orders the members of a dimension based on the values of an expression. The function returns the sequence numbers of the dimension members.

`DENSE_RANK` assigns the same minimum rank to identical values, and returns the results in a sequential list. The result may be fewer ranks than values in the series. For example, `DENSE_RANK` may return 1, 2, 3, 3, 4 for a series of five dimension members.

#### Return Value

    NUMBER

#### Syntax

    DENSE_RANK ( ) OVER (rank_clause)

rank_clause::=

    { DIMENSION dimension_id | HIERARCHY hierarchy_id }
      ORDER BY order_by_clause [, order_by_clause]...
      [ WITHIN { LEVEL
               | PARENT
               | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                             | HIERARCHY LEVEL hier_level_id
                             }
               }
      ]

order_by_clause::=

    expression [ASC | DESC] [NULLS {FIRST | LAST}]

#### Arguments

dimension_id
The dimension over which the values are calculated using the default hierarchy.

hierarchy_id
The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

ORDER BY
Provides the basis for the ranking. You can provide additional `ORDER BY` clauses to break any ties in the order.

expression
Provides the values to use as the basis for the rankings.

ASC \| DESC
Sorts the ranking from smallest to largest (ascending) or from largest to smallest (descending).

NULLS {FIRST \| LAST}
Determines whether members with null values are listed first or last.

WITHIN
Selects a set of related dimension members to be ranked.

`LEVEL` ranks all members at the same level.

`PARENT` ranks members at the same level with the same parent.

`ANCESTOR` ranks all members at the same level and with the same ancestor at a specified level.

dim_level_id
The name of a level of `dimension_id`.

hier_level_id
The name of a level of `hierarchy_id`.

#### Example

This example ranks time periods within a calendar year by Unit Cost, using the default Calendar hierarchy. Notice that although two months (JAN-02 and JUL-02) have the same value and the same rank (6), the ranking continues at 7 for JUN-02.

`DENSE_RANK() OVER (DIMENSION "TIME" ORDER BY PRICE_CUBE.UNIT_COST DESC NULLS LAST WITHIN ANCESTOR AT DIMENSION LEVEL TIME.CALENDAR_YEAR)`

| Product      | Time   | Cost  | Dense Rank |
|:-------------|:-------|:------|:-----------|
| Deluxe Mouse | MAR-02 | 24.05 | 1          |
| Deluxe Mouse | APR-02 | 23.95 | 2          |
| Deluxe Mouse | FEB-02 | 23.94 | 3          |
| Deluxe Mouse | AUG-02 | 23.88 | 4          |
| Deluxe Mouse | MAY-02 | 23.84 | 5          |
| Deluxe Mouse | JAN-02 | 23.73 | 6          |
| Deluxe Mouse | JUL-02 | 23.73 | 6          |
| Deluxe Mouse | JUN-02 | 23.72 | 7          |
| Deluxe Mouse | SEP-02 | 23.71 | 8          |
| Deluxe Mouse | NOV-02 | 23.65 | 9          |
| Deluxe Mouse | DEC-02 | 23.62 | 10         |
| Deluxe Mouse | OCT-02 | 23.37 | 11         |

#### Related Topics

AVERAGE_RANK, RANK, ROW_NUMBER

### 2.7 HIER_ANCESTOR

`HIER_ANCESTOR` returns the ancestor at a particular level of a hierarchy for either all members in the hierarchy or a particular member. The hierarchy must be level-based.

#### Return Value

    VARCHAR2

#### Syntax

    HIER_ANCESTOR(
      [member_expression] [WITHIN]
      {DIMENSION dimension_id | HIERARCHY hierarchy_id}
      {DIMENSION LEVEL dim_level_id | HIERARCHY LEVEL hier_level_id} )

#### Arguments

member_expression
Identifies a dimension member within the hierarchy whose ancestor is returned. If this optional argument is specified, then the result does not vary across dimension members.

dimension_id
The dimension over which the values are calculated using the default hierarchy.

hierarchy_id
The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

dim_level_id
The level of the ancestor in `dimension_id`.

hier_level_id
The level of the ancestor in `hierarchy_id`.

#### Example

This example returns the ancestor at the Calendar Quarter level for members of the default Calendar hierarchy of the Time dimension.

`HIER_ANCESTOR(DIMENSION "TIME" DIMENSION LEVEL TIME.CALENDAR_QUARTER)`

| Time   | Ancestor  |
|:-------|:----------|
| 2006   | --        |
| Q1.06  | CY2006.Q1 |
| Q2.06  | CY2006.Q2 |
| Q3.06  | CY2006.Q3 |
| Q4.06  | CY2006.Q4 |
| JAN-06 | CY2006.Q1 |
| FEB-06 | CY2006.Q1 |
| MAR-06 | CY2006.Q1 |
| APR-06 | CY2006.Q2 |
| MAY-06 | CY2006.Q2 |
| JUN-06 | CY2006.Q2 |
| JUL-06 | CY2006.Q3 |
| AUG-06 | CY2006.Q3 |
| SEP-06 | CY2006.Q3 |
| OCT-06 | CY2006.Q4 |
| NOV-06 | CY2006.Q4 |
| DEC-06 | CY2006.Q4 |

The next example returns `GOV` as the ancestor of the US Department of Labor at the Customer Market Segment level in the Market hierarchy of the Customer dimension.

`HIER_ANCESTOR('US DPT LBR' WITHIN HIERARCHY CUSTOMER.MARKET DIMENSION LEVEL CUSTOMER.MARKET_SEGMENT)`

### 2.8 HIER_CHILD_COUNT

`HIER_CHILD_COUNT` returns the number of children of either all dimension members in a hierarchy or a particular member. The hierarchy can be either level-based or value-based.

#### Return Value

    NUMBER

#### Syntax

    HIER_CHILD_COUNT (
       [member_expression] [WITHIN]
       {DIMENSION dimension_id | HIERARCHY hierarchy_id} )

#### Arguments

#### member_expression

Identifies a single dimension member within the hierarchy used for the calculation. If this optional argument is specified, then the result does not vary across dimension members.

#### dimension_id

The dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

#### Example

This example returns the number of children for each member of the default hierarchy of the Time dimension.

`HIER_CHILD_COUNT(DIMENSION "TIME")`

| Time   | Children |
|:-------|:---------|
| 2006   | 4        |
| Q1.06  | 3        |
| Q2.06  | 3        |
| Q3.06  | 3        |
| Q4.06  | 3        |
| JAN-06 | 0        |
| FEB-06 | 0        |
| MAR-06 | 0        |
| APR-06 | 0        |
| MAY-06 | 0        |
| JUN-06 | 0        |
| JUL-06 | 0        |
| AUG-06 | 0        |
| SEP-06 | 0        |
| OCT-06 | 0        |
| NOV-06 | 0        |
| DEC-06 | 0        |

The next example returns `8` as the number of children for Government within the Market hierarchy of the Customer dimension.

`HIER_CHILD_COUNT('GOV' WITHIN HIERARCHY CUSTOMER.MARKET)`

### 2.9 HIER_DEPTH

`HIER_DEPTH` returns a number representing the level depth of either all members of a hierarchy or a particular member, where 0 is the top level. The hierarchy can be either level-based or value-based.

#### Return Value

    NUMBER

#### Syntax

    HIER_DEPTH (
       [member_expression] [WITHIN]
       {DIMENSION dimension_id | HIERARCHY hierarchy_id} )

#### Arguments

#### member_expression

Identifies a single dimension member within the hierarchy used for the calculation. If this optional argument is specified, then the result does not vary across dimension members.

#### dimension_id

The dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

#### Example

This example returns the depth of each member in the default hierarchy of the Time dimension.

`HIER_DEPTH(DIMENSION "TIME")`

| Time   | Depth |
|:-------|:------|
| 2006   | 1     |
| Q1.06  | 2     |
| Q2.06  | 2     |
| Q3.06  | 2     |
| Q4.06  | 2     |
| JAN-06 | 3     |
| FEB-06 | 3     |
| MAR-06 | 3     |
| APR-06 | 3     |
| MAY-06 | 3     |
| JUN-06 | 3     |
| JUL-06 | 3     |
| AUG-06 | 3     |
| SEP-06 | 3     |
| OCT-06 | 3     |
| NOV-06 | 3     |
| DEC-06 | 3     |

The next example returns `2` as the depth of Italy in the default Customer hierarchy.

`HIER_DEPTH('ITA' WITHIN DIMENSION CUSTOMER)`

### 2.10 HIER_LEVEL

`HIER_LEVEL` returns the level of either all members of a hierarchy or a particular member. The hierarchy must be level-based.

#### Return Value

    VARCHAR2

#### Syntax

    HIER_LEVEL (
       [member_expression] [WITHIN]
       {DIMENSION dimension_id | HIERARCHY hierarchy_id} )

#### Arguments

#### member_expression

Identifies a single dimension member within the hierarchy used for the calculation. If this optional argument is specified, then the result does not vary across dimension members.

#### dimension_id

The dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

#### Example

This example returns the level of each member of the default hierarchy of the Time dimension.

`HIER_LEVEL(DIMENSION "TIME")`

| Time   | Level            |
|:-------|:-----------------|
| 2006   | CALENDAR_YEAR    |
| Q1.06  | CALENDAR_QUARTER |
| Q2.06  | CALENDAR_QUARTER |
| Q3.06  | CALENDAR_QUARTER |
| Q4.06  | CALENDAR_QUARTER |
| JAN-06 | MONTH            |
| FEB-06 | MONTH            |
| MAR-06 | MONTH            |
| APR-06 | MONTH            |
| MAY-06 | MONTH            |
| JUN-06 | MONTH            |
| JUL-06 | MONTH            |
| AUG-06 | MONTH            |
| SEP-06 | MONTH            |
| OCT-06 | MONTH            |
| NOV-06 | MONTH            |
| DEC-06 | MONTH            |

The next example returns `ACCOUNT` as the level of Business World in the Market hierarchy of the Customer dimension.

`HIER_LEVEL('BUSN WRLD' WITHIN HIERARCHY CUSTOMER.MARKET)`

### 2.11 HIER_ORDER

`HIER_ORDER` sorts the members of a dimension with children immediately after their parents, and returns a sequential number for each member.

#### Return Value

    NUMBER

#### Syntax

    HIER_ORDER (
       [member_expression] [WITHIN]
       {DIMENSION dimension_id | HIERARCHY hierarchy_id} )

#### Arguments

#### member_expression

Identifies a single dimension member within the hierarchy used for the calculation. If this optional argument is specified, then the result does not vary across dimension members.

#### dimension_id

The dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

#### Example

This example orders the values of the Time dimension:

`HIER_ORDER(DIMENSION "TIME")`

| Time   | Order |
|:-------|:------|
| 2006   | 138   |
| Q1.06  | 139   |
| JAN-06 | 140   |
| FEB-06 | 141   |
| MAR-06 | 142   |
| Q2.06  | 143   |
| APR-06 | 144   |
| MAY-06 | 145   |
| JUN-06 | 146   |
| Q3.06  | 147   |
| JUL-06 | 148   |
| AUG-06 | 149   |
| SEP-06 | 150   |
| Q4.06  | 151   |
| OCT-06 | 152   |
| NOV-06 | 153   |
| DEC-06 | 154   |

The next example returns `78` as the order number of Business World in the Market hierarchy of the Customer dimension.

`HIER_ORDER('BUSN WRLD' WITHIN HIERARCHY CUSTOMER.MARKET)`

### 2.12 HIER_PARENT

`HIER_PARENT` returns the parent of either all dimension members in a hierarchy or a particular member. The hierarchy can be either level-based or value-based.

#### Return Value

    VARCHAR2

#### Syntax

    HIER_PARENT (
       [member_expression] [WITHIN]
       {DIMENSION dimension_id | HIERARCHY hierarchy_id} )

#### Arguments

#### member_expression

Identifies a single dimension member within the hierarchy used for the calculation. If this optional argument is specified, then the result does not vary across dimension members.

#### dimension_id

The dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

#### Example

This example returns the parents of all members of the default hierarchy of the Time dimension.

`HIER_PARENT(DIMENSION GLOBAL.TIME)`

| Time   | Parent    |
|:-------|:----------|
| 2006   | TOTAL     |
| Q1.06  | CY2006    |
| Q2.06  | CY2006    |
| Q3.06  | CY2006    |
| Q4.06  | CY2006    |
| JAN-06 | CY2006.Q1 |
| FEB-06 | CY2006.Q1 |
| MAR-06 | CY2006.Q1 |
| APR-06 | CY2006.Q2 |
| MAY-06 | CY2006.Q2 |
| JUN-06 | CY2006.Q2 |
| JUL-06 | CY2006.Q3 |
| AUG-06 | CY2006.Q3 |
| SEP-06 | CY2006.Q3 |
| OCT-06 | CY2006.Q4 |
| NOV-06 | CY2006.Q4 |
| DEC-06 | CY2006.Q4 |

The next example returns `EMEA` as the parent of Italy within the default hierarchy of the Customer dimension.

`HIER_PARENT('ITA' WITHIN DIMENSION CUSTOMER)`

### 2.13 HIER_TOP

`HIER_TOP` returns the topmost ancestor of either all members of a hierarchy or a particular member. The hierarchy can be either level-based or value-based.

#### Return Value

    VARCHAR2

#### Syntax

    HIER_TOP (
       [member_expression] [WITHIN]
       {DIMENSION dimension_id | HIERARCHY hierarchy_id} )

#### Arguments

#### member_expression

Identifies a single dimension member within the hierarchy used for the calculation. If this optional argument is specified, then the result does not vary across dimension members.

#### dimension_id

The dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

#### Example

This example returns the top member of the default hierarchy of the Time dimension.

`HIER_TOP(DIMENSION "TIME")`

| Time   | Top   |
|:-------|:------|
| 2006   | TOTAL |
| Q1.06  | TOTAL |
| Q2.06  | TOTAL |
| Q3.06  | TOTAL |
| Q4.06  | TOTAL |
| JAN-06 | TOTAL |
| FEB-06 | TOTAL |
| MAR-06 | TOTAL |
| APR-06 | TOTAL |
| MAY-06 | TOTAL |
| JUN-06 | TOTAL |
| JUL-06 | TOTAL |
| AUG-06 | TOTAL |
| SEP-06 | TOTAL |
| OCT-06 | TOTAL |
| NOV-06 | TOTAL |
| DEC-06 | TOTAL |

The next example returns `TOTAL`, which is the top member for Europe in the default hierarchy of the Customer dimension.

`HIER_TOP('EMEA' WITHIN DIMENSION CUSTOMER)`

### 2.14 LAG

`LAG` returns the value from an earlier time period.

#### Return Value

The same data type as the value expression

#### Syntax

    LAG (lag_args) OVER (lag_clause)

lag_args::=

    expression, offset [, {default_expression | CLOSEST} ]

lag_clause::=

    [ {DIMENSION dimension_id | HIERARCHY hierarchy_id} ]
    [ [BY] { LEVEL
           | PARENT
           | GREGORIAN {YEAR | QUARTER | MONTH | WEEK | DAY}
           | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                         | HIERARCHY LEVEL hier_level_id
                         }
           }
      [POSITION FROM {BEGINNING | END}]
    ]

#### Arguments

| Offset Unit         | Description                                                                                                                            |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `LEVEL`             | The member at the same level `offset` periods before the current member. (Default)                                                     |
| `PARENT`            | The member at the same level with the same parent `offset` periods before the current member.                                          |
| `GREGORIAN YEAR`    | The period at the same level with a start date exactly `offset` years before the start date of the current period.                     |
| `GREGORIAN QUARTER` | The period at the same level with a start date exactly `offset` quarters before the start date of the current period.                  |
| `GREGORIAN MONTH`   | The period at the same level with a start date exactly `offset` months before the start date of the current period.                    |
| `GREGORIAN WEEK`    | The period at the same level with a start date exactly `offset` weeks before the start date of the current period.                     |
| `GREGORIAN DAY`     | The period at the same level with a start date exactly `offset` days before the start date of the current period.                      |
| `ANCESTOR`          | The period at the same level as the current period and whose ancestor is `offset` positions before the ancestor of the current period. |

#### expression

A dimensional expression whose values you want to calculate.

#### offset

A numeric expression for the number of periods to count back from the current time period.

#### default_expression

The value returned when `offset` does not identify a valid period. This clause is either an expression of any data type or the `CLOSEST` keyword for the closest match. The closest match is the first member when counting back.

#### dimension_id

The Time dimension over which the lag is calculated.

#### hierarchy_id

The hierarchy over which the lag is calculated. Otherwise, the default hierarchy for `dimension_id` is used.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### BY subclause

The BY subclause identifies the range of time periods used when counting the offset. Following are descriptions of the keywords:

#### Example

This example returns the value from the prior year for each period.

`LAG(UNITS_CUBE.UNITS, 1) OVER (HIERARCHY "TIME".CALENDAR ANCESTOR AT DIMENSION LEVEL "TIME".CALENDAR_YEAR)`

| Time  | Units  | Last Year |
|:------|:-------|:----------|
| Q1.05 | 143607 | 146529    |
| Q2.05 | 138096 | 143070    |
| Q3.05 | 138953 | 148292    |
| Q4.05 | 145062 | 149528    |
| Q1.06 | 146819 | 143607    |
| Q2.06 | 145233 | 138096    |
| Q3.06 | 143572 | 138953    |
| Q4.06 | 149305 | 145062    |

#### Related Topics

LAG_VARIANCE, LAG_VARIANCE_PERCENT, LEAD

### 2.15 LAG_VARIANCE

`LAG_VARIANCE` returns the difference between values for the current time period and an earlier period.

#### Return Value

The same data type as the value expression

#### Syntax

    LAG_VARIANCE (lag_args) OVER (lag_clause)

lag_args::=

    expression, offset [, {default_expression | CLOSEST} ]

lag_clause::=

    [ {DIMENSION dimension_id | HIERARCHY hierarchy_id} ]
    [ [BY] { LEVEL
           | PARENT
           | GREGORIAN {YEAR | QUARTER | MONTH | WEEK | DAY}
           | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                         | HIERARCHY LEVEL hier_level_id
                         }
           }
      [POSITION FROM {BEGINNING | END}]
    ]

#### Arguments

| Offset Unit         | Description                                                                                                                            |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `LEVEL`             | The member at the same level `offset` periods before the current member. (Default)                                                     |
| `PARENT`            | The member at the same level with the same parent `offset` periods before the current member.                                          |
| `GREGORIAN YEAR`    | The period at the same level with a start date exactly `offset` years before the start date of the current period.                     |
| `GREGORIAN QUARTER` | The period at the same level with a start date exactly `offset` quarters before the start date of the current period.                  |
| `GREGORIAN MONTH`   | The period at the same level with a start date exactly `offset` months before the start date of the current period.                    |
| `GREGORIAN WEEK`    | The period at the same level with a start date exactly `offset` weeks before the start date of the current period.                     |
| `GREGORIAN DAY`     | The period at the same level with a start date exactly `offset` days before the start date of the current period.                      |
| `ANCESTOR`          | The period at the same level as the current period and whose ancestor is `offset` positions before the ancestor of the current period. |

#### expression

A dimensional expression whose values you want to calculate.

#### offset

A numeric expression for the number of periods to count back from the current time period.

#### default_expression

The value returned when `offset` does not identify a valid period. This clause is either an expression of any data type or the `CLOSEST` keyword for the closest match. The closest match is the first member when counting back.

#### dimension_id

The Time dimension over which the lag is calculated.

#### hierarchy_id

The hierarchy over which the lag is calculated. Otherwise, the default hierarchy for `dimension_id` is used.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### BY subclause

The BY subclause identifies the range of time periods used when counting the offset. Following are descriptions of the keywords:

#### Examples

This example returns the difference in values between the current period and the equivalent period in the prior year.

`LAG_VARIANCE (GLOBAL.UNITS_CUBE.UNITS, 1) OVER (HIERARCHY GLOBAL.TIME.CALENDAR ANCESTOR AT DIMENSION LEVEL GLOBAL.TIME.CALENDAR_YEAR)`

| Time  | Units  | Last Year | Difference |
|:------|:-------|:----------|:-----------|
| Q1.05 | 143607 | 146529    | -2922      |
| Q2.05 | 138096 | 143070    | -4974      |
| Q3.05 | 138953 | 148292    | -9339      |
| Q4.05 | 145062 | 149528    | -4466      |
| Q1.06 | 146819 | 143607    | 3212       |
| Q2.06 | 145233 | 138096    | 7137       |
| Q3.06 | 143572 | 138953    | 4619       |
| Q4.06 | 149305 | 145062    | 4243       |

#### Related Topics

LAG, LAG_VARIANCE_PERCENT, LEAD

### 2.16 LAG_VARIANCE_PERCENT

`LAG_VARIANCE_PERCENT` returns the percent difference between values for the current time period and an earlier period.

#### Return Value

    NUMBER

#### Syntax

    LAG_VARIANCE_PERCENT (lag_args) OVER (lag_clause)

lag_args::=

    expression, offset [, {default_expression | CLOSEST} ]

lag_clause::=

    [ {DIMENSION dimension_id | HIERARCHY hierarchy_id} ]
    [ [BY] { LEVEL
           | PARENT
           | GREGORIAN {YEAR | QUARTER | MONTH | WEEK | DAY}
           | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                         | HIERARCHY LEVEL hier_level_id
                         }
           }
      [POSITION FROM {BEGINNING | END}]
    ]

#### Arguments

| Offset Unit         | Description                                                                                                                            |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `LEVEL`             | The member at the same level `offset` periods before the current member. (Default)                                                     |
| `PARENT`            | The member at the same level with the same parent `offset` periods before the current member.                                          |
| `GREGORIAN YEAR`    | The period at the same level with a start date exactly `offset` years before the start date of the current period.                     |
| `GREGORIAN QUARTER` | The period at the same level with a start date exactly `offset` quarters before the start date of the current period.                  |
| `GREGORIAN MONTH`   | The period at the same level with a start date exactly `offset` months before the start date of the current period.                    |
| `GREGORIAN WEEK`    | The period at the same level with a start date exactly `offset` weeks before the start date of the current period.                     |
| `GREGORIAN DAY`     | The period at the same level with a start date exactly `offset` days before the start date of the current period.                      |
| `ANCESTOR`          | The period at the same level as the current period and whose ancestor is `offset` positions before the ancestor of the current period. |

#### expression

A dimensional expression whose values you want to calculate.

#### offset

A numeric expression for the number of periods to count back from the current time period.

#### default_expression

The value returned when `offset` does not identify a valid period. This clause is either an expression of any data type or the `CLOSEST` keyword for the closest match. The closest match is the first member when counting back.

#### dimension_id

The Time dimension over which the lag is calculated.

#### hierarchy_id

The hierarchy over which the lag is calculated. Otherwise, the default hierarchy for `dimension_id` is used.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### BY subclause

The BY subclause identifies the range of time periods used when counting the offset. Following are descriptions of the keywords:

#### Examples

This example returns the percent difference in value between the current period and the equivalent period in the prior year.

`LAG_VARIANCE_PERCENT (GLOBAL.UNITS_CUBE.UNITS, 1) OVER (HIERARCHY GLOBAL.TIME.CALENDAR ANCESTOR AT DIMENSION LEVEL GLOBAL.TIME.CALENDAR_YEAR)`

| Time  | Units  | Last Year | Difference | Percent |
|:------|:-------|:----------|:-----------|:--------|
| Q1.05 | 143607 | 146529    | -2922      | -.02    |
| Q2.05 | 138096 | 143070    | -4974      | -.03    |
| Q3.05 | 138953 | 148292    | -9339      | -.06    |
| Q4.05 | 145062 | 149528    | -4466      | -.03    |
| Q1.06 | 146819 | 143607    | 3212       | .02     |
| Q2.06 | 145233 | 138096    | 7137       | .05     |
| Q3.06 | 143572 | 138953    | 4619       | .03     |
| Q4.06 | 149305 | 145062    | 4243       | .03     |

#### Related Topics

LAG, LAG_VARIANCE, LEAD

### 2.17 LEAD

`LEAD` returns the value of an expression for a later time period.

#### Return Value

The same data type as the value expression

#### Syntax

    LEAD (lead_args) OVER (lead_clause)

lead_args::=

    expression, offset [, {default_expression | CLOSEST} ]

lead_clause::=

    [ {DIMENSION dimension_id | HIERARCHY hierarchy_id} ]
    [ [BY] { LEVEL
           | PARENT
           | GREGORIAN {YEAR | QUARTER | MONTH | WEEK | DAY}
           | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                         | HIERARCHY LEVEL hier_level_id
                         }
           }
      [POSITION FROM {BEGINNING | END}]
    ]

#### Arguments

| Offset Unit         | Description                                                                                                                           |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| `LEVEL`             | The member at the same level `offset` periods after the current member. (Default)                                                     |
| `PARENT`            | The member at the same level with the same parent `offset` periods after the current member.                                          |
| `GREGORIAN YEAR`    | The period at the same level with a start date exactly `offset` years after the start date of the current period.                     |
| `GREGORIAN QUARTER` | The period at the same level with a start date exactly `offset` quarters after the start date of the current period.                  |
| `GREGORIAN MONTH`   | The period at the same level with a start date exactly `offset` months after the start date of the current period.                    |
| `GREGORIAN WEEK`    | The period at the same level with a start date exactly `offset` weeks after the start date of the current period.                     |
| `GREGORIAN DAY`     | The period at the same level with a start date exactly `offset` days after the start date of the current period.                      |
| `ANCESTOR`          | The period at the same level as the current period and whose ancestor is `offset` positions after the ancestor of the current period. |

#### expression

A dimensional expression whose values you want to calculate.

#### offset

A numeric expression for the number of periods to count forward from the current time period.

#### default_expression

The value returned when `offset` does not identify a valid period. This clause is either an expression of any data type or the `CLOSEST` keyword for the closest match. The closest match is the first member when counting forward.

#### dimension_id

The Time dimension over which the lead is calculated.

#### hierarchy_id

The hierarchy over which the lead is calculated. Otherwise, the default hierarchy for `dimension_id` is used.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### BY subclause

The BY subclause identifies the range of time periods used when counting the offset. Following are descriptions of the keywords:

#### Examples

This calculation returns the value of the next time period based on calendar quarter. The sample output from this calculation appears in the Next Qtr column.

`LEAD (GLOBAL.UNITS_CUBE.UNITS, 1, CLOSEST) OVER (DIMENSION GLOBAL.TIME BY ANCESTOR AT DIMENSION LEVEL GLOBAL.TIME.CALENDAR_QUARTER)`

| Time     | Parent    | Units  | Next Qtr |
|:---------|:----------|:-------|:---------|
| `2005`   | TOTAL     | 565718 | --       |
| `Q1-05`  | CY2005    | 143607 | 138096   |
| `Q2-05`  | CY2005    | 138096 | 138953   |
| `Q3-05`  | CY2005    | 138953 | 145062   |
| `Q4-05`  | CY2005    | 145062 | 146819   |
| `Jan-05` | CY2005.Q1 | 50098  | 40223    |
| `Feb-05` | CY2005.Q1 | 43990  | 45477    |
| `Mar-05` | CY2005.Q1 | 49519  | 52396    |
| `Apr-05` | CY2005.Q2 | 40223  | 45595    |
| `May-05` | CY2005.Q2 | 45477  | 46882    |
| `Jun-05` | CY2005.Q2 | 52396  | 46476    |
| `Jul-05` | CY2005.Q3 | 45595  | 47476    |
| `Aug-05` | CY2005.Q3 | 46882  | 47496    |
| `Sep-05` | CY2005.Q3 | 46476  | 50090    |
| `Oct-05` | CY2005.Q4 | 47476  | 47776    |
| `Nov-05` | CY2005.Q4 | 47496  | 47695    |
| `Dec-05` | CY2005.Q4 | 50090  | 51348    |

#### Related Topics

LAG, LEAD_VARIANCE, LEAD_VARIANCE_PERCENT

### 2.18 LEAD_VARIANCE

`LEAD_VARIANCE` returns the difference between values for the current time period and the offset period.

#### Return Value

The same data type as the value expression

#### Syntax

    LEAD_VARIANCE (lead_args) OVER (lead_clause)

lead_args::=

    expression, offset [, {default_expression | CLOSEST} ]

lead_clause::=

    [ {DIMENSION dimension_id | HIERARCHY hierarchy_id} ]
    [ [BY] { LEVEL
           | PARENT
           | GREGORIAN {YEAR | QUARTER | MONTH | WEEK | DAY}
           | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                         | HIERARCHY LEVEL hier_level_id
                         }
           }
      [POSITION FROM {BEGINNING | END}]
    ]

#### Arguments

| Offset Unit         | Description                                                                                                                           |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| `LEVEL`             | The member at the same level `offset` periods after the current member. (Default)                                                     |
| `PARENT`            | The member at the same level with the same parent `offset` periods after the current member.                                          |
| `GREGORIAN YEAR`    | The period at the same level with a start date exactly `offset` years after the start date of the current period.                     |
| `GREGORIAN QUARTER` | The period at the same level with a start date exactly `offset` quarters after the start date of the current period.                  |
| `GREGORIAN MONTH`   | The period at the same level with a start date exactly `offset` months after the start date of the current period.                    |
| `GREGORIAN WEEK`    | The period at the same level with a start date exactly `offset` weeks after the start date of the current period.                     |
| `GREGORIAN DAY`     | The period at the same level with a start date exactly `offset` days after the start date of the current period.                      |
| `ANCESTOR`          | The period at the same level as the current period and whose ancestor is `offset` positions after the ancestor of the current period. |

#### expression

A dimensional expression whose values you want to calculate.

#### offset

A numeric expression for the number of periods to count forward from the current time period.

#### default_expression

The value returned when `offset` does not identify a valid period. This clause is either an expression of any data type or the `CLOSEST` keyword for the closest match. The closest match is the first member when counting forward.

#### dimension_id

The Time dimension over which the lead is calculated.

#### hierarchy_id

The hierarchy over which the lead is calculated. Otherwise, the default hierarchy for `dimension_id` is used.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### BY subclause

The BY subclause identifies the range of time periods used when counting the offset. Following are descriptions of the keywords:

#### Examples

This calculation returns the difference between the current value and the value of the next time period based on calendar quarter. The sample output from this calculation appears in the Difference column.

`LEAD_VARIANCE (GLOBAL.UNITS_CUBE.UNITS, 1, CLOSEST) OVER (DIMENSION GLOBAL.TIME BY ANCESTOR AT DIMENSION LEVEL GLOBAL.TIME.CALENDAR_QUARTER)`

| Time     | Parent    | Units  | Next Qtr | Difference |
|:---------|:----------|:-------|:---------|:-----------|
| `2005`   | TOTAL     | 565718 | --       | --         |
| `Q1-05`  | CY2005    | 143607 | 138096   | 5511       |
| `Q2-05`  | CY2005    | 138096 | 138953   | -857       |
| `Q3-05`  | CY2005    | 138953 | 145062   | -6109      |
| `Q4-05`  | CY2005    | 145062 | 146819   | -1757      |
| `Jan-05` | CY2005.Q1 | 50098  | 40223    | 9875       |
| `Feb-05` | CY2005.Q1 | 43990  | 45477    | -1487      |
| `Mar-05` | CY2005.Q1 | 49519  | 52396    | -2877      |
| `Apr-05` | CY2005.Q2 | 40223  | 45595    | -5372      |
| `May-05` | CY2005.Q2 | 45477  | 46882    | -1405      |
| `Jun-05` | CY2005.Q2 | 52396  | 46476    | 5920       |
| `Jul-05` | CY2005.Q3 | 45595  | 47476    | -1881      |
| `Aug-05` | CY2005.Q3 | 46882  | 47496    | -614       |
| `Sep-05` | CY2005.Q3 | 46476  | 50090    | -3614      |
| `Oct-05` | CY2005.Q4 | 47476  | 47776    | -300       |
| `Nov-05` | CY2005.Q4 | 47496  | 47695    | -199       |
| `Dec-05` | CY2005.Q4 | 50090  | 51348    | -1258      |

#### Related Topics

LAG, LEAD, LEAD_VARIANCE_PERCENT

### 2.19 LEAD_VARIANCE_PERCENT

`LEAD_VARIANCE_PERCENT` returns the percent difference between values for the current time period and the offset period.

#### Return Value

    NUMBER

#### Syntax

    LEAD_VARIANCE_PERCENT (lead_args) OVER (lead_clause)

lead_args::=

    expression, offset [, {default_expression | CLOSEST} ]

lead_clause::=

    [ {DIMENSION dimension_id | HIERARCHY hierarchy_id} ]
    [ [BY] { LEVEL
           | PARENT
           | GREGORIAN {YEAR | QUARTER | MONTH | WEEK | DAY}
           | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                         | HIERARCHY LEVEL hier_level_id
                         }
           }
      [POSITION FROM {BEGINNING | END}]
    ]

#### Arguments

| Offset Unit         | Description                                                                                                                           |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| `LEVEL`             | The member at the same level `offset` periods after the current member. (Default)                                                     |
| `PARENT`            | The member at the same level with the same parent `offset` periods after the current member.                                          |
| `GREGORIAN YEAR`    | The period at the same level with a start date exactly `offset` years after the start date of the current period.                     |
| `GREGORIAN QUARTER` | The period at the same level with a start date exactly `offset` quarters after the start date of the current period.                  |
| `GREGORIAN MONTH`   | The period at the same level with a start date exactly `offset` months after the start date of the current period.                    |
| `GREGORIAN WEEK`    | The period at the same level with a start date exactly `offset` weeks after the start date of the current period.                     |
| `GREGORIAN DAY`     | The period at the same level with a start date exactly `offset` days after the start date of the current period.                      |
| `ANCESTOR`          | The period at the same level as the current period and whose ancestor is `offset` positions after the ancestor of the current period. |

#### expression

A dimensional expression whose values you want to calculate.

#### offset

A numeric expression for the number of periods to count forward from the current time period.

#### default_expression

The value returned when `offset` does not identify a valid period. This clause is either an expression of any data type or the `CLOSEST` keyword for the closest match. The closest match is the first member when counting forward.

#### dimension_id

The Time dimension over which the lead is calculated.

#### hierarchy_id

The hierarchy over which the lead is calculated. Otherwise, the default hierarchy for `dimension_id` is used.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### BY subclause

The BY subclause identifies the range of time periods used when counting the offset. Following are descriptions of the keywords:

#### Example

This calculation returns the percent difference between the current value and the value of the next time period based on calendar quarter. The sample output from this calculation appears in the Percent column.

`LEAD_VARIANCE_PERCENT (GLOBAL.UNITS_CUBE.UNITS, 1, CLOSEST) OVER (DIMENSION GLOBAL.TIME BY ANCESTOR AT DIMENSION LEVEL GLOBAL.TIME.CALENDAR_QUARTER)`

| Time     | Parent    | Units  | Next Qtr | Difference | Percent |
|:---------|:----------|:-------|:---------|:-----------|:--------|
| `2005`   | TOTAL     | 565718 | --       | --         | --      |
| `Q1-05`  | CY2005    | 143607 | 138096   | 5511       | .04     |
| `Q2-05`  | CY2005    | 138096 | 138953   | -857       | -.01    |
| `Q3-05`  | CY2005    | 138953 | 145062   | -6109      | -.04    |
| `Q4-05`  | CY2005    | 145062 | 146819   | -1757      | -.01    |
| `Jan-05` | CY2005.Q1 | 50098  | 40223    | 9875       | .25     |
| `Feb-05` | CY2005.Q1 | 43990  | 45477    | -1487      | -.03    |
| `Mar-05` | CY2005.Q1 | 49519  | 52396    | -2877      | -.05    |
| `Apr-05` | CY2005.Q2 | 40223  | 45595    | -5372      | -.12    |
| `May-05` | CY2005.Q2 | 45477  | 46882    | -1405      | -.03    |
| `Jun-05` | CY2005.Q2 | 52396  | 46476    | 5920       | .13     |
| `Jul-05` | CY2005.Q3 | 45595  | 47476    | -1881      | -.04    |
| `Aug-05` | CY2005.Q3 | 46882  | 47496    | -614       | -.01    |
| `Sep-05` | CY2005.Q3 | 46476  | 50090    | -3614      | -.07    |
| `Oct-05` | CY2005.Q4 | 47476  | 47776    | -300       | -.01    |
| `Nov-05` | CY2005.Q4 | 47496  | 47695    | -199       | 0       |
| `Dec-05` | CY2005.Q4 | 50090  | 51348    | -1258      | -.02    |

#### Related Topics

LAG, LEAD, LEAD_VARIANCE

### 2.20 MAX

`MAX` returns the largest of a selection of data values calculated over a Time dimension.

The `GREGORIAN` relations superimpose the Gregorian calendar on the Time dimension. These relations can be useful for calculations on fiscal and nonstandard hierarchies.

#### Return Value

    NUMBER

#### Syntax

    MAX (value_expr) OVER (window_clause)

window_clause::=

    [ { DIMENSION dimension_id | HIERARCHY hierarchy_id } ]
        BETWEEN preceding_boundary | following_boundary
         [WITHIN { PARENT
                 | LEVEL
                 | GREGORIAN {YEAR | QUARTER | MONTH | WEEK}
                 | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                               | HIERARCHY LEVEL hier_level_id
                               }
                 }
         ]

preceding_boundary::=

    {UNBOUNDED PRECEDING | expression PRECEDING} AND
       { CURRENT MEMBER
       | expression {PRECEDING | FOLLOWING}
       | UNBOUNDED FOLLOWING
       }

following_boundary::=

    {CURRENT MEMBER | expression FOLLOWING} AND
      { expression FOLLOWING
      | UNBOUNDED FOLLOWING
      }

#### Arguments

| Range               | Description                                                                              |
|:--------------------|:-----------------------------------------------------------------------------------------|
| `LEVEL`             | Calculates all time periods at the same level. (Default)                                 |
| `PARENT`            | Calculates time periods at the same level with the same parent.                          |
| `GREGORIAN YEAR`    | Calculates time periods within the same Gregorian year.                                  |
| `GREGORIAN QUARTER` | Calculates time periods within the same Gregorian quarter.                               |
| `GREGORIAN MONTH`   | Calculates time periods within the same Gregorian month.                                 |
| `GREGORIAN WEEK`    | Calculates time periods within the same Gregorian week.                                  |
| `ANCESTOR`          | Includes time periods at the same level and with the same ancestor at a specified level. |

#### value_expr

A dimensional expression whose values you want to calculate.

#### dimension_id

The Time dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### boundaries

The preceding_boundary and following_boundary identify a range of time periods within the group identified by the dimension or hierarchy.

`UNBOUNDED` starts with the first period or ends with the last period of the group.

`CURRENT MEMBER` starts or ends the calculation at the current time period.

#### expression

A numeric value identifying a period at a particular distance from the current time period that starts or ends the range.

#### WITHIN subclause

Identifies the range of time periods used in the calculation. Following are descriptions of the keywords.

#### Example

This example calculates a moving maximum within the calendar year.

`MAX(GLOBAL.UNITS_CUBE.UNITS) OVER (DIMENSION GLOBAL.TIME BETWEEN UNBOUNDED PRECEDING AND CURRENT MEMBER WITHIN ANCESTOR AT DIMENSION LEVEL GLOBAL.TIME.CALENDAR_YEAR)`

| Time   | Units | Maximum |
|:-------|:------|:--------|
| JAN-06 | 47776 | 47776   |
| FEB-06 | 47695 | 47776   |
| MAR-06 | 51348 | 51348   |
| APR-06 | 47005 | 51348   |
| MAY-06 | 52809 | 52809   |
| JUN-06 | 45419 | 52809   |
| JUL-06 | 48388 | 52809   |
| AUG-06 | 48830 | 52809   |
| SEP-06 | 46354 | 52809   |
| OCT-06 | 47411 | 52809   |
| NOV-06 | 46842 | 52809   |
| DEC-06 | 55052 | 55052   |

#### Related Topics

AVG, COUNT, MIN, SUM

### 2.21 MIN

`MIN` returns the smallest of a selection of data values calculated over a Time dimension.

The `GREGORIAN` relations superimpose the Gregorian calendar on the Time dimension. These relations can be useful for calculations on fiscal and nonstandard hierarchies.

#### Return Value

    NUMBER

#### Syntax

    MIN (value_expr) OVER (window_clause)

window_clause::=

    [ { DIMENSION dimension_id | HIERARCHY hierarchy_id } ]
        BETWEEN preceding_boundary | following_boundary
         [WITHIN { LEVEL
                 | PARENT
                 | GREGORIAN {YEAR | QUARTER | MONTH | WEEK}
                 | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                               | HIERARCHY LEVEL hier_level_id
                               }
                 }
         ]

preceding_boundary::=

    {UNBOUNDED PRECEDING | expression PRECEDING} AND
       { CURRENT MEMBER
       | expression {PRECEDING | FOLLOWING}
       | UNBOUNDED FOLLOWING
       }

following_boundary::=

    {CURRENT MEMBER | expression FOLLOWING} AND
      { expression FOLLOWING
      | UNBOUNDED FOLLOWING
      }

#### Arguments

| Range               | Description                                                                              |
|:--------------------|:-----------------------------------------------------------------------------------------|
| `LEVEL`             | Calculates all time periods at the same level. (Default)                                 |
| `PARENT`            | Calculates time periods at the same level with the same parent.                          |
| `GREGORIAN YEAR`    | Calculates time periods within the same Gregorian year.                                  |
| `GREGORIAN QUARTER` | Calculates time periods within the same Gregorian quarter.                               |
| `GREGORIAN MONTH`   | Calculates time periods within the same Gregorian month.                                 |
| `GREGORIAN WEEK`    | Calculates time periods within the same Gregorian week.                                  |
| `ANCESTOR`          | Includes time periods at the same level and with the same ancestor at a specified level. |

#### value_expr

A dimensional expression whose values you want to calculate.

#### dimension_id

The Time dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### boundaries

The preceding_boundary and following_boundary identify a range of time periods within the group identified by the dimension or hierarchy.

`UNBOUNDED` starts with the first period or ends with the last period of the group.

`CURRENT MEMBER` starts or ends the calculation at the current time period.

#### expression

A numeric value identifying a period at a particular distance from the current time period that starts or ends the range.

#### WITHIN subclause

Identifies the range of time periods used in the calculation. Following are descriptions of the keywords.

#### Example

This example calculates the minimum value between the current member and all subsequent members in the same calendar year. The selection of the data displays the minimum values for the months in 2006.

`MIN(GLOBAL.UNITS_CUBE.UNITS) OVER (DIMENSION GLOBAL.TIME BETWEEN CURRENT MEMBER AND UNBOUNDED FOLLOWING WITHIN ANCESTOR AT DIMENSION LEVEL GLOBAL.TIME.CALENDAR_YEAR)`

| Time   | Units | Minimum |
|:-------|:------|:--------|
| JAN-06 | 47776 | 45419   |
| FEB-06 | 47695 | 45419   |
| MAR-06 | 51348 | 45419   |
| APR-06 | 47005 | 45419   |
| MAY-06 | 52809 | 45419   |
| JUN-06 | 45419 | 45419   |
| JUL-06 | 48388 | 46354   |
| AUG-06 | 48830 | 46354   |
| SEP-06 | 46354 | 46354   |
| OCT-06 | 47411 | 46842   |
| NOV-06 | 46842 | 46842   |
| DEC-06 | 55052 | 55052   |

#### Related Topics

AVG, COUNT, MAX, SUM

### 2.22 OLAP_DML_EXPRESSION

`OLAP_DML_EXPRESSION` executes an expression in the OLAP DML language.

#### Return Value

The data type specified in the syntax

#### Syntax

    OLAP_DML_EXPRESSION (expression, datatype)

#### Arguments

#### expression

An expression in the OLAP DML language, such as a call to a function or a program.

#### datatype

The data type of the return value from `expression`.

#### Example

In this example, the `OLAP_DML_EXPRESSION` function executes the OLAP DML `RANDOM` function to generate a calculated measure with random numbers between 1.05 and 1.10.

`OLAP_DML_EXPRESSION('RANDOM(1.05, 1.10)', NUMBER)`

| Time | Product        | Random     |
|:-----|:---------------|:-----------|
| 2005 | Hardware       | 1.07663806 |
| 2005 | Software/Other | 1.08295738 |
| 2006 | Hardware       | 1.08707305 |
| 2006 | Software/Other | 1.09730881 |

### 2.23 RANK

`RANK` orders the members of a dimension based on the values of an expression. The function returns the sequence numbers of the dimension members.

`RANK` assigns the same rank to identical values. For example, `RANK` may return 1, 2, 3, 3, 5 for a series of five dimension members.

#### Return Value

    NUMBER

#### Syntax

    RANK ( ) OVER (rank_clause)

rank_clause::=

    { DIMENSION dimension_id | HIERARCHY hierarchy_id }
      ORDER BY order_by_clause [, order_by_clause]...
      [ WITHIN { PARENT
               | LEVEL
               | ANCESTOR AT { DIMENSION LEVEL dim_lvl_id
                             | HIERARCHY LEVEL hier_level_id
                             }
               }
      ]

order_by_clause::=

    expression [ASC | DESC] [NULLS {FIRST | LAST}]

#### Arguments

`PARENT` ranks members at the same level with the same parent.

`LEVEL` ranks all members at the same level.

`ANCESTOR` ranks all members at the same level and with the same ancestor at a specified level.

#### dimension_id

The dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, then the default hierarchy is used.

#### ORDER BY

Provides the basis for the ranking. You can provide additional `ORDER BY` clauses to break any ties in the order.

#### expression

Provides the values to use as the basis for the rankings.

#### ASC \| DESC

Sorts the ranking from smallest to largest (ascending) or from largest to smallest (descending).

#### NULLS {FIRST \| LAST}

Determines whether members with null values are listed first or last.

#### WITHIN

Selects a set of related dimension members to be ranked.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### Example

This example ranks time periods within a calendar year by Unit Cost. Notice that no month is ranked 7, because two months (JAN-02 and JUL-02) have the same value and the same rank (6).

`RANK() OVER (DIMENSION TIME.CALENDAR ORDER BY PRICE_CUBE.UNIT_COST DESC NULLS LAST WITHIN ANCESTOR AT DIMENSION LEVEL TIME.CALENDAR_YEAR)`

| Product      | Time   | Cost  | Rank |
|:-------------|:-------|:------|:-----|
| Deluxe Mouse | MAR-02 | 24.05 | 1    |
| Deluxe Mouse | APR-02 | 23.95 | 2    |
| Deluxe Mouse | FEB-02 | 23.94 | 3    |
| Deluxe Mouse | AUG-02 | 23.88 | 4    |
| Deluxe Mouse | MAY-02 | 23.84 | 5    |
| Deluxe Mouse | JAN-02 | 23.73 | 6    |
| Deluxe Mouse | JUL-02 | 23.73 | 6    |
| Deluxe Mouse | JUN-02 | 23.72 | 8    |
| Deluxe Mouse | SEP-02 | 23.71 | 9    |
| Deluxe Mouse | NOV-02 | 23.65 | 10   |
| Deluxe Mouse | DEC-02 | 23.62 | 11   |
| Deluxe Mouse | OCT-02 | 23.37 | 12   |

#### Related Topics

AVERAGE_RANK, DENSE_RANK, ROW_NUMBER

### 2.24 ROW_NUMBER

`ROW_NUMBER` orders the members of a dimension based on the values of an expression. The function returns the sequence numbers of the dimension members.

`ROW_NUMBER` assigns a unique rank to each dimension member; for identical values, the rank is arbitrary. For example, `ROW_NUMBER` always returns 1, 2, 3, 4, 5 for a series of five dimension members, even when they have the same value.

#### Return Value

    NUMBER

#### Syntax

    ROW_NUMBER ( ) OVER (rank_clause)

rank_clause::=

    { DIMENSION dimension_id | HIERARCHY hierarchy_id }
      ORDER BY order_by_clause [, order_by_clause]...
      [ WITHIN { PARENT
               | LEVEL
               | ANCESTOR AT { DIMENSION LEVEL dim_lvl_id
                             | HIERARCHY LEVEL hier_level_id
                             }
               }
      ]

order_by_clause::=

    expression [ASC | DESC] [NULLS {FIRST | LAST}]

#### Arguments

`PARENT` ranks members at the same level with the same parent.

`LEVEL` ranks all members at the same level.

`ANCESTOR` ranks all members at the same level and with the same ancestor at a specified level.

#### dimension_id

The dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, then the default hierarchy is used.

#### ORDER BY

Provides the basis for the ranking. You can provide additional `ORDER BY` clauses to break any ties in the order.

#### expression

Provides the values to use as the basis for the rankings.

#### ASC \| DESC

Sorts the ranking from smallest to largest (ascending) or from largest to smallest (descending).

#### NULLS {FIRST \| LAST}

Determines whether members with null values are listed first or last.

#### WITHIN

Selects a set of related dimension members to be ranked.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### Example

This example ranks time periods within a calendar year by Unit Cost. Notice even though two months (JAN-02 and JUL-02) have the same value, they are assigned sequential numbers (6 and 7).

`ROW_NUMBER() OVER (HIERARCHY TIME.CALENDAR ORDER BY PRICE_CUBE.UNIT_COST DESC NULLS LAST WITHIN ANCESTOR AT DIMENSION LEVEL TIME.CALENDAR_YEAR)`

| Product      | Time   | Cost  | Row Number |
|:-------------|:-------|:------|:-----------|
| Deluxe Mouse | MAR-02 | 24.05 | 1          |
| Deluxe Mouse | APR-02 | 23.95 | 2          |
| Deluxe Mouse | FEB-02 | 23.94 | 3          |
| Deluxe Mouse | AUG-02 | 23.88 | 4          |
| Deluxe Mouse | MAY-02 | 23.84 | 5          |
| Deluxe Mouse | JAN-02 | 23.73 | 6          |
| Deluxe Mouse | JUL-02 | 23.73 | 7          |
| Deluxe Mouse | JUN-02 | 23.72 | 8          |
| Deluxe Mouse | SEP-02 | 23.71 | 9          |
| Deluxe Mouse | NOV-02 | 23.65 | 10         |
| Deluxe Mouse | DEC-02 | 23.62 | 11         |
| Deluxe Mouse | OCT-02 | 23.37 | 12         |

#### Related Topics

AVERAGE_RANK, DENSE_RANK, RANK

### 2.25 SHARE

`SHARE` calculates the ratio of an expression's value for the current dimension member to the value for a related member of the same dimension. Arguments to this function identify which related member is used in the ratio.

#### Return Value

    NUMBER

#### Syntax

share_expression::=

    SHARE (expression share_clause [share_clause]... )


share_clause::=

    OF { DIMENSION dimension_id | HIERARCHY hierarchy_id }
       { PARENT
       | TOP
       | MEMBER 'member_name'
       | DIMENSION LEVEL dim_level_id
       | HIERARCHY LEVEL hier_level_id
       }

#### Arguments

Share is calculated with these formulas:

| Keyword           | Formula                                                                                                |
|:------------------|:-------------------------------------------------------------------------------------------------------|
| `PARENT`          | current member/parent                                                                                  |
| `TOP`             | current member/root ancestor                                                                           |
| `MEMBER`          | current member/specified member                                                                        |
| `DIMENSION LEVEL` | current member/ancestor at specified level or null if the current member is above the specified level. |

#### expression

A dimensional expression whose values you want to calculate.

#### dimension_id

A dimension of `expression`. The default hierarchy is used in the calculation. If you want to use a different hierarchy, then use the `HIERARCHY` argument instead.

#### hierarchy_id

A level hierarchy of `expression`.

#### member_name

A member of the specified dimension or hierarchy.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### Example

This example calculates the percent share of the parent member for each product. The results appear in the Share of Parent column.

`(SHARE(UNITS_CUBE.SALES OF HIERARCHY PRODUCT.PRIMARY PARENT))*100`

The next example calculates the percent share of Total Product for each product. The results appear in the Share of Top column.

`(SHARE(UNITS_CUBE.SALES OF HIERARCHY PRODUCT.PRIMARY TOP))*100`

| Product           | Parent | Sales     | Share of Parent | Share of Top |
|:------------------|:-------|:----------|:----------------|:-------------|
| Desktop PCs       | HRD    | 74556528  | 60              | 54           |
| Portable PCs      | HRD    | 18338225  | 15              | 13           |
| CD/DVD            | HRD    | 16129497  | 13              | 12           |
| Memory            | HRD    | 5619219   | 5               | 4            |
| Modems/Fax        | HRD    | 5575726   | 4               | 4            |
| Monitors          | HRD    | 3972142   | 3               | 3            |
| Accessories       | SFT    | 6213535   | 49              | 5            |
| Operating Systems | SFT    | 4766857   | 37              | 3            |
| Documentation     | SFT    | 1814844   | 14              | 1            |
| Hardware          | TOTAL  | 124191336 | 91              | 91           |
| Software/Other    | TOTAL  | 12795236  | 9               | 9            |

### 2.26 SUM

`SUM` returns the total of a selection of values calculated over a Time dimension. You can use the `SUM` function to create period-to-date calculations.

The `GREGORIAN` relations superimpose the Gregorian calendar on the Time dimension. These relations can be useful for calculations on fiscal and nonstandard hierarchies.

#### Return Value

    NUMBER

#### Syntax

    SUM (value_expr) OVER (window_clause)

window_clause::=

    [ { DIMENSION dimension_id | HIERARCHY hierarchy_id } ]
        BETWEEN preceding_boundary | following_boundary
          [WITHIN { PARENT
                  | LEVEL
                  | GREGORIAN {YEAR | QUARTER | MONTH | WEEK}
                  | ANCESTOR AT { DIMENSION LEVEL dim_level_id
                                | HIERARCHY LEVEL hier_level_id
                                }
                  }
          ]

preceding_boundary::=

    {UNBOUNDED PRECEDING | expression PRECEDING} AND
       { CURRENT MEMBER
       | expression {PRECEDING | FOLLOWING}
       | UNBOUNDED FOLLOWING
       }

following_boundary::=

    {CURRENT MEMBER | expression FOLLOWING} AND
      { expression FOLLOWING
      | UNBOUNDED FOLLOWING
      }

#### Arguments

| Range               | Description                                                                              |
|:--------------------|:-----------------------------------------------------------------------------------------|
| `LEVEL`             | Calculates all time periods at the same level. (Default)                                 |
| `PARENT`            | Calculates time periods at the same level with the same parent.                          |
| `GREGORIAN YEAR`    | Calculates time periods within the same Gregorian year.                                  |
| `GREGORIAN QUARTER` | Calculates time periods within the same Gregorian quarter.                               |
| `GREGORIAN MONTH`   | Calculates time periods within the same Gregorian month.                                 |
| `GREGORIAN WEEK`    | Calculates time periods within the same Gregorian week.                                  |
| `ANCESTOR`          | Includes time periods at the same level and with the same ancestor at a specified level. |

#### value_expr

A dimensional expression whose values you want to calculate.

#### dimension_id

The Time dimension over which the values are calculated using the default hierarchy.

#### hierarchy_id

The hierarchy over which the values are calculated. If `dimension_id` is used instead, the default hierarchy is used.

#### dim_level_id

The name of a level of `dimension_id`.

#### hier_level_id

The name of a level of `hierarchy_id`.

#### boundaries

The preceding_boundary and following_boundary identify a range of time periods within the group identified by the dimension or hierarchy.

`UNBOUNDED` starts with the first period or ends with the last period of the group.

`CURRENT MEMBER` starts or ends the calculation at the current time period.

#### expression

A numeric value identifying a period at a particular distance from the current time period that starts or ends the range.

#### WITHIN subclause

Identifies the range of time periods used in the calculation. Following are descriptions of the keywords.

#### Example

This example calculates the sum of two values, for the current and the following time periods, within a level. The results appear in the Sum column.

`SUM(UNITS_CUBE.SALES) OVER (DIMENSION "TIME" BETWEEN 1 PRECEDING AND CURRENT MEMBER WITHIN LEVEL)`

| Time  | Sales  | Sum    |
|:------|:-------|:-------|
| Q1.04 | 146529 | 289599 |
| Q2.04 | 143070 | 291362 |
| Q3.04 | 148292 | 297820 |
| Q4.04 | 149528 | 293135 |
| Q1.05 | 143607 | 281703 |
| Q2.05 | 138096 | 277049 |
| Q3.05 | 138953 | 284015 |
| Q4.05 | 145062 | 291881 |

The next example calculates Year-to-Date Sales.

`SUM(UNITS_CUBE.SALES) OVER (HIERARCHY TIME.CALENDAR BETWEEN UNBOUNDED PRECEDING AND CURRENT MEMBER WITHIN ANCESTOR AT DIMENSION LEVEL TIME.CALENDAR_YEAR)`

| Time   | Sales    | Sales YTD |
|:-------|:---------|:----------|
| JAN-05 | 12093518 | 12093518  |
| FEB-05 | 10103162 | 22196680  |
| MAR-05 | 9184658  | 31381338  |
| APR-05 | 9185964  | 40567302  |
| MAY-05 | 11640216 | 52207519  |
| JUN-05 | 16816561 | 69024079  |
| JUL-05 | 11110903 | 80134982  |
| AUG-05 | 9475807  | 89610789  |
| SEP-05 | 12030538 | 101641328 |
| OCT-05 | 11135032 | 112776359 |
| NOV-05 | 11067754 | 123844113 |

#### Related Topics

AVG, COUNT, MAX, MIN
