## 9  SQL and PL/SQL Programming in a Global Environment

This chapter contains information useful for SQL programming in a globalization support environment. This chapter includes the following topics:

- Locale-Dependent SQL Functions with Optional NLS Parameters

- Other Locale-Dependent SQL Functions

- Miscellaneous Topics for SQL and PL/SQL Programming in a Global Environment

### 9.1 Locale-Dependent SQL Functions with Optional NLS Parameters

NLS parameters can be specified for all SQL functions whose behavior depends on globalization support conventions. These functions are:

    TO_CHAR
    TO_DATE
    TO_NUMBER
    NLS_UPPER
    NLS_LOWER
    NLS_INITCAP
    NLSSORT

Explicitly specifying the optional NLS parameters for these functions enables the functions to be evaluated independently of the session's NLS parameters. This feature can be important for SQL statements that contain numbers and dates as string literals.

For example, the following query is evaluated correctly if the language specified for dates is `AMERICAN`:

    SELECT last_name FROM employees WHERE hire_date > '01-JAN-2005';

Such a query can be made independent of the current date language by using a statement similar to the following:

    SELECT last_name FROM employees
         WHERE hire_date > TO_DATE('01-JAN-2005','DD-MON-YYYY',
         'NLS_DATE_LANGUAGE = AMERICAN');

In this way, SQL statements that are independent of the session language can be defined where necessary. Such statements are necessary when string literals appear in SQL statements in views, `CHECK` constraints, or triggers.

**Note:**

Only SQL statements that must be independent of the session NLS parameter values should explicitly specify optional NLS parameters in locale-dependent SQL functions. Using session default values for NLS parameters in SQL functions usually results in better performance.

All character functions support both single-byte and multibyte characters. Except where explicitly stated, character functions operate character by character, rather than byte by byte.

The rest of this section includes the following topics:

- Default Values for NLS Parameters in SQL Functions

- Specifying NLS Parameters in SQL Functions

- Unacceptable NLS Parameters in SQL Functions

#### 9.1.1 Default Values for NLS Parameters in SQL Functions

When SQL functions evaluate views and triggers, default values from the current session are used for the NLS function parameters. When SQL functions evaluate `CHECK` constraints, they use the default values that were specified for the NLS parameters when the database was created.

#### 9.1.2 Specifying NLS Parameters in SQL Functions

NLS parameters are specified in SQL functions as follows:

    'parameter = value'

For example:

    'NLS_DATE_LANGUAGE = AMERICAN'

The following NLS parameters can be specified in SQL functions:

    NLS_DATE_LANGUAGE
    NLS_NUMERIC_CHARACTERS
    NLS_CURRENCY
    NLS_ISO_CURRENCY
    NLS_DUAL_CURRENCY
    NLS_CALENDAR
    NLS_SORT

Table 9-1 shows which NLS parameters are valid for specific SQL functions.

Table 9-1 SQL Functions and Their Valid NLS Parameters

| SQL Functions                                     | Valid NLS Parameters                                                                                                             |
|:--------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `TO_DATE`                                         | `NLS_DATE_LANGUAGE`<br>`NLS_CALENDAR`                                                                                            |
| `TO_NUMBER`                                       | `NLS_NUMERIC_CHARACTERS`<br>`NLS_CURRENCY`<br>`NLS_DUAL_CURRENCY`<br>`NLS_ISO_CURRENCY`                                          |
| `TO_CHAR, TO_NCHAR`                               | `NLS_DATE_LANGUAGE`<br>`NLS_NUMERIC_CHARACTERS`<br>`NLS_CURRENCY`<br>`NLS_ISO_CURRENCY`<br>`NLS_DUAL_CURRENCY`<br>`NLS_CALENDAR` |
| `NLS_UPPER, NLS_LOWER,`<br>`NLS_INITCAP, NLSSORT` | `NLS_SORT`                                                                                                                       |

