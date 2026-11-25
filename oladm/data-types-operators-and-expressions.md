This chapter contains information about the following:

- OLAP DML Data Types

- OLAP DML Operators

- OLAP DML Expressions

### 2.1 OLAP DML Data Types

In the OLAP DML, as in other languages, a data type is a collection of values and the definition of one or more operations on those values.

The Oracle OLAP DML supports the data types outlined in the following table.

Table 2-1 Summary of OLAP DML Data Types

| Data Type                  | Abbreviation | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:---------------------------|:-------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BOOLEAN`                  | BOOL         | Represents the logical `TRUE` and `FALSE` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `DATE`                     | None         | Does not correspond to the SQL data type of the same name; but, instead, is an older data type that is unique to the OLAP DML.<br>Day, month, and year data (but not hour and minute data) between January 1, 1000 A.D. and December 31, 9999 A.D.                                                                                                                                                                                                                                                                                                                                 |
| `DATETIME`                 | None         | Corresponds to the SQL `DATE` data type.<br>Valid date range from January 1, 4712 BC to December 31, 9999 AD. The default format is determined explicitly by the `NLS_DATE_FORMAT` parameter or implicitly by the `NLS_TERRITORY` parameter. The size is fixed at 7 bytes. This data type contains the datetime fields `YEAR`, `MONTH`, `DAY`, `HOUR`, `MINUTE`, and `SECOND`. It does not have fractional seconds or a time zone.                                                                                                                                                 |
| `TIMESTAMP`                | None         | Corresponds to the SQL `TIMESTAMP` data type.<br>Year, month, and day values of date, and hour, minute, and second values of time up to a precision of 9 places for the fractional part of the `SECOND` datetime field. The default format is determined explicitly by the `NLS_DATE_FORMAT` parameter or implicitly by the `NLS_TERRITORY` parameter. The size is 11 bytes. This data type contains the datetime fields `YEAR`, `MONTH`, `DAY`, `HOUR`, `MINUTE`, and `SECOND`. It contains fractional seconds but does not have a time zone.                                     |
| `TIMESTAMP_TZ`             | None         | Corresponds to the SQL `TIMESTAMP WITH TIME ZONE` data type.<br>All values of `TIMESTAMP` as well as time zone displacement value, with a precision of 9 places for the fractional part of the `SECOND` datetime field. The default format is determined explicitly by the `NLS_DATE_FORMAT` parameter or implicitly by the `NLS_TERRITORY` parameter. The size is fixed at 13 bytes. This data type contains the datetime fields `YEAR`, `MONTH`, `DAY`, `HOUR`, `MINUTE`, `SECOND`, `TIMEZONE_HOUR`, and `TIMEZONE_MINUTE`. It has fractional seconds and an explicit time zone. |
| `TIMESTAMP_LTZ`            |              | Corresponds to the SQL `TIMESTAMP WITH LOCAL TIME ZONE` data type.<br>All values of `TIMESTAMP_TZ`, with the following exceptions:<br>• Data is normalized to the database time zone when it is stored in the database.<br>• When the data is retrieved, users see the data in the session time zone.<br>The default format is determined explicitly by the `NLS_DATE_FORMAT` parameter or implicitly by the `NLS_TERRITORY` parameter. The size is 11 bytes.                                                                                                                      |
| `DSINTERVAL`               | None         | Corresponds to the SQL `INTERVAL DAY TO SECOND` data type.<br>Stores a period of time in days, hours, minutes, and seconds.                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `YMINTERVAL`               | None         | Corresponds to the SQL `INTERVAL YEAR TO MONTH` data type.<br>Stores a period of time in years and months.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `INTEGER`                  | INT          | A whole number in the range of (-2\*\*31) to (2\*\*31)-1.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `SHORTINTEGER`             | SHORTINT     | A whole number in the range of (-2\*\*15) to (2\*\*15)-1.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `LONGINTEGER`              | LONGINT      | A whole number in the range of (-2\*\*63) to (2\*\*63)-1.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `DECIMAL`                  | DEC          | A decimal number with up to 15 significant digits in the range of -(10\*\*308) to +(10\*\*308).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `SHORTDECIMAL`             | SHORT        | A decimal number with up to 7 significant digits in the range of -(10\*\*38) to +(10\*\*38).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `NUMBER [(``p``,[``s``])]` | None         | A decimal number with up to 38 significant digits in the range of -(10\*\*125) to +(10\*\*125).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `TEXT`                     | None         | Up to 32,767 bytes for each line in the database character set. This data type is equivalent to the `CHAR` and `VARCHAR2` data types in the database. (Note that when defining a variable of this data type you specify the RANSPACE64 keyword in the DEFINE VARIABLE statement to increase the maximum number of characters for the values of the variable from nearly `2**32` to nearly `2**64`.)                                                                                                                                                                                |
| `NTEXT`                    | None         | Up to 32,767 bytes for each line in UTF-8 character encoding. This data type is equivalent to the `NCHAR` and `NVARCHAR2` data types in the database. (Note that when defining a variable of this data type you specify the RANSPACE64 keyword in the DEFINE VARIABLE statement to increase the maximum number of characters for the values of the variable from nearly `2**32` to nearly `2**64`.)                                                                                                                                                                                |
| `ID`                       | None         | Up to 8 single-byte characters for each line in the database character set. (`ID` is valid only for values of simple dimensions, see [DEFINE DIMENSION (simple)](olap-dml-commands-a-g.md).)                                                                                                                                                                                                                                                                                                                                                                                       |
| `RAW (``size``)`           | None         | Raw binary data of length size bytes. Maximum size is 2000 bytes. You must specify size for a RAW value. (Note that when defining a variable of this data type you specify the RANSPACE64 keyword in the DEFINE VARIABLE statement to increase the maximum number of characters for the values of the variable from nearly `2**32` to nearly `2**64`.)                                                                                                                                                                                                                             |
| `ROWID`                    | None.        | Base 64 string representing the unique address of a row in its table. This data type is primarily for values returned by the ROWID pseudocolumn.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `UROWID`                   | None         | Base 64 string representing the logical address of a row of an index-organized table. The optional size is the size of a column of type UROWID. The maximum size and default is 4,000 bytes.                                                                                                                                                                                                                                                                                                                                                                                       |
| `WORKSHEET`                |              | Specified for arguments and temporary variables in an OLAP DML program when you want to handle arguments without converting values to a specific data type. Use the WKSDATA function to retrieve the data type of an argument with a `WORKSHEET` data type.                                                                                                                                                                                                                                                                                                                        |

#### Categories of Data Types

Frequently, these data types are thought of as belonging to the following categories:

- Numeric Data Types which are` INTEGER`, `SHORTINTEGER`, `LONGINTEGER`, `DECIMAL`, `SHORTDECIMAL`, and `NUMBER`

- Text Data Types which are `TEXT`, `NTEXT` and `ID`.

- Datetime and Interval Data Types which include the datetime data types of `DATETIME`, `TIMESTAMP`, `TIMESTAMP_TZ`, and `TIMESTAMP-LTZ` and the interval data types of `DSINTERVAL` and `YMINTERVAL`.

- Date-only Data Type which is the `DATE` data type that is unique to the OLAP DML.

- Boolean Data Type which is BOOLEAN.

- Row Identifier Data Types which are ROWID and UROWID.

#### Which OLAP DML Data Objects Can Have Which Data Type?

Different objects support the use of different data types for their values:

- For variables, all of the data types are supported.

- For dimensions and surrogates, the `INTEGER`, `NUMBER`, `TEXT`, `ID` (simple dimensions only), `NTEXT`, `DATETIME`, `TIMESTAMP`, `TIMESTAMP_TZ`, `TIMESTAMP-LTZ`, `DSINTERVAL`, and `YMINTERVAL` data types are supported. Additionally, when you define a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR using a [DEFINE DIMENSION (DWMQY)](olap-dml-commands-a-g.md) statement, the data type of the values of that dimension are `DATE`-only.

#### 2.1.1 Numeric Data Types

The numeric data types described in the following table are supported.

Table 2-2 OLAP DML Numeric Data Types

| Data Type      | Data Value                                                                                      |
|:---------------|:------------------------------------------------------------------------------------------------|
| `INTEGER`      | A whole number in the range of (-2\*\*31) to (2\*\*31)-1.                                       |
| `SHORTINTEGER` | A whole number in the range of (-2\*\*15) to (2\*\*15)-1.                                       |
| `LONGINTEGER`  | A whole number in the range of (-2\*\*63) to (2\*\*63)-1.                                       |
| `DECIMAL`      | A decimal number with up to 15 significant digits in the range of -(10\*\*308) to +(10\*\*308). |
| `SHORTDECIMAL` | A decimal number with up to 7 significant digits in the range of -(10\*\*38) to +(10\*\*38).    |
| `NUMBER`       | A decimal number with up to 38 significant digits in the range of -(10\*\*125) to +(10\*\*125). |

For data entry, a value for any of these data types can begin with a plus (+) or minus (-) sign; it cannot contain commas. Note, however, that a comma is required before a negative number that follows another numeric expression, or the minus sign is interpreted as a subtraction operator. Additionally, a decimal value can contain a decimal point. For data display, thousands and decimal markers are controlled by the NLS_NUMERIC_CHARACTERS option.

##### 2.1.1.1 Using LONGINTEGER Values

Most of the numeric data types return `NA` when a value is outside its range. However, the `LONGINTEGER` data type does not have overflow protection and returns an incorrect value when, for example, a calculation produces a number that exceeds its range. Use the `NUMBER` data type instead of `LONGINTEGER` when this is likely to be a problem.

##### 2.1.1.2 Using NUMBER Values

When you define a `NUMBER` variable, you can specify its precision (p) and scale (s) so that it is sufficiently, but not unnecessarily, large. Precision is the number of significant digits. Scale can be positive or negative. Positive scale identifies the number of digits to the right of the decimal point; negative scale identifies the number of digits to the left of the decimal point that can be rounded up or down.

The `NUMBER` data type is supported by Oracle Database standard libraries and operates the same way as it does in SQL. It is used for dimensions and surrogates when a text or `INTEGER` data type is not appropriate. It is typically assigned to variables that are not used for calculations (like forecasts and aggregations), and it is used for variables that must match the rounding behavior of the database or require a high degree of precision. When deciding whether to assign the `NUMBER` data type to a variable, keep the following facts in mind to maximize performance:

- Analytic workspace calculations on `NUMBER` variables is slower than other numeric data types because `NUMBER` values are calculated in software (for accuracy) rather than in hardware (for speed).

- When data is fetched from an analytic workspace to a relational column that has the `NUMBER` data type, performance is best when the data has the `NUMBER` data type in the analytic workspace because a conversion step is not required.

#### 2.1.2 Text Data Types

The text data types described in the following table are supported by Oracle OLAP.

Table 2-3 OLAP DML Text Data Types

| Data Type | Data Value                                                                                                                                                                                   |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TEXT`    | Up to 32,767 bytes for each line in the database character set. This data type is equivalent to the `CHAR` and `VARCHAR2` data types in the database.                                        |
| `NTEXT`   | Up to 32,767 bytes for each line in UTF-8 character encoding. This data type is equivalent to the `NCHAR` and `NVARCHAR2` data types in the database.                                        |
| `ID`      | Up to 8 single-byte characters for each line in the database character set. (`ID` is valid only for values of simple dimensions, see [DEFINE DIMENSION (simple)](olap-dml-commands-a-g.md).) |

##### 2.1.2.1 Text Literals

Enclose text literals in single quotes. Oracle OLAP recognizes unquoted alpha-numeric values as object names and double quotes as the beginning of a comment.

You can embed quoted strings within a quoted string, which is necessary when you want to specify the base dimension value of a composite or conjoint dimension or when a value includes an apostrophe. Because a single quotation mark is used in Oracle OLAP to indicate a text string, it is considered a special character when used within such a string. Consequently, to specify the literal value of a single quotation mark within a text string, precede the quotation mark with a backslash.

For example, suppose you want to find out if `New` `York` and `Apple` `Sauce` are a valid combination of base dimension values in the `markprod` conjoint dimension. The following statement produces the answer YES or `NO`.

    SHOW ISVALUE(markprod, '<\'New York\' \'Apple Sauce\'>')

When embedded quoted strings have a further level of embedding, you must use backslashes before each special character, such as the apostrophe and the backslash that must precede it in "Joe's Deli," as shown in the following statement.

    SHOW ISVALUE(markprod, '<\'Joe\\\'s Deli\' \'Apple Sauce\'>')

##### 2.1.2.2 Escape Sequences

The following table shows escape sequences that are recognized by Oracle OLAP.

Table 2-4 Recognized Escape Sequences

| Sequence | Meaning                                                                                                                                                                                                            |
|:---------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `\b`     | Backspace                                                                                                                                                                                                          |
| `\f`     | Form feed                                                                                                                                                                                                          |
| `\n`     | Line feed                                                                                                                                                                                                          |
| `\r`     | Carriage return                                                                                                                                                                                                    |
| `\t`     | Horizontal tab                                                                                                                                                                                                     |
| `\"`     | Double quote                                                                                                                                                                                                       |
| `\'`     | Single quote                                                                                                                                                                                                       |
| `\\`     | Backslash                                                                                                                                                                                                          |
| `\d`nnn  | Character with ASCII code nnn decimal, where \\`d` indicates a decimal escape and nnn is the decimal value for the character                                                                                       |
| `\x`nn   | Character with ASCII code nn hexadecimal, where `\x` indicates a hexadecimal escape and nn is the hexadecimal value for the character                                                                              |
| `\U`nnnn | Character with Unicode nnnn, where `\U` indicates a Unicode escape and nnnn is a four-digit hexadecimal `INTEGER` that represents the Unicode codepoint with the value `U`+nnnn. The `U` must be a capital letter. |

#### 2.1.3 Date-only Data Type

