Consider datatype support in Oracle, and conversion between Oracle and DRDA datatypes.

### 7.1 Overview of Datatype Conversion

DRDA utilizes Formatted Data Object Content Architecture (FD:OCA) for datatype encoding. Several types do not have a direct analog to Oracle native types, and require conversion. Also, some Oracle datatypes have no direct encoding support in FD:OCA.For example, consider Oracle `NUMBER`, which may contain a wide range of values, both integers and floating point. This duality prevents it from being mapped to a specific DRDA type, to mitigate loss of value of the number. Any choice of type will have some loss of either precision or scale at extreme ranges of value.

There are two datatype conversions used by Oracle Database Provider for DRDA: conversion of DRDA MetaData Descriptors to Oracle OCI interface types, and conversion of Oracle column types to DRDA MetaData Descriptors. For application programmers, these are described through the SQL Type of the bind variable or described column type. See sections “Conversion between DRDA Datatypes to Oracle Datatypes” and “Conversion of Oracle Datatype to DRDA.”

A general mechanism for mapping Oracle `NUMBER` is covered in section “Datatype Equivalence and Remapping”.

**Related Topics**

- Conversion between DRDA Datatypes to Oracle Datatypes
- Conversion of Oracle Datatype to DRDA
- Datatype Equivalence and Remapping

### 7.2 Numerical Range Considerations; General

When converting between Oracle `NUMBER`, IEEE floating point, IBM Hexadecimal floating point (HEX floating point, S390 or System390 floating point), and Decimal floating point (`DECFLOAT`) datatypes, note that they have different ranges and capabilities. For example, all values of `IBM HEX FLOAT` bind variables in a client-side program fit in an Oracle `NUMBER`, but not all values of Oracle `NUMBER` may be returned correctly in an `IBM HEX FLOAT`; `DECFLOAT34` is a better choice.

Some other considerations include the following:

- Infinities. Some floating point types support positive and negative infinities.

  When infinities are used for datatypes that don't support them, the highest possible number for positive infinities and its negative for negative infinities is used.

- Floating Point. IEEE `FLOAT` columns may be defined in Oracle with types of `BINARY_FLOAT` and `BINARY_DOUBLE`. In DB2 z/OS the floating point types (`REAL`, `FLOAT`, `DOUBLE` and `DOUBLE PRECISION`) are IBM HEX floating point. In DB2/400 and DB2 LUW, the floating point types (`REAL`, `FLOAT`, `DOUBLE` and `DOUBLE PRECISION`) are IEEE floating point.

- Not a Number. Some datatypes support Not A Number (NAN), a special value to indicate either that no value was assigned, or the result of a computation is invalid or undefined.

#### 7.2.1 Oracle NUMBER

Oracle `NUMBER` has the following characteristics:

##### Lower Range

1E-130

##### Upper Range

9.999 999 999 999 999 999 999 999 999 999 999 999 9E+125

##### Infinity

Supported for both negative and positive infinity

##### Not A Number

Not supported

#### 7.2.2 FLOAT (IBM HEX or S390)

The following characteristics apply to `FLOAT`, `DOUBLE` and `LONG DOUBLE` sub datatypes.

##### Lower Range

5.397605 x 10<sup>-79</sup>

##### Upper Range

7.237005 x 10<sup>+75</sup>

##### Infinity

Not supported

##### Not A Number

Not supported

#### 7.2.3 FLOAT (IEEE)

The following characteristics apply to `FLOAT `(Oracle `BINARY_FLOAT`), `DOUBLE` (Oracle `BINARY_DOUBLE`), and `LONG DOUBLE` sub datatypes.

##### Infinity

Supported for both positive and negative infinity

##### Not A Number

Supported

The bounds for the subtypes follow:

##### Lower Range

`FLOAT` (Oracle `BINARY_FLOAT`): 1.175 494 x 10<sup>-38</sup>

`DOUBLE` (Oracle `BINARY_DOUBLE`): 2.225 074 x 10<sup>-308</sup>

`LONG DOUBLE`: 3.362 103 x 10<sup>-4932</sup>

##### Upper Range

`FLOAT `(Oracle `BINARY_FLOAT`): 3.402 823 x 10<sup>+38</sup>

