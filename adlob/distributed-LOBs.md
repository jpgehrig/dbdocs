## 5 Distributed LOBs

Topics:

- Working with Remote LOBs

- SQL Semantics with LOBs in Remote Tables

- Working with Remote LOBs in PL/SQL

- Using Remote Locators with OCILOB API

<!-- -->

- Working with Remote LOBs
- SQL Semantics with LOBs in Remote Tables
- Working with Remote LOBs in PL/SQL
- Using Remote Locators with OCILOB API

**Parent topic:** [Getting Started](getting-started.md)

### 5.1 Working with Remote LOBs

You can work with LOB data in remote tables is the following ways:

- Directly referencing LOB columns in remote tables (Remote LOB Columns) accessed using a database link.

- Selecting remote LOB columns into a local LOB locator variable (Remote locator)

Topics

- Working with Remote LOB Columns

- Working with Remote Locator

<!-- -->

- Working with Remote LOB Columns
- Working with Remote Locator

**Parent topic:** Distributed LOBs

#### 5.1.1 Working with Remote LOB Columns

Remote LOBs are supported in these ways:

- Create table as select or insert as select

- Functions on remote LOBs returning scalars

- Data Interface for remote LOBs

<!-- -->

- Create table as select or insert as select
- Functions on remote LOBs returning scalars
- Data Interface for remote LOBs

**Parent topic:** Working with Remote LOBs

##### 5.1.1.1 Create table as select or insert as select

Only standalone LOB columns are allowed in the select list for statements that are structured in the following manner:

    CREATE TABLE t AS SELECT * FROM table1@remote_site;
    INSERT INTO t SELECT * FROM table1@remote_site;
    UPDATE t SET lobcol = (SELECT lobcol FROM table1@remote_site);
    INSERT INTO table1@remote_site SELECT * FROM local_table;
    UPDATE table1@remote_site SET lobcol = (SELECT lobcol FROM local_table);
    DELETE FROM table1@remote_site <WHERE clause involving non_lob_columns>

**Parent topic:** Working with Remote LOB Columns

##### 5.1.1.2 Functions on remote LOBs returning scalars

SQL and PL/SQL functions having a LOB parameter and returning a scalar data type are supported. Other SQL functions and `DBMS_LOB` APIs are not supported for use with remote LOB columns. For example, the following statement is supported:

    CREATE TABLE tab AS SELECT DBMS_LOB.GETLENGTH@dbs2(clob_col) len FROM tab@dbs2;
    CREATE TABLE tab AS SELECT LENGTH(clob_col) len FROM tab@dbs2;

However, the following statement is not supported because `DBMS_LOB.SUBSTR` returns a LOB:

    CREATE TABLE tab AS SELECT DBMS_LOB.SUBSTR(clob_col) from tab@dbs2;

**Parent topic:** Working with Remote LOB Columns

##### 5.1.1.3 Data Interface for remote LOBs

You can insert a character or binary buffer into a remote `CLOB` or `BLOB`, and select a remote `CLOB` or `BLOB` into a character or binary buffer, for example, using PL/SQL:

    SELECT clobcol1, type1.blobattr INTO varchar_buf1, raw_buf2 FROM table1@remote_site;
    INSERT INTO table1@remotesite (clobcol1, type1.blobattr) VALUES varchar_buf1, raw_buf2;
    INSERT INTO table1@remotesite (lobcol) VALUES ('test');
    UPDATE table1 SET lobcol = 'xxx';

**Parent topic:** Working with Remote LOB Columns

#### 5.1.2 Working with Remote Locator

You can select a persistent LOB locator from a remote table into a local variable and this can be done in PL/SQL or in OCI. The remote columns can be of type BLOB, CLOB or NCLOB. The following SQL statement is the basis for all the examples with remote LOB locator in this chapter.

    CREATE TABLE lob_tab (c1 NUMBER, c2 CLOB);

