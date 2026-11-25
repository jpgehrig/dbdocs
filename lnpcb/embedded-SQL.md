This chapter describes the basic techniques of embedded SQL programming. Topics are:

- Using Host Variables

- Using Indicator Variables

- The Basic SQL Statements

- Cursors

- Scrollable Cursors

- Flexible B Area Length

- Fix Execution Plans

- Sample Program 2: Cursor Operations

### 5.1 Using Host Variables

Use host variables to pass data and status information to your program from the database, and to pass data to the database.

#### 5.1.1 Output Versus Input Host Variables

Depending on how they are used, host variables are called output or input host variables. Host variables in the INTO clause of a SELECT or FETCH statement are called output host variables because they hold column values output by Oracle. Oracle assigns the column values to corresponding output host variables in the INTO clause.

All other host variables in a SQL statement are called input host variables because your program inputs their values to Oracle. For example, you use input host variables in the VALUES clause of an INSERT statement and in the SET clause of an UPDATE statement. They are also used in the WHERE, HAVING, and FOR clauses. In fact, input host variables can appear in a SQL statement wherever a value or expression is allowed.

You cannot use input host variables to supply SQL keywords or the names of database objects. Thus, you cannot use input host variables in data definition statements (sometimes called DDL) such as ALTER, CREATE, and DROP. In the following example, the DROP TABLE statement is invalid:

         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
             01 TABLE-NAME    PIC X(30) VARYING.
              ...
         EXEC SQL END DECLARE SECTION END-EXEC.
         ...
         DISPLAY 'Table name? '.
         ACCEPT TABLE-NAME.
         EXEC SQL DROP TABLE :TABLE-NAME END-EXEC.
    *  -- host variable not allowed

**Note:**

In an ORDER BY clause, you can use a host variable, but it is treated as a constant or literal, and hence the contents of the host variable have no effect. For example, the SQL statement:

         EXEC SQL SELECT ENAME, EMPNO INTO :NAME, :NUMBER
             FROM EMP
             ORDER BY :ORD
         END-EXEC.

appears to contain an input host variable, ORD. However, the host variable in this case is treated as a constant, and regardless of the value of ORD, no ordering is done.

Before Oracle executes a SQL statement containing input host variables, your program must assign values to them. Consider the following example:

         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01     EMP-NUMBER   PIC S9(4) COMP.
     01     EMP-NAME     PIC X(20) VARYING.
         EXEC SQL END DECLARE SECTION END-EXEC.
         ...
    * -- get values for input host variables
         DISPLAY 'Employee number? '.
         ACCEPT EMP-NUMBER.
         DISPLAY 'Employee name? '.
         ACCEPT EMP-NAME.
         EXEC SQL INSERT INTO EMP (EMPNO, ENAME)
             VALUES (:EMP-NUMBER, :EMP-NAME)
         END-EXEC.

Notice that the input host variables in the VALUES clause of the INSERT statement are prefixed with colons.

### 5.2 Using Indicator Variables

You can associate any host variable with an optional indicator variable. Each time the host variable is used in a SQL statement, a result code is stored in its associated indicator variable. Thus, indicator variables let you monitor host variables.

You use indicator variables in the VALUES or SET clause to assign NULLs to input host variables and in the INTO clause to detect NULLs or truncated values in output host variables.

#### 5.2.1 Input Variables

For input host variables, the values your program can assign to an indicator variable have the following meanings:

| Variable | Meaning                                                                           |
|:---------|:----------------------------------------------------------------------------------|
| -1       | Oracle will assign a NULL to the column, ignoring the value of the host variable. |
| \>= 0    | Oracle will assigns the value of the host variable to the column.                 |

#### 5.2.2 Output Variables

For output host variables, the values Oracle can assign to an indicator variable have the following meanings:

| Variable | Meaning                                                                                                                                                                                                                                                             |
|:---------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -2       | Oracle assigned a truncated column value to the host variable, but could not assign the original length of the column value to the indicator variable because the number was too large.                                                                             |
| -1       | The column value is NULL, so the value of the host variable is indeterminate.                                                                                                                                                                                       |
| 0        | Oracle assigned an intact column value to the host variable.                                                                                                                                                                                                        |
| \> 0     | Oracle assigned a truncated column value to the host variable, assigned the original column length (expressed in characters, instead of bytes, for multibyte Globalization Support host variables) to the indicator variable, and set SQLCODE in the SQLCA to zero. |

Remember, an indicator variable must be declared as a 2-byte integer and, in SQL statements, must be prefixed with a colon and appended to its host variable (unless you use the keyword INDICATOR).

#### 5.2.3 Inserting NULLs

You can use indicator variables to insert NULLs. Before the insert, for each column you want to be NULL, set the appropriate indicator variable to -1, as shown in the following example:

          MOVE -1 TO IND-COMM.
          EXEC SQL INSERT INTO EMP (EMPNO, COMM)
              VALUES (:EMP-NUMBER, :COMMISSION:IND-COMM)
          END-EXEC.

The indicator variable IND-COMM specifies that a NULL is to be stored in the COMM column.

You can hard-code the NULL instead, as follows:

          EXEC SQL INSERT INTO EMP (EMPNO, COMM)
              VALUES (:EMP-NUMBER, NULL)
          END-EXEC.

But this is less flexible.

Typically, you insert NULLs conditionally, as the next example shows:

          DISPLAY 'Enter employee number or 0 if not available: '
              WITH NO ADVANCING.
          ACCEPT EMP-NUMBER.
          IF EMP-NUMBER = 0
             MOVE -1 TO IND-EMPNUM
          ELSE
              MOVE 0 TO IND-EMPNUM
          END-IF.
          EXEC SQL INSERT INTO EMP (EMPNO, SAL)
             VALUES (:EMP-NUMBER:IND-EMPNUM, :SALARY)
          END-EXEC.

#### 5.2.4 Handling Returned NULLs

