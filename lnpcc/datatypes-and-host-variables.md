This chapter provides the basic information you need to write a Pro\*C/C++ program. This chapter contains the following topics:

- Oracle Datatypes

- Host Variables

- Indicator Variables

- VARCHAR Variables

- Cursor Variables

- CONTEXT Variables

- Universal ROWIDs

- Host Structures

- Pointer Variables

- Globalization Support

- NCHAR Variables

This chapter also includes several complete demonstration programs that you can study. These programs illustrate the techniques described. They are available on-line in your `demo` directory, so you can compile and run them, and modify them for your own uses.

### 4.1 Oracle Datatypes

Oracle recognizes two kinds of datatypes: internal and external. Internal datatypes specify how Oracle stores column values in database tables, as well as the formats used to represent pseudocolumn values such as NULL, SYSDATE, USER, and so on. External datatypes specify the formats used to store values in input and output host variables.

**Related Topics**

- [Oracle Built-in Data Types](../sqlrf/Data-Types.md)

#### 4.1.1 Internal Datatypes

For values stored in database columns, Oracle uses the internal datatypes shown in Table 4-1

Table 4-1 Oracle Internal Datatypes

| Name                       | Description                                                                                             |
|:---------------------------|:--------------------------------------------------------------------------------------------------------|
| VARCHAR2                   | Variable-length character string, \<= 4000 bytes.                                                       |
| NVARCHAR2 or NCHAR VARYING | Variable-length single-byte or National Character string,\<= 4000 bytes.                                |
| NUMBER                     | Numeric value having precision and scale, represented in a base-100 format.                             |
| LONG                       | Variable-length character string \<=2\*\*31-1 bytes.                                                    |
| BINARY_FLOAT               | 32-bit floating point number, 4 bytes.                                                                  |
| BINARY_DOUBLE              | 64-bit floating point number, 8 bytes.                                                                  |
| TIMESTAMP                  | Year, month, and day values of date, as well as hour, minute, and second values of time, 7 or 11 bytes. |
| DATE                       | Fixed-length date + time value, 7 bytes.                                                                |
| INTERVAL YEAR              | Stores a period of time in years and months, 5 bytes.                                                   |
| INTERVAL DAY               | Stores a period of time in days, hours, minutes, and seconds, 11 bytes.                                 |
| RAW                        | Variable-length binary data, \<=2000 bytes.                                                             |
| LONG RAW                   | Variable-length binary data, \<=2\*\*31-1 bytes.                                                        |
| ROWID                      | Binary value.                                                                                           |
| UROWID                     | Binary value, \<=4000 bytes.                                                                            |
| CHAR                       | Fixed-length character string, \<=2000 bytes.                                                           |
| NCHAR                      | Fixed-length single-byte or National Character string, \<= 2000 bytes.                                  |
| CLOB                       | Character data, \<= 4 Gbytes.                                                                           |
| NCLOB                      | National Character Set data, \<= 4 Gbytes.                                                              |
| BLOB                       | Binary data, \<= 4 Gbytes.                                                                              |
| BFILE                      | External file binary data, \<= 4 Gbytes.                                                                |

These internal datatypes can be quite different from C datatypes. For example, C has no datatype that is equivalent to the Oracle NUMBER datatype. However, NUMBERs can be converted between C datatypes such as float and double, with some restrictions. For example, the Oracle NUMBER datatype allows up to 38 decimal digits of precision, while no current C implementations can represent double with that degree of precision.

The Oracle NUMBER datatype represents values exactly (within the precision limits), while floating-point formats cannot represent values such as 10.0 exactly.

Use the LOB datatypes to store unstructured data (text, graphic images, video clips, or sound waveforms). BFILE data is stored in an operating system file outside the database. LOB types store locators that specify the location of the data.

NCHAR and NVARCHAR2 are used to store multibyte character data.

**Related Topics**

- [LOBs](about-LOBs.md)

#### 4.1.2 External Datatypes

As shown in Table 4-2, the external datatypes include all the internal datatypes plus several datatypes that closely match C constructs. For example, the STRING external datatype refers to a C null-terminated string.

Table 4-2 Oracle External Datatypes

| Name         | Description                                                                                    |
|:-------------|:-----------------------------------------------------------------------------------------------|
| VARCHAR2     | Variable-length character string, \<= 65535 bytes.                                             |
| NUMBER       | Decimal number, represented using a base-100 format.                                           |
| INTEGER      | Signed integer.                                                                                |
| FLOAT        | Real number.                                                                                   |
| STRING       | Null-terminated variable length character string.                                              |
| VARNUM       | Decimal number, like NUMBER, but includes representation length component.                     |
| LONG         | Fixed-length character string, up to 2\*\*31-1 bytes.                                          |
| VARCHAR      | Variable-length character string, \<= 65533 bytes.                                             |
| ROWID        | Binary value, external length is system dependent.                                             |
| DATE         | Fixed-length date/time value, 7 bytes.                                                         |
| VARRAW       | Variable-length binary data, \<= 65533 bytes.                                                  |
| RAW          | Fixed-length binary data, \<= 65535 bytes.                                                     |
| LONG RAW     | Fixed-length binary data, \<= 2\*\*31-1 bytes.                                                 |
| UNSIGNED     | Unsigned integer.                                                                              |
| LONG VARCHAR | Variable-length character string, \<= 2\*\*31-5 bytes.                                         |
| LONG VARRAW  | Variable-length binary data, \<= 2\*\*31-5 bytes.                                              |
| CHAR         | Fixed-length character string, \<= 65535 bytes.                                                |
| CHARZ        | Fixed-length, null-terminated character string, \<= 65534 bytes.                               |
| CHARF        | Used in TYPE or VAR statements to force CHAR to default to CHAR, instead of VARCHAR2 or CHARZ. |

Brief descriptions of the Oracle datatypes follow.

##### 4.1.2.1 VARCHAR2

You use the VARCHAR2 datatype to store variable-length character strings. The maximum length of a VARCHAR2 value is 64K bytes.

You specify the maximum length of a VARCHAR2(n) value in bytes, not characters. So, if a VARCHAR2(n) variable stores multibyte characters, its maximum length can be less than n characters.

When you precompile using the option CHAR_MAP=VARCHAR2, Oracle assigns the VARCHAR2 datatype to all host variables that you declare as char\[n\] or char.

###### 4.1.2.1.1 On Input

Oracle reads the number of bytes specified for the input host variable, strips any trailing blanks, then stores the input value in the target database column. Be careful. An uninitialized host variable can contain NULLs. So, always blank-pad a character input host variable to its declared length, and do not null-terminate it.

If the input value is longer than the defined width of the database column, Oracle generates an error. If the input value contains nothing but blanks, Oracle treats it like a NULL.

Oracle can convert a character value to a NUMBER column value if the character value represents a valid number. Otherwise, Oracle generates an error.

###### 4.1.2.1.2 On Output

Oracle returns the number of bytes specified for the output host variable, blank-padding if necessary. It then assigns the output value to the target host variable. If a NULL is returned, Oracle fills the host variable with blanks.

If the output value is longer than the declared length of the host variable, Oracle truncates the value before assigning it to the host variable. If there is an indicator variable associated with the host variable, Oracle sets it to the original length of the output value.

Oracle can convert NUMBER column values to character values. The length of the character host variable determines precision. If the host variable is too short for the number, scientific notation is used. For example, if you SELECT the column value 123456789 into a character host variable of length 6, Oracle returns the value '1.2E08'. If a NULL is selected explicitly, the value in the host variable is indeterminate. The value of the indicator variable needs to be checked for NULL-ness.

##### 4.1.2.2 NUMBER

You use the NUMBER datatype to store fixed or floating-point numbers. You can specify precision and scale. The maximum precision of a NUMBER value is 38. The magnitude range is 1.0E-130 to 9.99...9E125 (38 nines followed by 88 zeroes). Scale can range from -84 to 127.

NUMBER values are stored in a variable-length format, starting with an exponent byte and followed by 19 mantissa bytes. The high-order bit of the exponent byte is a sign bit, which is set for positive numbers. The low-order 7 bits represent the magnitude.

The mantissa forms a 38-digit number with each byte representing 2 of the digits in a base-100 format. The sign of the mantissa is specified by the value of the first (left-most) byte. If greater than 101 then the mantissa is negative and the first digit of the mantissa is equal to the left-most byte minus 101.

On output, the host variable contains the number as represented internally by Oracle. To accommodate the largest possible number, the output host variable must be 22 bytes long. Only the bytes used to represent the number are returned. Oracle does not blank-pad or null-terminate the output value. If you need to know the length of the returned value, use the VARNUM datatype instead.

There is seldom a need to use this external datatype.

##### 4.1.2.3 INTEGER

You use the INTEGER datatype to store numbers that have no fractional part. An integer is a signed, 2-byte, 4-byte or 8-byte binary number. The order of the bytes in a word is system dependent. You must specify a length for input and output host variables. On output, if the column value is a real number, Oracle truncates any fractional part.

##### 4.1.2.4 FLOAT

You use the FLOAT datatype to store numbers that have a fractional part or that exceed the capacity of the INTEGER datatype. The number is represented using the floating-point format of your computer and typically requires 4 or 8 bytes of storage. You must specify a length for input and output host variables.

Oracle can represent numbers with greater precision than most floating-point implementations because the internal format of Oracle numbers is decimal. This can cause a loss of precision when fetching into a FLOAT variable.

##### 4.1.2.5 STRING

The STRING datatype is like the VARCHAR2 datatype, except that a STRING value is always null-terminated. When you precompile using the option CHAR_MAP=STRING, Oracle assigns the STRING datatype to all host variables that you declare as char\[n\] or char.

###### 4.1.2.5.1 On Input

Oracle uses the specified length to limit the scan for the null terminator. If a null terminator is not found, Oracle generates an error. If you do not specify a length, Oracle assumes the maximum length of 2000 bytes. The minimum length of a STRING value is 2 bytes. If the first character is a null terminator and the specified length is 2, Oracle inserts a null unless the column is defined as NOT NULL. If the column is defined as NOT NULL, an error occurs. An all-blank value is stored intact.

###### 4.1.2.5.2 On Output

Oracle appends a null byte to the last character returned. If the string length exceeds the specified length, Oracle truncates the output value and appends a null byte. If a NULL is SELECTed, Oracle returns a null byte in the first character position. If a NULL is selected explicitly, the value in the host variable is indeterminate. The value of the indicator variable needs to be checked for NULL-ness.

##### 4.1.2.6 VARNUM

The VARNUM datatype is like the NUMBER datatype, except that the first byte of a VARNUM variable stores the length of the representation.