In the following example, the table `lob_tab` (with columns `c2` of type `CLOB` and `c1` of type number) defined in the remote database is accessible using database link `db2` and a local `CLOB` variable `lob_var1`.

    SELECT c2 INTO lob_var1 FROM lob_tab@db2 WHERE c1=1;
    SELECT c2 INTO lob_var1 FROM lob_tab@db2 WHERE c1=1 for update;

In PL/SQL, the function `dbms_lob.isremote` can be used to check if a particular LOB belongs to a remote table. Similarly, in `OCI`, you can use the `OCI_ATTR_LOB_REMOTE` attribute of `OCILobLocator` to check if a particular LOB belongs to a remote table. For example,

    IF(dbms_lob.isremote(lob_var1)) THEN
    dbms_output.put_line(‘LOB locator is remote)
    ENDIF;

**See Also:**

- [ISREMOTE](../arpls/DBMS_LOB.md) Function

- [OCI_ATTR_LOB_REMOTE](../lnoci/handle-and-descriptor-attributes.md) Attribute

Topics:

- Using Local and Remote locators as bind with queries and DML on remote tables

- Restrictions when using remote LOB locators

<!-- -->

- Using Local and Remote locators as bind with queries and DML on remote tables
- Restrictions when using remote LOB locators

**Parent topic:** Working with Remote LOBs

##### 5.1.2.1 Using Local and Remote locators as bind with queries and DML on remote tables

For the Queries and DMLs (`INSERT`, `UPDATE`, `DELETE`) with bind values, the following four cases are possible. The first case involves local tables and locators and is the standard LOB functionality. The other three cases are part of the distributed LOBs functionality and have restrictions listed at the end of this section.

- Local table with local locator as bind value.

- Local table with remote locator as bind value

- Remote table with local locator as bind value

- Remote table with remote locator as bind value

Queries of the following form which use remote lob locator as bind value will be supported:

`SELECT name FROM lob_tab@db2 WHERE length(c1)=length(:lob_v1);`

In the above query, `c1` is an LOB column and `lob_v1` is a remote locator.

DMLs of the following forms using a remote LOB locator will be supported. Here, the bind values can be local or remote persistent LOB locators.

`UPDATE lob_tab@db2 SET c1=:lob_v1;`

`INSERT into lob_tab@db2 VALUES (:1, :2);`

**Note:**

DMLs with `returning` clause are not supported on remote tables for both scalar and LOB columns.

**Parent topic:** Working with Remote Locator

##### 5.1.2.2 Restrictions when using remote LOB locators

General restrictions while using remote LOB locators include the following:

- You cannot select a remote temporary LOB locator into a local variable using `SELECT` statement. For example,

  `select substr(c2, 3, 1) from lob_tab@db2 where c1=1`

  The above query returns an error.

- Remote lob functionality will not be supported for Index Organized tables (IOT). An attempt to get a locator from remote an IOT table will result in an error.

- Both local database and remote database have to be of Database release 12.2 or higher version.

- With distributed LOBs functionality, tables mentioned in the `from` clause or `where` clause should be collocated on the same database. If remote locators are used as bind variables in the `where` clauses, they should belong to the same remote database. You cannot have one locator from DB1 and another locator from DB2 to be used as bind variables.

- Collocated tables or locators use the same database link. It is possible to have 2 different DB Links pointing to the same database. In the example below, both `dblink1` and `dblink2` point to the same remote database, but perhaps with different authentication method. Oracle Database does not support such operations.

  `INSERT into tab1@dblink1 SELECT * from tab2@dblink2;`

- Bind values should be the same LOB type as the column LOB type. For example, `NCLOB` locators should be bound to `NCLOB` column and `CLOB` locators should be bound to `CLOB` column. Implicit conversion between `NCLOB` and `CLOB` types is not supported in remote LOBs case.

- DMLs (`INSERT`s/ `UPDATE`s) with Array Binds is not supported when bind involves a remote locator or if table involved is a remote table

- You cannot select a `BFILE` column from a remote table into a local variable.

**Parent topic:** Working with Remote Locator

### 5.2 SQL Semantics with LOBs in Remote Tables

Topics:

- Built-in Functions for Remote LOBs and BFILEs

