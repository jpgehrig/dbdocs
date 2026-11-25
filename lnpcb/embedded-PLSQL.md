This chapter shows you how to improve performance by embedding PL/SQL transaction processing blocks in your program. This chapter has the following sections:

- Embedding PL/SQL

- Advantages of PL/SQL

- Embedding PL/SQL Blocks

- Host Variables and PL/SQL

- Indicator Variables and PL/SQL

- Host Tables and PL/SQL

- Cursor Usage in Embedded PL/SQL

- Stored PL/SQL and Java Subprograms

- Sample Program 9: Calling a Stored Procedure

- Cursor Variables

### 6.1 Embedding PL/SQL

Pro\*COBOL treats a PL/SQL block like a single embedded SQL statement. You can place a PL/SQL block anywhere in a host program that you can place a SQL statement.

To embed a PL/SQL block in your host program, declare the variables to be shared with PL/SQL and bracket the PL/SQL block with the EXEC SQL EXECUTE and END-EXEC keywords.

#### 6.1.1 Host Variables

Inside a PL/SQL block, host variables are global to the entire block and can be used anywhere a PL/SQL variable is allowed. Like host variables in a SQL statement, host variables in a PL/SQL block must be prefixed with a colon. The colon sets host variables apart from PL/SQL variables and database objects.

#### 6.1.2 VARCHAR Variables

When entering a PL/SQL block, Oracle automatically checks the length fields of VARCHAR host variables. Therefore, you must set the length fields before the block is entered. For input variables, set the length field to the length of the value stored in the string field. For output variables, set the length field to the maximum length allowed by the string field.

#### 6.1.3 Indicator Variables

In a PL/SQL block, you cannot refer to an indicator variable by itself; it must be appended to its associated host variable. Further, if you refer to a host variable with its indicator variable, you must always refer to it that way in the same block.

##### 6.1.3.1 Handling NULLs

When entering a block, if an indicator variable has a value of -1, PL/SQL automatically assigns a NULL to the host variable. When exiting the block, if a host variable is NULL, PL/SQL automatically assigns a value of -1 to the indicator variable.

##### 6.1.3.2 Handling Truncated Values

PL/SQL does not raise an exception when a truncated string value is assigned to a host variable. However, if you use an indicator variable, PL/SQL sets it to the original length of the string.

#### 6.1.4 SQLCHECK

You must specify SQLCHECK=SEMANTICS when precompiling a program with an embedded PL/SQL block. You must also use the USERID option.

**Related Topics**

- [Precompiler Options](precompiler-options.md)

### 6.2 Advantages of PL/SQL

This section looks at some of the features and benefits offered by PL/SQL, such as:

- Better performance

- Integration with Oracle

- Cursor FOR loops

- Procedures and functions

- Packages

- PL/SQL tables

- User-defined records

**See Also:**

[Oracle Database PL/SQL Language Reference](../lnpls/index.md) for more information about PL/SQL.

#### 6.2.1 Better Performance

PL/SQL can help you reduce overhead, improve performance, and increase productivity. For example, without PL/SQL, Oracle must process SQL statements one at a time. Each SQL statement results in another call to the Server and higher overhead. However, with PL/SQL, you can send an entire block of SQL statements to the server. This minimizes communication between your application and the server.

#### 6.2.2 Integration with Oracle

PL/SQL is tightly integrated with the server. For example, most PL/SQL datatypes are native to the data dictionary. Furthermore, you can use the %TYPE attribute to base variable declarations on column definitions stored in the data dictionary, as the following example shows:

    job_title  emp.job%TYPE;

That way, you need not know the exact datatype of the column. Furthermore, if a column definition changes, the variable declaration changes accordingly and automatically. This provides data independence, reduces maintenance costs, and allows programs to adapt as the database changes.

#### 6.2.3 Cursor FOR Loops

With PL/SQL, you need not use the DECLARE, OPEN, FETCH, and CLOSE statements to define and manipulate a cursor. Instead, you can use a cursor FOR loop, which implicitly declares its loop index as a record, opens the cursor associated with a given query, repeatedly fetches data from the cursor into the record and then closes the cursor. An example follows:

    DECLARE
        ...
    BEGIN
        FOR emprec IN (SELECT empno, sal, comm FROM emp) LOOP
            IF emprec.comm / emprec.sal > 0.25 THEN ...
            ...
        END LOOP;
    END;

Notice that you use dot notation to reference fields in the record.

#### 6.2.4 Subprograms

PL/SQL has two types of subprograms called procedures and functions, which aid application development by letting you isolate operations. Generally, you use a procedure to perform an action and a function to compute a value.

Procedures and functions provide extensibility. That is, they let you tailor the PL/SQL language to suit your needs. For example, if you need a procedure that creates a new department, you can write your own, such as follows:

    PROCEDURE create_dept
        (new_dname  IN CHAR(14),
         new_loc    IN CHAR(13),
         new_deptno OUT NUMBER(2)) IS
    BEGIN
        SELECT deptno_seq.NEXTVAL INTO new_deptno FROM dual;
        INSERT INTO dept VALUES (new_deptno, new_dname, new_loc);
    END create_dept;

When called, this procedure accepts a new department name and location, selects the next value in a department-number database sequence, inserts the new number, name, and location into the dept table and then returns the new number to the caller.

You can store subprograms in the database (using CREATE FUNCTION and CREATE PROCEDURE) that can be called from multiple applications without needing to be re-compiled each time.

##### 6.2.4.1 Parameter Modes

You use parameter modes to define the behavior of formal parameters. There are three parameter modes: IN (the default), OUT, and IN OUT. An IN parameter lets you pass values to the subprogram being called. An OUT parameter lets you return values to the caller of a subprogram. An IN OUT parameter lets you pass initial values to the subprogram being called and return updated values to the caller.

The datatype of each actual parameter must be convertible to the datatype of its corresponding formal parameter. Table 6-1 shows the legal conversions between datatypes.

#### 6.2.5 Packages

PL/SQL lets you bundle logically related types, program objects, and subprograms into a package. Packages can be compiled and stored in a database, where their contents can be shared by multiple applications.

Packages usually have two parts: a specification and a body. The specification is the interface to your applications; it declares the types, constants, variables, exceptions, cursors, and subprograms available for use. The body defines cursors and subprograms and so implements the specification. The following example "packages" two employment procedures:

    PACKAGE emp_actions IS  -- package specification
        PROCEDURE hire_employee (empno NUMBER, ename CHAR, ...);
        PROCEDURE fire_employee (emp_id NUMBER);
    END emp_actions;

    PACKAGE BODY emp_actions IS  -- package body
        PROCEDURE hire_employee (empno NUMBER, ename CHAR, ...) IS
        BEGIN
            INSERT INTO emp VALUES (empno, ename, ...);
        END hire_employee;
        PROCEDURE fire_employee (emp_id NUMBER) IS
        BEGIN
            DELETE FROM emp WHERE empno = emp_id;
        END fire_employee;
    END emp_actions;

Only the declarations in the package specification are visible and accessible to applications. Implementation details in the package body are hidden and inaccessible.

#### 6.2.6 PL/SQL Tables

PL/SQL provides a composite datatype named TABLE. Objects of type TABLE are called PL/SQL tables, which are modeled as (but not the same as) database tables. PL/SQL tables have only one column and use a primary key to give you array-like access to rows. The column can belong to any scalar type (such as CHAR, DATE, or NUMBER), but the primary key must belong to type BINARY_INTEGER, PLS_INTEGER or VARCHAR2.

You can declare PL/SQL table types in the declarative part of any block, procedure, function, or package. The following example declares a TABLE type called NumTabTyp:

    DECLARE
        TYPE NumTabTyp IS TABLE OF NUMBER
            INDEX BY BINARY_INTEGER;
        ...
    BEGIN
        ...
    END;

Once you define type NumTabTyp, you can declare PL/SQL tables of that type, as the next example shows:

    num_tab  NumTabTyp;

The identifier num_tab represents an entire PL/SQL table.

