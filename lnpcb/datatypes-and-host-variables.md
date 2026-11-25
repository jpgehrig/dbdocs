This chapter provides the basic information you need to write a Pro\*COBOL program, including:

- The Oracle Database Datatypes

- Datetime and Interval Datatype Descriptors

- Host Variables

- Indicator Variables

- VARCHAR Variables

- Handling Character Data

- Universal ROWIDs

- Globalization Support

- Unicode Support for Pro\*COBOL

- Datatype Conversion

- Explicit Control Over DATE String Format

- Datatype Equivalencing

- Platform Endianness Support

- Sample Program 4: Datatype Equivalencing

### 4.1 The Oracle Database Datatypes

Oracle Database recognizes two kinds of datatypes: internal and external. Internal datatypes specify how Oracle Database stores data in database columns.

Oracle Database also uses internal datatypes to represent database pseudocolumns. An external datatype specifies how data is stored in a host variable.

**See Also:**

[Data Types](../sqlrf/Data-Types.md) for complete descriptions of the Oracle internal (also called built-in) datatypes.

#### 4.1.1 Internal Datatypes

Table 4-1 summarizes the information about each Oracle built-in datatype.

Table 4-1 Summary of Oracle Built-In Datatypes

| Datatype         | Description                                                                                                                                   | Column Length and Default                                                                                                                                                                                                                                                                                                                                                                                              |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CHAR (size)      | Fixed-length character data of length size in characters or bytes, depending on the national character set                                    | Fixed for every row in the table (with trailing blanks.) Column size is the number of characters for a fixed-width national character set or the number of bytes required to store one character, with an upper limit of 2000 bytes for each row. Default size is 1 character or 1 byte for each row, depending on the national character set. Consider the character set (one-byte or multibyte) before setting size. |
| VARCHAR2 (size)  | Fixed-length character data of length size in characters or bytes, depending on the national character set. A maximum size must be specified. | Variable for each row. Column size is the number of characters for a fixed-width national character set or the number of bytes for a varying-width national character set. Maximum size is determined by the number of bytes required to store one character, with an upper limit of 4000 bytes for each row. Default size is 1 character or 1 byte, depending on the national character set.                          |
| NCHAR (size)     | Fixed-length character data of length size in characters or bytes, depending on national character set.                                       | Fixed for every row in the table (with trailing blanks). Column size is the number of bytes for a national character set or the number of bytes for a varying-width national character set. Maximum size is determined by the number of bytes required to store one character, with an upper limit of 2000 bytes for each row. Default is 1 character or 1 byte, depending on the character set.                       |
| NVARCHAR2 (size) | Variable-length character data of length size in characters or bytes, depending on national character set. A maximum size must be specified.  | Variable for each row. Column size is the number of bytes for a national character set. Maximum size is determined by the number of bytes required to store one character, with an upper limit of 4000 bytes for each row. Default is 1 character or 1 byte, depending on the character set.                                                                                                                           |
| CLOB             | Single-byte character data                                                                                                                    | Up to 2^32 - 1 bytes, or 4 gigabytes.                                                                                                                                                                                                                                                                                                                                                                                  |
| NCLOB            | Single-byte or fixed-length multibyte national character set (`NCHAR`) data                                                                   | Up to 2^32 - 1 bytes, or 4 gigabytes.                                                                                                                                                                                                                                                                                                                                                                                  |
| LONG             | Variable-length character data                                                                                                                | Variable for each row in the table, up to 2^31 - 1 bytes, or 2 gigabytes, for each row. Provided for backward compatibility.                                                                                                                                                                                                                                                                                           |
| NUMBER(p,s)      | Variable-length numeric data.: Maximum precision p, or scale s is 38, or both.                                                                | Variable for each row. The maximum space required for a given column is 21 bytes for each row.                                                                                                                                                                                                                                                                                                                         |
| DATE             | Fixed-length date and time data, ranging from Jan. 1, 4712 B.C.E. to Dec. 31, 4712 C.E.                                                       | Fixed at 7 bytes for each row in the table. Default format is a string (such as `DD`-`MON`-`YY`) specified by `NLS_DATE_FORMAT` parameter.                                                                                                                                                                                                                                                                             |
| BLOB             | Unstructured binary data                                                                                                                      | Up to 2^32 - 1 bytes, or 4 gigabytes.                                                                                                                                                                                                                                                                                                                                                                                  |
| BFILE            | Binary data stored in an external file                                                                                                        | Up to 2^32 - 1 bytes, or 4 gigabytes.                                                                                                                                                                                                                                                                                                                                                                                  |
| RAW (size)       | Variable-length raw binary data                                                                                                               | Variable for each row in the table, up to 2000 bytes for each row. A maximum size must be specified. Provided for backward compatibility.                                                                                                                                                                                                                                                                              |
| LONG RAW         | Variable-length raw binary data                                                                                                               | Variable for each row in the table, up to 2^31 - 1 bytes, or 2 gigabytes, for each row. Provided for backward compatibility.                                                                                                                                                                                                                                                                                           |
| ROWID            | Binary data representing row addresses                                                                                                        | Fixed at 10 bytes (extended `ROWID`) or 6 bytes (restricted `ROWID`) for each row in the table.                                                                                                                                                                                                                                                                                                                        |

#### 4.1.2 External Datatypes

The external datatypes include all the internal datatypes plus several datatypes found in other supported host languages. Use the datatype names in datatype equivalencing, and the datatype codes in dynamic SQL Method 4. The following table lists external datatypes.

Table 4-2 External Datatypes

| Name               | Code    | Description                                                                                                                |
|:-------------------|:--------|:---------------------------------------------------------------------------------------------------------------------------|
| CHAR               | 1<br>96 | \<= 65535-byte, variable-length character string ()<br>\<= 65535-byte, fixed-length character string ()                    |
| CHARF              | 96      | \<= 65535-byte, fixed-length character string                                                                              |
| CHARZ              | 97      | \<= 65535-byte, fixed-length, null-terminated string ()                                                                    |
| DATE               | 12      | 7-byte, fixed-length date/time value                                                                                       |
| DECIMAL            | 7       | COBOL packed decimal                                                                                                       |
| DISPLAY            | 91      | COBOL numeric character string with leading sign                                                                           |
| DISPLAY TRAILING   | 152     | COBOL numeric with trailing sign                                                                                           |
| FLOAT              | 4       | 4-byte or 8-byte floating-point number                                                                                     |
| INTEGER            | 3       | 2-byte, 4-byte, or 8-byte signed integer.                                                                                  |
| LONG               | 8       | \<= 2147483647-byte, fixed-length string                                                                                   |
| LONG RAW           | 24      | \<= 217483647-byte, fixed-length binary data                                                                               |
| LONG VARCHAR       | 94      | \<= 217483643-byte, variable-length string                                                                                 |
| LONG VARRAW        | 95      | \<= 217483643-byte, variable-length binary data                                                                            |
| NUMBER             | 2       | Internal Oracle Format Number represented in binary coded decimal format.                                                  |
| OVERPUNCH LEADING  | 172     | COBOL numeric character string with embedded leading sign                                                                  |
| OVERPUNCH TRAILING | 154     | COBOL numeric character string with embedded trailing sign (equivalent to declarations of the form PIC S9(n)V9(m) DISPLAY) |
| RAW                | 23      | \<= 65535-byte, fixed-length binary data ()                                                                                |
| ROWID              | 11      | fixed-length binary value (system-specific)                                                                                |
| STRING             | 5       | \<= 65535-byte, null-terminated character string ()                                                                        |
| UNSIGNED           | 68      | 2-byte or 4-byte unsigned integer                                                                                          |
| UNSIGNED DISPLAY   | 153     | COBOL unsigned numeric                                                                                                     |
| VARCHAR            | 9       | \<= 65533-byte, variable-length character string                                                                           |
| VARCHAR2           | 1       | \<= 65535-byte, variable-length character string ()                                                                        |
| VARNUM             | 6       | variable-length binary number                                                                                              |
| VARRAW             | 15      | \<= 65533-byte, variable-length binary data                                                                                |

Notes:

CHAR is datatype 1 when PICX=VARCHAR2 and datatype 96 when PICX=CHARF.

Maximum size is 32767 (32K) on some platforms.

##### 4.1.2.1 CHAR

CHAR behavior depends on the settings of the option PICX. See "[PICX](precompiler-options.md)".

##### 4.1.2.2 CHARF

By default, the CHARF datatype represents all non-varying character host variables. You use the CHARF datatype to store fixed-length character strings. On most platforms, the maximum length of a CHARF value is 65535 (64K) bytes. See "[PICX](precompiler-options.md)".

On Input. Oracle reads the number of bytes specified for the input host variable, does not strip trailing blanks, then stores the input value in the target database column.

If the input value is longer than the defined width of the database column, Oracle generates an error. If the input value is all-blank, then a string of spaces is stored.

On Output. Oracle returns the number of bytes specified for the output host variable, blank-padding if necessary, then assigns the output value to the target host variable. If a NULL is returned, then the original value of the variable is not overwritten.

If the output value is longer than the declared length of the host variable, Oracle truncates the value before assigning it to the host variable. If an indicator variable is available, Oracle sets it to the original length of the output value.

##### 4.1.2.3 CHARZ

The CHARZ datatype represents fixed-length, null-terminated character strings. On most platforms, the maximum length of a CHARZ value is 65535 bytes. You usually will not need this external type in Pro\*COBOL.

##### 4.1.2.4 DATE

The DATE datatype represents dates and times in 7-byte, fixed-length fields. As Table 4-3 shows, the century, year, month, day, hour (in 24-hour format), minute, and second are stored in that order from left to right.

Table 4-3 Date Format

| Byte                                 | 1       | 2    | 3     | 4   | 5    | 6      | 7      |
|:-------------------------------------|:--------|:-----|:------|:----|:-----|:-------|:-------|
| Meaning                              | Century | Year | Month | Day | Hour | Minute | Second |
| Example<br>17-Oct-1994 at 1:23:12 PM | 119     | 194  | 10    | 17  | 14   | 24     | 13     |

The century and year bytes are in excess-100 notation. The hour, minute, and second are in excess-1 notation. Dates before the Common Era (B.C.E.) are less than 100. The epoch is January 1, 4712 B.C.E. For this date, the century byte is 53 and the year byte is 88. The hour byte ranges from 1 to 24. The minute and second bytes range from 1 to 60. The time defaults to midnight (1, 1, 1). Pro\*COBOL also supports five additional datetime datetypes, as described in "Datetime and Interval Datatype Descriptors" .

##### 4.1.2.5 DECIMAL

The DECIMAL datatype represents packed decimal numbers for calculation. In COBOL, the host variable must be a signed COMP-3 field with an implied decimal point. If significant digits are lost during data conversion, the value is truncated to the declared length.

##### 4.1.2.6 DISPLAY

The DISPLAY datatype represents numeric character data. The DISPLAY datatype refers to a COBOL "DISPLAY SIGN LEADING SEPARATE" number, which requires n + 1 bytes of storage for PIC S9(n), and n + d + 1 bytes of storage for PIC S9(n)V9(d).

##### 4.1.2.7 FLOAT

The FLOAT datatype represents numbers that have a fractional part or that exceed the capacity of the INTEGER datatype. FLOAT relates to the COBOL datatypes COMP-1 (4-byte floating point) and COMP-2 (8-byte floating point).

Oracle can represent numbers with greater precision than floating point implementations because the internal format of Oracle numbers is decimal.

Note: In SQL statements, when comparing FLOAT values, use the SQL function ROUND because FLOAT stores binary (not decimal) numbers; so, fractions do not convert exactly.

##### 4.1.2.8 INTEGER

The INTEGER datatype represents numbers that have no fractional part. An integer is a signed, 2-byte, 4-byte, or 8-byte binary number. The order of the bytes in a word is platform-dependent. You must specify a length for input and output host variables. On output, if the column has a fractional part, the digits after the decimal point are truncated.

##### 4.1.2.9 LONG

The LONG datatype represents fixed-length character strings. The LONG datatype is like the VARCHAR2 datatype, except that the maximum length of a LONG value is 2147483647 bytes (two gigabytes).

##### 4.1.2.10 LONG RAW

The LONG RAW datatype represents fixed-length, binary data or byte strings. The maximum length of a LONG RAW value is 2147483647 bytes (two gigabytes).

LONG RAW data is like LONG data, except that Oracle assumes nothing about the meaning of LONG RAW data and does no character set conversions when you transmit LONG RAW data from one system to another.

##### 4.1.2.11 LONG VARCHAR

