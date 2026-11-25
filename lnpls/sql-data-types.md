## 3.1 SQL Data Types

The PL/SQL data types include the SQL data types.

For information about the SQL data types, see [Oracle Database SQL Language Reference](../sqlrf/Basic-Elements-of-Oracle-SQL.md)—all information there about data types and subtypes, data type comparison rules, data conversion, literals, and format models applies to both SQL and PL/SQL, except as noted here:

- Different Maximum Sizes

- Additional PL/SQL Constants for BINARY_FLOAT and BINARY_DOUBLE

- Additional PL/SQL Subtypes of BINARY_FLOAT and BINARY_DOUBLE

Unlike SQL, PL/SQL lets you declare variables, to which the following topics apply:

- CHAR and VARCHAR2 Variables

- LONG and LONG RAW Variables

- ROWID and UROWID Variables

### 3.1.1 Different Maximum Sizes

The SQL data types listed in Table 3-1 have different maximum sizes in PL/SQL and SQL.

Table 3-1 Data Types with Different Maximum Sizes in PL/SQL and SQL

| Data Type                     | Maximum Size in PL/SQL | Maximum Size in SQL                 |
|:------------------------------|:-----------------------|:------------------------------------|
| `CHAR`<sup>Foot 1</sup>       | 32,767 bytes           | 2,000 bytes                         |
| `NCHAR`<sup>Foot 1</sup>      | 32,767 bytes           | 2,000 bytes                         |
| `RAW`<sup>Foot 1</sup>        | 32,767 bytes           | 2,000 bytes<sup>Foot 2</sup>        |
| `VARCHAR2`<sup>Foot 1</sup>   | 32,767 bytes           | 4,000 bytes<sup>Foot 2</sup>        |
| `NVARCHAR2`<sup>Foot 1</sup>  | 32,767 bytes           | 4,000 bytes<sup>Foot 2</sup>        |
| `LONG`<sup>Foot 3</sup>       | 32,760 bytes           | 2 gigabytes (GB) - 1                |
| `LONG` `RAW`<sup>Foot 3</sup> | 32,760 bytes           | 2 GB                                |
| `BLOB`                        | 128 terabytes (TB)     | (4 GB - 1) \* `database_block_size` |
| `CLOB`                        | 128 TB                 | (4 GB - 1) \* `database_block_size` |
| `NCLOB`                       | 128 TB                 | (4 GB - 1) \* `database_block_size` |

<sup>Footnote 1</sup>

When specifying the maximum size of a value of this data type in PL/SQL, use an integer literal (not a constant or variable) whose value is in the range from 1 through 32,767.

<sup>Footnote 2</sup>

To eliminate this size difference, follow the instructions in [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md).

<sup>Footnote 3</sup>

Supported only for backward compatibility with existing applications.

### 3.1.2 Additional PL/SQL Constants for BINARY_FLOAT and BINARY_DOUBLE

The SQL data types `BINARY_FLOAT` and `BINARY_DOUBLE` represent single-precision and double-precision IEEE 754-format floating-point numbers, respectively.

`BINARY_FLOAT` and `BINARY_DOUBLE` computations do not raise exceptions, so you must check the values that they produce for conditions such as overflow and underflow by comparing them to predefined constants (for examples, see [Oracle Database SQL Language Reference](../sqlrf/Literals.md)). PL/SQL has more of these constants than SQL does.

Table 3-2 lists and describes the predefined PL/SQL constants for `BINARY_FLOAT` and `BINARY_DOUBLE`, and identifies those that SQL also defines.

Table 3-2 Predefined PL/SQL BINARY_FLOAT and BINARY_DOUBLE Constants

| Constant                      | Description                                                                     |
|:------------------------------|:--------------------------------------------------------------------------------|
| `BINARY_FLOAT_NAN` (\*)       | `BINARY_FLOAT` value for which the condition `IS` `NAN` (not a number) is true  |
| `BINARY_FLOAT_INFINITY` (\*)  | Single-precision positive infinity                                              |
| `BINARY_FLOAT_MAX_NORMAL`     | Maximum normal `BINARY_FLOAT` value                                             |
| `BINARY_FLOAT_MIN_NORMAL`     | Minimum normal `BINARY_FLOAT` value                                             |
| `BINARY_FLOAT_MAX_SUBNORMAL`  | Maximum subnormal `BINARY_FLOAT` value                                          |
| `BINARY_FLOAT_MIN_SUBNORMAL`  | Minimum subnormal `BINARY_FLOAT` value                                          |
| `BINARY_DOUBLE_NAN` (\*)      | `BINARY_DOUBLE` value for which the condition `IS` `NAN` (not a number) is true |
| `BINARY_DOUBLE_INFINITY` (\*) | Double-precision positive infinity                                              |
| `BINARY_DOUBLE_MAX_NORMAL`    | Maximum normal `BINARY_DOUBLE` value                                            |
| `BINARY_DOUBLE_MIN_NORMAL`    | Minimum normal `BINARY_DOUBLE` value                                            |
| `BINARY_DOUBLE_MAX_SUBNORMAL` | Maximum subnormal `BINARY_DOUBLE` value                                         |
| `BINARY_DOUBLE_MIN_SUBNORMAL` | Minimum subnormal `BINARY_DOUBLE` value                                         |