`DOUBLE` (Oracle `BINARY_DOUBLE`): 1.797 693 x 10<sup>+308</sup>

`LONG DOUBLE`: 1.189 731 x 10<sup>+4932</sup>

#### 7.2.4 DECFLOAT

The following characteristics apply to `DECFLOAT7`, `DECFLOAT16`, and `DECFLOAT34` sub datatypes.

##### Infinity

Supported for both positive and negative infinity

##### Not A Number

Supported

The bounds for the subtypes follow:

##### Lower Range

`DECFLOAT7`: 0.000 001 x 10<sup>-95</sup>

`DECFLOAT16`: 0.000 000 000 000 001 x 10<sup>-383</sup>

`DECFLOAT34`: 0.000 000 000 000 000 000 000 000 000 000 001 x 10<sup>-6143</sup>

##### Upper Range

`DECFLOAT7`: 9.999 999 x 10<sup>+96</sup>

`DECFLOAT16`: 9.999 999 999 999 999 x 10<sup>+384</sup>

`DECFLOAT34`: 9.999 999 999 999 999 999 999 999 999 999 999 x 10<sup>+6144</sup>

### 7.3 Numerical Range Considerations, for COBOL Users

DRDA databases offer three options for integer types: `SMALLINT` (2 binary bytes), `INTEGER` (4 binary bytes), and `BIGINT` (8 binary bytes). During conversion, Oracle columns that hold equivalent values must be defined based on usage rather than on the type used in the DB2 `CREATE TABLE` definition.

The actual range of DRDA `SMALLINT`, `INTEGER` and `BIGINT` follows:

- `SMALLINT` has a lower bound of `-32,768` and an upper bound of `32,767`

- `INTEGER` has a lower bound of `-2,147,483,648` and an upper bound of `2,147,483,647`

- `BIGINT` has a lower bound of `-9,223,372,036,854,775,808` and an upper bound of `9,223,372,036,854,775,807`

However, at the level of the application, the COBOL variables that hold these DRDA column values may be declared either with a fixed number of decimal digits, or with the full binary precision of the corresponding DRDA integer datatypes.

In COBOL, the equivalent binary integer datatypes are defined as follows:

- `USAGE` of `BINARY`, `COMPUTATIONAL`, `COMP`, `COMPUTATIONAL-4`, and `COMP-4`; these are equivalent

- `PICTURE` of `S9(1-4)` for a 2-byte integer, `S9(5-9)` for a 4-byte integer, and `S9(10-18)` for an 8-byte integer.

The value is normally limited to the number of digits in the picture.

For example `PICTURE S9(4) COMP` is a 2-byte integer that normally ranges from `-32,768` to `+32,767`. However, the generated COBOL code only allows the value to range from `-9,999` to `+9,999`. When using these types of bind variables exclusively to access and update DRDA `SMALLINT`, `INTEGER`, and `BIGINT` columns, define the columns in Oracle as `NUMBER(``n``)`, where `n` matches the above `PICTURE S9(``n``)` definition.

When using `BINARY`, `COMPUTATIONAL`, `COMP`, `COMPUTATIONAL-4`, and `COMP-4` COBOL variables with the `TRUNC(BIN)` COBOL compiler option, the binary integers may range to the full bounds of the datatype. Using `COMPUTATIONAL-5` or `COMP-5` has the same effect, regardless whether the `TRUNC` compiler option is in effect. When programming in COBOL, C, PL/I, or Assembler with a full range of the binary integers, define the Oracle column as `NUMBER(``n``+1)`, where `n` matches the above `PICTURE S9(``n``)` definition.

Based on datatype and usage in DRDA, here are the recommended substitute Oracle datatypes:

#### Used with COBOL COMP:

- `SMALLINT` should be converted to Oracle `NUMBER(4)`

- `INTEGER` should be converted to Oracle `NUMBER(9)`

- `BIGINT` should be converted to Oracle `NUMBER(18)`

#### Used with COBOL COMP, TRUNC(BIN), COMP-5, C, PL/I, or Assembler binary integer variables:

- `SMALLINT` should be converted to Oracle `NUMBER(5)`

- `INTEGER` should be converted to Oracle `NUMBER(10)`

- `BIGINT` should be converted to Oracle `NUMBER(19)`

