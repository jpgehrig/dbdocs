## 2  Working with LOBs

Working with LOBs for application development requires that you understand LOB semantics and various techniques used with LOBs.

Most of the discussions regarding persistent LOBs assume that you are dealing with existing LOBs in tables. The task of creating tables with LOB columns is typically performed by your database administrator.

**See Also:**

- [Using Oracle LOB Storage](using-oracle-LOBs-storage.md) for creating LOBs using the SecureFiles paradigm

- [LOB Storage with Applications](LOB-storage-with-applications.md) for storage parameters used in creating LOBs

Topics:

- LOB Column States

- Locking a Row Containing a LOB

- LOB Open and Close Operations

- LOB Locator and LOB Value

- LOB Locators and BFILE Locators

- LOB Access

- LOB Rules and Restrictions

<!-- -->

- LOB Column States
  The techniques you use when accessing a cell in a LOB column differ depending on the state of the given cell.
- Locking a Row Containing a LOB
  You can lock a row containing a LOB to prevent other database users from writing to the LOB during a transaction.
- LOB Open and Close Operations
  The LOB APIs include operations that enable you to explicitly open and close a LOB instance.
- LOB Locator and LOB Value
  You can use two different techniques to access and modify LOB values.
- LOB Locators and BFILE Locators
  There are differences between the semantics of locators for the LOB types `BLOB`, `CLOB`, and `NCLOB`, and the semantics of locators for the `BFILE` type:
- LOB Access
- LOB Rules and Restrictions
  This section provides details on LOB rules and restrictions.

**Parent topic:** [Getting Started](getting-started.md)

### 2.1 LOB Column States

The techniques you use when accessing a cell in a LOB column differ depending on the state of the given cell.

A cell in a LOB Column can be in one of the following states:

- NULL

  The table cell is created, but the cell holds no locator or value.

- Empty

  A LOB instance with a locator exists in the cell, but it has no value. The length of the LOB is zero.

- Populated

  A LOB instance with a locator and a value exists in the cell.

**Parent topic:** Working with LOBs

### 2.2 Locking a Row Containing a LOB

You can lock a row containing a LOB to prevent other database users from writing to the LOB during a transaction.

- To lock the row, specify the `FOR UPDATE` clause when you select the row. While the row is locked, other users cannot lock or update the LOB until you end your transaction.

**Parent topic:** Working with LOBs

### 2.3 LOB Open and Close Operations

The LOB APIs include operations that enable you to explicitly open and close a LOB instance.

You can open and close a persistent LOB instance of any type: `BLOB`, `CLOB`, `NCLOB`, or `BFILE`. You open a LOB to achieve one or both of the following results:

- Open the LOB in read-only mode

  This ensures that the LOB (both the LOB locator and LOB value) cannot be changed in your session until you explicitly close the LOB. For example, you can open the LOB to ensure that the LOB is not changed by some other part of your program while you are using the LOB in a critical operation. After you perform the operation, you can then close the LOB.

- Open the LOB in read write/mode, for persistent `BLOB`, `CLOB`, or `NCLOB` instances only

  Opening a LOB in read/write mode defers any index maintenance on the LOB column until you close the LOB. Opening a LOB in read/write mode is only useful if there is an extensible index on the LOB column, and you do not want the database to perform index maintenance every time you write to the LOB. This technique can increase the performance of your application if you are doing several write operations on the LOB while it is open.

If you open a LOB, then you must close the LOB at some point later in your session. This is the only requirement for an open LOB. While a LOB instance is open, you can perform as many operations as you want on the LOB—provided the operations are allowed in the given mode.

**See Also:**

[Opening Persistent LOBs with the OPEN and CLOSE Interfaces](advanced-design-considerations.md) for more information about usage of these APIs

**Parent topic:** Working with LOBs

### 2.4 LOB Locator and LOB Value

You can use two different techniques to access and modify LOB values.

Topics:

- Using the Data Interface for LOBs

- Use the LOB Locator to Access and Modify LOB Values

<!-- -->

- Using the Data Interface for LOBs
  You can perform bind and define operations on `CLOB` and `BLOB` columns in C applications using the data interface for LOBs in OCI.