You reference rows in a PL/SQL table using array-like syntax to specify the primary key value. For example, you reference the ninth row in the PL/SQL table named num_tab as follows:

    num_tab(9) ...

#### 6.2.7 User-Defined Records

You can use the %ROWTYPE attribute to declare a record that represents a row in a database table or a row fetched by a cursor. However, you cannot specify the datatypes of fields in the record or define fields of your own. The composite datatype RECORD lifts those restrictions.

Objects of type RECORD are called records. Unlike PL/SQL tables, records have uniquely named fields, which can belong to different datatypes. For example, suppose you have different kinds of data about an employee such as name, salary, hire date, and so on. This data is dissimilar in type but logically related. A record that contains such fields as the name, salary, and hire date of an employee would let you treat the data as a logical unit.

You can declare record types and objects in the declarative part of any block, procedure, function, or package. The following example declares a RECORD type called DeptRecTyp:

    DECLARE
        TYPE DeptRecTyp IS RECORD
            (deptno  NUMBER(4) NOT NULL := 10,  -- must initialize
             dname   CHAR(9),
             loc     CHAR(14));

Notice that the field declarations are like variable declarations. Each field has a unique name and specific datatype. You can add the NOT NULL option to any field declaration and so prevent the assigning of NULLs to that field. However, you must initialize NOT NULL fields.

Once you define type DeptRecTyp, you can declare records of that type, as the next example shows:

    dept_rec  DeptRecTyp;

The identifier dept_rec represents an entire record.

You use dot notation to reference individual fields in a record. For example, you reference the dname field in the dept_rec record as follows:

    dept_rec.dname ...

### 6.3 Embedding PL/SQL Blocks

Pro\*COBOL treats a PL/SQL block like a single embedded SQL statement. Thus, you can place a PL/SQL block anywhere in a host program that you can place a SQL statement.

To embed a PL/SQL block in your host program, simply bracket the PL/SQL block with the keywords EXEC SQL EXECUTE and END-EXEC as follows:

         EXEC SQL EXECUTE
             DECLARE
             ...
             BEGIN
             ...
             END;
         END-EXEC.

When your program embeds PL/SQL blocks, you must specify the precompiler option SQLCHECK=SEMANTICS because PL/SQL must be parsed by Pro\*COBOL. To connect to the server, you must also specify the option USERID.

**Related Topics**

- [Using Pro\*COBOL Precompiler Options](precompiler-options.md)

### 6.4 Host Variables and PL/SQL

Host variables are the key to communication between a host language and a PL/SQL block. Host variables can be shared with PL/SQL, meaning that PL/SQL can set and reference host variables.

For example, you can prompt a user for information and use host variables to pass that information to a PL/SQL block. Then, PL/SQL can access the database and use host variables to pass the results back to your host program.

Inside a PL/SQL block, host variables are treated as global to the entire block and can be used anywhere a PL/SQL variable is allowed. Like host variables in a SQL statement, host variables in a PL/SQL block must be prefixed with a colon. The colon sets host variables apart from PL/SQL variables and database objects.

#### 6.4.1 PL/SQL Examples

The following example illustrates the use of host variables with PL/SQL. The program prompts the user for an employee number and then displays the job title, hire date, and salary of that employee.

         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01 USERNAME   PIC X(20) VARYING.
     01 PASSWORD   PIC X(20) VARYING.
     01 EMP-NUMBER PIC S9(4) COMP.
     01 JOB-TITLE  PIC X(20) VARYING.
     01 HIRE-DATE  PIC X(9) VARYING.
     01 SALARY     PIC S9(6)V99
                              DISPLAY SIGN LEADING SEPARATE.
         EXEC SQL END DECLARE SECTION END-EXEC.
         EXEC SQL INCLUDE SQLCA END-EXEC.
         ...
         DISPLAY 'Connected to Oracle'.
     PERFORM
         DISPLAY 'Employee Number (0 to end)? 'WITH NO ADVANCING
         ACCEPT EMP-NUMBER
         IF EMP-NUMBER = 0
             EXEC SQL COMMIT WORK RELEASE END-EXEC
             DISPLAY 'Exiting program'
             STOP RUN
         END-IF.
    *   ---------------- begin PL/SQL block -----------------
         EXEC SQL EXECUTE
            BEGIN
                SELECT job, hiredate, sal
                    INTO :JOB-TITLE, :HIRE-DATE, :SALARY
                    FROM EMP
                    WHERE EMPNO = :EMP-NUMBER;
            END;
         END-EXEC.
    *    ---------------- end PL/SQL block -----------------
         DISPLAY 'Number  Job Title  Hire Date  Salary'.
         DISPLAY '------------------------------------'.
         DISPLAY EMP-NUMBER, JOB-TITLE, HIRE-DATE, SALARY.
     END-PERFORM.
         ...
     SQL-ERROR.
         EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.
         EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
         DISPLAY 'Processing error'.
         STOP RUN.

Notice that the host variable EMP-NUMBER is set before the PL/SQL block is entered, and the host variables JOB-TITLE, HIRE-DATE, and SALARY are set inside the block.

#### 6.4.2 A More Complex PL/SQL Example

In the following example the user is prompted for a bank account number, transaction type, and transaction amount. The account is then debited or credited. If the account does not exist, an exception is raised. When the transaction is complete its status is displayed.

         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01 USERNAME   PIC X(20) VARYING.
     01 ACCT-NUM   PIC S9(4) COMP.
     01 TRANS-TYPE PIC X(1).
     01 TRANS-AMT  PIC PIC S9(6)V99
                           DISPLAY SIGN LEADING SEPARATE.
     01 STATUS     PIC X(80) VARYING.
        EXEC SQL END DECLARE SECTION END-EXEC.
         EXEC SQL INCLUDE SQLCA END-EXEC.
         DISPLAY 'Username? 'WITH NO ADVANCING.
         ACCEPT USERNAME.
         DISPLAY 'Password? '.
         ACCEPT PASSWORD.
         EXEC SQL WHENEVER SQLERROR DO PERFORM SQL-ERROR.
         EXEC SQL CONNECT :USERNAME IDENTIFIED BY :PASSWORD.
         PERFORM
         DISPLAY 'Account Number (0 to end)? '
             WITH NO ADVANCING
         ACCEPT ACCT_NUM
         IF ACCT-NUM = 0
             EXEC SQL COMMIT WORK RELEASE END-EXEC
             DISPLAY 'Exiting program' WITH NO ADVANCING
             STOP RUN
         END-IF.
         DISPLAY 'Transaction Type - D)ebit or C)redit? '
             WITH NO ADVANCING
         ACCEPT TRANS-TYPE
         DISPLAY 'Transaction Amount? '
         ACCEPT trans_amt
    *   --------------------- begin PL/SQL block -------------------
         EXEC SQL EXECUTE
            DECLARE
                old_bal      NUMBER(9,2);
                err_msg      CHAR(70);
                nonexistent  EXCEPTION;
            BEGIN
               IF :TRANS-TYP-TYPE = 'C' THEN       -- credit the account
                    UPDATE accts SET bal = bal + :TRANS-AMT
                        WHERE acctid = :acct-num;
                    IF SQL%ROWCOUNT = 0 THEN    -- no rows affected
                        RAISE nonexistent;
                    ELSE
                       :STATUs := 'Credit applied';
                    END IF;
                ELSIF :TRANS-TYPe = 'D' THEN    -- debit the account
                    SELECT bal INTO old_bal FROM accts
                        WHERE acctid = :ACCT-NUM;
                    IF old_bal >= :TRANS-AMT THEN   -- enough funds
                        UPDATE accts SET bal = bal - :TRANS-AMT
                            WHERE acctid = :ACCT-NUM;
                        :STATUS := 'Debit applied';
                    ELSE
                        :STATUS := 'Insufficient funds';
                    END IF;
                ELSE
                  :STATUS := 'Invalid type: ' || :TRANS-TYPE;
                END IF;
                COMMIT;
            EXCEPTION
                WHEN NO_DATA_FOUND OR nonexistent THEN
                    :STATUS := 'Nonexistent account';
                WHEN OTHERS THEN
                    err_msg := SUBSTR(SQLERRM, 1, 70);
                   :STATUS := 'Error: ' || err_msg;
            END;
         END-EXEC.
    *     ------------------- end PL/SQL block -----------------------
         DISPLAY 'Status: ', STATUS
     END-PERFORM.
         ...
     SQL-ERROR.
         EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.
         EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
         DISPLAY 'Processing error'.
         STOP RUN.

