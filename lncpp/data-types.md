This chapter is a reference for Oracle data types used by Oracle C++ Interface applications. This information helps you to understand the conversions between internal and external representations of data that occur when you transfer data between your application and the database server.

This chapter contains these topics:

- Overview of Oracle Data Types

- Internal Data Types

- External Data Types

- Data Conversions

### 5.1 Overview of Oracle Data Types

Accurate communication between your C++ program and the Oracle database server is critical. OCCI applications can retrieve data from database tables by using SQL queries or they can modify existing data with SQL `INSERT`, `UPDATE`, and `DELETE` functions. To facilitate communication between the host language C++ and the database server, you must be aware of how C++ data types are converted to Oracle data types and back again.

In the Oracle database, values are stored in columns in tables. Internally, Oracle represents data in particular formats called internal data types. `NUMBER`, `VARCHAR2`, and `DATE `are examples of Oracle internal data types.

OCCI applications work with host language data types, or external data types, predefined by the host language. When data is transferred between an OCCI application and the database server, the data from the database is converted from internal data types to external data types.

This section includes the following topic: About OCCI Type and Data Conversion.

#### 5.1.1 About OCCI Type and Data Conversion

OCCI defines an enumerator called `Type` that lists the possible data representation formats available in an OCCI application. These representation formats are called external data types. When data is sent to the database server from the OCCI application, the external data type indicates to the database server what format to expect the data. When data is requested from the database server by the OCCI application, the external data type indicates the format of the data to be returned.

For example, on retrieving a value from a `NUMBER` column, the program may be set to retrieve it in `OCCIINT` format (a signed integer format into an integer variable). Or, the client might be set to send data in `OCCIFLOAT` format (floating-point format) stored in a C++ float variable to be inserted in a column of `NUMBER` type.

An OCCI application binds input parameters to a `Statement`, by calling a `set``xxx``()` method (the `external datatype` is implicitly specified by the method name), or by calling the `registerOutParam()`, `setDataBuffer()`, or `setDataBufferArray()` method (the external data type is explicitly specified in the method call). Similarly, when data values are fetched through a `ResultSet` object, the external representation of the retrieved data must be specified. This is done by calling a `get``xxx``()` method (the `external datatype` is implicitly specified by the method name) or by calling the `setDataBuffer()` method (the external data type is explicitly specified in the method call).

Note that there are more external data types than internal data types. In some cases, a single external data type maps to a single internal data type; in other cases, many external data types map to a single internal data type. The many-to-one mapping provides you with added flexibility.

**See Also:**

External Data Types

### 5.2 Internal Data Types

The internal (built-in) data types provided by Oracle are listed in this section. A brief summary of internal Oracle data types, including description, code, and maximum size, appears in Table 5-1.

Table 5-1 Summary of Oracle Internal Data Types

| Internal Data Type                                      | Maximum Size                                   |
|:--------------------------------------------------------|:-----------------------------------------------|
| `BFILE`                                                 | 4 gigabytes                                    |
| `BINARY_DOUBLE`                                         | 8 bytes                                        |
| `BINARY_FLOAT`                                          | 4 bytes                                        |
| `CHAR`                                                  | 2,000 bytes                                    |
| `DATE`                                                  | 7 bytes                                        |
| `INTERVAL DAY TO SECOND REF`                            | 11 bytes                                       |
| `INTERVAL YEAR TO MONTH REF`                            | 5 bytes                                        |
| `LONG`                                                  | 2 gigabytes (2^31-1 bytes)                     |
| `LONG RAW`                                              | 2 gigabytes (2^31-1 bytes)                     |
| `NCHAR`                                                 | 2,000 bytes                                    |
| `NUMBER`                                                | 21 bytes                                       |
| `NVARCHAR2`                                             | 32,767 bytes                                   |
| `RAW`                                                   | 2000 bytes (standard), 32,767 bytes (extended) |
| `REF`                                                   | Not Applicable                                 |
| `BLOB`                                                  | 4 gigabytes                                    |
| `CLOB`                                                  | 4 gigabytes                                    |
| `NCLOB`                                                 | 4 gigabytes                                    |
| `ROWID`                                                 | 10 bytes                                       |
| `TIMESTAMP`                                             | 11 bytes                                       |
| `TIMESTAMP WITH LOCAL TIME ZONE`                        | 7 bytes                                        |
| `TIMESTAMP WITH TIME ZONE`                              | 13 bytes                                       |
| `UROWID`                                                | 4000 bytes                                     |
| User-defined type (object type, `VARRAY`, nested table) | Not Applicable                                 |
| `VARCHAR2`                                              | 4000 bytes (standard), 32,767 bytes extended   |

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md)

- [Oracle Database Concepts](../cncpt/tables-and-table-clusters.md)

This section includes the following topics:

- Character Strings and Byte Arrays

- Universal Rowid (UROWID)

#### 5.2.1 Character Strings and Byte Arrays

You can use five Oracle internal data types to specify columns that contain either characters or arrays of bytes: `CHAR`, `VARCHAR2`, `RAW`, `LONG`, and `LONG` `RAW`.

`CHAR`, `VARCHAR2`, and `LONG` columns normally hold character data. `RAW` and `LONG` `RAW` hold bytes that are not interpreted as characters, for example, pixel values in a bitmapped graphics image. Character data can be transformed when passed through a gateway between networks. For example, character data passed between systems by using different languages (where single characters may be represented by differing numbers of bytes) can be significantly changed in length. Raw data is never converted in this way.

The database designer is responsible for choosing the appropriate Oracle internal data type for each column in a table. You must be aware of the many possible ways that character and byte-array data can be represented and converted between variables in the OCCI program and Oracle database tables.

#### 5.2.2 Universal Rowid (UROWID)

The universal rowid (`UROWID`) is a data type that can store both the logical and the physical rowid of rows in Oracle tables and in foreign tables, such as DB2 tables accessed through a gateway. Logical `rowid` values are primary key-based logical identifiers for the rows of index-organized tables.

To use columns of the `UROWID` data type, the value of the `COMPATIBLE` initialization parameter must be set to `8.1` or higher.

The following `OCCI_SQLT` types can be bound to universal `rowid`s:

- `OCCI_SQLT_CHR` (`VARCHAR2`)

- `OCCI_SQLT_VCS` (`VARCHAR`)

- `OCCI_SQLT_STR` (`NULL` terminated string)

- `OCCI_SQLT_LVC` (long `VARCHAR`)

