This chapter describes the following:

- What Is a Host Array?

- Why Use Arrays?

- Declaring Host Arrays

- About Using Arrays in SQL Statements

- About Selecting into Arrays

- About Using Indicator Arrays

- About Using the FOR Clause

- About Using the WHERE Clause

- About Mimicking the CURRENT OF Clause

- About Using SQLERRD(3)

This chapter looks at using arrays to simplify coding and improve program performance. You learn how to manipulate Oracle data using arrays, how to operate on all the elements of an array with a single SQL statement, and how to limit the number of array elements processed. The following questions are answered:

- What is a host array?

- Why use arrays?

- How are host arrays declared?

- How are arrays used in SQL statements?

### 9.1 What Is a Host Array?

An array is a collection of related data items, called elements, associated with a single variable name. When declared as a host variable, the array is called a host array. Likewise, an indicator variable declared as an array is called an indicator array. An indicator array can be associated with any host array.

### 9.2 Why Use Arrays?

Arrays can ease programming and offer improved performance. When writing an application, you are usually faced with the problem of storing and manipulating large collections of data. Arrays simplify the task of naming and referencing the individual items in each collection.

Using arrays can boost the performance of your application. Arrays let you manipulate an entire collection of data items with a single SQL statement. Thus, Oracle communication overhead is reduced markedly, especially in a networked environment. For example, suppose you want to insert information about 300 employees into the EMP table. Without arrays, your program must do 300 individual `INSERTs`--one for each employee. With arrays, only one `INSERT` need be done.

### 9.3 Declaring Host Arrays

You declare host arrays in the Declare Section like simple host variables. You also dimension (set the size of) host arrays in the Declare Section. In the following example, you declare three host arrays and dimension them with 50 elements:

    EXEC SQL BEGIN DECLARE SECTION;
     emp_name (50) CHARACTER(20);
     emp_number (50) INTEGER;
     salary (50) REAL;
    EXEC SQL END DECLARE SECTION;

#### 9.3.1 Dimensioning Arrays

The maximum dimension of a host array is 32,767 elements. If you use a host array that exceeds the maximum, you get a "parameter out of range" run-time error. If you use multiple host arrays in a single SQL statement, their dimensions should be the same. Otherwise, an "array size mismatch" warning message is issued at precompile time. If you ignore this warning, the precompiler uses the smallest dimension for the SQL operation.

#### 9.3.2 Restrictions

You cannot declare host arrays of pointers. Also, host arrays that might be referenced in a SQL statement are limited to one dimension. So, the two-dimensional array declared in the following example is invalid:

    EXEC SQL BEGIN DECLARE SECTION;
     hi_lo_scores (25, 25) INTEGER; -- not allowed
    EXEC SQL END DECLARE SECTION;

### 9.4 About Using Arrays in SQL Statements

The Oracle Precompilers allow the use of host arrays in data manipulation statements. You can use host arrays as input variables in the `INSERT`, `UPDATE`, and `DELETE` statements and as output variables in the `INTO` clause of `SELECT` and `FETCH` statements.