(\*) SQL also predefines this constant.

### 3.1.3 Additional PL/SQL Subtypes of BINARY_FLOAT and BINARY_DOUBLE

PL/SQL predefines these subtypes:

- `SIMPLE_FLOAT`, a subtype of SQL data type `BINARY_FLOAT`

- `SIMPLE_DOUBLE`, a subtype of SQL data type `BINARY_DOUBLE`

Each subtype has the same range as its base type and has a `NOT` `NULL` constraint (explained in "[NOT NULL Constraint](declarations.md)").

If you know that a variable will never have the value `NULL`, declare it as `SIMPLE_FLOAT` or `SIMPLE_DOUBLE`, rather than `BINARY_FLOAT` or `BINARY_DOUBLE`. Without the overhead of checking for nullness, the subtypes provide significantly better performance than their base types. The performance improvement is greater with `PLSQL_CODE_TYPE='NATIVE'` than with `PLSQL_CODE_TYPE='INTERPRETED'` (for more information, see "[Use Data Types that Use Hardware Arithmetic](minimizing-cpu-overhead.md)").

### 3.1.4 CHAR and VARCHAR2 Variables

#### Topics

- Assigning or Inserting Too-Long Values

- Declaring Variables for Multibyte Characters

- Differences Between CHAR and VARCHAR2 Data Types

#### 3.1.4.1 Assigning or Inserting Too-Long Values

If the value that you assign to a character variable is longer than the maximum size of the variable, an error occurs. For example:

    DECLARE
      c VARCHAR2(3 CHAR);
    BEGIN
      c := 'abc  ';
    END;
    /

Result:

    DECLARE
    *
    ERROR at line 1:
    ORA-06502: PL/SQL: numeric or value error: character string buffer too small
    ORA-06512: at line 4

Similarly, if you insert a character variable into a column, and the value of the variable is longer than the defined width of the column, an error occurs. For example:

    DROP TABLE t;
    CREATE TABLE t (c CHAR(3 CHAR));

    DECLARE
      s VARCHAR2(5 CHAR) := 'abc  ';
    BEGIN
      INSERT INTO t(c) VALUES(s);
    END;
    /

Result:

    BEGIN
    *
    ERROR at line 1:
    ORA-12899: value too large for column "HR"."T"."C" (actual: 5, maximum: 3)
    ORA-06512: at line 4

To strip trailing blanks from a character value before assigning it to a variable or inserting it into a column, use the `RTRIM` function, explained in [Oracle Database SQL Language Reference](../sqlrf/RTRIM.md). For example:

    DECLARE
      c VARCHAR2(3 CHAR);
    BEGIN
      c := RTRIM('abc  ');
      INSERT INTO t(c) VALUES(RTRIM('abc  '));
    END;
    /

Result:

    PL/SQL procedure successfully completed.

#### 3.1.4.2 Declaring Variables for Multibyte Characters

The maximum size of a `CHAR` or `VARCHAR2` variable is 32,767 bytes, whether you specify the maximum size in characters or bytes. The maximum number of characters in the variable depends on the character set type and sometimes on the characters themselves:

| Character Set Type                                                                                                            | Maximum Number of Characters                                                                                                                                                                  |
|:------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Single-byte character set                                                                                                     | 32,767                                                                                                                                                                                        |
| n-byte fixed-width multibyte character set (for example, AL16UTF16)                                                           | `FLOOR(32,767/``n``)`                                                                                                                                                                         |
| n-byte variable-width multibyte character set with character widths between 1 and n bytes (for example, JA16SJIS or AL32UTF8) | Depends on characters themselves—can be anything from 32,767 (for a string containing only 1-byte characters) through `FLOOR(32,767/``n``)` (for a string containing only n-byte characters). |

When declaring a `CHAR` or `VARCHAR2` variable, to ensure that it can always hold n characters in any multibyte character set, declare its length in characters—that is, `CHAR(``n` `CHAR)` or `VARCHAR2(``n` `CHAR)`, where n does not exceed `FLOOR(32767/4)` = 8191.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md) for information about Oracle Database character set support

#### 3.1.4.3 Differences Between CHAR and VARCHAR2 Data Types

`CHAR` and `VARCHAR2` data types differ in:

- Predefined Subtypes

- How Blank-Padding Works

- Value Comparisons

##### 3.1.4.3.1 Predefined Subtypes