#### 6.4.3 VARCHAR Pseudotype

Recall that you can use the VARCHAR pseudotype to declare variable-length character strings. If the VARCHAR is an input host variable, you must tell Pro\*COBOL what length to expect. Therefore, set the length field to the actual length of the value stored in the string field.

If the VARCHAR is an output host variable, Pro\*COBOL automatically sets the length field. However, to use a VARCHAR output host variable in your PL/SQL block, you must initialize the length field before entering the block. Therefore, set the length field to the declared (maximum) length of the VARCHAR, as shown in the following example:

         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
            01 EMP-NUM   PIC S9(4) COMP.
            01 EMP-NAME  PIC X(10) VARYING.
            01 SALARY    PIC S9(6)V99
                         DISPLAY SIGN LEADING SEPARATE.
         ...
         EXEC SQL END DECLARE SECTION END-EXEC.
     PROCEDURE DIVISION.
         ...
    * -- initialize length field
         MOVE 10 TO EMP-NAME-LEN.
         EXEC SQL EXECUTE
         BEGIN
            SELECT ename, sal INTO :EMP-NAME, :SALARY
                FROM emp
                WHERE empno = :EMP-NUM;
            ...
         END;
         END-EXEC.

### 6.5 Indicator Variables and PL/SQL

PL/SQL does not need indicator variables because it can manipulate NULLs. For example, within PL/SQL, you can use the IS NULL operator to test for NULLs, as follows:

    IF variable IS NULL THEN ...

You can use the assignment operator (:=) to assign NULLs, as follows:

    variable := NULL;

However, host languages need indicator variables because they cannot manipulate NULLs. Embedded PL/SQL meets this need by letting you use indicator variables to:

- Accept NULLs input from a host program

- Output NULLs or truncated values to a host program

When used in a PL/SQL block, indicator variables are subject to the following rule:

- If you refer to a host variable with an indicator variable, you must always refer to it that way in the same block.

In the following example, the indicator variable IND-COMM appears with its host variable COMMISSION in the SELECT statement, so it must appear that way in the IF statement:

         EXEC SQL EXECUTE
         BEGIN
            SELECT ename, comm
                INTO :EMP-NAME, :COMMISSION:IND-COMM FROM emp
                WHERE empno = :EMP-NUM;
            IF :COMMISSION:IND-COMM IS NULL THEN ...
            ...
         END;
         END-EXEC.

Notice that PL/SQL treats :COMMISSION:IND-COMM like any other simple variable. Though you cannot refer directly to an indicator variable inside a PL/SQL block, PL/SQL checks the value of the indicator variable when entering the block and sets the value correctly when exiting the block.

#### 6.5.1 Handling NULLs

When entering a block, if an indicator variable has a value of -1, PL/SQL automatically assigns a NULL to the host variable. When exiting the block, if a host variable is NULL, PL/SQL automatically assigns a value of -1 to the indicator variable. In the next example, if IND-SAL had a value of -1 before the PL/SQL block was entered, the salary_missing exception is raised. An exception is a named error condition.

        EXEC SQL EXECUTE
        BEGIN
            IF :SALARY:IND-SAL IS NULL THEN
                RAISE salary_missing;
            END IF;
            ...
        END;
        END-EXEC.

#### 6.5.2 Handling Truncated Values

PL/SQL does not raise an exception when a truncated string value is assigned to a host variable. However, if you use an indicator variable, PL/SQL sets it to the original length of the string. The following example the host program will be able to tell, by checking the value of IND-NAME, if a truncated value was assigned to EMP-NAME:

         EXEC SQL EXECUTE
         DECLARE
            ...
            new_name  CHAR(10);
         BEGIN
            ...
            :EMP_NAME:IND-NAME := new_name;
            ...
         END;
         END-EXEC.

### 6.6 Host Tables and PL/SQL

You can pass input host tables and indicator tables to a PL/SQL block. They can be indexed by a PL/SQL variable of type BINARY_INTEGER or PLS_INTEGER; VARCHAR2 key types are not permitted. Normally, the entire host table is passed to PL/SQL, but you can use the ARRAYLEN statement (discussed later) to specify a smaller table dimension.

Furthermore, you can use a subprogram call to assign all the values in a host table to rows in a PL/SQL table. Given that the table subscript range is m .. n, the corresponding PL/SQL table index range is always 1 .. (n - m + 1). For example, if the table subscript range is 5 .. 10, the corresponding PL/SQL table index range is 1 .. (10 - 5 + 1) or 1 .. 6.

Note: Pro\*COBOL does not check your usage of host tables. For instance, no index range checking is done.