You can also use indicator variables to manipulate returned NULLs, as the following example shows:

          EXEC SQL SELECT ENAME, SAL, COMM
             INTO :EMP-NAME, :SALARY, :COMMISSION:IND-COMM
              FROM EMP
              WHERE EMPNO = :EMP_NUMBER
          END-EXEC.
          IF IND-COMM = -1
              MOVE SALARY TO PAY.
    *   -- commission is null; ignore it
          ELSE
              ADD SALARY TO COMMISSION GIVING PAY.
          END-IF.

#### 5.2.5 Fetching NULLs

Using the precompiler option UNSAFE_NULL=YES, you can select or fetch NULLs into a host variable that lacks an indicator variable, as the following example shows:

    * --  assume that commission is NULL
          EXEC SQL SELECT ENAME, SAL, COMM
             INTO :EMP-NAME, :SALARY, :COMMISSION
             FROM EMP
             WHERE EMPNO = :EMP-NUMBER
          END-EXEC.

SQLCODE in the SQLCA is set to zero indicating that Oracle executed the statement without detecting an error or exception.

Without an indicator variable there is no way to know whether or not a NULL was returned. The value of the host variable is undefined. If you do not use indicator variables, set the precompiler option UNSAFE_NULL=YES. Oracle therefore advises that UNSAFE_NULL=YES only be used to upgrade existing programs and that indicator variables be used for all new programs.

When UNSAFE_NULL=NO, if you select or fetch NULLs into a host variable that lacks an indicator variable, Oracle issues an error message.

**Related Topics**

- [UNSAFE_NULL](precompiler-options.md)

#### 5.2.6 Testing for NULLs

You can use indicator variables in the WHERE clause to test for NULLs, as the following example shows:

          EXEC SQL SELECT ENAME, SAL
             INTO :EMP-NAME, :SALARY
             FROM EMP
             WHERE :COMMISSION:IND-COMM IS NULL ...

However, you cannot use a relational operator to compare NULLs with each other or with other values. For example, the following SELECT statement fails if the COMM column contains one or more NULLs:

          EXEC SQL SELECT ENAME, SAL
             INTO :EMP-NAME, :SALARY
              FROM EMP
              WHERE COMM = :COMMISSION:IND-COMM
          END-EXEC.

The next example shows how to compare values for equality when some of them might be NULLs:

          EXEC SQL SELECT ENAME, SAL
             INTO :EMP_NAME, :SALARY
             FROM EMP
             WHERE (COMM = :COMMISSION) OR ((COMM IS NULL) AND
                 (:COMMISSION:IND-COMM IS NULL))
          END-EXEC.

#### 5.2.7 Fetching Truncated Values

If a value is truncated when fetched into a host variable, no error is generated. In all cases a WARNING will be signaled (see "[Warning Flags](error-handling-and-diagnostics.md)"). if an indicator variable is used with a character string, when a value is truncated, the indicator variable is set to the length of the value in the database. Note that no warning is flagged if a numeric value is truncated.

### 5.3 The Basic SQL Statements

Executable SQL statements let you query, manipulate, and control Oracle data and create, define, and maintain Oracle objects such as tables, views, and indexes. This chapter focuses on statements which manipulate data in database tables (sometimes called DML) and cursor control statements.

The following SQL statements let you query and manipulate Oracle data:

| SQL Statements | Description                           |
|:---------------|:--------------------------------------|
| SELECT         | Returns rows from one or more tables. |
| INSERT         | Adds new rows to a table.             |
| UPDATE         | Modifies rows in a table.             |
| DELETE         | Removes rows from a table.            |

When executing a data manipulation statement such as INSERT, UPDATE, or DELETE, you want to know how many rows have been updated as well as whether it succeeded. To find out, you simply check the SQLCA. (Executing any SQL statement sets the SQLCA variables.) You can check in the following two ways:

- Implicit checking with the WHENEVER statement

- Explicit checking of SQLCA variables

Alternatively, when MODE={ANSI \| ANSI14}, you can check the status variable SQLSTATE or SQLCODE. For more information, see "[ANSI SQLSTATE Variable](error-handling-and-diagnostics.md)".

When executing a SELECT statement (query), however, you must also deal with the rows of data it returns. Queries can be classified as follows:

- queries that return no rows (that is, merely check for existence)

- queries that return only one row

- queries that return more than one row

Queries that return more than one row require an explicitly declared cursor or cursor variable. The following embedded SQL statements let you define and control an explicit cursor:

| SQL Statements | Description                                                               |
|:---------------|:--------------------------------------------------------------------------|
| DECLARE        | Names the cursor and associates it with a query.                          |
| OPEN           | Executes the query and identifies the active set.                         |
| FETCH          | Advances the cursor and retrieves each row in the active set, one by one. |
| CLOSE          | Disables the cursor (the active set becomes undefined.)                   |

In the coming sections, first you learn how to code INSERT, UPDATE, DELETE, and single-row SELECT statements. Then, you progress to multirow SELECT statements. , see the

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for more information about statements and their clauses.

#### 5.3.1 Selecting Rows

Querying the database is a common SQL operation. To issue a query you use the SELECT statement. In the following example, you query the EMP table:

          EXEC SQL SELECT ENAME, JOB, SAL + 2000
             INTO :emp_name, :JOB-TITLE, :SALARY
             FROM EMP
             WHERE EMPNO = :EMP-NUMBER
          END-EXEC.

The column names and expressions following the keyword SELECT make up the select list. The select list in our example contains three items. Under the conditions specified in the WHERE clause (and following clauses, if present), Oracle returns column values to the host variables in the INTO clause. The number of items in the select list should equal the number of host variables in the INTO clause, so there is a place to store every returned value.

In the simplest case, when a query returns one row, its form is that shown in the last example (in which EMPNO is a unique key). However, if a query can return more than one row, you must fetch the rows using a cursor or select them into a host array.

If a query is written to return only one row but might actually return several rows, the result depends on how you specify the option SELECT_ERROR. When SELECT_ERROR=YES (the default), Oracle issues an message if more than one row is returned.

When SELECT_ERROR=NO, a row is returned and Oracle generates no error.

##### 5.3.1.1 Available Clauses