The LONG VARCHAR datatype represents variable-length character strings. LONG VARCHAR variables have a 4-byte length field followed by a string field. The maximum length of the string field is 2147483643 bytes. In an EXEC SQL VAR statement, do not include the 4-byte length field.

##### 4.1.2.12 LONG VARRAW

The LONG VARRAW datatype represents binary data or byte strings. LONG VARRAW variables have a 4-byte length field followed by a data field. The maximum length of the data field is 2147483643 bytes. In an EXEC SQL VAR statement, do not include the 4-byte length field.

##### 4.1.2.13 NUMBER

The NUMBER datatype represents the internal Oracle NUMBER format which cannot be represented by a COBOL datatype.

##### 4.1.2.14 OVER-PUNCH

OVER-PUNCH is the default signed numeric for the COBOL language. Digits are held in ASCII or EBCDIC format in radix 10, with one digit for each byte of computer storage. The sign is held in the high order nibble of one of the bytes. It is called OVER-PUNCH because the sign is "punched-over" the digit in either the first or last byte. The default sign position will be over the trailing byte. PIC S9(n)V9(m) TRAILING or PIC S9(n)V9(m) LEADING is used to specify the over-punch.

##### 4.1.2.15 RAW

The RAW datatype represents fixed-length binary data or byte strings. On most platforms, the maximum length of a RAW value is 65535 bytes.

RAW data is like CHAR data, except that Oracle assumes nothing about the meaning of RAW data and does no character set conversions when you transmit RAW data from one system to another.

##### 4.1.2.16 ROWID

The ROWID datatype is the database row identifier in COBOL. To support both logical and physical ROWIDs (as well as ROWIDs of non-Oracle tables) the Universal ROWID (UROWID) was defined. Use the SQL-ROWID pseudotype for this datatype (see "Universal ROWIDs").

You can use VARCHAR2 host variables to store ROWIDs in a readable format. When you select or fetch a ROWID into a VARCHAR2 host variable, Oracle converts the binary value to an 18-byte character string and returns it in the format:

BBBBBBBB.RRRR.FFFF

where BBBBBBBB is the block in the database file, RRRR is the row in the block (the first row is 0), and FFFF is the database file. These numbers are hexadecimal. For example, the ROWID:

    0000000E.000A.0007

points to the 11th row in the 15th block in the 7th database file.

Typically, you fetch a ROWID into a VARCHAR2 host variable, and hen compare the host variable to the ROWID pseudocolumn in the WHERE clause of an UPDATE or DELETE statement. That way, you can identify the latest row fetched by a cursor. For an example, see "[Mimicking the CURRENT OF Clause](host-tables.md)".

Note: If you need full portability or your application communicates with a non-Oracle database through Transparent Gateway, specify a maximum length of 256 (not 18) bytes when declaring the VARCHAR2 host variable. If your application communicates with a non-Oracle data source through Oracle Open Gateway, specify a maximum length of 256 bytes. Though you can assume nothing about its contents, the host variable will behave normally in SQL statements.

##### 4.1.2.17 STRING

The STRING datatype is like the VARCHAR2 datatype except that a STRING value is always terminated by a LOW-VALUE character. This datatype is usually not used in Pro\*COBOL.

##### 4.1.2.18 UNSIGNED

The UNSIGNED datatype represents unsigned integers. This datatype is usually not used in Pro\*COBOL.

##### 4.1.2.19 VARCHAR

The VARCHAR datatype represents variable-length character strings. VARCHAR variables have a 2-byte length field followed by a 65533-byte string field. However, for VARCHAR array elements, the maximum length of the string field is 65530 bytes. When you specify the length of a VARCHAR variable, be sure to include 2 bytes for the length field. For longer strings, use the LONG VARCHAR datatype. In an EXEC SQL VAR statement, do not include the 2-byte length field.

##### 4.1.2.20 VARCHAR2

The VARCHAR2 datatype represents variable-length character strings. On most platforms, the maximum length of a VARCHAR2 value is 65535 bytes.

Specify the maximum length of a VARCHAR2(n) value in bytes, not characters. So, if a VARCHAR2(n) variable stores multibyte characters, its maximum length is less than n characters.

On Input. Oracle reads the number of bytes specified for the input host variable, strips any trailing blanks, and then stores the input value in the target database column.

If the input value is longer than the defined width of the database column, Oracle generates an error. If the input value is all SPACES, Oracle treats it like a NULL.

Oracle can convert a character value to a NUMBER column value if the character value represents a valid number. Otherwise, Oracle generates an error.

On Output. Oracle returns the number of bytes specified for the output host variable, blank-padding if necessary, and then assigns the output value to the target host variable. If a NULL is returned, Oracle fills the host variable with blanks.

If the output value is longer than the declared length of the host variable, Oracle truncates the value before assigning it to the host variable. If an indicator variable is available, Oracle sets it to the original length of the output value.

Oracle can convert NUMBER column values to character values. The length of the character host variable determines precision. If the host variable is too short for the number, scientific notation is used. For example, if you select the column value 123456789 into a host variable of length 6, Oracle returns the value `1.2E08` to the host variable.

##### 4.1.2.21 VARNUM

The VARNUM datatype is similar in format to NUMBER and is usually not used in Pro\*COBOL.

##### 4.1.2.22 VARRAW

The VARRAW datatype represents variable-length binary data or byte strings. The VARRAW datatype is like the RAW datatype, except that VARRAW variables have a 2-byte length field followed by a \<= 65533-byte data field. For longer strings, use the LONG VARRAW datatype. In an EXEC SQL VAR statement, do not include the 2-byte length field. To get the length of a VARRAW variable, simply refer to its length field.

##### 4.1.2.23 SQL Pseudocolumns and Functions

SQL recognizes the pseudocolumns listed in Table 4-4, which return specific data items.

Table 4-4 Pseudocolumns and Internal Datatypes

| Pseudocolumn | Internal Datatype |
|:-------------|:------------------|
| CURRVAL      | NUMBER            |
| LEVEL        | NUMBER            |
| NEXTVAL      | NUMBER            |
| ROWID        | ROWID             |
| ROWNUM       | NUMBER            |

Pseudocolumns are not actual columns in a table. However, pseudocolumns are treated like columns, so their values must be SELECTed from a table. Sometimes it is convenient to select pseudocolumn values from a dummy table.

In addition, SQL recognizes the functions without parameters listed in Table 4-5, which also return specific data items.

Table 4-5 Functions and Internal Datatypes

| Function | Internal Datatype |
|:---------|:------------------|
| SYSDATE  | DATE              |
| UID      | NUMBER            |
| USER     | VARCHAR2          |

You can refer to SQL pseudocolumns and functions in SELECT, INSERT, UPDATE, and DELETE statements. In the following example, you use SYSDATE to compute the number of months since an employee was hired:

         EXEC SQL SELECT MONTHS_BETWEEN(SYSDATE, HIREDATE)
             INTO :MONTHS-OF-SERVICE
             FROM EMP
             WHERE EMPNO = :EMP-NUMBER
         END EXEC.

Brief descriptions of the SQL pseudocolumns and functions follow.

CURRVAL returns the current number in a specified sequence. Before you can reference CURRVAL, you must use NEXTVAL to generate a sequence number.

LEVEL returns the level number of a node in a tree structure. The root is level 1, children of the root are level 2, grandchildren are level 3, and so on.

LEVEL is used in the SELECT CONNECT BY statement to incorporate some or all the rows of a table into a tree structure. In an ORDER BY or GROUP BY clause, LEVEL segregates the data at each level in the tree.

Specify the direction in which the query walks the tree (down from the root or up from the branches) with the PRIOR operator. In the START WITH clause, you can specify a condition that identifies the root of the tree.

