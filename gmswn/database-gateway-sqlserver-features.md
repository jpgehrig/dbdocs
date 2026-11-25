After the gateway is installed and configured, you can use the gateway to access SQL Server data, pass SQL Server commands from applications to the SQL Server database, perform distributed queries, and copy data.

Topics:

- Remote Insert Rowsource

- Using the Pass-Through Feature

- Executing Stored Procedures and Functions

- CHAR Semantics

- Multi-byte Character Sets Ratio Suppression

- IPv6 Support

- Remote User-defined Function Support

- Database Compatibility Issues for SQL Server

- Known Restrictions

- Known Problems

### 2.1 Remote Insert Rowsource

A remote insert rowsource feature allows remote insert requiring local Oracle data to work through the Oracle database and Oracle Database Gateway. This functionality requires that the Oracle database and the Oracle Database Gateway to be version 12.2 or later.

By Oracle Database design, some distributed statement must be executed at the database link site. But in certain circumstances, there is data needed to execute these queries that must be fetched from the originating Oracle Database. Under homogeneous connections, the remote Oracle database would call back the source Oracle database for such data. But in heterogeneous connections, this is not viable, because this means that the Foreign Data Store would have to query call back functions, or data, that can only be provided by the Oracle instance that issued the query. In general, these kinds of statements are not something that can be supported through the Oracle Database Gateway.

The following categories of SQL statements results in a callback:

- Any DML with a sub-select, which refers to a table in Oracle database.