You can use all of the following standard SQL clauses in your SELECT statements: INTO, FROM, WHERE, CONNECT BY, START WITH, GROUP BY, HAVING, ORDER BY, and FOR UPDATE OF.

#### 5.3.2 Inserting Rows

You use the INSERT statement to add rows to a table or view. In the following example, you add a row to the EMP table:

          EXEC SQL INSERT INTO EMP (EMPNO, ENAME, SAL, DEPTNO)
             VALUES (:EMP_NUMBER, :EMP-NAME, :SALARY, :DEPT-NUMBER)
          END-EXEC.

Each column you specify in the column list must belong to the table named in the INTO clause. The VALUES clause specifies the row of values to be inserted. The values can be those of constants, host variables, SQL expressions, or pseudocolumns, such as USER and SYSDATE.

The number of values in the VALUES clause must equal the number of names in the column list. You can omit the column list if the VALUES clause contains a value for each column in the table in the same order they were defined by CREATE TABLE, but this is not recommended because a table's definition can change.

#### 5.3.3 DML Returning Clause

The INSERT, UPDATE, and DELETE statements can have an optional DML returning clause which returns column value expressions expr, into host variables hv, with host indicator variables iv. The returning clausehas this syntax:

    {RETURNING | RETURN} {expr [,expr]}
        INTO {:hv [[INDICATOR]:iv] [, :hv [[INDICATOR]:iv]]}

The number of expressions must equal the number of host variables. This clause eliminates the need for selecting the rows after an INSERT or UPDATE, and before a DELETE when you need to record that information for your application. The `DML returning clause` eliminates inefficient network round-trips, extra processing, and server memory. You will also note, for example, when a trigger inserts default values or a primary key value.

The returning_clause is not allowed with a subquery. It is only allowed after the VALUES clause.

For example, our INSERT could have a clause at its end such as:

    RETURNING EMPNO, ENAME, DEPTNO INTO :NEW-EMP-NUMBER, :NEW-EMP-NAME, :DEPT

**Related Topics**

- [Embedded SQL Statements and Precompiler Directives](embedded-SQL-statements-and-precompiler-directives.md)

#### 5.3.4 Using Subqueries

A subquery is a nested SELECT statement. Subqueries let you conduct multi-part searches. They can be used to

- supply values for comparison in the WHERE, HAVING, and START WITH clauses of SELECT, UPDATE, and DELETE statements

- define the set of rows to be inserted by a CREATE TABLE or INSERT statement

- define values for the SET clause of an UPDATE statement

For example, to copy rows from one table to another, replace the VALUES clause in an INSERT statement with a subquery, as follows:

         EXEC SQL INSERT INTO EMP2 (EMPNO, ENAME, SAL, DEPTNO)
             SELECT EMPNO, ENAME, SAL, DEPTNO FROM EMP
             WHERE JOB = :JOB-TITLE
         END-EXEC.

Notice how the INSERT statement uses the subquery to obtain intermediate results.

#### 5.3.5 Updating Rows

You use the UPDATE statement to change the values of specified columns in a table or view. In the following example, you update the SAL and COMM columns in the EMP table:

          EXEC SQL UPDATE EMP
             SET SAL = :SALARY, COMM = :COMMISSION
             WHERE EMPNO = :EMP-NUMBER
          END-EXEC.

You can use the optional WHERE clause to specify the conditions under which rows are updated. See "Using the WHERE Clause ".

The SET clause lists the names of one or more columns for which you must provide values. You can use a subquery to provide the values, as the following example shows:

          EXEC SQL UPDATE EMP
          SET SAL = (SELECT AVG(SAL)*1.1 FROM EMP WHERE DEPTNO = 20)
          WHERE EMPNO = :EMP-NUMBER
          END-EXEC.

#### 5.3.6 Deleting Rows

You use the DELETE statement to remove rows from a table or view. In the following example, you delete all employees in a given department from the EMP table:

          EXEC SQL DELETE FROM EMP
             WHERE DEPTNO = :DEPT-NUMBER
          END-EXEC.

You can use the optional WHERE clause to specify the condition under which rows are deleted.

#### 5.3.7 Using the WHERE Clause

You use the WHERE clause to select, update, or delete only those rows in a table or view that meet your search condition. The WHERE-clause search condition is a Boolean expression, which can include scalar host variables, host arrays (not in SELECT statements), and subqueries.

If you omit the WHERE clause, all rows in the table or view are processed. If you omit the WHERE clause in an UPDATE or DELETE statement, Oracle sets SQLWARN(5) in the SQLCA to 'W' to warn that all rows were processed.

### 5.4 Cursors

To process a SQL statement, Oracle opens a work area called a private SQL area. The private SQL area stores information needed to execute the SQL statement. An identifier called a cursor lets you name a SQL statement, access the information in its private SQL area, and, to some extent, control its processing.

For static SQL statements, there are two types of cursors: implicit and explicit. Oracle implicitly declares a cursor for all data definition and data manipulation statements, including SELECT statements that use the INTO clause.

The set of rows retrieved is called the results set; its size depends on how many rows meet the query search condition. You use an explicit cursor to identify the row currently being processed, which is called the current row.

When a query returns multiple rows, you can explicitly define a cursor to

- Process beyond the first row returned by the query

- Keep track of which row is currently being processed

A cursor identifies the current row in the set of rows returned by the query. This allows your program to process the rows one at a time. The following statements let you define and manipulate a cursor:

- DECLARE

- OPEN

- FETCH

- CLOSE

First you use the DECLARE statement (more precisely, a directive) to name the cursor and associate it with a query.

The OPEN statement executes the query and identifies all the rows that meet the query search condition. These rows form a set called the active set of the cursor. After opening the cursor, you can use it to retrieve the rows returned by its associated query.

Rows of the active set are retrieved one by one (unless you use host arrays). You use a FETCH statement to retrieve the current row in the active set. You can execute FETCH repeatedly until all rows have been retrieved.

When done fetching rows from the active set, you disable the cursor with a CLOSE statement, and the active set becomes undefined.

#### 5.4.1 Declaring a Cursor

