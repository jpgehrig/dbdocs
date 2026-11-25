This chapter provides reference topics for the second set (in alphabetical order) of the OLAP DML functions. There is one topic for each of the OLAP DML functions that begins with the letters L-Z, beginning with LAG.

Alphabetical and categorical listings of the OLAP DML functions and reference topics for the remaining OLAP DML functions appear in [OLAP DML Functions: A - K](olap-dml-functions-a-k.md).

For other OLAP DML reference topics, see [OLAP DML Properties](olap-dml-properties.md), [OLAP DML Options](olap-dml-options.md), [OLAP DML Commands: A-G](olap-dml-commands-a-g.md), and [OLAP DML Commands: H-Z](olap-dml-commands-h-z.md).

**Tip:**

Many OLAP DML statements can be coded as a 3-character abbreviation that consists of the first letter of the statement plus the next two consonants.

### 8.1 LAG

The LAG function returns the values of a dimensioned variable or expression at a specified offset of a dimension before the current value of that dimension. Typically, you use the LAG function to retrieve values for a previous time period.

#### Return Value

The data type of the variable argument or `NA` when you try to lag before the first period of a time dimension.

#### Syntax

LAG(variable n, dimension, \[STATUS\|NOSTATUS\|limit-clause\])

#### Parameters

variable
A variable or expression that is dimensioned by dimension.

n
The offset (that is, the number of dimension values) to lag. LAG uses this value to determine the number of values that LAG should go back in dimension to retrieve the value of variable.

Typically, n is a positive `INTEGER` that indicates the number of time periods (or dimension values) before the current one. When you specify a negative value for n, it indicates the number of time periods after the current o ne. In other words, using a negative value for n turns LAG into a LEAD function.

**Note:**

When using LAG in a model, see "[Ensuring One-Way Dimensional Dependence](formulas-models-aggregations-and-allocations.md)" for information on how to code a value for `n` so that Oracle OLAP does not use simultaneous blocks when solving the model.

dimension
The dimension along which the lag occurs. While this can be any dimension, it is typically a hierarchical time dimension of type TEXT that is limited to a single level (for example, the month or year level) or a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR.

When variable has a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR and you want LAG to use that dimension, you can omit the dimension argument.

STATUS
Specifies that LAG should use the current status list (that is, only the dimension values currently in status in their current status order) when computing the lag.

NOSTATUS
(Default) Specifies that LAG should use the default status (that is, a list all the dimension values in their original order) when computing the lag.

limit-clause
Specifies that LAG should use the default status limited by limit-clause when computing the lag.

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

To specify that LAG should use the current status limited by limit-clause when computing the lag, specify a LIMIT function for limit-clause.

#### Usage Notes

#### Assigning Results to a Time-Series Variable

Use care when assigning the results of LAG back into the time-series variable. Results are assigned one cell at a time, so you can overwrite the whole array with the first value returned, instead of moving all the values over n positions. You can, however, use LAG to calculate a series of values based on the initial value.

#### Examples

Example 8-1 Using LAG

Assume that you have the following definitions in your analytic workspace.

    DEFINE time DIMENSION TEXT
    DEFINE timelevels DIMENSION TEXT
    DEFINE timelevelrel RELATION timelevels <time>
    DEFINE product DIMENSION TEXT
    DEFINE district DIMENSION TEXT
    DEFINE sales VARIABLE DECIMAL <time product district>


Assume also that those object have the values shown in the following reports.

    REPORT timelevelrel

    TIME           TIMELEVELREL
    -------------- ----------
    AllYears       AllYears
    2004           Years
    2005           Years
    2006           Years
    Jan2005        Months
    Feb2005        Months
    Mar2005        Months
    Apr2005        Months
    ...            ...
    Oct2006        Months
    Nov2006        Months
    Dec2006        Months


    REPORT product

    PRODUCT
    --------------
    TVs
    DVDs
    Computers

    REPORT district

    DISTRICT
    --------------
    All Districts
    Mass
    Conn
    Boston
    Springfield
    Hartford
    New Haven


Now assume that you issue the following LIMIT statements to limit product, district, and time.

    LIMIT product TO 'TVs'
    LIMIT district TO 'Hartford'
    LIMIT time TO 'Jan2006' 'Feb2006' 'Mar2006' 'Apr2006' 'May2006' 'Jun2006' 'Jul2006' 'Aug2006' 'Sep2006' 'Oct2006' 'Nov2006' 'Dec2006'


You can issue a REPORT statement with LAG to show the value of sales for months in both 2006 and for 2005.

    REPORT DOWN time HEADING 'Sales 2006' sales HEADING 'Sales 2005' LAG(sales, 12, time, RELATION timelevelrel)


    DISTRICT: Hartford
                   -------PRODUCT-------
                   ---------TVs---------
    TIME           Sales 2006 Sales 2005
    -------------- ---------- ----------
    Jan2006          1,542.91   1,627.51
    Feb2006          1,786.07   1,100.13
    Mar2006          1,794.43   1,667.61
    Apr2006          1,942.92   1,346.66
    May2006          1,530.08   1,509.51
    Jun2006          1,613.60   1,242.47
    Jul2006          1,666.35   1,307.17
    Aug2006          1,413.79   1,033.93
    Sep2006          1,526.98   1,773.96
    Oct2006          1,112.85   1,103.78
    Nov2006          1,193.41   1,132.39
    Dec2006          1,851.19   1,543.62

### 8.2 LAGABSPCT

The LAGABSPCT function returns the percentage difference between the value of a dimensioned variable or expression at a specified offset of a dimension before the current value of that dimension and the current value of the dimensioned variable or expression.

Unlike the LAGPCT function, which always uses the sign of the previous period value in calculating the result, LAGABSPCT uses the absolute value of the previous period value and therefore provides the direction of the percentage difference.

**See Also:**

"Example 8-2"

#### Return Value

DECIMAL value that corresponds to a percent difference or `NA` when you try to lag before the first period of a time dimension.

#### Syntax

LAGABSPCT(variable, n, dimension, \[STATUS\|NOSTATUS\|limit-clause\] )

#### Parameters

time-series
A variable or expression that is dimensioned by dimension.

n
The offset (that is, the number of dimension values) to lag. LAGABSPCT uses this value to determine the number of values that LAGABSPCT should go back in dimension to retrieve the value of variable.

Typically, n is a positive `INTEGER` that indicates the number of time periods (or dimension values) before the current one. When you specify a negative value for n, it indicates the number of time periods after the current one. In this case, LAGABSPCT compares the current value of the time series with a subsequent value.

dimension
The dimension along which the lag occurs. While this can be any dimension, it is typically a hierarchical time dimension of type TEXT that is limited to a single level (for example, the month or year level) or a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR.

When variable has a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR and you want LAGABSPCT to use that dimension, you can omit the dimension argument.

STATUS
Specifies that LAGABSPCT should use the current status list (that is, only the dimension values currently in status in their current status order) when computing the lag.

NOSTATUS
(Default) Specifies that LAGABSPCT should use the default status (that is, a list all the dimension values in their original order) when computing the lag.

limit-clause
Specifies that LAGABSPCT should use the default status limited by limit-clause when computing the lag.

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

To specify that LAG should use the current status limited by limit-clause when computing the lag, specify a LIMIT function for limit-clause.

#### Usage Notes

Formula Used by LAGABSPCT

To obtain its results, LAGABSPCT uses the following formula.

    (currentvalue - previousvalue) / ABS(previousvalue)

When the Previous Value of the Time Series Used by LAGABSPCT is Zero

When the previous value of the time series used by LAGABSPCT is zero, the result LAGABSPCT returns is determined by the DIVIDEBYZERO option. When DIVIDEBYZERO is set to `NO`, an error occurs. When DIVIDEBYZERO is set to `YES`, LAGABSPCT returns `NA`.

#### Examples

Example 8-2 Using LAGDIF and LAGABSPCT

Suppose you have a variable called `sales` that is dimensioned by a hierarchical dimension named `time`, and dimensions called `district` and `products`. Assume also that there is a dimension named `timelevels` that contains the names of the levels of the `time` dimension (that is, `Month` and `Year`) and a relation named `timelevelrel` that is dimensioned by `time` and that has values from `timelevels` (that is, the related dimension of `timelevelrel` is `timelevels`).

You want to compare sales for racquets in Dallas for the January, 2000 and the previous year. You can use the LAG function to display sales from the previous years. You can use the LAGABSPCT function to calculate the percentage difference between the two months and indicate the direction of the change. For example, when sales increase, the percentage difference LAGABSPCT returns is positive. When sales decrease, the percentage difference LAGABSPCT returns is negative.

You can also use the LAGPCT function to calculate the percentage difference between two years. You can multiply the values returned by LAGABSPCT by 100 to display them as percentage points.

The following statements

    ALLSTAT
    LIMIT product TO 'Racquets'
    LIMIT district TO 'Dallas'
    LIMIT time TO 'Jan2000'
    REPORT DOWN time sales -
    HEADING 'Last Jan' LAG(sales, 12, time, time LEVELREL timelevelrel)-
    HEADING 'Lagdif' LAGDIF(sales, 12, time, time LEVELREL timelevelrel)-
    HEADING 'Lagabspct' rset '%' d 0 LAGABSPCT(sales, 12, time, -
                        time LEVELREL timelevelrel) * 100

produce this report.

    DISTRICT: Dallas
                   ------------------PRODUCT------------------
                   -----------------Racquets------------------
    TIME           SALES      Last Jan   Lagdif     Lagabspct
    -------------- ---------- ---------- ---------- ----------
    Jan2000        125,879.86 118,686.75 7,193.11   6%

### 8.3 LAGDIF

The LAGDIF function returns the difference between the value of a dimensioned variable or expression at a specified offset of a dimension before the current value of that dimension and the current value of the dimensioned variable or expression.

**See Also:**

"Example 8-2"

#### Return Value

DECIMAL or `NA` when you try to lag before the first period of a time dimension.

#### Syntax

LAGDIF(variable, n, dimension, \[STATUS\|NOSTATUS\|limit-clause\] )

#### Parameters

variable
A variable or expression that is dimensioned by dimension.

n
The offset (that is, the number of dimension values) to lag. LAGDIF uses this value to determine the number of values that LAGDIF should go back in dimension to retrieve the value of variable. Typically, n is a positive `INTEGER` that indicates the number of time periods (or dimension values) before the current one. When you specify a negative value for n, it indicates the number of time periods after the current one. In this case, LAGDIF compares the current value of the time series with a subsequent value.

dimension
The dimension along which the lag occurs. While this can be any dimension, it is typically a hierarchical time dimension of type TEXT that is limited to a single level (for example, the month or year level) or a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR.

When variable has a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR and you want LAGDIF to use that dimension, you can omit the dimension argument.

STATUS
Specifies that LAGDIF should use the current status list (that is, only the dimension values currently in status in their current status order) when computing the lag.

NOSTATUS
(Default) Specifies that LAGDIF should use the default status (that is, a list all the dimension values in their original order) when computing the lag.

limit-clause
Specifies that LAGDIF should use the default status limited by limit-clause when computing the lag.

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

To specify that LAG should use the current status limited by limit-clause when computing the lag, specify a LIMIT function for limit-clause.

#### Examples

For an example of using LAGDIF, see Example 8-2.

### 8.4 LAGPCT

The LAGPCT function returns the percentage difference between the value of a dimensioned variable or expression at a specified offset of a dimension before the current value of that dimension and the current value of the dimensioned variable or expression.

**See Also:**

"Example 8-3"

#### Return Value

DECIMAL or `NA` when you try to lag before the first period of a dimension of a time dimension.

#### Syntax

LAGPCT(variable, n, \[dimension\], \[STATUS\|NOSTATUS\|limit-clause\] )

#### Parameters

variable
A variable or expression that is dimensioned by dimension.

n
The offset (that is, the number of dimension values) to lag. LAGPCT uses this value to determine the number of values that LAGPCT should go back in dimension to retrieve the value of variable. Typically, n is a positive `INTEGER` that indicates the number of time periods (or dimension values) before the current one. When you specify a negative value for n, it indicates the number of time periods after the current one. In this case, LAGPCT compares the current value of the time series with a subsequent value.

dimension
The dimension along which the lag occurs. While this can be any dimension, it is typically a hierarchical time dimension of type TEXT that is limited to a single level (for example, the month or year level) or a dimension with a type of DAY, WEEK, MONTH, QUARTER or YEAR.

When variable has a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR and you want LAGPCT to use that dimension, you can omit the dimension argument.

STATUS
Specifies that LAGPCT should use the current status list (that is, only the dimension values currently in status in their current status order) when computing the lag.

NOSTATUS
(Default) Specifies that LAGPCT should use the default status (that is, a list all the dimension values in their original order) when computing the lag.

limit-clause
Specifies that LAGPCT should use the default status limited by limit-clause when computing the lag.

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

To specify that LAG should use the current status limited by limit-clause when computing the lag, specify a LIMIT function for limit-clause.

#### Usage Notes

Formula Used by LAGPCT

To obtain its results, LAGPCT uses the following formula.

    (currentvalue - previousvalue) / previousvalue

When the Previous Value of the Time Series Used by LAGPCT is Zero

When the previous value of the time series used by LAGPCT is zero, the result LAGPCT returns is determined by the DIVIDEBYZERO option. When DIVIDEBYZERO is set to `NO`, an error occurs. When DIVIDEBYZERO is set to `YES`, LAGPCT returns `NA`.

#### Examples

Example 8-3 Using LAGPCT

Suppose you have a variable called `sales` that is dimensioned by a hierarchical dimension named `time`, and dimensions called `district` and `products`. Assume also that there is a dimension named `timelevels` that contains the names of the levels of the `time` dimension (that is, `Month` and `Year`) and a relation named `timelevelrel` that is dimensioned by `time` and that has values from `timelevels` (that is, the related dimension of `timelevelrel` is `timelevels`).

You can compare racquet sales in Dallas for 2000 with sales for 1999 by using the LAG function to show 199 values. You can use the LAGPCT function to calculate the percentage difference between the two. You can multiply the value LAGPCT returns by 100 and include a percent sign to display the difference as percentage points.

    ALLSTAT
    LIMIT product TO 'Racquets'
    LIMIT district TO 'Dallas'
    LIMIT TIME TO '2000'
    REPORT DOWN time sales HEADING 'Last Year' -
    LAG(sales, 1, time, time LEVELREL timelevelrel)-
    HEADING 'LAGPCT (Decimal Format)' -
    LAGPCT(sales, 1, time LEVELREL timelevelrel) -
    HEADING 'LAGPCT (Percent Format)' rset '%' -
    LAGPCT(sales, 1, time LEVELREL timelevelrel) * 100

produce this report.

    DISTRICT: Dallas
                   ------------------PRODUCT------------------
                   -----------------racquets------------------
                                         LAGPCT     LAGPCT
                                         (Decimal   (Percent
    TIME           SALES      Last Year  Format)    Format)
    -------------- ---------- ---------- ---------- ----------
    2000           93,000,003 89,000,891 0.04       4.49%

### 8.5 LARGEST

The LARGEST function returns the largest value of an expression. You can use this function to compare numeric values or date values.

#### Return Value

The data type of the expression. It can be INTEGER, LONGINT, DECIMAL, or DATE.

#### Syntax

LARGEST(expression \[CACHE\] \[dimension...\])

#### Parameters

expression
The expression whose largest value is to be returned.

CACHE
Specifies slightly different internal behavior. Specify this keyword only when the original performance is extremely slow.

dimension
The name of a dimension of the result; or, the name of a relation between one dimension of expression and another dimension that you want as a dimension of the result.

By default, LARGEST returns a single value. When you indicate one or more dimensions for the result, LARGEST tests for values along the dimensions that are specified and returns an array of values. Each dimension must be either a dimension of expression or related to one of its dimensions.

**Tip:**

When you specify a dimension that is not an actual dimension of expression, but, instead, is dimension that is related to a dimension of expression and when there are multiple relations between the two dimensions, Oracle OLAP uses the default relation between the dimensions to perform the calculation. (See the [RELATION command](olap-dml-commands-h-z.md) for more information on default relations.) When you do not want Oracle OLAP to use this default relation, specify the related dimension by specifying the name of a specify relation.

#### Usage Notes

NA Values and LARGEST

LARGEST is affected by the NASKIP option in the same manner as other aggregate functions. When NASKIP is set to `YES` (the default), LARGEST ignores `NA` values and returns the largest value or values that are not `NA`. When NASKIP is set to `NO`, LARGEST returns `NA` when any value of the expression is `NA`. When all the values of the expression are `NA`, LARGEST returns `NA` for either setting of NASKIP.

Using LARGEST With an Expression Dimensioned by a DWMQY Dimension

When expression is dimensioned by a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, you can specify any other DAY, WEEK, MONTH, QUARTER, or YEAR dimension as a related dimension. Oracle OLAP uses the implicit relation between the dimensions. To control the mapping of one DAY, WEEK, MONTH, QUARTER, or YEAR dimension to another (for example, from weeks to months), you can define an explicit relation between the two dimensions and specify the name of the relation as the dimension argument to the LARGEST function.

For each time period in the related dimension, Oracle OLAP finds the largest data value in any source time period that ends in the target time period. This method is used regardless of which dimension has the more aggregate periods.

#### Examples

Example 8-4 Finding the Largest Monthly Sales

This example uses the LARGEST function to find the largest monthly sportswear sales for each district during the first half of 1996. To see the largest sales figure for each district, specify `district` as the dimension of the results.

    LIMIT product TO 'Sportswear'
    LIMIT month TO 'Jan96' TO 'Jun96'
    REPORT HEADING 'Largest Sales' LARGEST(sales district)

The preceding statements produce the following output.

                    Largest
    DISTRICT         Sales
    -------------- ----------
    Boston          79,630.20
    Atlanta        177,967.49
    Chicago        112,792.78
    Dallas         175,716.31
    Denver          97,236.88
    Seattle         60,322.88

### 8.6 LAST_DAY

The LAST_DAY function returns the last day of the month in which a particular date falls.

#### Return Value

DATETIME

#### Syntax

LAST_DAY(datetime-expression)

#### Parameters

datetime-expression
An expression that has the DATETIME data type.

#### Examples

Example 8-5 Calculating Remaining Days in a Month

The following statement calculates how many days remain between today's date and the end of the month.

    SHOW JOINCHARS('Days left: ' LAST_DAY(SYSDATE) - SYSDATE)

When today's date is September 8, 2000, then this statement returns the following.

    Days left: 22

### 8.7 LEAD

The LEAD function returns the values of a dimensioned variable or expression at a specified offset of a dimension after the current value of that dimension. Typically, you use the LEAD function to retrieve values for a future time period.

#### Return Value

The data type of the variable argument or `NA` when you try to retrieve a value from beyond the last period defined for the time dimension.

#### Syntax

LEAD(variable, n, \[time-dimension\], \[\[STATUS\|NOSTATUS\|limit-clause\] )

#### Parameters

variable
A variable or expression that is dimensioned by dimension.

n
The offset (that is, the number of dimension values) to lead. LEAD uses this value to determine the number of values that LEAD should go ahead in dimension to retrieve the value of variable. To count the values, LEAD uses the default status, unless you use the STATUS keyword or the limit-clause argument to specify a different dimension status.

Normally, n is a positive `INTEGER` that indicates the number of time periods (or dimension values) after the current one. When you specify a negative value for n, it indicates the number of time periods before the current one. In effect, using a negative value for n turns LEAD into a LAG function.

**Note:**

When using LEAD in a model, see "[Ensuring One-Way Dimensional Dependence](formulas-models-aggregations-and-allocations.md)" for information on how to code a value for `n` so that Oracle OLAP does not use simultaneous blocks when solving the model.

dimension
The dimension along which the lead occurs. While this can be any dimension, it is typically a hierarchical time dimension of type TEXT that is limited to a single level (for example, the month or year level) or a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR.

When variable has a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR and you want LEAD to use that dimension, you can omit the dimension argument.

STATUS
Specifies that LEAD should use the current status list (that is, only the dimension values currently in status in their current status order) when computing the lead.

NOSTATUS
Specifies that LEAD should use the default status (that is, a list all the dimension values in their original order) when computing the lead.

limit-clause
Specifies that LEAD should use the default status limited by limit-clause when computing the lead.

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

To specify that LAG should use the current status limited by limit-clause when computing the lag, specify a LIMIT function for limit-clause.

#### Examples

Example 8-6 Using LEAD

Assume that you have a `sales` variable that is dimensioned by three dimensions of the TEXT type (named `product`, `district`, and `time`). The `time` dimension is a hierarchical dimension with the following values.

    1999
    2000
    Jan1999
    Feb1999
    ...
    Dec1999
    Jan2000
    Feb2000
    ...
    Dec2000

Also, assume that there is a dimension named `timelevels` that contains the names of the levels of the `time` dimension (that is, `Month` and `Year`) and a relation named `timelevelrel` that is dimensioned by `time` and that has values from `timelevels` (that is, the related dimension of `timelevelrel` is `timelevels`). A report of `timelevelrel` shows these relationships.

    TIME           TIMELEVELREL
    -------------- ------------
    1999           Year
    2000           Year
    Jan1999        Month
    Feb1999        Month
    ...            ...
    Dec1999        Month
    Jan2000        Month
    Feb2000        Month
    ...            ...
    Dec2000        Month

Suppose you want to compare racquet sales in Dallas for the first two months of 1999 with sales for the corresponding months of 2000. You can use the LEAD function to produce the values from 2000 in the same report with the 1999 values. The following statements

    LIMIT product TO 'Racquets'
    LIMIT district TO 'Dallas'
    LIMIT time TO 'JAN1999' 'FEB1999'
    REPORT DOWN time sales HEADING 'Following Year' LEAD(sales, 12, time, time LEVELREL timelevelrel)

produce this report.

    DISTRICT: DALLAS
                   -------PRODUCT-------
                   ------RACQUETS-------
    TIME           SALES      Following Year
    -------------- ---------- ---------------------
    Jan2000        118,686.75 125,879.86
    Feb2000        142,305.99 150,833.64

### 8.8 LEAST

The LEAST function returns the smallest expression in a list of expressions. All expressions after the first are implicitly converted to the data type of the first expression before the comparison.

To retrieve the largest expression in a list of expressions, use [GREATEST](olap-dml-functions-a-k.md).

#### Return Value

The data type of the first expression.

#### Syntax

LEAST (expr \[, expr\]...)

#### Parameters

expr
An expression.

#### Examples

Example 8-7 Finding the Text Expression that is First Alphabetically

The following statement returns the string that is first in alphabetic sequence.

    SHOW LEAST('Harry','Harriot','Harold')
    Harold

Example 8-8 Finding the Smallest Numerical Expressions

The following statement selects the number with the smallest value.

    SHOW LEAST (5, 3, 18)
    3

### 8.9 LENGTH functions

The LENGTH functions return the length of a text expression including trailing blanks. LENGTH calculates length using characters as defined by the input character set. LENGTHB uses bytes instead of characters. LENGTHC uses Unicode complete characters.

#### Return Value

NUMBER or NA if the expression is an empty string or NA

#### Syntax

{ LENGTH \| LENGTHB \| LENGTHC}(char)

#### Parameters

char
A text expression.

### 8.10 LIMIT function

The LIMIT function returns the dimension or dimension surrogate values that result from a specified LIMIT command or a specified dimension status stack. A dimension and any surrogate for that dimension share the same status. The LIMIT function does not change the status of a dimension or a valueset.

**See Also::**

[LIMIT command](olap-dml-commands-h-z.md)

#### Return Value

The return value varies depending on the use of the function and whether or not you specify the INTEGER keyword:

- When the LIMIT function is an argument to an OLAP DML statement (including a user-defined command or function) that expects a valueset, it returns a valueset.

- When the LIMIT function returns an empty valueset, it returns it as a valueset with null status.

- In all other cases, the LIMIT function returns either a TEXT value or an INTEGER value depending on whether or not you include the INTEGER keyword. When it returns a TEXT value that represents empty status, it returns it as `NA`.

#### Syntax

The syntax of the LIMIT function varies depending on whether you want to retrieve the values of the dimension or dimension surrogate values that result from a specified LIMIT command or the values of a specified dimension status stack.

Syntax for Retrieving Values From a LIMIT Command

LIMIT(\[INTEGER\] {dimension \| valueset \| LIMIT_function} \[concat-component\] limit-type -      \[limit-clause\] \[IFNONE label\])

Syntax for Retrieving Values From a Dimension Status Stack

LIMIT(\[INTEGER\] dimension  STATDEPTH stack-position\] \[IFNONE label\])

#### Parameters

dimension
See the [LIMIT command](olap-dml-commands-h-z.md) for a complete description of this argument.

valueset
See the [LIMIT command](olap-dml-commands-h-z.md) for a complete description of this argument.

LIMIT_function
Another LIMIT function.

**Note:**

When you nest LIMIT functions inside each other in this manner, the first argument of the innermost LIMIT function must be the a dimension or a valueset. See also "Nesting the LIMIT Function".

concat-component
See the [LIMIT command](olap-dml-commands-h-z.md) for a complete description of this argument.

limit-type
See the [LIMIT command](olap-dml-commands-h-z.md) for a complete description of this argument.

limit-clause
Specifies the values to use for the limit. There are several types of limit clauses— for example, a limit clause you can use to specifying the limit using values (including using a valueset) and a limit clause you can use to specify the limit using a related dimension. Each of these types of limit clauses has a very complex syntax. Because the syntax is complex, the syntax for the various types of limit clauses are documented separately as part of the following topics:

- [LIMIT (using values) command](olap-dml-commands-h-z.md)
- [LIMIT using LEVELREL command](olap-dml-commands-h-z.md)
- [LIMIT (using related dimension) command](olap-dml-commands-h-z.md)
- [LIMIT (using parent relation)](olap-dml-commands-h-z.md)
- [LIMIT NOCONVERT command](olap-dml-commands-h-z.md)
- [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md)
-

In the syntax of each of these LIMIT command topics, the limit-clause is that portion of the syntax following the limit-type argument.

INTEGER
When you use the INTEGER keyword, the function returns the position numbers of the values in the default dimension status rather than the names. When you use INTEGER with a valueset, the function returns the position numbers of the values in the default dimension status, not in the valueset.

STATDEPTH
Specifies that Oracle OLAP retrieve the status list values for the status list stack for the specified dimension.

stack-position
An INTEGER value that specifies the position in the status list stack from which to retrieve the values. Keep the following in mind when specifying a value:

- Values from `0` to `1-STATDEPTH(``dimension``)` retrieve stacked values from the top (current status) to the bottom (oldest status.)

- Values from `1` to `STATDEPTH(``dimension`) retrieve stacked values from the bottom of the stack (that is, the oldest status) to the top of the stack (that is, the current status).

See the STATDEPTH function for more information about status list stacks.

#### Usage Notes

Nesting the LIMIT Function

Use the following syntax to return the result of several LIMIT commands for the same dimension by nesting the LIMIT function.

LIMIT (LIMIT (LIMIT (lim-exp1) lim-exp2) lim-exp3)

Use this nested construction to find the status of a series of LIMIT commands. For example, the following are some LIMIT commands.

    LIMIT product TO division 'Camping'
    LIMIT product KEEP -
       EVERY(sales GT 50000, product)
    LIMIT product KEEP FIRST 1

To see the status of the preceding LIMIT commands, you execute the following statement.

    REPORT LIMIT(LIMIT(LIMIT(product TO -
       division 'Camping') KEEP EVERY -
       (sales GT 50000, product))KEEP FIRST 1)

Limiting with a Component of a Concat Dimension

You can limit a concat dimension to the current status of one of its component dimensions as in the following statement.

    LIMIT(reg.dist.ccdim TO district)

You can also limit a concat dimension to a set of the values of one of its component dimensions as in the following statement.

    LIMIT(reg.dist.ccdim TO district 'Boston' 'Chicago' 'Seattle')

Returning Multidimensional Results

The LIMIT function returns multidimensional results when evaluating multidimensional expressions. In the following example, the `sales` variable has three dimensions: `product`, `district`, and `month`.

    LIMIT product TO ALL
    LIMIT district TO 'Boston'
    LIMIT month TO 'Jan95' 'Feb95' 'Mar95'

A `REPORT sales` statement produces the following output.

    DISTRICT: BOSTON
              -------------SALES--------------
              -------------MONTH--------------
    PRODUCT     Jan95      Feb95      Mar95
    --------- ---------- ---------- ----------
    Tents      32,153.52  32,536.30  43,062.75
    Canoes     66,013.92  76,083.84  91,748.16
    Racquets   52,420.86  56,837.88  58,838.04
    Sportswear 53,194.70  58,913.40  62,797.80
    Footwear   91,406.82  86,827.32 100,199.46

Suppose you want a list of products whose sales exceed \$90,000 for the status shown in the preceding report. The LIMIT function evaluates the product sales in each month and district combination and produces a list that is dimensioned by the months and districts in status.

A `REPORT limit (product TO sales GT 90000)` statement produces the following output.

              ---LIMIT (PRODUCT TO SALES GT---
              -------------90000)-------------
              -------------MONTH--------------
    DISTRICT    Jan95      Feb95      Mar95
    --------- ---------- ---------- ----------
    Boston    Footwear   NA         Canoes
                                    Footwear

#### Examples

Example 8-9 Returning Multidimensional Results

This example prints a report of the products whose sales were greater than \$50,000 in the first two months of 1995 in Boston and Atlanta. Notice that the LIMIT function returns multidimensional results.

These statements

    LIMIT month TO 'Jan95' 'Feb95'
    LIMIT district TO 'Boston' 'Atlanta'
    LIMIT product TO ALL
    REPORT LIMIT (product TO sales GT 50000)

produce this report.

                   --LIMIT (PRODUCT TO--
                   ---SALES GT 50000)---
                   --------MONTH--------
    DISTRICT         JAn95      Feb95
    -------------- ---------- ----------
    Boston         Canoes     Canoes
                   Racquets   Racquets
                   Sportswear Sportswear
                   Footwear   Footwear
    Atlanta        Racquets   Canoes
                   Sportswear Racquets
                   Footwear   Sportswear
                              Footwear

Example 8-10 LIMIT Command with the LIMIT Function

The following example shows the LIMIT function being used as an argument to the LIMIT command. The result of the LIMIT function is converted to a valueset.

    ALLSTAT
    LIMIT month TO LIMIT (LIMIT (month TO LAST 10) KEEP FIRST 3)

After the preceding LIMIT statement, a `STATUS month` statement produces this output.

    The current status of MONTH is:
    MAR97 TO MAY97

### 8.11 LIMITMAPINFO

The LIMITMAPINFO function returns the analytic workspace expression that a specified limit map uses to map data into a specified column of a relational table.

#### Return Value

A TEXT expression.

#### Syntax

LIMITMAPINFO (\[aw\], limit-map, column-name)  

#### Parameters

aw
The name of the analytic workspace that contains the analytic workspace object.

limit-map
The limit map as a text expression.

column-name
The name of the column of a relational table as it appears in `limit-map`.

#### Examples

Example 8-11 Retrieving the Name of a Dimension

Assume that you have an analytic workspace named `myaw` that contains a text variable named `mylimitmap` that is a limit map that maps some analytic workspace data to a relational table with a column named `et_product`.

    MEASURE sales FROM aw_f.sales
    DIMENSION et_chan FROM aw_channel WITH
    HIERARCHY aw_channel.parent
    GID gid_chan FROM aw_channel.gid
    DIMENSION et_prod FROM aw_product WITH
    HIERARCHY aw_product.parent
    GID gid_prod FROM aw_prod.gid
    DIMENSION et_geog FROM aw_geography WITH
    HIERARCHY aw_geography.parent
    GID gid_geog FROM aw_geog.gid
    DIMENSION et_time FROM aw_time WITH
    HIERARCHY time.parent
    GID gid_time FROM aw_time.gid

To retrieve the name of the analytic workspace object from which data for the `et_prod` column is retrieved, you issue the following OLAP DML statement.

    show LIMITMAPINFO ('myaw', mylimitmap, 'et_prod')

The following value displays because the `et_prod` column is mapped to the `aw_product` dimension.

    aw_product

### 8.12 LNNVL

The LNNVL function provides a concise way to evaluate a condition when one or both operands of the condition may be null. LNNVL can be used anywhere a scalar expression can appear, even in contexts where the `IS [NOT] NULL`, `AND`, or `OR` conditions are not valid but would otherwise be required to account for potential nulls.

#### Return Values

`TRUE` if the condition is false or unknown and `FALSE` if the condition is true.

#### Syntax

LNNVL(condition)

#### Parameters

condition
An expression constructed using any scalar values. Note that you cannot specify an expression that contains AND, OR, or BETWEEN.

#### Examples

Example 8-12 Evaluating Expressions Using LNNVL

    SHOW LNNVL('apples' EQ 'oranges')
    yes

    SHOW LNNVL(7 LT 11)
    no

    SHOW LNNVL('vegetables' EQ NA)
    yes

### 8.13 LOCALTIMESTAMP

The LOCALTIMESTAMP function returns the current date and time in the session time zone as a value of data type `TIMESTAMP`.

When you want to retrieve the current date and time in the session time zone as a `TIMESTAMP_TZ` value, use the [CURRENT_TIMESTAMP](olap-dml-functions-a-k.md) function.

#### Return Values

`TIMESTAMP`

#### Syntax

LOCALTIMESTAMP \[ (timestamp-precision) \]

#### ARGUMENTS

timestamp-precision
Specifies the fractional second precision of the time value returned

#### Examples

Example 8-13 Retrieving the Local Timestamp

    SHOW LOCALTIMESTAMP
    13-FEB-07 12.11.33.454834 PM

### 8.14 LOG function

The LOG function computes the logarithm of an expression.

**Note:**

Do not confuse the LOG function with the function of the same name which creates a log file.

#### Return Value

DECIMAL

#### Syntax

LOG(\[base,\] expression)

#### Parameters

base
The base by which to compute the logarithm. When you do not specify a value, the function computes the natural logarithm of the expression by using e for the base where e equals `2.718281828459`.

expression
A numeric expression which is greater than zero. When the value is equal to or less than zero, LOG returns an `NA` value.

#### Examples

Example 8-14 Calculating a Natural Logarithm

In this example the LOG function is used to calculate the natural logarithm of the expression `4,000 +` `6,000`. The statements

    DECIMALS = 5
    SHOW LOG(4000 + 6000)

produce the following result.

    9.21034

### 8.15 LOG10

The LOG10 function computes the logarithm base `10` of an expression.

#### Return Value

DECIMAL

#### Syntax

LOG10(expression)

#### Parameters

expression
The value of expression must be greater than zero. When the value is equal to or less than `0` (zero), LOG10 returns an `NA` value.

#### Examples

Example 8-15 Calculating a Base 10 Logarithm

This example uses the LOG10 function to calculate the base 10 logarithm of 1,000. The statement

    SHOW LOG10(1000)

produces the following result.

    3.00

### 8.16 LOWCASE

The LOWCASE function converts all alphabetic characters in a text expression into lowercase.

#### Return Value

TEXT or NTEXT

When the expression is TEXT, the return value is TEXT. When the expression is NTEXT, the return value is NTEXT

#### Syntax

LOWCASE(text-expression)

#### Parameters

text-expression
The text expression whose characters are to be converted.

#### Examples

Example 8-16 Converting Part of an Expression to Lowercase

Suppose you get some new data to add to a mailing list. In the existing mailing list, people's names have only the first letter capitalized. In the new data, however, the whole name is capitalized. You can use LOWCASE to make the new data correspond to the current data with a statement similar to the following.

    lastname = JOINCHARS(EXTCHARS(lastname, 1, 1), -
               LOWCASE(EXTCHARS(lastname, 2, NUMCHARS(lastname))))

### 8.17 LOWER

The LOWER function converts all alphabetic characters in a text expression into lowercase.

#### Return Value

The data type of text-expression.

**See Also:**

The LOWER function in [Oracle Database SQL Language Reference](../sqlrf/LOWER.md)

#### Syntax

LOWER(text-expression)

#### Parameters

text-expression
The text expression whose characters are to be converted.

### 8.18 LPAD

The LPAD function returns an expression, left-padded to a specified length with the specified characters; or, when the expression to be padded is longer than the length specified after padding, only that portion of the expression that fits into the specified length.

To right-pad a text expression, use RPAD.

#### Return Value

TEXT or NTEXT based on the data type of the expression you want to pad (text-exp).

#### Syntax

LPAD (text-exp , length \[, pad-exp\])

#### Parameters

text-exp
A text expression to pad.

length
The total length of the return value as it is displayed on your screen. In most character sets, this is also the number of characters in the return value. However, in some multibyte character sets, the display length of a character string can differ from the number of characters in the string.

When you specify a value for length that is shorter than the length of text-exp, then this function returns only that portion of the expression that fits into the specified length.

pad-exp
A text expression that specifies the padding characters. The default value of pad-exp is a single blank.

#### Examples

Example 8-17 Left-Padding a String

The following example left-pads a string with the characters "\*" and ".".

    SHOW LPAD('Page 1',15,'*.')
    *.*.*.*.*Page 1

### 8.19 LTRIM

The LTRIM function removes characters from the left of a text expression, with all the leftmost characters that appear in another text expression removed. The function begins scanning the base text expression from its first character and removes all characters that appear in the trim expression until reaching a character that is not in the trim expression and then returns the result.

To trailing characters, use RTRIM. To trim both leading or trailing characters, use TRIM.

#### Return Value

TEXT or NTEXT based on the data type of the first argument.

#### Syntax

LTRIM (text-exp \[,  trim-exp\])

#### Parameters

text-exp
A text expression that you want trimmed.

trim-exp
A text expression that is the characters to trim. The default value of trim-exp is a single blank.

#### Examples

Example 8-18 Trimming Left-Most Characters

The following example trims all of the left-most x's and y's from a string.

    SHOW LTRIM('xyxxxyLast Word','xy')
    Last Word

### 8.20 MAKEDATE

The MAKEDATE function returns the DATE value that corresponds to specified `INTEGER` values for a year, month, and day.

#### Return Value

DATE or text

#### Syntax

MAKEDATE(year month day)

#### Parameters

year
An `INTEGER` expression that represents the year of the test date. For any year, you can specify the year as a four-digit number in the range 1000 to 9999. For years in the range 1950 to 2049 (the default) or some other range (as set through the YRABSTART option), you have the alternative of specifying a two-digit number that represents the last two digits of the year (96 represents 1996, for example).

month
Any `INTEGER` expression, normally in the range 1 to 12. When you specify an `INTEGER` less than 1 or greater than 12, MAKEDATE returns a date in a year before or after the year specified by the `INTEGER` expression for year.

For example, if the arguments to MAKEDATE are (`97` `14` `21`), MAKEDATE returns the date `February 21, 1998` because, in effect, February 1998 is the fourteenth month of 1997.

day
An `INTEGER` expression in the range 1 to 31.

#### Usage Notes

Format of the Result Returned by MAKEDATE

When you display the result returned by MAKEDATE, the date is formatted according to the date template in the DATEFORMAT option. When the day of the week or the name of the month is used in the date template, the day names specified in the DAYNAMES option and the month names specified in the MONTHNAMES option are used. You can use the result returned by MAKEDATE anywhere that a DATE value is expected.

Invalid Dates

When the arguments to MAKEDATE do not represent a valid date between January 1, 1000, and December 31, 9999, MAKEDATE returns an `NA` value.

#### Examples

Example 8-19 Converting Integers to a Date

The following statements specify the date format and send the output to the current outfile.

    DATEFORMAT = '<mtextl> <d>, <yyyy>'
    SHOW MAKEDATE(97 11 14)

These statements produce the following output.

    November 14, 1997

Example 8-20 Calculating a Date Using YYOR, MMOF, and DDOF Functions

The following statement calculates the date one year from today, and sends the output to the current outfile. The TODAY function returns today's date. The INTEGER functions YYOF, MMOF, and DDOF return the INTEGER values that correspond to the year, month, and day of today's date.

    SHOW MAKEDATE(YYOF(TODAY) + 1 MMOF(TODAY) DDOF(TODAY))

When today's date is January 15, 1995, this statement produces the following output.

    January 15, 1996

### 8.21 MAX

The MAX function calculates the larger value of two expressions.

#### Return Value

DECIMAL. The results of MAX are dimensioned by the union of the dimensions of the two expressions

#### Syntax

MAX(expression1, expression2)

#### Parameters

expression1
One expression to be compared.

expression2
The other expression to be compared.

#### Examples

Example 8-21 Calculating Whether Actual or Budget Values Are Larger

Suppose, for each of the first six months of 1996, you want to find whether the `actual` value or the `budget` value is larger for the line item Cost of Goods Sold (Cogs) in the `Sporting` division.

    LIMIT line TO 'Cogs'
    LIMIT division TO 'Sporting'
    LIMIT month TO 'Jan96' TO 'Jun96'
    REPORT DOWN month actual budget MAX(actual budget)

The preceding statements produce the following output.

    DIVISION: SPORTING
                   --------------LINE--------------
                   --------------COGS--------------
                                            MAX    
                                          (ACTUAL  
    MONTH            ACTUAL     BUDGET    BUDGET)  
    -------------- ---------- ---------- ----------
    Jan96          287,557.87 279,773.01 287,557.87
    Feb96          315,298.82 323,981.56 323,981.56
    Mar96          326,184.87 302,177.88 326,184.87
    Apr96          394,544.27 386,100.82 394,544.27
    May96          449,862.25 433,997.89 449,862.25
    Jun96          457,347.55 448,042.45 457,347.55

### 8.22 MAXBYTES

The MAXBYTES function counts the number of bytes in the longest line of a multiline text expression. The result returned by MAXBYTES has the same dimensions as the specified expression.

#### Return Value

INTEGER

#### Syntax

MAXBYTES(text-expression)

#### Parameters

text-expression
The `TEXT` expression whose bytes for each line are to be counted.

#### Examples

Example 8-22 Finding the Length of the Longest Line Using Bytes

You would like to know the length of the longest line in a text variable called `mytext`. The following example shows the value of the variable and the result returned by MAXBYTES.

The statement

    SHOW mytext

produces the following output.

    This is a multiline text variable. 
    The longest line is this one in the middle.
    The third line is short.

The statement

    SHOW MAXBYTES(mytext)

produces the following output.

    43

### 8.23 MAXCHARS

The MAXCHARS function counts the number of characters in the longest line of a multiline text expression. The result returned by MAXCHARS has the same dimensions as the specified expression.

**Tip:**

When you are using a multibyte character set, you can use the MAXBYTES function instead of the MAXCHARS function.

#### Return Value

INTEGER

#### Syntax

MAXCHARS(text-expression)

#### Parameters

text-expression
The text expression whose characters for each line are to be counted. MAXCHARS accepts either a TEXT or NTEXT argument. It does not perform an automatic conversion to either data type. It returns the information that is correct for the data type of the specified argument.

#### Examples

Example 8-23 Finding the Length of the Longest Line Using Characters

You would like to know the length of the longest line in a text variable called `mytext`. The following example shows the value of the variable and the result returned by MAXCHARS.

The statement

    SHOW mytext

produces the following output.

    This is a multiline text variable. 
    The longest line is this one in the middle.
    The third line is short.

The statement

    SHOW MAXCHARS(mytext)

produces the following output.

    43

### 8.24 MEDIAN

The MEDIAN function calculates the median of the values of an expression. The median is the middle number in a given sequence of numbers.

#### Return Value

DECIMAL

#### Syntax

MEDIAN(expression \[CACHE\] \[dimension...\])

#### Parameters

expression
The expression whose median value is to be calculated.

CACHE
Specifies slightly different internal behavior. Specify this keyword only when the original performance is extremely slow.

dimension
The name of a dimension of the result; or, the name of a relation between one dimension of expression and another dimension that you want as a dimension of the result.

By default, MEDIAN returns a single value. When you indicate one or more dimensions for the result, MEDIAN calculates values along the dimensions that are specified and returns an array of values. Each dimension must be either a dimension of expression or related to one of its dimensions.

**Tip:**

When you specify a dimension that is not an actual dimension of expression, but, instead, is dimension that is related to a dimension of expression and when there are multiple relations between the two dimensions, Oracle OLAP uses the default relation between the dimensions to perform the calculation. (See the [RELATION command](olap-dml-commands-h-z.md) for more information on default relations.) When you do not want Oracle OLAP to use this default relation, specify the related dimension by specifying the name of a specify relation.

#### Usage Notes

NA Values and MEDIAN

MEDIAN is affected by the NASKIP option in the same manner as other aggregate functions. When NASKIP is set to `YES` (the default), MEDIAN ignores `NA` values and returns the median of the values that are not `NA`. When NASKIP is set to `NO`, MEDIAN returns `NA` when any value of the expression is `NA`. When all the values of the expression are `NA`, MEDIAN returns `NA` for either setting of NASKIP.

#### Examples

Example 8-24 Calculating Median Monthly Sales

This example shows how to calculate the median monthly sales of sportswear for each sales district.

    LIMIT product TO 'Sportswear'
    REPORT W 12 HEADING 'Median Sales' MEDIAN(sales district)

The preceding statements produce the following output.

    DISTRICT          Median Sales
    ----------------- ------------
    Boston               67,923.05
    Atlanta             152,186.52
    Chicago              94,372.06
    Dallas              160,854.60
    Denver               86,745.40
    Seattle              53,950.28

### 8.25 MIN

The MIN function calculates the smaller value of two expressions.

#### Return Value

DECIMAL. The results of MIN are dimensioned by the union of the dimensions of the two expressions.

#### Syntax

MIN(expression1, expression2)

#### Parameters

expression1
One expression to be compared.

expression2
The other expression to be compared.

#### Examples

Example 8-25 Calculating Whether Actual or Budget Values Are Smaller

Suppose, for each of the first six months of 1996, you want to find whether the `actual` value or the `budget` value is smaller for the line item Cost of Goods Sold (`Cogs`) in the `Sporting` division.

    LIMIT line TO 'Cogs'
    LIMIT division TO 'Sporting'
    LIMIT month TO 'Jan96' TO 'Jun96'
    REPORT DOWN month actual budget MIN(actual budget)

The preceding statements produce the following output.

    DIVISION: SPORTING
                   --------------LINE--------------
                   --------------COGS--------------
                                            MIN    
                                          (ACTUAL  
    MONTH            ACTUAL     BUDGET    BUDGET)  
    -------------- ---------- ---------- ----------
    Jan96          287,557.87 279,773.01 279,773.01
    Feb96          315,298.82 323,981.56 315,298.82
    Mar96          326,184.87 302,177.88 302,177.88
    Apr96          394,544.27 386,100.82 386,100.82
    May96          449,862.25 433,997.89 433,997.89
    Jun96          457,347.55 448,042.45 448,042.45

### 8.26 MMOF

The MMOF function returns an `INTEGER` in the range of 1 to 12, giving the month in which a specified date falls. The result returned by MMOF has the same dimensions as the specified DATE expression.

#### Return Value

INTEGER

#### Syntax

MMOF(date-expression)

#### Parameters

date-expression
An expression that has the DATE data type, or a text expression that specifies a date. The values of the text expression are converted automatically to DATE values, using the current setting of the DATEORDER option to resolve any ambiguity.

#### Examples

Example 8-26 Finding the Current Month

The following statement determines the month in which today's date falls.

    SHOW MMOF(TODAY)

When today's date is January 15, 1996, this statement produces the following output.

    1

### 8.27 MODE

The MODE function returns the mode (the most frequently occurring value) of a numeric expression. When there are no duplicate values in the data, then MODE returns `NA`.

#### Return Value

DECIMAL

#### Syntax

MODE(expression \[CACHE} \[dimensions\])

#### Parameters

expression
The numeric expression whose mode is to be calculated.

CACHE
Specifies slightly different internal behavior. Specify this keyword only when the original performance is extremely slow.

dimensions
The dimensions of the result. When you do not specify any dimensions, MODE calculates the mode over all the dimensions of expression and it returns a single value. When you specify one or more dimensions (but fewer than all of the dimensions of expression) in the dimension argument, then MODE calculates the mode for each value of the dimensions that you specified and returns an array of values. Each dimension must be a dimension of expression.

#### Usage Notes

The Effect of NASKIP on MODE

MODE is not affected by the NASKIP option.

More Than One Set of Duplicate Values

When multiple values qualify as having the greatest number of occurrences in the expression, then MODE sorts the values and returns the lowest one. For example, for the data series {4,5,2,3,7,4,6,2,1}, the mode for the series is 2 even though 2 and 4 both occur twice.

#### Examples

Example 8-27 Reporting the Mode

These examples use the following `geography` and `items` dimensions and `sales2` variable.

    DEFINE geography DIMENSION TEXT 
    MAINTAIN geography ADD 'g1' 'g2' 'g3'
    DEFINE items DIMENSION TEXT
    MAINTAIN items ADD 'Item1' 'Item2' 'Item3' 'Item4' 'Item5'
    DEFINE sales2 DECIMAL <geography items>

Assume the `sales2` variable has the following data values.

                   -------------SALES2-------------
                   -----------GEOGRAPHY------------
    ITEMS              G1         G2         G3
    -------------- ---------- ---------- ----------
    Item1               30.00      15.00      12.00
    Item2               10.00      20.00      18.00
    Item3               15.00      20.00      24.00
    Item4               30.00      25.00      25.00
    Item5                  NA       7.00      21.00

- This statement reports the mode that is calculated over the `geography` dimension.

      REPORT W 22 MODE(sales2, geography)

  The preceding statement produces the following output.

                          MODE(SALES2,
      GEOGRAPHY            GEOGRAPHY)
      -------------- ----------------------
      g1                              30.00
      g2                              20.00
      g3                                 NA

- This statement reports the mode that is calculated over the `items` dimension.

      REPORT W 18 MODE(sales2, items)

  The preceding statement produces the following output.

                        MODE(SALES2,
      ITEMS                ITEMS)
      -------------- ------------------
      Item1                          NA
      Item2                          NA
      Item3                          NA
      Item4                       25.00
      ITEM5                          NA

- This statement reports the mode that is calculated over all of the dimensions of the `sales2` variable.

      REPORT MODE(sales2)

  The preceding statement produces the following output.

      Mode
      ----
      15

### 8.28 MODULO

The MODULO function, like the SQL `MOD` function, returns the remainder after a number is divided by another; or the number if the divisor is 0 (zero).

#### Return Values

Numeric.

Oracle determines the argument with the highest numeric precedence, implicitly converts the remaining arguments to that data type, and returns that data type

#### Syntax

MOD(dividend, divisor)

#### Parameters

dividend
A numeric expression (or an expression that Oracle OLAP can implicitly convert to a numeric expression) that is the number you want to divide.

divisor
A numeric expression (or an expression that Oracle OLAP can implicitly convert to a numeric expression) that is the divisor.

#### Examples

Example 8-28 Using MODULO to Find the Remainder After Division

    SHOW MODULO(13,7)
    6.00

### 8.29 MONTHS_BETWEEN

The MONTHS_BETWEEN function calculates the number of months between two dates. When the two dates have the same day component or are both the last day of the month, then the return value is a whole number. Otherwise, the return value includes a fraction that considers the difference in the days based on a 31-day month. The return value is positive when the first date is later than the second date, and negative when the first date is earlier than the second date.

#### Return Value

NUMBER

#### Syntax

MONTHS_BETWEEN(datetime_expression1, datetime_expression2)

#### Parameters

datetime-expression1
One expression that has the `DATETIME` data type, or a text expression that specifies a date.

datetime-expression2
A second expression that has the `DATETIME` data type, or a text expression that specifies a date.

#### Examples

Example 8-29 Calculating the Number of Months Between Dates

The following statement calculates the number of months between March 26, 2004, and July 6, 2001.

    SHOW months_between('06Jul2005' '17Jul2003')
    23.65

Example 8-30 Last Days

The return value is a whole number when both dates are the last day of the month.

    SHOW months_between('29Feb2000', '30Sep2000')
    -7.00

### 8.30 MOVINGAVERAGE

The MOVINGAVERAGE function (abbreviated MVAVG) computes a series of averages for the values of a dimensioned variable or expression over a specified dimension. For each dimension value in status, MOVINGAVERAGE computes the average of the data in the range specified, relative to the current dimension value.

When the data being averaged has only one dimension, MOVINGAVERAGE produces a single series of averages, one for each dimension value in status. When the data has dimensions other than the one being averaged over, MOVINGAVERAGE produces a separate series of averages for each combination of values in the status list of the other dimensions.

#### Return Value

DECIMAL when the data type of expression is DECIMAL or SHORT; otherwise, NUMBER.

#### Syntax

MOVINGAVERAGE(expression, start, stop, step, -

     \[dimension \[STATUS\|limit-clause\]\])

#### Parameters

expression
A numeric variable or calculation whose values you want to average; for example, `units` or `sales-expense`.

start
stop
Integer values that specify the range of values over which you want to average. The value of start specifies the beginning of the range. The value of stop specifies the end of the range. Specify the values of start and stop relative to the current value of dimension. To specify a negative position for start or stop precede the value with a comma. Thus, you specify zero (`0`) for the current dimension value, and `-1` for the value preceding the current value. (See also "How the Moving Functions Handle Out-of-Range and NA Values".)

**Note:**

By default this function uses the default status list when identifying the range of values to average. You can specify either the STATUS or limit-clause phrase to change this behavior.

**Tip:**

When you want to range to the end of status, for convenience and to document your intent, specify the value of stop as OBJ function with the DIMMAX keyword

step
A positive whole number that specifies whether to average over every value in the range, every other value, every third value, and so on. A value of `1` for step means average over every value. A value of `2` means average over the first value, the third value, the fifth value, and so on. For example, when the current month is `Jun96` and the start and stop values are `-3` and `3`, a step value of `2` means average over `Mar96`, `May96`, `Jul96`, and `Sep96`.

dimension
The dimension over which the moving average is calculated. The data type of dimension can be of any type, but typically, is a time dimension.

When expression has a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR and you want the function to use that dimension, you can omit the dimension argument.

STATUS
Specifies that MOVINGAVERAGE should use the current status list (that is, only the dimension values currently in status in their current status order) when calculating the moving average.

limit-clause
Specifies that MOVINGAVERAGE uses the values specified by a LIMIT function or those specified with the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

#### Usage Notes

How the Moving Functions Handle Out-of-Range and NA Values

As a moving function loops through the values, at each step in the loop, if the in-loop dimension position is `NA` or out of range, then the function considers expression as an `NA` value. The function treats these `NA` values in the manner specified by the setting of the [NASKIP](olap-dml-options.md) option (by default, as `NA`) so, typically, the function ignores out-of-range (`NA`) values and does not evaluate the expression for that step in the loop.

#### Examples

Example 8-31 Calculating a Moving Average

Suppose you have a variable called `sales` that is dimensioned by a hierarchical dimension named `time`, a dimension named `product`, a dimension named `timelevelnames` that contains the names of the levels of `time` (for example, `Quarter` and `Year`), and a relation named `time.levelrels` that relates the values of `time` to the values of `timelevelnames`. Assume also that using the following statements you limit `product` to `Womens - Trousers` and time to quarters from `Q4-1999` to present.

    LIMIT product TO 'Womens - Trousers'
    LIMIT timelevelnames TO 'Quarter'
    LIMIT time TO time.levelrels
    LIMIT time REMOVE 'Q1-1999' 'Q2-1999' 'Q3-1999'

After you have limited `product` and `sales`, you issue the following report statement.

    REPORT DOWN time sales -
    HEADING 'Running Yearly\nTotal' MOVINGTOTAL(sales, -4, 0, 1, time, -
         LEVELREL time.levelrels) -
    HEADING 'Minimum\nQuarter' MOVINGMIN(sales, -4, 0, 1, time, -
         LEVELREL time.levelrels) -
    HEADING 'Maximum\nQuarter' MOVINGMAX(sales, -4, 0, 1, time, -
         LEVELREL time.levelrels) -
    HEADING 'Average\nQuarter' MOVINGAVERAGE(sales, -4, 0, 1, time, -
         LEVELREL time.levelrels)

The following report was created by the preceding statement.

                   -----------------------PRODUCT------------------------
                   ------------------Womens - Trousers-------------------
                              Running
                              Yearly     Minimum    Maximum    Average
    TIME           SALES      Total      Quarter    Quarter    Quarter
    -------------- ---------- ---------- ---------- ---------- ----------
    Q4-1999         416            1,386        233        480     346.50
    Q1-2000         465            1,851        233        480     370.20
    Q2-2000         351            1,969        257        480     393.80
    Q3-2000         403            2,115        351        480     423.00
    Q4-2000         281            1,916        281        465     383.20
    Q1-2001         419            1,919        281        465     383.80
    Q2-2001         349            1,803        281        419     360.60
    Q3-2001         467            1,919        281        467     383.80
    Q4-2001         484            2,000        281        484     400.00
    Q1-2002         362            2,081        349        484     416.20
    Q2-2002         237            1,899        237        484     379.80
    Q3-2002         497            2,047        237        497     409.40
    Q4-2002         390            1,970        237        497     394.00

### 8.31 MOVINGMAX

The MOVINGMAX function (abbreviated MVMAX) returns a series of maximum values of a dimensioned variable or expression over a specified dimension. For each dimension value in status, MOVINGMAX searches the data for the maximum value in the range specified, relative to the current dimension value.

When the variable or expression has only the specified dimension, MOVINGMAX produces a single series of maximum values, one for each dimension value in the status. When the variable or expression has dimensions other than the one specified, MOVINGMAX produces a separate series of maximum values for each combination of values in the status list of the other dimensions

#### Return Value

DECIMAL when the data type of expression is DECIMAL or SHORT; otherwise, NUMBER.

#### Syntax

MOVINGMAX(expression, start, stop, step, \[dimension \[STATUS\|limit-clause\]\])

#### Parameters

expression
A numeric variable or calculation from whose values you want to find the maximum values; for example, `units` or `sales-expense`.

start
stop
Integer values that specify the range of values over which you want to find the maximum values. The value of start specifies the beginning of the range. The value of stop specifies the end of the range. Specify the values of start and stop relative to the current value of dimension. To specify a negative position for start or stop precede the value with a comma. Thus, you specify zero (`0`) for the current dimension value, and `-1` for the value preceding the current value. (See also "How the Moving Functions Handle Out-of-Range and NA Values".)

**Note:**

By default this function uses the default status list when identifying the range of values to average. You can specify either the STATUS or limit-clause phrase to change this behavior.

**Tip:**

When you want to range to the end of status, for convenience and to document your intent, specify the value of stop as OBJ function with the DIMMAX keyword

step
A positive whole number that specifies whether to search every value in the range, every other value, every third value, and so on. A value of `1` for step means search every value. A value of `2` means check the first value, the third value, the fifth value, and so on. For example, when the current month is` Jun96` and the start and stop values are `-3` and `3`, a step value of `2` means search the months `Mar96`, `May96`, `Jul96`, and `Sep96` and return the maximum value that occurs in one of those four months.

dimension
The dimension over which the moving maximum is calculated. While this can be any dimension, it is typically a hierarchical time dimension of type TEXT that is limited to a single level (for example, the month or year level) or a dimension with a type of DAY, WEEK, MONTH, Quarter, or YEAR.

When expression has a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR and you want MOVINGMAX to use that dimension, you can omit the dimension argument.

STATUS
Specifies that MOVINGMAX uses the values specified by a LIMIT function or those specified with the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

#### Examples

For an example of calculating maximum sales, see Example 8-31.

### 8.32 MOVINGMIN

The MOVINGMIN function (abbreviated MVMIN) returns a series of minimum values for the values of a dimensioned variable or expression over a specified dimension. For each dimension value in status, MOVINGMIN searches the data for the minimum value in the range specified, relative to the current dimension value.

When the variable or expression has only the specified dimension, MOVINGMIN produces a single series of minimum values, one for each dimension value in the status. When the variable or expression has dimensions other than the one specified, MOVINGMIN produces a separate series of minimum values for each combination of values in the status list of the other dimensions.

#### Return Value

DECIMAL when the data type of expression is DECIMAL or SHORT; otherwise, NUMBER.

#### Syntax

MOVINGMIN(expression, start, stop, step, \[dimension \[STATUS\|limit-clause\]\])

#### Parameters

expression
A numeric variable or calculation from whose values you want to find the minimum values; for example, UNITS or SALES-EXPENSE.

start
stop
Integer values that specify the range of values over which you want to find minimum values. The value of start specifies the beginning of the range. The value of stop specifies the end of the range. Specify the values of start and stop relative to the current value of dimension. To specify a negative position for start or stop precede the value with a comma. Thus, you specify zero (`0`) for the current dimension value, and `-1` for the value preceding the current value. (See also "How the Moving Functions Handle Out-of-Range and NA Values".)

**Note:**

By default this function uses the default status list when identifying the range of values to average. You can specify either the STATUS or limit-clause phrase to change this behavior.

**Tip:**

When you want to range to the end of status, for convenience and to document your intent, specify the value of stop as OBJ function with the DIMMAX keyword

step
A positive whole number that specifies whether to search every value in the range, or every other value, or every third value, and so on. A value of `1` for step means search every value. A value of `2` means check the first value, the third value, the fifth value, and so on. For example, when the current month is `Jun96` and the start and stop values are `-3` and `3`, a step value of `2` means search the months `Mar96`, `May96`, `Jul96` and `Sep96` and return the minimum value that occurs in one of those four months.

dimension
The dimension over which the moving minimum is calculated. While this can be any dimension, it is typically a hierarchical time dimension of type TEXT that is limited to a single level (for example, the month or year level) or a dimension with a type of DAY, WEEK, MONTH, Quarter, or YEAR.

When expression has a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR and you want MOVINGMIN to use that dimension, you can omit the dimension argument.

STATUS
Specifies that MOVINGMIN should use the current status list (that is, only the dimension values currently in status in their current status order) when calculating the moving minimum.

limit-clause
Specifies that MOVINGMIN uses the values specified by a LIMIT function or those specified with the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

#### Examples

For an example of calculating minimum sales, see Example 8-31.

### 8.33 MOVINGTOTAL

The MOVINGTOTAL function (abbreviated MVTOT) computes a series of totals for the values of a dimensioned variable or expression over a specified dimension. For each dimension value in status, MOVINGTOTAL computes the total of the data in the range specified, relative to the current dimension value.

When the variable or expression has only the specified dimension, MOVINGTOTAL produces a single series of totals, one for each dimension value in the status. When the variable or expression has dimensions other than the one specified, MOVINGTOTAL produces a separate series of totals for each combination of values in the status list of the other dimensions.

#### Return Value

DECIMAL when the data type of expression is DECIMAL or SHORT; otherwise, NUMBER.

#### Syntax

MOVINGTOTAL(expression, start, stop, step, \[dimension \[STATUS\|limit-clause\]\])

#### Parameters

expression
A numeric variable or calculation whose values you want to total; for example, UNITS or SALES-EXPENSE.

start
stop
Integer values that specify the range of values over which you want to total. The value of start specifies the beginning of the range. The value of stop specifies the end of the range. Specify the values of start and stop relative to the current value of dimension. To specify a negative position for start or stop precede the value with a comma. Thus, you specify zero (`0`) for the current dimension value, and `-1` for the value preceding the current value. (See also "How the Moving Functions Handle Out-of-Range and NA ValuesHow the Moving Functions Handle Out-of-Range and NA Values".)

**Note:**

By default this function uses the default status list when identifying the range of values to average. You can specify either the STATUS or limit-clause phrase to change this behavior.

**Tip:**

When you want to range to the end of status, for convenience and to document your intent, specify the value of stop as OBJ function with the DIMMAX keyword

step
A positive whole number that specifies whether to total over every value in the range, every other value, every third value, and so on. A value of `1` for step means total over every value. A value of `2` means total over the first value, the third value, the fifth value, and so on. When the current month is `Jun96` and the start and stop values are `-3` and `3`, a step value of `2` means total over `Mar96`, `May96`, `Jul96`, and `Sep96`.

dimension
The dimension over which the moving total is calculated. While this can be any dimension, it is typically a time dimension.

When expression has a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR and you want MOVINGTOTAL to use that dimension, you can omit the dimension argument.

STATUS
Specifies that MOVINGTOTAL should use the current status list (that is, only the dimension values currently in status in their current status order) when calculating the moving total.

limit-clause
Specifies that MOVINGTOTAL uses the values specified by a LIMIT function or those specified with the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

#### Examples

For an example of calculating a moving total sales, see Example 8-31.

### 8.34 NA2

Used for debugging and testing variables defined with null tracking, the NA2 function returns an NA value that takes the NA2 bit into consideration.

**See Also:**

"[NA2 Bits and Null Tracking](olap-dml-commands-a-g.md)"

#### Return Value

An NA value with the NA flag set to TRUE.

#### Syntax

NA2

#### Examples

See [Example 9-104](olap-dml-commands-a-g.md).

### 8.35 NAFILL

The NAFILL function returns the values of the source expression with any `NA` values replaced with the specified fill expression.

#### Return Value

The value returned is the same data type as source-expression. When the fill and source expressions do not have the same data type, Oracle OLAP converts the fill expression to the data type of the source expression when possible. Otherwise, an error is produced. When both the source and fill expressions equal `NA`, then NAFILL returns `NA`.

#### Syntax

NAFILL(source-expression fill-expression)

#### Parameters

source-expression
The expression being evaluated. For values of source-expression that do not equal `NA`, NAFILL returns the corresponding values of source-expression. Source-expression determines the dimensions and data type of the result.

fill-expression
The expression to be substituted in the return value. Fill-expression must have the same data type as source-expression. Fill-expression is only evaluated for values of source-expression that equal `NA`.

#### Usage Notes

Functions in the Fill Expression

You can use any functions in the fill expression if they return the same data type as the source expression.

NATRIGGER Takes Precedence Over NAFILL

Oracle OLAP evaluates an \$NATRIGGER property expression before applying the NAFILL function. When the \$NATRIGGER expression is `NA`, then the NAFILL function has an effect.

#### Examples

Example 8-32 Filling NA Values with Zeros

Suppose you have `NA` values in the variable `sales` and you want to calculate an average that counts those values as zeros. Ordinarily, AVERAGE ignores `NA` values and does not count them in the number of values being averaged. You can use NAFILL inside the AVERAGE function to temporarily treat those values as zeros so the NA values count in calculating the average.

    REPORT AVERAGE(NAFILL(sales 0.0))

### 8.36 NAFLAG

Used for debugging and testing variables defined with null tracking, the function identifies if a value is a NA2 value or a non-NA value.

**See Also:**

"[NA2 Bits and Null Tracking](olap-dml-commands-a-g.md)"

#### Return Values

INTEGER

`0` for a non-NA value, `2` if the NA value is an NA2 value, or `1` for all other NA values

#### Syntax

NAFLAG (expression)

#### Parameters

expression
An OLAP DML expression.

#### Examples

See [Example 9-104](olap-dml-commands-a-g.md).

### 8.37 NEW_TIME

The NEW_TIME function converts a date and time from one time zone to another.

#### Return Value

DATETIME

#### Syntax

NEW_TIME(datetime-exp this_zone new_zone)

#### Parameters

this_zone
A text expression that indicates the time zone from which you want to convert datetime-exp. It must be a valid time zone, as listed in the following table.

new_zone
A text expression that indicates the time zone into which you want to convert datetime-exp. It is the time zone of the return value. It must be a valid time zone, as listed in the following table.

Table 8-1 Time Zones

| AST | Atlantic Standard Time      |
|:----|:----------------------------|
| ADT | Atlantic Daylight Time      |
| BST | Bering Standard Time        |
| BDT | Bering Daylight Time        |
| CST | Central Standard Time       |
| CDT | Central Daylight Time       |
| EST | Eastern Standard Time       |
| EDT | Eastern Daylight Time       |
| GMT | Greenwich Mean Time         |
| HST | Alaska-Hawaii Standard Time |
| HDT | Alaska-Hawaii Daylight Time |
| MST | Mountain Standard Time      |
| MDT | Mountain Daylight Time      |
| NST | Newfoundland Standard Time  |
| PST | Pacific Standard Time       |
| PDT | Pacific Daylight Time       |
| YST | Yukon Standard Time         |
| YDT | Yukon Daylight Time         |

#### Examples

Example 8-33 Using the Current Time of day

The SYSDATE function returns the current date and time to the NEW_TIME function.

    SHOW new_time(SYSDATE 'EST' 'PST')

When the date and time in Eastern Standard Time are October 20, 2000, at 1:20 A.M., then the date in Pacific Standard Time, which is three hours earlier, is October 19, 2000. Because SYSDATE uses the format specified by NLS_DATE_FORMAT, which by default only shows the date, the time is not displayed.

    19-OCT-00

Example 8-34 Specifying the Time of day

In the following example, the TO_DATE function converts a text string to a valid date and time. The TO_CHAR function includes a date format that temporarily overrides the date format specified by the NLS_DATE_FORMAT option.

    SHOW TO_CHAR(NEW_TIME(TO_DATE('11-27-00 22:15:00', 'MM-DD-YY HH24:MI:SS'), -
       'HST' 'PST') 'MM-DD-YY HH24:MI:SS')

This statement converts November 27 at 10:15 P.M. (22:15:00) Alaska-Hawaii Standard Time to November 28 at 12:15 A.M. (00:15:00) Pacific Standard Time. The date format specified in the TO_CHAR function allows the time to be displayed along with the date.

    11-28-00 00:15:00

Alternatively, you can change the value of NLS_DATE_FORMAT.

    NLS_DATE_FORMAT = 'MM-DD-YY HH24:MI:SS'

Then this statement produces the same result, without requiring the use of TO_CHAR.

    SHOW NEW_TIME(TO_DATE('11-27-00 22:15:00', 'MM-DD-YY HH24:MI:SS'), -
       'HST' 'PST')

### 8.38 NEXT_DAY

The NEXT_DAY function returns the date of the first instance of a particular day of the week that follows the specified date.

#### Return Value

DATETIME

#### Syntax

NEXT_DAY(datetime-expression, weekday)

#### Parameters

datetime-expression
An expression that has the DATETIME data type.

weekday
A text expression that identifies a day of the week (for example, Monday). Valid names are controlled by the NLS_DATE_LANGUAGE option.

#### Examples

Example 8-35 Getting a Future Date

The following statement returns the date of the first Tuesday following today's date.

    SHOW NEXT_DAY(SYSDATE, 'Tues')

When today is Friday, September 8, 2000, then the following Tuesday is

    11-SEP-00

### 8.39 NLS_CHARSET_ID

The NLS_CHARSET_ID function returns the character set identification number corresponding to a specified character set name.

**See Also:**

NLS_CHARSET_NAME

#### Return Value

INTEGER when you specify a valid value for the name of the character set, a number; otherwise NA.

#### Syntax

NLS_CHARSET_ID (charset_name)

#### Parameters

charset_name
A VARCHAR2 text expression that is a valid character set name or one of the following values:

- CHAR_CS which specifies that the function return the database character set identification number of the server.

- NCHAR_CS which specifies that the function return the national character set id number of the server.

**See Also:**

[Choosing a Character Set](../nlspg/choosing-character-set.md) in Oracle Database Globalization Support Guide for a list of character set identifiers.

### 8.40 NLS_CHARSET_NAME

The NLS_CHARSET_NAME function returns the name of the character set corresponding to a specified character set identification number.

**See Also:**

[Choosing a Character Set](../nlspg/choosing-character-set.md) in Oracle Database Globalization Support Guide for a list of character set names.

#### Return Value

When the number is recognized as a valid character, VARCHAR2; otherwise, NA.

#### Syntax

NSL_CHARSET_NAME (number-exp)

#### Parameters

number-exp
A number that is the character set ID.

**See Also:**

[Choosing a Character Set](../nlspg/choosing-character-set.md) in Oracle Database Globalization Support Guide for a list of character set identifiers

### 8.41 NLSSORT

The NLSSORT function returns a string of bytes used to sort a text string. You can use this function to specify sorting and comparison operations based on a linguistic sort sequence rather than on the binary value of a string.

**See Also:**

[Linguistic Sorting and Matching](../nlspg/linguistic-sorting-and-matching.md) in Oracle Database Globalization Support Guide

#### Return Value

RAW

#### Syntax

NLSSORT(char \[, 'NLS_SORT = sort\[\_ai \|\_ci\]' \])

#### Parameters

char
A text expression.

sort
An NLS language.

\_ai
Specifies an accent-insensitive sort.

\_ci
Specifies a case-insensitive sort.

#### Examples

Example 8-36 Determining the Bytes by Which Values Are Sorted Based on Linguistic Sort Sequence

Assume you want to know the bytes by which a single value is sorted in the German language without regard to case. To do this you can execute the following SHOW command.

    show  NLSSORT('Mary Ann' , 'NLS_SORT = German_ai' )
    501464820114555500010101010201010100

To see this same data for all of the values in a text dimension named `myname` are sorted, you can execute the following statement.

    REPORT NLSSORT(MYname , 'NLS_SORT = German_ci' )

    MYNAME           NLSSORT(MYNAME , 'NLS_SORT = German_ci')
    ---------------- ----------------------------------------
    Adelaid          1423284B143C23000101010101010100
    Maryann          50146482145555000101010101010100
    Mary Ann         501464820114555500010101010201010100
    Donna            235A55551400010101010100

### 8.42 NONE

The NONE function returns `YES` when none of the values of a Boolean expression are `TRUE`. It returns `NO` when any value of the expression is `TRUE`.

#### Return Value

BOOLEAN or `NA` if all the values of the expression are `NA`

#### Syntax

NONE(boolean-expression \[CACHE\] \[dimension...\])

#### Parameters

boolean-expression
The Boolean expression to be evaluated.

CACHE
Specifies slightly different internal behavior. Specify this keyword only when the original performance is extremely slow.

dimension
The name of a dimension of the result; or, the name of a relation between one dimension of boolean-expression and another dimension that you want as a dimension of the result.

By default, NONE returns a single `YES` or `NO` value. When you indicate one or more dimensions for the result, NONE tests for `TRUE` values along the dimensions that are specified and returns an array of values. Each dimension must be either a dimension of boolean-expression or related to one of its dimensions.

**Tip:**

When you specify a dimension that is not an actual dimension of boolean-expression, but, instead, is dimension that is related to a dimension of boolean-expression and when there are multiple relations between the two dimensions, Oracle OLAP uses the default relation between the dimensions to perform the calculation. (See the [RELATION command](olap-dml-commands-h-z.md) for more information on default relations.) When you do not want Oracle OLAP to use this default relation, specify the related dimension by specifying the name of a specify relation.

#### Usage Notes

The Effect of NASKIP on NONE

NONE is affected by the NASKIP option. When NASKIP is set to `YES` (the default), and all of the values in the expression are `NA` NONE returns `NA`; if even one value is not `NA`, NONE ignores all of the `NA` values in the expression. When NASKIP is set to `NO`, NONE returns `NA` when any value of the expression is `NA`.

#### Examples

Example 8-37 Testing for No True Values by District

Suppose you want to find out which districts had no months in which sales fell below \$50,000. Use the NONE function to determine whether the Boolean expression (`SALES` `LT` `50000`) is `TRUE` for no months. To have the results dimensioned by district, specify `district` as the second argument to NONE.

    LIMIT product TO 'Sportswear'
    REPORT NONE(sales LT 50000, district)

The preceding statements produce the following output.

                   NONE(SALES
                   LT 50000,
    DISTRICT       DISTRICT)
    -------------- ----------
    Boston                 NO
    Atlanta               YES
    Chicago               YES
    Dallas                YES
    Denver                YES
    Seattle                NO

Example 8-38 Testing for No True Values by Region

You might also want to find out which regions had no months in which no districts had sportswear sales of less than \$50,000. Because the `region` dimension is related to the `district` dimension, you can specify `region` instead of `district` as a dimension for the results of ANY.

    REPORT NONE(sales LT 50000, region)

The preceding statement produces the following output.

                   NONE(SALES
                   LT 50000,
    REGION          REGION)
    -------------- ----------
    East                   NO
    Central               YES
    West                   NO

### 8.43 NORMAL

The NORMAL function returns a random value from a normal distribution with a specified mean and standard deviation. The result returned by NORMAL is dimensioned by all the dimensions of the mean and standard deviation expressions.

#### Return Value

DECIMAL

#### Syntax

NORMAL(mean standard-deviation)

#### Parameters

mean
A numeric expression that represents the mean of a normal distribution. When mean is `NA`, NORMAL returns `NA`.

standard-deviation
A numeric expression that represents the standard deviation of a normal distribution. When standard-deviation is `NA`, NORMAL returns the mean.

#### Examples

Example 8-39 Showing Random Values

Each of the following examples shows a random number that might be returned from a normal distribution with a mean of 0 and a standard deviation of 1.

The first time you execute the following statement,

    SHOW NORMAL(0 1)

it might produce the following result.

    -0.75

However, when you execute the same statement again, it might produce the following result.

    0.87

### 8.44 NPV

The NPV function computes the net present value of a series of cash flow values.

#### Return Value

DECIMAL

The result returned by the NPV function is dimensioned by all the dimensions of cashflows except its time dimension. When cashflows is dimensioned only by the time dimension, NPV returns a single value.

#### Syntax

NPV(cashflows, discount-rate, \[time-dimension\])

#### Parameters

cashflows
A numeric expression that is dimensioned by time-dimension and specifies the series of cash flow values.

**Note:**

All cash flows are assumed to occur at the beginning of the time period with which they are associated. The cash flows are discounted back to the beginning of the earliest time period that appears in the current status of the time dimension. NPV ignores cash flows that corresponds to out-of-status dimension positions.

discount-rate
A numeric expression that specifies the interest rate for each period to be used to discount the cash flow values. It can either be a single value or an array of values with one or more non-time dimensions. Express the discount rate as a decimal quantity; for example, 8.25 percent as `.0825`.

NPV accepts any positive discount rate, and it also accepts a negative discount rate when the rate is greater than minus one (that is, rate `>` `-1`). When you supply a negative rate, you must precede it with a comma.

time-dimension
A name that specifies the time dimension. When cashflows has a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, NPV automatically uses that dimension, and you can omit the time-dimension argument.

#### Usage Notes

NA Discount Rate

When the discount rate used to compute a result value equals `NA`, then that result value is `NA`.

Cash Flow Timing

Different assumptions about the intra-period timing of the cash flows, or the base time point for the present value calculations, can be accommodated by multiplying the result of the NPV function by the following quantity: one plus the discount rate, raised to an appropriate positive or negative power.

#### Examples

Example 8-40 Computing the Net Present Value

The following statements create a dimension called `project`, add values to it, and create a variable called `cflow`, which is dimensioned by `year` and `project`.

    DEFINE project DIMENSION TEXT
    MAINTAIN project ADD 'a' 'b' 'c' 'd' 'e'
    DEFINE cflow VARIABLE DECIMAL <project year>

When you assign the following values to CFLOW,

                 ------------------------CFLOW----------------------
                 -----------------------PROJECT---------------------
    YEAR             a          b          c          d          e
    ------------ ---------- ---------- ---------- ---------- -------
    Yr95           -200.00    -200.00    -300.00    -100.00  -200.00
    Yr96            100.00     150.00     200.00      25.00    25.00
    Yr97            100.00     400.00     200.00     100.00   200.00

then the following statement

    REPORT NPV(cflow, .08, year)

uses a discount rate of 8 percent to create the following report of the net present value of the `cflow` data.

                   NPV(CFLOW,
    PROJECT        .08, YEAR)
    -------------- ----------
    a                  -21.67
    b                  281.82
    c                   56.65
    d                    8.88
    e                   -5.38

### 8.45 NULLIF

The NULLIF function compares one expression with another and returns `NA` when the expressions are equal, or the base expression when they are not.

#### Return Value

`NA` when the expressions are equal, or the base expression when they are not.

#### Syntax

NULLIF (expr1 , expr2)

#### Parameters

expr1
An expression. The base expression for the comparison.

expr2
An expression to compare to expr1.

#### Examples

Example 8-41 Comparing Values Using NULLIF

    SHOW NULLIF(1, '1')
    NA

    SHOW NULLIF('red', 'Red')
    red

### 8.46 NUMBYTES

The NUMBYTES function counts the number of bytes in a text expression. When the value is a multiline text value, NUMBYTES returns the total number of bytes in all the lines. The result returned by NUMBYTES has the same dimensions as the specified expression.

#### Return Value

INTEGER

#### Syntax

NUMBYTES(text-expression)

#### Parameters

text-expression
The `TEXT` expression whose bytes are to be counted.

#### Examples

Example 8-42 Counting the Bytes in the Longest Name

You would like to know the length of the names of your products so you can specify the appropriate width for the label column in a report. You can use the NUMBYTES function in combination with the LARGEST function to find the length of the longest label. Then use that value to set the column size. The following statements in a program find the longest name and use the byte count to format a report.

    firstcol = LARGEST(NUMBYTES(name.product))+1
    LIMIT month TO FIRST 3
    FOR product
       DO
         ROW WIDTH FIRSTCOL name.product WIDTH 6 ACROSS month - 
         FIRST 3: units
       DOEND

When the program is run, it produces the following output.

    3-Person Tents      200    203    269
    Aluminum Canoes     347    400    482
    Tennis Racquets     992  1,076  1,114
    Warm-up Suits     1,096  1,214  1,294
    Running Shoes     2,532  2,405  2,775

### 8.47 NUMCHARS

The NUMCHARS function counts the number of characters in a text expression. When the value is a multiline text value, NUMCHARS returns the total number of characters in all the lines. The result returned by NUMCHARS has the same dimensions as the specified expression.

**Tip:**

When you are using a multibyte character set, you can use the NULLIF function instead of the NUMCHARS function.

#### Return Value

INTEGER

#### Syntax

NUMCHARS(text-expression)

#### Parameters

text-expression
The text expression whose characters are to be counted. NUMCHARS accepts either a TEXT or NTEXT argument. It does not perform an automatic conversion to either data type. It returns the information that is correct for the data type of the specified argument.

#### Examples

Example 8-43 Counting the Characters in the Longest Name

You would like to know the length of the names of your products so you can specify the appropriate width for the label column in a report. You can use the NUMCHARS function in combination with the LARGEST function to find the length of the longest label. Then use that value to set the column size. The following statements in a program find the longest name and use the character count to format a report.

    firstcol = LARGEST(NUMCHARS(name.product))+1
    LIMIT month TO FIRST 3
    FOR product
       DO
         ROW WIDTH FIRSTCOL name.product WIDTH 6 ACROSS month - 
         FIRST 3: units
       DOEND

When the program is run, it produces the following output.

    3-Person Tents      200    203    269
    Aluminum Canoes     347    400    482
    Tennis Racquets     992  1,076  1,114
    Warm-up Suits     1,096  1,214  1,294
    Running Shoes     2,532  2,405  2,775

### 8.48 NUMLINES

The NUMLINES function counts the number of lines in each value of a text expression. The result returned by NUMLINES has the same dimensions as the specified expression.

NUMLINES accepts either a TEXT or NTEXT argument. It does not perform an automatic conversion to either data type.

#### Return Value

INTEGER

#### Syntax

NUMLINES(text-expression)

#### Parameters

text-expression
The text expression whose lines are to be counted.

#### Examples

Example 8-44 Counting the Number of Lines

In this example, you want to determine the number of lines in the multiline text variable LASTNAMES. The LASTNAMES variable has the following values.

    Adamson
    Jones
    Smith
    Taylor

The statement

    SHOW NUMLINES(lastnames)

produces the following output.

    4

### 8.49 NUMTODSINTERVAL

The NUMTODSINTERVAL function converts a number to a DSINTERVAL literal.

#### Syntax

NUMTODSINTERVAL (number, interval_unit)

#### Parameters

number
Any NUMBER value or an expression that can be implicitly converted to a NUMBER value.

interval_unit
A text value that specifies the unit of number and must resolve to one of the following string values: DAY, HOUR, MINUTE, or SECOND.

interval_unit is case insensitive. Leading and trailing values within the parentheses are ignored. By default, the precision of the return is 9.

### 8.50 NUMTOYMINTERVAL

The NUMTOYMNTERVAL function converts a number to a YMINTERVAL literal.

#### Syntax

NUMTOYMINTERVAL (number, interval_unit)

#### Parameters

number
Any NUMBER value or an expression that can be implicitly converted to a NUMBER value.

interval_unit
A text value that specifies the unit of number and must resolve to one of the following string values: YEAR or MONTH.

interval_unit is case insensitive. Leading and trailing values within the parentheses are ignored. By default, the precision of the return is 9.

### 8.51 NVL

The NVL function replaces a `NA` value or an empty string with a string.

To evaluate a specified expression and replace a non-`NA` value or empty string with one value and a `NA` value with another, use NVL2.

#### Return Value

The specified replacement value when the value of the base expression is `NA`, or the base expression when the value of the base expression is not `NA`. The data type of the return value is always the same as the data type of the base expression.

#### Syntax

NVL (exp , replacement-exp)

#### Parameters

expr
The expression to replace when it has a `NA` value or an empty string.

replacement-exp
The value with which you want to replace a `NA` value.

#### Examples

Example 8-45 Working with NVL

    SHOW NVL('First String', 'Second String')
    First String

    SHOW NVL('', 'Second String')
    Second String

### 8.52 NVL2

The NVL2 function returns one value when the value of a specified expression is not `NA` or an empty string, or another value when the value of the specified expression is an empty string or `NA`.

To replace a `NA` value or an empty string with a string, use NVL.

#### Return Value

The data type of the return value is always the data type of expr2 (that is, the expression whose value is returned when the value of expr1 is not `NA`).

#### Syntax

NVL2 (expr1 , expr2 , expr3)

#### Parameters

expr1
The expression whose value this function evaluates.

expr2
An expression whose value is returned when the value of expr1 is not an empty string or `NA.`

expr3
An expression whose value is returned when the value of expr1 is `NA.`

#### Usage Notes

Comparing Values of Different Data Types

When the data types of expr2 and expr3 are different, then the function converts expr3 to the data type of expr2 before comparing them.

#### Examples

Example 8-46 Working with NVL2

    SHOW NVL2('Which string?', 'First String', 'Second String')
    First String

    SHOW NVL2('', 'First String', 'Second String')
    Second String

### 8.53 OBJ

The OBJ function returns information about an analytic workspace object.

#### Return Value

The return value depends on the value specified for choice. Also, when choice is applicable to only a specific type of object, and you specify a different type of object for object-name, then OBJ returns `NA` unless otherwise noted.

#### Syntax

OBJ(choice \[object-name\])

#### Parameters

object-name
A `TEXT` expression that is the name of the object that you want to retrieve information about.

choice
A keyword or keyword phrase which indicates the type of information you want. The following table lists the syntax, data type of the returned value, and description of valid keywords.

Table 8-2 Keywords for the choice argument of the OBJ Function

| Keyword for choice                   | Data Type        | Description of Returned Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-------------------------------------|:-----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ACQUIRED                             | BOOLEAN          | Whether the specified object has been acquired for modification in multiwriter mode. For a partitioned variable, returns YES only when all of the partitions of that variable have been acquire.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ACQUIREDPARTITIONS                   | TEXT (multiline) | The names of the partitions of the variable specified by object-name that are acquired for modification in multiwriter mode.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| AGGMAP                               | TEXT (multiline) | The specification of the specified aggmap.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| AGGMAPLIST                           | TEXT (multiline) | The names of the aggmap objects in the specified formula.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ALIASLIST                            | TEXT (multiline) | The names of the alias dimensions for the specified dimension.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ALIASOF                              | TEXT             | The name of the base dimension for the specified alias dimension.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| AW                                   | TEXT             | The name of an attached workspace that contains the specified object. When the specified object is in only one attached workspace, AW returns the name of the workspace. When the specified object is in multiple attached workspaces, AW still returns only one workspace name. You must use the AWLIST keyword to get all the relevant workspace names. When the object is not in any attached workspace, AW returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| AWLIST                               | TEXT (multiline) | The names of the attached workspaces that contain an object with the specified name. When you specify a qualified object name for the object, AWLIST returns only the relevant workspace name. When no workspace contains the specified object, AWLIST returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| BTREE                                | BOOLEAN          | Whether a BTREE index was defined for the specified conjoint dimension or composite.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| CACHEEMPTY                           | BOOLEAN          | Whether a session cache has been emptied of data for the specified variable. A cache can be emptied by using a CLEAR statement with the CACHE keyword. When object-name is not a variable or when it has no session cache, then CACHEEMPTY returns `NA`. (For more information on the session cache, see "[What is an Oracle OLAP Session Cache?](olap-dml-options.md)".)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| CACHECOUNT                           | LONG INTEGER     | The number of non-`NA` cells in the session cache for the specified variable. When object-name is not a variable or when it does not have a no session cache, then CACHECOUNT returns `NA`. (For more information on the session cache, see "[What is an Oracle OLAP Session Cache?](olap-dml-options.md)".).)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| CHANGED                              | BOOLEAN          | Whether the specified variable, relation, dimension, or valueset has been modified since the last UPDATE.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| CHANGEDPAGES                         | INTEGER          | The number of pages in the analytic workspace that have changed since the last update. This is approximately the number of pages that an UPDATE command will write to disk. The larger the number of changed pages, the longer the UPDATE command takes to complete.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| CLASS                                | TEXT             | The storage class of the specified object. Possible return values are:<br>• TEMPORARY — An object whose values are not saved in the workspace; applicable to valuesets, variables, relations, and worksheets.<br>• An empty string — A permanent object whose values, when modified, are stored in a new place in the workspace until you update and are then included in the update; applicable to all object types.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| DATA                                 | TEXT             | The data type of the specified object.<br>• For dimensions, variables, and formulas, possible return values are `INTEGER`, `SHORTINTEGER`, `LONGINTEGER`, `DECIMAL`, `NUMBER`, `SHORT` (for SHORTDECIMAL), `BOOLEAN`, `ID`, `TEXT`, `NTEXT`, `DATE` or `DATETIME`.<br>• For a relation, it returns the name of the related dimension.<br>• For a concat dimension, conjoint dimension, composite, or partition template, it returns the names of the base dimensions of an object as a multiline text value.<br>• For a program defined with a data type, it returns the name of the data type. For a program defined to return a value of a dimension, returns the name of the dimension.<br>• For a valueset, it returns the name of the dimension for which the valueset was defined.<br>• For other types of objects, it returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| DEFINE                               | TEXT (multiline) | The description of the specified object. The value is the same value that DESCRIBE would display for the object minus the words DEFINE and the name of the object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| DFNCHANGED                           | BOOLEAN          | Whether the definition of the specified object has changed since the last UPDATE.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| DFNDIMS                              | TEXT (multiline) | The names of the dimensions and composites in the dimension list that is used to define the specified object. Note that:<br>• For an unnamed composite, it returns the form used in the object definition: `SPARSE<dim1 dim2 ...>`.<br>• For a dimension surrogate, it returns the name of the dimension for which the surrogate was defined.<br>• When no dimension list was used when the specified object was defined, it returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| DIMMAX                               | INTEGER          | The number of values in the specified dimension. For other object types, it returns `0` (zero).<br>Note: When you use the DIMMAX choice with a dimension that has a read permission that restricts access to the dimension values, the result returned depends on whether the dimension has previously been loaded. Permissions are evaluated when an object is loaded. Generally, the first time you refer to an object in your session, Oracle OLAP loads the object and evaluates its permissions. However, the OBJ function does not load objects, because it is just providing information about them. When you use DIMMAX with a dimension that has not yet been loaded, the result reflects the entire number of values in the dimension, regardless of whether the dimension has read permissions. When a dimension with permissions has been loaded, then the DIMMAX choice reflects the permitted size. To ensure that the DIMMAX choice returns the permitted size, you can execute a LOAD statement before using the OBJ function.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| DIMS                                 | TEXT (multiline) | The names of the dimensions of the specified object. Specifically:<br>• For dimensions, simple, concat, or conjoint, it returns the name of the dimension itself. To find out the base dimensions of a concat or conjoint dimension, use the DATA keyword.<br>• For composites, it returns the base dimensions of the composite.<br>• For a dimension surrogate, it returns the name of the dimension for which the surrogate was defined.<br>• For dimensioned objects, it returns the names of the dimensions of the object.<br>• When an object has no dimensions, it returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| DIMTYPE                              | TEXT             | The type of the specified dimension. Specifically:<br>• For a concat dimension, it returns `CONCAT`.<br>• For a conjoint dimension, it returns `CONJOINT`.<br>• For a composite, it returns `COMPOSITE`.<br>• For a simple dimension, it returns the data type of the dimension.<br>• For a partition template object, it returns `PARTITION TEMPLATE`.<br>• For all other objects, it returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| DISKSIZE                             | INTEGER          | The total number of pages used to store the specified object.<br>Note: For a temporary object, OBJ(DISKSIZE) returns a value of 0 (zero), because the values of a temporary object are stored in temporary storage and not in the database file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| FORMULA                              | TEXT             | The expression in the definition of the specified formula.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| HASAGGCOUNT                          | BOOLEAN          | Whether an Aggcount object is associated with the specified variable. (For more information on Aggcount variables, see "[Aggcount Variables](olap-dml-commands-a-g.md)".)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| HASCACHE                             | BOOLEAN          | Whether a session cache that is local to the session has been established to store data for the specified variable. (For more information on the session cache, see "[What is an Oracle OLAP Session Cache?](olap-dml-options.md)".)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| HASH                                 | BOOLEAN          | Whether a HASH index was defined for the specified conjoint dimension or composite.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| HASHSIZE                             | INTEGER          | The number of pages allocated for the specified hashed dimension's TBLSPACE (that is, the page space containing the anchors for the hash table's K/V node lists). Note that this does not include the number of pages used for the actual Key/Value nodes, which are allocated from the RANSPACE's page space (KVPAGES).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| HASPROPERTY prop-name                | BOOLEAN          | Whether the property specified by prop-name exists for the specified object. (Abbreviated HASPRP)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| HIDDEN                               | BOOLEAN          | Whether the text of the specified program or model has been hidden. (For more information on hiding programs and models, see the [HIDE](olap-dml-commands-h-z.md) and [UNHIDE](olap-dml-commands-h-z.md) commands.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| INDEXSIZE                            | INTEGER          | The total size of all inversions associated with the specified relation or conjoint dimension.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| INORDER                              | BOOLEAN          | Whether the logical order of the values of the underlying dimensions of the specified object matches the physical order in the analytic workspace. INORDER returns `TRUE` when the logical order of the values of the dimension has not been specified using MAINTAIN with the keywords ADD FIRST, ADD AFTER, ADD BEFORE, or MOVE.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ISBY \[RECURSIVE\] dimname           | BOOLEAN          | When you supply object-name, whether the specified object is dimensioned by, related to, or a surrogate for the specified dimension (dimname). When you supply only dimname, whether an object is dimensioned by the dimension you specify in dimname; or when the object is an aggmap, whether the specified dimension is a dimension of any relations or models in the aggmap.<br>• RECURSIVE specifies that Oracle OLAP should search for dimname in the base dimensions of the specified object, at any level. the. See Example 8-49 .<br>• dimname is a text expression that is the name of a dimension. (Oracle OLAP automatically converts the name to uppercase.) When dimname is a composite, the value returned by ISBY indicates if an object was defined with the composite.<br>Specify a value for object-name when the object is a dimension surrogate, variable, relation, or valueset name to learn if that object is dimensioned by or related to or a surrogate for the specified dimension. You can omit object-name when you are looping through the list of workspace objects to obtain information about multiple objects, or when you are using OBJ to limit the NAME dimension.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ISCOMPILED                           | BOOLEAN          | Whether the compilation status of the specified compilable object (such as a program, model, or formula). The value returned depends on the type of object and on whether a compilation error was found in that object. For example:<br>• For programs, returns `YES` when the program has been processed by the compiler since the last time it was modified. A return value of `YES` does not necessarily indicate that all lines of the program are compiled. See the [COMPILE](olap-dml-commands-a-g.md) command for more information.<br>• For formulas, returns `YES` only when the formula was compiled without finding a single error and when the formula can be saved. When the formula contains ampersand substitution, it cannot be saved. When the formula is empty, the ISCOMPILED choice returns `NO`.<br>• For models, returns `YES` only when the model was compiled without a single error found or when the model is empty.<br>• For programs, formulas, and models, returns `NO` when you delete an object that the program, formula, or model references.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ISCOMPRESSED                         | BOOLEAN          | Whether the specified object is a compressed composite.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ISLATEST                             | BOOLEAN          | Whether the specified object is the latest version of the object. This syntax is the equivalent of `OBJ(VERSION)EQ OBJ(LATESTVER)`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| ISSOLVED                             | BOOLEAN          | When the specified object is a variable which is dimensioned by a compressed composite, whether the variable has been aggregated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| KVSIZE                               | INTEGER          | The number of pages currently allocated to hash and BTREE indexes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| LATESTVER                            | INTEGER          | The current state of the specified object, referring to the most recently committed version of the object. The returned value is either equal to or greater than the value returned by `OBJ(VERSION)`. When the value returned by LATESTVER is greater than that returned by `OBJ(VERSION)`, then another user has updated this object since the analytic workspace was attached in read-only or read/write mode, or, if the analytic workspace was attached in multiwriter mode, since the last synchronization.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| LD                                   | TEXT (multiline) | The LD (long description) of the specified object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| MODEL                                | TEXT (multiline) | The specification of the specified model.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| NACACHECOUNT                         | INTEGER          | The total number of `NA` cached cells.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| NACACHEEMPTY                         | BOOLEAN          | Whether the `NA` cache is empty.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| NAPAGES                              | INTEGER          | The number of pages that contain only `NA` values and are not stored in the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| NOHASH                               | BOOLEAN          | Whether the specified conjoint dimension uses the NOHASH index algorithm to load and access data.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| NUMCELLS                             | INTEGER          | The total number of physical cells within the specified variable. Oracle OLAP determines this value by finding the Cartesian product of the `OBJ(DIMMAX)` values for the dimensions of the variable, taking composites into account.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| NUMDELS                              | DECIMAL          | The number of deleted cells for the specified dimensioned object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| NUMDFNDIMS                           | INTEGER          | The number of dimensions or composites in the dimension list used to define the specified object. For this count, each composite counts as one, and the dimensions within the dimension list of the composite are not counted. An object defined with a dimension list could be a variable, relation, formula, valueset, concat or conjoint dimension, dimension surrogate, or composite. When no dimension list was used when defining the object (as for single-cell variables, programs, and so on.), it returns `0` (zero).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| NUMDIMS                              | INTEGER          | The number of dimensions of the specified dimensioned object; or the number of base dimensions of the specified composite. When the specified object is a dimension is a dimension or dimension surrogate, it returns `1`, and for all other objects, it returns `0` (zero).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| NUMSEGS                              | INTEGER          | The number of analytic workspace segments associated with the specified object when that object has multiple dimensions. (Note that Oracle OLAP uses segments internally to keep track of the physical storage of the object's values. Too many segments may slow the retrieval of information.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| NUMVALS                              | INTEGER          | The number of values or cells in the specified object. For a compressed composite or a variable dimensioned by a compressed composite, returns an `INTEGER` value that is the number of logical values in the object (that is, the value that would be returned if the composite was a b-tree composite).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| OWNSPACE                             | BOOLEAN          | When the specified object is a conjoint dimension or a composite defined with a BTREE index algorithm, whether the object is using private page space to store BTREE nodes. When the specified object is a variable-width text dimension, a relation, or a variable-width text variable, whether the data for the object is stored in one or more private page spaces that are associated with that object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| PARTBY                               | TEXT (multiline) | The names of the partition dimensions of the specified partitioned variable or partition template object. The names are returned as a multiline text value (one line for each dimension).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| PARTDIMS partitions                  | TEXT (multiline) | The names of the dimensions of the partitions of the specified partition template or a partitioned variable. The value is returned as a multiline text value (one line for each dimension).<br>partitions is a multiline text value (one line for each partition name) that specifies which partitions you're asking about. When you specify a partition name that is not a valid partition in partitions, an error occurs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| PARTITION partitions                 | TEXT (multiline) | For a partitioned variable or a partition template object, a textual description of the partitions of the specified partition template or a partitioned variable. When called on a partition template, the returned description is similar to the DEFINE PARTITION TEMPLATE statement. When called on a partitioned variable, the returned description is similar to the DEFINE VARIABLE statement.<br>partitions is a multiline text value (one line for each partition name) that specifies which partitions you're asking about.When you specify a partition name that is not a valid partition in partitions, an error occurs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| PARTMETH                             | TEXT             | The method (`RANGE` or `LIST`) by which the specified partition template or a partitioned variable is partitioned.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| PARTNAMES                            | TEXT (multiline) | A multiline `TEXT` value containing the names of all the defined partitions of the specified partition template. When name is the name of a partitioned variable, returns a multiline TEXT value containing the names of all the partitions of the variable.<br>Note: Not all of the partitions defined by a partition template necessarily exist in each partitioned variable. Calling `OBJ(PARTNAMES)`on a partitioned variable returns only those partitions that actually exist within the variable.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| PARTRANGE partitions                 | TEXT (multiline) | The values of the `LESS THAN` clause for each of the partitions for the specified RANGE partition template or RANGE partitioned variable.<br>partitions is a multiline text value (one line for each partition name) that specifies which partitions you're asking about. When you specify a partition name that is not a valid partition in partitions, an error occurs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| PERIOD                               | TEXT             | When the specified object is a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, the type of the dimension plus an indication of multiple periods or phasing, if any.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| PHYSMAX                              | INTEGER          | The maximum physical value for positions within the specified dimension or composite.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| PMTMAINTAIN                          | TEXT             | The permission condition for the maintain permission associated with the specified dimension. When there is no maintain permission for the dimension, it returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| PMTPERMIT                            | TEXT             | The permission condition for the permit permission associated with the specified object. When there is no permit permission for the object, it returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| PMTREAD                              | TEXT             | The permission condition for the read permission associated with the specified object. When there is no read permission for the object, it returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| PMTWRITE                             | TEXT             | The permission condition for the write permission associated with the specified object. When there is no write permission for the object, it returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| PRECISION                            | INTEGER          | The precision of the specified `NUMBER` dimension or variable. The precision is the total number of digits. When the variable was defined without a precision specification, then OBJ returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| PROGRAM                              | TEXT (multiline) | The text of the specified program.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| PROPCHANGED                          | BOOLEAN          | Whether the properties of the specified object have changed since the last UPDATE.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| PROPERTY prop-name                   | WORKSHEET        | The value of the specified object's property as specified by prop-name which is a text expression that specifies the name of the property. The data type of the return value is determined at run time. When the named property does not exist, it returns `NA`. (Abbreviated PRP)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| PROPERTYLIST                         | TEXT (multiline) | The names of the properties associated with the specified object, one property on a line. The names are in uppercase letters and are stored in the collating sequence for ASCII characters. For objects without properties, it returns `NA`. (Abbreviated PRPLIST)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| PROPERTYTYPE prop-name               | TEXT             | The data type of object's property as specified by prop-name which is a text expression that specifies the name of the property. The type is derived from the expression used in the PROPERTY statement that created the property. Possible return values are `BOOLEAN`, `TEXT`, `ID`, `DATE`, `DATETIME`, `NUMBER`, `INTEGER`, `LONGINTEGER`, `DECIMAL`, and `SHORT`.When the named property does not exist or has a value of `NA`, it returns `NA`. (Abbreviated PRPTYPE)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| PUSHCOUNT                            | INTEGER          | The number of times PUSH has executed for the specified executed (that is, the number of pushed values currently saved for the specified object).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| REFERS \[RECURSIVE\] text-expression | TEXT (multiline) | The words found in the specified compilable object (for example, a program) that match the ones you specify in text-expression. REFERS returns `NA` when it does not find any of the specified words, when the specified object is not a compilable object, or when the workspace does not contain any compilable objects. When you supply both arguments, REFERS searches only the specified object for the listed words. When you omit object-name, REFERS searches all the compilable objects in the current workspace.<br>• text-expression is a multiline `TEXT` expression that is the words for which it should search. Each line in the text value is considered a separate word to be searched for. When, for text-expression, you specify a list of words that is the result of the OBJLIST function, you can produce a cross-reference for compilable objects in the current workspace.<br>• RECURSIVE specifies that Oracle OLAP should search (following the calling tree) for the text-expression to retrieve a list of all of the occurrences of text-expression, at any level.<br>Tip: The search is not case-sensitive; REFERS treats `TEXTVAR` and `Textvar` as the same word. REFERS ignores all text that is included in a comment or enclosed in single quotes.                                                                                                                                                                                                                                                                                                                                                                     |
| RELATION relation-query              | TEXT (multiline) | The default relation (as specified the RELATION command) for the specified object. The values that are returned vary depending on what you specify for relation-query. The syntax for relation-query is:<br>` DEFINELIST | DIMLIST | ACTUAL ``rel-dimname`` | SPECIFIED ``rel-dimname`<br>where:<br>• DEFINELIST specifies that the function return all of the names of the dimensions and their associated default relations. As shown in the following example, the names are returned and it associated default relation are returned one per line, alternating between dimension name and its associated default relation.<br>`                  dimname1`<br>`                  relname1`<br>`                  dimname2`<br>`                  relname2`<br>• DIMLIST specifies that the function return all of the names of the dimensions for which default relations have been specified. As shown in the following example, Oracle OLAP returns the values one dimension name per line.<br>`                  dimname1`<br>`                  dimname2`<br>• ACTUAL `dimname` specifies that the function return the relation that Oracle OLAP uses as the default relation between object-name and its related dimension specified by rel-dimname.<br>• SPECIFIED `dimname` specifies that the function return the name of the relation specified in the RELATION command as the default relation between object-name and its related dimension specified by rel-dimname which is the value as actually entered in the RELATION command, even if an error occurred entering the data and there is no such relation in the analytic workspace. |
| RSSIZE                               | INTEGER          | The number of random subset pages used by main object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| SCALE                                | INTEGER          | The scale of a `NUMBER` dimension or variable. A positive scale indicates the number of digits to the right of the decimal point. A negative scale indicates the number of rounded digits to the left of the decimal point. When the variable was defined without a scale specification, then OBJ returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| SEGWIDTH {dim-name\|ALL}             | TEXT (multiline) | The default or user-specified segment size of a variable that has multiple dimensions and that is associated with either a particular dimension or all dimensions. Each line begins with a segment-size (up to 11 digits) followed by the name of the associated dimension or composite. The dimension name is not included in the line when you specify a dimension and its dimensioned object. In that case only the segment value is returned. When the segment size is reported as zero, it means the default segment size is in effect, and therefore you may have to use CHGDFN to set an appropriate size for the variable's segments.<br>• dim-name is a text expression that is the name of a dimension.<br>• ALL specifies all dimensions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| SESSION                              | BOOLEAN          | Whether the specified object is a session object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| SHAREMAP                             | BOOLEAN          | When the specified object is dimensioned by a compound dimension, whether the compound dimension is shared with other objects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| SPARSE                               | TEXT (multiline) | The composites used in the definition of the specified object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| SURROGATELIST                        | TEXT (multiline) | The surrogates defined for the specified surrogate or dimension.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| TRIGGER \[triggering-event}          | TEXT (multiline) | TRIGGER without a triggering-event keyword returns all the triggering-event keywords and trigger programs names associated with the specified object; or `NA` when the object does not have any trigger programs associated with it. TRIGGER with a triggering-event keyword returns the names of the trigger programs associated with the specified object event.<br>Specify the triggering-event using one of the following keywords:<br>• MAINTAIN<br>• DELETE<br>• PROPERTY<br>• ASSIGN<br>• BEFORE_UPDATE<br>• AFTER_UPDATE                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| TYPE                                 | TEXT             | The object type of the specified object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| UNIQUE                               | BOOLEAN          | Whether the specified concat dimension is unique. Returns `FALSE` for other dimensions, and `NA` for other object types (including Partition Templates).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| UPDATED                              | BOOLEAN          | When the analytic workspace is attached in multiwriter mode, whether the specified object been updated. For other attachment modes, returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| VALCOUNT                             | INTEGER          | The number of logical uncompressed values in the specified compressed composite. For all other dimensions the result is identical to DIMMAX.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| VALSIZE                              | INTEGER          | The number of pages used to store the specified object's values. For text dimensions and variables defined without the WIDTH keyword, OBJ(VALSIZE) counts only those pages that contain the four-byte pointers to the text, not the storage for the text itself. For a temporary variable, OBJ(VALSIZE) returns a value of 0 (zero) because the values of a temporary variable are stored in temporary storage and not in the analytic workspace.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| VERSION                              | INTEGER          | The current state of the attached version of the specified object. (Note that changes that are updated and committed increase this number.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| VNF                                  | TEXT             | When the specified object is a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR for which you have defined a VNF (value name format), the VNF of the dimension. For other types of objects, it returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| WIDTH                                | INTEGER          | The width, in bytes, of the storage area of each value of the specified object:<br>• For dimensioned INTEGER and BOOLEAN variables that you defined with a width, it returns `1`.<br>• For dimensioned text variables and text dimensions that you defined with a width, it returns a value between `1` and `4000`, which identifies the defined width.<br>• For all other objects, it returns `NA`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

object-name
A text expression that contains the name of the object in which you are interested. The object can be in any attached workspace. When you specify object-name as a text literal, you must enclose it in single quotes. (Oracle OLAP automatically converts the name to uppercase.) When you specify the name of a program as the object-name and you omit the quotes, Oracle OLAP runs the program and uses its return value as the name of the object to be supplied as object-name.

You can omit object-name when you are using the OBJ function as part of a statement, such as the LIMIT command, that loops through the NAME dimension. In this case, the return value is dimensioned by the NAME dimension in the current workspace.

#### Examples

**See Also:**

[Example 10-95](olap-dml-commands-h-z.md) for examples of using the OBJ function to retrieve default relation information

Example 8-47 Listing Dimensions

Suppose you want a list of all the dimensions in an analytic workspace. First, use a LIMIT command and the OBJ function to limit the status of the NAME dimension. Then use a STATUS statement to produce a list of dimensions. Because the values returned by `OBJ(TYPE)` are always in uppercase, you must use `'DIMENSION'` (not `'dimension'`) in the LIMIT statement to get a match. The statements

    LIMIT NAME TO OBJ(TYPE) EQ 'DIMENSION'
    STATUS NAME

produce the following output.

    The current status of NAME is:
    PRODUCT, DISTRICT, DIVISION, LINE, REGION, MARKETLEVEL, MARKET,
    MONTH, YEAR, QUARTER

Example 8-48 Listing Relations

Suppose you want to see the definitions of all the relations in an analytic workspace. Use the LIMIT command and the OBJ function to select these names. Then use DESCRIBE to produce a list of their definitions. The statements

    LIMIT NAME TO OBJ(TYPE) EQ 'RELATION'
    DESCRIBE

produce the following output.

    DEFINE REGION.DISTRICT RELATION REGION <DISTRICT>
    LD REGION for each DISTRICT
     
    DEFINE DIVISION.PRODUCT RELATION DIVISION <PRODUCT>
    LD DIVISION for each PRODUCT
     
    DEFINE MLV.MARKET RELATION MARKETLEVEL <MARKET>
     
    DEFINE MARKET.MARKET RELATION MARKET <MARKET>
    LD Self-relation for the Market Dimension

Example 8-49 OBJ With ISBY

For example, the following statement limits NAME to all the objects dimensioned by `month`.

    LIMIT NAME TO OBJ(ISBY 'month')

You can use ISBY to find out if a dimension is a base dimension of a concat or conjoint dimension or a composite. For example, assume that you had a conjoint dimension named `proddist` whose base dimensions were `product` and `district`. In this case, the following statement returns `YES`.

    SHOW OBJ(ISBY 'district' 'proddist')

You can use ISBY to find out if a dimension is a dimension of a relation or a model used in an aggmap. For example, assume that you had an aggmap called `myaggmap` and you wanted to find out if a dimension named `mydimension` was used in any relations or models within `myaggmap`. In this case, you could issue the following statement.

    SHOW OBJ(ISBY 'mydimension' 'myaggmap')

To determine whether a specified dimension is a base dimension at any level, you must use ISBY with the RECURSIVE keyword. For example, assume that you had a conjoint dimension named `proddist.mon` whose base dimensions were `proddist` and `month` and a variable `proddist.sales` dimensioned by `proddist`. In this case, each of the following statements would return `NO`.

    SHOW OBJ(ISBY 'district' 'proddist.mon')
    SHOW OBJ(ISBY 'district' 'proddist.sales')

However, when you use ISBY with the RECURSIVE keyword, each of the following statements would return `YES`.

    SHOW OBJ(ISBY RECURSIVE 'district' 'proddist.mon')
    SHOW OBJ(ISBY RECURSIVE 'district' 'proddist.sales')

Example 8-50 Getting Information about a Variable

This example illustrates the use of several choices of the OBJ function to obtain information about the variable `sales`. The definition of `sales` is as follows.

    DEFINE sales VARIABLE DECIMAL <month product district>
    LD Sales Revenue

- The statement

      SHOW OBJ(TYPE 'sales')

  produces the following output.

      VARIABLE

- The statement

      SHOW OBJ(DATA 'sales')

  produces the following output.

      DECIMAL

- The statement

      SHOW OBJ(DIMS 'sales')

  produces the following output.

      MONTH
      PRODUCT
      DISTRICT

- The statement

      SHOW OBJ(ISBY 'product' 'sales')

  produces the following output.

      YES

- The statement

      SHOW OBJ(LD 'sales')

  produces the following output.

      Sales Revenue

Example 8-51 Returning the Name of the Object or the Type of the Object

Suppose `textvar` is a variable whose value is `geog`, which is the name of a dimension. Whether you enclose the word `textvar` in quotation marks determines whether the following `OBJ` function calls return the word `VARIABLE` (the type of object `textvar` is) or `DIMENSION` (the type of object `geog` is).

    SHOW OBJ(TYPE 'textvar')
    VARIABLE

    SHOW OBJ(TYPE textvar)
    DIMENSION

Example 8-52 Using OBJ to Select Objects

This example uses OBJ and DESCRIBE to look at the definitions of all the relations in an analytic workspace. The Oracle OLAP statements

    LIMIT NAME TO OBJ(TYPE) EQ 'RELATION'
    DESCRIBE

produce the following output.

    DEFINE REGION.DISTRICT RELATION REGION <DISTRICT>
    LD REGION for each DISTRICT
     
    DEFINE DIVISION.PRODUCT RELATION DIVISION <PRODUCT>
    LD DIVISION for each PRODUCT
     
    DEFINE MLV.MARKET RELATION MARKETLEVEL <MARKET>
     
    DEFINE MARKET.MARKET RELATION MARKET <MARKET>
    LD Self-relation for the Market Dimension

Example 8-53 Counting Compiled Objects

The following statements count how many compilable objects in your workspace are compiled and how many are not compiled. Each statement loops over the objects in the current workspace. The OBJ function returns `YES` for each object that is compiled, `NO` for each compilable object that is not compiled, and `NA` for objects that are not compilable. When NASKIP is `YES` (the default), the COUNT function in the first statement counts the number of `YES` values that are returned by OBJ, and in the second statement it counts the number of `NO` values that are returned.

    SHOW COUNT(OBJ(ISCOMPILED))
    SHOW COUNT(NOT OBJ(ISCOMPILED))

Example 8-54 OBJ with REFERS

The following statement searches the compilable objects in the current workspace for references to the objects in all the attached workspaces. The output lists the non-compilable objects in the current workspace too, but the return value for them is `NA`.

    REPORT OBJ(REFERS OBJLIST(AW(LIST)))

In the following example, `OBJ(REFERS)` tells you whether `var1`, `var2`, or `var3` appears in the `myprog` program. The return value of `OBJ(REFERS)` is a multiline text value that contains the references it finds. When only `var1` and `var3` appear in the program, then the return value contains those two names, each on a separate line. The statement

    SHOW OBJ(REFERS 'var1\nvar2\nvar3' 'myprog')

produces the following output.

    VAR1
    VAR3

When you do not specify the name of a program or formula to be searched, OBJ(REFERS) returns a single-line or multiline text value for each object in the NAME dimension of the current workspace. For objects that are not programs or formulas, `NA` is returned. The statement

    REPORT OBJ(REFERS 'var1\nvar2\nvar3')

produces the following output.

                   OBJ(REFERS
                     'var1
                      var2
    NAME           var3' )
    -------------- ----------
    PRODUCT        NA
    DISTRICT       NA
    DIVISION       NA
    LINE           NA
    QUARTER        NA
    REGION         NA
    YEAR           NA
    MONTH          NA
       ...
    MYPROG         VAR1
                   VAR3
    VAR1           NA
    VAR2           NA
    VAR3           NA

Example 8-55 OBJ with PROPERTY

In the following example, OBJ(PROPERTY) returns information about the `decplace` property of the `actual` variable. (See the [PROPERTY](olap-dml-commands-h-z.md) command for more information.) The user created this property to store the number of decimal places and now wants to obtain that value to produce a report of the `actual` variable.

The statements

    CONSIDER actual
    PROPERTY 'decplace' 4
    LIMIT month TO FIRST 1
    LIMIT division TO 'Camping'
    REPORT ACROSS month W 20 DECIMAL OBJ(PROPERTY 'decplace' -
    'actual') actual 

produce the following output.

    DIVISION: CAMPING
                   -------ACTUAL-------
                   -------MONTH--------
    LINE                  JAN 95
    -------------- --------------------
    Revenue                533,362.8800
    Cogs                   360,810.6600
    Gross.Margin           172,552.2200
    Marketing               37,369.5000
    Selling                 89,007.3800
    R.D                     24,307.5000
    Opr.Income              21,867.8400
    Taxes                   15,970.3900
    Net.Income               5,897.4500

Example 8-56 OBJ with SEGWIDTH

The following statements show how to change and display segment size values for all of a variable's dimensions.

    CHGDFN sales SEGWIDTH 150 5000 50
    SHOW OBJ(SEGWIDTH ALL 'sales')

These statements produce the following output.

     150 MONTH
    5000 PRODUCT
      50 DISTRICT

The following statement shows how to obtain the segment size value for a specific dimension.

    SHOW OBJ(SEGWIDTH 'product' 'sales')

This statement produces the following output.

    5000

The following statement shows how to obtain a list of segment sizes for every multidimensional variable or relation associated with the dimension.

When object-name is not specified, you must use REPORT rather than SHOW to obtain a value for each object in the NAME dimension.

    REPORT OBJ(SEGWIDTH 'product')

This statement produces the following output.

    NAME           OBJ(SEGWIDTH 'product')
    -------------- -----------------------
    SALES          5000
    SALES.FORECAST 5000
    SALES.PLAN     5000
    SHARE          5000
    UNITS          5000
    UNITS.M        0
       ...

The following statement shows how to produce a list of segment sizes for all dimensions in the current workspace.

    REPORT OBJ(SEGWIDTH ALL)

This statement produces the following output.

    NAME           OBJ(SEGWIDTH ALL)
    -------------- -----------------
    SALES          150 MONTH
                   5000 PRODUCT
                   50 DISTRICT
     
    SALES.FORECAST 150 MONTH
                   5000 PRODUCT
                   50 DISTRICT
        ...

### 8.54 OBJLIST

The OBJLIST function provides a list of the objects that are contained in one or more workspaces that you specify. The list of workspace objects returned by OBJLIST has duplicates removed and it is sorted in ascending order. The specified workspaces must be currently attached when you use the function.

The result, a multiline TEXT value, can be used as an argument to the OBJ function with the REFERS keyword. This usage helps in producing a cross-reference list for compilable objects, such as programs and models, in the current workspace.

**Note:**

OBJLIST always returns the names of all the objects in a given workspace, even when you have limited its NAME dimension.

#### Return Value

TEXT

#### Syntax

OBJLIST\[(text-expression)\]

#### Parameters

text-expression
A text expression that contains a single name or several names of currently attached workspaces. Each workspace name must be on a separate line of a multiline TEXT value. When you do not supply this argument, OBJLIST uses the current workspace name. When text-expression includes the name of an analytic workspace that is not attached, OBJLIST does not return a value. Instead, it signals an error.

#### Examples

Example 8-57 Listing Objects in Three Workspaces

In the following example, OBJLIST returns a multiline TEXT value that includes all the objects in the three workspaces specified: `mycode`, `mydata`, and `mytools`. The statement

    SHOW OBJLIST('mycode\nmydata\nmytools')

produces the following output.

    ACTUAL
    ADDFIVE
    ADVERTISING
    BUDGET
    CITYLIST
    CITYREPINIT
    CITYREPS
        ...
    YEAR

Example 8-58 Listing Referenced Objects

In the following example, OBJ(REFERS) returns a multiline TEXT value that contains every object from the `mycode`, `mydata`, and `mytools` workspaces that is referenced in the `myprog` program. The statement

    SHOW OBJ(REFERS OBJLIST('mycode\nmydata\nmytools') 'myprog')

produces the following output.

    ACTUAL
    BUDGET
     ...
    YEAR

### 8.55 OBJORG

The OBJORG function takes, as input, the name of an OLAP cube or cube dimension as defined in the Oracle data dictionary (sometimes called a "logical OLAP object") and returns information about the lower-level, "physical," analytic workspace objects by which that cube or cube dimension is implemented.

Use this function in OLAP DML statements that require an analytic workspace object name rather than an OLAP cube or cube dimension name.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Return value

Analytic workspace object name or `TEXT`; or `NA` if an analytic workspace has the requested definition information, but the field is empty.

#### Syntax

OBJORG(keyword \[OWNER owner \] top-level-object-name \[ sub-object-name \] )

#### Parameters

keyword
The valid keywords vary by the type of top-level-object or sub-object specified, as documented in:

- Table 8-3.

- Table 8-4.

- Table 8-5.

- Table 8-6.

- Table 8-7.

- Table 8-8.

- Table 8-9.

Table 8-3 Keywords when the top-level-object is a Cube

| Keyword                 | Returns                                                                                                                                                                                                                                |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Aggmap`                | The aggmap for the cube. (Note: The function will never return NA when you specify this keyword.)                                                                                                                                      |
| `Composite`             | When a composite is used for the cube, the name of the composite; or NA if the cube's sparsity type is DENSE, or if the cube is partitioned. (See also the keyword `PartitionComposite`.)                                              |
| `CubeStorageType`       | (Property.) The DML data type used for all of the cube's measures; or NA if there is no such single data type (that is, if different measures have different data types).                                                              |
| `MeasureDim`            | When the value returned for the keyword `CubeStorageType` is not NA, the analytic workspace measure dimension used to refer to the cube's base measures; or NA when the value returned for the keyword `CubeStorageType` is NA.        |
| `PartitionCompositeVar` | The text variable, dimensioned by `PartitionDim`, that holds the names of the composites for the cube's partitions; or NA if the cube's sparsity type is DENSE, or if the cube is not partitioned. (See also the `Composite` keyword.) |
| `PartitionDim`          | The analytic workspace dimension that contains the names of the partitions for the cube; or NA if the cube is not partitioned.                                                                                                         |
| `PartitionRel`          | The relation, dimensioned by `PartitionDim`, that relates each cube partition to its corresponding root dimension value; or NA if the cube is not partitioned.                                                                         |
| `PartitionTemplate`     | The partition template relating each cube partition to its corresponding analytic workspace dimension values; or NA if the cube is not partitioned.                                                                                    |
| `SharedMeasureVar`      | When the cube has a storage type, the variable (of that type) that stores all of the cube's measures; or NA when it does not.                                                                                                          |
| `SparseType`            | (Property.) The cube sparsity type. Valid values are: COMPRESSED, SPARSE, DENSE, or SPARSE_GLOBAL. Corresponds to column SPARSE_TYPE in the USER_CUBES and ALL_CUBES views.                                                            |

Table 8-4 Keywords when the top-level-object is a Cube and the sub-object is a Measure

| Keyword          | Returns                                                                                                                                                                                                                 |
|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Measure`        | When the value returned when you specify the `CubeStorageType` keyword for a cube is NA, the variable that stores this measure; or when not NA, the formula extracting this measure from the cube's top level variable. |
| `OverrideAggMap` | The aggmap for the measure, if the measure has one; otherwise returns NA. (Note that when the measure has no aggmap, then the cube's aggmap is used.)                                                                   |

Table 8-5 Keywords when the top-level-object is Cube and the sub-object is a Dimension Calculation Model

| Keyword              | Returns                                                                                                                                                                                                                                              |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AggFloorValueSet`   | If the cube's consistent solve specification specifies an aggregation at a specific level, the valueset consisting of all members of the dimension that belong to that level; otherwise, NA.                                                         |
| `HierValueSet`       | The valueset containing the names of all hierarchies of the analytic workspace dimension over which the cube is aggregated. (Note that when you specify this keyword, the function never returns NA.)                                                |
| `OperVar`            | If at least one of the cube's measures has an `OverrideAggMap`, the variable, dimensioned by the cube's measure dimension, that contains the aggregation operator used for each measure for which an `OverrideAggMap` exists.; otherwise, NA.        |
| `PrecomputeValueSet` | When the cube organization specifies a precompute condition, the valueset containing all members of the dimension that satisfy that condition; otherwise NA. (In particular, when the cube organization specifies a precompute percent, returns NA.) |

Table 8-6 Keywords when the top-level-object is a Cube Dimension

| Keyword               | Returns                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AggRel`              | The relation, dimensioned by `Dim` and `HierDim`, that relates each dimension value (in each hierarchy) to its parent dimension value (in that hierarchy). (Note that when you specify this keyword, the function never returns NA, even if the dimension has no hierarchies.)                                                                                                                                                                                                                                              |
| `AttributeCubeGIDRel` | The relation, dimensioned by `Dim`, that relates each dimension value to its cube GID (including attribute columns) in `___AW_GID_DIMENSION`. `AttributeCubeGIDRel` is the same as `CubeGIDRel`, except it includes attribute columns. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                                                                            |
| `CubeGIDRel`          | The relation, dimensioned by `Dim`, that relates each dimension value to its cube GID in `___AW_GID_DIMENSION`. When the dimension does not have a materialized view (MV), then `CubeGIDRel` is empty. The difference between a GID and a cube GID is that cube GIDs span all hierarchies. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                        |
| `Dim`                 | The analytic workspace physical dimension corresponding to this logical dimension. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                                                                                                                                                                                                                                |
| `DimOrderVar`         | The variable, dimensioned by `Dim` and `___AW_ALL_LANGUAGES`, that contains integers (for each dimension value, in each language) used for sorting. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                                                                                                                                                               |
| `FamilyRel`           | The relation, dimensioned by `Dim`, `LevelDim`, and `HierDim`, that relates each dimension value (in each level, in each hierarchy) to the dimension value (at that level, in that hierarchy), if any, of which it is a descendant. `FamilyRel` is similar to `ParentRel`, but it allows you to specify a level rather than automatically choosing the next level up. `FamilyRel` is similar to `ValueFamilyRel`, but used for level hierarchies. (Note that when you specify this keyword, the function never returns NA.) |
| `GIDRel`              | The relation, dimensioned by `Dim` and `HierDim`, that relates each dimension value (in each hierarchy) to its GID, if any, in` ___AW_GID_DIMENSION`. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                                                                                                                                                             |
| `HierDim`             | The dimension containing all hierarchies for this dimension. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                                                                                                                                                                                                                                                      |
| `HierLevelValueSet`   | The valueset, dimensioned by `HierDim`, that (for each hierarchy) contains all levels (from the `LevelDim`) that belong to that hierarchy. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                                                                                                                                                                        |
| `HierOrderVar`        | The variable, dimensioned by `Dim`, `HierDim`, and `___AW_ALL_LANGUAGES`, that contains integers (for each dimension value, in each hierarchy, in each language) used for sorting. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                                                                                                                                |
| `InHierValueSet`      | The valueset, dimensioned by `HierDim`, that (for each hierarchy) contains all dimension values (contained in that hierarchy). (Note that when you specify this keyword, the function never returns NA, even if the dimension has no hierarchies.)                                                                                                                                                                                                                                                                          |
| `LevelDim`            | The dimension containing all levels for this dimension. (Note that when you specify this keyword, the function never returns NA, even if the dimension has no levels.)                                                                                                                                                                                                                                                                                                                                                      |
| `LevelRel`            | The relation, dimensioned by the `Dim`, that relates each dimension value to a level in the `LevelList`. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                                                                                                                                                                                                          |
| `MemberDepthRel`      | The relation, dimensioned by `Dim` and `HierDim`, that relates each dimension value (in each hierarchy) to its depth (if any) in `___AW_DEPTH_DIMENSION`. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                                                                                                                                                         |
| `MemberSourceRel`     | The relation, dimensioned by `Dim`, that relates each dimension value to an element of `___AW_MEMBER_SOURCES`. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                                                                                                                                                                                                                                    |
| `ParentRel`           | The relation, dimensioned by `Dim` and `HierDim`, that relates each dimension value (in each hierarchy) to its parent dimension value (in that hierarchy). (Note that when you specify this keyword, the function never returns NA, even if the dimension has no hierarchies.)                                                                                                                                                                                                                                              |
| `ValueFamilyRel`      | The relation, dimensioned by `Dim`, `___AW_GID_DIMENSION`, and `HierDim`, that relates each dimension value (for each GID, in each hierarchy) to the dimension value (with that GID, in that hierarchy), if any, of which it is a descendant. `ValueFamilyRel` is similar to `FamilyRel`, but used for value hierarchies. (Note that when you specify this keyword, the function never returns NA.)                                                                                                                         |

Table 8-7 Keywords when the top-level-object is a Cube Dimension and the sub-object is a Base Attribute

| Keyword            | Returns                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Attribute`        | The value returned varies depending on whether or not the dimension is indexed.<br>• When the dimension is not indexed, the (physical) variable, dimensioned by `Dim` corresponding to the attribute's dimension and used to hold this (logical) attribute.<br>• When the dimension is indexed, the (physical) relation, dimensioned by `Dim` corresponding to the attribute's dimension, that relates each dimension value to a corresponding value from `AttributeDim`.<br>(Note that when you specify this keyword, the function never returns NA.) |
| `AttributeDim`     | When the attribute is indexed, the dimension that stores all of the attributes values; otherwise NA.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `HierUniqueKeyRel` | When the attribute is a unique key attribute, the relation, dimensioned by `Dim` and `HierDim` corresponding to the attribute's dimension, that relates each analytic workspace dimension value (in each hierarchy) to a corresponding value from `AttributeDim`; otherwise, NA.                                                                                                                                                                                                                                                                       |
| `UniqueKeyRel`     | When the attribute is a unique key attribute (that is, indexed), the relation, dimensioned by `Dim`, that corresponds to the attribute's dimension, that relates each dimension value to a corresponding value from `AttributeDim`.; otherwise, NA.                                                                                                                                                                                                                                                                                                    |

Table 8-8 Keywords when the top-level-object is a Cube Dimension and the sub-object is a Dimension Level

| Keyword        | Returns                                                                                                                                                                                               |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SurrogateDim` | The surrogate for the owning dimension's` Dim` that contains only those dimension values contained in this dimension level. (Note that when you specify this keyword, the function never returns NA.) |

Table 8-9 Keywords when the top-level-object is a Cube Dimension and the sub-object is a Dimension Calculation Model

| Keyword | Returns                                                                                                                                  |
|:--------|:-----------------------------------------------------------------------------------------------------------------------------------------|
| `Model` | The model corresponding to this dimension's calculation model. (Note that when you specify this keyword, the function never returns NA.) |

OWNER owner
The owner of the cube or cube dimension identified by top-level-object. If you do not include this clause, the function uses the current owner.

top-level-object
A text expression that specifies the name of the cube or the cube dimension for which information is requested.

sub-object
A text expression that specifies the name of the "logical" OLAP sub-object, if any, for which information is requested. Valid values vary depending on whether the top-level-object is a cube or a cube dimension:

- When top-level-object is a cube, you can specify the name of a measure or dimensionality

- When top-level-object is a cube dimension, you can specify the name of a base attribute, hierarchy, dimension level, or dimension calculation model.

#### Examples

Examples of using OBJORG with various keyword appear in several sample OLAP DML programs described within this manual:

- For examples of using OBJORG with the Dim keyword, see the following sample OLAP DML programs:

  - ADD_L1_2 program in [Example 9-5](olap-dml-commands-a-g.md)

  - REMOVE_L2_1 program in [Example 10-98](olap-dml-commands-h-z.md)

  - SETUP_PRE_MODEL and SETUP_POST_MODEL programs in [Example 10-118](olap-dml-commands-h-z.md)

  - ADD_L1_2_DATES program in [Example 10-169](olap-dml-commands-h-z.md)

- For an example of using OBJORG with the Measure keyword, see the ADD_L1_2 program in [Example 9-5](olap-dml-commands-a-g.md).

- For an example of using OBJORG with the Parentrel keyword, see the REMOVE_L2-1 program in [Example 10-98](olap-dml-commands-h-z.md).

- For examples of using OBJORG with the Attribute keyword, see the following sample programs:

  - SETUP_POST_MODEL program in [Example 10-118](olap-dml-commands-h-z.md)

  - ADD_L1_2_DATES program in [Example 10-169](olap-dml-commands-h-z.md)

### 8.56 OBSCURE

The OBSCURE function provides two mechanisms for encoding a single-line text expression. Depending on the mechanism you use, OBSCURE can also restore the encoded value to its original form.

**Note:**

This function performs simple encoding. For information on using secure encryption and other security features in Oracle, see [About Oracle Database Security](../dbseg/introduction-to-oracle-database-security.md) in Oracle Database Security Guide.

#### Return Value

TEXT

**Note:**

The return value of the OBSCURE function always has a text data type. However, unless you specify the TEXT keyword, the actual value returned by `OBSCURE(HASH)` and `OBSCURE(HIDE)` is binary. When you want to be able to manage these encoded values as text (for example, when you want to be able to store them in a text file), you must specify the TEXT keyword. See Example 8-59.

#### Syntax

OBSCURE({HASH\|HIDE\|UNHIDE} \[TEXT\] seed-exp input-exp)

#### Parameters

HASH
Specifies that Oracle OLAP encodes the input text expression according to the seed expression that you specify. With the HASH keyword:

- Encoded values cannot be restored to their original form.

- The same seed expression and input text always produce the same result.

HIDE
Specifies that Oracle OLAP encodes the input text expression according to the seed expression that you specify. With the HIDE keyword:

- Encoded values can be un-encoded to their original form with UNHIDE.

- The same seed expression and input text always produce different results.

The HIDE keyword provides a mechanism for storing values in encoded form while actually comparing their un-encoded values.

UNHIDE
When specified with the original seed expression, decodes values encoded with the HIDE keyword to their original form. See "Decoding Text".

TEXT
The TEXT keyword causes OBSCURE to convert binary data to text, such that the return value consists only of text data. When you do not specify the TEXT keyword, the output of OBSCURE is binary data. See "Decoding Text", and "Example 8-59".

seed-exp
A single-line case-sensitive text expression that is used as a seed value when encoding of the input text expression.

input-exp
A single-line case-sensitive text expression to be encoded or decoded by OBSCURE.

#### Usage Notes

Decoding Text

When you have used OBSCURE(HIDE) with the TEXT keyword to encode a text expression, you must also specify the TEXT keyword with `OBSCURE(UNHIDE)` to decoded expression to its original value.

#### Examples

Example 8-59 Generating Text Data

The following statements illustrate the use of the TEXT keyword.

    DEFINE encoded_text VARIABLE TEXT
    DEFINE unencoded_text VARIABLE TEXT
     
    unencoded_text = 'max'
    encoded_text = OBSCURE(HIDE TEXT 'XXXX' unencoded_text)
    SHOW encoded_text

This SHOW statement generates the following output.

    c5WF/XfABuY

The same statements without the TEXT keyword would produce binary output from the SHOW statement.

### 8.57 ORA_HASH

The ORA_HASH function computes a hash value for a given expression. This function is useful for operations such as analyzing a subset of data and generating a random sample.

#### Return Value

NUMBER

#### Syntax

ORA_HASH (expr \[, max_bucket \[, seed_value \] \])

#### Parameters

expr
The data for which you want the function to compute a hash value. There are no restrictions on the type or length of data represented by expr.

max_bucket
The maximum bucket value returned by the function. You can specify any value between 0 and 4294967295. The default is 4294967295.

seed_value
A value between 0 and 4294967295. The default is 0. When you want to produce different has values for the same set of data, specify a value for this argument.

### 8.58 PARTITION

The PARTITION function returns the name of the partition in which a value is stored.

#### Return Value

Text

#### Syntax

PARTITION (partition_template_values)

#### Parameters

partition_template_values
An expression that represents one or more values of the partition template (for example, the name of a partition template or a QDR).

#### Examples

Example 8-60 Retrieving the Name of a Partition

Assume that you have defined the following objects.

    DEFINE time DIMENSION TEXT
    DEFINE product DIMENSION TEXT
    DEFINE time_parentrel RELATION time <time>
    DEFINE partition_sales_by_year PARTITION TEMPLATE <time product> -
    PARTITION BY LIST (time)(PARTITION time_2003 VALUES -
    ('2003','Dec2003', 'Jan2003','31Dec2003','01Dec2003','31Jan2003','01Jan2003')-
    <time product> PARTITION time_2002 VALUES -
    ('2002', 'Dec2002', 'Jan2002', '31Dec2002', '01Dec2002','31Jan2002','01Jan2002')-
     <time product>)
    DEFINE sales DECIMAL <partition_sales_by_year<time product>>

Assume that these object have the values shown in the following report.

    REPORT DOWN PARTITION(partition_sales_by_year) time product sales

    PARTITION(PART
    ITION_SALES_BY
    _YEAR)            TIME     PRODUCT     SALES
    -------------- ---------- ---------- ----------
    TIME_2003      2003       00001              NA
    TIME_2003      Dec2003    00001              NA
    TIME_2003      Jan2003    00001              NA
    TIME_2003      31Dec2003  00001           14.78
    TIME_2003      01Dec2003  00001           15.52
    TIME_2003      31Jan2003  00001           13.61
    TIME_2003      01Jan2003  00001           10.39
    TIME_2003      2003       00002              NA
    TIME_2003      Dec2003    00002              NA
    TIME_2003      Jan2003    00002              NA
    TIME_2003      31Dec2003  00002           16.05
    TIME_2003      01Dec2003  00002           12.27
    TIME_2003      31Jan2003  00002           10.83
    TIME_2003      01Jan2003  00002           11.07
    TIME_2002      2002       00001              NA
    TIME_2002      Dec2002    00001              NA
    TIME_2002      Jan2002    00001              NA
    TIME_2002      31Dec2002  00001           18.80
    TIME_2002      01Dec2002  00001           13.64
    TIME_2002      31Jan2002  00001           12.41
    TIME_2002      01Jan2002  00001           16.97
    TIME_2002      2002       00002              NA
    TIME_2002      Dec2002    00002              NA
    TIME_2002      Jan2002    00002              NA
    TIME_2002      31Dec2002  00002           17.47
    TIME_2002      01Dec2002  00002           16.58
    TIME_2002      31Jan2002  00002           18.94
    TIME_2002      01Jan2002  00002           18.36


As shown in the following code, you can use the PARTITION function to retrieve the names of the partition in which a value is stored.

    SHOW partition_sales_by_year
    <2003, 00001>

    " Use a QDR to identify the partition of a specific time value
    SHOW PARTITION(partition_sales_by_year (time '31Jan2002'))
    TIME_2002

    REPORT DOWN time PARTITION(partition_sales_by_year)

                   PARTITION(PARTITION_S
                   ----ALES_BY_YEAR)----
                   -------PRODUCT-------
    TIME             00001      00002
    -------------- ---------- ----------
    2003           TIME_2003  TIME_2003
    2002           TIME_2002  TIME_2002
    Dec2003        TIME_2003  TIME_2003
    Jan2003        TIME_2003  TIME_2003
    Dec2002        TIME_2002  TIME_2002
    Jan2002        TIME_2002  TIME_2002
    31Dec2003      TIME_2003  TIME_2003
    01Dec2003      TIME_2003  TIME_2003
    31Jan2003      TIME_2003  TIME_2003
    01Jan2003      TIME_2003  TIME_2003
    31Dec2002      TIME_2002  TIME_2002
    01Dec2002      TIME_2002  TIME_2002
    31Jan2002      TIME_2002  TIME_2002
    01Jan2002      TIME_2002  TIME_2002

### 8.59 PARTITIONCHECK

The PARTITIONCHECK function identifies whether an aggmap object is compatible with the partitioning specified by a partition template object.

Aggregation can cross partitions; however, the data flow must always be in one direction. The data cannot go both in and out of the same partition; this processing causes Oracle OLAP to produce an error during the aggregation.

#### Return Value

`BOOLEAN`.

YE`S` when Oracle OLAP would not issue an error when aggregating a variable partitioned using the specified partition template using the specified aggmap; or `NO` when an error would occur.

#### Syntax

PARITITONCHECK (aggmap parttition-template)

#### Parameters

aggmap
A text expression that is the name of an aggmap object.

partition-template
A text expression that is the name of the partition template object to check for compatibility with aggregation.

### 8.60 PERCENTAGE

The PERCENTAGE function computes the percent of total for each value in a numeric expression.

#### Return Value

DECIMAL

#### Syntax

PERCENTAGE(expression \[CACHE\] \[BASEDON dimension-list\])

#### Parameters

expression
The numeric expression for which percent figures are to be computed.

CACHE
Specifies slightly different internal behavior. Specify this keyword only when the original performance is extremely slow.

BASEDON dimension-list
An optional list of one or more of the dimensions of expression on which to base the percentage for each value. When you do not specify the dimensions, then PERCENTAGE bases the percentage on the total of all of the values of all of the dimensions of expression.

#### Usage Notes

The Effect of NASKIP on PERCENTAGE

PERCENTAGE is affected by the NASKIP option. When NASKIP is set to `YES` (the default), then PERCENTAGE ignores `NA` values. When NASKIP is set to `NO`, then PERCENTAGE returns `NA` for any cell in expression whose value is `NA`.

#### Examples

Example 8-61 Calculating the Percentage

The following statements s limit the `month` and `district` dimensions, and report the data values, with subtotals, for the `units` variable.

    LIMIT month TO 'Jul96' TO 'Sep96'
    LIMIT district TO 'Denver'
    REPORT SUBTOTALS W 8 units

The preceding statement produces the following output.

    DISTRICT: DENVER
                   ----------UNITS-----------
                   ----------MONTH-----------
    PRODUCT         Jul96    Aug96    Sep96
    -------------- -------- -------- --------
    Tents               608      517      441
    Canoes              467      363      411
    Racquets          3,006    2,836    2,838
    Sportswear        2,395    2,039    2,138
    Footwear          1,581    1,532    1,667
    -------------- -------- -------- --------
    TOTAL DENVER      8,057    7,287    7,495

This statement reports the percentage that each `month` value represents of the total `month` values for each of the `product` values that are in status. The total of the values that PERCENTAGE returns for each `product` value is `1`.

    REPORT SUBTOTALS W 8 DOWN month PERCENTAGE(units BASEDON month)

    DISTRICT: DENVER
             -----------PERCENTAGE(UNITS BASEDON MONTH)------------
             -----------------------PRODUCT------------------------
    MONTH      Tents      Canoes    Racquets  Sportswear  Footwear
    -------- ---------- ---------- ---------- ---------- ----------
    Jul96          0.39       0.38       0.35       0.36       0.33
    Aug96          0.33       0.29       0.33       0.31       0.32
    Sep96          0.28       0.33       0.33       0.33       0.35
    -------- ---------- ---------- ---------- ---------- ----------
    TOTAL          1.00       1.00       1.00       1.00       1.00
    DENVER

This statement reports the percentage that each `product` value represents of the total `product` values for each of the `month` values that are in status.

    REPORT SUBTOTALS W 8 PERCENTAGE(units BASEDON product)

    DISTRICT: DENVER
                   -PERCENTAGE(UNITS BASEDON-
                   ---------PRODUCT)---------
                   ----------MONTH-----------
    PRODUCT         Jul96    Aug96    Sep96
    -------------- -------- -------- --------
    Tents              0.08     0.07     0.06
    Canoes             0.06     0.05     0.05
    Racquets           0.37     0.39     0.38
    Sportswear         0.30     0.28     0.29
    Footwear           0.20     0.21     0.22
    -------------- -------- -------- --------
    TOTAL DENVER       1.00     1.00     1.00

This statement reports the percentage based on all of the dimensions of the `units` variable. The total of all of the values that PERCENTAGE returns is `1`.

    REPORT SUBTOTALS W 8 PERCENTAGE(units)

    DISTRICT: DENVER
                   ----PERCENTAGE(UNITS)-----
                   ----------MONTH-----------
    PRODUCT         Jul96    Aug96    Sep96
    -------------- -------- -------- --------
    Tents              0.03     0.02     0.02
    Canoes             0.02     0.02     0.02
    Racquets           0.13     0.12     0.12
    Sportswear         0.10     0.09     0.09
    Footwear           0.07     0.07     0.07
    -------------- -------- -------- --------
    TOTAL DENVER       0.35     0.32     0.33

The total for all of the values for both the `product` and `month` dimensions is `1.00`.

### 8.61 QUAL

The QUAL function lets you explicitly specify a qualified data reference (QDR). Use QUAL in cases where the syntax of a QDR is ambiguous and could either be misinterpreted by Oracle OLAP or cause a syntax error.

QDRs provide a mechanism for limiting one or more dimensions of an expression to a single value. QDRs are useful when you want to temporarily reference a value that is not in the current status.

#### Return Value

The value that is returned has the same data type as the expression being qualified.

#### Syntax

QUAL(expression, dimname1 dimexp1 \[, dimnameN dimexpN\])

#### Parameters

expression
The expression being qualified. Use QUAL to qualify complex expressions that contain computation, function calls, or ampersand substitution. You can also use QUAL when the expression is a simple variable name. However, QUAL is not required for simple expressions, and you can use the following standard QDR syntax.

expression(dimname1 dimexp1 \[, dimname2 dimexp2 ...\])

dimname
The dimension to be limited. You can specify one or more of the dimensions of the expression. Each dimension must be paired with a dimexp. You can specify a dimension surrogate instead of the dimension.

dimexp
An expression that represents the value to which the dimension should be limited. The expression can be a value of the dimension, a text expression whose result is a value of the dimension, a numeric expression whose result is the logical position of a value of the dimension, or a relation of the dimension.

When the dimension being limited is a conjoint dimension, then dimexp must be enclosed in angle brackets and must include a value for each of its base dimensions.

When the dimension being limited is a concat dimension, then dimname and dimexp can be one combination listed in the following table:

Table 8-10 Valid dimname and dimexp Combinations for Concat Dimensions

| dimname                                              | dimexp                           |
|:-----------------------------------------------------|:---------------------------------|
| The name of the concat dimension                     | A value of the concat dimension  |
| The name of the concat dimension                     | The name of a base dimension     |
| The name of a base dimension of the concat dimension | A value of the base dimension    |
| The name of a base dimension of the concat dimension | The name of the concat dimension |

#### Examples

Example 8-62 Using QUAL with MAX

The following example first shows how you might view your data by limiting its dimensions, and then how you might view it by using QUAL.

Assume that you issue the following OLAP DML statements to limit the view of the Cogs line data in the Sporting division to January 1996 through June 1996, and, then, report by month on the maximum value of actual costs or budgeted costs or MAX(actual,budget), actual costs, and budgeted costs for each month.

    LIMIT month TO 'Jan96' TO 'Jun96'
    LIMIT line TO 'Cogs'
    LIMIT division TO 'Sporting'
    REPORT DOWN month W 11 MAX(actual,budget) W 11 actual W 11 budget

The preceding statements produce the following report.

    DIVISION: SPORTING
                   ---------------LINE----------------
                   ---------------COGS----------------
                   MAX(ACTUAL,
    MONTH            BUDGET)     ACTUAL      BUDGET
    -------------- ----------- ----------- -----------
    Jan96           287,557.87  287,557.87  279,773.01
    Feb96           323,981.56  315,298.82  323,981.56
    Mar96           326,184.87  326,184.87  302,177.88
    Apr96           394,544.27  394,544.27  386,100.82
    May96           449,862.25  449,862.25  433,997.89
    Jun96           457,347.55  457,347.55  448,042.45

Now consider how you might view the same figures for `MAX(actual,budget)` without changing the status of `line` or `division`.

    ALLSTAT
    LIMIT month TO 'Jan96' TO 'Jun96'
    REPORT HEADING 'For Cogs in Sporting Division' DOWN month -
       W 11 HEADING 'MAX(actual,budget)'-
       QUAL(MAX(actual,budget), line 'Cogs', division 'Sporting')

    For Cogs in
    Sporting       MAX(actual,
    Division         budget)
    -------------- -----------
    Jan96           287,557.87
    Feb96           323,981.56
    Mar96           326,184.87
    Apr96           394,544.27
    May96           449,862.25
    Jun96           457,347.55

When you attempt to produce the same report with standard QDR syntax, Oracle OLAP signals an error.

    REPORT HEADING 'For Cogs in Sporting Division' DOWN month -
       W 11 HEADING 'MAX(actual,budget)'-
       MAX(actual,budget) (line cogs, division sporting)

The following error message is produced.

    ERROR: A right parenthesis or an operator is expected after LINE.

Example 8-63 Using QUAL with a Concat Dimension

The following example shows two ways of limiting the values of a concat dimension in a QUAL function. The `reg.dist.ccdim` concat dimension has `region` and `district` as its base dimensions. The `rdsales` variable is dimensioned by `month`, `product`, and `reg.dist.ccdim`.

    LIMIT month TO 'Jan96' TO 'Jun96'
    LIMIT product TO 'Tents' 'Canoes'
     
    " Limit the concat by specifying one of its component dimensions
    REPORT W 30 QUAL(rdsales * 2, month 'Feb96', district 'Boston')

These statements produce the following report.

                     QUAL(RDSALES * 2, MONTH
    PRODUCT          'Feb96', DISTRICT 'Boston')
    -------------- ------------------------------
    Tents                               69,283.18
    Canoes                             164,475.36
     
    " Limit the concat by specifying one of its values
    REPORT W 30 QUAL(rdsales * 2, month 'Mar96', reg.dist.ccdim  '<district: Boston>')
     
                      QUAL(RDSALES * 2, MONTH
                      'Mar96', REG.DIST.CCDIM
    PRODUCT            '<district: Boston>')
    -------------- ------------------------------
    TENTS                               91,484.42
    CANOES                             195,244.56

### 8.62 RANDOM

The RANDOM function produces a number that is randomly distributed between specified low and high boundaries. Randomly generated numbers are useful when building and duplicating tests of applications. They are especially useful for simulation and forecasting applications.

**Tip:**

To compute the number, RANDOM uses the values of the [RANDOM.SEED.1 and RANDOM.SEED.2](olap-dml-options.md) options and then changes the values for the next time. When you create your own seeds, set the value of both options to odd numbers. This practice enhances the randomness of the numbers that are produced.

#### Return Value

DECIMAL

#### Syntax

RANDOM(\[lowbound\] \[highbound\])

#### Parameters

lowbound
A numeric expression that specifies the lower boundary for the random number series. The default is `0`. When lowbound is `NA`, the RANDOM function produces `NA`.

highbound
A numeric expression that specifies the upper boundary for the random number series. The default is `1`. When highbound is `NA`, the RANDOM function produces `NA`

#### Examples

Example 8-64 Producing Random Numbers

This example assigns random numbers between 100 and 200 to a variable called `test`, which is dimensioned by `product`.

    test = RANDOM(100 200)
    REPORT test

These statements produce a report such as the following.

    PRODUCT           TEST
    -------------- ----------
    Tents              122.93
    Canoes             176.69
    Racquets           168.32
    Sportswear         150.92
    Footwear           187.46

### 8.63 RANK

The RANK function computes the rank of values in a numeric expression.

#### Return Value

DECIMAL

#### Syntax

RANK(expression method \[attributes\] \[BASEDON dimension-list\])

where `attributes` is one or more of the following:

- `RESET`
- `NAFIRST`
- `NALAST`
- `LIMITSAVE (``limit-expression``...)`
- `TIEBREAKERS (``target-expression``...)`

#### Parameters

expression
The numeric expression for which rankings are to be computed.

method
The method to use in computing the rank of the values in expression. The method argument can be one of the following keywords. See also "Results of Method Values".

Table 8-11 Methods for Computing RANK

| Method     | Description                                                                                             |
|:-----------|:--------------------------------------------------------------------------------------------------------|
| MIN        | Identical values get the same minimum rank.                                                             |
| MAX        | Identical values get the same maximum rank.                                                             |
| AVERAGE    | Identical values get the same average rank.                                                             |
| PACKED     | Identical values get the same rank but the results are packed into consecutive `INTEGER` values.        |
| UNIQUE     | All values get a unique rank; for identical values the rank is arbitrary.                               |
| PERCENTILE | Values are ranked from 1 to 100, based on the relative frequency of their occurrence in the expression. |
| DECILE     | Values are ranked from 1 to 10, based on the relative frequency of their occurrence in the expression.  |
| QUARTILE   | Values are ranked from 1 to 4, based on the relative frequency of their occurrence in the expression.   |

RESET
Changes how Oracle OLAP computes RANK within a looping statement (for example, an assignment statement):

- When you do not specify RESET, Oracle OLAP ranks the members of each group only once and, then caches those ranked values. As the looping statement continues to execute and RANK executes against same set of values, Oracle OLAP uses those cached values to return values for RANK.

- When you include RESET, Oracle OLAP recomputes RANK each and every time it executes within the looping statement. This behavior significantly increases the time it takes for Oracle OLAP to execute the looping statement that contains RANK.

Within a looping statement, the only time you use RANK with RESET is when you know that within any group the rankings of members within that group will change during the execution of the looping statement.

NAFIRST
Specifies that Oracle OLAP converts all NA values to the largest positive decimal number or `(10**308)` before ranking the values.

**Note:**

An NA expression value produces an NA rank unless you specify either NAFIRST or NALIST.

NALAST
Specifies that Oracle OLAP converts all NA values to the largest negative decimal number or `-(10**308)` before ranking the values.

**Note:**

An NA expression value produces an NA rank unless you specify either NAFIRST or NALIST.

LIMITSAVE
Specifies the status of the dimensions that Oracle OLAP uses when calculating RANK. By specifying LIMITSAVE within the RANK function, rather than specify CHGDIMS with LIMITSAVE, you insure that Oracle OLAP evaluates the status only once when RANK needs to calculate a new result.

limit-expression
The dimension values that Oracle OLAP uses to determine dimension status while executing RANK. For the limit-expression argument, you can specify any expression including a valueset, a LIMIT function, or a SORT function.

TIEBREAKERS
Specifies how Oracle OLAP sequences values of equal rank.

tiebreaker-expression
Any expression including a valueset, a LIMIT function, or a SORT function. Oracle OLAP executes the tiebreaker-expressions in the order in which they are specified. The status of the dimensions of each tiebreaker-expression is the current status of the dimensions or the status specified in the LIMITSAVE clause, if any.

**Note:**

When you specify a valueset for tiebreaker-expression, Oracle OLAP returns the ranked items in -(STATRANK) order.

BASEDON dimension-list
An optional list of one or more of the dimensions of expression to include in the ranking. When you do not specify the dimensions, then RANK bases the ranking on all of the dimensions of expression.

**Note:**

When the current value of a BASEDON dimension is not in ranking status, Oracle OLAP returns a rank of `NA`.

#### Usage Notes

Monitoring the Behavior of RANK

The OLAP DML provides the RANK_CALLS, RANK_CELLS, and RANK_SORTS options that you can use to monitor the behavior of the RANK function.

RANK_CALLS

The RANK_CALLS option is an `INTEGER`, read-only option that holds the number of calls that Oracle OLAP has made to the RANK function.

RANK_CELLS

The RANK_CELLS option is an `INTEGER`, read-only option that holds the number of values that Oracle OLAP has computed when executing the RANK function.

RANK_SORTS

The RANK_SORTS option is a read-only option that holds the number of sorts that have been triggered by the execution of the RANK function

Results of Method Values

This note describes the results of the different methods of ranking values. The results are based on the `sales2` variable, which is described in "Example 8-65", with the `geography` dimension limited to `G2` as the following statements demonstrate.

    LIMIT geography TO 'G2'
    SORT items D sales2
    REPORT DOWN geography sales2

The preceding statements produce the following output.

                   ------------------------SALES2------------------------
                   ------------------------ITEMS-------------------------
    GEOGRAPHY        ITEM4      ITEM2      ITEM3      ITEM1      ITEM5
    -------------- ---------- ---------- ---------- ---------- ----------
    G2                  25.00      20.00      20.00      15.00       7.00

The following table shows the results of the different methods of ranking that are produced by a statement of the form

    REPORT DOWN geography RANK(sales2 MIN BASEDON items)

with the different method keywords substituted for MIN.

Table 8-12 Results of Different Methods of Ranking

| Methods    | (ITEM4, G2) = 25 | (ITEM2, G2) = 20 | (ITEM3, G2) = 20 | (ITEM1,G2) = 15 | (ITEM5,G2) = 7 |
|:-----------|:-----------------|:-----------------|:-----------------|:----------------|:---------------|
| MIN        |    1             |  2               |  2               |  4              |  5             |
| MAX        |    1             |  3               |  3               |  4              |  5             |
| AVERAGE    |    1             |  2.5             |  2.5             |  4              |  5             |
| PACKED     |    1             |  2               |  2               |  3              |  4             |
| UNIQUE     |    1             |  2               |  3               |  4              |  5             |
| PERCENTILE | 100              | 62               | 62               | 25              |  1             |
| DECILE     |  10              |  7               |  7               |  3              |  1             |
| QUARTILE   |   4              |  3               |  3               |  1              |  1             |

Note that the value that is returned by the UNIQUE method for `Item2` and `Item3` can be either `2` or `3`, because the RANK function randomly assigns a unique rank for identical values in the expression.

#### Examples

Example 8-65 Ranking Values

Assume that your analytic workspace contains `geography` and `items` dimensions and `sales2` variable.

    DEFINE geography DIMENSION TEXT 
    MAINTAIN geography ADD 'g1' 'g2' 'g3'
    DEFINE items DIMENSION TEXT
    MAINTAIN items ADD 'Item1' 'Item2' 'Item3' 'Item4' 'Item5'
    DEFINE sales2 DECIMAL <geography items>

Assume the `sales2` variable has the following data values.

                   -------------SALES2-------------
                   -----------GEOGRAPHY------------
    ITEMS              g1         g2         g3
    -------------- ---------- ---------- ----------
    Item1               30.00      15.00      12.00
    Item2               10.00      20.00      18.00
    Item3               15.00      20.00      24.00
    Item4               30.00      25.00      25.00
    Item5                  NA       7.00      21.00

This statement reports the results of using the MIN method to rank the `sales2` values based on the `items` dimension.

    report rank(sales2 min basedon items)

The preceding statement produces the following output.

                   -RANK(SALES2 MIN BASEDON ITEMS)-
                   -----------GEOGRAPHY------------
    ITEMS              g1         g2         g3
    -------------- ---------- ---------- ----------
    Item1                1.00       4.00       5.00
    Item2                4.00       2.00       4.00
    Item3                3.00       2.00       2.00
    Item4                1.00       1.00       1.00
    Item5                  NA       5.00       3.00

This statement reports the results of using the MIN method to rank the `sales2` values based on the geography dimension.

    REPORT RANK(sales2 MIN BASEDON geography)

The preceding statement produces the following output.

                   ----RANK(SALES2 MIN BASEDON-----
                   -----------GEOGRAPHY)-----------
                   -----------GEOGRAPHY------------
    ITEMS              g1         g2         g3
    -------------- ---------- ---------- ----------
    Item1                1.00       2.00       3.00
    Item2                3.00       1.00       2.00
    Item3                3.00       2.00       1.00
    Item4                1.00       2.00       2.00
    Item5                  NA       2.00       1.00

This statement reports the results of using the MIN method to rank the `sales2` values based on all of its dimensions.

    REPORT RANK(sales2, MIN)

The preceding statement produces the following output.

                   -------RANK(SALES2, MIN)--------
                   -----------GEOGRAPHY------------
    ITEMS              g1         g2         g3
    -------------- ---------- ---------- ----------
    Item1                1.00      10.00      12.00
    Item2               13.00       7.00       9.00
    Item3               10.00       7.00       5.00
    Item4                1.00       3.00       3.00
    Item5                  NA      14.00       6.00

### 8.64 RAWTOHEX

The RAWTOHEX function converts a raw value to a character string of hexadecimal digits.

**See Also:**

"[RAW Data Type](data-types-operators-and-expressions.md)" and the [HEXTORAW](olap-dml-functions-a-k.md) function

#### Returns

TEXT

#### Syntax

RAWTOHEX(raw-exp)

#### Parameters

raw-exp
A raw expression.

### 8.65 RECNO

The RECNO function reports the current record number of a file opened for reading. It returns `NA` when Oracle OLAP has reached the end of the file.

#### Return Value

INTEGER

#### Syntax

RECNO(fileunit)

#### Parameters

fileunit
A file unit number assigned to a file opened for reading in a previous call to the FILEOPEN function.

#### Usage Notes

Opening Files

Before you can use the RECNO function, you must open the file for reading. When the file unit number is not associated with an open file or the file has been opened for writing, RECNO returns an error.

Using RECNO with FILEGET

RECNO is usually used with FILEREAD or FILENEXT, which read whole records. When you are reading data from a file with the FILEGET function, which can read partial records, RECNO returns the number of times you have read data from the file, not the number of actual records.

LINENUM Option

See also the [LINENUM](olap-dml-options.md) option, which holds the current line number of output.

Records in Text Files

When the file is a text file, a record is delimited by a newline character. When the file is a binary file, you must set the file's LSIZE attribute to the record length with a FILESET statement. TEXT is the default file type.

#### Examples

Example 8-66 Using RECNO with FILEREAD

In the following example code, a FILEREAD statement maintains the INTEGER dimension, adding each record number associated with `filename.` The text associated with each record number becomes each value of the variable `textvar`.

    DEFINE dim1 INTEGER DIMENSION
    DEFINE textvar TEXT <dim1>
    x = FILEOPEN('filename' R)
    FILEREAD x APPEND dim1 = RECNO(x) W 8 TEXTVAR

### 8.66 REGEXP_COUNT

The REGEXP_COUNT function returns the number of times a pattern occurs in a source string. The function evaluates strings using characters as defined by the input character set.

**See Also:**

REGEXP_INSTR

#### Return value

When a match is found, an INTEGER that indicates the number of occurrences of the pattern; otherwise 0.

#### Syntax

REGEXP_COUNT (source_char, pattern \[, position \[, match_param\]\])

#### Parameters

source_char
The text expression for which the function searches.

pattern
The text expression for which the function searches. It is usually a text literal and can contain up to 512 bytes. If the data type of pattern is different from the data type of source_char, then the function converts pattern to the data type of source_char.

Note that the function ignores subexpression parentheses in pattern. For example, the pattern '(123(45))' is equivalent to '12345'. Also, the function interprets a period as a wildcard character that matches any character.

**See:**

For a listing of the operators you can specify in pattern, see "Oracle Regular Expression Support" in Oracle Database SQL Language Reference.

**See Also:**

"Oracle Regular Expression Support" in [Oracle Database SQL Language Reference](../sqlrf/Oracle-Regular-Expression-Support.md) for a listing of the operators that you can specify in pattern

position
A positive INTEGER indicating the character of source_char where the function should begin the search. The default is 1, meaning that the function begins the search at the first character of source_char. After finding the first occurrence of pattern, the function searches for a second occurrence beginning with the first character following the first occurrence.

match_parameter
A text expression that lets you change the default matching behavior of the function. You can specify one or more of the values shown in the following table.

| Value | Specifies                                                                                                                                                                                                                                                                                                                  |
|:------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `c`   | Case-sensitive matching.                                                                                                                                                                                                                                                                                                   |
| `i`   | Case-insensitive matching.                                                                                                                                                                                                                                                                                                 |
| `m`   | Treat the source string as multiple lines. The function interprets ` ^` (caret) and `$` (dollar sign) as the start and end, respectively, of any line anywhere in the source string, rather than only at the start or end of the entire source string. By default, the function treats the source string as a single line. |
| `n`   | A newline character is among the characters matched by a period (the wildcard character). By default, it is not.                                                                                                                                                                                                           |
| `x`   | Ignores whitespace characters.                                                                                                                                                                                                                                                                                             |

If you specify multiple contradictory values for this argument, then the function uses the last value. For example, if you specify 'ic', then the function uses case-sensitive matching. If you specify a character other than those shown above, then the function returns an error.

If you omit this optional argument, then the default case sensitivity is determined by the value of the NLS_SORT parameter; a period (.) does not match the newline character; and the source string is treated as a single line.

### 8.67 REGEXP_INSTR

The REGEXP_INSTR function searches a string for a substring with a specified pattern and returns the position of that substring.

The function evaluates strings using characters as defined by the input character set.

**See Also:**

REGEXP_COUNT, REGEXP_REPLACE, and REGEXP_SUBSTR

#### Return Value

When the pattern is found a NUMBER; otherwise 0.

#### Syntax

REGEXP_INSTR (source_char, pattern\[, position\[, occurrence\[, return_option\[, match_parameter \]\]\]\])

#### Parameters

source_char
The text expression for which the function searches.

pattern
The text expression for which the function searches. It is usually a text literal and can contain up to 512 bytes. The function interprets a period as a wildcard character that matches any character.

position
A positive integer that indicates the character of source_char at which the function begins the search. The default value of position is `1`, which means that the function begins searching at the first character of source_char.

occurrence
A positive integer that indicates which occurrence of pattern the function should search for. The default value of occurrence is `1`, meaning that the function searches for the first occurrence of pattern.

return_option
Specify `0` (zero) when you want the function to return the position of the first matched character (default), or `1` when you want the function to return the position of the character following the match.

match_parameter
A text expression that lets you change the default matching behavior of the function. You can specify one or more of the values shown in the following table.

| Value | Specifies                                                                                                                                                                                                                                                                                                                  |
|:------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `c`   | Case-sensitive matching.                                                                                                                                                                                                                                                                                                   |
| `i`   | Case-insensitive matching.                                                                                                                                                                                                                                                                                                 |
| `m`   | Treat the source string as multiple lines. The function interprets ` ^` (caret) and `$` (dollar sign) as the start and end, respectively, of any line anywhere in the source string, rather than only at the start or end of the entire source string. By default, the function treats the source string as a single line. |
| `n`   | A newline character is among the characters matched by a period (the wildcard character). By default, it is not.                                                                                                                                                                                                           |
| `x`   | Ignores whitespace characters.                                                                                                                                                                                                                                                                                             |

#### Examples

The following statement

    REGEXP_INSTR('Mississippi', 'i', 1, 3)

searches the string Mississippi for the third instance of the letter i, beginning the search at the first letter. It returns the value 8.

### 8.68 REGEXP_REPLACE

The REGEXP_REPLACE function searches a string for a substring with a specified pattern and replaces that substring with another substring.

**See Also:**

REGEXP_COUNT, REGEXP_INSTR, and REGEXP_SUBSTR

#### Return Value

`VARCHAR2`

#### Syntax

REGEXP_REPLACE(source_char, pattern\[, replace_string\[, position\[, occurrence\[, match_parameter \]\]\]\])

#### Parameters

source_char
The text expression for which the function searches.

pattern
The text expression for which the function searches. It is usually a text literal and can contain up to 512 bytes. The function interprets a period as a wildcard character that matches any character.

replace_string
The text that replaces pattern in source_char.

position
A positive integer that indicates the character of source_char at which the function begins the search. The default value of position is `1`, which means that the function begins searching at the first character of source_char.

occurrence
A positive integer that indicates which occurrence of pattern the function should search for. The default values of occurrence is `1`, meaning that the function searches for the first occurrence of pattern.

match_parameter
A text expression that lets you change the default matching behavior of the function. You can specify one or more of the values shown in the following table.

| Value | Specifies                                                                                                                                                                                                                                                                                                                  |
|:------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `c`   | Case-sensitive matching.                                                                                                                                                                                                                                                                                                   |
| `i`   | Case-insensitive matching.                                                                                                                                                                                                                                                                                                 |
| `m`   | Treat the source string as multiple lines. The function interprets ` ^` (caret) and `$` (dollar sign) as the start and end, respectively, of any line anywhere in the source string, rather than only at the start or end of the entire source string. By default, the function treats the source string as a single line. |
| `n`   | A newline character is among the characters matched by a period (the wildcard character). By default, it is not.                                                                                                                                                                                                           |
| `x`   | Ignores whitespace characters.                                                                                                                                                                                                                                                                                             |

#### Example

The following statement

    REGEXP_REPLACE('500   Oracle     Parkway,    Redwood  Shores, CA', '( ){2,}', ' ')

eliminates extra spaces and returns the following string

    500 Oracle Parkway, Redwood Shores, CA

### 8.69 REGEXP_SUBSTR

The REGEXP_SUBSTR function searches a string for a substring of a specified pattern and returns that substring.

**See Also:**

REGEXP_COUNT, REGEXP_INSTR, and REGEXP_REPLACE

#### Return Value

`VARCHAR2` \| `CLOB`

#### Syntax

REGEXP_SUBSTR(source_char, pattern\[, position\[, occurrence\[, match_parameter \]\]\])

#### Parameters

source_char
The text expression for which the function searches.

pattern
The text expression for which the function searches. It is usually a text literal and can contain up to 512 bytes. The function interprets a period as a wildcard character that matches any character

position
A positive integer that indicates the character of source_char at which the function begins the search. The default value of position is `1`, which means that the function begins searching at the first character of source_char.

occurrence
A positive integer that indicates which occurrence of pattern the function should search for. The default value of occurrence is `1`, which means that the function searches for the first occurrence of pattern.

match_parameter
A text expression that lets you change the default matching behavior of the function. You can specify one or more of the values shown in the following table.

| Value | Specifies                                                                                                                                                                                                                                                                                                                  |
|:------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `c`   | Case-sensitive matching.                                                                                                                                                                                                                                                                                                   |
| `i`   | Case-insensitive matching.                                                                                                                                                                                                                                                                                                 |
| `m`   | Treat the source string as multiple lines. The function interprets ` ^` (caret) and `$` (dollar sign) as the start and end, respectively, of any line anywhere in the source string, rather than only at the start or end of the entire source string. By default, the function treats the source string as a single line. |
| `n`   | A newline character is among the characters matched by a period (the wildcard character). By default, it is not.                                                                                                                                                                                                           |
| `x`   | Ignores whitespace characters.                                                                                                                                                                                                                                                                                             |

#### Examples

Example 8-67 Using REGEXP_SUBSTRING to search for a case-insensitive substring

The following statement

    REGEXP_SUBSTR('7 W 96th St, New York, New York', 'new york', 10, 2, 'i')

starts searching at the tenth character and matches the second instance of New York in a case-insensitive match.

Example 8-68 Using REGEXP_SUBSTRING to return a substring from a string enclosed in single quotes

The following statement

    REGEXP_SUBSTR('parsley, sage, rosemary, thyme', ',[^,]+,', 1)

matches the first substring enclosed in single quotes (`'`), and returns the value, sage,.

### 8.70 REM

The REM function returns the remainder after one numeric expression is divided by another.

#### Return Value

DECIMAL

#### Syntax

REM(expression1 expression2)

#### Parameters

expression
REM returns the remainder of expression1 divided by expression2.

#### Examples

Example 8-69 Calculating a Remainder

This example illustrates the use of REM to find the remainder after `14` is divided by `5`. The statement

    SHOW REM(14 5)

produces the following result.

    4.00

### 8.71 REMAINDER

The REMAINDER function returns the remainder when one number is divided by another.

#### Return Values

Numeric. Oracle OLAP determines the argument with the highest numeric precedence, implicitly converts the remaining arguments to that data type, and returns that data type.

#### Syntax

REMAINDER (diviidend, divisor)

#### Parameters

dividend
A numeric expression (or an expression that Oracle OLAP can implicitly convert to a numeric expression) that is the number you want to divide.

divisor
A numeric expression (or an expression that Oracle OLAP can implicitly convert to a numeric expression) that is the divisor.

#### Examples

Example 8-70 Finding the Remainder After Division

    SHOW REMAINDER(18,7)
    -3.00

### 8.72 REMBYTES

The REMBYTES function removes one or more bytes from a text expression and returns the value that remains.

#### Return Value

TEXT

#### Syntax

REMBYTES(text-expression start \[length\])

#### Parameters

text-expression
The `TEXT` expression from which REMBYTES removes bytes. When the characters to be removed from text-expression contain embedded line breaks, these breaks are also removed. Other line breaks are preserved. Removed line breaks are not counted toward the total number of characters removed.

**Tip:**

When you must use this function on NTEXT values, use the CONVERT or TO_CHAR function to convert the NTEXT value to TEXT.

start
An `INTEGER` that represents the character position at which to begin removing characters. The position of the first character in text-expression is `1`. When the value of start is greater than the length of text-expression, REMBYTES simply returns text-expression.

length
An `INTEGER` that represents the number of characters to be removed. When length is not specified, only the character at start is removed.

#### Examples

Example 8-71 Using REMBYTES to Remove a Substring

This example shows how to remove the substring `there` from the text value `hellotherejoe`.

The statement

    SHOW REMBYTES('hellotherejoe', 6, 5)

produces the following output.

    hellojoe

### 8.73 REMCHARS

The REMCHARS function removes one or more characters from a text expression and returns the value that remains.

**Tip:**

When you are using a multibyte character set, you can use the REMBYTES function instead of the REMCHARS function.

#### Return Value

TEXT or NTEXT

#### Syntax

REMCHARS(text-expression start \[length\])

#### Parameters

text-expression
The expression from which REMCHARS removes characters. When the characters to remove from text-expression contain embedded line breaks, these breaks are also removed. Other line breaks are preserved. Removed line breaks are not counted toward the total number of characters removed.

When you specify a TEXT expression, the return value is TEXT. When you specify an NTEXT expression, the return value is NTEXT.

start
An `INTEGER` that represents the character position at which to begin removing characters. The position of the first character in text-expression is `1`. When the value of start is greater than the length of text-expression, REMCHARS simply returns text-expression.

length
An `INTEGER` that represents the number of characters to be removed. When length is not specified, only the character at start is removed.

#### Examples

Example 8-72 Using REMCHARS to Remove a Substring

This example shows how to remove the substring `there` from the text value `hellotherejoe`.

    SHOW REMCHARS('hellotherejoe', 6, 5)

    hellojoe

Example 8-73 Removing a Single Character

This example shows how to remove the character `t` from the text value `hellotherejoe`.

    SHOW REMCHARS('hellotherejoe', 6)

    helloherejoe

### 8.74 REMCOLS

The REMCOLS function removes specified columns from every line of a multiline TEXT value. The function returns a multiline text value that includes only the remaining columns.

Columns refer to the character positions in each line of a multiline TEXT value. The first character in each line is in column one, the second is in column two, and so on.

#### Return Value

TEXT or NTEXT

REMCOLS always returns a TEXT value that has the same number of lines as text-expression, though some lines may be empty.

#### Syntax

REMCOLS(text-expression start \[length\])

#### Parameters

text-expression
The text expression from which the specified columns should be removed. When text-expression is a multiline TEXT value, the characters in the specified columns are removed from each one of its lines.

When you specify a TEXT expression, the return value is TEXT. When you specify an NTEXT expression, the return value is NTEXT.

start
An `INTEGER`, between 1 and 32,767, representing the column position at which to begin removing columns. The column position of the first character in each line of text-expression is `1`. When you specify a starting column that is to the right of the last character in a given line in text expression, the corresponding line in the return value is identical to the given line.

length
An `INTEGER` representing the number of columns to be removed. When you do not specify length, REMCOLS removes only the starting column. When you specify a length that exceeds the number of characters that follow the starting position in a given line in text expression, the corresponding line in the return value includes only the characters that precede the starting column.

#### Examples

Example 8-74 Removing Text Columns

In the following example, four columns are removed from each line of CITYLIST, starting from the second column.

    DEFINE citylist VARIABLE TEXT
    CITYLIST = 'Boston\nHouston\nChicago\nDenver'

The statement

    SHOW citylist

produces the following output.

    Boston
    Houston
    Chicago
    Denver

The statement

    SHOW REMCOLS(citylist 2 4)

produces the following output.

    Bn
    Hon
    Cgo
    Dr

### 8.75 REMLINES

The REMLINES function removes one or more lines from a multiline TEXT expression and returns the value that remains.

#### Return Value

TEXT or NTEXT

#### Syntax

REMLINES(text-expression start \[length\])

#### Parameters

text-expression
A multiline text expression from whose values REMLINES removes one or more lines. When you specify a TEXT expression, the return value is TEXT. When you specify an NTEXT expression, the return value is NTEXT.

start
An `INTEGER` that represents the line number at which to begin removing lines. The position of the first line in text-expression is `1`.

length
An `INTEGER` that represents the number of lines to be extracted. When you do not specify length, only the line at start is removed.

#### Examples

Example 8-75 Removing Text Lines

This example shows how to remove the second line from a multiline text value in a variable called `mktglist` with the following values.

    Salespeople
    Products
    Services

The statement

    SHOW REMLINES(mktglist, 2)

produces the following output.

    Salespeople
    Services

### 8.76 REPLACE

The REPLACE function returns a specified character each time a specified string is replaced with another string; or removes all occurrences of a specified string.

REPLACE provides functionality related to that provided by the TRANSLATE function. TRANSLATE provides single-character, one-to-one substitution. REPLACE lets you substitute one string for another as well as to remove character strings.

**See Also:**

REPLACE function in [Oracle Database SQL Language Reference](../sqlrf/REPLACE.md) for more details

#### Return Value

The same data type as` char`.

#### Syntax

REPLACE ( char, search_string \[, replacement_string \])

#### Parameters

char
A text expression that is the character that you want returned when a replacement is made.

search_string
A text expression that is the string you want to replace. When you specify NA, then the function returns char.

replacement_string
A text expression that is the string with which you want to replace search_string. When you do not specify a value for this argument or when you specify the value of `NA`, all occurrences of search_string are removed.

### 8.77 REPLBYTES

The REPLBYTES function replaces one or more bytes in a text expression.

**Tip:**

When you are using a single-byte character set, you can use the REPLCHARS function instead of the REPLBYTES function. Also, to change one or more occurrences of a specified string in a text value to another string, use the CHANGECHARS function

#### Return Value

TEXT

#### Syntax

REPLBYTES(text-expression replacement \[start\])

#### Parameters

text-expression
A `TEXT` expression in which REPLBYTES replaces bytes. When the bytes to replace from text-expression contain embedded line breaks, these breaks are removed. Other line breaks are preserved. Removed line breaks are not counted toward the total number of bytes replaced. Line breaks in the replacement expression are retained in the output of REPLBYTES, but are likewise not counted.

**Tip:**

When you must use this function on `NTEXT` values, use the CONVERT or TO_CHAR function to convert the `NTEXT` value to `TEXT`.

replacement
A text expression that contains one or more bytes that replaces existing bytes in text-expression.

start
An `INTEGER` that represents the byte position at which to begin replacing bytes. The position of the first byte in text-expression is 1. When you omit this argument, REPLBYTES starts with the first byte. REPLBYTES replaces as many bytes of text-expression as are required for the bytes specified by replacement. When the value of start is greater than the length of text-expression, REPLBYTES simply returns text-expression.

#### Examples

Example 8-76 Replacing Text as Bytes

This example shows how to replace a portion of the text value `Hello there, Joe`.

The statement

    SHOW REPLBYTES('Hello there, Joe', 'Jane', 14)

produces the following output.

    Hello there, Jane

Example 8-77 How REPLBYTES Handles Line Breaks

This example shows how REPLBYTES preserves but ignores line breaks.

    var1 = JOINLINES('Hello' 'there' 'Joe')
    var2 = JOINLINES('Hi' 'Jane')

The statement

    SHOW REPLBYTES(var1 var2)

produces the following output.

    Hi
    Janehere
    Joe

REPLBYTES has replaced the first 6 bytes of `var1` (`Hellot` of `HellothereJoe`) with the 6 bytes of `var2` (`HiJane`). It has preserved the line breaks following `Hi` (from `var2`) and `there` (from `var1`).

To replace all 13 bytes in var1, you must specify 13 replacement bytes; for example, you can add 7 spaces after `Jane`.

    var2 = JOINLINES('Hi' 'Jane       ')

The statement

    SHOW REPLBYTES(var1 var2)

produces the following output.

    Hi
    Jane

### 8.78 REPLCHARS

The REPLCHARS function replaces one or more characters in a text expression.

**Tip:**

When you are using a multibyte character set, you can use the REPLBYTES function instead of the REPLCHARS function. Also, you can use the CHANGECHARS function to change one or more occurrences of a specified string in a text value to another string.

#### Return Value

TEXT or NTEXT

This function accepts TEXT values and NTEXT values as arguments. The data type of the return value depends on the data type of the values specified for the arguments:

- When all arguments are TEXT values, the return value is TEXT.

- When all arguments are NTEXT values, the return value is NTEXT.

- When the arguments include both TEXT and NTEXT values, the function converts all TEXT values to NTEXT before performing the function operation, and the return value is NTEXT.

#### Syntax

REPLCHARS(text-expression characters \[start\])

#### Parameters

text-expression
The expression in which characters are to be replaced. When the characters to be replaced from text-expression contain embedded line breaks, these breaks are removed. Other line breaks are preserved. Removed line breaks are not counted toward the total number of characters replaced. Line breaks in the replacement expression are retained in the output of REPLCHARS, but are likewise not counted.

characters
A text expression that contains one or more characters that replaces existing characters in text-expression.

start
An `INTEGER` that represents the character position at which to begin replacing characters. The position of the first character in text-expression is `1`. When you omit this argument, REPLCHARS starts with the first character. REPLCHARS replaces as many characters of text-expression as are required for the specified new characters. When the value of start is greater than the length of text-expression, REPLCHARS simply returns text-expression.

#### Examples

REPLCHARS has replaced the first 6 characters of `var1` (`Hellot` of `HellothereJoe`) with the 6 characters of `var2` (`HiJane`). It has preserved the line breaks following `Hi` (from` var2`) and `there` (from `var1`).

To replace all 13 characters in `var1`, you must specify 13 replacement characters; for example, you can add 7 spaces after `Jane`.

    var2 = JOINLINES('Hi' 'Jane       ')

The statement

    SHOW REPLCHARS(var1 var2)

produces the following output.

    Hi
    Jane

Example 8-78 Replacing Text Characters

This example shows how to replace a portion of the text value `Hello there, Joe`.

The statement

    SHOW REPLCHARS('Hello there, Joe', 'Jane', 14)

produces the following output.

    Hello there, Jane

Example 8-79 How REPLCHARS Handles Line Breaks

This example shows how REPLCHARS preserves but ignores line breaks.

    var1 = JOINLINES('Hello' 'there' 'Joe')
    var2 = JOINLINES('Hi' 'Jane')

The statement

    show REPLCHARS(var1 var2)

produces the following output.

    Hi
    Janehere
    Joe

### 8.79 REPLCOLS

The REPLCOLS function replaces some or all of the character columns in one multiline TEXT value with the columns of another. The function returns a multiline TEXT value composed of the resulting lines.

Columns refer to the character positions in each line of a multiline TEXT value. The first character in each line is in column one, the second is in column two, and so on.

#### Return Value

TEXT or NTEXT

This function accepts TEXT values and NTEXT values as arguments. The data type of the return value depends on the data type of the values specified for the arguments:

- When all arguments are TEXT values, the return value is TEXT.

- When all arguments are NTEXT values, the return value is NTEXT.

- When the arguments include both TEXT and NTEXT values, the function converts all TEXT values to NTEXT before performing the function operation, and the return value is NTEXT.

The number of lines in the return value is always the same as the number of lines in text-expression. When the columns text expression has fewer lines, REPLCOLS repeats its last line in each subsequent line of the return value.

#### Syntax

REPLCOLS(text-expression columns \[start\])

#### Parameters

text-expression
The text expression in which you want to replace one or more columns.

columns
A text expression containing one or more lines. This expression provides the columns to replace some or all of the columns in text-expression.

start
An `INTEGER`, between 1 and 32,767, representing the column position at which to begin replacing. The column position of the first character in each line of text-expression is 1. When you do not specify start, replacement begins with Column 1. When you specify a starting column that is to the right of the last character in a given line in text-expression, the corresponding line in the return value has spaces filling in the intervening columns. See Example 8-80.

#### Examples

Example 8-80 Joining and Aligning Columns

In the following example, the `citylist` and `cityreps` lines are joined so that the values are aligned, one under the other. The replacement begins at Column 11. When JOINCOLS were used instead of REPLCOLS, the `cityreps` list would be misaligned.

The statement

    SHOW citylist

produces the following output.

    Boston
    Houston
    Chicago
    Denver

The statement

    SHOW cityreps

produces the following output.

    Brady
    Lopez
    Alfonso
    Cody

The statement

    SHOW REPLCOLS(citylist cityreps 11)

produces the following output.

    Boston    Brady
    Houston   Lopez
    Chicago   Alfonso
    Denver    Cody

### 8.80 REPLLINES

The REPLLINES function replaces one or more lines in a multiline TEXT expression.

#### Return Value

TEXT or NTEXT

This function accepts TEXT values and NTEXT values as arguments. The data type of the return value depends on the data type of the values specified for the arguments. When all arguments are TEXT values, the return value is TEXT. When all arguments are NTEXT values, the return value is NTEXT. When the arguments include both TEXT and NTEXT values, the function converts all TEXT values to NTEXT before performing the function operation, and the return value is NTEXT.

#### Syntax

REPLLINES(text-expression lines \[start\])

#### Parameters

text-expression
A multiline text expression in which you want to replace one or more lines.

lines
A text expression that contains one or more lines that replace the existing lines in text-expression.

start
An `INTEGER` that represents the line number at which to begin replacing. The position of the first line in text-expression is `1`. When you omit this argument, REPLLINES starts with line `1`. REPLLINES replaces as many lines of text-expression as are required for the specified new lines.

#### Examples

Example 8-81 Replacing a Text Line

This example shows how to replace the second line in a multiline TEXT value in a variable called `mktglist`. Assume first that the statement `SHOW mktglist` produces the following output.

    Salespeople
    Products
    Services

By using REPLLINES, you can display a different value for "Products".

    SHOW REPLLINES(mktglist, 'advertising', 2)

    Salespeople
    Advertising
    Services

### 8.81 RESERVED

The RESERVED function can provide a list of all the words that are reserved because they are known to the OLAP DML parser, or it can indicate if a word that you specify is known to the OLAP DML parser. Some other words are also reserved as discussed in "Other Reserved Words".

#### Return Value

Either a multiline text expression or BOOLEAN, depending on whether or not you specify an argument to the function.

#### Syntax

RESERVED \[(word-expression)\]

#### Parameters

word-expression
A text expression that represents a word that may or may not be reserved in the OLAP DML. When you specify word-expression, the RESERVED function returns a BOOLEAN value indicating if the word is reserved in OLAP DML. When you do not specify an argument, RESERVED returns a TEXT value consisting of all the reserved words in OLAP DML, with each word on a separate line.

#### Usage Notes

Other Reserved Words

The RESERVED function only recognizes words known to the OLAP DML parser. The RESERVED function des not recognize the names of option objects and some other objects in the `EXPRESS` analytic workspace. The names of these objects are reserved in Oracle OLAP, but are ignored by the RESERVED function. To identify the names of these objects, issue the following statements.

    AW ATTACH EXPRESS
    LISTNAMES

NA is Reserved

When you specify `NA` for the argument, the RESERVED function returns `NO`. When you specify `NA`, the RESERVED function returns `YES`.

Case-Sensitivity

The list of reserved words returned by the RESERVED function contains some words in all uppercase and some in mixed case. Words all in uppercase are reserved in their entirety. Words in mixed case can be abbreviated to the uppercase portion. For such words, any subset of the word containing the uppercase portion is reserved. For example, one word in the list returned by RESERVED is `CODEVERsion`. The following are all reserved: `codever`, `codeversi`, `codeversio`, and `codeversion`. However, `codeve` is not reserved.

#### Examples

Example 8-82 Determining If a Word Is Reserved

The following example shows how you can use the RESERVED function to determine if a word is reserved in OLAP DML.

The function call

    SHOW RESERVED('update')

returns the following value

    YES

### 8.82 ROUND

Depending on the syntax you specify, the ROUND function performs a numeric operation or a date and time operation. Because the syntax for the ROUND function differs for each type of operation, there are two topics for the ROUND function:

- ROUND (datetime)

- ROUND (number)

#### 8.82.1 ROUND (datetime)

The ROUND (datetime) function returns date rounded to the unit specified by the format model `fmt`. The value returned is always of data type `DATETIME`, even if you specify a different datetime data type for date.

##### Return Value

DATETIME

##### Syntax

ROUND(datetime_exp, \[format \])

##### Parameters

datetime-exp
A datetime expression that identifies a date and time number.

format
A text expression that specifies a format model shown in the following table. A format model indicates how the date and time number should be rounded.

If you omit this argument, then `datetime-exp` is rounded to the nearest day.

The following table lists the format models you can use with the `ROUND` and `TRUNC` date functions and the units to which they round and truncate dates. The default model, 'DD', returns the date rounded or truncated to the day with a time of midnight.

Table 8-13 Datetime Format Templates for the ROUND and TRUNC Date Functions

| Format Model                                                   | Rounding or Truncating Unit                                                 |
|:---------------------------------------------------------------|:----------------------------------------------------------------------------|
| `CC`<br>`SCC`                                                  | One greater than the first two digits of a four-digit year                  |
| `SYYYY`<br>`YYYY`<br>`YEAR`<br>`SYEAR`<br>`YYY`<br>`YY`<br>`Y` | Year (rounds up on July 1)                                                  |
| `IYYY`<br>`IY`<br>`IY`<br>`I`                                  | ISO Year                                                                    |
| `Q`                                                            | Quarter (rounds up on the sixteenth day of the second month of the quarter) |
| `MONTH`<br>`MON`<br>`MM`<br>`RM`                               | Month (rounds up on the sixteenth day)                                      |
| `WW`                                                           | Same day of the week as the first day of the year                           |
| `IW`                                                           | Same day of the week as the first day of the ISO year                       |
| `W`                                                            | Same day of the week as the first day of the month                          |
| `DDD`<br>`DD`<br>`J`                                           | Day                                                                         |
| `DAY`<br>`DY`<br>`D`                                           | Starting day of the week                                                    |
| `HH`<br>`HH12`<br>`HH24`                                       | Hour                                                                        |
| `MI`                                                           | Minute                                                                      |

The starting day of the week used by the format models DAY, DY, and D is specified implicitly by the initialization parameter `NLS_TERRITORY`.

##### Examples

Example 8-83 Rounding to the Nearest Year

When the value of the NLS_DATE_FORMAT option is `DD-MON-YY`, then this statement:

    SHOW ROUND (TO_DATE('27-OCT-92'),'year')

returns this value:

    01-JAN-93

Example 8-84 Rounding to Different Formats

Assume that you have a variable named `mydatetime` with the following definition and value defined in your analytic workspace.

    DEFINE MYDATETIME VARIABLE DATETIME
    DATE_FORMAT = 'MON-RRRR-DD-HH24'
    mydatetime = CURRENT_TIMESTAMP
    SHOW mydatetime
    = 'AUG-2006-07-13'

As the following SHOW statements illustrate, depending on what date format value you specify, the ROUND function returns different values for the `mydatetime` variable.

    SHOW ROUND(mydatetime, 'RRRR')
    01-JAN-07

    SHOW ROUND(mydatetime, 'MON')
    01-AUG-06

    SHOW ROUND(mydatetime, 'DD')
    08-AUG-06

    SHOW ROUND(mydatetime)
    = 'AUG-2006-08-00'

#### 8.82.2 ROUND (number)

When a number is specified as an argument, the ROUND function returns the number rounded to the nearest multiple of a second number you specify or to the number of decimal places indicated by the second number.

##### Return Value

DECIMAL (when the round type is MULTIPLE)

NUMBER (when the round type is DECIMAL)

##### Syntax

ROUND(number_exp roundvalue) \[MULTIPLE\|DECIMAL\]

##### Parameters

number_exp
An expression that identifies the number to round.

roundvalue
A value that specifies the basis for rounding.

When the round type is MULTIPLE:

- number_exp is rounded to the nearest multiple of roundvalue.

- roundvalue can be an `INTEGER` or decimal number.

When the round type is DECIMAL:

- roundvalue specifies the number of places to the right or left of the decimal point to which number_exp should be rounded. When roundvalue is positive, digits to the right of the decimal point are rounded. When it is negative, digits to the left of the decimal point are rounded.

- When roundvalue is omitted, number_exp is rounded to `0` decimal places.

- roundvalue must be an `INTEGER`.

MULTIPLE
(Default) Specifies that rounding is performed by rounding to the nearest multiple of roundvalue.

DECIMAL
Specifies that rounding is performed by rounding to the number of decimal places indicated by roundvalue.

##### Usage Notes

Using ROUND to Compare Expressions

A DECIMAL value might be stored in a slightly different form than shows up at the level of significant digits you are using. This small difference can cause unexpected results when you are comparing two expressions. The problem can occur even when you are comparing INTEGER expressions that involve calculations because many calculations are done only after converting INTEGER values to DECIMAL values. You do not generally see the difference in reports because reports usually show only two or three decimal places.

For example, when you compare two numbers with the EQ or NE operators, you probably want to ignore any difference caused by the least significant digits. When `expense` was stored as `100.00000001`, the least significant digit would not be ignored by the simple form of the comparison.

The statement

    SHOW expense EQ 100.00

produces the following result.

    NO

However, you can use ROUND to force EQ or NE to ignore the least significant digits.

    SHOW ROUND(expense, .01) EQ 100.00

This statement produces the following result.

    YES

Using ABS to Compare Expressions

When speed of calculation is important in your application, you may want to use the ABS function with LT to compare numbers, instead of using ROUND with EQ or NE.

##### Examples

Example 8-85 Rounding to Different Multiples

The following statements show the results of rounding the expression `2/3` to different multiples. The value of the DECIMALS setting is `2`.

The statement

    SHOW ROUND(2/3, .01)

produces the following result.

    0.67

The statement

    SHOW ROUND(2/3, .1)

produces the following result.

    0.70

The statement

    SHOW ROUND(2/3, .5)

produces the following result.

    0.50

Example 8-86 Rounding to the Nearest Thousand

The following example shows `sales` rounded to the nearest thousand.

    LIMIT month TO FIRST 4
    LIMIT district TO FIRST 1
    REPORT ROUND(sales 1000)

These statements produce the following output.

    DISTRICT: BOSTON
                   -------------ROUND(SALES 1000)-------------
                   -------------------MONTH-------------------
    PRODUCT          Jan95      Feb95      Mar95      Apr95
    -------------- ---------- ---------- ---------- ----------
    Tents           32,000.00  33,000.00  43,000.00  58,000.00
    Canoes          66,000.00  76,000.00  92,000.00 126,000.00
    Racquets        52,000.00  57,000.00  59,000.00  69,000.00
    Sportswear      53,000.00  59,000.00  63,000.00  68,000.00
    Footwear        91,000.00  87,000.00 100,000.00 108,000.00

Example 8-87 Rounding to the Nearest Multiple of 12

To show `units` rounded to the nearest multiple of 12, use the following statements.

    LIMIT month TO FIRST 4
    LIMIT district TO FIRST 1
    REPORT DECIMAL 0 ROUND(units 12)

These statements produce the following output.

    DISTRICT: BOSTON
                   --------------ROUND(UNITS 12)--------------
                   -------------------MONTH-------------------
    PRODUCT          Jan95      Feb95      Mar95      Apr95
    -------------- ---------- ---------- ---------- ----------
    Tents                 204        204        264        360
    Canoes                348        396        480        660
    Racquets              996      1,080      1,116      1,308
    Sportswear          1,092      1,212      1,296      1,404
    Footwear            2,532      2,400      2,772      2,976

Example 8-88 Rounding to Decimal Places

The following statements show the results of rounding `15.193` to various decimal places.

The statement

    ROUND(15.193, 1)

produces the following result

    15.2

The statement

    ROUND(15.193, -1)

produces the following result

    20
     

### 8.83 ROW function

The ROW function returns a line of data in cells, one after another in a single row. It is identical to the ROW command, except that it returns a text value, instead of sending the text to the current outfile.

The ROW function, just like the ROW command, consists of a series of column descriptions that specify the data to be returned and, optionally, the way in which it is to be formatted. The ROW function lets you assign the returned value to a text variable, send it to your current outfile with the SHOW or REPORT command, or process it further as an argument to a character manipulation function.

**See Also:**

[ROW command](olap-dml-commands-h-z.md)

#### Return Value

TEXT

#### Syntax

ROW(\[attribs\] \[ACROSS dimension \[limit-clause\]:\] {exp1\|SKIP} -      \[\[attribs\] \[ACROSS dimension \[limit-clause\]:\] {expn\|SKIP}\])

See the [ROW command](olap-dml-commands-h-z.md) for a complete description of the arguments.

The ROW function without any arguments returns a blank line.

#### Usage Notes

The notes for the ROW command also apply to the ROW function.

#### Examples

Example 8-89 Assigning Output to a Text Variable

The following assignment statement assigns three lines of output to the text variable `textvar`.

    textvar = ROW(OVER '-' UNDER '=' 'This is a Row.')
    SHOW textvar

These statements produce the following output.

    --------------
    This is a Row.
    ==============

Example 8-90 Producing Multiple Rows of Output

You can use the ROW function with JOINLINES in a program to loop over a group of dimension values and assign several rows of data to a text variable. Instead of using the SHOW command in the following program excerpt, you could use the contents of` textvar` for some other purpose.

    LIMIT month TO 'Jan95' 'Feb95'
    LIMIT district TO 'Boston' 'Atlanta' 'Chicago'
    textvar = NA
    textvar = ROW(W 8 SKIP ACROSS month: <month SKIP>)
    textvar = JOINLINES(textvar ROW(W 8 SKIP ACROSS month: -
       CENTER <'Sales' 'Plan'>))
    FOR district
    textvar = JOINLINES(textvar ROW(W 8  district ACROSS month: -
       <sales sales.plan>))
    SHOW textvar

These statements produce the following output.

    OUTPUT:
             Jan95                 Feb95
              Sales       Plan      Sales       Plan
    Boston   32,153.52  42,346.89  32,536.30  43,265.50
    Atlanta  40,674.20  54,583.41  44,236.55  57,559.87
    Chicago  29,098.94  36,834.37  29,010.20  37,667.66

### 8.84 ROWIDTOCHAR

The ROWIDTOCHAR function converts a value of the `ROWID` data type to a value of the TEXT data type.

#### Return Value

`TEXT`

The result of this conversion is always in the national character set and is 18 characters long.

#### Syntax

ROWIDTOCHAR (rowid)

#### Parameters

rowid
The value of type `ROWID` to convert.

#### Examples

Example 8-91 Converting ROWID Data to TEXT or NTEXT Data

Assume the following your analytic workspace has the following object definitions.

    DEFINE myrowid DIMENSION ROWID
    DEFINE mytext VARIABLE TEXT
    DEFINE myntext VARIABLE NTEXT

Now you populate `myrowid` which has a data type of ROWID using a MAINTAIN statement. Then you use the ROWIDTOCHAR function to populate `mytext` which has a data type of TEXT and ROWIDTONCHAR function to populate `myntext` which has a data type of NTEXT. Reports show that all of the variables are populated.

    MAINTAIN myrowid ADD CHARTOROWID('AAAFd1AAFAAAABSAA/')
    mytext = ROWIDTOCHAR (myrowid)
    myntext = ROWIDTONCHAR (myrowid)

    MYROWID
    ------------------------------
    AAAFd1AAFAAAABSAA/

    MYTEXT
    ------------------------------
    AAAFd1AAFAAAABSAA/

    MYNTEXT
    ------------------------------
    AAAFd1AAFAAAABSAA/

### 8.85 ROWIDTONCHAR

The ROWIDTONCHAR function converts a value of the `ROWID` data type to a value of the `NCHAR` data type. The result of this conversion is always in the national character set and is 18 characters long.

#### Return Value

`NCHAR`

The result of this conversion is always in the national character set and is 18 characters long.

#### Syntax

ROWIDTONCHAR (rowid)

#### Parameters

rowid
The value of type `ROWID` to convert.

#### Examples

See Example 8-91.

### 8.86 RPAD

The RPAD function returns an expression, right-padded to a specified length with the specified characters; or, when the expression to be padded is longer than the length specified after padding, only that portion of the expression that fits into the specified length.

#### Return Value

TEXT or NTEXT based on the data type of the expression you want to pad (text-exp).

#### Syntax

RPAD (text-exp , length \[, pad-exp\])

#### Parameters

text-exp
A text expression to pad.

length
The total length of the return value as it is displayed on your terminal screen. In most character sets, this is also the number of characters in the return value. However, in some multibyte character sets, the display length of a character string can differ from the number of characters in the string.

When you specify a value for length that is shorter than the length of text-exp, then this function truncates the expression to the specified length.

pad-exp
A text expression that specifies the padding characters. The default value of pad-exp is a single blank.

#### Examples

Example 8-92 Right-Padding a String

The following example right-pads a name with the letters "ab" until it is 12 characters long.

    SHOW RPAD('Morrison',12,'ab')
    Morrisonabab

### 8.87 RTRIM

The RTRIM function removes characters from the right of a text expression, with all the rightmost characters that appear in another text expression removed. The function begins scanning the base text expression from its last character and removes all characters that appear in the trim expression until reaching a character that is not in the trim expression and then returns the result.

#### Return Value

TEXT or NTEXT based on the data type of the first argument.

#### Syntax

RTRIM (text-exp \[,  trim-exp\])

#### Parameters

text-exp
A text expression that you want trimmed.

trim-exp
A text expression that is the characters to trim. The default value of trim-exp is a single blank.

#### Examples

Example 8-93 Trimming Right-Most Characters

The following example trims all of the right-most x's and y's from a string.

    SHOW RTRIM('Last Wordxxyxy','xy')
    Last Word

### 8.88 RUNTOTAL

The RUNTOTAL function returns the running total of an expression. You can use the RUNTOTAL function in a ROW command, ROW function, or REPORT command to generate a running total of the value of an expression.

#### Return Value

DECIMAL

#### Syntax

RUNTOTAL(n)

#### Parameters

n
One of the 32 subtotals (1 to 32) that Oracle OLAP accumulates for the current column of a report. RUNTOTAL returns the value of this subtotal for the specified column, but does not reset the value of the subtotal to zero.

The numbers by which the 32 subtotals are referenced (1 to 32) have no intrinsic significance; all the subtotals are the same until you reference them.

#### Usage Notes

How RUNTOTAL Works

Unlike the SUBSTR function, RUNTOTAL does not reset the indicated subtotal to zero, nor does it add the value returned by RUNTOTAL to the indicated subtotal. However, the value returned by RUNTOTAL is added to the other 31 accumulating totals for the current column.

Accessing Data from Another Column

You can obtain a running total of an expression shown in another column of a report by adding that expression to RUNTOTAL. You can use the COALESCE function to refer to the values in the other column. For example, to show the sales for each month in the first data column of a row, and a cumulative total of sales in the second data column, you could use this statement.

    ROW month sales COLVAL(-1) + RUNTOTAL(1)

Resetting Subtotals

When you use a ROW statement to produce a report, you can use a ZEROTOTAL statement to reset any subtotal of any column to zero. Typically, use ZEROTOTAL at the beginning of a report program to make sure all totals begin at zero. A REPORT statement automatically resets all subtotals to zero before producing output.

NA Values and RUNTOTAL

RUNTOTAL ignores `NA` values unless all values are `NA`. When all values are `NA`, the total is `NA`.

#### Examples

Example 8-94 Calculating a Running Total in a Report

In a report, suppose you want column 2 to contain a running total of the values in column 1.

Assume that you issue the following OLAP DML statements

    ZEROTOTAL ALL
    ROW W 4 R 2 RUNTOTAL(1) + COLVAL(1)
    ROW W 4 R 5 RUNTOTAL(1) + COLVAL(1)
    ROW W 4 R 3 RUNTOTAL(1) + COLVAL(1)

These statements produce the following output.

    2     2.00
    5     7.00
    3    10.00

Example 8-95 Calculating a Running Total over Two Districts

In this example, you want your report to contain the unit sales of tents for two districts for the first six months of 1996. Along with the monthly sales figures, you want to see a running total of tent sales for these two districts for the year to date. To produce this cumulative total, use the RUNTOTAL function.

    LIMIT product TO 'Tents'
    LIMIT month TO 'Jan96' TO 'Jun96'
    LIMIT district TO 'Boston' 'Chicago'
    REPORT ACROSS district: units -
       DECIMAL 0 TOTAL(units, month)+RUNTOTAL(1)

These statements produce the following output.

    PRODUCT: TENTS
                   --------UNITS--------
                   ------DISTRICT-------
                                         TOTAL(UNIT
                                             S,
                                         MONTH)+RUN
    MONTH            Boston    Chicago    TOTAL(1)
    -------------- ---------- ---------- ----------
    Jan96                 307        189        496
    Feb96                 209        190        895
    Mar96                 277        257      1,429
    Apr96                 372        318      2,119
    May96                 525        433      3,077
    Jun96                 576        466      4,119

### 8.89 SESSIONTIMEZONE

The SESSIONTIMEZONE function returns the time zone of the current session.

#### Return Values

A time zone offset (a character type in the format `'[+|]TZH:TZM'`) or a time zone region name, depending on how the user specified the session time zone value in the most recent ALTER SESSION statement

#### Syntax

SESSIONTIMEZONE

#### Examples

Example 8-96 Retrieving the Session Time Zone

    SHOW SESSIONTIMEZONE
    -05:00

### 8.90 SIGN

The SIGN function returns a value that indicates when a specified number is less than, equal to, or greater than `0` (zero).

#### Return Value

INTEGER. SIGN returns `-1` when `n<0`, `0` (zero) when `n=0`, or `1` when `n>0`.

#### Syntax

SIGN (n)

#### Parameters

n
A numeric expression.

#### Examples

Example 8-97 Determining if the Result of a Numeric Expression is Greater or Less Than Zero

The following example indicates that the function's argument (`-15`) is less than `0` (zero).

    SHOW SIGN(-15)
     -1

### 8.91 SIN

The SIN function calculates the sine of an angle expression.

#### Return Value

NUMBER

The result returned by SIN is a value with the same dimensions as the specified expression.

#### Syntax

SIN(angle-expression)

#### Parameters

angle-expression
A numeric expression that contains an angle value, which is specified in radians.

#### Examples

Example 8-98 Calculating the Sine of an Angle in Radians

This example calculates the sine of an angle of 1 radian. The statements

    DECIMALS = 5
    SHOW SIN(1)

produce the following result.

    0.84147

Example 8-99 Calculating the Sine of an Angle in Degrees

This example calculates the sine of an angle of 30 degrees. Because `1` degree = `2*(pi)/360` radians, `30` degrees is about` 30*2*3.14159/360` radians. The OLAP DML statement

    SHOW SIN(30 * 2 * 3.14159 / 360)

produces the following result.

    0.50000

### 8.92 SINH

The SINH function calculates the hyperbolic sine of a number.

#### Return Value

NUMBER

#### Syntax

SINH(expression)

#### Parameters

expression
A numeric expression that contains an angle value, which is specified in radians.

#### Examples

Example 8-100 Calculating the Hyperbolic Sine of an Angle

This example calculates the hyperbolic sine of an angle of 1 radian. The statements

    DECIMALS = 5
    SHOW SINH(1)

produce the following result.

    1.17520

### 8.93 SMALLEST

The SMALLEST function returns the smallest value of an expression. You can use this function to compare numeric values or date values.

#### Return Value

The data type of the expression. It can be INTEGER, LONGINT, DECIMAL, or DATE.

#### Syntax

SMALLEST(expression \[CACHE\] \[dimension...\])

#### Parameters

expression
The expression whose smallest value is to be returned.

CACHE
Specifies slightly different internal behavior. Specify this keyword only when the original performance is extremely slow.

dimension
The name of a dimension of the result; or, the name of a relation between one dimension of expression and another dimension that you want as a dimension of the result.

By default, SMALLEST returns a single value. When you indicate one or more dimensions for the result, SMALLEST tests for values along the dimensions that are specified and returns an array of values. Each dimension must be either a dimension of expression or related to one of its dimensions.

**Tip:**

When you specify a dimension that is not an actual dimension of expression, but, instead, is dimension that is related to a dimension of expression and when there are multiple relations between the two dimensions, Oracle OLAP uses the default relation between the dimensions to perform the calculation. (See the [RELATION command](olap-dml-commands-h-z.md) for more information on default relations.) When you do not want Oracle OLAP to use this default relation, specify the related dimension by specifying the name of a specify relation.

#### Usage Notes

NA Values and SMALLEST

SMALLEST is affected by the NASKIP option in the same manner as other aggregate functions. When NASKIP is set to `YES` (the default), SMALLEST ignores `NA` values and returns the smallest value or values that are not `NA`. When NASKIP is set to `NO`, SMALLEST returns `NA` when any value of the expression is `NA`. When all the values of the expression are `NA`, SMALLEST returns `NA` for either setting of NASKIP.

#### Examples

Example 8-101 Finding the Month with the Least Amount of Sportswear Sales

This example uses the SMALLEST function to find the smallest monthly sportswear sales for three districts during the first half of 1996. To see the smallest sales figure for each district, specify `district` as the dimension of the results.

    LIMIT product TO 'Sportswear'
    LIMIT district TO FIRST 3
    LIMIT month TO 'Jan96' TO 'Jun96'
    REPORT HEADING 'Smallest Sales' SMALLEST(sales district)

The preceding statements produce the following output.

                    Smallest
    DISTRICT         Sales
    -------------- ----------
    Boston          57,079.10
    Atlanta        129,616.08
    Chicago         77,489.51

### 8.94 SMOOTH

The SMOOTH function computes a single or a double exponential smoothing of a numeric expression.

#### Return Value

DECIMAL

#### Syntax

SMOOTH(expression {SINGLE alpha\|DOUBLE alpha beta m} \[BASEDON dimension-list\])

#### Parameters

expression
The numeric expression whose values are to be smoothed.

SINGLE
DOUBLE
The method to use in the exponential smoothing of the values in expression. The SINGLE method specifies single exponential smoothing and requires an alpha argument. The DOUBLE method specifies double exponential smoothing (also known as Holt's linear exponential smoothing) and requires an alpha argument, a beta argument, and an m argument.

alpha
A number in the range from 0 to 1 that smooths the difference between the observed data forecast and the last forecast. The higher the value, the more weight the most recent forecast has, so smoothing decreases as the smoothing factor increases. A smoothing factor of 0 completely smooths the forecasts and always returns the first forecast, which is the first data observation. A smoothing factor of 1 produces no smoothing at all and returns the previous data observation. (See "alpha ".)

beta
A number in the range from 0 to 1 that smooths the difference between the previous forecast and the current forecast. As with the alpha argument, smoothing decreases as the smoothing factor increases.

m
A positive `INTEGER` between 1 and the total number of periods of data in the data series. The m argument specifies the number of periods on which to base the forecasts.

BASEDON dimension-list
An optional list of one or more of the dimensions of expression to include in the exponential smoothing. When you do not specify the dimensions, then SMOOTH bases the smoothing on all of the dimensions of expression.

#### Usage Notes

The Effect of NASKIP on SMOOTH

SMOOTH is affected by the NASKIP option. When NASKIP is set to `YES` (the default), then SMOOTH ignores `NA` values. When NASKIP is set to `NO`, then SMOOTH returns `NA` for every forecast after the `NA` value.

Results of alpha Values

This note illustrates the results of using different alpha values for single exponential smoothing. The results are based on the `sales` variable with the dimensions limited by the following statements.

    LIMIT month TO 'Jan96' TO 'Dec96'
    LIMIT product TO 'Tents'
    LIMIT district TO 'Boston'
    REPORT DOWN month SMOOTH(sales, SINGLE, ALPHA, BASEDON month)

The following table shows the data values of the `sales` variable and also shows the results of the SMOOTH function in the preceding statement when the alpha argument variable has the different values shown in the table.

| MONTH | Sales of tents in Boston | alpha = 0 | alpha = .1 | alpha = .5 | alpha = .9 |
|:------|:-------------------------|:----------|:-----------|:-----------|:-----------|
| Jan96 | 50,808.96                | NA        | NA         | NA         | NA         |
| Feb96 | 34,641.59                | 50,808.96 | 50,808.96  | 50,808.96  | 50,808.96  |
| Mar96 | 45,742.21                | 50,808.96 | 49,192.22  | 42,725.28  | 36,258.33  |
| Apr96 | 61,436.19                | 50,808.96 | 48,847.22  | 44,233.74  | 44,793.82  |
| May96 | 86,699.67                | 50,808.96 | 50,106.12  | 52,834.97  | 59,771.95  |
| Jun96 | 95,120.83                | 50,808.96 | 53,765.47  | 69,767.32  | 84,006.90  |
| Jul96 | 93,972.49                | 50,808.96 | 57,901.01  | 82,444.07  | 94,009.44  |
| Aug96 | 94,738.05                | 50,808.96 | 61,508.16  | 88,208.28  | 93,976.18  |
| Sep96 | 75,407.66                | 50,808.96 | 64,831.15  | 91,473.17  | 94,661.86  |
| Oct96 | 70,622.91                | 50,808.96 | 65,888.80  | 83,440.41  | 77,333.08  |
| Nov96 | 46,124.99                | 50,808.96 | 66,362.21  | 77,031.66  | 71,293.93  |
| Dec96 | 36,938.27                | 50,808.96 | 64,338.49  | 61,578.33  | 48,641.88  |

#### Examples

Example 8-102 Smoothing Values

These statements limit the dimensions of the `sales` variable, set the data column width for reports, and report the data values for `sales`.

    LIMIT month TO 'Jan96' TO 'Dec96'
    LIMIT product TO 'Tents'
    LIMIT district TO 'Boston'
    COLWIDTH = 14

    REPORT W 6 DOWN month sales

The preceding statements produce the following output.

    DISTRICT: Boston
           ----SALES-----
           ---PRODUCT----
    MONTH      Tents
    ------ --------------
    Jan96       50,808.96
    Feb96       34,641.59
    Mar96       45,742.21
    Apr96       61,436.19
    ...
    Nov96       46,124.99
    Dec96       36,938.27

This statement reports the results of using the SMOOTH function on the `sales` variable with the SINGLE method, a data smoothing factor of `.5`, and based on the `month` dimension.

    REPORT W 6 DOWN month SMOOTH(sales, SINGLE, .5, BASEDON month)

The preceding statement produces the following output.

    DISTRICT: Boston
           SMOOTH(SALES,-
           -SINGLE, .5,--
           BASEDON MONTH)
           ---PRODUCT----
    MONTH      Tents
    ------ --------------
    Jan96              NA
    Feb96       50,808.96
    Mar96       42,725.28
    Apr96       44,233.74
    ...
    Nov96       77,031.66
    Dec96       61,578.33

### 8.95 SORT function

The SORT function returns the dimension or dimension surrogate values that result from a specified SORT command.

**See Also:**

[SORT command](olap-dml-commands-h-z.md)

#### Return value

The return value varies depending on the use of the function:

- When the SORT function is an argument to an OLAP DML statement (including a user-defined command or function) that expects a valueset, it returns a valueset. When the SORT function returns an empty valueset, it returns it as a valueset with null status.

- When you include the INTEGER keyword, the SORT function returns the position numbers of the values as INTEGERS.

- In all other cases, the SORT function returns either a TEXT value. When it returns a TEXT value that represents empty status, it returns the value as `NA`.

#### Syntax

SORT(\[INTEGER\]dimension \[byhierarchy\] \[bycriterion...\])

where:

- `byhierarchy` is an optional phrase that uses a parent relation to arrange the order of values in the current status list of a hierarchical dimension or its dimension surrogate, or to assign values to a valueset, based on family relationships within the hierarchy. You can include only one `byhierarchy` phrase in a SORT statement. It must be the first phrase in a SORT statement.

  `HIERARCHY` `parent-relation` ` [INVERT] [DEPTH` `n``] [SORTORPHANS] `

- `bycriterion` uses an explicit criterion to arrange the order of values in the current status list of a dimension or its dimension surrogate, or to assign values to a valueset. You can include as many `bycriterion` phrases as you want in a SORT statement.

  `{A|D} [NAFIRST] ``criterion`

#### Parameters

See the [SORT command](olap-dml-commands-h-z.md) for a complete description of all arguments except INTEGER.

INTEGER
When you use the INTEGER keyword, the function returns the position numbers of the values in the default dimension status rather than the names. When you use INTEGER with a valueset, the function returns the position numbers of the values in the default dimension status, not in the valueset.

### 8.96 SORTLINES

The SORTLINES function sorts the lines in a multiline TEXT value.

#### Return Value

TEXT or NTEXT

#### Syntax

SORTLINES(text-expression \[A\|D\])

#### Parameters

text-expression
A multiline text expression whose lines SORTLINES sorts. When you specify a TEXT expression, the return value is TEXT. When you specify an NTEXT expression, the return value is NTEXT.

A
D
Specifies whether the sorting order should be ascending, or alphabetical (A), or descending, or reverse alphabetical (D). The default is A (ascending). The sort order is controlled by the NLS_SORT option.

#### Examples

Example 8-103 Sorting Text Lines

This example shows how to sort the lines in a multiline text value in a variable called MKTREGIONS.

The statement

    SHOW mktregions

produces the following output.

    New York
    Boston
    Atlanta
    San Francisco

The statement

    SHOW SORTLINES(mktregions)

produces the following output.

    Atlanta
    Boston
    New York
    San Francisco

### 8.97 SOUNDEX

The SOUNDEX function returns a character string containing the phonetic representation of a text expression. This function lets you compare words that are spelled differently, but sound alike in English.

**See Also:**

The SOUNDEX function in [Oracle Database SQL Language Reference](../sqlrf/SOUNDEX.md) for a discussion of how the phonetic representation is constructed

#### Return Value

The same data type as text_exp.

#### Syntax

SOUNDEX(text_exp)

#### Parameters

text_exp
The expression for which you want a phonetic representation. It can be any of the text data types.

### 8.98 SQLFETCH

The SQLFETCH function retrieves one or more rows of a column in a relational text.

#### Return value

`TEXT`

#### Syntax

SQLFETCH (cursorname \[COLUMN column-number} {STOPAFTER number-of-rows\])

#### Parameters

cursorname
A `TEXT` expression that is the name of the SQL cursor. The cursor must be opened and closed by the caller.

column-number
An `INTEGER` value that is the number of the column. (Default is 1.)

number-of-rows
The number of rows to read. (Default is all remaining rows).

### 8.99 SQRT

The SQRT function computes the square root of an expression.

#### Return Value

DECIMAL

#### Syntax

SQRT(expression)

#### Parameters

expression
The numeric expression whose square root is to be computed.

#### Usage Notes

Negative Expressions

When expression is negative and ROOTOFNEGATIVE is set to `NO`, an error occurs. When expression is negative and ROOTOFNEGATIVE is set to `YES`, SQRT returns the value `NA`.

#### Examples

Example 8-104 Calculating a Square Root

This example calculates the square root of `144`. The statement

    SHOW SQRT(144)

produces the following result.

    12.00

### 8.100 STARTOF

The STARTOF function returns the starting date of a time period in a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR.

**Note:**

You can only use this function with dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR.You cannot use this function for time dimensions that are implemented as hierarchical dimensions of type TEXT.

#### Return Value

DATE or text

#### Syntax

STARTOF(dwmqy-dimension)

#### Parameters

dwmqy-dimension
A dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR. When you have explicitly defined your own relation between dimensions of this type, you can use the name of this time relation here.

#### Usage Notes

How STARTOF Works

STARTOF returns the first date of the time period that is first in the current status list of the dimension.

Phased or Multiple Periods

STARTOF is particularly useful when the dimension has a phase that differs from the default or when the time periods are formed from multiple weeks or years. For example, when the dimension has four-week time periods, the STARTOF function identifies the starting date of a particular four-week period.

Format of the Result Returned by STARTOF

When you display the result returned by STARTOF, the date is formatted according to the date template in the DATEFORMAT option. When the day of the week or the name of the month is used in the date template, the day names specified in the DAYNAMES option and the month names specified in the MONTHNAMES option are used. You can use the result returned by STARTOF anywhere that a DATE value is expected.

Retrieving the Last Valid Date of a Time Period

The ENDOF function, which returns the last date of a time period.

#### Examples

Example 8-105 Finding the Fiscal Year Starting Date

The following statements define a year dimension (called FYEAR, for a fiscal year that ends in June), specify how the year is formatted, add dimension values for fiscal years 1996 through 1998, and produce a report of the starting date of each fiscal year.

    DEFINE fyear DIMENSION YEAR ENDING June
    VNF 'FY<ff>'
    MAINTAIN fyear ADD '30JUN96' '30JUN98'
    REPORT W 14 STARTOF(fyear)

These statements produce the following output.

    FYEAR          STARTOF(FYEAR)
    ---------      --------------
    FY96           01JUL95
    FY97           01JUL96
    FY98           01JUL97

### 8.101 STATALL

The STATALL function indicates whether default status is currently in effect for a given dimension. That is, STATALL returns `YES` when STATLIST would return ALL. Otherwise, STATALL returns `NO`.

#### Return Value

BOOLEAN

#### Syntax

STATALL(dimension)

#### Parameters

dimension
A text expression whose value is the name of a dimension or dimension surrogate.

#### Usage Notes

STATALL Compared to STATLIST

STATALL provides an alternative to running the STATLIST program to determine if the status of a specified dimension is ALL.

#### Examples

Example 8-106 Using STATALL

With the following statement, you can see whether the status of the MONTH dimension is ALL.

    SHOW STATALL(month)

The return value is either `YES` or `NO`.

### 8.102 STATCURR

The STATCURR function returns the values of a specified status list for a dimension

#### Return Value

The data type of the returned value varies depending on the data type of the dimension.

#### Syntax

STATCURR (dimension, integer)

#### Parameters

dimension
The name of the dimension for which the function searches for status lists.

integer
Specifies the position in the status list stack of the status list the function returns.

| Value | Specifies                                                                                                    |
|:------|:-------------------------------------------------------------------------------------------------------------|
| `0`   | The current value of the dimension.                                                                          |
| `-1`  | Returns the current value of status for the previous status list in the status list stack for the dimension. |
| `1`   | Returns the current value of the status list on the bottom of the status list stack for the dimension.       |

### 8.103 STATDEPTH

The STATDEPTH function returns the number of status lists that Oracle OLAP has saved for a specified dimension. The current status list of a dimension is at the top of the stack which means that it has a depth of `1` (one.

#### Return Value

INTEGER

#### Syntax

STATDEPTH (dimension)

#### Parameters

dimension
The name of the dimension for which you want to retrieve information.

#### Usage Notes

What is a Status List Stack?

A status list stack for a dimension is a stack of the dimension statuses that Oracle OLAP uses to manage status when executing PUSH and POP statements. The depth of the list varies depending on what Oracle OLAP statements have executed:

- When you first attach an analytic workspace, the current status of each dimension is ALL and the status list stack for each dimension has a depth of one (that is, there is only one status list in the stack).

- The depth of the status list stack for a dimension stays at one (for the current status list) no matter how often current status changes (that is, no matter how many LIMIT commands execute against it), except in the following situations:

  - Oracle OLAP executes a PUSH statement for the dimension. After a PUSH statement executes, each time a LIMIT command executes for a pushed dimension, Oracle OLAP adds status list to the status list stack for that dimension. A POP statement for the dimension originally pushed, clears the status list stack for the dimension. The status list stack for the dimension, once again becomes one.

  - Oracle OLAP executes a statement (like CHGDIMS or TEMPSTAT) that temporarily changes the status of the dimension. In this case, Oracle OLAP adds a status list to the status list stack during the time the statement is in effect, and removes it immediately afterward. You can only access the status list from the status list stack while the temporary status is in effect.

### 8.104 STATEQUAL

The STATEQUAL function compares the status lists of a dimension.

#### Return Value

BOOLEAN

#### Syntax

STATEQUAL (statlist1, statlist2 \[INORDER\])

#### Parameters

statlist1
The status list of a dimension as specified using the name of the dimension, a valueset dimensioned by the dimension; or a LIMIT or SORT function for the dimension.

statlist2
The status list of the same dimension as that specified by statlist1. You can specify statlist2 using the name of the dimension, a valueset dimensioned by the dimension; or a LIMIT or SORT function for the dimension.

INORDER
Specifies that the values must be in the same order.

### 8.105 STATFIRST

 The STATFIRST function returns the first value in the current status list of a dimension or a dimension surrogate, or in a valueset.

#### Return Value

The data type returned by STATFIRST is either the data type of the dimension or dimension surrogate value or an `INTEGER` that indicates its position in the default status list of the dimension.The dimension value returned by STATFIRST is converted to a number or a text value, as appropriate to the context. See Example 8-107.

#### Syntax

STATFIRST(dimension)

#### Parameters

dimension
A text expression whose value is the name of a dimension, a dimension surrogate, or a valueset.

#### Examples

Example 8-107 Assigning value of STATFIRST to Variables of Different Types

The following statements

    DEFINE textvar TEXT
    textvar = STATFIRST(month)
    SHOW textvar

produce this output.

    Jun95

In contrast, these statements

    DEFINE intvar INTEGER
    intvar = STATFIRST(month)
    SHOW INTVAR

produce this output.

    6

Example 8-108 STATFIRST with KEEP

The following line from a program uses STATFIRST to limit `month` to all values in the status up to a value that has been stored previously in a variable called `onemonth`. The keyword KEEP means the new status is always a subset of the old status.

    LIMIT month KEEP STATFIRST(month) TO onemonth

STATFIRST is used here, rather than a particular `month` value, so that the limit can work on any status list.

### 8.106 STATLAST

The STATLAST function returns the last value in the current status list of a dimension or a dimension surrogate, or in a valueset.

#### Return Value

The data type returned by STATLAST is either the data type of the dimension or dimension surrogate value or an `INTEGER` that indicates its position in the default status list of the dimension. See "Automatic Data Conversion of Returned Dimension Values".

#### Syntax

STATLAST(dimension)

#### Parameters

dimension
A text expression whose value is the name of a dimension, a dimension surrogate, or a valueset.

#### Usage Notes

Automatic Data Conversion of Returned Dimension Values

The dimension value returned by STATLAST is converted to a number or a text value, as appropriate to the context. Suppose, for example, that `jun95` is the sixth `month` value but the last value in the current status list. The value of `STATLAST(month)` can be assigned either to a text variable or a numeric variable.

The following statements produce a text output value.

    DEFINE textvar TEXT
    TEXTVAR = statlast(MONTH)
    SHOW textvar

    Jun95

In contrast, these statements produce a numeric output value.

    DEFINE intvar INTEGER
    INTVAR = STATLAST(month)
    SHOW INTVAR

    6

#### Examples

Example 8-109 Setting Status with STATLAST

The following line from a program uses STATLAST to limit `month` to the values in the status, beginning with a month that has been stored previously in a variable called `onemonth`, and ending with the last value in the status.

    LIMIT month KEEP onemonth TO STATLAST(month)

STATLAST is used here, rather than a particular `month` value, so that the limit can work on any status list.

### 8.107 STATLEN

The STATLEN function returns the number of values in the current status list of a dimension or a dimension surrogate, or in a valueset.

#### Return Value

INTEGER

#### Syntax

STATLEN(dimension)

#### Parameters

dimension
A text expression whose value is the name of a dimension, a dimension surrogate, or a valueset.

#### Examples

Example 8-110 Counting Months in Status

The following statement sends to the current outfile the number of months in the current status list of the `month` dimension.

    SHOW STATLEN(month)

### 8.108 STATLIST

The STATLIST function returns a list of all values in the current status list of a dimension or dimension surrogate, or in a valueset. You can format the list to a specified width. The STATLIST function is employed by the STATUS command, which summarizes the status of a dimension. Use STATLIST rather than STATUS when you want to control the width or placement of the display.

#### Return Value

STATLIST returns a list of TEXT values that contains either the dimension or dimension surrogate values themselves (for example, `Jan95`) or numbers (for example, `6`) that represent the positions of the values in the default status list.

The returned values are in the form `value` `TO` `value`, for example, `Jan9`6 `TO` `Jun96`. When default status is in effect, it displays `ALL`. When the current status list or the valueset is empty, it displays `NULL`.

#### Syntax

STATLIST(dimension \[keyword\] \[width\])

#### Parameters

dimension
A text expression whose value is the name of a dimension, a dimension surrogate, or a valueset.

keyword
A keyword from the following table. The keywords allow you to specify the form in which you want the values in the current status list to appear.

Table 8-14 Keywords for STATLIST

| Keyword | Description                                                                                                                                                                                       |
|:--------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| INTEGER | Specifies that STATLIST should return the list of values in the current status of a dimension in the form of the `INTEGER` positions of those values in the default status list of the dimension. |
| TEXT    | (Default) Specifies that STATLIST should return the list of values in the current status of a dimension in the form of the value names of those values.                                           |

width
An optional `INTEGER` expression that specifies the width of the list in characters. When no width is specified, STATLIST uses the current value of the LSIZE option. LSIZE has a default value of `80`.

#### Examples

Example 8-111 Producing a Status List with ROW

This example lists months in which total sales exceed \$3,000,000.

These statements

    LIMIT month TO TOTAL(sales, month) GE 3000000
    ROW W 40 'Months with total sales over $3,000,000: '-
       W 40 STATLIST(month, 40)

produce the following output.

    Months with total sales over $3,000,000: Jun95 TO Sep95, May96 TO Sep96

Example 8-112 Producing a Status List with SHOW

The following STATLIST statement formats dimension values to a 20-character width.

    LIMIT month TO 'Jan95' 'Mar95' 'May95' 'Jul96' 'Sep96' 'Nov96'
    SHOW STATLIST(month 20)

These statements produce this output.

    Jan95, Mar95, May95,
    Jul96, Sep96, Nov96

This statement lists dimension positions.

    SHOW STATLIST(month INTEGER 20)

This is the output.

    1, 3, 5, 19, 21, 23

### 8.109 STATMAX

The STATMAX function returns the latest value in the current status list of a dimension or a dimension surrogate, or in a valueset.

#### Return Value

The data type returned by STATMAX is either the data type of the dimension or dimension surrogate value or an `INTEGER` that indicates its position in the default status list of the dimension or surrogate. See "Automatic Conversion of Values Returned by STATMAX".

#### Syntax

STATMAX(dimension)

#### Parameters

dimension
A text expression whose value is the name of a dimension, dimension surrogate, or valueset.

#### Usage Notes

Automatic Conversion of Values Returned by STATMAX

The value that STATMAX returns is converted to a number or a text value as appropriate to the context. For example, suppose that the status of `month` is limited to `Jun95` to `Dec95` and that `Dec95` is the twelfth month in the default status list. The value of `STATMAX(month)` can be assigned either to a text variable or a numeric variable.

The following statements

    DEFINE textvar TEXT
    textvar = STATMAX(month)
    SHOW textvar

produce this output.

    Dec95

In contrast, these statements

    DEFINE intvar INTEGER
    intvar = STATMAX(month)
    SHOW intvar

produce this output.

    12

#### Examples

Example 8-113 STATMAX Used in a Title

The following statements from a program use STATMAX to determine the latest of the 10 months with the highest total sales.

    LIMIT month TO BOTTOM 10 BASEDON TOTAL(sales, month)
    SHOW JOINCHARS(STATMAX(month) ' is the latest month -
      of the ten months with the lowest sales.')
    SHOW JOINCHARS('the months range from ' STATMIN(month) ' to '-  
      STATMAX(month)) 

These statements produce the following sales report.

    Dec96 is the latest month of the ten months with the lowest sales.
    The months range from Jan95 to Dec96

When you used STATLAST instead of STATMAX, you could have produced a different value, because the LIMIT command arranged the `month` values by increasing sales rather than chronologically.

### 8.110 STATMIN

The STATMIN function returns the earliest value in the current status list of a dimension or a dimension surrogate, or in a valueset.

#### Return Value

Either a dimension or surrogate value or an `INTEGER` that indicates the position of the value in the default status list of the dimension or surrogate. The return value varies depending on the dimension argument and the object receiving the return value. See "Automatic Data Type Conversion of Values Returned by STATMIN".

#### Syntax

STATMIN(dimension)

#### Parameters

dimension
A text expression whose value is the name of a dimension, dimension surrogate, or valueset.

#### Usage Notes

Automatic Data Type Conversion of Values Returned by STATMIN

The dimension value that STATMIN returns is converted, if necessary, to a number or a text value. For example, suppose the status of `month` is limited to `Jun95` to `Dec95`, and `Jun95` is the sixth `month` value in the default status list. The value of `STATMIN(month)` can be assigned either to a text variable, a numeric variable, or DATE variable.

The following statements

    DEFINE textvar TEXT
    textvar = STATMIN(month)
    SHOW textvar

produce this output.

    Jun95

In contrast, these statements

    DEFINE intvar INTEGER
    intvar = STATMIN(month)
    SHOW intvar

produce this output.

    6

#### Examples

Example 8-114 Using STATMIN in a Title

The following statements from a program use STATMIN to determine the earliest of the 10 months with the highest total sales.

    LIMIT month TO TOP 10 BASEDON TOTAL(sales, month)
    SHOW JOINCHARS(STATMIN(month) ' is the earliest of the - 
      ten months with the highest sales.')
    SHOW JOINCHARS( 'The months range from ' statmin(month) ' TO '- 
      statmax(month) )

The preceding statements produce the following sales report.

    May95 is the earliest of the ten months with the highest sales.
    The months range from May95 to Sep96

Example 8-115 Comparing to STATFIRST

In the following example, you can see the difference between STATMIN and STATFIRST, which returns the first value in the current status list.

Assume that you issue the following statements.

    LIMIT month TO TOP 10 BASEDON TOTAL(sales, month)
    REPORT WIDTH 20 TOTAL(sales, month)

When the proceeding statements execute, the following report is produced.

    MONTH          TOTAL(SALES, MONTH) 
    -------------- --------------------
    Jul96                  3,647,085.39
    Jun96                  3,458,438.30
    Jul95                  3,414,210.05
    Aug96                  3,246,601.97
    Jun95                  3,228,824.80
    Sep96                  3,215,883.93
    May96                  3,112,854.59
    Aug95                  3,044,694.29
    Sep95                  3,006,242.58
    May95                  2,908,539.45

Notice that the `month` values in this report are arranged by decreasing sales rather than chronologically, and this is now the order in which they occur in the status list:

- STATMIN gives the chronologically first value in the status (though it is positionally last) as illustrated in the following statement and output.

      SHOW STATMIN(month)
      May95
       

- STATFIRST gives the value that is positionally first in the status (though it is chronologically eighth) as illustrated in the following statement and output.

      SHOW STATFIRST(month)
      Jul96

### 8.111 STATRANK

The STATRANK function returns the position of a dimension or dimension surrogate value in the current status list or in a valueset.

#### Return Value

INTEGER

#### Syntax

STATRANK(dimension \[value\])

#### Parameters

dimension
A text expression whose value is the name of a dimension, dimension surrogate, or valueset.

value
The value you want to check, which is an appropriate data type for dimension. For example, value can be a text expression for an ID or TEXT dimension, an `INTEGER` for an INTEGER dimension, a date for a time dimension, or a combination of values enclosed by angle brackets for conjoint or concat dimensions. The value of a text expression must have the same capitalization as the actual dimension value. When you use a text expression, it must be a single-line value.

When you specify the value of a conjoint dimension, be sure to enclose the value in angle brackets, and separate the base dimension values with a comma and space. When you specify the value of a concat dimension, be sure to enclose the value in angle brackets, and separate the base dimension name from the value with a colon and space.

When you do not specify value, STATRANK returns the position of the current value. When you specify the name of a valid dimension value that is not in the current status list or in the valueset, STATRANK returns `NA`.

#### Examples

Example 8-116 Using STATRANK to Identify Position Numbers

Suppose you want to produce a report of the top five months by total sales, displayed in order as a numbered list. You can use STATRANK to number each month. Assume that you have written a report program with the following definition and contents.

    DEFINE sales.rpt PROGRAM
    PROGRAM
    LIMIT month TO TOP 5 BASEDON TOTAL(sales, month)
    SHOW 'Top five months by total sales:'
    for month
        ROW WIDTH 4 JOINCHARS(STATRANK(month) '.') WIDTH 5 month
    END

The report program produces the following output.

    Top five months by total sales:
    1.   Jul96
    2.   Jun96
    3.   Jul95
    4.   Aug96
    5.   Jun95

After executing the `sales.rpt` program, you can use a SHOW statement with the STATRANK function to learn the position of a particular month within the top five months by total sales.

The following statement

    SHOW STATRANK(month Jun96)

produces this output.

    2

Example 8-117 Using STATRANK When the Dimension Is a Conjoint Dimension

When the dimension that you specify is a conjoint dimension, then the entire value must be enclosed in single quotes.

For example, suppose the analytic workspace has a `region` dimension and a `product` dimension. The `region` dimension values include` East`, `Central`, and `West`. The `product` dimension values include `Tents`, `Canoes`, and `Racquets`.

The following statements define a conjoint dimension, and add values to it.

    DEFINE reg.prod DIMENSION <region product>
    MAINTAIN reg.prod ADD <'East', 'Tents'> <'West', 'Canoes'>

To specify base positions, use a statement such as the following. Because the position of `East` in the `region` dimension is `1` and the position of `Tents` in the `product` dimension is `1`, the following statement returns the position of the corresponding `reg.prod` value.

    SHOW STATRANK(reg.prod '<1, 1>')

    1

To specify base text values, use a statement such as the following.

    SHOW STATRANK(reg.prod '<\'East\', \'Tents\'>')

    1

Example 8-118 Using STATRANK When the Dimension Is a Concat Dimension

When the dimension that you specify is a concat dimension, then the entire value must be enclosed in single quotes. The following statement defines a concat dimension named `reg.prod.ccdim` that has as its base dimensions `region` and `product`.

    DEFINE reg.prod.ccdim DIMENSION CONCAT(region product)

A report of `reg.prod.ccdim` returns the following.

    REG.PROD.CCDIM
    ----------------------
    <Region: East>
    <Region: Central>
    <Region: West>
    <Product: Tents>
    <Product: Canoes>
    <Product: Racquets>

To specify a base dimension position, use a statement such as the following. Because the position of `racquets` in the `product` dimension is `3`, the statement returns the position in `reg.prod.ccdim` of the `<product:` `Racquets>` value.

    SHOW STATRANK(reg.prod.ccdim '<product: 3>')

    6

To specify base dimension text values, use a statement such as the following.

    SHOW STATRANK(reg.prod.ccdim '<product: Tents>')

    4

### 8.112 STATVAL

The STATVAL function returns the dimension value that corresponds to a specified position in the current status list of a dimension or a dimension surrogate, or in a valueset.

#### Return Value

The data type returned by STATVAL is either the data type of the dimension or dimension surrogate value or an `INTEGER` that indicates its position in the default status list of the dimension. The dimension value that STATVAL returns is converted to a number or a text value, as appropriate to the context. To ensure that STATVAL returns an `INTEGER` value, specify the INTEGER keyword. See Example 8-120.

#### Syntax

STATVAL(dimension position \[INTEGER\])

#### Parameters

dimension
A text expression whose value is the name of a dimension, a dimension surrogate, or a valueset.

position
An `INTEGER` expression that specifies the position in the current status list of a dimension or a valueset. When you specify a position that has no values, STATVAL returns `NA`.

INTEGER
Specifies that STATVAL must return an `INTEGER` that represents the position of the dimension value in the default status list.

#### Usage Notes

STATVAL in a FOR Loop

In a FOR loop over a dimension, the status is limited to a single dimension value for each iteration of the loop. Therefore, STATVAL has a value only for position `1`. For other positions, STATVAL returns `NA`.

#### Examples

Example 8-119 STAVAL with Qualified Data References

Suppose you want to know the sales figures for the month ranked fifth among the 10 months with the highest total sales. After limiting `month` to the `TOP` `10`, use STATVAL in a qualified data reference to produce sales figures for the month ranked fifth.

    LIMIT month TO TOP 10 BASEDON TOTAL(sales, month)
    REPORT month

These statements produce the following report.

    MONTH
    --------------
    Jul96
    Jun96
    Jul95
    Aug96
    Jun95
    Sep96
    May96
    Aug95
    Sep95
    MAY95

Using STATVAL in the following REPORT statement produces a different report.

    REPORT W 8 DOWN district HEADING -
       JOINCHARS('Sales: 5th of Top Ten - ' STATVAL(month 5)) -
       sales(month STATVAL(month 5))

This is the report produced by the preceding statement.

             ------------Sales: 5th of Top Ten - Jun95-------------
             -----------------------PRODUCT------------------------
    DISTRICT   Tents      Canoes    Racquets  Sportswear  Footwear
    -------- ---------- ---------- ---------- ---------- ----------
    Boston    88,996.35 147,412.44  90,840.60  75,206.30 144,162.66
    Atlanta  110,765.24 106,327.17 109,695.31 155,652.78 146,364.99
    Chicago   70,908.96 108,039.05 100,030.29 104,900.66 148,386.81
    Dallas   128,692.56  71,899.23 176,452.58 164,823.10  32,421.25
    Denver    91,717.46  99,099.20 140,961.37  99,951.60  70,149.77
    Seattle  113,806.48 143,037.62  54,926.87  57,739.03  75,457.04

Notice that the qualified data reference in the following statement means "sales for the fifth month in the default status of `month`."

    sales(month 5)

While the qualified data reference in the following statement means "sales for the fifth month in the current status of `month`."

    sales(month STATVAL(month 5))

The following statements show the different values that are returned for a qualified data reference of `month` and for STATVAL with `month` as an argument.

    SHOW month(month 5)
    SHOW STATVAL(month 5)

The preceding statements produce the following output.

    May95
    Jun95

Example 8-120 Ensuring that STATVAL Returns an INTEGER

Depending on the context, STATVAL may return an `INTEGER` value without your specifying the INTEGER keyword.

The following statements

    LIMIT month TO 'Jun95' TO 'Dec95'
    SHOW STATVAL(month 3)

produce this output.

    Aug95

With the INTEGER keyword,

    SHOW STATVAL(month 3 INTEGER)

the following output is produced.

    8

### 8.113 STDDEV

The STDDEV function calculates the standard deviation of the values of an expression.

When STDDEV is affected by the NASKIP option. When NASKIP is set to `YES` (the default), STDDEV ignores `NA` values and returns the standard deviation of the values that are not `NA`. When NASKIP is set to `NO`, STDDEV returns `NA` when any value in the calculation is `NA`. When all data values for a calculation are `NA`, STDDEV returns `NA` for either setting of NASKIP.

#### Return Value

DECIMAL

#### Syntax

STDDEV(expression \[dimensions\])

#### Parameters

expression
The numeric expression whose standard deviation is to be calculated.

dimensions
The dimensions of the result. By default, STDDEV returns a single value. When you indicate one or more dimensions for the results, STDDEV calculates a standard deviation along the specified dimension(s) and returns an array of values. Each dimension must be either a dimension of expression or related to one of its dimensions. When it is a related dimension, you can specify the name of the relation instead of the dimension name which enables you to choose the relation to use when there are multiple relations between dimensions.

#### Usage Notes

Using STDDEV With an Expression Dimensioned by a DWMQY Dimension

When expression is dimensioned by a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, you can specify any other dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR as a related dimension. Oracle OLAP uses the implicit relation between the dimensions. To control the mapping of one dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR to another (for example, from weeks to months), you can define an explicit relation between the two dimensions and specify the name of the relation as the dimension argument to the STDDEV function.

For each time period in the related dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR, Oracle OLAP calculates the standard deviation of the data values of the source time periods that end in the target time period. This method is used regardless of which dimension has the more aggregate time periods. To control the way in which data is aggregated or allocated between the periods of two dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR, you can use the TCONVERT function.

#### Examples

Example 8-121 Calculating the Standard Deviation of Monthly Sales

This example calculates the average number of tents sold during the first three months of 1996, along with the standard deviation from that average.

    LIMIT district TO ALL
    LIMIT month TO 'Jan96' TO 'Mar96'
    LIMIT product TO 'Tents'
    REPORT HEADING 'Average' AVERAGE(units month) -
       HEADING 'Stddev'STDDEV(units months)

These statements produce the following output.

    MONTH           Average     Stddev
    -------------- ---------- ----------
    Jan96              262.33      49.32
    Feb96              247.83      57.37
    Mar96              320.50      68.17

### 8.114 SUBSTR functions

The SUBSTR functions (SUBSTR, SUBSTRB, and SUBSTRC) return a portion of a string, beginning at a specified position in the string.

The functions vary in how they calculate the length of the substring to return.

- SUBSTR calculates lengths using characters as defined by the input character set.

- SUBSTRB calculates lengths using bytes.

- SUBSTRC calculates lengths using Unicode complete characters.

#### Return Value

The return value is the same data type as string.

#### Syntax

{SUBSTR \| SUBSTRB \| SUBSTRC }(string, position \[, substring_length \])

#### Parameters

string
A text expression that is the base string from which the substring is created.

position
The position at which the first character of the returned string begins.

- When position is `0` (zero), then it is treated as` 1`.

- When position is positive, then the function counts from the beginning of string to find the first character.

- When position is negative, then the function counts backward from the end of string.

substring_length
The length of the returned string. SUBSTR calculates lengths using characters as defined by the input character set. SUBSTRB uses bytes instead of characters. SUBSTRC uses Unicode complete characters.

When you do not specify a value for this argument, then the function returns all characters to the end of string. If you specify a value that is less than `1` or a value that is greater than the number of characters in the string, then the function returns `NA`.

#### Examples

Example 8-122 Retrieving a Character Substring

The following example returns the specified substrings of "abcdefg".

    SHOW SUBSTR('abcdefg',3,4)
    cdef

    SHOW SUBSTR('abcdefg',-5,4)
    cdef

Example 8-123 Retrieving a Substring Using Bytes

Assume an AL32UTF8 database character set. For the string Fußball, the following statement returns a substring 4 bytes long, beginning with the second byte.

    SHOW SUBSTRB('Fußball',2,4)
    ußb

### 8.115 SUBTOTAL

The SUBTOTAL function returns the value of one subtotal accumulated in a report. You normally use the SUBTOTAL function in a ROW command to include a subtotal or grand total in the report. Because Oracle OLAP maintains 32 running totals for each column, you can include up to 32 levels of subtotals

**Note:**

In a REPORT statement, use the GRANDTOTALS and SUBTOTALS keywords to include rows of grand totals and subtotals.

#### Return Value

DECIMAL

#### Syntax

SUBTOTAL(n)

#### Parameters

n
An `INTEGER` value that indicates the level of a running total for each numeric column in a report. For example, a "Total" may be a level 1 subtotal and a "Grand Total" may be a level 2 subtotal. Because it is possible to have up to 32 levels of running totals in a column, n must be an `INTEGER` between 1 and 32. SUBTOTAL returns the value of this subtotal for the current column and then resets the value of subtotal n to zero.

The numbers by which the 32 subtotals are referenced (1 to 32) have no intrinsic significance; all the subtotals are the same until you reference them.

#### Usage Notes

Resetting Subtotals Automatically

When you use the SUBTOTAL function in a ROW command to include a subtotal of the current column, the subtotal at that level is reset to zero.

Resetting Subtotals with ZEROTOTAL

When you use the ROW command to produce a report, you can use a ZEROTOTAL statement to reset any subtotal of any column to zero.Typically, use ZEROTOTAL this at the beginning of a report program to make sure all totals begin at zero.

NA Values and SUBTOTAL

SUBTOTAL ignores `NA` values. When all values are `NA`, SUBTOTAL returns zero.

#### Examples

Example 8-124 Calculating Subtotals and Grand Totals in a Report

In a sales report, suppose you want to show a subtotal for each region. You also want to see a grand total of all sales at the end of the report. You can use `SUBTOTAL(1)` to produce the subtotal for each region. This subtotal is reset to `0` each time you use it, so it provides a separate subtotal for each region. At the end of the report you can use `SUBTOTAL(2)` to produce the grand total. Because you have not yet used it in your report, it holds a total of the sales figures for all regions.

    LIMIT month TO FIRST 3
    LIMIT region TO ALL
    ZEROTOTAL ALL
    FOR region
       DO 
       ROW region
       LIMIT DISTRICT TO region
       FOR district
          DO
          ROW INDENT 5 district ACROSS month: sales
          DOEND
       ROW INDENT 5 'Total' ACROSS month: OVER '-' SUBTOTAL(1)
       BLANK
       DOEND
    ROW 'Grand Total' ACROSS month: OVER '=' SUBTOTAL(2)

The program produces the following output.

    East
         Boston     32,153.52  32,536.30  43,062.75
         Atlanta    40,674.20  44,236.55  51,227.06
                   ---------- ---------- ----------
         Total      72,827.72  76,772.85  94,289.81
    Central
         Chicago    29,098.94  29,010.20  39,540.89
         Dallas     47,747.98  50,166.81  67,075.44
                   ---------- ---------- ----------
         Total      76,846.92  79,177.01 106,616.33
    West
         Denver     36,494.25  33,658.24  45,303.93
         Seattle    43,568.02  41,191.28  51,547.23
                   ---------- ---------- ----------
         Total      80,062.27  74,849.52  96,851.16
     
                   ========== ========== ==========
    Grand Total    229,736.91 230,799.38 297,757.30

### 8.116 SYS_CONTEXT

The SYS_CONTEXT function returns the value of parameter associated with the context namespace.

**See Also:**

For more information, see the SYS_CONTEXT function in [Oracle Database SQL Language Reference](../sqlrf/SYS_CONTEXT.md)

#### Return Values

VARCHAR2.

#### Syntax

SYS_CONTEXT(namespace, parameter \[, length \])

#### Parameters

namespace
A text expression that specifies a namespace which is a valid SQL identifier. The context namespace must have been created, and the associated parameter and its value must also have been set using the `DBMS_SESSION.set_context` procedure.

parameter
A text expression that specifies an attribute associated with a namespace. This parameter and its value must have previously been set using the `DBMS_SESSION.set_context` procedure. The parameter is not case sensitive, but it cannot exceed 30 bytes in length.

length
A numeric expression that specifies the maximum size of the return value. The value that you specify must be a `NUMBER` (or a value that can be implicitly converted to `NUMBER`) and in the range of 1 to 4000 bytes,. If you specify an invalid value, then Oracle OLAP ignores it and uses the default value of 256 bytes.

#### Usage Notes

USERENV Built-In Namespace

Oracle provides a built-in namespace called `USERENV`, which describes the current session.

For more information on the predefined parameters of namespace `USERENV`, see the SYS_CONTEXT function in [Oracle Database SQL Language Reference](../sqlrf/SYS_CONTEXT.md).

#### Examples

Example 8-125 Retrieving the Name of the User of the Session

The following hypothetical example retrieves the value `JOHNSMITH` which is the name of the user who logged onto the database.

    SHOW SYS_CONTEXT ('USERENV', 'SESSION_USER')
    JOHNSMITH

### 8.117 SYSDATE

The SYSDATE function returns the current date and time as a DATETIME value. The format of the date is controlled by the NLS_DATE_FORMAT option. The default DATETIME format (`DD-MM-RR`) does not display the time.

#### Return Value

DATETIME

#### Syntax

SYSDATE

#### Examples

Example 8-126 Displaying the Current Date

The following statement:

    SHOW SYSDATE

displays the current date:

    08-Sep-00

### 8.118 SYSINFO

The SYSINFO function provides information about the Oracle user ID for the current session.

#### Return Value

TEXT

#### Syntax

SYSINFO (keyword)

where `keyword` is one of the following:

- `USER`
- `ROLES`
- `PROFILES`
- `HOSTNAME`
- `OSUSER`
- `INSTNAME`
- `PID`
- `PROGNAME`
- `CHOSTNAME`
- `COSUSER`
- `TERMNAME`

#### Parameters

USER
Returns a TEXT value that indicates the user ID under which the Oracle Database session is running which is the same value that is returned by USERID.

ROLES
Returns a multiline TEXT value that lists the roles that apply to the user ID of the session.

PROFILES
Returns a multiline TEXT value that lists the profiles that apply to the user ID of the session.

OSUSER
Returns TEXT value that indicates the operating system user name under which the Oracle Database server is running.

INSTNAME
Returns a TEXT value that is the instance name of the Oracle Database server.

PID
Returns a TEXT value that is the operating system id number of your Oracle Database session.

HOSTNAME
Returns a TEXT value that is the host name of the Oracle Database server.

PROGNAME
Returns a TEXT value that identifies the client that is connecting to the database.

CHOSTNAME
Returns a TEXT value that is the host name of the client.

COSUSER
Returns a TEXT value that is the operating system user name of the client.

TERMNAME
Returns a TEXT value that is the terminal name of the client.

#### Examples

Example 8-127 Obtaining the User ID

You can use the SYSINFO function to obtain the user of the current session.

    SHOW SYSINFO(USER)

produces output like the following.

    Scott

### 8.119 SYSTEM

The SYSTEM function identifies the platform on which Oracle OLAP is running.

#### Data Type

TEXT

#### Syntax

SYSTEM

#### Usage Notes

Relevance of the Platform

Because Oracle OLAP is incorporated in Oracle Database, the operating system on which it is running should not be an important factor in its behavior.

**Note:**

All references to external files are made through directory objects, which are not platform specific

#### Examples

Example 8-128 Displaying the Platform

Issuing the following SYSTEM statement on Intel NT returns the value `NTX86`.

    SHOW SYSTEM

    NTX86

### 8.120 SYSTIMESTAMP

The SYSTIMESTAMP function returns the current date and time as a TIMESTAMP_TZ value.

#### Data Type

TIMESTAMP_TZ

#### Syntax

SYSTIMESTAMP

#### Examples

Example 8-129 Retrieving the current date and time as a TIMESTAMP value.

    SHOW systimestamp
    26-APR-07 02.18.47.030587 PM -04:00

### 8.121 TALLY

The TALLY function counts the number of values of a dimension that correspond to each value of one or more related dimensions.

#### Return Value

INTEGER

#### Syntax

TALLY(dimension \[related-dimensions\])

#### Parameters

dimension
A dimension whose values are to be counted. When you specify related-dimensions, TALLY counts the number of values of dimension that correspond to each value of a single related dimension, or to each combination of values of two or more related dimensions. When you do not specify related-dimensions, TALLY counts the number of values in the dimension. Only values in the current status of dimension are counted.

related-dimensions
One or more related dimensions for the results. These must be related to dimension. Alternatively, you can specify the name of the relation instead of the dimension name which enables you to choose which relation is used when there are multiple relations between dimensions. When no related-dimensions are specified, TALLY returns the total number of values in the current status of dimension.

#### Usage Notes

TALLY with NA

TALLY returns `NA` for any related-dimension position that has no dimension values corresponding to it.

TALLY with DWMQY Dimensions

When expression is dimensioned by a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, you can specify any other dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR as a related-dimension. Oracle OLAP uses the implicit relation between the dimensions. To control the mapping of one DAY, WEEK, MONTH, QUARTER, or YEAR dimension to another (for example, from weeks to months), you can define an explicit relation between the two dimensions and specify the name of the relation as the related-dimension argument to the TALLY function.

For each time period in the related dimension, Oracle OLAP tallies all the source time periods that end in the target time period. This method is used regardless of which dimension has the more aggregate time periods.

#### Examples

Example 8-130 Breaking Out TALLY Results

Here you use TALLY to determine how many products are produced by each division. The `division.product` relation records the division to which each product belongs. The following is a report of `division.product`.

    PRODUCT          DIVISION.PRODUCT
    ---------------------------------
    Tents          Camping
    Canoes         Camping
    Racquets       Sporting
    Sportswear     Clothing
    Footwear       Clothing

The following statement includes TALLY to present the number of products produced by each division.

    REPORT HEADING 'Products' TALLY(product, division)

The statement produces this report.

    DIVISION        Products
    -------------------------
    Camping                 2
    Sporting                1
    Clothing                2

### 8.122 TAN

The TAN function calculates the tangent of an angle expression.

#### Return Value

NUMBER

#### Syntax

TAN(expression)

#### Parameters

expression
A numeric expression that contains an angle value, which is specified in radians.

#### Examples

Example 8-131 Calculating the Tangent of an Angle

This example calculates the tangent of an angle of `1` radian. The statements

    DECIMALS = 5
    SHOW TAN(1)

produce the following result.

    1.55741

### 8.123 TANH

The TANH function calculates the hyperbolic tangent of an angle expression.

#### Return Value

NUMBER

#### Syntax

TANH(expression)

#### Parameters

expression
A numeric expression that contains an angle value, which is specified in radians.

#### Examples

Example 8-132 Calculating the Hyperbolic Tangent of an Angle

This example calculates the hyperbolic tangent of an angle of `1` radian. The statements

    DECIMALS = 5
    SHOW TANH(1)

produce the following result.

    0.76159

### 8.124 TCONVERT

The TCONVERT function converts time-series data from one dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR to another dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR. You can specify an aggregation method or an allocation method to use in the conversion.

**Note:**

You can only use this function with dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR.You cannot use this function for time dimensions that are implemented as hierarchical dimensions of type TEXT.

#### Return Value

The value returned by the TCONVERT function depends on the type of conversion you specify and the type of the dimension being converted.

#### Syntax

TCONVERT(expression time-dimension method \[method\])

where the syntax for `method` varies by method type:

-      `SUM|AVERAGE|LAST [BY PERIOD|BY DAY] [STATUS|NOSTATUS]`
-
-      `SPLIT|REPEAT|INTERPOLATE [BY PERIOD|BY DAY]`

#### Parameters

expression
An expression whose values you want to convert. Expression must be dimensioned by a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR. This dimension is referred to as the source dimension. Usually expression is numeric, but with some conversion methods you can also convert text data. See "Converting Text Data".

time-dimension
The DAY, WEEK, MONTH, QUARTER, or YEAR dimension to which you want to convert the expression. This dimension is referred to as the target dimension.

method
The method to use for converting data from the source dimension to the target dimension. You can specify an aggregation method or an allocation method:

- Aggregation methods are SUM, AVERAGE, and LAST. They are typically used to convert data from smaller time periods to larger time periods (for example, months to years).

- Allocation methods are SPLIT, REPEAT, and INTERPOLATE. They are typically used to convert data from larger to smaller time periods (for example, years to quarters). The allocation methods all use the full default status of the source dimension to determine the periods that contribute to the allocation.

Except for a case in which the source dimension and target dimension have overlapping periods of equal length (as with a calendar year and a fiscal year), you can specify both an aggregation method and an allocation method. See "Compatible Aggregation and Allocation Methods" and "Using Both Aggregation and Allocation".

For all methods, results are calculated for the values in the current status of the target dimension.

The results you obtain depend on the method you specify and on whether you convert data between dimensions with periods of equal length or unequal length. See "Using Both Aggregation and Allocation", "Overlapping Periods of Equal Length", and "Substituting a Compatible Method".

SUM \[BY PERIOD\]
Aggregates data to a target period by totaling the data of the contributing source periods. For each target period, SUM BY PERIOD returns the total for all the source periods that end in the target period. SUM uses the implicit relation between the source and target dimensions.

SUM BY DAY
Weights each source value according to the portion of target days it represents. For each target period, SUM BY DAY multiplies each contributing source period value by a weighting factor that has this form where source-days-in-target is the Number of source-period days that actually fall in target period and total-days-in-period is the total number of days in source period:

source-days-in-target / total-days-in-period

SUM BY DAY then returns the total of these weighted source values. When you use SUM BY DAY, the value of an individual source period may be apportioned across adjacent target periods.

For example, suppose you convert weekly data to monthly data. When three days of a week fall in January and four fall in February, then SUM BY DAY adds `3/7` of the data for that week to the January total and `4/7` to the February total. In contrast, SUM BY PERIOD adds the entire data value for the week to the February total (because the week ends in February).

As another example, suppose you want to convert calendar year data to a fiscal year ending in June. Calendar year 1996 (`Cal96`) is the only calendar year that ends in fiscal year 1997 (`Fy97`). The SUM BY PERIOD method assigns the value for `Cal96` to `Fy97`. In contrast, SUM BY DAY apportions the `Cal96` value to the fiscal years `Fy96` and `Fy97`, according to the number of calendar days that fall in each fiscal year. Of the 366 days of `Cal96`, 182 days (January 1 - June 30) fall in `Fy96` and 184 days (July 1 - December 31) fall in `Fy97`. Therefore, for the `CAL96` data, SUM BY DAY uses a weighting factor of `182/366` for `Fy96` and a factor of `184/366` for `Fy97`.

AVERAGE \[BY PERIOD\]
Aggregates data to a target period by averaging the data of the contributing source periods. For each target period, AVERAGE BY PERIOD adds up the data from all the source periods that end within the target period and divides this total by the number of source periods. AVERAGE BY PERIOD uses the implicit relation between the two time dimensions.

AVERAGE BY DAY
Weights the value of each contributing source period by the portion of target days it represents. For each target period, AVERAGE BY DAY multiplies the value of each source period by the number of days of that source period that actually fall within the target period. The average is then calculated by adding these weighted source values and dividing by the total number of days in the target period. When you use AVERAGE BY DAY, the value of a single source period may be apportioned across adjacent target periods.

LAST \[BY PERIOD\]
For each target period, LAST BY PERIOD returns the data value from the last source period that ends within the target period. It uses the implicit relation between the source and target dimensions.

LAST BY DAY
Has the same effect as LAST BY PERIOD, provided you are converting data from smaller periods to larger periods. See "Substituting a Compatible Method".

STATUS
Indicates that the current status of the source dimension is used. It is the default for the SUM and AVERAGE methods.

NOSTATUS
Indicates that the full default status of the source dimension is used. It is the default for the LAST method.

SPLIT \[BY PERIOD\]
Allocates data to target periods by splitting the data from the source periods. SPLIT BY PERIOD divides a source value evenly among the target periods that end in that source period. SPLIT BY PERIOD uses the implicit relation between the two DAY, WEEK, MONTH, QUARTER, or YEAR dimensions.

SPLIT BY DAY
Weights each source value according to the portion of target days it represents. For each target period, SPLIT BY DAY multiplies each contributing source period value by a weighting factor that has this form where target-days-in-source is the Number of target-period days that actually fall in source period and total-period-days is the total number of days in source period:

target-days-in-source / total-period-days

SPLIT BY DAY then returns the total of these weighted source values. When you use SPLIT BY DAY, the value of an individual source period may be apportioned across adjacent target periods.

REPEAT
For each target period, REPEAT returns the value of a source period. The target periods are the periods that end within the source period. REPEAT uses the implicit relation between the source and target dimensions. REPEAT BY DAY has the same effect as REPEAT BY PERIOD, provided you are converting data from larger time periods to smaller time periods. See "Substituting a Compatible Method".

INTERPOLATE \[BY PERIOD\]
The INTERPOLATE method allocates data to target periods by first calculating the difference between the values of the current and previous source periods, and then splitting the result incrementally over the target periods. INTERPOLATE divides the difference between the current and previous source period values by the number of target periods that end in the source period, and it increments each target period by this amount.

INTERPOLATE BY DAY
For each target period, adds the value of the previous source period to a value that is calculated as follows where end-days is the number of days from end of previous source period to end of current target period and period-days is the total number of days in current source period:

(end-days / period-days) \* (current-source-value - previous-source-value)

When a target period has days that fall in multiple source periods, a similar calculation is made for each source period.

#### Usage Notes

Dimensions of the Result Returned by TCONVERT

The results returned by TCONVERT are dimensioned by the target DAY, WEEK, MONTH, QUARTER, or YEAR dimension and by all of expression dimensions that are not DAY, WEEK, MONTH, QUARTER, or YEAR dimensions.

Status Used with Allocation

The STATUS and NOSTATUS keywords have no effect with the allocation methods. The allocation methods always use the full default status of the source dimension to determine the contributing periods.

Compatible Aggregation and Allocation Methods

Except for a case in which the source dimension and the target dimension have overlapping periods of equal length, you can specify both an aggregation method and an allocation method. However, the two methods must be compatible. The following table shows the compatible methods:

Table 8-15 Compatible Aggregation and Allocation Methods

| Aggregation | Compatible Allocation |
|:------------|:----------------------|
| SUM         | SPLIT                 |
| AVERAGE     | REPEAT                |
| LAST        | INTERPOLATE           |

When you specify both an aggregation method and an allocation method, you can specify BY PERIOD or BY DAY with either method. When you specify BY PERIOD (explicitly or by default) for one method and BY DAY for the other method, BY DAY takes precedence.

Using Both Aggregation and Allocation

When you specify both an aggregation method and a compatible allocation method, Oracle OLAP handles this as follows:

- When you convert data from smaller periods to larger periods, Oracle OLAP uses the aggregation method (with BY DAY, if specified for either method).

- When you convert data from larger periods to smaller periods, Oracle OLAP uses the allocation method (with BY DAY, if specified for either method).

- When you convert data between dimensions that have non-overlapping periods of equal length, such as a quarter ending in March and a quarter ending in June, the results of the aggregation and allocation methods are identical.

Overlapping Periods of Equal Length

When you convert data between two dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR that have overlapping periods of equal length, such as a calendar year and a fiscal year, or a quarter ending in March and a quarter ending in April, you must specify either an aggregation method or allocation method, but not both. For these dimensions, the compatible aggregation and allocation methods may yield different results.

For example, when you convert data from a calendar year dimension to a fiscal year dimension that ends in June, the SUM and SPLIT methods return different results:

- The SUM method totals up the data from the source periods that end in the target period. Because the calendar year 1996 ends in fiscal year 1997, the SUM method assigns the value for calendar year 1996 to fiscal year 1997.

- The SPLIT method allocates a source data value to the target periods that end in the source period. Because the fiscal year 1996 ends in calendar year 1996, the SPLIT method assigns the value for calendar year 1996 to fiscal year 1996.

Substituting a Compatible Method

When you specify a single conversion method, and you use an aggregation method to convert data from a larger period to a smaller period (for example, from months to weeks) Oracle OLAP automatically uses the compatible allocation method instead of the specified aggregation method. Similarly, when you use an allocation method to convert data from a smaller period to a larger period, Oracle OLAP automatically uses the compatible aggregation method. See "Compatible Aggregation and Allocation Methods".

Data Type of the Result

When possible, TCONVERT returns results that have the same data type as expression. When expression is DECIMAL, the results are always DECIMAL. When expression is INTEGER, the results are INTEGER when the required calculations do not involve division. For example, when two dimensions are aligned (that is, they have the same phase and are based on the same periods, such as a calendar year dimension and a quarter dimension ending in December), the result is INTEGER when you use the REPEAT method to convert an INTEGER expression from larger periods to smaller periods. Similarly, the result is INTEGER when you use the SUM or LAST method to convert the expression from smaller to larger periods.

Converting Text Data

You can also use TCONVERT to convert the values of a text expression when no numeric calculations are needed for the conversion. For aligned dimensions, for example, you can use the LAST method to convert text values from smaller periods to larger periods, and you can use the REPEAT method to convert text values from larger periods to smaller periods. You can also use the LAST and REPEAT methods to convert text data between dimensions that have periods of equal length. When you attempt to convert a text expression with a method that requires numeric calculations, you receive an error message.

Methods for Financial Data

When you work with financial data, you can use an appropriate conversion method for each type of data. The following table gives some examples:

Table 8-16 Examples of Conversion Methods for Different Types of Financial Data

| Type of Financial Data | Conversion       | Conversion Method |
|:-----------------------|:-----------------|:------------------|
| Revenue or expenses    | Month to year    | SUM               |
| Stock quotations       | Day to quarter   | AVERAGE           |
| Balance sheet items    | Month to quarter | LAST              |
| Quarterly tax payment  | Year to quarter  | SPLIT BY PERIOD   |
| Money supply           | Year to quarter  | INTERPOLATE       |

#### How TCONVERT Handles NA Values

TCONVERT is affected by the NASKIP option. When NASKIP is set to `NO`, TCONVERT returns an `NA` value for any target period that receives contributions from a source period with an `NA` value.

#### Examples

Example 8-133 Splitting Data Across Quarters

This example shows the effects of using the SPLIT method and the SPLIT BY DAY method to allocate an annual budget revenue figure of \$120,000 across the quarters of the year 1996. An existing `year` dimension is the source dimension and an existing `quarter` dimension is the target dimension.

The following statements

    DEFINE budget.revenue DECIMAL <year>
    budget.revenue(year 'Yr96') = 120000
    LIMIT quarter TO year 'Yr96'
    REPORT W 12 HEADING 'Split Evenly' -
       TCONVERT(budget.revenue quarter SPLIT) -
       W 12 HEADING 'Split by Day' -
       TCONVERT(budget.revenue quarter Split by day)

produce this report.

    QUARTER        Split Evenly Split by Day
    -------------- ------------ ------------
    Q1.96             30,000.00    29,836.07
    Q2.96             30,000.00    29,836.07
    Q3.96             30,000.00    30,163.93
    Q4.96             30,000.00    30,163.93

Example 8-134 Aggregating Weekly Data to Monthly Using TCONVERT

This example aggregates weekly data to monthly data. First, define a week dimension named `week` and add weeks that include the dates January 1, 1996 and June 30, 1996 (Oracle OLAP automatically adds the intervening weeks).

    DEFINE week DIMENSION WEEK
    MAINTAIN week ADD '01Jan96' '30Jun96'

Next, define a variable named `weekvar`, dimensioned by `week`, and assign a value of `7` to each week.

    DEFINE weekvar DECIMAL <week>
    weekvar = 7

The following statements show that December 31, 1995 is the beginning date of the first week for which `weekvar` contains non-`NA` data and that July 6, 1996 is the ending date of the final week for which `weekvar` contains non-`NA` data.

    SHOW BEGINDATE(weekvar)
    SHOW ENDDATE(weekvar)

The statements produce this output.

    31Dec95
    06Jul96

With these beginning and ending dates, when the data is converted to monthly data, it is aggregated over the months `Dec95` through `Jul96`. The following statements show the effects of using the SUM method and the SUM BY DAY method to convert the weekly `weekvar` data to monthly data.

    LIMIT month TO 'Jan96' TO 'Jul96'
    REPORT HEADING 'Sum' TCONVERT(weekvar month SUM) -
       HEADING 'Sum by Day' -
       TCONVERT(weekvar month SUM BY day)

These statements produce the following report.

    MONTH              Sum    Sum by Day
    -------------- ---------- ----------
    Jan96               28.00      31.00
    Feb96               28.00      29.00
    Mar96               35.00      31.00
    Apr96               28.00      30.00
    May96               28.00      31.00
    Jun96               35.00      30.00
    Jul96                7.00       6.00

### 8.125 TEXTFILL

The TEXTFILL function reformats a text value to fit compactly into lines of a specified width, regardless of its current format. TEXTFILL is commonly used to reformat text with an unnecessarily ragged right margin or with a bad line width.

**Note:**

TEXTFILL joins lines of text while reformatting, whereas ROW and REPORT reformat without joining lines. See Example 8-135.

#### Return Value

TEXT or NTEXT

#### Syntax

TEXTFILL(text-expression, width)

#### Parameters

text-expression
A text expression to be reformatted to the specified width, regardless of the current format of the data. When you specify a TEXT expression, the return value is TEXT. When you specify an NTEXT expression, the return value is NTEXT.

width
The desired width of the reformatted data, entered as an `INTEGER` value from `1` to `132`.

In a structured report, TEXTFILL reformats text-expression to the width you specify if that width is less than the width of the report column. When width is greater than the column width, it is ignored by TEXTFILL, and the expression is reformatted to the width of the column.

TEXTFILL fits as many words of text-expression as it can onto one line, placing just one space between words and removing extra spaces between words. When a word is longer than width, TEXTFILL breaks it across two or more lines. In this case there may be extra spaces at the end of lines.

#### Examples

Example 8-135 The Effects of TEXTFILL on ROW

The following example shows the effect of TEXTFILL on a ROW command, using the nicely formatted text variable `textvar`.

The statement

    SHOW textvar

produces the following output.

    You can use the following options to control the format of 
       your display.
     
       BMARGIN    Controls the bottom margin.
       COLWIDTH   Controls column width.
       COMMAS     Controls the use of commas in numbers.
       DECIMALS   Controls number of decimal places in numbers.
       LSIZE      Controls the maximum length of a line.
       NASPELL    Controls the spelling of NA values in output.

The ROW statement

    ROW W 50 textvar

produces the following output.

    You can use the following options to control the
    format of your
    display.
    BMARGIN       Controls the bottom margin.
    COLWIDTH      Controls column width.
    COMMAS        Controls the use of commas in
    numbers.
    DECIMALS      Controls the number of decimal
    places in numbers.
    LSIZE         Controls the maximum length of a
    line.
    NASPELL       Controls the spelling of NA values
    in output.

By contrast, the ROW statement with TEXTFILL

    ROW W 50 TEXTFILL(textvar, 50)

produces the following output.

    You can use the following options to control the
    format of your display. BMARGIN Controls the
    bottom margin. COLWIDTH Controls column width.
    COMMAS Controls the use of commas in numbers.
    DECIMALS Controls the number of decimal places in
    numbers. LSIZE Controls the maximum length of a 
    line. NASPELL Controls the spelling of NA values
    in output.

### 8.126 TO_BINARY_DOUBLE

The TO_BINARY_DOUBLE function converts a text or numeric expression to a DECIMAL numeric expression.

#### Return Value

DECIMAL

#### Syntax

TO_BINARY_DOUBLE(expr \[, fmt \[, nlsparam \] \])

#### Parameters

expr
A text or numeric expression. When expr is a text expression, the function converts the following case-insensitive values to particular values:

- `INF` to positive infinity

- `-INF` to negative infinity

- `NaN` to `NaN` (not a number)

fmt
A text expression that specifies a number format model. This argument is valid only when expr is a text expression.

**See Also:**

"Number Format Models" in [Oracle Database SQL Language Reference](../sqlrf/Format-Models.md)

The default number format model uses the decimal and thousands group markers identified by NLS_NUMERIC_CHARACTERS.

**Note:**

You cannot use a floating-point number format element (F, f, D, or d) in a text expression.

nlsparams
A text expression that specifies how the function uses the thousands group marker, decimal marker, and currency symbols when converting a text expression. This argument is valid only when expr is a text expression. This expression contains one or more of the following parameters, separated by commas:

NLS_CURRENCY symbol  NLS_ISO_CURRENCY territory  NLS_NUMERIC_CHARACTERS dg 

### 8.127 TO_BINARY_FLOAT

The TO_BINARY_FLOAT function converts a text or numeric expression to a SHORTDECIMAL numeric expression.

#### Return Value

SHORTDECIMAL

#### Syntax

TO_BINARY_FLOAT(expr \[, fmt \[, nlsparam \] \])

#### Parameters

expr
A text or a numeric expression. When expr is a text expression, the function converts the following case-insensitive values to particular values:

- `INF` to positive infinity

- `-INF` to negative infinity

- `NaN` to `NaN` (not a number)

fmt
A text expression that specifies a number format model. This argument is valid only when expr is a text expression.

**See Also:**

["Number Format Models"](../sqlrf/Format-Models.md) in Oracle Database SQL Language Reference

The default number format model uses the decimal and thousands group markers identified by NLS_NUMERIC_CHARACTERS.

**Note:**

You cannot use a floating-point number format element (F, f, D, or d) in a text expression.

nlsparams
A text expression that specifies how the function uses the thousands group marker, decimal marker, and currency symbols when converting a text expression. This argument is valid only when expr is a text expression. This expression contains one or more of the following parameters, separated by commas:

NLS_CURRENCY symbol  NLS_ISO_CURRENCY territory  NLS_NUMERIC_CHARACTERS dg 

### 8.128 TO_CHAR

The TO_CHAR function converts a DATETIME, number, or NTEXT expression to a TEXT expression in a specified format. This function is typically used to format output data.

#### Return Value

TEXT

#### Syntax

TO_CHAR(datetime-exp, \[datetime-fmt,\] \[option setting\])

or

TO_CHAR(num-exp, \[num-fmt,\] \[nlsparams\])

or

TO_CHAR(ntext-exp)

#### Parameters

datetime-exp
A DATETIME expression to be converted to TEXT.

datetime-fmt
A text expression that identifies a datetime format template. This template specifies how the conversion from a DATETIME data type to TEXT should be performed. For information about datetime format templates, see [Table 9-4](olap-dml-commands-a-g.md). The default value of datetime-fmt is controlled by the NLS_DATE_FORMAT option.

option setting
An OLAP option (such as NLS_DATE_LANGUAGE) and its new setting, which temporarily overrides the setting currently in effect for the session. Typically, this option identifies the language that you want datetime-exp to be translated into. See Example 8-138.

Do not specify an option that set other options. For example, do not set NLS_DATE_LANGUAGE or NLS_TERRITORY; set NLS_DATE_LANGUAGE instead. While TO_CHAR saves and restores the current setting of the specified option so that it has a new value only for the duration of the statement, TO_CHAR cannot save and restore any side effects of changing that option. For example, NLS_TERRITORY controls the value of NLS_DATE_FORMAT, NLS_NUMERIC_CHARACTERS, NLS_CURRENCY, NLS_CALENDAR, and other options. When you change the value of NLS_TERRITORY in a call to TO_CHAR, all of these options are reset to their territory-appropriate default values twice: once when NLS_TERRITORY is set to its new value for the duration of the TO_CHAR statement, and again when the saved value of NLS_TERRITORY is restored.

num-exp
A numeric expression to be converted to TEXT.

num-fmt
A text expression that identifies a number format model. This model specifies how the conversion from a numeric data type (NUMBER, INTEGER, SHORTINTEGER, LONGINTEGER, DECIMAL, SHORTDECIMAL) to TEXT should be performed.

The default number format model uses the decimal and thousands group markers identified by NLS_NUMERIC_CHARACTERS.

**See Also:**

["Number Format Models"](../sqlrf/Format-Models.md) in Oracle Database SQL Language Reference

nlsparams
A text expression that specifies the thousands group marker, decimal marker, and currency symbols used in num-exp. This expression contains one or more of the following parameters, separated by commas:

NLS_CURRENCY symbol  NLS_ISO_CURRENCY territory  NLS_NUMERIC_CHARACTERS dg 

symbol
A text expression that specifies the local currency symbol. It can be no more than 10 characters.

territory
A text expression that identifies the territory whose ISO currency symbol is used.

dg
A text expression composed of two different, single-byte characters for the decimal marker (`d`) and thousands group marker (`g`).

These parameters override the default values specified by the NLS_CURRENCY, NLS_ISO_CURRENCY, and NLS_NUMERIC_CHARACTERS options.

ntext-exp
An NTEXT expression to be converted to TEXT. A conversion from NTEXT to TEXT can result in data loss when the NTEXT value cannot be represented in the database character set.

#### Usage Notes

How TO_CHAR Handles Numerical Data Types

The TO_CHAR function converts INTEGER, SHORTINTEGER, LONGINTEGER, DECIMAL, and SHORTDECIMAL values to NUMBER before converting them to TEXT. Thus, TO_CHAR converts NUMBER values faster than other numeric data types.

Possible Effects of TO_CHAR Rounding

All number format models cause the number to be rounded to the specified number of significant digits. The following table identifies some effects of rounding.

Table 8-17 Possible Effects of Rounding

| IF num-exp                                                                                     | THEN the return value                          |
|:-----------------------------------------------------------------------------------------------|:-----------------------------------------------|
| has more significant digits to the left of the decimal place than are specified in the format, | appears as pound signs (`#`).                  |
| is a very large positive value that cannot be represented in the specified format,             | is a tilde (`~`).                              |
| is a very small negative value that cannot be represented in the specified format,             | is a negative sign followed by a tilde (`-~`). |

#### Examples

Example 8-136 Converting a Date to CHAR

This statement converts today's date and specifies the format.

    SHOW TO_CHAR(SYSDATE, 'Month DD, YYYY HH24:MI:SS')

The specified date format allows the time to be displayed along with the date.

    November  30, 2000 10:01:29

Example 8-137 Converting a Numerical Value to Text

This statement converts a number to text and specifies a space as the decimal marker and a period as the thousands group marker.

    SHOW TO_CHAR(1013.50, NA, NLS_NUMERIC_CHARACTERS ' .')

The value 1013.50 now appears like this:

    1.013 50

Example 8-138 Displaying the Current Date and Time in Spanish

The following statements set the default language to Spanish and specify a new date format.

    NLS_DATE_LANGUAGE = 'spanish'
    NLS_DATE_FORMAT = 'Day: Month dd, yyyy HH:MI:SS am'

The following statement displays the current date and time in Spanish.

    SHOW TO_CHAR(SYSDATE)
    Viernes  : Diciembre  01, 2000 08:21:17 AM

The NLS_DATE_LANGUAGE option changes the language for the duration of the statement. The following statement displays the date and time in German.

    SHOW TO_CHAR(SYSDATE, NA, NLS_DATE_LANGUAGE 'german')
    Freitag   : Dezember  01, 2000 08:26:00 AM

### 8.129 TO_DATE

The TO_DATE function converts a formatted TEXT or NTEXT expression to a DATETIME value.

#### Return Value

DATETIME

#### Syntax

TO_DATE(text-exp, \[fmt,\] \[option setting\])

#### Parameters

text-exp
The text expression that contains a date to be converted. The expression can have the TEXT or NTEXT data type. A conversion from NTEXT can result in an incorrect result when the NTEXT value cannot be interpreted as a date.

fmt
A text expression that identifies a datetime format template. This template specifies how the conversion from text to DATETIME should be performed. For information about datetime format templates, see the datetime_format_template parameter in [DATE_FORMAT](olap-dml-commands-a-g.md).

option setting
An OLAP option (such as NLS_DATE_LANGUAGE) and its new setting, which temporarily overrides the setting currently in effect for the session. Typically, this option identifies the language of text-exp when it is different from the session language. See Example 8-140.

Do not specify an option that sets other options. For example, do not set NLS_LANGUAGE or NLS_TERRITORY; set NLS_DATE_LANGUAGE instead. While TO_DATE saves and restores the current setting of the specified option so that it has a new value only for the duration of the statement, TO_DATE cannot save and restore any side effects of changing that option. For example, NLS_TERRITORY controls the value of NLS_DATE_FORMAT, NLS_NUMERIC_CHARACTERS, NLS_CURRENCY, NLS_CALENDAR, and other options. When you change the value of NLS_TERRITORY in a call to TO_DATE, all of these options are reset to their territory-appropriate default values twice: once when NLS_TERRITORY is set to its new value for the duration of the TO_DATE statement, and again when the saved value of NLS_TERRITORY is restored.

#### Usage Notes

Capitalization

Capital letters in words, abbreviation, or Roman numerals in a format element produce corresponding capitalization in the return value. For example, the format element `DAY` produces `MONDAY`, `Day` produces `Monday`, and `day` produces `monday`.

Unrecognized Dates

When TO_DATE cannot construct a value with a valid DATE value using fmt, it returns an error. For example, when an alphanumeric character appears in text-exp where fmt indicates a punctuation character, then an error results.

#### Examples

Example 8-139 Converting Text Values to DATE Values

The following statement converts `January` `15,` `2002,` `11:00` `A.M.` to the default date format of `15JAN02`, and stores that value in a DATE variable named `bonusdate`.

    bonusdate = TO_DATE('January 15, 2002, 11:00 A.M.', -
       'Month dd, YYYY, HH:MI A.M.')

Example 8-140 Specifying a Default Language and a Date Format

The following statements set the default language to Spanish and specify a new date format. The NLS_DATE_LANGUAGE option, when used in the TO_DATE function, allows the American month name to be translated.

    NLS_DATE_FORMAT = 'Day: Month dd, yyyy HH:MI:SS am'
    NLS_DATE_LANGUAGE = 'spanish'
    SHOW TO_DATE('November 15, 2001', 'Month dd, yyyy', -
       NLS_DATE_LANGUAGE 'american')

The date is translated from American to Spanish and displayed in the new date format.

    Jueves   : Noviembre  15, 2001 12:00:00 AM

### 8.130 TO_DSINTERVAL

The TO_DSINTERVAL function converts a character to a DSINTERVAL value.

#### Return Value

`DSINTERVAL`

#### Syntax

TO_DSINTERVAL(char)

#### Parameters

char
Specifies the character string to be converted.

### 8.131 TO_NCHAR

The TO_NCHAR function converts a TEXT expression, date, or number to NTEXT in a specified format. This function is typically used to format output data.

#### Return Value

NTEXT

#### Syntax

TO_NCHAR(text-exp)

or

TO_NCHAR(datetime-exp, \[datetime-fmt,\] \[option setting\]

or

TO_NCHAR(num-exp, \[num-fmt,\] \[nlsparams\]

#### Parameters

text-exp
A TEXT expression to be converted to NTEXT.

datetime-exp
A DATETIME expression to be converted to NTEXT.

datetime-fmt
A text expression that identifies a datetime format template. This template specifies how the conversion from a DATETIME data type to NTEXT should be performed. For information about datetime format templates, see the datetime_format_template parameter in [DATE_FORMAT](olap-dml-commands-a-g.md). The default value of datetime-fmt is controlled by the NLS_DATE_FORMAT option.

option setting
An OLAP option (such as NLS_DATE_LANGUAGE) and its new setting, which temporarily overrides the setting currently in effect for the session. Typically, this option identifies the language that you want datetime-exp to be translated into. See Example 8-143.

Do not specify an option that sets other options. For example, do not set NLS_LANGUAGE or NLS_TERRITORY; set NLS_DATE_LANGUAGE instead.While TO_NCHAR saves and restores the current setting of the specified option so that it has a new value only for the duration of the statement, TO_NCHAR cannot save and restore any side effects of changing that option. For example, NLS_TERRITORY controls the value of NLS_DATE_FORMATE, NLS_NUMERIC_CHARACTERS, NLS_CURRENCY, NLS_CALENDAR, and other options. When you change the value of NLS_TERRITORY in a call to TO_NCHAR, all of these options are reset to their territory-appropriate default values twice: once when NLS_TERRITORY is set to its new value for the duration of the TO_NCHAR statement, and again when the saved value of NLS_TERRITORY is restored.

num-exp
A numeric expression to be converted to NTEXT.

num-fmt
A text expression that identifies a number format model. This model specifies how the conversion from a numeric data type (NUMBER, INTEGER, SHORTINTEGER, LONGINTEGER, DECIMAL, SHORTDECIMAL) to TEXT should be performed.

**See Also:**

["Number Format Models"](../sqlrf/Format-Models.md) in Oracle Database SQL Language Reference

The default number format model uses the decimal and thousands group markers identified by NLS_NUMERIC_CHARACTERS option.

nlsparams
A text expression that specifies the thousands group marker, decimal marker, and currency symbols used in num-exp. This expression contains one or more of the following parameters, separated by commas:

NLS_CURRENCY symbol  NLS_ISO_CURRENCY territory  NLS_NUMERIC_CHARACTERS dg 

symbol
A text expression that specifies the local currency symbol. It can be no more than 10 characters.

territory
A text expression that identifies the territory whose ISO currency symbol is used.

dg
A text expression composed of two different, single-byte characters for the decimal marker (`d`) and thousands group marker (`g`).

These parameters override the default values specified by the NLS_CURRENCY, NLS_ISO_CURRENCY, and NLS_NUMERIC_CHARACTERS options.

#### Examples

Example 8-141 Date Conversion

This statement converts today's date and specifies the format.

    SHOW TO_NCHAR(SYSDATE, 'Month DD, YYYY HH24:MI:SS')

The specified date format allows the time to be displayed along with the date.

    November  30, 2000 10:01:29

Example 8-142 Converting Numerical Data to NTEXT Data

This statement converts a number to NTEXT and specifies a space as the decimal marker and a period as the thousands group marker.

    SHOW TO_NCHAR(1013.50, NA, NLS_NUMERIC_CHARACTERS ' .')

The value 1013.50 now appears like this:

    1.013 50

Example 8-143 Specifying the Default Language and a Date Format

The following statements set the default language to Spanish and specify a new date format.

    NLS_DATE_LANGUAGE = 'spanish'
    NLS_DATE_FORMAT = 'Day: Month dd, yyyy HH:MI:SS am'

The following statement:

    SHOW TO_NCHAR(SYSDATE)

Displays the current date and time in Spanish:

    Viernes  : Diciembre  01, 2000 08:21:17 AM

The NLS_DATE_LANGUAGE option changes the language for the duration of the statement. The following statement

    SHOW TO_NCHAR(SYSDATE, NA, NLS_DATE_LANGUAGE 'german')

displays the date and time in German:

    Freitag   : Dezember  01, 2000 08:26:00 AM

### 8.132 TO_NUMBER

The TO_NUMBER function converts a formatted TEXT or NTEXT expression to a number. This function is typically used to convert the formatted numeric output of one application (which includes currency symbols, decimal markers, thousands group markers, and so forth) so that it can be used as input to another application.

#### Return Value

NUMBER. Negative return values contain a leading negative sign, and positive values contain a leading space, unless the format model contains the `MI`, `S`, or `PR` format elements.

#### Syntax

TO_NUMBER(text-exp, \[fmt,\] \[nlsparams\])

#### Parameters

text-exp
A text expression that contains a number to be converted. The expression can have the TEXT or NTEXT data type. A conversion from NTEXT can result in an incorrect result when the NTEXT value cannot be interpreted as a number.

fmt
A text expression that identifies a number format model. This model specifies how the conversion to NUMBER should be performed.

**See Also:**

["Number Format Models"](../sqlrf/Format-Models.md) in Oracle Database SQL Language Reference

The default number format identifies a period (`.`) as the decimal marker and does not recognize any other symbol.

nlsparams
A text expression that specifies the thousands group marker, decimal marker, and currency symbols used in text-exp. This expression contains one or more of the following parameters, separated by commas:

NLS_CURRENCY symbol  NLS_ISO_CURRENCY territory  NLS_NUMERIC_CHARACTERS dg 

symbol
A text expression that specifies the local currency symbol. It can be no more than 10 characters.

territory
A text expression that identifies the territory whose ISO currency symbol is used.

dg
A text expression composed of two different, single-byte characters for the decimal marker (`d`) and thousands group marker (`g`).

These parameters override the default values specified by the NLS_CURRENCY, NLS_ISO_CURRENCY, and NLS_NUMERIC_CHARACTERS options. Refer to NLS Options for additional information.

#### Usage Notes

Default Number Format Values

The values of some formats are determined by the value of [NLS_TERRITORY](olap-dml-options.md).

Possible Effects of TO_NUMBER Rounding

All number format models cause the number to be rounded to the specified number of significant digits. Table 8-17 identifies some effects of rounding.

#### Examples

Example 8-144 Converting Text Data to Decimal Data

The following statements convert a text string to a DECIMAL data type in the current number format, which is American. The text-exp parameter is a text string in European format. The fmt parameter identifies the local currency symbol (`L`), the thousands group separator (`G`), and the decimal marker (`D`). The NLS_NUMERIC_CHARACTERS option identifies the characters used for the `G` and `D` formats in the text-exp parameter because they are different from the current setting for the session. In text_exp, `D` is a comma and `G` is a space.

    DEFINE money VARIABLE DECIMAL
    money = TO_NUMBER('$94 567,00', 'L999G999D00', NLS_NUMERIC_CHARACTERS ', ')
    SHOW money

The output of this statement is:

    94,567.00

### 8.133 TO_TIMESTAMP

The TO_TIMESTAMP function converts text data to a value of `TIMESTAMP` data type.

#### Return Values

TIMESTAMP

#### Syntax

TO_TIMESTAMP(char-exp \[, fmt \[ 'nlsparam' \] \])

#### Parameters

char-exp
A text expression that you want to convert.

fmt
Specifies the datetime format template to be used to convert the text expression. See the datetime_format_template parameter in [DATE_FORMAT](olap-dml-commands-a-g.md) for more information about the datetime format template.

When you omit this argument, the function uses the default format of `TIMESTAMP` for the object.

nlsparam
Specifies the language in which month and day names and abbreviations are returned. This argument can have this form:

    'NLS_DATE_LANGUAGE = language'

If you omit this argument, then this function uses the default date language for your session.

#### Examples

Example 8-145 Converting To and Extracting From Timestamp Data

    SHOW NLS_DATE_FORMAT
    DD-MON-RR

    SHOW TO_TIMESTAMP('10-SEP-0614:10:10:10.123000' 'DD MON RR HH24:MI:SS.FF')
    10-SEP-14 10.10.10.123 AM

    SHOW TO_TIMESTAMP_TZ ('2006-03-26 7:33:00 -4:00', 'YYYY-MM-DD HH:MI:SS TZH:TZM')
    26-MAR-06 07.33.00 AM -04:00

    DEFINE mytimestamp VARIABLE TIMESTAMP
    DEFINE mytimezone VARIABLE TEXT
    DEFINE mytimestamptz VARIABLE TIMESTAMP_TZ
    mytimestamp = '26-MAR-06'
    mytimezone = '-04:00'
    mytimestamptz = FROM_TZ (mytimestamp mytimezone)
    REPORT mytimestamptz

    MYTIMESTAMPTZ
    ------------------------------
      26-MAR-06 12.00.00 AM -04:00
    SHOW EXTRACT (TIMEZONE_HOUR FROM mytimestamptz)
    -4.00

### 8.134 TO_TIMESTAMP_TZ

The TO_TIMESTAMP_TZ function converts text data to a value with the `TIMESTAMP_TZ` data type.

#### Return Value

TIMESTAMP_TZ

#### Syntax

TO_TIMESTAMP_TZ (char-exp \[, fmt \[ 'nlsparam' \] \])

#### Parameters

char-exp
A text expression that you wan to convert.

fmt
Specifies the datetime format template to be used to convert the text expression. See the datetime_format_template parameter in [DATE_FORMAT](olap-dml-commands-a-g.md) for more information about the datetime format template.

When you omit this argument, the function uses the default format of `TIMESTAMP_TZ` for the object.

nlsparam
Specifies the language in which month and day names and abbreviations are returned. This argument can have this form:

    'NLS_DATE_LANGUAGE = language'

If you omit this argument, then this function uses the default date language for your session.

#### Examples

Example 8-146 Converting Text Data to TIMESTAMP_TZ DAta

    SHOW TO_TIMESTAMP_TZ ('2006-03-26 7:33:00 -4:00', 'YYYY-MM-DD HH:MI:SS TZH:TZM')
    26-MAR-06 07.33.00 AM -04:00

### 8.135 TO_YMINTERVAL

The TO_YMINTERVAL function converts a character to a YMINTERVAL value.

#### Return Value

`YMINTERVAL`

#### Syntax

TO_YMINTERVAL(char)

#### Parameters

char
Specifies the character string to be converted.

### 8.136 TOD

The TOD function returns the current time of day in the form hh:mm:ss using a 24-hour format.

#### Return Value

ID

#### Syntax

TOD

#### Examples

Example 8-147 Displaying the Current Time

The following statement sends the current time of day to the current outfile.

    show tod

This statement produces the following output.

    17:30:46

### 8.137 TODAY

The TODAY function returns the current date as a DATE or TEXT value.

#### Return Value

DATE or TEXT depending on the data type that is expected:

- DATE

  When you display a returned DATE value, the value has the format specified by the date template in the DATEFORMAT option. When the day of the week or the name of the month is used in the date template, TODAY uses the day names specified in the DAYNAMES option and the month names specified in the MONTHNAMES option.

- TEXT

  Where a text value is expected. TODAY automatically converts the date to a TEXT value, using the current template in the DATEFORMAT option to format the text value. When you want to override the current DATEFORMAT template, you can convert the date result to text by using the CONVERT function with a date-format argument.

#### Syntax

TODAY

#### Examples

Example 8-148 Displaying Today's Date

The following statements send the current date in DATE format to the current outfile.

    DATEFORMAT = '<wtextl> <mtextl> <d>, <yyyy>'
    SHOW TODAY

When the current date is January 15, 1996, then these statements produce the following output.

    Monday January 15, 1996

Example 8-149 Calculating a Date Using the TODAY Function

The following statement calculates the date 60 days from today.

    SHOW TODAY + 60

When the current date is January 15, 1996, then this statement produces the following output.

    Friday March 15, 1996

### 8.138 TOTAL

The TOTAL function calculates the total of the values of an expression.

#### Return Value

The data type of the expression. It can be INTEGER, LONGINT, or DECIMAL.

#### Syntax

TOTAL(expression \[CACHE\] \[dimension...\])

#### Parameters

expression
The expression to be totalled.

CACHE
Specifies slightly different internal behavior. Specify this keyword only when the original performance is extremely slow.

dimension
The name of a dimension of the result; or, the name of a relation between one dimension of expression and another dimension that you want as a dimension of the result.

By default, TOTAL returns a single value. When you indicate one or more dimensions for the result, TOTAL calculates values along the dimensions that are specified and returns an array of values. Each dimension must be either a dimension of expression or related to one of its dimensions.

**Tip:**

When you specify a dimension that is not an actual dimension of expression, but, instead, is dimension that is related to a dimension of expression and when there are multiple relations between the two dimensions, Oracle OLAP uses the default relation between the dimensions to perform the calculation. (See the [RELATION command](olap-dml-commands-h-z.md) for more information on default relations.) When you do not want Oracle OLAP to use this default relation, specify the related dimension by specifying the name of a specify relation.

#### Usage Notes

How TOTAL Handles NA Values

TOTAL is affected by the NASKIP option. When NASKIP is set to `YES` (the default), TOTAL ignores `NA` values and returns the sum of the values that are not `NA`. When NASKIP is set to `NO`, TOTAL returns `NA` when any value in the calculation is `NA`. When all data values for a calculation are `NA`, TOTAL returns `NA` for either setting of NASKIP.

Totaling over a DWMQY Dimension

When expression is dimensioned by a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, you can specify any other DAY, WEEK, MONTH, QUARTER, or YEAR dimension as a related dimension. Oracle OLAP uses the implicit relation between the dimensions. To control the mapping of one DAY, WEEK, MONTH, QUARTER, or YEAR dimension to another (for example, from weeks to months), you can define an explicit relation between the two dimensions and specify the name of the relation as the dimension argument to the TOTAL function.

For each time period in the related dimension, Oracle OLAP totals the data for all the source time periods that end in the target time period. This method is used regardless of which dimension has the more aggregate time periods. To control the way in which data is aggregated or allocated between the periods of two time dimensions, you can use the TCONVERT function.

Multiple Relations in a TOTAL Function

When you break out the total by a related dimension, you are changing the dimensionality of the expression, so Oracle OLAP expects values based on this new dimensionality. It chooses the relation that holds values of that dimension.

When there are multiple relations that hold values of the expected dimension, Oracle OLAP uses the one that was defined first. When there is no relation in which the related dimension is the one expected, Oracle OLAP looks for a relation that is dimensioned by the expected dimension.

For example, assume that there are two relations between `district` and `region`, as follows.

    DEFINE REGION.DISTRICT RELATION REGION <DISTRICT>
    LD The region each district belongs to
     
    DEFINE DISTRICT.REGION RELATION DISTRICT <REGION>
    LD The primary district in each region

When an analytic workspace had the two relations described earlier and you specified the following TOTAL function, Oracle OLAP would use the relation `region.district` by default, because it holds values of the specified dimension.

    REPORT TOTAL(sales region)

#### Examples

Example 8-150 Totaling Sales over All Months

Suppose you would like to see the total sportswear sales for all months for each district. Use the TOTAL function to calculate the total sales. To see a total for each district, specify `district` as the dimension of the results.

    LIMIT product TO 'Sportswear'
    REPORT W 15 HEADING 'Total Sales' TOTAL(sales district)

The preceding statements produce the following output.

    DISTRICT         Total Sales
    -------------- ---------------
    Boston            1,659,609.90
    Atlanta           3,628,616.62
    Chicago           2,296,631.81
    Dallas            3,893,829.30
    Denver            2,133,425.29
    Seattle           1,298,215.59

### 8.139 TRANSLATE

The TRANSLATE function replaces all occurrences of each character of one string with the corresponding character in another string.

**Note:**

TRANSLATE provides functionality related to that provided by the REPLCHARS function. REPLCHARS lets you substitute a single string for another single string and remove character strings. TRANSLATE lets you make several single-character, one-to-one substitutions in one operation.

#### Return value

Text.

#### Syntax

TRANSLATE ( exp from_string to_string)

#### Parameters

exp
A text expression in which you want to replace characters.

from_string
A text expression that is the characters you want to replace.

to_string
A text expression that is the characters to use for replacement in the order of from_string. When you include fewer characters in this argument than are in from_string, the function removes the extra characters in from_string from the return value. Note, however, that to remove all characters in from_string, you cannot specify an empty string for to_string as an empty string is interpreted as a null argument.

#### Examples

Example 8-151 Replacing several Characters Using TRANSLATE

The following statement translates a book title into a string that could be used (for example) as a filename. The from_string contains three characters: an asterisk, a space, asterisk, and apostrophe (with a backslash as the escape character). The to_string contains only two underscores which leaves the third character in the from_string without a corresponding replacement, so the return value does not contain any apostrophes.

    SHOW TRANSLATE ('SQL*Plus User\'s Guide' '* \'' '__')
    SQL_Plus_Users_Guide

### 8.140 TRIGGER function

The TRIGGER function retrieves the event, subevent, or name of the object or analytic workspace that caused the execution of a trigger program (that is, a TRIGGER_DEFINE, TRIGGER_AFTER_UPDATE, or TRIGGER_BEFORE_UPDATE program, or any program identified as a trigger program using the TRIGGER command).

When the current program is a trigger program, the TRIGGER function returns the trigger information for that program. When it is not, the TRIGGER function returns trigger information for the most recently executed trigger program.

**See Also:**

"[Trigger Programs](olap-dml-programs.md)" and the "[TRIGGER command](olap-dml-commands-h-z.md)"

#### Return Values

`TEXT`

#### Syntax

TRIGGER (NAME \| EVENT \| SUBEVENT)

#### Parameters

NAME
For a program identified as a trigger program using the TRIGGER command, returns the object for which the trigger program is association. For a TRIGGER_AW, TRIGGER_DEFINE, TRIGGER_AFTER_UPDATE, or TRIGGER_BEFORE_UPDATE program, returns the name of the analytic workspace that caused the program to execute.

EVENT
Returns the name of the event (DML statement) that triggered the execution of the program.

- `AW`
- `MAINTAIN`
- `DELETE`
- `DEFINE`
- `PROPERTY`
- `ASSIGN`
- `BEFORE_UPDATE`
- `AFTER_UPDATE`

**See Also:**

"[Trigger Programs](olap-dml-programs.md)" and "[TRIGGER command](olap-dml-commands-h-z.md)" for more information on events

SUBEVENT
When the value returned by EVENT is `MAINTAIN`, `AFTER_UPDATE` or `BEFORE_UPDATE`, returns more information on the OLAP DML statement that triggered the execution of the program. Valid subevents for `AW` are outlined in the following table. Valid subevents for `MAINTAIN` are outlined in Table 8-19. Valid subevents for `UPDATE` are outlined in Table 8-20.

Table 8-18 Subevents for the AW Event

| Subevent | Description                                                                  |
|:---------|:-----------------------------------------------------------------------------|
| CREATE   | Returned when an AW CREATE statement triggered the execution of the program. |
| ATTACH   | Returned when an AW ATTACH statement triggered the execution of the program. |
| DELETE   | Returned when an AW DELETE statement triggered the execution of the program. |
| DETACH   | Returned when an AW DETACH statement triggered the execution of the program. |

Table 8-19 Subevents for the MAINTAIN Event

| Subevent   | Description                                                                                                                |
|:-----------|:---------------------------------------------------------------------------------------------------------------------------|
| ADD        | Returned when a MAINTAIN ADD statement triggered the execution of the program.                                             |
| DELETE     | Returned when any MAINTAIN DELETE statement except a MAINTAIN DELETE ALL statement triggered the execution of the program. |
| DELETE ALL | Returned when a MAINTAIN DELETE ALL statement triggered the execution of the program.                                      |
| MERGE      | Returned when a MAINTAIN MERGE statement triggered the execution of the program.                                           |
| MOVE       | Returned when a MAINTAIN MOVE statement triggered the execution of the program.                                            |
| RENAME     | Returned when a MAINTAIN RENAME statement triggered the execution of the program.                                          |

Table 8-20 Subevents for UPDATE Events

| Subevent | Description                                                                                                                                                                    |
|:---------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AW       | Returned when an UPDATE command triggered the execution of a TRIGGER_AFTER_UPDATE or TRIGGER_BEFORE_UPDATE program.                                                            |
| MULTI    | Returned when an UPDATE command triggered the execution of a program identified as a trigger program using the TRIGGER command when an object is acquired in multiwriter mode. |

#### Examples

For examples of using the TRIGGER function, see [Example 6-3](olap-dml-programs.md) and [Example 10-166](olap-dml-commands-h-z.md).

### 8.141 TRIM

The TRIM function enables you to trim leading or trailing characters (or both) from a character string.

You can also trim leading characters using LTRIM and trailing characters using RTRIM.

#### Return Value

The data type of the string you are trimming (that is, trim-source).

#### Syntax

TRIM (\[{{LEADING\|TRAILING\|BOTH} \[trim_characters\])\|trim_character} FROM\]  trim_source)

#### Parameters

trim-characters
An expression that specifies the character values to be trimmed. This text expression can be any of the text data types.

When you specify multiple characters in trim-characters, the function searches for each character in trim_source, in turn, removing characters from trim_source until it encounters a character in trim_source that is not in trim-characters.

When you do not specify a value, then the default value is a blank space and the function removes leading and trailing blank spaces.

LEADING
Specifies that the function removes any leading characters from trim_source that are equal to trim_characters.

TRAILING
Specifies that the function removes any trailing characters from trim_source that are equal to trim_characters.

BOTH
Specifies that the function removes leading and trailing characters from trim_source that are equal to trim_characters.

trim-source
An expression that is the string value to be trimmed. This text expression can be any of the text data types.

### 8.142 TRUNCATE

The TRUNCATE function (abbreviated as TRUNC) truncates either a number or a datetime value. Because the syntax of the TRUNC function is different depending on the whether it is being used for a number or a date and time value, two separate entries are provided:

- TRUNCATE (datetime)

- TRUNCATE (number)

#### 8.142.1 TRUNCATE (datetime)

The TRUNCATE (datetime) function returns date with the time portion of the day truncated to the unit specified by the format model.

##### Return Value

DATETIME

##### Syntax

TRUNC (datetime_exp, \[fmt\])

##### Parameters

datetime-exp
A datetime expression that identifies a date and time number.

fmt
A text expression that specifies a format model shown in Table 8-13. A format model indicates how the date and time number should be truncated. If you omit `fmt`, then `date` is truncated to the nearest day.

##### Examples

Example 8-152 Truncating to the Nearest Year

When the value of the NLS_DATE_FORMAT option is `DD-MON-YY`, then this statement:

    SHOW TRUNC (TO_DATE('27-OCT-92'),'YEAR')

returns this value:

    01-JAN-92

Example 8-153 Truncating Using Different Formats

Assume the following option values, variables, and values are in your analytic workspace.

    SHOW NLS_DATE_FORMAT
    DD-MON-RR
    DEFINE MYDATETIME VARIABLE DATETIME
    DATE_FORMAT = 'MON-RRRR-DD-HH24'
    mydatetime = CURRENT_TIMESTAMP
    SHOW mydatetime
    = 'AUG-2006-07-14'

As the following SHOW statements illustrate, the value you specify for the format argument of TRUNCATE function determines the value returned by that function.

    SHOW TRUNCATE(mydatetime, 'MON')
    01-AUG-06
    SHOW TRUNCATE(mydatetime, 'DD')
    07-AUG-06
    SHOW TRUNCATE(mydatetime)
    = 'AUG-2006-07-00'

#### 8.142.2 TRUNCATE (number)

When you specify a number as an argument, the TRUNCATE function truncates a number to a specified number of decimal places.

##### Return Value

DECIMAL

##### Syntax

TRUNC (number, truncvalue)

##### Parameters

number
The number to truncate. The value specified for number must be followed by a comma.

truncvalue
An `INTEGER` value that specifies the number of places to the right or left of the decimal point to which number should be truncated. When truncvalue is positive, digits to the right of the decimal point are truncated. When it is negative, digits to the left of the decimal point are truncated (that is, made zero). When truncvalue is omitted, number is truncated to `0` decimal places.

##### Examples

Example 8-154 Truncating to the Right of the Decimal Point

The following statement

    SHOW TRUNC (15.79, 1)

returns this value

    15.7

Example 8-155 Truncating to the Left of the Decimal Point

The following statement

    SHOW TRUNC (15.79, -1)

returns this value

    10

### 8.143 TZ_OFFSET

The TZ_OFFSET function returns the time zone offset corresponding to the argument based on the date the statement is executed.

**Note:**

Time zone region names are needed by the daylight savings feature. The region names are stored in two time zone files. The default time zone file is a small file containing only the most common time zones to maximize performance. If your time zone is not in the default file, then you do not have daylight savings support until you provide a path to the complete (larger) file by way of the ORA_TZFILE environment variable.

#### Return Values

A text value in the format shown below which represents the offset

'{ + \| - } hh : mi'

#### Syntax

TZ_OFFSET( 'time_zone_name' \| '{ + \| - } hh : mi' \| SESSIONTIMEZONE \| DBTMEZONE)

#### Parameters

time_zone_name
A text value that specifies a valid time zone name. For a listing of valid values for time_zone_name, query the TZNAME column of the V\$TIMEZONE_NAMES dynamic performance view.

**Note:**

Time zone region names are needed by the daylight savings feature. The region names are stored in two time zone files. The default time zone file is a small file containing only the most common time zones to maximize performance. If your time zone is not in the default file, then you do not have daylight savings support until you provide a path to the complete (larger) file by way of the ORA_TZFILE environment variable.

{ + \| - } hh : mi'
Specifies a time zone offset from UTC (which simply returns itself)

SESSIONTIMEZONE
Specifies the time zone of the current session.

DBTIMEZONE
Specifies the value of the database time zone.

### 8.144 UNIQUELINES

The UNIQUELINES function removes duplicate lines in a multiline text value and sorts the lines in ascending order. The function returns a multiline text value composed of the resulting lines.

#### Return Value

TEXT or NTEXT

#### Syntax

UNIQUELINES(text-expression)

#### Parameters

text-expression
A multiline text expression from which UNIQUELINES removes duplicate lines and in which it sorts the remaining lines. UNIQUELINES is case-sensitive when it checks for duplicates, and it compares all characters, including spaces.

When you specify a TEXT expression, the return value is TEXT. When you specify an NTEXT expression, the return value is NTEXT.

#### Examples

Example 8-156 Removing Duplicate Text Lines

In the following example, one line is removed from the value of `officelist`, and the lines are sorted.

The statement

    SHOW officelist

produces the following output.

    MIAMI
    Providence
    Miami
    Baltimore
    Saratoga
    Baltimore

The statement

    show uniquelines(officelist)

produces the following output.

    Baltimore
    Miami
    MIAMI
    Providence
    Saratoga

### 8.145 UNRAVEL

The UNRAVEL function is used with an assignment statement to copy the values of an expression into the cells of a variable when the dimensions of the expression are different from the dimensions of the variable.

An assignment statement created using an assignment statement assigns the values obtained from UNRAVEL by looping over the status of the dimensions of the target variable. The first dimension listed in the variable's definition varies the fastest. UNRAVEL obtains the values of the expression in the same way, looping over the status of the dimensions of the expression with the first dimension varying the fastest. You can alter the order in which UNRAVEL obtains its values by specifying the dimensions over which to loop.

#### Return Value

The data type returned by UNRAVEL is the data type of the values specified by the expression.

#### Syntax

UNRAVEL(expression \[dimension1...\])

#### Parameters

expression
The expression whose values are to be copied.

dimension
Specifies one or more dimensions over which to loop; the dimension specified first varies fastest as the data is unraveled.

Specifying dimensions in UNRAVEL overrides the default looping order and the extent to which the expression is unraveled. By default, unraveling extends through all the dimensions of the expression. However, when you specify some but not all the dimensions of the expression, any dimensions you have not specified do not unravel. Instead, the unraveled values include only the first value of each of the omitted dimensions.

#### Usage Notes

Moving Worksheet Data

One common use of UNRAVEL is to move data from a worksheet to a variable, because the worksheet usually does not have the same dimensions as the variable. See Example 8-157.

Filling Extra Target Cells

When there are still more cells in the target for the assignment statement (created using an assignment statement) to fill after it has used the last value from the expression, UNRAVEL starts over at the first value again.

Setting Status

Because the order in which unraveled values are assigned depends on the current status of the dimensions of both the variable and the expression, ensure that the appropriate LIMIT commands have been given so that the cells match up correctly.

Assigning Data Values

See [SET](olap-dml-commands-h-z.md) for information on how data values are assigned.

#### Examples

Example 8-157 Copying Data from a Worksheet to a Variable

In an analytic workspace, you have imported some product price data from a spreadsheet into a worksheet. You now want to transfer that data to a variable called `newprice`. You can produce a report of a worksheet, called `pricedata`, with these statements.

    LIMIT wksrow TO 1 TO 6
    LIMIT wkscol TO 1 2 3
    REPORT pricedata

This is the report.

                   -----------PRICEDATA------------
                   -------------WKSCOL-------------
    WKSROW             1          2          3
    -------------- ---------- ---------- ----------
                 1            Jan95      Jan96
                 2 Tents          191.39     194.00
                 3 Canoes         279.92     300.00
                 4 Racquets        83.34      85.00
                 5 Sportswear     107.90     110.00
                 6 Footwear       183.18     195.00

As you can see, row 1 contains month labels, while column 1 contains product labels. The variable `newprice` is dimensioned by `month` and `product`, as shown in its definition.

    DEFINE newprice VARIABLE DECIMAL <month product>
    LD Wholesale Unit Selling Price

Even though the worksheet has different dimensions (`wkscol` and `wksrow`) than `newprice`, the data contained in it is well organized for transferring to the variable.

However, you do not want to take data from all the rows and columns in the worksheet, so limit `wkscol` and `wksrow` to the rows and columns that contain the price data itself.

    LIMIT wkscol TO 2 3
    LIMIT wksrow TO 2 TO 6

Also, you only want to set values into the variable `newprice` for January 1995 and January 1996. So first limit `month` to these values, then type an assignment statement using UNRAVEL to move the values from the worksheet to the variable.

    LIMIT month TO 'Jan95' 'Jan96'
    newprice = UNRAVEL(pricedata)

You do not have to specify dimensions in the UNRAVEL function because `wkscol` is the fastest varying dimension. Consequently, both months unravel for the first product, then both months for the second product. Because the fastest-varying dimension of the variable is `month`, SET assigns values to the variable in the same order.

A report of `newprice` looks like this.

                   ------NEWPRICE-------
                   --------MONTH--------
    PRODUCT          Jan95      Jan96
    -------------- ---------- ----------
    Tents              191.39     194.00
    Canoes             279.92     300.00
    Racquets            83.34      85.00
    Sportswear         107.90     110.00
    Footwear           183.18     195.00

### 8.146 UPPER

The UPCASE function converts all alphabetic characters in a text expression into uppercase. When you specify a TEXT expression, the return value is TEXT. When you specify an NTEXT expression, the return value is NTEXT.

#### Return Value

TEXT or NTEXT

#### Syntax

UPCASE(text-expression)

#### Parameters

text-expression
The text expression whose characters are to be converted.

#### Examples

Example 8-158 Converting Part of a Text Expression to Uppercase

Suppose you get some new data to add to a mailing list. In the existing mailing list, people's names have the first letter capitalized. In the new data, however, the whole name is in lowercase. You can use UPCASE to make the new data correspond to the current data with a statement similar to the following.

    lastname = JOINCHARS(UPCASE(EXTCHARS(lastname, 1, 1)), -
               EXTCHARS(lastname, 2, NUMCHARS(lastname)))

### 8.147 UPPER

The UPPER function converts all alphabetic characters in a text expression into uppercase.

#### Return Value

The data type of text-expression.

**See Also:**

The [UPPER](../sqlrf/UPPER.md) function in Oracle Database SQL Language Reference

#### Syntax

UPPER(text-expression)

#### Parameters

text-expression
The text expression whose characters are to be converted.

### 8.148 VALSPERPAGE

The VALSPERPAGE program calculates the maximum number of values for a variable of a given width that fits on one page. Pages are units of storage in the workspace.

#### Return Value

INTEGER

#### Syntax

VALSPERPAGE(n)

#### Parameters

n
An `INTEGER` expression specifying the width of a variable in bytes. This value should be between `1` and `4000`. When you specify a value greater than `4000` or less than `1`, the result is `NA`.

#### Usage Notes

Large Variables

Oracle OLAP lets you create very large, multidimensional variables. Theoretically, a variable can contain up to `2**63` cells, although this maximum is subject to memory constraints and other factors specific to your system.

#### Examples

Example 8-159 Calculating the Number of Cells in a Page

The following statement calculates the maximum number of cells available in a single page for a variable with an `INTEGER` data type. The default width of an `INTEGER` value in Oracle OLAP is `4` bytes.

    SHOW VALSPERPAGE(4)

The output of this statement is

    992

### 8.149 VALUES

The VALUES function returns the default status list or the current status list of a dimension or dimension surrogate, or it returns the values in a valueset. VALUES returns a multiline text value that contains one dimension value on a line.

**Note:**

Because composites do not have status, you cannot use the VALUES function with a composite. When you attempt to do so, Oracle OLAP displays an error message.

#### Return Value

TEXT

#### Syntax

VALUES(dimension \[keyword\] \[INTEGER\])

#### Parameters

dimension
A text expression whose value is the name of a dimension, dimension surrogate, or valueset.

keyword
One of the following keywords that specify whether you want the current status list or the default status list for a dimension or a surrogate:

- `NOSTATUS` which indicates that VALUES should return the default status list of a dimension or dimension surrogate rather than its current status list.

- `STATUS` which indicates that VALUES should return the current status list of a dimension or dimension surrogate (Default).

These keywords do not affect valuesets. For a valueset, VALUES returns all the values in that valueset whether you specify `NOSTATUS`, `STATUS`, or nothing.

INTEGER
When you use the INTEGER keyword, the function returns the position numbers of the dimension or dimension surrogate values rather than the values. When you use INTEGER with a valueset, the function returns the position numbers of the values in the existing dimension, not in the valueset.

#### Usage Notes

Using a LIMIT Statement With a STATUS Keyword Rather than VALUES

When possible, when you want Oracle OLAP to use the dimension values that are presently in status, use a [LIMIT (using values) command](olap-dml-commands-h-z.md) with the STATUS keyword (or a LIMIT function with a similar construction) rather than using a VALUES statement. A LIMIT with the STATUS keyword is more efficient than a VALUES (dimname) statement.

Comparing VALUES to CHARLIST

The VALUES function is very similar to the CHARLIST function. `VALUES(MONTH)` returns the same list as `CHARLIST(MONTH)`.

The main differences are:

- For dimensions, the NOSTATUS keyword of VALUES lets you use the default status without first limiting the dimension values to `ALL`.

- The VALUES function lets you use a text expression to specify the dimension or valueset name. See Example 8-162.

Special Considerations for an Ampersand (&)

Under certain circumstances, an ampersand (`&`) that is intended to be a character in a dimension value name is interpreted as ampersand substitution. When this happens, Oracle OLAP generates an error message.

This happens because Oracle OLAP recognizes special characters in dimension value names with when they are used in tuples in text expressions. For example, you can include spaces, such as naming a dimension value `New` `York` instead of `NewYork`. When you have dimension values that include ampersands in their names, refer to Example 8-163.

#### Examples

Example 8-160 Listing the Values of a Valueset

The easiest way to display the values of a valueset is simply by using the name of the valueset in a SHOW or a REPORT statement. You can also use VALUES to list the values in that valueset.

For example, suppose an analytic workspace contains a valueset called `monthset` that has the values `Jan95`, `May95`, and `Dec95`. The following statement displays the values.

    SHOW VALUES(monthset)
    Jan95
    May95
    Dec95

Example 8-161 Listing Position Numbers of a Dimension

You can use VALUES to list the position numbers instead of the actual values in a dimension or valueset. In this example, because you are using the INTEGER keyword with a valueset instead of a dimension, the function returns the position numbers of the values in the `month` dimension as shown by the output returned by the following statement.

    SHOW VALUES(monthset INTEGER)
    61
    65
    72

Therefore, the value `Jan95` is shown as the 61st value in the `month` dimension, `May95` as the 65th value, and `Dec95` as the 72nd value, although they are the first, second, and third values in `monthset`.

Example 8-162 VALUES with Text Variables

This example shows how to assign a dimension name to a text variable and use the text variable in the VALUES function instead of the variable name itself. As the following statements illustrate, when the variable `textvar` has the value `district`, `VALUES(textvar)` returns a list of `district` values.

    textvar = 'district'
    SHOW VALUES(textvar)
    Boston
    Atlanta
    Chicago
    Dallas
    Denver
    Seattle

To list the values of `district` using the CHARLIST function rather than VALUES, you must use an ampersand.

    SHOW CHARLIST(&textvar)

Because ampersands in a program can degrade performance, use VALUES rather than CHARLIST in such cases.

Example 8-163 Workaround for Dimension Value Names Including an Ampersand

When a dimension value name contains an ampersand (`&`) as one of its characters, and when that dimension is a base dimension of a conjoint dimension, then a text expression that contains the names of dimension values in a tuple can generate an error in certain circumstances. This example shows how to avoid this error.

Suppose you use the following statements to define two dimensions.

    DEFINE prod DIMENSION TEXT
    DEFINE geog DIMENSION TEXT

Next, you use the following statements to define two conjoint dimensions.

    DEFINE conj1 DIMENSION <prod geog>
    DEFINE conj2 DIMENSION <prod geog>

The following statements add dimension values to the `prod` and `geog` dimensions.

    MAINTAIN prod ADD 'prod1' 'prod&val2'
    MAINTAIN geog ADD 'geog1' 'geog&val2'

The following statements add tuples (combinations of dimension values) to the CONJ1 conjoint dimension.

    MAINTAIN conj1 ADD <'prod1' 'geog1'>
    MAINTAIN conj1 ADD <'prod&val2' 'geog1'>

Now, suppose you want to use the VALUE function with a MAINTAIN statement to add those same tuples to the `conj2` conjoint dimension. When you attempt to use the following statement, it generates an error message.

    MAINTAIN conj2 ADD VALUES(conj1)
    ERROR: (MXMSERR) val2 does not exist in any attached workspace.

This error occurs because the ampersand in the dimension value name `prod&val2` is interpreted as an attempt at ampersand substitution.

Instead of using the preceding MAINTAIN statement, you can use the following statement to add the tuples to the CONJ2 conjoint dimension.

    MAINTAIN conj2 MERGE < KEY(conj1 prod) KEY(conj1 geog) >

### 8.150 VINTSCHED

The VINTSCHED function calculates the interest portion of the payments on a series of variable-rate installment loans that are paid off over a specified number of time periods. VINTSCHED calculates the result for a given time period as the sum of the interest due on each loan that is incurred or outstanding in that period. For each time period, you specify the initial amount of the loans incurred in that time period and the interest rate that is charged in that time period for each new or outstanding loan.

#### Return Value

DECIMAL

The result returned by the VINTSCHED function is dimensioned by the union of all the dimensions of loans and rates and the dimension that is used as the time-dimension argument.

#### Syntax

VINTSCHED(loans, rates, n, \[time-dimension\] \[STATUS\])

#### Parameters

loans
A numeric expression that contains the initial amounts of the loans. When loans does not have a time dimension, or when loans is dimensioned by multiple time dimensions, the time-dimension argument is required.

rates
A numeric expression that contains the interest rates charged for loans. When rates is a dimensioned variable, it can be dimensioned by any dimension, including a different time dimension. When rates is dimensioned by a time dimension, you specify the interest rate in each time period that applies to the loans incurred or outstanding in that period. The interest rates are expressed as decimal values; for example, a 5 percent rate is expressed as `.05`.

n
A numeric expression that specifies the number of payments required to pay off the loans in the series. The n expression can be dimensioned, but it cannot be dimensioned by the time dimension argument. One payment is made in each time period of the time dimension by which loans is dimensioned or in each time period of the dimension specified in the time-dimension argument. For example, one payment a month is made when loans is dimensioned by `month`.

time-dimension
The name of the dimension along which the interest payments are calculated. When loans has a dimension of type of DAY, WEEK, MONTH, QUARTER, or YEAR, the time-dimension argument is optional, unless loans has multiple dimensions of these types.

STATUS
Specifies that VINTSCHED should use the current status list (that is, only the dimension values currently in status in their current status order) when computing the interest portion of the payments. By default VINTSCHED uses the default status list.

#### Usage Notes

VINTSCHED and NA Values

When loans has a value other than `NA` and the corresponding value of rates is `NA`, an error occurs.

VINTSCHED is affected by the NASKIP option. When NASKIP is set to YES (the default), and a loan value is `NA` for the affected time period, the result returned by VINTSCHED depends on whether the corresponding interest rate has a value of `NA` or a value other than `NA`. The following table illustrates how NASKIP affects the results when a loan or rate value is `NA` for a given time period:

Table 8-21 How NASKIP Affects the Results When a Loan or Rate Value is NA for a Given Time Period

| Loan Value | Rate Value | Result when NASKIP = YES                             | Result when NASKIP = NO        |
|:-----------|:-----------|:-----------------------------------------------------|:-------------------------------|
| Non-`NA`   | `NA`       | Error                                                | Error                          |
| `NA`       | Non-`NA`   | Interest values (`NA` loan value is treated as zero) | `NA` for affected time periods |
| `NA`       | `NA`       | `NA` for affected time periods                       | `NA` for affected time periods |

As an example, suppose a loan expression and a corresponding interest expression both have `NA` values for 1997, but both have values other than `NA` for succeeding years. When the number of payments is `3`, VINTSCHED returns `NA` for 1997, 1996, and 1995. For 1997, VINTSCHED returns the interest portion of the payment due for loans incurred in 1995, 1996, and 1997.

VINTSCHED Ignores the Status of a Time Dimension

The VINTSCHED calculation begins with the first value of the time dimension, regardless of how the status of that dimension may be limited. For example, suppose loans is dimensioned by `year`, and the values of `year` range from `Yr95` to `Yr99`. The calculation always begins with `Yr95`, even when you limit the status of `year` so that it does not include `Yr95`.

However, when loans is not dimensioned by the time dimension, the VINTSCHED calculation begins with the first value in the current status of the time dimension. For example, suppose loans is not dimensioned by `year`, but `year` is specified as time-dimension. When the status of `year` is limited to `Yr97` to `Yr99`, the calculation begins with `Yr97` instead of `Yr95`.

#### Examples

Example 8-164 Using VINTSCHED

The following statements create two variables called `loans` and `rates`.

    DEFINE loans DECIMAL <year>
    DEFINE rates DECIMAL <year>

Suppose you assign the following values to the variables `loans` and `rates`.

    YEAR             LOANS      RATES
    -------------- ---------- ----------
    Yr95               100.00       0.05
    Yr96               200.00       0.06
    Yr97               300.00       0.07
    Yr98                 0.00       0.07
    Yr99                 0.00       0.07

For each year, `loans` contains the initial value of the variable-rate loan incurred during that year. For each year, the value of `rates` is the interest rate that is charged for that year on any loans incurred or outstanding in that year.

The following statement specifies that each loan is to be paid off in three payments, calculates the interest portion of the payments on the loans,

    REPORT W 20 HEADING 'Payment' VINTSCHED(loans, rates, 3, year)

and produces the following report.

    YEAR                        Payment
    -------------- --------------------
    Yr95                           5.00
    Yr96                          16.10
    Yr97                          33.06
    Yr98                          19.43
    Yr99                           7.48

The interest payment for 1995 is interest on the loan of \$100 incurred in 1995, at 5 percent. The interest payment for 1996 is the sum of the interest on the remaining principal of the 1995 loan, plus interest on the loan of \$200 incurred in 1996; the interest rate for both loans is 6 percent. The 1997 interest payment is the sum of the interest on the remaining principal of the 1995 loan, interest on the remaining principal of the 1996 loan, and interest on the loan of \$300 incurred in 1997; the interest rate for all three loans is 7 percent. Because the 1995 loan is paid off in 1997, the payment for 1998 represents 7 percent interest on the remaining principal of the 1996 and 1997 loans. In 1999, the interest payment is on the remaining principal of the 1997 loan.

### 8.151 VPMTSCHED

The VPMTSCHED function calculates a payment schedule (principal plus interest) for paying off a series of variable-rate installment loans over a specified number of time periods. VPMTSCHED calculates the payment for a given time period as the sum of the principal and interest due on each loan that is incurred or outstanding in that period. For each time period, you specify the initial amount of the loans incurred in that time period and the interest rate that is charged in that time period for each new or outstanding loan.

#### Return Value

DECIMAL

The result returned by the VPMTSCHED function is dimensioned by the union of all the dimensions of loans and rates and the dimension used as the time-dimension argument.

#### Syntax

VPMTSCHED(loans, rates, n, \[time-dimension\] \[STATUS\])

#### Parameters

loans
A numeric expression that contains the initial amounts of the loans. When loans does not have a time dimension, or when loans is dimensioned by multiple time dimensions, the time-dimension argument is required.

rates
A numeric expression that contains the interest rates charged for loans. When rates is a dimensioned variable, it can be dimensioned by any dimension, including a different time dimension. When rates is dimensioned by a time dimension, you specify the interest rate in each time period that applies to the loans incurred or outstanding in that period. The interest rates are expressed as decimal values; for example, a 5 percent rate is expressed as .05.

n
A numeric expression that specifies the number of payments required to pay off the loans in the series. The n expression can be dimensioned, but it cannot be dimensioned by the time dimension argument. One payment is made in each time period of the time dimension by which loans is dimensioned or in each time period of the dimension specified in the time-dimension argument. For example, one payment a month is made when loans is dimensioned by `month`.

time-dimension
The name of the dimension along which the interest payments are calculated. When loans has a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, the time-dimension argument is optional, unless loans has more than dimension of this type.

STATUS
Specifies that VPMTSCHED should use the current status list (that is, only the dimension values currently in status in their current status order) when computing the payment schedule. By default VPMTSCHED uses the default status list.

#### Usage Notes

VPMTSCHED and NA Values

When loans has a value other than `NA` and the corresponding value of rates is `NA`, an error occurs.

VPMTSCHED is affected by the NASKIP option. When NASKIP is set to YES (the default), and a loan value is `NA` for the affected time period, the result returned by VPMTSCHED depends on whether the corresponding interest rate has a value of `NA` or a value other than `NA`. Table 8-21 illustrates how NASKIP affects the results when a loan or rate value is `NA` for a given time period.

As an example, suppose a loan expression and a corresponding interest expression both have `NA` values for 1994, but both have values other than `NA` for succeeding years. When the number of payments is 3, VPMTSCHED returns `NA` for 1994, 1995, and 1996. For 1997, VPMTSCHED returns the payment due for loans incurred in 1995, 1996, and 1997.

VPTMPTSCHED Ignores the Status of the Time Dimension

The VPMTSCHED calculation begins with the first value of the time dimension, regardless of how the status of that dimension may be limited. For example, suppose loans is dimensioned by `year`, and the values of `year` range from `Yr95` to `Yr99`. The calculation always begins with `Yr95`, even when you limit the status of `year` so that it does not include `Yr95`.

However, when loans is not dimensioned by the time dimension, the VPMTSCHED calculation begins with the first value in the current status of the time dimension. For example, suppose loans is not dimensioned by `year`, but `year` is specified as time-dimension. When the status of `year` is limited to `Yr97` to `Yr99`, the calculation begins with `Yr97` instead of `Yr95`.

#### Examples

Example 8-165 Using VPMTSCHED

The following statements create two variables called `loans` and `rates`.

    DEFINE loans DECIMAL <year>
    DEFINE rates DECIMAL <year>

Suppose you assign the following values to the variables `loans` and `rates`.

    YEAR             LOANS      RATES
    -------------- ---------- ----------
    Yr95               100.00       0.05
    Yr96               200.00       0.06
    Yr97               300.00       0.07
    Yr98                 0.00       0.07
    Yr99                 0.00       0.07

For each year, `loans` contains the initial value of the variable-rate loan incurred during that year. For each year, the value of `rates` is the interest rate that is charged for that year on any loans incurred or outstanding in that year.

The following statement specifies that each loan is to be paid off in three payments, calculates the schedule for paying off the principal and interest on the loans,

    REPORT W 20 HEADING 'Payment' VPMTSCHED(loans, rates, 3, year)

and produces the following report.

    YEAR                        Payment
    -------------- --------------------
    Yr95                          36.72
    Yr96                         112.06
    Yr97                         227.78
    Yr98                         190.19
    Yr99                         114.32

The payment for 1995 is the principal due on the loan of \$100 incurred in 1995, plus interest on the loan at 5 percent. The payment due in 1996 is the sum of the second payment of principal on the loan incurred in 1995, plus the first payment of principal on the loan of \$200 incurred in 1996, plus interest on the remaining principals of both loans at 6 percent. The 1997 payment is the sum of the third and final principal payment on the loan incurred in 1995, the second of the three principal payments on the 1996 loan, the first payment of principal on the loan of \$300 incurred in 1997, plus interest on the remaining principals of all three loans at 7 percent. Because the 1995 loan is paid off in 1997, the payment for 1998 covers the principal and interest for the 1996 and 1997 loans. The payment for 1999 is the final payment of principal and interest for the 1997 loan.

### 8.152 VSIZE

The VSIZE function returns the number of bytes in the internal representation of an expression.

#### Return Value

INTEGER

If expr is null, then this function returns NA.

#### Syntax

VSIZE(expr)

#### Parameters

expr
An expression of any data type.

### 8.153 WEEKOF

The WEEKOF function returns an `INTEGER` in the range of 1 to 53, which gives the week of the year in which a specified date falls. The result has the same dimensions as the specified `DATE` expression.

#### Return Value

`INTEGER`

#### Syntax

WEEKOF(date-expression)

#### Parameters

date-expression
An expression that has the DATE data type, or a text expression that specifies a date. The values of the text expression are converted automatically to DATE values, using the current setting of the DATEORDER option to resolve any ambiguity.

#### Usage Notes

Determining Week 1

The value of WEEKDSYSNEWYEAR specifies how many days of the new year there must be in the week for WEEKOF to consider it to be week 1 of the new year. For example, when January 1 is on a Wednesday, then the week of December 29 to January 4 has four days in the new year. WEEKDSYSNEWYEAR must therefore have a value of 4 or less for that week to be counted as week 1. This determination of week 1 affects the numbering of all weeks in the year.

#### Examples

Example 8-166 Finding Today's Week

The following statement sends the week of the year in which today's date falls to the current outfile.

    SHOW WEEKOF(TODAY)

When today's date is August 5, 1996, which is a Monday, this statement produces the following output.

    32

Example 8-167 Finding the Week of a Date

The following statement sends the week of the year in which July 4 falls in 1996 to the current outfile.

    SHOW WEEKOF('04JUL96')

This statement produces the following output.

    27

### 8.154 WIDTH_BUCKET

For a given expression, the WIDTH_BUCKET function returns the bucket number into which the value of this expression would fall after being evaluated.

#### Return Value

An `INTEGER`.

#### Syntax

WIDTH_BUCKET (expr , min_value , max_value , num_buckets)

#### Parameters

expr
The expression for which the histogram is being created. This expression must evaluate to a number or a datetime value. When expr evaluates to `NA`, then the expression returns `NA`.

min_value
An expression that resolves to the minimum end point of the acceptable range for expr. This expression must evaluate to number or datetime values, and cannot evaluate to `NA`.

max_value
An expression that resolves to the maximum end point of the acceptable range for expr. This expression must evaluate to number or datetime values, and cannot evaluate to `NA`.

num_buckets
An expression that resolves to a constant indicating the number of buckets. This expression must evaluate to a positive `INTEGER`.

#### Usage Notes

Underflow and Overflow Buckets

WIDTH_BUCKET also creates (when needed) an underflow bucket numbered `0` and an overflow bucket numbered num_buckets`+1`. These buckets handle values less than min_value and more than max_value and are helpful in checking the reasonableness of endpoints.

Constructing Equiwidth Histograms

WIDTH_BUCKET lets you construct equiwidth histograms, in which the histogram range is divided into intervals that have identical size. (Compare this function with NTILE, which creates equiheight histograms.) Ideally each bucket is a "closed-open" interval of the real number line. For example, a bucket can be assigned to cores between `10.00` and `19.999...` to indicate that `10` is included in the interval and `20` is excluded. A bucket of this size is sometimes denoted as `(10,` `20)`.

#### Examples

Example 8-168 Grouping Values Into a Ten-Bucket Histogram

The following example limits the customers to those customers who have a `customer_id` of 825 through 853 and, then, creates a ten-bucket histogram on the `credit_limit` variable for those customer. It uses the `credit_group` formula to calculate the bucket number for each customer. Customers with credit limits greater than the maximum value are assigned to the overflow bucket, 11.

    DESCRIBE
    DEFINE customer_id DIMENSION INTEGER
    DEFINE cust_last_name VARIABLE TEXT <customer_id>
    DEFINE credit_limit VARIABLE INTEGER <customer_id>
    DEFINE credit_group FORMULA INTEGER <customer_id>
    EQ WIDTH_BUCKET(credit_limit, 100, 5000, 10)

    LIMIT customer_id to 825 TO 853
    REPORT cust_last_name, credit_limit, credit_group

    CUSTOMER_ID     CUST_LAST_NAME    CREDIT_LIMIT     CREDIT_GROUP
    -------------- ---------------- ---------------- ----------------
               825 Dreyfuss                      500                1
               826 Barkin                        500                1
               827 Siegel                        500                1
               828 Minnelli                    2,300                5
               829 Hunter                      2,300                5
               830 Dutt                        3,500                7
               831 Bel Geddes                  3,500                7
               832 Spacek                      3,500                7
               833 Moranis                     3,500                7
               834 Idle                        3,500                7
               835 Eastwood                    1,200                3
               836 Berenger                    1,200                3
               837 Stanton                     1,200                3
               838 Nicholson                   3,500                7
               839 Johnson                     3,500                7
               840 Elliott                     1,400                3
               841 Boyer                       1,400                3
               842 Stern                       1,400                3
               843 Oates                         700                2
               844 Julius                        700                2
               845 Fawcett                     5,000               11
               846 Brando                      5,000               11
               847 Streep                      5,000               11
               848 Olmos                       1,800                4
               849 Kaurusmdki                  1,800                4
               850 Finney                      2,300                5
               851 Brown                       2,300                5
               852 Tanner                      2,300                5
               853 Palin                         400                1


### 8.155 WKSDATA

The WKSDATA function returns the data type of each individual cell in a worksheet or the data type of a program argument with the WORKSHEET data type. You can use WKSDATA to help in the process of transferring labels and data between text files and Oracle OLAP.

#### Return Value

The data type of individual worksheet cells.

#### Syntax

WKSDATA(worksheetname)

#### Parameters

worksheetname
Specifies the name of an Oracle OLAP worksheet object, such as `workunits`.

#### Usage Notes

Checking One or More Cells

You can use WKSDATA to return the data type of a single worksheet cell by using a qualified data reference for the cell, as in the following format.

SHOW WKSDATA(worksheetname(WKSROW n, WKSCOL n))

Or you can use a REPORT statement in this format with WKSDATA to provide the contents of all the cells in a worksheet side-by-side with their data types.

REPORT worksheetname WKSDATA(worksheetname)

Multiple Data Types

Always use care when using worksheet objects in expressions. Because a worksheet object can contain multiple data types, the actual data type of individual worksheet cells is not considered when an OLAP DML statement is compiled. Instead, code is generated to convert each worksheet cell to the data type it expects at that position in the expression which may lead to unexpected results in some cases.

Text Data

All textual data (as opposed to numeric, Boolean, date, and so on) in a worksheet has the TEXT data type. The ID and NTEXT data types are not supported in worksheets.

#### Examples

Example 8-169 Checking Data Imported from a Worksheet

Suppose you have imported a flat data file into a worksheet called `workunits`. You can use WKSDATA to provide a quick way to determine which areas to treat as dimension values and which as data values in bringing the worksheet into standard OLAP workspace format.

This statement produces this output following the statement that shows the data in `workunits`

    REPORT workunits

                   -----------------WORKUNITS-----------------
                   ------------------WKSCOL-------------------
    WKSROW             1          2          3          4
    -------------- ---------- ---------- ---------- ----------
                 1         NA Jan96      Feb96      Mar96
                 2 Tents             307        209        277
                 3 Canoes            352        411        488
                 4 Racquets        1,024      1,098      1,144
                 5 Sportswear      1,141      1,262      1,340
                 6 Footwear        2,525      2,660      2,728

This statement uses the WKSDATA function to produce the report following the statement, which shows the data type of each cell in the worksheet.

    REPORT WKSDATA(workunits)

                   ------------WKSDATA(WORKUNITS)-------------
                   ------------------WKSCOL-------------------
    WKSROW             1          2          3          4
    -------------- ---------- ---------- ---------- ----------
                 1         NA TEXT       TEXT       TEXT
                 2 TEXT       INTEGER    INTEGER    INTEGER
                 3 TEXT       INTEGER    INTEGER    INTEGER
                 4 TEXT       INTEGER    INTEGER    INTEGER
                 5 TEXT       INTEGER    INTEGER    INTEGER
                 6 TEXT       INTEGER    INTEGER    INTEGER

### 8.156 WRITABLE

The WRITABLE function returns `TRUE` when the user has WRITE permission for the object and `FALSE` when the user does not or when the object is not a variable, worksheet object, relation, or valueset.

#### Return value

`BOOLEAN`

The result has the same dimensions as expression.

#### Syntax

WRITABLE (expression)

#### Parameters

expression
An expression that is the name or QDR of an object that has values (that is, a variable, relation, valueset, or worksheet object).

### 8.157 YYOF

The YYOF function returns an `INTEGER` in the range of 1000 to 9999, giving the year in which a specified date falls. The result returned by YYOF has the same dimensions as the specified date expression.

#### Return Value

`INTEGER`

#### Syntax

YYOF(date-expression)

#### Parameters

date-expression
An expression that has the DATE data type, or a text expression that specifies a date. The values of the text expression are converted automatically to DATE values, using the current setting of the DATEORDER option to resolve any ambiguity.

#### Usage Notes

Commas in Year Values

When the COMMAS option is set to YES when you display the value returned by YYOF, the year is displayed with a comma separating the thousands (for example, `1,996`). To avoid this, you can set the COMMAS option to `NO` before displaying the year.

#### Examples

Example 8-170 Obtaining the Current Year

The following statements send the year in which today's date falls to the current outfile.

    COMMAS = NO
    SHOW YYOF(TODAY)

When today's date is January 15, 1996, these statements produce the following output.

    1996
