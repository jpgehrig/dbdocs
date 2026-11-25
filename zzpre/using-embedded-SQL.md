This chapter contains the following:

- About Using Host Variables

- About Using Indicator Variables

- The Basic SQL Statements

- Cursors

- Cursor Variables

This chapter helps you to understand and apply the basic techniques of embedded SQL programming. You learn how to use host variables, indicator variables, cursors, cursor variables, and the fundamental SQL commands that insert, update, select, and delete Oracle data.

### 4.1 About Using Host Variables

Oracle uses host variables to pass data and status information to your program; your program uses host variables to pass data to Oracle.

#### 4.1.1 Output versus Input Host Variables

Depending on how they are used, host variables are called output or input host variables. Host variables in the `INTO` clause of a `SELECT` or `FETCH` statement are called output host variables because they hold column values output by Oracle. Oracle assigns the column values to corresponding output host variables in the `INTO` clause.

All other host variables in a SQL statement are called input host variables because your program inputs their values to Oracle. For example, you use input host variables in the `VALUES` clause of an `INSERT` statement and in the `SET` clause of an `UPDATE` statement. They are also used in the `WHERE`, `HAVING`, and `FOR` clauses. In fact, input host variables can appear in a SQL statement wherever a value or expression is allowed.

In an `ORDER` `BY` clause, you can use a host variable, but it is treated as a constant or literal, and hence the contents of the host variable have no effect. For example, the SQL statement

    EXEC SQL SELECT ename, empno INTO :name, :number
     FROM emp
     ORDER BY :ord;

appears to contain an input host variable, ord. However, the host variable in this case is treated as a constant, and regardless of the value of ord, no ordering is done.

You cannot use input host variables to supply SQL keywords or the names of database objects. Thus, you cannot use input host variables in data definition statements (sometimes called DDL) such as `ALTER`, `CREATE`, and `DROP`. In the following example, the `DROP` `TABLE` statement is invalid:

    EXEC SQL BEGIN DECLARE SECTION;
     table_name CHARACTER(30);
    EXEC SQL END DECLARE SECTION;
    display 'Table name? ';
    read table_name;
    EXEC SQL DROP TABLE :table_name; -- host variable not allowed

Before Oracle executes a SQL statement containing input host variables, your program must assign values to them. Consider the following example:

    EXEC SQL BEGIN DECLARE SECTION;
     emp_number INTEGER;
     emp_name CHARACTER(20);
    EXEC SQL END DECLARE SECTION;
    -- get values for input host variables
    display 'Employee number? ';
    read emp_number;
    display 'Employee name? ';
    read emp_name;
    EXEC SQL INSERT INTO EMP (EMPNO, ENAME)
     VALUES (:emp_number, :emp_name);

Notice that the input host variables in the `VALUES` clause of the `INSERT` statement are prefixed with colons.

### 4.2 About Using Indicator Variables

You can associate any host variable with an optional indicator variable. Each time the host variable is used in a SQL statement, a result code is stored in its associated indicator variable. Thus, indicator variables let you monitor host variables.

You use indicator variables in the `VALUES` or `SET` clause to assign nulls to input host variables and in the `INTO` clause to detect nulls or truncated values in output host variables.

#### 4.2.1 Input Variables

For input host variables, the values your program can assign to an indicator variable have the following meanings:

- -1: Oracle will assign a null to the column, ignoring the value of the host variable.

- \>= 0: Oracle will assigns the value of the host variable to the column.

#### 4.2.2 Output Variables

For output host variables, the values Oracle can assign to an indicator variable have the following meanings:

- -2: Oracle assigned a truncated column value to the host variable, but could not assign the original length of the column value to the indicator variable because the number was too large.

- -1: The column value is null, so the value of the host variable is indeterminate.

- 0: Oracle assigned an intact column value to the host variable.

- \> 0: Oracle assigned a truncated column value to the host variable, assigned the original column length (expressed in characters, instead of bytes, for multibyte Globalization Support host variables) to the indicator variable, and set SQLCODE in the SQLCA to zero.

Remember, an indicator variable must be defined in the Declare Section as a 2-byte integer and, in SQL statements, must be prefixed with a colon and appended to its host variable (unless you use the keyword INDICATOR).

#### 4.2.3 Inserting Nulls