- Passing Remote Locator to Built in SQL Functions

<!-- -->

- Built-in Functions for Remote LOBs and BFILEs
- Passing Remote Locator to Built in SQL Functions

**Parent topic:** Distributed LOBs

#### 5.2.1  Built-in Functions for Remote LOBs and BFILEs

Any SQL built-in functions and user-defined functions that are supported on local LOBs and BFILEs are also supported on remote LOBs and BFILEs, as long as the final value returned by nested functions is not a LOB type. This includes functions for remote persistent and temporary LOBs and for BFILEs.

Built-in SQL functions which are executed on a remote site can be part of any SQL statement, like `SELECT`, `INSERT`, `UPDATE`, and `DELETE`. For example:

    SELECT LENGTH(ad_sourcetext) FROM print_media@remote_site -- CLOB
    SELECT LENGTH(ad_fltextn) FROM print_media@remote_site;   -- NCLOB
    SELECT LENGTH(ad_composite) FROM print_media@remote_site; -- BLOB
    SELECT product_id from print_media@remote_site WHERE LENGTH(ad_sourcetext) > 3;

    UPDATE print_media@remote_site SET product_id = 2 WHERE LENGTH(ad_sourcetext) > 3;

    SELECT TO_CHAR(foo@dbs2(...)) FROM dual@dbs2;
    -- where foo@dbs2 returns a temporary LOB

The SQL functions fall under the following (not necessarily exclusive) categories:

- SQL functions that are not supported on LOBs:

  These functions are relevant only for `CLOB`s: an example is `DECODE`.

  These functions cannot be supported on remote LOBs because they are not supported on local LOBs.

- Functions taking exactly one LOB argument (all other arguments are of other data types) and not returning a LOB:

  These functions are relevant only for CLOBs, NCLOBs, and BLOBs: an example is `LENGTH` and it is supported. For example:

      SELECT LENGTH(ad_composite) FROM print_media@remote_site;
      SELECT LENGTH(ad_header.logo) FROM print_media@remote_site; -- LOB in object
      SELECT product_id from print_media@remote_site WHERE LENGTH(ad_sourcetext) > 3;

- Functions that return a LOB:

  All these functions are relevant only for CLOBs and NCLOBs. These functions may return the original LOB or produce a temporary LOB. These functions can be performed on the remote site, as long as the result returned to the local site is not a LOB.

  Functions returning a temporary LOB are: `REPLACE`, `SUBSTR`, `CONCAT`, \|\|, `TRIM`, `LTRIM`, `RTRIM`, `LOWER`, `UPPER`, `NLS_LOWER`, `NLS_UPPER`, `LPAD`, and `RPAD`.

  Functions returning the original LOB locator are: `NVL`, `DECODE`, and `CASE`. Note that even though `DECODE` and `CASE` are not supported currently to operate on LOBs, they could operate on other data types and return a LOB.

  For example, the following statements are supported:

      SELECT TO_CHAR(CONCAT(ad_sourcetext, ad_sourcetext)) FROM print_media@remote_site;
      SELECT TO_CHAR(SUBSTR(ad_fltextnfs, 1, 3)) FROM print_media@remote_site;

  But the following statements are not supported:

      SELECT CONCAT(ad_sourcetext, ad_sourcetext) FROM print_media@remote_site;
      SELECT SUBSTR(ad_sourcetext, 1, 3) FROM print_media@remote_site;

- Functions that take in more than one LOB argument:

  These are: `INSTR`, `LIKE`, `REPLACE`, `CONCAT`, \|\|, `SUBSTR`, `TRIM`, `LTRIM`, `RTRIM`, `LPAD`, and `RPAD`. All these functions are relevant only for `CLOB`s and `NCLOB`s.

  These functions are supported only if all the LOB arguments are in the same `dblink`, and the value returned is not a LOB. For example, the following is supported:

      SELECT TO_CHAR(CONCAT(ad_sourcetext, ad_sourcetext)) FROM print_media@remote_site; -- CLOB
      SELECT TO_CHAR(CONCAT(ad_fltextn, ad_fltextn)) FROM print_media@remote_site; -- NCLOB

  But the following is not supported:

      SELECT TO_CHAR(CONCAT(a.ad_sourcetext, b.ad_sourcetext)) FROM print_media@db1 a, print_media@db2 b WHERE a.product_id = b.product_id;