The Oracle OLAP DML DATE data type does not correspond to the SQL data type of the same name. It is, instead, is an older data type that is unique to the OLAP DML. The OLAP DML `DATE `data type is a valid data type for variables and for dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR as discussed in the [DEFINE DIMENSION (DWMQY)](olap-dml-commands-a-g.md) command topic. It is used to store day, month, and year data (but not hour and minute data) between January 1, 1000 A.D. and December 31, 9999 A.D. Because the OLAP DML `DATE `data type does not include hour and minute data, it is often referred to as the DATE-only data type.

**Tip:**

The Oracle OLAP DML data type that corresponds to the SQL DATE data type is named `DATETIME`. See DATETIME Data Type for more information.

**See Also:**

"[Date-only Data Type Options](olap-dml-options.md)".

##### 2.1.3.1 Date-only Input Values

A valid input literal value of type DATE must conform to one of three styles: numeric, packed numeric, or month name. You can mix these styles throughout a session.

**Tip:**

To determine whether a text expression (such as an expression with a data type of TEXT or ID) represents a valid DATE-only value, use the [ISDATE](olap-dml-functions-a-k.md) program

##### Numeric style

Specify the day, month, and year as three `INTEGER` values with one or more separators between them, using these rules:

- The day and month components can have one digit or two digits.

- For any year, the year component can have four digits (for example, 1997). For years in the range 1950 to 2049, the year component can, alternatively, have two digits (50 represents 1950, and so on).

- To separate the components, you can use a space, dash (`-`), slash (`/`), colon (`:`), or comma (`,`).

Examples: `'24/4/97'` or `'24-04-1997'`

##### Packed numeric style

Specify the day, month, and year as three `INTEGER` values with no separators between them, using these rules:

- The day and month components must have two digits. When the day or month is less than 10, it must be preceded by a zero.

- For any year, the year component can have four digits (for example, 1997). For years in the range 1950 to 2049, the year component can, alternatively, have two digits (50 represents 1950, and so on).

- You cannot use any separators between the date components.

Examples:` '240497'` or` '04241997'`

##### Month name style

Specify the day and year as `INTEGER` values and the month as text, using these rules:

- The month component must match one name listed in the MONTHNAMES option. You can abbreviate the month name to one letter or more, when you supply enough letters to uniquely match the beginning of a name in MONTHNAMES. The case of the letters in the month component (uppercase or lowercase) does not need to match the case in MONTHNAMES.

- The day component can have one digit or two digits.

- For any year, the year component can have four digits (for example, 1997). For years in the range 1950 to 2049, the year component can, alternatively, have two digits (50 represents 1950, and so on).

- When the day and year components are adjacent, they must have at least one separator between them. As separators, you can use a space, dash (`-`), slash (`/`), colon (`:`), or comma (`,`). When you want, you can place one or more separators between the day and month or between the year and month.

Examples:` '24APR97'` or `'24 ap 97'` or `'April 24, 1997'`

##### 2.1.3.2 Date-only Dimension Values

The format of a `DATE` -only value of a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR is determined by the value name format (VNF) associated with the object. A VNF is a template that controls the input and display format for `DATE` -only values. The template can include format specifications for any of the components that identify a time period (day, month, calendar year, fiscal year, and period within a fiscal year). You associate a VNF with an object by adding a VNF statement to its definition. When you do not add a VNF to the definition of an object, the object uses the default VNF shown in the following table.

Table 2-5 Default VNFs for DWMQY Dimensions

| Type of Dimension | Default VNF          | Example     |
|:------------------|:---------------------|:------------|
| DAY               | \<DD\>\<MTXT\>\<YY\> | 01JAN95     |
| WEEK              | W\<P\>.\<FF\>        | W1.95       |
| Multiple WEEK     | \<NAME\>\<P\>.\<FF\> | MYWEEK1.95  |
| MONTH             | \<MTXT\>\<YY\>       | JAN95       |
| Multiple MONTH    | \<NAME\>\<P\>.\<FF\> | MYMONTH1.95 |
| QUARTER           | Q\<P\>.\<FF\>        | Q1.95       |
| YEAR              | YR\<YY\>             | YR95        |

`DATE`-only values have independent input and output formats. You can enter `DATE`-only values in one style and report them in a different style.

##### 2.1.3.3 DATE-only Variable Display Styles

When you show a `DATE`-only variable value in output, the format depends on the DATEFORMAT option. The default format is a 2-digit day, a 3-letter month, and a 2-digit year; for example, `03MAR97`. The text for the month names depends on the MONTHNAMES option. To change the order of the month, day, and year components, see the [DATEORDER](olap-dml-options.md) option.

#### 2.1.4 Datetime and Interval Data Types

The OLAP DML has data types that correspond to SQL datetime and interval data types. As outlined in the following table, the names of the data types are different in OLAP DML than they are in SQL.

Table 2-6 OLAP DML Datetime and Interval Data Types and the Corresponding SQL Data Types

| OLAP DML Data Type | Corresponding SQL Data Type      |
|:-------------------|:---------------------------------|
| `DATETIME`         | `DATE`                           |
| `TIMESTAMP`        | `TIMESTAMP`                      |
| `TIMESTAMP_TZ`     | `TIMESTAMP WITH TIMEZONE`        |
| `TIMESTAMP_LTZ`    | `TIMESTAMP WITH LOCAL TIME ZONE` |
| `DSINTERVAL`       | `INTERVAL DAY TO SECOND`         |
| `YMINTERVAL`       | `INTERVAL YEAR TO MONTH`         |

In the OLAP DML, the datetime data types are `DATETIME`, `TIMESTAMP`, `TIMESTAMP`\_TZ, and `TIMESTAMP`\_LTZ. The interval data types are `YMINTERVAL` and `DSINTERVAL`. Both datetimes and intervals are made up of fields as discussed in "Datetime and Interval Fields".

**Note:**

The Oracle OLAP DML has a date data type named `DATE `that does not correspond to the SQL data type of that name. (The OLAP DML DATE data type was implement before the SQL datetime and interval data types were implemented in the OLAP DML.) The OLAP DML DATE data type stores only date values (no time values) and is therefore sometimes referred to as the DATE-only data type.

##### 2.1.4.1 Datetime and Interval Fields

Both datetimes and intervals are made up of fields. The values of these fields determine the value of the data type. The following table lists the datetime fields and their possible values for datetimes and intervals.

**Tip:**

To avoid unexpected results in your operations on datetime data, you can verify the database and session time zones using DBTIMEZONE and SESSIONTIMEZONE If the time zones have not been set manually, Oracle Database uses the operating system time zone by default. If the operating system time zone is not a valid Oracle time zone, then Oracle uses UTC as the default value.

Table 2-7 Datetime Fields and Values

| Datetime Field                                  | Valid Values for Datetime Data Types                                                                                                                                                                                              | Valid Values for Interval Data Types                                     |
|:------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------|
| `YEAR`                                          | -4712 to 9999 (excluding year 0)                                                                                                                                                                                                  | Any positive or negative integer                                         |
| `MONTH`                                         | 01 to 12                                                                                                                                                                                                                          | 0 to 11                                                                  |
| `DAY`                                           | 01 to 31 (limited by the values of `MONTH` and `YEAR`, according to the rules of the current NLS calendar parameter)                                                                                                              | Any positive or negative integer                                         |
| `HOUR`                                          | 00 to 23                                                                                                                                                                                                                          | 0 to 23                                                                  |
| `MINUTE`                                        | 00 to 59                                                                                                                                                                                                                          | 0 to 59                                                                  |
| `SECOND`                                        | 00 to 59.9(n), where 9(n) is the precision of time fractional seconds. The 9(n) portion is not applicable for `DATETIME`.                                                                                                         | 0 to 59.9(n), where 9(n) is the precision of interval fractional seconds |
| `TIMEZONE_HOUR`                                 | -12 to 14 (This range accommodates daylight saving time changes.) Not applicable for `DATETIME` or `TIMESTAMP`.                                                                                                                   | Not applicable                                                           |
| `TIMEZONE_MINUTE`<br>(See note at end of table) | 00 to 59. Not applicable for `DATETIME` or `TIMESTAMP`.                                                                                                                                                                           | Not applicable                                                           |
| `TIMEZONE_REGION`                               | Query the `TZNAME` column of the `V$TIMEZONE_NAMES` data dictionary view. Not applicable for `DATETIME` or `TIMESTAMP`.<br>For a complete listing of all time zone regions, refer to Oracle Database Globalization Support Guide. | Not applicable                                                           |
| `TIMEZONE_ABBR`                                 | Query the `TZABBREV` column of the `V$TIMEZONE_NAMES` data dictionary view. Not applicable for `DATETIME` or `TIMESTAMP`.                                                                                                         | Not applicable                                                           |

Note: `TIMEZONE_HOUR` and `TIMEZONE_MINUTE` are specified together and interpreted as an entity in the format +\|- hh:mm, with values ranging from -12:59 to +14:00.

**See Also:**

"Datetime and Interval Expressions"

##### 2.1.4.2 Datetime Format Templates

A datetime format template is a template that describes the format of datetime data stored in a character string. A format model does not change the internal representation of the value in the database. When you convert a character string into a date, a format model determines how Oracle Database interprets the string. In OLAP DML statements, you can use a format model as an argument of the `TO_CHAR` and `TO_DATE` functions to specify:

- The format for Oracle to use to return a value from the database

- The format for a value you have specified for Oracle to store in the database

You can use datetime format templates in the following functions:

- In the `TO_*` datetime functions to translate a character value that is in a format other than the default format into a datetime value. (The `TO_`\* datetime functions are `TO_CHAR`, `TO_DATE`, `TO_TIMESTAMP`, `TO_TIMESTAMP_TZ`, `TO_YMINTERVAL`, and `TO_DSINTERVAL`.)

- In the `TO_CHAR` function to translate a datetime value that is in a format other than the default format into a string (for example, to print the date from an application)

The default datetime formats are specified either explicitly with the initialization parameter `NLS_DATE_FORMAT` or implicitly with the initialization parameter `NLS_TERRITORY`. You can change the default datetime formats for your session with the `ALTER` `SESSION` statement. You can override this default and specify a datetime format for use with a particular OLAP DML object by using the [DATE_FORMAT](olap-dml-commands-a-g.md) command to add a datetime format to the definition of the object.

##### 2.1.4.3 String-to-Date Conversion Rules

The following additional formatting rules apply when converting string values to datetime values (unless you have used the `FX` or `FXFM` modifiers in the format model to control exact format checking):

- You can omit punctuation included in the format string from the date string if all the digits of the numeric format elements, including leading zeros, are specified. In other words, specify 02 and not 2 for two-digit format elements such as MM, DD, and YY.

- You can omit time fields found at the end of a format string from the date string.

- If a match fails between a datetime format element and the corresponding characters in the date string, then Oracle attempts alternative format elements, as shown in the following table.

Table 2-8 Oracle Format Matching

| Original Format Element | Additional Format Elements to Try instead Of the Original |
|:------------------------|:----------------------------------------------------------|
| `'MM'`                  | `'MON'` and `'MONTH'`                                     |
| `'MON`                  | `'MONTH'`                                                 |
| `'MONTH'`               | `'MON'`                                                   |
| `'YY'`                  | `'YYYY'`                                                  |
| `'RR'`                  | `'RRRR'`                                                  |

##### 2.1.4.4 DATETIME Data Type

The OLAP DML DATETIME data type corresponds to the SQL `DATE` data type. As such, the format and language of `DATETIME` values are controlled by the settings of the NLS_DATE_FORMAT and NLS_DATE_LANGUAGE options. The `DATETIME` data type is supported by Oracle Database standard libraries and operates the same way in the OLAP DML as it does the `DATE` data type in SQL.

**Note:**

The Oracle OLAP DML has a date data type named `DATE `that does not correspond to the SQL data type of that name. The OLAP DML DATE data type stores only date values (no time values) and is therefore sometimes referred to as the DATE-only data type. The DATEORDER, DATEFORMAT, and MONTHNAMES options, which control the formatting of `DATE` values, have no effect on `DATETIME` values. However, `DATETIME` and `DATE` values can be used interchangeably in most DML statements.

You can specify a `DATETIME` value as a string literal, or you can convert a character or numeric value to a date value with the `TO_DATE` function.

To specify a `DATETIME` value as a literal, you must use the Gregorian calendar. You can specify an ANSI literal, as shown in this example:

    DATETIME '1998-12-25'

The ANSI date literal contains no time portion, and must be specified in exactly this format ('`YYYY-MM-DD`').

Alternatively you can specify a DATETIME value us the TO_DATE function and include, as in the following example:

    TO_DATE('98-DEC-25 17:30','YY-MON-DD HH24:MI')

The default date format template for an Oracle `DATETIME` value is specified by the initialization parameter `NLS_DATE_FORMAT`. This example date format includes a two-digit number for the day of the month, an abbreviation of the month name, the last two digits of the year, and a 24-hour time designation.

Oracle automatically converts character values that are in the default datetime format into datetime values when they are used in datetime expressions.

If you specify a datetime value without a time component, then the default time is midnight (00:00:00 or 12:00:00 for 24-hour and 12-hour clock time, respectively). If you specify a datetime value without a date, then the default date is the first day of the current month.

Values of `DATETIME` always contain both the date and time fields. Therefore, if you use `DATETIME` values in an expression, you must either specify the time field in your query or ensure that the time fields in the `DATETIME` values are set to midnight. Otherwise, Oracle may not return the results you expect. You can use the `TRUNC` (date) function to set the time field to midnight, or you can include a greater-than or less-than condition in the query instead of an equality or inequality condition. However, if the expression contains DATETIME values other than midnight, then you must filter out the time fields in the query to get the correct result.

The date function `SYSDATE` returns the current system date and time. The function `CURRENT_DATE` returns the current session date. For information on `SYSDATE`, the `TO_*` datetime functions, and the default date format, see "[Datetime functions](olap-dml-functions-a-k.md)" and the [DATE_FORMAT](olap-dml-commands-a-g.md) command.

##### 2.1.4.5 TIMESTAMP Data Type