- `OCCI_SQLT_AFC` (`CHAR)`

- `OCCI_SQLT_AVC` (`CHARZ`)

- `OCCI_SQLT_VST` (string)

- `OCCI_SQLT_RDD` (`ROWID` descriptor)

### 5.3 External Data Types

OCCI application communicate with the Oracle database server by using external data types. Specifically, external data types are mapped to C++ data types.

Table 5-2 lists the Oracle external data types, the C++ equivalent (what the Oracle internal data type is usually converted to), and the corresponding OCCI type. Note the following conditions:

- In C++ Data Type column, `n` stands for variable length and depends on program requirements or operating system.

- The usage of types in `Statement` class methods is as follows:

  - `setDataBuffer()` and `setDataBufferArray()`: Only types of the form `OCCI_SQLT_``xxx` (for example, `OCCI_SQLT_INT`) in the `occiCommon.h` file are permitted.

  - `registerOutParam()`: Only types of the form `OCCI``xxx` (for example, `OCCIDOUBLE`, `OCCICURSOR`, and so on) on the `occiCommon.h` file are permitted. However, there are some exceptions: `OCCIANYDATA`, `OCCIMETADATA`, `OCCISTREAM`, and `OCCIBOOL` are not permitted.

- In the `ResultSet` class, only types of the form `OCCI_SQLT_``xxx` (for example, `OCCI_SQLT_INT`) in the `occiCommon.h` file are permitted for use in `setDataBuffer()` and `setDataBufferArray()` methods.

- The `TIMESTAMP` and `TIMESTAMP` `WITH` `TIME` `ZONE` data types are collectively known as datetimes. The `INTERVAL` `YEAR` `TO` `MONTH` and `INTERVAL` `DAY` `TO` `SECOND` are collectively known as intervals.

Table 5-2 External Data Types and Corresponding C++ and OCCI Types

| External Data Type               | C++ Type                                     | OCCI Type                 | Usage Notes                                         |
|:---------------------------------|:---------------------------------------------|:--------------------------|:----------------------------------------------------|
| 16 bit signed `INTEGER`          | `signed short, signed int`                   | `OCCIINT`                 | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| 32 bit signed `INTEGER`          | `signed int, signed long`                    | `OCCIINT`                 | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| 8 bit signed `INTEGER`           | `signed char`                                | `OCCIINT`                 | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `BFILE`                          | `Bfile`                                      | `OCCIBFILE`               | Use with `regiserOutParam()`.                       |
| `FBFILE `                        | `OCILobLocator`                              | `OCCI_SQLT_FILE`          | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `BLOB `                          | `OCILobLocator`                              | `OCCI_SQLT_BLOB`          | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `BLOB `                          | `Blob`                                       | `OCCIBLOB`                | Use with `regiserOutParam()`.                       |
| `BOOL`                           | `bool`                                       | `OCCIBOOL`                | Use with `regiserOutParam()`.                       |
| `BYTES`                          | `Bytes`                                      | `OCCIBYTES`               | Use with `regiserOutParam()`.                       |
| `CHAR`                           | `char[n]`                                    | `OCCI_SQLT_AFC`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `CHAR`                           | `string`                                     | `OCCICHAR`                | Use with `regiserOutParam()`.                       |
| `CLOB`                           | `OCILobLocator`                              | `OCCI_SQLT_CLOB`          | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `CHARZ`                          | `char[n+1]`                                  | `OCCI_SQLT_RDD`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `CLOB`                           | `Clob`                                       | `OCCICLOB`                | Use with `regiserOutParam()`.                       |
| `CURSOR`                         | `ResultSet`                                  | `OCCICURSOR`              | Use with `regiserOutParam()`.                       |
| `DATE`                           | `char[7]`                                    | `OCCI_SQLT_DAT`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `DATE `                          | `Date`                                       | `OCCIDATE`                | Use with `regiserOutParam()`.                       |
| `DOUBLE `                        | `double`                                     | `OCCIDOUBLE`              | Use with `regiserOutParam()`.                       |
| `FLOAT`                          | `float, double`                              | `OCCIFLOAT`               | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `FLOAT`                          | `float`                                      | `OCCIFLOAT`               | Use with `regiserOutParam()`.                       |
| `INT`                            | `int`                                        | `OCCIINT`                 | Use with `regiserOutParam()`.                       |
| `INTERVAL DAY TO SECOND`         | `char[11]`                                   | `OCCI_SQLT_INTERVAL_DS`   | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `INTERVAL YEAR TO MONTH`         | `char[5]`                                    | `OCCI_SQLT_INTERVAL_YM`   | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `INTERVALDS`                     | `IntervalDS`                                 | `OCCIINTERVALDS`          | Use with `regiserOutParam()`.                       |
| `INTERVALYM`                     | `IntervalYM`                                 | `OCCIINTERVALYM`          | Use with `regiserOutParam()`.                       |
| `LONG`                           | `char[n]`                                    | `OCCI_SQLT_LNG`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `LONG RAW`                       | `unsigned char[n]`                           | `OCCI_SQLT_LBI`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `LONG VARCHAR`                   | `char[n+siezeof(integer)]`                   | `OCCI_SQLT_LVC`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `LONG VARRAW`                    | `unsigned char[n+siezeof(integer)]`          | `OCCI_SQLT_LVB`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `METADATA`                       | `MetaData`                                   | `OCCIMETADATA`            | Use with `regiserOutParam()`.                       |
| `NAMED DATA TYPE`                | `struct`                                     | `OCCI_SQLT_NTY`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `NATIVE DOUBLE`                  | `double`                                     | `OCCIBDOUBLE`             | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `NATIVE DOUBLE`                  | `Bdouble, double`                            | `OCCIBDOUBLE`             | Use with `regiserOutParam()`.                       |
| `NATIVE FLOAT`                   | `float`                                      | `OCCIBFLOAT`              | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `NATIVE FLOAT`                   | `BFloat, float`                              | `OCCIBFLOAT`              | Use with `regiserOutParam()`.                       |
| null terminated `STRING`         | `char[n+1]`                                  | `OCCI_SQLT_STR`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `NUMBER`                         | `unsigned char[21]`                          | `OCCI_SQLT_NUM`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `NUMBER `                        | `Number`                                     | `OCCINUMBER`              | Use with `regiserOutParam()`.                       |
| `POBJECT`                        | User defined types generated by OTT utility. | `OCCIPOBJECT`             | Use with `regiserOutParam()`.                       |
| `RAW`                            | `unsigned char[n]`                           | `OCCI_SQLT_BIN`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `REF`                            | `OCIRef`                                     | `OCCI_SQLT_REF`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `REF`                            | `Ref`                                        | `OCCIREF`                 | Use with `regiserOutParam()`.                       |
| `REFANY`                         | `RefAny`                                     | `OCCIREFANY`              | Use with `regiserOutParam()`.                       |
| `ROWID`                          | `OCIRowid`                                   | `OCCI_SQLT_RID`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `ROWID`                          | `Bytes`                                      | `OCCIROWID`               | Use with `regiserOutParam()`.                       |
| `ROWID` descriptor               | `OCIRowid`                                   | `OCCI_SQLT_RDD`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `STRING`                         | `STL string`                                 | `OCCISTRING`              | Use with `regiserOutParam()`.                       |
| `TIMESTAMP`                      | `char[11]`                                   | `OCCI_SQLT_TIMESTAMP`     | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `TIMESTAMP`                      | `Timestamp`                                  | `OCCITIMESTAMP`           | Use with `regiserOutParam()`.                       |
| `TIMESTAMP WITH LOCAL TIME ZONE` | `char[7]`                                    | `OCCI_SQLT_TIMESTAMP_LTZ` | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `TIMESTAMP WITH TIME ZONE`       | `char[13]`                                   | `OCCI_SQLT_TIMESTAMP_TZ`  | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `UNSIGNED INT`                   | `unsigned int`                               | `OCCIUNSIGNED_INT`        | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `UNSIGNED INT`                   | `unsigned int`                               | `OCCIUNSIGNED_INT`        | Use with `regiserOutParam()`.                       |
| `VARCHAR`                        | `char[n+sizeof( short integer)]`             | `OCCI_SQLT_VCS`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `VARCHAR2`                       | `char[n]`                                    | `OCCI_SQLT_CHR`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `VARNUM`                         | `char[22]`                                   | `OCCI_SQLT_VNU`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `VARRAW`                         | `unsigned char[n+sizeof( short integer)]`    | `OCCI_SQLT_VBI`           | Use with `setDataBuffer()`, `setDataBufferArray()`. |
| `VECTOR`                         | `STL vector`                                 | `OCCIVECTOR`              | Use with `regiserOutParam()`.                       |

This section includes the following topic: Description of External Data Types.

#### 5.3.1 Description of External Data Types

This section provides a description for each of the external data types:

- BFILE

- BDOUBLE

- BFLOAT

- BLOB

- CHAR

- CHARZ

- CLOB

- DATE

- FLOAT

- INTEGER

- INTERVAL DAY TO SECOND

- INTERVAL YEAR TO MONTH

- LONG

- LONG RAW

- LONG VARCHAR

- LONG VARRAW

- NCLOB

- NUMBER

- OCCI BFILE

- OCCI BLOB

- OCCI BYTES

- OCCI CLOB

- OCCI DATE

- OCCI INTERVALDS

- OCCI INTERVALYM

- OCCI NUMBER

- OCCI POBJECT

- OCCI REF

- OCCI REFANY

- OCCI STRING

- OCCI TIMESTAMP

- OCCI VECTOR

- RAW

- REF

- ROWID

- STRING

- TIMESTAMP

- TIMESTAMP WITH LOCAL TIME ZONE

- TIMESTAMP WITH TIME ZONE

- UNSIGNED INT

- VARCHAR

- VARCHAR2

- VARNUM

- VARRAW

- NATIVE DOUBLE

- NATIVE FLOAT

##### 5.3.1.1 BFILE

The external data type `BFILE` allows read-only byte stream access to large files on the file system of the database server. A `BFILE` is a large binary data object stored in operating system files outside database tablespaces. These files use reference semantics. The Oracle server can access a `BFILE` provided the underlying server operating system supports stream-mode access to these operating system files.

##### 5.3.1.2 BDOUBLE

The `BDouble` interface in OCCI encapsulates the native double data and the `NULL` information of a column or object attribute of the type `binary_double`. The OCCI methods in [AnyData Class](anydata-class.md), [ResultSet Class](resultset-class.md) and [Statement Class](statement-class.md), and the global methods that take these class objects as parameters, use the following definition for the `BDOUBLE` data type:

Example 5-1 Definition of the BDOUBLE Data Type

    struct BDouble
    {
      double value;
      bool isNull;

     BDouble()
     {
        isNull = false;
        value = 0.;
     }
    };

##### 5.3.1.3 BFLOAT

The `BFloat` interface in OCCI encapsulates the native float data and the `NULL` information of a column or object attribute of the type `binary_float`. The OCCI methods in [AnyData Class](anydata-class.md), [ResultSet Class](resultset-class.md) and [Statement Class](statement-class.md), and the global methods that take these class objects as parameters, use the following definition for the `BFLOAT` data type:

Example 5-2 Definition of the BFLOAT Data Type

    struct BFloat
    {
      float value;
      bool isNull;

     BFloat()
     {
        isNull = false;
        value = 0.;
     }
    };

##### 5.3.1.4 BLOB

The external data type `BLOB` stores unstructured binary large objects. A `BLOB` can be thought of as a bitstream with no character set semantics. `BLOB`s can store up to `4` gigabytes of binary data.

`BLOB` data types have full transactional support. Changes made through OCCI participate fully in the transaction. `BLOB` value manipulations can be committed or rolled back. You cannot save a `BLOB` locator in a variable in one transaction and then use it in another transaction or session.

##### 5.3.1.5 CHAR

The external data type `CHAR` is a string of characters, with a maximum length of `2000` characters. Character strings are compared by using blank-padded comparison semantics.

##### 5.3.1.6 CHARZ

The external data type `CHARZ` is similar to the `CHAR` data type, except that the string must be `NULL` terminated on input, and Oracle places a `NULL` terminator character at the end of the string on output. The `NULL` terminator serves only to delimit the string on input or output. It is not part of the data in the table.

##### 5.3.1.7 CLOB

The external data type `CLOB` stores fixed-width or varying-width character data. A `CLOB` can store up to `4` gigabytes of character data. `CLOB`s have full transactional support. Changes made through OCCI participate fully in the transaction. `CLOB` value manipulations can be committed or rolled back. You cannot save a `CLOB` locator in a variable in one transaction and then use it in another transaction or session.

##### 5.3.1.8 DATE

The external data type `DATE` can update, insert, or retrieve a date value using the Oracle internal seven byte date binary format, as listed in Table 5-3:

Table 5-3 Format of the DATE Data Type

| Example                | Byte 1: Century | Byte 2: Year | Byte 3: Month | Byte 4: Day | Byte 5: Hour | Byte 6: Minute | Byte 7: Second |
|:-----------------------|:----------------|:-------------|:--------------|:------------|:-------------|:---------------|:---------------|
| 1: 01-JUN-2000, 3:17PM | 120             | 100          | 6             | 1           | 16           | 18             | 1              |
| 2: 01-JAN-4712 BCE     | 53              | 88           | 1             | 1           | 1            | 1              | 1              |

###### 5.3.1.8.1 Example 1, 01-JUN-2000, 3:17PM:

- The century and year bytes (1 and 2) are in excess-`100 `notation. Dates BCE (Before Common Era) are less than `100`. Dates in the Common Era (CE), 0 and after, are greater than `100`. For dates 0 and after, the first digit of both bytes 1 and 2 signifies that it is of the CE.

- For byte 1, the second and third digits of the century are calculated as the year (an integer) divided by 100. With integer division, the fractional portion is discarded. The following calculation is for the year 1992: `1992 / 100 = 19`.

- For byte 1, `119` represents the twentieth century, 1900 to 1999. A value of `120` would represent the twenty-first century, 2000 to 2099.

- For byte 2, the second and third digits of the year are calculated as the year modulo 100: `1992 % 100 = 92`.

- For byte 2, `192` represents the ninety-second year of the current century. A value of `100` would represent the zeroth year of the current century.

- The year 2000 would yield `120 `for byte 1 and `100` for byte 2.

- For bytes 3 through 7, valid dates begin at 01-JAN of the year. The month byte ranges from `1` to `12`, the date byte ranges from `1` to `31`, the hour byte ranges from `1` to `24`, the minute byte ranges from `1` to `60`, and the second byte ranges from `1` to `60`.

###### 5.3.1.8.2 Example 2, 01-JAN-4712 BCE:

- For years before 0 CE, centuries and years are represented by the difference between 100 and the number.

- For byte 1, 01-JAN-4712 BCE is century `53:` `100 - 47 = 53.`

- For byte 2, 01-JAN-4712 BCE is year `88`: `100 - 12 = 88`.

If no time is specified for a date, the time defaults to midnight and bytes 5 through 6 are set to `1`: `1`, `1`, `1`.

When you enter a date in binary format by using the external data type `DATE`, the database does not perform consistency or range checking. All data in this format must be validated before input.

There is little need for the external data type `DATE`. It is more convenient to convert `DATE` values to a character format, because most programs deal with dates in a character format, such as `DD-MON-YYYY`. Instead, you may use the `Date` data type.

When a `DATE` column is converted to a character string in your program, it is returned in the default format mask for your session, or as specified in the `INIT.ORA` file.

This data type is different from `OCCI DATE` which corresponds to a C++ `Date` data type.

##### 5.3.1.9 FLOAT

The external data type `FLOAT` processes numbers with fractional parts. The number is represented in the host system's floating-point format. Normally, the length is 4 or 8 bytes.

The internal format of an Oracle number is decimal. Most floating-point implementations are binary. Oracle, therefore, represents numbers with greater precision than floating-point representations.

##### 5.3.1.10 INTEGER

The external data type `INTEGER` is used for converting numbers. An external integer is a signed binary number. Its size is operating system-dependent. If the number being returned from Oracle is not an integer, then the fractional part is discarded, and no error is returned. If the number returned exceeds the capacity of a signed integer for the system, then Oracle returns an overflow on conversion error.

A rounding error may occur when converting between `FLOAT` and `NUMBER`. Using a `FLOAT` as a bind variable in a query may return an error. You can work around this by converting the `FLOAT` to a string and using the OCCI type `OCCI_SQLT_CHR` or the OCCI type `OCCI_SQLT_STR` for the operation.

##### 5.3.1.11 INTERVAL DAY TO SECOND

The external data type `INTERVAL` `DAY` `TO` `SECOND` stores the difference between two datetime values in terms of days, hours, minutes, and seconds. Specify this data type as follows:

    INTERVAL DAY [(day_precision)]
       TO SECOND [(fractional_seconds_precision)]

This example uses the following placeholders:

- `day_precision`: Number of digits in the `DAY` datetime field. Accepted values are `1` to `9`. The default is `2`.

- `fractional_seconds_precision`: Number of digits in the fractional part of the `SECOND` datetime field. Accepted values are `0` to `9`. The default is `6`.

To specify an `INTERVAL` `DAY` `TO` `SECOND` literal with nondefault day and second precision, you must specify the precisions in the literal. For example, you might specify an interval of `100` days, `10` hours, `20` minutes, `42` seconds, and `22` hundredths of a second as follows:

    INTERVAL '100 10:20:42.22' DAY(3) TO SECOND(2)

You can also use abbreviated forms of the `INTERVAL` `DAY` `TO` `SECOND` literal. For example:

- `INTERVAL '90' MINUTE` maps to `INTERVAL '00 00:90:00.00' DAY TO SECOND(2)`

- `INTERVAL '30:30' HOUR TO MINUTE` maps to `INTERVAL '00 30:30:00.00' DAY TO SECOND(2)`

- `INTERVAL '30' SECOND(2,2) `maps to `INTERVAL '00 00:00:30.00' DAY TO SECOND(2)`

##### 5.3.1.12 INTERVAL YEAR TO MONTH

The external data type `INTERVAL` `YEAR` `TO` `MONTH` stores the difference between two datetime values by using the `YEAR` and `MONTH` datetime fields. Specify `INTERVAL` `YEAR` `TO` `MONTH` as follows:

    INTERVAL YEAR [(year_precision)] TO MONTH

The placeholder `year_precision` is the number of digits in the `YEAR` datetime field. The default value of `year_precision` is `2`. To specify an `INTERVAL` `YEAR` `TO` `MONTH` literal with a nondefault `year_precision`, you must specify the precision in the literal. For example, the following `INTERVAL` `YEAR` `TO` `MONTH` literal indicates an interval of `123` years, `2` months:

    INTERVAL '123-2' YEAR(3) TO MONTH

You can also use abbreviated forms of the `INTERVAL` `YEAR` `TO` `MONTH` literal. For example,

- `INTERVAL '10' MONTH` maps `to INTERVAL '0-10' YEAR TO MONTH`

- `INTERVAL '123' YEAR(3)` maps `to INTERVAL '123-0' YEAR(3) TO MONTH`

##### 5.3.1.13 LONG

The external data type `LONG` stores character strings longer than 4000 bytes and up to `2` gigabytes in a column of data type `LONG`. Columns of this type are only used for storage and retrieval of long strings. They cannot be used in methods, expressions, or `WHERE` clauses. `LONG` column values are generally converted to and from character strings.

##### 5.3.1.14 LONG RAW

The external data type `LONG RAW` is similar to the external data type `RAW`, except that it stores up to `2` gigabytes.

##### 5.3.1.15 LONG VARCHAR

The external data type `LONG VARCHAR` stores data from and into an Oracle `LONG` column. The first four bytes contain the length of the item. The maximum length of a `LONG` `VARCHAR` is `2` gigabytes.

##### 5.3.1.16 LONG VARRAW

The external data type `LONG VARRAW` store data from and into an Oracle `LONG` `RAW` column. The length is contained in the first four bytes. The maximum length is `2` gigabytes.

##### 5.3.1.17 NCLOB

The external data type `NCLOB` is a national character version of a `CLOB`. It stores fixed-width, multibyte national character set character (`NCHAR`), or varying-width character set data. An `NCLOB` can store up to 4 gigabytes of character text data.

`NCLOB`s have full transactional support. Changes made through OCCI participate fully in the transaction. `NCLOB` value manipulations can be committed or rolled back. You cannot save an `NCLOB` locator in a variable in one transaction and then use it in another transaction or session.

You cannot create an object with `NCLOB` attributes, but you can specify `NCLOB` parameters in methods.

##### 5.3.1.18 NUMBER

You should not have to use `NUMBER` as an external data type. If you do use it, Oracle returns numeric values in its internal `21`-byte binary format and expects this format on input. The following discussion is included for completeness only.

Oracle stores values of the `NUMBER` data type in a variable-length format. The first byte is the exponent and is followed by `1` to `20 `mantissa bytes. The high-order bit of the exponent byte is the sign bit; it is set for positive numbers and it is cleared for negative numbers. The lower `7` bits represent the exponent, which is a base-`100` digit with an offset of `65`.

To calculate the decimal exponent, add `65` to the base-`100` exponent and add another `128` if the number is positive. If the number is negative, you do the same, but subsequently the bits are inverted. For example, `-5` has a base-`100` exponent `=` `62 (0x3e)`. The decimal exponent is thus `(~0x3e)-128-65 = 0xc1-128-65 = 193-128-65 = 0`.

Each mantissa byte is a base-`100` digit, in the range `1` to `100`. For positive numbers, the digit has `1` added to it. So, the mantissa digit for the value `5` is `6`. For negative numbers, instead of adding 1, the digit is subtracted from `101`. So, the mantissa digit for the number `-5 `is: `101-5 = 96`. Negative numbers have a byte containing `102` appended to the data bytes. However, negative numbers that have `20` mantissa bytes do not have the trailing `102` byte. Because the mantissa digits are stored in base-`100,` each byte can represent two decimal digits. The mantissa is normalized; leading zeroes are not stored.

Up to` 20` data bytes can represent the mantissa. However, only `19` are guaranteed to be accurate. The `19` data bytes, each representing a base-`100` digit, yield a maximum precision of `38` digits for an internal data type `NUMBER`.

Note that this data type is different from `OCCI NUMBER` which corresponds to a C++ `Number` data type.

##### 5.3.1.19 OCCI BFILE

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [Bfile Class](bfile-class.md)

##### 5.3.1.20 OCCI BLOB

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [Blob Class](blob-class.md)

##### 5.3.1.21 OCCI BYTES

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [Bytes Class](bytes-class.md)

##### 5.3.1.22 OCCI CLOB

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [Clob Class](clob-class.md)

##### 5.3.1.23 OCCI DATE

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [Date Class](date-class.md)

##### 5.3.1.24 OCCI INTERVALDS

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [IntervalDS Class](intervalds-class.md)

##### 5.3.1.25 OCCI INTERVALYM

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [IntervalYM Class](intervalym-class.md)

##### 5.3.1.26 OCCI NUMBER

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [Number Class](number-class.md)

##### 5.3.1.27 OCCI POBJECT

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [PObject Class](pobject-class.md)

##### 5.3.1.28 OCCI REF

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [Ref Class](ref-class.md)

##### 5.3.1.29 OCCI REFANY

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [RefAny Class](refany-class.md)

##### 5.3.1.30 OCCI STRING

The external data type `OCCI STRING` corresponds to an `STL string`.

##### 5.3.1.31 OCCI TIMESTAMP

**See Also:**

[OCCI Application Programming Interface](occi-application-programing-interface.md), [Timestamp Class](timestamp-class.md)

##### 5.3.1.32 OCCI VECTOR

The external data type `OCCI VECTOR` is used to represent collections, for example, a nested table or `VARRAY`. `CREATE TYPE num_type as VARRAY OF NUMBER(10)` can be represented in a C++ application as `vector<int>`, `vector<Number>`, and so on.

##### 5.3.1.33 RAW

The external data type `RAW` is used for binary data or byte strings that are not to be interpreted or processed by Oracle. `RAW` could be used, for example, for graphics character sequences. The maximum length of a `RAW` column is 2000 bytes. If the `init.ora` parameter `max_string_size = standard` (default value), the maximum length of a `RAW` can be 2000 bytes. If the `init.ora` parameter `max_string_size = extended`, the maximum length of a `RAW` can be 32767 bytes. See the `init.ora` parameter [MAX_STRING_SIZE](../refrn/MAX_STRING_SIZE.md) in Oracle Database Reference for more information about extended data types.

When `RAW` data in an Oracle table is converted to a character string, the data is represented in hexadecimal code. Each byte of `RAW` data is represented as two characters that indicate the value of the byte, ranging from 00 to FF. If you input a character string by using `RAW`, then you must use hexadecimal coding.

##### 5.3.1.34 REF

The external data type `REF` is a reference to a named data type. To allocate a `REF` for use in an application, declare a variable as a pointer to a `REF`.

##### 5.3.1.35 ROWID

The external data type `ROWID` identifies a particular row in a database table. The `ROWID` is often returned from a query by issuing a statement similar to the following example:

    SELECT ROWID, var1, var2 FROM db;

You can then use the returned `ROWID` in further `DELETE` statements.

If you are performing a `SELECT` for an `UPDATE` operation, then the `ROWID` is implicitly returned.

##### 5.3.1.36 STRING

The external data type `STRING` behaves like the external data type `VARCHAR2` (data type code 1), except that the external data type `STRING` must be `NULL`-terminated.

Note that this data type is different from `OCCI STRING` which corresponds to a C++ STL string data type.

##### 5.3.1.37 TIMESTAMP

The external data type `TIMESTAMP` is an extension of the `DATE` data type. It stores the year, month, and day of the `DATE` data type, plus hour, minute, and second values. Specify the `TIMESTAMP` data type as follows:

    TIMESTAMP [(fractional_seconds_precision)]

The placeholder `fractional_seconds_precision` optionally specifies the number of digits in the fractional part of the `SECOND` datetime field and can be a number in the range 0 to 9. The default is 6. For example, you specify `TIMESTAMP(2)` as a literal as follows:

    TIMESTAMP '1997-01-31 09:26:50.10'

Note that this data type is different from `OCCI TIMESTAMP`.

##### 5.3.1.38 TIMESTAMP WITH LOCAL TIME ZONE

The external data type `TIMESTAMP` `WITH` `TIME` `ZONE` (`TSTZ`) is a variant of `TIMESTAMP` that includes an explicit time zone displacement in its value. The time zone displacement is the difference (in hours and minutes) between local time and Coordinated Universal Time (UTC), formerly Greenwich Mean Time. Specify the `TIMESTAMP` `WITH` `TIME` `ZONE` data type as follows:

    TIMESTAMP(fractional_seconds_precision) WITH TIME ZONE

The placeholder `fractional_seconds_precision` optionally specifies the number of digits in the fractional part of the `SECOND` datetime field and can be a number in the range `0` to `9`. The default is `6`.

Two `TIMESTAMP` `WITH` `TIME` `ZONE` values are considered identical if they represent the same instant in UTC, regardless of the `TIME` `ZONE` offsets stored in the data.

##### 5.3.1.39 TIMESTAMP WITH TIME ZONE

The external data type `TIMESTAMP` `WITH` `TIME` `ZONE` is a variant of `TIMESTAMP` that includes a time zone displacement in its value. The time zone displacement is the difference (in hours and minutes) between local time and Coordinated Universal Time (UTC), formerly Greenwich Mean Time. Specify the `TIMESTAMP` `WITH` `TIME` `ZONE` data type as follows:

    TIMESTAMP [(fractional_seconds_precision)] WITH TIME ZONE

The placeholder `fractional_seconds_precision` optionally specifies the number of digits in the fractional part of the SECOND datetime field and can be a number in the range `0` to `9`. The default is `6`. For example, you might specify `TIMESTAMP(0)` `WITH` `TIME` `ZONE` as a literal as follows:

    TIMESTAMP '1997-01-31 09:26:50+02.00'

##### 5.3.1.40 UNSIGNED INT

The external data type `UNSIGNED INT` is used for unsigned binary integers. The size in bytes is operating system dependent. The host system architecture determines the order of the bytes in a word. If the number being output from Oracle is not an integer, the fractional part is discarded, and no error is returned. If the number to be returned exceeds the capacity of an unsigned integer for the operating system, Oracle returns an overflow on conversion error.

##### 5.3.1.41 VARCHAR

The external data type `VARCHAR` store character strings of varying length. The first two bytes contain the length of the character string, and the remaining bytes contain the actual string. The specified length of the string in a bind or a define call must include the two length bytes, meaning the largest `VARCHAR` string is `65533` bytes long, not `65535`. For converting longer strings, use the `LONG` `VARCHAR` external data type.

##### 5.3.1.42 VARCHAR2

The external data type `VARCHAR2` is a variable-length string of characters up to 4000 bytes. If the `init.ora` parameter `max_string_size = standard` (default value), the maximum length of a `VARCHAR2` can be 4000 bytes. If the `init.ora` parameter `max_string_size = extended`, the maximum length of a `VARCHAR2` can be 32767 bytes. See the `init.ora` parameter [MAX_STRING_SIZE](../refrn/MAX_STRING_SIZE.md) in Oracle Database Reference for more information about extended data types.

##### 5.3.1.43 VARNUM

The external data type `VARNUM` is similar to the external data type `NUMBER`, except that the first byte contains the length of the number representation. This length value does not include the length byte itself. Reserve 22 bytes to receive the longest possible `VARNUM`. You must set the length byte when you send a `VARNUM` value to the database.

Table 5-4 VARNUM Examples

| Decimal Value | Length Byte | Exponent Byte | Mantissa Bytes      | Terminator Byte |
|:--------------|:------------|:--------------|:--------------------|:----------------|
| `0`           | `1`         | `128`         | NA<sup>Foot 1</sup> | NA              |
| `5`           | `2`         | `193`         | `6`                 | NA              |
| `-5`          | `3`         | `62`          | `96`                | `102`           |
| `2767`        | `3`         | `194`         | `28, 68`            | NA              |
| `-2767`       | `4`         | `61`          | `74, 34`            | `102`           |
| `100000`      | `2`         | `195`         | `11`                | NA              |
| `1234567`     | `5`         | `196`         | `2, 24, 46, 68`     | NA              |

<sup>Footnote 1</sup>

NA means not applicable.

##### 5.3.1.44 VARRAW

The external data type `VARRAW` is similar to the external data type `RAW`, except that the first two bytes contain the length of the data. The specified length of the string in a bind or a define call must include the two length bytes. So the largest `VARRAW` string that can be received or sent is `65533` bytes, not `65535`. For converting longer strings, use the `LONG` `VARRAW` data type.

##### 5.3.1.45 NATIVE DOUBLE

This external data type implements the IEEE 754 standard double-precision floating point data type. It is represented in the host system's native floating point format. The data type is stored in the Oracle Server in a byte comparable canonical format, and requires 8 bytes for storage, including the length byte. It is an alternative to Oracle `NUMBER` and has the following advantages over `NUMBER`:

- Fewer bytes used in storage

- Matches data types used by RDBMS Clients

- Supports a wider range of values used in scientific calculations.

##### 5.3.1.46 NATIVE FLOAT

This external data type implements the IEEE 754 single-precision floating point data type. It is represented in the host system's native floating point format. The data type is stored in the Oracle Server in a byte comparable canonical format, and requires 4 bytes for storage, including the length byte. It is an alternative to Oracle `NUMBER` and has the following advantages over `NUMBER`:

- Fewer bytes used in storage

- Matches data types used by RDBMS Clients

- Supports a wider range of values used in scientific calculations

### 5.4 Data Conversions

Table 5-5 lists the supported conversions from Oracle internal data types to external data types, and from external data types to internal column representations.

Note the following conditions:

- A `REF` stored in the database is converted to `OCCI_SQLT_REF` on output.

- An `OCCI_SQLT_REF` is converted to the internal representation of a `REF` on input.

- A named data type stored in the database is converted to `OCCI_SQLT_NTY` (and represented by a C structure in the application) on output.

- An `OCCI_SQLT_NTY` (represented by a C structure in an application) is converted to the internal representation of the corresponding data type on input.

- LOBs and `BFILE`s are represented by descriptors in OCCI applications, so there are no input or output conversions.

Also note that in Table 5-5, conversions have the following numeric codes:

1.  The data type must be in Oracle `ROWID` format for input; it is returned in Oracle `ROWID` format on output.

2.  The data type must be in Oracle `DATE` format for input; it is returned in `Oracle DATE` format on output.

3.  The data type must be in hexadecimal format for input; it is returned in hexadecimal format on output.

4.  The data type must represent a valid number for output.

5.  The length must be less than or equal to 2000 characters.

6.  The data type must be stored in hexadecimal format on output; it is in hexadecimal format on output.

Table 5-5 Data Conversions Between External and Internal Data Types

| NA(2)               | Internal Data Types  |        |                  |                 |                 |                 |                    |                 |                 |                 |
|:--------------------|:---------------------|:-------|:-----------------|:----------------|:----------------|:----------------|:-------------------|:----------------|:----------------|:----------------|
| External Data Types | VARCHAR2             | NUMBER | LONG             | ROWID           | DATE            | RAW             | LONG RAW           | CHAR            | BFLOAT          | BDOUBLE         |
| `CHAR`              | I/O                  | I/O    | I/O              | I/O<sup>1</sup> | I/O<sup>2</sup> | I/O<sup>3</sup> | I<sup>3, 5</sup>   | I/O             | I/O             | I/O             |
| `CHARZ`             | I/O                  | I/O    | I/O              | I/O<sup>1</sup> | I/O<sup>2</sup> | I/O<sup>3</sup> | I<sup>3, 5</sup>   | I/O             | NA              | NA              |
| `DATE`              | I/O                  | NA     | I                | NA              | I/O             | NA              | NA                 | I/O             | NA              | NA              |
| `DECIMAL`           | I/O<sup>4</sup>      | I/O    | I                | NA              | NA              | NA              | NA                 | I/O<sup>4</sup> | NA              | NA              |
| `FLOAT`             | I/O<sup>4</sup>      | I/O    | I                | NA              | NA              | NA              | NA                 | I/O<sup>4</sup> | I/O             | I/O             |
| `INTEGER`           | I/O<sup>4</sup>      | I/O    | I                | NA              | NA              | NA              | NA                 | I/O<sup>4</sup> | I/O             | I/O             |
| `LONG`              | I/O                  | I/O    | I/O              | I/O<sup>1</sup> | I/O<sup>2</sup> | I/O<sup>3</sup> | I/O<sup>3, 5</sup> | I/O             | I/O             | II/O            |
| `LONG RAW`          | O<sup>6</sup>        | NA     | I<sup>5, 6</sup> | NA              | NA              | I/O             | I/O                | O<sup>6</sup>   | NA              | NA              |
| `LONG VARCHAR`      | I/O                  | I/O    | I/O              | I/O<sup>1</sup> | I/O<sup>2</sup> | I/O<sup>3</sup> | I/O<sup>3, 5</sup> | I/O             | I/O             | I/O             |
| `LONG VARRAW`       | I/O<sup>6</sup>      | NA     | I<sup>5, 6</sup> | NA              | NA              | I/O             | I/O                | I/O<sup>6</sup> | NA              | NA              |
| `NUMBER`            | I/O<sup>4</sup>      | I/O    | I                | NA              | NA              | NA              | NA                 | I/O<sup>4</sup> | I/O             | I/O             |
| `OCCI BDouble`      | I/O                  | 1/O    | I                | NA              | NA              | NA              | NA                 | I/O             | I/O             | I/O             |
| `OCCI BFloat`       | I/O                  | 1/O    | I                | NA              | NA              | NA              | NA                 | I/O             | I/O             | I/O             |
| `OCCI Bytes`        | I/O<sup>6</sup>      | NA     | I<sup>5, 6</sup> | NA              | NA              | I/O             | I/O                | I/O<sup>6</sup> | NA              | NA              |
| `OCCI Date`         | I/O<sup>Foot 3</sup> | NA     | I                | NA              | I/O             | NA              | NA                 | I/O             | NA              | NA              |
| `OCCI Number`       | I/O<sup>4</sup>      | I/O    | I                | NA              | NA              | NA              | NA                 | I/O<sup>4</sup> | I/O             | I/O             |
| `OCCI Timestamp`    | NA                   | NA     | NA               | NA              | NA              | NA              | NA                 | NA              | NA              | NA              |
| `RAW`               | I/O<sup>6</sup>      | NA     | I<sup>5, 6</sup> | NA              | NA              | I/O             | I/O                | I/O<sup>6</sup> | NA              | NA              |
| `ROWID`             | I                    | NA     | I                | I/O             | NA              | NA              | NA                 | I               | NA              | NA              |
| `STL string`        | I/O                  | I/O    | I/O              | I/O<sup>1</sup> | I/O<sup>2</sup> | I/O<sup>3</sup> | I/O<sup>3</sup>    | \-              | I/O<sup>4</sup> | I/O<sup>4</sup> |
| `STRING`            | I/O                  | I/O    | I/O              | I/O<sup>1</sup> | I/O<sup>2</sup> | I/O<sup>3</sup> | I/O<sup>3, 5</sup> | I/O             | I/O             | I/O             |
| `UNSIGNED`          | I/O<sup>4</sup>      | I/O    | I                | NA              | NA              | NA              | NA                 | I/O<sup>4</sup> | I/O             | I/O             |
| `VARCHAR`           | I/O                  | I/O    | I/O              | I/O<sup>1</sup> | I/O<sup>2</sup> | I/O<sup>3</sup> | I/O<sup>3</sup>    | NA              | I/O             | I/O             |
| `VARCHAR`2          | I/O                  | I/O    | I/O              | I/O<sup>1</sup> | I/O<sup>2</sup> | I/O<sup>3</sup> | I/O<sup>3, 5</sup> | I/O             | I/O             | I/O             |
| `VARNUM`            | I/O<sup>4</sup>      | I/O    | I                | NA              | NA              | NA              | NA                 | I/O<sup>4</sup> | I/O             | I/O             |
| `VARRAW`            | I/O<sup>6</sup>      | NA     | I<sup>5, 6</sup> | NA              | NA              | I/O             | I/O                | I/O<sup>6</sup> | NA              | NA              |

<sup>Footnote 2</sup> NA means not applicable.

<sup>Footnote 3</sup>

I/O = Conversion is valid for input and output, unless otherwise specified.

This section includes the following topics:

- Data Conversions for LOB Data Types

- Data Conversions for Date, Timestamp, and Interval Data Types

#### 5.4.1 Data Conversions for LOB Data Types

Table 5-6 Data Conversions for LOBs

| EXTERNAL DATATYPES | INTERNAL DATATYPES   |                     |
|:-------------------|:---------------------|:--------------------|
| CLOB               | BLOB                 |                     |
| `VARCHAR`          | I/O<sup>Foot 4</sup> | NA<sup>Foot 5</sup> |
| `CHAR`             | I/O                  | NA                  |
| `LONG`             | I/O                  | NA                  |
| `LONG VARCHAR`     | I/O                  | NA                  |
| `STL String`       | I/O                  | NA                  |
| `RAW`              | NA                   | I/O                 |
| `VARRAW`           | NA                   | I/O                 |
| `LONG RAW`         | NA                   | I/O                 |
| `LONG VARRAW`      | NA                   | I/O                 |
| `OCCI Bytes`       | NA                   | I/O                 |

<sup>Footnote 4</sup>

I/O = Conversion is valid for input and output.

<sup>Footnote 5</sup>

NA means not applicable.

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md) for an introduction to `LOB` data types.