- Any `DELETE`, `INSERT`, `UPDATE` or "`SELECT... FOR UPDATE..."` SQL statement containing SQL functions or statements that needs to be executed at the originating Oracle database.

  These SQL functions include `USER`, `USERENV`, and `SYSDATE`; and involve the selection of data from the originating Oracle database.

- Any SQL statement that involves a table in Oracle database, and a `LONG` or `LOB` column in a remote table.

An example of a remote `INSERT` statement that can work through the remote insert rowsource feature is as follows:

    INSERT INTO gateway_table@gateway_link select * from local_table;

### 2.2 Using the Pass-Through Feature

The gateway can pass SQL Server commands or statements from the application to the SQL Server database using the `DBMS_HS_PASSTHROUGH` package.

Use the `DBMS_HS_PASSTHROUGH` package in a PL/SQL block to specify the statement to be passed to the SQL Server database, as follows:

    DECLARE
        num_rows INTEGER;
    BEGIN
        num_rows := DBMS_HS_PASSTHROUGH.EXECUTE_IMMEDIATE@MSQL('command');
    END;
    /

Where command cannot be one of the following:

- `BEGIN` `TRANSACTION`

- `COMMIT`

- `ROLLBACK`

- `SAVE`

- `SHUTDOWN`

- `RELEASE`

- `SAVEPOINT`

- `CONNECT`

- SQL Server tool commands

The `DBMS_HS_PASSTHROUGH` package supports passing bind values and executing SELECT statements.

**Note:**

TRUNCATE cannot be used in a pass-through statement.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_HS_PASSTHROUGH.md) and [Chapter 3, Features of Oracle Database Gateways,](../heter/oracle-database-gateways-features.md) of Oracle Database Heterogeneous Connectivity User's Guide for more information about the `DBMS_HS_PASSTHROUGH` package.

### 2.3 Executing Stored Procedures and Functions

Using the procedural feature, the gateway can execute stored procedures that are defined in the SQL Server database. It is not necessary to relink the gateway or define the procedure to the gateway, but the procedure's access privileges must permit access by the user that the gateway is logging in as.

Standard PL/SQL statements are used to execute a stored procedure.

The gateway supports stored procedures in three mutually exclusive modes:

- Normal mode: Have access to `IN`/`OUT` arguments only

- Return value mode: Have a return value for all stored procedures

- Resultset mode: Out values are available as last result set

### 2.4 CHAR Semantics

This feature allows the gateway to optionally run in `CHAR` Semantics mode. Rather than always describing SQL Server `CHAR` columns as `CHAR(n BYTE)`, this feature describes them as `CHAR(n CHAR)` and `VARCHAR(n CHAR)`. The concept is similar to Oracle database `CHAR` Semantics. You need to specify `HS_NLS_LENGTH_SEMANTICS=CHAR` gateway parameter to activate this option. Refer to [Initialization Parameters](database-gateway-sqlserver-initialization-parameters.md) for more detail.

### 2.5 Multi-byte Character Sets Ratio Suppression

This feature optionally suppresses the ratio expansion from SQL Server database to Oracle database involving multi-byte character set. By default, Oracle gateways assume the worst ratio to prevent data being truncated or insufficient buffer size situation. However, if you have specific knowledge of your SQL Server database and do not want the expansion to occur, you can specify `HS_KEEP_REMOTE_COLUMN_SIZE` parameter to suppress the expansion. Refer to [Initialization Parameters](database-gateway-sqlserver-initialization-parameters.md) for more detail.

### 2.6 IPv6 Support

Besides full IPv6 support between Oracle databases and the gateway, IPv6 is also supported between this gateway and SQL Server database. Refer to the `HS_FDS_CONNECT_INFO` parameter in [Initialization Parameters](database-gateway-sqlserver-initialization-parameters.md) for more detail.

### 2.7 Gateway Session IDLE Timeout

You can optionally choose to terminate long idle gateway sessions automatically with the gateway parameter `HS_IDLE_TIMEOUT`. Specifically, when a gateway session is idle for more than the specified time limit, the gateway session is terminated with any pending update rolled back. Refer to the `HS_IDLE_TIMEOUT` parameter in [Initialization Parameters](database-gateway-sqlserver-initialization-parameters.md) for more detail.

### 2.8 Remote User-defined Function Support

User-defined functions in a remote non-Oracle database can be used in SQL statements.

**See Also:**

[Oracle Database Heterogeneous Connectivity User's Guide](../heter/executing-user-defined-functions-non-oracle-database.md) for more information about executing user-defined functions on a non-Oracle database.

#### 2.8.1 Return Values and Stored Procedures

By default, all stored procedures and functions do not return a return value to the user. To enable return values, set the `HS_FDS_PROC_IS_FUNC` parameter value to `TRUE`.

**See Also:**

[Initialization Parameters](database-gateway-sqlserver-initialization-parameters.md) for information about both editing the initialization parameter file and the `HS_FDS_PROC_IS_FUNC` parameter.

**Note:**

If you set the `HS_FDS_PROC_IS_FUNC` gateway initialization parameter to `TRUE`, you must change the syntax of the procedure execute statement for all existing stored procedures.

In the following example, the employee name `JOHN SMYTHE` is passed to the SQL Server stored procedure `REVISE_SALARY`. The stored procedure retrieves the salary value from the SQL Server database to calculate a new yearly salary for `JOHN SMYTHE`. The revised salary returned in `RESULT` is used to update `EMP` in a table of an Oracle database:

    DECLARE
      INPUT VARCHAR2(15);
      RESULT NUMBER(8,2);
    BEGIN
      INPUT := 'JOHN SMYTHE';
      RESULT := REVISE_SALARY@MSQL(INPUT);
      UPDATE EMP SET SAL = RESULT WHERE ENAME =: INPUT;
    END;
    /

The procedural feature automatically converts non-Oracle data types to and from PL/SQL data types.

#### 2.8.2 Result Sets and Stored Procedures

The Oracle Database Gateway for SQL Server provides support for stored procedures which return result sets.

By default, all stored procedures and functions do not return a result set to the user. To enable result sets, set the `HS_FDS_RESULTSET_SUPPORT` parameter value to `TRUE`.

**See Also:**

[Initialization Parameters](database-gateway-sqlserver-initialization-parameters.md) for information about both editing the initialization parameter file and the `HS_FDS_RESULTSET_SUPPORT` parameter. For further information about Oracle support for result sets in non-Oracle databases see [Oracle Database Heterogeneous Connectivity User's Guide](../heter/result-set-support.md).

**Note:**

If you set the `HS_FDS_RESULTSET_SUPPORT` gateway initialization parameter to `TRUE`, then you must change the syntax of the procedure execute statement for all existing stored procedures, else errors will occur.

When accessing stored procedures with result sets through the Oracle Database Gateway for SQL Server, you will be in the sequential mode of Heterogeneous Services.

The Oracle Database Gateway for SQL Server returns the following information to Heterogeneous Services during procedure description:

- All the input arguments of the remote stored procedure

- None of the output arguments

- One out argument of type ref cursor (corresponding to the first result set returned by the stored procedure)

Client programs have to use the virtual package function `DBMS_HS_RESULT_SET.GET_NEXT_RESULT_SET` to get the ref cursor for subsequent result sets. The last result set returned is the out argument from the procedure.

The limitations of accessing result sets are the following:

- Result sets returned by a remote stored procedure have to be retrieved in the order in which they were placed on the wire

- On execution of a stored procedure, all result sets returned by a previously executed stored procedure will be closed (regardless of whether the data has been completely retrieved or not)

In the following example, the SQL Server stored procedure is executed to fetch the contents of the `emp` and `dept` tables from SQL Server:

    create procedure REFCURPROC (@arg1 varchar(255), @arg2 varchar(255) output)
    as
    select @arg2 = @arg1
    select * from EMP
    select * from DEPT
    go

This stored procedure assigns the input parameter arg1 to the output parameter arg2, opens the query `SELECT * FROM EMP` in ref cursor rc1, and opens the query `SELECT * FROM DEPT` in ref cursor rc2.

##### 2.8.2.1 OCI Program Fetching from Result Sets in Sequential Mode

The following example shows OCI program fetching from result sets in sequential mode:

    OCIEnv *ENVH;
    OCISvcCtx *SVCH;
    OCIStmt *STMH;
    OCIError *ERRH;
    OCIBind *BNDH[3];
    OraText arg1[20];
    OraText arg2[255];
    OCIResult *rset;
    OCIStmt *rstmt;
    ub2 rcode[3];
    ub2 rlens[3];
    sb2 inds[3];
    OraText *stmt = (OraText *) "begin refcurproc@MSQL(:1,:2,:3); end;";
    OraText *n_rs_stm = (OraText *)
      "begin :ret := DBMS_HS_RESULT_SET.GET_NEXT_RESULT_SET@MSQL; end;";

    /* Prepare procedure call statement */

    /* Handle Initialization code skipped */
    OCIStmtPrepare(STMH, ERRH, stmt, strlen(stmt), OCI_NTV_SYNTAX, OCI_DEFAULT);

    /* Bind procedure arguments */
    inds[0] = 0;
    strcpy((char *) arg1, "Hello World");
    rlens[0] = strlen(arg1);
    OCIBindByPos(STMH, &BNDH[0], ERRH, 1, (dvoid *) arg1, 20, SQLT_CHR,
                 (dvoid *) &(inds[0]), &(rlens[0]), &(rcode[0]), 0, (ub4 *) 0,
                 OCI_DEFAULT);

    inds[1] = -1;
    OCIBindByPos(STMH, &BNDH[1], ERRH, 1, (dvoid *) arg2, 20, SQLT_CHR,
                 (dvoid *) &(inds[1]), &(rlens[1]), &(rcode[1]), 0, (ub4 *) 0,
                 OCI_DEFAULT);

    inds[2] = 0;
    rlens[2] = 0;
    OCIDescriptorAlloc(ENVH, (dvoid **) &rset, OCI_DTYPE_RSET, 0, (dvoid **) 0);
    OCIBindByPos(STMH, &BNDH[2], ERRH, 2, (dvoid *) rset, 0, SQLT_RSET,
                 (dvoid *) &(inds[2]), &(rlens[2]), &(rcode[2]),
                 0, (ub4 *) 0, OCI_DEFAULT);

    /* Execute procedure */
    OCIStmtExecute(SVCH, STMH, ERRH, 1, 0, (CONST OCISnapshot *) 0,
                   (OCISnapshot *) 0, OCI_DEFAULT);

    /* Convert result set to statement handle */
    OCIResultSetToStmt(rset, ERRH);
    rstmt = (OCIStmt *) rset;

    /* After this the user can fetch from rstmt */
    /* Issue get_next_result_set call to get handle to next_result set */
    /* Prepare Get next result set procedure call */

    OCIStmtPrepare(STMH, ERRH, n_rs_stm, strlen(n_rs_stm), OCI_NTV_SYNTAX,
                   OCI_DEFAULT);

    /* Bind return value */
    OCIBindByPos(STMH, &BNDH[1], ERRH, 1, (dvoid *) rset, 0, SQLT_RSET,
                 (dvoid *) &(inds[1]), &(rlens[1]), &(rcode[1]),
                 0, (ub4 *) 0, OCI_DEFAULT);

    /* Execute statement to get next result set*/
    OCIStmtExecute(SVCH, STMH, ERRH, 1, 0, (CONST OCISnapshot *) 0,
                   (OCISnapshot *) 0, OCI_DEFAULT);

    /* Convert next result set to statement handle */
    OCIResultSetToStmt(rset, ERRH);
    rstmt = (OCIStmt *) rset;

    /* Now rstmt will point to the second result set returned by the
    remote stored procedure */

    /* Repeat execution of get_next_result_set to get the output arguments */

##### 2.8.2.2 PL/SQL Program Fetching from Result Sets in Sequential Mode

Assume that the table `loc_emp` is a local table exactly like the SQL Server `emp` table. The same assumption applies for `loc_dept`. The table `outargs` has columns corresponding to the `out` arguments of the SQL Server stored procedure.

    create table outargs (outarg varchar2(255), retval number);

    create or replace package rcpackage is
      type RCTYPE is ref cursor;
    end rcpackage;
    /

    declare
      rc1 rcpackage.rctype;
      rec1 loc_emp%rowtype;
      rc2 rcpackage.rctype;
      rec2 loc_dept%rowtype;
      rc3 rcpackage.rctype;
      rec3 outargs%rowtype;
      out_arg varchar2(255);

    begin

      -- Execute procedure
      out_arg := null;
      refcurproc@MSQL('Hello World', out_arg, rc1);

      -- Fetch 20 rows from the remote emp table and insert them into loc_emp
      for i in 1 .. 20 loop
        fetch rc1 into rec1;
        insert into loc_emp (rec1.empno, rec1.ename, rec1.job,
        rec1.mgr, rec1.hiredate, rec1.sal, rec1.comm, rec1.deptno);
      end loop;

      -- Close ref cursor
      close rc1;

      -- Get the next result set returned by the stored procedure
      rc2 := dbms_hs_result_set.get_next_result_set@MSQL;

      -- Fetch 5 rows from the remote dept table and insert them into loc_dept
      for i in 1 .. 5 loop
        fetch rc2 into rec2;
        insert into loc_dept values (rec2.deptno, rec2.dname, rec2.loc);
      end loop;

      --Close ref cursor
      close rc2;

      -- Get the output arguments from the remote stored procedure
      -- Since we are in sequential mode, they will be returned in the
      -- form of a result set
      rc3 := dbms_hs_result_set.get_next_result_set@MSQL;

      -- Fetch them and insert them into the outargs table
      fetch rc3 into rec3;
      insert into outargs (rec3.outarg, rec3.retval);

      -- Close ref cursor
      close rc3;

    end;
    /

### 2.9 Database Compatibility Issues for SQL Server

SQL Server and Oracle databases function differently in some areas, causing compatibility problems. The compatibility issues are described in the following links:

- Implicit Transactions (Chained Mode)

- Column Definitions

- Naming Rules

- Data Types

- Queries

- Locking

#### 2.9.1 Implicit Transactions (Chained Mode)

The gateway supports the ANSI-standard implicit transactions. SQL Server stored procedures must be written for this mode. Running implicit transactions allows the gateway to extend the Oracle two-phase commit protection to transactions updating Oracle and SQL Server databases.

#### 2.9.2 Column Definitions

By default, a SQL Server table column cannot contain null values unless `NULL` is specified in the column definition. SQL Server assumes all columns cannot contain null values unless you set a SQL Server option to override this default.

For an Oracle table, null values are allowed in a column unless `NOT NULL` is specified in the column definition.

#### 2.9.3 Naming Rules

Naming rule issues include the following:

- Rules for Naming Objects

- Case Sensitivity

##### 2.9.3.1 Rules for Naming Objects

Oracle and SQL Server use different database object naming rules. For example, the maximum number of characters allowed for each object name can be different. Also, the use of single and double quotation marks, case sensitivity, and the use of alphanumeric characters can all be different.

**See Also:**

[Oracle Database Reference](../refrn/index.md) and SQL Server documentation.

##### 2.9.3.2 Case Sensitivity

The Oracle database defaults to uppercase unless you surround identifiers with double quote characters. For example, to refer to the SQL Server table called `emp`, enter the name with double quote characters, as follows:

    SQL> SELECT * FROM "emp"@MSQL;

However, to refer to the SQL Server table called `emp` owned by Scott from an Oracle application, enter the following:

    SQL> SELECT * FROM "Scott"."emp"@MSQL;

If the SQL Server table called `emp` is owned by `SCOTT`, a table owner name in uppercase letters, you can enter the owner name without double quote characters, as follows:

    SQL> SELECT * FROM SCOTT."emp"@MSQL;

or

    SQL> SELECT * FROM scott."emp"@MSQL;

Oracle recommends that you surround all SQL Server object names with double quote characters and use the exact letter case for the object names as they appear in the SQL Server data dictionary. This convention is not required when referring to the supported Oracle data dictionary tables or views listed in [Data Dictionary](database-gateway-sqlserver-data-dictionary.md).

If existing applications cannot be changed according to these conventions, create views in Oracle to associate SQL Server names to the correct letter case. For example, to refer to the SQL Server table `emp` from an existing Oracle application by using only uppercase names, define the following view:

    SQL> CREATE VIEW EMP (EMPNO, ENAME, SAL, HIREDATE)
          AS SELECT "empno", "ename", "sal", "hiredate"
          FROM "emp"@MSQL;

With this view, the application can issue statements such as the following:

    SQL> SELECT EMPNO, ENAME FROM EMP;

Using views is a workaround solution that duplicates data dictionary information originating in the SQL Server data dictionary. You must be prepared to update the Oracle view definitions whenever the data definitions for the corresponding tables are changed in the SQL Server database.

#### 2.9.4 Data Types

Data type issues include the following:

- Binary Literal Notation

- Bind Variables With LONG Columns

- Data Type Conversion

##### 2.9.4.1 Binary Literal Notation

Oracle SQL uses hexadecimal digits surrounded by single quotes to express literal values being compared or inserted into columns defined as data type `RAW`.

This notation is not converted to syntax compatible with the SQL Server `VARBINARY` and `BINARY` data types (a `0x `followed by hexadecimal digits, surrounded by single quotes).

For example, the following statement is not supported:

    SQL> INSERT INTO BINARY_TAB@MSQL VALUES ('0xff')

Where `BINARY_TAB` contains a column of data type `VARBINARY` or `BINARY`. Use bind variables when inserting into or updating `VARBINARY` and `BINARY` data types.

##### 2.9.4.2 Bind Variables With LONG Columns

The gateway does not support using bind variables to update columns of data type `LONG`.

##### 2.9.4.3 Data Type Conversion

SQL Server does not support implicit date conversions. Such conversions must be explicit.

For example, the gateway issues an error for the following `SELECT` statement:

    SELECT DATE_COL FROM TEST@MSQL WHERE DATE_COL = "1-JAN-2004";

To avoid problems with implicit conversions, add explicit conversions, as in the following:

    SELECT DATE_COL FROM TEST@MSQL WHERE DATE_COL = TO_DATE("1-JAN-2004")

**See Also:**

[Data Type Conversion](database-gateway-sqlserver-data-type-conversion.md) for more information about restrictions on data types.

#### 2.9.5 Queries

Query issues include the following:

- Row Selection

- Empty Strings

- Empty Bind Variables

##### 2.9.5.1 Row Selection

SQL Server evaluates a query condition for all selected rows before returning any of the rows. If there is an error in the evaluation process for one or more rows, no rows are returned even though the remaining rows satisfy the condition.

Oracle evaluates the query condition row-by-row and returns a row when the evaluation is successful. Rows are returned until a row fails the evaluation.

##### 2.9.5.2 Empty Strings

Oracle processes an empty string in a SQL statement as a null value. SQL Server processes an empty string as an empty string.

When comparing an empty string the gateway passes literal empty strings to the SQL Server database without any conversion. If you intended an empty string to represent a null value, SQL Server does not process the statement that way; it uses the empty string.

You can avoid this problem by using `NULL` or `IS NULL` in the SQL statement instead of the empty string syntax, as in the following example:

    SELECT * from "emp"@MSQL where "ename" IS NULL;

To select an empty string:

- For `VARCHAR` columns, the gateway returns an empty string to the Oracle database as `NULL` value.

- For `CHAR` columns, the gateway returns the full size of the column with each character as empty space (' ').

##### 2.9.5.3 Empty Bind Variables

For `VARCHAR` bind variables, the gateway passes empty bind variables to the SQL Server database as a `NULL` value.

#### 2.9.6 Locking

The locking model for an SQL Server database differs significantly from the Oracle model. The gateway depends on the underlying SQL Server behavior, so the following possible scenarios can affect Oracle applications that access SQL Server through the gateway:

- Read access might block write access

- Write access might block read access

- Statement-level read consistency is not guaranteed

  **See Also:**

  SQL Server documentation for information about the SQL Server locking model.

### 2.10 Known Restrictions

If you encounter incompatibility problems not listed in this section or in "Known Problems", contact Oracle Support Services. The following section describes the known restrictions and includes suggestions for dealing with them when possible:

- Multiple Open Statements

- Transactional Integrity

- Transaction Capability

- COMMIT or ROLLBACK in PL/SQL Cursor Loops Closes Open Cursors

- Stored Procedures

- Pass-Through Feature

- DDL Statements

- SQL Syntax

- Functions

- SQL\*Plus COPY Command with Lowercase Table Names

- Database Links

**Note:**

If you have any questions or concerns about the restrictions, contact Oracle Support Services.

#### 2.10.1 Multiple Open Statements

Accessing SQL Server has the limitation that one open statement or cursor is allowed for each connection. If a second statement or cursor needs to open in the same transaction to access SQL Server, it requires a new connection.

Because of this limitation multiple open statements or cursors within the same transaction can lock each other because they use different connections to SQL Server.

To avoid this restriction, issue a commit, or modify the logic, or both.

#### 2.10.2 Transactional Integrity

The gateway cannot guarantee transactional integrity in the following cases:

- When a statement that is processed by the gateway causes an implicit commit in the target database

- When the target database is configured to work in Autocommit Mode

  **Note:**

  Oracle strongly recommends the following:

  - If you know that executing a particular statement causes an implicit commit in the target database, then ensure that this statement is executed in its own transaction.

The gateway sets Autocommit Mode to Off when a connection is established to the SQL Server database.

#### 2.10.3 Transaction Capability

The gateway does not support savepoints. If a distributed update transaction is under way involving the gateway, and a user attempts to create a savepoint, the following error occurs:

    ORA-02070: database dblink does not support savepoint in this context

By default, the gateway is configured as `COMMIT_CONFIRM`.

#### 2.10.4 COMMIT or ROLLBACK in PL/SQL Cursor Loops Closes Open Cursors

Any `COMMIT` or `ROLLBACK` issued in a PL/SQL cursor loop closes all open cursors, which can result in the following error:

    ORA-1002:  fetch out of sequence

To prevent this error, move the `COMMIT` or `ROLLBACK` statement outside the cursor loop.

#### 2.10.5 Stored Procedures

The Oracle transaction manager or Oracle `COMMIT` or `ROLLBACK` commands cannot contril changes issued through stored procedures that embed commits or rollbacks

When accessing stored procedures with result sets through the Oracle Database Gateway for SQL Server, you must work in the sequential mode of Heterogeneous Services.

When accessing stored procedures with multiple result sets through the Oracle Database Gateway for SQL Server, you must read all the result sets before continuing.

Output parameters of stored procedures must be initialized to an empty string.

#### 2.10.6 Pass-Through Feature

If the SQL statements being passed through the gateway result in an implicit commit at the SQL Server database, the Oracle transaction manager is unaware of the commit and an Oracle `ROLLBACK` command cannot be used to roll back the transaction.

#### 2.10.7 DDL Statements

SQL Server requires some DDL statements to be executed in their own transaction, and only one DDL statement can be executed in a given transaction.

If you use these DDL statements in a SQL Server stored procedure and you execute the stored procedure through the gateway using the procedural feature, or, if you execute the DDL statements through the gateway using the pass-through feature, an error condition might result. This is because the procedural feature and the pass-through feature of the gateway cannot guarantee that the DDL statements are executed in their own separate transaction.

The following SQL Server DDL statements can cause an error condition if you attempt to pass them with the gateway pass-through feature, or if you execute a SQL Server stored procedure that contains them:

- `ALTER DATABASE`

- `CREATE DATABASE`

- `CREATE INDEX`

- `CREATE PROCEDURE`

- `CREATE TABLE`

- `CREATE VIEW`

- `DISK INIT`

- `DROP <``object``>`

- `DUMP TRANSACTION`

- `GRANT`

- `LOAD DATABASE`

- `LOAD TRANSACTION`

- `RECONFIGURE`

- `REVOKE`

- `SELECT INTO`

- `TRUNCATE TABLE`

- `UPDATE STATISTICS`

**See Also:**

SQL Server documentation for more information about DDL statements.

#### 2.10.8 SQL Syntax

This section lists restrictions on the following SQL syntax:

- WHERE CURRENT OF Clause

- CONNECT BY Clause

- Functions in Subqueries

- Parameters in Subqueries

- Data Dictionary Table and Views in UPDATE Statement

- ROWID

- TO_DATE

- EXPLAIN PLAN Statement

**See Also:**

[Supported SQL Syntax and Functions](database-gateway-sqlserver-supported-sql-syntax-functions.md) for more information about restrictions on SQL syntax.

##### 2.10.8.1 WHERE CURRENT OF Clause

`UPDATE` and `DELETE` statements with the `WHERE CURRENT OF` clause are not supported by the gateway because they rely on the Oracle `ROWID` implementation. To update or delete a specific row through the gateway, a condition style `WHERE` clause must be used.

##### 2.10.8.2 CONNECT BY Clause

The gateway does not support the `CONNECT BY` clause in a `SELECT` statement.

##### 2.10.8.3 Functions in Subqueries

Bind variables and expressions are not supported as operands in string functions or mathematical functions, when part of subquery in an `INSERT`, `UPDATE`, or `DELETE` SQL statement.

##### 2.10.8.4 Parameters in Subqueries

Due to a limitation in SQL Server, you cannot use parameters in subqueries.

##### 2.10.8.5 Data Dictionary Table and Views in UPDATE Statement

Data dictionary tables and views in the `SET` clause of an `UPDATE` statement are not supported.

##### 2.10.8.6 ROWID

The Oracle `ROWID` implementation is not supported.

##### 2.10.8.7 TO_DATE

`TO_DATE` is a reserved word and cannot be used as a database identifier name.

##### 2.10.8.8 EXPLAIN PLAN Statement

The `EXPLAIN PLAN` statement is not supported.

#### 2.10.9 Functions

The following restrictions apply to using functions:

- Unsupported functions cannot be used in statements that refer to `LONG` columns.

- When negative numbers are used as the second parameter in a `SUBSTR` function, incorrect results are returned. This is due to incompatibility between the Oracle `SUBSTR` function and the equivalent in SQL Server.

#### 2.10.10 SQL\*Plus COPY Command with Lowercase Table Names

You need to wrap lower case table names in double quotes.

For example:

    copy from tkhouser/tkhouser@inst1 insert loc_tkhodept using select * from "tkhodept"@holink2;

#### 2.10.11 Database Links

The gateway is not multithreaded and cannot support shared database links. Each gateway session spawns a separate gateway process and connections cannot be shared.

### 2.11 Known Problems

This section describes known problems and includes suggestions for correcting them when possible. If you have any questions or concerns about the problems, contact Oracle Support Services. A current list of problems is available online. Contact your local Oracle office for information about accessing the list.

The following known problems are described in this section:

- Encrypted Format Login

- Date Arithmetic

- SQL Server IMAGE\_ TEXT and NTEXT Data Types

- String Functions

- Schema Names and PL/SQL

- Data Dictionary Views and PL/SQL

- Stored Procedures

#### 2.11.1 Encrypted Format Login

The Oracle9i database (Release 9.2 and earlier) supported an Oracle initialization parameter, `DBLINK_ENCRYPT_LOGIN`. When this parameter is set to `TRUE`, the password for the login user ID is not sent over the network.

If this parameter is set to `TRUE` in the initialization parameter file used by the Oracle9i database, you must change the setting to `FALSE`, the default setting, to allow Oracle9i to communicate with the gateway.

In the current release, the `DBLINK_ENCRYPT_LOGIN` initialization parameter is obsolete, so you do not need to check it.

#### 2.11.2 Date Arithmetic

The following SQL expressions do not function correctly with the gateway:

    date + number
    number + date
    date - number
    date1 - date2

Statements with the preceding expressions are sent to the SQL Server database without any translation. Since SQL Server does not support these date arithmetic functions, the statements return an error.

#### 2.11.3 SQL Server IMAGE, TEXT and NTEXT Data Types

The following restrictions apply when using `IMAGE`, `TEXT`, and `NTEXT` data types:

- An unsupported SQL function cannot be used in a SQL statement that accesses a column defined as SQL Server data type `IMAGE`, `TEXT`, or `NTEXT`.

- You cannot use SQL\*Plus to select data from a column defined as SQL Server data type `IMAGE`, `TEXT`, or `NTEXT` when the data is greater than 80 characters in length. Oracle recommends using Pro\*C or Oracle Call Interface to access such data in a SQL Server database.

- `IMAGE`, `TEXT`, and `NTEXT` data cannot be read through pass-through queries.

- If a SQL statement is accessing a table including an `IMAGE`, `TEXT`, or `NTEXT` column, the statement will be sent to SQL Server as two separate statements. One statement to access the `IMAGE`, `TEXT` or `NTEXT` column, and a second statement for the other columns in the original statement.

The gateway does not support the PL/SQL function `COLUMN_VALUE_LONG` of the `DBMS_SQL` package.

**See Also:**

[Supported SQL Syntax and Functions](database-gateway-sqlserver-supported-sql-syntax-functions.md) for more information about restrictions on SQL syntax.

#### 2.11.4 String Functions

If you concatenate numeric literals using the "`||`" or `CONCAT` operator when using the gateway to query a SQL Server database, the result is an arithmetic addition. For example, the result of the following statement is 18:

    SQL> SELECT 9 || 9 FROM DUAL@MSQL;

The result is 99 when using Oracle to query an Oracle database.

#### 2.11.5 Schema Names and PL/SQL

If you do not prefix a SQL Server database object with its schema name in a SQL statement within a PL/SQL block, the following error message occurs:

    ORA-6550 PLS-201 Identifier table_name must be declared.

Change the SQL statement to include the schema name of the object.

#### 2.11.6 Data Dictionary Views and PL/SQL

You cannot refer to data dictionary views in SQL statements that are inside a PL/SQL block.

#### 2.11.7 Stored Procedures

Return values of stored procedures that return result sets are incorrect.