**Parent topic:** SQL Semantics with LOBs in Remote Tables

#### 5.2.2 Passing Remote Locator to Built in SQL Functions

You can pass a remote locator to most built-in SQL functions such as `LENGTH, INSTR, SUBSTR`, and `UPPER`. For example,

    Var lob1 CLOB;
    BEGIN
        select c2 into lob1 from lob_tab@db2 where c1=1;
    END;
    /
    select length(:lob1) from dual;

**Parent topic:** SQL Semantics with LOBs in Remote Tables

### 5.3 Working with Remote LOBs in PL/SQL

Topics:

- PL/SQL Functions for Remote LOBs and BFILEs

- Using Remote Locators with DBMS_LOB

<!-- -->

- PL/SQL Functions for Remote LOBs and BFILEs
- Using Remote Locator in PL/SQL
- Using Remote Locators with DBMS_LOB

**Parent topic:** Distributed LOBs

#### 5.3.1  PL/SQL Functions for Remote LOBs and BFILEs

Built-in and user-defined PL/SQL functions that are executed on the remote site and operate on remote LOBs and BFILEs are allowed, as long as the final value returned by nested functions is not a LOB.

The following example uses the `print_media` table described in "[Table for LOB Examples: The PM Schema print_media Table](working-with-LOBs.md)"

    SELECT product_id FROM print_media@dbs2 WHERE foo@dbs2(ad_sourcetext, 'aa') > 0;
    -- foo is a user-define function returning a NUMBER

    DELETE FROM print_media@dbs2 WHERE DBMS_LOB.GETLENGTH@dbs2(ad_graphic) = 0;

- Restrictions on Remote User-Defined Functions
- Remote Functions in PL/SQL, OCI, and JDBC

**Parent topic:** Working with Remote LOBs in PL/SQL

##### 5.3.1.1 Restrictions on Remote User-Defined Functions

- The restrictions that apply to SQL functions apply here also.

  **See Also:**

  Built-in Functions for Remote LOBs and BFILEs

- A function in one `dblink` cannot operate on LOB data in another dblink.For example, the following statement is not supported:

      SELECT a.product_id FROM print_media@dbs1 a, print_media@dbs2 b WHERE
         CONTAINS@dbs1(b.ad_sourcetext, 'aa') > 0;

- One query block cannot contain tables and functions at different `dblink`s. For example, the following statement is not supported:

      SELECT a.product_id FROM print_media@dbs2 a, print_media@dbs3 b
          WHERE CONTAINS@dbs2(a.ad_sourcetext, 'aa') > 0 AND
          foo@dbs3(b.ad_sourcetext) > 0;
      --  foo is a user-defined function in dbs3

- There is no support for performing remote LOB operations (that is, `DBMS_LOB`) from within PL/SQL, other than issuing SQL statements from PL/SQL.

**Parent topic:** PL/SQL Functions for Remote LOBs and BFILEs

##### 5.3.1.2 Remote Functions in PL/SQL, OCI, and JDBC

All the SQL statements listed in Restrictions on Remote User-Defined Functions work the same if they are executed from inside PL/SQL, OCI, and JDBC. No additional functionality is provided.

**Parent topic:** PL/SQL Functions for Remote LOBs and BFILEs

#### 5.3.2 Using Remote Locator in PL/SQL

A remote locator can be passed as a parameter to built in PL/SQL functions like `LENGTH`, `INSTR`, `SUBSTR`, `UPPER` and so on which accepts LOB as input. For example,

    DECLARE
    substr_data varchar2(4000);
    remote_loc CLOB;
    BEGIN
    SELECT c2 into remote_loc
    FROM lob_tab@db2 WHERE c1=1;
    substr_data := substr(remote_loc, position, length)
    END;