You use the DECLARE statement to define a cursor by giving it a name, as the following example shows:

          EXEC SQL DECLARE EMPCURSOR CURSOR FOR
             SELECT ENAME, EMPNO, SAL
             FROM EMP
             WHERE DEPTNO = :DEPT_NUMBER
          END-EXEC.

The cursor name is an identifier used by the precompiler, not a host or program variable, and should not be declared in a COBOL statement. Therefore, cursor names cannot be passed from one precompilation unit to another. Cursor names cannot be hyphenated. They can be any length, but only the first 31 characters are significant. For ANSI compatibility, use cursor names no longer than 18 characters.

The precompiler option CLOSE_ON_COMMIT is provided for use in the command line or in a configuration file. Any cursor not declared with the WITH HOLD clause is closed after a COMMIT or ROLLBACK when CLOSE_ON_COMMIT=YES.

If MODE is specified at a higher level than CLOSE_ON_COMMIT, then MODE takes precedence. The defaults are MODE=ORACLE and CLOSE_ON_COMMIT=NO. If you specify MODE=ANSI then any cursors not using the WITH HOLD clause will be closed on COMMIT. The application will run more slowly because cursors are closed and re-opened many times. Setting CLOSE_ON_COMMIT=NO when MODE=ANSI results in performance improvement. To see how macro options such as MODE affect micro options such as CLOSE_ON_COMMIT, see "[Precedence of Option Values](precompiler-options.md)".

The SELECT statement associated with the cursor cannot include an INTO clause. Rather, the INTO clause and list of output host variables are part of the FETCH statement.

Because it is declarative, the DECLARE statement must physically (not just logically) precede all other SQL statements referencing the cursor. That is, forward references to the cursor are not allowed. In the following example, the OPEN statement is misplaced:

          EXEC SQL OPEN EMPCURSOR END-EXEC.
    *    -- MISPLACED OPEN STATEMENT
          EXEC SQL DECLARE EMPCURSOR CURSOR FOR
             SELECT ENAME, EMPNO, SAL
             FROM EMP
             WHERE ENAME = :EMP-NAME
          END-EXEC.

The cursor control statements (DECLARE, OPEN, FETCH, CLOSE) must all occur within the same precompiled unit. For example, you cannot declare a cursor in source file A.PCO, then open it in source file B.PCO.

Your host program can declare as many cursors as it needs. However, in a given file, every DECLARE statement must be unique. That is, you cannot declare two cursors with the same name in one precompilation unit, even across blocks or procedures, because the scope of a cursor is global within a file.

For users of MODE=ANSI or CLOSE_ON_COMMIT=YES, the WITH HOLD clause can be used in a DECLARE section to override the behavior defined by the two options. With these options set, the behavior will be for all cursors to be closed when a COMMIT is issued. This can have performance implications due to the overhead of re-opening the cursor to continue processing. The careful use of WITH HOLD can speed up programs that need to conform to the ANSI standard for precompilers in most respects.

**Related Topics**

- [CLOSE_ON_COMMIT](precompiler-options.md)
- [WITH HOLD Clause in DECLARE CURSOR Statements](database-concepts.md)

#### 5.4.2 Opening a Cursor

Use the OPEN statement to execute the query and identify the active set. In the following example, a cursor named EMPCURSOR is opened.

         EXEC SQL OPEN EMPCURSOR END-EXEC.

OPEN positions the cursor just before the first row of the active set. However, none of the rows is actually retrieved at this point. That will be done by the FETCH statement.

Once you open a cursor, the query's input host variables are not reexamined until you reopen the cursor. Thus, the active set does not change. To change the active set, you must reopen the cursor.

The amount of work done by OPEN depends on the values of three precompiler options: HOLD_CURSOR, RELEASE_CURSOR, and MAXOPENCURSORS.

**Related Topics**

- [Using Pro\*COBOL Precompiler Options](precompiler-options.md)

#### 5.4.3 Fetching from a Cursor

You use the FETCH statement to retrieve rows from the active set and specify the output host variables that will contain the results. Recall that the SELECT statement associated with the cursor cannot include an INTO clause. Rather, the INTO clause and list of output host variables are part of the FETCH statement. In the following example, you fetch into three host variables:

          EXEC SQL FETCH EMPCURSOR
             INTO :EMP-NAME, :EMP-NUMBER, :SALARY
          END-EXEC.

The cursor must have been previously declared and opened. The first time you execute FETCH, the cursor moves from before the first row in the active set to the first row. This row becomes the current row. Each subsequent execution of FETCH advances the cursor to the next row in the active set, changing the current row. The cursor can only move forward in the active set. To return to a row that has already been fetched, you must reopen the cursor, then begin again at the first row of the active set.

If you want to change the active set, you must assign new values to the input host variables in the query associated with the cursor, then reopen the cursor. When MODE=ANSI, you must close the cursor before reopening it.

As the next example shows, you can fetch from the same cursor using different sets of output host variables. However, corresponding host variables in the INTO clause of each FETCH statement must have the same datatype.

         EXEC SQL DECLARE EMPCURSOR CURSOR FOR
             SELECT ENAME, SAL FROM EMP WHERE DEPTNO = 20
         END-EXEC.
         ...
         EXEC SQL OPEN EMPCURSOR END-EXEC.
         EXEC SQL WHENEVER NOT FOUND DO ...
     LOOP.
         EXEC SQL FETCH EMPCURSOR INTO :EMP-NAME1, :SAL1 END-EXEC
         EXEC SQL FETCH EMPCURSOR INTO :EMP-NAME2, :SAL2 END-EXEC
         EXEC SQL FETCH EMPCURSOR INTO :EMP-NAME3, :SAL3 END-EXEC
         ...
         GO TO LOOP.
         ...
     END-PERFORM.

If the active set is empty or contains no more rows, FETCH returns the "no data found" Oracle warning code to SQLCODE in the SQLCA (if MODE=ANSI then the optional SQLSTATE variable will also be set.) The status of the output host variables is indeterminate. (In a typical program, the WHENEVER NOT FOUND statement detects this error.) To reuse the cursor, you must reopen it.

