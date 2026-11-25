## 17  Migrating Columns from LONGs to LOBs

There are techniques for migrating tables that use `LONG` data types to LOB data types.

Topics:

- Benefits of Migrating LONG Columns to LOB Columns

- Preconditions for Migrating LONG Columns to LOB Columns

- Determining how to Optimize the Application Using utldtree.sql

- Converting Tables from LONG to LOB Data Types

- Migrating Applications from LONGs to LOBs

  **See Also:**

  For support for LOB data types in various programming environments:

  - [SQL Semantics and LOBs](SQL-semantics-and-LOBs.md)

  - [PL/SQL Semantics for LOBs](PLSQL-semantics-for-LOBs.md)

  - [Data Interface for Persistent LOBs](data-interface-for-persistent-LOBs.md)

<!-- -->

- Benefits of Migrating LONG Columns to LOB Columns
- Preconditions for Migrating LONG Columns to LOB Columns
- Determining how to Optimize the Application Using utldtree.sql
- Converting Tables from LONG to LOB Data Types
- Migrating Applications from LONGs to LOBs

**Parent topic:** [LOB Administration](LOB-administration.md)

### 17.1 Benefits of Migrating LONG Columns to LOB Columns

There are many benefits to migrating table columns from `LONG` data types to LOB data types.

**Note:**

You can use various techniques to do either of the following:

- Convert columns of type `LONG` to either `CLOB` or `NCLOB` columns

- Convert columns of type `LONG` `RAW` to `BLOB` type columns

Unless otherwise noted, discussions in this chapter regarding LONG to LOB conversions apply to both of these data type conversions.

These items compare the semantics of `LONG` and LOB data types in various application development scenarios:

- The number of `LONG` type columns is limited. Any given table can have a maximum of only one `LONG` type column. The number of LOB type columns in a table is not limited.

**Parent topic:** Migrating Columns from LONGs to LOBs

### 17.2 Preconditions for Migrating LONG Columns to LOB Columns

Various preconditions must be met before converting a `LONG` column to a LOB column.

- Dropping a Domain Index on a LONG Column Before Converting to a LOB
- Preventing Generation of Redo Space on Tables Converted to LOB Data Types

**See Also:**

"Migrating Applications from LONGs to LOBs" before converting your table to determine whether any limitations on LOB columns prevent you from converting to LOBs.

**Parent topic:** Migrating Columns from LONGs to LOBs

#### 17.2.1 Dropping a Domain Index on a LONG Column Before Converting to a LOB

Any domain index on a `LONG` column must be dropped before converting the `LONG` column to LOB column.

**See Also:**

Rebuilding Indexes on Columns Converted from LONG to LOB Data Types

**Parent topic:** Preconditions for Migrating LONG Columns to LOB Columns

#### 17.2.2 Preventing Generation of Redo Space on Tables Converted to LOB Data Types

Generation of redo space can cause performance problems during the process of converting `LONG` columns. Redo changes for the table are logged during the conversion process only if the table has `LOGGING` on.

Redo changes for the column being converted from `LONG` to LOB are logged only if the storage characteristics of the LOB column indicate `LOGGING`. The logging setting (`LOGGING` or `NOLOGGING`) for the LOB column is inherited from the tablespace in which the LOB is created.

To prevent generation of redo space during migration, do the following before migrating your table (syntax is in BNF):

1.  `ALTER TABLE Long_tab NOLOGGING;`
2.  `ALTER TABLE Long_tab MODIFY (long_col CLOB [DEFAULT <``default_val``>]) LOB (long_col) STORE AS (NOCACHE NOLOGGING);`
    Note that you must also specify `NOCACHE` when you specify `NOLOGGING` in the `STORE AS `clause.
3.  `ALTER TABLE Long_tab MODIFY LOB (long_col) (CACHE);`
4.  `ALTER TABLE Long_tab LOGGING;`
5.  Make a backup of the tablespaces containing the table and the LOB column.

**Parent topic:** Preconditions for Migrating LONG Columns to LOB Columns

### 17.3 Determining how to Optimize the Application Using utldtree.sql

When you migrate your table from `LONG` to LOB column types, in PL/SQL, certain parts of your application may require rewriting. You can use the utility, `rdbms/admin/utldtree.sql`, to determine which parts.

