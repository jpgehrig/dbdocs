This chapter helps you to understand and apply the basic techniques of embedded SQL programming. This chapter contains the following topics:

- Host Variables

- Indicator Variables

- The Basic SQL Statements

- The DML Returning Clause

- Cursors

- Scrollable Cursors

- Optimizer Hints

- Fix Execution Plan

- The CURRENT OF Clause

- The Cursor Statements

- A Complete Example Using Non-Scrollable Cursor

- A Complete Example Using Scrollable Cursor

### 6.1 Host Variables

Oracle uses host variables to pass data and status information to your program; your program uses host variables to pass data to Oracle.

#### 6.1.1 Output versus Input Host Variables

Depending on how they are used, host variables are called output or input host variables.

Host variables in the INTO clause of a SELECT or FETCH statement are called output host variables because they hold column values output by Oracle. Oracle assigns the column values to corresponding output host variables in the INTO clause.

All other host variables in a SQL statement are called input host variables because your program inputs their values to Oracle. For example, you use input host variables in the VALUES clause of an INSERT statement and in the SET clause of an UPDATE statement. They are also used in the WHERE, HAVING, and FOR clauses. Input host variables can appear in a SQL statement wherever a value or expression is allowed.

**Note:**

In an ORDER BY clause, you can use a host variable, but it is treated as a constant or literal, and hence the contents of the host variable have no effect. For example, the SQL statement

    EXEC SQL SELECT ename, empno INTO :name,:number FROM emp ORDER BY :ord;

appears to contain an input host variable :ord. However, the host variable in this case is treated as a constant, and regardless of the value of :ord, no ordering is done.

You cannot use input host variables to supply SQL keywords or the names of database objects. Thus, you cannot use input host variables in data definition statements such as ALTER, CREATE, and DROP. In the following example, the DROP TABLE statement is invalid:

    char table_name[30];

    printf("Table name? ");
    gets(table_name);

    EXEC SQL DROP TABLE :table_name;  -- host variable not allowed

If you need to change database object names at runtime, use dynamic SQL.

Before Oracle executes a SQL statement containing input host variables, your program must assign values to them. An example follows:

    int     emp_number;
    char    temp[20];
    VARCHAR emp_name[20];

    /* get values for input host variables */
    printf("Employee number? ");
    gets(temp);
    emp_number = atoi(temp);
    printf("Employee name? ");
    gets(emp_name.arr);
    emp_name.len = strlen(emp_name.arr);

    EXEC SQL INSERT INTO EMP (EMPNO, ENAME)
        VALUES (:emp_number, :emp_name);

Notice that the input host variables in the VALUES clause of the INSERT statement are prefixed with colons.

**Related Topics**

- [Oracle Dynamic SQL](Oracle-dynamic-SQL.md)

### 6.2 Indicator Variables

You can associate any host variable with an optional indicator variable. Each time the host variable is used in a SQL statement, a result code is stored in its associated indicator variable. Thus, indicator variables let you monitor host variables.

**Note:**

You cannot use multiple indicator variables with a single host variable within PL/SQL blocks. Doing so results in a "not all variables bound" error.

You use indicator variables in the VALUES or SET clauses to assign NULLs to input host variables. Use indicator variables in the INTO clause to detect NULLs or truncated values in output host variables.

#### On Input

The values your program can assign to an indicator variable have the following meanings:

| Variable | Description                                                                       |
|:---------|:----------------------------------------------------------------------------------|
| -1       | Oracle will assign a NULL to the column, ignoring the value of the host variable. |
| \>=0     | Oracle will assign the value of the host variable to the column.                  |

#### On Output

The values Oracle can assign to an indicator variable have the following meanings:

| Variable | Description                                                                                                                                                                                    |
|:---------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -1       | The column value is NULL, so the value of the host variable is indeterminate.                                                                                                                  |
| 0        | Oracle assigned an intact column value to the host variable.                                                                                                                                   |
| \>0      | Oracle assigned a truncated column value to the host variable. The integer returned by the indicator variable is the original length of the column value, and SQLCODE in SQLCA is set to zero. |
| -2       | Oracle assigned a truncated column variable to the host variable, but the original column value could not be determined (a LONG column, for example).                                          |

Remember, an indicator variable must be defined as a 2-byte integer and, in SQL statements, must be prefixed with a colon and must immediately follow its host variable.

#### 6.2.1 Insert NULLs

You can use indicator variables to INSERT NULLs. Before the INSERT, for each column you want to be NULL, set the appropriate indicator variable to -1, as shown in the following example:

    set ind_comm = -1;

    EXEC SQL INSERT INTO emp (empno, comm)
         VALUES (:emp_number, :commission:ind_comm);

The indicator variable ind_comm specifies that a NULL is to be stored in the COMM column.

You can hard code the NULL instead, as follows:

    EXEC SQL INSERT INTO emp (empno, comm)
         VALUES (:emp_number, NULL);

While this is less flexible, it might be more readable. Typically, you insert NULLs conditionally, as the next example shows:

    printf("Enter employee number or 0 if not available: ");
    scanf("%d", &emp_number);

    if (emp_number == 0)
        ind_empnum = -1;
    else
        ind_empnum = 0;

    EXEC SQL INSERT INTO emp (empno, sal)
         VALUES (:emp_number:ind_empnum, :salary);