On input, you must set the first byte of the host variable to the length of the value. On output, the host variable contains the length followed by the number as represented internally by Oracle. To accommodate the largest possible number, the host variable must be 22 bytes long. After SELECTing a column value into a VARNUM host variable, you can check the first byte to get the length of the value.

Normally, there is little reason to use this datatype.

##### 4.1.2.7 LONG

You use the LONG datatype to store fixed-length character strings.

The LONG datatype is like the VARCHAR2 datatype, except that the maximum length of a LONG value is 2147483647 bytes or two gigabytes.

##### 4.1.2.8 VARCHAR

You use the VARCHAR datatype to store variable-length character strings. VARCHAR variables have a 2-byte length field followed by a \<=65533-byte string field. However, for VARCHAR array elements, the maximum length of the string field is 65530 bytes. When you specify the length of a VARCHAR variable, be sure to include 2 bytes for the length field. For longer strings, use the LONG VARCHAR datatype. If a NULL is selected explicitly, the value in the host variable is indeterminate. The value of the indicator variable needs to be checked for NULL-ness.

##### 4.1.2.9 ROWID

Rows in Index-Organized tables do not have permanent physical addresses. The logical ROWID is accessed using the same syntax as the physical ROWID. For this reason, the physical ROWID includes a data object number (schema objects in the same segment).

To support both logical and physical ROWIDs (as well as ROWIDs of non-Oracle tables) the universal ROWID was defined.

You can use character host variables to store rowids in a readable format. When you SELECT or FETCH a rowid into a character host variable, Oracle converts the binary value to an 18-byte character string and returns it in the format

    BBBBBBBB.RRRR.FFFF

where BBBBBBBB is the block in the database file, RRRR is the row in the block (the first row is 0), and FFFF is the database file. These numbers are hexadecimal. For example, the rowid

    0000000E.000A.0007
    points to the 11th row in the 15th block in the 7th database file.

Typically, you FETCH a rowid into a character host variable, then compare the host variable to the ROWID pseudocolumn in the WHERE clause of an UPDATE or DELETE statement. That way, you can identify the latest row fetched by a cursor.

**Note:**

If you need full portability or your application communicates with a non-Oracle database using Oracle Open Gateway technology, specify a maximum length of 256 (not 18) bytes when declaring the host variable. Though you can assume nothing about the host variable's contents, the host variable will behave normally in SQL statements.

**Related Topics**

- Universal ROWIDs
- [About Mimicking CURRENT OF](host-arrays.md)

##### 4.1.2.10 DATE

You use the DATE datatype to store dates and times in 7-byte, fixed-length fields. As Table 4-3 shows, the century, year, month, day, hour (in 24-hour format), minute, and second are stored in that order from left to right.

Table 4-3 DATE Format

| Date Datatype                        | Century | Year | Month | Day | Hour | Minutes | Second |
|:-------------------------------------|:--------|:-----|:------|:----|:-----|:--------|:-------|
| Byte                                 | 1       | 2    | 3     | 4   | 5    | 6       | 7      |
| Meaning                              | Century | Year | Month | Day | Hour | Minute  | Second |
| Example<br>17-OCT-1994 at 1:23:12 PM | 119     | 194  | 10    | 17  | 14   | 24      | 13     |

The century and year bytes are in excess-100 notation. The hour, minute, and second are in excess-1 notation. Dates before the Common Era (B.C.E.) are less than 100. The epoch is January 1, 4712 B.C.E. For this date, the century byte is 53 and the year byte is 88. The hour byte ranges from 1 to 24. The minute and second bytes range from 1 to 60. The time defaults to midnight (1, 1, 1).

Normally, there is little reason to use the DATE datatype.

##### 4.1.2.11 RAW

You use the RAW datatype to store binary data or byte strings. The maximum length of a RAW value is 65535 bytes.

RAW data is like CHARACTER data, except that Oracle assumes nothing about the meaning of RAW data and does no character set conversions when you transmit RAW data from one system to another.

##### 4.1.2.12 VARRAW

You use the VARRAW datatype to store variable-length binary data or byte strings. The VARRAW datatype is like the RAW datatype, except that VARRAW variables have a 2-byte length field followed by a data field \<= 65533 bytes in length. For longer strings, use the LONG VARRAW datatype.

When you specify the length of a VARRAW variable, be sure to include 2 bytes for the length field. The first two bytes of the variable must be interpretable as an integer.

To get the length of a VARRAW variable, simply refer to its length field.

##### 4.1.2.13 LONG RAW

You use the LONG RAW datatype to store binary data or byte strings. The maximum length of a LONG RAW value is 2147483647 bytes or two gigabytes.

LONG RAW data is like LONG data, except that Oracle assumes nothing about the meaning of LONG RAW data and does no character set conversions when you transmit LONG RAW data from one system to another.

##### 4.1.2.14 UNSIGNED

You use the UNSIGNED datatype to store unsigned integers. An unsigned integer is a binary number of 2 or 4 bytes. The order of the bytes in a word is system dependent. You must specify a length for input and output host variables. On output, if the column value is a floating-point number, Oracle truncates the fractional part.

##### 4.1.2.15 LONG VARCHAR

You use the LONG VARCHAR datatype to store variable-length character strings. LONG VARCHAR variables have a 4-byte length field followed by a string field. The maximum length of the string field is 2147483643 (2\*\*31 - 5) bytes. When you specify the length of a LONG VARCHAR for use in a VAR or TYPE statement, do not include the 4 length bytes.

##### 4.1.2.16 LONG VARRAW

You use the LONG VARRAW datatype to store variable-length binary data or byte strings. LONG VARRAW variables have a 4-byte length field followed by a data field. The maximum length of the data field is 2147483643 bytes. When you specify the length of a LONG VARRAW for use in a VAR or TYPE statement, do not include the 4 length bytes.

##### 4.1.2.17 CHAR

You use the CHAR datatype to store fixed-length character strings. The maximum length of a CHAR value is 65535 bytes.

###### 4.1.2.17.1 On Input

Oracle reads the number of bytes specified for the input host variable, does not strip trailing blanks, then stores the input value in the target database column.

If the input value is longer than the defined width of the database column, Oracle generates an error. If the input value is all-blank, Oracle treats it like a character value.

###### 4.1.2.17.2 On Output

Oracle returns the number of bytes specified for the output host variable, doing blank-padding if necessary, then assigns the output value to the target host variable. If a NULL is returned, Oracle fills the host variable with blanks.

If the output value is longer than the declared length of the host variable, Oracle truncates the value before assigning it to the host variable. If an indicator variable is available, Oracle sets it to the original length of the output value. If a NULL is selected explicitly, the value in the host variable is indeterminate. The value of the indicator variable needs to be checked for NULL-ness.

##### 4.1.2.18 CHARZ

When DBMS=V7 or V8, Oracle, by default, assigns the CHARZ datatype to all character host variables in a Pro\*C/C++ program. The CHARZ datatype indicates fixed-length, null-terminated character strings. The maximum length of a CHARZ value is 65534 bytes.

###### 4.1.2.18.1 On Input

The CHARZ and STRING datatypes work the same way. You must null-terminate the input value. The null terminator serves only to delimit the string; it does not become part of the stored data.

###### 4.1.2.18.2 On Output

CHARZ host variables are blank-padded if necessary, then null-terminated. The output value is always null-terminated, even if data must be truncated. If a NULL is selected explicitly, the value in the host variable is indeterminate. The value of the indicator variable needs to be checked for NULL-ness.

##### 4.1.2.19 CHARF

The CHARF datatype is used in EXEC SQL TYPE and EXEC SQL VAR statements. When you precompile with the DBMS option set to V7 or V8, specifying the external datatype CHAR in a TYPE or VAR statement equivalences the C type or variable to the fixed-length, null-terminated datatype CHARZ.

However, you might not want either of these type equivalences, but rather an equivalence to the fixed-length external type CHAR. If you use the external type CHARF, the C type or variable is always equivalenced to the fixed-length ANSI datatype CHAR, regardless of the DBMS value. CHARF never allows the C type to be equivalenced to VARCHAR2 or CHARZ. Alternatively, when you set the option CHAR_MAP=CHARF, all host variables declared as char\[n\] or char are equivalenced to a CHAR string. If a NULL is selected explicitly, the value in the host variable is indeterminate. The value of the indicator variable needs to be checked for NULL-ness.

#### 4.1.3 Additional External Datatypes

This section describes additional external datatypes.

##### 4.1.3.1 Datetime and Interval Datatypes

The datetime and interval datatypes are briefly summarized here.

**Related Topics**

- [Oracle Database SQL Language Reference](../sqlrf/index.md)

##### 4.1.3.2 ANSI DATE

The `ANSI` `DATE` is based on the `DATE`, but contains no time portion. (Therefore, it also has no time zone.) `ANSI` `DATE` follows the `ANSI` specification for the `DATE` datatype. When assigning an `ANSI` `DATE` to a `DATE` or a timestamp datatype, the time portion of the Oracle `DATE` and the timestamp are set to zero. When assigning a `DATE` or a timestamp to an `ANSI` `DATE`, the time portion is ignored.

You are encouraged to instead use the `TIMESTAMP` datatype which contains both date and time.

##### 4.1.3.3 TIMESTAMP

The `TIMESTAMP` datatype is an extension of the `DATE` datatype. It stores the year, month, and day of the `DATE` datatype, plus the hour, minute, and second values. It has no time zone. The `TIMESTAMP` datatype has the form:

    TIMESTAMP(fractional_seconds_precision)

where `fractional_seconds_precision` (which is optional) specifies the number of digits in the fractional part of the `SECOND` datetime field and can be a number in the range 0 to 9. The default is 6.

##### 4.1.3.4 TIMESTAMP WITH TIME ZONE

`TIMESTAMP` `WITH` `TIME` `ZONE` (`TSTZ`) is a variant of `TIMESTAMP` that includes an explicit time zone displacement in its value. The time zone displacement is the difference (in hours and minutes) between local time and UTC (Coordinated Universal Time—formerly Greenwich Mean Time). The `TIMESTAMP` `WITH` `TIME` ZONE datatype has the form:

    TIMESTAMP(fractional_seconds_precision) WITH TIME ZONE

where `fractional_seconds_precision` optionally specifies the number of digits in the fractional part of the `SECOND` datetime field and can be a number in the range 0 to 9. The default is 6.

Two `TIMESTAMP` `WITH` `TIME` `ZONE` values are considered identical if they represent the same instant in UTC, regardless of the `TIME` `ZONE` offsets stored in the data.

##### 4.1.3.5 TIMESTAMP WITH LOCAL TIME ZONE

`TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` (`TSLTZ`) is another variant of `TIMESTAMP` that includes a time zone displacement in its value. Storage is in the same format as for `TIMESTAMP`. This type differs from `TIMESTAMP` `WITH` `TIME` `ZONE` in that data stored in the database is normalized to the database time zone, and the time zone displacement is not stored as part of the column data. When users retrieve the data, Oracle returns it in the users' local session time zone.

The time zone displacement is the difference (in hours and minutes) between local time and UTC (Coordinated Universal Time—formerly Greenwich Mean Time). The `TIMESTAMP` `WITH` `LOCAL` `TIME` ZONE datatype has the form:

    TIMESTAMP(fractional_seconds_precision) WITH LOCAL TIME ZONE

where `fractional_seconds_precision` optionally specifies the number of digits in the fractional part of the `SECOND` datetime field and can be a number in the range 0 to 9. The default is 6.

##### 4.1.3.6 INTERVAL YEAR TO MONTH

`INTERVAL` `YEAR` `TO` `MONTH` stores a period of time using the `YEAR` and `MONTH` datetime fields. The `INTERVAL` `YEAR` `TO` `MONTH` datatype has the form:

    INTERVAL YEAR(year_precision) TO MONTH

where the optional `year_precision` is the number of digits in the `YEAR` datetime field. The default value of `year_precision` is 2.

##### 4.1.3.7 INTERVAL DAY TO SECOND

`INTERVAL` `DAY` `TO` `SECOND` stores a period of time in terms of days, hours, minutes, and seconds. The `INTERVAL` `DAY` `TO` `SECOND` datatype has the form:

    INTERVAL DAY (day_precision) TO SECOND(fractional_seconds_precision)

where:

- `day_precision` is the number of digits in the `DAY` datetime field. It is optional. Accepted values are 0 to 9. The default is 2.

`fractional_seconds_precision` is the number of digits in the fractional part of the `SECOND` datetime field. It is optional. Accepted values are 0 to 9. The default is 6.

##### 4.1.3.8 Avoiding Unexpected Results Using Datetime

**Note:**

To avoid unexpected results in your DML operations on datetime data, you can verify the database and session time zones by querying the built-in SQL functions `DBTIMEZONE` and `SESSIONTIMEZONE`. If the time zones have not been set manually, Oracle uses the operating system time zone by default. If the operating system time zone is not a valid Oracle time zone, Oracle uses UTC as the default value.

### 4.2 Host Variables

Host variables are the key to communication between your host program and Oracle. Typically, a precompiler program inputs data from a host variable to Oracle, and Oracle outputs data to a host variable in the program. Oracle stores input data in database columns, and stores output data in program host variables.

A host variable can be any arbitrary C expression that resolves to a scalar type. But, a host variable must also be an lvalue. Host arrays of most host variables are also supported.

#### 4.2.1 Host Variable Declaration

You declare a host variable according to the rules of the C programming language, specifying a C datatype supported by the Oracle program interface. The C datatype must be compatible with that of the source or target database column.

If MODE=ORACLE, you do not have to declare host variables in a special Declare Section. However, if you do not use a Declare Section, the FIPS flagger warns you about this, as the Declare Section is part of the ANSI SQL Standard. If CODE=CPP (you are compiling C++ code) or PARSE=NONE or PARSE=PARTIAL, then you must have a Declare Section.

Table 4-4 shows the C datatypes and the pseudotypes that you can use when declaring host variables. Only these datatypes can be used for host variables.

Table 4-4 C Datatypes for Host Variables

| C Datatype or Pseudotype | Description                                      |
|:-------------------------|:-------------------------------------------------|
| char                     | single character                                 |
| char\[n\]                | n-character array (string)                       |
| int                      | integer                                          |
| short                    | small integer                                    |
| long                     | large integer                                    |
| long long                | very large (8-byte) integer                      |
| float                    | floating-point number (usually single precision) |
| double                   | floating-point number (always double precision)  |
| VARCHAR\[n\]             | variable-length string                           |

Table 4-5 shows the compatible Oracle internal datatypes.

Table 4-5 C to Oracle Datatype Compatibility

| Internal Type                                                                                                                                 | C Type                                                                            | Description                                                                                                                                                                                                        |
|:----------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| VARCHAR2(Y)<br>(Note 1)                                                                                                                       | char                                                                              | single character                                                                                                                                                                                                   |
| CHAR(X)<br>(Note 1)                                                                                                                           | char\[n\]<br>VARCHAR\[n\]<br>int<br>short<br>long<br>long long<br>float<br>double | n-byte character array<br>n-byte variable-length character array<br>integer<br>small integer<br>large integer<br>very large (8-byte) integer<br>floating-point number<br>double-precision floating-point<br>number |
| NUMBER                                                                                                                                        | int                                                                               | integer                                                                                                                                                                                                            |
| NUMBER(P,S)<br>(Note 2)                                                                                                                       | short<br>int<br>long<br>float<br>double<br>char<br>char\[n\]<br>VARCHAR\[n\]      | small integer<br>integer<br>large integer<br>floating-point number<br>double-precision floating-point<br>number<br>single character<br>n-byte character array<br>n-byte variable-length character array            |
| DATE                                                                                                                                          | char\[n\]<br>VARCHAR\[n\]                                                         | n-byte character array<br>n-byte variable-length character array                                                                                                                                                   |
| LONG                                                                                                                                          | char\[n\]<br>VARCHAR\[n\]                                                         | n-byte character array<br>n-byte variable-length character array                                                                                                                                                   |
| RAW(X)<br>(Note 1)                                                                                                                            | unsigned char\[n\]<br>VARCHAR\[n\]                                                | n-byte character array<br>n-byte variable-length character array                                                                                                                                                   |
| LONG RAW                                                                                                                                      | unsigned char\[n\]<br>VARCHAR\[n\]                                                | n-byte character array<br>n-byte variable-length character array                                                                                                                                                   |
| ROWID                                                                                                                                         | unsigned char\[n\]<br>VARCHAR\[n\]                                                | n-byte character array<br>n-byte variable-length character array                                                                                                                                                   |
| Notes:<br>1. X ranges from 1 to 2000. 1 is the default value. Y ranges from 1 to 4000.<br>2. P ranges from 1 to 38. S ranges from -84 to 127. |                                                                                   |                                                                                                                                                                                                                    |

One-dimensional arrays of simple C types can also serve as host variables. For char\[n\] and VARCHAR\[n\], n specifies the maximum string length, not the number of strings in the array. Two-dimensional arrays are allowed only for char\[m\]\[n\] and VARCHAR\[m\]\[n\], where m specifies the number of strings in the array and n specifies the maximum string length.

Pointers to simple C types are supported. Pointers to char\[n\] and VARCHAR\[n\] variables should be declared as pointer to char or VARCHAR (with no length specification). Arrays of pointers, however, are not supported.

##### 4.2.1.1 Storage-Class Specifiers

Pro\*C/C++ lets you use the auto, extern, and static storage-class specifiers when you declare host variables. However, you cannot use the register storage-class specifier to store host variables, since the precompiler takes the address of host variables by placing an ampersand (&) before them. Following the rules of C, you can use the auto storage class specifier only within a block.

To comply with the ANSI C standard, the Pro\*C/C++ Precompiler provides the ability to declare an extern char\[n\] host variable with or without a maximum length, as the following examples shows:

    extern char  protocol[15];
    extern char  msg[];

However, you should always specify the maximum length. In the last example, if msg is an output host variable declared in one precompilation unit but defined in another, the precompiler has no way of knowing its maximum length. If you have not allocated enough storage for msg in the second precompilation unit, you might corrupt memory. (Usually, "enough" is the number of bytes in the longest column value that might be SELECTed or FETCHed into the host variable, plus one byte for a possible null terminator.)

If you neglect to specify the maximum length for an extern char\[ \] host variable, the precompiler issues a warning message. The precompiler also assumes that the host variable will store a CHARACTER column value, which cannot exceed 255 characters in length. So, if you want to SELECT or FETCH a VARCHAR2 or a LONG column value of length greater than 255 characters into the host variable, you must specify a maximum length.

##### 4.2.1.2 Type Qualifiers

You can also use the const and volatile type qualifiers when you declare host variables.

A const host variable must have a constant value, that is, your program cannot change its initial value. A volatile host variable can have its value changed in ways unknown to your program (for example, by a device attached to the system).

#### 4.2.2 Host Variable Referencing

You use host variables in SQL data manipulation statements. A host variable must be prefixed with a colon (:) in SQL statements but must not be prefixed with a colon in C statements, as the following example shows:

    char    buf[15];
    int     emp_number;
    float   salary;
    ...
    gets(buf);
    emp_number = atoi(buf);

    EXEC SQL SELECT sal INTO :salary FROM emp
        WHERE empno = :emp_number;

Though it might be confusing, you can give a host variable the same name as an Oracle table or column, as this example shows:

    int     empno;
    char    ename[10];
    float   sal;
    ...
    EXEC SQL SELECT ename, sal INTO :ename, :sal FROM emp
        WHERE empno = :empno;

##### 4.2.2.1 Restrictions

A host variable name is a C identifier, hence it must be declared and referenced in the same upper/lower case format. It cannot substitute for a column, table, or other Oracle object in a SQL statement, and must not be an Oracle reserved word.

A host variable must resolve to an address in the program. For this reason, function calls and numeric expressions cannot serve as host variables. The following code is invalid:

    #define MAX_EMP_NUM    9000
    ...
    int get_dept();
    ...
    EXEC SQL INSERT INTO emp (empno, ename, deptno) VALUES
        (:MAX_EMP_NUM + 10, 'CHEN', :get_dept());

**Related Topics**

- [Reserved Words, Keywords, and Namespaces](reserved-words-keywords-namespaces.md)

### 4.3 Indicator Variables

You can associate every host variable with an optional indicator variable. An indicator variable must be defined as a 2-byte integer and, in SQL statements, must be prefixed with a colon and immediately follow its host variable (unless you use the keyword INDICATOR). If you are using Declare Sections, you must also declare indicator variables inside the Declare Sections.

This applies to relational columns, not object types.

**Related Topics**

- [Objects](about-Objects.md)

#### 4.3.1 The INDICATOR Keyword

To improve readability, you can precede any indicator variable with the optional keyword INDICATOR. You must still prefix the indicator variable with a colon. The correct syntax is:

    :host_variable INDICATOR :indicator_variable

which is equivalent to

    :host_variable:indicator_variable

You can use both forms of expression in your host program.

Possible indicator values, and their meanings, are:

| Indicator Values | Meanings                                                                                                                                                                                                                                                                                                                                          |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0                | The operation was successful                                                                                                                                                                                                                                                                                                                      |
| -1               | A NULL was returned, inserted, or updated.                                                                                                                                                                                                                                                                                                        |
| -2               | Output to a character host variable from a "long" type was truncated, but the original column length cannot be determined.                                                                                                                                                                                                                        |
| \>0              | The result of a SELECT or FETCH into a character host variable was truncated. In this case, if the host variable is a multibyte character variable, the indicator value is the original column length in characters. If the host variable is not a multibye character variable, then the indicator length is the original column length in bytes. |

#### 4.3.2 Example of INDICATOR Variable Usage

Typically, you use indicator variables to assign NULLs to input host variables and detect NULLs or truncated values in output host variables. In the example later, you declare three host variables and one indicator variable, then use a SELECT statement to search the database for an employee number matching the value of host variable emp_number. When a matching row is found, Oracle sets output host variables salary and commission to the values of columns SAL and COMM in that row and stores a return code in indicator variable ind_comm. The next statements use ind_comm to select a course of action.

    EXEC SQL BEGIN DECLARE SECTION;
        int    emp_number;
        float  salary, commission;
        short comm_ind;  /* indicator variable  */
    EXEC SQL END DECLARE SECTION;
        char temp[16];
        float  pay;      /* not used in a SQL statement */
    ...
    printf("Employee number? ");
    gets(temp);
    emp_number = atof(temp);
    EXEC SQL SELECT SAL, COMM
        INTO :salary, :commission:ind_comm
        FROM EMP
        WHERE EMPNO = :emp_number;
    if(ind_comm == -1)    /* commission is null */
        pay = salary;
    else
        pay = salary + commission;

**Related Topics**

- [Indicator Variables](embedded-SQL.md)

#### 4.3.3 INDICATOR Variable Guidelines

The following guidelines apply to declaring and referencing indicator variables. An indicator variable must

- Be declared explicitly (in the Declare Section if present) as a 2-byte integer.

- Be prefixed with a colon (:) in SQL statements.

- Immediately follow its host variable in SQL statements and PL/SQL blocks (unless preceded by the keyword INDICATOR).

An indicator variable must not:

- Be prefixed with a colon in host language statements.

- Follow its host variable in host language statements.

- Be an Oracle reserved word.

#### 4.3.4 Oracle Restrictions

When DBMS=V7 or V8, if you SELECT or FETCH a NULL into a host variable that has no indicator, Oracle issues the following error message:

    ORA-01405: fetched column value is NULL

When precompiling with MODE=ORACLE and DBMS=V7 or V8 specified, you can specify UNSAFE_NULL=YES to disable the ORA-01405 message.

**Related Topics**

- [UNSAFE_NULL](precompiler-options.md)

### 4.4 VARCHAR Variables

You can use the VARCHAR pseudotype to declare variable-length character strings. When your program deals with strings that are output from, or input to, VARCHAR2 or LONG columns, you might find it more convenient to use VARCHAR host variables instead of standard C strings. The datatype name VARCHAR can be uppercase or lowercase, but it cannot be mixed case. In this Guide, uppercase is used to emphasize that VARCHAR is not a native C datatype.

#### 4.4.1 VARCHAR Variable Declaration

Think of a VARCHAR as an extended C type or pre-declared struct. For example, the precompiler expands the VARCHAR declaration

    VARCHAR   username[20];


into the following struct with array and length members:

    struct
    {
        unsigned short  len;
        unsigned char   arr[20];
    } username;

The advantage of using VARCHAR variables is that you can explicitly reference the length member of the VARCHAR structure after a SELECT or FETCH. Oracle puts the length of the selected character string in the length member. You can then use this member to do things such as adding the null ('\0') terminator.

    username.arr[username.len] = '\0';

or using the length in a strncpy or printf statement; for example:

    printf("Username is %.*s\n", username.len, username.arr);

You specify the maximum length of a VARCHAR variable in its declaration. The length must lie in the range 1.65533. For example, the following declaration is invalid because no length is specified:

    VARCHAR   null_string[];    /* invalid */

The length specification holds the current length of the value stored in the array member.

You can declare multiple VARCHARs on a single line; for example:

    VARCHAR emp_name[ENAME_LEN], dept_loc[DEPT_NAME_LEN];

The length specifier for a VARCHAR can be a \#defined macro, or any complex expression that can be resolved to an integer at precompile time.

You can also declare pointers to VARCHAR datatypes.

**Note:**

Do not attempt to use a typedef statement such as:

    typedef VARCHAR buf[64];

This causes errors during C compilation.

**Related Topics**

- [VARCHAR Variables and Pointers](advanced-topics.md)

#### 4.4.2 VARCHAR Variable Referencing