#### 5.4.2 Data Conversions for Date, Timestamp, and Interval Data Types

You can also use a character data type for the host variable used in a fetch or insert operation from or to a datetime or interval column. Oracle performs the conversion between the character data type and datetime/interval data type for you.

Table 5-7 Data Conversions for Date, Timestamp, and Interval Data Types

| External Types                           | Internal Types       |      |     |      |       |                        |                        |
|:-----------------------------------------|:---------------------|:-----|:----|:-----|:------|:-----------------------|:-----------------------|
| NA(6)                                    | VARCHAR, CHAR        | DATE | TS  | TSTZ | TSLTZ | INTERVAL YEAR TO MONTH | INTERVAL DAY TO SECOND |
| `VARCHAR2, CHAR`                         | I/O<sup>Foot 7</sup> | I/O  | I/O | I/O  | I/O   | I/O                    | I/O                    |
| `STL String`                             | I/O                  | I/O  | I/O | I/O  | I/O   | I/O                    | I/O                    |
| `DATE`                                   | I/O                  | I/O  | I/O | I/O  | I/O   | NA                     | NA                     |
| `OCCI Date`                              | I/O                  | I/O  | I/O | I/O  | I/O   | NA                     | NA                     |
| `ANSI DATE`                              | I/O                  | I/O  | I/O | I/O  | I/O   | NA                     | NA                     |
| `TIMESTAMP (TS)`                         | I/O                  | I/O  | I/O | I/O  | I/O   | NA                     | NA                     |
| `OCCI Timestamp`                         | I/O                  | I/O  | I/O | I/O  | I/O   | NA                     | NA                     |
| `TIMESTAMP WITH TIME ZONE (TSTZ)`        | I/O                  | I/O  | I/O | I/O  | I/O   | NA                     | NA                     |
| `TIMESTAMP WITH LOCAL TIME ZONE (TSLTZ)` | I/O                  | I/O  | I/O | I/O  | I/O   | NA                     | NA                     |
| `INTERVAL YEAR TO MONTH`                 | I/O                  | NA   | NA  | NA   | NA    | I/O                    | NA                     |
| `OCCI IntervalYM`                        | I/O                  | NA   | NA  | NA   | NA    | I/O                    | NA                     |
| `INTERVAL DAY TO SECOND`                 | I/O                  | NA   | NA  | NA   | NA    | NA                     | I/O                    |
| `OCCI IntervalDS`                        | I/O                  | NA   | NA  | NA   | NA    | NA                     | I/O                    |