The `utldtree.sql` utility enables you to recursively see all objects that are dependent on a given object. For example, you can see all objects which depend on a table with a `LONG` column. You can only see objects for which you have permission.

Instructions on how to use `utldtree.sql` are documented in the file itself. Also, `utldtree.sql` is only needed for PL/SQL. For SQL and OCI, you have no requirement to change your applications.

**Parent topic:** Migrating Columns from LONGs to LOBs

### 17.4 Converting Tables from LONG to LOB Data Types

There are various issues and techniques for migrating existing tables from `LONG` to LOB data types.

Topics:

- Migration Issues

- Using ALTER TABLE to Convert LONG Columns to LOB Columns

- Copying a LONG to a LOB Column Using the TO_LOB Operator

- Online Redefinition of Tables with LONG Columns where high availability is critical

- Migrating LOBs with Data Pump when you can convert using this utility

<!-- -->

- Migration Issues
- Using ALTER TABLE to Convert LONG Columns to LOB Columns
- Copying a LONG to a LOB Column Using the TO_LOB Operator
- Online Redefinition of Tables with LONG Columns
- Migrating LOBs with Data Pump
  Oracle Data Pump can either recreate tables as they are in your source database, or recreate LOB columns as SecureFile LOBs.

**Parent topic:** Migrating Columns from LONGs to LOBs

#### 17.4.1 Migration Issues

General issues concerning migration include the following:

- All constraints of your previous `LONG` columns are maintained for the new LOB columns. The only constraint allowed on `LONG` columns are `NULL` and `NOT` `NULL`. To alter the constraints for these columns, or alter any other columns or properties of this table, you have to do so in a subsequent `ALTER` `TABLE` statement.

- If you do not specify a default value, then the default value for the `LONG` column becomes the default value of the LOB column.

- Most of the existing triggers on your table are still usable, however `UPDATE OF` triggers can cause issues.

**See Also:**

Migrating Applications from LONGs to LOBs

**Parent topic:** Converting Tables from LONG to LOB Data Types

#### 17.4.2 Using ALTER TABLE to Convert LONG Columns to LOB Columns

You can use the `ALTER` `TABLE` statement in SQL to convert a `LONG` column to a LOB column.

To do so, use the following syntax:

    ALTER TABLE [<schema>.]<table_name>
       MODIFY ( <long_column_name> { CLOB | BLOB | NCLOB }
      [DEFAULT <default_value>]) [LOB_storage_clause];

For example, if you had a table that was created as follows:

    CREATE TABLE Long_tab (id NUMBER, long_col LONG);

then you can change the column `long_col` in table `Long_tab` to data type `CLOB` using following `ALTER` `TABLE` statement:

    ALTER TABLE Long_tab MODIFY ( long_col CLOB );

**Note:**

The `ALTER` `TABLE` statement copies the contents of the table into a new space, and frees the old space at the end of the operation. This temporarily doubles the space requirements.

Note that when using the `ALTER` `TABLE` statement to convert a `LONG` column to a LOB column, only the following options are allowed:

- `DEFAULT` which enables you to specify a default value for the LOB column.

- The `LOB_storage_clause`, which enables you to specify the LOB storage characteristics for the converted column, can be specified in the `MODIFY` clause.

Other `ALTER` `TABLE` options are not allowed when converting a `LONG` column to a LOB type column.

**Parent topic:** Converting Tables from LONG to LOB Data Types

#### 17.4.3 Copying a LONG to a LOB Column Using the TO_LOB Operator

If you do not want to use `ALTER` `TABLE`, then you can use the `TO_LOB` operator on a `LONG` column to copy it to a LOB column. You can use the `CREATE` `TABLE` `AS` `SELECT` statement or the `INSERT` `AS` `SELECT` statement with the `TO_LOB` operator to copy data from a `LONG` column to a `CLOB` or `NCLOB` column, or from a `LONG` `RAW` column to a `BLOB` column. For example, if you have a table with a `LONG` column that was created as follows:

    CREATE TABLE Long_tab (id NUMBER, long_col LONG);