#### 6.2.2 Returned NULLs

You can also use indicator variables to manipulate returned NULLs, as the following example shows:

    EXEC SQL SELECT ename, sal, comm
        INTO :emp_name, :salary, :commission:ind_comm
        FROM emp
        WHERE empno = :emp_number;
     if (ind_comm == -1)
        pay = salary;   /* commission is NULL; ignore it */
    else
        pay = salary + commission;

#### 6.2.3 Fetch NULLs

When DBMS=V7 or DBMS=V8, if you SELECT or FETCH NULLs into a host variable not associated with an indicator variable, Oracle issues the following error message:

    ORA-01405: fetched column value is NULL

**Related Topics**

- [DBMS](precompiler-options.md)

#### 6.2.4 Test for NULLs

You can use indicator variables in the WHERE clause to test for NULLs, as the following example shows:

    EXEC SQL SELECT ename, sal
    INTO :emp_name, :salary
    FROM emp
    WHERE :commission INDICATOR :ind_comm IS NULL ...

However, you cannot use a relational operator to compare NULLs with each other or with other values. For example, the following SELECT statement fails if the COMM column contains one or more NULLs:

    EXEC SQL SELECT ename, sal
    INTO :emp_name, :salary
    FROM emp
    WHERE comm = :commission;

The next example shows how to compare values for equality when some of them might be NULLs:

    EXEC SQL SELECT ename, sal
         INTO :emp_name, :salary
         FROM emp
         WHERE (comm = :commission) OR ((comm IS NULL) AND
              (:commission INDICATOR :ind_comm IS NULL));

#### 6.2.5 Truncated Values

When DBMS=V7 or V8, if you SELECT or FETCH a truncated column value into a host variable not associated with an indicator variable, a warning is generated instead of an error.

### 6.3 The Basic SQL Statements

Executable SQL statements let you query, manipulate, and control Oracle data and create, define, and maintain Oracle objects such as tables, views, and indexes. This chapter focuses on the statements that query and manipulate data.

When executing a data manipulation statement such as INSERT, UPDATE, or DELETE, your only concern, besides setting the values of any input host variables, is whether the statement succeeds or fails. To find out, you simply check the SQLCA. (Executing any SQL statement sets the SQLCA variables.) You can check in the following two ways:

- Implicit checking with the WHENEVER statement

- Explicit checking of SQLCA variables

When executing a SELECT statement (query), however, you must also deal with the rows of data it returns. Queries can be classified as follows:

- Queries that return no rows (that is, merely check for existence)

- Queries that return only one row

- Queries that return more than one row

Queries that return more than one row require explicitly declared cursors or the use of host arrays (host variables declared as arrays).

**Note:**

Host arrays let you process "batches" of rows.

This chapter assumes the use of scalar host variables.

The following embedded SQL statements let you query and manipulate Oracle data:

| Embedded SQL Statements | Description                           |
|:------------------------|:--------------------------------------|
| SELECT                  | Returns rows from one or more tables. |
| INSERT                  | Adds new rows to a table.             |
| UPDATE                  | Modifies rows in a table.             |
| DELETE                  | Removes unwanted rows from a table.   |

The following embedded SQL statements let you define and manipulate an explicit cursor:

| Embedded SQL Statements | Description                                                               |
|:------------------------|:--------------------------------------------------------------------------|
| DECLARE                 | Names the cursor and associates it with a query.                          |
| OPEN                    | Executes the query and identifies the active set.                         |
| FETCH                   | Advances the cursor and retrieves each row in the active set, one by one. |
| CLOSE                   | Disables the cursor (the active set becomes undefined).                   |

The following sections, you first learn how to code INSERT, UPDATE, DELETE, and single-row SELECT statements. Then, you progress to multirow SELECT statements.

**Related Topics**

- [Handling Runtime Errors](handling-run-time-errors.md)
- [Host Arrays](host-arrays.md)
- [Embedded SQL Statements and Directives](embedded-SQL-statements-and-directives.md)
- [Oracle Database SQL Language Reference](../sqlrf/index.md)

#### 6.3.1 The SELECT Statement

Querying the database is a common SQL operation. To issue a query you use the SELECT statement. In the following example, you query the EMP table:

    EXEC SQL SELECT ename, job, sal + 2000
    INTO :emp_name, :job_title, :salary
    FROM emp
    WHERE empno = :emp_number;

The column names and expressions following the keyword SELECT make up the select list. The select list in our example contains three items. Under the conditions specified in the WHERE clause (and following clauses, if present), Oracle returns column values to the host variables in the INTO clause.

The number of items in the select list should equal the number of host variables in the INTO clause, so there is a place to store every returned value.

In the simplest case, when a query returns one row, its form is that shown in the last example. However, if a query can return more than one row, you must FETCH the rows using a cursor or SELECT them into a host-variable array. Cursors and the FETCH statement are discussed later in this chapter.

If a query is written to return only one row but might actually return several rows, the result of the SELECT is indeterminate. Whether this causes an error depends on how you specify the SELECT_ERROR option. The default value, YES, generates an error if more than one row is returned.

**Related Topics**

- [Host Arrays](embedded-PL-SQL.md)

##### 6.3.1.1 Available Clauses

You can use all of the following standard SQL clauses in your

SELECT statements:

- INTO

- FROM

- WHERE

- CONNECT BY