You can use indicator variables to insert nulls. Before the insert, for each column you want to be null, set the appropriate indicator variable to -1, as shown in the following example:

    set ind_comm = -1;
    EXEC SQL INSERT INTO EMP (EMPNO, COMM)
     VALUES (:emp_number, :commission:ind_comm);

The indicator variable ind_comm specifies that a null is to be stored in the `COMM` column.

You can hardcode the null instead, as follows:

    EXEC SQL INSERT INTO EMP (EMPNO, COMM)
     VALUES (:emp_number, NULL);

While this is less flexible, it might be more readable.

Typically, you insert nulls conditionally, as the next example shows:

    display 'Enter employee number or 0 if not available: ';
    read emp_number;
    IF emp_number = 0 THEN
     set ind_empnum = -1; ELSE
     set ind_empnum = 0;
    ENDIF;
    EXEC SQL INSERT INTO EMP (EMPNO, SAL)
     VALUES (:emp_number:ind_empnum, :salary);

#### 4.2.4 Handling Returned Nulls

You can also use indicator variables to manipulate returned nulls, as the following example shows:

    EXEC SQL SELECT ENAME, SAL, COMM
     INTO :emp_name, :salary, :commission:ind_comm
     FROM EMP
     WHERE EMPNO = :emp_number;
    IF ind_comm = -1 THEN
     set pay = salary; -- commission is null; ignore it
    ELSE
     set pay = salary + commission;
    ENDIF;

#### 4.2.5 Fetching Nulls

When DBMS=NATIVE, V7, or V8, if you select or fetch nulls into a host variable that lacks an indicator variable, Oracle issues the following error message:

    ORA-01405: fetched column value is NULL

#### 4.2.6 Testing for Nulls

You can use indicator variables in the `WHERE` clause to test for nulls, as the following example shows:

    EXEC SQL SELECT ENAME, SAL
     INTO :emp_name, :salary
     FROM EMP
     WHERE :commission:ind_comm IS NULL ...

However, you cannot use a relational operator to compare nulls with each other or with other values. For example, the following `SELECT` statement fails if the `COMM` column contains one or more nulls:

    EXEC SQL SELECT ENAME, SAL
     INTO :emp_name, :salary
     FROM EMP
     WHERE COMM = :commission:ind_comm;

The next example shows how to compare values for equality when some of them might be nulls:

    EXEC SQL SELECT ENAME, SAL
     INTO :emp_name, :salary
     FROM EMP
     WHERE (COMM = :commission) OR ((COMM IS NULL) AND
     (:commission:ind_comm IS NULL));

#### 4.2.7 Fetching Truncated Values

If you select or fetch a truncated column value into a host variable that lacks an indicator variable, no error is generated.

### 4.3 The Basic SQL Statements

Executable SQL statements let you query, manipulate, and control Oracle data and create, define, and maintain Oracle objects such as tables, views, and indexes. This chapter focuses on data manipulation statements (sometimes called DML) and cursor control statements. The following SQL statements let you query and manipulate Oracle data:

- `SELECT`: Returns rows from one or more tables.

- `INSERT`: Adds new rows to a table.

- `UPDATE`: Modifies rows in a table.

- `DELETE`: Removes rows from a table.

When executing a data manipulation statement such as `INSERT`, `UPDATE`, or `DELETE`, your only concern, besides setting the values of any input host variables, is whether the statement succeeds or fails. To find out, you simply check the SQLCA. (Executing any SQL statement sets the SQLCA variables.) You can check in the following two ways:

- Implicit checking with the `WHENEVER` statement

- Explicit checking of SQLCA variables

Alternatively, when `MODE={ANSI|ANSI14}`, you can check the status variable `SQLSTATE` or `SQLCODE`. For more information, see "[About Using Status Variables when MODE={ANSI\|ANSI14}](error-handling-diagnostics.md)".

When executing a `SELECT` statement (query), however, you must also deal with the rows of data it returns. Queries can be classified as follows:

- queries that return no rows (that is, merely check for existence)

- queries that return only one row

- queries that return more than one row

Queries that return more than one row require an explicitly declared cursor or cursor variable (or the use of host arrays, which are discussed in [Using Host Arrays](using-host-arrays.md)). The following embedded SQL statements let you define and control an explicit cursor:

- `DECLARE`: Names the cursor and associates it with a query.

- `OPEN`: Executes the query and identifies the active set.

- `FETCH`: Advances the cursor and retrieves each row in the active set, one by one.