then you can do the following to copy the column to a LOB column:

    CREATE TABLE Lob_tab (id NUMBER, clob_col CLOB);
    INSERT INTO Lob_tab SELECT id, TO_LOB(long_col) FROM long_tab;
    COMMIT;

If the `INSERT` returns an error (because of lack of undo space), then you can incrementally migrate `LONG` data to the LOB column using the `WHERE` clause. After you ensure that the data is accurately copied, you can drop the original table and create a view or synonym for the new table using one of the following sequences:

    DROP TABLE Long_tab;
    CREATE VIEW Long_tab (id, long_col) AS SELECT * from Lob_tab;

or

    DROP TABLE Long_tab;
    CREATE SYNONYM Long_tab FOR Lob_tab;

This series of operations is equivalent to changing the data type of the column `Long_col` of table `Long_tab` from `LONG` to `CLOB`. With this technique, you have to re-create any constraints, triggers, grants and indexes on the new table.

Use of the `TO_LOB` operator is subject to the following limitations:

- You can use `TO_LOB` to copy data to a LOB column, but not to a LOB attribute of an object type.

- You cannot use `TO_LOB` with a remote table. For example, the following statements do not work:

      INSERT INTO tb1@dblink (lob_col) SELECT TO_LOB(long_col) FROM tb2;
      INSERT INTO tb1 (lob_col) SELECT TO_LOB(long_col) FROM tb2@dblink;
      CREATE TABLE tb1 AS SELECT TO_LOB(long_col) FROM tb2@dblink;

- The `TO_LOB` operator cannot be used in the `CREATE` `TABLE` `AS` `SELECT` statement to convert a `LONG` or `LONG` `RAW` column to a LOB column when creating an index organized table.

  To work around this limitation, create the index organized table, and then do an `INSERT` `AS` `SELECT` of the `LONG` or `LONG` `RAW` column using the `TO_LOB` operator.

- You cannot use `TO_LOB` inside any PL/SQL block.

**Parent topic:** Converting Tables from LONG to LOB Data Types

#### 17.4.4 Online Redefinition of Tables with LONG Columns

Tables with `LONG` and `LONG` `RAW` columns can be migrated using online table redefinition. This technique is suitable for migrating LONG columns in database tables where high availability is critical.

To use this technique, you must convert `LONG` columns to LOB types during the redefinition process as follows:

- Any `LONG` column must be converted to a `CLOB` or `NCLOB` column.

- Any `LONG` `RAW` column must be converted to a `BLOB` column.

This conversion is performed using the `TO_LOB() `operator in the column mapping of the `DBMS_REDEFINITION.START_REDEF_TABLE()` procedure.

**Note:**

You cannot perform online redefinition of tables with `LONG` or `LONG` `RAW` columns unless you convert the columns to LOB types as described in this section.

General tasks involved in the online redefinition process are given in the following list. Issues specific to converting `LONG` and `LONG` `RAW` columns are called out. See the related documentation referenced at the end of this section for additional details on the online redefinition process that are not described here.

- Create an empty interim table. This table holds the migrated data when the redefinition process is done. In the interim table:

  - Define a `CLOB` or `NCLOB` column for each `LONG` column in the original table that you are migrating.

  - Define a `BLOB` column for each `LONG` `RAW` column in the original table that you are migrating.

- Start the redefinition process. To do so, call `DBMS_REDEFINITION.START_REDEF_TABLE` and pass the column mapping using the `TO_LOB` operator as follows:

      DBMS_REDEFINITION.START_REDEF_TABLE(
          'schema_name',
          'original_table',
          'interim_table',
          'TO_LOB(long_col_name) lob_col_name',
          'options_flag',
          'orderby_cols');

  where `long_col_name` is the name of the `LONG` or `LONG` `RAW` column that you are converting in the original table and `lob_col_name` is the name of the LOB column in the interim table. This LOB column holds the converted data.

- Call the `DBMS_REDEFINITION.COPY_TABLE_DEPENDENTS` procedure as described in the related documentation.

- Call the `DBMS_REDEFINITION.FINISH_REDEF_TABLE` procedure as described in the related documentation.

##### Parallel Online Redefinition

On a system with sufficient resources for parallel execution, redefinition of a `LONG` column to a LOB column can be executed in parallel under the following conditions:

In the case where the destination table is non-partitioned:

- The segment used to store the LOB column in the destination table belongs to a locally managed tablespace with Automatic Segment Space Management (ASSM) enabled, which is now the default.

- There is a simple mapping from one `LONG` column to one LOB column, and the destination table has only one LOB column.

In the case where the destination table is partitioned, the normal methods for parallel execution for partitioning apply. When the destination table is partitioned, then online redefinition is executed in parallel.

##### Example of Online Redefinition

The following example demonstrates online redefinition with LOB columns.

    REM Grant privileges required for online redefinition.
    GRANT execute ON DBMS_REDEFINITION TO pm;
    GRANT ALTER ANY TABLE TO pm;
    GRANT DROP ANY TABLE TO pm;
    GRANT LOCK ANY TABLE TO pm;
    GRANT CREATE ANY TABLE TO pm;
    GRANT SELECT ANY TABLE TO pm;

    REM Privileges required to perform cloning of dependent objects.
    GRANT CREATE ANY TRIGGER TO pm;
    GRANT CREATE ANY INDEX TO pm;

    connect pm/passwd

    drop table cust;
    create table cust(c_id   number primary key,
                      c_zip  number,
                      c_name varchar(30) default null,
                      c_long long
                      );
    insert into cust values(1, 94065, 'hhh', 'ttt');

    -- Creating Interim Table
    -- There is no requirement to specify constraints because they are
    -- copied over from the original table.
    create table cust_int(c_id   number not null,
                      c_zip  number,
                      c_name varchar(30) default null,
                      c_long clob
                      );

    declare
     col_mapping varchar2(1000);
    BEGIN
    --  map all the columns in the interim table to the original table
     col_mapping :=
                   'c_id             c_id  , '||
                   'c_zip            c_zip , '||
                   'c_name           c_name, '||
                   'to_lob(c_long)   c_long';

    dbms_redefinition.start_redef_table('pm', 'cust', 'cust_int', col_mapping);
    END;
    /

    declare
     error_count pls_integer := 0;
    BEGIN
      dbms_redefinition.copy_table_dependents('pm', 'cust', 'cust_int',
                                              1, true, true, true, false,
                                              error_count);

      dbms_output.put_line('errors := ' || to_char(error_count));
    END;
    /

    exec  dbms_redefinition.finish_redef_table('pm', 'cust', 'cust_int');

    -- Drop the interim table
    drop table cust_int;

    desc cust;

    -- The following insert statement fails. This illustrates
    -- that the primary key constraint on the c_id column is
    -- preserved after migration.

    insert into cust values(1, 94065, 'hhh', 'ttt');

    select * from cust;

**Note:**

Related documentation provides additional details on the redefinition process:

- [Oracle Database Administrator's Guide ](../admin/managing-tables.md)gives detailed procedures and examples of redefining tables online.

- [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_REDEFINITION.md)includes information on syntax and other details on usage of procedures in the `DBMS_REDEFINITION` package.

**Parent topic:** Converting Tables from LONG to LOB Data Types

#### 17.4.5 Migrating LOBs with Data Pump

Oracle Data Pump can either recreate tables as they are in your source database, or recreate LOB columns as SecureFile LOBs.

When Oracle Data Pump recreates tables, by default, it recreates them as they existed in the source database. Therefore, if a LOB column was a BasicFiles LOB in the source database, Oracle Data Pump attempts to recreate it as a BasicFile LOB in the imported database. However, you can force creation of LOBs as SecureFile LOBs in the recreated tables by using a `TRANSFORM` parameter for the command line, or by using a `LOB_STORAGE` parameter for the `DBMS_DATAPUMP` and `DBMS_METADATA` packages.

Example:

    impdp system/manager directory=dpump_dir schemas=lobuser dumpfile=lobuser.dmp
          transform=lob_storage:securefile

**Note:**

The transform name is not valid in transportable import.

**See Also:**

[TRANSFORM](../sutil/datapump-import-utility.md) for using TRANSFORM parameter to convert to SecureFile LOBs

##### Restrictions on Migrating LOBs with Data Pump

You can't use SecureFile LOBs in non-ASSM tablespace. If the source database contains LOB columns in a tablespace that does not support ASSM, then you'll see an error message when you use Oracle Data Dump to recreate the tables using the securefile clause for LOB columns.

To import non-ASSM tables with LOB columns, run another import for these tables without using `TRANSFORM=LOB_STORAGE:SECUREFILE`.

Example:

    impdp system/manager directory=dpump_dir schemas=lobuser dumpfile=lobuser.dmp

**Parent topic:** Converting Tables from LONG to LOB Data Types

### 17.5 Migrating Applications from LONGs to LOBs

There are differences between `LONG` and LOB data types that may impact your application migration plans or require you to modify your application.

- About Migrating Applications from Longs to LOBs
- LOB Columns Are Not Allowed in Clustered Tables
- LOB Columns Are Not Allowed in AFTER UPDATE OF Triggers
- Rebuilding Indexes on Columns Converted from LONG to LOB Data Types
- Empty LOBs Compared to NULL and Zero Length LONGs
- Overloading with Anchored Types
- Some Implicit Conversions Are Not Supported for LOB Data Types

**Parent topic:** Migrating Columns from LONGs to LOBs

#### 17.5.1 About Migrating Applications from Longs to LOBs

Most APIs that work with `LONG` data types in the PL/SQL and OCI environments are enhanced to also work with LOB data types.

These APIs are collectively referred to as the data interface for persistent LOBs, or simply the data interface. Among other things, the data interface provides the following benefits:

- Changes needed are minimal in PL/SQL and OCI applications that use tables with columns converted from `LONG` to LOB data types.

- You can work with LOB data types in your application without having to deal with LOB locators.

  **See Also:**

  - [Data Interface for Persistent LOBs](data-interface-for-persistent-LOBs.md) for details on PL/SQL and OCI APIs included in the data interface.

  - [SQL Semantics and LOBs](SQL-semantics-and-LOBs.md) for details on SQL syntax supported for LOB data types.

  - [PL/SQL Semantics for LOBs](PLSQL-semantics-for-LOBs.md) for details on PL/SQL syntax supported for LOB data types.

**Parent topic:** Migrating Applications from LONGs to LOBs

#### 17.5.2 LOB Columns Are Not Allowed in Clustered Tables

LOB columns are not allowed in clustered tables, whereas `LONG`s are allowed. If a table is a part of a cluster, then any `LONG` or `LONG` `RAW` column cannot be changed to a LOB column.

**Parent topic:** Migrating Applications from LONGs to LOBs

#### 17.5.3 LOB Columns Are Not Allowed in AFTER UPDATE OF Triggers

You cannot have LOB columns in the `UPDATE` `OF` list of an `AFTER UPDATE` `OF` trigger. `LONG` columns are allowed in such triggers. For example, the following create trigger statement is not valid:

    CREATE TABLE t(lobcol CLOB);
    CREATE TRIGGER trig AFTER UPDATE OF lobcol ON t ...;

All other triggers work on LOB columns.

**Parent topic:** Migrating Applications from LONGs to LOBs

#### 17.5.4 Rebuilding Indexes on Columns Converted from LONG to LOB Data Types

Indexes on any column of the table being migrated must be manually rebuilt after converting any `LONG` column to a LOB column. This includes function-based indexes.

Any function-based index on a `LONG` column is unusable during the conversion process and must be rebuilt after converting. Application code that uses function-based indexing should work without modification after converting.

Note that, any domain indexes on a `LONG` column must be dropped before converting the `LONG` column to LOB column. You can rebuild the domain index after converting.

To rebuild an index after converting, use the following steps:

1.  Select the index from your original table as follows:
        SELECT index_name FROM user_indexes WHERE table_name='LONG_TAB';

    **Note:**

    The table name must be capitalized in this query.
2.  For the selected index, use the command:
        ALTER INDEX <index> REBUILD

**Parent topic:** Migrating Applications from LONGs to LOBs

#### 17.5.5 Empty LOBs Compared to NULL and Zero Length LONGs

A LOB column can hold an empty LOB. An empty LOB is a LOB locator that is fully initialized, but not populated with data. Because `LONG` data types do not use locators, the empty concept does not apply to `LONG` data types.

Both LOB column values and `LONG` column values, inserted with an initial value of `NULL` or an empty string literal, have a `NULL` value. Therefore, application code that uses `NULL` or zero-length values in a `LONG` column functions exactly the same after you convert the column to a LOB type column.

In contrast, a LOB initialized to empty has a non-`NULL` value as illustrated in the following example:

    CREATE TABLE long_tab(id NUMBER, long_col LONG);
    CREATE TABLE lob_tab(id NUMBER, lob_col CLOB);

    INSERT INTO long_tab values(1, NULL);

    REM     A zero length string inserts a NULL into the LONG column:
    INSERT INTO long_tab values(1, '');

    INSERT INTO lob_tab values(1, NULL);

    REM     A zero length string inserts a NULL into the LOB column:
    INSERT INTO lob_tab values(1, '');

    REM     Inserting an empty LOB inserts a non-NULL value:
    INSERT INTO lob_tab values(1, empty_clob());

    DROP TABLE long_tab;
    DROP TABLE lob_tab;

**Parent topic:** Migrating Applications from LONGs to LOBs

#### 17.5.6 Overloading with Anchored Types

For applications using anchored types, some overloaded variables resolve to different targets during the conversion to LOBs. For example, given the procedure `p` overloaded with specifications 1 and 2:

    procedure p(l long) is ...;       -- (specification 1)
    procedure p(c clob) is ...;       -- (specification 2)

and the procedure call:

    declare
         var  longtab.longcol%type;
       BEGIN
         ...
       p(var);
         ...
    END;

Prior to migrating from `LONG` to LOB columns, this call would resolve to specification 1. Once `longtab` is migrated to LOB columns this call resolves to specification 2. Note that this would also be true if the parameter type in specification 1 were a `CHAR`, `VARCHAR2`, `RAW`, `LONG` `RAW`.

If you have migrated you tables from `LONG` columns to LOB columns, then you must manually examine your applications and determine whether overloaded procedures must be changed.

Some applications that included overloaded procedures with LOB arguments before migrating may still break. This includes applications that do not use `LONG` anchored types. For example, given the following specifications (1 and 2) and procedure call for procedure `p`:

    procedure p(n number) is ...;       -- (1)
    procedure p(c clob) is ...;         -- (2)

    p('123');                 -- procedure call

Before migrating, the only conversion allowed was `CHAR` to `NUMBER`, so specification 1 would be chosen. After migrating, both conversions are allowed, so the call is ambiguous and raises an overloading error.

**Parent topic:** Migrating Applications from LONGs to LOBs

#### 17.5.7 Some Implicit Conversions Are Not Supported for LOB Data Types

PL/SQL permits implicit conversion from `NUMBER`, `DATE`, `ROW_ID`, `BINARY_INTEGER`, and `PLS_INTEGER` data types to a `LONG`; however, implicit conversion from these data types to a LOB is not allowed.

If your application uses these implicit conversions, then you have to explicitly convert these types using the `TO_CHAR` operator for character data or the `TO_RAW` operator for binary data. For example, if your application has an assignment operation such as:

    number_var := long_var;  -- The RHS is a LOB variable after converting.

then you must modify your code as follows:

    number_var := TO_CHAR(long_var);
    -- Assuming that long_var is of type CLOB after conversion

The following conversions are not supported for LOB types:

- `BLOB` to `VARCHAR2`, `CHAR`, or `LONG`

- `CLOB` to `RAW` or `LONG` `RAW`

This applies to all operations where implicit conversion takes place. For example if you have a `SELECT` statement in your application as follows:

    SELECT long_raw_column INTO my_varchar2 VARIABLE FROM my_table

and `long_raw_column` is a `BLOB` after converting your table, then the `SELECT` statement produces an error. To make this conversion work, you must use the `TO_RAW` operator to explicitly convert the `BLOB` to a `RAW` as follows:

    SELECT TO_RAW(long_raw_column) INTO my_varchar2 VARIABLE FROM my_table

The same holds for selecting a `CLOB` into a `RAW` variable, or for assignments of `CLOB` to `RAW` and `BLOB` to `VARCHAR2`.

**Parent topic:** Migrating Applications from LONGs to LOBs