NEXTVAL returns the next number in a specified sequence. After creating a sequence, you can use it to generate unique sequence numbers for transaction processing. In the following example, the sequence named partno assigns part numbers:

         EXEC SQL INSERT INTO PARTS
             VALUES (PARTNO.NEXTVAL, :DESCRIPTION, :QUANTITY, :PRICE
         END EXEC.

If a transaction generates a sequence number, the sequence is incremented when you commit or roll back the transaction. A reference to NEXTVAL stores the current sequence number in CURRVAL.

ROWNUM returns a number indicating the sequence in which a row was selected from a table. The first row selected has a ROWNUM of 1, the second row has a ROWNUM of 2, and so on. If a SELECT statement includes an ORDER BY clause, ROWNUMs are assigned to the selected rows before the sort is done.

You can use ROWNUM to limit the number of rows returned by a SELECT statement. Also, you can use ROWNUM in an UPDATE statement to assign unique values to each row in a table. Using ROWNUM in the WHERE clause does not stop the processing of a SELECT statement; it just limits the number of rows retrieved. The only meaningful use of ROWNUM in a WHERE clause is:

         ... WHERE ROWNUM < constant END-EXEC.

because the value of ROWNUM increases only when a row is retrieved. The following search condition can never be met because the first four rows are not retrieved:

         ... WHERE ROWNUM = 5 END-EXEC.

SYSDATE returns the current date and time.

UID returns the unique ID number assigned to an Oracle user.

USER returns the username of the current Oracle user.

### 4.2 Datetime and Interval Datatype Descriptors

The OCI datetime and interval datatypes supported by Pro\*COBOL are briefly summarized here.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for more a more complete discussion datetime datatype descriptors

#### ANSI DATE

The `ANSI` `DATE` is based on the `DATE`, but contains no time portion. (Therefore, it also has no time zone.) `ANSI` `DATE` follows the `ANSI` specification for the `DATE` datatype. When assigning an `ANSI` `DATE` to a `DATE` or a timestamp datatype, the time portion of the Oracle `DATE` and the timestamp are set to zero. When assigning a `DATE` or a timestamp to an `ANSI` `DATE`, the time portion is ignored.

You are encouraged to instead use the `TIMESTAMP` datatype which contains both date and time.

#### TIMESTAMP

The `TIMESTAMP` datatype is an extension of the `DATE` datatype. It stores the year, month, and day of the `DATE` datatype, plus the hour, minute, and second values. It has no time zone. The `TIMESTAMP` datatype has the form:

    TIMESTAMP(fractional_seconds_precision)

where `fractional_seconds_precision` (which is optional) specifies the number of digits in the fractional part of the `SECOND` datetime field and can be a number in the range 0 to 9. The default is 6.

#### TIMESTAMP WITH TIME ZONE

`TIMESTAMP` `WITH` `TIME` `ZONE` (`TSTZ`) is a variant of `TIMESTAMP` that includes an explicit time zone displacement in its value. The time zone displacement is the difference (in hours and minutes) between local time and UTC (Coordinated Universal Time—formerly Greenwich Mean Time). The `TIMESTAMP` `WITH` `TIME` ZONE datatype has the form:

    TIMESTAMP(fractional_seconds_precision) WITH TIME ZONE

where `fractional_seconds_precision` optionally specifies the number of digits in the fractional part of the `SECOND` datetime field and can be a number in the range 0 to 9. The default is 6.

Two `TIMESTAMP` `WITH` `TIME` `ZONE` values are considered identical if they represent the same instant in UTC, regardless of the `TIME` `ZONE` offsets stored in the data.

#### TIMESTAMP WITH LOCAL TIME ZONE

`TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` (`TSLTZ`) is another variant of `TIMESTAMP` that includes a time zone displacement in its value. Storage is in the same format as for `TIMESTAMP`. This type differs from `TIMESTAMP` `WITH` `TIME` `ZONE` in that data stored in the database is normalized to the database time zone, and the time zone displacement is not stored as part of the column data. When users retrieve the data, Oracle returns it in the users' local session time zone.

The time zone displacement is the difference (in hours and minutes) between local time and UTC (Coordinated Universal Time—formerly Greenwich Mean Time). The `TIMESTAMP` `WITH` `LOCAL` `TIME` ZONE datatype has the form:

    TIMESTAMP(fractional_seconds_precision) WITH LOCAL TIME ZONE

where `fractional_seconds_precision` optionally specifies the number of digits in the fractional part of the `SECOND` datetime field and can be a number in the range 0 to 9. The default is 6.

#### INTERVAL YEAR TO MONTH

`INTERVAL` `YEAR` `TO` `MONTH` stores a period of time using the `YEAR` and `MONTH` datetime fields. The `INTERVAL` `YEAR` `TO` `MONTH` datatype has the form:

    INTERVAL YEAR(year_precision) TO MONTH

where the optional `year_precision` is the number of digits in the `YEAR` datetime field. The default value of `year_precision` is 2.

#### INTERVAL DAY TO SECOND

`INTERVAL` `DAY` `TO` `SECOND` stores a period of time in terms of days, hours, minutes, and seconds. The `INTERVAL` `DAY` `TO` `SECOND` datatype has the form:

    INTERVAL DAY (day_precision) TO SECOND(fractional_seconds_precision)

where:

- `day_precision` is the number of digits in the `DAY` datetime field. It is optional. Accepted values are 0 to 9. The default is 2.

- `fractional_seconds_precision` is the number of digits in the fractional part of the `SECOND` datetime field. It is optional. Accepted values are 0 to 9. The default is 6.

**Note:**

To avoid unexpected results in your DML operations on datetime data, you can verify the database and session time zones by querying the built-in SQL functions `DBTIMEZONE` and `SESSIONTIMEZONE`. If the time zones have not been set manually, Oracle uses the operating system time zone by default. If the operating system time zone is not a valid Oracle time zone, Oracle uses UTC as the default value.

### 4.3 Host Variables

Host variables are the key to communication between your host program and the server. Typically, a host program inputs data to the server, and the server outputs data to the program. The server stores input data in database columns and stores output data in program host variables.

#### 4.3.1 Declaring Host Variables

Host variables are declared according to COBOL rules, using the COBOL datatypes that are supported by Pro\*COBOL. COBOL datatypes must be compatible with the source/target database column.

The supported COBOL variable declarations, descriptions, corresponding external datatypes, and Oracle datatype codes are shown in Table 4-6.

Table 4-6 Host Variable Declarations

| Variable Declaration                                                                                                                                                                                                           | Description                                                                                                                                                                                                                                    | External Datatype                            | Type Code  |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------|:-----------|
| PIC X...X<br>PIC X(n)<br>PIC X...X VARYING<br>PIC X(n) VARYING                                                                                                                                                                 | fixed-length string of 1-byte characters (1)<br>n-length string of 1-byte characters<br>variable-length string of 1-byte characters (1,2)<br>variable-length (n max.) string of 1-byte characters (2)                                          | CHARF<br>VARCHAR                             | 96<br>9    |
| PIC N...N<br>PIC G...G<br>PIC N(n)<br>PIC G(n)<br>PIC N...N VARYING<br>PIC N(n) VARYING<br>PIC G...G VARYING<br>PIC G(n) VARYING                                                                                               | fixed-length string of multibyte NCHAR<br>characters (1,3)<br>n-length string of multibyte NCHAR characters<br>(3)<br>variable-length string of multibyte characters (2,3)<br>variable-length (n max.) string of multibyte<br>characters (2,3) | CHARF<br>VARCHAR                             | 96<br>9    |
| PIC S9...9 BINARY<br>PIC S9(n) BINARY<br>PIC S9...9 COMP<br>PIC S9(n) COMP<br>PIC S9...9 COMP-4<br>PIC S9(n) COMP-4                                                                                                            | integer (4,5,7)                                                                                                                                                                                                                                | INTEGER                                      | 3          |
| PIC S9...9 COMP-5<br>PIC S9(n) COMP-5                                                                                                                                                                                          | byte-swapped integer (4,5,6,7)                                                                                                                                                                                                                 | INTEGER                                      | 3          |
| COMP-1<br>COMP-2                                                                                                                                                                                                               | floating-point number (5)                                                                                                                                                                                                                      | FLOAT                                        | 4          |
| PIC S9...9\[V9...9\] COMP-3<br>PIC S9(n)\[V9(n)\] COMP-3<br>PIC S9...9\[V9...9\]<br>PACKED-DECIMAL<br>PIC S9(n)\[V9(n)\]<br>PACKED-DECIMAL                                                                                     | packed-decimal (4,5)                                                                                                                                                                                                                           | DECIMAL                                      | 7          |
| PIC S9...9\[V9...9\] DISPLAY<br>SIGN LEADING SEPARATE<br>PIC S9(n)\[V9(m)\] DISPLAY<br>SIGN LEADING SEPARATE<br>PIC S9...9\[V9...9\] DISPLAY<br>SIGN TRAILING SEPARATE<br>PIC S9(n)\[V9(m)\] DISPLAY<br>SIGN TRAILING SEPARATE | display leading (8,11)<br>display trailing (8)                                                                                                                                                                                                 | DISPLAY<br>DISPLAY TRAILING                  | 91<br>152  |
| PIC 9...9 DISPLAY<br>PIC 9(n)\[V9(m)\] DISPLAY                                                                                                                                                                                 | unsigned display (9)                                                                                                                                                                                                                           | UNSIGNED DISPLAY                             | 153        |
| PIC S9...9\[V9...9\] DISPLAY<br>SIGN TRAILING<br>PIC S9(n)\[V9(m)\] DISPLAY<br>SIGN TRAILING<br>PIC S9...9\[V9...9\] DISPLAY<br>SIGN LEADING<br>PIC S9(n)\[V9(m)\] DISPLAY<br>SIGN LEADING                                     | over-punch trailing (9)<br>over-punch leading (9)                                                                                                                                                                                              | OVER-PUNCH<br>TRAILING<br>OVER-PUNCH LEADING | 154<br>172 |
| SQL-CURSOR                                                                                                                                                                                                                     | cursor variable                                                                                                                                                                                                                                |                                              |            |
| SQL-CONTEXT                                                                                                                                                                                                                    | runtime context                                                                                                                                                                                                                                |                                              |            |
| SQL-ROWID                                                                                                                                                                                                                      | universal ROWID                                                                                                                                                                                                                                | UROWID                                       | 104        |
| SQL-BFILE                                                                                                                                                                                                                      | external binary file                                                                                                                                                                                                                           | BFILE                                        | 112        |
| SQL-BLOB                                                                                                                                                                                                                       | binary LOB                                                                                                                                                                                                                                     | BLOB                                         | 113        |
| SQL-CLOB                                                                                                                                                                                                                       | character LOB                                                                                                                                                                                                                                  | CLOB                                         | 114        |

Notes:

1.  X...X and 9...9 stand for a given number (n) of Xs or 9s. For variable-length strings, n is the maximum length.

2.  The keyword VARYING assigns the VARCHAR external datatype to a character string. For more information, see "Declaring VARCHAR Variables".

3.  Before using the PIC N or PIC G datatype in your Pro\*COBOL source files, verify that it is supported by your COBOL compiler.

4.  Only signed numbers (PIC S...) are allowed. For floating-point numbers, however, PIC strings are not accepted.

5.  Not all COBOL compilers support all of these datatypes.

6.  With COMP or COMP-5, the number cannot have a fractional part; scaled binary numbers are not supported. COMP-5 is not supported on the SPARC Solaris 64 bit platform, use COMP instead.

7.  The maximum value of the integer is n to 18. This may vary, depending on the operating system and the compilers for Pro\*Cobol and Cobol.

8.  Both DISPLAY and SIGN are optional.

9.  DISPLAY is optional

10. If TRAILING is omitted, the embedded sign position is operating-system dependent.

11. LEADING is optional.

In Table 4-6 and Table 4-7 the symbols '\[' and '\]' denote that an optional entry is contained inside. The symbols '{' and '}' denote that a choice must be made between tokens separated by the symbol '\|'.

Table 4-7 shows all the COBOL datatypes that can be converted to and from each internal datatype.

Table 4-7 Compatible Oracle Internal Datatypes

| Internal Datatype                        | Notes             | COBOL Datatype                                                                                                                                                                                                                                                                                                                                                | Description                                                                                                                                                                                      |
|:-----------------------------------------|:------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CHAR(x) VARCHAR2(y)                      | (1)<br>(1)        | PIC X(n)<br>PIC X...X<br>PIC X(n) VARYING<br>PIC X...X VARYING<br>PIC S9...9 COMP<br>PIC S9(n) COMP<br>PIC S9...9 BINARY<br>PIC S9(n) BINARY<br>PIC S9...9 COMP-5<br>PIC S9(n) COMP-5<br>COMP-1<br>COMP-2<br>PIC S9...9\[V9...9\] COMP-3<br>PIC S9(n)\[V9(n)\] COMP-3<br>PIC S9...9\[V9...9\] DISPLAY<br>PIC S9(n)\[V9(n)\] DISPLAY                           | character string<br>n-character string<br>variable-length string<br>integer<br>integer<br>integer<br>floating point number<br>packed decimal<br>display                                          |
| NCHAR(u) NVARCHAR2(v)                    | (2)<br>(2)        | PIC {N...N \| G...G}<br>PIC { N(n) \| G(n)}                                                                                                                                                                                                                                                                                                                   | national character string<br>n-national character string                                                                                                                                         |
| BLOB<br>CLOB<br>NCLOB<br>BFILE           |                   | SQL-BLOB<br>SQL-CLOB<br>SQL-NCLOB<br>SQL-BFILE                                                                                                                                                                                                                                                                                                                | binary LOB<br>character LOB<br>national character LOB<br>external binary file                                                                                                                    |
| NUMBER<br>NUMBER (p,s)                   | \(3\)             | PIC S9...9 COMP<br>PIC S9(n) COMP<br>PIC S9...9 BINARY<br>PIC S9(n) BINARY<br>PIC S9...9 COMP-5<br>PIC S9(n) COMP-5<br>COMP-1<br>COMP-2<br>PIC S9...9V9...9 COMP-3<br>PIC S9(n)V9(n) COMP-3<br>PIC S9...9V9...9 DISPLAY<br>PIC S9(n)V9(n) DISPLAY<br>PIC \[X...X \| N...N \| G...G\]<br>PIC \[X(n) \| N(n) \| G(n)\]<br>PIC X...X VARYING<br>PIC X(n) VARYING | integer<br>integer<br>integer<br>floating point number<br>packed decimal<br>display<br>character string (4)<br>n-character string (4)<br>variable-length string<br>n-byte variable-length string |
| DATE<br>LONG<br>RAW<br>LONG RAW<br>ROWID | (5)<br>(1)<br>(6) | PIC X(n)<br>PIC X...X<br>PIC X(n)<br>PIC X(n) VARYING<br>PIC X...X VARYING<br>SQL-ROWID                                                                                                                                                                                                                                                                       | n-byte character string<br>character string<br>n-byte variable-length string<br>universal rowid                                                                                                  |

Notes:

Bug 7225844 - Following para - substituted 1\<= x \< =2000 bytes, default is 1

for

\<= x \< =2000 bytes, default is 1.

1.  1\<= x \< =2000 bytes, default is 1. 1\<=y \<=4000 bytes, default is 1.

2.  1\<=u\<=2000 bytes, default is 1. 1\<=v\<=4000 bytes, default is 1.

3.  p ranges from 2 to 38. s ranges from -84 to 127.

4.  Strings can be converted to NUMBERs only if they consist of convertible characters — 0 to 9, period (.), +, -, E, e. The Globalization Support (formerly called National Language Support or NLS) settings for your system might change the decimal point from a period (.) to a comma (,).

5.  When converted to a string type, the default size of a DATE depends on the NCHAR settings in effect on your system. When converted to a binary value, the length is 7 bytes.

6.  When converted to a string type, a ROWID requires from 18 to 4000 bytes. ROWID can also be converted to a character type. Oracle recommends the use of SQL-ROWID for all new programs.

##### 4.3.1.1 Example Declarations

The following example declares several host variables for later use:

        ...
     01  STR1  PIC X(3).
     01  STR2  PIC X(3) VARYING.
     01  NUM1  PIC S9(5) COMP.
     01  NUM2  COMP-1.
     01  NUM3  COMP-2.
         ...

You can also declare one-dimensional tables of simple COBOL types, as the next example shows:

         ...
     01  XMP-TABLES.
         05  TAB1  PIC XXX OCCURS 3 TIMES.
         05  TAB2  PIC XXX VARYING OCCURS 3 TIMES.
         05  TAB3  PIC S999 COMP-3 OCCURS 3 TIMES.
         ...

##### 4.3.1.2 Initialization

You can initialize host variables, except pseudotype host variables, using the VALUE clause, as shown in the following example:

     01  USERNAME    PIC X(10) VALUE "SCOTT".
     01  MAX-SALARY  PIC S9(4) COMP VALUE 5000.


If a string value assigned to a character variable is shorter than the declared length of the variable, the string is blank-padded on the right. If the string value assigned to a character variable is longer than the declared length, the string is truncated.

No error or warning is issued, but any VALUES clause on a pseudotype variable is ignored and discarded.

##### 4.3.1.3 Restrictions

You cannot use alphabetic character (PIC A) variables or edited data items as host variables. Therefore, the following variable declarations cannot be made for host variables:

         ....
     01  AMOUNT-OF-CHECK  PIC ****9.99.
     01  FIRST-NAME       PIC A(10).
     01  BIRTH-DATE       PIC 99/99/99.

         ....

#### 4.3.2 Referencing Host Variables

Host variables are used in SQL data manipulation statements. A host variable must be prefixed with a colon (:) in SQL statements but must not be prefixed with a colon in COBOL statements, as this example shows:

     WORKING-STORAGE SECTION.
         ...
         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01  EMP-NUMBER  PIC S9(4) COMP VALUE ZERO.
     01  EMP-NAME    PIC X(10) VALUE SPACE.
     01  SALARY      PIC S9(5)V99 COMP-3.
         EXEC SQL END DECLARE SECTION END-EXEC.
         ...
     PROCEDURE DIVISION.
         ...
         DISPLAY "Employee number? " WITH NO ADVANCING.
         ACCEPT EMP-NUMBER.
         EXEC SQL SELECT ENAME, SAL
             INTO :EMP-NAME, :SALARY FROM EMP
             WHERE EMPNO = :EMP-NUMBER
         END-EXEC.
         COMPUTE BONUS = SALARY / 10.
         ...

Though it might be confusing, you can give a host variable the same name as a table or column, as the following example shows:

     WORKING-STORAGE SECTION.
         ...
         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01  EMPNO  PIC S9(4) COMP VALUE ZERO.
     01  ENAME  PIC X(10) VALUE SPACE.
     01  COMM   PIC S9(5)V99 COMP-3.
         EXEC SQL END DECLARE SECTION END-EXEC.
         ...
     PROCEDURE DIVISION.
         ...
         EXEC SQL SELECT ENAME, COMM
             INTO :ENAME, :COMM FROM EMP
             WHERE EMPNO = :EMPNO
         END-EXEC.

##### 4.3.2.1 Group Items as Host Variables

Pro\*COBOL allows the use of group items in embedded SQL statements. Group items with elementary items (containing only one level) can be used as host variables. The host group items (also referred to as host structures) can be referenced in the INTO clause of a SELECT or a FETCH statement, and in the VALUES list of an INSERT statement. When a group item is used as a host variable, only the group name is used in the SQL statement. For example, given the following declaration

     01  DEPARTURE.
         05 HOUR    PIC X(2).
         05 MINUTE  PIC X(2).

the following statement is valid:

         EXEC SQL SELECT DHOUR, DMINUTE
             INTO :DEPARTURE
             FROM SCHEDULE
             WHERE ...

The order that the members are declared in the group item must match the order that the associated columns occur in the SQL statement, or in the database table if the column list in the INSERT statement is omitted. Using a group item as a host variable has the semantics of substituting the group item with elementary items. In the preceding example, it would mean substituting :DEPARTURE with :DEPARTURE.HOUR, :DEPARTURE.MINUTE.

Group items used as host variables can contain host tables. In the following example, the group item containing tables is used to INSERT three entries into the SCHEDULE table:

     01  DEPARTURE.
         05  HOUR    PIC X(2) OCCURS 3 TIMES.
         05  MINUTE  PIC X(2) OCCURS 3 TIMES.
     ...
         EXEC SQL INSERT INTO SCHEDULE (DHOUR, DMINUTE)
              VALUES (:DEPARTURE) END-EXEC.

If VARCHAR=YES is specified, Pro\*COBOL will recognize implicit VARCHARs. If the nested group item declaration resembles a VARCHAR host variable, then the entire group item is treated like an elementary item of VARYING type. See "[VARCHAR](precompiler-options.md)".

When referencing elementary items instead of the group items as host variables elementary names need not be unique because you can qualify them using the following syntax:

    group_item.elementary_item

This naming convention is allowed only in SQL statements. It is similar to the IN (or OF) clause in COBOL, examples of which follow:

              MOVE MINUTE IN DEPARTURE TO MINUTE-OUT.
              DISPLAY HOUR OF DEPARTURE.

The COBOL IN (or OF) clause is not allowed in SQL statements. Qualify elementary names to avoid ambiguity. For example:

         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01  DEPARTURE.
         05  HOUR    PIC X(2).
         05  MINUTE  PIC X(2).
     01  ARRIVAL.
         05  HOUR    PIC X(2).
         05  MINUTE  PIC X(2).
         EXEC SQL END DECLARE SECTION END-EXEC.
      ...
         EXEC SQL SELECT DHR, DMIN INTO :DEPARTURE.HOUR, :DEPARTURE.MINUTE
             FROM TIMETABLE
             WHERE ...

##### 4.3.2.2 Restrictions

A host variable cannot substitute for a column, table, or other object in a SQL statement and must not be an Oracle reserved word. See [Reserved Words\_ Keywords\_ and Namespaces](reserved-words-keywords-and-namespaces.md) for a list of reserved words and keywords.

### 4.4 Indicator Variables

You can associate any host variable with an optional indicator variable. Each time the host variable is used in a SQL statement, a result code is stored in its associated indicator variable. Thus, indicator variables let you monitor host variables.

You use indicator variables in the VALUES or SET clause to assign NULLs to input host variables and in the INTO clause to detect NULLs (or truncated values for character columns) in output host variables.

#### 4.4.1 Using Indicator Variables

Here are the values indicator variables can take on.

##### 4.4.1.1 On Input

The values your program can assign to an indicator variable have the following meanings:

| Indicator Variables | Description                                                                       |
|:--------------------|:----------------------------------------------------------------------------------|
| -1                  | Oracle will assign a NULL to the column, ignoring the value of the host variable. |
| \>=0                | Oracle will assign the value of the host variable to the column.                  |

##### 4.4.1.2 On Output

The values Oracle can assign to an indicator variable have the following meanings:

| Indicator Variables | Description                                                                                                                                                                                    |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -1                  | The column value is NULL, so the value of the host variable is indeterminate.                                                                                                                  |
| 0                   | Oracle assigned an intact column value to the host variable.                                                                                                                                   |
| \>0                 | Oracle assigned a truncated column value to the host variable. The integer returned by the indicator variable is the original length of the column value, and SQLCODE in SQLCA is set to zero. |
| -2                  | Oracle assigned a truncated column variable to the host variable, but the original column value could not be determined (a LONG column, for example).                                          |

#### 4.4.2 Declaring Indicator Variables

An indicator variable must be explicitly declared as PIC S9(4) COMP and must not be a reserved word. In the following example, you declare an indicator variable named COMM-IND (the name is arbitrary):

     WORKING-STORAGE SECTION.
     ...
     01  EMP-NAME    PIC X(10) VALUE SPACE.
     01  SALARY      PIC S9(5)V99 COMP-3.
     01  COMMISSION  PIC S9(5)V99 COMP-3.
     01  COMM-IND    PIC S9(4) COMP.
     ...

#### 4.4.3 Referencing Indicator Variables

In SQL statements, an indicator variable must be prefixed with a colon and appended to its associated host variable. In COBOL statements, an indicator variable must not be prefixed with a colon or appended to its associated host variable. An example follows:

         EXEC SQL SELECT SAL, COMM
            INTO :SALARY, :COMMISSION:COMM-IND FROM EMP
            WHERE EMPNO = :EMP-NUMBER
         END-EXEC.
         IF COMM-IND = -1
            COMPUTE PAY = SALARY
         ELSE
            COMPUTE PAY = SALARY + COMMISSION.


To improve readability, you can precede any indicator variable with the optional keyword INDICATOR. You must still prefix the indicator variable with a colon. The correct syntax is

    :host_variableINDICATOR:indicator_variable

and is equivalent to

    :host_variable:indicator_variable

You can use both forms of expression in your host program.

##### 4.4.3.1 Use in Where Clauses

Indicator variables cannot be used in the WHERE clause to search for NULLs. For example, the following DELETE statement triggers an error at run time:

    *    Set indicator variable.
         COMM-IND = -1
         EXEC SQL
             DELETE FROM EMP WHERE COMM = :COMMISSION:COMM-IND
         END-EXEC.

The correct syntax follows:

         EXEC SQL
             DELETE FROM EMP WHERE COMM IS NULL
         END-EXEC.

##### 4.4.3.2 Avoid Error Messages

If you SELECT or FETCH a NULL into a host variable that has no indicator, Oracle issues an error message.

You can disable the error message by also specifying UNSAFE_NULL=YES on the command line.

**Related Topics**

- [Precompiler Options](precompiler-options.md)

##### 4.4.3.3 ANSI Requirements

When MODE=ORACLE, if you SELECT or FETCH a truncated column value into a host variable that is not associated with an indicator variable, Oracle issues an error message.

However, when MODE={ANSI \| ANSI14 \| ANSI13}, no error is generated.

**See Also:**

[Embedded SQL](embedded-SQL.md) for values for indicator variables.

##### 4.4.3.4 Indicator Variables for Multibyte NCHAR Variables

Indicator variables for multibyte NCHAR character variables can be used as with any other host variable. However, a positive value (the result of a SELECT or FETCH was truncated) represents the string length in multibyte characters instead of 1-byte characters.

##### 4.4.3.5 Indicator Variables with Host Group Items

To use indicator variables with a host group item, either setup a second group item that contains an indicator variable for each nullable variable in the group item or use a table of half-word integer variables. You do NOT have to have an indicator variable for each variable in the group item, but the nullable fields which you wish to use indicators for must be placed at the beginning of the data group item. The following indicator group item can be used with the DEPARTURE group item:

     01  DEPARTURE-IND.
         05  HOUR-IND   PIC S9(4) COMP.
         05  MINUTE-IND PIC S9(4) COMP.

If you use an indicator table, you do NOT have to declare a table of as many elements as there are members in the host group item. The following indicator table can be used with the DEPARTURE group item:

     01 DEPARTURE-IND PIC S9(4) COMP OCCURS 2 TIMES.

Reference the indicator group item in the SQL statement in the same way that a host indicator variable is referenced:

         EXEC SQL SELECT DHOUR, DMINUTE
            INTO :DEPARTURE:DEPARTURE-IND
              FROM SCHEDULE
                WHERE ...

When the query completes, the NULL/NOT NULL status of each selected component is available in the host indicator group item. The restrictions on indicator host variables and the ANSI requirements also apply to host indicator group items.

### 4.5 VARCHAR Variables

COBOL string datatypes are fixed length. However, Pro\*COBOL lets you declare a variable-length string pseudotype called VARCHAR. A VARCHAR variable is a pseudotype that enables you to specify the exact length of the data stored in the database and to specify the exact length of the data to be passed to the database.

#### 4.5.1 Declaring VARCHAR Variables

You define a VARCHAR host variable by adding the keyword VARYING to its declaration, as shown in the following example:

     01  ENAME  PIC X(15) VARYING.

**Note:**

PIC N and PIC G are not allowed in definitions that use VARYING. To see how to correctly use PIC N and PIC G in VARCHAR variables, see "Implicit VARCHAR Group Items".

**Note:**

Pro\*COBOL adds 4 characters to variable names declared with VARYING. So, if your COBOL compiler supports a variable name length of `n`, then Pro\*COBOL supports a variable name that is four characters less (`n`-4).

The COBOL VARYING phrase is used in PERFORM and SEARCH statements to increment subscripts and indexes. Do not confuse this with the Pro\*COBOL VARYING clause in the preceding example.

VARCHAR is an extended Pro\*COBOL datatype or pre-declared group item. For example, Pro\*COBOL expands the VARCHAR declaration

     01  ENAME  PIC X(15) VARYING.

into a group item with length and string fields, as follows:

     01  ENAME.
         05  ENAME-LEN  PIC S9(4) COMP.
         05  ENAME-ARR  PIC X(15).

The length field (suffixed with -LEN) holds the current length of the value stored in the string field (suffixed with -ARR). The maximum length in the VARCHAR host-variable declaration must be in the range of 1 to 9,999 bytes.

The advantage of using VARCHAR variables is that you can explicitly set and reference the length field. With input host variables, Pro\*COBOL reads the value of the length field and uses that many characters of the string field. With output host variables, Pro\*COBOL sets the length value to the length of the character string stored in the string field.

#### 4.5.2 Implicit VARCHAR Group Items

Pro\*COBOL implicitly recognizes some group items as VARCHAR host variables when the precompiler option VARCHAR=YES is specified on the command line. For variable-length single-byte character types, use the following structure (length expressed in single-byte characters):

      nn   data-name-1.
           49  data-name-2 PIC S9(4) COMP.
           49  data-name-3 PIC X(length).

nn must be 01 through 48.

For variable-length multibyte NCHAR characters, use these formats (length is expressed in double-byte characters):

     nn  DATA-NAME-1.
         49 DATA-NAME-2  PIC  S9(4)  COMP.
         49 DATA-NAME-3  PIC  N(length).

     nn  DATA-NAME-1.
         49 DATA-NAME-2  PIC  S9(4)  COMP.
         49 DATA-NAME-3  PIC  G(length).

    The elementary items in these group-item structures must be declared as level 49 for Pro*COBOL to recognize them as VARCHAR host variables.

The VARCHAR=YES command line option must be specified for Pro\*COBOL to recognize the extended form of the VARCHAR group items. If VARCHAR=NO, then any declarations that resemble the preceding formats will be interpreted as regular group items. If VARCHAR=YES and a group item declaration format looks similar (but not identical) to the extended VARCHAR format, then the item will be interpreted as a regular group item rather than a VARCHAR group item. For example, if VARCHAR=YES is specified and you write the following:

      01  LASTNAME.
          48 LASTNAME-LEN  PIC S9(4) COMP.
          48 LASTNAME-TEXT PIC X(15).

then, since level 48 instead of 49 is used for the group item elements, the item is interpreted as a regular group item rather than a VARCHAR group item.

**See Also:**

[Precompiler Options](precompiler-options.md) for more information about the Pro\*COBOL VARCHAR option.

#### 4.5.3 Referencing VARCHAR Variables

In SQL statements, you reference a VARCHAR variable using the group name prefixed with a colon, as the following example shows:

     WORKING-STORAGE SECTION.
         ...
         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
             ...
     01  PART-NUMBER  PIC X(5).
     01  PART-DESC    PIC X(20) VARYING.
         EXEC SQL END DECLARE SECTION END-EXEC.
         ...
     PROCEDURE DIVISION.
         ...

         EXEC SQL
             SELECT PDESC INTO :PART-DESC FROM PARTS
             WHERE PNUM = :PART-NUMBER
         END-EXEC.

After the query executes, PART-DESC-LEN holds the actual length of the character string retrieved from the database and stored in PART-DESC-ARR.

### 4.6 Handling Character Data

This section explains how Pro\*COBOL handles character host variables. There are two kinds of single-byte character host variables and two kinds of multibyte Globalization Support (formerly called NLS) character host variables:

- PIC X(n) (or PIC X...X)

- PIC X(n) VARYING (or PIC X...X VARYING)

- PIC N(n) (or PIC N...N) or PIC G(n) (or PIC G...G) 

**Note:**

Before using multibyte NCHAR datatypes, verify that the PIC N or PIC G datatype is supported by your COBOL compiler.

#### 4.6.1 Default for PIC X

The default datatype of PIC X variables is CHARF (was VARCHAR2 before release 8.0.) The precompiler command line option, PICX, is provided for backward compatibility. PICX can be entered only on the command line or in a configuration file. See "[PICX](precompiler-options.md)" for more details.

#### 4.6.2 Effects of the PICX Option

The PICX option determines how Pro\*COBOL treats data in character strings. The PICX option enables your program to use ANSI fixed-length strings or to maintain compatibility with previous versions of the database server and Pro\*COBOL.

You must use PICX=VARCHAR2 (not the default) to obtain the same results as releases of Pro\*COBOL before 8.0. Or, use

         EXEC SQL varname IS VARCHAR2 END-EXEC.

for each variable.

#### 4.6.3 Fixed-Length Character Variables

Fixed-length character variables are declared using the PIC X(n) and PIC G(n) and PIC N(n) datatypes. These types of variables handle character data based on their roles as input or output variables.

##### 4.6.3.1 On Input

When PICX=VARCHAR2, the program interface strips trailing blanks before sending the value to the database. If you insert into a fixed-length CHAR column, Pro\*COBOL re-appends trailing blanks up to the length of the database column. However, if you insert into a variable-length VARCHAR2 column, Pro\*COBOL never appends blanks.

When PICX=CHARF, trailing blanks are never stripped.

Host input variables for multibyte Globalization Support data are not stripped of trailing double-byte spaces. The length component is assumed to be the length of the data in characters, not bytes.

Make sure that the input value is not trailed by extraneous characters. Normally, this is not a problem because when a value is ACCEPTed or MOVEd into a PIC X(n) variable, COBOL appends blanks up to the length of the variable.

The following example illustrates the point:

     WORKING-STORAGE SECTION.
         ...
         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01  EMPLOYEES.
         05  EMP-NAME     PIC X(10).
         05  DEPT-NUMBER  PIC S9(4) VALUE 20 COMP.
         05  EMP-NUMBER   PIC S9(9) VALUE 9999 COMP.
         05  JOB-NAME     PIC X(8).
                 ...
         EXEC SQL END DECLARE SECTION END-EXEC.
         ...
     PROCEDURE DIVISION.
         ...
         DISPLAY "Employee name? " WITH NO ADVANCING.
         ACCEPT EMP-NAME.
    *    Assume that the name MILLER was entered
    *    EMP-NAME contains "MILLER    " (4 trailing blanks)
         MOVE "SALES" TO JOB-NAME.
    *    JOB-NAME now contains "SALES   " (3 trailing blanks)
         EXEC SQL INSERT INTO EMP (EMPNO, ENAME, DEPTNO, JOB)
             VALUES (:EMP-NUMBER, :EMP-NAME, :DEPT-NUMBER, :JOB-NAME
         END-EXEC.
         ...

If you precompile the last example with PICX=VARCHAR2 and the target database columns are VARCHAR2, the program interface strips the trailing blanks on input and inserts just the 6-character string "MILLER" and the 5-character string "SALES" into the database. However, if the target database columns are CHAR, the strings are blank-padded to the width of the columns.

If you precompile the last example with PICX=CHARF and the JOB column is defined as CHAR(10), the value inserted into that column is "SALES#####" (five trailing blanks). However, if the JOB column is defined as VARCHAR2(10), the value inserted is "SALES###" (three trailing blanks), because the host variable is declared as PIC X(8). This might not be what you want, so be careful.

##### 4.6.3.2 On Output

The PICX option has no effect on output to fixed-length character variables. When you use a PIC X(n) variable as an output host variable, Pro\*COBOL blank-pads it. In our example, when your program fetches the string "MILLER" from the database, EMP-NAME contains the value "MILLER####" (with four trailing blanks). This character string can be used without change as input to another SQL statement.

#### 4.6.4 Varying-Length Variables

VARCHAR variables handle character data based on their roles as input or output variables.

##### 4.6.4.1 On Input

When you use a VARCHAR variable as an input host variable, your program must assign values to the length and string fields of the expanded VARCHAR declaration, as shown in the following example:

         IF ENAME-IND = -1
             MOVE "NOT AVAILABLE" TO ENAME-ARR
             MOVE 13 TO ENAME-LEN.

You need not blank-pad the string variable. In SQL operations, Pro\*COBOL uses exactly the number of characters given by the length field, counting any spaces.

##### 4.6.4.2 On Output

When you use a VARCHAR variable as an output host variable, Pro\*COBOL sets the length field. An example follows:

     WORKING-STORAGE SECTION.
         ...
         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01  EMPNO  PIC S9(4) COMP.
     01  ENAME  PIC X(15) VARYING.
             ...
         EXEC SQL END DECLARE SECTION END-EXEC.
         ...
     PROCEDURE DIVISION.
         ...
         EXEC SQL
             SELECT ENAME INTO :ENAME FROM EMP
             WHERE EMPNO = :EMPNO
         END-EXEC.
         IF ENAME-LEN = 0
             MOVE FALSE TO VALID-DATA.

An advantage of VARCHAR variables over fixed-length strings is that the length of the value returned by Pro\*COBOL is available right away. With fixed-length strings, to get the length of the value, your program must count the number of characters.

Host output variables for multibyte NCHAR data are not padded at all. The length of the buffer is set to the length in bytes, not characters.

**Note:**

When `PICN_ENDIAN=OS`, the length of the buffer for multibyte NCHAR data is set to the length in characters, not bytes.

### 4.7 Universal ROWIDs

There are two kinds of table organization used in the database server: heap tables and index-organized tables.

Heap tables are the default. This is the organization used in all tables before Oracle. The physical row address (ROWID) is a permanent property that is used to identify a row in a heap table. The external character format of the physical ROWID is an 18-byte character string in base-64 encoding.

An index-organized table does not have physical row addresses as permanent identifiers. A logical ROWID is defined for these tables. When you use a SELECT ROWID ... statement from an index-organized table the ROWID is an opaque structure that contains the primary key of the table, control information, and an optional physical "guess". You can use this ROWID in a SQL statement containing a clause such as "WHERE ROWID = ..." to retrieve values from the table.

The universal ROWID was introduced in the Oracle 8.1 Database release. Universal ROWID can be used for both physical ROWID and logical ROWID. You can use universal ROWIDs to access data in heap tables, or index-organized tables, since the table organization can change with no effect on applications. The column datatype used for ROWID is UROWID(length), where length is optional.

Use the universal ROWID in all new applications.

Declare a universal ROWID, which uses the pseudotype SQL-ROWID, this way:

     01  MY-ROWID SQL-ROWID.

Memory for the universal ROWID is allocated with the ALLOCATE statement:

         EXEC SQL ALLOCATE :MY-ROWID END-EXEC.

Use MY-ROWID in SQL DML statements like this:

         EXEC SQL SELECT ROWID INTO :MY-ROWID FROM MYTABLE WHERE ... END-EXEC.
    ...
         EXEC SQL UPDATE MYTABLE SET ... WHERE ROWID = :MY-ROWID END-EXEC.
    ...

Free the memory when you no longer need it with the FREE directive:

         EXEC SQL FREE :MY-ROWID END-EXEC.

You also have the option of using a character host variable of width between 18 and 4000 as the host bind variable for universal ROWID. Character-based universal ROWIDs are supported for heap tables only for backward compatibility. Because a universal ROWID can be variable length there can be truncation when it is selected.

Use the character variable like this:

     01  MY-ROWID-CHAR PIC X(4000) VARYING.
    ...
         EXEC SQL ALLOCATE :MY-ROWID-CHAR END-EXEC.
         EXEC SQL SELECT ROWID INTO :MY-ROWID-CHAR FROM MYTABLE WHERE ... END-EXEC.
    ...
         EXEC SQL UPDATE MYTABLE SET ... WHERE ROWID = :MY-ROWID-CHAR END-EXEC.
    ...
         EXEC SQL FREE :MY-ROWID-CHAR END-EXEC.

**See Also:**

- [Oracle Database Concepts](../cncpt/tables-and-table-clusters.md) for more information on universal ROWIDs.

- "[Positioned Update](embedded-SQL.md)" for an example of a positioned update using the universal ROWID.

#### 4.7.1 Subprogram SQLROWIDGET

The Oracle subprogram SQLROWIDGET enables you to retrieve the ROWID of the last row inserted, updated, or selected. SQLROWIDGET requires a context or NULL and a ROWID as its arguments.

To use the default context, pass the figurative constant NULL as the first parameter in the call to SQLROWIDGET.

Note that the universal ROWID must be declared and allocated before the call. The context, if used must be declared and allocated before the call. Here is the syntax:

         CALL "SQLROWIDGET" USING NULL rowid.

or

         CALL "SQLROWIDGET" USING context rowid.

where

context (IN)

is the runtime context variable, of pseudotype SQL-CONTEXT, or the figurative constant NULL for the default context. For a discussion of runtime contexts, see "[Embedded SQL Statements and Directives for Runtime Contexts](multithreaded-applications.md)".

rowid (OUT)

is a universal ROWID variable, of pseudotype SQL-ROWID. When a normal execution finishes, this will point to a valid universal ROWID. In case of an error, rowid is undefined.

Here is a sample showing its use with the default context:

     01  MY-ROWID SQL-ROWID.
     ...
         EXEC SQL ALLOCATE :MY-ROWID END-EXEC.

    * INSERT, or UPDATE or DELETE Goes here:
     ...
         CALL "SQLROWIDGET" USING NULL MY-ROWID.
    * MY-ROWID now has the universal rowid descriptor for the last row
     ...
         EXEC SQL FREE :MY-ROWID END-EXEC.
     ...

If your compiler does not allow using the figurative constant NULL in a CALL statement, you can declare a variable with picture S9(9) COMP VALUE 0 and use that with the BY VALUE clause in the call to SQLROWIDGET, as follows:

     01 NULL-CONTEXT  PIC S9(9) COMP VALUE ZERO.
     01 MY-ROWID SQLROWID.
    ....
            CALL "SQLROWIDGET" USING BY VALUE NULL-CONTEXT BY REFERENCE MY-ROWID.

### 4.8 Globalization Support

Although the widely-used 7-bit or 8-bit ASCII and EBCDIC character sets are adequate to represent the Roman alphabet, some Asian languages, such as Japanese, contain thousands of characters. These languages require 16 bits or more, to represent each character. How does Oracle deal with such dissimilar languages?

Oracle provides Globalization Support (formerly called National Language Support or NLS), which lets you process single-byte and multibyte character data and convert between character sets. It also lets your applications run in different language environments. With Globalization Support, number and date formats adapt automatically to the language conventions specified for a user session. Thus, Globalization Support enables users around the world to interact with Oracle in their native languages.

You control the operation of language-dependent features by specifying various Globalization Support parameters. You can set default parameter values in the initialization file. Table 4-8 shows what each Globalization Support parameter specifies.

Table 4-8 Globalization Support Parameters

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

The main parameters are NLS_LANGUAGE and NLS_TERRITORY. NLS_LANGUAGE specifies the default values for language-dependent features, which include

- language for Server messages

- language for day and month names

- sort sequence

NLS_TERRITORY specifies the default values for territory-dependent features, which include

- Date format

- Decimal character

- Group separator

- Local currency symbol

- ISO currency symbol

You can control the operation of language-dependent Globalization Support features for a user session by specifying the parameter NLS_LANG as follows

    NLS_LANG = language_territory.character set

where language specifies the value of NLS_LANGUAGE for the user session, territory specifies the value of NLS_TERRITORY, and character set specifies the encoding scheme used for the terminal. An encoding scheme (usually called a character set or code page) is a range of numeric codes that corresponds to the set of characters a terminal can display. It also includes codes that control communication with the terminal.

You define NLS_LANG as an environment variable (or the equivalent on your system). For example, on UNIX using the C shell, you might define NLS_LANG as follows:

    setenv NLS_LANG French_France.WE8ISO8859P1


To change the values of Globalization Support parameters during a session, you use the ALTER SESSION statement as follows:

    ALTER SESSION SET nls_parameter = value

Pro\*COBOL fully supports all the Globalization Support features that allow your applications to process multilingual data stored in an Oracle database. For example, you can declare foreign-language character variables and pass them to string functions such as INSTRB, LENGTHB, and SUBSTRB. These functions have the same syntax as the INSTR, LENGTH, and SUBSTR functions, respectively, but operate on a per-byte basis rather than a per-character basis.

You can use the functions NLS_INITCAP, NLS_LOWER, and NLS_UPPER to handle special instances of case conversion. And, you can use the function NLSSORT to specify WHERE-clause comparisons based on linguistic rather than binary ordering. You can even pass Globalization Support parameters to the TO_CHAR, TO_DATE, and TO_NUMBER functions.

**See Also:**

[ Oracle Database Globalization Support Guide](../nlspg/index.md) for more information about Globalization Support.

### 4.9 Unicode Support for Pro\*COBOL

Pro\*COBOL does not support source code written with Unicode. If you want to set UTF8 to locale, source code should be written with only ASCII code.

If you want to use Unicode variables, you need to remember the following:

- Pro\*COBOL does not support "USAGE NATIONAL". If you want to use Unicode variables, use -C NSYMBOL="NATIONAL" for compiling Cobol programs with MF Cobol.

- Unicode can be used with PIC X and PIC N:

  - AL32UTF8 and UTF8 can be used with PIC X.

  - AL16UTF16 can be used with PIC N.

- Equate NLS_NCHAR environment variable to the client-side character set used in PIC N. If NLS_NCHAR is not set, then NLS_LANG is used.

- Equate NLS_LANG environment variable to the client-side character set used in PIC X.

- AL16UTF16, JA16SJISFIXED and JA16EUCFIXED can be set in NLS_NCHAR.

- JA16SJIS and JA16SJISTILDE can also be set in NLS_NCHAR.

- JA16EUC and JA16EUCTILDE cannot be used with NLS_NCHAR.

**See Also:**

For the character sets that can be used in NLS_LANG, refer to the Globalization Support Guide.

PICX=charf/varchar2 works for unicode PIC X variables and for PIC N it works with the restrictions mentioned in the aforementioned list.

#### 4.9.1 NLS_LOCAL=YES Restrictions

When the precompiler option NLS_LOCAL is YES, the runtime library (SQLLIB) performs blank-padding and blank-stripping for Globalization Support multibyte datatypes.

When NLS_LOCAL=YES, multibyte NCHAR features are not supported within a PL/SQL block. These features include N-quoted character literals and fixed-length character variables.

These restrictions then apply:

Tables Disallowed. Host variables declared using the PIC N or PIC G datatype must not be tables.

No Odd-Byte Widths. Oracle CHAR columns should not be used to store multibyte NCHAR characters. A run-time error is generated if data with an odd number of bytes is FETCHed from a single-byte column into a multibyte NCHAR host variable.

No Host Variable Equivalencing. Multibyte NCHAR character variables cannot be equivalenced using an EXEC SQL VAR statement.

No Dynamic SQL. Dynamic SQL is not available for NCHAR multibyte character string host variables in Pro\*COBOL.

Functions should not be used on columns that store multibyte Globalization Support data.

#### 4.9.2 Character Strings in Embedded SQL

A multibyte Globalization Support character string in an embedded SQL statement consists of the letter N, followed by the string enclosed in single quotes.

For example,

         EXEC SQL
             SELECT EMPNO INTO :EMP-NUM FROM EMP
             WHERE ENAME=N'NLS_string'
         END-EXEC.

#### 4.9.3 Embedded DDL

When the precompiler option, NLS_LOCAL=YES, columns storing NCHAR data cannot be used in embedded data definition language (DDL) statements. This restriction cannot be enforced when precompiling, so the use of extended column types, such as NCHAR, within embedded DDL statements results in an execution error rather than a precompile error.

**Related Topics**

- [Precompiler Options](precompiler-options.md)

#### 4.9.4 Blank Padding

When a Pro\*COBOL character variable is defined as a multibyte Globalization Support variable, the following blank padding and blank stripping rules apply, depending on the external datatype of the variable.

CHARF. Input data is stripped of any trailing double-byte spaces. However, if a string consists only of multibyte spaces, a single multibyte space is left in the buffer to act as a sentinel.

Output host variables are blank padded with multibyte spaces.

VARCHAR. On input, host variables are not stripped of trailing double-byte spaces. The length component is assumed to be the length of the data in characters, not bytes.

On output, the host variable is not blank padded at all. The length of the buffer is set to the length of the data in characters, not bytes.

STRING/LONG VARCHAR. These host variables are not supported for Globalization Support data, since they can only be specified using dynamic SQL or datatype equivalencing, neither of which is supported for Globalization Support data.

**Related Topics**

- Handling Character Data

#### 4.9.5 Indicator Variables

You can use indicator variables with multibyte Globalization Support character variables as use you would with any other variable, except column length values are expressed in characters instead of bytes.

**Related Topics**

- [Using Indicator Variables](embedded-SQL.md)

#### 4.9.6 Various Combinations of PIC X/PIC N Variables and NCHAR/CHAR Columns

Pro\*Cobol supports various combinations of PIC X /PIC N variables and NCHAR/CHAR columns for select, insert and update statements through command line options `charset_picx` and `charset_picn`.

##### 4.9.6.1 PIC X and NCHAR Column

By default, PIC X variables are converted to the server-side Database Character Set so that these variables can be used with CHAR columns. Therefore, when you use the PIC X variables with NCHAR columns, there can be some data loss. To avoid this, use the following command to set the character set form used by PIC X variables to NCHAR:

    charset_picx=nchar_charset

##### 4.9.6.2 PIC N and CHAR column

By default, PIC N variables are converted to the server-side National Character Set so that these variables can be used with CHAR columns. Therefore, when you use the PIC N variables with NCHAR columns, there may be some performance impact. To avoid this, use the following command to set the character set form used by PIC N variables to CHAR:

    charset_picn=db_charset

**See Also:**

[Using Pro\*COBOL Precompiler Options](precompiler-options.md) for more information on CHARSET_PICX and CHARSET_PICN.

#### 4.9.7 Working With New Options

The following table shows how to work with the new options:

- Host var : Host variables type

- DB column type : CHAR/NCHAR

- charset_picx : value for charset_picx option

- charset_picn : value for charset_picn option

- NLS_NCHAR : value for NLS_NCHAR

- data charset : character set of host variables

| Host var | DB col type | charset_picx  | charset_picN  | NLS_NCHAR | Data charset |
|:---------|:------------|:--------------|:--------------|:----------|:-------------|
| PIC X    | CHAR        | nchar_charset | \-            | set       | NLS_NCHAR    |
| PIC X    | CHAR        | db_charset    | \-            | set       | NLS_LANG     |
| PIC X    | CHAR        | nchar_charset | \-            | not set   | NLS_LANG     |
| PIC X    | CHAR        | db_charset    | \-            | not set   | NLS_LANG     |
| PIC X    | NCHAR       | nchar_charset | \-            | set       | NLS_NCHAR    |
| PIC X    | NCHAR       | db_charset    | \-            | set       | NLS_LANG     |
| PIC X    | NCHAR       | nchar_charset | \-            | not set   | NLS_LANG     |
| PIC X    | NCHAR       | db_charset    | \-            | not set   | NLS_LANG     |
| PIC N    | CHAR        | \-            | nchar_charset | set       | NLS_NCHAR    |
| PIC N    | CHAR        | \-            | db_charset    | set       | NLS_NCHAR    |
| PIC N    | CHAR        | \-            | nchar_charset | not set   | NLS_LANG     |
| PIC N    | CHAR        | \-            | db_charset    | not set   | NLS_LANG     |
| PIC N    | NCHAR       | \-            | nchar_charset | set       | NLS_NCHAR    |
| PIC N    | NCHAR       | \-            | db_charset    | set       | NLS_NCHAR    |
| PIC N    | NCHAR       | \-            | nchar_charset | not set   | NLS_LANG     |
| PIC N    | NCHAR       | \-            | db_charset    | not set   | NLS_LANG     |

### 4.10 Datatype Conversion

At precompile time, an external datatype is assigned to each host variable. For example, Pro\*COBOL assigns the INTEGER external datatype to host variables of type PIC S9(n) COMP. At run time, the datatype code of every host variable used in a SQL statement is passed to Oracle. Oracle uses the codes to convert between internal and external datatypes.

Before assigning a SELECTed column value to an output host variable, Oracle must convert the internal datatype of the source column to the datatype of the host variable. Likewise, before assigning or comparing the value of an input host variable to a column, Oracle must convert the external datatype of the host variable to the internal datatype of the target column.

Conversions between internal and external datatypes follow the usual data conversion rules. For example, you can convert a CHAR value of 1234 to a PIC S9(4) COMP value. You cannot, however, convert a CHAR value of 123465543 (number too large) or 10F (number not decimal) to a PIC S9(4) COMP value. Likewise, you cannot convert a PIC X(n) value that contains alphabetic characters to a NUMBER value.

The datatype of the host variable must be compatible with that of the database column. It is your responsibility to make sure that values are convertible. For example, if you try to convert the string value `YESTERDAY `to a DATE column value, you get an error. Conversions between internal and external datatypes follow the usual data conversion rules. For instance, you can convert a CHAR value of `1234` to a 2-byte integer. But, you cannot convert a CHAR value of `65543` (number too large) or `10F` (number not decimal) to a 2-byte integer. Likewise, you cannot convert a string value that contains alphabetic characters to a NUMBER value.

Number conversion follows the conventions specified by Globalization Support parameters in the Oracle initialization file. For example, your system might be configured to recognize a comma (,) instead of a period (.) as the decimal character.

The following table shows the supported conversions between internal and external datatypes.

Table 4-9 Conversions Between Internal and External Datatypes

| External     | Internal | \-      | \-      | \-      | \-  | \-  | \-      | \-      |
|:-------------|:---------|:--------|:--------|:--------|:----|:----|:--------|:--------|
| CHAR         | I/O      | I/O (2) | I/O     | I(3)    |     | I/O | I/O (3) | I/O (1) |
| CHARF        | I/O      | I/O (2) | I/O     | I (3)   |     | I/O | I/O (3) | I/O (1) |
| CHARZ        | I/O      | I/O (2) | I/O     | I (3)   |     | I/O | I/O (3) | I/O (1) |
| DATE         | I/O      | I/O     | I       | \-      | \-  | \-  | --      |         |
| DECIMAL      | I/O (4)  | \-      | I       | \-      | \-  | I/O | \-      | \-      |
| DISPLAY      | I/O (4)) | \-      | I       | \-      | \-  | I/O | \-      | \-      |
| FLOAT        | I/O (4)  | \-      | I       | \-      | \-  | I/O | \-      | \-      |
| INTEGER      | I/O (4)  | \-      | I       | \-      | \-  | I/O | \-      | \-      |
| LONG         | I/O      | I/O (2) | I/O     | I (3.5) | \-  | I/O | I/O (3) | I/O (1) |
| LONG RAW     | O(6)     | \-      | I (5,6) | I/O     | \-  | \-  | I/O     | \-      |
| LONG VARCHAR | I/O      | I/O(2)  | I/O     | I (3,5) | \-  | I/O | I/O(3)) | I/O (1) |
| LONG VARRAW  | I/O (6)  | \-      | I (5,6) | I/O     | \-  | \-  | I/O     | \-      |
| NUMBER       | I/O (4)  | \-      | I       | \-      | \-  | I/O | \-      | \-      |
| RAW          | I/O (6)  | \-      | I (5,6) | I/O     | \-  | \-  | I/O     | \-      |
| ROWID        | I        | \-      | I       | \-      | \-  | \-  | \-      | I/O     |
| STRING       | I/O      | I/O (2) | I/O     | I (3.5) | \-  | I/O | I/O (3) | I/O (1) |
| UNSIGNED     | I/O (4)  | \-      | I       | \-      | \-  | I/O | \-      | \-      |
| VARCHAR      | I/O      | I/O (2) | I/O     | I (3,5) | \-  | I/O | I/O (3) | \-      |
| VARCHAR2     | I/O      | I/O (2) | I/O     | I (3)   | \-  | I/O | I/O (3) | I/O (1) |
| VARNUM       | I/O (4)  | \-      | I       | \-      | \-  | I/O | \-      | \-      |
| VARRAW       | I/O (6)  | \-      | I (5,6) | I/O     | \-  | \-  | I/O     | \-      |

