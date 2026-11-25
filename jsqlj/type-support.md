This chapter documents data types supported by the Oracle SQLJ implementation, listing supported SQL types and the Java types that correspond to them. This is followed by details about support for streams and Oracle type extensions. SQLJ support of Java types refers to types that can be used in host expressions.

This chapter covers the following topics:

- Supported Types for Host Expressions

- Support for Streams

- Support for JDBC 2.0 LOB Types and Oracle Type Extensions

**See Also:**

[Objects\_ Collections\_ and OPAQUE Types](objects-collections-and-OPAQUE-types.md)

### 6.1 Supported Types for Host Expressions

This section summarizes the types supported by the Oracle SQLJ implementation, including information about new support for Java Database Connectivity (JDBC) 2.0 types.

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/JDBC-reference-information.md) for a complete list of legal Java mappings for each Oracle SQL type

**Note:**

SQLJ performs implicit conversions between SQL and Java types. Although this is generally useful and helpful, it can produce unexpected results. Do not rely on translation-time type-checking alone to ensure the correctness of your code.

This section covers the following topics:

- Summary of Supported Types

- Supported Types and Requirements for JDBC 2.0

- Using PL/SQL BOOLEAN\_ RECORD Types\_ and TABLE Types

#### 6.1.1 Summary of Supported Types

Table 6-1 lists the Java types that you can use in host expressions when employing Oracle JDBC drivers. This table also documents the correlation between Java types, SQL types whose type codes are defined in the `oracle.jdbc.OracleTypes` class, and data types in Oracle Database 12c Release 2 (12.2).

**Note:**

The `OracleTypes` class simply defines a type code, which is an integer constant, for each Oracle data type. For standard JDBC types, the `OracleTypes` value is identical to the standard `java.sql.Types` value.

SQL data output to a Java variable is converted to the corresponding Java type. A Java variable input to SQL is converted to the corresponding Oracle data type.

Table 6-1 Type Mappings for Supported Host Expression Types

| Java Type                                                                                                                      | OracleTypes Definition               | Oracle SQL Data Type                                                                                       |
|:-------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------|:-----------------------------------------------------------------------------------------------------------|
| STANDARD JDBC 1.x TYPES                                                                                                        |                                      |                                                                                                            |
| `boolean`                                                                                                                      | `BIT`                                | `NUMBER`                                                                                                   |
| `byte`                                                                                                                         | `TINYINT`                            | `NUMBER`                                                                                                   |
| `short`                                                                                                                        | `SMALLINT`                           | `NUMBER`                                                                                                   |
| `int`                                                                                                                          | `INTEGER`                            | `NUMBER`                                                                                                   |
| `long`                                                                                                                         | `BIGINT`                             | `NUMBER`                                                                                                   |
| `float`                                                                                                                        | `REAL`                               | `NUMBER`                                                                                                   |
| `double`                                                                                                                       | `FLOAT`, `DOUBLE`                    | `NUMBER`                                                                                                   |
| `java.lang.String`                                                                                                             | `CHAR` `VARCHAR` `LONGVARCHAR`       | `CHAR` `VARCHAR2` `LONG`                                                                                   |
| `byte[]`                                                                                                                       | `BINARY` `VARBINARY` `LONGVARBINARY` | `RAW` `RAW` `LONGRAW`                                                                                      |
| `java.sql.Date`                                                                                                                | `DATE`                               | `DATE`                                                                                                     |
| `java.sql.Time`                                                                                                                | `TIME`                               | `DATE`                                                                                                     |
| `java.sql.Timestamp`                                                                                                           | `TIMESTAMP` `TIMESTAMP`              | `DATE` `TIMESTAMP`                                                                                         |
| `java.math.BigDecimal`                                                                                                         | `NUMERIC` `DECIMAL`                  | `NUMBER` `NUMBER`                                                                                          |
| STANDARD JDBC 2.0 TYPES                                                                                                        |                                      |                                                                                                            |
| `java.sql.Blob`                                                                                                                | `BLOB`                               | `BLOB`                                                                                                     |
| `java.sql.Clob`                                                                                                                | `CLOB`                               | `CLOB`                                                                                                     |
| `java.sql.Struct`                                                                                                              | `STRUCT`                             | Object types                                                                                               |
| `java.sql.Ref`                                                                                                                 | `REF`                                | Reference types                                                                                            |
| `java.sql.Array`                                                                                                               | `ARRAY`                              | Collection types                                                                                           |
| Custom object classes implementing `java.sql.SQLData`                                                                          | `STRUCT`                             | Object types                                                                                               |
| JAVA WRAPPER CLASSES                                                                                                           |                                      |                                                                                                            |
| `java.lang.Boolean`                                                                                                            | `BIT`                                | `NUMBER`                                                                                                   |
| `java.lang.Byte`                                                                                                               | `TINYINT`                            | `NUMBER`                                                                                                   |
| `java.lang.Short`                                                                                                              | `SMALLINT`                           | `NUMBER`                                                                                                   |
| `java.lang.Integer`                                                                                                            | `INTEGER`                            | `NUMBER`                                                                                                   |
| `java.lang.Long`                                                                                                               | `BIGINT`                             | `NUMBER`                                                                                                   |
| `java.lang.Float`                                                                                                              | `REAL`                               | `NUMBER`                                                                                                   |
| `java.lang.Double`                                                                                                             | `FLOAT`, `DOUBLE`                    | `NUMBER`                                                                                                   |
| SQLJ STREAM CLASSES                                                                                                            |                                      |                                                                                                            |
| `sqlj.runtime.BinaryStream`                                                                                                    | `LONGVARBINARY`                      | `LONG RAW`                                                                                                 |
| `sqlj.runtime.CharacterStream`                                                                                                 | `LONGVARCHAR`                        | `LONG`                                                                                                     |
| `sqlj.runtime.AsciiStream` (Deprecated; use `CharacterStream`.)                                                                | `LONGVARCHAR`                        | `LONG`                                                                                                     |
| `sqlj.runtime.UnicodeStream` (Deprecated; use `CharacterStream`.)                                                              | `LONGVARCHAR`                        | `LONG`                                                                                                     |
| ORACLE EXTENSIONS                                                                                                              |                                      |                                                                                                            |
| `oracle.sql.NUMBER`                                                                                                            | `NUMBER`                             | `NUMBER`                                                                                                   |
| `oracle.sql.CHAR`                                                                                                              | `CHAR`                               | `CHAR`                                                                                                     |
| `oracle.sql.RAW`                                                                                                               | `RAW`                                | `RAW`                                                                                                      |
| `oracle.sql.DATE`                                                                                                              | `DATE`                               | `DATE`                                                                                                     |
| `oracle.sql.TIMESTAMP`                                                                                                         | `TIMESTAMP`                          | `TIMESTAMP`                                                                                                |
| `oracle.sql.TIMESTAMPTZ`                                                                                                       | `TIMESTAMPTZ`                        | `TIMESTAMP-WITH- TIMEZONE`                                                                                 |
| `oracle.sql.TIMESTAMPLTZ`                                                                                                      | `TIMESTAMPLTZ`                       | `TIMESTAMP-WITH- LOCAL-TIMEZONE`                                                                           |
| `oracle.sql.ROWID`                                                                                                             | `ROWID`                              | `ROWID`                                                                                                    |
| `oracle.sql.BLOB`                                                                                                              | `BLOB`                               | `BLOB`                                                                                                     |
| `oracle.sql.CLOB`                                                                                                              | `CLOB`                               | `CLOB`                                                                                                     |
| `oracle.sql.BFILE`                                                                                                             | `BFILE`                              | `BFILE`                                                                                                    |
| `oracle.sql.STRUCT`                                                                                                            | `STRUCT`                             | Object types                                                                                               |
| `oracle.sql.REF`                                                                                                               | `REF`                                | Reference types                                                                                            |
| `oracle.sql.ARRAY`                                                                                                             | `ARRAY`                              | Collection types                                                                                           |
| `oracle.sql.OPAQUE`                                                                                                            | `OPAQUE`                             | `OPAQUE` types                                                                                             |
| Custom object classes implementing `oracle.sql.ORAData`                                                                        | `STRUCT`                             | Object types                                                                                               |
| Custom reference classes implementing `oracle.sql.ORAData`                                                                     | `REF`                                | Reference types                                                                                            |
| Custom collection classes implementing `oracle.sql.ORAData`                                                                    | `ARRAY`                              | Collection types                                                                                           |
| Custom classes implementing `oracle.sql.ORAData` for `OPAQUE` types (for example, `oracle.xdb.XMLType`)                        | `OPAQUE`                             | `OPAQUE` types                                                                                             |
| Other custom Java classes implementing `oracle.sql.ORAData` (to wrap any `oracle.sql` type)                                    | Any                                  | Any                                                                                                        |
| SQLJ object Java types (can implement either `SQLData` or `ORAData`)                                                           | `JAVA_STRUCT`                        | SQLJ object SQL types (`JAVA_STRUCT` behind the scenes; automatic conversion to an appropriate Java class) |
| JAVA TYPES FOR PL/SQL TYPES                                                                                                    |                                      |                                                                                                            |
| Scalar indexed-by table represented by a Java numeric array or an array of `String`, `oracle.sql.CHAR`, or `oracle.sql.NUMBER` | NA                                   | NA<br>Note: There is a `PLSQL_INDEX_TABLE` type, but it does not appear to be used externally.             |
| GLOBALIZATION SUPPORT                                                                                                          |                                      |                                                                                                            |
| `oracle.sql.NCHAR`                                                                                                             | `CHAR`                               | `CHAR`                                                                                                     |
| `oracle.sql.NString`                                                                                                           | `CHAR` `VARCHAR` `LONGVARCHAR`       | `CHAR` `VARCHAR2` `LONG`                                                                                   |
| `oracle.sql.NCLOB`                                                                                                             | `CLOB`                               | `CLOB`                                                                                                     |
| `oracle.sqlj.runtime.NcharCharacterStream`                                                                                     | `LONGVARCHAR`                        | `LONG`                                                                                                     |
| `oracle.sqlj.runtime. NcharAsciiStream` (Deprecated; use `NcharCharacterStream`.)                                              | `LONGVARCHAR`                        | `LONG`                                                                                                     |
| `oracle.sqlj.runtime. NcharUnicodeStream` (Deprecated; use `NcharCharacterStream`.)                                            | `LONGVARCHAR`                        | `LONG`                                                                                                     |
| QUERY RESULT OBJECTS                                                                                                           |                                      |                                                                                                            |
| `java.sql.ResultSet`                                                                                                           | `CURSOR`                             | `CURSOR`                                                                                                   |
| SQLJ iterator objects                                                                                                          | `CURSOR`                             | `CURSOR`                                                                                                   |

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/JDBC-standards-support.md) for more information about Oracle type support.