Note that when `MODE=ANSI14`, array operations are not allowed. In other words, you can reference host arrays in a SQL statement only when `MODE`={`ANSI|ANSI13|ORACLE}`.

The syntax used for host arrays and simple host variables is nearly the same. One difference is the optional FOR clause, which lets you control array processing. Also, there are restrictions on mixing host arrays and simple host variables in a SQL statement.

The following sections illustrate the use of host arrays in data manipulation statements.

### 9.5 About Selecting into Arrays

You can use host arrays as output variables in the `SELECT` statement. If you know the maximum number of rows the select will return, simply dimension the host arrays with that number of elements. In the following example, you select directly into three host arrays. Knowing the select will return no more than 50 rows, you dimension the arrays with 50 elements:

    EXEC SQL BEGIN DECLARE SECTION;
     emp_name (50) CHARACTER(20);
     emp_number (50) INTEGER;
     salary (50) REAL;
    EXEC SQL END DECLARE SECTION;
    EXEC SQL SELECT ENAME, EMPNO, SAL
     INTO :emp_name, :emp_number, :salary
     FROM EMP
     WHERE SAL > 1000;

In this example, the `SELECT` statement returns up to 50 rows. If there are fewer than 50 eligible rows or you want to retrieve only 50 rows, this method will suffice. However, if there are more than 50 eligible rows, you cannot retrieve all of them this way. If you reexecute the `SELECT` statement, it just returns the first 50 rows again, even if more are eligible. You must either dimension a larger array or declare a cursor for use with the `FETCH` statement.

If a `SELECT INTO` statement returns more rows than the number of elements you dimensioned, Oracle issues the error message

    SQL-02112: SELECT...INTO returns too many rows

unless you specify `SELECT_ERROR`=`NO`. For more information about the option `SELECT_ERROR`, refer to "[SELECT_ERROR](running-Oracle-precompilers.md)"

#### 9.5.1 Batch Fetches

If you do not know the maximum number of rows a select will return, you can declare and open a cursor_name fetch from it in "batches." Batch fetches within a loop let you retrieve a large number of rows with ease. Each fetch returns the next batch of rows from the current active set. In the following example, you fetch in 20-row batches:

    EXEC SQL BEGIN DECLARE SECTION;
     emp_number (20) INTEGER;
     salary (20) REAL;
    EXEC SQL END DECLARE SECTION;
    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT EMPNO, SAL FROM EMP;
    EXEC SQL OPEN emp_cursor;
    EXEC SQL WHENEVER NOT FOUND DO ...
    LOOP
     EXEC SQL FETCH emp_cursor INTO :emp_number, :salary;
     -- process batch of rows
    ENDLOOP;

#### 9.5.2 Number of Rows Fetched

Each fetch returns, at most, the number of rows in the array dimension. Fewer rows are returned in the following cases:

- The end of the active set is reached. The "no data found" Oracle warning code is returned to SQLCODE in the SQLCA. For example, this happens if you fetch into an array of dimension 100 but only 20 rows are returned.

- Fewer than a full batch of rows remain to be fetched. For example, this happens if you fetch 70 rows into an array of dimension 20 because after the third fetch, only 10 rows remain to be fetched.

- An error is detected while processing a row. The fetch fails and the applicable Oracle error code is returned to SQLCODE.

The cumulative number of rows returned can be found in the third element of SQLERRD in the SQLCA, called SQLERRD(3) in this guide. This applies to each open cursor. In the following example, notice how the status of each cursor is maintained separately:

    EXEC SQL OPEN cursor1;
    EXEC SQL OPEN cursor2;
    EXEC SQL FETCH cursor1 INTO :array_of_20;
     -- now running total in SQLERRD(3) is 20
    EXEC SQL FETCH cursor2 INTO :array_of_30;
     -- now running total in SQLERRD(3) is 30, not 50
    EXEC SQL FETCH cursor1 INTO :array_of_20;
     -- now running total in SQLERRD(3) is 40 (20 + 20)
    EXEC SQL FETCH cursor2 INTO :array_of_30;
     -- now running total in SQLERRD(3) is 60 (30 + 30)

#### 9.5.3 Restrictions

Using host arrays in the `WHERE` clause of a `SELECT` statement is allowed only in a subquery. (For example, refer to "About Using the WHERE Clause".) Also, you cannot mix simple host variables with host arrays in the INTO clause of a `SELECT` or `FETCH` statement; if any of the host variables is an array, all must be arrays. Table 9-1 shows which uses of host arrays are valid in a `SELECT` `INTO` statement.

Table 9-1 Valid Host Arrays for SELECT INTO

| INTO Clause | WHERE Clause | Valid? |
|:------------|:-------------|:-------|
| array       | array        | no     |
| scalar      | scalar       | yes    |
| array       | scalar       | yes    |
| scalar      | array        | no     |

#### 9.5.4 About Fetching Nulls

If you select or fetch a null into a host array that lacks an indicator array, Oracle stops processing, sets SQLERRD(3) to the number of rows processed, and issues the following error message:

    ORA-01405: fetched column value is NULL

To learn how to find nulls and truncated values, refer to "[About Using Indicator Variables](using-embedded-SQL.md)".

#### 9.5.5 About Fetching Truncated Values

When DBMS=V7, if you select or fetch a truncated column value into a host array that lacks an indicator array, Oracle stops processing, sets SQLERRD(3) to the number of rows processed, and issues the following error message:

    ORA-01406: fetched column value was truncated

You can check SQLERRD(3) for the number of rows processed before the truncation occurred. The rows-processed count includes the row that caused the truncation error.

When MODE=ANSI, truncation is not considered an error, so Oracle continues processing.

Again, when doing array selects and fetches, always use indicator arrays. That way, if Oracle assigns one or more truncated column values to an output host array, you can find the original lengths of the column values in the associated indicator array.

#### 9.5.6 About Inserting with Arrays

You can use host arrays as input variables in an `INSERT` statement. Just make sure your program populates the arrays with data before executing the `INSERT` statement. If some elements in the arrays are irrelevant, you can use the `FOR` clause to control the number of rows inserted. Refer to About Using the FOR Clause.

An example of inserting with host arrays follows:

    EXEC SQL BEGIN DECLARE SECTION;
     emp_name (50) CHARACTER(20);
     emp_number (50) INTEGER;
     salary (50) REAL;
    EXEC SQL END DECLARE SECTION;
    -- populate the host arrays
    EXEC SQL INSERT INTO EMP (ENAME, EMPNO, SAL)
     VALUES (:emp_name, :emp_number, :salary);

The cumulative number of rows inserted can be found in SQLERRD(3).

Although functionally equivalent to the following statement, the `INSERT` statement in the last example is much more efficient because it issues only one call to Oracle:

    FOR i = 1 TO array_dimension
     EXEC SQL INSERT INTO EMP (ENAME, EMPNO, SAL)
     VALUES (:emp_name[i], :emp_number[i], :salary[i]);
    ENDFOR;

In this imaginary example (imaginary because host variables cannot be subscripted in a SQL statement), you use a FOR loop to access all array elements in sequential order.

##### Restrictions

You cannot use an array of pointers in the VALUES clause of an `INSERT` statement; all array elements must be data items. Also, mixing simple host variables with host arrays in the VALUES clause of an `INSERT` statement is not allowed; if any of the host variables is an array, all must be arrays.

#### 9.5.7 About Updating with Arrays

You can also use host arrays as input variables in an `UPDATE` statement, as the following example shows:

    EXEC SQL BEGIN DECLARE SECTION;
     emp_number (50) INTEGER;
     salary (50) REAL;
    EXEC SQL END DECLARE SECTION;
    -- populate the host arrays
    EXEC SQL UPDATE EMP SET SAL = :salary WHERE EMPNO = :emp_number;

The cumulative number of rows updated can be found in SQLERRD(3). The number does not include rows processed by an update cascade.

If some elements in the arrays are irrelevant, you can use the FOR clause to limit the number of rows updated.

The last example showed a typical update using a unique key (emp_number). Each array element qualified just one row for updating. In the following example, each array element qualifies multiple rows:

    EXEC SQL BEGIN DECLARE SECTION;
     job_title (10) CHARACTER(10);
     commission (50) REAL;
    EXEC SQL END DECLARE SECTION;
    -- populate the host arrays
    EXEC SQL UPDATE EMP SET COMM = :commission WHERE JOB = :job_title;

Restrictions: Mixing simple host variables with host arrays in the `SET` or `WHERE` clause of an `UPDATE` statement is not allowed. If any of the host variables is an array, all must be arrays. Furthermore, if you use a host array in the SET clause, you must use one in the `WHERE` clause. However, their dimensions and datatypes need not match.

You cannot use host arrays with the `CURRENT` OF clause in an UPDATE statement. For an alternative, refer to About Mimicking the CURRENT OF Clause.

Table 9-2 shows which uses of host arrays are valid in an `UPDATE` statement:

Table 9-2 Valid Host Arrays for UPDATE

| SET Clause | WHERE Clause | Valid? |
|:-----------|:-------------|:-------|
| array      | array        | yes    |
| scalar     | scalar       | yes    |
| array      | scalar       | no     |
| scalar     | array        | no     |

#### 9.5.8 About Deleting with Arrays

You can also use host arrays as input variables in a `DELETE` statement. It is like executing the `DELETE` statement repeatedly using successive elements of the host array in the `WHERE` clause. Thus, each execution might delete zero, one, or more rows from the table. An example of deleting with host arrays follows:

    EXEC SQL BEGIN DECLARE SECTION;
     ...
     emp_number (50) INTEGER;
     EXEC SQL END DECLARE SECTION;
    -- populate the host array
    EXEC SQL DELETE FROM EMP WHERE EMPNO = :emp_number;

The cumulative number of rows deleted can be found in SQLERRD(3). That number does not include rows processed by a delete cascade.

The last example showed a typical delete using a unique key (emp_number). Each array element qualified just one row for deletion. In the following example, each array element qualifies multiple rows:

    EXEC SQL BEGIN DECLARE SECTION;
     ...
     job_title (10) CHARACTER(10);
    EXEC SQL END DECLARE SECTION;
    -- populate the host array
    EXEC SQL DELETE FROM EMP WHERE JOB = :job_title;

#### 9.5.9 Restrictions

Mixing simple host variables with host arrays in the `WHERE` clause of a `DELETE` statement is not allowed; if any of the host variables is an array, all must be arrays. Also, you cannot use host arrays with the `CURRENT` `OF` clause in a `DELETE` statement. For an alternative, refer to "About Mimicking the CURRENT OF Clause".

### 9.6 About Using Indicator Arrays

You use indicator arrays to assign nulls to input host arrays and to detect null or truncated values in output host arrays. The following example shows how to insert with indicator arrays:

    EXEC SQL BEGIN DECLARE SECTION;
     emp_number (50) INTEGER;
     dept_number (50) INTEGER;
     commission (50) REAL;
     ind_comm (50) SMALLINT; -- indicator array
    EXEC SQL END DECLARE SECTION;
    -- populate the host arrays
    -- populate the indicator array; to insert a null into
    -- the COMM column, assign -1 to the appropriate element in
    -- the indicator array
    EXEC SQL INSERT INTO EMP (EMPNO, DEPTNO, COMM)
     VALUES (:emp_number, :dept_number, :commission:ind_comm);

The dimension of the indicator array cannot be smaller than the dimension of the host array.

### 9.7 About Using the FOR Clause

You can use the optional FOR clause to set the number of array elements processed by any of the following SQL statements:

- `DELETE`

- `EXECUTE`

- `FETCH`

- `INSERT`

- `OPEN`

- `UPDATE`

The `FOR` clause is especially useful in `UPDATE`, `INSERT`, and `DELETE` statements. With these statements, you might not want to use the entire array. The `FOR` clause lets you limit the elements used to just the number you need, as the following example shows:

    EXEC SQL BEGIN DECLARE SECTION;
     emp_name (100) CHARACTER(20);
     salary (100) REAL;
     rows_to_insert INTEGER;
    EXEC SQL END DECLARE SECTION;
    -- populate the host arrays
    set rows_to_insert = 25; -- set FOR-clause variable
    EXEC SQL FOR :rows_to_insert -- will process only 25 rows
     INSERT INTO EMP (ENAME, SAL)
     VALUES (:emp_name, :salary);

The `FOR` clause must use an integer host variable to count array elements. For example, the following statement is illegal:

    EXEC SQL FOR 25 -- illegal
     INSERT INTO EMP (ENAME, EMPNO, SAL)
     VALUES (:emp_name, :emp_number, :salary);

The `FOR`-clause variable specifies the number of array elements to be processed. Make sure the number does not exceed the smallest array dimension. Also, the number must be positive. If it is negative or zero, no rows are processed.

#### 9.7.1 Restrictions

Two restrictions keep `FOR` clause semantics clear.: You cannot use the FOR clause in a `SELECT` statement or with the `CURRENT` `OF` clause.

#### 9.7.2 In a SELECT Statement

If you use the `FOR` clause in a `SELECT` statement, you get the following error message:

    PCC-E-0056: FOR clause not allowed on SELECT statement at ...

The `FOR` clause is not allowed in `SELECT` statements because its meaning is unclear. Does it mean "execute this `SELECT` statement n times"? Or, does it mean "execute this `SELECT` statement once, but return n rows"? The problem in the former case is that each execution might return multiple rows. In the latter case, it is better to declare a cursor and use the `FOR` clause in a `FETCH` statement, as follows:

    EXEC SQL FOR :limit FETCH emp_cursor INTO ...

#### 9.7.3 With the CURRENT OF Clause

You can use the `CURRENT OF` clause in an `UPDATE` or `DELETE` statement to refer to the latest row returned by a `FETCH` statement, as the following example shows:

    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME, SAL FROM EMP WHERE EMPNO = :emp_number;
    ...
    EXEC SQL OPEN emp_cursor;
    ...
    EXEC SQL FETCH emp_cursor INTO :emp_name, :salary;
    ...
    EXEC SQL UPDATE EMP SET SAL = :new_salary
     WHERE CURRENT OF emp_cursor;

However, you cannot use the FOR clause with the `CURRENT` `OF` clause. The following statements are invalid because the only logical value of limit is 1 (you can only update or delete the current row once):

    EXEC SQL FOR :limit UPDATE EMP SET SAL = :new_salary
     WHERE CURRENT OF emp_cursor;
    ...
    EXEC SQL FOR :limit DELETE FROM EMP
     WHERE CURRENT OF emp_cursor;

### 9.8 About Using the WHERE Clause

Oracle treats a SQL statement containing host arrays of dimension n like the same SQL statement executed n times with n different scalar variables (the individual array elements). The precompiler issues the following error message only when such treatment is ambiguous:

    PCC-S-0055: Array <name> not allowed as bind variable at ...

For example, assuming the declarations

    EXEC SQL BEGIN DECLARE SECTION;
     mgr_number (50) INTEGER;
     job_title (50) CHARACTER(20);
    EXEC SQL END DECLARE SECTION;

it would be ambiguous if the statement

    EXEC SQL SELECT MGR INTO :mgr_number FROM EMP
     WHERE JOB = :job_title;

were treated like the imaginary statement

    FOR i = 1 TO 50
     SELECT MGR INTO :mgr_number[i] FROM EMP
     WHERE JOB = :job_title[i];
    ENDFOR;

because multiple rows might meet the `WHERE`-clause search condition, but only one output variable is available to receive data. Therefore, an error message is issued.

However, it would not be ambiguous if the statement

    EXEC SQL UPDATE EMP SET MGR = :mgr_number
     WHERE EMPNO IN (SELECT EMPNO FROM EMP WHERE JOB = :job_title);

were treated like the imaginary statement

    FOR i = 1 TO 50
     UPDATE EMP SET MGR = :mgr_number[i]
     WHERE EMPNO IN
     (SELECT EMPNO FROM EMP WHERE JOB = :job_title[i]);
    ENDFOR;

because there is a mgr_number in the `SET` clause for each row matching job_title in the `WHERE` clause, even if each job_title matches multiple rows. All rows matching each job_title can be `SET` to the same mgr_number. So, no error message is issued.

### 9.9 About Mimicking the CURRENT OF Clause

You use the `CURRENT OF` cursor clause in a `DELETE` or `UPDATE` statement to refer to the latest row fetched from the cursor. However, you cannot use `CURRENT OF` with host arrays. Instead, select the `ROWID` of each row, then use that value to identify the current row during the update or delete. An example follows:

    EXEC SQL BEGIN DECLARE SECTION;
     emp_name (25) CHARACTER(20);
     job_title (25) CHARACTER(15);
     old_title (25) CHARACTER(15);
     row_id (25) CHARACTER(18);
    EXEC SQL END DECLARE SECTION;
    ...
    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME, JOB, ROWID FROM EMP;
    ...
    EXEC SQL OPEN emp_cursor;
    EXEC SQL WHENEVER NOT FOUND GOTO ...
    ...
    LOOP
     EXEC SQL FETCH emp_cursor
     INTO :emp_name, :job_title, :row_id;
     ...
     EXEC SQL DELETE FROM EMP
     WHERE JOB = :old_title AND ROWID = :row_id;
     EXEC SQL COMMIT WORK;
    ENDLOOP;

However, the fetched rows are not locked because no `FOR UPDATE OF` clause is used. So, you might get inconsistent results if another user changes a row after you read it but before you delete it.

### 9.10 About Using SQLERRD(3)

For `INSERT`, `UPDATE`, `DELETE`, and `SELECT` `INTO` statements, SQLERRD(3) records the number of rows processed. For `FETCH` statements, it records the cumulative sum of rows processed.

When using host arrays with `FETCH`, to find the number of rows returned by the most recent iteration, subtract the current value of SQLERRD(3) from its previous value (stored in another variable). In the following example, you determine the number of rows returned by the most recent fetch:

    EXEC SQL BEGIN DECLARE SECTION;
     emp_number (100) INTEGER;
     emp_name (100) CHARACTER(20);
    EXEC SQL END DECLARE SECTION;
    ...
     rows_to fetch INTEGER;
     rows_before INTEGER;
     rows_this_time INTEGER;
    ...
    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT EMPNO, ENAME
     FROM EMP
     WHERE DEPTNO = 30;
    EXEC SQL OPEN emp_cursor;
    EXEC SQL WHENEVER NOT FOUND CONTINUE;
    ...
    -- initialize loop variables
    set rows_to_fetch = 20; -- number of rows in each "batch"
    set rows_before = 0; -- previous value of sqlerrd(3)
    set rows_this_time = 20;
    WHILE rows_this_time = rows_to_fetch
     LOOP
     EXEC SQL FOR :rows_to_fetch
     FETCH emp_cursor
     INTO :emp_number, :emp_name;
     set rows_this_time = sqlca.sqlerrd(3) - rows_before;
     set rows_before = sqlca.sqlerrd(3);
     ENDLOOP;
    ENDWHILE;

SQLERRD(3) is also useful when an error occurs during an array operation. Processing stops at the row that caused the error, so SQLERRD(3) gives the number of rows processed successfully.