The following examples show how to use NLS parameters in SQL functions:

    TO_DATE ('1-JAN-99', 'DD-MON-YY',
       'nls_date_language = American')

    TO_CHAR (hire_date, 'DD/MON/YYYY',
       'nls_date_language = French')

    TO_CHAR (SYSDATE, 'DD/MON/YYYY',
        'nls_date_language=''Traditional Chinese'' ')

    TO_NUMBER ('13.000,00', '99G999D99',
       'nls_numeric_characters = '',.''')

    TO_CHAR (salary, '9G999D99L', 'nls_numeric_characters = '',.''
       nls_currency = ''EUR''')

    TO_CHAR (salary, '9G999D99C', 'nls_numeric_characters = ''.,''
       nls_iso_currency = Japan')

    NLS_UPPER (last_name, 'nls_sort = Swiss')

    NLSSORT (last_name, 'nls_sort = German')

**Note:**

In some languages, some lowercase characters correspond to more than one uppercase character or vice versa. As a result, the length of the output from the `NLS_UPPER`, `NLS_LOWER`, and `NLS_INITCAP` functions can differ from the length of the input.

**See Also:**

- "[Special Uppercase Letters](linguistic-sorting-and-matching.md)"

- "[Special Lowercase Letters](linguistic-sorting-and-matching.md)"

#### 9.1.3 Unacceptable NLS Parameters in SQL Functions

The following NLS parameters are not accepted in SQL functions except for `NLSSORT`:

    NLS_LANGUAGE
    NLS_TERRITORY
    NLS_DATE_FORMAT

`NLS_DATE_FORMAT` and `NLS_TERRITORY_FORMAT` are not accepted as parameters because they can interfere with required format masks. A date format must always be specified if an NLS parameter is in a `TO_CHAR` or `TO_DATE` function. As a result, `NLS_DATE_FORMAT` and `NLS_TERRITORY_FORMAT` are not valid NLS parameters for the `TO_CHAR` or `TO_DATE` functions. If you specify `NLS_DATE_FORMAT` or `NLS_TERRITORY_FORMAT` in the `TO_CHAR` or `TO_DATE` function, then an error is returned.

`NLS_LANGUAGE` can interfere with the session value of `NLS_DATE_LANGUAGE`. If you specify `NLS_LANGUAGE` in the `TO_CHAR` function, for example, then its value is ignored if it differs from the session value of `NLS_DATE_LANGUAGE`.

### 9.2 Other Locale-Dependent SQL Functions

This section includes the following topics:

- The CONVERT Function

- SQL Functions for Different Length Semantics

- LIKE Conditions for Different Length Semantics

- Character Set SQL Functions

- The NLSSORT Function

#### 9.2.1 The CONVERT Function

The `CONVERT` function enables conversion of character data between character sets.

The `CONVERT` function converts the binary representation of a character string in one character set to another. It uses exactly the same technique as conversion between database and client character sets. Hence, it uses replacement characters and has the same limitations.

**See Also:**

"[Character Set Conversion Between Clients and the Server](choosing-character-set.md)"

The syntax for `CONVERT` is as follows:

    CONVERT(char, dest_char_set[, source_char_set])

`char` is the value to be converted. `source_char_set` is the source character set and `dest_char_set` is the destination character set. If the `source_char_set` parameter is not specified, then it defaults to the database character set.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/CONVERT.md) for more information about the `CONVERT` function

- "[Character Set Conversion Support](appendix-A-locale-data.md)" for character set encodings that are used only for the `CONVERT` function

#### 9.2.2 SQL Functions for Different Length Semantics

Oracle provides SQL functions that work in accordance with different length semantics. There are three groups of such SQL functions: `SUBSTR`, `LENGTH`, and `INSTR`. Each function in a group is based on a different kind of length semantics and is distinguished by the character or number appended to the function name. For example, `SUBSTRB` is based on byte semantics.

The `SUBSTR` functions return a requested portion of a substring. The `LENGTH` functions return the length of a string. The `INSTR` functions search for a substring in a string.

The `SUBSTR` functions calculate the length of a string differently. Table 9-2 summarizes the calculation methods.

Table 9-2 How the SUBSTR Functions Calculate the Length of a String

| Function  | Calculation Method                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SUBSTR`  | Calculates the length of a string in characters based on the length semantics associated with the character set of the data type. For example, AL32UTF8 characters are calculated in UCS-4 characters. UTF8 and AL16UTF16 characters are calculated in UCS-2 characters. A supplementary character is counted as one character in AL32UTF8 and as two characters in UTF8 and AL16UTF16. Because `VARCHAR` and `NVARCHAR2` may use different character sets, `SUBSTR` may give different results for different data types even if two strings are identical. If your application requires consistency, then use `SUBSTR2` or `SUBSTR4` to force all semantic calculations to be UCS-2 or UCS-4, respectively. |
| `SUBSTRB` | Calculates the length of a string in bytes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `SUBSTR2` | Calculates the length of a string in UCS-2 characters, which is compliant with Java strings and Windows client environments. Characters are represented in UCS-2 or 16-bit Unicode values. Supplementary characters are counted as two characters.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `SUBSTR4` | Calculates the length of a string in UCS-4 characters. Characters are represented in UCS-4 or 32-bit Unicode values. Supplementary characters are counted as one character.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `SUBSTRC` | Calculates the length of a string in Unicode composed characters. Supplementary characters and composed characters are counted as one character.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

The `LENGTH` and `INSTR` functions calculate string length in the same way, according to the character or number added to the function name.

The following examples demonstrate the differences between `SUBSTR` and `SUBSTRB` on a database whose character set is AL32UTF8.

For the string `Fußball,` the following statement returns a substring that is 4 characters long, beginning with the second character:

    SELECT SUBSTR ('Fußball', 2 , 4) SUBSTR FROM DUAL;

    SUBS
    ----
    ußba

For the string `Fußball,` the following statement returns a substring 4 bytes long, beginning with the second byte:

    SELECT SUBSTRB ('Fußball', 2 , 4) SUBSTRB FROM DUAL;

    SUB
    ---
    ußb

**See Also:**

[Oracle Database SQL Language Reference ](../sqlrf/About-SQL-Functions.md)for more information about the `SUBSTR`, `LENGTH`, and `INSTR` functions

#### 9.2.3 LIKE Conditions for Different Length Semantics

The `LIKE` conditions specify a test that uses pattern-matching. The equality operator (=) exactly matches one character value to another, but the `LIKE` conditions match a portion of one character value to another by searching the first value for the pattern specified by the second.

`LIKE` calculates the length of strings in characters using the length semantics associated with the input character set. The `LIKE2`, `LIKE4`, and `LIKEC` conditions are summarized in Table 9-3.

Table 9-3 LIKE Conditions

| Function | Description                                                                                                                    |
|:---------|:-------------------------------------------------------------------------------------------------------------------------------|
| `LIKE2`  | Use when characters are represented in UCS-2 semantics. A supplementary character is considered as two characters.             |
| `LIKE4`  | Use when characters are represented in UCS-4 semantics. A supplementary character is considered as one character.              |
| `LIKEC`  | Use when characters are represented in Unicode complete character semantics. A composed character is treated as one character. |

There is no `LIKEB` condition.

#### 9.2.4 Character Set SQL Functions

Two SQL functions, `NLS_CHARSET_NAME` and `NLS_CHARSET_ID`, can convert between character set ID numbers and character set names. They are used by programs that need to determine character set ID numbers for binding variables through OCI.

Another SQL function, `NLS_CHARSET_DECL_LEN`, returns the declaration length of a column in number of characters, given the byte length of the column.

This section includes the following topics:

- Converting from Character Set Number to Character Set Name

- Converting from Character Set Name to Character Set Number

- Returning the Length of an NCHAR Column

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/About-SQL-Functions.md)

##### 9.2.4.1 Converting from Character Set Number to Character Set Name

The `NLS_CHARSET_NAME`(`n`) function returns the name of the character set corresponding to ID number`n`. The function returns `NULL` if `n` is not a recognized character set ID value.

##### 9.2.4.2 Converting from Character Set Name to Character Set Number

`NLS_CHARSET_ID`(`text`) returns the character set ID corresponding to the name specified by `text`. `text` is defined as a run-time `VARCHAR2` quantity, a character set name. Values for `text` can be `NLSRTL` names that resolve to character sets that are not the database character set or the national character set.

If the value `CHAR_CS` is entered for `text`, then the function returns the ID of the database character set. If the value `NCHAR_CS` is entered for `text`, then the function returns the ID of the database's national character set. The function returns `NULL` if `text` is not a recognized name.

**Note:**

The value for `text` must be entered in uppercase characters.

##### 9.2.4.3 Returning the Length of an NCHAR Column

`NLS_CHARSET_DECL_LEN`(`BYTECNT`, `CSID`) returns the declaration length of a column in number of characters, given the byte length of the column. `BYTECNT` is the byte length of the column. `CSID` is the character set ID of the column.

#### 9.2.5 The NLSSORT Function

The `NLSSORT` function enables you to force a specific collation (sort order) for `ORDER BY`, `GROUP BY`, comparison conditions, and a number of other collation-sensitive operations. However, starting with Oracle Database 12c Release 2 (12.2), the recommended way to force a specific collation for such operations is to use the `COLLATE` operator. The `COLLATE` operator works for all the collation-sensitive operations, including those for which `NLSSORT` cannot be used, for example `MAX`, `MIN`, and `INSTR`.

**See Also:**

"[Expression Evaluation and the COLLATE Operator](linguistic-sorting-and-matching.md)"

The `NLSSORT` function calculates a collation key for its character argument. The collation key is a value of data type `RAW`, which has the following property: when two collation keys created for a given collation for two (possibly different) source character values are compared as binary, their mutual ordering corresponds to the expected mutual ordering of the source character values in this collation, that is, `NLSSORT(c1) < NLSSORT(c2)`, if and only if `c1 < c2`, where both `NLSSORT` and the character operator `<` (less-than) use the same collation.

The collations used for `ORDER BY`, `GROUP BY`, comparison conditions, and other collation-sensitive operations are determined by the data-bound collation determination rules. If these rules yield a pseudo-collation, the session parameters `NLS_COMP` and `NLS_SORT` determine the actual collation.

**See Also:**

"[Collation Determination](appendix-C-collation-derivation-and-determination-rules-for-SQL-operations.md)"

The following example specifies a German collation with the `NLS_SORT` session parameter. It assumes that the declared collation of `column1` is `USING_NLS_COMP` or `USING_NLS_SORT`.

    ALTER SESSION SET NLS_SORT = GERMAN;
    SELECT * FROM table1
         ORDER BY column1;

The following example first sets the `NLS_SORT` session parameter to German, but the `NLSSORT` function overrides it by specifying a French sort.

    ALTER SESSION SET NLS_SORT = GERMAN;
    SELECT * FROM table1
         ORDER BY NLSSORT(column1, 'NLS_SORT=FRENCH');

The `WHERE` clause uses binary comparison when `NLS_COMP` is set to `BINARY` and the declared collation of referenced columns is `USING_NLS_COMP`. But, this can be overridden by using the `NLSSORT` function in the `WHERE` clause.

**Note:**

If the Data-bound Collation feature is not used, then all the columns have the declared collation of `USING_NLS_COMP`.

The following example makes a linguistic comparison using the `WHERE` clause.

    ALTER SESSION SET NLS_COMP = BINARY;
    SELECT * FROM table1
    WHERE NLSSORT(column1, 'NLS_SORT=FRENCH')>
          NLSSORT(column2, 'NLS_SORT=FRENCH');

Setting the `NLS_COMP` session parameter to `LINGUISTIC` causes the `NLS_SORT` value to be used in the `WHERE` clause.

Oracle Database may add the `NLSSORT` function implicitly to SQL expressions in a subquery to implement linguistic behavior for a category of collation-sensitive operations. The implicitly added `NLSSORT` calls are visible in the execution plan for an SQL statement.

**Note:**

The `NLSSORT` function, whether called explicitly or implicitly, may report error `ORA-12742` under certain conditions. See "[Avoiding ORA-12742 Error](linguistic-sorting-and-matching.md)" for more details regarding this error.

The rest of this section contains the following topics:

- NLSSORT Syntax

- Comparing Strings in a WHERE Clause

- Controlling an ORDER BY Clause

##### 9.2.5.1 NLSSORT Syntax

There are four ways to use `NLSSORT`:

- `NLSSORT()`, which relies on the collation determination rules

- `NLSSORT(column1, 'NLS_SORT=``xxxx``')`

- `NLSSORT(column1, 'NLS_LANG=``xxxx``')`

- `NLSSORT(column1, 'NLS_LANGUAGE=``xxxx``')`

The `NLS_LANG` parameter of the `NLSSORT` function is not the same as the `NLS_LANG` client environment setting. In the `NLSSORT` function, `NLS_LANG` specifies the abbreviated language name, such as `US` for American or `PL` for Polish. For example:

    SELECT * FROM table1
    ORDER BY NLSSORT(column1, 'NLS_LANG=PL');

When a language is specified in an `NLSSORT` call, the default collation for that language is used by the function.

##### 9.2.5.2 Comparing Strings in a WHERE Clause

`NLSSORT` enables applications to perform string matching that follows alphabetic conventions. Normally, character strings in a `WHERE` clause are compared by using the binary values of the characters. One character is considered greater than another character if it has a greater binary value in the database character set. Because the sequence of characters based on their binary values might not match the alphabetic sequence for a language, such comparisons may not follow alphabetic conventions. For example, if a column (`column1`) contains the values ABC, ABZ, BCD, and ÄBC in the ISO 8859-1 8-bit character set, then the following query returns both `BCD` and `ÄBC` because `Ä` has a higher numeric value than `B`:

    SELECT column1 FROM table1 WHERE column1 > 'B';

In German, `Ä` is sorted alphabetically before `B`, but in Swedish, `Ä` is sorted after `Z`. Linguistic comparisons can be made by using `NLSSORT` in the `WHERE` clause:

    WHERE NLSSORT(col) comparison_operator NLSSORT(comparison_string)

Note that `NLSSORT` must be on both sides of the comparison operator. For example:

    SELECT column1 FROM table1 WHERE NLSSORT(column1) > NLSSORT('B');

If a German linguistic sort has been set, then the statement does not return strings beginning with `Ä` because `Ä` comes before `B` in the German alphabet. If a Swedish linguistic sort has been set, then strings beginning with `Ä` are returned because `Ä` comes after `Z` in the Swedish alphabet.

Starting with Oracle Database 12c Release 2 (12.2), the recommended way to make the `>` (greater-than) operator use linguistic comparison is to add the `COLLATE` operator to one of the compared values. For example:

    SELECT column1 FROM table1 WHERE column1 COLLATE USING_NLS_SORT > 'B';

When you want to force a particular collation, independent of the session NLS parameters, you can specify it in place of the pseudo-collation `USING_NLS_SORT`. For example:

    SELECT column1 FROM table1 WHERE column1 COLLATE GERMAN > 'B';

**Note:**

You will get the same result as shown in the preceding examples for the `COLLATE` operator, if you remove the operator `COLLATE` and specify the corresponding collation when declaring collation of `column1` in `table1`.

**See Also:**

"[Specifying Data-Bound Collation for a Column](linguistic-sorting-and-matching.md)"

##### 9.2.5.3 Controlling an ORDER BY Clause

If a linguistic sort is in use, then `ORDER BY` clauses use an implicit `NLSSORT` on character data. The sort mechanism (linguistic or binary) for an `ORDER` `BY` clause is transparent to the application. However, if the `NLSSORT` function is explicitly specified in an `ORDER` `BY` clause, then the implicit `NLSSORT` is not done.

If a linguistic sort has been defined by the `NLS_SORT` session parameter, then an `ORDER BY` clause in an application uses an implicit `NLSSORT` function. If you specify an explicit `NLSSORT` function, then it overrides the implicit `NLSSORT` function.

When the sort mechanism has been defined as linguistic, the `NLSSORT` function is usually unnecessary in an `ORDER` `BY` clause.

When the sort mechanism either defaults or is defined as binary, then a query like the following uses a binary sort:

    SELECT last_name FROM employees
         ORDER BY last_name;

A German linguistic sort can be obtained as follows:

    SELECT last_name FROM employees
         ORDER BY NLSSORT(last_name, 'NLS_SORT = GERMAN');

**See Also:**

"[Using Linguistic Collation](linguistic-sorting-and-matching.md)"

### 9.3 Miscellaneous Topics for SQL and PL/SQL Programming in a Global Environment

This section contains the following topics:

- SQL Date Format Masks

- Calculating Week Numbers

- SQL Numeric Format Masks

- Loading External BFILE Data into LOB Columns

  **See Also:**

  [Oracle Database SQL Language Reference](../sqlrf/Format-Models.md) for a complete description of format masks

#### 9.3.1 SQL Date Format Masks

Several format masks are provided with the `TO_CHAR`, `TO_DATE`, and `TO_NUMBER` functions.

The `RM` (Roman Month) format element returns a month as a Roman numeral. You can specify either upper case or lower case by using `RM` or `rm`. For example, for the date 7 Sep 2007, `DD-rm-YYYY` returns `07-ix-2007` and `DD-RM-YYYY` returns `07-IX-2007`.

Note that the `MON` and `DY` format masks explicitly support month and day abbreviations that may not be three characters in length. For example, the abbreviations "Lu" and "Ma" can be specified for the French "Lundi" and "Mardi", respectively.

#### 9.3.2 Calculating Week Numbers

The week numbers returned by the `WW` format mask are calculated according to the following algorithm: `int(dayOfYear+6)/7`. This algorithm does not follow the ISO standard (2015, 1992-06-15).

To support the ISO standard, the `IW` format element is provided. It returns the ISO week number. In addition, the `I`, `IY`, `IYY`, and `IYYY` format elements, equivalent in behavior to the `Y`, `YY`, `YYY`, and `YYYY` format elements, return the year relating to the ISO week number.

In the ISO standard, the year relating to an ISO week number can be different from the calendar year. For example, 1st Jan 1988 is in ISO week number 53 of 1987. A week always starts on a Monday and ends on a Sunday. The week number is determined according the following rules:

- If January 1 falls on a Friday, Saturday, or Sunday, then the week including January 1 is the last week of the previous year, because most of the days in the week belong to the previous year.

- If January 1 falls on a Monday, Tuesday, Wednesday, or Thursday, then the week is the first week of the new year, because most of the days in the week belong to the new year.

For example, January 1, 1991, is a Tuesday, so Monday, December 31, 1990, to Sunday, January 6, 1991, is in week 1. Thus, the ISO week number and year for December 31, 1990, is 1, 1991. To get the ISO week number, use the `IW` format mask for the week number and one of the `IY` formats for the year.

#### 9.3.3 SQL Numeric Format Masks

Several additional format elements are provided for formatting numbers:

| Element | Description            | Purpose                                            |
|:--------|:-----------------------|:---------------------------------------------------|
| `D`     | Decimal                | Returns the decimal point character                |
| `G`     | Group                  | Returns the group separator                        |
| `L`     | Local currency         | Returns the local currency symbol                  |
| `C`     | International currency | Returns the ISO currency symbol                    |
| `RN`    | Roman numeral          | Returns the number as its Roman numeral equivalent |

For Roman numerals, you can specify either upper case or lower case, using `RN` or `rn`, respectively. The number being converted must be an integer in the range 1 to 3999.

#### 9.3.4 Loading External BFILE Data into LOB Columns

The `DBMS_LOB` PL/SQL package can load external `BFILE` data into `LOB` columns. Oracle Database performs character set conversion before loading the binary data into `CLOB` or `NCLOB` columns. Thus, the `BFILE` data does not need to be in the same character set as the database or national character set to work properly. The APIs convert the data from the specified `BFILE` character set into the database character set for the `CLOB` data type, or the national character set for the `NCLOB` data type. The loading takes place on the server because `BFILE` data is not supported on the client.

- Use `DBMS_LOB.LOADBLOBFROMFILE` to load `BLOB` columns.

- Use `DBMS_LOB.LOADCLOBFROMFILE` to load `CLOB` and `NCLOB` columns.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/using-LOB-APIs.md)