#### 7.3.1 Constraining Oracle NUMBER

When using the full range of binary integer values, it is advisable to implement Oracle constraints and limit the value to the range of the corresponding datatype.

For example, a DRDA `SMALLINT` gets an equivalent Oracle `NUMBER` column that supports a full range of `SMALLINT` values, only, as demonstrated in Example 7-1.

Note however that there is a performance penalty for specifying this type of check constraint, Oracle verifies all constraints every time the column is updated.

Example 7-1 Constraining Oracle NUMBER to Exactly Match DRDA SMALLINT

    CREATE TABLE smint_tab
      (smint NUMBER(5)
             CONSTRAINT check_smallint CHECK (smint BETWEEN -32768 AND 32767)
      )

### 7.4 Conversion between DRDA Datatypes to Oracle Datatypes

Consider the mappings between DRDA and Oracle datatypes.

Note the following abbreviations:

- In a Single Byte Character Set (SBCS), the column can only contain single byte data.

- In a Multi-Byte Character Set (MBCS), the column may contain a combination of single-byte and multi-byte characters.

#### 7.4.1 INTEGER

4-byte binary number

##### SQL Type

496, 497

##### Size

4 bytes

##### Oracle Type

`NUMBER(10)`

#### 7.4.2 SMALLINT

2-byte binary number

##### SQL Type

500, 501

##### Size

2 bytes

##### Oracle Type

`NUMBER(5)`

#### 7.4.3 BIGINT

8-byte binary number

##### SQL Type

492, 493

##### Size

8 bytes

##### Oracle Type

`NUMBER(19)`

#### 7.4.4 float

long double-precision (16 bytes)

##### SQL Type

480, 481

##### Range

`54≤ b≤126`

##### Oracle Type

`NUMBER`

#### 7.4.5 DOUBLE PRECISION or FLOAT(b)

double-precision (8 bytes)

##### SQL Type

480, 481

##### Range

`22≤ b≤ 53`

##### Oracle Type

`BINARY_DOUBLE`

#### 7.4.6 REAL or FLOAT(b)

Single-precision (4 bytes)

##### SQL Type

480, 481

##### Range

`1≤b≤21`

##### Oracle Type

`BINARY_FLOAT`

#### 7.4.7 DECIMAL(p,s)

precision and scale packed decimal

##### SQL Type

484, 485

##### Range

`1≤p≤31`, `1≤s≤31`

##### Oracle Type

`NUMBER(p,s)`

#### 7.4.8 DECIMAL(p,s) zoned

precision and scale zoned decimal

##### SQL Type

488, 489

##### Range

`1≤p≤31`, `1≤s≤31`

##### Oracle Type

`NUMBER(p,s)`

#### 7.4.9 NUMERIC(p,s)

precision and scale character decimal

##### SQL Type

504, 505

##### Range

`1≤p≤31`, `1≤s≤31`

##### Oracle Type

`NUMBER(p,s)`

#### 7.4.10 DECFLOAT(n=34)

precision and scale, with exponent; subject to loss

##### SQL Type

996, 997

##### Range

n=34

##### Oracle Type

`NUMBER`

#### 7.4.11 DECFLOAT(n=16)

precision and scale, with exponent; subject to loss

##### SQL Type

996, 997

##### Range

n=16

##### Oracle Type

`NUMBER`

#### 7.4.12 CHAR(n)

sbcs and mixed

##### SQL Type

452,453

##### Range

1≤ n≤255

##### Oracle Type

`CHAR`

#### 7.4.13 CHAR(n) for Bit Data

byte

##### SQL Type

452,453

##### Range

1≤ n≤255

##### Oracle Type

`RAW`

#### 7.4.14 VARCHAR(n)

sbcs

##### SQL Type

448,449

##### Oracle Type

VARCHAR2

#### 7.4.15 VARCHAR(n)

mixed

##### SQL Type

448,449

##### Oracle Type

`VARCHAR2`

#### 7.4.16 VARCHAR(n) for Bit Data

byte

##### SQL Type

448,449

##### Range

1≤ n≤2000

##### Oracle Type

`RAW`

#### 7.4.17 VARCHAR(n)

sbcs

##### SQL Type

456,457

##### Range

1≤ n≤32767