The following points relate to type support for standard features:

- JDBC and SQLJ do not support Java `char` and `Character` types. Instead, use the Java `String` type to represent character data.

- Do not confuse the supported `java.sql.Date` type with `java.util.Date`, which is not directly supported. The `java.sql.Date` class is a wrapper for `java.util.Date` that enables JDBC to identify the data as a SQL `DATE` and adds formatting and parsing operations to support JDBC escape syntax for date values.

- Remember that all numeric types in Oracle Database 12c Release 2 (12.2) are stored as `NUMBER`. Although you can specify additional precision when you declare a `NUMBER` during table creation, this precision may be lost when retrieving the data through Oracle JDBC drivers, depending on the Java type that you use to receive the data. An `oracle.sql.NUMBER` instance would preserve full information.

- The Java wrapper classes, such as `Integer` and `Float`, are useful in cases where `NULL` may be returned by the SQL statement. Primitive types, such as `int` and `float`, cannot contain null values.

  **See Also:**

  "[NULL-Handling](key-programming-considerations.md)"

- The SQLJ stream classes are required in using streams as host variables.

  **See Also:**

  "Support for Streams"

- Weak types cannot be used for `OUT` or `INOUT` parameters. This applies to the `Struct`, `Ref`, and `Array` standard JDBC 2.0 types, as well as to corresponding Oracle extended types.

- A new set of interfaces, in the `oracle.jdbc` package, was first added in the Oracle9i JDBC implementation in place of classes of the `oracle.jdbc.driver` package. These interfaces provide a more generic way for users to access Oracle-specific features using Oracle JDBC drivers. Specifically, when creating programs for the middle tier, you should use the `oracle.jdbc` application programming interface (API). However, SQLJ programmers will not typically use these interfaces directly. They are used transparently by the SQLJ run time or in Oracle-specific generated code.

  **See Also:**

  "[Custom Java Class Interface Specifications](objects-collections-and-OPAQUE-types.md)"

- For information about SQLJ support for result set and iterator host variables, refer to "[Using Iterators and Result Sets as Host Variables](basic-language-features.md)"[Using Iterators and Result Sets as Stored Function Returns](basic-language-features.md).

The following points relate to Oracle extensions:

- The Oracle SQLJ implementation requires any class that implements `oracle.sql.ORAData` to set the static` _SQL_TYPECODE` parameter according to values defined in the `OracleTypes` class. In some cases, an additional parameter must be set as well, such as` _SQL_NAME` for objects and` _SQL_BASETYPE` for object references.

- The `oracle.sql` classes are wrappers for SQL data for each of the Oracle data types. The `ARRAY`, `STRUCT`, `REF`, `BLOB`, and `CLOB` classes correspond to standard JDBC 2.0 interfaces.

  **See Also:**

  [Oracle Database JDBC Developer's Guide](../jjdbc/Oracle-extensions.md) for information about these classes and Oracle extensions

- Custom Java classes can map to Oracle objects, which implement `ORAData` or `SQLData`, references, which implement `ORAData` only, collections, which implement `ORAData` only, `OPAQUE` types, which implement `ORAData` only, or other SQL types for customized handling, which implement `ORAData` only.

- The Oracle SQLJ implementation has functionality for automatic blank padding when comparing a string to a `CHAR` column value for a `WHERE` clause. Otherwise the string would have to be padded to match the number of characters in the database column. This is available as a SQLJ translator option for Oracle-specific code generation, or as an Oracle customizer option for ISO standard code generation.

- Weak types cannot be used for `OUT` or `INOUT` parameters. This applies to the `STRUCT`, `REF`, and `ARRAY` Oracle extended types and corresponding standard JDBC 2.0 types, as well as to Oracle `OPAQUE` types.

- Using any of the Oracle extensions requires the following:

  - Oracle JDBC driver

  - Oracle-specific code generation or Oracle customization during translation

  - Oracle SQLJ run time when your application runs

#### 6.1.2 Supported Types and Requirements for JDBC 2.0

As indicated in Table 6-1, the Oracle JDBC and SQLJ implementations support JDBC 2.0 types in the standard `java.sql` package. This section lists JDBC 2.0 supported types and related Oracle extensions.

Table 6-2 lists the JDBC 2.0 types supported by the Oracle SQLJ implementation. You can use them wherever you can use the corresponding Oracle extensions, summarized in the table.

The Oracle extensions have been available in prior releases and are still available as well. These `oracle.sql.*` classes provide functionality to wrap raw SQL data.

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/Oracle-extensions.md)

Table 6-2 Correlation between Oracle Extensions and JDBC 2.0 Types

| JDBC 2.0 Type      | Oracle Extension                                          |
|:-------------------|:----------------------------------------------------------|
| `java.sql.Blob`    | `oracle.sql.BLOB`                                         |
| `java.sql.Clob`    | `oracle.sql.CLOB`                                         |
| `java.sql.Struct`  | `oracle.sql.STRUCT`                                       |
| `java.sql.Ref`     | `oracle.sql.REF`                                          |
| `java.sql.Array`   | `oracle.sql.ARRAY`                                        |
| `java.sql.SQLData` | NA                                                        |
| NA                 | `oracle.sql.ORAData (_SQL_TYPECODE = OracleTypes.STRUCT)` |

`ORAData` functionality is an Oracle-specific alternative to standard `SQLData` functionality for Java support of user-defined types.

**See Also:**

"[Custom Java Classes](objects-collections-and-OPAQUE-types.md)", "Support for BLOB\_ CLOB\_ and BFILE", and "[Support for Weakly Typed Objects\_ References\_ and Collections](objects-collections-and-OPAQUE-types.md)"

The following JDBC 2.0 types are currently not supported in the Oracle JDBC and SQLJ implementations:

- `JAVA_OBJECT`: Represents an instance of a Java type in a SQL column.

- `DISTINCT`: A distinct SQL type represented in or retrievable from a basic SQL type. For example, `SHOESIZE` --\> `NUMBER`.

**Note:**

Beginning with Oracle Database 11g, the Oracle SQLJ implementation supports the ISO SQLJ feature of allowing array types for iterator columns. You can declare an iterator that uses `java.sql.Array` or `oracle.sql.ARRAY` columns. For example, suppose the following database table is defined:

    CREATE OR REPLACE TYPE arr_type IS VARRAY(20) OF NUMBER;
    CREATE TABLE arr_type (arr_col1 arr_type, arr_col2
                           arr_type);

You could define a corresponding iterator type as follows:

    #sql static iterator MyIter (oracle.sql.ARRAY arr_col1,
                                 java.sql.Array arr_col2);

#### 6.1.3 Using PL/SQL BOOLEAN, RECORD Types, and TABLE Types

The Oracle SQLJ and JDBC implementations do not support calling arguments or return values of the PL/SQL `BOOLEAN` type or RECORD types.