- `CLOSE`: Disables the cursor (the active set becomes undefined).

In the following sections, first you learn how to code `INSERT`, `UPDATE`, `DELETE`, and single-row `SELECT` statements. Then, you progress to multi-row `SELECT` statements.

#### 4.3.1 Selecting Rows

Querying the database is a common SQL operation. To issue a query you use the `SELECT` statement. In the following example, you query the `EMP` table:

    EXEC SQL SELECT ENAME, JOB, SAL + 2000
     INTO :emp_name, :job_title, :salary
     FROM EMP
     WHERE EMPNO = :emp_number;

The column names and expressions following the keyword `SELECT` make up the select list. The select list in our example contains three items. Under the conditions specified in the `WHERE` clause (and following clauses, if present), Oracle returns column values to the host variables in the `INTO` clause. The number of items in the select list should equal the number of host variables in the `INTO` clause, so there is a place to store every returned value.

In the simplest case, when a query returns one row, its form is that shown in the last example (in which `EMPNO` is a unique key). However, if a query can return more than one row, you must fetch the rows using a cursor or select them into a host array.

If you write a query to return only one row but it might actually return several rows, the result depends on how you specify the option `SELECT_ERROR`. When `SELECT_ERROR``=``YES` (the default), Oracle issues the following error message if more than one row is returned:

    ORA-01422: exact fetch returns more than requested number of rows

When `SELECT_ERROR=NO`, a row is returned and Oracle generates no error.

#### 4.3.2 Available Clauses

You can use all of the following standard SQL clauses in your `SELECT` statements: `INTO`, `FROM`, `WHERE`, `CONNECT` `BY`, `START` `WITH`, `GROUP` `BY`, `HAVING`, `ORDER` `BY`, and `FOR` `UPDATE` `OF`.

#### 4.3.3 Inserting Rows

You use the `INSERT` statement to add rows to a table or view. In the following example, you add a row to the `EMP` table:

    EXEC SQL INSERT INTO EMP (EMPNO, ENAME, SAL, DEPTNO)
     VALUES (:emp_number, :emp_name, :salary, :dept_number);

Each column you specify in the column list must belong to the table named in the `INTO` clause. The `VALUES` clause specifies the row of values to be inserted. The values can be those of constants, host variables, SQL expressions, or pseudocolumns, such as `USER` and `SYSDATE`.

The number of values in the `VALUES` clause must equal the number of names in the column list. However, you can omit the column list if the `VALUES` clause contains a value for each column in the table in the same order they were defined by `CREATE` `TABLE`.

#### 4.3.4 Using Subqueries

A subquery is a nested `SELECT` statement. Subqueries let you conduct multipart searches. They can be used to

- supply values for comparison in the `WHERE`, `HAVING`, and `START` `WITH` clauses of `SELECT`, `UPDATE`, and `DELETE` statements

- define the set of rows to be inserted by a `CREATE` `TABLE` or `INSERT` statement

- define values for the `SET` clause of an `UPDATE` statement

For example, to copy rows from one table to another, replace the `VALUES` clause in an `INSERT` statement with a subquery, as follows:

    EXEC SQL INSERT INTO EMP2 (EMPNO, ENAME, SAL, DEPTNO)
     SELECT EMPNO, ENAME, SAL, DEPTNO FROM EMP
     WHERE JOB = :job_title;

Notice how the `INSERT` statement uses the subquery to obtain intermediate results.

#### 4.3.5 Updating Rows

You use the `UPDATE` statement to change the values of specified columns in a table or view. In the following example, you update the `SAL` and `COMM` columns in the `EMP` table:

    EXEC SQL UPDATE EMP
     SET SAL = :salary, COMM = :commission
     WHERE EMPNO = :emp_number;

You can use the optional `WHERE` clause to specify the conditions under which rows are updated. See "Using the WHERE Clause".

The `SET` clause lists the names of one or more columns for which you must provide values. You can use a subquery to provide the values, as the following example shows:

    EXEC SQL UPDATE EMP
     SET SAL = (SELECT AVG(SAL)*1.1 FROM EMP WHERE DEPTNO = 20)
     WHERE EMPNO = :emp_number;

#### 4.3.6 Deleting Rows

You use the `DELETE` statement to remove rows from a table or view. In the following example, you delete all employees in a given department from the `EMP` table:

    EXEC SQL DELETE FROM EMP
     WHERE DEPTNO = :dept_number;