#### 5.4.4 Closing a Cursor

When finished fetching rows from the active set, you close the cursor to free the resources, such as storage, acquired by opening the cursor. When a cursor is closed, parse locks are released. What resources are freed depends on how you specify the options HOLD_CURSOR and RELEASE_CURSOR. In the following example, you close the cursor named EMPCURSOR:

         EXEC SQL CLOSE EMPCURSOR END-EXEC.

You cannot fetch from a closed cursor because its active set becomes undefined. If necessary, you can reopen a cursor (with new values for the input host variables, for example).

When CLOSE_ON_COMMIT=NO (the default when MODE=ORACLE), issuing a COMMIT or ROLLBACK will only close cursors declared using the FOR UPDATE clause or referred to by the CURRENT OF clause. Other cursors that are not affected by the COMMIT or ROLLBACK statement, remain open, if they are open already. However, when CLOSE_ON_COMMIT=YES (the default when MODE=ANSI), issuing a COMMIT or ROLLBACK closes all cursors.

**Related Topics**

- [CLOSE_ON_COMMIT](precompiler-options.md)

#### 5.4.5 Using the CURRENT OF Clause

You use the CURRENT OF cursor_name clause in a DELETE or UPDATE statement to refer to the latest row fetched from the named cursor. The cursor must be open and positioned on a row. If no fetch has been done or if the cursor is not open, the CURRENT OF clause results in an error and processes no rows.

The FOR UPDATE OF clause is optional when you declare a cursor that is referenced in the CURRENT OF clause of an UPDATE or DELETE statement. The CURRENT OF clause signals the precompiler to add a FOR UPDATE clause if necessary.

In the following example, you use the CURRENT OF clause to refer to the latest row fetched from a cursor named EMPCURSOR:

         EXEC SQL DECLARE EMPCURSOR CURSOR FOR
             SELECT ENAME, SAL FROM EMP WHERE JOB = 'CLERK'
         END-EXEC.
         ...
         EXEC SQL OPEN EMPCURSOR END-EXEC.
         EXEC SQL WHENEVER NOT FOUND DO ...
     LOOP.
         EXEC SQL FETCH EMPCURSOR INTO :EMP-NAME, :SALARY
         END-EXEC.
         ...
         EXEC SQL UPDATE EMP SET SAL = :NEW-SALARY
             WHERE CURRENT OF EMPCURSOR
         END-EXEC.
         GO TO LOOP.

**Related Topics**

- [Mimicking the CURRENT OF Clause](host-tables.md)

#### 5.4.6 Restrictions

An explicit FOR UPDATE OF or an implicit FOR UPDATE acquires exclusive row locks. All rows are locked at the open, not as they are fetched, and are released when you commit or rollback. If you try to fetch from a FOR UPDATE cursor after a commit, Oracle generates an error.

You cannot use the CURRENT OF clause with a cursor declared with a join since internally, the CURRENT OF mechanism uses the ROWID pseudocolumn and there is no way to specify which table the ROWID relates to. For an alternative, see "[Mimicking the CURRENT OF Clause](host-tables.md)". Finally, you cannot use the CURRENT OF clause in dynamic SQL.

#### 5.4.7 A Typical Sequence of Statements

The following example shows the typical sequence of cursor control statements using the CURRENT OF clause and the FOR UPDATE OF clause:

    * --  Define a cursor.
         EXEC SQL DECLARE EMPCURSOR CURSOR FOR
             SELECT ENAME, JOB FROM EMP
             WHERE EMPNO = :EMP-NUMBER
             FOR UPDATE OF JOB
         END-EXEC.
    * --  Open the cursor and identify the active set.
         EXEC SQL OPEN EMPCURSOR END-EXEC.
    * --  Exit if the last row was already fetched.
         EXEC SQL
             WHENEVER NOT FOUND GOTO NO-MORE
         END-EXEC.
    * --  Fetch and process data in a loop.
     LOOP.
     EXEC SQL FETCH EMPCURSOR INTO :EMP-NAME, :JOB-TITLE
           END-EXEC.
    * -- host-language statements that operate on the fetched data
           EXEC SQL UPDATE EMP
              SET JOB = :NEW-JOB-TITLE
              WHERE CURRENT OF EMPCURSOR
           END-EXEC.
           GO TO LOOP.
         ...
     MO-MORE.
    * --  Disable the cursor.
          EXEC SQL CLOSE EMPCURSOR END-EXEC.
           EXEC SQL COMMIT WORK RELEASE END-EXEC.
        STOP RUN.

#### 5.4.8 Positioned Update

The following skeletal example demonstrates positioned update using the universal ROWID, which is defined in "[Universal ROWIDs](datatypes-and-host-variables.md)":

    ...
     01  MY-ROWID SQL-ROWID.
    ...
         EXEC SQL ALLOCATE :MY-ROWID END-EXEC.
         EXEC SQL DECLARE C CURSOR FOR
            SELECT ROWID, ... FROM MYTABLE FOR UPDATE OF ... END-EXEC.
         EXEC SQL OPEN C END-EXEC.
         EXEC SQL FETCH C INTO :MY-ROWID ... END-EXEC.
    * Process retrieved data.
    ...
         EXEC SQL UPDATE MYTABLE SET ... WHERE ROWID = :MY-ROWID END-EXEC.
     ...
     NO-MORE-DATA:
         EXEC SQL CLOSE C END-EXEC.
         EXEC SQL FREE :MY-ROWID END-EXEC.
    ...

#### 5.4.9 The PREFETCH Precompiler Option

The precompiler option PREFETCH allows for more efficient queries by pre-fetching rows. This decreases the number of server round-trips needed and reduces memory required. The number of rows set by the PREFETCH option value in a configuration file or on the command line is used for all queries involving explicit cursors, subject to the standard precedence rules.

When used inline, the PREFETCH option must precede any of these cursor statements:

- EXEC SQL OPEN cursor

- EXEC SQL OPEN cursor USING host_var_list

- EXEC SQL OPEN cursor USING DESCRIPTOR desc_name