##### Support for TABLE Types

Oracle JDBC drivers support scalar PL/SQL indexed-by tables.

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/JDBC-reference-information.md)

The Oracle SQLJ implementation simplifies the process of writing and retrieving data in scalar indexed-by tables. The following array types are supported:

- Numeric types: `int[]`, `long[]`, `float[]`, `double[]`, `short[]`, `java.math.BigDecimal[]`, `oracle.sql.NUMBER[]`

- Character types: `java.lang.String[]`, `oracle.sql.CHAR[]`

The following is an example of writing indexed-by table data to the database:

    int[] vals = {1,2,3};
    #sql { call procin(:vals) };

The following is an example of retrieving indexed-by table data from the database:

    oracle.sql.CHAR[] outvals;
    #sql { call procout(:OUT outvals/*[111](22)*/) };

You must specify the maximum length of the output array being retrieved, using the `[xxx]` syntax inside the `/*...*/` syntax, as shown. Also, for character-like binds, you can optionally include the `(xx)` syntax, as shown, to specify the maximum length of an array element in bytes.

**Note:**

The `oracle.sql.Datum` class is not supported directly. You must use an appropriate subclass, such as `oracle.sql.CHAR` or `oracle.sql.NUMBER`.

##### Workarounds for Unsupported Types

As a workaround for an unsupported type, you can create wrapper procedures that process the data using supported types. For example, to wrap a stored procedure that uses PL/SQL boolean values, you can create a stored procedure that takes a character or number from JDBC and passes it to the original procedure as `BOOLEAN`, or for an output parameter, accepts a `BOOLEAN` argument from the original procedure and passes it as a `CHAR` or `NUMBER` to JDBC. Similarly, to wrap a stored procedure that uses PL/SQL records, you can create a stored procedure that handles a record in its individual components, such as `CHAR` and `NUMBER`. To wrap a stored procedure that uses PL/SQL TABLE types, you can break the data into components or perhaps use Oracle collection types.

The following is an example of a PL/SQL wrapper procedure `MY_PROC` for a stored procedure `PROC` that takes a `BOOLEAN` as input:

    PROCEDURE MY_PROC (n NUMBER) IS
    BEGIN
       IF n=0
          THEN proc(false);
          ELSE proc(true);
       END IF;
    END;

    PROCEDURE PROC (b BOOLEAN) IS
    BEGIN
    ...
    END;

#### 6.1.4 Backward Compatibility for Previous Oracle JDBC Releases

This section summarizes backward compatibility issues when using the Oracle SQLJ implementation with earlier Oracle JDBC releases.

In Oracle Database 11g release 1 (11.1), SQLJ fully supports applications developed in Oracle9i Database and Oracle Database 10g release 1 (10.1). However, in Oracle Database 11g release 1 (11.1), JDBC resources are no longer closed by the SQLJ run time resource finalizers. Therefore, some applications developed prior to Oracle Database 11g release 1 (11.1) may observe JDBC connection and statement leaking. To prevent such leaking, you must properly close all the SQLJ run-time resources, such as connection context, execution context, and iterator, in your SQLJ applications.

**Note:**

Oracle9i release 2 first added support for OPAQUE types and TIMESTAMP types.

##### Backward Compatibility for Oracle8i Database

The following Oracle Database 11g features, which are also available in Oracle9i Database, are not supported or supported differently in the Oracle8i JDBC drivers:

- The `oracle.sql.ORAData` and `ORADataFactory` interfaces for Java mapping of user-defined SQL types

  Use the `oracle.sql.CustomDatum` and `CustomDatumFactory` interfaces instead.

- Oracle extensions for character types for globalization support: `NCHAR`, `NCLOB`, `NString`, and `NcharCharacterStream` (or `NcharAsciiStream` and `NcharUnicodeStream` in earlier releases)

### 6.2 Support for Streams

Standard SQLJ provides the following specialized classes for convenient processing of long data in streams:

- `sqlj.runtime.BinaryStream`

- `sqlj.runtime.CharacterStream`

These stream types can be used for iterator columns to retrieve data from the database or for input host variables to send data to the database. As with Java streams in general, these classes allow the convenience of processing and transferring large data items in manageable chunks.

This section discusses general use of these classes, Oracle SQLJ extended functionality, and stream class methods. It covers the following topics:

- General Use of SQLJ Streams

- Key Aspects of Stream Support Classes

- Using SQLJ Streams to Send Data

- Retrieving Data into Streams: Precautions

- Using SQLJ Streams to Retrieve Data

- Stream Class Methods

- Examples of Retrieving and Processing Stream Data

- SQLJ Stream Objects as Output Parameters and Function Return Values

**Note:**

Starting from JDBC 2.0, the `CharacterStream` class replaces the `AsciiStream` and `UnicodeStream` classes. `CharacterStream` shelters users from unnecessary logistics regarding encoding.

#### 6.2.1 General Use of SQLJ Streams

Table 6-1 lists the data types you would typically process using these stream classes. To summarize:

- `BinaryStream` is typically used for `LONG RAW` (`Types.LONGVARBINARY`), but might also be used for `RAW` (`Types.BINARY` or `Types.VARBINARY`).

- `CharacterStream` is typically used for `LONG` (`java.sql.Types.LONGVARCHAR`), but might also be used for `VARCHAR2` (`Types.VARCHAR`).

Of course, any use of streams is at your discretion. You can use the SQLJ stream types for host variables to either send or retrieve data.

As Table 6-1 documents, `LONG` and `VARCHAR2` data can also be manifested in Java `String`, while `RAW` and `LONGRAW` data can also be manifested in Java `byte[]` arrays. Also, if your database supports large object types, such as `BLOB` and `CLOB`, then you may find these to be preferable to types like `LONG` and `LONG RAW`, although streams might still be used in extracting data from large objects. The Oracle SQLJ and JDBC implementations support large object types.

**See Also:**

"Support for BLOB\_ CLOB\_ and BFILE"

Both SQLJ stream classes are subclasses of standard Java classes, `java.io.InputStream` for `BinaryStream` and `java.io.Reader` for `CharacterStream`, and act as wrappers to provide the functionality required by SQLJ. This functionality is to communicate to SQLJ the type and length of the underlying data so that it can be processed and formatted properly.

#### 6.2.2 Key Aspects of Stream Support Classes

The following abbreviated code illustrates key aspects of the `BinaryStream` class, such as what it extends, constructor signatures, and key method signatures:

    public class sqlj.runtime.BinaryStream extends sqlj.runtime.StreamWrapper
    {   public sqlj.runtime.BinaryStream(java.io.InputStream);
        public sqlj.runtime.BinaryStream(java.io.InputStream,int);
        public java.io.InputStream getInputStream();
        public int getLength();
        public void setLength(int);
    }

The following abbreviated code illustrates key aspects of the `CharacterStream` class:

    public class sqlj.runtime.CharacterStream extends java.io.FilterReader
    {   public sqlj.runtime.CharacterStream(java.io.Reader);
        public sqlj.runtime.CharacterStream(java.io.Reader,int);
        public int getLength();
        public java.io.Reader getReader();
        public void setLength(int);
    }

**Note:**

- The `int` parameters in the constructors are for data length, in bytes or characters as applicable.

- For any method that takes a `java.io.InputStream` object as input, you can use a `BinaryStream` object instead. Similarly, for any method that takes a `java.io.Reader` object as input, you can use a `CharacterStream` object instead.

- The deprecated `AsciiStream` and `UnicodeStream` classes have the same key aspects and signatures as `BinaryStream`.

#### 6.2.3 Using SQLJ Streams to Send Data

Standard SQLJ enables you to use streams as host variables to update the database. A key point in sending a SQLJ stream to the database is that you must somehow determine the length of the data and specify that length to the constructor of the SQLJ stream.

You can use a SQLJ stream to send data to the database as follows:

1.  Determine the length of the data.

2.  Create an appropriate standard Java data object for input. For `BinaryStream`, this would be an input stream, an instance of `java.io.InputStream` or some subclass. For `CharacterStream`, this would be a reader object, an instance of `java.io.Reader` or some subclass.

3.  Create an instance of the appropriate SQLJ stream class depending on the type of data, passing the data object and length to the constructor.

4.  Use the SQLJ stream instance as a host variable in a suitable SQL operation in a SQLJ executable statement.

5.  Close the stream.

**Note:**

Although not required, it is recommended that you close the stream after using it.

##### Updating LONG or LONG RAW from a File

This section illustrates how to create a `CharacterStream` object or a `BinaryStream` object from a `File` object and use it to update the database. The code example at the end uses a `CharacterStream` for a `LONG` column.

In updating a database column from a file, a step is needed to determine the length. You can do this by creating a `java.io.File` object before you create your input stream.

Following are the steps for updating the database from a file:

1.  Create a `java.io.File` object from your file. You can specify the file path name to the `File` class constructor.