- START WITH

- GROUP BY

- HAVING

- ORDER BY

- FOR UPDATE OF

Except for the INTO clause, the text of embedded SELECT statements can be executed and tested interactively using SQL\*Plus. In SQL\*Plus, you use substitution variables or constants instead of input host variables.

#### 6.3.2 The INSERT Statement

Use the INSERT statement to add rows to a table or view. In the following example, you add a row to the EMP table:

    EXEC SQL INSERT INTO emp (empno, ename, sal, deptno)
    VALUES (:emp_number, :emp_name, :salary, :dept_number);

Each column you specify in the column list must belong to the table named in the INTO clause. The VALUES clause specifies the row of values to be inserted. The values can be those of constants, host variables, SQL expressions, SQL functions such as USER and SYSDATE, or user-defined PL/SQL functions.

The number of values in the VALUES clause must equal the number of names in the column list. However, you can omit the column list if the VALUES clause contains a value for each column in the table, in the order that they are defined in the table.

**Related Topics**

- [INSERT (Executable Embedded SQL)](embedded-SQL-statements-and-directives.md)

##### 6.3.2.1 About Using Subqueries

A subquery is a nested SELECT statement. Subqueries let you conduct multipart searches. They can be used to

- Supply values for comparison in the WHERE, HAVING, and START WITH clauses of SELECT, UPDATE, and DELETE statements

- Define the set of rows to be inserted by a CREATE TABLE or INSERT statement

- Define values for the SET clause of an UPDATE statement

The following example uses a subquery in an INSERT statement to copy rows from one table to another:

    EXEC SQL INSERT INTO emp2 (empno, ename, sal, deptno)
    SELECT empno, ename, sal, deptno FROM emp
    WHERE job= :job_title ;

This INSERT statement uses the subquery to obtain intermediate results.

#### 6.3.3 The UPDATE Statement

Use the UPDATE statement to change the values of specified columns in a table or view. In the following example, we update the `SAL` and `COMM` columns in the` EMP` table:

    EXEC SQL UPDATE emp
    SET sal = :salary, comm = :commission
    WHERE empno = :emp_number;

Use the optional WHERE clause to specify the conditions under which rows are updated.

The SET clause lists the names of one or more columns for which you must provide values. You can use a subquery to provide the values, as the following example shows:

    EXEC SQL UPDATE emp
    SET sal = (SELECT AVG(sal)*1.1 FROM emp WHERE deptno = 20)
    WHERE empno = :emp_number;

The UPDATE statement has an optional `returning clause`, like the INSERT and DELETE statements. It is only allowed after the optional WHERE condition.

**Related Topics**

- The WHERE Clause
- [UPDATE (Executable Embedded SQL)](embedded-SQL-statements-and-directives.md)

#### 6.3.4 The DELETE Statement

Use the DELETE statement to remove rows from a table or view. In the following example, you delete all employees in a given department from the EMP table:

    EXEC SQL DELETE FROM emp
    WHERE deptno = :dept_number ;

We have used the optional WHERE clause to specify the condition under which rows are deleted.

The `returning clause` option can be used in DELETE statements also. It is allowed after the optional WHERE condition. In the earlier example, it is good practice to record the field values of each employee that is deleted.

**Related Topics**

- [DELETE (Executable Embedded SQL)](embedded-SQL-statements-and-directives.md)

#### 6.3.5 The WHERE Clause

Use the WHERE clause to SELECT, UPDATE, or DELETE only those rows in a table or view that meet your search condition. The WHERE-clause search condition is a Boolean expression, which can include scalar host variables, host arrays (not in SELECT statements), subqueries, and user-defined stored functions.

If you omit the WHERE clause, all rows in the table or view are processed. If you omit the WHERE clause in an UPDATE or DELETE statement, Oracle sets `sqlwarn[4]` in the SQLCA to 'W' to warn that all rows were processed.

### 6.4 The DML Returning Clause

The INSERT, UPDATE, and DELETE statements can have an optional DML returning clause which returns column value expressions expr, into host variables hv, with host indicator variables iv. The DML returning clause looks like this:

    {RETURNING | RETURN} {expr [,expr]}
        INTO {:hv [[INDICATOR]:iv] [, :hv [[INDICATOR]:iv]]}

The number of expressions must equal the number of host variables. This clause eliminates the need for selecting the rows after an INSERT or UPDATE, and before a DELETE when you need to record that information for your application. The `returning clause` eliminates inefficient network round trips, extra processing, and server memory.

Oracle Dynamic SQL Method 4 does not support the DML returning clause; but ANSI Dynamic SQL Method 4 does. Support for DML statements with a DML returning clause that affects more than a single row is not supported by ANSI DYNAMIC SQL.

**Related Topics**

- [ANSI Dynamic SQL](ANSI-dynamic-SQL.md)

### 6.5 Cursors

When a query returns multiple rows, you can explicitly define a cursor to

- Process beyond the first row returned by the query

- Keep track of which row is currently being processed

Or, you can use host arrays.

A cursor identifies the current row in the set of rows returned by the query. This allows your program to process the rows one at a time. The following statements let you define and manipulate a cursor:

- DECLARE CURSOR

- OPEN

- FETCH

- CLOSE

First you use the DECLARE CURSOR statement to name the cursor and associate it with a query.