When an OPEN is executed, the value of PREFETCH gives the number of rows to be pre-fetched when the query is executed. You can set the value from 0 (no pre-fetching) to 9999. The default value is 1.

**Note:**

The PREFETCH precompiler option is specifically designed for enhancing the performance of single row fetches. PREFETCH values have no effect when doing array fetches, regardless of which value is assigned.

### 5.5 Scrollable Cursors

A scrollable cursor is a work area where Oracle executes SQL statements and stores information that is processed during execution.

When a cursor is executed, the results of the query are placed into a a set of rows called the result set. The result set can be fetched either sequentially or non-sequentially. Non-sequential result sets are called scrollable cursors.

A scrollable cursor enables users to access the rows of a database result set in a forward, backward, and random manner. This enables the program to fetch any row in the result set.

**Related Topics**

- [About Using Scrollable Cursors in OCI](../lnoci/using-sql_statements-in-oci.md)

#### 5.5.1 Using Scrollable Cursors

The following statements let you define and manipulate a scrollable cursor.

##### 5.5.1.1 DECLARE SCROLL CURSOR

You can use the DECLARE \<cursor name\> SCROLL CURSOR statement to name the scrollable cursor and associate it with a query.

##### 5.5.1.2 OPEN

You can use the OPEN statement in the same way as in the case of a non-scrollable cursor.

##### 5.5.1.3 FETCH

You can use the FETCH statement to fetch required rows in a random manner. An application can fetch rows up or down, first or last row directly, or fetch any single row in a random manner.

The following options are available with the FETCH statement.

1.  FETCH FIRST

    Fetches the first row from the result set.

2.  FETCH PRIOR

    Fetches the row prior to the current row.

3.  FETCH NEXT

    Fetches the next row from the current position. This is same as the non-scrollable cursor FETCH.

4.  FETCH LAST

    Fetches the last row from the result set.

5.  FETCH CURRENT

    Fetches the current row.

6.  FETCH RELATIVE n

    Fetches the nth row relative to the current row, where n is the offset.

7.  FETCH ABSOLUTE n

    Fetches the nth row, where n is the offset from the start of the result set.

The following example describes how to FETCH the last record from a result set.

    EXEC SQL DECLARE emp_cursor SCROLL CURSOR FOR
    SELECT ename, sal FROM emp WHERE deptno=20;
    ...
    EXEC SQL OPEN emp_cursor;
    EXEC SQL FETCH LAST emp_cursor INTO :emp_name, :sal;
    EXEC SQL CLOSE emp_cursor;

##### 5.5.1.4 CLOSE

You can use the CLOSE statement in the same way as in the case of a non-scrollable cursor.

**Note:**

You cannot use scrollable cursors for REF cursors.

#### 5.5.2 The CLOSE_ON_COMMIT Precompiler Option

The CLOSE_ON_COMMIT micro precompiler option provides the ability to choose whether or not to close all cursors when a COMMIT is executed and the macro option MODE=ANSI. When MODE=ANSI, CLOSE_ON_COMMIT has the default value YES. Explicitly setting CLOSE_ON_COMMIT=NO results in better performance because cursors will not be closed when a COMMIT is executed, removing the need to re-open the cursors and incur extra parsing.

#### 5.5.3 The PREFETCH Precompiler Option

The precompiler option PREFETCH allows for more efficient queries by pre-fetching a given number of rows. This decreases the number of server round trips needed and reduces overall memory usage. The number of rows set by the PREFETCH option value is used for all queries involving explicit cursors, subject to the standard precedence rules. When used inline, the PREFETCH option must precede any of these cursor statements:

- EXEC SQL OPEN cursor

- EXEC SQL OPEN cursor USING host_var_list

- EXEC SQL OPEN cursor USING DESCRIPTOR desc_name

When an OPEN is executed, the value of PREFETCH gives the number of rows to be pre-fetched when the query is executed. You can set the value from 0 (no pre-fetching) to 65535. The default value is 1.

**Note:**

The default value of the PREFETCH option is 1 - return a single row for each round-trip. If you choose not to use the PREFETCH option, using the command line, you must explicitly disable it by setting the PREFETCH option to 0.

PREFETCH is automatically disabled when LONG or LOB columns are being retrieved.

**Note:**

PREFETCH is used primarily to enhance the performance of single row fetches. PREFETCH has no effect when array fetches are used.

**Note:**

The PREFETCH option should be used wisely, and on a case-by-case basis. Select an appropriate prefetch value that will optimize performance of a specific FETCH statement. To accomplish this, use the inline prefetch option instead of the command line prefetch option.

**Note:**

The performance of many large applications can be improved simply by using indicator variables with host variables in FETCH statements.

To enable precompiler applications to obtain the maximum advantage from the use of the PREFETCH option on single row fetches, it is strongly recommended that you use indicator variables.

### 5.6 Flexible B Area Length

The length of B Area for a Pro\*Cobol program is limited to 72 when the format is set to ANSI. Cobol compilers now can support B Area length up to 253. This provides a programmer with the flexibility to type a line that is longer than 72 columns. Pro\*Cobol now supports B area length up to 253 when a Pro\*Cobol application is precompiled with the

`FORMAT=VARIABLE` ` IRECLEN=300`

options.

### 5.7 Fix Execution Plans

In application development environments where modules are developed in one environment, and then integrated and deployed into another, the performance of the applications are affected. At times, the performance of the precompiler applications are affected by changes in the database environment. These may include changes in the optimizer statistics, changes to the optimizer settings, or changes to parameters affecting the sizes of memory structures.

To fix execution plans for SQL's used in Pro\*Cobol in the development environment, you need to use the outline feature of Oracle at the time of precompiling. An outline is implemented as a set of optimizer hints that are associated with the SQL statement. If you enable the use of the outline for the statement, Oracle automatically considers the stored hints and tries to generate an execution plan in accordance with those hints. In this way, you can ensure that the performance is not affected when the modules are integrated or deployed into different environments.

You can use the following SQL statements to create outlines in Pro\*Cobol:

- `SELECT`

