After the gateway is installed and configured, you can use the gateway to access Teradata data, pass Teradata commands from applications to the Teradata database, perform distributed queries, and copy data.

Topics:

- Remote Insert Rowsource

- Using the Pass-Through Feature

- Executing Stored Procedures and Functions

- CHAR Semantics

- Multi-byte Character Sets Ratio Suppression

- IPv6 Support

- Gateway Session IDLE Timeout

- Database Compatibility Issues for Teradata

- Known Restrictions

- Known Problems

### Remote Insert Rowsource

A remote insert rowsource feature allows remote insert requiring local Oracle data to work through the Oracle database and Oracle Database Gateway. This functionality requires that the Oracle database and the Oracle Database Gateway to be version 12.2 or later.

By Oracle Database design, some distributed statement must be executed at the database link site. But in certain circumstances, there is data needed to execute these queries that must be fetched from the originating Oracle Database. Under homogeneous connections, the remote Oracle database would call back the source Oracle database for such data. But in heterogeneous connections, this is not viable, because this means that the Foreign Data Store would have to query call back functions, or data, that can only be provided by the Oracle instance that issued the query. In general, these kinds of statements are not something that can be supported through the Oracle Database Gateway.

The following categories of SQL statements results in a callback:

- Any DML with a sub-select, which refers to a table in Oracle database.