You can use the optional `WHERE` clause to specify the condition under which rows are deleted.

#### 4.3.7 Using the WHERE Clause

You use the `WHERE` clause to select, update, or delete only those rows in a table or view that meet your search condition. The `WHERE`-clause search condition is a Boolean expression, which can include scalar host variables, host arrays (not in `SELECT` statements), and subqueries.

If you omit the `WHERE` clause, all rows in the table or view are processed. If you omit the `WHERE` clause in an `UPDATE` or `DELETE` statement, Oracle sets SQLWARN(5) in the SQLCA to 'W' to warn that all rows were processed.

### 4.4 Cursors

When a query returns multiple rows, you can explicitly define a cursor to:

- Process beyond the first row returned by the query

- Keep track of which row is currently being processed

A cursor identifies the current row in the set of rows returned by the query. This allows your program to process the rows one at a time. The following statements let you define and manipulate a cursor:

- `DECLARE`

- `OPEN`

- `FETCH`

- `CLOSE`

First you use the `DECLARE` statement to name the cursor and associate it with a query.

The `OPEN` statement executes the query and identifies all the rows that meet the query search condition. These rows form a set called the active set of the cursor. After opening the cursor, you can use it to retrieve the rows returned by its associated query.

Rows of the active set are retrieved one by one (unless you use host arrays). You use a `FETCH` statement to retrieve the current row in the active set. You can execute `FETCH` repeatedly until all rows have been retrieved.

When you complete fetching rows from the active set, you disable the cursor with a `CLOSE` statement, and the active set becomes undefined.

#### 4.4.1 Declaring a Cursor

You use the `DECLARE` statement to define a cursor by giving it a name and associating it with a query, as the following example shows:

    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME, EMPNO, SAL
     FROM EMP
     WHERE DEPTNO = :dept_number;

The cursor name is an identifier used by the precompiler, not a host or program variable, and should not be defined in the Declare Section. Therefore, cursor names cannot be passed from one precompilation unit to another. Also, cursor names cannot be hyphenated. They can be any length, but only the first 31 characters are significant. For ANSI compatibility, use cursor names no longer than 18 characters.

The `SELECT` statement associated with the cursor cannot include an `INTO` clause. Rather, the `INTO` clause and list of output host variables are part of the `FETCH` statement.

Because it is declarative, the `DECLARE` statement must physically (not just logically) precede all other SQL statements referencing the cursor. That is, forward references to the cursor are not allowed. In the following example, the `OPEN` statement is misplaced:

    EXEC SQL OPEN emp_cursor; -- misplaced OPEN statement
    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME, EMPNO, SAL
     FROM EMP
     WHERE ENAME = :emp_name;

The cursor control statements must all occur within the same precompiled unit. For example, you cannot declare a cursor in file A, then open it in file B.

Your host program can declare as many cursors as it needs. However, in a given file, every `DECLARE` statement must be unique. That is, you cannot declare two cursors with the same name in one precompilation unit, even across blocks or procedures, because the scope of a cursor is global within a file. If you will be using many cursors, you might want to specify the `MAXOPENCURSORS` option. For more information, see "[MAXOPENCURSORS](running-Oracle-precompilers.md)".

#### 4.4.2 Opening a Cursor

Use the `OPEN` statement to execute the query and identify the active set. In the following example, a cursor named emp_cursor is opened.

    EXEC SQL OPEN emp_cursor;

`OPEN` positions the cursor just before the first row of the active set. It also zeroes the rows-processed count kept by SQLERRD(3) in the SQLCA. However, none of the rows is actually retrieved at this point. That will be done by the `FETCH` statement.

After you open a cursor, the query's input host variables are not reexamined until you reopen the cursor. Thus, the active set does not change. To change the active set, you must reopen the cursor.

Generally, you should close a cursor before reopening it. However, if you specify `MODE=ORACLE` (the default), you need not close a cursor before reopening it. This can boost performance; for details, see [Performance Tuning](performance-tuning.md)

The amount of work done by OPEN depends on the values of three precompiler options: `HOLD_CURSOR, RELEASE_CURSOR`, and `MAXOPENCURSORS`. For more information, see "[About Using the Precompiler Options](running-Oracle-precompilers.md)".

#### 4.4.3 Fetching from a Cursor