- `DELETE`

- `UPDATE`

- `INSERT... SELECT`

- `CREATE TABLE... AS SELECT`

If the outline option is set, then the precompiler generates two files, a SQL file and a LOG file at the end of successful precompilation. Command line options `outline` and `outlnprefix` control the generation of the outlines.

**See Also:**

[Precompiler Options](precompiler-options.md) for more details on these command line options

Each generated outline name is unique. Because the file names used in the application are unique, this information is used in generating the outline name. In addition, the category name is also prefixed.

**Caution:**

Oracle allows only 128 bytes for the outline name. If you exceed the limit, the precompiler will flag an error. You can restrict the length of the outline name by using the `outlnprefix` option.

Example 5-1 Generating a SQL File Containing Outlines

You need to precompile the following program by using the outline option to generate SQL files containing the outlines for all the outline-supported SQL statements in this program.

     *****************************************************************
          * outlndemo:                                                    *

          * Outlines will be created for the following SQL operations,    *
          * 1. CREATE ... SELECT                                          *
          * 2. INSERT ... SELECT                                          *
          * 3. UPDATE                                                     *
          * 4. DELETE                                                     *
          * 5. SELECT                                                     *
          *****************************************************************

           IDENTIFICATION DIVISION.
           PROGRAM-ID.  outlndemo.
           ENVIRONMENT DIVISION.
           CONFIGURATION SECTION.
           DATA DIVISION.
           WORKING-STORAGE SECTION.

          * EMBEDDED COBOL (file "OUTNDEMO.PCO")

               EXEC SQL BEGIN DECLARE SECTION END-EXEC.
           01  USERNAME          PIC X(10) VARYING.
           01  PASSWD            PIC X(10) VARYING.

           01  ENAME PIC  X(10).
           01  JOB PIC  X(9).
           01  SAL PIC  X(6).
           01  COMM PIC  X(6).

               EXEC SQL END DECLARE SECTION END-EXEC.

           01  STRINGFIELDS.
               02 STR PIC X(18) VARYING.

               EXEC SQL INCLUDE SQLCA END-EXEC.

           PROCEDURE DIVISION.
           BEGIN-PGM.
               EXEC SQL WHENEVER SQLERROR DO PERFORM SQL-ERROR END-EXEC.

               PERFORM LOGON.

     EXEC SQL INSERT INTO BONUS
     SELECT ENAME, JOB, SAL, COMM FROM EMP
     WHERE JOB LIKE 'SALESMAN'
     END-EXEC.

     EXEC SQL UPDATE BONUS
     SET SAL = SAL * 1.1 WHERE SAL < 1500
               END-EXEC.

     EXEC SQL DECLARE C1 CURSOR FOR
     SELECT ENAME, JOB, SAL, COMM FROM BONUS ORDER BY SAL
     END-EXEC.
     EXEC SQL OPEN C1 END-EXEC.
     DISPLAY "Contents of updated BONUS table".
     DISPLAY "ENAME       JOB     SAL  COMM".
     DISPLAY " ".

     EXEC SQL WHENEVER NOT FOUND GOTO END-FETCH END-EXEC.
           FETCH-DATA.
     EXEC SQL FETCH C1 INTO :ENAME, :JOB, :SAL, :COMM END-EXEC.
     DISPLAY ENAME, JOB, SAL, COMM.
     GO TO FETCH-DATA.

           END-FETCH.
     EXEC SQL CLOSE C1 END-EXEC.
               EXEC SQL WHENEVER NOT FOUND DO PERFORM SQL-ERROR END-EXEC.

     EXEC SQL DELETE FROM BONUS END-EXEC.

     EXEC SQL CREATE TABLE OUTLNDEMO_TAB AS
     SELECT EMPNO, ENAME, SAL FROM EMP WHERE DEPTNO = 10
     END-EXEC.

     EXEC SQL DROP TABLE OUTLNDEMO_TAB END-EXEC.

               EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
               STOP RUN.

           LOGON.
               MOVE "scott" TO USERNAME-ARR.
               MOVE 5 TO USERNAME-LEN.
               MOVE "tiger" TO PASSWD-ARR.
               MOVE 5 TO PASSWD-LEN.
               EXEC SQL
                   CONNECT :USERNAME IDENTIFIED BY :PASSWD
               END-EXEC.

          * HANDLES SQL ERROR CONDITIONS
           SQL-ERROR.
               EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.
               DISPLAY " ".
               DISPLAY "ORACLE ERROR DETECTED:".
               DISPLAY " ".
               DISPLAY SQLERRMC.
               EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
               STOP RUN.

#### 5.7.1 SQL File

The generated file name has the following format:

    <filename>_<filetype>.sql

In Pro\*Cobol, for the file "abc.pco", the generated SQL file will be abc_pco.sql.

##### Generated file format

If the outlnprefix option is not used, then the format of the unique identifier used as outline name and comment is:

    <category_name>_<filename>_<filetype>_<sequence no.>

If the outlnprefix option is used (outlnprefix=\<prefix_name\>), then the format of the unique identifier used as outline name and comment is:

    <prefix_name>_<sequence no.>

If outline=yes, which is the default category, then \<category_name\> will be DEFAULT and outline name will be:

    DEFAULT_<filename>_<filetype>_<sequence no.>

or

    <prefix_name>_<sequence no.>

The allowed range for `<sequence no.>` is 0000 to 9999.

SQL in the generated precompiled file will have the comment appended to it as it appears in the outline for that SQL.

##### 5.7.1.1 Examples

Consider the following examples.

##### Example 1

If abc.pco has the statements

    EXEC SQL select * from emp where empno=:var END-EXEC.
    EXEC SQL select * from dept END-EXEC.

and if outline=mycat1 and outlnprefix is not used, then:

##### Contents of abc_pco.sql

create or replace outline mycat1_abc_pco_0000 for category mycat1 on `select * from emp where empno=:b1 /* mycat1_abc_pco_0000 */;`

create or replace outline mycat1_abc_pco_0001 for category mycat1 on `select * from dept /* mycat1_abc_pco_0001 */;`