The OPEN statement executes the query and identifies all the rows that meet the query search condition. These rows form a set called the active set of the cursor. After OPENing the cursor, you can use it to retrieve the rows returned by its associated query.

Rows of the active set are retrieved one by one (unless you use host arrays). You use a FETCH statement to retrieve the current row in the active set. You can execute FETCH repeatedly until all rows have been retrieved.

When done FETCHing rows from the active set, you disable the cursor with a CLOSE statement, and the active set becomes undefined.

The following sections show you how to use these cursor control statements in your application program.

**Related Topics**

- [Host Arrays](embedded-PL-SQL.md)

#### 6.5.1 The DECLARE CURSOR Statement

You use the DECLARE CURSOR statement to define a cursor by giving it a name and associating it with a query, as the following example shows:

    EXEC SQL DECLARE emp_cursor CURSOR FOR
         SELECT ename, empno, sal
         FROM emp
         WHERE deptno = :dept_number;

The cursor name is an identifier used by the precompiler, not a host or program variable, and should not be defined in the Declare Section. Therefore, cursor names cannot be passed from one precompilation unit to another. Cursor names cannot be hyphenated. They can be any length, but only the first 31 characters are significant. For ANSI compatibility, use cursor names no longer than 18 characters.

The precompiler option CLOSE_ON_COMMIT is provided for use in the command line or in a configuration file. Any cursor not declared with the WITH HOLD clause is closed after a COMMIT or ROLLBACK when CLOSE_ON_COMMIT=YES.

If MODE is specified at a higher level than CLOSE_ON_COMMIT, then MODE takes precedence. The defaults are MODE=ORACLE and CLOSE_ON_COMMIT=NO. If you specify MODE=ANSI then any cursors not using the WITH HOLD clause will be closed on COMMIT. The application will run more slowly because cursors are closed and re-opened many times. Setting CLOSE_ON_COMMIT=NO when MODE=ANSI results in performance improvement. To see how macro options such as MODE affect micro options such as CLOSE_ON_COMMIT, see "[Precedence of Option Values](precompiler-options.md)".

The SELECT statement associated with the cursor cannot include an INTO clause. Rather, the INTO clause and list of output host variables are part of the FETCH statement.

Because it is declarative, the DECLARE CURSOR statement must physically (not just logically) precede all other SQL statements referencing the cursor. That is, forward references to the cursor are not allowed. In the following example, the OPEN statement is misplaced:

    ...
    EXEC SQL OPEN emp_cursor;
    *    -- MISPLACED OPEN STATEMENT
    EXEC SQL DECLARE emp_cursor CURSOR FOR
    SELECT ename, empno, sal
        FROM emp
        WHERE ename = :emp_name;

The cursor control statements (DECLARE, OPEN, FETCH, CLOSE) must all occur within the same precompiled unit. For example, you cannot DECLARE a cursor in file A, then OPEN it in file B.

Your host program can DECLARE as many cursors as it needs. However, in a given file, every DECLARE statement must be unique. That is, you cannot DECLARE two cursors with the same name in one precompilation unit, even across blocks or procedures, because the scope of a cursor is global within a file.

For users of MODE=ANSI or CLOSE_ON_COMMIT=YES, the WITH HOLD clause can be used in a DECLARE section to override the behavior defined by the two options. With these options set, the behavior will be for all cursors to be closed when a COMMIT is issued. This can have performance implications due to the overhead of re-opening the cursor to continue processing. The careful use of WITH HOLD can speed up programs that need to conform to the ANSI standard for precompilers in most respects.

If you will be using many cursors, you might want to specify the MAXOPENCURSORS option.

**Related Topics**

- [WITH HOLD Clause in DECLARE CURSOR Statements](database-concepts.md)
- [CLOSE_ON_COMMIT](precompiler-options.md)
- [Precompiler Options](precompiler-options.md)
- [Performance Tuning](performance-tuning.md)

#### 6.5.2 The OPEN Statement

You use the OPEN statement to execute the query and identify the active set. In the following example, you OPEN a cursor named emp_cursor:

    EXEC SQL OPEN emp_cursor;


OPEN zeroes the rows-processed count kept by the third element of SQLERRD in the SQLCA. However, none of the rows are visible to the application at this point. That is handled by the FETCH statement.

OPEN positions the cursor just before the first row of the active set. It also zeroes the rows-processed count kept by the third element of SQLERRD in the SQLCA. However, none of the rows is actually retrieved at this point. That will be done by the FETCH statement.

Once you OPEN a cursor, the query's input host variables are not re-examined until you reOPEN the cursor. Thus, the active set does not change. To change the active set, you must reOPEN the cursor.

Generally, you should CLOSE a cursor before reOPENing it. However, if you specify MODE=ORACLE (the default), you need not CLOSE a cursor before reOPENing it. This can increase performance.

The amount of work done by OPEN depends on the values of three precompiler options: HOLD_CURSOR, RELEASE_CURSOR, and MAXOPENCURSORS.

**Related Topics**

- [About Using the Precompiler Options](precompiler-options.md)

#### 6.5.3 The FETCH Statement

You use the FETCH statement to retrieve rows from the active set and specify the output host variables that will contain the results. Recall that the SELECT statement associated with the cursor cannot include an INTO clause. Rather, the INTO clause and list of output host variables are part of the FETCH statement. In the following example, you FETCH INTO three host variables:

    EXEC SQL FETCH emp_cursor
    INTO :emp_name, :emp_number, :salary;