2.  Use the `length()` method of the `File` object to determine the length of the data. This method returns a `long` value, which you must cast to an `int` for input to the SQLJ stream class constructor.

    **Note:**

    Before performing this cast, test the `long` value to ensure that it is not too big to fit into an `int` variable. The static constant `MAX_VALUE` in the class `java.lang.Integer` indicates the largest possible Java `int` value.

3.  For character data, create a `java.io.FileReader` object from the `File` object. You can pass the `File` object to the `FileReader` constructor.

    For binary data, create a `java.io.FileInputStream` object from the `File` object. You can pass the `File` object to the `FileInputStream` constructor.

4.  Create an appropriate SQLJ stream object. This would be a `CharacterStream` object for a character file or a `BinaryStream` object for a binary file. Pass the `FileReader` or `FileInputStream` object, as applicable, and the data length as an `int` to the SQLJ stream class constructor.

5.  Use the SQLJ stream object as a host variable in an appropriate SQL operation in a SQLJ executable statement.

The following is an example of writing `LONG` data to the database from a file. Presume you have an HTML file in `/private/mydir/myfile.html` and want to insert the file contents into a `LONG` column, `chardata`, in the `filetable` database table.

    import java.io.*;
    import sqlj.runtime.*;

    ...
    File myfile = new File ("/private/mydir/myfile.html");
    int length = (int)myfile.length();     // Must cast long output to int.
    FileReader filereader = new FileReader(myfile);
    CharacterStream charstream = new CharacterStream(filereader, length);
    #sql { INSERT INTO filetable (chardata) VALUES (:charstream) };
    charstream.close();
    ...

##### Updating LONG RAW from a Byte Array

This section illustrates how to create a `BinaryStream` object from a byte array and uses it to update the database.

You must determine the length of the data before updating the database from a byte array. This is more trivial for arrays than for files, though, because all Java arrays have functionality to return the length.

Following are the steps in updating the database from a byte array:

1.  Use the `length` functionality of the array to determine the length of the data. This returns an `int`, which is what you will need for the constructor of any of the SQLJ stream classes.
2.  Create a `java.io.ByteArrayInputStream` object from your array. You can pass the byte array to the `ByteArrayInputStream` constructor.
3.  Create a `BinaryStream` object. Pass the `ByteArrayInputStream` object and data length as an `int` to the `BinaryStream` class constructor.
    The constructor signature is as follows:

        BinaryStream (InputStream in, int length)

    You can use an instance of `java.io.InputStream` or of any subclass, such as the `ByteArrayInputStream` class.
4.  Use the SQLJ stream object as a host variable in an appropriate SQL operation in a SQLJ executable statement.

The following is an example of writing `LONG RAW` data to the database from a byte array. Presume you have a byte array, `bytearray[]`, and you want to insert its contents into a `LONG RAW` column, `BINDATA`, in the `BINTABLE` database table.

    import java.io.*;
    import sqlj.runtime.*;

    ...
    byte[] bytearray = new byte[100];

    (Populate bytearray somehow.)
    ...
    int length = bytearray.length;
    ByteArrayInputStream arraystream = new ByteArrayInputStream(bytearray);
    BinaryStream binstream = new BinaryStream(arraystream, length);
    #sql { INSERT INTO bintable (bindata) VALUES (:binstream) };
    binstream.close();
    ...

**Note:**

It is not necessary to use a stream as in this example. Alternatively, you can update the database directly from a byte array.

#### 6.2.4 Retrieving Data into Streams: Precautions

You can also use the SQLJ stream classes to retrieve data, but the logistics of using streams make certain precautions necessary with some database products. When reading long data and writing it to a stream using Oracle Database 12c Release 2 (12.2) and an Oracle JDBC driver, you must be careful in how you access and process the stream data.

As Oracle JDBC drivers access data from an iterator row, they must flush any stream item from the communications pipe before accessing the next data item. Even though the stream data is written to a local stream while the iterator row is processed, this stream data will be lost if you do not read it from the local stream before the JDBC driver accesses the next data item. This is because of the manner in which streams must be processed, which is due to their potentially large size and unknown length.

Therefore, as soon as your Oracle JDBC driver has accessed a stream item and written it to a local stream variable, you must read and process the local stream before anything else is accessed from the iterator.

This is especially problematic in using positional iterators, with their requisite `FETCH INTO` syntax. With each fetch, all columns are read before any are processed. Therefore, there can be only one stream item and it must be the last item accessed.

The precautions you must take can be summarized as follows:

- When using a positional iterator, you can have only one stream column and it must be the last column. As soon as you have fetched each row of the iterator, writing the stream item to a local input stream variable in the process, you must read and process the local stream variable before advancing to the next row of the iterator.

- When using a named iterator, you can have multiple stream columns. However, as you process each iterator row, each time you access a stream field, writing the data to a local stream variable in the process, you must read and process the local stream immediately, before reading anything else from the iterator.

  Furthermore, in processing each row of a named iterator, you must call the column accessor methods in the same order in which the database columns were selected in the query that populated the iterator. As mentioned in the preceding discussion, this is because stream data remains in the communications pipe after the query. If you try to access columns out of order, then the stream data may be skipped over and lost in the course of accessing other columns.

**Note:**

- Oracle Database 12c Release 2 (12.2) and Oracle JDBC drivers do not support use of streams in `SELECT INTO` statements.

- Input streams, by default, do not support `mark` and `reset` methods. If you pass any arbitrary input stream to the constructor, then the `reset` method of `InputStream` class will throw an `IOException`. So, always ensure that the input stream is in the proper state when passed to the `NcharAsciiStream` constructor. For example, reset the stream before passing it to `NcharAsciiStream` if the stream has no more data or if the stream is closed.

#### 6.2.5 Using SQLJ Streams to Retrieve Data

To retrieve data as a stream, standard SQLJ enables you to select data into a named or positional iterator that has a column of the appropriate SQLJ stream type.

This section covers the basic steps in retrieving data into a SQLJ stream using a positional iterator or a named iterator, taking into account the precautions documented in the preceding section.

**See Also:**

"Stream Class Methods" and "Examples of Retrieving and Processing Stream Data"

##### Using a SQLJ Stream Column in a Positional Iterator

Use the following steps to retrieve data into a SQLJ stream using a positional iterator:

1.  Declare a positional iterator class with the last column being of the appropriate SQLJ stream type.

2.  Declare a local variable of your iterator type.

3.  Declare a local variable of the appropriate SQLJ stream type. This will be used as a host variable to receive data from each row of the SQLJ stream column of the iterator.

4.  Execute a query to populate the iterator you declared in Step 2.

5.  Process the iterator as usual. Because the host variables in the `INTO`-list of the `FETCH INTO` statement must be in the same order as the columns of the positional iterator, the local input stream variable is the last host variable in the list.

    **See Also:**

    "[Using Positional Iterators](basic-language-features.md)"

6.  In the iterator processing loop, after each iterator row is accessed, immediately read and process the local input stream, storing or printing the stream data as desired.

7.  Close the local input stream each time through the iterator processing loop.

8.  Close the iterator.

**Note:**

Although not required, it is recommended that you close the local input stream each time through the iterator processing loop.

\<\<\<\[for 11g?\] Use code examples. \>\>\>

##### Using SQLJ Stream Columns in a Named Iterator

Use the following steps to retrieve data into one or more SQLJ streams using a named iterator:

1.  Declare a named iterator class with one or more columns of appropriate SQLJ stream type.
2.  Declare a local variable of your iterator type.
3.  Declare a local variable of some input stream or reader type for each SQLJ stream column in the iterator. These will be used to receive data from the stream-column accessor methods. These local stream variables need not be of the SQLJ stream types. They can be standard `java.io.InputStream` or `java.io.Reader`, as applicable.
    **Note:**

    The local stream variables need not be of the SQLJ stream types, because the data was already correctly formatted as a result of the iterator columns being of appropriate SQLJ stream types.
4.  Execute a query to populate the iterator you declared in Step 2.
5.  Process the iterator as usual. In processing each row of the iterator, as each stream-column accessor method returns the stream data, write it to the corresponding local input stream variable you declared in Step 3.
    To ensure that stream data will not be lost, call the column accessor methods in the same order in which columns were selected in the query in Step 4.

    **See Also:**

    "[Using Positional Iterators](basic-language-features.md)"
6.  In the iterator processing loop, immediately after calling the accessor method for any stream column and writing the data to a local input stream variable, read and process the local input stream, storing or printing the stream data as desired.
7.  Close the local input stream each time through the iterator processing loop.
8.  Close the iterator.

\<\<\<\[for 11g?\] Use code examples. \>\>\>

**Note:**

- When you populate a SQLJ stream object with data, the length attribute of the stream will not be meaningful. This attribute is meaningful only when you set it explicitly, either using the `setLength()` method that each SQLJ stream class provides or specifying the length to the constructor.