The `TIMESTAMP` data type is an extension of the `DATETIME` data type. It stores the year, month, and day of the `DATETIME` data type, plus hour, minute, and second values. This data type is useful for storing precise time values.

    SHOW SYSDATE
    26-JUL-06

    DEFINE mytimestamp VARIABLE TIMESTAMP
    mytimestamp = SYSDATE
    COLWIDTH = 30
    REPORT mytimestamp
    MYTIMESTAMP
    ------------------------------
             26-JUL-06 10.44.42 AM

The `TIMESTAMP` data type stores year, month, day, hour, minute, and second, and fractional second values. When you specify `TIMESTAMP` as a literal, the fractional seconds precision value can be any number of digits up to 9, as follows:

    TIMESTAMP '1997-01-31 09:26:50.124'

##### 2.1.4.6 TIMESTAMP_TZ Data Type

`TIMESTAMP_TZ` corresponds to the SQL `TIMESTAMP WITH TIMEZONE` data type. It is a variant of `TIMESTAMP` that includes a time zone offset in its value. The time zone offset is the difference (in hours and minutes) between local time and UTC (Coordinated Universal Time—formerly Greenwich Mean Time). This data type is useful for collecting and evaluating date information across geographic regions.

Oracle from the public domain information available at [`http://www.iana.org/time-zones`](http://www.iana.org/time-zones). Oracle time zone data may not reflect the most recent data available at this site.

The `TIMESTAMP_TZ` data type is a variant of `TIMESTAMP` that includes a time zone offset. When you specify `TIMESTAMP_TZ` as a literal, the fractional seconds precision value can be any number of digits up to 9. For example:

    TIMESTAMP '1997-01-31 09:26:56.66 +02:00'

Two TIMESTAMP_TZ values are considered identical if they represent the same instant in UTC, regardless of the `TIME` `ZONE` offsets stored in the data. For example,

    TIMESTAMP '1999-04-15 8:00:00 -8:00'

equals

    TIMESTAMP '1999-04-15 11:00:00 -5:00'

That is, 8:00 a.m. Pacific Standard Time equals 11:00 a.m. Eastern Standard Time.

You can replace the UTC offset with the `TZR` (time zone region) format element. For example, the following example has the same value as the preceding example:

    TIMESTAMP '1999-04-15 8:00:00 US/Pacific'

To eliminate the ambiguity of boundary cases when the daylight saving time switches, use both the `TZR` and a corresponding `TZD` format element. The following example ensures that the preceding example returns a daylight saving time value:

    TIMESTAMP '1999-10-29 01:30:00 US/Pacific PDT'

You can also express the time zone offset using a datetime expression.

**See Also:**

"Datetime and Interval Expressions"

If you do not add the `TZD` format element, and the datetime value is ambiguous, then Oracle returns an error if you have the `ERROR_ON_OVERLAP_TIME` session parameter set to `TRUE`. If that parameter is set to `FALSE`, then Oracle interprets the ambiguous datetime as standard time in the specified region.

##### 2.1.4.7 TIMESTAMP_LTZ Data Type

`TIMESTAMP_LTZ` corresponds to the SQL `TIMESTAMP WITH LOCAL TIMEZONE` data type. It is another variant of `TIMESTAMP` that includes a time zone offset in its value. It differs from `TIMESTAMP_LTZ` in that data stored in the database is normalized to the database time zone, and the time zone offset is not stored as part of the column data. When a user retrieves the data, Oracle returns it in the user's local session time zone. The time zone offset is the difference (in hours and minutes) between local time and UTC (Coordinated Universal Time—formerly Greenwich Mean Time). This data type is useful for displaying date information in the time zone of the client system in a two-tier application.

Oracle time zone data is derived from the public domain information available at [`http://www.iana.org/time-zones`](http://www.iana.org/time-zones). Oracle time zone data may not reflect the most recent data available at this site.

The `TIMESTAMP_LTZ` data type differs from `TIMESTAMP_TZ` in that data stored in the database is normalized to the database time zone. The time zone offset is not stored as part of the column data. There is no literal for `TIMESTAMP_LTZ`. Rather, you represent values of this data type using any of the other valid datetime literals. The table that follows shows some formats you can use to add a `TIMESTAMP_LTZ` value into object, along with the corresponding value returned by an OLAP DML statement such as a [SHOW](olap-dml-commands-h-z.md) command.

| Value Specified When Adding Value              | Value Returned               |
|:-----------------------------------------------|:-----------------------------|
| `'19-FEB-2004'`                                | 19-FEB-2004.00.00.000000 AM  |
| `SYSTIMESTAMP`                                 | 19-FEB-04 02.54.36.497659 PM |
| `TO_TIMESTAMP('19-FEB-2004', 'DD-MON-YYYY'));` | 19-FEB-04 12.00.00.000000 AM |
| `SYSDATE`                                      | 19-FEB-04 02.55.29.000000 PM |
| `TO_DATE('19-FEB-2004', 'DD-MON-YYYY'));`      | 19-FEB-04 12.00.00.000000 AM |
| `TIMESTAMP'2004-02-19 8:00:00 US/Pacific'); `  | 19-FEB-04 08.00.00.000000 AM |

Notice that if the value specified does not include a time component (either explicitly or implicitly), then the value returned defaults to midnight.

##### 2.1.4.8 YMINTERVAL Data Type

`YMINTERVAL` corresponds to the SQL `INTERVAL YEAR TO MONTH` data type. It stores a period of time using the `YEAR` and `MONTH` datetime fields. This data type is useful for representing the difference between two datetime values when only the year and month values are significant.

Specify `YMINTERVAL` interval literals using the following syntax.

INTERVAL 'integer \[- integer \]'  YEAR\|MONTH \[(precision) \] \[TO  YEAR \| MONTH \]

where

- `'integer [-integer]'` specifies integer values for the leading and optional trailing field of the literal. If the leading field is `YEAR` and the trailing field is `MONTH`, then the range of integer values for the month field is 0 to 11.

- `precision` is the maximum number of digits in the leading field. The valid range of the leading field precision is 0 to 9 and its default value is 2.

If you specify a trailing field, it must be less significant than the leading field. For example, `INTERVAL` '`0-1`' `MONTH` `TO` `YEAR` is not valid.

The following `YMINTERVAL` literal indicates an interval of 123 years, 2 months:

    INTERVAL '123-2' YEAR(3) TO MONTH

Examples of the other forms of the literal follow, including some abbreviated versions:

| Form of Interval Literal            | Interpretation                                                                                                                  |
|:------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| `INTERVAL '123-2' YEAR(3) TO MONTH` | An interval of 123 years, 2 months. You must specify the leading field precision if it is greater than the default of 2 digits. |
| `INTERVAL '123' YEAR(3)`            | An interval of 123 years 0 months.                                                                                              |
| `INTERVAL '300' MONTH(3)`           | An interval of 300 months.                                                                                                      |
| `INTERVAL '4' YEAR`                 | Maps to `INTERVAL '4-0' YEAR TO MONTH` and indicates 4 years.                                                                   |
| `INTERVAL '50' MONTH`               | Maps to `INTERVAL '4-2' YEAR TO MONTH` and indicates 50 months or 4 years 2 months.                                             |
| `INTERVAL '123' YEAR`               | Returns an error, because the default precision is 2, and '123' has 3 digits.                                                   |

You can add or subtract one `INTERVAL` `YEAR` `TO` `MONTH` literal to or from another to yield another `INTERVAL` `YEAR` `TO` `MONTH` literal. For example:

    INTERVAL '5-3' YEAR TO MONTH + INTERVAL'20' MONTH =
    INTERVAL '6-11' YEAR TO MONTH

##### 2.1.4.9 DSINTERVAL Data Type

DSINTERVAL corresponds to the SQL `INTERVAL DAY TO SECOND` data type. It stores a period of time in terms of days, hours, minutes, and seconds. This data type is useful for representing the precise difference between two datetime values.

Specify `DSINTERVAL` interval literals using the following syntax.

INTERVAL   'integer\|integer time_expr\|time_expr

DAY\|HOUR\|MINUTE \[(leading_precision)\] \| SECOND \[leading_precision\[, fractional_seconds_precision \])\]

\[ TO  DAY\|HOUR\|MINUTE\|SECOND \[(fractional_seconds_precision) \]\]

where

- `integer` specifies the number of days. If this value contains more digits than the number specified by the leading precision, then Oracle returns an error.

- `time_expr` specifies a time in the format `HH[:MI[:SS[.n]]]` or `MI[:SS[.n]]` or `SS[.n]`, where `n` specifies the fractional part of a second. If `n` contains more digits than the number specified by `fractional_seconds_precision`, then `n` is rounded to the number of digits specified by the `fractional_seconds_precision` value. You can specify `time_expr` following an integer and a space only if the leading field is `DAY`.

- `leading_precision` is the number of digits in the leading field. Accepted values are 0 to 9. The default is 2.

- `fractional_seconds_precision` is the number of digits in the fractional part of the `SECOND` datetime field. Accepted values are 1 to 9. The default is 6.

If you specify a trailing field, it must be less significant than the leading field. For example, `INTERVAL` `MINUTE` `TO` `DAY` is not valid. Because of this restriction, if `SECOND` is the leading field, the interval literal cannot have any trailing field.

The valid range of values for the trailing field are as follows:

- `HOUR`: 0 to 23

- `MINUTE`: 0 to 59

- `SECOND`: 0 to 59.999999999

Examples of the various forms of `DSINTERVAL` literals follow, including some abbreviated versions:

| Form of Interval Literal                        | Interpretation                                                                                  |
|:------------------------------------------------|:------------------------------------------------------------------------------------------------|
| `INTERVAL '4 5:12:10.222' DAY TO SECOND(3)`     | 4 days, 5 hours, 12 minutes, 10 seconds, and 222 thousandths of a second.                       |
| `INTERVAL '4 5:12' DAY TO MINUTE`               | 4 days, 5 hours and 12 minutes.                                                                 |
| `INTERVAL '400 5' DAY(3) TO HOUR`               | 400 days 5 hours.                                                                               |
| `INTERVAL '400' DAY(3) `                        | 400 days.                                                                                       |
| `INTERVAL '11:12:10.2222222' HOUR TO SECOND(7)` | 11 hours, 12 minutes, and 10.2222222 seconds.                                                   |
| `INTERVAL '11:20' HOUR TO MINUTE`               | 11 hours and 20 minutes.                                                                        |
| `INTERVAL '10' HOUR`                            | 10 hours.                                                                                       |
| `INTERVAL '10:22' MINUTE TO SECOND`             | 10 minutes 22 seconds.                                                                          |
| `INTERVAL '10' MINUTE`                          | 10 minutes.                                                                                     |
| `INTERVAL '4' DAY`                              | 4 days.                                                                                         |
| `INTERVAL '25' HOUR `                           | 25 hours.                                                                                       |
| `INTERVAL '40' MINUTE`                          | 40 minutes.                                                                                     |
| `INTERVAL '120' HOUR(3)`                        | 120 hours.                                                                                      |
| `INTERVAL '30.12345' SECOND(2,4) `              | 30.1235 seconds. The fractional second '12345' is rounded to '1235' because the precision is 4. |

You can add or subtract one `DAY` `TO` `SECOND` interval literal from another `DAY` `TO` `SECOND` literal. For example.

    INTERVAL'20' DAY - INTERVAL'240' HOUR = INTERVAL'10-0' DAY TO SECOND

#### 2.1.5 Boolean Data Type

A `BOOLEAN` data type enables you to represent logical values. In code, `BOOLEAN` values are represented by values for "no" and "yes" (in any combination of uppercase and lowercase characters). The actual values that are recognized in your version of Oracle OLAP are determined by the language identified by the NLS_LANGUAGE option. You can use the read-only NOSPELL and YESSPELL options to obtain the values represent `BOOLEAN` values. In English language code, you can represent `BOOLEAN` values, using:

- `YES`, `TRUE`, `ON`

- `NO`, `FALSE`, `OFF`

Working with `BOOLEAN` expressions is discussed in "Boolean Expressions".

#### 2.1.6 RAW Data Type

The `RAW` data type stores data that is not to be interpreted (that is, not explicitly converted when moving data between different systems) by Oracle Database. The `RAW` data type is intended for binary data or byte strings.

The syntax for specifying `RAW` data is as follows:

RAW (size)

where you must specify a size up to the maximum of 2000 bytes

`RAW` is a variable-length data type, however Oracle Net (which connects user sessions to the instance) and Oracle Database utilities do not perform character conversion when transmitting `RAW` data.

When Oracle automatically converts `RAW` data to and from text data, the binary data is represented in hexadecimal form, with one hexadecimal character representing every four bits of RAW data. For example, one byte of RAW data with bits `11001011` is displayed and entered as `CB`.

**See Also:**

[HEXTORAW](olap-dml-functions-a-k.md) and [RAWTOHEX](olap-dml-functions-l-z.md) functions

#### 2.1.7 Row Identifier Data Types

The row identifier data types are used to store an address of a row in a relational table. The OLAP DML supports two different data types that you can use to copy this data from a relational table into objects in an analytic workspace:

- ROWID Data Type

- UROWID Data Type

##### 2.1.7.1 ROWID Data Type

You can examine a row address of a relational table by querying the pseudocolumn ROWID. Values of this pseudocolumn are strings representing the address of each row. These strings have the data type ROWID.

**Note:**

Although you can create relational tables and clusters that contain actual columns having the ROWID data type. Oracle Database does not guarantee that the values of such columns are valid rowids

The extended ROWID data type stored in a user column includes the data in the restricted rowid plus a data object number. The data object number is an identification number assigned to every database segment. You can retrieve the data object number from the data dictionary views USER_OBJECTS, DBA_OBJECTS, and ALL_OBJECTS. Objects that share the same segment (clustered tables in the same cluster, for example) have the same object number.

Extended rowids are stored as base 64 values that can contain the characters A-Z, a-z, 0-9, and the plus sign (+) and forward slash (/). Extended rowids are not available directly. You can use a supplied package, DBMS_ROWID, to interpret extended rowid contents. The package functions extract and provide information that would be available directly from a restricted rowid as well as information specific to extended rowids.

**See Also:**

["ROWID Pseudocolumn](../sqlrf/ROWID-Pseudocolumn.md)" in Oracle Database SQL Language Reference.

##### 2.1.7.2 UROWID Data Type

The rows of some relational tables have addresses that are not physical or permanent or were not generated by Oracle Database. For example, the row addresses of index-organized tables are stored in index leaves, which can move. Rowids of foreign tables (such as DB2 tables accessed through a gateway) are not standard Oracle rowids.

Oracle uses universal rowids (urowids) to store the addresses of index-organized and foreign tables. Index-organized tables have logical urowids and foreign tables have foreign urowids. Both types of urowid are stored in the ROWID pseudocolumn (as are the physical rowids of heap-organized tables).

Oracle creates logical rowids based on the primary key of the table. The logical rowids do not change if the primary key does not change. The ROWID pseudocolumn of an index-organized table has a data type of UROWID. You can access this pseudocolumn as you would the ROWID pseudocolumn of a heap-organized table (that is, using a SELECT ... ROWID statement). To store the rowids of an index-organized table, then define a column of type UROWID for the table and retrieve the value of the ROWID pseudocolumn into that column.

**See Also:**

[UROWID](../sqlrf/Data-Types.md) in Oracle Database SQL Language Reference.

#### 2.1.8 Converting from One Data Type to Another

In many cases, Oracle OLAP performs automatic data type conversion for you as discussed in "Automatic Conversion of Textual Data Types" and "Automatic Conversion of Numeric Data Types". Additionally there are a number of OLAP DML functions that you can use to convert values from one data type to another.

##### 2.1.8.1 Automatic Conversion of Textual Data Types

Oracle OLAP automatically converts `NTEXT` values to `TEXT` when they are specified as arguments to OLAP DML statements. This can result in data loss when the `NTEXT` values cannot be represented in the database character set

##### 2.1.8.2 Automatic Conversion of Numeric Data Types

Oracle OLAP automatically converts `SHORTINTEGER` variables and `INTEGER` variables (with a fixed width of 1 byte to `INTEGER` (with a width of 4 bytes) for calculations. When you calculate a total of `SHORTINTEGER` variables, then you can obtain and report a result greater than 32,767 or less than -32,768. When you calculate a total of 1-byte `INTEGER` variables, then you can obtain and report a result greater than 127 or less than -128. However, when you try to assign the result to a `SHORTINTEGER` variable or a 1-byte `INTEGER` variable respectively, then the variable is set to `NA`.

Oracle OLAP automatically converts numeric data types according to the following rules:

- When you use a value with the `SHORTINTEGER` or `SHORTDECIMAL` data type in an expression, then the value is converted to its long counterpart before using it. See "Boolean Expressions" for information about problems that can occur when you mix `SHORTDECIMAL` and `DECIMAL` data types in a comparison expression.

- When you save the results of a calculation as a value with the `SHORTINTEGER` data type, then NA is stored when the result is outside the range of a `SHORTINTEGER` (‐32768 to 32767).

- When you assign the value of a `DECIMAL` expression to an object with the `INTEGER` data type, then the value is rounded before storing or using it.

  **Note:**

  When a `DECIMAL` value is outside the range of an `INTEGER`, then an NA is stored.

- When you use a decimal value where a value with the `INTEGER` data type is required, then the value is rounded before storing or using it.

  **Note:**

  When the DECIMAL value is outside the range of an INTEGER, then an NA is stored.

- When you assign the value of a decimal expression to a variable with the `SHORTDECIMAL` data type, then only the first 7 significant digits are stored.

- When you combine `NUMBER` values with other numeric data types, then all values are converted to `NUMBER`.

When these conversion are not what you want, then you can use the CONVERT, TO_CHAR, TO_NCHAR, TO_NUMBER, or TO_DATE functions to get different results.

### 2.2 OLAP DML Operators

An operator is a symbol that transforms a value or combines it in some way with another value. The following table describes the categories of OLAP DML operators.

Table 2-9 OLAP DML Operators

| Category     | Description                                                                                                                                                                                                                                                                                                                                                                                |
|:-------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Arithmetic   | Operators that you can use in numeric expressions with numeric data to produce a numeric result. You can also use some arithmetic operators in date expressions with a mix of date and numeric data, which returns either a date or numeric result. For a list of arithmetic operators, see "Arithmetic Operators". For more information on numeric expressions, see "Numeric Expressions" |
| Comparison   | Operators that you can use to compare two values of the same basic type (numeric, text, date, or, in rare cases, Boolean), which returns a `BOOLEAN` result. For a list of comparison operators, see "Comparison and Logical Operators". For more information on `BOOLEAN` expressions, see "Boolean Expressions".                                                                         |
| Logical      | The `AND`, `OR`, and `NOT` operators that you can use to transform `BOOLEAN` values using logical operations, which returns a `BOOLEAN` result. For a list of logical operators, see "Comparison and Logical Operators". For more information on `BOOLEAN` expressions, see "Boolean Expressions".                                                                                         |
| Assignment   | An operator that you use to assign the results of an expression into an object or to assign a value to an OLAP DML option. For more information on using assignment statements, see the [SET](olap-dml-commands-h-z.md), and [SET1](olap-dml-commands-h-z.md) commands, and "Assignment Operator".                                                                                         |
| Conditional  | The `IF...THEN...ELSE`, `SWITCH`, and `CASE` operators that you can use to use to select between values based on a condition. For more information, see "Conditional Expressions".                                                                                                                                                                                                         |
| Substitution | The `&` (ampersand) operator that you can use to evaluate an expression and substitute the resulting value. For more information, see "Substitution Expressions".                                                                                                                                                                                                                          |

#### 2.2.1 Arithmetic Operators

The following table shows the OLAP DML arithmetic operators, their operations, and priority where priority is the order in which that operator is evaluated. Operators of the same priority are evaluated from left to right. When you use two or more operators in a numeric expression, the expression is evaluated according to standard rules of arithmetic. You must code a comma before a negative number that follows another numeric expression, or the minus sign is interpreted as a subtraction operator. For example, `intvar,-4`

Table 2-10 Arithmetic Operators

| Operator | Operation      | Priority |
|:---------|:---------------|:---------|
| `-`      | Sign reversal  | 1        |
| `**`     | Exponentiation | 2        |
| `*`      | Multiplication | 3        |
| `/`      | Division       | 3        |
| \*       | Addition       | 4        |
| `-`      | Subtraction    | 4        |

#### 2.2.2 Comparison and Logical Operators

You use comparison and logical operators to make expressions in much the same way as arithmetic operators. Each operator has a priority that determines its order of evaluation. Operators of equal priority are evaluated left to right, unless parentheses change the order of evaluation. However, the evaluation is halted when the truth value is decided.

The following table shows the OLAP DML comparison operators and logical operators (`AND`, `OR`, and `NOT`). It lists the operator, the operations, example, and priority where priority is the order in which that operator is evaluated. Operators of the same priority are evaluated from left to right.

Table 2-11 Comparison and Logical Operators

| Operator | Operation                                         | Example                         | Priority |
|:---------|:--------------------------------------------------|:--------------------------------|:---------|
| `NOT`    | Returns opposite of `BOOLEAN` expression          | `NOT(YES) = NO`                 | 1        |
| `EQ`     | Equal to                                          | `4 EQ 4 = YES`                  | 2        |
| `NE`     | Not equal to                                      | `5 NE 2 = YES`                  | 2        |
| `GT`     | Greater than                                      | `5 GT 7 = NO`                   | 2        |
| `LT`     | Less than                                         | `5 LT 7 = YES`                  | 2        |
| `GE`     | Greater than or equal to                          | `8 GE 8 = YES`                  | 2        |
| `LE`     | Less than or equal to                             | `8 LE 9 = YES`                  | 2        |
| `IN`     | Is a date in a time period?                       | `'1Jan02' IN myDimension = YES` | 2        |
| `LIKE`   | Does a text value match a specified text pattern? | `'Finance' LIKE '%nan%' = YES`  | 2        |
| `AND`    | Both expressions are true                         | `8 GE 8 AND 5 LT 7 = YES`       | 3        |
| `OR`     | Either expression is true                         | `8 GE 8 OR 5 GT 7 = YES`        | 4        |

#### 2.2.3 Assignment Operator

In the OLAP DML, as in many other programming languages, the = (equal) sign is used as an assignment operator.

An expression creates temporary data; you can display the resulting values, but these values are not automatically stored in your analytic workspace for future reference during a session. You use an assignment statement to store the result of an expression in an object that has the same data type and dimensions as the expression. If you update and commit the object, then the values are available to you in future sessions.

Like other programming languages, an assignment statement in the OLAP DML sets the value of the target expression equal to the results of the source expression. However, an OLAP DML assignment statement does not work exactly as it does in other programming languages. Like many other OLAP DML statements it does not assign a value to a single cell, instead, when the target-expression is a multidimensional object, Oracle OLAP loops through the cells of the target object setting each one to the results of the source-expression. Additionally, you can use UNRAVEL to copy the values of an expression into the cells of a target object when the dimensions of the expression are different from the dimensions of the target object.

For more information on using assignment statements in the OLAP DML, see [SET](olap-dml-commands-h-z.md) and [SET1](olap-dml-commands-h-z.md).

### 2.3  OLAP DML Expressions

Expressions represent data values in the syntax of the OLAP DML. This section provides the following information about OLAP DML expressions:

- "About OLAP DML Expressions"

- "Using Workspace Objects in Expressions".

- "Working with Empty Cells in Expressions"

- Detailed information about the various types of OLAP DML expressions:

  - Numeric Expressions
  - Text Expressions
  - Datetime and Interval Expressions
  - Date-only Expressions
  - Boolean Expressions
  - Conditional Expressions
  - Substitution Expressions

#### 2.3.1 About OLAP DML Expressions

An OLAP DML expression has a data type and can also have dimensions. You can use expressions as arguments in statements. An expression often performs a mathematical or logical operation. It always evaluates to a result in a workspace data type.

An expression can be:

- A literal value. For example, `10` or `'East'`

- An analytic workspace object that contains multiple values. For example, the variable `sales`

- A function that returns one or more values. For example, TOTAL or JOINLINES

- Another expression that combines literal values, dimensions, variables, formulas, and functions with operators. For example, `inflation*1.02`

You can save an expression as a formula as described in "[OLAP DML Formulas](formulas-models-aggregations-and-allocations.md)"

##### 2.3.1.1 How the Data Type of an Expression is Determined

The data type of an expression is the data type of the resulting value. It might not be the same as the data type of the data objects that constitute the expression; it depends on the data and on the operators and functions that are involved.

In addition, a conditional expression that is indicated by an `IF`... `THEN`...`ELSE` operator is supported. A conditional expression returns a value whose data type depends on the expressions in the `THEN` and `ELSE` clauses, not on the expression in the `IF` clause, which must be `BOOLEAN`.

**Note:**

Do not confuse a conditional expression with the IF...THEN...ELSE command in a program, which has similar syntax but a different purpose. The `IF` statement does not have a data type and is not evaluated like an expression.

##### 2.3.1.2 How the Dimensionality of an Expression is Determined

An expression is dimensioned by a union of the dimensions of all of the variables, dimensions, relations, formulas, qualified data references, and functions in the expression:

- Variables, relations, and formulas are dimensioned by the dimensions listed in the definition of the object.

  Example 1: When the `price` variable is dimensioned by `month` and `product`, then the expression `price` `*` `1.2` is also dimensioned by `month` and `product`.

  Example 2: When the `units` variable is dimensioned by `month`, `product`, and `district`, then the expression `units` `*` `price` is dimensioned by `month`, `product`, and `district` (even though the dimensions of the `price` variable are `month` and `product` only).

- Qualified data references (QDRs) are dimensioned by all of the dimensions of the associated object, except for the dimensions being qualified. (For more information about qualified data references, see "Limiting a Dimension to a Single Value Without Changing Status".)

- The return values of most OLAP DML functions are, in most cases, dimensioned by the union of the dimensions of the input arguments. However, some functions (such as aggregation functions) have fewer dimensions than the input arguments. In these cases, the dimensionality of the return value is documented in the topic for the function in [OLAP DML Functions: A - K](olap-dml-functions-a-k.md).

  **Note:**

  Unless otherwise noted, when you specify breakout dimensions or relations in an aggregation function, you change the dimensionality of the expression. The first dimension that you specify as a breakout dimension is the slowest varying and the last dimension that you specify is the fastest varying.

**Note:**

You can change the dimensionality of an expression or subexpression using the CHGDIMS function

###### 2.3.1.2.1 Determining the Dimensions of an Expression

You can find out the dimensions of an expression by issuing a PARSE statement, followed by the INFO function. PARSE evaluates the text of an expression; the INFO indicates how the expression is interpreted.

This example illustrates the use of the DIMENSION keyword with the INFO function to retrieve the dimensions of the expression just analyzed by PARSE. Assume that you issue the following statement.

    PARSE 'TOTAL(sales region)'

The statement produces the following output.

    SHOW INFO(PARSE DIMENSION)
    REGION

###### 2.3.1.2.2 How Dimension Status Affects the Number of Values in the Results of Expressions

The number of values an expression yields depends on the dimensions of the expression and the status of those dimensions. An expression yields one data value for each combination of dimension values in the current status. For example, when three dimension values are in status for `month`, and two for `product`, then the expression `price` GT `100` results in six values (3 times 2).

Thus, to get the desired results, you must ensure that the dimensions of an expression are limited to the range of data you want to consider. In addition, you must consider any PERMIT statements that might limit access to the dimensions of the data.

When you want to specify a single value without changing the current status you can use a qualified data reference (QDR). Using a QDR, you can qualify a dimension (which enables you to specify one dimension value in an expression) or one or more dimensions of a variable or relation. For more information on dimension status, see "[How to Specify the Set of Data that OLAP DML Operations Work Against](olap-dml-basic-concepts.md)"; for more information on QDRs, see "Limiting a Dimension to a Single Value Without Changing Status".

#### 2.3.2 Using Workspace Objects in Expressions

You can use an analytic workspace data object in an expression by specifying its name as described in "Syntax for Specifying an Object in an Expression". When calculating the expression, Oracle OLAP uses the data in the specified object as described in "How OLAP DML Data Objects Behave in Expressions".

##### 2.3.2.1 How OLAP DML Data Objects Behave in Expressions

The following table summarizes how Oracle OLAP uses the data in an object used as an argument in an expression.

Table 2-12 Objects in Expressions

| Object               | Use in Expressions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Variables            | As a one-dimensional or multi-dimensional array of data, depending on its definition. For example, as the target or source expression in an assignment statement.<br>See also "Using Variables and Relations in Expressions" and "[OLAP DML Commands: H-Z](olap-dml-commands-h-z.md)".                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Relations            | As a one-dimensional or multi-dimensional of data, depending on its definition. For example, as the target or source expression in an assignment statement as outlined in "[OLAP DML Commands: H-Z](olap-dml-commands-h-z.md)".<br>• When you use a relation in a text expression, the relation value is referenced as a text value. The values of the related dimension that is contained in the relation are converted into text, and you can use these values in an expression. You can also compare a text literal to a relation.<br>• When you use a relation in a numeric expression, the relation value is referenced by its position (an `INTEGER`) in its related dimension array. You can use this numeric value in an expression. The position number is based on the default status list of the dimension, not the current status list of the dimension.<br>See also "Using Variables and Relations in Expressions" , "Using Related Dimensions in Expressions". |
| Dimensions           | As a one-dimensional array of data. When you use a `TEXT` dimension value in a numeric expression or compare values in a non-numeric dimension, Oracle OLAP uses the `INTEGER` position number of the value in the array (as based on the default status list) rather than the value itself.<br>See also "Specifying a Value of a CONCAT Dimension" and "Using Related Dimensions in Expressions".                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Composites           | You can use a composite wherever you can use a dimension.<br>See also "Specifying a Value of a Composite" .                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Valuesets            | As a list of dimension values.<br>See also "Using Variables and Relations in Expressions" and the [DEFINE VALUESET](olap-dml-commands-a-g.md) command.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Dimension surrogates | As a one-dimensional array. A surrogate provides an alternative set of values for a dimension. When you use a `TEXT` surrogate value in a numeric expression or compare values in a non-numeric surrogate, Oracle OLAP uses the `INTEGER` position number of the value in the array (as based on the default status list) rather than the value itself.<br>Note: You can use a surrogate rather than a dimension in a model, in a LIMIT command, in a qualified data reference, or in data loading with statements such as FILEREAD, FILEVIEW, SQL FETCH, and SQL IMPORT. A surrogate cannot be a participant object in any argument in a DEFINE statement that defines another object.                                                                                                                                                                                                                                                                                      |
| Formulas             | As a sub-expression or as an expression in a statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Programs             | For a program that does not return a value, use the program name as you would an OLAP DML command. For a program that returns a value, invoke the program the same way that you invoke an OLAP DML function: use the program name in the expression and enclose the program arguments, if any, in parentheses.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

##### 2.3.2.2 Syntax for Specifying an Object in an Expression

You can specify an analytic workspace object in an expression using the following syntax.

\[\[schema-name.\]analytic-workspace-name!\]object-name

schema-name
The name of the schema in which the analytic workspace was defined when it was created. By default, an analytic workspace is created in the schema for the database user ID of the user issuing the AW CREATE statement. In almost any DML statement, you can specify the full name of an analytic workspace (for example, `Scott.demo`).

analytic-workspace-name
The name of the workspace that contains the desired object. By specify the analytic workspace name along with the object name you create a qualified object name (QON) for the object. Using a qualified object name for an object is recommended except in those situations described in "When Not to Use Qualified Object Names".

You can specify the value for analytic-workspace-name in any of the following ways:

- The name of an analytic workspace. A workspace name is assigned when an analytic workspace is created with an AW CREATE statement.

- The alias name of an analytic workspace. An analytic workspace alias is an alternative name for an attached analytic workspace. You can assign or delete an alias with an AW ALIAS LIST statement. An alias is in effect from the time it is assigned to the time that the workspace is detached (or until the alias is deleted). Therefore, each time you attach an unattached workspace, you must reassign its aliases.

  One reason for assigning an alias is to have a short way to reference an analytic workspace that belongs to a schema that is not yours. For example, you can use the alias in qualified object names and statements that reference such an analytic workspace. Another reason for assigning an alias is to write generic code that includes a reference to an analytic workspace but does not hard-code its name. With the alias providing a generic reference, you can assign the alias and run the code on different workspaces at different times.

- Within an aggregation specification, model, or program, you can use `THIS_AW` to qualify an object name. When Oracle OLAP compiles an object, it interprets any occurrence of `THIS_AW` as the name of the workspace in which the object is being compiled. Thus if you have an analytic workspace named `myworkspace` that contains a program named `myprog` and a variable named `myvar`, Oracle OLAP interprets a statement myvar=1 as though it was written `myworkspace!myvar=1`. Within a program, you can retrieve the value of `THIS_AW` using the THIS_AW option.

When you do not specify a value for analytic-workspace-name, Oracle OLAP assumes that the specified object is in the current analytic workspace. The current analytic workspace is the first analytic workspace in the list of the active analytic workspaces that you view with an AW LIST statement. You can retrieve the name of the current analytic workspace by using the AW function with the NAME keyword.

**Note:**

Your session does not have to have a current analytic workspace. When you start Oracle OLAP without specifying an analytic workspace name, then the `EXPRESS` analytic workspace is first on the list. However, in this case, the `EXPRESS` analytic workspace is not current; there is no current analytic workspace until you specify one with the AW command.

object-name
The name of the object unless the object is an unnamed composite. When the object is an unnamed composite, use the following syntax.

    SPARSE \<basedims....\>

For the basedims argument, specify the names of the dimensions, separated by spaces, for which the unnamed composite was created. For an example of using an unnamed composite in an OLAP DML statement, see [Example 10-104](olap-dml-commands-h-z.md).

Objects with the same name in different workspaces are treated as completely separate objects, and no similarity or relationship is assumed to exist between them. Any OLAP DML language restrictions that apply between objects in different workspaces apply even when the objects have the same name. For example, you cannot dimension an object in one workspace by a dimension that resides in another workspace, even when both workspaces have dimensions with the same name.

###### 2.3.2.2.1 Considerations When Creating and Using Qualified Object Names

Although the use of qualified object names for objects is typical, there are several considerations to keep in mind:

- There are some situations where you cannot use a qualified object name or do not need to use a qualified object name. See "When Not to Use Qualified Object Names" for more information

- Before you use ampersand substitution when creating a qualified object name you must understand how and when the substitution occurs. See "Using Ampersand Substitution for Workspace and Object Names" for more information.

- Special considerations apply when passing a qualified object name as an argument to a program. See "Passing Qualified Object Names to Programs" for more information.

##### When Not to Use Qualified Object Names

Generally it is good practice to use a qualified object name in an expression. However, there are some situations where you cannot use a qualified object name or when a qualified object name is not necessary:

- The following objects cannot have qualified object names:

  - An object that is local to a particular program because it was created by an ARGUMENT or VARIABLE statement.

  - The NAME dimension of any given workspace. When you reference the NAME dimension, Oracle OLAP always uses the NAME dimension of the current workspace.

- You do not need to use a qualified object name in the following circumstances:

  - In the qualifiers of a qualified data reference (QDR). Only the object being qualified needs to be named with a qualified object name. Any unqualified names are assumed to apply to objects in the same workspace as the object being qualified.

  - In an unnamed composite, when you specify one base dimension as a qualified object name, then all the others are assumed to come from the same workspace.

  - In a named composite, when the name is a qualified object name then its base dimensions are assumed to come from the same workspace.

  - In a model, when you specify the solution variable as a qualified object name, then all the dimensions named in DIMENSION statements are assumed to come from the same workspace.

##### Using Ampersand Substitution for Workspace and Object Names

The workspace name, or the object name, or both can be supplied using ampersand substitution. However, take care when using a qualified object name with ampersand substitution because Oracle OLAP parses the qualified object name (with its exclamation point) before it resolves the ampersand reference. For example, in the expression `&awname!objname`, the ampersand (`&`) applies to the entire qualified object name, not just to the workspace name.

##### Passing Qualified Object Names to Programs

When you pass a qualified object name as an argument to a program and you use an ARGUMENT statement and the ARG, ARGFR, and ARGS functions, the entire qualified object name is considered to be a single argument. Its component parts are not passed separately.

##### 2.3.2.3 Specifying Values of Dimensions and Composites in Expressions

In most cases, you refer to the value of a dimension by specifying the value following the conventions for the data type of the value. For example, assume that you have a `TEXT` dimension named `geog`. You can add the value "World" to the dimension by issuing the following statement.

    MAINTAIN geog ADD 'World'

Note, however, that when you use a `TEXT` dimension value in a numeric expression or compare values in a non-numeric dimension, Oracle OLAP uses the `INTEGER` position number of the value in the array (as based on the default status list) rather than the value itself.

Special considerations apply to specifying the values of composites and concat dimensions.

###### 2.3.2.3.1 Specifying a Value of a Composite

You can specify a value of a composite in the following ways:

- By specifying a set of values of the base dimensions of the composite using the following syntax.

        {composite_name  \| SPARSE} {\<base_dimension_name base_dimension_value }, ...\>

- (Named composites only) By specifying just the values of the composite using the following syntax.

         composite_name   \<base_dimension_value ...\>

  where base_dimension_value is a set of values of the base dimensions, in the order in which they were defined in the composite, separated by spaces.

###### 2.3.2.3.2 Specifying a Value of a CONCAT Dimension

Once you have defined a unique CONCAT dimension, you can refer to its values simply by specifying the values of the base dimensions.

However, you must specify a value of a nonunique CONCAT dimension as a concatenation of the name of the base dimension and the base dimension value separated by a colon (:) and a space and enclosed in angle brackets(\<\>). In an expression, use the following format.

     \<BASE_DIMENSION_NAME: base_dimension value\>

For example, assume that you have defined the base dimensions named `city` and `state` and, a CONCAT dimension for them named `geog`. When you report on the `geog` dimension, the values of `geog` include the names of the base dimensions along with the values.

    DEFINE city DIMENSION TEXT
    DEFINE state DIMENSION TEXT
    DEFINE geog DIMENSION CONCAT(city state)
    MAINTAIN city ADD 'New York'
    MAINTAIN state ADD 'New York'
    REPORT geog

     GEOG
    -----------------------------------
    <CITY: New York>
    <STATE: New York>

###### 2.3.2.3.3 Using Related Dimensions in Expressions

The syntax of some OLAP DML statements (for example, some variations of the LIMIT command) include two dimension arguments referred to as a dimension, and a related dimension. Other OLAP DML statements (for example, AVERAGE, ANY, COUNT, CUMSUM, NONE, LARGEST, SMALLEST, and TOTAL) allow you to specify the dimensionality of the result in terms of a related dimension. In these contexts, the related dimension is any dimension that shares a relation with another dimension.

Even though the value that you specify for the arguments in these statements is the name of a dimension, in actuality Oracle OLAP uses a relation between the dimensions to perform its calculations. When the two dimensions share only one relation, the behavior is clear. Oracle OLAP performs the calculation based on the values in that relation.

However, when two dimensions share multiple relations, then the behavior is less clear. In some cases, as with a LIMIT using LEVELREL command, you can specify the shared relation you want Oracle OLAP to use. In other cases, the statement syntax does not allow you to specify the name of a relation. In this case, Oracle OLAP chooses among the multiple relations as described in "[OLAP DML Commands: H-Z](olap-dml-commands-h-z.md)".

##### 2.3.2.4 Using Variables and Relations in Expressions

In expressions, a variable is referenced as an array containing values of the specified data type. A relation is referenced as an array containing values of the specified dimension. In most other respects, variables and relations (both typically multidimensional objects) share the same characteristics.

In most cases, when you use OLAP DML statements with variables that are defined with composites, the statements treat those variables as if they were defined with base dimensions:

- You can access a variable that is dimensioned by a composite by requesting any of the base dimension values.

- The values of a composite that are in status are determined by the status of the base dimensions of the composite. Composites are not dimensions, and therefore, they do not have any independent status.

When you use a REPORT statement or any other statement that loops over a variable that uses a composite, the default behavior is to evaluate all the combinations of the values of the base dimensions of the composite that are in status. Any combinations that do not exist in the composite display NA for their associated data.

For example, the following statements create a report for the East region that shows the number of coupons issued for sportswear from January through March 2002. Because no coupons were issued in March 2002, the report displays NA in that column.

    LIMIT month TO 'Jan02' 'Feb02' 'Mar02'
    LIMIT market TO 'East'
    LIMIT product TO 'Sportswear'
    REPORT coupons

    MARKET: EAST
                   ------------COUPONS-------------
                   -------------MONTH--------------
    PRODUCT          Jan02      Feb02      Mar02
    -------------- ---------- ---------- ----------
    Sportswear          1,000      1,000         NA

However, for performance reasons, you can change the default looping behavior for statements such as REPORT, ROW, and the assignment statement (SET) so that they loop over the values in the composite rather than all of the base dimension values.

##### 2.3.2.5 Limiting a Dimension to a Single Value Without Changing Status

A qualified data reference (QDR) is a way of limiting one or more dimensions of a data object to a single value. QDRs are useful when you want to specify a single value of a data object without changing the current status. Using a QDR, you can qualify a dimension (which enables you to specify one dimension value in an expression) or one or more dimensions of a variable or relation.

Sometimes the syntax of a QDR is ambiguous and could either be misinterpreted or cause a syntax error. In this case, you can use the [QUAL](olap-dml-functions-l-z.md) function to explicitly specify a qualified data reference (QDR).

###### 2.3.2.5.1 Syntax of a Qualified Data Reference

You specify a qualified data reference using the following syntax

     expression(dimname1 dimexp1 \[, dimname2 dimexp2. . .\])

The `dimname` argument is the name of a dimension or a dimension surrogate of the dimension, of the expression and the dimexp argument is one of the following:

- A value of dimname.

  **Note:**

  The setting of the [LIMITSTRICT](olap-dml-options.md) option determines how Oracle OLAP behaves when a QDR specifies a nonexistent value. By default, when you specify a nonexistent value, Oracle OLAP treats the nonexistent value as an invalid value and issues an error. If, instead, you want Oracle OLAP to treat a nonexistent value as an `NA` value, set the value of LIMITSTRICT to `NO`.

- A text expression whose result is a value of dimname.

- A numeric expression whose result is the logical position of a value of dimname.

- A relation of `dimname.`

  **Note:**

  When syntax of a QDR is ambiguous and could either be misinterpreted or cause a syntax error, use the [QUAL](olap-dml-functions-l-z.md) function to explicitly specify a qualified data reference (QDR).

###### 2.3.2.5.2 Qualifying a Variable

You can qualify any or all of the dimensions of a variable using either of the following techniques:

- The QDR can temporarily limit a dimension of the variable by selecting one specified value of the dimension. This value can be outside the current status.

- The QDR can replace a dimension of the variable with a less aggregate related dimension when you supply the name of an appropriate relation as the qualifier. The dimension is temporarily replaced by the dimension(s) of the relation.

For example, the variable `sales` has three dimensions, `month`, `product`, and `district`. You might want to compare total sales in Boston to the total sales in all cities. In a single statement, you want `district` to be limited to two different values:

- For the numerator of the expression, you want the status of `district` to be `Boston`.

- For the denominator of the expression, you want the status of `district` to be `ALL`.

The following statement lets you calculate this result by using a QDR.

    SHOW sales(district 'Boston')/TOTAL(sales)

You can qualify multiple dimensions of a variable. For example, when you qualify all the dimensions of the `sales` variable by specifying one dimension value of each dimension, then you narrow `sales` down to a single–cell value.

To fetch sales for `Jun02`, `Tents`, and `Seattle`, use the following QDR.

    SHOW sales(month 'Jun02', product 'Tents', district 'Seattle')

This statement fetches a single value.

You can use a qualified data reference with the target expression of an assignment ([SET](olap-dml-commands-h-z.md)) statement. This lets you assign a value to a specific cell in a data object.

The following example assigns the value 10200 to the data cell of the `sales` composite that is specified in the qualified data reference. When the composite named `sales` does not have a value for the combination `Boston` and `Tents`, then this value combination is added to the composite, thus adding the data cell.

    sales(market 'Boston' product 'Tents' month 'Jan99')= 10200

###### 2.3.2.5.3 Replacing a Dimension in a Variable

When you use a relation as the qualifier in the QDR, you replace a dimension of the variable with the dimension or dimensions of the relation. The relation must be related to the dimension that you are qualifying, and it must be dimensioned by the replacement dimension.

Example 2-1 Replacing a Dimension in a Variable

Suppose you have two variables, `sales` and `quota`, which are dimensioned by `month`, `product`, and `district`. A third variable, `division`.`mgr`, is dimensioned by `month` and `division`. You also have a relation between `division` and `product`, called `division`.`product`. These objects have the following definitions.

    DEFINE sales VARIABLE DECIMAL <month product district>
    LD Sales Revenue
    DEFINE quota VARIABLE DECIMAL <month product district>
    DEFINE division.mgr VARIABLE TEXT <month division>
    DEFINE division.product RELATION division <product>
    LD Division for each product

The following statement produces the report following it.

    REPORT division.mgr

    -------------------DIVISION.MGR----------------------
              ----------------------MONTH--------------------------
    DIVISION  JAn02    Feb02    Mar02    Apr02    May02    Jun02
    --------  -------- -------- -------- -------- -------- --------
    Camping   Hawley   Hawley   Jones    Jones    Jones    Jones
    Sporting  Carey    Carey    Carey    Carey    Carey    Musgrave
    Clothing  Musgrave Musgrave Musgrave Musgrave Musgrave Wong

Suppose you want to obtain a report that shows the fraction by which sales have exceeded quota and you want to include the appropriate division manager for each product. You can show the division manager for each product by using the relation `division`.`product`, which is related to `division` and dimensioned by `product`, as the qualifier. The QDR replaces the `division` dimension with `product`, so that it has the same dimensions as the other expression in the report `sales` / `quota`. The following statement produces the report following it.

    REPORT DOWN month sales W 6 sales/quota W 8 HEADING -
       'MANAGER' division.mgr(division division.product)

    DISTRICT: BOSTON
            -----------------------------PRODUCT------------------------------------
            ----TEnts---- ---canoes---- --racquets---  --sportswear-- ---footwear---
            Sales/        Sales/        Sales/         Sales/         Sales/
    Month   Quota Manager Quota Manager Quota Manager  Quota Manager  Quota  Manager
    ------  ----- ------- ----- ------- ----- -------  ----- -------- ----- --------
    Jan02   1.00  Hawley  0.82  Hawley  1.02  Carey    0.91  Musgrave 0.92  Musgrave
    Feb02   0.84  Hawley  0.96  Hawley  1.00  Carey    0.80  Musgrave 1.07  Musgrave
    Mar02   0.87  Jones   0.95  Jones   0.87  Carey    0.88  Musgrave 0.91  Musgrave
    Apr02   0.91  Jones   0.93  Jones   0.99  Carey    0.94  Musgrave 0.95  Musgrave
    ...

###### 2.3.2.5.4 Qualifying a Relation

You can also use a QDR to qualify a relation (which is really a special kind of variable).

Suppose the `region`.`district` relation is dimensioned by `district`. When you qualify `district` with the value `Seattle`, then the value of the expression is the value of the relation for `Seattle`. Because the QDR specifies one value of `district`, the expression has a single–cell result.

The definition of `region`.`district` is as follows.

    DEFINE region.district RELATION region <district>
    LD The region for each district

The following statement displays the value `WEST`.

    SHOW region.district(district 'Seattle')

###### 2.3.2.5.5 Qualifying a Dimension

You can use a QDR to qualify the dimension itself, which enables you to specify one dimension value in an expression. The following expression specifies one value of `district`, the one contained in the single‐cell variable `mydistrict`.

    district(district mydistrict)

For a concat dimension, you can use a QDR to qualify the dimension by specifying a value from a base dimension of the concat dimension. The following expression specifies one value of `reg.dist.ccdim`, a concat dimension that has `region` and `district` as its base dimensions. The costs variable is dimensioned by the `division` and `reg.dist.ccdim` dimensions.

    SHOW reg.dist.ccdim(district 'Boston')

The preceding expression produces the following result.

    <DISTRICT: Boston>

###### 2.3.2.5.6 Using Ampersand Substitution with QDRs

An ampersand character (`&`) at the beginning of an expression substitutes the value of the expression for the expression itself in a statement. When you use an ampersand with a QDR, you must enclose the whole expression in parentheses when you want the variable to be qualified before the substitution is made.

Suppose you have a text variable named `myvar` that is dimensioned by `reptype` and that contains the names of variables. Remember that it is `myvar` that is dimensioned by `reptype`, not the variables named by `myvar`. Therefore, you must use parentheses so that `myvar` is qualified and the resulting value is used in a REPORT statement.

    REPORT &(myvar(reptype 'actual'))

When you do not use parentheses and the variable that is specified in `myvar` is `sales`, then you get an error message that `sales` is not dimensioned by `reptype`.

#### 2.3.3 Working with Empty Cells in Expressions

At any given time, some cells of an analytic workspace data object may be empty. An empty cell occurs when a specific data value has not been assigned to it or when a data value cannot be calculated for the cell. The value of any empty cell in an object is `NA`. An `NA` value has no specific data type. Certain functions (for example, the aggregation functions) return NA when the requested information is not available or cannot be calculated. Similarly, an expression whose value cannot be calculated has `NA` as its value.

**Note:**

To support OLAP DML composite-dimensioned variables that correspond to relational fact tables with null facts, OLAP has a special NA value which is controlled by an NA2 bit. For more information on how Oracle OLAP manages NA values controlled by NA2 bits, see "[NA2 Bits and Null Tracking](olap-dml-commands-a-g.md)".

##### 2.3.3.1 Specifying a Value of NA

There are cases in which you might specify an operation for which no data is available. For example, there might be no appropriate value for a given cell in a variable, for the return value of a function, or for the value of an expression that includes an arithmetic operator. In these cases, an `NA` (Not Available) value is automatically supplied.

To set the values of a variable or relation to `NA`, you can use an assignment statement (SET), as shown in the following example.

    sales = NA

##### 2.3.3.2 Controlling how NA values are treated

Several options and functions control how `NA` values are treated. For example:

- The NA options listed in "[Options by Category](olap-dml-options.md)".

- The NAFILL function returns the values of the source expression with any `NA` values appearing as the specified fill expression. You can include this function in an expression to control the format of its value.

- System properties listed in [OLAP DML Properties](olap-dml-properties.md).

#### 2.3.4 Numeric Expressions

A numeric expression evaluates to any of the numeric data types. The data in a numeric expression can be any combination of the following:

- Numeric literals as discussed in "Numeric Data Types".

- Numeric variables or formulas

- Dimensions

- Functions that yield numeric results

- Date literals, variables, formulas, or functions

In addition, you can join any of these expressions with the arithmetic operators for a more complex numeric expression. You use arithmetic operators in numeric expressions with numeric data, which returns a numeric result. You can also use some arithmetic operators in date expressions with a mix of date and numeric data, to retrieve either a date or numeric result.

Several options determine how Oracle OLAP handles numeric expressions.

##### 2.3.4.1 Mixing Numeric Data Types

You can include any type of numeric data in the same numeric expression.

The data type of the result is determined according to the following rules:

- When all the data in the expression is `INTEGER` or `SHORTINTEGER`, and the only operations are addition, subtraction, and multiplication, then the result is `INTEGER`.

- When any of the data is `NUMBER`, then the result is `NUMBER`.

- When any of the data is `DECIMAL` or `SHORTDECIMAL`, and no data is `NUMBER`, then the result is `DECIMAL`.

- When you perform any division or exponentiation operations, then the result is `DECIMAL`.

##### 2.3.4.2 Using Text Dimensions in Arithmetic Expressions

When you use a dimension with a data type of `TEXT` in a numeric expression, the dimension value is treated as a position (an `INTEGER`) and is used as a numeric. The position number is based on the default status list, not on current status.

##### 2.3.4.3 Limitations of Floating Point Calculations

All decimal data is converted to floating point format, both for storing and for calculations. In floating point format, a number is represented by means of a mantissa and an exponent. The mantissa and the exponent are stored as binary numbers. The mantissa is a binary fraction which, when multiplied by a number equal to 2 raised to the exponent, produces a number that equals or closely approximates the original decimal number.

Because there is not always an exact binary representation for a fractional decimal number, just as there is not an exact representation for the decimal value of 1/3, fractional parts of decimal numbers cannot always be represented exactly as binary fractions. Arithmetic operations on floating point numbers can result in further approximations, and the inaccuracy gradually increases with the number of operations. In addition to the approximation factor, the available number of significant digits affects the exactness of the result.

For all of these reasons, a result computed by the TOTAL, AVERAGE, or other aggregation functions on a `DECIMAL` or `SHORTDECIMAL` variable can differ in the least significant digits from a result you compute by hand. Because the `SHORTDECIMAL` data type provides a maximum of only seven significant digits, you see more of these differences with `SHORTDECIMAL` data. Therefore, you might want to use the `NUMBER` data type when accuracy is more important than computational speed, such as variables that contain currency amounts.

Another result of the fact that some fractional decimal numbers cannot be exactly represented by binary fractions is that for such numbers, the `DECIMAL` data type offers a different and closer approximation than the `SHORTDECIMAL` data type, because it has more significant digits. This can lead to problems when `SHORTDECIMAL` and `DECIMAL` data types are mixed in a comparison expression. For information on how to handle such comparisons, see "Boolean Expressions" .

##### 2.3.4.4 Controlling Errors During Calculations

You can control the following types of errors:

- Division by zero. When you divide an NA value by zero, then the result is NA; no error occurs. Dividing a non‐NA value by zero normally produces an error. When a divide‐by‐zero error occurs when you are making a calculation on dimensioned data, then you can end up with partial results. When you use REPORT or an assignment statement (SET), values are reported or stored as they are calculated, so the division by zero halts the loop before it has gone through all the values.

  When you want to suppress the divide‐by‐zero error, then you can change the value of the DIVIDEBYZERO option to `YES`. Consequently, the result of any division by zero is NA and no error occurs. This allows the calculation of the other values of a dimensioned expression to continue.

- Root of negative numbers. It is normally an error to try to take the root of a negative number (which includes raising a number to a non‐integer power). When you want to suppress the error message and allow the calculation of roots for non‐negative values of the expression to continue, then set the ROOTOFNEGATIVE option to `YES`.

- Overflow errors. The DECIMALOVERFLOW option works in a similar manner to DIVIDEBYZERO. It lets you control whether an error is generated when a calculation produces a decimal result larger than it can handle.

#### 2.3.5 Text Expressions

A text expression evaluates to data with the `TEXT,` `NTEXT,` or `ID` data type. Text expressions can be any combination of the following:

- Text literals. For example, `'Boston'` or `'Current` `Sales` `Report'`

- Text dimensions. For example, `district` or `month`

- Text variables or formulas. For example, `product.name`

- Functions that yield text results. For example,` JOINLINES('Product:` ' `product.name)`

##### 2.3.5.1 Language of Text Expressions

Oracle OLAP supports text expressions in all languages that you can identify using the [NLS_LANGUAGE](olap-dml-options.md) option. It also supports multi-language programs and applications using a language dimension.

**See Also:**

"Language of Text Expressions"in [\$DEFAULT_LANGUAGE](olap-dml-properties.md)

##### 2.3.5.2 Working with DATETIME Values in Text Expressions

When you use a `DATETIME` value where a text value (`TEXT,` `NTEXT,` or `ID`) is expected, or when you store a `DATETIME` value in a text variable, then the `DATETIME` value is automatically converted to a text value.

The format of a `DATETIME` value is controlled by the NLS_DATE_FORMAT option. Once a `DATETIME` value is stored in a text variable, the NLS_DATE_FORMAT setting has no impact.

##### 2.3.5.3 Working with NTEXT Data

`TEXT` and `NTEXT` data are interchangeable in most cases. However, implicit conversion can occur, such as when an `NTEXT` value is assigned to a `TEXT` variable. When `TEXT` is converted to `NTEXT`, no data loss occurs because the UTF-8 character encoding of the `NTEXT` data type encompasses most other data types. However, when `NTEXT` is converted to `TEXT`, data loss occurs when `NTEXT` characters are not represented in the workspace character set.

When `TEXT` and `NTEXT` values are used together, for example in a call to the `JOINCHARS` function, the `TEXT` value is converted to `NTEXT` and an `NTEXT` value is returned.

#### 2.3.6 Datetime and Interval Expressions

As discussed in "Datetime and Interval Data Types", the OLAP DML supports the same datetime and interval data types that are supported by SQL. This section discusses:

- "Datetime Expressions"

- "Interval Expressions"

- "Datetime/Interval Arithmetic"

##### 2.3.6.1 Datetime Expressions

A datetime expression yields a value of a datetime data type. A datetime expression has the following syntax.

datetime_value_expr AT LOCAL \|

TIME ZONE { ' \[ + \| - \] hh:mm' \| DBTIMEZONE \| 'time_zone_name' \| expr }

A `datetime_value_expr` can be a datetime value or a compound expression that yields a datetime value. Datetimes and intervals can be combined according to the rules defined in Table 2-7. The three combinations that yield datetime values are valid in a datetime expression.

If you specify `AT` `LOCAL`, Oracle uses the current session time zone.

The settings for `AT` `TIME` `ZONE` are interpreted as follows:

- The string `'(+|-)HH:MM'` specifies a time zone as an offset from UTC.

- `DBTIMEZONE`: Oracle uses the database time zone established (explicitly or by default) during database creation.

- `SESSIONTIMEZONE`: Oracle uses the session time zone established by default or in the most recent `ALTER` `SESSION` statement.

- `time_zone_name`: Oracle returns the `datetime_value_expr` in the time zone indicated by `time_zone_name`. For a listing of valid time zone names, query the `V$TIMEZONE_NAMES` dynamic performance view.

  **Note:**

  Timezone region names are needed by the daylight savings feature. The region names are stored in the time zone files under `oracore/zoneinfo`. The server always uses the large time zone file corresponding to the version number recorded in `sys.props$`.

<!-- -->

- `expr`: If `expr` returns a character string with a valid time zone format, Oracle returns the input in that time zone. Otherwise, Oracle returns an error.

##### 2.3.6.2 Interval Expressions

An interval expression yields a value of `DSNTERVAL` or `MYINTERVAL` where the expression has the following syntax.

interval_value_expr  DAY \[(leading_field_precision)\] TO  

   SECOND \[(fractional_second_precision)\]\| YEAR \[(leading_field_precision)\] TO  MONTH

The `interval_value_expr` can be a `DSNTERVAL` or `MYINTERVAL` value or a compound expression that yields a `DSNTERVAL` or `MYINTERVAL` value. Datetimes and intervals can be combined according to the rules defined in Table 2-7 . The six combinations that yield interval values are valid in an interval expression.

Both `leading_field_precision` and `fractional_second_precision` can be any integer from 0 to 9. If you omit the `leading_field_precision` for either `DAY` or `YEAR`, then Oracle Database uses the default value of 2. If you omit the `fractional_second_precision` for second, then the database uses the default value of 6. If the value returned by a query contains more digits that the default precision, then Oracle Database returns an error. Therefore, it is good practice to specify a precision that you know is at least as large as any value returned by the query.

##### 2.3.6.3 Datetime/Interval Arithmetic

You can perform several arithmetic operations on date (`DATETIME`), timestamp (`TIMESTAMP`, `TIMESTAMP_TZ`, and `TIMESTAMP_LTZ`) and interval (`DSINTERVAL` and `YMINTERVAL`) data. Oracle calculates the results based on the following rules:

- You can use `NUMBER` constants in arithmetic operations on date and timestamp values, but not interval values. Oracle internally converts timestamp values to date values and interprets `NUMBER` constants in arithmetic datetime and interval expressions as numbers of days. For example, `SYSDATE` + 1 is tomorrow. `SYSDATE` - 7 is one week ago. `SYSDATE` + (10/1440) is ten minutes from now. Subtracting the `hire_date` column of the sample table `employees` from `SYSDATE` returns the number of days since each employee was hired. You cannot multiply or divide date or timestamp values.

- Oracle implicitly converts `BINARY_FLOAT` and `BINARY_DOUBLE` operands to `NUMBER`.

- Each `DATETIME` value contains a time component, and the result of many date operations include a fraction. This fraction means a portion of one day. For example, 1.5 days is 36 hours. These fractions are also returned by Oracle built-in functions for common operations on `DATETIME` data. For example, the `MONTHS_BETWEEN` function returns the number of months between two dates. The fractional portion of the result represents that portion of a 31-day month.

- If one operand is a `DATETIME` value or a numeric value (neither of which contains time zone or fractional seconds components), then:

  - Oracle implicitly converts the other operand to `DATETIME` data. (The exception is multiplication of a numeric value times an interval, which returns an interval.)

  - If the other operand has a time zone value, then Oracle uses the session time zone in the returned value.

  - If the other operand has a fractional seconds value, then the fractional seconds value is lost.

- When you pass a timestamp, interval, or numeric value to a built-in function that was designed only for the `DATETIME` data type, Oracle implicitly converts the non-`DATETIME` value to a `DATETIME` value.

- When interval calculations return a datetime value, the result must be an actual datetime value or the database returns an error.

- Oracle performs all timestamp arithmetic in UTC time. For `TIMESTAMP_LTZ`, Oracle converts the datetime value from the database time zone to UTC and converts back to the database time zone after performing the arithmetic. For `TIMESTAMP_TZ`, the datetime value is always in UTC, so no conversion is necessary.

The following table is a matrix of datetime arithmetic operations. Dashes represent operations that are not supported.

Table 2-13 Matrix of Datetime Arithmetic

| Operand & Operator | DATETIME   | TIMESTAMP   | INTERVAL    | Numeric     |
|:-------------------|:-----------|:------------|:------------|:------------|
| `DATETIME`         | —          | —           | —           | —           |
| `+ `               | `—`        | `—`         | `DATETIME`  | `DATETIME`  |
| `- `               | `DATETIME` | `DATETIME`  | `DATETIME`  | `DATETIME`  |
| `* `               | `—`        | `—`         | `—`         | `—`         |
| `/ `               | `—`        | `—`         | `—`         | `—`         |
| `TIMESTAMP`        | —          | —           | —           | —           |
| `+ `               | `—`        | `—`         | `TIMESTAMP` | `—`         |
| `- `               | `INTERVAL` | `INTERVAL`  | `TIMESTAMP` | `TIMESTAMP` |
| `* `               | `—`        | `—`         | `—`         | `—`         |
| `/ `               | `—`        | `—`         | `—`         | `—`         |
| `INTERVAL`         | —          | —           | —           | —           |
| `+ `               | `DATETIME` | `TIMESTAMP` | `INTERVAL`  | `—`         |
| `- `               | `—`        | `—`         | `INTERVAL`  | `—`         |
| `* `               | `—`        | `—`         | `—`         | `INTERVAL`  |
| `/ `               | `—`        | `—`         | `—`         | `INTERVAL`  |
| `Numeric`          | —          | —           | —           | —           |
| `+ `               | `DATETIME` | `DATETIME`  | `—`         | `NA`        |
| `- `               | `—`        | `—`         | `—`         | `NA`        |
| `* `               | `—`        | `—`         | `INTERVAL`  | `NA`        |
| `/ `               | `—`        | `—`         | `—`         | `NA`        |

##### Examples

You can add an interval value expression to a start time. Consider the sample table `oe.orders` with a column `order_date`.

#### 2.3.7 Date-only Expressions

A date-only expression is an expression that evaluates to the OLAP DML `DATE` data type as discussed in "Date-only Data Type". The expression might be a function that returns a date-only value, a date-only literal, or a more complex expression.

**See Also:**

"Date-only Input Values", "Date-only Dimension Values", and "DATE-only Variable Display Styles".

##### Calculating DATE-only Values

You can add numbers to a `DATE` value, or subtract numbers from them. Whole numbers are calculated as days, and decimal values are calculated as fractions of a day. For example, `SYSDATE+1.5` adds 1 day and 12 hours to the current date and time. You cannot divide or multiply `DATE` values, and you cannot subtract them from numbers. For example, `1-SYSDATE` and `1*SYSDATE` return errors.

##### Using DATE-only Values in Arithmetic Expressions

When you use DATE values in arithmetic expressions, the result can be numeric or it can be a date. The legal operations for dates and the data type of the result are outlined in the following table:

Table 2-14 Legal Operations for DATE Values

| Operation                                    | Result                                                                                                                                                                                                                                                                                                                       |
|:---------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Add or subtract a number from a date         | Future or prior date                                                                                                                                                                                                                                                                                                         |
| Subtract a date from a date                  | The number of days between the dates.                                                                                                                                                                                                                                                                                        |
| Add or subtract a number from a time period. | The time period at the appropriate interval in the future or the past, similar to the return values of the LEAD or LAG function. The result is NA when there is no dimension value that corresponds to the result. The calculation is made based on the positions of the values in the default status list of the dimension. |

#### 2.3.8 Boolean Expressions

A Boolean expression is a logical statement that is either `TRUE` or `FALSE`. Boolean expressions can compare data of any type if both parts of the expression have the same basic data type. You can test data to see if it is equal to, greater than, or less than other data.

A Boolean expression can consist of Boolean data, such as the following:

- `BOOLEAN` values (`YES` and `NO`, and their synonyms, `ON` and `OFF`, and `TRUE` and `FALSE`)

- `BOOLEAN` variables or formulas

- Functions that yield `BOOLEAN` results

- `BOOLEAN` values calculated by comparison operators

For example, assume that your code contains the following Boolean expression.

       actual GT 20000

When processing this expression, Oracle OLAP compares each value of the variable `actual` to the constant 20,000. When the value is greater than 20,000, then the statement is `TRUE`; when the value is less than or equal to 20,000, then the statement is `FALSE`.

When you are supplying a Boolean value, you can type either `YES`, `ON`, or `TRUE` for a true value, and `NO`, `OFF`, or `FALSE` for a false value. When the result of a Boolean calculation is produced, the defaults are `YES` and `NO` in the language specified by the NLS_LANGUAGE option. The read-only YESSPELL and NOSPELL options record the `YES` and `NO` values.

Table 2-11 shows the comparison and logical operators. Each operator has a priority that determines its order of evaluation. Operators of equal priority are evaluated left to right, unless parentheses change the order of evaluation. However, the evaluation is halted when the truth value is decided. For example, in the following expression, the TOTAL function is never executed because the first phrase determines that the whole expression is true.

          yes EQ yes OR TOTAL(sales) GT 20000

##### 2.3.8.1 Creating Boolean Expressions

A Boolean expression is a three-part clause that consists of two items to be compared, separated by a comparison operator. You can create a more complex Boolean expression by joining any of these three-part expressions with the `AND` and `OR` logical operators. Each expression that is connected by `AND` or `OR` must be a complete Boolean expression in itself, even when it means specifying the same variable several times.

For example, the following expression is not valid because the second part is incomplete.

       sales GT 50000 AND LE 20000

In the next expression, both parts are complete so the expression is valid.

       sales GT 50000 AND sales LE 20000

When you combine several Boolean expressions, the whole expression must be valid even when the truth value can be determined by the first part of the expression. The whole expression is compiled before it is evaluated, so when there are undefined variables in the second part of a Boolean expression, you get an error.

Use the `NOT` operator, with parentheses around the expression, to reverse the sense of a Boolean expression.

The following two expressions are equivalent.

       district NE 'BOSTON'
       NOT(district EQ 'BOSTON')

Example 2-2 Using Boolean Comparisons

The following example shows a report that displays whether sales in Boston for each product were greater than a literal amount.

    LIMIT time TO FIRST 2
    LIMIT geography TO 'BOSTON'
    REPORT DOWN product ACROSS time: f.sales GT 7500

This `REPORT` statement returns the following data.

    CHANNEL: TOTALCHANNEL
    GEOGRAPHY: BOSTON
                   ---F.SALES GT 7500---
                   --------TIME---------
    PRODUCT          Jan02      Feb02
    -------------- ---------- ----------
    Portaudio              NO         NO
    Audiocomp             YES        YES
    TV                     NO         NO
    VCR                    NO         NO
    Camcorder             YES        YES
    Audiotape              NO         NO
    Videotape             YES        YES

##### 2.3.8.2 Comparing NA Values in Boolean Expressions

When the data you are comparing in a Boolean expression involves an NA value, a `YES` or `NO` result is returned when that makes sense. For example, when you test whether an NA value equals a non‐NA value, then the result is `NO`. However, when the result would be misleading, then `NA` is returned. For example, testing whether an NA value is less than or greater than a non–NA value gives a result of `NA`.

The following table shows the results of Boolean expressions involving NA values, which yield non‐NA values:

Table 2-15 Boolean Expressions with NA Values that Result in non-NA Values

| Expressions      | Result |
|:-----------------|:-------|
| `NA EQ NA`       | `YES`  |
| `NA NE NA`       | `NO`   |
| `NA EQ `non-`NA` | `NO`   |
| `NA NE n`on-`NA` | `YES`  |
| `NA AND NO`      | `NO`   |
| `NA OR YES`      | `YES`  |

##### 2.3.8.3 Controlling Errors When Comparing Numeric Data

When you get unexpected results when comparing numeric data, then there are several possible causes to consider:

- A number you are comparing might have a small decimal part that does not show in output because of the setting of the DECIMALS option.

- You are comparing two floating point numbers and at least one number is the result of an arithmetic operation.

- You have mixed `SHORTDECIMAL` and `DECIMAL` data types in a comparison.

Oracle recommends that you use the ABS and ROUND functions to do approximate tests for equality and avoid all three causes of unexpected comparison failure. When using ABS or ROUND, you can adjust the absolute difference or the rounding factor to values you feel are appropriate for your application. When speed of calculation is important, then you probably want to use the ABS rather than the ROUND function.

###### 2.3.8.3.1 Controlling Errors Due to Numerical Precision

Suppose `expense` is a decimal variable whose value is set by a calculation. When the result of the calculation is 100.000001 and the number of decimal places is two, then the value appears in output as 100.00. However, the output of the following statement returns `NO`.

    SHOW expense EQ 100.00

You can use the `ABS` or the `ROUND` function to ignore these slight differences when making comparisons.

###### 2.3.8.3.2 Controlling Errors When Comparing Floating Point Numbers

A standard restriction on the use of floating point numbers in a computer language is that you cannot expect exact equality in a comparison of two floating point numbers when either number is the result of an arithmetic operation. For example, on some systems, the following statement returns a `NO` instead of the expected `YES`.

    SHOW .1 + .2 EQ .3

When you deal with decimal data, do not code direct comparisons. Instead, use the ABS or the ROUND function to allow a tolerance for approximate equality. For example, either of the following two statements produce the desired `YES`.

    SHOW ABS((.1 + .2) - .3) LT .00001
    SHOW ROUND(.1 + .2) EQ ROUND(.3, .00001)

###### 2.3.8.3.3 Controlling Errors When Comparing Different Numeric Data Types

You cannot expect exact equality between `SHORTDECIMAL` and `DECIMAL` or `NUMBER` representations of a decimal number with a fractional component, because the `DECIMAL` and `NUMBER` data types have more significant digits to approximate fractional components that cannot be represented exactly.

Suppose you define a variable with a `SHORTDECIMAL` data type and set it to a fractional decimal number, then compare the `SHORTDECIMAL` number to the fractional decimal number, as shown here.

    DEFINE sdvar SHORTDECIMAL
    sdvar = 1.3
    SHOW sdvar EQ 1.3

The comparison is likely to return `NO`. What happens in this situation is that the literal is automatically typed as `DECIMAL` and converts the `SHORTDECIMAL` variable `sdvar` to `DECIMAL`, which extends the decimal places with zeros. A bit-by-bit comparison is then performed, which fails. The same comparison using a variable with a `DECIMAL` or a `NUMBER` data type is likely to return `YES`.

There are several ways to avoid this type of comparison failure:

- Do not mix the `SHORTDECIMAL` with `DECIMAL` or `NUMBER` types in comparisons. To avoid mixing these two data types, generally avoid defining variables with decimal components as `SHORTDECIMAL`.

- Use the `ABS` or `ROUND` function to allow for approximate equality. The following statements both produce `YES`.

      SHOW ABS(sdvar - 1.3) LT .00001
      SHOW ROUND(sdvar, .00001) EQ ROUND(.3, .00001)

##### 2.3.8.4 Comparing Dimension Values

Values are not compared in the same dimension based on their textual values. Instead, Oracle OLAP compares the positions of the values in the default status of the dimension. This enables you to specify statements like the following statement.

    REPORT district LT 'Seattle'

Statements are interpreted such as these using the following process:

1.  The text literal `'Seattle'` is converted to its position in the `district` default status list of the dimension.

2.  That position is compared to the position of all other values in the `district` dimension.

3.  As shown by the following report, the value `YES` is returned for districts that are positioned before `Seattle` in the `district` default status list of the dimension, and `NO` for `Seattle` itself.

        REPORT 22 WIDTH district LT 'Seattle'

        District       DISTRICT LT 'Seattle'
        -------------- ----------------------
        Boston                            YES
        Atlanta                           YES
        Chicago                           YES
        Dallas                            YES
        Denver                            YES
        Seattle                            NO

A more complex example assigns increasing values to the variable `quota` based on initial values assigned to the first six months. The comparison depends on the position of the values in the `month` dimension. Because it is a time dimension, the values are in chronological order.

    quota = IF month LE 'Jun02' THEN 100 ELSE LAG(quota, 1, month)* 1.15

However, when you compare values from different dimensions, such as in the expression `region` `lt` `district`, then the only common denominator is `TEXT`, and text values are compared, not dimension positions.

##### 2.3.8.5 Comparing Dates

You can compare two dates with any of the Boolean comparison operators. For dates, "less" means before and "greater" means after. The expressions being compared can include any of the date calculations discussed in Table 2-11. For example, in a billing application, you can determine whether today is 60 or more days after the billing date to send out a more strongly worded bill.

    bill.date + 60 LE SYSDATE

Dates also have a numeric value. You can use the TO_NUMBER and TO_DATE functions to change a value from a `DATE` to an I`NTEGER` or an `INTEGER` to a `DATE` for comparison.

##### 2.3.8.6 Comparing Text Data

When you compare text data, you must specify the text exactly as it appears, with punctuation, spaces, and uppercase or lowercase letters. A text literal must be enclosed in single quotes. For example, this expression tests whether the first letter of each employee's name is greater than the letter "M."

    EXTCHARS(employee.name, 1, 1) GT 'M'

You can compare `TEXT` and `ID` values, but they can only be equal when they are the same length. When you test whether a text value is greater or less than another, the ordering is based on the setting of the NLS_SORT option.

You can compare numbers with text by first converting the number to text. Ordering is based on the values of the characters. This can produce unexpected results because the text is evaluated from left to right. For example, the text literal `1234` is greater than `100,999.00` because `2`, the second character in the first text literal, is greater than `0`, the second character in the second text literal.

Suppose `name.label` is an `ID` variable whose value is `3‐Person` and `name.desc` is a `TEXT` variable whose value is `3‐Person Tents`.

The result of the following `SHOW` statement is `NO`.

    SHOW name.desc EQ name.label

The result of the following statements is `YES`.

    name.desc = '3-Person'
    SHOW name.desc EQ name.label

###### 2.3.8.6.1 Comparing a Text Value to a Text Pattern

The Boolean operator `LIKE` is designed for comparing a text value to a text pattern. A text value is like another text value or pattern when corresponding characters match.

Besides literal matching, `LIKE` lets you use wildcard characters to match multiple characters in a string:

- An underscore (\_) character in a pattern matches any single character.

- A percent (%) character in a pattern matches zero or more characters in the first string.

For example, a pattern of `%AT_` matches any text that contains zero or more characters, followed by the characters `AT`, followed by any other single character. Both `DATA` and `ERRATA` return `YES` when `LIKE` is used to compare them with the pattern `%AT_`.

The results of expressions using the LIKE operator are affected by the settings of the LIKECASE and LIKENL options.

No negation operator exists for LIKE. To accomplish negation, you must negate the entire expression. For example, the result of the following statement is `NO`.

    SHOW NOT ('Boston' LIKE 'Bo%')

###### 2.3.8.6.2 Comparing Text Literals to Relations

You can also compare a text literal to a relation. A relation contains values of the related dimension and the text literal is compared to a value of that dimension. For example, `region`.`district` holds values of `region`, so you can do the following comparison.

    region.district EQ 'West'

#### 2.3.9 Conditional Expressions

A conditional expression is an expression you can use to select between values based on a condition. You can use conditional expression as part of any other expression if the data type is appropriate. Oracle OLAP supports the use of the following conditional expressions:

- IF...THEN...ELSE expression

- SWITCH Expressions

##### 2.3.9.1 IF...THEN...ELSE expression

An IF expression is an expression you can use to select one of two values based on a Boolean condition.

**Note:**

Do not confuse the IF expression with the IF...THEN...ELSE command, which has similar syntax but a different purpose, and which must be used in an Oracle OLAP program. The IF...THEN...ELSE command does not have a data type and is not evaluated like an expression.

An IF expression has the following syntax.

IF Boolean-expression THEN expression1 ELSE expression2

In most cases, expression1 and expression2 must be of the same basic data type (numeric, text, or Boolean) and the data type of the whole expression is determined using the same rules as those for the binary operators. However, when the data type of either expression1 or expression2 is DATE, it is possible for the other expression to have a numeric or text data type. Because Oracle OLAP expects both data types to be DATE, it converts the numeric or text value to a DATE. Also, when the value of one expression is a dimension value then the value of the other expression is converted to a dimension value as it is for QDRs.

You can nest IF expressions; however, in this case, you might want to use a SWITCH expression instead as discussed in "SWITCH Expressions".

An IF expression is processed by first evaluating the Boolean expression; then:

- When the result of the Boolean expression is `TRUE`, then expression1 is evaluated and returns that value.

- When the result of the Boolean expression is `FALSE`, then expression2 is evaluated and returns that value.

The `expression1` and `expression2` arguments are any valid OLAP DML expressions that evaluate to the same basic data type. However, when the data type of either value is `DATE`, it is possible for the other value to have a numeric or text data type. Because both data types are expected to be `DATE`, Oracle OLAP converts the numeric or text value to a `DATE`. The data type of the whole expression is the same as the two expressions. When the result of the Boolean expression is `NA`, then `NA` is returned.

Example 2-3 Using an IF Expression

This example shows a sales bonus report. The bonus is 5 percent of the amount that sales exceeded budget, but when sales in the district are below budget, then the bonus is zero.

    LIMIT month TO 'Jan02' TO 'Jun02'
    LIMIT product TO 'Tents'
    REPORT DOWN district IF sales-sales.plan LT 0 THEN 0
           ELSE .05*(sales-sales.plan)

    PRODUCT: TENTS
            ---IF SALES-SALES.PLAN LT 0 THEN 0 ELSE .05*(SALES-SALES.PLAN)---
              ----------------------MONTH------------------------------
    DISTRICT   Jan02    Feb02    Mar02     Apr02    May02    Jun02
    --------- -------- -------- -------- ------- --------- ----------
    Boston      229.53     0.00     0.00    0.00    584.51     749.13
    Atlanta       0.00     0.00     0.00  190.34    837.62   1,154.87
    Chicago       0.00     0.00     0.00   84.06    504.95     786.81
    ...

##### 2.3.9.2 SWITCH Expressions

A SWITCH expression consists of a series of CASE expressions. You can use a SWITCH expression as an alternative to a complicated, nested IF ... THEN ... ELSE expression when all the conditions are equality comparisons with a single value.

**Note:**

Do not confuse the SWTICH expression with the SWITCH command, which has similar syntax but a different purpose, and which must be used in an Oracle OLAP program. The SWITCH command is not evaluated like an expression.

A SWITCH expression has the following syntax.

SWITCH expression DO { case-label ...  exp \[,\] }  ... DOEND

where `case-label` has the following syntax:

     CASE exp: \| DEFAULT:

When processing a SWITCH expression, Oracle OLAP compares each CASE expression in succession until it finds a match. When a match is found, it returns the value specified after the last label of the current case group. When no match is found and a DEFAULT label is specified, it returns the value specified for the DEFAULT case; otherwise it returns `NA`.

Example 2-4 Using a SWITCH Expression Instead of an IF Expression

Assume that you have coded the following OLAP DML statement which includes nested IF...THEN...ELSE statements.

       testprogram = IF testtype EQ 0 -
                    THEN 'program0' -
                    ELSE IF testtype EQ 1 -
                      THEN 'program1' -
                      ELSE IF testtype EQ 2 OR testtype EQ 3 -
                        THEN 'program2'
                        ELSE NA


You could, instead, code the same behavior using a SWITCH expression as shown below.

       testprogram = SWITCH testtype DO -
                    CASE 0: 'program0', -
                    CASE 1: 'program1', -
                    CASE 2: -
                    CASE 3: 'program2', -
                    DEFAULT: NA -
                    DOEND

You could also code the same behavior using a SWITCH statement that spans fewer lines, omits commas, and omits the DEFAULT case because `NA` is the default return value when a match is not found.

       testprogram = SWITCH testtype DO CASE 0: 'program0' CASE 1: 'program1' -
                  CASE 2: CASE 3: 'program2' DOEND

#### 2.3.10 Substitution Expressions

To construct a substitution expression, use an ampersand character (`&`) at the beginning of an expression. Using an ampersand (that is, the substitution operator) this way is also called ampersand substitution. The ampersand specifies that Oracle OLAP evaluates an expression containing a substitution expression as follows:

1.  Evaluate the expression following the ampersand (the substitution expression).

2.  Evaluate the rest of the expression using the result of step 1 (that is, the result of the substitution expression).

Ampersand substitution gives you a level of indirection when you are specifying an expression. For example, when you specify an ampersand followed by a variable that holds the name of another variable, the value of the expression becomes the data in the second variable. Ampersand substitution lets you write more general programs that can operate on data that is chosen when the program is run. Note, however, that, Oracle OLAP does not compile program lines with ampersand substitution; instead these lines are interpreted when the program runs. To avoid ampersand substitution in a program, you can often use an IF or SWITCH command instead.

You cannot use ampersand substitution in model equations.

##### Using Ampersand Substitution with QDRs

When you use an ampersand with a QDR, you must enclose the whole expression in parentheses if you want the variable to be qualified before the substitution is made.

Suppose you have a text variable named `myvar` that is dimensioned by `reptype` and that contains the names of variables. Remember that it is `myvar` that is dimensioned by `reptype`, not the variables named by `myvar`. Therefore, you must use parentheses so that `myvar` is qualified and the resulting value is used in a REPORT statement.

    REPORT &(myvar(reptype 'actual'))

When you do not use parentheses and the variable that is specified in `myvar` is `sales`, then you get an error message that `sales` is not dimensioned by `reptyp`

Example 2-5 Using Ampersand Substitution

Suppose you have a variable called `curname` that holds the name of a dimension in the analytic workspace (`product`). When you execute the following statement, then REPORT produces the single value, `product`, which is the actual value stored in the `curname` variable.

    REPORT curname

    CURNAME
    ----------
    PRODUCT

However, when you execute the following statement, then REPORT produces the values of the dimension `product`.

    REPORT &curname

    PRODUCT
    --------------
    Tents
    Canoes
    Racquets
    Sportswear
    Footwear