The cursor must have been previously DECLAREd and OPENed. The first time you execute FETCH, the cursor moves from before the first row in the active set to the first row. This row becomes the current row. Each subsequent execution of FETCH advances the cursor to the next row in the active set, changing the current row. The cursor can only move forward in the active set. To return to a row that has already been FETCHed, you must reOPEN the cursor, then begin again at the first row of the active set.

If you want to change the active set, you must assign new values to the input host variables in the query associated with the cursor, then reOPEN the cursor. When MODE=ANSI, you must CLOSE the cursor before reOPENing it.

As the next example shows, you can FETCH from the same cursor using different sets of output host variables. However, corresponding host variables in the INTO clause of each FETCH statement must have the same datatype.

    EXEC SQL DECLARE emp_cursor CURSOR FOR
    SELECT ename, sal FROM emp WHERE deptno = 20;
    ...
    EXEC SQL OPEN emp_cursor;

    EXEC SQL WHENEVER NOT FOUND GOTO ...
    for (;;)
    {
        EXEC SQL FETCH emp_cursor INTO :emp_name1, :salary1;
        EXEC SQL FETCH emp_cursor INTO :emp_name2, :salary2;
        EXEC SQL FETCH emp_cursor INTO :emp_name3, :salary3;
        ...
    }

If the active set is empty or contains no more rows, FETCH returns the "no data found" error code to sqlcode in the SQLCA, or to the SQLCODE or SQLSTATE status variables. The status of the output host variables is indeterminate. (In a typical program, the WHENEVER NOT FOUND statement detects this error.) To reuse the cursor, you must reOPEN it.

It is an error to FETCH on a cursor under the following conditions:

- Before OPENing the cursor

- After a "no data found" condition

- After CLOSEing it

#### 6.5.4 The CLOSE Statement

When done FETCHing rows from the active set, you CLOSE the cursor to free the resources, such as storage, acquired by OPENing the cursor. When a cursor is closed, parse locks are released. What resources are freed depends on how you specify the HOLD_CURSOR and RELEASE_CURSOR options. In the following example, you CLOSE the cursor named emp_cursor:

    EXEC SQL CLOSE emp_cursor;

You cannot FETCH from a closed cursor because its active set becomes undefined. If necessary, you can reOPEN a cursor (with new values for the input host variables, for example).

When MODE=ORACLE, issuing a COMMIT or ROLLBACK closes cursors referenced in a CURRENT OF clause. Other cursors are unaffected by COMMIT or ROLLBACK and if open, remain open. However, when MODE=ANSI, issuing a COMMIT or ROLLBACK closes all explicit cursors.

**Related Topics**

- [Database Concepts](database-concepts.md)

### 6.6 Scrollable Cursors

A scrollable cursor is a work area where Oracle executes SQL statements and stores information that is processed during execution.

When a cursor is executed, the results of the query are placed into a a set of rows called the result set. The result set can be fetched either sequentially or non-sequentially. Non-sequential result sets are called scrollable cursors.

A scrollable cursor enables users to access the rows of a database result set in a forward, backward, and random manner. This enables the program to fetch any row in the result set. See Oracle Call Interface Programmer's Guide, Release 9.2.0.

#### 6.6.1 About Using Scrollable Cursors

The following statements let you define and manipulate a scrollable cursor.

##### 6.6.1.1 DECLARE SCROLL CURSOR

You can use the DECLARE \<cursor name\> SCROLL CURSOR statement to name the scrollable cursor and associate it with a query.

##### 6.6.1.2 OPEN for Scrollable Cursors

You can use the OPEN statement in the same way as in the case of a non-scrollable cursor.

##### 6.6.1.3 FETCH for Scrollable Cursors

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

##### 6.6.1.4 CLOSE for Scrollable Cursors

You can use the CLOSE statement in the same way as in the case of a non-scrollable cursor.

**Note:**

You cannot use scrollable cursors for REF cursors.

#### 6.6.2 The CLOSE_ON_COMMIT Precompiler Option

The CLOSE_ON_COMMIT micro precompiler option provides the ability to choose whether or not to close all cursors when a COMMIT is executed and the macro option MODE=ANSI. When MODE=ANSI, CLOSE_ON_COMMIT has the default value YES. Explicitly setting CLOSE_ON_COMMIT=NO results in better performance because cursors will not be closed when a COMMIT is executed, removing the need to re-open the cursors and incur extra parsing.

#### 6.6.3 The PREFETCH Precompiler Option

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

The PREFETCH option should be used wisely, and on a case-by-case basis. Select an appropriate PREFETCH value that will optimize performance of a specific FETCH statement. To accomplish this, use the inline prefetch option instead of the command line prefetch option.

**Note:**

The performance of many large applications can be improved simply by using indicator variables with host variables in FETCH statements.

To enable precompiler applications to obtain the maximum advantage from the use of the PREFETCH option on single row fetches, it is strongly recommended that you use indicator variables.

### 6.7 Optimizer Hints

The Pro\*C/C++ Precompiler supports optimizer hints in SQL statements. An optimizer hint is a suggestion to the Oracle SQL optimizer that can override the optimization approach that would normally be taken. You can use hints to specify the

- Optimization approach for a SQL statement