You use the `FETCH` statement to retrieve rows from the active set and specify the output host variables that will contain the results. Recall that the `SELECT` statement associated with the cursor cannot include an `INTO` clause. Rather, the `INTO` clause and list of output host variables are part of the `FETCH` statement. In the following example, you fetch into three host variables:

    EXEC SQL FETCH emp_cursor
     INTO :emp_name, :emp_number, :salary;

The cursor must have been previously declared and opened. The first time you execute `FETCH`, the cursor moves from before the first row in the active set to the first row. This row becomes the current row. Each subsequent execution of `FETCH` advances the cursor to the next row in the active set, changing the current row. The cursor can only move forward in the active set. To return to a row that has already been fetched, you must reopen the cursor, then begin again at the first row of the active set.

If you want to change the active set, you must assign new values to the input host variables in the query associated with the cursor, then reopen the cursor. When `MODE={ANSI | ANSI14 | ANSI13}`, you must close the cursor before reopening it.

As the next example shows, you can fetch from the same cursor using different sets of output host variables. However, corresponding host variables in the `INTO` clause of each `FETCH` statement must have the same datatype.

    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME, SAL FROM EMP WHERE DEPTNO = 20;
    ...
    EXEC SQL OPEN emp_cursor;
    EXEC SQL WHENEVER NOT FOUND DO ...
    LOOP
     EXEC SQL FETCH emp_cursor INTO :emp_name1, :salary1;
     EXEC SQL FETCH emp_cursor INTO :emp_name2, :salary2;
     EXEC SQL FETCH emp_cursor INTO :emp_name3, :salary3;
     ...
    ENDLOOP;

If the active set is empty or contains no more rows, `FETCH` returns the "no data found" Oracle warning code to `SQLCODE` in the SQLCA (or when MODE=ANSI, to the status variable `SQLSTATE`). The status of the output host variables is indeterminate. (In a typical program, the `WHENEVER NOT FOUND` statement detects this error.) To reuse the cursor, you must reopen it.

#### 4.4.4 Closing a Cursor

When finished fetching rows from the active set, you close the cursor to free the resources, such as storage, acquired by opening the cursor. When a cursor is closed, parse locks are released. What resources are freed depends on how you specify the options `HOLD_CURSOR` and `RELEASE_CURSOR`. In the following example, you close the cursor named` emp_cursor`:

    EXEC SQL CLOSE emp_cursor;

You cannot fetch from a closed cursor because its active set becomes undefined. If necessary, you can reopen a cursor (with new values for the input host variables, for example).

When `MODE={ANSI13|ORACLE}`, issuing a commit or rollback closes cursors referenced in a `CURRENT OF` clause. Other cursors are unaffected by a commit or rollback and if open, remain open. However, when `MODE={ANSI|ANSI14}`, issuing a commit or rollback closes all explicit cursors.

#### 4.4.5 Using the CURRENT OF Clause

You use the `CURRENT OF` cursor_name clause in a `DELETE` or `UPDATE` statement to refer to the latest row fetched from the named cursor. The cursor must be open and positioned on a row. If no fetch has been done or if the cursor is not open, the `CURRENT OF` clause results in an error and processes no rows.

The `FOR UPDATE OF` clause is optional when you declare a cursor that is referenced in the `CURRENT OF` clause of an `UPDATE` or `DELETE` statement. The `CURRENT OF` clause signals the precompiler to add a `FOR UPDATE` clause if necessary. For more information, see "[About Using the FOR UPDATE OF Clause](defining-controlling-transactions.md)".

In the following example, you use the `CURRENT OF` clause to refer to the latest row fetched from a cursor named emp_cursor:

    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME, SAL FROM EMP WHERE JOB = 'CLERK'
     FOR UPDATE OF SAL;
    ...
    EXEC SQL OPEN emp_cursor;
    EXEC SQL WHENEVER NOT FOUND DO ...
    LOOP
     EXEC SQL FETCH emp_cursor INTO :emp_name, :salary;
     ...
     EXEC SQL UPDATE EMP SET SAL = :new_salary
     WHERE CURRENT OF emp_cursor;
    ENDLOOP;

#### 4.4.6 Restrictions

An explicit `FOR UPDATE OF` or an implicit `FOR UPDATE` acquires exclusive row locks. All rows are locked at the open, not as they are fetched, and are released when you commit or rollback. If you try to fetch from a `FOR UPDATE` cursor after a commit, Oracle generates the following error:

    ORA-01002: fetch out of sequence

