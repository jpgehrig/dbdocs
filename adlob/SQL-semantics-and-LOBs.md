## 7  SQL Semantics and LOBs

Various SQL semantics are supported for LOBs.

These techniques allow you to use LOBs directly in SQL code and provide an alternative to using LOB-specific APIs for some operations.

Topics:

- About Using LOBs in SQL

- SQL Functions and Operators Supported for Use with LOBs

- Implicit Conversion of LOB Data Types in SQL

- Unsupported Use of LOBs in SQL

- VARCHAR2 and RAW Semantics for LOBs

- Built-in Functions for Remote LOBs and BFILEs

<!-- -->

- About Using LOBs in SQL
- SQL Functions and Operators Supported for Use with LOBs
- Implicit Conversion of LOB Data Types in SQL
- Unsupported Use of LOBs in SQL
- VARCHAR2 and RAW Semantics for LOBs
- Built-in Functions for Remote LOBs and BFILEs

**Parent topic:** [Value Semantics LOBs](value-semantic-LOBs.md)

### 7.1 About Using LOBs in SQL

You can access `CLOB` and `NCLOB` data types using SQL `VARCHAR2` semantics, such as SQL string operators and functions. (`LENGTH` functions can be used with `BLOB` data types and `CLOB` and `NCLOB`s.) These techniques are beneficial in the following situations:

- When performing operations on LOBs that are relatively small in size (up to about 100K bytes).

- After migrating your database from `LONG` columns to LOB data types, any SQL string functions, contained in your existing PL/SQL application, continue to work after the migration.

SQL semantics are not recommended in the following situations:

- When you use advanced features such as random access and piece-wise fetch, you must use LOB APIs.

- When performing operations on LOBs that are relatively large in size (greater than 1MB) using SQL semantics can impact performance. Using the LOB APIs is recommended in this situation.

  **Note:**

  SQL semantics are used with persistent and temporary LOBs. (SQL semantics do not apply to `BFILE` columns because `BFILE` is a read-only data type.)

**Parent topic:** SQL Semantics and LOBs

### 7.2 SQL Functions and Operators Supported for Use with LOBs

Many SQL operators and functions that take `VARCHAR2` columns as arguments also accept LOB columns.

- About SQL Functions and Operators for LOBs
- Implicit Conversion of CLOB to CHAR Types
- CLOBs and NCLOBs Do Not Follow Session Collation Settings
- UNICODE Support
  Variations on certain functions are provided for Unicode support.
- Codepoint Semantics
- Return Values for SQL Semantics on LOBs
- LENGTH Return Value for LOBs

**Parent topic:** SQL Semantics and LOBs

#### 7.2.1 About SQL Functions and Operators for LOBs

This list summarizes those categories of SQL functions and operators that are supported for use with LOBs. Details on individual functions and operators are given in Table 7-1.

- Concatenation

- Comparison

  (Some comparison functions are not supported for use with LOBs.)

- Character functions

- Conversion

  (Some conversion functions are not supported for use with LOBs.)

The following categories of functions are not supported for use with LOBs:

- Aggregate functions

  Note that although pre-defined aggregate functions are not supported for use with LOBs, you can create user-defined aggregate functions to use with LOBs.

- Unicode functions

Details on individual functions and operators are in Table 7-1, which lists SQL operators and functions that take `VARCHAR2` types as operands or arguments, or return a `VARCHAR2` value. The SQL column identifies the functions and operators that are supported for `CLOB` and `NCLOB` data types. (The `LENGTH` function is also supported for the `BLOB` data type.)

The `DBMS_LOB` PL/SQL package supplied with Oracle Database supports using LOBs with most of the functions listed in Table 7-1 as indicated in the PL/SQL column.

**Note:**

Operators and functions with No indicated in the SQL column of Table 7-1 do not work in SQL queries used in PL/SQL blocks - even though some of these operators and functions are supported for use directly in PL/SQL code.

**See Also:**