In the preceding table:

- I = input only

- O = output only

- I/O = input or output

**Note:**

On input, host string must be in Oracle'BBBBBBBB.RRRR.FFFF' format.

On output, column value is returned in same format.

On input, host string must be the default DATE character format.

On output, column value is returned in same format

On input, host string must be in hex format.

On output, column value is returned in same format.

On output, column value must represent a valid number.

On input, length must be less than or equal to 2000.

**See Also:**

[ Oracle Database Globalization Support Guide](../nlspg/index.md) for more information about Globalization Support.

### 4.11 Explicit Control Over DATE String Format

When you select a DATE column value into a character host variable, Oracle must convert the internal binary value to an external character value. So, Oracle implicitly calls the SQL function TO_CHAR, which returns a character string in the default date format. The default is set by the Oracle initialization parameter NLS_DATE_FORMAT. To get other information such as the time or Julian date, you must explicitly call TO_CHAR with a format mask.

A conversion is also necessary when you insert a character host value into a DATE column. Oracle implicitly calls the SQL function TO_DATE, which expects the default date format. To insert dates in other formats, you must explicitly call TO_DATE with a format mask.

For compatibility with other versions of SQL Pro\*COBOL now provides the following precompiler option to specify date strings:

DATE_FORMAT={ISO \| USA \| EUR \| JIS \| LOCAL \| 'fmt'

The DATE_FORMAT option must be used on the command line or in a configuration file. The date strings are shown in the following table:

Table 4-10 Formats for Date Strings

| Format Name                          | Abbreviation | Date Format                    |
|:-------------------------------------|:-------------|:-------------------------------|
| International Standards Organization | ISO          | yyyy-mm-dd                     |
| USA standard                         | USA          | mm/dd/yyyy                     |
| European standard                    | EUR          | dd.mm.yyyy                     |
| Japanese Industrial Standard         | JIS          | yyyy-mm-dd                     |
| installation-defined                 | LOCAL        | Any installation-defined form. |

'fmt' is a date format model, such as 'Month dd, yyyy'. Note that all separately compiled units linked together must use the same DATE_FORMAT value.

**See Also:**

[Datetime Format Elements](../sqlrf/Format-Models.md) for the list of date format model elements.

### 4.12 Datatype Equivalencing

Datatype equivalencing lets you control the way Oracle interprets input data and the way Oracle formats output data. You can equivalence supported COBOL datatypes to external datatypes on a variable-by-variable basis. 

#### 4.12.1 Usefulness of Equivalencing

Datatype equivalencing is useful in several ways. For example, suppose you want to use a variable-length string in a COBOL program. You can declare a PIC X host variable, then equivalence it to the external datatype VARCHAR2.

In addition, you can use datatype equivalencing to override default datatype conversions. Unless Globalization Support parameters in the initialization file specify otherwise, if you select a DATE column value into a character host variable, Oracle returns a 9-byte string formatted as follows:

    DD-MON-YY

However, if you equivalence the character host variable to the DATE external datatype, Oracle returns a 7-byte value in the internal format.

#### 4.12.2 Host Variable Equivalencing

By default, Pro\*COBOL assigns a specific external datatype to every host variable. You can override the default assignments by equivalencing host variables to external datatypes. This is called host variable equivalencing.

The syntax of the VAR embedded SQL statement is:

          EXEC SQL
              VAR host_variable IS datatype [CONVBUFSZ [IS] (size)]
          END-EXEC

or

          EXEC SQL VAR host_variable [CONVBUFSZ [IS] (size)] END-EXEC

where datatype is:

    SQL datatype [ ( {length | precision, scale } ) ]

There must be at least one of the two clauses, or both.

where:

Table 4-11 Host Variable Equivalencing

| Variable            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| precision and scale | Integer literals that represent, respectively, the number of significant digits and the point at which rounding will occur. For example, a scale of 2 means the value is rounded to the nearest hundredth (3.456 becomes 3.46); a scale of -3 means the number is rounded to the nearest thousand (3456 becomes 3000).<br>You can specify a precision of 1 .. 99 and a scale of -84 .. 99. However, the maximum precision and scale of a database column are 38 and 127, respectively. So, if precision exceeds 38, you cannot insert the value of host_variable into a database column. On the other hand, if the scale of a column value exceeds 99, you cannot select or fetch the value into host_variable.<br>Specify precision and scale only when type_name is DECIMAL or DISPLAY |
| length              | Input or output host variable (or host table) declared earlier.<br>The VARCHAR and VARRAW external datatypes have a 2-byte length field followed by an n-byte data field, where n lies in the range 1 .. 65533. So, if type_name is VARCHAR or VARRAW, host_variable must be at least 3 bytes long.<br>The LONG VARCHAR and LONG VARRAW external datatypes have a 4-byte length field followed by an n-byte data field, where n lies in the range 1 .. 2147483643. So, if type_name is LONG VARCHAR or LONG VARRAW, host_variable must be at least 5 bytes long.                                                                                                                                                                                                                         |
| size                | An integer which is the size, in bytes, of a buffer used to perform conversion of the specified host_variable to another character set.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| SQL datatype        | Name of a valid external datatype such as RAW or STRING.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| host_variable       | Input or output host variable or host table declared earlier.<br>The VARCHAR and VARRAW external datatypes have a 2-byte length field followed by an n-byte data field, where n lies in the range 1 .. 65533. So, if type_name is VARCHAR or VARRAW, host_variable must be at least 3 bytes long.<br>The LONG VARCHAR and LONG VARRAW external datatypes have a 4-byte length field followed by an n-byte data field, where n lies in the range 1 .. 2147483643. So, if type_name is LONG VARCHAR or LONG VARRAW, host_variable must be at least 5 bytes long.                                                                                                                                                                                                                           |

An Example shows which parameters to use with each external datatype.

You cannot use EXEC SQL VAR with NCHAR host variables (those containing PIC G or PIC N clauses).

If DECLARE_SECTION=TRUE then you must have a Declare Section and you must place EXEC SQL VAR statements in the Declare Section.

When ext_type_name is FLOAT, use length; when ext_type_name is DECIMAL, you must specify precision and scale instead of length.

Host variable equivalencing is useful in several ways. For example, you can use it when you want Oracle to store but not interpret data. Suppose you want to store a host table of 4-byte integers in a RAW database column. Simply equivalence the host table to the RAW external datatype, as follows:

     WORKING-STORAGE SECTION.
         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01  EMP-TABLES.
         05  EMP-NUMBER  PIC S9(4) COMP OCCURS 50 TIMES.
                 ...
    *    Reset default datatype (INTEGER) to RAW.
         EXEC SQL VAR EMP-NUMBER IS RAW (200) END-EXEC.
         EXEC SQL END DECLARE SECTION END-EXEC.

With host tables, the length you specify must match the buffer size required to hold the table. In the last example, you specified a length of 200, which is the buffer size needed to hold 50 4-byte integers.

You can also declare a group item to be used as a LONG VARCHAR:

     01  MY-LONG-VARCHAR.
         05 UC-LEN PIC S9(9) COMP.
         05 UC-ARR PIC X(6000).
         EXEC SQL VAR MY-LONG-VARCHAR IS LONG VARCHAR(6000).

**See Also:**

- "CONVBUFSZ Clause in VAR Statement" for more information about CONVBUFSZ clause.

- "[VAR (Oracle Embedded SQL Directive)](embedded-SQL-statements-and-precompiler-directives.md) " for a syntax diagram of EXEC SQL VAR statement.

##### 4.12.2.1 CONVBUFSZ Clause in VAR Statement

The EXEC SQL VAR statement can have an optional CONVBUFSZ clause. You specify the size, in bytes, of the buffer in the runtime library used to perform conversion of the specified host variable between character sets.

When you have not used the CONVBUFSZ clause, the runtime automatically determines a buffer size based on the ratio of the host variable character size (determined by NLS_LANG) and the character size of the database character set. This can sometimes result in the creation of a buffer of LONG size. Databases are allowed to have only one LONG column. An error is raised if there is more than one LONG value.

To avoid such errors, you use a length shorter than the size of a LONG. If a character set conversion results in a value longer than the length specified by CONVBUFSZ, then Pro\*COBOL returns an error.

##### 4.12.2.2 An Example

Suppose you want to select employee names from the EMP table, then pass them to a C-language routine that expects null-terminated strings. You need not explicitly null-terminate the names. Simply equivalence a host variable to the STRING external datatype, as follows:

          EXEC SQL BEGIN DECLARE SECTION END-EXEC.
          ...
     01   EMP-NAME  PIC X(11).
    EXEC SQL VAR EMP-NAME IS STRING (11) END-EXEC.
          EXEC SQL END DECLARE SECTION END-EXEC.

The width of the ENAME column is 10 characters, so you allocate the new EMP-NAME 11 characters to accommodate the null terminator. (Here, length is optional because it defaults to the length of the host variable.) When you select a value from the ENAME column into EMP-NAME, Oracle null-terminates the value for you.

Table 4-12 Parameters for Host Variable Equivalencing

| External Datatype  | Length                  | Precision | Scale    | Default Length              |
|:-------------------|:------------------------|:----------|:---------|:----------------------------|
| CHAR               | optional                | n/a       | n/a      | declared length of variable |
| CHARZ              | optional                | n/a       | n/a      | declared length of variable |
| DATE               | n/a                     | n/a       | n/a      | 7 bytes                     |
| DECIMAL            | n/a                     | required  | required | none                        |
| DISPLAY            | n/a                     | required  | required | none                        |
| DISPLAY TRAILING   | n/a                     | required  | required | none                        |
| UNSIGNED DISPLAY   | n/a                     | required  | required | none                        |
| OVERPUNCH TRAILING | n/a                     | required  | required | none                        |
| OVERPUNCH LEADING  | n/a                     | required  | required | none                        |
| FLOAT              | optional (4 or 8)       | n/a       | n/a      | declared length of variable |
| INTEGER            | optional (1, 2, 4 or 8) | n/a       | n/a      | declared length of variable |
| LONG               | optional                | n/a       | n/a      | declared length of variable |
| LONG RAW           | optional                | n/a       | n/a      | declared length of variable |
| LONG VARCHAR       | required (note 1)       | n/a       | n/a      | none                        |
| LONG VARRAW        | required (note 1)       | n/a       | n/a      | none                        |
| NUMBER             | n/a                     | n/a       | n/a      | not available               |
| STRING             | optional                | n/a       | n/a      | declared length of variable |
| RAW                | optional                | n/a       | n/a      | declared length of variable |
| ROWID              | n/a                     | n/a       | n/a      | 18 bytes (see note 2)       |
| UNSIGNED           | optional (1, 2, or 4)   | n/a       | n/a      | declared length of variable |
| VARCHAR            | required                | n/a       | n/a      | none                        |
| VARCHAR2           | optional                | n/a       | n/a      | declared length of variable |
| VARNUM             | n/a                     | n/a       | n/a      | 22 bytes                    |
| VARRAW             | optional                | n/a       | n/a      | none                        |

1.  If the data field exceeds 65533 bytes, pass -1.

2.  This length is typical but the default is port-specific.

#### 4.12.3 Using the CHARF Datatype Specifier

You can use the datatype specifier CHARF in VAR statements to equivalence COBOL datatypes to the fixed-length ANSI datatype CHAR.s

When PICX=CHARF, specifying the datatype CHAR in a VAR statement equivalences the host-language datatype to the fixed-length ANSI datatype CHAR (Oracle external datatype code 96). However, when PICX=VARCHAR2, the host-language datatype is equivalenced to the variable-length datatype VARCHAR2 (code 1).

However, you can always equivalence host-language datatypes to the fixed-length ANSI datatype CHAR. Simply specify the datatype CHARF in the VAR statement. If you use CHARF, the host-language datatype is equivalenced to the fixed-length ANSI datatype CHAR even when PICX=VARCHAR2.

#### 4.12.4 Guidelines

To input VARNUM or DATE values, you must use the Oracle internal format. Keep in mind that Oracle uses the internal format to output VARNUM and DATE values.

After selecting a column value into a VARNUM host variable, you can check the first byte to get the length of the value. Internal Datatypes gives some examples of returned VARNUM values.

Table 4-13 VARNUM Examples

| Decimal Value | Length Byte | Exponent Byte | Mantissa Bytes | Terminator Byte |
|:--------------|:------------|:--------------|:---------------|:----------------|
| 5             | 2           | 193           | 6              | n/a             |
| -5            | 3           | 62            | 96             | 102             |
| 2767          | 3           | 194           | 28, 68         | n/a             |
| -2767         | 4           | 61            | 74, 34         | 102             |
| 100000        | 2           | 195           | 11             | n/a             |
| 1234567       | 5           | 196           | 2, 24, 46, 68  | n/a             |

If no Oracle external datatype suits your needs exactly, use a VARCHAR2-based or RAW-based external datatype.

**See Also:**

"Explicit Control Over DATE String Format" for converting DATE values.

#### 4.12.5 RAW and LONG RAW Values

When you select a RAW or LONG RAW column value into a character host variable, Oracle must convert the internal binary value to an external character value. In this case, Oracle returns each binary byte of RAW or LONG RAW data as a pair of characters. Each character represents the hexadecimal equivalent of a nibble (half a byte). For example, Oracle returns the binary byte 11111111 as the pair of characters "FF". The SQL function RAWTOHEX performs the same conversion.

A conversion is also necessary when you insert a character host value into a RAW or LONG RAW column. Each pair of characters in the host variable must represent the hexadecimal equivalent of a binary byte. If a character does not represent the hexadecimal value of a nibble, Oracle issues an error message.

**See Also:**

"Sample Program 4: Datatype Equivalencing" for more information about datatype conversion.

### 4.13 Platform Endianness Support

Oracle stored unicode data (UTF16) is always in big endian. Currently, client applications run on different platforms. Linux and Windows have little endian representation and Solaris has big endian representation. When UTF16 data is inserted or selected, Pro\*Cobol doesn't convert endian form between server and the client. This leads to corrupted UTF16 (UCS2) strings in the PIC N variable.

Platform endianness (Little endian for Linux and Windows, Big endian for Solaris) in PIC N variables can be maintained using the command line option `picn_endian`.

#### New Command Line Option

    picn_endian={BIG|OS}

If picn_endian=big, then PIC N variables are bound with character set ID AL16UTF16.

If picn_endian=os then PIC N variables are bound with character set ID UCS2.

The default value for this option is "big" to preserve the current behavior. This option is ignored if NLS_NCHAR is not AL16UTF16.

Character set form for PIC N variables can be set by using the existing Pro\*Cobol command line option:

    charset_picn={nchar_charset|db_charset}

**See Also:**

"Varying-Length Variables" for more information about varchar host variable if `PICN_ENDIAN=OS`.

### 4.14 Sample Program 4: Datatype Equivalencing

After connecting to Oracle, this program creates a database table named IMAGE in the SCOTT account, then simulates the insertion of bitmap images of employee numbers into the table. Datatype equivalencing lets the program use the Oracle external datatype LONG RAW to represent the images. Later, when the user enters an employee number, the number's "bitmap" is selected from the IMAGE table and displayed on the terminal screen.

    * This program simulates the storage and retrieval of bitmap images into table
    * IMAGE, which is created in the SCOTT account after logging on to ORACLE.
    * Datatype equivalencing allows an ORACLE external type of LONG RAW to be
    * specified for the programs representation of the images.

           IDENTIFICATION DIVISION.
           PROGRAM-ID. DTY-EQUIV.
           ENVIRONMENT DIVISION.
           DATA DIVISION.
           WORKING-STORAGE SECTION.

               EXEC SQL BEGIN DECLARE SECTION END-EXEC.
           01  USERNAME          PIC X(10) VARYING.
           01  PASSWD            PIC X(10) VARYING.
           01  EMP-REC-VARS.
               05  EMP-NUMBER    PIC S9(4) COMP.
               05  EMP-NAME      PIC X(10) VARYING.
               05  SALARY        PIC S9(6)V99
                                   DISPLAY SIGN LEADING SEPARATE.
               05  COMMISSION    PIC S9(6)V99
                                   DISPLAY SIGN LEADING SEPARATE.
               05  COMM-IND      PIC S9(4) COMP.

               EXEC SQL VAR SALARY IS DISPLAY(8,2) END-EXEC.
               EXEC SQL VAR COMMISSION IS DISPLAY(8,2) END-EXEC.

           01  BUFFER-VAR.
               05  BUFFER        PIC X(8192).
               EXEC SQL VAR BUFFER IS LONG RAW END-EXEC.

           01  INEMPNO           PIC S9(4) COMP.
               EXEC SQL END DECLARE SECTION END-EXEC.
               EXEC SQL INCLUDE SQLCA END-EXEC.

           01  DISPLAY-VARIABLES.
               05  D-EMP-NAME    PIC X(10).
               05  D-SALARY      PIC $Z(4)9.99.
               05  D-COMMISSION  PIC $Z(4)9.99.
               05  D-INEMPNO     PIC 9(4).
           01  REPLY             PIC X(10).
           01  INDX              PIC S9(9) COMP.
           01  PRT-QUOT          PIC S9(9) COMP.
           01  PRT-MOD           PIC S9(9) COMP.

           PROCEDURE DIVISION.

           BEGIN-PGM.
               EXEC SQL WHENEVER SQLERROR
                   DO PERFORM SQL-ERROR END-EXEC.

               PERFORM LOGON.
               DISPLAY "OK TO DROP THE IMAGE TABLE? (Y/N)  "
                   WITH NO ADVANCING.

               ACCEPT REPLY.

               IF (REPLY NOT = "Y") AND (REPLY NOT = "y")
                   GO TO SIGN-OFF-EXIT.
               EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.
               EXEC SQL DROP TABLE IMAGE END-EXEC.
               DISPLAY " ".
               IF (SQLCODE = 0) DISPLAY
                   "TABLE IMAGE DROPPED - CREATING NEW TABLE."
               ELSE IF (SQLCODE = -942) DISPLAY
                   "TABLE IMAGE DOES NOT EXIST - CREATING NEW TABLE."
               ELSE PERFORM SQL-ERROR.
               EXEC SQL WHENEVER SQLERROR
                   DO PERFORM SQL-ERROR END-EXEC.
               EXEC SQL CREATE TABLE IMAGE
                   (EMPNO NUMBER(4) NOT NULL, BITMAP LONG RAW)
               END-EXEC.
               EXEC SQL DECLARE EMPCUR CURSOR FOR
                   SELECT EMPNO, ENAME FROM EMP
               END-EXEC.
               EXEC SQL OPEN EMPCUR END-EXEC.
               DISPLAY " ".
               DISPLAY
                 "INSERTING BITMAPS INTO IMAGE FOR ALL EMPLOYEES ...".
               DISPLAY " ".

           INSERT-LOOP.
               EXEC SQL WHENEVER NOT FOUND GOTO NOT-FOUND END-EXEC.
               EXEC SQL FETCH EMPCUR
                   INTO :EMP-NUMBER, :EMP-NAME
               END-EXEC.
               MOVE EMP-NAME-ARR TO D-EMP-NAME.
               DISPLAY "EMPLOYEE ", D-EMP-NAME WITH NO ADVANCING.
               PERFORM GET-IMAGE.
               EXEC SQL INSERT INTO IMAGE
                   VALUES (:EMP-NUMBER, :BUFFER)
               END-EXEC.
               DISPLAY " IS DONE!".
               MOVE SPACES TO EMP-NAME-ARR.
               GO TO INSERT-LOOP.

           NOT-FOUND.
               EXEC SQL CLOSE EMPCUR END-EXEC.
               EXEC SQL COMMIT WORK END-EXEC.
               DISPLAY " ".
               DISPLAY
                 "DONE INSERTING BITMAPS.  NEXT, LET'S DISPLAY SOME.".

           DISP-LOOP.
               MOVE 0 TO INEMPNO.
               DISPLAY " ".
               DISPLAY "ENTER EMPLOYEE NUMBER (0 TO QUIT):  "
                   WITH NO ADVANCING.

               ACCEPT D-INEMPNO.

               MOVE D-INEMPNO TO INEMPNO.
               IF (INEMPNO = 0)
                   GO TO SIGN-OFF.
               EXEC SQL WHENEVER NOT FOUND GOTO NO-EMP END-EXEC.
               EXEC SQL SELECT EMP.EMPNO, ENAME, SAL, NVL(COMM, 0), BITMAP
                   INTO :EMP-NUMBER, :EMP-NAME, :SALARY,
                        :COMMISSION:COMM-IND, :BUFFER
                   FROM EMP, IMAGE
                   WHERE EMP.EMPNO = :INEMPNO
                     AND EMP.EMPNO = IMAGE.EMPNO
               END-EXEC.
               DISPLAY " ".
               PERFORM SHOW-IMAGE.
               MOVE EMP-NAME-ARR TO D-EMP-NAME.
               MOVE SALARY TO D-SALARY.
               MOVE COMMISSION TO D-COMMISSION.
               DISPLAY "EMPLOYEE ", D-EMP-NAME, " HAS SALARY ", D-SALARY
                   WITH NO ADVANCING.
               IF COMM-IND = -1
                   DISPLAY " AND NO COMMISSION."
               ELSE
                   DISPLAY " AND COMMISSION ", D-COMMISSION, "."
               END-IF.
               MOVE SPACES TO EMP-NAME-ARR.
               GO TO DISP-LOOP.

           NO-EMP.
               DISPLAY "NOT A VALID EMPLOYEE NUMBER - TRY AGAIN.".
               GO TO DISP-LOOP.

           LOGON.
               MOVE "SCOTT" TO USERNAME-ARR.
               MOVE 5 TO USERNAME-LEN.
               MOVE "TIGER" TO PASSWD-ARR.
               MOVE 5 TO PASSWD-LEN.
               EXEC SQL
                   CONNECT :USERNAME IDENTIFIED BY :PASSWD
               END-EXEC.
               DISPLAY " ".
               DISPLAY "CONNECTED TO ORACLE AS USER:  ", USERNAME-ARR.
               DISPLAY " ".

           GET-IMAGE.
               PERFORM MOVE-IMAGE
                   VARYING INDX FROM 1 BY 1 UNTIL INDX > 8192.

           MOVE-IMAGE.
               STRING '*' DELIMITED BY SIZE
                   INTO BUFFER
                   WITH POINTER INDX.
               DIVIDE 256 INTO INDX
                   GIVING PRT-QUOT REMAINDER PRT-MOD.
               IF (PRT-MOD = 0) DISPLAY "." WITH NO ADVANCING.

           SHOW-IMAGE.
               PERFORM VARYING INDX FROM 1 BY 1 UNTIL INDX > 10
                   DISPLAY "               *************************"
               END-PERFORM.
               DISPLAY " ".

           SIGN-OFF.
               EXEC SQL DROP TABLE IMAGE END-EXEC.
           SIGN-OFF-EXIT.
               DISPLAY " ".
               DISPLAY "HAVE A GOOD DAY.".
               DISPLAY " ".
               EXEC SQL COMMIT WORK RELEASE END-EXEC.
               STOP RUN.

           SQL-ERROR.
               EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.
               DISPLAY " ".
               DISPLAY "ORACLE ERROR DETECTED:  ".
               DISPLAY " ".
               DISPLAY SQLERRMC.
               EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
               STOP RUN.