<sup>Footnote 6</sup> NA means not applicable.

<sup>Footnote 7</sup>

I/O = Conversion is valid for input and output.

These consideration apply when converting between Date, Timestamp and Interval data types:

- When assigning a source with time zone to a target without a time zone, the time zone portion of the source is ignored. On assigning a source without a time zone to a target with a time zone, the time zone of the target is set to the session's default time zone.

- When assigning an Oracle `DATE` to a `TIMESTAMP`, the `TIME` portion of the `DATE` is copied over to the `TIMESTAMP`. When assigning a `TIMESTAMP` to Oracle `DATE`, the `TIME` portion of the result `DATE` is set to zero. This is done to encourage migration of Oracle `DATE` to `ANSI` compliant `DATETIME` data types.

- (When assigning an `ANSI` `DATE` to an Oracle `DATE` or a `TIMESTAMP`, the `TIME` portion of the Oracle `DATE` and the `TIMESTAMP` are set to zero. When assigning an Oracle `DATE` or a `TIMESTAMP` to an ANSI `DATE`, the `TIME` portion is ignored.

- When assigning a `DATETIME` to a character string, the `DATETIME` is converted using the session's default `DATETIME` format. When assigning a character string to a `DATETIME`, the string must contain a valid `DATETIME` value based on the session's default `DATETIME` format.

- When assigning a character string to an `INTERVAL`, the character string must be a valid `INTERVAL` character format.

- When converting from `TSLTZ` to `CHAR`, `DATE`, `TIMESTAMP` and `TSTZ`, the value is adjusted to the session time zone.

- When converting from `CHAR`, `DATE`, and `TIMESTAMP` to `TSLTZ`, the session time zone is stored in memory.

- When assigning `TSLTZ` to `ANSI` `DATE`, the time portion is `0`.

- When converting from `TSTZ`, the time zone that the time stamp is in is stored in memory.

- When assigning a character string to an interval, the character string must be a valid interval character format.