##### Contents of abc.cob

    01 SQ0001 GLOBAL.
      02 FILLER PIC X(60) VALUE "select * from emp where empno=:b1
      -  /* mycat1_abc_pco_0000 */
    -    "".

##### Example 2

If abc.pco has the statements

    EXEC SQL select * from emp where empno=:var END-EXEC.
    EXEC SQL select * from dept END-EXEC.

and if outline=mycat1 and outlnprefix=myprefix, then:

##### Contents of abc_pco.sql

create or replace outline myprefix_0000 for category mycat1 on `select * from emp where empno=:b1 /* myprefix_0000 */;`

create or replace outline myprefix_0001 for category mycat1 on `select * from dept /* myprefix_0001 */;`

##### Contents of abc.cob

    01 SQ0001 GLOBAL.
      02 FILLER PIC X(60) VALUE "select * from emp where empno=:b1
      -  /* myprefix_0000 */
    - "".

##### Example 3

If abc.pco has the statements

    EXEC SQL select * from emp where empno=:var END-EXEC.
    EXEC SQL select * from dept END-EXEC.

and if outline=yes and outlnprefix=myprefix, then:

##### Contents of abc_pco.sql

create or replace outline myprefix_0000 on `select * from emp where empno=:b1 /* myprefix_0000 */;`

create or replace outline myprefix_0001 on `select * from dept /* myprefix_0001 */;`

##### Contents of abc.cob

    01 SQ0001 GLOBAL.
      03 FILLER PIC X(60) VALUE "select * from emp where empno=:b1
      -  /* myprefix_0000 */
    - "".

#### 5.7.2 LOG File

The generated file name has the following format:

    <filename>_<filetype>.log

In Pro\*Cobol, for the file "abc.pco", the generated LOG file will be abc_pco.log.

Consider the following example.

##### Example 1

If abc.pco has the statement

    EXEC SQL select * from emp END-EXEC.

##### Contents of abc_pco.log

    CATEGORY <Category_name>
         Source SQL_0
            SELECT * FROM emp
         OUTLINE NAME
            abc_pco_0000
         OUTLINE SQL_0
            Select * from emp /* abc_pco_0000 */

### 5.8 Sample Program 2: Cursor Operations

This program logs on to Oracle, declares and opens a cursor, fetches the names, salaries, and commissions of all salespeople, displays the results, then closes the cursor

All fetches except the final one return a row and, if no errors were detected during the fetch, a success status code. The final fetch fails and returns the "no data found" Oracle warning code to SQLCODE in the SQLCA. The cumulative number of rows actually fetched is found in SQLERRD(3) in the SQLCA.

          *****************************************************************
          * Sample Program 2:  Cursor Operations                          *
          *                                                               *
          * This program logs on to ORACLE, declares and opens a cursor,  *
          * fetches the names, salaries, and commissions of all           *
          * salespeople, displays the results, then closes the cursor.    *
          *****************************************************************

           IDENTIFICATION DIVISION.
           PROGRAM-ID. CURSOR-OPS.
           ENVIRONMENT DIVISION.
           DATA DIVISION.
           WORKING-STORAGE SECTION.

               EXEC SQL BEGIN DECLARE SECTION END-EXEC.
           01  USERNAME          PIC X(10) VARYING.
           01  PASSWD            PIC X(10) VARYING.
           01  EMP-REC-VARS.
               05  EMP-NAME      PIC X(10) VARYING.
               05  SALARY        PIC S9(6)V99
                                 DISPLAY SIGN LEADING SEPARATE.
               05  COMMISSION    PIC S9(6)V99
                                 DISPLAY SIGN LEADING SEPARATE.
               EXEC SQL VAR SALARY IS DISPLAY(8,2) END-EXEC.
               EXEC SQL VAR COMMISSION IS DISPLAY(8,2) END-EXEC.
               EXEC SQL END DECLARE SECTION END-EXEC.

               EXEC SQL INCLUDE SQLCA END-EXEC.

           01  DISPLAY-VARIABLES.
               05  D-EMP-NAME    PIC X(10).
               05  D-SALARY      PIC Z(4)9.99.
               05  D-COMMISSION  PIC Z(4)9.99.

           PROCEDURE DIVISION.

           BEGIN-PGM.
               EXEC SQL WHENEVER SQLERROR
                   DO PERFORM SQL-ERROR END-EXEC.
               PERFORM LOGON.
               EXEC SQL DECLARE SALESPEOPLE CURSOR FOR
                   SELECT ENAME, SAL, COMM
                   FROM EMP
                   WHERE JOB LIKE 'SALES%'
               END-EXEC.
               EXEC SQL OPEN SALESPEOPLE END-EXEC.
               DISPLAY " ".
               DISPLAY "SALESPERSON  SALARY      COMMISSION".
               DISPLAY "-----------  ----------  ----------".

           FETCH-LOOP.
               EXEC SQL WHENEVER NOT FOUND
                   DO PERFORM SIGN-OFF END-EXEC.
               EXEC SQL FETCH SALESPEOPLE
                   INTO :EMP-NAME, :SALARY, :COMMISSION
               END-EXEC.
               MOVE EMP-NAME-ARR TO D-EMP-NAME.
               MOVE SALARY TO D-SALARY.
               MOVE COMMISSION TO D-COMMISSION.
               DISPLAY D-EMP-NAME, "     ", D-SALARY, "    ", D-COMMISSION.
               MOVE SPACES TO EMP-NAME-ARR.
               GO TO FETCH-LOOP.

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

           SIGN-OFF.
               EXEC SQL CLOSE SALESPEOPLE END-EXEC.
               DISPLAY " ".
               DISPLAY "HAVE A GOOD DAY.".
               DISPLAY " ".
               EXEC SQL COMMIT WORK RELEASE END-EXEC.
               STOP RUN.

           SQL-ERROR.
               EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.
               DISPLAY " ".
               DISPLAY "ORACLE ERROR DETECTED:".
               DISPLAY " ".
               DISPLAY SQLERRMC.
               EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
               STOP RUN.