You cannot use host arrays with the `CURRENT OF` clause. For an alternative, see "[About Mimicking the CURRENT OF Clause](using-host-arrays.md)". Also, you cannot reference multiple tables in an associated `FOR UPDATE OF` clause, which means that you cannot do joins with the `CURRENT OF` clause. Finally, you cannot use the `CURRENT OF` clause in dynamic SQL.

#### 4.4.7 A Typical Sequence of Statements

The following example shows the typical sequence of cursor control statements in an application program:

    -- Define a cursor.
    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME, JOB FROM EMP
     WHERE EMPNO = :emp_number
     FOR UPDATE OF JOB;

    -- Open the cursor and identify the active set.
    EXEC SQL OPEN emp_cursor;
    -- Exit if the last row was already fetched.
    EXEC SQL WHENEVER NOT FOUND DO no_more;

    -- Fetch and process data in a loop.
    LOOP
     EXEC SQL FETCH emp_cursor INTO :emp_name, :job_title;
     -- host-language statements that operate on the fetched data
     EXEC SQL UPDATE EMP
     SET JOB = :new_job_title
     WHERE CURRENT OF emp_cursor;
    ENDLOOP;
    ...
    ROUTINE no_more
    BEGIN
    -- Disable the cursor.
     EXEC SQL CLOSE emp_cursor;
     EXEC SQL COMMIT WORK RELEASE;
     exit program;
    END no_more;

#### 4.4.8 A Complete Example

The following program illustrates the use of a cursor and the `FETCH` statement. The program prompts for a department number, then displays the names of all employees in that department.

All fetches except the final one return a row and, if no errors were detected during the fetch, a success status code. The final fetch fails and returns the "no data found" Oracle warning code to `SQLCODE` in the SQLCA. The cumulative number of rows actually fetched is found in `SQLERRD(3)` in the SQLCA.

    -- declare host variables
    EXEC SQL BEGIN DECLARE SECTION;
     username CHARACTER(20);
     password CHARACTER(20);
     emp_name CHARACTER(10);
     dept_number INTEGER;
    EXEC SQL END DECLARE SECTION;
    -- copy in the SQL Communications Area
    EXEC SQL INCLUDE SQLCA;

    display 'Username? ';
    read username;
    display 'Password? ';
    read password;

    -- handle processing errors
    EXEC SQL WHENEVER SQLERROR DO sql_error;

    -- log on to Oracle
    EXEC SQL CONNECT :username IDENTIFIED BY :password;
    display 'Connected to Oracle';

    -- declare a cursor
    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME FROM EMP WHERE DEPTNO = :dept_number;

    display 'Department number? ';
    read dept_number;

    -- open the cursor and identify the active set
    EXEC SQL OPEN emp_cursor;

    -- exit if the last row was already fetched
    EXEC SQL WHENEVER NOT FOUND DO no_more;

    display 'Employee Name';
    display '-------------';

    -- fetch and process data in a loop
    LOOP
     EXEC SQL FETCH emp_cursor INTO :emp_name; display emp_name;
    ENDLOOP;
    ROUTINE no_more
    BEGIN
     EXEC SQL CLOSE emp_cursor;
     EXEC SQL COMMIT WORK RELEASE;
     display 'End of program';
     exit program;
    END no_more;

    ROUTINE sql_error
    BEGIN
     EXEC SQL WHENEVER SQLERROR CONTINUE;
     EXEC SQL ROLLBACK WORK RELEASE;
     display 'Processing error';
     exit program with an error;
    END sql_error;

### 4.5 Cursor Variables

This section gives a brief overview of cursor variables. For more information, see your host language supplement and [Cursor Variables](../lnpls/cursor-variables.md).

When using static embedded SQL with the Pro\*COBOL and Pro\*FORTRAN Precompilers, you can declare cursor variables. Like a cursor, a cursor variable points to the current row in the active set of a multi-row query. Cursors differ from cursor variables the way constants differ from variables. While a cursor is static, a cursor variable is dynamic, because it is not tied to a specific query. You can open a cursor variable for any type-compatible query.

Also, you can assign new values to a cursor variable and pass it as a parameter to subprograms, including subprograms stored in an Oracle database. This gives you a convenient way to centralize data retrieval.