- Use the LOB Locator to Access and Modify LOB Values
  You can use the LOB locator to access and modify LOB values.

**Parent topic:** Working with LOBs

#### 2.4.1 Using the Data Interface for LOBs

You can perform bind and define operations on `CLOB` and `BLOB` columns in C applications using the data interface for LOBs in OCI.

Using the data interface enables you to insert or select out data in a LOB column without using a LOB locator as follows:

- Use a bind variable associated with a LOB column to insert character data into a `CLOB`, or `RAW` data into a `BLOB`.

- Use a define operation to define an output buffer in your application that holds character data selected from a `CLOB` or `RAW` data selected from a `BLOB`.

  **See Also:**

  [Data Interface for Persistent LOBs](data-interface-for-persistent-LOBs.md) for more information on implicit assignment of LOBs to other data types

**Parent topic:** LOB Locator and LOB Value

#### 2.4.2 Use the LOB Locator to Access and Modify LOB Values

You can use the LOB locator to access and modify LOB values.

A LOB locator, which is a reference to the location of the LOB value, can access the value of a LOB instanced stored in the database. Database tables store only locators in `CLOB`, `BLOB`, `NCLOB` and `BFILE` columns.

Note the following with respect to LOB locators and values:

- LOB locators are passed to various LOB APIs to access or manipulate a LOB value.

- A LOB locator can be assigned to any LOB instance of the same type.

- LOB instances are characterized as temporary or persistent, but the locator is not.

**Parent topic:** LOB Locator and LOB Value

### 2.5 LOB Locators and BFILE Locators

There are differences between the semantics of locators for the LOB types `BLOB`, `CLOB`, and `NCLOB`, and the semantics of locators for the `BFILE` type:

- For LOB types `BLOB`, `CLOB`, and `NCLOB`, the LOB column stores a locator to the LOB value. Each LOB instance has its own distinct LOB locator and also a distinct copy of the LOB value.

- For initialized `BFILE` columns, the row stores a locator to the external operating system file that holds the value of the `BFILE`. Each `BFILE` instance in a given row has its own distinct locator; however, two different rows can contain a `BFILE` locator that points to the same operating system file.

Regardless of where the value of a LOB is stored, a locator is stored in the table row of any initialized LOB column. Also, when you select a LOB from a table, the LOB returned is always a temporary LOB.

**Note:**

When the term locator is used without an identifying prefix term, it refers to both LOB locators and `BFILE` locators.

**See Also:**

[LOBs Returned from SQL Functions](SQL-semantics-and-LOBs.md) for more information on locators for temporary LOBs

Topics:

- Table for LOB Examples: The PM Schema print_media Table

- LOB Column Initialization

<!-- -->

- Table for LOB Examples: The PM Schema print_media Table
  Many Oracle LOB examples use the `print_media` table of the Oracle Database Sample Schema `PM`.
- LOB Column Initialization
  LOB instances that are `NULL` do not have a locator.

**Parent topic:** Working with LOBs

#### 2.5.1 Table for LOB Examples: The PM Schema print_media Table

Many Oracle LOB examples use the `print_media` table of the Oracle Database Sample Schema `PM`.

The `print_media` table is defined as:

    CREATE TABLE print_media
        ( product_id        NUMBER(6)
        , ad_id             NUMBER(6)
        , ad_composite      BLOB
        , ad_sourcetext     CLOB
        , ad_finaltext      CLOB
        , ad_fltextn        NCLOB
        , ad_textdocs_ntab  textdoc_tab
        , ad_photo          BLOB
        , ad_graphic        BFILE
        , ad_header         adheader_typ
        ) NESTED TABLE ad_textdocs_ntab STORE AS textdocs_nestedtab;

**See Also:**

"[Creating a Table Containing One or More LOB Columns](DDL-DML-statements-with-LOBs.md)" for information about creating `print_media` and its associated tables and files

**Parent topic:** LOB Locators and BFILE Locators

#### 2.5.2  LOB Column Initialization

LOB instances that are `NULL` do not have a locator.

