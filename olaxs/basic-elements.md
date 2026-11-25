This chapter describes the basic building blocks of the OLAP expression syntax. It contains these topics:

- Dimensional Object Names

- Dimensional Data Types

- Operators

- Conditions

- Literal Expressions

- CASE Expressions

- Qualified Data References (QDRs)

### 1.1 Dimensional Object Names

The naming conventions for dimensional objects follow standard Oracle naming rules. All names are case-insensitive.

#### 1.1.1 Syntax

    owner.{ cube | dimension | table }.{ measure | column | attribute }

Table 1-1 Naming Conventions for Dimensional Objects

| Convention        | Quoted ID                                                                                                                | Unquoted ID                                                                                                                                                                                                                          |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Initial Character | Any character.                                                                                                           | Alphabetic character from the database character set.                                                                                                                                                                                |
| Other Characters  | All characters, punctuation marks, and spaces are permitted.<br>Double quotation marks and nulls (\0) are not permitted. | Alphanumeric characters from the database character set and underscore (\_) are permitted.<br>The dollar sign (\$) and pound sign (#) are permitted but not recommended.<br>Double quotation marks and nulls (\0) are not permitted. |
| Reserved Words    | Permitted but not recommended.                                                                                           | Not permitted.                                                                                                                                                                                                                       |

#### 1.1.2 Examples

`GLOBAL.UNITS_CUBE.SALES` identifies the `SALES` measure in the Units Cube.

`TIME.DIM_KEY` and `TIME.LEVEL_NAME` identify columns in the Time view.

`TIME.CALENDAR` identifies the `CALENDAR` hierarchy in the Time dimension.

`TIME.CALENDAR.CALENDAR_YEAR` identifies the `CALENDAR_YEAR` level of the `CALENDAR` hierarchy in the Time dimension.

`GLOBAL.UNITS_FACT.MONTH_ID` identifies a foreign key column in the `UNITS_FACT` table.

`TIME_DIM.CALENDAR_YEAR_DSC` identifies a column in the `TIME_DIM` table.

### 1.2 Dimensional Data Types

Table 1-2 describes the data types that can be used for cubes and measures.

Table 1-2 Dimensional Data Types

| Data Type                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:----------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BINARY_DOUBLE`                                                       | A 64-bit floating number. A `BINARY_DOUBLE` value requires 9 bytes.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `BINARY_FLOAT`                                                        | A 32-bit floating number. A `BINARY_FLOAT` value requires 5 bytes.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `CHAR (``size`` [BYTE|CHAR])`                                         | A fixed length character string with a length of size characters or bytes. The size can range from 1 to 2000.                                                                                                                                                                                                                                                                                                                                                                                             |
| `DATE`                                                                | A valid date in the range from January 1, 4712 BC to December 31, 9999 CE. It contains the datetime fields `YEAR`, `MONTH`, `DAY`, `HOUR`, `MINUTE`, and `SECOND`. It does not have fractional seconds or a time zone. The default format is determined explicitly by the `NLS_DATE_FORMAT` parameter and implicitly by the `NLS_TERRITORY` parameter. A `DATE` value requires 7 bytes.                                                                                                                   |
| `DECIMAL (``p,s``)`                                                   | A decimal number with precision p and scale s represented as a `NUMBER` data type.                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `FLOAT [(``p``)]`                                                     | A subtype of `NUMBER` with precision p. A `FLOAT` is represented internally as `NUMBER`. The precision can range from 1 to 126 binary digits. A `FLOAT` value requires from 1 to 22 bytes.                                                                                                                                                                                                                                                                                                                |
| `INTEGER`                                                             | A whole number represented as a `NUMBER` data type with a scale of 0.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `INTERVAL DAY[(``day_precision``)] TO SECOND[(``second_precision``)]` | A period of time in days, hours, minutes, and seconds. The day precision is the maximum number of digits in the `DAY` datetime field. The default is 2. The second precision is the number of digits in the fractional part of the `SECOND` field. The default value is 6. Both day and second precision can have a value from 0 to 9. An `INTERVAL DAY TO SECOND` value requires 11 bytes.                                                                                                               |
| `INTERVAL YEAR[(``precision``)] TO MONTH`                             | A period of time in years and months. The precision is the number of digits in the `YEAR` datetime field, which can have a value of 0 to 9. The default precision is 2 digits. An `INTERVAL YEAR TO MONTH` value requires 5 bytes.                                                                                                                                                                                                                                                                        |
| `NCHAR[(``size``)]`                                                   | A fixed length character string with a length of size characters. The size can range from 1 character to 2000 bytes. The maximum number of characters depends on the national character set, which can require up to four bytes per character.                                                                                                                                                                                                                                                            |
| `NUMBER [(``p``[,``s``])]`                                            | A decimal number with precision p and scale s. The precision can range from 1 to 38. The scale can range from -84 to 127. A `NUMBER` value requires from 1 to 22 bytes.                                                                                                                                                                                                                                                                                                                                   |
| `NVARCHAR2(``size``)`                                                 | A variable length Unicode character string with a maximum length of size characters. The size can range from 1 character to 32,767 bytes. The maximum number of characters depends on the national character set, which can require up to four bytes per character.                                                                                                                                                                                                                                       |
| `TIMESTAMP[(``precision``)]`                                          | A valid date that contains the datetime fields `YEAR`, `MONTH`, `DAY`, `HOUR`, `MINUTE`, and `SECOND`. It does not have a time zone. The precision is the number of digits in the fractional part of the `SECOND` field, which can have a value of 0 to 9. The default precision is 6 digits. The default format is determined explicitly by the `NLS_DATE_FORMAT` parameter and implicitly by the `NLS_TERRITORY` parameter. A `TIMESTAMP` value requires from 7 to 11 bytes depending on the precision. |
| `TIMESTAMP [(``precision``)] WITH LOCAL TIME ZONE`                    | A valid date with the same description as `TIMESTAMP WITH TIME ZONE` with these exceptions:<br>• The data is stored in the database with the database time zone.<br>• The data is converted to the session time zone when it is retrieved.<br>• A `TIMESTAMP WITH LOCAL TIME ZONE` value requires from 7 to 11 bytes depending on the precision.                                                                                                                                                          |
| `TIMESTAMP[(``precision``)] WITH TIME ZONE`                           | A valid date that contains the datetime fields `YEAR`, `MONTH`, `DAY`, `HOUR`, `MINUTE`, `SECOND`, `TIMEZONE_HOUR`, and `TIMEZONE_MINUTE`. The precision is the number of digits in the fractional part of the `SECOND` field, which can have a value of 0 to 9. The default precision is 6 digits. The default format is determined explicitly by the `NLS_DATE_FORMAT` parameter and implicitly by the `NLS_TERRITORY` parameter. A `TIMESTAMP WITH TIMEZONE` value requires 13 bytes.                  |
| `VARCHAR2(``size`` [BYTE|CHAR])`                                      | A variable length character string with a maximum length of size characters or bytes. The size can range from 1 to 32,767 bytes.                                                                                                                                                                                                                                                                                                                                                                          |

### 1.3 Operators

An operator manipulates data items and returns a result. Operators manipulate individual data items called operands or arguments. They are represented by special characters or by keywords. Syntactically, an operator appears before an operand, after an operand, or between two operands.

The OLAP Expression Syntax has these types of operators:

- Unary Arithmetic Operators

- Binary Arithmetic Operators

- Concatenation Operator

For conditional operators, go to "Conditions".

#### 1.3.1 Unary Arithmetic Operators

A unary operator operates on only one operand.

Table 1-3 Unary Operators

| Operator | Description    |
|:---------|:---------------|
| \+       | Positive value |
| \-       | Negative value |

##### 1.3.1.1 Syntax

    operator operand

##### 1.3.1.2 Example

`-5` is a negative number.

#### 1.3.2 Binary Arithmetic Operators

A binary operator operates on two operands.

Table 1-4 Binary Operators

| Operator | Description |
|:---------|:------------|
| \+       | Add         |
| \-       | Subtract    |
| \*       | Multiply    |
| /        | Divide      |

##### 1.3.2.1 Syntax

    operand operator operand

##### 1.3.2.2 Examples

Here are two simple examples using numeric literals for the operands.

`7 * 2` is `14`.

`(8/2) + 1` is `5`.

This example multiplies the values of the Sales measure by a numeric literal to create a calculated measure named Sales Budget.

`UNITS_CUBE.SALES * 1.06`

Table 1-5 Multiplication Operator Example

| Product      | Level  | Sales     | Sales Budget |
|:-------------|:-------|:----------|:-------------|
| Hardware     | CLASS  | 124191336 | 131642816    |
| Desktop PCs  | FAMILY | 74556528  | 79029919     |
| Monitors     | FAMILY | 3972142   | 4210470      |
| Memory       | FAMILY | 5619219   | 5956372      |
| Modems/Fax   | FAMILY | 5575726   | 5910269      |
| CD/DVD       | FAMILY | 16129497  | 17097267     |
| Portable PCs | FAMILY | 18338225  | 19438518     |

The next example creates a calculated measure named Profit by subtracting Cost from Sales.

`UNITS_CUBE.SALES - UNITS_CUBE.COST`

| Product      | Level  | Sales     | Cost      | Profit  |
|:-------------|:-------|:----------|:----------|:--------|
| Hardware     | CLASS  | 124191336 | 116058248 | 8133088 |
| Desktop PCs  | FAMILY | 74556528  | 71937312  | 2619215 |
| Monitors     | FAMILY | 3972142   | 3546195   | 425947  |
| Memory       | FAMILY | 5619219   | 4962527   | 656692  |
| Modems/Fax   | FAMILY | 5575726   | 5162879   | 412847  |
| CD/DVD       | FAMILY | 16129497  | 12510832  | 3618664 |
| Portable PCs | FAMILY | 18338225  | 17938502  | 399723  |

#### 1.3.3 Concatenation Operator

The concatenation operator (`||`) combines text expressions.

##### 1.3.3.1 Syntax

    operand || operand

##### 1.3.3.2 Example

`'The date today is: ' || sysdate` generates a text string such as `The date today is: 23-AUG-06`.

The next example concatenates the level name and dimension keys of the Product dimension to create an identifier.

`PRODUCT.LEVEL_NAME || ' ' || PRODUCT.DIM_KEY`

| Level  | Dim Key | Identifier  |
|:-------|:--------|:------------|
| CLASS  | HRD     | CLASS HRD   |
| FAMILY | DTPC    | FAMILY DTPC |
| FAMILY | MON     | FAMILY MON  |
| FAMILY | MEM     | FAMILY MEM  |
| FAMILY | MOD     | FAMILY MOD  |
| FAMILY | DISK    | FAMILY DISK |
| FAMILY | LTPC    | FAMILY LTPC |

### 1.4 Conditions

A condition specifies a combination of one or more expressions and logical (Boolean) operators. The OLAP Expression Syntax has these types of conditions:

- Simple Comparison Conditions

- Group Comparison Conditions

- Range Conditions

- Multiple Conditions

- Negation Conditions

- Special Conditions

- Pattern-Matching Conditions

#### Return Value

`NUMBER` (`0=FALSE, 1=TRUE`)

#### 1.4.1 Simple Comparison Conditions

Comparison conditions compare one expression with another.

You can use these comparison operators:

Table 1-6 Simple Comparison Operators

| Operator   | Description              |
|:-----------|:-------------------------|
| `>`        | Greater than             |
| `>=`       | Greater than or equal to |
| `<`        | Less than                |
| `<=`       | Less than or equal to    |
| `=`        | Equal to                 |
| `!= ˆ= <>` | Not equal to             |

##### 1.4.1.1 Syntax

    expr { > | >= | < | <= | = | != | ˆ= | <> } expr

##### 1.4.1.2 Arguments

`expr` can be any expression.

##### 1.4.1.3 Examples

`5 > 3` is true, `4 != 5` is true, `6 >= 9` is false.

#### 1.4.2 Group Comparison Conditions

A group comparison condition specifies a comparison with any or all members in a list or subquery.

You can use these comparison operators:

Table 1-7 Group Comparison Operators

| Operator   | Description                                                                                |
|:-----------|:-------------------------------------------------------------------------------------------|
| `>`        | Greater than                                                                               |
| `>=`       | Greater than or equal to                                                                   |
| `<`        | Less than                                                                                  |
| `<=`       | Less than or equal to                                                                      |
| `=`        | Equal to                                                                                   |
| `!= ˆ= <>` | Not equal to                                                                               |
| `ANY SOME` | Returns true if one or more values in the list match, or false if no values match.         |
| `ALL`      | Returns true if all values in the list match, or false if one or more values do not match. |

##### 1.4.2.1 Syntax

    expr
         { = | != | ˆ= | <> | > | < | >= | <= }
         { ANY | SOME | ALL }
         ({ expression_list | subquery })

##### 1.4.2.2 Examples

`5 <= ALL (5, 10, 15)` is true, `5 <> ANY (5, 10, 15)` is true.

#### 1.4.3 Hierarchical Relation Conditions

Hierarchical relation conditions specify the comparison of the relationship of a hierarchy member to itself or to another member of the hierarchy.

##### 1.4.3.1 Syntax

    expr1 IS [ NOT ]
     { PARENT
     | CHILD
     | ANCESTOR
     | ROOT_ANCESTOR
     | DESCENDANT
     | LEAF_DESCENDANT
     | RELATIVE
     }
     [ OR SELF ] OF expr2 WITHIN hierarchy

##### 1.4.3.2 Arguments

`expr1` is any expression, including a literal or a column, that resolves to a dimension member.

`PARENT` compares expr1 as the parent of expr2.

`CHILD` compares expr1 as a child of expr2.

`ANCESTOR` compares expr1 as an ancestor of expr2.

`ROOT_ANCESTOR` compares expr1 as the highest-level ancestor of expr2.

`DESCENDANT` compares expr1 as a descendant of expr2.

`LEAF_DESCENDANT` compares expr1 as a descendant that has no children of expr2.

`RELATIVE` compares expr1 as a dimension member that has a parent in common with expr2.

`OR SELF` compares expr1 as the same dimension member as expr2.

`expr2` is any expression, including a literal or a column, that resolves to a dimension member.

hierarchy is the hierarchy to consider when determining the relationship between expr1 and expr2, expressed in the form dimension_name`.`hierarchy_name, as in `PRODUCT.PRIMARY`, or owner`.`dimension_name.hierarchy_name, as in `GLOBAL.PRODUCT.PRIMARY`.

##### 1.4.3.3 Examples

    TIME.DIM_KEY IS CHILD OR SELF OF 'FY2008' WITHIN TIME.FISCAL
    'FY2008' IS ROOT_ANCESTOR OR SELF OF TIME.DIM_KEY WITHIN TIME.FISCAL
    'MEMORY' IS NOT ANCESTOR OF PRODUCT.DIM_KEY WITHIN GLOBAL.PRODUCT.PRIMARY

#### 1.4.4 Range Conditions

The `BETWEEN` operator tests whether a value is in a specific range of values. It returns true if the value being tested is greater than or equal to a low value and less than or equal to a high value.

##### 1.4.4.1 Syntax

    expr [ NOT ] BETWEEN expr AND expr

##### 1.4.4.2 Example

`7 NOT BETWEEN 10 AND 15` is true.

#### 1.4.5 Multiple Conditions

Conjunctions compare a single expression with two conditions.

Table 1-8 Conjunctions

| Operator | Description                                                                           |
|:---------|:--------------------------------------------------------------------------------------|
| `AND`    | Returns true if both component conditions are true. Returns false if either is false. |
| `OR`     | Returns true if either component condition is true. Returns false if both are false.  |

##### 1.4.5.1 Syntax

    expr operator condition1 { AND | OR } condition2

##### 1.4.5.2 Example

`5 < 7 AND 5 > 3` is true; `5 < 3 OR 10 < 15` is true.

#### 1.4.6 Negation Conditions

The `NOT` operator reverses the meaning of a condition. It returns true if the condition is false. It returns false if the condition is true.

##### 1.4.6.1 Syntax

    NOT {BETWEEN | IN | LIKE | NULL }

##### 1.4.6.2 Example

`5 IS NOT NULL` is true; `5 NOT IN (5, 10, 15)` is false.

#### 1.4.7 Special Conditions

The `IS` operator tests for special conditions, such as nulls, infinity and values that are not numbers.

Table 1-9 Special Conditions Operators

| Operator      | Description                                                                            |
|:--------------|:---------------------------------------------------------------------------------------|
| `IS INFINITE` | Returns true if the expression is infinite, or false otherwise. For mappings only.     |
| `IS NAN`      | Returns true if the expression is not a number, or false otherwise. For mappings only. |
| `IS NULL`     | Returns true if the expression is null, or false otherwise.                            |

##### 1.4.7.1 Syntax

    expr IS [ NOT ] NULL

##### 1.4.7.2 Example

`13 IS NOT NULL` is true.

#### 1.4.8 Pattern-Matching Conditions

The pattern-matching conditions compare character data.

##### 1.4.8.1 LIKE Operators

The `LIKE` operators specify a test involving pattern matching. Whereas the equality operator (`=`) exactly matches one character value to another, the `LIKE` operators can match patterns defined by special pattern-matching ("wildcard") characters.

You can choose from these `LIKE` operators:

Table 1-10 LIKE Pattern-Matching Operators

| Operator | Description                                                                                      |
|:---------|:-------------------------------------------------------------------------------------------------|
| `LIKE`   | Uses characters in the input character set.                                                      |
| `LIKEC`  | Uses Unicode complete characters. It treats a Unicode supplementary character as two characters. |
| `LIKE2`  | Uses UCS2 code points. It treats a Unicode supplementary character as one character.             |
| `LIKE4`  | Uses UCS4 code points. It treats a composite character as one character.                         |

##### 1.4.8.2 Syntax

    char1 [ NOT ] ( LIKE | LIKEC | LIKE2 | LIKE4 )
      char2 [ ESCAPE esc_char ]

##### 1.4.8.3 Arguments

`char1` is a text expression for the search value.

`char2` is a text expression for the pattern. The pattern can contain these wildcard characters:

- An underscore (\_) matches exactly one character (as opposed to one byte in a multibyte character set) in the value.

- A percent sign (%) can match zero or more characters (as opposed to bytes in a multibyte character set) in the value. A '%' cannot match a null.

`esc_char` is a text expression, usually a literal, that is one character long. This escape character identifies an underscore or a percent sign in the pattern as literal characters instead of wildcard characters. You can also search for the escape character itself by repeating it. For example, if @ is the escape character, then you can use @% to search for % and @@ to search for @.

##### 1.4.8.4 Examples

`'Ducks' LIKE 'Duck_'` and `'Ducky' LIKE 'Duck_'` are true.

`'Duckling' LIKE 'Duck_'` is false.

`'Duckling' LIKE 'Duck%'` is true.

### 1.5 Literal Expressions

The OLAP Expression Syntax has three types of literal expressions: strings, numbers, and null. Other data types must be created using conversion functions such as `TO_DATE`.

The terms text literal, character literal, and string are used interchangeably. They are always enclosed in single quotes to distinguish them from object names.

#### 1.5.1 Examples

    'A Literal Text String'

    'A Literal Text String with ''Quotes '''

    'A Literal Text String
    That Crosses Into a Second Line'

    2

    2.4

    +1

    -1

    NULL

### 1.6 CASE Expressions

`CASE` expressions let you use `IF`... `THEN`... `ELSE` logic in expressions.

In a simple case expression, `CASE` searches for the first `WHEN`... `THEN` pair for which `expr` equals `comparison_expr,` then it returns `return_expr`. If none of the `WHEN`... `THEN` pairs meet this condition, and an `ELSE` clause exists, then `CASE` returns `else_expr`. Otherwise, `CASE` returns `NULL`.

In a searched `CASE` expression, `CASE` searches from left to right until it finds an occurrence of `condition` that is true, and then returns `return_expr`. If no `condition` is found to be true, and an `ELSE` clause exists, `CASE` returns `else_expr`. Otherwise, `CASE` returns `NULL`.

#### 1.6.1 Return Value

Same as the `else_expression` argument

#### 1.6.2 Syntax

    CASE { simple_case_expression
         | searched_case_expression
         }
         [ ELSE else_expression ]
         END

    simple_case_expression::=
         expr WHEN comparison_expr
              THEN return_expr
              [ WHEN comparison_expr
                THEN return_expr ]...

    searched_case_expression::=
         WHEN condition THEN return_expr
         [ WHEN condition THEN return_expr ]...

#### 1.6.3 Arguments

`expr` is the base expression being tested.

`comparison_expr` is the expression against which `expr` is being tested. It must be the same basic data type (numeric or text) as `expr`.

`condition` is a conditional expression.

`return_expr` is the value returned when a match is found or the condition is true.

#### 1.6.4 Examples

This statement returns `Single Item` or `Value Pack` depending on whether the `PACKAGE` attribute of the `PRODUCT` dimension is null or has a value:

    CASE PRODUCT.PACKAGE WHEN NULL THEN 'Single Item'  ELSE 'Value Pack'END

| Product                       | Package           | Category    |
|:------------------------------|:------------------|:------------|
| 1.44MB External 3.5" Diskette | Executive         | Value Pack  |
| 1GB USB Drive                 | --                | Single Item |
| 512MB USB Drive               | --                | Single Item |
| 56Kbps V.90 Type II Modem     | Executive         | Value Pack  |
| 56Kbps V.92 Type II Fax/Modem | Laptop Value Pack | Value Pack  |
| Deluxe Mouse                  | Executive         | Value Pack  |
| Envoy Ambassador              | --                | Single Item |
| Envoy Executive               | Executive         | Value Pack  |
| Envoy External Keyboard       | Executive         | Value Pack  |
| Envoy Standard Laptop         | Value Pack        | Value Pack  |
| External - DVD-RW - 8X        | Executive         | Value Pack  |
| External 101-key keyboard     | Multimedia        | Value Pack  |
| External 48X CD-ROM           | --                | Single Item |
| Internal - DVD-RW - 6X        | Multimedia        | Value Pack  |

The next statement increases the unit price by 20%, truncated to the nearest dollar, if the difference between price and cost is less than 10%. Otherwise, it returns the current unit price.

    CASE
      WHEN PRICE_CUBE.UNIT_PRICE < PRICE_CUBE.UNIT_COST * 1.1
      THEN TRUNC(PRICE_CUBE.UNIT_COST * 1.2)  ELSE PRICE_CUBE.UNIT_PRICE
    END

| Product                       | Cost    | Price   |
|:------------------------------|:--------|:--------|
| 1GB USB Drive                 | 483.55  | 546.83  |
| 512MB USB Drive               | 234.69  | 275.91  |
| 56Kbps V.90 Type II Modem     | 135.72  | 158.58  |
| 56Kbps V.92 Type II Fax/Modem | 95.01   | 111.08  |
| Envoy Ambassador              | 2686.01 | 2850.88 |
| Envoy Executive               | 2799.80 | 2943.96 |
| Envoy Standard                | 1933.82 | 1921.62 |
| External - DVD-RW - 8X        | 263.83  | 300.34  |
| External 48X CD-ROM           | 223.11  | 254.15  |
| Internal - DVD-RW - 6X        | 134.46  | 160.18  |
| Internal 48X CD-ROM           | 108.32  | 127.54  |
| Internal 48X CD-ROM USB       | 46.00   | 68.54   |
| Monitor- 17"Super VGA         | 228.53  | 269.70  |
| Monitor- 19"Super VGA         | 445.04  | 504.84  |
| Sentinel Financial            | 1685.72 | 1764.14 |
| Sentinel Multimedia           | 1849.17 | 1932.54 |
| Sentinel Standard             | 1572.98 | 1610.53 |

The next example creates a Sales Budget calculated measure by multiplying Sales from the previous year by 1.06 for a 6% increase. The detail levels of all dimensions are excluded from the calculation. The Budget is projected only using data from 2006 or later.

    CASE
       WHEN TIME.END_DATE >= TO_DATE('01-JAN-2006')
          AND TIME.LEVEL_NAME IN ('CALENDAR_YEAR', 'CALENDAR_QUARTER')
          AND PRODUCT.LEVEL_NAME != 'ITEM'
          AND CUSTOMER.LEVEL_NAME IN ('TOTAL', 'REGION', 'WAREHOUSE')
       THEN TRUNC(LAG(UNITS_CUBE.SALES, 1) OVER HIERARCHY
          (TIME.CALENDAR BY ANCESTOR AT LEVEL TIME.CALENDAR.CALENDAR_YEAR
          POSITION FROM BEGINNING) * 1.06)
       ELSE NULL
    END

| Product  | Time  | Sales    |
|:---------|:------|:---------|
| Hardware | Q1.05 | 28172590 |
| Hardware | Q2.05 | 34520379 |
| Hardware | Q3.05 | 29466573 |
| Hardware | Q4.05 | 32031795 |
| Hardware | Q1.06 | 32711891 |
| Hardware | Q2.06 | 33637473 |
| Hardware | Q3.06 | 29227635 |
| Hardware | Q4.06 | 31319881 |
| Hardware | Q1.07 | --       |
| Hardware | Q2.07 | --       |
| Hardware | Q3.07 | --       |
| Hardware | Q4.07 | --       |

### 1.7 Qualified Data References (QDRs)

Qualified data references (QDRs) limit a dimensional object to a single member in one or more dimensions for the duration of a query.

#### 1.7.1 Syntax

    expression [ qualifier [ , qualifier]... ]

qualifier::=

    dimension_id = member_expression

Note: The outside square brackets shown in bold are part of the syntax. In this case, they do not indicate an optional argument.

#### 1.7.2 Arguments

`expression` is a dimensional expression, typically the name of a measure.

`dimension_id` is a cube dimension of `expression`.

`member_expression` resolves to a single member of `dimension_id`.

#### 1.7.3 Examples

`global.sales[global.time = 'CY2007']` returns Sales values for the year 2007.

`sales[customer = 'US', time = 'CY2007']` returns Sales values only for the United States in calendar year 2007.