- Although not required, it is recommended that you close the local input stream each time through the iterator processing loop.

#### 6.2.6 Stream Class Methods

In processing a SQLJ stream column in a named or positional iterator, the local stream variable used to receive the stream data can be either a SQLJ stream type or the standard `java.io.InputStream` or `java.io.Reader` type, as applicable. In either case, standard methods of the input data object are supported.

If the local stream variable is a SQLJ stream type, `BinaryStream` or `CharacterStream`, you have the option of either reading data directly from the SQLJ stream object or retrieving the underlying `InputStream` or `Reader` object and reading data from that.

**Note:**

This is just a matter of preference. The former approach is simpler. However, the latter approach involves more direct and efficient data access.

##### Binary Stream Methods

The `BinaryStream` class is a subclass of the `sqlj.runtime.StreamWrapper` class. The `StreamWrapper` class provides the following key methods:

- `InputStream getInputStream()`: You can optionally use this method to get the underlying `java.io.InputStream` object. However, this is not required, because you can also process SQLJ stream objects directly.

- `void setLength(int length)`: You can use this to set the `length` attribute of a SQLJ stream object. This is not necessary if you have already set `length` in constructing the stream object, unless you want to change it for some reason.

  The `length` attribute must be set to an appropriate value before you send a SQLJ stream to the database.

- `int getLength()`: This method returns the value of the `length` attribute of a SQLJ stream. This value is meaningful only if you explicitly set it using the stream object constructor or the `setLength()` method. When you retrieve data into a stream, the `length` attribute is not set automatically.

The `sqlj.runtime.StreamWrapper` class is a subclass of the `java.io.FilterInputStream` class, which is a subclass of the `java.io.InputStream` class. The following important methods of the `InputStream` class are supported by the SQLJ `BinaryStream` class as well:

- `int read ()`: Reads the next byte of data from the input stream. The byte of data is returned as an `int` value in the range 0 to 255. If the end of the stream has already been reached, then the value `-1` is returned. This method blocks program execution until one of the following:

  - Input data is available

  - The end of the stream is detected

  - An exception is thrown

- `int read (byte b[])`: Reads up to `b.length` bytes of data from the input stream, writing the data into the specified `b[]` byte array. It returns an `int` value indicating how many bytes were read, or `-1` if the end of the stream has already been reached. This method blocks program execution until input is available.

- `int read (byte b[], int off, int len)`: Reads up to `len` bytes of data from the input stream, starting at the byte specified by the offset, `off`, and writing the data into the specified `b[]` byte array. It returns an `int` value indicating how many bytes were read, or `-1` if the end of the stream has already been reached. This method blocks until input is available.

- `long skip (long n)`: Skips over and discards `n` bytes of data from the input stream. However, in some circumstances, this method will actually skip a smaller number of bytes. It returns a `long` value indicating the actual number of bytes skipped.

- `void close()`: Closes the stream and releases any associated resources.

##### Character Stream Methods

The `CharacterStream` class provides the following key methods:

- `Reader getReader()`: You can optionally use this method to get the underlying `java.io.Reader` object. However, this is not required, because you can also process SQLJ stream objects directly.

- `void setLength(int length)`: You can use this method to set the length of the stream object.

- `int getLength()`: You can use this method to get the length of the stream object.

The `sqlj.runtime.CharacterStream` class is a subclass of the `java.io.FilterReader` class, which is a subclass of the `java.io.Reader` class. The following important methods of the `Reader` class are supported by the SQLJ `CharacterStream` class as well:

- `int read ()`: Reads the next character of data from the reader. The data is returned as an `int` value in the range 0 to 65535. If the end of the data has already been reached, then the value `-1` is returned. This method blocks program execution until one of the following:

  - Input data is available

  - The end of the data is detected

  - An exception is thrown

- `int read (char cbuf[])`: Reads characters into an array, writing the data into the specified `cbuf[]` char array. It returns an `int` value indicating how many characters were read, or `-1` if the end of the data has already been reached. This method blocks program execution until input is available.

- `int read (char cbuf[], int off, int len)`: Reads up to `len` characters of data from the input, starting at the character specified by the offset, `off`, and writing the data into the specified `char[]` char array. It returns an `int` value indicating how many characters were read, or `-1` if the end of the data has already been reached. This method blocks until input is available.

- `long skip (long n)`: Skips over and discards `n` characters of data from the input. However, in some circumstances, this method will actually skip a smaller number of characters. It returns a `long` value indicating the actual number of characters skipped.

- `void close()`: Closes the stream and releases any associated resources.

#### 6.2.7 Examples of Retrieving and Processing Stream Data

This section provides examples of various scenarios of retrieving stream data, as follows:

- Using a `SELECT` statement to select data from a `LONG` column and populate a SQLJ `CharacterStream` column in a named iterator, as shown in Example 6-1

- Using a `SELECT` statement to select data from a `LONG RAW` column and populate a SQLJ `BinaryStream` column in a positional iterator, as shown in Example 6-2

Example 6-1 Selecting LONG Data into CharacterStream Column of Named Iterator

This example selects data from a `LONG` database column, populating a SQLJ `CharacterStream` column in a named iterator.

Assume there is a table named `FILETABLE` with a `VARCHAR2` column called `FILENAME` that contains file names and a `LONG` column called `FILECONTENTS` that contains file contents in character format. The code is as follows:

    import sqlj.runtime.*;
    import java.io.*;
    ...
    #sql iterator MyNamedIter (String filename, CharacterStream filecontents);

    ...
    MyNamedIter namediter = null;
    String fname;
    CharacterStream charstream;
    #sql namediter = { SELECT filename, filecontents FROM filetable };
    while (namediter.next()) {
       fname = namediter.filename();
       charstream = namediter.filecontents();
       System.out.println("Contents for file " + fname + ":");
       printStream(charstream);
       charstream.close();
    }

    namediter.close();
    ...
    public void printStream(Reader in) throws IOException
    {
       int character;
       while ((character = in.read()) != -1) {
          System.out.print((char)character);
       }
    }

Remember that you can pass a SQLJ character stream to any method that takes a standard `java.io.Reader` as an input parameter.

Example 6-2 : Selecting LONG RAW Data into BinaryStream Column of Positional Iterator

This example selects data from a `LONG RAW` column, populating a SQLJ `BinaryStream` column in a positional iterator.

As explained in the preceding section, there can be only one stream column in a positional iterator and it must be the last column. Assume there is a table named `BINTABLE` with a `NUMBER` column called `IDENTIFIER` and a `LONG RAW` column called `BINDATA` that contains binary data associated with the identifier. The code is as follows:

    import sqlj.runtime.*;
    ...
    #sql iterator MyPosIter (int, BinaryStream);

    ...
    MyPosIter positer = null;
    int id=0;
    BinaryStream binstream=null;
    #sql positer = { SELECT identifier, bindata FROM bintable };
    while (true) {
       #sql { FETCH :positer INTO :id, :binstream };
       if (positer.endFetch()) break;

       (...process data as desired...)

       binstream.close();
    }
    positer.close();
    ...

#### 6.2.8 SQLJ Stream Objects as Output Parameters and Function Return Values

As described in the preceding sections, standard SQLJ supports the use of the `BinaryStream` and `CharacterStream` classes in the `sqlj.runtime` package for retrieval of stream data into iterator columns.

In addition, the Oracle SQLJ implementation enables the following uses of the SQLJ stream types if you use Oracle9i Database or later version, an Oracle JDBC driver, Oracle-specific code generation or Oracle customizer, and Oracle SQLJ run time:

- They can appear as `OUT` or `INOUT` host variables from a stored procedure or function call.

- They can appear as the return value from a stored function call.

##### Streams as Stored Procedure Output Parameters

You can use the `BinaryStream` and `CharacterStream` types as the assignment type for a stored procedure or stored function `OUT` or `INOUT` parameter.

Assume the following table definition:

    CREATE TABLE streamexample (name VARCHAR2 (256), data LONG);
    INSERT INTO streamexample (data, name)
       VALUES
       ('0000000000111111111112222222222333333333344444444445555555555',
       'StreamExample');

Also, presume the following stored procedure definition, which uses the `STREAMEXAMPLE` table:

    CREATE OR REPLACE PROCEDURE out_longdata
                                (dataname VARCHAR2, longdata OUT LONG) IS
    BEGIN
       SELECT data INTO longdata FROM streamexample WHERE name = dataname;
    END out_longdata;

The following sample code uses a call to the `out_longdata` stored procedure to read the long data:

    import sqlj.runtime.*;

    ...
    CharacterStream data;
    #sql { CALL out_longdata('StreamExample', :OUT data) };
    int c;
    while ((c = data.read ()) != -1)
       System.out.print((char)c);
    System.out.flush();
    data.close();
    ...