Before you can pass a LOB instance to any LOB API routine, the instance must contain a locator. For example, you can select a `NULL` LOB from a row, but you cannot pass the instance to the PL/SQL `DBMS_LOB.READ` procedure. You must initialize a LOB instance, which provides it with a locator, to make it non-`NULL`. Then you can pass the LOB instance.

Topics:

- Initializing a Persistent LOB Column

- Initializing BFILEs

<!-- -->

- Initializing a Persistent LOB Column
  Before you can start writing data to a persistent LOB using supported programmatic environment interfaces such as PL/SQL, OCI, Visual Basic, or Java, you must make the LOB column/attribute non-`NULL`.
- Initializing BFILEs
  Before you can access `BFILE` values using LOB APIs, the `BFILE` column or attribute must be made non-`NULL`.

**Parent topic:** LOB Locators and BFILE Locators

##### 2.5.2.1 Initializing a Persistent LOB Column

Before you can start writing data to a persistent LOB using supported programmatic environment interfaces such as PL/SQL, OCI, Visual Basic, or Java, you must make the LOB column/attribute non-`NULL`.

You can make a LOB column/attribute non-`NULL` by initializing the persistent LOB to empty, using an `INSERT`/`UPDATE` statement with the function `EMPTY_BLOB` for `BLOB`s or `EMPTY_CLOB` for `CLOB`s and `NCLOB`s.

**Note:**

You can use SQL to populate a LOB column with data even if it contains a `NULL` value.

**See Also:**

- [LOB Storage with Applications](LOB-storage-with-applications.md) for more information on initializing LOB columns

- "[Programmatic Environments That Support LOBs](overview-of-supplied-LOB-APIs.md)" for all supported interfaces

Running the `EMPTY_BLOB()` or `EMPTY_CLOB()` function in and of itself does not raise an exception. However, using a LOB locator that was set to empty to access or manipulate the LOB value in any PL/SQL `DBMS_LOB` or OCI function raises an exception.

Valid places where empty LOB locators may be used include the `VALUES` clause of an `INSERT` statement and the `SET` clause of an `UPDATE` statement.

**See Also:**

- "[Directory Objects](LOB-APIs-for-BFILE-operations.md)" for details of `CREATE DIRECTORY` and `BFILENAME` usage

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DIRECTORY.md), `CREATE` `DIRECTORY` statement

**Note:**

Character strings are inserted using the default character set for the instance.

The `INSERT` statement in the next example uses the `print_media` table described in "Table for LOB Examples: The PM Schema print_media Table" and does the following:

- Populates `ad_sourcetext` with the character string `'my Oracle'`

- Sets `ad_composite`, `ad_finaltext`, and `ad_fltextn` to an empty value

- Sets `ad_photo`to `NULL`

- Initializes `ad_graphic` to point to the file `my_picture` located under the logical directory `my_directory_object`

<!-- -->

    CREATE OR REPLACE DIRECTORY my_directory_object AS 'oracle/work/tklocal';
    INSERT INTO print_media VALUES (1726, 1, EMPTY_BLOB(),
        'my Oracle', EMPTY_CLOB(), EMPTY_CLOB(),
        NULL, NULL, BFILENAME('my_directory_object', 'my_picture'), NULL);

Similarly, the LOB attributes for the `ad_header` column in `print_media` can be initialized to `NULL`, empty, or a character/raw literal, which is shown in the following statement:

    INSERT INTO print_media (product_id, ad_id, ad_header)
        VALUES (1726, 1, adheader_typ('AD FOR ORACLE', sysdate,
        'Have Grid', EMPTY_BLOB()));

**See Also:**

- "[Inserting a Row by Selecting a LOB From Another Table](DDL-DML-statements-with-LOBs.md)"

- "[Inserting a LOB Value Into a Table](DDL-DML-statements-with-LOBs.md)"

- "[Inserting a Row by Initializing a LOB Locator Bind Variable](DDL-DML-statements-with-LOBs.md)"

- "[OCILobLocator Pointer Assignment](overview-of-supplied-LOB-APIs.md)" for details on LOB locator semantics in OCI

**Parent topic:** LOB Column Initialization

##### 2.5.2.2 Initializing BFILEs