The `CHAR` data type has one predefined subtype in both PL/SQL and SQL—`CHARACTER`.

The `VARCHAR2` data type has one predefined subtype in both PL/SQL and SQL, `VARCHAR`, and an additional predefined subtype in PL/SQL, `STRING`.

Each subtype has the same range of values as its base type.

**Note:**

In a future PL/SQL release, to accommodate emerging SQL standards, `VARCHAR` might become a separate data type, no longer synonymous with `VARCHAR2`.

##### 3.1.4.3.2 How Blank-Padding Works

This explains the differences and considerations of using blank-padding with CHAR and VARCHAR2.

Consider these situations:

- The value that you assign to a variable is shorter than the maximum size of the variable.

- The value that you insert into a column is shorter than the defined width of the column.

- The value that you retrieve from a column into a variable is shorter than the maximum size of the variable.

If the data type of the receiver is `CHAR`, PL/SQL blank-pads the value to the maximum size. Information about trailing blanks in the original value is lost.

If the data type of the receiver is `VARCHAR2`, PL/SQL neither blank-pads the value nor strips trailing blanks. Character values are assigned intact, and no information is lost.

Example 3-1 CHAR and VARCHAR2 Blank-Padding Difference

In this example, both the `CHAR` variable and the `VARCHAR2` variable have the maximum size of 10 characters. Each variable receives a five-character value with one trailing blank. The value assigned to the `CHAR` variable is blank-padded to 10 characters, and you cannot tell that one of the six trailing blanks in the resulting value was in the original value. The value assigned to the `VARCHAR2` variable is not changed, and you can see that it has one trailing blank.

    DECLARE
      first_name  CHAR(10 CHAR);
      last_name   VARCHAR2(10 CHAR);
    BEGIN
      first_name := 'John ';
      last_name  := 'Chen ';

      DBMS_OUTPUT.PUT_LINE('*' || first_name || '*');
      DBMS_OUTPUT.PUT_LINE('*' || last_name || '*');
    END;
    /

Result:

    *John      *
    *Chen *

##### 3.1.4.3.3 Value Comparisons

The SQL rules for comparing character values apply to PL/SQL character variables.

Whenever one or both values in the comparison have the data type `VARCHAR2` or `NVARCHAR2`, nonpadded comparison semantics apply; otherwise, blank-padded semantics apply. For more information, see [Oracle Database SQL Language Reference](../sqlrf/Data-Type-Comparison-Rules.md).

### 3.1.5 LONG and LONG RAW Variables

**Note:**

Oracle supports the `LONG` and `LONG` `RAW` data types only for backward compatibility with existing applications. For new applications:

- Instead of `LONG`, use `VARCHAR2(32760)`, `BLOB`, `CLOB` or `NCLOB`.

- Instead of `LONG` `RAW`, use `BLOB`.

You can insert any `LONG` value into a `LONG` column. You can insert any `LONG` `RAW` value into a `LONG` `RAW` column. You cannot retrieve a value longer than 32,760 bytes from a `LONG` or `LONG` `RAW` column into a `LONG` or `LONG` `RAW` variable.

You can insert any `CHAR` or `VARCHAR2` value into a `LONG` column. You cannot retrieve a value longer than 32,767 bytes from a `LONG` column into a `CHAR` or `VARCHAR2` variable.

You can insert any `RAW` value into a `LONG` `RAW` column. You cannot retrieve a value longer than 32,767 bytes from a `LONG` `RAW` column into a `RAW` variable.

**See Also:**

"[Trigger LONG and LONG RAW Data Type Restrictions](trigger-restrictions.md)" for restrictions on `LONG` and `LONG` `RAW` data types in triggers

### 3.1.6 ROWID and UROWID Variables

When you retrieve a rowid into a `ROWID` variable, use the `ROWIDTOCHAR` function to convert the binary value to a character value. For information about this function, see [Oracle Database SQL Language Reference](../sqlrf/ROWIDTOCHAR.md).

To convert the value of a `ROWID` variable to a rowid, use the `CHARTOROWID` function, explained in [Oracle Database SQL Language Reference](../sqlrf/CHARTOROWID.md). If the value does not represent a valid rowid, PL/SQL raises the predefined exception `SYS_INVALID_ROWID`.

To retrieve a rowid into a `UROWID` variable, or to convert the value of a `UROWID` variable to a rowid, use an assignment statement; conversion is implicit.

**Note:**

- `UROWID` is a more versatile data type than `ROWID`, because it is compatible with both logical and physical rowids.

- When you update a row in a table compressed with Hybrid Columnar Compression (HCC), the `ROWID` of the row changes. HCC, a feature of certain Oracle storage systems, is described in [Oracle Database Concepts](../cncpt/tables-and-table-clusters.md).

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ROWID.md) for information about the `DBMS_ROWID` package, whose subprograms let you create and return information about `ROWID` values (but not `UROWID` values)