- Access path for each referenced table

- Join order for a join

- Method used to join tables

Hints allow you to choose between rule-based and cost-based optimization. With cost-based optimization, you can use further hints to maximize throughput or response time.

#### 6.7.1 Issuing Hints

You can issue an optimizer hint inside a C or C++ style comment, immediately after a SELECT, DELETE, or UPDATE command. You indicate that the comment contains one or more hints by following the comment opener with a plus sign, leaving no space between the opener and the '+'. For example, the following statement uses the ALL_ROWS hint to let the cost-based approach optimize the statement for the goal of best throughput:

    EXEC SQL SELECT /*+ ALL_ROWS (cost-based) */ empno, ename, sal, job
        INTO :emp_rec FROM emp
        WHERE deptno = :dept_number;

As shown in this statement, the comment can contain optimizer hints as well as other comments.

### 6.8 Fix Execution Plan

In application development environments where modules are developed in one environment, and then integrated and deployed into another, the performance of the applications are affected. At times, the performance of the precompiler applications are affected by changes in the database environment. These may include changes in the optimizer statistics, changes to the optimizer settings, or changes to parameters affecting the sizes of memory structures.

To fix execution plans for SQL's used in Pro\*C/C++ in the development environment, you need to use the outline feature of Oracle at the time of precompiling. An outline is implemented as a set of optimizer hints that are associated with the SQL statement. If you enable the use of the outline for the statement, Oracle automatically considers the stored hints and tries to generate an execution plan in accordance with those hints. In this way, you can ensure that the performance is not affected when the modules are integrated or deployed into different environments.

You can use the following SQL statements to create outlines in Pro\*C/C++:

- `SELECT`

- `DELETE`

- `UPDATE`

- `INSERT ... SELECT`

- `CREATE TABLE ... AS SELECT`

If the outline option is set, then the precompiler generates two files, a SQL file and a LOG file at the end of successful precompilation. Command line options `outline` and `outlnprefix` control the generation of the outlines.

Each generated outline name is unique. Because the file names used in the application are unique, this information is used in generating the outline name. In addition, the category name is also prefixed.

**Caution:**

Oracle allows only 128 bytes for the outline name. If you exceed the limit, the precompiler will flag an error. You can restrict the length of the outline name by using the `outlnprefix` option.

Example 6-1 Generating a SQL File Containing Outlines

You need to precompile the following program by using the outline option to generate SQL files containing the outlines for all the outline-supported SQL statements in this program.

    /*
     * outlndemo.pc
     *
     * Outlines will be created for the following SQL operations,
     * 1. CREATE ... SELECT
     * 2. INSERT ... SELECT
     * 3. UPDATE
     * 4. DELETE
     * 5. SELECT
     */

    #include <stdio.h>
    #include <string.h>
    #include <stdlib.h>
    #include <sqlda.h>
    #include <sqlcpr.h>
    #include <sqlca.h>

    /* Error handling function. */
    void sql_error(char *msg)
    {
      exec sql whenever sqlerror continue;

      printf("\n%s\n", msg);
      printf("%.70s\n", sqlca.sqlerrm.sqlerrmc);
      exec sql rollback release;

      exit(EXIT_FAILURE);
    }

    int main()
    {
      varchar ename[10];
      varchar job[9];
      float sal, comm;

      exec sql begin declare section;
        char *uid = "scott/tiger";
      exec sql end declare section;

      exec sql whenever sqlerror do sql_error("ORACLE error--\n");
      exec sql connect :uid;

      exec sql insert into bonus
               select ename, job, sal, comm from emp where job like 'SALESMAN';

      exec sql update bonus set sal = sal * 1.1 where sal < 1500;

      exec sql declare c1 cursor for
               select ename, job, sal, comm from bonus order by sal;
      exec sql open c1;
      printf ("Contents of updated BONUS table\n\n");
      printf ("ENAME       JOB        SALARY   COMMISSION\n\n");
      exec sql whenever not found do break;
      while (1)
      {
        exec sql fetch c1 into :ename, :job, :sal, :comm;
        ename.arr[ename.len]='\0';
        job.arr[job.len]='\0';
        printf ("%-9s %-9s   %8.2f    %8.2f\n", ename.arr,
                job.arr, sal, comm);
      }
      exec sql close c1;
      exec sql whenever not found do sql_error("ORACLE error--\n");

      exec sql delete from bonus;

      exec sql create table outlndemo_tab as
               select empno, ename, sal from emp where deptno = 10;

      /* Outline will not be created for this DDL statement */
      exec sql drop table outlndemo_tab;

      exec sql rollback work release;
      exit(EXIT_SUCCESS);
    }

#### 6.8.1 SQL File

The generated file name has the following format:

    <filename>_<filetype>.sql

In Pro\*C, for the file "abc.pc", the generated SQL file will be abc_pc.sql.

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

##### 6.8.1.1 Examples

Consider the following examples.

##### Example 1

If abc.pc has the statements

    EXEC SQL select * from emp where empno=:var;
    EXEC SQL select * from dept;

and if outline=mycat1 and outlnprefix is not used, then:

##### Contents of abc_pc.sql

create or replace outline mycat1_abc_pc_0000 for category mycat1 on `select * from emp where empno=:b1 /* mycat1_abc_pc_0000 */``;`

