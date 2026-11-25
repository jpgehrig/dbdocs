## 9  Data Interface for Persistent LOBs

Data interface is a generic term referring to whichever interface is in use, to query the database or to update the database.

Topics:

- Overview of the Data Interface for Persistent LOBs

- Benefits of Using the Data Interface for Persistent LOBs

- Using the Data Interface for Persistent LOBs in PL/SQL

- The Data Interface Used for Persistent LOBs in OCI

- The Data Interface Used with Persistent LOBs in Java

- The Data Interface Used with Remote LOBs

<!-- -->

- Overview of the Data Interface for Persistent LOBs
- Benefits of Using the Data Interface for Persistent LOBs
- Using the Data Interface for Persistent LOBs in PL/SQL
- The Data Interface Used for Persistent LOBs in OCI
- The Data Interface Used with Persistent LOBs in Java
- The Data Interface Used with Remote LOBs

**Parent topic:** [Value Semantics LOBs](value-semantic-LOBs.md)

### 9.1 Overview of the Data Interface for Persistent LOBs

The data interface for persistent LOBs includes a set of Java, PL/SQL, and OCI APIs that are extended to work with LOB data types.

These APIs, originally designed for use with legacy data types such as `LONG`, `LONG` `RAW`, and `VARCHAR2`, can also be used with the corresponding LOB data types shown in Table 9-1 and Table 9-2. These tables show the legacy data types in the bind or define type column and the corresponding supported LOB data type in the LOB column type column. You can use the data interface for LOBs to store and manipulate character data and binary data in a LOB column just as if it were stored in the corresponding legacy data type.

**Note:**

The data interface works for LOB columns and LOBs that are attributes of objects. In this chapter LOB columns means LOB columns and LOB attributes.

You can use array bind and define interfaces to insert and select multiple rows in one round-trip.

While most of this discussion focuses on character data types, the same concepts apply to the full set of character and binary data types listed in Table 9-1 and Table 9-2. `CLOB` also means `NCLOB` in these tables.

Table 9-1 Corresponding LONG and LOB Data Types in SQL and PL/SQL

| Bind or Define Type | LOB Column Type | Used For Storing |
|:--------------------|:----------------|:-----------------|
| `CHAR`              | `CLOB`          | Character data   |
| `LONG`              | `CLOB`          | Character data   |
| `VARCHAR2`          | `CLOB`          | Character data   |
| `LONG RAW `         | `BLOB`          | Binary data      |
| `RAW`               | `BLOB`          | Binary data      |

Table 9-2 Corresponding LONG and LOB Data Types in OCI

| Bind or Define Type | LOB Column Type | Used For Storing |
|:--------------------|:----------------|:-----------------|
| `SQLT_AFC(n)`       | `CLOB`          | Character data   |
| `SQLT_CHR`          | `CLOB`          | Character data   |
| `SQLT_LNG`          | `CLOB`          | Character data   |
| `SQLT_VCS`          | `CLOB`          | Character data   |
| `SQLT_BIN`          | `BLOB`          | Binary data      |
| `SQLT_LBI`          | `BLOB`          | Binary data      |
| `SQLT_LVB`          | `BLOB`          | Binary data      |

**Parent topic:** Data Interface for Persistent LOBs

### 9.2 Benefits of Using the Data Interface for Persistent LOBs

Using the data interface for persistent LOBs has the following benefits:

- If your application uses `LONG` data types, then you can use the same application with LOB data types with little or no modification of your existing application required. To do so, just convert `LONG` audiotape columns in your tables to LOB audiotape columns as discussed in [Migrating Columns from LONGs to LOBs](migrating-columns-from-LONGs-to-LOBs.md).

- Performance is better for OCI applications that use sequential access techniques. A piecewise `INSERT` or fetch using the data interface has comparable performance to using OCI functions like `OCILobRead2()` and `OCILobWrite2()`. Because the data interface allows more than 4K bytes of data to be inserted into a LOB in a single OCI call, a round-trip to the server is saved.

- You can read LOB data in one `OCIStmtFetch()` call, instead of fetching the LOB locator first and then calling `OCILobRead2()`. This improves performance when you want to read LOB data starting at the beginning.

- You can use array bind and define interfaces to insert and select multiple rows with LOBs in one round trip.

**Parent topic:** Data Interface for Persistent LOBs

### 9.3 Using the Data Interface for Persistent LOBs in PL/SQL

The data interface enables you to use `LONG` and LOB data types listed in Table 9-1 to perform the following operations in PL/SQL:

- About Using the Data Interface for Persistent LOBs in PL/SQL
- Guidelines for Accessing LOB Columns Using the Data Interface in SQL and PL/SQL
- Implicit Assignment and Parameter Passing
- Passing CLOBs to SQL and PL/SQL Built-In Functions
- Explicit Conversion Functions
- Calling PL/SQL and C Procedures from SQL
- Calling PL/SQL and C Procedures from PL/SQL
- Binds of All Sizes in INSERT and UPDATE Operations
- 4000 Byte Limit on Results of a SQL Operator
- Example of 4000 Byte Result Limit of a SQL Operator
- Restrictions on Binds of More Than 4000 Bytes
- Performing Parallel DDL, Parallel DML (PDML), and Parallel Query (PQ) Operations on LOBs
  Oracle supports parallel execution of the following operations when performed on partitioned tables with SecureFiles LOBs or BasicFiles LOBs.
- Example: PL/SQL - Using Binds of More Than 4000 Bytes in INSERT and UPDATE
- Using the Data Interface for LOBs with INSERT, UPDATE, and SELECT Operations
- Using the Data Interface for LOBs in Assignments and Parameter Passing
- Using the Data Interface for LOBs with PL/SQL Built-In Functions

**Parent topic:** Data Interface for Persistent LOBs

#### 9.3.1 About Using the Data Interface for Persistent LOBs in PL/SQL

- `INSERT` or `UPDATE` character data stored in datatypes such as `VARCHAR2`, `CHAR`, or `LONG` into a `CLOB` column.

- `INSERT` or `UPDATE` binary data stored in datatypes such as `RAW` or `LONG` `RAW` into a `BLOB` column.

- Use the `SELECT` statement on `CLOB` columns to select data into a character buffer variable such as `CHAR`, `LONG`, or `VARCHAR2`.

- Use the `SELECT` statement on `BLOB` columns to select data into a binary buffer variable such as `RAW` and `LONG` `RAW`.

- Make cross-type assignments (implicit type conversions) between `CLOB` and `VARCHAR2`, `CHAR`, or `LONG` variables.

- Make cross-type assignments (implicit type conversions) between `BLOB` and `RAW` or `LONG` `RAW` variables.

- Pass LOB datatypes to functions defined to accept `LONG` datatypes or pass `LONG` datatypes to functions defined to accept LOB datatypes. For example, you can pass a `CLOB` instance to a function defined to accept another character type, such as `VARCHAR2`, `CHAR`, or `LONG`.

- Use `CLOB`s with other PL/SQL functions and operators that accept `VARCHAR2` arguments such as `INSTR` and `SUBSTR`.

  **Note:**

  When using the data interface for LOBs with the `SELECT` statement in PL/SQL, you cannot specify the amount you want to read. You can only specify the buffer length of your buffer. If your buffer length is smaller than the LOB data length, then the database throws an exception.

  **See Also:**

  - [SQL Semantics and LOBs](SQL-semantics-and-LOBs.md) for details on LOB support in SQL statements

  - [Some Implicit Conversions Are Not Supported for LOB Data Types](migrating-columns-from-LONGs-to-LOBs.md)

  - Passing CLOBs to SQL and PL/SQL Built-In Functions for the complete list of functions that accept `VARCHAR2` arguments such as `INSTR` and `SUBSTR`

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.2 Guidelines for Accessing LOB Columns Using the Data Interface in SQL and PL/SQL

This section describes techniques you use to access LOB columns or attributes using the data interface for persistent LOBs.

Data from `CLOB` and `BLOB` columns or attributes can be referenced by regular SQL statements, such as `INSERT`, `UPDATE`, and `SELECT`.

There is no piecewise `INSERT`, `UPDATE`, or fetch routine in PL/SQL. Therefore, the amount of data that can be accessed from a LOB column or attribute is limited by the maximum character buffer size. PL/SQL supports character buffer sizes up to 32KB - 1 (32767 bytes). For this reason, only LOBs less than 32K bytes in size can be accessed by PL/SQL applications using the data interface for persistent LOBs.