In the following example, you pass a host table named salary to a PL/SQL block, which uses the host table in a function call. The function is named median because it finds the middle value in a series of numbers. Its formal parameters include a PL/SQL table named num_tab. The function call assigns all the values in the actual parameter salary to rows in the formal parameter num_tab.

         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
         ...
     01  SALARY OCCURS 100 TIMES PIC S9(6)V99 COMP-3.
     01  MEDIAN-SALARY  PIC S9(6)V99 COMP-3.
         EXEC SQL END DECLARE SECTION END-EXEC.
    * -- populate the host table
         EXEC SQL EXECUTE
         DECLARE
            TYPE NumTabTyp IS TABLE OF REAL
                INDEX BY BINARY_INTEGER;
            n  BINARY_INTEGER;
            ...
            FUNCTION median (num_tab NumTabTyp, n INTEGER)
                RETURN REAL IS
            BEGIN
    * -- compute median
            END;
         BEGIN
            n := 100;
            :MEDIAN-SALARY := median(:SALARY    END;
         END-EXEC.

You can also use a subprogram call to assign all row values in a PL/SQL table to corresponding elements in a host table. For an example, see "Stored PL/SQL and Java Subprograms".

The interface between Host Tables and PL/SQL strictly controls datatypes. The default external type for PIC X is CHARF (fixed length character string) and this can only be mapped to PL/SQL tables of type CHAR.

Table 6-1 shows the legal conversions between row values in a PL/SQL table and elements in a host table. The most notable fact is that you cannot pass a PIC X variable to a table of type VARCHAR2 without using datatype equivalencing to equivalence the variable to VARCHAR2, or using PICX=VARCHAR2 on the command line.

Table 6-1 Legal Datatype Conversions

| PL/SQL Table | \-   | \-   | \-   | \-       | \-     | \-  | \-    | \-       |
|:-------------|:-----|:-----|:-----|:---------|:-------|:----|:------|:---------|
| Host Table   | CHAR | DATE | LONG | LONG RAW | NUMBER | RAW | ROWID | VARCHAR2 |
| CHARF        | X    | \-   | \-   | \-       | \-     | \-  | \-    | \-       |
| CHARZ        | X    | \-   | \-   | \-       | \-     | \-  | \-    | \-       |
| DATE         | \-   | X    | \-   | \-       | \-     | \-  | \-    | \-       |
| DECIMAL      | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| DISPLAY      | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| FLOAT        | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| INTEGER      | \-   | \-   | \-   | \-       | \-     | \-  | \-    | \-       |
| LONG         | X    | \-   | X    | \-       | \-     | \-  | \-    | \-       |
| LONG VARCHAR | \-   | \-   | X    | X        | \-     | X   | \-    | X        |
| LONG VARRAW  | \-   | \-   | \-   | X        | \-     | X   | \-    | \-       |
| NUMBER       | \-   | \-   | \-   | \-       | X      |     | \-    | \-       |
| RAW          | \-   | \-   | \-   | X        | \-     | X   | \-    | \-       |
| ROWID        | \-   | \-   | \-   | \-       | \-     | \-  | X     | \-       |
| STRING       | \-   | \-   | X    | X        | \-     | X   | \-    | X        |
| UNSIGNED     | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| VARCHAR      | \-   | \-   | X    | X        | \-     | X   | \-    | X        |
| VARCHAR2     | \-   | \-   | X    | X        | \-     | X   | \-    | X        |
| VARNUM       | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| VARRAW       | \-   | \-   | \-   | X        | \-     | X   | \-    | \-       |

#### 6.6.1 ARRAYLEN Statement

Suppose you must pass an input host table to a PL/SQL block for processing. By default, when binding such a host table, Pro\*COBOL use its declared dimension. However, you might not want to process the entire table. In that case, you can use the ARRAYLEN statement to specify a smaller table dimension. ARRAYLEN associates the host table with a host variable, which stores the smaller dimension. The statement syntax is:

         EXEC SQL ARRAYLEN host_array (dimension) EXECUTE END-EXEC.

where dimension is a 4-byte, integer host variable, not a literal or an expression.

The ARRAYLEN statement must appear somewhere after the declarations of host_array and dimension. You cannot specify an offset into the host table. However, you might be able to use COBOL features for that purpose.

The following example uses ARRAYLEN to override the default dimension of a host table named BONUS:

         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01 BONUS OCCURS 100 TIMES PIC S9(6)V99
             DISPLAY SIGN LEADING SEPARATE.
     01 MY-DIM  PIC S9(9) COMP.
         ...
         EXEC SQL ARRAYLEN BONUS (MY-DIM) END-EXEC.
         EXEC SQL END DECLARE SECTION END-EXEC.
    * -- populate the host table
         ...
    * -- set smaller table dimension
         MOVE 25 TO MY-DIM.
         EXEC SQL EXECUTE
         DECLARE
            TYPE NumTabTyp IS TABLE OF REAL
                INDEX BY BINARY_INTEGER;
            median_bonus  REAL;
            FUNCTION median (num_tab NumTabTyp, n INTEGER)
                RETURN REAL IS
            BEGIN
    * -- compute median
            END;
         BEGIN
            median_bonus := median(:BONUS, :MY-DIM);
            ...
         END;
         END-EXEC.

Only 25 table elements are passed to the PL/SQL block because ARRAYLEN reduces the host table from 100 to 25 elements. As a result, when the PL/SQL block is sent to the server for execution, a much smaller host table is sent along. This saves time and, in a networked environment, reduces network traffic.

##### 6.6.1.1 Optional Keyword EXECUTE to ARRAYLEN Statement

The use of host tables used in a dynamic SQL Method 2 statement (see "[Using Method 2](Oracle-dynamic-SQL.md)") may have two different interpretations based on the presence or absence of the keyword to EXECUTE the ARRAYLEN statement. .

If the EXECUTE keyword is absent:

- The PL/SQL block will be executed multiple times, with the actual number determined by the minimum dimension of ARRAYLEN used.

- The host array cannot be bound to a PL/SQL table.

If EXECUTE is present:

- The host table must be bound to an index table.

- The PL/SQL block will be executed once.

- All host variables specified in the EXEC SQL EXECUTE statement must:

  - Be specified in an ARRAYLEN ... EXECUTE statement, or

  - Be a scalar.

The following Pro\*COBOL example demonstrates how host tables can be used to determine how many times a given PL/SQL block is executed. In this case, the PL/SQL block will be execute 3 times resulting in 3 new rows in the emp table.

           ...
     01  DYNSTMT   PIC X(80) VARYING.
     01  EMPNOTAB  PIC S9(4) COMPUTATIONAL OCCURS 5 TIMES.
     01  ENAMETAB  PIC X(10) OCCURS 3 TIMES.
           ...
               MOVE 1111 TO EMPNOTAB(1).
               MOVE 2222 TO EMPNOTAB(2).
               MOVE 3333 TO EMPNOTAB(3).
               MOVE 4444 TO EMPNOTAB(4).
               MOVE 5555 TO EMPNOTAB(5).

               MOVE "MICKEY" TO ENAMETAB(1).
               MOVE "MINNIE" TO ENAMETAB(2).
               MOVE "GOOFY" TO ENAMETAB(3).

               MOVE "BEGIN INSERT INTO emp(empno, ename) VALUES :b1, :b2; END;"
                 TO DYNSTMT-ARR.
               MOVE 57 TO DYNSTMT-LEN.

               EXEC SQL PREPARE s1 FROM :DYNSTMT END-EXEC.
               EXEC SQL EXECUTE s1 USING :EMPNOTAB, :ENAMETAB END-EXEC.
           ...


Given the following PL/SQL procedure:

      CREATE OR REPLACE PACKAGE pkg AS
         TYPE tab IS TABLE OF NUMBER(5) INDEX BY BINARY_INTEGER;
         PROCEDURE proc1 (parm1 tab, parm2 NUMBER, parm3 tab);
      END;


The following Pro\*COBOL example demonstrates how to bind a host table to a PL/SQL index table through dynamic method 2. Note the presence of the ARRAYLEN...EXECUTE statement for all host arrays specified in the EXEC SQL EXECUTE statement.

           ...
     01  DYNSTMT   PIC X(80) VARYING.
     01  II        PIC S9(4) COMP VALUE 2.
     01  INTTAB    PIC S9(9) COMP OCCURS 3 TIMES.
     01  DIM       PIC S9(9) COMP VALUE 3.

               EXEC SQL ARRAYLEN INTTAB (DIM) EXECUTE END-EXEC.
           ...
               MOVE 1 TO INTTAB(1).
               MOVE 2 TO INTTAB(2).
               MOVE 3 TO INTTAB(3).

               MOVE "BEGIN pkg.proc1 (:v1, :v2, :v3); end;";
                 TO DYNSTMT-ARR.
               MOVE 37 TO DYNSTMT-LEN.

               EXEC SQL PREPARE s1 FROM :DYNSTMT END-EXEC.
               EXEC SQL EXECUTE s1 USING :INTTAB, :II, :INTTAB END-EXEC.
           ...


However, the following Pro\*COBOL example will result in a precompile-time error because there is no ARRAYLEN...EXECUTE statement for INTTAB2.

           ...
     01  DYNSTMT   PIC X(80) VARYING.
     01  INTTAB    PIC S9(9) COMP OCCURS 3 TIMES.
     01  INTTAB2   PIC S9(9) COMP OCCURS 3 TIMES.
     01  DIM       PIC S9(9) COMP VALUE 3.

               EXEC SQL ARRAYLEN INTTAB (DIM) EXECUTE END-EXEC.
           ...
               MOVE 1 TO INTTAB(1).
               MOVE 2 TO INTTAB(2).
               MOVE 3 TO INTTAB(3).

               MOVE "BEGIN pkg.proc1 (:v1, :v2, :v3); end;";
                 TO DYNSTMT-ARR.
               MOVE 37 TO DYNSTMT-LEN.

               EXEC SQL PREPARE s1 FROM :DYNSTMT END-EXEC.
               EXEC SQL EXECUTE s1 USING :INTTAB, :INTTAB2, :INTTAB END-EXEC.
           ...

### 6.7 Cursor Usage in Embedded PL/SQL

The maximum number of cursors your program can simultaneously use is determined by the database initialization parameter OPEN_CURSORS. Normally, to prevent OPEN_CURSORS being exceeded, the precompiler allows management of statement cursors. The precompiler options HOLD_CURSOR, RELEASE_CURSOR and MAXOPENCURSORS are used. While executing an embedded PL/SQL block there will be one cursor, the parent cursor, associated with the entire PL/SQL block and a separate child cursor for each statement executed during the execution of the PL/SQL block. Because the PL/SQL block is passed to the server for execution, only the parent cursor can be tracked by the precompiler runtime library. Thus, it is possible for applications that use a lot of cursors in this way to exceed OPEN_CURSORS. Figure 6-1 shows how to calculate the maximum number of cursors used.

Figure 6-1 Maximum Cursors in Use

![Description of Figure 6-1 follows](img/pco81054.gif)
[Description of "Figure 6-1 Maximum Cursors in Use"](img_text/pco81054.md)

Developers should be aware of this situation and plan for this in the setting of OPEN_CURSORS and MAXOPENCURSORS.

If there are problems with this, you may wish to free all child cursors after a SQL statement is executed.

This can be achieved by setting RELEASE_CURSOR=YES and HOLD_CURSOR=NO. Because the use of the first setting for the entire program is likely to have an impact on performance, you can set these options in line as follows:

         EXEC ORACLE OPTION (RELEASE_CURSOR=YES) END-EXEC.
    * --  first embedded PL/SQL block
         EXEC ORACLE OPTION (RELEASE_CURSOR=NO)END-EXEC.
    * --  embedded SQL statements
         EXEC ORACLE OPTION (RELEASE_CURSOR=YES)END-EXEC.
    * --  second embedded PL/SQL block
         EXEC ORACLE OPTION (RELEASE_CURSOR=NO)END-EXEC.
    * --  embedded SQL statements

**Related Topics**

- [Embedded PL/SQL Considerations](performance-tuning.md)

### 6.8 Stored PL/SQL and Java Subprograms

Unlike anonymous blocks, PL/SQL subprograms (procedures and functions) and Java methods can be compiled separately, stored in the database, and invoked.

A subprogram explicitly created using an Oracle tool such as SQL\*Plus is called a stored subprogram. Once compiled and stored in the data dictionary, it is a database object can be re-executed without being re-compiled.

When a subprogram within a PL/SQL block or stored subprogram is sent to the database by your application, it is called an inline subprogram and is compiled by the database. Pro\*COBOL sends the statement to the server for execution.

Subprograms defined within a package are considered part of the package, and so are called packaged subprograms. Stored subprograms not defined within a package are called standalone subprograms.

#### 6.8.1 Creating Stored Subprograms

You can embed the SQL statements CREATE FUNCTION, CREATE PROCEDURE, and CREATE PACKAGE in a COBOL program, as the following example shows:

         EXEC SQL CREATE
         FUNCTION sal_ok (salary REAL, title CHAR)
          RETURN BOOLEAN AS
            min_sal  REAL;
            max_sal  REAL;
         BEGIN
            SELECT losal, hisal INTO min_sal, max_sal
                FROM sals
                WHERE job = title;
            RETURN (salary >= min_sal) AND
                   (salary <= max_sal);
         END sal_ok;
         END-EXEC.

Notice that the embedded CREATE {FUNCTION \| PROCEDURE \| PACKAGE} statement is a hybrid. Like all other embedded CREATE statements, it begins with the keywords EXEC SQL (not EXEC SQL EXECUTE).

If an embedded CREATE {FUNCTION \| PROCEDURE \| PACKAGE} statement fails, Oracle generates a warning, not an error.

**See Also:**

[ Oracle Database SQL Language Reference.](../sqlrf/index.md) for the full syntax of the CREATE statement.

#### 6.8.2 Calling a Stored PL/SQL or Java Subprogram

To call a stored subprogram from your host program, you can use either an anonymous PL/SQL block or the CALL embedded SQL statement.

##### 6.8.2.1 Anonymous PL/SQL Block

The following example calls a standalone procedure named raise_salary:

         EXEC SQL EXECUTE
         BEGIN
            raise_salary(:emp_id, :increase);
         END;
         END-EXEC.

Notice that stored subprograms can take parameters. In this example, the actual parameters emp_id and increase are host variables.

In the next example, the procedure raise_salary is stored in a package named emp_actions, so you must use dot notation to fully qualify the procedure call:

         EXEC SQL EXECUTE
         BEGIN
            emp_actions.raise_salary(:emp_id, :increase);
         END;
         END-EXEC.

An actual IN parameter can be a literal, host variable, host table, PL/SQL constant or variable, PL/SQL table, PL/SQL user-defined record, subprogram call, or expression. However, an actual OUT parameter cannot be a literal, subprogram call, or expression.

You must use precompiler option SQLCHECK=SEMANTICS with an embedded PL/SQL block.

##### 6.8.2.2 CALL Statement

The concepts presented earlier for the embedded PL/SQL block holds true for the CALL statement. The CALL embedded SQL statement has the form:

          EXEC SQL
            CALL [schema.][package.]stored_proc[@db_link](arg1, ...)
            [INTO :ret_var[[INDICATOR]:ret_ind]]
         END-EXEC.

where:

    schema

the schema containing the procedure

    package

the package containing the procedure

    stored_proc

is the Java or PL/SQL stored procedure to be called

    db_link

is the optional remote database link

    arg1...

is the list of arguments (variables, literals, or expressions) passed,

    ret_var

is the optional host variable which receives the result

    ind_var

the optional indicator variable for ret_var.

You can use either SQLCHECK=SYNTAX, or SQLCHECK=SEMANTICS with the CALL statement.

##### 6.8.2.3 CALL Example

If you have created a PL/SQL function `fact` (stored in the package `mathpkg`) that takes an integer as input and returns its factorial in an integer:

         EXEC SQL CREATE OR REPLACE PACKAGE BODY mathpkg as
           function fact(n IN INTEGER) RETURN INTEGER AS
             BEGIN
               IF (n <= 0) then return 1;
               ELSE return n * fact(n - 1);
               END IF;
             END fact;
           END mathpkge;
         END-EXEC.

then to use` fact` in a Pro\*COBOL application:

...

              01 N      PIC S9(4) COMP.
              01 FACT   PIC S9(9) COMP.
    ...
         EXEC SQL CALL mathpkge.fact(:N) INTO :FACT END-EXEC.
    ...

**See Also:**

- "[CALL (Executable Embedded SQL)](embedded-SQL-statements-and-precompiler-directives.md)" for more information about the CALL statement.

- [Developing Applications with Multiple Programming Languages](../adfns/external-procedures.md) for a complete explanation of passing arguments and other issues.

#### 6.8.3 Using Dynamic PL/SQL

Recall that Pro\*COBOL treats an entire PL/SQL block like a single SQL statement. Therefore, you can store a PL/SQL block in a string host variable. Then, if the block contains no host variables, you can use dynamic SQL Method 1 to execute the PL/SQL string. Or, if the block contains a known number of host variables, you can use dynamic SQL Method 2 to prepare and execute the PL/SQL string. If the block contains an unknown number of host variables, you must use dynamic SQL Method 4.

**Related Topics**

- [Oracle Dynamic SQL](Oracle-dynamic-SQL.md)
- [ANSI Dynamic SQL](ANSI-dynamic-SQL.md)
- [Oracle Dynamic SQL: Method 4](Oracle-dynamic-SQL-method-4.md)

#### 6.8.4 Subprograms Restriction

In dynamic SQL Method 4, a host table cannot be bound to a PL/SQL procedure with a parameter of type TABLE.

### 6.9 Sample Program 9: Calling a Stored Procedure

Before trying the sample program, you must create a PL/SQL package named calldemo, by running the following script, titled CALLDEMO.SQL, which is supplied with Pro\*COBOL. The script can be found in the Pro\*COBOL demo library. Check your system-specific Oracle documentation for exact spelling of the the name of the script.

    CREATE OR REPLACE PACKAGE calldemo AS

       TYPE name_array IS TABLE OF emp.ename%type
           INDEX BY BINARY_INTEGER;
       TYPE job_array IS TABLE OF emp.job%type
           INDEX BY BINARY_INTEGER;
       TYPE sal_array IS TABLE OF emp.sal%type
           INDEX BY BINARY_INTEGER;

       PROCEDURE get_employees(
         dept_number IN     number,    -- department to query
         batch_size  IN     INTEGER,   -- rows at a time
         found       IN OUT INTEGER,   -- rows actually returned
         done_fetch  OUT    INTEGER,   -- all done flag
         emp_name    OUT    name_array,
         job         OUT    job_array,
         sal         OUT    sal_array);

    END calldemo;
    /

    CREATE OR REPLACE PACKAGE BODY calldemo AS

       CURSOR get_emp (dept_number IN number) IS
           SELECT ename, job, sal FROM emp
               WHERE deptno = dept_number;

       -- Procedure "get_employees" fetches a batch of employee
       -- rows (batch size is determined by the client/caller
       -- of the procedure).  It can be called from other
       -- stored procedures or client application programs.
       -- The procedure opens the cursor if it is not
       -- already open, fetches a batch of rows, and
       -- returns the number of rows actually retrieved. At
       -- end of fetch, the procedure closes the cursor.

       PROCEDURE get_employees(
         dept_number IN     number,
         batch_size  IN     INTEGER,
         found       IN OUT INTEGER,
         done_fetch  OUT    INTEGER,
         emp_name    OUT    name_array,
         job         OUT    job_array,
         sal         OUT    sal_array) IS

       BEGIN
           IF NOT get_emp%ISOPEN THEN      -- open the cursor if
               OPEN get_emp(dept_number);  -- not already open
           END IF;

           -- Fetch up to "batch_size" rows into PL/SQL table,
           -- tallying rows found as they are retrieved. When all
           -- rows have been fetched, close the cursor and exit
           -- the loop, returning only the last set of rows found.

           done_fetch := 0;  -- set the done flag FALSE
           found := 0;

           FOR i IN 1..batch_size LOOP
               FETCH get_emp INTO emp_name(i), job(i), sal(i);
               IF get_emp%NOTFOUND THEN    -- if no row was found
                   CLOSE get_emp;
                   done_fetch := 1;   -- indicate all done
                   EXIT;
               ELSE
                   found := found + 1;  -- count row
               END IF;
           END LOOP;
       END;
    END;
    /

The following sample program connects to the database, prompts the user for a department number and then calls a PL/SQL procedure named get_employees, which is stored in package calldemo. The procedure declares three PL/SQL tables as OUT formal parameters and then fetches a batch of employee data into the PL/SQL tables. The matching actual parameters are host tables. When the procedure finishes, row values in the PL/SQL tables are automatically assigned to the corresponding elements in the host tables. The program calls the procedure repeatedly, displaying each batch of employee data, until no more data is found.

          *****************************************************************
          * Sample Program 9: Calling a Stored Procedure
          *
          * This program connects to ORACLE, prompts the user for a
          * department number, then calls a PL/SQL stored procedure named
          * GET_EMPLOYEES, which is stored in package CALLDEMO.  The
          * procedure declares three PL/SQL tables ast OUT formal
          * parameters, then fetches a batch of employee data into the
          * PL/SQL tables.  The matching actual parameters are host tables.
          * When the procedure finishes, it automatically assigns all row
          * values in the PL/SQL tables to corresponding elements in the
          * host tables.  The program calls the procedure repeatedly,
          * displaying each batch of employee data, until no more data
          * is found.
          * Use option picx=varchar2 when precompiling this sample program.
          *****************************************************************

           IDENTIFICATION DIVISION.
           PROGRAM-ID. CALL-STORED-PROC.
           ENVIRONMENT DIVISION.
           DATA DIVISION.
           WORKING-STORAGE SECTION.

               EXEC SQL BEGIN DECLARE SECTION END-EXEC.
           01  USERNAME         PIC X(15) VARYING.
           01  PASSWD           PIC X(15) VARYING.
           01  DEPT-NUM         PIC S9(9) COMP.
           01  EMP-TABLES.
               05  EMP-NAME     OCCURS 10 TIMES PIC X(10).
               05  JOB-TITLE    OCCURS 10 TIMES PIC X(10).

               05  SALARY       OCCURS 10 TIMES COMP-2.

           01  DONE-FLAG        PIC S9(9) COMP.
           01  TABLE-SIZE       PIC S9(9) COMP VALUE 10.
           01  NUM-RET          PIC S9(9) COMP.
           01  SQLCODE          PIC S9(9) COMP.
               EXEC SQL END DECLARE SECTION END-EXEC.

           01  COUNTER          PIC S9(9) COMP.
           01  DISPLAY-VARIABLES.
               05  D-EMP-NAME   PIC X(10).
               05  D-JOB-TITLE  PIC X(10).

               05  D-SALARY     PIC Z(5)9.

               05  D-DEPT-NUM   PIC 9(2).

               EXEC SQL INCLUDE SQLCA END-EXEC.

           PROCEDURE DIVISION.

           BEGIN-PGM.
               EXEC SQL WHENEVER SQLERROR DO
                   PERFORM SQL-ERROR END-EXEC.

               PERFORM LOGON.
               PERFORM INIT-TABLES VARYING COUNTER FROM 1 BY 1
                   UNTIL COUNTER > 10.
               PERFORM GET-DEPT-NUM.
               PERFORM DISPLAY-HEADER.
               MOVE ZERO TO DONE-FLAG.
               MOVE ZERO TO NUM-RET.
               PERFORM FETCH-BATCH UNTIL DONE-FLAG = 1.
               PERFORM LOGOFF.

           INIT-TABLES.
               MOVE SPACE TO EMP-NAME(COUNTER).
               MOVE SPACE TO JOB-TITLE(COUNTER).
               MOVE ZERO TO SALARY(COUNTER).

           GET-DEPT-NUM.
               MOVE ZERO TO DEPT-NUM.
               DISPLAY " ".
               DISPLAY "ENTER DEPARTMENT NUMBER: "
                   WITH NO ADVANCING.

               ACCEPT D-DEPT-NUM.

               MOVE D-DEPT-NUM TO DEPT-NUM.

           DISPLAY-HEADER.
               DISPLAY " ".
               DISPLAY "EMPLOYEE    JOB TITLE    SALARY".
               DISPLAY "--------    ---------    ------".

           FETCH-BATCH.
               EXEC SQL EXECUTE
                   BEGIN
                       CALLDEMO.GET_EMPLOYEES
                           (:DEPT-NUM, :TABLE-SIZE,
                            :NUM-RET,  :DONE-FLAG,
                            :EMP-NAME, :JOB-TITLE, :SALARY);
                   END;
               END-EXEC.
               PERFORM PRINT-ROWS VARYING COUNTER FROM 1 BY 1
                   UNTIL COUNTER > NUM-RET.

           PRINT-ROWS.
               MOVE EMP-NAME(COUNTER) TO D-EMP-NAME.
               MOVE JOB-TITLE(COUNTER) TO D-JOB-TITLE.
               MOVE SALARY(COUNTER) TO D-SALARY.
               DISPLAY D-EMP-NAME, "  ",
                       D-JOB-TITLE, "   ",
                       D-SALARY.

           LOGON.
               MOVE "SCOTT" TO USERNAME-ARR.
               MOVE 5 TO USERNAME-LEN.
               MOVE "TIGER" TO PASSWD-ARR.
               MOVE 5 TO PASSWD-LEN.
               EXEC SQL
                   CONNECT :USERNAME IDENTIFIED BY :PASSWD
               END-EXEC.
               DISPLAY " ".
               DISPLAY "CONNECTED TO ORACLE AS USER: ", USERNAME-ARR.

           LOGOFF.
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

Remember that the datatype of each actual parameter must be convertible to the datatype of its corresponding formal parameter. Further, before a stored subprogram exits, all OUT formal parameters must be assigned values. Otherwise, the values of corresponding actual parameters are indeterminate.

#### 6.9.1 Remote Access

PL/SQL lets you access remote databases through database links. Typically, database links are established by your DBA and stored in the data dictionary. A database link tells your program where the remote database is located, the path to it, and what username and password to use. The following example uses the database link dallas to call the raise_salary procedure:

         EXEC SQL EXECUTE
            BEGIN
            raise_salary@dallas(:emp_id, :increase);
            END;
         END-EXEC.

You can create synonyms to provide location transparency for remote subprograms, as the following example shows:

     CREATE PUBLIC SYNONYM raise_salary FOR raise_salary@dallas;

### 6.10 Cursor Variables

You can use cursor variables in your Pro\*COBOL programs to process multi-row queries using static embedded SQL. A cursor variable identifies a cursor reference that is defined and opened on the database server, using PL/SQL.

Like a cursor, a cursor variable points to the current row in the active set of a multi-row query. Cursors differ from cursor variables the way constants differ from variables. While a cursor is static, a cursor variable is dynamic, because it is not tied to a specific query. You can open a cursor variable for any type-compatible query.

You can assign new values to a cursor variable and pass it as a parameter to subprograms, including subprograms stored in a database. This gives you a convenient way to centralize data retrieval.

First, you declare the cursor variable. After declaring the variable, you use these statements to control a cursor variable:

- ALLOCATE

- OPEN ... FOR

- FETCH

- CLOSE

- FREE

After you declare the cursor variable and allocate memory for it, you must pass it as an input host variable (bind variable) to PL/SQL, OPEN it FOR a multi-row query on the server side, FETCH from it on the client side and then CLOSE it on either side.

The advantages of cursor variables are

- Ease of maintenance. Queries are centralized, in the stored procedure that opens the cursor variable. If you need to change the cursor, you only need to make the change in one place: the stored procedure. There is no need to change each application.

- Increased Security. The user of the application (the username when the Pro\*COBOL application connected to the database) must have execute permission on the stored procedure that opens the cursor. This user, however, does not need to have read permission on the tables used in the query. This capability can be used to limit access to the columns in the table.

**See Also:**

[Cursor Variables](../lnpls/cursor-variables.md) for complete information about cursor variables.

#### 6.10.1 Declaring a Cursor Variable

You declare a Pro\*COBOL cursor variable using the SQL-CURSOR pseudotype. For example:

     WORKING-STORAGE SECTION.
         ...
         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
             ...
             01  CUR-VAR  SQL-CURSOR.
             ...
         EXEC SQL END DECLARE SECTION END-EXEC.

A SQL-CURSOR variable is implemented as a COBOL group item in the code that Pro\*COBOL generates. A cursor variable is just like any other Pro\*COBOL host variable.

#### 6.10.2 Allocating a Cursor Variable

Before you can OPEN or FETCH from a cursor variable, you must initialize it using the Pro\*COBOL ALLOCATE command. For example, to initialize the cursor variable CUR-VAR that was declared in the previous section, write the following statement:

         EXEC SQL ALLOCATE :CUR-VAR END-EXEC.

Allocating a cursor variable does not require a call to the server, either at precompile time or at runtime.

The AT clause cannot be used in an ALLOCATE statement.

Caution: Allocating a cursor variable does cause heap memory to be used. For this reason, avoid allocating a cursor variable in a program loop.

#### 6.10.3 Opening a Cursor Variable

You must use an embedded anonymous PL/SQL block to open a cursor variable on the database server. The anonymous PL/SQL block may open the cursor either indirectly by calling a PL/SQL stored procedure that opens the cursor (and defines it in the same statement) or directly from the Pro\*COBOL program.

##### 6.10.3.1 Opening Indirectly through a Stored PL/SQL Procedure

Consider the following PL/SQL package stored in the database:

    CREATE PACKAGE demo_cur_pkg AS
        TYPE EmpName IS RECORD (name VARCHAR2(10));
        TYPE cur_type IS REF CURSOR RETURN EmpName;
        PROCEDURE open_emp_cur (
                   curs     IN OUT curtype,
                   dept_num IN     number);
    END;

    CREATE PACKAGE BODY demo_cur_pkg AS
        CREATE PROCEDURE open_emp_cur (
                   curs     IN OUT curtype,
                   dept_num IN     number) IS
        BEGIN
            OPEN curs FOR
                SELECT ename FROM emp
                    WHERE deptno = dept_num
                    ORDER BY ename ASC;
        END;
    END;

After this package has been stored, you can open the cursor curs by first calling the open_emp_cur stored procedure from your Pro\*COBOL program and then issuing a FETCH from the cursor variable emp_cursor in the program. For example:

     WORKING-STORAGE SECTION.
         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01  emp_cursor     sql-cursor.
     01  DEPT-NUM      PIC S9(4).
     01  EMP-NAME      PIC X(10) VARYING.
         EXEC SQL END DECLARE SECTION END-EXEC.
         ...

     PROCEDURE DIVISION.
         ...
    *    Allocate the cursor variable.
         EXEC SQL
             ALLOCATE :emp-cursor
         END-EXEC.
         ...
         MOVE 30 TO dept_num.
    *    Open the cursor on the Oracle Server.
         EXEC SQL EXECUTE
             begin
                 demo_cur_pkg.open_emp_cur(:emp-cursor, :dept-num);
             END;
         END-EXEC.
         EXEC SQL
             WHENEVER NOT FOUND DO PERFORM SIGN-OFF
         END-EXEC.
     FETCH-LOOP.
         EXEC SQL
             FETCH :emp_cursor INTO :EMP-NAME
         END-EXEC.
         DISPLAY "Employee Name: ",:EMP-NAME.
         GO TO FETCH-LOOP.
         ...
     SIGN-OFF.
         ...

##### 6.10.3.2 Opening Directly from Your Pro\*COBOL Application

To open a cursor using a PL/SQL anonymous block in a Pro\*COBOL program, define the cursor in the anonymous block. Consider the following example:

     PROCEDURE DIVISION.
         ...
         EXEC SQL EXECUTE
             begin
                 OPEN :emp_cursor FOR SELECT ename FROM emp
                     WHERE deptno = :DEPT-NUM;
             end;
         END-EXEC.
         ...

#### 6.10.4 Fetching from a Cursor Variable

After opening a cursor variable for a multi-row query, you use the FETCH statement to retrieve rows as you would from a static cursor. The syntax follows:

         EXEC SQL FETCH cursor_variable_name
             INTO {record_name | variable_name[, variable_name, ...]}
         END-EXEC.

Each column value returned by the cursor variable is assigned to a corresponding field or variable in the INTO clause, providing that their datatypes are compatible.

The FETCH statement must be executed on the client side. The following example fetches rows into a host record named EMP-REC:

    * -- exit loop when done fetching
         EXEC SQL
             WHENEVER NOT FOUND DO PERFORM NO-MORE
         END-EXEC.
         PERFORM
    * -- fetch row into record
         EXEC SQL FETCH :EMP-CUR INTO :EMP-REC END-EXEC
    * -- test for transfer out of loop
         ...
    * -- process the data
         ...
         END-PERFORM.
         ...
     NO-MORE.
         ...

Use the embedded SQL FETCH .... INTO command to retrieve the rows selected when you opened the cursor variable. For example:

     EXEC SQL
         FETCH :emp_cursor INTO :EMP-INFO:EMP-INFO-IND
     END-EXEC.

Before you can FETCH from a cursor variable, the variable must be initialized and opened. You cannot FETCH from an unopened cursor variable.

#### 6.10.5 Closing a Cursor Variable

Use the embedded SQL CLOSE statement to close a cursor variable. At this point its active set becomes undefined. The syntax follows:

         EXEC SQL CLOSE cursor_variable_name END-EXEC.

The CLOSE statement can be executed on the client side or the server side. The following example closes the cursor variable CUR-VAR when the last row is processed:

     WORKING-STORAGE SECTION.
         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
    *    Declare the cursor variable.
             01  CUR-VAR       SQL-CURSOR.
             ...
         EXEC SQL END DECLARE SECTION END-EXEC.

     PROCEDURE DIVISION.
    *    Allocate and open the cursor variable, then
    *    Fetch one or more rows.
         ...
    *    Close the cursor variable.
         EXEC SQL
             CLOSE :CUR-VAR
         END-EXEC.

#### 6.10.6 Freeing a Cursor Variable

To free memory allocated for the cursor variable, CUR-VAR, use the FREE statement after the CLOSE:

    *    Free the cursor variable memory.
         EXEC SQL
             FREE :CUR-VAR
         END-EXEC.

#### 6.10.7 Restrictions on Cursor Variables

The following restrictions apply to the use of cursor variables:

- Cursor variables are not supported in dynamic SQL.

- You can only use cursor variables with the ALLOCATE, FETCH, FREE, and CLOSE commands. The DECLARE CURSOR command does not apply to cursor variables.

- You cannot use the AT clause with the ALLOCATE command.

#### 6.10.8 Sample Program 11: Cursor Variables

The following sample programs—a SQL script (SAMPLE11.sql) and a Pro\*COBOL program (SAMPLE11.pco)—demonstrate how you can use cursor variables in Pro\*COBOL.

##### 6.10.8.1 SAMPLE11.SQL

Following is the PL/SQL source code for a creating a package that declares and opens a cursor variable:

    CONNECT SCOTT/TIGER
    CREATE OR REPLACE PACKAGE emp_demo_pkg AS
        TYPE emp_cur_type IS REF CURSOR RETURN emp%ROWTYPE;
        PROCEDURE open_cur (
            cursor   IN OUT emp_cur_type,
            dept_num IN     number);
    END emp_demo_pkg;
    /
    CREATE OR REPLACE PACKAGE BODY emp_demo_pkg AS

        PROCEDURE open_cur (
            cursor   IN OUT emp_cur_type,
            dept_num IN     number) IS
        BEGIN
            OPEN cursor FOR SELECT * FROM emp
            WHERE deptno = dept_num
            ORDER BY ename ASC;
        END;
    END emp_demo_pkg;
    /

##### 6.10.8.2 SAMPLE11.PCO

Following is a Pro\*COBOL sample program, SAMPLE11.PCO, that uses the cursor variable declared in the SAMPLE11.sql example to fetch employee names, salaries, and commissions from the EMP table:

          *****************************************************************
          * Sample Program 11:  Cursor Variable Operations                *
          *                                                               *
          * This program logs on to ORACLE, allocates and opens a cursor  *
          * variable fetches the names, salaries, and commissions of all  *
          * salespeople, displays the results, then closes the cursor.    *
          *****************************************************************

           IDENTIFICATION DIVISION.
           PROGRAM-ID. CURSOR-VARIABLES.
           ENVIRONMENT DIVISION.
           DATA DIVISION.
           WORKING-STORAGE SECTION.

               EXEC SQL BEGIN DECLARE SECTION END-EXEC.
           01  USERNAME          PIC X(15) VARYING.
           01  PASSWD            PIC X(15) VARYING.
           01  HOST              PIC X(15) VARYING.
           01  EMP-CUR           SQL-CURSOR.
           01  EMP-INFO.
               05  EMP-NUM       PIC S9(4) COMP.
               05  EMP-NAM       PIC X(10) VARYING.
               05  EMP-JOB       PIC X(10) VARYING.
               05  EMP-MGR       PIC S9(4) COMP.
               05  EMP-DAT       PIC X(10) VARYING.
               05  EMP-SAL       PIC S9(6)V99
                                   DISPLAY SIGN LEADING SEPARATE.
               05  EMP-COM       PIC S9(6)V99
                                   DISPLAY SIGN LEADING SEPARATE.
               05  EMP-DEP       PIC S9(4) COMP.
           01  EMP-INFO-IND.
               05  EMP-NUM-IND   PIC S9(4) COMP.
               05  EMP-NAM-IND   PIC S9(4) COMP.
               05  EMP-JOB-IND   PIC S9(4) COMP.
               05  EMP-MGR-IND   PIC S9(4) COMP.
               05  EMP-DAT-IND   PIC S9(4) COMP.
               05  EMP-SAL-IND   PIC S9(4) COMP.
               05  EMP-COM-IND   PIC S9(4) COMP.
               05  EMP-DEP-IND   PIC S9(4) COMP.
               EXEC SQL END DECLARE SECTION END-EXEC.

               EXEC SQL INCLUDE SQLCA END-EXEC.

           01  DISPLAY-VARIABLES.
               05  D-DEP-NUM     PIC Z(3)9.
               05  D-EMP-NAM     PIC X(10).
               05  D-EMP-SAL     PIC Z(4)9.99.
               05  D-EMP-COM     PIC Z(4)9.99.
               05  D-EMP-DEP     PIC 9(2).

           PROCEDURE DIVISION.

           BEGIN-PGM.
               EXEC SQL
                   WHENEVER SQLERROR DO PERFORM SQL-ERROR
               END-EXEC.
               PERFORM LOGON.
               EXEC SQL
                   ALLOCATE :EMP-CUR
               END-EXEC.
               DISPLAY "Enter department number (0 to exit):  "
                   WITH NO ADVANCING.
               ACCEPT D-EMP-DEP.
               MOVE D-EMP-DEP TO EMP-DEP.
               IF EMP-DEP <= 0
                   GO TO SIGN-OFF
               END-IF.
               MOVE EMP-DEP TO D-DEP-NUM.
               EXEC SQL EXECUTE
                   BEGIN
                       emp_demo_pkg.open_cur(:EMP-CUR, :EMP-DEP);
                   END;
               END-EXEC.
               DISPLAY " ".
               DISPLAY "For department ", D-DEP-NUM, ":".
               DISPLAY " ".
               DISPLAY "EMPLOYEE   SALARY     COMMISSION".
               DISPLAY "---------- ---------- ----------".

           FETCH-LOOP.
               EXEC SQL
                   WHENEVER NOT FOUND GOTO CLOSE-UP
               END-EXEC.
               MOVE SPACES TO EMP-NAM-ARR.
               EXEC SQL FETCH :EMP-CUR
                   INTO :EMP-NUM:EMP-NUM-IND,
                        :EMP-NAM:EMP-NAM-IND,
                        :EMP-JOB:EMP-JOB-IND,
                        :EMP-MGR:EMP-MGR-IND,
                        :EMP-DAT:EMP-DAT-IND,
                        :EMP-SAL:EMP-SAL-IND,
                        :EMP-COM:EMP-COM-IND,
                        :EMP-DEP:EMP-DEP-IND
               END-EXEC.
               MOVE EMP-SAL TO D-EMP-SAL.
               IF EMP-COM-IND = 0
                   MOVE EMP-COM TO D-EMP-COM
                   DISPLAY EMP-NAM-ARR, "   ", D-EMP-SAL,
                           "   ", D-EMP-COM
               ELSE
                   DISPLAY EMP-NAM-ARR, "   ", D-EMP-SAL,
                           "        N/A"
               END-IF.
               GO TO FETCH-LOOP.

           LOGON.
               MOVE "SCOTT" TO USERNAME-ARR.
               MOVE 5 TO USERNAME-LEN.
               MOVE "TIGER" TO PASSWD-ARR.
               MOVE 5 TO PASSWD-LEN.
               MOVE "INST1_ALIAS" TO HOST-ARR.
               MOVE 11 TO HOST-LEN.
               EXEC SQL
                   CONNECT :USERNAME IDENTIFIED BY :PASSWD
               END-EXEC.
               DISPLAY " ".
               DISPLAY "CONNECTED TO ORACLE AS USER: ", USERNAME-ARR.

           CLOSE-UP.
               EXEC SQL
                   CLOSE :EMP-CUR
               END-EXEC.
               EXEC SQL
                   FREE :EMP-CUR
               END-EXEC.
           SIGN-OFF.
               DISPLAY " ".
               DISPLAY "HAVE A GOOD DAY.".
               DISPLAY " ".
               EXEC SQL
                   COMMIT WORK RELEASE
               END-EXEC.
               STOP RUN.

           SQL-ERROR.
               EXEC SQL
                   WHENEVER SQLERROR CONTINUE
               END-EXEC.
               DISPLAY " ".
               DISPLAY "ORACLE ERROR DETECTED:".
               DISPLAY " ".
               DISPLAY SQLERRMC.
               EXEC SQL
                   ROLLBACK WORK RELEASE
               END-EXEC.
               STOP RUN.