**Note:**

Closing the stream is recommended, but not required.

##### Streams as Stored Function Results

You can use the `BinaryStream` and `CharacterStream` types as the assignment type for a stored function return result.

Assume the same `STREAMEXAMPLE` table definition as in the preceding stored procedure example. Also, assume the following stored function definition, which uses the `STREAMEXAMPLE` table:

    CREATE OR REPLACE FUNCTION get_longdata (dataname VARCHAR2) RETURN long
       IS longdata LONG;
    BEGIN
       SELECT data INTO longdata FROM streamexample WHERE name = dataname;
       RETURN longdata;
    END get_longdata;

The following sample code uses a call to the `get_longdata` stored function to read the long data:

    import sqlj.runtime.*;

    ...
    CharacterStream data;
    #sql data = { VALUES(get_longdata('StreamExample')) };
    int c;
    while ((c = data.read ()) != -1)
       System.out.print((char)c);
    System.out.flush();
    data.close();
    ...

**Note:**

Closing the stream is recommended, but not required.

### 6.3 Support for JDBC 2.0 LOB Types and Oracle Type Extensions

The Oracle SQLJ implementation offers extended functionality for the following JDBC 2.0 and Oracle-specific data types:

- JDBC 2.0 large object (LOB) types (`BLOB` and `CLOB`)

- Oracle `BFILE` type

- Oracle `ROWID` type

- Oracle REF CURSOR types

- Other Oracle Database 12c Release 2 (12.2) data types, such as `NUMBER` and `RAW`

These data types are supported by classes in the `oracle.sql` package. LOBs and binary files (BFILEs) are handled similarly in many ways, so are discussed together. Additionally, the Oracle SQLJ implementation offers extended support for the standard BigDecimal JDBC type.

JDBC 2.0 functionality for user-defined SQL objects, object references, and collections are also supported.

**See Also:**

[Objects\_ Collections\_ and OPAQUE Types](objects-collections-and-OPAQUE-types.md)

Note that using Oracle extensions in your code requires the following:

- Use one of Oracle JDBC drivers.

- Use Oracle-specific code generation or for ISO code generation, customize the profiles appropriately. The default customizer, `oracle.sqlj.runtime.util.OraCustomizer`, is recommended.

- Use Oracle SQLJ run time when your application runs.

Oracle SQLJ run time and an Oracle JDBC driver are required whenever you use Oracle customizer, even if you do not actually use Oracle extensions in your code.

For Oracle-specific semantics-checking, you must use an appropriate checker. The default checker, `oracle.sqlj.checker.OracleChecker`, acts as a front end and will run the appropriate checker based on your environment. This will be one of the Oracle specific checkers if you are using an Oracle JDBC driver.

This section covers the following topics:

- Package oracle.sql

- Support for BLOB\_ CLOB\_ and BFILE

- Support for Oracle ROWID

- Support for Oracle REF CURSOR Types

- Support for Other Oracle Database 11g Data Types

- Extended Support for BigDecimal

#### 6.3.1 Package oracle.sql

SQLJ users, as well as JDBC users, should be aware of the `oracle.sql` package, which includes classes to support all the Oracle Database 12c Release 2 (12.2) data types, such as `oracle.sql.ROWID`, `oracle.sql.CLOB`, and `oracle.sql.NUMBER`. The `oracle.sql` classes are wrappers for the raw SQL data and provide appropriate mappings and conversion methods to Java formats. An `oracle.sql.*` object contains a binary representation of the corresponding SQL data in the form of a byte array. Each `oracle.sql.*` data type class is a subclass of the `oracle.sql.Datum` class.

For Oracle-specific semantics-checking, you must use an appropriate checker. The default checker, `oracle.sqlj.checker.OracleChecker`, acts as a front end and will run the appropriate checker based on your environment. This will be one of the Oracle specific checkers if you are using an Oracle JDBC driver.

**See Also:**

- "[Connection Options](translator-command-line-and-options.md)"

- "[Semantics-Checking and Offline-Parsing Options](translator-command-line-and-options.md)"