If you must access more than 32KB -1 using the data interface, then you must make OCI calls from the PL/SQL code to use the APIs for piece-wise insert and fetch.

Use the following guidelines for using the data interface to access LOB columns or attributes:

- `INSERT` operations

  You can `INSERT` into tables containing LOB columns or attributes using regular `INSERT` statements in the `VALUES` clause. The field of the LOB column can be a literal, a character datatype, a binary datatype, or a LOB locator.

- `UPDATE` operations

  LOB columns or attributes can be updated as a whole by `UPDATE`... `SET` statements. In the `SET` clause, the new value can be a literal, a character datatype, a binary datatype, or a LOB locator.

- 4000 byte limit on hexadecimal to raw and raw to hexadecimal conversions

  The database does not do implicit hexadecimal to `RAW` or `RAW` to hexadecimal conversions on data that is more than 4000 bytes in size. You cannot bind a buffer of character data to a binary datatype column, and you cannot bind a buffer of binary data to a character datatype column if the buffer is over 4000 bytes in size. Attempting to do so results in your column data being truncated at 4000 bytes.

  For example, you cannot bind a `VARCHAR2` buffer to a `LONG` `RAW` or a `BLOB` column if the buffer is more than 4000 bytes in size. Similarly, you cannot bind a `RAW` buffer to a `LONG` or a `CLOB` column if the buffer is more than 4000 bytes in size.

- `SELECT` operations

  LOB columns or attributes can be selected into character or binary buffers in PL/SQL. If the LOB column or attribute is longer than the buffer size, then an exception is raised without filling the buffer with any data. LOB columns or attributes can also be selected into LOB locators.

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.3 Implicit Assignment and Parameter Passing

Implicit assignment and parameter passing are supported for LOB columns.

For the data types listed in Table 9-1 and Table 9-2, you can pass or assign: any character type to any other character type, or any binary type to any other binary type using the data interface for persistent LOBs.

Implicit assignment works for variables declared explicitly and for variables declared by referencing an existing column type using the `%TYPE` attribute as show in the following example. This example assumes that column `long_col` in table `t` has been migrated from a `LONG` to a `CLOB` column.

    CREATE TABLE t (long_col LONG); -- Alter this table to change LONG column to LOB
    DECLARE
       a VARCHAR2(100);
       b t.long_col%type; -- This variable changes from LONG to CLOB
    BEGIN
       SELECT * INTO b FROM t;
       a := b;  -- This changes from "VARCHAR2 := LONG to VARCHAR2 := CLOB
       b := a;  -- This changes from "LONG := VARCHAR2 to CLOB := VARCHAR2
    END;

Implicit parameter passing is allowed between functions and procedures. For example, you can pass a `CLOB` to a function or procedure where the formal parameter is defined as a `VARCHAR2`.

**Note:**

The assigning a `VARCHAR2` buffer to a LOB variable is somewhat less efficient than assigning a `VARCHAR2` to a `LONG` variable because the former involves creating a temporary LOB. Therefore, PL/SQL users experience a slight deterioration in the performance of their applications.

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.4 Passing CLOBs to SQL and PL/SQL Built-In Functions

Implicit parameter passing is also supported for built-in PL/SQL functions that accept character data. For example, `INSTR` can accept a `CLOB` and other character data.

Any SQL or PL/SQL built-in function that accepts a `VARCHAR2` can accept a `CLOB` as an argument. Similarly, a `VARCHAR2` variable can be passed to any `DBMS_LOB` API for any parameter that takes a LOB locator.

**See Also:**

[SQL Semantics and LOBs](SQL-semantics-and-LOBs.md)

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.5 Explicit Conversion Functions

In PL/SQL, these explicit conversion functions convert other data types to `CLOB` and `BLOB` datatypes as follows:

- `TO_CLOB()` converts `LONG`, `VARCHAR2`, and `CHAR` to `CLOB`

- `TO_BLOB()` converts `LONG RAW` and `RAW` to `BLOB`

Also note that the conversion function `TO_CHAR()` can convert a `CLOB` to a `CHAR` type.

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.6 Calling PL/SQL and C Procedures from SQL

When a PL/SQL or C procedure is called from SQL, buffers with more than 4000 bytes of data are not allowed.

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.7 Calling PL/SQL and C Procedures from PL/SQL

You can call a PL/SQL or C procedure from PL/SQL. You can pass a `CLOB` as an actual parameter where `CHR` is the formal parameter, or vice versa. The same holds for `BLOB`s and `RAW`s.

One example of when these cases can arise is when either the formal or the actual parameter is an anchored type, that is, the variable is declared using the `table_name.column_name``%type` syntax.

PL/SQL procedures or functions can accept a `CLOB` or a `VARCHAR2` as a formal parameter. For example the PL/SQL procedure could be one of the following:

- When the formal parameter is a `CLOB`:

      CREATE OR REPLACE PROCEDURE get_lob(table_name IN VARCHAR2, lob INOUT
      CLOB) AS
         ...
      BEGIN
        ...
      END;
      /

- When the formal parameter is a `VARCHAR2`:

      CREATE OR REPLACE PROCEDURE get_lob(table_name IN VARCHAR2, lob INOUT
      VARCHAR2) AS
         ...
      BEGIN
        ...
      END;
      /

The calling function could be of any of the following types:

- When the actual parameter is a CHR:

      create procedure ...
      declare
      c VARCHAR2[200];
      BEGIN
        get_lob('table_name', c);
      END;


- When the actual parameter is a `CLOB`:

      create procedure ...
      declare
      c CLOB;
      BEGIN
        get_lob('table_name', c);
      END;

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.8 Binds of All Sizes in INSERT and UPDATE Operations

Binds of all sizes are supported for `INSERT` and `UPDATE` operations on LOB columns. Multiple binds of any size are allowed in a single `INSERT` or `UPDATE` statement.

**Note:**

When you create a table, the length of the default value you specify for any LOB column is restricted to 4000 bytes.

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.9 4000 Byte Limit on Results of a SQL Operator

If you bind more than 4000 bytes of data to a `BLOB` or a `CLOB`, and the data consists of a SQL operator, then Oracle Database limits the size of the result to at most 4000 bytes.

The following statement inserts only 4000 bytes because the result of `LPAD` is limited to 4000 bytes:

    INSERT INTO print_media (ad_sourcetext) VALUES (lpad('a', 5000, 'a'));

The following statement inserts only 2000 bytes because the result of `LPAD` is limited to 4000 bytes, and the implicit hexadecimal to raw conversion converts it to 2000 bytes of `RAW` data:

    INSERT INTO print_media (ad_photo) VALUES (lpad('a', 5000, 'a'));

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.10 Example of 4000 Byte Result Limit of a SQL Operator

This example illustrates how the result for SQL operators is limited to 4000 bytes.

    /* The following command inserts only 4000 bytes because the result of
     * LPAD is limited to 4000 bytes */
    INSERT INTO print_media(product_id, ad_id, ad_sourcetext)
      VALUES (2004, 5, lpad('a', 5000, 'a'));
    SELECT LENGTH(ad_sourcetext) FROM print_media
      WHERE product_id=2004 AND ad_id=5;
    ROLLBACK;

    /* The following command inserts only 2000 bytes because the result of
     * LPAD is limited to 4000 bytes, and the implicit hex to raw conversion
     * converts it to 2000 bytes of RAW data. */
    INSERT INTO print_media(product_id, ad_id, ad_composite)
      VALUES (2004, 5, lpad('a', 5000, 'a'));
    SELECT LENGTH(ad_composite) from print_media
      WHERE product_id=2004 AND ad_id=5;
    ROLLBAACK;

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.11 Restrictions on Binds of More Than 4000 Bytes

There are restrictions for binds of more than 4000 bytes:

- If a table has both `LONG` and LOB columns, then you can bind more than 4000 bytes of data to either the `LONG` or LOB columns, but not both in the same statement.

- In an `INSERT` `AS` `SELECT` operation, binding of any length data to LOB columns is not allowed.

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.12 Performing Parallel DDL, Parallel DML (PDML), and Parallel Query (PQ) Operations on LOBs

Oracle supports parallel execution of the following operations when performed on partitioned tables with SecureFiles LOBs or BasicFiles LOBs.

- `CREATE TABLE AS SELECT`
- `INSERT AS SELECT`
- Multitable `INSERT`
- `SELECT`
- `DELETE`
- `UPDATE`
- `MERGE` (conditional `UPDATE` and `INSERT`)
- `ALTER TABLE MOVE`
- SQL Loader
- Import/Export