create or replace outline mycat1_abc_pc_0001 for category mycat1 on `select * from dept /* mycat1_abc_pc_0001 */;`

##### Contents of abc.c

    sqlstm.stmt = select * from emp where empno=:b1 /* mycat1_abc_pc_0000 */;

    sqlstm.stmt = select * from dept /* mycat1_abc_pc_0001 */;

##### Example 2

If abc.pc has the statements

    EXEC SQL select * from emp where empno=:var;
    EXEC SQL select * from dept;

and if outline=mycat1 and outlnprefix=myprefix, then:

##### Contents of abc_pc.sql

create or replace outline myprefix_0000 for category mycat1 on `select * from emp where empno=:b1 /* myprefix_0000 */;`

create or replace outline myprefix_0001 for category mycat1 on `select * from dept /* myprefix_0001 */;`

##### Contents of abc.c

    sqlstm.stmt = select * from emp where empno=:b1 /* myprefix_0000 */;

    sqlstm.stmt = select * from dept /* myprefix_0001 */;

##### Example 3

If abc.pc has the statements

    EXEC SQL select * from emp where empno=:var;
    EXEC SQL select * from dept;

and if outline=yes and outlnprefix=myprefix, then:

##### Contents of abc_pc.sql

create or replace outline myprefix_0000 on `select * from emp where empno=:b1 /* myprefix_0000 */;`

create or replace outline myprefix_0001 on `select * from dept /* myprefix_0001 */;`

##### Contents of abc.c

    sqlstm.stmt = "select * from emp where empno=:b1 /* myprefix_0000 */;

    sqlstm.stmt = "select * from dept /* myprefix_0001 */";

#### 6.8.2 LOG File

The generated file name has the following format:

    <filename>_<filetype>.log

In Pro\*C, for the file "abc.pc", the generated LOG file will be abc_pc.log.

Consider the following example.

##### Example 1

If abc.pc has the statements

    EXEC SQL select * from emp;

##### Contents of abc_pc.log

    CATEGORY <Category_name>
         Source SQL_0
            SELECT * FROM emp
         OUTLINE NAME
            abc_pc_0000
         OUTLINE SQL_0
            Select * from emp /* abc_pc_0000 */

### 6.9 The CURRENT OF Clause

You use the CURRENT OF cursor_name clause in a DELETE or UPDATE statement to refer to the latest row FETCHed from the named cursor. The cursor must be open and positioned on a row. If no FETCH has been done or if the cursor is not open, the CURRENT OF clause results in an error and processes no rows.

The FOR UPDATE OF clause is optional when you DECLARE a cursor that is referenced in the CURRENT OF clause of an UPDATE or DELETE statement. The CURRENT OF clause signals the precompiler to add a FOR UPDATE clause if necessary.

In the following example, you use the CURRENT OF clause to refer to the latest row FETCHed from a cursor named emp_cursor:

    EXEC SQL DECLARE emp_cursor CURSOR FOR
         SELECT ename, sal FROM emp WHERE job = 'CLERK'
         FOR UPDATE OF sal;
    ...
    EXEC SQL OPEN emp_cursor;
    EXEC SQL WHENEVER NOT FOUND GOTO ...
    for (;;) {
        EXEC SQL FETCH emp_cursor INTO :emp_name, :salary;
        ...
        EXEC SQL UPDATE emp SET sal = :new_salary
             WHERE CURRENT OF emp_cursor;
    }

**Related Topics**

- [Using FOR UPDATE OF](database-concepts.md)

#### 6.9.1 Restrictions (FOR UPDATE OF)

You cannot use CURRENT OF clause on an index-organized table.

Explicit FOR UPDATE OF clauses or implicit FOR UPDATE clauses acquire exclusive row locks. All rows are locked at the OPEN, not as they are FETCHed, and are released when you COMMIT or ROLLBACK. Therefore, you cannot FETCH from a FOR UPDATE cursor after a COMMIT. If you try to do this, Oracle returns a 1002 error code.

Also, you cannot use host arrays with the CURRENT OF clause. For an alternative, see also "[About Mimicking CURRENT OF](host-arrays.md) ".

Furthermore, you cannot reference multiple tables in an associated FOR UPDATE OF clause, which means that you cannot do joins with the CURRENT OF clause.

Finally, you cannot use dynamic SQL with the CURRENT OF clause.

### 6.10 The Cursor Statements

The following example shows the typical sequence of cursor control statements in an application program:

       ...
    /* define a cursor */
       EXEC SQL DECLARE emp_cursor CURSOR FOR
            SELECT ename, job
            FROM emp
            WHERE empno = :emp_number
            FOR UPDATE OF job;

    /* open the cursor and identify the active set */
       EXEC SQL OPEN emp_cursor;

    /* break if the last row was already fetched */
       EXEC SQL WHENEVER NOT FOUND DO break;

    /* fetch and process data in a loop */
       for (;;)
       {
          EXEC SQL FETCH emp_cursor INTO :emp_name, :job_title;

    /* optional host-language statements that operate on
       the FETCHed data */

          EXEC SQL UPDATE emp
               SET job = :new_job_title
               WHERE CURRENT OF emp_cursor;
       }
    ...
    /* disable the cursor */
       EXEC SQL CLOSE emp_cursor;
       EXEC SQL COMMIT WORK RELEASE;
       ...