- [Oracle Database JDBC Developer's Guide](../jjdbc/Oracle-extensions.md)

#### 6.3.2 Support for BLOB, CLOB, and BFILE

The Oracle SQLJ and JDBC implementations support JDBC 2.0 LOB types and provide similar support for the Oracle specific `BFILE` type (read-only binary files stored outside the database). These data types are supported by the following classes:

- `oracle.sql.BLOB`

- `oracle.sql.CLOB`

- `oracle.sql.BFILE`

These classes can be used in Oracle-specific SQLJ applications in the following ways:

- As `IN`, `OUT`, or `INOUT` host variables in executable SQLJ statements and in `INTO`-lists

- As return values from stored function calls

- As column types in iterator declarations

**See Also:**

[Oracle Database JDBC Developer's Guide ](../jjdbc/JDBC-reference-information.md)for more information about LOBs and BFILEs and use of supported stream APIs.

You can manipulate LOBs by using methods defined in the `BLOB` and `CLOB` classes, which is recommended, or by using the procedures and functions defined in the `DBMS_LOB` PL/SQL package. All procedures and functions defined in this package can be called by SQLJ programs.

You can manipulate BFILEs by using methods defined in the `BFILE` class, which is recommended, or by using the file-handling routines of the `DBMS_LOB` package.

Using methods of the `BLOB`, `CLOB`, and `BFILE` classes in a Java application is more convenient than using the `DBMS_LOB` package and may also lead to faster execution in some cases.

Note that the type of the chunk being read or written depends on the kind of LOB being manipulated. For example, character large objects (CLOBs) contain character data and, therefore, Java strings are used to hold chunks of data. Binary large objects (BLOBs) contain binary data and, therefore, Java byte arrays are used to hold chunks of data.

**Note:**

The `DBMS_LOB` package requires a round trip to the server. Methods in the `BLOB`, `CLOB`, and `BFILE` classes may also result in a round trip to the server.

##### BFILE Class versus DBMS_LOB Functionality for BFILEs

Example 6-3 and Example 6-4 contrast use of the `oracle.sql` methods with use of the `DBMS_LOB` package for BFILEs:

##### BLOB and CLOB Classes versus DBMS_LOB Functionality for LOBs

Example 6-5 and Example 6-6 contrast use of the `oracle.sql` methods with use of the `DBMS_LOB` package for BLOBs, and Example 6-7 and Example 6-8 contrast use of the `oracle.sql` methods with use of the `DBMS_LOB` package for CLOBs.

##### LOB and BFILE Stored Function Results

Host variables of the `BLOB`, `CLOB`, and `BFILE` type can be assigned to the result of a stored function call. The following example is for a CLOB, but code for BLOBs and BFILEs would be functionally the same.

First, presume the following function definition:

    CREATE OR REPLACE FUNCTION longer_clob (c1 CLOB, c2 CLOB) RETURN CLOB IS
       result CLOB;
    BEGIN
       IF dbms_lob.getLength(c2) > dbms_lob.getLength(c1) THEN
          result := c2;
       ELSE
          result := c1;
       END IF;
       RETURN result;
    END longer_clob;

The following example uses a CLOB as the assignment type for a return value from the `longer_clob` function:

    void readFromLongest(CLOB c1, CLOB c2) throws SQLException
    {
       CLOB longest;
       #sql longest = { VALUES(longer_clob(:c1, :c2)) };
       readFromClob(longest);
    }

The `readFromLongest()` method prints the contents of the longer passed CLOB, using the `readFromClob()` method defined previously.

##### LOB and BFILE Host Variables and SELECT INTO Targets

Host variables of the `BLOB`, `CLOB`, and `BFILE` type can appear in the `INTO`-list of a `SELECT INTO` executable statement. The following example is for a BLOB and CLOB, but code for BFILEs would be functionally the same.

Assume the following table definition:

    CREATE TABLE basic_lob_table(x VARCHAR2(30), b BLOB, c CLOB);
    INSERT INTO basic_lob_table
       VALUES('one', '010101010101010101010101010101', 'onetwothreefour');
    INSERT INTO basic_lob_table
       VALUES('two', '020202020202020202020202020202', 'twothreefourfivesix');

The following example uses a BLOB and a CLOB as host variables that receive data from the table defined, using a `SELECT INTO` statement:

    ...
    BLOB blob;
    CLOB clob;
    #sql { SELECT one.b, two.c INTO :blob, :clob
         FROM basic_lob_table one, basic_lob_table two
         WHERE one.x='one' AND two.x='two' };
    #sql { INSERT INTO basic_lob_table VALUES('three', :blob, :clob) };
    ...

This example selects the BLOB from the first row and the CLOB from the second row of `BASIC_LOB_TABLE`. It then inserts a third row into the table using the BLOB and CLOB selected in the previous operation.

##### LOBs and BFILEs in Iterator Declarations

The `BLOB`, `CLOB`, and `BFILE` types can be used as column types for SQLJ positional and named iterators. Such iterators can be populated as a result of compatible executable SQLJ operations.

Following are sample declarations:

    #sql iterator NamedLOBIter(CLOB c);
    #sql iterator PositionedLOBIter(BLOB);
    #sql iterator NamedFILEIter(BFILE bf);

##### LOB and BFILE Host Variables and Named Iterator Results

The following example uses the `BASIC_LOB_TABLE` table and the `readFromLongest()` method defined in previous examples and a CLOB in a named iterator. Similar code could be written for BLOBs and BFILEs.

    #sql iterator NamedLOBIter(CLOB c);

    ...
    NamedLOBIter iter;
    #sql iter = { SELECT c FROM basic_lob_table };
    if (iter.next())
       CLOB c1 = iter.c();
    if (iter.next())
       CLOB c2 = iter.c();
    iter.close();
    readFromLongest(c1, c2);
    ...

This example uses an iterator to select two CLOBs from the first two rows of `BASIC_LOB_TABLE`, then prints the larger of the two using the `readFromLongest()` method.

##### LOB and BFILE Host Variables and Positional Iterator FETCH INTO Targets

Host variables of the `BLOB`, `CLOB`, and `BFILE` type can be used with positional iterators and appear in the `INTO`-list of the associated `FETCH INTO` statement if the corresponding column attribute in the iterator is of the identical type.

The following example uses the `BASIC_LOB_TABLE` table and the `writeToBlob()` method defined in previous examples. Similar code could be written for CLOBs and BFILEs.

    #sql iterator PositionedLOBIter(BLOB);

    ...
    PositionedLOBIter iter;
    BLOB blob = null;
    #sql iter = { SELECT b FROM basic_lob_table };
    for (long rowNum = 1; ; rowNum++)
    {
        #sql { FETCH :iter INTO :blob };
        if (iter.endFetch()) break;
        writeToBlob(blob, 512*rowNum);
    }
    iter.close();
    ...

This example calls `writeToBlob()` for each BLOB in `BASIC_LOB_TABLE`. Each row writes an additional 512 bytes of data.

Example 6-3 Use of oracle.sql.BFILE File-Handling Methods with BFILE

This example manipulates a BFILE using file-handling methods of the `oracle.sql.BFILE` class.

    BFILE openFile (BFILE file) throws SQLException
    {
      String dirAlias, name;
      dirAlias = file.getDirAlias();
      name = file.getName();
      System.out.println("name: " + dirAlias + "/" + name);

      if (!file.isFileOpen())
      {
        file.openFile();
      }
      return file;
    }

The `BFILE` `getDirAlias()` and `getName()` methods construct the full path and file name. The `openFile()` method opens the file. You cannot manipulate BFILEs until they have been opened.

Example 6-4 Use of DBMS_LOB File-Handling Routines with BFILE

This example manipulates a BFILE using file-handling routines of the `DBMS_LOB` package.

    BFILE openFile(BFILE file) throws SQLException
    {
       String dirAlias, name;
       #sql { CALL dbms_lob.filegetname(:file, :out dirAlias, :out name) };
       System.out.println("name: " + dirAlias + "/" + name);

       boolean isOpen;
       #sql isOpen = { VALUES(dbms_lob.fileisopen(:file)) };
       if (!isOpen)
       {
          #sql { CALL dbms_lob.fileopen(:inout file) };
       }
       return file;
    }

The `openFile()` method prints the name of a file object and then returns an opened version of the file. Note that BFILEs can be manipulated only after being opened with a call to `DBMS_LOB.FILEOPEN` or equivalent method in the `BFILE` class.

Example 6-5 Example: Use of oracle.sql.CLOB Read Methods with CLOB

This example reads data from a CLOB using methods of the `oracle.sql.CLOB` class.

    void readFromClob(CLOB clob) throws SQLException
    {
      long clobLen, readLen;
      String chunk;

      clobLen = clob.length();

      for (long i = 0; i < clobLen; i+= readLen) {
        chunk = clob.getSubString(i, 10);
        readLen = chunk.length();
        System.out.println("read " + readLen + " chars: " + chunk);
      }
    }

This method contains a loop that reads from the CLOB and returns a 10-character Java string each time. The loop continues until the entire CLOB has been read.

Example 6-6 Example: Use of DBMS_LOB Read Routines with CLOB

This example uses routines of the `DBMS_LOB` package to read from a CLOB.

    void readFromClob(CLOB clob) throws SQLException
    {
       long clobLen, readLen;
       String chunk;

       #sql clobLen = { VALUES(dbms_lob.getlength(:clob)) };

       for (long i = 1; i <= clobLen; i += readLen) {
           readLen = 10;
           #sql { CALL dbms_lob.read(:clob, :inout readLen, :i, :out chunk) };
           System.out.println("read " + readLen + " chars: " + chunk);
       }
    }

This method reads the contents of a CLOB in chunks of 10 characters at a time. Note that the chunk host variable is of the `String` type.

Example 6-7 Example: Use of oracle.sql.BLOB Write Routines with BLOB

This example writes data to a BLOB using methods of the `oracle.sql.BLOB` class. Input a BLOB and specified length.

    void writeToBlob(BLOB blob, long blobLen) throws SQLException
    {
      byte[] chunk = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
      long chunkLen = (long)chunk.length;

      for (long i = 0; i < blobLen; i+= chunkLen) {
        if (blobLen < chunkLen) chunkLen = blobLen;
        chunk[0] = (byte)(i+1);
        chunkLen = blob.putBytes(i, chunk);
      }
    }

This method goes through a loop that writes to the BLOB in 10-byte chunks until the specified BLOB length has been reached.

Example 6-8 Example: Use of DBMS_LOB Write Routines with BLOB

This example uses routines of the `DBMS_LOB` package to write to a BLOB.

    void writeToBlob(BLOB blob, long blobLen) throws SQLException
    {
       byte[] chunk = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
       long chunkLen = (long)chunk.length;

       for (long i = 1; i <= blobLen; i += chunkLen) {
          if ((blobLen - i + 1) < chunkLen) chunkLen = blobLen - i + 1;
          chunk[0] = (byte)i;
          #sql { CALL dbms_lob.write(:INOUT blob, :chunkLen, :i, :chunk) };
       }
    }

This method fills the contents of a BLOB in 10-byte chunks. Note that the chunk host variable is of the `byte[]` type.

#### 6.3.3 Support for Oracle ROWID

The Oracle specific `ROWID` type stores the unique address for each row in a database table. The `oracle.sql.ROWID` class wraps ROWID information and is used to bind and define variables of the `ROWID` type.

Variables of the `oracle.sql.ROWID` type can be used in SQLJ applications connecting to Oracle Database 12c Release 2 (12.2) in the following ways:

- As `IN`, `OUT` or `INOUT` host variables in SQLJ executable statements and in `INTO`-lists

- As a return value from a stored function call

- As column types in iterator declarations

##### ROWIDs in Iterator Declarations

You can use `oracle.sql.ROWID` as a column type for SQLJ positional and named iterators, as shown in the following declarations:

    #sql iterator NamedRowidIter (String ename, ROWID rowid);

    #sql iterator PositionedRowidIter (String, ROWID);

##### ROWID Host Variables and Named-Iterator SELECT Results

You can use `ROWID` objects as `IN`, `OUT` and `INOUT` parameters in SQLJ executable statements. In addition, you can populate iterators whose columns include `ROWID` types. This code example uses the preceding example declarations.

    #sql iterator NamedRowidIter (String ename, ROWID rowid);

    ...
    NamedRowidIter iter;
    ROWID rowid;
    #sql iter = { SELECT first_name, rowid FROM employees };
    while (iter.next())
    {
       if (iter.first_name().equals("Peter Hall"))
       {
           rowid = iter.rowid();
           #sql { UPDATE employees SET salary = salary + 500 WHERE rowid = :rowid };
       }
    }
    iter.close();
    ...

This example increases the salary of the employee named Peter Hall by \$500 according to the ROWID.

##### ROWID Stored Function Results

Consider the following function:

    CREATE OR REPLACE FUNCTION get_rowid (name VARCHAR2) RETURN ROWID IS
       rid ROWID;
    BEGIN
       SELECT rowid INTO rid FROM employees WHERE first_name = name;
       RETURN rid;
    END get_rowid;

Given the preceding stored function, the following example indicates how a `ROWID` object is used as the assignment type for the function return result:

    ROWID rowid;
    #sql rowid = { values(get_rowid('AMY FEINER')) };
    #sql { UPDATE employees SET salary = salary + 500 WHERE rowid = :rowid };

This example increases the salary of the employee named Amy Feiner by \$500 according to the `ROWID`.

##### ROWID SELECT INTO Targets

Host variables of the `ROWID` type can appear in the `INTO`-list of a `SELECT INTO` statement.

    ROWID rowid;
    #sql { SELECT rowid INTO :rowid FROM employees WHERE first_name='PETER HALL' };
    #sql { UPDATE employees SET salary = salary + 500 WHERE rowid = :rowid };

This example increases the salary of the employee named Peter Hall by \$500 according to the `ROWID`.

##### ROWID Host Variables and Positional Iterator FETCH INTO Targets

Host variables of the `ROWID` type can appear in the `INTO`-list of a `FETCH INTO` statement if the corresponding column attribute in the iterator is of the identical type.

    #sql iterator PositionedRowidIter (String, ROWID);

    ...
    PositionedRowidIter iter;
    ROWID rowid = null;
    String ename = null;
    #sql iter = { SELECT first_name, rowid FROM employees };
    while (true)
    {
       #sql { FETCH :iter INTO :ename, :rowid };
       if (iter.endFetch()) break;
       if (ename.equals("PETER HALL"))
       {
           #sql { UPDATE employees SET salary = salary + 500 WHERE rowid = :rowid };
       }
    }
    iter.close();
    ...

This example is similar to the previous named iterator example, but uses a positional iterator with its customary `FETCH INTO` syntax.

##### Positioned Update and Delete

Since Oracle Database 11g Release 1, SQLJ supports positioned update and delete operations. A positioned update or delete operation can be done using an iterator. The iterator used for positioned update or delete should implement the `sqlj.runtime.ForUpdate` interface. You can use a named iterator, positional iterator, or scrollable iterator.

The following code illustrates a positioned update:

    ...
    #sql iterator iter implements sqlj.runtime.ForUpdate(String str)
    ...
    #sql iter = {SELECT first_name FROM employees WHERE department_id=10};
    ...
    while(iter.next())
    {
     #sql {UPDATE employees SET salary=salary+5000 WHERE CURRENT OF :iter};
    }
    ...

In the preceding code, an iterator `iter` is created and used to update the `employees` table.

**Note:**

If you want to avoid synchronization problems, then issue a `SELECT ... FOR UPDATE` statement.

You can similarly perform a positioned delete. For example:

    ...
    #sql {DELETE FROM employees WHERE CURRENT OF :iter}
    ...

In the preceding example, `iter` is an iterator used to perform positioned delete.

The iterators that can be used with the `WHERE CURRENT OF` clause have the following limitations:

- The query used to populate the iterator should not operate on multiple tables.

- You cannot use a PL/SQL procedure returning a `REF CURSOR` with the iterator.

- You cannot use an iterator that has been populated from a result set. That is, an iterator populated using the following statement, where `rs` is a result set:

      #sql iter = {cast :rs}

##### for_update Option

If `for_update` option is set at translation time, then `"FOR UPDATE`" is appended to the SELECT statements, which in turn return results into a `ForUpdate` iterator as follows:

    % sqlj –for_update abc.sqlj

    /* abc.sqlj */
    #sql iterator  SalByName (double sal, String ename)  implements sqlj.runtime.ForUpdate;

    public class abc {
    …..
      void func1()
      {
        SalByName salbn;
        #sql salbn = {select salary, first_name from employees };
      }
    …..
    }

Now, "`FOR UPDATE`" is appended to the SELECT statement returning the `ForUpdate` iterator `salbn` in the following way:

    ………
    String theSqlTS = “SELECT rowid sjT_rowid,first_name, salary FROM employees WHERE first_name =  :1 FOR UPDATE";
    ………

Table 6-3 shows the plausible values for the `for_update` option and the corresponding SQL statement for the preceding example:

Table 6-3 Plausible values for the for_update option and the corresponding SQL statement

| for_update option | SQLJ Statement                             | SQL Statement                                                                                       |
|:------------------|:-------------------------------------------|:----------------------------------------------------------------------------------------------------|
| none              | `sqlj -for_update abc.sqlj`                | `SELECT rowid sjT_rowid,first_name, salary FROM employees WHERE first_name = :1 FOR UPDATE`         |
| `nowait`          | `sqlj -P-for_update=nowait QueryDemo.sqlj` | `SELECT rowid sjT_rowid,first_name, salary FROM employees WHERE first_name = :1 FOR UPDATE nowait`  |
| `number`          | `sqlj -P-for_update=10 QueryDemo.sqlj`     | `SELECT rowid sjT_rowid,first_name, salary FROM employees WHERE first_name = :1 FOR UPDATE wait 10` |

**Note:**

If the application already has `FOR UPDATE` in the select query, then using these new translator options will throw warnings during online check at translation time. If offline parsing is chosen during translation, then errors are not detected at translation time.

#### 6.3.4 Support for Oracle REF CURSOR Types

Oracle PL/SQL and the Oracle SQLJ implementation support the use of cursor variables that represent database cursors.

##### Overview of REF CURSOR Types

Cursor variables are functionally equivalent to JDBC result sets, essentially encapsulating the results of a query. A cursor variable is often referred to as a REF CURSOR, but `REF CURSOR` itself is a type specifier, and not a type name. Instead, named REF CURSOR types must be specified. The following example shows a REF CURSOR type specification:

    TYPE EmpCurType IS REF CURSOR;

Stored procedures and stored functions can return parameters of Oracle REF CURSOR types. You must use PL/SQL to return a REF CURSOR parameter. You cannot accomplish this using SQL alone. A PL/SQL stored procedure or function can declare a variable of some named REF CURSOR type, execute a `SELECT` statement, and return the results in the REF CURSOR variable.

**See Also:**

[Oracle Database PL/SQL Language Reference](../lnpls/dbms_sql-package.md)

##### REF CURSOR Types in SQLJ

In the Oracle SQLJ implementation, a REF CURSOR type can be mapped to iterator columns or host variables of any iterator class type or of the `java.sql.ResultSet` type, but host variables can be `OUT` only. Support for REF CURSOR types can be summarized as follows:

- As result expressions for stored function returns

- As output host expressions for stored procedure or function output parameters

- As output host expressions in `INTO`-lists

- As iterator columns

You can use the SQL `CURSOR` operator for a nested `SELECT` within an outer `SELECT` statement. This is how you can write a REF CURSOR object to an iterator column or `ResultSet` column in an iterator, or write a REF CURSOR object to an iterator host variable or `ResultSet` host variable in an `INTO`-list.

**See Also:**

"[Using Iterators and Result Sets as Host Variables](basic-language-features.md)" for examples illustrating the use of implicit REF CURSOR variables, including an example of the `CURSOR` operator.

**Note:**

- Use the type code `OracleTypes.CURSOR` for REF CURSOR types.

- There is no `oracle.sql` class for REF CURSOR types. Use either `java.sql.ResultSet` or an iterator class. Close the result set or iterator to release resources when you are done processing it.

##### REF CURSOR Example

The following sample method shows a REF CURSOR type being retrieved from an anonymous block:

    private static EmpIter refCursInAnonBlock(String name, int no)
      throws java.sql.SQLException {
      EmpIter emps = null;

      System.out.println("Using anonymous block for ref cursor..");
      #sql { begin
               INSERT INTO employees (first_name, employee_id) VALUES (:name, :no);
               OPEN :out emps FOR SELECT first_name, employee_id FROM employees ORDER BY employee_id;
             end
           };
      return emps;
    }