Additionally, Oracle supports parallel execution of the following operations when performed on non-partitioned tables with only SecureFile LOBs:

- `CREATE TABLE AS SELECT`
- `INSERT AS SELECT`
- Multitable `INSERT`
- `SELECT`
- `DELETE`
- `UPDATE`
- `MERGE` (conditional `UPDATE` and `INSERT`)
- `ALTER TABLE MOVE`
- SQL Loader

Restrictions on parallel operations with LOBs

- Parallel insert direct load (PIDL) is disabled if a table also has a BasicFiles LOB column, in addition to a SecureFiles LOB column.
- PDML is disabled if LOB column is part of a constraint.
- PDML does not work when there are any domain indexes defined on the LOB column.
- Parallelism must be specified only for top-level non-partitioned tables.
- Use the `ALTER TABLE MOVE` statement with LOB storage clause, to change the storage properties of LOB columns instead of the `ALTER TABLE MODIFY` statement. The `ALTER TABLE MOVE` statement is more efficient because it executes in parallel and does not generate undo logs.

**See Also:**

[Oracle Database Administrator's Guide](../admin/managing-processes.md) section "Managing Processes for Parallel SQL Execution"

[Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) section "ALTER TABLE"

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.13 Example: PL/SQL - Using Binds of More Than 4000 Bytes in INSERT and UPDATE

This example demonstrates using binds larger than 4000 bytes in `INSERT` and `UPDATE` operations.

    DECLARE
      bigtext VARCHAR2(32767);
      smalltext VARCHAR2(2000);
      bigraw RAW (32767);
    BEGIN
      bigtext := LPAD('a', 32767, 'a');
      smalltext := LPAD('a', 2000, 'a');
      bigraw := utl_raw.cast_to_raw (bigtext);

      /* Multiple long binds for LOB columns are allowed for INSERT: */
      INSERT INTO print_media(product_id, ad_id, ad_sourcetext, ad_composite)
        VALUES (2004, 1, bigtext, bigraw);

      /* Single long bind for LOB columns is allowed for INSERT: */
      INSERT INTO print_media (product_id, ad_id, ad_sourcetext)
        VALUES (2005, 2, smalltext);

      bigtext := LPAD('b', 32767, 'b');
      smalltext := LPAD('b', 20, 'a');
      bigraw := utl_raw.cast_to_raw (bigtext);

      /* Multiple long binds for LOB columns are allowed for UPDATE: */
      UPDATE print_media SET ad_sourcetext = bigtext, ad_composite = bigraw,
        ad_finaltext = smalltext;

      /* Single long bind for LOB columns is allowed for UPDATE: */
      UPDATE print_media SET ad_sourcetext = smalltext, ad_finaltext = bigtext;

      /* The following is NOT allowed because we are trying to insert more than
         4000 bytes of data in a LONG and a LOB column: */
      INSERT INTO print_media(product_id, ad_id, ad_sourcetext, press_release)
        VALUES (2030, 3, bigtext, bigtext);

      /* Insert of data into LOB attribute is allowed */
      INSERT INTO print_media(product_id, ad_id, ad_header)
         VALUES (2049, 4, adheader_typ(null, null, null, bigraw));

      /* The following is not allowed because we try to perform INSERT AS
         SELECT data INTO LOB */
      INSERT INTO print_media(product_id, ad_id, ad_sourcetext)
        SELECT 2056, 5, bigtext FROM dual;

    END;
    /

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.14 Using the Data Interface for LOBs with INSERT, UPDATE, and SELECT Operations

`INSERT` and `UPDATE` statements on LOBs are used in the same way as on `LONG`s. For example:

    DECLARE
      ad_buffer VARCHAR2(100);
    BEGIN
      INSERT INTO print_media(product_id, ad_id, ad_sourcetext)
        VALUES(2004, 5, 'Source for advertisement 1');
      UPDATE print_media SET ad_sourcetext= 'Source for advertisement 2'
        WHERE product_id=2004 AND ad_id=5;
      /* This retrieves the LOB column if it is up to 100 bytes, otherwise it
       * raises an exception */
      SELECT ad_sourcetext INTO ad_buffer FROM print_media
        WHERE product_id=2004 AND ad_id=5;
    END;
    /

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.15 Using the Data Interface for LOBs in Assignments and Parameter Passing

The data interface for LOBs enables implicit assignment and parameter passing as shown in the following example:

    CREATE TABLE t (clob_col CLOB, blob_col BLOB);
    INSERT INTO t VALUES('abcdefg', 'aaaaaa');

    DECLARE
      var_buf VARCHAR2(100);
      clob_buf CLOB;
      raw_buf RAW(100);
      blob_buf BLOB;
    BEGIN
      SELECT * INTO clob_buf, blob_buf FROM t;
      var_buf := clob_buf;
      clob_buf:= var_buf;
      raw_buf := blob_buf;
      blob_buf := raw_buf;
    END;
    /

    CREATE OR REPLACE PROCEDURE FOO ( a IN OUT CLOB) IS
    BEGIN
      -- Any procedure body
      a := 'abc';
    END;
    /

    CREATE OR REPLACE PROCEDURE BAR (b IN OUT VARCHAR2) IS
    BEGIN
      -- Any procedure body
      b := 'xyz';
    END;
    /

    DECLARE
      a VARCHAR2(100) := '1234567';
      b CLOB;
    BEGIN
      FOO(a);
      SELECT clob_col INTO b FROM t;
      BAR(b);
    END;
    /

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

#### 9.3.16 Using the Data Interface for LOBs with PL/SQL Built-In Functions

This example illustrates the use of `CLOB`s in PL/SQL built-in functions, using the data interface for LOBs:

    DECLARE
      my_ad CLOB;
      revised_ad CLOB;
      myGist VARCHAR2(100):= 'This is my gist.';
      revisedGist VARCHAR2(100);
    BEGIN
      INSERT INTO print_media (product_id, ad_id, ad_sourcetext)
        VALUES (2004, 5, 'Source for advertisement 1');

      -- select a CLOB column into a CLOB variable
      SELECT ad_sourcetext INTO my_ad FROM print_media
        WHERE product_id=2004 AND ad_id=5;

      -- perform VARCHAR2 operations on a CLOB variable
      revised_ad := UPPER(SUBSTR(my_ad, 1, 20));

      -- revised_ad is a temporary LOB
      -- Concat a VARCHAR2 at the end of a CLOB
      revised_ad := revised_ad || myGist;

      -- The following statement raises an error if my_ad is
      -- longer than 100 bytes
      myGist := my_ad;
    END;
    /

**Parent topic:** Using the Data Interface for Persistent LOBs in PL/SQL

### 9.4 The Data Interface Used for Persistent LOBs in OCI

This section discusses OCI functions included in the data interface for persistent LOBs. These OCI functions work for LOB datatypes exactly the same way as they do for `LONG` datatypes. Using these functions, you can perform `INSERT`, `UPDATE`, fetch, bind, and define operations in OCI on LOBs using the same techniques you would use on other datatypes that store character or binary data.

**Note:**

You can use array bind and define interfaces to insert and select multiple rows with LOBs in one round trip.

- LOB Data Types Bound in OCI
- LOB Data Types Defined in OCI
- Multibyte Character Sets Used in OCI with the Data Interface for LOBs
- OCI Functions Used to Perform INSERT or UPDATE on LOB Columns
- The Data Interface Used to Fetch LOB Data in OCI
- PL/SQL and C Binds from OCI
- Example: C (OCI) - Binds of More than 4000 Bytes for INSERT and UPDATE
- Using the Data Interface for LOBs in PL/SQL Binds from OCI on LOBs
- Binding LONG Data for LOB Columns in Binds Greater Than 4000 Bytes
- Binding LONG Data to LOB Columns Using Piecewise INSERT with Polling
- Binding LONG Data to LOB Columns Using Piecewise INSERT with Callback
- Binding LONG Data to LOB Columns Using an Array INSERT
- Selecting a LOB Column into a LONG Buffer Using a Simple Fetch
- Selecting a LOB Column into a LONG Buffer Using Piecewise Fetch with Polling
- Selecting a LOB Column into a LONG Buffer Using Piecewise Fetch with Callback
- Selecting a LOB Column into a LONG Buffer Using an Array Fetch

**See Also:**

[ Oracle Call Interface Programmer's Guide](../lnoci/binding-and-defining-in-oci.md), section "Runtime Data Allocation and Piecewise Operations in OCI"

**Parent topic:** Data Interface for Persistent LOBs

#### 9.4.1 LOB Data Types Bound in OCI

You can bind LOB datatypes in the following operations:

- Regular, piecewise, and callback binds for `INSERT` and `UPDATE` operations

- Array binds for `INSERT` and `UPDATE` operations

- Parameter passing across PL/SQL and OCI boundaries

Piecewise operations can be performed by polling or by providing a callback. To support these operations, the following OCI functions accept the `LONG` and LOB data types listed in Table 9-2.

- `OCIBindByName()` and `OCIBindByPos()`

  These functions create an association between a program variable and a placeholder in the SQL statement or a PL/SQL block for `INSERT` and `UPDATE` operations.

- `OCIBindDynamic()`

  You use this call to register callbacks for dynamic data allocation for `INSERT` and `UPDATE` operations

- `OCIStmtGetPieceInfo()` and `OCIStmtSetPieceInfo()`

  These calls are used to get or set piece information for piecewise operations.

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.2 LOB Data Types Defined in OCI

The data interface for persistent LOBs allows the following OCI functions to accept the LONG and LOB data types listed in Table 9-2.

- `OCIDefineByPos()`

  This call associates an item in a `SELECT` list with the type and output data buffer.

- `OCIDefineDynamic()`

  This call registers user callbacks for `SELECT` operations if the `OCI_DYNAMIC_FETCH` mode was selected in `OCIDefineByPos()` function call.

When you use these functions with LOB types, the LOB data, and not the locator, is selected into your buffer. Note that in OCI, you cannot specify the amount you want to read using the data interface for LOBs. You can only specify the buffer length of your buffer. The database only reads whatever amount fits into your buffer and the data is truncated.

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.3 Multibyte Character Sets Used in OCI with the Data Interface for LOBs

When the client character set is in a multibyte format, functions included in the data interface operate the same way with LOB datatypes as they do for LONG datatypes as follows:

- For a piecewise fetch in a multibyte character set, a multibyte character could be cut in the middle, with some bytes at the end of one buffer and remaining bytes in the next buffer.

- For a regular fetch, if the buffer cannot hold all bytes of the last character, then Oracle returns as many bytes as fit into the buffer, hence returning partial characters.

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.4 OCI Functions Used to Perform INSERT or UPDATE on LOB Columns

This section discusses the various techniques you can use to perform `INSERT` or `UPDATE` operations on LOB columns or attributes using the data interface. The operations described in this section assume that you have initialized the OCI environment and allocated all necessary handles.

- Performing Simple INSERTs or UPDATEs in One Piece
- Using Piecewise INSERTs and UPDATEs with Polling
- Performing Piecewise INSERTs and UPDATEs with Callback
- Array INSERT and UPDATE Operations

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

##### 9.4.4.1 Performing Simple INSERTs or UPDATEs in One Piece

To perform simple `INSERT` or `UPDATE` operations in one piece using the data interface for persistent LOBs, perform the following steps:

1.  Call `OCIStmtPrepare()` to prepare the statement in `OCI_DEFAULT` mode.
2.  Call `OCIBindByName()` or `OCIBindbyPos()` in `OCI_DEFAULT` mode to bind a placeholder for LOB as character data or binary data.
3.  Call `OCIStmtExecute()` to do the actual `INSERT` or `UPDATE` operation.

**Parent topic:** OCI Functions Used to Perform INSERT or UPDATE on LOB Columns

##### 9.4.4.2 Using Piecewise INSERTs and UPDATEs with Polling

To perform piecewise `INSERT` or `UPDATE` operations with polling using the data interface for persistent LOBs, do the following steps:

1.  Call `OCIStmtPrepare()` to prepare the statement in `OCI_DEFAULT` mode.
2.  Call `OCIBindByName()` or `OCIBindbyPos()` in `OCI_DATA_AT_EXEC` mode to bind a LOB as character data or binary data.
3.  Call `OCIStmtExecute()` in default mode. Do each of the following in a loop while the value returned from `OCIStmtExecute()` is `OCI_NEED_DATA`. Terminate your loop when the value returned from `OCIStmtExecute()` is `OCI_SUCCESS`.
    - Call `OCIStmtGetPieceInfo()` to retrieve information about the piece to be inserted.

    - Call `OCIStmtSetPieceInfo()` to set information about piece to be inserted.

**Parent topic:** OCI Functions Used to Perform INSERT or UPDATE on LOB Columns

##### 9.4.4.3 Performing Piecewise INSERTs and UPDATEs with Callback

To perform piecewise `INSERT` or `UPDATE` operations with callback using the data interface for persistent LOBs, do the following steps:

1.  Call `OCIStmtPrepare()` to prepare the statement in `OCI_DEFAULT` mode.
2.  Call `OCIBindByName()` or `OCIBindbyPos()` in `OCI_DATA_AT_EXEC` mode to bind a placeholder for the LOB column as character data or binary data.
3.  Call `OCIBindDynamic()` to specify the callback.
4.  Call `OCIStmtExecute()` in default mode.

**Parent topic:** OCI Functions Used to Perform INSERT or UPDATE on LOB Columns

##### 9.4.4.4 Array INSERT and UPDATE Operations

To perform array `INSERT` or `UPDATE` operations using the data interface for persistent LOBs, use any of the techniques discussed in this section in conjunction with `OCIBindArrayOfStruct()`, or by specifying the number of iterations (`iter`), with `iter` value greater than 1, in the `OCIStmtExecute()` call.

**Parent topic:** OCI Functions Used to Perform INSERT or UPDATE on LOB Columns

#### 9.4.5 The Data Interface Used to Fetch LOB Data in OCI

This section discusses techniques you can use to fetch data from LOB columns or attributes in OCI using the data interface for persistent LOBs.

- Simple Fetch in One Piece
- Performing a Piecewise Fetch with Polling
- Performing a Piecewise with Callback
- Array Fetch

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

##### 9.4.5.1 Simple Fetch in One Piece

To perform a simple fetch operation on LOBs in one piece using the data interface for persistent LOBs, do the following:

1.  Call `OCIStmtPrepare()` to prepare the `SELECT` statement in `OCI_DEFAULT` mode.
2.  Call `OCIDefineByPos()` to define a select list position in `OCI_DEFAULT` mode to define a LOB as character data or binary data.
3.  Call `OCIStmtExecute()` to run the `SELECT` statement.
4.  Call `OCIStmtFetch()` to do the actual fetch.

**Parent topic:** The Data Interface Used to Fetch LOB Data in OCI

##### 9.4.5.2 Performing a Piecewise Fetch with Polling

To perform a piecewise fetch operation on a LOB column with polling using the data interface for LOBs, do the following steps:

1.  Call `OCIStmtPrepare()` to prepare the `SELECT` statement in `OCI_DEFAULT` mode.
2.  Call `OCIDefinebyPos()` to define a select list position in `OCI_DYNAMIC_FETCH` mode to define the LOB column as character data or binary data.
3.  Call `OCIStmtExecute()` to run the `SELECT` statement.
4.  Call `OCIStmtFetch()` in default mode. Do each of the following in a loop while the value returned from `OCIStmtFetch()` is `OCI_NEED_DATA.` Terminate your loop when the value returned from `OCIStmtFetch()` is `OCI_SUCCESS`.
    - Call `OCIStmtGetPieceInfo()` to retrieve information about the piece to be fetched.

    - Call `OCIStmtSetPieceInfo()` to set information about piece to be fetched.

**Parent topic:** The Data Interface Used to Fetch LOB Data in OCI

##### 9.4.5.3 Performing a Piecewise with Callback

To perform a piecewise fetch operation on a LOB column with callback using the data interface for persistent LOBs, do the following:

1.  Call `OCIStmtPrepare()` to prepare the statement in `OCI_DEFAULT` mode.
2.  Call `OCIDefinebyPos()` to define a select list position in `OCI_DYNAMIC_FETCH` mode to define the LOB column as character data or binary data.
3.  Call `OCIStmtExecute()` to run the `SELECT` statement.
4.  Call `OCIDefineDynamic()` to specify the callback.
5.  Call `OCIStmtFetch()` in default mode.

**Parent topic:** The Data Interface Used to Fetch LOB Data in OCI

##### 9.4.5.4 Array Fetch

To perform an array fetch in OCI using the data interface for persistent LOBs, use any of the techniques discussed in this section in conjunction with `OCIDefineArrayOfStruct()`, or by specifying the number of iterations (`iter`), with the value of `iter` greater than 1, in the `OCIStmtExecute()` call.

**Parent topic:** The Data Interface Used to Fetch LOB Data in OCI

#### 9.4.6 PL/SQL and C Binds from OCI

When you call a PL/SQL procedure from OCI, and have an `IN` or `OUT` or `IN OUT` bind, you should be able to:

- Bind a variable as `SQLT_CHR` or `SQLT_LNG` where the formal parameter of the PL/SQL procedure is `SQLT_CLOB`, or

- Bind a variable as `SQLT_BIN` or `SQLT_LBI` where the formal parameter is `SQLT_BLOB`

The following two cases work:

##### Calling PL/SQL Out-binds in the "begin foo(:1); end;" Manner

Here is an example of calling PL/SQL out-binds in the "begin foo(:1); end;" Manner:

    text *sqlstmt = (text *)"BEGIN get_lob(:c); END; " ;

##### Calling PL/SQL Out-binds in the "call foo(:1);" Manner

Here is an example of calling PL/SQL out-binds in the "call foo(:1);" manner:

    text *sqlstmt = (text *)"CALL get_lob(:c);" ;

In both these cases, the rest of the program has these statements:

    OCIStmtPrepare(stmthp, errhp, sqlstmt, (ub4)strlen((char *)sqlstmt),
                   (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT);
       curlen = 0;
    OCIBindByName(stmthp, &bndhp[3], errhp,
            (text *) ":c", (sb4) strlen((char *) ":c"),
            (dvoid *) buf5, (sb4) LONGLEN, SQLT_CHR,
            (dvoid *) 0, (ub2 *) 0, (ub2 *) 0,
            (ub4) 1, (ub4 *) &curlen, (ub4) OCI_DATA_AT_EXEC);

The PL/SQL procedure, `get_lob()`, is as follows:

    procedure get_lob(c INOUT CLOB) is  -- This might have been column%type
      BEGIN
      ... /* The procedure body could be in PL/SQL or C*/
      END;

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.7 Example: C (OCI) - Binds of More than 4000 Bytes for INSERT and UPDATE

You can use binds of more than 4000 byes for `INSERT` and `UPDATE` operations.

    void insert3()
    {
    /* Insert of data into LOB attributes is allowed. */
       ub1 buffer[8000];
       text *insert_sql = (text *)"INSERT INTO Print_media (ad_header) \
                   VALUES (adheader_typ(NULL, NULL, NULL,:1))";
       OCIStmtPrepare(stmthp, errhp, insert_sql, strlen((char*)insert_sql),
                (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT);
       OCIBindByPos(stmthp, &bindhp[0], errhp, 1, (dvoid *)buffer, 2000,
                 SQLT_LNG, 0, 0, 0, 0, 0, (ub4) OCI_DEFAULT);
       OCIStmtExecute(svchp, stmthp, errhp, 1, 0, (const OCISnapshot*) 0,
                      (OCISnapshot*)0, OCI_DEFAULT);
    }

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.8 Using the Data Interface for LOBs in PL/SQL Binds from OCI on LOBs

The data interface for LOBs allows LOB PL/SQL binds from OCI to work. When you call a PL/SQL procedure from OCI, and have an `IN` or `OUT` or `IN OUT` bind, you should be able to bind a variable as `SQLT_CHR`, where the formal parameter of the PL/SQL procedure is `SQLT_CLOB`.

**Note:**

C procedures are wrapped inside a PL/SQL stub, so the OCI application always calls the PL/SQL stub.

For the OCI calling program, the following are likely cases:

##### Calling PL/SQL Out-binds in the "begin foo(:1); end;" Manner

For example:

    text *sqlstmt = (text *)"BEGIN PKG1.P5 (:c); END; " ;

##### Calling PL/SQL Out-binds in the "call foo(:1);" Manner

For example:

    text *sqlstmt = (text *)"CALL PKG1.P5( :c );" ;

In both these cases, the rest of the program is as follows:

       OCIStmtPrepare(stmthp, errhp, sqlstmt, (ub4)strlen((char *)sqlstmt),
                (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT);
       curlen = 0;

       OCIBindByName(stmthp, &bndhp[3], errhp,
                (text *) ":c4", (sb4) strlen((char *) ":c"),
                (dvoid *) buf5, (sb4) LONGLEN, SQLT_CHR,
                (dvoid *) 0, (ub2 *) 0, (ub2 *) 0,
                (ub4) 1, (ub4 *) &curlen, (ub4) OCI_DATA_AT_EXEC);

        OCIStmtExecute(svchp, stmthp, errhp,(ub4) 0,(ub4) 0, (const OCISnapshot*) 0,
                (OCISnapshot*) 0,(ub4) OCI_DEFAULT);

The PL/SQL procedure `PKG1.P5` is as follows:

       CREATE OR REPLACE PACKAGE BODY pkg1 AS
         ...
       procedure p5 (c OUT CLOB) is
         -- This might have been table%rowtype (so it   is CLOB now)
       BEGIN
         ...
       END p5;

    END pkg1;

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.9 Binding LONG Data for LOB Columns in Binds Greater Than 4000 Bytes

This example illustrates binding character data for a LOB column:

    void simple_insert()
    {
      word buflen;
      text buf[5000];
      text *insstmt = (text *) "INSERT INTO Print_media(Product_id, Ad_id,\
                      Ad_sourcetext) VALUES (2004, 1, :SRCTXT)";

      OCIStmtPrepare(stmthp, errhp, insstmt, (ub4)strlen((char *)insstmt),
                    (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT);

      OCIBindByName(stmthp, &bndhp[0], errhp,
                    (text *) ":SRCTXT", (sb4) strlen((char *) ":SRCTXT"),
                    (dvoid *) buf, (sb4) sizeof(buf), SQLT_CHR,
                    (dvoid *) 0, (ub2 *) 0, (ub2 *) 0,
                    (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT);

      memset((void *)buf, (int)'A', (size_t)5000);
      OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4) 0,
                     (const OCISnapshot*) 0, (OCISnapshot*) 0, (ub4) OCI_DEFAULT);
    }

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.10 Binding LONG Data to LOB Columns Using Piecewise INSERT with Polling

This example illustrates using piecewise `INSERT` with polling using the data interface for LOBs.

    void piecewise_insert()
    {
      text *sqlstmt = (text *)"INSERT INTO Print_media(Product_id, Ad_id,\
                      Ad_sourcetext) VALUES (:1, :2, :3)";
      ub2 rcode;
      ub1 piece, i;
      word product_id = 2004;
      word ad_id = 2;
      ub4 buflen;
      char buf[5000];

      OCIStmtPrepare(stmthp, errhp, sqlstmt, (ub4)strlen((char *)sqlstmt),
                     (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT);
      OCIBindByPos(stmthp, &bndhp[0], errhp, (ub4) 1,
                   (dvoid *) &product_id, (sb4) sizeof(product_id), SQLT_INT,
                   (dvoid *) 0, (ub2 *)0, (ub2 *)0,
                   (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT);
      OCIBindByPos(stmthp, &bndhp[1], errhp, (ub4) 2,
                   (dvoid *) &ad_id, (sb4) sizeof(ad_id), SQLT_INT,
                   (dvoid *) 0, (ub2 *)0, (ub2 *)0,
                   (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT);
      OCIBindByPos(stmthp, &bndhp[2], errhp, (ub4) 3,
                   (dvoid *) 0, (sb4) 15000, SQLT_LNG,
                   (dvoid *) 0, (ub2 *)0, (ub2 *)0,
                   (ub4) 0, (ub4 *) 0, (ub4) OCI_DATA_AT_EXEC);

      i = 0;
      while (1)
      {
        i++;
        retval = OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4) 0,
                                (CONST OCISnapshot*) 0, (OCISnapshot*) 0,
                                (ub4) OCI_DEFAULT);
        switch(retval)
        {
        case OCI_NEED_DATA:
          memset((void *)buf, (int)'A'+i, (size_t)5000);
          buflen = 5000;
          if (i == 1) piece = OCI_FIRST_PIECE;
          else if (i == 3) piece = OCI_LAST_PIECE;
          else piece = OCI_NEXT_PIECE;

          if (OCIStmtSetPieceInfo((dvoid *)bndhp[2],
                                  (ub4)OCI_HTYPE_BIND, errhp, (dvoid *)buf,
                                  &buflen, piece, (dvoid *) 0, &rcode))
            {
              printf("ERROR: OCIStmtSetPieceInfo: %d \n", retval);
              break;
            }

          break;
        case OCI_SUCCESS:
          break;
        default:
          printf( "oci exec returned %d \n", retval);
          report_error(errhp);
          retval = OCI_SUCCESS;
        } /* end switch */
        if (retval == OCI_SUCCESS)
          break;
      } /* end while(1) */
    }

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.11 Binding LONG Data to LOB Columns Using Piecewise INSERT with Callback

This example illustrates binding `LONG` data to LOB columns using a piecewise `INSERT` with callback:

    void callback_insert()
    {
      word buflen = 15000;
      word product_id = 2004;
      word ad_id = 3;
      text *sqlstmt = (text *) "INSERT INTO Print_media(Product_id, Ad_id,\
                      Ad_sourcetext) VALUES (:1, :2, :3)";
      word pos = 3;

      OCIStmtPrepare(stmthp, errhp, sqlstmt, (ub4)strlen((char *)sqlstmt),
                     (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT)

      OCIBindByPos(stmthp, &bndhp[0], errhp, (ub4) 1,
                   (dvoid *) &product_id, (sb4) sizeof(product_id), SQLT_INT,
                   (dvoid *) 0, (ub2 *)0, (ub2 *)0,
                   (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT);
      OCIBindByPos(stmthp, &bndhp[1], errhp, (ub4) 2,
                   (dvoid *) &ad_id, (sb4) sizeof(ad_id), SQLT_INT,
                   (dvoid *) 0, (ub2 *)0, (ub2 *)0,
                   (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT);
      OCIBindByPos(stmthp, &bndhp[2], errhp, (ub4) 3,
                   (dvoid *) 0, (sb4) buflen, SQLT_CHR,
                   (dvoid *) 0, (ub2 *)0, (ub2 *)0,
                   (ub4) 0, (ub4 *) 0, (ub4) OCI_DATA_AT_EXEC);

      OCIBindDynamic(bndhp[2], errhp, (dvoid *) (dvoid *) &pos,
                     insert_cbk, (dvoid *) 0, (OCICallbackOutBind) 0);

      OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4) 0,
                     (const OCISnapshot*) 0, (OCISnapshot*) 0,
                     (ub4) OCI_DEFAULT);
    } /* end insert_data() */

    /* Inbind callback to specify input data. */
    static sb4 insert_cbk(dvoid *ctxp, OCIBind *bindp, ub4 iter, ub4 index,
                           dvoid **bufpp, ub4 *alenpp, ub1 *piecep, dvoid **indpp)
    {
      static int a = 0;
      word   j;
      ub4    inpos = *((ub4 *)ctxp);
      char   buf[5000];

      switch(inpos)
      {
      case 3:
        memset((void *)buf, (int) 'A'+a, (size_t) 5000);
        *bufpp = (dvoid *) buf;
        *alenpp = 5000 ;
        a++;
        break;
      default: printf("ERROR: invalid position number: %d\n", inpos);
      }

      *indpp = (dvoid *) 0;
      *piecep = OCI_ONE_PIECE;
      if (inpos == 3)
      {
        if (a<=1)
        {
          *piecep = OCI_FIRST_PIECE;
          printf("Insert callback: 1st piece\n");
        }
        else if (a<3)
        {
          *piecep = OCI_NEXT_PIECE;
          printf("Insert callback: %d'th piece\n", a);
        }
        else {
          *piecep = OCI_LAST_PIECE;
          printf("Insert callback: %d'th piece\n", a);
          a = 0;
        }
      }
      return OCI_CONTINUE;
    }

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.12 Binding LONG Data to LOB Columns Using an Array INSERT

This example illustrates binding character data for LOB columns using an array `INSERT` operation:

    void array_insert()
    {
      ub4 i;
      word buflen;
      word arrbuf1[5];
      word arrbuf2[5];
      text arrbuf3[5][5000];
      text *insstmt = (text *)"INSERT INTO Print_media(Product_id, Ad_id,\
                      Ad_sourcetext) VALUES (:PID, :AID, :SRCTXT)";

      OCIStmtPrepare(stmthp, errhp, insstmt,
                     (ub4)strlen((char *)insstmt), (ub4) OCI_NTV_SYNTAX,
                     (ub4) OCI_DEFAULT);

      OCIBindByName(stmthp, &bndhp[0], errhp,
                    (text *) ":PID", (sb4) strlen((char *) ":PID"),
                    (dvoid *) &arrbuf1[0], (sb4) sizeof(arrbuf1[0]), SQLT_INT,
                    (dvoid *) 0, (ub2 *)0, (ub2 *) 0,
                    (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT);

      OCIBindByName(stmthp, &bndhp[1], errhp,
                    (text *) ":AID", (sb4) strlen((char *) ":AID"),
                    (dvoid *) &arrbuf2[0], (sb4) sizeof(arrbuf2[0]), SQLT_INT,
                    (dvoid *) 0, (ub2 *)0, (ub2 *) 0,
                    (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT);

      OCIBindByName(stmthp, &bndhp[2], errhp,
                    (text *) ":SRCTXT", (sb4) strlen((char *) ":SRCTXT"),
                    (dvoid *) arrbuf3[0], (sb4) sizeof(arrbuf3[0]), SQLT_CHR,
                    (dvoid *) 0, (ub2 *) 0, (ub2 *) 0,
                    (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT);

      OCIBindArrayOfStruct(bndhp[0], errhp sizeof(arrbuf1[0]),
                           indsk, rlsk, rcsk);
      OCIBindArrayOfStruct(bndhp[1], errhp, sizeof(arrbuf2[0]),
                           indsk, rlsk, rcsk);
      OCIBindArrayOfStruct(bndhp[2], errhp, sizeof(arrbuf3[0]),
                           indsk, rlsk, rcsk);

      for (i=0; i<5; i++)
      {
        arrbuf1[i] = 2004;
        arrbuf2[i] = i+4;
        memset((void *)arrbuf3[i], (int)'A'+i, (size_t)5000);
      }
      OCIStmtExecute(svchp, stmthp, errhp, (ub4) 5, (ub4) 0,
                     (const OCISnapshot*) 0, (OCISnapshot*) 0,
                     (ub4) OCI_DEFAULT);

    }

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.13 Selecting a LOB Column into a LONG Buffer Using a Simple Fetch

This example illustrates selecting a LOB column using a simple fetch:

    void simple_fetch()
    {
      word retval;
      text buf[15000];
      text *selstmt = (text *) "SELECT Ad_sourcetext FROM Print_media WHERE\
                      Product_id = 2004";

      OCIStmtPrepare(stmthp, errhp, selstmt, (ub4)strlen((char *)selstmt),
                     (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT);

      retval = OCIStmtExecute(svchp, stmthp, errhp, (ub4) 0, (ub4) 0,
                              (const OCISnapshot*) 0, (OCISnapshot*) 0,
                              (ub4) OCI_DEFAULT);
      while (retval == OCI_SUCCESS || retval == OCI_SUCCESS_WITH_INFO)
      {
        OCIDefineByPos(stmthp, &defhp, errhp, (ub4) 1, (dvoid *) buf,
                       (sb4) sizeof(buf), (ub2) SQLT_CHR, (dvoid *) 0,
                       (ub2 *) 0, (ub2 *) 0, (ub4) OCI_DEFAULT);
        retval = OCIStmtFetch(stmthp, errhp, (ub4) 1,
                              (ub4) OCI_FETCH_NEXT, (ub4) OCI_DEFAULT);
        if (retval == OCI_SUCCESS || retval == OCI_SUCCESS_WITH_INFO)
          printf("buf = %.*s\n", 15000, buf);
      }
    }

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.14 Selecting a LOB Column into a LONG Buffer Using Piecewise Fetch with Polling

This example illustrates selecting a LOB column into a `LONG` buffer using a piecewise fetch with polling:

    void piecewise_fetch()
    {
      text buf[15000];
      ub4 buflen=5000;
      word retval;
      text *selstmt = (text *) "SELECT Ad_sourcetext FROM Print_media
                      WHERE Product_id = 2004 AND Ad_id = 2";

      OCIStmtPrepare(stmthp, errhp, selstmt,
                     (ub4) strlen((char *)selstmt),
                     (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT);

      OCIDefineByPos(stmthp, &dfnhp, errhp, (ub4) 1,
                     (dvoid *) NULL, (sb4) 100000, SQLT_LNG,
                     (dvoid *) 0, (ub2 *) 0,
                     (ub2 *) 0, (ub4) OCI_DYNAMIC_FETCH);

      retval = OCIStmtExecute(svchp, stmthp, errhp, (ub4) 0, (ub4) 0,
                              (CONST OCISnapshot*) 0, (OCISnapshot*) 0,
                              (ub4) OCI_DEFAULT);

      retval = OCIStmtFetch(stmthp, errhp, (ub4) 1 ,
                            (ub2) OCI_FETCH_NEXT, (ub4) OCI_DEFAULT);

      while (retval != OCI_NO_DATA && retval != OCI_SUCCESS)
      {
        ub1 piece;
        ub4 iter;
        ub4 idx;

        genclr((void *)buf, 5000);
        switch(retval)
        {
        case OCI_NEED_DATA:
          OCIStmtGetPieceInfo(stmthp, errhp, &hdlptr, &hdltype,
                              &in_out, &iter, &idx, &piece);
          buflen = 5000;
          OCIStmtSetPieceInfo(hdlptr, hdltype, errhp,
                              (dvoid *) buf, &buflen, piece,
                              (CONST dvoid *) &indp1, (ub2 *) 0);
          retval = OCI_NEED_DATA;
          break;
        default:
          printf("ERROR: piece-wise fetching, %d\n", retval);
          return;
        } /* end switch */
        retval = OCIStmtFetch(stmthp, errhp, (ub4) 1 ,
                              (ub2) OCI_FETCH_NEXT, (ub4) OCI_DEFAULT);
        printf("Data : %.5000s\n", buf);
      } /* end while */
    }

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.15 Selecting a LOB Column into a LONG Buffer Using Piecewise Fetch with Callback

This example illustrates selecting a `LONG` column into a LOB buffer when using a piecewise fetch with callback:

    char buf[5000];
    void callback_fetch()
    {
      word outpos = 1;
      text *sqlstmt = (text *) "SELECT Ad_sourcetext FROM Print_media WHERE
                      Product_id = 2004 AND Ad_id = 3";

      OCIStmtPrepare(stmthp, errhp, sqlstmt, (ub4)strlen((char *)sqlstmt),
                     (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT);
      OCIDefineByPos(stmthp, &dfnhp[0], errhp, (ub4) 1,
                     (dvoid *) 0, (sb4)3 * sizeof(buf), SQLT_CHR,
                     (dvoid *) 0, (ub2 *)0, (ub2 *)0,
                     (ub4) OCI_DYNAMIC_FETCH);

      OCIDefineDynamic(dfnhp[0], errhp, (dvoid *) &outpos,
                       (OCICallbackDefine) fetch_cbk);

      OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4) 0,
                     (const OCISnapshot*) 0, (OCISnapshot*) 0,
                     (ub4) OCI_DEFAULT);
      buf[ 4999 ] = '\0';
      printf("Select callback: Last piece: %s\n", buf);
    }

    /* -------------------------------------------------------------- */
    /* Fetch callback to specify buffers. */
    /* -------------------------------------------------------------- */
    static sb4 fetch_cbk(dvoid *ctxp, OCIDefine *dfnhp, ub4 iter, dvoid **bufpp,
                          ub4 **alenpp, ub1 *piecep, dvoid **indpp, ub2 **rcpp)
    {
      static int a = 0;
      ub4 outpos = *((ub4 *)ctxp);
      ub4 len = 5000;
      switch(outpos)
      {
      case 1:
        a ++;
        *bufpp = (dvoid *) buf;
        *alenpp = &len;
        break;
      default:
        *bufpp = (dvoid *) 0;
        *alenpp = (ub4 *) 0;
        printf("ERROR: invalid position number: %d\n", outpos);
      }
      *indpp = (dvoid *) 0;
      *rcpp = (ub2 *) 0;

      buf[len] = '\0';
      if (a<=1)
      {
        *piecep = OCI_FIRST_PIECE;
        printf("Select callback: 0th piece\n");
      }
      else if (a<3)
      {
        *piecep = OCI_NEXT_PIECE;
        printf("Select callback: %d'th piece: %s\n", a-1, buf);
      }
      else {
        *piecep = OCI_LAST_PIECE;
        printf("Select callback: %d'th piece: %s\n", a-1, buf);
        a = 0;
      }
      return OCI_CONTINUE;
    }

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

#### 9.4.16 Selecting a LOB Column into a LONG Buffer Using an Array Fetch

This example illustrates selecting a LOB column into a `LONG` buffer using an array fetch:

    void array_fetch()
    {
      word i;
      text arrbuf[5][5000];
      text *selstmt = (text *) "SELECT Ad_sourcetext FROM Print_media WHERE
                      Product_id = 2004 AND Ad_id >=4";

      OCIStmtPrepare(stmthp, errhp, selstmt, (ub4)strlen((char *)selstmt),
                     (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT);

      OCIStmtExecute(svchp, stmthp, errhp, (ub4) 0, (ub4) 0,
                     (const OCISnapshot*) 0, (OCISnapshot*) 0, (ub4) OCI_DEFAULT);

      OCIDefineByPos(stmthp, &defhp1, errhp, (ub4) 1,
                       (dvoid *) arrbuf[0], (sb4) sizeof(arrbuf[0]),
                       (ub2) SQLT_CHR, (dvoid *) 0,
                       (ub2 *) 0, (ub2 *) 0, (ub4) OCI_DEFAULT);

      OCIDefineArrayOfStruct(dfnhp1, errhp, sizeof(arrbuf[0]), indsk,
                             rlsk, rcsk);

      retval = OCIStmtFetch(stmthp, errhp, (ub4) 5,
                            (ub4) OCI_FETCH_NEXT, (ub4) OCI_DEFAULT);
      if (retval == OCI_SUCCESS || retval == OCI_SUCCESS_WITH_INFO)
      {
         printf("%.5000s\n", arrbuf[0]);
         printf("%.5000s\n", arrbuf[1]);
         printf("%.5000s\n", arrbuf[2]);
         printf("%.5000s\n", arrbuf[3]);
         printf("%.5000s\n", arrbuf[4]);
      }
    }

**Parent topic:** The Data Interface Used for Persistent LOBs in OCI

### 9.5 The Data Interface Used with Persistent LOBs in Java

You can also read and write `CLOB` and `BLOB` data using the same streaming mechanism as for `LONG` and `LONG` `RAW` data.

To read, use `defineColumnType(nn, Types.LONGVARCHAR)` or `defineColumnType(nn, Types.LONGVARBINARY)`on the column. This produces a direct stream on the data as if it is a `LONG` or `LONG` `RAW` column. For input in a `PreparedStatement`, you may use `setBinaryStream()`, `setCharacterStream()`, or `setAsciiStream()` for a parameter which is a `BLOB` or `CLOB`. These methods use the stream interface to create a LOB in the database from the data in the stream. If the length of the data is known, for better performance, use the versions of setBinaryStream() or setCharacterStream functions which accept the length parameter. The data interface also supports standard JDBC methods such as getString/getBytes on ResultSet and CallableStatement and setString/setBytes on PreparedStatement to read and write LOB data. It is easier to code, and in many cases faster, to use these APIs for LOB access. All these techniques reduce database round trips and may result in improved performance in some cases. See the Javadoc on stream data for the significant restrictions which apply, at [`http://www.oracle.com/technology/`](http://www.oracle.com/technology/).

Refer to the following in the JDBC Developer's Guide and Reference:

**See Also:**

- [Oracle Database JDBC Developer's Guide](../jjdbc/LOBs-and-BFiles.md), "Working with LOBs and BFILEs", section "Data Interface for LOBs"

- [Oracle Database JDBC Developer's Guide](../jjdbc/JDBC-standards-support.md), "JDBC Standards Support"

**Parent topic:** Data Interface for Persistent LOBs

### 9.6 The Data Interface Used with Remote LOBs

The data interface for insert, update, and select of remote LOBs (access over a `dblink`) is supported after Oracle Database 10g Release 2.

- About the Data Interface with Remote LOBs
- Non-Supported Syntax
- Remote Data Interface Example in PL/SQL
- Remote Data Interface Example in OCI
- Remote Data Interface Examples in JDBC

**Parent topic:** Data Interface for Persistent LOBs

#### 9.6.1 About the Data Interface with Remote LOBs

The examples discussed use the `print_media` table created in two schemas: `dbs1` and `dbs2`. The `CLOB` column of that table used in the examples shown is `ad_finaltext`. The examples to be given for PL/SQL, OCI, and Java use binds and defines for this one column, but multiple columns can also be accessed. Here is the functionality supported and its limitations:

- You can define a `CLOB` as `CHAR` or `NCHAR` and an `NCLOB` as CHAR or NCHAR. `CLOB` and `NCLOB` can be defined as a `LONG`. A `BLOB` can be defined as a `RAW` or a `LONG` `RAW`.

- Array binds and defines are supported.

**See Also:**

"Remote Data Interface Example in PL/SQL" and the sections following it.

**Parent topic:** The Data Interface Used with Remote LOBs

#### 9.6.2 Non-Supported Syntax

Certain syntax is not supported for remote LOBs.

- Queries involving more than one database are not supported:

      SELECT t1.lobcol, a2.lobcol FROM t1, t2.lobcol@dbs2 a2 WHERE
      LENGTH(t1.lobcol) = LENGTH(a2.lobcol);

  Neither is this query (in a PL/SQL block):

      SELECT t1.lobcol INTO varchar_buf1 FROM t1@dbs1
      UNION ALL
      SELECT t2.lobcol INTO varchar_buf2 FROM t2@dbs2;

- Only binds and defines for data going into remote persistent LOB columns are supported, so that parameter passing in PL/SQL where `CHAR` data is bound or defined for remote LOBs is not allowed because this could produce a remote temporary LOB, which are not supported. These statements all produce errors:

      SELECT foo() INTO varchar_buf FROM table1@dbs2; -- foo returns a LOB

      SELECT foo()@dbs INTO char_val FROM DUAL; -- foo returns a LOB

      SELECT XMLType().getclobval INTO varchar_buf FROM table1@dbs2;

- If the remote object is a view such as

      CREATE VIEW v AS SELECT foo() a FROM ... ; -- foo returns a LOB
      /* The local database then tries to get the CLOB data and returns an error */
      SELECT a INTO varchar_buf FROM v@dbs2;

  This returns an error because it produces a remote temporary LOB, which is not supported.

- `RETURNING` `INTO` does not support implicit conversions between `CHAR` and `CLOB`.

- PL/SQL parameter passing is not allowed where the actual argument is a LOB type and the remote argument is a `VARCHAR2`, `NVARCHAR2`, `CHAR`, `NCHAR`, or `RAW`.

**Parent topic:** The Data Interface Used with Remote LOBs

#### 9.6.3 Remote Data Interface Example in PL/SQL

The data interface only supports data of size less than 32KB in PL/SQL. The following snippet shows a PL/SQL example:

    CONNECT pm
    declare
      my_ad varchar(6000) := lpad('b', 6000, 'b');
    BEGIN
      INSERT INTO print_media@dbs2(product_id, ad_id, ad_finaltext)
           VALUES (10000, 10, my_ad);
      -- Reset the buffer value
      my_ad := 'a';
      SELECT ad_finaltext INTO my_ad FROM print_media@dbs2
           WHERE product_id = 10000;
    END;
    /

If `ad_finaltext` were a `BLOB` column instead of a `CLOB`, `my_ad` has to be of type `RAW`. If the LOB is greater than 32KB - 1 in size, then PL/SQL raises a truncation error and the contents of the buffer are undefined.

**Parent topic:** The Data Interface Used with Remote LOBs

#### 9.6.4 Remote Data Interface Example in OCI

The data interface only supports data of size less than `2 GBytes` (the maximum value possible of a variable declared as `sb4`) for OCI. The following pseudocode can be enhanced to be a part of an OCI program:

    ...
    text *sql = (text *)"insert into print_media@dbs2
                        (product_id, ad_id, ad_finaltext)
                        values (:1, :2, :3)";
    OCIStmtPrepare(...);
    OCIBindByPos(...); /* Bind data for positions 1 and 2
                         * which are independent of LOB */
    OCIBindByPos(stmthp, &bndhp[2], errhp, (ub4) 3,
                 (dvoid *) charbuf1, (sb4) len_charbuf1, SQLT_CHR,
                 (dvoid *) 0, (ub2 *)0, (ub2 *)0, 0, 0, OCI_DEFAULT);
    OCIStmtExecute(...);

    ...

    text *sql = (text *)"select ad_finaltext from print_media@dbs2
                        where product_id = 10000";
    OCIStmtPrepare(...);
    OCIDefineByPos(stmthp, &dfnhp[2], errhp, (ub4) 1,
                 (dvoid *) charbuf2, (sb4) len_charbuf2, SQLT_CHR,
                 (dvoid *) 0, (ub2 *)0, (ub2 *)0, OCI_DEFAULT);
    OCIStmtExecute(...);
    ...

If `ad_finaltext` were a `BLOB` instead of a `CLOB`, then you bind and define using type `SQLT_BIN`. If the LOB is greater than 2GB - 1 in size, then OCI raises a truncation error and the contents of the buffer are undefined.

**Parent topic:** The Data Interface Used with Remote LOBs

#### 9.6.5 Remote Data Interface Examples in JDBC

The following code snippets works with all three JDBC drivers (OCI, Thin, and `kprb` in the database):

Bind:

This is for the non-streaming mode:

    ...
    String sql = "insert into print_media@dbs2 (product_id, ad_id, ad_final_text)" +
                 " values (:1, :2, :3)";
        PreparedStatement pstmt = conn.prepareStatement(sql);
        pstmt.setInt( 1, 2 );
        pstmt.setInt( 2, 20);
        pstmt.setString( 3, "Java string" );
        int rows = pstmt.executeUpdate();
    ...

For the streaming mode, the same code as the preceding works, except that the `setString()` statement is replaced by one of the following:

    pstmt.setCharacterStream( 3, new LabeledReader(), 1000000 );
    pstmt.setAsciiStream( 3, new LabeledAsciiInputStream(), 1000000 );

Here, `LabeledReader()` and `LabeledAsciiInputStream()` produce character and ASCII streams respectively. If `ad_finaltext` were a `BLOB` column instead of a `CLOB`, then the preceding example works if the bind is of type `RAW`:

    pstmt.setBytes( 3, <some byte[] array> );

    pstmt.setBinaryStream( 3, new LabeledInputStream(), 1000000 );

Here, `LabeledInputStream()` produces a binary stream.

Define:

For non-streaming mode:

    OracleStatement stmt = (OracleStatement)(conn.createStatement());
      stmt.defineColumnType( 1, Types.VARCHAR );
      ResultSet rst = stmt.executeQuery("select ad_finaltext from print_media@dbs2" );
      while( rst.next() )
         {
           String s = rst.getString( 1 );
           System.out.println( s );
         }

For streaming mode:

    OracleStatement stmt = (OracleStatement)(conn.createStatement());
      stmt.defineColumnType( 1, Types.LONGVARCHAR );
      ResultSet rst = stmt.executeQuery("select ad_finaltext from print_media@dbs2" );
      while( rst.next() )
         {
           Reader reader = rst.getCharacterStream( 1 );
           while( reader.ready() )
           {
             System.out.print( (char)(reader.next()) );
           }
           System.out.println();
         }

If `ad_finaltext` were a `BLOB` column instead of a `CLOB`, then the preceding examples work if the define is of type `LONGVARBINARY`:

    ...
       OracleStatement stmt = (OracleStatement)conn.createStatement();

       stmt.defineColumnType( 1, Types.INTEGER );
       stmt.defineColumnType( 2, Types.LONGVARBINARY );

       ResultSet rset = stmt.executeQuery("SELECT ID, LOBCOL FROM LOBTAB@MYSELF");

       while(rset.next())
        {
         /* using getBytes() */
         /*
         byte[] b = rset.getBytes("LOBCOL");
         System.out.println("ID: " + rset.getInt("ID") + "  length: " + b.length);
         */

            /* using getBinaryStream() */
            InputStream byte_stream = rset.getBinaryStream("LOBCOL");
            byte [] b = new byte [100000];
            int b_len = byte_stream.read(b);
            System.out.println("ID: " + rset.getInt("ID") + "  length: " + b_len);

            byte_stream.close();
        }
    ...

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/LOBs-and-BFiles.md)

**Parent topic:** The Data Interface Used with Remote LOBs