- Any `DELETE`, `INSERT`, `UPDATE` or "`SELECT... FOR UPDATE..."` SQL statement containing SQL functions or statements that needs to be executed at the originating Oracle database.

  These SQL functions include `USER`, `USERENV`, and `SYSDATE`; and involve the selection of data from the originating Oracle database.

- Any SQL statement that involves a table in Oracle database, and a `LONG` or `LOB` column in a remote table.

An example of a remote `INSERT` statement that can work through the remote insert rowsource feature is as follows:

    INSERT INTO gateway_table@gateway_link select * from local_table;

### Using the Pass-Through Feature

The gateway can pass Teradata commands or statements from the application directly to the Teradata database using the `DBMS_HS_PASSTHROUGH` package.

Use the `DBMS_HS_PASSTHROUGH` package in a PL/SQL block to specify the statement to be passed to the Teradata database, as follows:

    DECLARE
        num_rows INTEGER;
    BEGIN
        num_rows := DBMS_HS_PASSTHROUGH.EXECUTE_IMMEDIATE@TERA('command');
    END;
    /

Where `command` cannot be one of the following:

- `BEGIN TRANSACTION`

- `BT`

- `COMMIT`

- `END TRANSACTION`

- `ET`

- `ROLLBACK`

The `DBMS_HS_PASSTHROUGH` package supports passing bind values and executing `SELECT` statements.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_HS_PASSTHROUGH.md) and [Chapter 3, Features of Oracle Database Gateways,](../heter/oracle-database-gateways-features.md) of Oracle Database Heterogeneous Connectivity User's Guide for more information about the `DBMS_HS_PASSTHROUGH` package.

### Executing Stored Procedures and Functions

Using the procedural feature, the gateway can execute stored procedures that are defined in the Teradata database. It is not necessary to relink the gateway or define the procedure to the gateway, but the procedure's access privileges must permit access by the gateway.

Standard PL/SQL statements are used to execute a stored procedure.

The gateway supports stored procedures in three mutually exclusive modes:

- Normal mode: Have access to `IN`/`OUT` arguments only

- Return value mode: Have a return value for all stored procedures

- Resultset mode: Out values are available as last result set

#### Return Values and Stored Procedures

By default, all stored procedures and functions do not return a return value to the user. To enable return values, set the `HS_FDS_PROC_IS_FUNC` parameter in the initialization parameter file.

**See Also:**

[Initialization Parameters](database-gateway-teradata-initialization-parameters.md) for information about both editing the initialization parameter file and the `HS_FDS_PROC_IS_FUNC` parameter.

**Note:**

If you set the `HS_FDS_PROC_IS_FUNC` gateway initialization parameter, you must change the syntax of the procedure execute statement for all existing stored procedures.

In the following example, the employee name `JOHN SMYTHE `is passed to the Teradata stored procedure `REVISE_SALARY`. The stored procedure retrieves the salary value from the Teradata database to calculate a new yearly salary for `JOHN SMYTHE`. The revised salary returned in `RESULT` is used to update `EMP` in a table of an Oracle database:

    DECLARE
      INPUT VARCHAR2(15);
      RESULT NUMBER(8,2);
    BEGIN
      INPUT := 'JOHN SMYTHE';
      RESULT := REVISE_SALARY@TERA(INPUT);
      UPDATE EMP SET SAL = RESULT WHERE ENAME =: INPUT;
    END;
    /

The procedural feature automatically converts non-Oracle data types to and from PL/SQL data types.

#### Result Sets and Stored Procedures

The Oracle Database Gateway for Teradata provides support for stored procedures which return result sets.

By default, all stored procedures and functions do not return a result set to the user. To enable result sets, set the `HS_FDS_RESULTSET_SUPPORT` parameter in the initialization parameter file.

**See Also:**

[Initialization Parameters](database-gateway-teradata-initialization-parameters.md) for information about both editing the initialization parameter file and the `HS_FDS_RESULTSET_SUPPORT` parameter. For further information about Oracle support for result sets in non-Oracle databases see [Oracle Database Heterogeneous Connectivity User's Guide](../heter/result-set-support.md).

**Note:**

If you set the `HS_FDS_RESULTSET_SUPPORT` gateway initialization parameter, you must change the syntax of the procedure execute statement for all existing stored procedures or errors will occur.

When accessing stored procedures with result sets through the Oracle Database Gateway for Teradata, you will be in the sequential mode of Heterogeneous Services.

The Oracle Database Gateway for Teradata returns the following information to Heterogeneous Services during procedure description:

- All the input arguments of the remote stored procedure

- None of the output arguments

- One out argument of type ref cursor (corresponding to the first result set returned by the stored procedure)

Client programs have to use the virtual package function `dbms_hs_result_set.get_next_result_set` to get the ref cursor for subsequent result sets. The last result set returned is the out argument from the procedure.

The limitations of accessing result sets are the following:

- Result sets returned by a remote stored procedure have to be retrieved in the order in which they were placed on the wire

- On execution of a stored procedure, all result sets returned by a previously executed stored procedure will be closed (regardless of whether the data has been completely

In the following example, the Teradata stored procedure is executed to fetch the contents of the `emp` and `dept` tables from Teradata:

    CREATE PROCEDURE refcurproc (@arg1 varchar(255), @arg2 varchar(255) output)
    AS
    SECLECT @arg2 = @arg1
    SELECT * FROM EMP
    SELECT * FROM DEPT
    GO

This stored procedure assigns the input parameter `arg1` to the output parameter `arg2`, opens the query `SELECT * FROM EMP` in ref cursor `rc1`, and opens the query `SELECT * FROM DEPT` in ref cursor `rc2`.

**Note:**

Chained mode must be set before creating the stored procedure. Issue the following command in Teradata: `set chained on`

##### OCI Program Fetching from Result Sets in Sequential Mode

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
    OraText *stmt = (OraText *) "begin refcurproc@TERA(:1,:2,:3); end;";
    OraText *n_rs_stm = (OraText *)
      "begin :ret := DBMS_HS_RESULT_SET.GET_NEXT_RESULT_SET@TERA; end;";

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

##### PL/SQL Program Fetching from Result Sets in Sequential Mode

Assume that the table `loc_emp` is a local table exactly like the Teradata emp table. The same assumption applies for `loc_dept`. `outargs` is a table with columns corresponding to the out arguments of the Teradata stored procedure.

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
      out_arg := null;  refcurproc@TERA('Hello World', out_arg, rc1);

      -- Fetch 20 rows from the remote emp table and insert them into loc_emp
      for i in 1 .. 20 loop
        fetch rc1 into rec1;
        insert into loc_emp (rec1.empno, rec1.ename, rec1.job,
        rec1.mgr, rec1.hiredate, rec1.sal, rec1.comm, rec1.deptno);
      end loop;

      -- Close ref cursor
      close rc1;

      -- Get the next result set returned by the stored procedure
      rc2 := dbms_hs_result_set.get_next_result_set@TERA;

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
      rc3 := dbms_hs_result_set.get_next_result_set@TERA;

      -- Fetch them and insert them into the outarguments table
      fetch rc3 into rec3;
      insert into outargs (rec3.outarg, rec3.retval);

      -- Close ref cursor
      close rc3;

    end;
    /

### CHAR Semantics

This feature allows the gateway to optionally run in `CHAR` Semantics mode. Rather than always describing Teradata `CHAR` columns as `CHAR(n BYTE)`, this feature describes them as `CHAR(n CHAR)` and `VARCHAR(n CHAR)`. The concept is similar to Oracle database `CHAR` Semantics. You need to specify `HS_NLS_LENGTH_SEMANTICS=CHAR` to activate this option. Refer to [Initialization Parameters](database-gateway-teradata-initialization-parameters.md) for more detail.

### Multi-byte Character Sets Ratio Suppression

This feature optionally suppresses the ratio expansion from Teradata database to Oracle databases involving a multi-byte character set (for example, from `US7ASCII` to `AL32UTF8`, or from `KO16MSWIN949` to `KO16KSC5601`). By default, Oracle gateways assume the worst ratio to prevent data being truncated or allocation of buffer with insufficient size. However, if you have specific knowledge of your Teradata database and do not want the expansion to occur, you can specify `HS_KEEP_REMOTE_COLUMN_SIZE` parameter to suppress the expansion. Refer to [Initialization Parameters](database-gateway-teradata-initialization-parameters.md) for more detail.

### IPv6 Support

Besides full IPv6 support between Oracle databases and the gateway, IPv6 is also supported between this gateway and Teradata. Refer to `HS_FDS_CONNECT_INFO` parameter in [Initialization Parameters](database-gateway-teradata-initialization-parameters.md) for more detail.

### Gateway Session IDLE Timeout

You can optionally choose to terminate long idle gateway sessions automatically with the gateway parameter `HS_IDLE_TIMEOUT`. Specifically, when a gateway session is idle for more than the specified time limit, the gateway session is terminated with any pending changes rolled back.

### Database Compatibility Issues for Teradata

Teradata and Oracle databases function differently in some areas, causing compatibility problems. The compatibility issues are described in the following links:

- Schema Considerations

- Naming Rules

- Data Types

- Queries

- Locking

#### Schema Considerations

The Oracle concept of a schema does not exist in Teradata. A schema name included in a query is recognized by Teradata as a database name. In the Oracle database, the schema of an object is identical to the owner of that object. However, when one retrieves or references an `OWNER` field in a Data Dictionary view such as `ALL_TABLES`, the `OWNER` field really is referencing a Teradata database name.

When querying data dictionary tables, the following results are returned:

- `ALL_*` data dictionary tables, data for every Teradata database is returned. The Teradata database name is returned in the `OWNER`, `INDEX_OWNER`, or `TABLE_OWNER` column depending on the data dictionary table being referenced.

- `ALL_USERS` data dictionary table, each Teradata database name is returned in the `USERNAME` column.

- `USER_*` data dictionary tables, data for the default Teradata database is returned for the `OWNER` or `TABLE_OWNER` column depending on the data dictionary table being referenced. If a default Teradata database is not defined, the DBC Teradata system database is used.

#### Naming Rules

Naming rule issues include the following:

- Rules for Naming Objects

- Case Sensitivity

##### Rules for Naming Objects

Oracle and Teradata use different database object naming rules. For example, the maximum number of characters allowed for each object name can be different. Also, the use of single and double quotation marks, case sensitivity, and the use of alphanumeric characters can all be different.

##### Case Sensitivity

The Oracle database defaults to uppercase unless you surround identifiers with double quote characters. For example, to refer to the Teradata table called `emp`, enter the name with double quote characters, as follows:

    SQL> SELECT * FROM "emp"@TERA;

However, to refer to the Teradata table called `emp` in the Teradata database named Scott from an Oracle application, enter the following:

    SQL> SELECT * FROM "Scott"."emp"@TERA;

If the Teradata table called `emp` in the Teradata database named `SCOTT`, a name consisting entirely of uppercase letters, you can enter the owner name without double quote characters, as follows:

    SQL> SELECT * FROM SCOTT."emp"@TERA;

or

    SQL> SELECT * FROM scott."emp"@TERA;

Oracle recommends that you surround all Teradata object names with double quote characters and use the exact letter case for the object names as they appear in the Teradata data dictionary. This convention is not required when referring to the supported Oracle data dictionary tables or views listed in [Data Dictionary](database-gateway-teradata-data-dictionary.md).

If existing applications cannot be changed according to these conventions, create views in Oracle to associate Teradata names to the correct letter case. For example, to refer to the Teradata table `emp` from an existing Oracle application by using only uppercase names, define the following view:

    SQL> CREATE VIEW EMP (EMPNO, ENAME, SAL, HIREDATE)
          AS SELECT "empno", "ename", "sal", "hiredate"
          FROM "emp"@TERA;

With this view, the application can issue statements such as the following:

    SQL> SELECT EMPNO, ENAME FROM EMP;

Using views is a workaround solution that duplicates data dictionary information originating in the Teradata data dictionary. You must be prepared to update the Oracle view definitions whenever the data definitions for the corresponding tables are changed in the Teradata database.

#### Data Types

Data type issues include the following:

- Binary Literal Notation

- Data Type Conversion

##### Binary Literal Notation

Oracle SQL uses hexadecimal digits surrounded by single quotes to express literal values being compared or inserted into columns defined as data type `RAW`.

This notation is not converted to syntax compatible with the Teradata `VARBINARY` and `BINARY` data types (a `ff` surrounded by single quotes followed by hexadecimal digits).

For example, the following statement is not supported:

    SQL> INSERT INTO BINARY_TAB@TERA VALUES ('ff'xb)

where `BINARY_TAB` contains a column of data type `VARBINARY` or `BINARY`. Use bind variables when inserting into or updating `VARBINARY` and `BINARY` data types.

##### Data Type Conversion

Teradata does not support implicit date conversions. Such conversions must be explicit.

For example, the gateway issues an error for the following `SELECT` statement:

    SELECT DATE_COL FROM TEST@TERA WHERE DATE_COL = "1-JAN-2001";

To avoid problems with implicit conversions, add explicit conversions, as in the following:

    SELECT DATE_COL FROM TEST@TERA WHERE DATE_COL = TO_DATE("1-JAN-2001")

**See Also:**

[Data Type Conversion](database-gateway-teradata-data-type-conversion.md) for more information about restrictions on data types.

#### Queries

Query issues include the following:

- Row Selection

- Empty Bind Variables

##### Row Selection

Teradata evaluates a query condition for all selected rows before returning any of the rows. If there is an error in the evaluation process for one or more rows, no rows are returned even though the remaining rows satisfy the condition.

Oracle evaluates the query condition row-by-row and returns a row when the evaluation is successful. Rows are returned until a row fails the evaluation.

##### Empty Bind Variables

For `VARCHAR` bind variables, the gateway passes empty bind variables to the Teradata database as a `NULL` value.

#### Locking

The locking model for an Teradata database differs significantly from the Oracle model. The gateway depends on the underlying Teradata behavior, so the following possible scenarios can affect Oracle applications that access Teradata through the gateway:

- Read access might block write access.

- Write access might block read access.

- Statement-level read consistency is not guaranteed.

  **See Also:**

  Teradata documentation for information about the Teradata locking model.

### Known Restrictions

If you encounter incompatibility problems not listed in this section or in "Known Problems", contact Oracle Support Services. The following topics describe the known restrictions and includes suggestions for dealing with them when possible:

- Transactional Integrity

- Transaction Capability

- COMMIT or ROLLBACK in PL/SQL Cursor Loops Closes Open Cursors

- Pass-Through Feature

- Bind Variables for Date Columns

- SQL Syntax

- SQL\*Plus

- Database Links

#### Transactional Integrity

The gateway cannot guarantee transactional integrity in the following cases:

- When a statement that is processed by the gateway causes an implicit commit in the target database

- When the target database is configured to work in autocommit mode

  **Note:**

  Oracle strongly recommends the following:

  - If you know that executing a particular statement causes an implicit commit in the target database, then ensure that this statement is executed in its own transaction.

  - Do not configure the target database to work in autocommit mode.

#### Transaction Capability

The gateway does not support savepoints. If a distributed update transaction is under way involving the gateway and a user attempts to create a savepoint, the following error occurs:

    ORA-02070: database dblink does not support savepoint in this context

By default, the gateway is configured as `COMMIT_CONFIRM` and it is always the commit point site when the Teradata database is updated by the transaction.

#### COMMIT or ROLLBACK in PL/SQL Cursor Loops Closes Open Cursors

Any `COMMIT` or `ROLLBACK` issued in a PL/SQL cursor loop closes all open cursors, which can result in the following error:

    ORA-1002:  fetch out of sequence

To prevent this error, move the `COMMIT` or `ROLLBACK` statement outside the cursor loop.

#### Pass-Through Feature

Oracle recommends that you place a DDL statement in its own transaction when executing such a statement with the pass-through feature. An explicit `COMMIT` must be issued after the DDL statement.

If the SQL statements being passed through the gateway result in an implicit commit at the Teradata database, the Oracle transaction manager is unaware of the commit and an Oracle `ROLLBACK` command cannot be used to roll back the transaction.

#### Bind Variables for Date Columns

You cannot compare columns of data type `TIME` or `TIMESTAMP` to a bind variable.

The following SQL statement causes an error message:

    SQL> select time_column from time_table@TERA where time_column = :a;

The following error is issued:

    Invalid operation on an ANSI Datetime or Interval value.

#### SQL Syntax

Restrictions on SQL syntax are listed as follows:

- WHERE CURRENT OF Clause

- CONNECT BY Clause

- ROWID

- EXPLAIN PLAN Statement

**See Also:**

[Supported SQL Syntax and Functions](database-gateway-teradata-supported-sql-syntax-functions.md) for more information about restrictions on SQL syntax.

##### WHERE CURRENT OF Clause

`UPDATE` and `DELETE` statements with the `WHERE CURRENT OF` clause are not supported by the gateway because they rely on the Oracle `ROWID` implementation. To update or delete a specific row through the gateway, a condition style `WHERE` clause must be used.

##### CONNECT BY Clause

The gateway does not support the `CONNECT BY` clause in a `SELECT` statement.

##### ROWID

The Oracle `ROWID` implementation is not supported.

##### EXPLAIN PLAN Statement

The `EXPLAIN PLAN `statement is not supported.

#### SQL\*Plus

You need to use double quotes to wrap around lowercase table names.

For example:

    copy from tkhouser/tkhouser@inst1 insert loc_tkhodept using select * from "tkhodept"@TERA;

#### Database Links

The gateway is not a shared server process and cannot support shared database links. Each gateway session spawns a separate gateway process and connections cannot be shared.

### Known Problems

This section describes known problems and includes suggestions for correcting them when possible. If you have any questions or concerns about the problems, contact Oracle Support Services. A current list of problems is available online. Contact your local Oracle office for information about accessing the list.

The known problems are as follows:

- Teradata LONG VARCHAR Data Type

- Schema Names and PL/SQL

- Data Dictionary Views and PL/SQL

#### Teradata LONG VARCHAR Data Type

The following restrictions apply when using` LONG VARCHAR` data types:

- An unsupported SQL function cannot be used in a SQL statement that accesses a column defined as Teradata data type `LONG VARCHAR`.

- You cannot use SQL\*Plus to select data from a column defined as Teradata data type `LONG VARCHAR` when the data is greater than 80 characters in length. Oracle recommends using Pro\*C or Oracle Call Interface to access such data in a Teradata database.

- `LONG VARCHAR` data types must be `NULLABLE` for `INSERT` or `UPDATE` to work.

- A table including a `LONG VARCHAR` column must have a unique index defined on the table or the table must have a separate column that serves as a primary key.

- `LONG VARCHAR` data cannot be read through pass-through queries.

The gateway does not support the PL/SQL function `COLUMN_VALUE_LONG` of the `DBMS_SQL` package.

**See Also:**

[Supported SQL Syntax and Functions](database-gateway-teradata-supported-sql-syntax-functions.md) for more information about restrictions on SQL syntax.

#### Schema Names and PL/SQL

If you do not prefix a Teradata database object with its schema name in a SQL statement within a PL/SQL block, the following error message occurs:

    ORA-6550 PLS-201 Identifier table_name must be declared.

Change the SQL statement to include the schema name of the object.

#### Data Dictionary Views and PL/SQL

You cannot refer to data dictionary views in SQL statements that are inside a PL/SQL block.