Before you can access `BFILE` values using LOB APIs, the `BFILE` column or attribute must be made non-`NULL`.

You can initialize the `BFILE` column to point to an external operating system file by using the `BFILENAME` function.

**See Also:**

"[About Accessing BFILEs](LOB-APIs-for-BFILE-operations.md)" for more information on initializing BFILE columns

**Parent topic:** LOB Column Initialization

### 2.6 LOB Access

You can access a LOB instance with several techniques.

Topics:

- Accessing a LOB Using SQL

- Accessing a LOB Using the Data Interface

- Accessing a LOB Using the Locator Interface

<!-- -->

- Accessing a LOB Using SQL
  You can access LOBs using SQL.
- Accessing a LOB Using the Data Interface
  You can access LOBs using the data interface.
- Accessing a LOB Using the Locator Interface
  You can access and manipulate a LOB instance by passing the LOB locator to the LOB APIs supplied with the database.

**Parent topic:** Working with LOBs

#### 2.6.1 Accessing a LOB Using SQL

You can access LOBs using SQL.

The support for columns that use LOB data types that is built into many SQL functions enables you to use SQL semantics to access LOB columns. In most cases, you can use the same SQL semantics on a LOB column that you would use on a `VARCHAR2` column.

**See Also:**

For details on SQL semantics support for LOBs, see [SQL Semantics and LOBs](SQL-semantics-and-LOBs.md)

**Parent topic:** LOB Access

#### 2.6.2 Accessing a LOB Using the Data Interface

You can access LOBs using the data interface.

You can select a LOB directly into `CHAR` or `RAW` buffers using LONG-to-LOB APIs in OCI and PL/SQL interfaces. In the following PL/SQL example, `ad_finaltext` is selected into a `VARCHAR2` buffer `final_ad`.

    DECLARE
        final_ad VARCHAR2(32767);
    BEGIN
        SELECT ad_finaltext INTO final_ad FROM print_media
            WHERE product_id = 2056 and ad_id = 12001 ;
        /* PUT_LINE can only output up to 255 characters at a time  */
        ...
        DBMS_OUTPUT.PUT_LINE(final_ad);
        /* more calls to read final_ad */
        ...
    END;

**See Also:**

For more details on accessing LOBs using the data interface, see [Data Interface for Persistent LOBs](data-interface-for-persistent-LOBs.md)

**Parent topic:** LOB Access

#### 2.6.3 Accessing a LOB Using the Locator Interface

You can access and manipulate a LOB instance by passing the LOB locator to the LOB APIs supplied with the database.

To access the LOB instance, use the extensive set of LOB APIs provided with each supported programmatic environment. In OCI, a LOB locator is mapped to a locator pointer, which is used to access the LOB value.

**Note:**

In all environments, including OCI, the LOB APIs operate on the LOB value implicitly—there is no requirement to dereference the LOB locator.

**See Also:**

- [Overview of Supplied LOB APIs](overview-of-supplied-LOB-APIs.md)

- "[OCILobLocator Pointer Assignment](overview-of-supplied-LOB-APIs.md)" for details on LOB locator semantics in OCI

**Parent topic:** LOB Access

### 2.7 LOB Rules and Restrictions

This section provides details on LOB rules and restrictions.

Topics:

- [Rules for LOB Columns](distributed-LOBs.md)

- Restrictions for LOB Operations

<!-- -->

- Rules for LOB Columns
- Restrictions for LOB Operations
  LOB operations have certain restrictions.

**Parent topic:** Working with LOBs

#### 2.7.1 Rules for LOB Columns

LOB columns are subject to the following rules and restrictions:

- You cannot specify a LOB as a primary key column.
- Oracle Database has limited support for remote LOBs and ORA-22992 errors can occur when remote LOBs are used in ways that are not supported.

<!-- -->

- Clusters cannot contain LOBs, either as key or nonkey columns.
- Even though compressed `VARRAY` data types are supported, they are less performant.
- The following data structures are supported only as temporary instances. You cannot store these instances in database tables:
  - `VARRAY` of any LOB type
  - `VARRAY` of any type containing a LOB type, such as an object type with a LOB attribute
  - `ANYDATA` of any LOB type
  - `ANYDATA` of any type containing a LOB