##### Oracle Type

`LONG`

#### 7.4.18 VARCHAR(n)

mixed

##### SQL Type

456,457

##### Range

1≤ n≤32767

##### Oracle Type

`LONG`

#### 7.4.19 VARCHAR(n) for Bit Data

byte

##### SQL Type

456,457

##### Range

1≤ n≤32767

##### Oracle Type

`LONG RAW`

#### 7.4.20 char(n+1)

sbcs

##### SQL Type

460,461

##### Range

1≤ n≤4000

##### Oracle Type

`CHAR`

#### 7.4.21 char(n+1)

mixed

##### SQL Type

460,461

##### Range

1≤ n≤2000

##### Oracle Type

`CHAR`

#### 7.4.22 char(n) for Bit Data

byte

##### SQL Type

460,461

##### Range

1≤ n≤2000

##### Oracle Type

`RAW`

#### 7.4.23 VARGRAPHIC(n)

dbcs

##### SQL Type

464,465

##### Range

1≤ n≤2000

##### Oracle Type

`NVARCHAR2`

#### 7.4.24 GRAPHIC(n)

dbcs

##### SQL Type

468,469

##### Range

1≤ n≤127

##### Oracle Type

`NCHAR`

#### 7.4.25 VARGRAPHIC(n)

dbcs

##### SQL Type

472,473

##### Range

1≤ n≤2000

##### Oracle Type

`NVARCHAR2`

#### 7.4.26 char(n) (Pascal L String)

byte

##### SQL Type

476,477

##### Range

1≤ n≤255

##### Oracle Type

`CHAR`

#### 7.4.27 char(n) for Bit Data (Pascal L String)

byte

##### SQL Type

476,477

##### Range

1≤ n≤255

##### Oracle Type

`RAW`

#### 7.4.28 DATE

Date with zero time component

##### SQL Type

384, 385

##### Oracle Type

`DATE`

#### 7.4.29 TIME

Uses time component of date only, or is formatted as textual time representation

##### SQL Type

388, 389

##### Oracle Type

`DATE` or `CHAR(8)`

#### 7.4.30 TIMESTAMP

Timestamp

##### SQL Type

392, 393

##### Oracle Type

`TIMESTAMP(6)`

#### 7.4.31 (datalink)

no equivalent representation

##### SQL Type

396, 397

##### Oracle Type

`VARCHAR2` for sbcs, or `NVARCHAR2` for dbcs

#### 7.4.32 BLOB

Binary Long OBject

##### SQL Type

404, 405

##### Oracle Type

`BLOB`

#### 7.4.33 CLOB

Character Long OBject (LOB) for sbcs or mixed representation

##### SQL Type

408, 409

##### Oracle Type

`CLOB` for sbcs, and `CLOB` for mixed representation

#### 7.4.34 DBCLOB

For dbcs

##### SQL Type

412, 413

##### Oracle Type

`NCLOB`

#### 7.4.35 BLOB LOCATOR

Binary Long OBject (LOB)

##### SQL Type

960, 961

##### Oracle Type

`BLOB`

#### 7.4.36 CLOB LOCATOR

For sbcs or mixed representation

##### SQL Type

964, 965

##### Oracle Type

`CLOB`

#### 7.4.37 DBCLOB LOCATOR

For dbcs representation

##### SQL Type

968, 969

##### Oracle Type

`NCLOB`

#### 7.4.38 boolean

No equivalent representation

##### SQL Type

2436, 2437

##### Oracle Type

`NUMBER(5)`

#### 7.4.39 BINARY(n)

Fixed-length binary string

##### SQL Type

912, 913

##### Range

1 ≤ n ≤ 255

##### Oracle Type

`RAW`

#### 7.4.40 VARBINARY(n)

Variable-length binary string

##### SQL Type

908, 909

##### Range

1 ≤ n ≤ 32767

##### Oracle Type

`LONG RAW`

#### 7.4.41 XML

External form

##### SQL Type

988, 989

##### Oracle Type

`SYS.XMLType`

### 7.5 Conversion of Oracle Datatype to DRDA

Tables and procedures use Oracle datatypes. When describing objects, or returning data from a table or procedure, Oracle maps Oracle datatypes onto equivalent DRDA datatypes.