#### 6.3.5 Support for Other Oracle Database 11g Data Types

All `oracle.sql` classes can be used for iterator columns or for input, output, or input-output host variables in the same way that any standard Java type can be used. This includes the classes mentioned in the preceding sections and others, such as the `oracle.sql.NUMBER`, `oracle.sql.CHAR`, and `oracle.sql.RAW` classes.

Because the `oracle.sql.*` classes do not require conversion to Java type format, they offer greater efficiency and precision than equivalent Java types. You would have to convert the data to standard Java types, however, to use it with standard Java programs or to display it to end users.

#### 6.3.6 Extended Support for BigDecimal

SQLJ supports `java.math.BigDecimal` in the following situations:

- As host variables in SQLJ executable statements

- As return values from stored function calls

- As iterator column types

Standard SQLJ has the limitation that a value can be retrieved as `BigDecimal` only if that is the JDBC default mapping, which is the case only for numeric and decimal data.

**See Also:**

Table 6-1

In the Oracle SQLJ implementation, however, you can map to nondefault types as long as the data type is convertible from numeric and you use Oracle9i Database or later version, an Oracle JDBC driver, Oracle-specific code generation or Oracle customizer, and Oracle SQLJ run time. The `CHAR`, `VARCHAR2`, `LONG`, and `NUMBER` types are convertible. For example, you can retrieve data from a `CHAR` column into a `BigDecimal` variable. However, to avoid errors, you must be careful that the character data consists only of numbers.

**Note:**

The `BigDecimal` class is in the standard `java.math` package.