- You cannot specify LOB columns in the `ORDER` `BY` clause of a query, the `GROUP` `BY` clause of a query, or an aggregate function.
- You cannot specify a LOB column in a `SELECT`... `DISTINCT` or `SELECT`... `UNIQUE` statement or in a join. However, you can specify a LOB attribute of an object type column in a `SELECT`... `DISTINCT` statement, a query that uses the `UNION`, or a `MINUS` set operator if the object type of the column has a `MAP` or `ORDER` function defined on it.
- The first (`INITIAL`) extent of a LOB segment must contain at least three database blocks.
- The minimum extent size is 14 blocks. For an 8K block size (the default), this is equivalent to 112K.
- When creating an `AFTER UPDATE` DML trigger, you cannot specify a LOB column in the `UPDATE` `OF` clause.
- You cannot specify a LOB column as part of an index key. However, you can specify a LOB column in the indextype specification of a domain index. In addition, Oracle Text lets you define an index on a `CLOB` column.
- In an `INSERT`... `AS` `SELECT` operation, you can bind up to 4000 bytes of data to LOB columns and attributes. There is no length restriction when you do`INSERT`... `AS` `SELECT` from one table to another table using SQL with no bind variables.
- If a table has both `LONG` and LOB columns, you cannot bind more than 4000 bytes of data to both the `LONG` and LOB columns in the same SQL statement. However, you can bind more than 4000 bytes of data to either the `LONG` or the LOB column.

**Note:**

For a table on which you have defined an `AFTER` `UPDATE` DML trigger, if you use OCI functions or the `DBMS_LOB` package to change the value of a LOB column or the LOB attribute of an object type column, the database does not fire the DML trigger.

**See Also:**

- [Using Oracle LOB Storage](using-oracle-LOBs-storage.md) for SecureFiles capabilities (encryption, compression, and deduplication)

- [Working with Remote LOB Columns](distributed-LOBs.md) for more information about Remote LOBs.

- [Restrictions for LOBs in Partitioned Index-Organized Tables](LOB-storage-with-applications.md)

- [Migrating Columns from LONGs to LOBs](migrating-columns-from-LONGs-to-LOBs.md) for migration limitations on clustered tables, domain indexes, and function-based indexes

- [Unsupported Use of LOBs in SQL](SQL-semantics-and-LOBs.md) for restrictions on SQL semantics

- [Restriction on First Extent of a LOB Segment](LOB-storage-with-applications.md)

- [The Data Interface Used with Remote LOBs](data-interface-for-persistent-LOBs.md)

**Parent topic:** LOB Rules and Restrictions

#### 2.7.2 Restrictions for LOB Operations

LOB operations have certain restrictions.

General LOB restrictions include the following:

- In SQL Loader, a field read from a LOB cannot be used as an argument to a clause.

- Case-insensitive searches on `CLOB` columns often do not succeed. For example, to do a case-insensitive search on a `CLOB` column:

      ALTER SESSION SET NLS_COMP=LINGUISTIC;
      ALTER SESSION SET NLS_SORT=BINARY_CI;
      SELECT * FROM ci_test WHERE LOWER(clob_col) LIKE 'aa%';

  The select fails without the `LOWER` function. You can do case-insensitive searches with Oracle Text or `DBMS_LOB.INSTR()`.

- Session migration is not supported for `BFILE`s in shared server (multithreaded server) mode. This implies that operations on open `BFILE`s can persist beyond the end of a call to a shared server. In shared server sessions, `BFILE` operations are bound to one shared server, they cannot migrate from one server to another.

- Symbolic links are not allowed in the directory paths or file names when opening BFILEs. The entire directory path and filename is checked and the following error is returned if any symbolic link is found:

  `ORA-22288: file or LOB operation FILEOPEN failed soft link in path`

**See Also:**

- [Database Utilities for Loading Data into LOBs](managing-LOBs.md)

- [SQL Semantics and LOBs](SQL-semantics-and-LOBs.md)

**Parent topic:** LOB Rules and Restrictions