[Oracle Database Data Cartridge Developer's Guide](../addci/using-user-defined-aggregate-functions.md) for more information about user-defined aggregate functions

**Parent topic:** SQL Functions and Operators Supported for Use with LOBs

#### 7.2.2 Implicit Conversion of CLOB to CHAR Types

Functions designated as CNV in the SQL or PL/SQL column of Table 7-1 are performed by converting the `CLOB` to a character data type, such as `VARCHAR2`. In the SQL environment, only the first 4K bytes of the `CLOB` are converted and used in the operation; in the PL/SQL environment, only the first 32K bytes of the `CLOB` are converted and used in the operation.

Table 7-1 SQL VARCHAR2 Functions and Operators on LOBs

| Category                                  | Operator / Function                           | SQL Example / Comments                                                                                                                                                                                                                                                                                                                                                                                                                                                    | SQL | PL/SQL |
|:------------------------------------------|:----------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----|:-------|
| Concatenation                             | `||`, `CONCAT()`                              | `Select clobCol || clobCol2 from tab;`                                                                                                                                                                                                                                                                                                                                                                                                                                    | Yes | Yes    |
| Comparison                                | `= `, `!=`, `>`, `>=`, `<`, `<=`, `<>`, ` ^=` | `if clobCol=clobCol2 then...`                                                                                                                                                                                                                                                                                                                                                                                                                                             | No  | Yes    |
| Comparison                                | `IN`, `NOT` `IN`                              | `if clobCol NOT IN (clob1, clob2, clob3) then...`                                                                                                                                                                                                                                                                                                                                                                                                                         | No  | Yes    |
| Comparison                                | `SOME`, `ANY`, `ALL`                          | `if clobCol < SOME (select clobCol2 from...) then...`                                                                                                                                                                                                                                                                                                                                                                                                                     | No  | N/A    |
| Comparison                                | `BETWEEN`                                     | `if clobCol BETWEEN clobCol2 and clobCol3 then...`                                                                                                                                                                                                                                                                                                                                                                                                                        | No  | Yes    |
| Comparison                                | `LIKE [ESCAPE]`                               | `if clobCol LIKE '%pattern%' then...`                                                                                                                                                                                                                                                                                                                                                                                                                                     | Yes | Yes    |
| Comparison                                | `IS [NOT] NULL`                               | `where clobCol IS NOT NULL `                                                                                                                                                                                                                                                                                                                                                                                                                                              | Yes | Yes    |
| Character Functions                       | `INITCAP`, `NLS_INITCAP`                      | `select INITCAP(clobCol) from...`                                                                                                                                                                                                                                                                                                                                                                                                                                         | CNV | CNV    |
| Character Functions                       | `LOWER`, `NLS_LOWER`, `UPPER`, `NLS_UPPER`    | `...where LOWER(clobCol1) = LOWER(clobCol2)`                                                                                                                                                                                                                                                                                                                                                                                                                              | Yes | Yes    |
| Character Functions                       | `LPAD`, `RPAD`                                | `select RPAD(clobCol, 20, ' La') from...`                                                                                                                                                                                                                                                                                                                                                                                                                                 | Yes | Yes    |
| Character Functions                       | `TRIM`, `LTRIM`, `RTRIM`                      | `...where RTRIM(LTRIM(clobCol,'ab'), 'xy') = 'cd'`                                                                                                                                                                                                                                                                                                                                                                                                                        | Yes | Yes    |
| Character Functions                       | `REPLACE`                                     | `select REPLACE(clobCol, 'orig','new') from...`                                                                                                                                                                                                                                                                                                                                                                                                                           | Yes | Yes    |
| Character Functions                       | `SOUNDEX`                                     | `...where SOUNDEX(clobCOl) = SOUNDEX('SMYTHE')`                                                                                                                                                                                                                                                                                                                                                                                                                           | CNV | CNV    |
| Character Functions                       | `SUBSTR`                                      | `...where substr(clobCol, 1,4) = like 'THIS'`                                                                                                                                                                                                                                                                                                                                                                                                                             | Yes | Yes    |
| Character Functions                       | `TRANSLATE`                                   | `select TRANSLATE(clobCol, '123abc','NC') from...`                                                                                                                                                                                                                                                                                                                                                                                                                        | CNV | CNV    |
| Character Functions                       | `ASCII`                                       | `select ASCII(clobCol) from...`                                                                                                                                                                                                                                                                                                                                                                                                                                           | CNV | CNV    |
| Character Functions                       | `INSTR`                                       | `...where instr(clobCol, 'book') = 11`                                                                                                                                                                                                                                                                                                                                                                                                                                    | Yes | Yes    |
| Character Functions                       | `LENGTH`                                      | `...where length(clobCol) != 7;`                                                                                                                                                                                                                                                                                                                                                                                                                                          | Yes | Yes    |
| Character Functions                       | `NLSSORT`                                     | `...where NLSSORT (clobCol,'NLS_SORT = German') > NLSSORT ('S','NLS_SORT = German')`                                                                                                                                                                                                                                                                                                                                                                                      | CNV | CNV    |
| Character Functions                       | `INSTRB`, `SUBSTRB`, `LENGTHB`                | These functions are supported only for `CLOB`s that use single-byte character sets. (`LENGTHB` is supported for `BLOB`s and `CLOB`s.)                                                                                                                                                                                                                                                                                                                                     | Yes | Yes    |
| Character Functions - Regular Expressions | `REGEXP_LIKE`                                 | This function searches a character column for a pattern. Use this function in the `WHERE` clause of a query to return rows matching the regular expression you specify.<br>**See Also:**<br>• [Oracle Database SQL Language Reference](../sqlrf/Pattern-matching-Conditions.md) for syntax details on SQL functions for regular expressions.<br>• [Oracle Database Development Guide](../adfns/regexp.md) for information on using regular expressions with the database. | Yes | Yes    |
| Character Functions - Regular Expressions | `REGEXP_REPLACE`                              | This function searches for a pattern in a character column and replaces each occurrence of that pattern with the pattern you specify.                                                                                                                                                                                                                                                                                                                                     | Yes | Yes    |
| Character Functions - Regular Expressions | `REGEXP_INSTR `                               | This function searches a string for a given occurrence of a regular expression pattern. You specify which occurrence you want to find and the start position to search from. This function returns an integer indicating the position in the string where the match is found.                                                                                                                                                                                             | Yes | Yes    |
| Character Functions - Regular Expressions | `REGEXP_SUBSTR`                               | This function returns the actual substring matching the regular expression pattern you specify.                                                                                                                                                                                                                                                                                                                                                                           | Yes | Yes    |
| Conversion                                | `CHARTOROWID`                                 | `CHARTOROWID(clobCol)`                                                                                                                                                                                                                                                                                                                                                                                                                                                    | CNV | CNV    |
| Conversion                                | `COMPOSE`                                     | `COMPOSE('string')`<br>Returns a Unicode string given a string in the data type `CHAR`, `VARCHAR2`, `CLOB`, `NCHAR`, `NVARCHAR2`, `NCLOB`. An o code point qualified by an umlaut code point is returned as the o-umlaut code point.                                                                                                                                                                                                                                      | CNV | CNV    |
| Conversion                                | `DECOMPOSE`                                   | `DECOMPOSE('str' [CANONICAL | COMPATIBILITY] )`<br>Valid for Unicode character arguments. Returns a Unicode string after decomposition in the same character set as the input. o-umlaut code point is returned as the o code point followed by the umlaut code point.                                                                                                                                                                                                     | CNV | CNV    |
| Conversion                                | `HEXTORAW`                                    | `HEXTORAW(CLOB)`                                                                                                                                                                                                                                                                                                                                                                                                                                                          | No  | CNV    |
| Conversion                                | `CONVERT`                                     | `select CONVERT(clobCol,'WE8DEC','WE8HP') from...`                                                                                                                                                                                                                                                                                                                                                                                                                        | Yes | CNV    |
| Conversion                                | `TO_DATE`                                     | `TO_DATE(clobCol)`                                                                                                                                                                                                                                                                                                                                                                                                                                                        | CNV | CNV    |
| Conversion                                | `TO_NUMBER`                                   | `TO_NUMBER(clobCol)`                                                                                                                                                                                                                                                                                                                                                                                                                                                      | CNV | CNV    |
| Conversion                                | `TO_TIMESTAMP`                                | `TO_TIMESTAMP(clobCol)`                                                                                                                                                                                                                                                                                                                                                                                                                                                   | No  | CNV    |
| Conversion                                | `TO_MULTI_BYTE`<br>`TO_SINGLE_BYTE`           | `TO_MULTI_BYTE(clobCol)`<br>`TO_SINGLE_BYTE(clobCol)`                                                                                                                                                                                                                                                                                                                                                                                                                     | CNV | CNV    |
| Conversion                                | `TO_CHAR`                                     | `TO_CHAR(clobCol)`                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Yes | Yes    |
| Conversion                                | `TO_NCHAR`                                    | `TO_NCHAR(clobCol)`                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Yes | Yes    |
| Conversion                                | `TO_LOB`                                      | `INSERT INTO... SELECT TO_LOB(longCol)...`<br>Note that `TO_LOB` can only be used to create or insert into a table with LOB columns as `SELECT` `FROM` a table with a `LONG` column.                                                                                                                                                                                                                                                                                      | N/A | N/A    |
| Conversion                                | `TO_CLOB`                                     | `TO_CLOB(varchar2Col)`                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Yes | Yes    |
| Conversion                                | `TO_NCLOB`                                    | `TO_NCLOB(varchar2Clob)`                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Yes | Yes    |
| Aggregate Functions                       | `COUNT`                                       | `select count(clobCol) from...`                                                                                                                                                                                                                                                                                                                                                                                                                                           | No  | N/A    |
| Aggregate Functions                       | `MAX`, `MIN`                                  | `select MAX(clobCol) from...`                                                                                                                                                                                                                                                                                                                                                                                                                                             | No  | N/A    |
| Aggregate Functions                       | `GROUPING`                                    | `select grouping(clobCol) from... group by cube (clobCol);`                                                                                                                                                                                                                                                                                                                                                                                                               | No  | N/A    |
| Other Functions                           | `GREATEST`, `LEAST`                           | `select GREATEST (clobCol1, clobCol2) from...`                                                                                                                                                                                                                                                                                                                                                                                                                            | No  | CNV    |
| Other Functions                           | `DECODE`                                      | `select DECODE(clobCol, condition1, value1, defaultValue) from...`                                                                                                                                                                                                                                                                                                                                                                                                        | CNV | CNV    |
| Other Functions                           | `NVL`                                         | `select NVL(clobCol,'NULL') from...`                                                                                                                                                                                                                                                                                                                                                                                                                                      | Yes | Yes    |
| Other Functions                           | `DUMP`                                        | `select DUMP(clobCol) from...`                                                                                                                                                                                                                                                                                                                                                                                                                                            | No  | N/A    |
| Other Functions                           | `VSIZE`                                       | `select VSIZE(clobCol) from...`                                                                                                                                                                                                                                                                                                                                                                                                                                           | No  | N/A    |
| Unicode                                   | `INSTR2`, `SUBSTR2`, `LENGTH2`, `LIKE2`       | These functions use UCS2 code point semantics.                                                                                                                                                                                                                                                                                                                                                                                                                            | No  | CNV    |
| Unicode                                   | `INSTR4`, `SUBSTR4`, `LENGTH4`, `LIKE4`       | These functions use UCS4 code point semantics.                                                                                                                                                                                                                                                                                                                                                                                                                            | No  | CNV    |
| Unicode                                   | `INSTRC`, `SUBSTRC`, `LENGTHC`, `LIKEC`       | These functions use complete character semantics.                                                                                                                                                                                                                                                                                                                                                                                                                         | No  | CNV    |

**Parent topic:** SQL Functions and Operators Supported for Use with LOBs

#### 7.2.3 CLOBs and NCLOBs Do Not Follow Session Collation Settings

Standard operators that operate on `CLOB`s and `NCLOB`s without first converting them to `VARCHAR2` or `NVARCHAR2`, (those marked Yes in the SQL or PL/SQL columns of Table 7-1), do not behave linguistically, except for `REGEXP` functions. Binary comparison of the character data is performed irrespective of the `NLS_COMP` and `NLS_SORT` parameter settings.

These `REGEXP` functions are the exceptions, where, if `CLOB` or `NCLOB` data is passed in, the linguistic comparison is similar to the comparison of `VARCHAR2` and `NVARCHAR2` values.

- `REGEXP_LIKE`

- `REGEXP_REPLACE`

- `REGEXP_INSTR`

- `REGEXP_SUBSTR`

- `REGEXP_COUNT`

**Note:**

CLOBs and NCLOBs support the default USING NLS_COMP option.

**See Also:**

[Oracle Database Reference](../refrn/PLSQL_OPTIMIZE_LEVEL.md) for more information about `NLS_COMP`

**Parent topic:** SQL Functions and Operators Supported for Use with LOBs

#### 7.2.4 UNICODE Support

Variations on certain functions are provided for Unicode support.

Variations on the `INSTR`, `SUBSTR`, `LENGTH`, and `LIKE` functions are provided for Unicode support. (These variations are indicated as Unicode in the Category column of Table 7-1.)

**See Also:**

- [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md)

- [Oracle Database Development Guide](../adfns/fundamentals.md)

- [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md)

  [Oracle Database PL/SQL Packages and Types Reference](../arpls/introduction-to-oracle-supplied-plsql-packages-and-types.md)for a detailed description on the usage of UNICODE functions

**Parent topic:** SQL Functions and Operators Supported for Use with LOBs

#### 7.2.5 Codepoint Semantics

Codepoint semantics of the `INSTR`, `SUBSTR`, `LENGTH`, and `LIKE` functions, described in Table 7-1, differ depending on the data type of the argument passed to the function. These functions use different codepoint semantics depending on whether the argument is a `VARCHAR2` or a `CLOB` type as follows:

- When the argument is a `CLOB`, UCS2 codepoint semantics are used for all character sets.

- When the argument is a character type, such as `VARCHAR2`, the default codepoint semantics are used for the given character set:

  - UCS2 codepoint semantics are used for AL16UTF16 and UTF8 character sets.

  - UCS4 codepoint semantics are used for all other character sets, such as AL32UTF8.

- If you are storing character data in a `CLOB` or `NCLOB`, then note that the amount and offset parameters for any APIs that read or write data to the `CLOB` or `NCLOB` are specified in UCS2 codepoints. In some character sets, a full character consists one or more UCS2 codepoints called a surrogate pair. In this scenario, you must ensure that the amount or offset you specify does not cut into a full character. This avoids reading or writing a partial character.

- Oracle Database helps to detect half surrogate pair on read or write boundaries in case of SQL functions and in case of read/write through LOB APIs. The behavior is as follows:
  - If the starting offset is in the middle of a surrogate pair, an error is raised for both read and write operations.

  - If the read amount reads only a partial character, increment or decrement the amount by 1 to read complete characters.

    **Note:**

    The output amount may vary from the input amount.

  - If the write amount overwrites a partial character, an error is raised to prevent the corruption of existing data caused by overwriting of a partial character in the destination `CLOB` or `NCLOB`.

    **Note:**

    This check only applies to the existing data in the CLOB or NCLOB. You must make sure that the incoming buffer for the write operation starts and ends in complete characters.

**Parent topic:** SQL Functions and Operators Supported for Use with LOBs

#### 7.2.6 Return Values for SQL Semantics on LOBs

The return type of a function or operator that takes a LOB or `VARCHAR2` is the same as the data type of the argument passed to the function or operator.

Functions that take more than one argument, such as `CONCAT`, return a LOB data type if one or more arguments is a LOB. For example, `CONCAT(CLOB, VARCHAR2)` returns a `CLOB`.

**See Also:**

[Oracle Database SQL Language Reference ](../sqlrf/CONCAT.md)for details on the CONCAT function and the concatenation operator (\|\|).

A LOB instance is always accessed and manipulated through a LOB locator. This is also true for return values: SQL functions and operators return a LOB locator when the return value is a LOB instance.

Any LOB instance returned by a SQL function is a temporary LOB instance. LOB instances in tables (persistent LOBs) are not modified by SQL functions, even when the function is used in the `SELECT` list of a query.

**Parent topic:** SQL Functions and Operators Supported for Use with LOBs

#### 7.2.7 LENGTH Return Value for LOBs

The return value of the `LENGTH` function differs depending on whether the argument passed is a LOB or a character string:

- If the input is a character string of length zero, then `LENGTH` returns `NULL`.

- For a `CLOB` of length zero, or an empty locator such as that returned by `EMPTY_CLOB()`, the `LENGTH` and `DBMS_LOB.GETLENGTH` functions return 0.

**Parent topic:** SQL Functions and Operators Supported for Use with LOBs

### 7.3 Implicit Conversion of LOB Data Types in SQL

Some LOB data types support implicit conversion and can be used in operations such as cross-type assignment and parameter passing. These conversions are processed at the SQL layer and can be performed in all client interfaces that use LOB types.

- Implicit Conversion Between CLOB and NCLOB Data Types in SQL

**Parent topic:** SQL Semantics and LOBs

#### 7.3.1 Implicit Conversion Between CLOB and NCLOB Data Types in SQL

The database enables you to perform operations such as cross-type assignment and cross-type parameter passing between `CLOB` and `NCLOB` data types. The database performs implicit conversions between these types when necessary to preserve properties such as character set formatting.

Note that, when implicit conversions occur, each character in the source LOB is changed to the character set of the destination LOB, if needed. In this situation, some degradation of performance may occur if the data size is large. When the character set of the destination and the source are the same, there is no degradation of performance.

After an implicit conversion between `CLOB` and `NCLOB` types, the destination LOB is implicitly created as a temporary LOB. This new temporary LOB is independent from the source LOB. If the implicit conversion occurs as part of a define operation in a `SELECT` statement, then any modifications to the destination LOB do not affect the persistent LOB in the table that the LOB was selected from as shown in the following example:

    SQL> -- check lob length before update
    SQL> select dbms_lob.getlength(ad_sourcetext) from Print_media
      2       where product_id=3106 and ad_id = 13001;

    DBMS_LOB.GETLENGTH(AD_SOURCETEXT)
    ---------------------------------
             205

    SQL>
    SQL> declare
      2   clob1 clob;
      3   amt number:=10;
      4  BEGIN
      5    -- select a clob column into a clob, no implicit convesion
      6    SELECT ad_sourcetext INTO clob1 FROM Print_media
      7      WHERE product_id=3106 and ad_id=13001 FOR UPDATE;
      8
      9    dbms_lob.trim(clob1, amt); -- Trim the selected lob to 10 bytes
     10  END;
     11  /

    PL/SQL procedure successfully completed.

    SQL> -- Modification is performed on clob1 which points to the
    SQL> -- clob column in the table
    SQL> select dbms_lob.getlength(ad_sourcetext) from Print_media
      2       where product_id=3106 and ad_id = 13001;

    DBMS_LOB.GETLENGTH(AD_SOURCETEXT)
    ---------------------------------
              10

    SQL>
    SQL> rollback;

    Rollback complete.

    SQL> -- check lob length before update
    SQL> select dbms_lob.getlength(ad_sourcetext) from Print_media
      2       where product_id=3106 and ad_id = 13001;

    DBMS_LOB.GETLENGTH(AD_SOURCETEXT)
    ---------------------------------
             205

    SQL>
    SQL> declare
      2   nclob1 nclob;
      3   amt number:=10;
      4  BEGIN
      5
      6    -- select a clob column into a nclob, implicit conversion occurs
      7    SELECT ad_sourcetext INTO nclob1 FROM Print_media
      8      WHERE product_id=3106 and ad_id=13001 FOR UPDATE;
      9
     10    dbms_lob.trim(nclob1, amt); -- Trim the selected lob to 10 bytes
     11  END;
     12  /

    PL/SQL procedure successfully completed.

    SQL> -- Modification to nclob1 does not affect the clob in the table,
    SQL> -- because nclob1 is a independent temporary LOB

    SQL> select dbms_lob.getlength(ad_sourcetext) from Print_media
      2       where product_id=3106 and ad_id = 13001;

    DBMS_LOB.GETLENGTH(AD_SOURCETEXT)
    ---------------------------------
             205


**See Also:**

- "[Implicit Conversions Between CLOB and VARCHAR2](PLSQL-semantics-for-LOBs.md)" for information on PL/SQL semantics support for implicit conversions between `CLOB` and `VARCHAR2` types.

- "[Converting Character Sets Implicitly with LOBs](LOB-storage-with-applications.md)" for more information on implicit character set conversions when loading LOBs from `BILE`s.

- [Oracle Database SQL Language Reference](../sqlrf/Data-Type-Comparison-Rules.md) for details on implicit conversions supported for all data types.

**Parent topic:** Implicit Conversion of LOB Data Types in SQL

### 7.4 Unsupported Use of LOBs in SQL

Table 7-2 lists SQL operations that are not supported on LOB columns.

Table 7-2 Unsupported Usage of LOBs in SQL

| SQL Operations Not Supported                                               | Example of unsupported usage                                 |
|:---------------------------------------------------------------------------|:-------------------------------------------------------------|
| `SELECT` `DISTINCT`                                                        | `SELECT DISTINCT clobCol from...`                            |
| `SELECT` clause<br>`ORDER BY`                                              | `SELECT...` `ORDER BY clobCol`                               |
| `SELECT` clause<br>`GROUP` `BY`                                            | `SELECT avg(num) FROM... `<br>`GROUP BY clobCol`             |
| `UNION`, `INTERSECT`, `MINUS`<br>(Note that `UNION` `ALL` works for LOBs.) | `SELECT clobCol1 from tab1 UNION SELECT clobCol2 from tab2;` |
| Join queries                                                               | `SELECT... FROM... WHERE tab1.clobCol = tab2.clobCol`        |
| Index columns                                                              | `CREATE INDEX clobIndx ON tab(clobCol)...`                   |

**Parent topic:** SQL Semantics and LOBs

### 7.5 VARCHAR2 and RAW Semantics for LOBs

Semantics used with `VARCHAR2` and `RAW` data types also apply to LOBs.

- About VARCHAR2 and RAW Semantics for LOBs
- LOBs Returned from SQL Functions
- IS NULL and IS NOT NULL Usage with VARCHAR2s and CLOBs
- WHERE Clause Usage with LOBs

**Parent topic:** SQL Semantics and LOBs

#### 7.5.1 About VARCHAR2 and RAW Semantics for LOBs

These semantics, used with `VARCHAR2` and `RAW` data types, also apply to LOBs:

- Defining a `CHAR` buffer on a `CLOB`

  You can define a `VARCHAR2` for a `CLOB` and `RAW` for a `BLOB` column. You can also define `CLOB` and `BLOB` types for `VARCHAR2` and `RAW` columns.

- Selecting a `CLOB` column into a `CHAR` buffer or `VARCHAR2`

  If a `CLOB` column is selected into a `VARCHAR2` variable, then data stored in the `CLOB` column is retrieved and put into the `CHAR` buffer. If the buffer is not large enough to contain all the `CLOB` data, then a truncation error is thrown and no data is written to the buffer. After successful completion of the `SELECT` operation, the `VARCHAR2` variable holds as a regular character buffer.

  In contrast, when a `CLOB` column is selected into a local `CLOB` variable, the `CLOB` locator is fetched.

- Selecting a `BLOB` column into a `RAW`

  When a `BLOB` column is selected into a `RAW` variable, the `BLOB` data is copied into the `RAW` buffer. If the size of the `BLOB` exceeds the size of the buffer, then a truncation error is thrown and no data is written to the buffer.

**Parent topic:** VARCHAR2 and RAW Semantics for LOBs

#### 7.5.2 LOBs Returned from SQL Functions

When a LOB is returned from a SQL function, the result returned is a temporary LOB.

Your application should view the temporary LOB as local storage for the data returned from the `SELECT` operation as follows:

- In PL/SQL, the temporary LOB has the same lifetime (duration) as other local PL/SQL program variables. It can be passed to subsequent SQL or PL/SQL `VARCHAR2` functions or queries as a PL/SQL local variable. The temporary LOB goes out of scope at the end of the program block at which time, the LOB is freed. These are the same semantics as those for PL/SQL `VARCHAR2` variables. At any time, nonetheless, you can use a `DBMS_LOB.FREETEMPORARY()` call to release the resources taken by the local temporary LOBs.

  **Note:**

  If the SQL statement returns a LOB or a LOB is an `OUT` parameter for a PL/SQL function or procedure, you must test if it is a temporary LOB, and if it is, then free it after you are done with it.

- In OCI, the temporary LOBs returned from SQL queries are always in session duration, unless a user-defined duration is present, in which case, the temporary LOBs are in the user-defined duration.

  **WARNING:**

  Ensure that your temporary tablespace is large enough to store all temporary LOB results returned from queries in your program(s).

The following example illustrates selecting out a `CLOB` column into a `VARCHAR2` and returning the result as a `CHAR` buffer of declared size:

    DECLARE
      vc1 VARCHAR2(32000);
      lb1 CLOB;
      lb2 CLOB;
    BEGIN
      SELECT clobCol1 INTO vc1 FROM tab WHERE colID=1;
      -- lb1 is a temporary LOB
      SELECT clobCol2 || clobCol3 INTO lb1 FROM tab WHERE colID=2;

      lb2 := vc1|| lb1;
      -- lb2 is a still temporary LOB, so the persistent data in the database
      -- is not modified. An update is necessary to modify the table data.
      UPDATE tab SET clobCol1 = lb2 WHERE colID = 1;

    DBMS_LOB.FREETEMPORARY(lb2); -- Free up the space taken by lb2

    <... some more queries ...>

    END; -- at the end of the block, lb1 is automatically freed

**Parent topic:** VARCHAR2 and RAW Semantics for LOBs

#### 7.5.3 IS NULL and IS NOT NULL Usage with VARCHAR2s and CLOBs

You can use the `IS NULL` and `IS NOT NULL` operators with LOB columns.

When used with LOBs, the `IS NULL` and `IS NOT NULL` operators determine whether a LOB locator is stored in the row.

**Note:**

In the SQL 92 standard, a character string of length zero is distinct from a `NULL` string. The return value of IS `NULL` differs when you pass a LOB compared to a `VARCHAR2`:

- When you pass an initialized LOB of length zero to the `IS NULL` function, zero (`FALSE`) is returned. These semantics are compliant with the SQL standard.

- When you pass a `VARCHAR2` of length zero to the `IS NULL` function, `TRUE` is returned.

**Parent topic:** VARCHAR2 and RAW Semantics for LOBs

#### 7.5.4 WHERE Clause Usage with LOBs

SQL functions with LOBs as arguments, except functions that compare LOB values, are allowed in predicates of the `WHERE` clause.

The `LENGTH` function, for example, can be included in the predicate of the `WHERE` clause:

    CREATE TABLE t (n NUMBER, c CLOB);
    INSERT INTO t VALUES (1, 'abc');

    SELECT * FROM t WHERE c IS NOT NULL;
    SELECT * FROM t WHERE LENGTH(c) > 0;
    SELECT * FROM t WHERE c LIKE '%a%';
    SELECT * FROM t WHERE SUBSTR(c, 1, 2) LIKE '%b%';
    SELECT * FROM t WHERE INSTR(c, 'b') = 2;

**Parent topic:** VARCHAR2 and RAW Semantics for LOBs

### 7.6 Built-in Functions for Remote LOBs and BFILEs

**See Also:**

[Built-in Functions for Remote LOBs and BFILEs](distributed-LOBs.md) for more information about built-in functions and user-defined functions supported on remote `LOB`s and `BFILE`s

**Parent topic:** SQL Semantics and LOBs