In SQL statements, you reference VARCHAR variables using the struct name prefixed with a colon, as the following example shows:

    ...
    int       part_number;
    VARCHAR   part_desc[40];
    ...
    main()
    {
        ...
        EXEC SQL SELECT pdesc INTO :part_desc
            FROM parts
            WHERE pnum = :part_number;
        ...

After the query is executed, part_desc.len holds the actual length of the character string retrieved from the database and stored in part_desc.arr.

In C statements, you reference VARCHAR variables using the component names, as the next example shows:

    printf("\n\nEnter part description: ");
    gets(part_desc.arr);
    /* You must set the length of the string
       before using the VARCHAR in an INSERT or UPDATE */
    part_desc.len = strlen(part_desc.arr);

#### 4.4.3 Return NULLs to a VARCHAR Variable

Oracle automatically sets the length component of a VARCHAR output host variable. If you SELECT or FETCH a NULL into a VARCHAR, the server does not change the length or array members.

**Note:**

If you select a NULL into a VARCHAR host variable, and there is no associated indicator variable, an ORA-01405 error occurs at run time. Avoid this by coding indicator variables with all host variables. (As a temporary fix, use the UNSAFE_NULL=YES precompiler option.

**Related Topics**

- [DBMS](precompiler-options.md)

#### 4.4.4 Insert NULLs Using VARCHAR Variables

If you set the length of a VARCHAR variable to zero before performing an UPDATE or INSERT statement, the column value is set to NULL. If the column has a NOT NULL constraint, Oracle returns an error.

#### 4.4.5 Pass VARCHAR Variables to a Function

VARCHARs are structures, and most C compilers permit passing of structures to a function by value, and returning structures by copy out from functions. However, in Pro\*C/C++ you must pass VARCHARs to functions by reference. The following example shows the correct way to pass a VARCHAR variable to a function:

    VARCHAR emp_name[20];
    ...
    emp_name.len = 20;
    SELECT ename INTO :emp_name FROM emp
    WHERE empno = 7499;
    ...
    print_employee_name(&emp_name); /* pass by pointer */
    ...

    print_employee_name(name)
    VARCHAR *name;
    {
        ...
        printf("name is %.*s\n", name->len, name->arr);
        ...
    }

#### 4.4.6 Find the Length of the VARCHAR Array Component

When the precompiler processes a VARCHAR declaration, the actual length of the array element in the generated structure can be longer than that declared. For example, on a Sun Solaris system, the Pro\*C/C++ declaration

    VARCHAR my_varchar[12];


is expanded by the precompiler to

    struct my_varchar
    {
        unsigned short len;
        unsigned char  arr[12];
    };

However, the precompiler or the C compiler on this system pads the length of the array component to 14 bytes. This alignment requirement pads the total length of the structure to 16 bytes: 14 for the padded array and 2 bytes for the length.

The `SQLVarcharGetLength()` (replaces the non-threaded `sqlvcp()`) function—part of the SQLLIB runtime library—returns the actual (possibly padded) length of the array member.

You pass the `SQLVarcharGetLength()` function the length of the data for a VARCHAR host variable or a VARCHAR pointer host variable, and `SQLVarcharGetLength()` returns the total length of the array component of the VARCHAR. The total length includes any padding that might be added by your C compiler.

The syntax of `SQLVarcharGetLength()` is

    SQLVarcharGetLength (dvoid *context, unsigned long *datlen, unsigned long *totlen);

For single-threaded applications, use `sqlvcp()`. Put the length of the VARCHAR in the `datlen` parameter before calling `sqlvcp()`. When the function returns, the `totlen` parameter contains the total length of the array element. Both parameters are pointers to unsigned long integers, so must be passed by reference.

**Related Topics**

- [New Names for SQLLIB Public Functions](advanced-topics.md)

#### 4.4.7 Example Program: Using sqlvcp()

The following example program shows how you can use the function in a Pro\*C/C++ application. The example also uses the `sqlgls()` function. The example declares a VARCHAR pointer, then uses the `sqlvcp() `function to determine the size required for the VARCHAR buffer. The program FETCHes employee names from the EMP table and prints them. Finally, the example uses the `sqlgls()` function to print out the SQL statement and its function code and length attributes. This program is available on-line as `sqlvcp.pc` in your `demo` directory.

    /*
     *  The sqlvcp.pc program demonstrates how you can use the
     *  sqlvcp() function to determine the actual size of a
     *  VARCHAR struct. The size is then used as an offset to
     *  increment a pointer that steps through an array of
     *  VARCHARs.
     *
     *  This program also demonstrates the use of the sqlgls()
     *  function, to get the text of the last SQL statement executed.
     *  sqlgls() is described in the "Error Handling" chapter of
     *  The Programmer's Guide to the Oracle Pro*C/C++ Precompiler.
     */

    #include <stdio.h>
    #include <sqlca.h>
    #include <sqlcpr.h>

    /*  Fake a VARCHAR pointer type. */

    struct my_vc_ptr
    {
        unsigned short len;
        unsigned char arr[32767];
    };

    /* Define a type for the VARCHAR pointer */
    typedef struct my_vc_ptr my_vc_ptr;
    my_vc_ptr *vc_ptr;

    EXEC SQL BEGIN DECLARE SECTION;
    VARCHAR *names;
    int      limit;    /* for use in FETCH FOR clause  */
    char    *username = "scott/tiger";
    EXEC SQL END DECLARE SECTION;
    void sql_error();
    extern void sqlvcp(), sqlgls();

    main()
    {
        unsigned int vcplen, function_code, padlen, buflen;
        int i;
        char stmt_buf[120];

        EXEC SQL WHENEVER SQLERROR DO sql_error();

        EXEC SQL CONNECT :username;
        printf("\nConnected.\n");

    /*  Find number of rows in table. */
        EXEC SQL SELECT COUNT(*) INTO :limit FROM emp;


    /*  Declare a cursor for the FETCH statement. */
        EXEC SQL DECLARE emp_name_cursor CURSOR FOR
        SELECT ename FROM emp;
        EXEC SQL FOR :limit OPEN emp_name_cursor;

    /*  Set the desired DATA length for the VARCHAR. */
        vcplen = 10;

    /*  Use SQLVCP to help find the length to malloc. */
        sqlvcp(&vcplen, &padlen);
        printf("Actual array length of VARCHAR is %ld\n", padlen);

    /*  Allocate the names buffer for names.
        Set the limit variable for the FOR clause. */
        names = (VARCHAR *) malloc((sizeof (short) +
        (int) padlen) * limit);
        if (names == 0)
        {
            printf("Memory allocation error.\n");
            exit(1);
        }
    /*  Set the maximum lengths before the FETCH.
     *  Note the "trick" to get an effective VARCHAR *.
     */
        for (vc_ptr = (my_vc_ptr *) names, i = 0; i < limit; i++)
        {
            vc_ptr->len = (short) padlen;
            vc_ptr = (my_vc_ptr *)((char *) vc_ptr +
            padlen + sizeof (short));
        }
    /*  Execute the FETCH. */
        EXEC SQL FOR :limit FETCH emp_name_cursor INTO :names;

    /*  Print the results. */
        printf("Employee names--\n");

        for (vc_ptr = (my_vc_ptr *) names, i = 0; i < limit; i++)
        {
            printf
             ("%.*s\t(%d)\n", vc_ptr->len, vc_ptr->arr, vc_ptr->len);
            vc_ptr = (my_vc_ptr *)((char *) vc_ptr +
                      padlen + sizeof (short));
        }

    /*  Get statistics about the most recent
     *  SQL statement using SQLGLS. Note that
     *  the most recent statement in this example
     *  is not a FETCH, but rather "SELECT ENAME FROM EMP"
     *  (the cursor).
     */
        buflen = (long) sizeof (stmt_buf);

    /*  The returned value should be 1, indicating no error. */
        sqlgls(stmt_buf, &buflen, &function_code);
        if (buflen != 0)
        {
            /* Print out the SQL statement. */
            printf("The SQL statement was--\n%.*s\n", buflen, stmt_buf);

            /* Print the returned length. */
            printf("The statement length is %ld\n", buflen);

            /* Print the attributes. */
            printf("The function code is %ld\n", function_code);

            EXEC SQL COMMIT RELEASE;
            exit(0);
        }
        else
        {
            printf("The SQLGLS function returned an error.\n");
            EXEC SQL ROLLBACK RELEASE;
            exit(1);
        }
    }

    void
    sql_error()
    {
        char err_msg[512];
        int buf_len, msg_len;


        EXEC SQL WHENEVER SQLERROR CONTINUE;

        buf_len = sizeof (err_msg);
        sqlglm(err_msg, &buf_len, &msg_len);
        printf("%.*s\n", msg_len, err_msg);

        EXEC SQL ROLLBACK RELEASE;
        exit(1);
    }

**Related Topics**

- [Handling Runtime Errors](handling-run-time-errors.md)

### 4.5 Cursor Variables

You can use cursor variables in your Pro\*C/C++ program for queries. A cursor variable is a handle for a cursor that must be defined and opened on the Oracle server using PL/SQL. See [Cursor Variables](../lnpls/cursor-variables.md) for complete information about cursor variables.

The advantages of cursor variables are:

- Ease of maintenance

  Queries are centralized, in the stored procedure that opens the cursor variable. If you need to change the cursor, you only need to make the change in one place: the stored procedure. There is no need to change each application.

- Convenient security

  The user of the application is the username used when the Pro\*C/C++ application connects to the server. The user must have execute permission on the stored procedure that opens the cursor but not read permission on the tables used in the query. This capability can be used to limit access to the columns in the table, and access to other stored procedures.

#### 4.5.1 Declare a Cursor Variable

You declare a cursor variable in your Pro\*C/C++ program using the Pro\*C/C++ pseudotype SQL_CURSOR. For example:

    EXEC SQL BEGIN DECLARE SECTION;
        sql_cursor     emp_cursor;             /* a cursor variable */
        SQL_CURSOR     dept_cursor;      /* another cursor variable */
        sql_cursor     *ecp;      /* a pointer to a cursor variable */
        ...
    EXEC SQL END DECLARE SECTION;
    ecp = &emp_cursor;             /* assign a value to the pointer */

You can declare a cursor variable using the type specification SQL_CURSOR, in all upper case, or sql_cursor, in all lower case; you cannot use mixed case.

A cursor variable is just like any other host variable in the Pro\*C/C++ program. It has scope, following the scope rules of C. You can pass it as a parameter to other functions, even functions external to the source file in which you declared it. You can also define functions that return cursor variables, or pointers to cursor variables.

**Note:**

A SQL_CURSOR is implemented as a C struct in the code that Pro\*C/C++ generates. So you can always pass it by pointer to another function, or return a pointer to a cursor variable from a function. But you can only pass it or return it by value if your C compiler supports these operations.

#### 4.5.2 Allocate a Cursor Variable

Before you can use a cursor variable, either to open it or to FETCH it, you must allocate the cursor. You do this using the new precompiler command ALLOCATE. For example, to allocate the SQL_CURSOR emp_cursor that was declared in the example earlier, you write the statement:

    EXEC SQL ALLOCATE :emp_cursor;

Allocating a cursor does not require a call to the server, either at precompile time or at runtime. If the ALLOCATE statement contains an error (for example, an undeclared host variable), Pro\*C/C++ issues a precompile-time error. Allocating a cursor variable does cause heap memory to be used. For this reason, you can free a cursor variable in a program loop. Memory allocated for cursor variables is not freed when the cursor is closed, but only when an explicit CLOSE is executed, or the connection is closed:

    EXEC SQL CLOSE :emp_cursor;

**Related Topics**

- Closing and Freeing a Cursor Variable

#### 4.5.3 Open a Cursor Variable

You must open a cursor variable on the Oracle database server. You cannot use the embedded SQL OPEN command to open a cursor variable. You can open a cursor variable either by calling a PL/SQL stored procedure that opens the cursor (and defines it in the same statement). Or, you can open and define a cursor variable using an anonymous PL/SQL block in your Pro\*C/C++ program.

For example, consider the following PL/SQL package, stored in the database:

    CREATE PACKAGE demo_cur_pkg AS
        TYPE EmpName IS RECORD (name VARCHAR2(10));
        TYPE cur_type IS REF CURSOR RETURN EmpName;
        PROCEDURE open_emp_cur (
                   curs     IN OUT cur_type,
                   dept_num IN     NUMBER);
    END;

    CREATE PACKAGE BODY demo_cur_pkg AS
        CREATE PROCEDURE open_emp_cur (
                   curs     IN OUT cur_type,
                   dept_num IN     NUMBER) IS
        BEGIN
            OPEN curs FOR
                SELECT ename FROM emp
                    WHERE deptno = dept_num
                    ORDER BY ename ASC;
        END;
    END;

After this package has been stored, you can open the cursor curs by calling the open_emp_cur stored procedure from your Pro\*C/C++ program, and FETCH from the cursor in the program. For example:

    ...
    sql_cursor    emp_cursor;
    char          emp_name[11];
    ...
    EXEC SQL ALLOCATE :emp_cursor;  /* allocate the cursor variable */
    ...
    /* Open the cursor on the server side. */
    EXEC SQL EXECUTE
        begin
            demo_cur_pkg.open_emp_cur(:emp_cursor, :dept_num);
        end;
    ;
    EXEC SQL WHENEVER NOT FOUND DO break;
    for (;;)
    {
        EXEC SQL FETCH :emp_cursor INTO :emp_name;
        printf("%s\n", emp_name);
    }
    ...

To open a cursor using a PL/SQL anonymous block in your Pro\*C/C++ program, you define the cursor in the anonymous block. For example:

    sql_cursor emp_cursor;
    int dept_num = 10;
    ...
    EXEC SQL EXECUTE
        BEGIN
            OPEN :emp_cursor FOR SELECT ename FROM emp
                 WHERE deptno = :dept_num;
        END;
    END-EXEC;
    ...

The earlier examples show how to use PL/SQL to open a cursor variable. You can also open a cursor variable using embedded SQL with the CURSOR clause:

    ...
    sql_cursor emp_cursor;
    ...
    EXEC ORACLE OPTION(select_error=no);
    EXEC SQL
        SELECT CURSOR(SELECT ename FROM emp WHERE deptno = :dept_num)
        INTO :emp_cursor FROM DUAL;
    EXEC ORACLE OPTION(select_error=yes);

In the statement earlier, the emp_cursor cursor variable is bound to the first column of the outermost select. The first column is itself a query, but it is represented in the form compatible with a sql_cursor host variable since the CURSOR(...) conversion clause is used.

Before using queries which involve the CURSOR clause, you must set the SELECT_ERROR option to NO. This will prevent the cancellation of the parent cursor and allow the program to run without errors.

##### 4.5.3.1 Opening in a Standalone Stored Procedure

In the example earlier, a reference cursor was defined inside a package, and the cursor was opened in a procedure in that package. But it is not always necessary to define a reference cursor inside the package that contains the procedures that open the cursor.

If you need to open a cursor inside a standalone stored procedure, you can define the cursor in a separate package, and then reference that package in the standalone stored procedure that opens the cursor. Here is an example:

    PACKAGE dummy IS
        TYPE EmpName IS RECORD (name VARCHAR2(10));
        TYPE emp_cursor_type IS REF CURSOR RETURN EmpName;
    END;
    -- and then define a standalone procedure:
    PROCEDURE open_emp_curs (
          emp_cursor IN OUT dummy.emp_cursor_type;
          dept_num   IN     NUMBER) IS
        BEGIN
            OPEN emp_cursor FOR
                SELECT ename FROM emp WHERE deptno = dept_num;
        END;
    END;

##### 4.5.3.2 Return Types

When you define a reference cursor in a PL/SQL stored procedure, you must declare the type that the cursor returns.

**Related Topics**

- [Cursor Variable Declaration](../lnpls/cursor-variable-declaration.md)

#### 4.5.4 Closing and Freeing a Cursor Variable

Use the CLOSE command to close a cursor variable. For example, to close the emp_cursor cursor variable that was OPENed in the examples earlier, use the embedded SQL statement:

    EXEC SQL CLOSE :emp_cursor;

The cursor variable is a host variable, and so you must precede it with a colon.

You can reuse ALLOCATEd cursor variables. You can open, FETCH, and CLOSE as many times as needed for your application. However, if you disconnect from the server, then reconnect, you must re-ALLOCATE cursor variables.

Cursors are deallocated by the FREE embedded SQL statement. For example:

    EXEC SQL FREE :emp_cursor;

If the cursor is still open, it is closed and the memory allocated for it is released.

#### 4.5.5 Cursor Variables with the OCI (Release 7 Only)

You can share a Pro\*C/C++ cursor variable with an OCI function. To do so, you must use the SQLLIB conversion functions,` SQLCDAFromResultSetCursor() `(formerly known as `sqlcdat()`) and SQLCDAToResultSetCursor (formerly known as `sqlcurt()`). These functions convert between OCI cursor data areas and Pro\*C/C++ cursor variables.

The `SQLCDAFromResultSetCursor()` function translates an allocated cursor variable to an OCI cursor data area. The syntax is:

    void SQLCDAFromResultSetCursor(dvoid *context, Cda_Def *cda, void *cur,
       sword *retval);

where the parameters are:

| Parameters | Description                                           |
|:-----------|:------------------------------------------------------|
| context    | A pointer to the SQLLIB runtime context.              |
| cda        | A pointer to the destination OCI cursor data area.    |
| cur        | A pointer to the source Pro\*C/C++ cursor variable.   |
| retval     | 0 if no error, otherwise a SQLLIB (SQL) error number. |

**Note:**

In the case of an error, the V2 and rc return code fields in the CDA also receive the error codes. The rows processed count field in the CDA is not set.

For non-threaded or default context applications, pass the defined constant SQL_SINGLE_RCTX as the context.

The `SQLCDAToResultSetCursor()` function translates an OCI cursor data area to a Pro\*C/C++ cursor variable. The syntax is:

    void SQLCDAToResultSetCursor(dvoid *context, void *cur, Cda_Def *cda,
       int *retval);

where the parameters are:

| Parameters | Description                                              |
|:-----------|:---------------------------------------------------------|
| context    | A pointer to the SQLLIB runtime context.                 |
| cur        | A pointer to the destination Pro\*C/C++ cursor variable. |
| cda        | A pointer to the source OCI cursor data area.            |
| retval     | 0 if no error, otherwise an error code.                  |

**Note:**

The SQLCA structure is not updated by this routine. The SQLCA components are only set after a database operation is performed using the translated cursor.

For non-threaded applications, pass the defined constant SQL_SINGLE_RCTX as the context.

ANSI and K&R prototypes for these functions are provided in the `sql2oci.h` header file. Memory for both cda and cur must be allocated prior to calling these functions.

**Related Topics**

- [New Names for SQLLIB Public Functions](advanced-topics.md)

#### 4.5.6 Restrictions (Cursor Variables)

The following restrictions apply to the use of cursor variables:

- If you use the same cursor variable in Pro\*C/C++ and OCI V7, then you must use either SQLLDAGetCurrent() or SQLLDAGetName() immediately after connecting.

- You cannot translate a cursor variable to an OCI release 8 equivalent.

- You cannot use cursor variables with dynamic SQL.

- You can only use cursor variables with the ALLOCATE, FETCH, FREE, and CLOSE commands

- The DECLARE CURSOR command does not apply to cursor variables.

- You cannot FETCH from a CLOSEd cursor variable.

- You cannot FETCH from a non-ALLOCATEd cursor variable.

- If you precompile with MODE=ANSI, it is an error to close a cursor variable that is already closed.

- You cannot use the AT clause with the ALLOCATE command, nor with the FETCH and CLOSE commands if they reference a cursor variable.

- Cursor variables cannot be stored in columns in the database.

- A cursor variable itself cannot be declared in a package specification. Only the type of the cursor variable can be declared in the package specification.

- A cursor variable cannot be a component of a PL/SQL record.

#### 4.5.7 Example: cv_demo.sql and sample11.pc

The following example programs—a PL/SQL script and a Pro\*C/C++ program—demonstrate how you can use cursor variables. These sources are available on-line in your `demo` directory. Also see another version of the same application,` cv_demo.pc`, in the demo directory.

##### 4.5.7.1 cv_demo.sql

    -- PL/SQL source for a package that declares and
    -- opens a ref cursor
    CONNECT SCOTT/TIGER;
    CREATE OR REPLACE PACKAGE emp_demo_pkg as
       TYPE emp_cur_type IS REF CURSOR RETURN emp%ROWTYPE;
         PROCEDURE open_cur(curs IN OUT emp_cur_type, dno IN NUMBER);
    END emp_demo_pkg;


    CREATE OR REPLACE PACKAGE BODY emp_demo_pkg AS
        PROCEDURE open_cur(curs IN OUT emp_cur_type, dno IN NUMBER) IS
        BEGIN
            OPEN curs FOR SELECT *
                FROM emp WHERE deptno = dno
                ORDER BY ename ASC;
        END;
    END emp_demo_pkg;

##### 4.5.7.2 sample11.pc

    /*
     *  Fetch from the EMP table, using a cursor variable.
     *  The cursor is opened in the stored PL/SQL procedure
     *  open_cur, in the EMP_DEMO_PKG package.
     *
     *  This package is available on-line in the file
     *  sample11.sql, in the demo directory.
     *
     */

    #include <stdio.h>
    #include <sqlca.h>
    #include <stdlib.h>
    #include <sqlda.h>
    #include <sqlcpr.h>

    /* Error handling function. */
    void sql_error(msg)
        char *msg;
    {
        size_t clen, fc;
        char cbuf[128];

        clen = sizeof (cbuf);
        sqlgls((char *)cbuf, (size_t *)&clen, (size_t *)&fc);

        printf("\n%s\n", msg);
        printf("Statement is--\n%s\n", cbuf);
        printf("Function code is %ld\n\n", fc);

        sqlglm((char *)cbuf, (size_t *) &clen, (size_t *) &clen);
        printf ("\n%.*s\n", clen, cbuf);

        EXEC SQL WHENEVER SQLERROR CONTINUE;
        EXEC SQL ROLLBACK WORK RELEASE;
        exit(EXIT_FAILURE);
    }

    void main()
    {
        char temp[32];

        EXEC SQL BEGIN DECLARE SECTION;
            char *uid = "scott/tiger";
            SQL_CURSOR emp_cursor;
            int dept_num;
            struct
            {
                int   emp_num;
                char  emp_name[11];
                char  job[10];
                int   manager;
                char  hire_date[10];
                float salary;
                float commission;
                int   dept_num;
            } emp_info;

            struct
            {
                short emp_num_ind;
                short emp_name_ind;
                short job_ind;
                short manager_ind;
                short hire_date_ind;
                short salary_ind;
                short commission_ind;
                short dept_num_ind;
            } emp_info_ind;
        EXEC SQL END DECLARE SECTION;

        EXEC SQL WHENEVER SQLERROR do sql_error("Oracle error");

    /* Connect to Oracle. */
        EXEC SQL CONNECT :uid;

    /* Allocate the cursor variable. */
        EXEC SQL ALLOCATE :emp_cursor;

    /* Exit the inner for (;;) loop when NO DATA FOUND. */
        EXEC SQL WHENEVER NOT FOUND DO break;

        for (;;)
        {
            printf("\nEnter department number  (0 to exit): ");
            gets(temp);
            dept_num = atoi(temp);
            if (dept_num <= 0)
                break;

            EXEC SQL EXECUTE
                begin
                    emp_demo_pkg.open_cur(:emp_cursor, :dept_num);
                end;
            END-EXEC;

            printf("\nFor department %d--\n", dept_num);
            printf("ENAME           SAL     COMM\n");
            printf("-----           ---     ----\n");

    /* Fetch each row in the EMP table into the data struct.
       Note the use of a parallel indicator struct. */
            for (;;)
            {
                 EXEC SQL FETCH :emp_cursor
                     INTO :emp_info INDICATOR :emp_info_ind;

                 printf("%s ", emp_info.emp_name);
                 printf("%8.2f ", emp_info.salary);
                 if (emp_info_ind.commission_ind != 0)
                     printf("    NULL\n");
                 else
                     printf("%8.2f\n", emp_info.commission);
            }

        }

    /* Close the cursor. */
        EXEC SQL WHENEVER SQLERROR CONTINUE;
        EXEC SQL CLOSE :emp_cursor;

    /* Disconnect from Oracle. */
        EXEC SQL ROLLBACK WORK RELEASE;
        exit(EXIT_SUCCESS);

    }

### 4.6 CONTEXT Variables

A runtime context, usually simply called a context, is a handle to a an area in client memory which contains zero or more connections, zero or more cursors, their inline options (such as MODE, HOLD_CURSOR, RELEASE_CURSOR, SELECT_ERROR, and so on.) and other additional state information.

To define a context host variable use pseudo-type sql_context. For example:

    sql_context my_context ;

Use the CONTEXT ALLOCATE precompiler directive to allocate and initialize memory for a context:

    EXEC SQL CONTEXT ALLOCATE :context ;

where `context` is a host variable that is a handle to the context. For example:

    EXEC SQL CONTEXT ALLOCATE :my_context ;

Use the CONTEXT USE precompiler directive to define which context is to be used by the embedded SQL statements (such as CONNECT, INSERT, DECLARE CURSOR, and so on.) from that point on in the source file, not in the flow of program logic. That context is used until another CONTEXT USE statement is encountered. The syntax is:

    EXEC SQL CONTEXT USE {:context | DEFAULT} ;

The keyword DEFAULT specifies that the default (also known as global) context is to be used in all the embedded SQL statements that are executed subsequently, until another CONTEXT USE directive is encountered. A simple example is:

    EXEC SQL CONTEXT USE :my_context ;

If the context variable `my_context` has not been defined and allocated already, an error is returned.

The CONTEXT FREE statement frees the memory used by the context after it is no longer needed:

    EXEC SQL CONTEXT FREE :context ;

An example is:

    EXEC SQL CONTEXT FREE :my_context ;

The following example demonstrates the use of a default context in the same application as a user-defined context:

#### CONTEXT USE Example

    #include <sqlca.h>
    #include <ociextp.h>
    main()
    {
       sql_context ctx1;
       char *usr1 = "scott/tiger";
       char *usr2 = "system/manager";

       /* Establish connection to SCOTT in global runtime context */
       EXEC SQL CONNECT :usr1;

       /* Establish connection to SYSTEM in runtime context ctx1 */
       EXEC SQL CONTEXT ALLOCATE :ctx1;
       EXEC SQL CONTEXT USE :ctx1;
       EXEC SQL CONNECT :usr2;

       /* Insert into the emp table from schema SCOTT */
       EXEC SQL CONTEXT USE DEFAULT;
       EXEC SQL INSERT INTO emp (empno, ename) VALUES (1234, 'WALKER');
       ...
    }

### 4.7 Universal ROWIDs

There are two kinds of table organization used in the database server: heap tables and index-organized tables.

Heap tables are the default. The physical row address (ROWID) is a permanent property that is used to identify a row in a heap table. The external character format of the physical ROWID is an 18-byte character string in base-64 encoding.

An index-organized table does not have physical row addresses as permanent identifiers. A logical ROWID is defined for these tables. When you use a SELECT ROWID ... statement from an index-organized table the ROWID is an opaque structure that contains the primary key of the table, control information, and an optional physical "guess". You can use this ROWID in a SQL statement containing a clause such as "WHERE ROWID = ..." to retrieve values from the table.

Universal ROWID can be used for both physical ROWID and logical ROWID. You can use universal ROWIDs to access data in heap tables, or index-organized tables, since the table organization can change with no effect on applications. The column datatype used for ROWID is UROWID(length), where `length` is optional.

Use the universal ROWID in all new applications.

Use a universal ROWID variable this way:

- Declare it as type pointer to OCIRowid.

- Allocate memory for the universal ROWID variable.

- Use the universal ROWID as a host bind variable.

- Free the memory when finished.

For example:

    OCIRowid *my_urowid ;
    ...
    EXEC SQL ALLOCATE :my_urowid ;
    /* Bind my_urowid as type SQLT_RDD -- no implicit conversion */
    EXEC SQL SELECT rowid INTO :my_urowid FROM my_table WHERE ... ;
    ...
    EXEC SQL UPDATE my_table SET ... WHERE rowid = :my_urowid ;
    EXEC SQL FREE my_urpwid ;
    ...

You also have the option of using a character host variable of width between 19 (18 bytes plus the null-terminator) and 4001 as the host bind variable for universal ROWID. Character-based universal ROWIDs are supported for heap tables only for backward compatibility. Because universal ROWID can be variable length, there can be truncation.

Use the character variable this way:

    /* n is based on table characteristics  */
    int n=4001 ;
    char my_urowid_char[n] ;
    ...
    EXEC SQL ALLOCATE :my_urowid_char ;
    /* Bind my_urowid_char as SQLT_STR  */
    EXEC SQL SELECT rowid INTO :my_urowid_char FROM my_table WHERE ... ;
    EXEC ORACLE OPTION(CHAR_MAP=STRING);
    EXEC SQL UPDATE my_table SET ... WHERE rowid = :my_urowid_char ;
    EXEC SQL FREE :my_urowid_char ;
    ...

**Related Topics**

- [Positioned Update](embedded-SQL.md)
- [Logical Storage Structures](../cncpt/logical-storage-structures.md)

#### 4.7.1 SQLRowidGet()

A SQLLIB function, SQLRowidGet(), provides the ability to retrieve a pointer to the universal ROWID of the last row inserted, updated, or selected. The function prototype and its arguments are:

    void SQLRowidGet (dvoid *rctx, OCIRowid **urid) ;

rctx (IN)

is a pointer to a runtime context. For the default context or a non-threaded case, pass SQL_SINGLE_RCTX.

urid (OUT)

is a pointer to a universal ROWID pointer. When a normal execution finishes, this will point to a valid ROWID. In case of an error, NULL is returned.

**Note:**

The universal ROWID pointer musthave been previously allocated to call SQLRowidGet(). Use FREE afterward on the universal ROWID.

### 4.8 Host Structures

You can use a C structure to contain host variables. You reference a structure containing host variables in the INTO clause of a SELECT or a FETCH statement, and in the VALUES list of an INSERT statement. Every component of the host structure must be a legal Pro\*C/C++ host variable, as defined in Table 4-4.

When a structure is used as a host variable, only the name of the structure is used in the SQL statement. However, each of the members of the structure sends data to Oracle, or receives data from Oracle on a query. The following example shows a host structure that is used to add an employee to the EMP table:

    typedef struct
    {
        char  emp_name[11]; /* one greater than column length */
        int   emp_number;
        int   dept_number;
        float salary;
    } emp_record;
    ...
    /* define a new structure of type "emp_record" */
    emp_record new_employee;

    strcpy(new_employee.emp_name, "CHEN");
    new_employee.emp_number = 9876;
    new_employee.dept_number = 20;
    new_employee.salary = 4250.00;

    EXEC SQL INSERT INTO emp (ename, empno, deptno, sal)
        VALUES (:new_employee);

The order that the members are declared in the structure must match the order that the associated columns occur in the SQL statement, or in the database table if the column list in the INSERT statement is omitted.

For example, the following use of a host structure is invalid, and causes a runtime error:

    struct
    {
        int empno;
        float salary;          /* struct components in wrong order */
        char emp_name[10];
    } emp_record;

    ...
    SELECT empno, ename, sal
       INTO :emp_record FROM emp;

The example is wrong because the components of the structure are not declared in the same order as the associated columns in the select list. The correct form of the SELECT statement is:

    SELECT empno, sal, ename   /* reverse order of sal and ename */
        INTO :emp_record FROM emp;

#### 4.8.1 Host Structures and Arrays

An array is a collection of related data items, called elements, associated with a single variable name. When declared as a host variable, the array is called a host array. Likewise, an indicator variable declared as an array is called an indicator array. An indicator array can be associated with any host array.

Host arrays can increase performance by letting you manipulate an entire collection of data items with a single SQL statement. With few exceptions, you can use host arrays wherever scalar host variables are allowed. Also, you can associate an indicator array with any host array.

You can use host arrays as components of host structures. In the following example, a structure containing arrays is used to INSERT three new entries into the EMP table:

    struct
    {
        char emp_name[3][10];
        int emp_number[3];
        int dept_number[3];
    } emp_rec;
    ...
    strcpy(emp_rec.emp_name[0], "ANQUETIL");
    strcpy(emp_rec.emp_name[1], "MERCKX");
    strcpy(emp_rec.emp_name[2], "HINAULT");
    emp_rec.emp_number[0] = 1964; emp_rec.dept_number[0] = 5;
    emp_rec.emp_number[1] = 1974; emp_rec.dept_number[1] = 5;
    emp_rec.emp_number[2] = 1985; emp_rec.dept_number[2] = 5;

    EXEC SQL INSERT INTO emp (ename, empno, deptno)
        VALUES (:emp_rec);
    ...

**Related Topics**

- [Host Arrays](embedded-PL-SQL.md)

#### 4.8.2 PL/SQL Records

You cannot bind a C struct to a PL/SQL record.

#### 4.8.3 Nested Structures and Unions

You cannot nest host structures. The following example is invalid:

    struct
    {
        int emp_number;
        struct
        {
            float salary;
            float commission;
        } sal_info;            /* INVALID */
        int dept_number;
    } emp_record;
    ...
    EXEC SQL SELECT empno, sal, comm, deptno
        INTO :emp_record
        FROM emp;

Also, you cannot use a C union as a host structure, nor can you nest a union in a structure that is to be used as a host structure.

#### 4.8.4 Host Indicator Structures

When you need to use indicator variables, but your host variables are contained in a host structure, you set up a second structure that contains an indicator variable for each host variable in the host structure.

For example, suppose you declare a host structure student_record as follows:

    struct
    {
        char s_name[32];
        int s_id;
        char grad_date[9];
    } student_record;

If you want to use the host structure in a query such as

    EXEC SQL SELECT student_name, student_idno, graduation_date
        INTO :student_record
        FROM college_enrollment
        WHERE student_idno = 7200;

and you need to know if the graduation date can be NULL, then you must declare a separate host indicator structure. You declare this as

    struct
    {
        short s_name_ind;  /* indicator variables must be shorts */
        short s_id_ind;
        short grad_date_ind;
    } student_record_ind;

Reference the indicator structure in the SQL statement in the same way that you reference a host indicator variable:

    EXEC SQL SELECT student_name, student_idno, graduation_date
        INTO :student_record INDICATOR :student_record_ind
        FROM college_enrollment
        WHERE student_idno = 7200;


When the query completes, the NULL/NOT NULL status of each selected component is available in the host indicator structure.

**Note:**

This Guide conventionally names indicator variables and indicator structures by appending \_ind to the host variable or structure name. However, the names of indicator variables are completely arbitrary. You can adopt a different convention, or use no convention at all.

#### 4.8.5 Example Program: Cursor and a Host Structure

The demonstration program in this section shows a query that uses an explicit cursor, selecting data into a host structure. This program is available in the file `sample2.pc` in your `demo` directory.

    /*
     *  sample2.pc
     *
     *  This program connects to ORACLE, declares and opens a cursor,
     *  fetches the names, salaries, and commissions of all
     *  salespeople, displays the results, then closes the cursor.
     */

    #include <stdio.h>
    #include <sqlca.h>

    #define UNAME_LEN      20
    #define PWD_LEN        40

    /*
     * Use the precompiler typedef'ing capability to create
     * null-terminated strings for the authentication host
     * variables. (This isn't really necessary--plain char *'s
     * does work as well. This is just for illustration.)
     */
    typedef char asciiz[PWD_LEN];

    EXEC SQL TYPE asciiz IS STRING(PWD_LEN) REFERENCE;
    asciiz     username;
    asciiz     password;

    struct emp_info
    {
        asciiz     emp_name;
        float      salary;
        float      commission;
    };

    /* Declare function to handle unrecoverable errors. */
    void sql_error();

    main()
    {
        struct emp_info *emp_rec_ptr;

    /* Allocate memory for emp_info struct. */
        if ((emp_rec_ptr =
            (struct emp_info *) malloc(sizeof(struct emp_info))) == 0)
        {
            fprintf(stderr, "Memory allocation error.\n");
            exit(1);
        }

    /* Connect to ORACLE. */
        strcpy(username, "SCOTT");
        strcpy(password, "TIGER");

        EXEC SQL WHENEVER SQLERROR DO sql_error("ORACLE error--");

        EXEC SQL CONNECT :username IDENTIFIED BY :password;
        printf("\nConnected to ORACLE as user: %s\n", username);

    /* Declare the cursor. All static SQL explicit cursors
     * contain SELECT commands. 'salespeople' is a SQL identifier,
     * not a (C) host variable.
     */
        EXEC SQL DECLARE salespeople CURSOR FOR
            SELECT ENAME, SAL, COMM
                FROM EMP
                WHERE JOB LIKE 'SALES%';

    /* Open the cursor. */
        EXEC SQL OPEN salespeople;

    /* Get ready to print results. */
        printf("\n\nThe company's salespeople are--\n\n");
        printf("Salesperson   Salary   Commission\n");
        printf("-----------   ------   ----------\n");

    /* Loop, fetching all salesperson's statistics.
     * Cause the program to break the loop when no more
     * data can be retrieved on the cursor.
     */
        EXEC SQL WHENEVER NOT FOUND DO break;

        for (;;)
        {
            EXEC SQL FETCH salespeople INTO :emp_rec_ptr;
            printf("%-11s%9.2f%13.2f\n", emp_rec_ptr->emp_name,
                    emp_rec_ptr->salary, emp_rec_ptr->commission);
        }

    /* Close the cursor. */
        EXEC SQL CLOSE salespeople;

        printf("\nArrivederci.\n\n");

        EXEC SQL COMMIT WORK RELEASE;
        exit(0);
    }

    void
    sql_error(msg)
    char *msg;
    {
        char err_msg[512];
        int buf_len, msg_len;

        EXEC SQL WHENEVER SQLERROR CONTINUE;

        printf("\n%s\n", msg);

    /* Call sqlglm() to get the complete text of the
     * error message.
     */
        buf_len = sizeof (err_msg);
        sqlglm(err_msg, &buf_len, &msg_len);
        printf("%.*s\n", msg_len, err_msg);

        EXEC SQL ROLLBACK RELEASE;
        exit(1);
    }

### 4.9 Pointer Variables

C supports pointers, which "point" to other variables. A pointer holds the address (storage location) of a variable, not its value.

#### 4.9.1 Pointer Variable Declaration

You define pointers as host variables following the normal C practice, as the next example shows:

    int   *int_ptr;
    char  *char_ptr;

#### 4.9.2 Pointer Variable Referencing

In SQL statements, prefix pointers with a colon, as shown in the following example:

    EXEC SQL SELECT intcol INTO :int_ptr FROM ...

Except for pointers to character strings, the size of the referenced value is given by the size of the base type specified in the declaration. For pointers to character strings, the referenced value is assumed to be a NULL-terminated string. Its size is determined at run time by calling the `strlen() `function.

You can use pointers to reference the members of a struct. First, declare a pointer host variable, then set the pointer to the address of the desired member, as shown in the example later. The datatypes of the struct member and the pointer variable must be the same. Most compilers will warn you of a mismatch.

    struct
    {
        int  i;
        char c;
    } structvar;
    int   *i_ptr;
    char  *c_ptr;
    ...
    main()
    {
        i_ptr = &structvar.i;
        c_ptr = &structvar.c;
    /* Use i_ptr and c_ptr in SQL statements. */
    ...

**Related Topics**

- Globalization Support

#### 4.9.3 Structure Pointers

You can use a pointer to a structure as a host variable. The following example

- Declares a structure

- Declares a pointer to the structure

- Allocates memory for the structure

- Uses the struct pointer as a host variable in a query

- Dereferences the struct components to print the results

<!-- -->

    struct EMP_REC
    {
        int emp_number;
        float salary;
    };
    char *name = "HINAULT";
    ...
    struct EMP_REC *sal_rec;
    sal_rec = (struct EMP_REC *) malloc(sizeof (struct EMP_REC));
    ...
    EXEC SQL SELECT empno, sal INTO :sal_rec
        FROM emp
        WHERE ename = :name;

    printf("Employee number and salary for %s: ", name);
    printf("%d, %g\n", sal_rec->emp_number, sal_rec->salary);

In the SQL statement, pointers to host structures are referred to in exactly the same way as a host structure. The "address of" notation (&) is not required; in fact, it is an error to use it.

### 4.10 Globalization Support

Although the widely-used 7- or 8-bit ASCII and EBCDIC character sets are adequate to represent the Roman alphabet, some Asian languages, such as Japanese, contain thousands of characters. These languages can require at least 16 bits (two bytes) to represent each character. How does Oracle deal with such dissimilar languages?

Oracle provides Globalization Support, which lets you process single-byte and multibyte character data and convert between character sets. It also lets your applications run in different language environments. With Globalization Support, number and date formats adapt automatically to the language conventions specified for a user session. Thus, Globalization Support allows users around the world to interact with Oracle in their native languages.

You control the operation of language-dependent features by specifying various Globalization Support or NLS parameters. Default values for these parameters can be set in the Oracle initialization file. The following table shows what each Globalization Support parameter specifies.

Table 4-6 Globalization Support Parameters

| Globalization Support Parameter | Specifies                             |
|:--------------------------------|:--------------------------------------|
| NLS_LANGUAGE                    | language-dependent conventions        |
| NLS_TERRITORY                   | territory-dependent conventions       |
| NLS_DATE_FORMAT                 | date format                           |
| NLS_DATE_LANGUAGE               | language for day and month names      |
| NLS_NUMERIC_CHARACTERS          | decimal character and group separator |
| NLS_CURRENCY                    | local currency symbol                 |
| NLS_ISO_CURRENCY                | ISO currency symbol                   |
| NLS_SORT                        | sort sequence                         |

The main parameters are NLS_LANGUAGE and NLS_TERRITORY. NLS_LANGUAGE specifies the default values for language-dependent features, which include:

- Language for server messages

- Language for day and month names

- Sort sequence

NLS_TERRITORY specifies the default values for territory-dependent features, which include

- Date format

- Decimal character

- Group separator

- Local currency symbol

- ISO currency symbol

You can control the operation of language-dependent Globalization Support features for a user session by specifying the parameter NLS_LANG as follows:

    NLS_LANG = <language>_<territory>.<character set>

where language specifies the value of NLS_LANGUAGE for the user session, territory specifies the value of NLS_TERRITORY, and character set specifies the encoding scheme used for the terminal. An encoding scheme (usually called a character set or code page) is a range of numeric codes that corresponds to the set of characters a terminal can display. It also includes codes that control communication with the terminal.

You define NLS_LANG as an environment variable (or the equivalent on your system). For example, on UNIX using the C shell, you might define NLS_LANG as follows:

    setenv NLS_LANG French_France.WE8ISO8859P1

During an Oracle database session you can change the values of Globalization Support parameters. Use the ALTER SESSION statement as follows:

    ALTER SESSION SET <globalization support_parameter> = <value>

Pro\*C/C++ fully supports all the Globalization Support features that allow your applications to process foreign language data stored in an Oracle database. For example, you can declare foreign language character variables and pass them to string functions such as INSTRB, LENGTHB, and SUBSTRB. These functions have the same syntax as the INSTR, LENGTH, and SUBSTR functions, respectively, but operate on a byte-by-byte basis rather than a character-by-character basis.

You can use the functions NLS_INITCAP, NLS_LOWER, and NLS_UPPER to handle special instances of case conversion. And, you can use the function NLSSORT to specify WHERE-clause comparisons based on linguistic rather than binary ordering. You can even pass globalization support parameters to the TO_CHAR, TO_DATE, and TO_NUMBER functions.

### 4.11 NCHAR Variables

Three internal database datatypes can store National Character Set data. They are NCHAR, NCLOB, and NVARCHAR2 (also known as NCHAR VARYING). You use these datatypes only in relational columns.

#### 4.11.1 CHARACTER SET \[IS\] NCHAR_CS

To specify which host variables hold National Character Set data, insert the clause "CHARACTER SET \[IS\] NCHAR_CS" in character variable declarations. Then you are able to store National Character Set data in those variables. You can omit the token IS. NCHAR_CS is the name of the National Character Set.

For example:

    char character set is nchar_cs *str = "<Japanese_string>";

In this example, \<Japanese_string\> consists of Unicode characters that are in the National Character Set AL16UTF16, as defined by the variable NLS_NCHAR.

You can accomplish the same thing by entering NLS_CHAR=str on the command line, and coding in your application:

    char *str = "<Japanese_string>"

Pro\*C/C++ treats variables declared this way as of the character set specified by the environment variable NLS_NCHAR. The variable size of an NCHAR variable is specified as a byte count, the same way that ordinary C variables are.

To select data into str, use the following simple query:

    EXEC SQL
       SELECT ENAME INTO :str FROM EMP WHERE DEPT = n'<Japanese_string1>';

Or, you can use str in the following SELECT:

    EXEC SQL
       SELECT DEPT INTO :dept FROM DEPT_TAB WHERE ENAME = :str;

#### 4.11.2 Environment Variable NLS_NCHAR

Pro\*C/C++ supports National Character Sets with database support when NLS_LOCAL=NO. When NLS_LOCAL=NO, and the new environmental variable NLS_NCHAR is set to a valid National Character Set, the database server supports NCHAR.

NLS_NCHAR specifies the character set used for National Character Set data (NCHAR, NVARCHAR2, NCLOB). If it is not specified, the character set defined or indirectly defined by NLS_LANG will be used.

NLS_NCHAR must have a valid National Character Set specification (not a language name, that is set by NLS_LANG) at both precompile-time and runtime. SQLLIB performs a runtime check when the first SQL statement is executed. If the precompile-time and runtime character sets are different, SQLLIB will return an error code.

#### 4.11.3 CONVBUFSZ Clause in VAR

You can override the default assignments by equivalencing host variables to Oracle external datatypes, using the EXEC SQL VAR statement, This is called host variable equivalencing.

The EXEC SQL VAR statement can have an optional clause: `CONVBUFSZ (<size>)`. You specify the size, `<size>`, in bytes, of the buffer in the Oracle runtime library used to perform conversion of the specified host variable between character sets.

The new syntax is:

    EXEC SQL VAR host_variable IS datatype [CONVBUFSZ [IS] (size)] ;


or

    EXEC SQL VAR host_variable [CONVBUFSZ [IS] (size)];

where datatype is:

    type_name [ ( { length | precision, scale } ) ]

**Related Topics**

- [VAR (Oracle Embedded SQL Directive)](embedded-SQL-statements-and-directives.md)

#### 4.11.4 Character Strings in Embedded SQL

A multibyte character string in an embedded SQL statement consists of a character literal that identifies the string as multibyte, immediately followed by the string. The string is enclosed in the usual single quotes.

For example, an embedded SQL statement such as

    EXEC SQL SELECT empno INTO :emp_num FROM emp
        WHERE ename = N'<Japanese_string>';

contains a multibyte character string (\<Japanese_string\> could actually be Kanji), since the N character literal preceding the string identifies it as a multibyte string. Since Oracle is case-insensitive, you can use "n" or "N" in the example.

#### 4.11.5 Strings Restrictions

You cannot use datatype equivalencing (the TYPE or VAR commands) with multibyte character strings.

Dynamic SQL method 4 is not available for multibyte character string host variables in Pro\*C/C++.

#### 4.11.6 Indicator Variables

You can use indicator variables with host character variables that are multibyte characters (as specified using the NLS_CHAR option).