#### 7.5.1 BINARY_FLOAT

8 bytes

##### SQL Type

480, 481

##### SQL Type Name

`DOUBLE` (8 byte floating point)

#### 7.5.2 BINARY_DOUBLE

8 bytes

##### SQL Type

480, 481

##### SQL Type Name

`DOUBLE` (8 byte floating point)

#### 7.5.3 VARCHAR2(n)

mixed variable length character string

##### SQL Type

448, 449

##### Range

1 ≤ n ≤ 32,767

##### SQL Type Name

`VARCHAR(n) FOR MIXED DATA`

#### 7.5.4 LONG

Mixed long variable-length character string; Oracle `LONG` supports up to 2^31-1 bytes, but only the first `32,767` bytes are currently returned.

##### SQL Type

448, 449

##### SQL Type Name

`VARCHAR(32767) FOR MIXED DATA`

#### 7.5.5 LONG RAW

Binary long variable length character string; Oracle `LONG RAW` supports up to 2^31-1 bytes, but only the first `32,767` bytes are currently returned.

##### SQL Type

448, 449

##### SQL Type Name

`VARCHAR(32767) FOR BIT DATA`

#### 7.5.6 NVARCHAR2(n)

National variable length character string

##### SQL Type

464, 465

##### Range

1 ≤ n ≤ 32,767

##### SQL Type Name

`VARGRAPHIC(n)`

#### 7.5.7 CHAR(n)

Mixed fixed length character string; there are two possibilities, determined by the range necessary for the datatype: converts to `CHAR(n)` for n under `256`, and to `VARCHAR(n)` for longer character strings.

##### 7.5.7.1 Shorter version

##### SQL Type

452, 453

##### Range

`1 ≤ n ≤ 255`

##### SQL Type Name

`CHAR(n) FOR MIXED DATA`

##### 7.5.7.2 Longer Version

##### SQL Type

448, 449

##### Range

`256 ≤ n ≤ 32,767`

##### SQL Type Name

`VARCHAR(n) FOR MIXED DATA`

#### 7.5.8 NCHAR(n)

National fixed length character string; there are two possibilities, determined by the range necessary for the datatype: converts to `CHAR(n)` for n under `256`, and to `VARCHAR(n)` for longer character strings.

##### 7.5.8.1 Shorter version

##### SQL Type

468, 469

##### Range

`1 ≤ n ≤ 255`

##### SQL Type Name

`GRAPHIC(n)`

##### 7.5.8.2 Longer Version

##### SQL Type

464, 465

##### Range

`256 ≤ n ≤ 32,767`

##### SQL Type Name

`VARGRAPHIC(n)`

#### 7.5.9 UROWID

Oracle universal `ROWID`

##### SQL Type

908, 909

##### SQL Type Name

`VARBINARY(4000)`

#### 7.5.10 DATE

Oracle `DATE`

##### SQL Type

384, 385

##### SQL Type Name

`DATE`

#### 7.5.11 TIMESTAMP

Oracle `TIMESTAMP`

##### SQL Type

392, 393

##### SQL Type Name

`TIMESTAMP`

#### 7.5.12 TIMESTAMP WITH LOCAL TIME ZONE

Oracle `TIMESTAMP WITH LOCAL TIME ZONE`

##### SQL Type

392, 393

##### SQL Type Name

`TIMESTAMP`

#### 7.5.13 TIMESTAMP(p) WITH TIME ZONE

Oracle `TIMESTAMP WITH LOCAL TIME ZONE`

##### SQL Type

448, 449

##### Range

`0 ≤ p ≤ 9`

##### SQL Type Name

`VARCHAR(n) FOR MIXED DATA`

`n=148` for `TIMESTAMP(0) WITH TIME ZONE`; otherwise, `149+p` for `TIMESTAMP(p)` `WITH TIME ZONE`

#### 7.5.14 RAW(n)

Binary variable length string

##### SQL Type

908, 909

##### Range

`1 ≤ n ≤ 2000`

##### SQL Type Name

`VARBINARY(n)`

#### 7.5.15 NUMBER and FLOAT

Oracle `NUMBER` and `FLOAT` may be used to represent several numeric types:

- simple integer types with only a decimal precision