### 6.11 A Complete Example Using Non-Scrollable Cursor

The following complete program illustrates the use of a cursor and the FETCH statement. The program prompts for a department number, then displays the names of all employees in that department.

All FETCHes except the final one return a row and, if no errors were detected during the FETCH, a success status code. The final FETCH fails and returns the "no data found" Oracle error code to sqlca.sqlcode. The cumulative number of rows actually FETCHed is found in `sqlerrd[2]` in the SQLCA.

    #include <stdio.h>

    /* declare host variables */
    char userid[12] = "SCOTT/TIGER";
    char emp_name[10];
    int  emp_number;
    int  dept_number;
    char temp[32];
    void sql_error();

    /* include the SQL Communications Area */
    #include <sqlca.h>

    main()
    {  emp_number = 7499;
    /* handle errors */
       EXEC SQL WHENEVER SQLERROR do sql_error("Oracle error");

    /* connect to Oracle */
       EXEC SQL CONNECT :userid;
       printf("Connected.\n");

    /* declare a cursor */
       EXEC SQL DECLARE emp_cursor CURSOR FOR
       SELECT ename
          FROM emp
          WHERE deptno = :dept_number;

       printf("Department number? ");
       gets(temp);
       dept_number = atoi(temp);

    /* open the cursor and identify the active set */
       EXEC SQL OPEN emp_cursor;

       printf("Employee Name\n");
       printf("-------------\n");
    /* fetch and process data in a loop
       exit when no more data */
       EXEC SQL WHENEVER NOT FOUND DO break;
       while (1)
       {
          EXEC SQL FETCH emp_cursor INTO :emp_name;
          printf("%s\n", emp_name);
       }
       EXEC SQL CLOSE emp_cursor;
       EXEC SQL COMMIT WORK RELEASE;
       exit(0);
    }

    void
    sql_error(msg)
    char *msg;
    {
       char buf[500];
       int buflen, msglen;

       EXEC SQL WHENEVER SQLERROR CONTINUE;
       EXEC SQL ROLLBACK WORK RELEASE;
       buflen = sizeof (buf);
       sqlglm(buf, &buflen, &msglen);
       printf("%s\n", msg);
       printf("%*.s\n", msglen, buf);
       exit(1);
    }

### 6.12 A Complete Example Using Scrollable Cursor

The following program illustrates the use of scrollable cursor and the various options used by the FETCH statement.

    #include <stdio.h>

    /* declare host variables */
    char userid[12]="SCOTT/TIGER";
    char emp_name[10];
    void sql_error();

    /*  include the SQL Communications Area */
    #include<sqlca.h>

    main()
    {
    /* handle errors */
        EXEC SQL WHENEVER SQLERROR do sql_error("Oracle error");

    /* connect to Oracle */
        EXEC SQL CONNECT :userid;
        printf("Connected.\n");

    /* declare a scrollable cursor */
        EXEC SQL DECLARE emp_cursor SCROLL CURSOR FOR
        SELECT ename FROM emp;

    /* open the cursor and identify the active set */
         EXEC SQL OPEN emp_cursor;

     /* Fetch the last row */
         EXEC SQL FETCH LAST emp_cursor INTO :emp_name;

     /* Fetch row number 5 */
          EXEC SQL FETCH ABSOLUTE 5 emp_cursor INTO :emp_name;

    /*  Fetch row number 10 */
           EXEC SQL FETCH RELATIVE 5 emp_cursor INTO :emp_name;

    /*  Fetch row number 7 */
           EXEC SQl FETCH RELATIVE -3 emp_cursor INTO :emp_name;

    /*  Fetch the first row */
           EXEC SQL FETCH FIRST emp_cursor INTO :emp_name;

    /*  Fetch row number 2*/
           EXEC SQL FETCH my_cursor INTO :emp_name;

    /*  Fetch row number 3 */
           EXEC SQL FETCH NEXT my_cursor INTO :emp_name;

    /*  Fetch row number 3 */
           EXEC SQL FETCH CURRENT my_cursor INTO :emp_name;

    /*  Fetch row number 2 */
            EXEC SQL FETCH PRIOR my_cursor INTO :emp_name;
    }

    void
    sql_error(msg)
    char *msg;
    {
         char buf[500];
         int buflen , msglen;

         EXEC SQL WHENEVER SQLERROR  CONTINUE;
         EXEC SQL ROLLBACK TRANSACTION;
         buflen = sizeof (buf);
         sqlglm(buf, &buflen, &mesglen);
         printf("%s\n",msg);
         printf("%*.s\n",msglen,buf);
         exit(1);
    }

### 6.13 Positioned Update

The following skeletal example demonstrates positioned update using the universal ROWID.

    #include <oci.h>
    ...
    OCIRowid *urowid;
    ...
    EXEC SQL ALLOCATE :urowid;
    EXEC SQL DECLARE cur CURSOR FOR
        SELECT rowid, ... FROM my_table FOR UPDATE OF ...;
    EXEC SQL OPEN cur;
    EXEC SQL FETCH cur INTO :urowid, ...;
    /* Process data */
    ...
    EXEC SQL UPDATE my_table SET ... WHERE CURRENT OF cur;
    EXEC SQL CLOSE cur;
    EXEC SQL FREE :urowid;
    ...

**Related Topics**

- [Universal ROWIDs](datatypes-and-host-variables.md)