**Parent topic:** Working with Remote LOBs in PL/SQL

#### 5.3.3 Using Remote Locators with `DBMS_LOB`

All `DBMS_LOB` APIs other than the APIs targeted for BFILEs support operations on remote LOB locators.

The following example shows how to pass remote locator as input to `dbms_lob` operations.

    DECLARE
      lob CLOB;
      buf VARCHAR2(120) := 'TST';
      amt NUMBER(2);
      len NUMBER(2);
    BEGIN
      amt :=30;
      select c2 into lob from lob_tab@db2 where c1=3 for update;
      dbms_lob.write(lob, amt, 1, buf);
      amt :=30;
      dbms_lob.read(lob, amt, 1, buf);
      len := dbms_lob.getlength(lob);
      dbms_output.put_line(buf);
      dbms_output.put_line(amt);
      dbms_output.put_line('get length output = ' || len);
    END;
    /

Topics:

- Restrictions on Using Remote Locators with DBMS_LOB

<!-- -->

- Restrictions on Using Remote Locators with DBMS_LOB

**Parent topic:** Working with Remote LOBs in PL/SQL

##### 5.3.3.1 Restrictions on Using Remote Locators with `DBMS_LOB`

All the APIs that accepts two LOB locators must have both LOBs collocated at one database.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md) to view the complete list of `DBMS_LOB` APIs.

**Parent topic:** Using Remote Locators with DBMS_LOB

### 5.4 Using Remote Locators with `OCILOB` API

All `OCILOB` APIs (except APIs meant for BFILEs) support operations on remote `LOB` locators.

**Note:**

All the APIs that accept two locators must obtain both the LOB locators through the same database link.

The following list of `OCILOB` functions will give an error when a remote `LOB` locator is passed to them:

- `OCILobAssign`

- `OCILobLocatorAssign`

- `OCILobArrayRead()`

- `OCILobArrayWrite()`

- `OCILobLoadFromFile2()`

The following example shows how to pass a remote locator to `OCILOB` API.

    void select_read_remote_lob()
    {
      text *select_sql = (text *)"SELECT c2 lob_tab@dbs1 where c1=1";
      ub4 amtp = 10;
      ub4 nbytes = 0;
      ub4 loblen=0;
      OCILobLocator * one_lob;
      text strbuf[40];

     /* initialize single locator */
     OCIDescriptorAlloc(envhp, (dvoid **) &one_lob,
                     (ub4) OCI_DTYPE_LOB,
                     (size_t) 0, (dvoid **) 0)

     OCIStmtPrepare(stmthp, errhp, select_sql, (ub4)strlen((char*)select_sql),
                     (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT);

     OCIDefineByPos(stmthp, &defp, errhp, (ub4) 1,
                         (dvoid *) &one_lob,
                         (sb4) -1,
                         (ub2) SQLT_CLOB,
                         (dvoid *) 0, (ub2 *) 0,
                         (ub2 *) 0, (ub4) OCI_DEFAULT));

     /* fetch the remote locator into the local variable one_lob */
     OCIStmtExecute(svchp, stmthp, errhp, 1, 0, (OCISnapshot *)0,
                     (OCISnapshot *)0, OCI_DEFAULT);

     /* Get the length of the remote LOB */
     OCILobGetLength(svchp, errhp,
                    (OCILobLocator *) one_lob, (ub4 *)&loblen)

     printf("LOB length = %d\n", loblen);

     memset((void*)strbuf, (int)'\0', (size_t)40);

     / * Read the data from the remote LOB */
     OCILobRead(svchp, errhp, one_lob, &amtp,
                    (ub4) 1, (dvoid *) strbuf, (ub4)& nbytes, (dvoid *)0,
                    (OCICallbackLobRead) 0,
                    (ub2) 0, (ub1) SQLCS_IMPLICIT));
     printf("LOB content = %s\n", strbuf);

    }

**See Also:**

OCI Programmer’s Guide, for the complete list of `OCILOB` APIs

**Parent topic:** Distributed LOBs