- fixed-point decimal types with a specific precision and scale

- floating point types with up to `38` decimal digits of precision and an exponent

Additionally, `NUMBER` may be defined with a scale that is greater than precision, with negative scale, and as a `FLOAT` with binary precision. See Table 7-1 and Table 7-2 for details.

Note that the general form of this datatype is `NUMBER(``p``,``s``)`, where `p` is the variable for precision and `s` is the variable for scale.

Table 7-1 Converting Oracle NUMBER Variants to DRDA Datatypes

| Oracle Variant of NUMBER(p,s)                 | DRDA Datatype    | Notes                                                                                                                                                    |
|:----------------------------------------------|:-----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NUMBER(1)`                                   | `DECIMAL(1)`     |                                                                                                                                                          |
| `NUMBER(2-4)`                                 | `SMALLINT`       |                                                                                                                                                          |
| `NUMBER(5-9`)                                 | `INTEGER`        |                                                                                                                                                          |
| `NUMBER(10-18)`                               | `BIGINT`         | Whenever the client does not support `BIGINT`, the mapping is made to `DECIMAL(n)`                                                                       |
| `NUMBER(19-31)`                               | `DECIMAL(``p``)` |                                                                                                                                                          |
| `NUMBER(1-31, 1-31)`                          | `DECIMAL(p,s)`   | For both datatypes, `scale <= precision`                                                                                                                 |
| `NUMBER(32-38)`                               | `DECFLOAT34`     | Whenever the client does not support `DECFLOAT`, the mapping is made to `DOUBLE.`<br>Oracle `NUMBER(35-38)` is rounded to `34` digits during conversion. |
| `NUMBER(1-38, -s)`<br>where scale is negative | `DECFLOAT34`     | Whenever the client does not support `DECFLOAT`, the mapping is made to `DOUBLE`.<br>Oracle `NUMBER(35-38)` is rounded to `34` digits during conversion. |
| `NUMBER(1-38, s)`<br>where scale \> precision | `DECFLOAT34`     | Whenever the client does not support `DECFLOAT`, the mapping is made to `DOUBLE`.<br>Oracle `NUMBER(35-38)` is rounded to `34` digits during conversion. |
| `NUMBER(32-38, s)`<br>with any scale          | `DECFLOAT34`     | Whenever the client does not support `DECFLOAT`, the mapping is made to `DOUBLE`.<br>Oracle `NUMBER(35-38)` is rounded to `34` digits during conversion. |
| `NUMBER`                                      | `DECFLOAT34`     | Whenever the client does not support `DECFLOAT`, the mapping is made to `DOUBLE`                                                                         |

Table 7-2 Converting Oracle FLOAT Variants to DRDA Datatypes

| Oracle Variant of FLOAT(n)   | DRDA Datatype | Notes                                                                            |
|:-----------------------------|:--------------|:---------------------------------------------------------------------------------|
| `FLOAT(1-53)`                | `DECFLOAT16`  | Whenever the client does not support `DECFLOAT`, the mapping is made to `DOUBLE` |
| `FLOAT(n)`<br>where `n > 53` | `DECFLOAT34`  | Whenever the client does not support `DECFLOAT`, the mapping is made to `DOUBLE` |
| `FLOAT`                      | `DECFLOAT34`  | Whenever the client does not support `DECFLOAT`, the mapping is made to `DOUBLE` |

### 7.6 Datatype Equivalence and Remapping

Oracle does not provide discrete database datatypes such as `SMALLINT`, `INTEGER` or `BIGINT` DRDA datatypes. In some cases, often to limit the column's range of values, it may become necessary to define a numeric column with specific precision or scale. Oracle therefore supplies a more flexible numeric database datatype, Oracle `NUMBER`, which may be defined by specified precision and scale. Oracle `NUMBER` may contain both integral and fractional values in the same column, if no specific range limitations have been defined for the column.

Consideration, therefore, must be made for appropriate database datatypes when migrating data from a non-Oracle database. This is particularly important when migrating applications that expect to handle data of a limited range or form.

For example, if the application accepts a data range specific to `NUMBER(5)`, but the column is defined by datatype `NUMBER`, it is likely that an inappropriate or invalid values may be inserted into the column and causing data issues when using or retrieving that value.

If the table definition is mapped to a close approximation of the original non-Oracle data, there should be no datatype compatibility issues. However, in cases where data that was not modeled accurately must be accessed, or if a query uses an expression that yields a non-range limited datatype, it may become necessary to apply an alternate datatype that is more compatible.

Consider that the `COUNT(*)` expression results in a non-range limited Oracle `NUMBER` datatype. If the application expects the result of the query that uses `COUNT` to be represented as a DRDA `INTEGER` datatype, it becomes necessary perform one of the following steps to avoid a type mis-match:

- change the application to use the Oracle `NUMBER`

- change the query expression to `CAST` the result to the appropriate form

- remap the resulting datatype form

Often, it is neither practical nor feasible to modify the application, and remapping the datatype is the only workable solution.

The Application Server has a limited facility to convert Oracle `NUMBER` datatype results to more discrete equivalent DRDA datatypes, on a per table or per column basis. This mechanism may also be used when the client AR is unable to properly convert the default mappings of Oracle `NUMBER` to DRDA datatype. See “Conversion of Oracle Datatype to DRDA” for all supported conversions.

**Related Topics**

- Conversion of Oracle Datatype to DRDA

#### 7.6.1 Applying Datatype Mapping

To apply datatype mappings, you must invoke the PL/SQL function. Refer the section on “`SET_TYPEMAP`.” The procedure `SET_TYPEMAP` implements a specified type conversion map for a specified table and column expression. The syntax for the type map object name is `table_name``:``column_expression`. The wildcard character, `*`, may be used in place of table name to include all tables with the specified column expression. It may also be used to indicate that all column expressions for a specified table that evaluate to an Oracle `NUMBER` be type mapped.

The syntax for converting from Oracle `NUMBER` to another datatype is `NUMBER=``datatype`. See Oracle `NUMBER TYPEMAP` Datatype Names for available datatype names.

The default mapping of Oracle `NUMBER` is to DRDA `DECFLOAT(34)`. “Using `TYPEMAP` in Queries that Use the Column Directly” shows that queries that use a column directly may use re-mapping on the retrieved column as a DRDA type `INTEGER`. When using a column in a function it may be necessary to apply a `typemap` for the expression, as described in “Using `TYPEMAP` in a function”.

**Related Topics**

- Using TYPEMAP in Queries

#### 7.6.2 Using TYPEMAP in Queries

Assume that an application expects an `EMPLOYEE_ID` value to be in a format of DRDA type `INTEGER`.

Example 7-2 Using TYPEMAP in Queries that Use the Column Directly

    CREATE TABLE employees(employee_id NUMBER(6), first_name VARCHAR2(20), ...);

This mapping enforces range limitations. To facilitate this mapping, apply the following `typemap` entry for the applications package `ORACLE.MYPACKAGE`:

    begin
       dbms_drdaas.set_typemap (
          'ORACLE', 'MYPACKAGE', 'EMPLOYEES:EMPLOYEE_ID',
          'NUMBER=INTEGER');
    end;

#### 7.6.3 Using TYPEMAP in Functions

When using the `COUNT` function against the column, as in

Example 7-3 Using TYPEMAP in a Function

    SELECT COUNT(employee_id) FROM employees;

apply the following `typemap` expression:

    begin
      dbms_drdaas.set_typemap (
        'ORACLE', 'MYPACKAGE', 'EMPLOYEES:COUNT(EMPLOYEE_ID)',
        'NUMBER=INTEGER' );
    end;

#### 7.6.4 Oracle NUMBER TYPEMAP

Table 7-3 lists available `typemap` names and their conversion to DRDA datatypes.

Table 7-3 Oracle NUMBER TYPEMAP Datatype Names

| Datatype Name | SQL Type  | Datatype Size | Notes                           |
|:--------------|:----------|:--------------|:--------------------------------|
| `SMALLINT`    | 500, 501  | `2` bytes     | small integer                   |
| `INTEGER`     | 496, 497  | `4` bytes     | integer                         |
| `BIGINT`      | 492, 493  | `8` bytes     | large integer                   |
| `FLOAT`       | 480\. 481 | `4` bytes     | single-precision floating point |
| `DOUBLE`      | 480, 481  | `8` bytes     | double-precision floating point |