First, you declare the cursor variable. After declaring the variable, you use four statements to control a cursor variable:

- `ALLOCATE`

- `OPEN ... FOR`

- `FETCH`

- `CLOSE`

After you declare the cursor variable and allocate memory for it, you must pass it as an input host variable (bind variable) to PL/SQL, OPEN it FOR a multi-row query on the server side, `FETCH` from it on the client side, then `CLOSE` it on either side.

#### 4.5.1 About Declaring a Cursor Variable

How you declare a cursor variable is dependent on your host language. For instructions about declaring a cursor variable, see your host-language supplement.

#### 4.5.2 Allocating a Cursor Variable

You use the `ALLOCATE` statement to allocate memory for the cursor variable. The syntax follows:

    EXEC SQL ALLOCATE <cursor_variable>;

#### 4.5.3 Opening a Cursor Variable

You use the `OPEN ... FOR` statement to associate a cursor variable with a multi-row query, execute the query, and identify the active set. The syntax follows:

    EXEC SQL OPEN <cursor_variable> FOR <select_statement>;

The `SELECT` statement can reference input host variables and PL/SQL variables, parameters, and functions but cannot be `FOR UPDATE`. In the following example, you open a cursor variable named emp_cv:

    EXEC SQL OPEN emp_cv FOR SELECT * FROM EMP;

You must open a cursor variable on the server side. You do that by passing it as an input host variable to an anonymous PL/SQL block. At run time, the block is sent to the Oracle Server for execution. In the following example, you declare and initialize a cursor variable, then pass it to a PL/SQL block, which opens the cursor variable:

    EXEC SQL BEGIN DECLARE SECTION;
     ...
    -- declare cursor variable
     emp_cur SQL_CURSOR;
    EXEC SQL END DECLARE SECTION;

    -- initialize cursor variable
    EXEC SQL ALLOCATE :emp_cur;

    EXEC SQL EXECUTE
     -- pass cursor variable to PL/SQL block
     BEGIN
     -- open cursor variable
     OPEN :emp_cur FOR SELECT * FROM EMP;
     END;
    END-EXEC;

Generally, you pass a cursor variable to PL/SQL by calling a stored procedure that declares a cursor variable as one of its formal parameters. For example, the following packaged procedure opens a cursor variable named emp_cv:

    CREATE PACKAGE emp_data AS
     -- define REF CURSOR type
     TYPE EmpCurTyp IS REF CURSOR RETURN emp%ROWTYPE;
     -- declare formal paramter of that type
     PROCEDURE open_emp_cv (emp_cv IN OUT EmpCurTyp);
    END emp_data;

    CREATE PACKAGE BODY emp_data AS
     PROCEDURE open_emp_cv (emp_cv IN OUT EmpCurTyp) IS
     BEGIN
     -- open cursor variable
     OPEN emp_cv FOR SELECT * FROM emp;
     END open_emp_cv;
    END emp_data;

You can call the procedure from any application, as follows:

    EXEC SQL EXECUTE
     BEGIN
     emp_data.open_emp_cv(:emp_cur);
     END;
    END-EXEC;

#### 4.5.4 Fetching from a Cursor Variable

After opening a cursor variable for a multi-row query, you use the `FETCH` statement to retrieve rows from the active set one at a time. The syntax follows:

    EXEC SQL FETCH cursor_variable_name
     INTO {record_name | variable_name[, variable_name, ...]};

Each column value returned by the cursor variable is assigned to a corresponding field or variable in the `INTO` clause, providing their datatypes are compatible.

The `FETCH` statement must be executed on the client side. In the following example, you fetch rows into a host record named emp_rec:

    -- exit loop when done fetching
    EXEC SQL WHENEVER NOT FOUND DO no_more;
    LOOP
     -- fetch row into record
     EXEC SQL FETCH :emp_cur INTO :emp_rec;
     -- process the data
    ENDLOOP;

#### 4.5.5 Closing a Cursor Variable

You use the `CLOSE` statement to close a cursor variable, at which point its active set becomes undefined. The syntax follows:

    EXEC SQL CLOSE cursor_variable_name;

The `CLOSE` statement can be executed on the client side or the server side. In the following example, when the last row is processed, you close the cursor variable emp_cur:

    -- close cursor variable
    EXEC SQL CLOSE :emp_cur;
