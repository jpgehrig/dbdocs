This chapter shows you how to improve performance by embedding PL/SQL transaction processing blocks in your program. This chapter contains the following topics:

- Advantages of PL/SQL

- Embedded PL/SQL Blocks

- Host Variables

- Indicator Variables

- Host Arrays

- Cursor Usage in Embedded PL/SQL

- Stored PL/SQL and Java Subprograms

- External Procedures

- About Using Dynamic SQL

**Related Topics**

- Embedded PL/SQL

### 7.1 Advantages of PL/SQL

This section looks at some of the features and benefits offered by PL/SQL, such as:

- Better Performance

- Integration with Oracle

- Cursor FOR Loops

- Procedures and Functions

- Packages

- PL/SQL Tables

- User-Defined Records

**Related Topics**

- [Oracle Database PL/SQL Language Reference](../lnpls/index.md)

#### 7.1.1 Better Performance

PL/SQL can help you reduce overhead, improve performance, and increase productivity. For example, without PL/SQL, Oracle must process SQL statements one at a time. Each SQL statement results in another call to the Server and higher overhead. However, with PL/SQL, you can send an entire block of SQL statements to the Server. This minimizes communication between your application and Oracle.

#### 7.1.2 Integration with Oracle

PL/SQL is tightly integrated with the Oracle Server. For example, most PL/SQL datatypes are native to the Oracle data dictionary. Furthermore, you can use the %TYPE attribute to base variable declarations on column definitions stored in the data dictionary, as the following example shows:

    job_title  emp.job%TYPE;

That way, you need not know the exact datatype of the column. Furthermore, if a column definition changes, the variable declaration changes accordingly and automatically. This provides data independence, reduces maintenance costs, and allows programs to adapt as the database changes.

#### 7.1.3 Cursor FOR Loops

With PL/SQL, you need not use the DECLARE, OPEN, FETCH, and CLOSE statements to define and manipulate a cursor. Instead, you can use a cursor FOR loop, which implicitly declares its loop index as a record, opens the cursor associated with a given query, repeatedly fetches data from the cursor into the record, then closes the cursor. An example follows:

    DECLARE
    ...
    BEGIN
       FOR emprec IN (SELECT empno, sal, comm FROM emp) LOOP
       IF emprec.comm / emprec.sal > 0.25 THEN ...
       ...
    END LOOP;
    END;

Notice that you use dot notation to reference components in the record.

#### 7.1.4 Procedures and Functions

PL/SQL has two types of subprograms called procedures and functions, which aid application development by letting you isolate operations. Generally, you use a procedure to perform an action and a function to compute a value.

Procedures and functions provide extensibility. That is, they let you tailor the PL/SQL language to suit your needs. For example, if you need a procedure that creates a new department, just write your own as follows:

    PROCEDURE create_dept
      (new_dname  IN CHAR(14),
       new_loc    IN CHAR(13),
       new_deptno OUT NUMBER(2)) IS
    BEGIN
       SELECT deptno_seq.NEXTVAL INTO new_deptno FROM dual;
       INSERT INTO dept VALUES (new_deptno, new_dname, new_loc);
    END create_dept;

When called, this procedure accepts a new department name and location, selects the next value in a department-number database sequence, inserts the new number, name, and location into the dept table, then returns the new number to the caller.

You use parameter modes to define the behavior of formal parameters. There are three parameter modes: IN (the default), OUT, and IN OUT. An IN parameter lets you pass values to the subprogram being called. An OUT parameter lets you return values to the caller of a subprogram. An IN OUT parameter lets you pass initial values to the subprogram being called and return updated values to the caller.

The datatype of each actual parameter must be convertible to the datatype of its corresponding formal parameter. Table 7-1 shows the legal conversions between datatypes.

#### 7.1.5 Packages

PL/SQL lets you bundle logically related types, program objects, and subprograms into a package. With the Procedural Database Extension, packages can be compiled and stored in an Oracle database, where their contents can be shared by many applications.

Packages usually have two parts: a specification and a body. The specification is the interface to your applications; it declares the types, constants, variables, exceptions, cursors, and subprograms available for use. The body defines cursors and subprograms; it implements the specification. In the following example, you "package" two employment procedures:

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

#### 7.1.6 PL/SQL Tables

PL/SQL provides a composite datatype named TABLE. Objects of type TABLE are called PL/SQL tables, which are modeled as (but not the same as) database tables. PL/SQL tables have only one column and use a primary key to give you array-like access to rows. The column can belong to any scalar type (such as CHAR, DATE, or NUMBER), but the primary key must belong to type BINARY_INTEGER, PLS_INTEGER or VARCHAR2.

You can declare PL/SQL table types in the declarative part of any block, procedure, function, or package. In the following example, you declare a TABLE type called NumTabTyp:

    ...
    DECLARE
       TYPE NumTabTyp IS TABLE OF NUMBER
          INDEX BY BINARY_INTEGER;
    ...
    BEGIN
       ...
    END;
    ...

Once you define type NumTabTyp, you can declare PL/SQL tables of that type, as the next example shows:

    num_tab  NumTabTyp;

The identifier num_tab represents an entire PL/SQL table.

You reference rows in a PL/SQL table using array-like syntax to specify the primary key value. For example, you reference the ninth row in the PL/SQL table named num_tab as follows:

    num_tab(9) ...

#### 7.1.7 User-Defined Records

You can use the %ROWTYPE attribute to declare a record that represents a row in a table or a row fetched by a cursor. However, you cannot specify the datatypes of components in the record or define components of your own. The composite datatype RECORD lifts those restrictions.

Objects of type RECORD are called records. Unlike PL/SQL tables, records have uniquely named components, which can belong to different datatypes. For example, suppose you have different kinds of data about an employee such as name, salary, hire date, and so on. This data is dissimilar in type but logically related. A record that contains such components as the name, salary, and hire date of an employee would let you treat the data as a logical unit.

You can declare record types and objects in the declarative part of any block, procedure, function, or package. In the following example, you declare a RECORD type called DeptRecTyp:

    DECLARE
    TYPE DeptRecTyp IS RECORD
        (deptno  NUMBER(4) NOT NULL, -- default is NULL allowed
        dname   CHAR(9),
        loc     CHAR(14));

Notice that the component declarations are like variable declarations. Each component has a unique name and specific datatype. You can add the NOT NULL option to any component declaration and so prevent the assigning of NULLs to that component.

Once you define type DeptRecTyp, you can declare records of that type, as the next example shows:

    dept_rec  DeptRecTyp;

The identifier dept_rec represents an entire record.

You use dot notation to reference individual components in a record. For example, you reference the dname component in the dept_rec record as follows:

    dept_rec.dname ...

### 7.2 Embedded PL/SQL Blocks

The Pro\*C/C++ Precompiler treats a PL/SQL block like a single embedded SQL statement. So, you can place a PL/SQL block anywhere in a program that you can place a SQL statement.

To embed a PL/SQL block in your Pro\*C/C++ program, simply bracket the PL/SQL block with the keywords EXEC SQL EXECUTE and END-EXEC as follows:

    EXEC SQL EXECUTE
    DECLARE
    ...
    BEGIN
       ...
    END;
    END-EXEC;

The keyword END-EXEC must be followed by a semicolon.

After writing your program, you precompile the source file in the usual way.

When the program contains embedded PL/SQL, you must use the SQLCHECK=SEMANTICS command-line option, since the PL/SQL must be parsed by the Oracle Server. SQLCHECK=SEMANTICS requires the USERID option also, to connect to a server.

**Related Topics**

- [About Using the Precompiler Options](precompiler-options.md)

### 7.3 Host Variables

Host variables are the key to communication between a host language and a PL/SQL block. Host variables can be shared with PL/SQL, meaning that PL/SQL can set and reference host variables.

For example, you can prompt a user for information and use host variables to pass that information to a PL/SQL block. Then, PL/SQL can access the database and use host variables to pass the results back to your host program.

Inside a PL/SQL block, host variables are treated as global to the entire block and can be used anywhere a PL/SQL variable is allowed. Like host variables in a SQL statement, host variables in a PL/SQL block must be prefixed with a colon. The colon sets host variables apart from PL/SQL variables and database objects.

**Note:**

To use VARCHAR, CHARZ, or STRING types as output host variables in PL/SQL blocks, you must initialize the length before entering the block. Set the length to the declared (maximum) length of the VARCHAR, CHARZ, or STRING.

**Related Topics**

- [Pointer Variables](datatypes-and-host-variables.md)

#### 7.3.1 Example: Using Host Variables with PL/SQL

The following example illustrates the use of host variables with PL/SQL. The program prompts the user for an employee number, then displays the job title, hire date, and salary of that employee.

    char username[100], password[20];
    char job_title[20], hire_date[9], temp[32];
    int emp_number;
    float salary;

    #include <sqlca.h>

    printf("Username? \n");
    gets(username);
    printf("Password? \n");
    gets(password);

    EXEC SQL WHENEVER SQLERROR GOTO sql_error;

    EXEC SQL CONNECT :username IDENTIFIED BY :password;
    printf("Connected to Oracle\n");
    for (;;)
    {
       printf("Employee Number (0 to end)? ");
       gets(temp);
       emp_number = atoi(temp);

       if (emp_number == 0)
       {
          EXEC SQL COMMIT WORK RELEASE;
          printf("Exiting program\n");
          break;
       }
    /*-------------- begin PL/SQL block -----------------*/
       EXEC SQL EXECUTE
       BEGIN
          SELECT job, hiredate, sal
             INTO :job_title, :hire_date, :salary
             FROM emp
             WHERE empno = :emp_number;
       END;
       END-EXEC;
    /*-------------- end PL/SQL block -----------------*/

       printf("Number  Job Title  Hire Date  Salary\n");
       printf("------------------------------------\n");
       printf("%6d  %8.8s  %9.9s  %6.2f\n",
       emp_number, job_title, hire_date, salary);
    }
    ...
    exit(0);

    sql_error:
    EXEC SQL WHENEVER SQLERROR CONTINUE;
    EXEC SQL ROLLBACK WORK RELEASE;
    printf("Processing error\n");
    exit(1);

Notice that the host variable emp_number is set before the PL/SQL block is entered, and the host variables job_title, hire_date, and salary are set inside the block.

#### 7.3.2 Complex Example

In the example later, you prompt the user for a bank account number, transaction type, and transaction amount, then debit or credit the account. If the account does not exist, you raise an exception. When the transaction is complete, you display its status.

    #include <stdio.h>
    #include <sqlca.h>

    char username[20];
    char password[20];
    char status[80];
    char temp[32];
    int  acct_num;
    double trans_amt;
    void sql_error();

    main()
    {
       char trans_type;

       strcpy(password, "TIGER");
       strcpy(username, "SCOTT");

       EXEC SQL WHENEVER SQLERROR DO sql_error();
       EXEC SQL CONNECT :username IDENTIFIED BY :password;
       printf("Connected to Oracle\n");

       for (;;)
       {
          printf("Account Number (0 to end)? ");
          gets(temp);
          acct_num = atoi(temp);

          if(acct_num == 0)
          {
             EXEC SQL COMMIT WORK RELEASE;
             printf("Exiting program\n");
             break;
          }

          printf("Transaction Type - D)ebit or C)redit? ");
          gets(temp);
          trans_type = temp[0];

          printf("Transaction Amount? ");
          gets(temp);
          trans_amt = atof(temp);

    /*----------------- begin PL/SQL block -------------------*/
          EXEC SQL EXECUTE
          DECLARE
             old_bal      NUMBER(9,2);
             err_msg      CHAR(70);
             nonexistent  EXCEPTION;

          BEGIN
             :trans_type := UPPER(:trans_type);
             IF :trans_type = 'C' THEN       -- credit the account
                UPDATE accts SET bal = bal + :trans_amt
                WHERE acctid = :acct_num;
                IF SQL%ROWCOUNT = 0 THEN    -- no rows affected
                   RAISE nonexistent;
                ELSE
                   :status := 'Credit applied';
                END IF;
             ELSIF :trans_type = 'D' THEN    -- debit the account
                SELECT bal INTO old_bal FROM accts
                   WHERE acctid = :acct_num;
                IF old_bal >= :trans_amt THEN   -- enough funds
                   UPDATE accts SET bal = bal - :trans_amt
                      WHERE acctid = :acct_num;
                   :status := 'Debit applied';
                ELSE
                   :status := 'Insufficient funds';
                END IF;
             ELSE
                :status := 'Invalid type: ' || :trans_type;
             END IF;
             COMMIT;
          EXCEPTION
             WHEN NO_DATA_FOUND OR nonexistent THEN
                :status := 'Nonexistent account';
             WHEN OTHERS THEN
                err_msg := SUBSTR(SQLERRM, 1, 70);
                :status := 'Error: ' || err_msg;
          END;
          END-EXEC;
    /*----------------- end PL/SQL block ----------------------- */

          printf("\nStatus: %s\n", status);
       }
       exit(0);
    }

    void
    sql_error()
    {
        EXEC SQL WHENEVER SQLERROR CONTINUE;
        EXEC SQL ROLLBACK WORK RELEASE;
        printf("Processing error\n");
        exit(1);
    }

#### 7.3.3 VARCHAR Pseudotype

You can use the VARCHAR datatype to declare variable-length character strings. If the VARCHAR is an input host variable, you must tell Oracle what length to expect. Therefore, set the length component to the actual length of the value stored in the string component.

If the VARCHAR is an output host variable, Oracle automatically sets the length component. However, to use a VARCHAR (as well as CHARZ and STRING) output host variable in your PL/SQL block, you must initialize the length component before entering the block. So, set the length component to the declared (maximum) length of the VARCHAR, as shown here:

    int     emp_number;
    varchar emp_name[10];
    float   salary;
    ...
    emp_name.len = 10;   /* initialize length component */

    EXEC SQL EXECUTE
      BEGIN
        SELECT ename, sal INTO :emp_name, :salary
            FROM emp
            WHERE empno = :emp_number;
        ...
      END;
    END-EXEC;
    ...

#### 7.3.4 Restriction

Do not use C pointer or array syntax in PL/SQL blocks. The PL/SQL compiler does not understand C host-variable expressions and is, therefore, unable to parse them. For example, the following is invalid:

    EXEC SQL EXECUTE
        BEGIN
            :x[5].name := 'SCOTT';
            ...
        END;
    END-EXEC;

To avoid syntax errors, use a place-holder (a temporary variable), to hold the address of the structure field to populate structures as shown in the following valid example:

    name = x[5].name ;
    EXEC SQL EXECUTE
        BEGIN
            :name := ...;
            ...
        END;
    END-EXEC;

### 7.4 Indicator Variables

PL/SQL does not need indicator variables because it can manipulate NULLs. For example, within PL/SQL, you can use the IS NULL operator to test for NULLs, as follows:

    IF variable IS NULL THEN ...

And, you can use the assignment operator (:=) to assign NULLs, as follows:

    variable := NULL;

However, a host language such as C needs indicator variables because it cannot manipulate NULLs. Embedded PL/SQL meets this need by letting you use indicator variables to

- Accept NULLs input from a host program

- Output NULLs or truncated values to a host program

When used in a PL/SQL block, indicator variables are subject to the following rules:

- You cannot refer to an indicator variable by itself; it must be appended to its associated host variable.

- If you refer to a host variable with its indicator variable, you must always refer to it that way in the same block.

In the following example, the indicator variable ind_comm appears with its host variable commission in the SELECT statement, so it must appear that way in the IF statement:

    ...
    EXEC SQL EXECUTE
    BEGIN
        SELECT ename, comm
            INTO :emp_name, :commission :ind_comm
            FROM emp
            WHERE empno = :emp_number;
        IF :commission :ind_comm IS NULL THEN ...
        ...
    END;
    END-EXEC;

Notice that PL/SQL treats :commission :ind_comm like any other simple variable. Though you cannot refer directly to an indicator variable inside a PL/SQL block, PL/SQL checks the value of the indicator variable when entering the block and sets the value correctly when exiting the block.

#### 7.4.1 NULLs Handling

When entering a block, if an indicator variable has a value of -1, PL/SQL automatically assigns a NULL to the host variable. When exiting the block, if a host variable is NULL, PL/SQL automatically assigns a value of -1 to the indicator variable. In the next example, if ind_sal had a value of -1 before the PL/SQL block was entered, the salary_missing exception is raised. An exception is a named error condition.

    ...
    EXEC SQL EXECUTE
    BEGIN
        IF :salary :ind_sal IS NULL THEN
        RAISE salary_missing;
    END IF;
    ...
    END;
    END-EXEC;
    ...

#### 7.4.2 Truncated Values

PL/SQL does not raise an exception when a truncated string value is assigned to a host variable. However, if you use an indicator variable, PL/SQL sets it to the original length of the string. In the following example, the host program will be able to tell, by checking the value of ind_name, if a truncated value was assigned to emp_name:

    ...
    EXEC SQL EXECUTE
    DECLARE
    ...
    new_name  CHAR(10);
    BEGIN
        ...
        :emp_name:ind_name := new_name;
        ...
    END;
    END-EXEC;

### 7.5 Host Arrays

You can pass input host arrays and indicator arrays to a PL/SQL block. They can be indexed by a PL/SQL variable of type BINARY_INTEGER or PLS_INTEGER; VARCHAR2 key types are not permitted. Normally, the entire host array is passed to PL/SQL, but you can use the ARRAYLEN statement (discussed later) to specify a smaller array dimension.

Furthermore, you can use a procedure call to assign all the values in a host array to rows in a PL/SQL table. Given that the array subscript range is m .. n, the corresponding PL/SQL table index range is always 1 .. n - m + 1. For example, if the array subscript range is 5 .. 10, the corresponding PL/SQL table index range is 1 .. (10 - 5 + 1) or 1 .. 6.

In the following example, you pass an array named salary to a PL/SQL block, which uses the array in a function call. The function is named median because it finds the middle value in a series of numbers. Its formal parameters include a PL/SQL table named num_tab. The function call assigns all the values in the actual parameter salary to rows in the formal parameter num_tab.

    ...
    float salary[100];

    /* populate the host array */

    EXEC SQL EXECUTE
      DECLARE
        TYPE NumTabTyp IS TABLE OF REAL
            INDEX BY BINARY_INTEGER;
        median_salary  REAL;
        n  BINARY_INTEGER;
    ...
      FUNCTION median (num_tab NumTabTyp, n INTEGER)
        RETURN REAL IS
      BEGIN
        -- compute median
      END;
      BEGIN
        n := 100;
        median_salary := median(:salary, n);
        ...
      END;
    END-EXEC;
    ...

**Note:**

In dynamic SQL Method 4, you cannot bind a host array to a PL/SQL procedure with a parameter of type "table."

You can also use a procedure call to assign all row values in a PL/SQL table to corresponding elements in a host array.

Table 7-1 shows the legal conversions between row values in a PL/SQL table and elements in a host array. For example, a host array of type LONG is compatible with a PL/SQL table of type VARCHAR2, LONG, RAW, or LONG RAW. Notably, it is not compatible with a PL/SQL table of type CHAR.

Table 7-1 Legal Datatype Conversions

| PL/SQL Table-\>Host Array | CHAR | DATE | LONG | LONG RAW | NUMBER | RAW | ROWID | VARCHAR2 |
|:--------------------------|:-----|:-----|:-----|:---------|:-------|:----|:------|:---------|
| CHARF                     | X    | \-   | \-   | \-       | \-     | \-  | \-    | \-       |
| CHARZ                     | X    | \-   | \-   | \-       | \-     | \-  | \-    | \-       |
| DATE                      | \-   | X    | \-   | \-       | \-     | \-  | \-    | \-       |
| DECIMAL                   | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| DISPLAY                   | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| FLOAT                     | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| INTEGER                   | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| LONG                      | X    | \-   | X    | \-       | \-     | \-  | \-    | \-       |
| LONG VARCHAR              | \-   | \-   | X    | X        | \-     | X   | \-    | X        |
| LONG VARRAW               | \-   | \-   | \-   | X        | \-     | X   | \-    | \-       |
| NUMBER                    | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| RAW                       | \-   | \-   | \-   | X        | \-     | X   | \-    | \-       |
| ROWID                     | \-   | \-   | \-   | \-       | \-     | \-  | X     | \-       |
| STRING                    | \-   | \-   | X    | X        | \-     | X   | \-    | X        |
| UNSIGNED                  | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| VARCHAR                   | \-   | \-   | X    | X        | \-     | X   | \-    | X        |
| VARCHAR2                  | \-   | \-   | X    | X        | \-     | X   | \-    | X        |
| VARNUM                    | \-   | \-   | \-   | \-       | X      | \-  | \-    | \-       |
| VARRAW                    | \-   | \-   | \-   | X        | \-     | X   | \-    | \-       |

**Note:**

The Pro\*C/C++ Precompiler does not check your usage of host arrays. For instance, no index range-checking is done.

**Related Topics**

- [Using Method 4](Oracle-dynamic-SQL.md)
- Stored PL/SQL and Java Subprograms

#### 7.5.1 ARRAYLEN Statement

Suppose you must pass an input host array to a PL/SQL block for processing. By default, when binding such a host array, the Pro\*C/C++ Precompiler uses its declared dimension. However, you might not want to process the entire array. In that case, you can use the ARRAYLEN statement to specify a smaller array dimension. ARRAYLEN associates the host array with a host variable, which stores the smaller dimension. The statement syntax is

    EXEC SQL ARRAYLEN host_array (dimension) [EXECUTE];

where dimension is a 4-byte integer host variable, not a literal or expression.

EXECUTE is an optional keyword.

The ARRAYLEN statement must appear along with, but somewhere after, the declarations of host_array and dimension. You cannot specify an offset into the host array. However, you might be able to use C features for that purpose. The following example uses ARRAYLEN to override the default dimension of a C host array named bonus:

    float bonus[100];
    int dimension;
    EXEC SQL ARRAYLEN bonus (dimension);
    /* populate the host array */
    ...
    dimension = 25;  /* set smaller array dimension */
    EXEC SQL EXECUTE
    DECLARE
        TYPE NumTabTyp IS TABLE OF REAL
        INDEX BY BINARY_INTEGER;
        median_bonus  REAL;
        FUNCTION median (num_tab NumTabTyp, n INTEGER)
            RETURN REAL IS
      BEGIN
        -- compute median
      END;
      BEGIN
        median_bonus := median(:bonus, :dimension);
        ...
      END;
    END-EXEC;

Only 25 array elements are passed to the PL/SQL block because ARRAYLEN reduces the array from 100 to 25 elements. As a result, when the PL/SQL block is sent to Oracle for execution, a much smaller host array is sent along. This saves time and, in a networked environment, reduces network traffic.

#### 7.5.2 Optional Keyword EXECUTE

Host arrays used in a dynamic SQL method 2 EXEC SQL EXECUTE statement may have two different interpretations based on the presence or absence of the optional keyword EXECUTE.

By default (if the EXECUTE keyword is absent on an ARRAYLEN statement):

- The host array is considered when determining the number of times a PL/SQL block will be executed. (The minimum array dimension is used.)

- The host array must not be bound to a PL/SQL index table.

If the keyword EXECUTE is present:

- The host array must be bound to an index table.

- The PL/SQL block will be executed one time.

- All host variables specified in the EXEC SQL EXECUTE statement must either

  - Be specified in an ARRAYLEN ... EXECUTE statement

  - Be scalar.

For example, given the following PL/SQL procedure:

       CREATE OR REPLACE PACKAGE pkg AS
              TYPE tab IS TABLE OF NUMBER(5) INDEX BY BINARY_INTEGER;
              PROCEDURE proc1 (parm1 tab, parm2 NUMBER, parm3 tab);
       END;


The following Pro\*C/C++ function demonstrates how host arrays can be used to determine how many times a given PL/SQL block is executed. In this case, the PL/SQL block will be executed 3 times resulting in 3 new rows in the `emp` table.

    func1()
    {
      int empno_arr[5] = {1111, 2222, 3333, 4444, 5555};
      char *ename_arr[3] = {"MICKEY", "MINNIE", "GOOFY"};
      char *stmt1 = "BEGIN INSERT INTO emp(empno, ename) VALUES :b1, :b2; END;";

      EXEC SQL PREPARE s1 FROM :stmt1;
      EXEC SQL EXECUTE s1 USING :empno_arr, :ename_arr;
    }


The following Pro\*C/C++ function demonstrates how to bind a host array to a PL/SQL index table through dynamic method 2. Note the presence of the ARRAYLEN...EXECUTE statement for all host arrays specified in the EXEC SQL EXECUTE statement.

    func2()
    {
      int ii = 2;
      int int_tab[3] = {1,2,3};
      int dim = 3;
      EXEC SQL ARRAYLEN int_tab (dim) EXECUTE;

      char *stmt2 = "begin pkg.proc1(:v1, :v2, :v3); end; ";

      EXEC SQL PREPARE s2 FROM :stmt2;
      EXEC SQL EXECUTE s2 USING :int_tab, :ii, :int_tab;
    }


However the following Pro\*C/C++ function will result in a precompile-time warning because there is no ARRAYLEN...EXECUTE statement for `int_arr`.

    func3()
    {
      int int_arr[3];
      int int_tab[3] = {1,2,3};
      int dim = 3;
      EXEC SQL ARRAYLEN int_tab (dim) EXECUTE;

      char *stmt3 = "begin pkg.proc1(:v1, :v2, :v3); end; ";

      EXEC SQL PREPARE s3 FROM :stmt3;
      EXEC SQL EXECUTE s3 USING :int_tab, :int_arr, :int_tab;
    }

**Related Topics**

- [Using Method 2](Oracle-dynamic-SQL.md)
- [Host Arrays](host-arrays.md)

### 7.6 Cursor Usage in Embedded PL/SQL

The maximum number of cursors your program can use simultaneously is determined by the database initialization parameter OPEN_CURSORS. While executing an embedded PL/SQL block, one cursor. the parent cursor, is associated with the entire block and one cursor, the child cursor, is associated with each SQL statement in the embedded PL/SQL block. Both parent and child cursors count toward the `OPEN_CURSORS` limit.

The following calculation shows how to determine the maximum number of cursors used. The sum of the cursors used must not exceed `OPEN_CURSORS`.

       SQL statement cursors
       PL/SQL parent cursors
       PL/SQL child cursors
    +  6 cursors for overhead
    --------------------------
       Sum of cursors in use

If your program exceeds the limit imposed by `OPEN_CURSORS`, Oracle gives you an error.

**Related Topics**

- [Embedded PL/SQL Considerations](performance-tuning.md)

### 7.7 Stored PL/SQL and Java Subprograms

Unlike anonymous blocks, PL/SQL subprograms (procedures and functions) and Java methods can be compiled separately, stored in an Oracle database, and invoked.

A subprogram explicitly created using an Oracle tool such as SQL\*Plus is called a stored subprogram. Once compiled and stored in the data dictionary, it is a database object, which can be re-executed without being recompiled.

When a subprogram within a PL/SQL block or stored procedure is sent to Oracle by your application, it is called an inline subprogram. Oracle compiles the inline subprogram and caches it in the System Global Area (SGA) but does not store the source or object code in the data dictionary.

Subprograms defined within a package are considered part of the package, and thus are called packaged subprograms. Stored subprograms not defined within a package are called standalone subprograms.

**Related Topics**

- [Java Applications on Oracle Database](../jjdev/Java-applications-in-database.md)

#### 7.7.1 About Creating Stored Subprograms

You can embed the SQL statements CREATE FUNCTION, CREATE PROCEDURE, and CREATE PACKAGE in a host program, as the following example shows:

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
    END-EXEC;

Notice that the embedded CREATE {FUNCTION \| PROCEDURE \| PACKAGE} statement is a hybrid. Like all other embedded CREATE statements, it begins with the keywords EXEC SQL (not EXEC SQL EXECUTE). But, unlike other embedded CREATE statements, it ends with the PL/SQL terminator END-EXEC.

In the example later, you create a package that contains a procedure named get_employees, which fetches a batch of rows from the EMP table. The batch size is determined by the caller of the procedure, which might be another stored subprogram or a client application.

The procedure declares three PL/SQL tables as OUT formal parameters, then fetches a batch of employee data into the PL/SQL tables. The matching actual parameters are host arrays. When the procedure finishes, it automatically assigns all row values in the PL/SQL tables to corresponding elements in the host arrays.

    EXEC SQL CREATE OR REPLACE PACKAGE emp_actions AS
        TYPE CharArrayTyp IS TABLE OF VARCHAR2(10)
            INDEX BY BINARY_INTEGER;
        TYPE NumArrayTyp IS TABLE OF FLOAT
            INDEX BY BINARY_INTEGER;
      PROCEDURE get_employees(
        dept_number IN     INTEGER,
        batch_size  IN     INTEGER,
        found       IN OUT INTEGER,
        done_fetch  OUT    INTEGER,
        emp_name    OUT    CharArrayTyp,
        job_title   OUT    CharArrayTyp,
        salary      OUT    NumArrayTyp);
      END emp_actions;
    END-EXEC;
    EXEC SQL CREATE OR REPLACE PACKAGE BODY emp_actions AS

        CURSOR get_emp (dept_number IN INTEGER) IS
            SELECT ename, job, sal FROM emp
                WHERE deptno = dept_number;

      PROCEDURE get_employees(
        dept_number IN     INTEGER,
        batch_size  IN     INTEGER,
        found       IN OUT INTEGER,
        done_fetch  OUT    INTEGER,
        emp_name    OUT    CharArrayTyp,
        job_title   OUT    CharArrayTyp,
        salary      OUT    NumArrayTyp) IS

      BEGIN
        IF NOT get_emp%ISOPEN THEN
            OPEN get_emp(dept_number);
        END IF;
        done_fetch := 0;
        found := 0;
        FOR i IN 1..batch_size LOOP
            FETCH get_emp INTO emp_name(i),
            job_title(i), salary(i);
            IF get_emp%NOTFOUND THEN
                CLOSE get_emp;
                done_fetch := 1;
                EXIT;
            ELSE
                found := found + 1;
            END IF;
        END LOOP;
      END get_employees;
    END emp_actions;
    END-EXEC;

You specify the REPLACE clause in the CREATE statement to redefine an existing package without having to drop the package, re-create it, and re-grant privileges on it. For the full syntax of the CREATE statement see [SQL Statements: COMMIT to CREATE JAVA](../sqlrf/SQL-Statements-COMMIT-to-CREATE-JAVA.md).

If an embedded CREATE {FUNCTION \| PROCEDURE \| PACKAGE} statement fails, Oracle generates a warning, not an error.

#### 7.7.2 About Calling a Stored PL/SQL or Java Subprogram

To call a stored subprogram from your host program, you can use either an anonymous PL/SQL block, or the CALL embedded SQL statement.

##### 7.7.2.1 Anonymous PL/SQL Block

In the following example, you call a standalone procedure named raise_salary:

    EXEC SQL EXECUTE
      BEGIN
        raise_salary(:emp_id, :increase);
      END;
    END-EXEC;

Notice that stored subprograms can take parameters. In this example, the actual parameters emp_id and increase are C host variables.

In the next example, the procedure raise_salary is stored in a package named emp_actions, so you must use dot notation to fully qualify the procedure call:

    EXEC SQL EXECUTE
    BEGIN
        emp_actions.raise_salary(:emp_id, :increase);
    END;
    END-EXEC;

An actual IN parameter can be a literal, scalar host variable, host array, PL/SQL constant or variable, PL/SQL table, PL/SQL user-defined record, procedure call, or expression. However, an actual OUT parameter cannot be a literal, procedure call, or expression.

You must use precompiler option SQLCHECK=SEMANTICS with an embedded PL/SQL block.

In the following example, three of the formal parameters are PL/SQL tables, and the corresponding actual parameters are host arrays. The program calls the stored procedure get_employees repeatedly, displaying each batch of employee data, until no more data is found. This program is available on-line in the `demo` directory, in the file `sample9.pc`. A SQL script to create the CALLDEMO stored package is available in the file `calldemo.sql`.

    /*************************************************************
    Sample Program 9:  Calling a stored procedure

    This program connects to ORACLE using the SCOTT/TIGER
    account.  The program declares several host arrays, then
    calls a PL/SQL stored procedure (GET_EMPLOYEES in the
    CALLDEMO package) that fills the table OUT parameters.  The
    PL/SQL procedure returns up to ASIZE values.

    Sample9 keeps calling GET_EMPLOYEES, getting ASIZE arrays
    each time, and printing the values, until all rows have been
    retrieved.  GET_EMPLOYEES sets the done_flag to indicate "no
    more data."
    *************************************************************/
    #include <stdio.h>
    #include <string.h>

    EXEC SQL INCLUDE sqlca.h;

    typedef char asciz[20];
    typedef char vc2_arr[11];

    EXEC SQL BEGIN DECLARE SECTION;
    /* User-defined type for null-terminated strings */
    EXEC SQL TYPE asciz  IS STRING(20) REFERENCE;

    /* User-defined type for a VARCHAR array element. */
    EXEC SQL TYPE vc2_arr IS VARCHAR2(11) REFERENCE;

    asciz     username;
    asciz     password;
    int       dept_no;              /* which department to query? */
    vc2_arr   emp_name[10];            /* array of returned names */
    vc2_arr   job[10];
    float     salary[10];
    int       done_flag;
    int       array_size;
    int       num_ret;                 /* number of rows returned */
    EXEC SQL END DECLARE SECTION;

    long      SQLCODE;

    void print_rows();            /* produces program output      */
    void sql_error();             /* handles unrecoverable errors */

    main()
    {
       int   i;
       char  temp_buf[32];

    /* Connect to ORACLE. */
       EXEC SQL WHENEVER SQLERROR DO sql_error();
       strcpy(username, "scott");
       strcpy(password, "tiger");
       EXEC SQL CONNECT :username IDENTIFIED BY :password;
       printf("\nConnected to ORACLE as user: %s\n\n", username);
       printf("Enter department number: ");
       gets(temp_buf);
       dept_no = atoi(temp_buf);/* Print column headers. */
       printf("\n\n");
       printf("%-10.10s%-10.10s%s\n", "Employee", "Job", "Salary");
       printf("%-10.10s%-10.10s%s\n", "--------", "---", "------");

    /* Set the array size. */
       array_size = 10;

       done_flag = 0;
       num_ret = 0;

    /*  Array fetch loop.
     *  The loop continues until the OUT parameter done_flag is set.
     *  Pass in the department number, and the array size--
     *  get names, jobs, and salaries back.
     */
       for (;;)
       {
          EXEC SQL EXECUTE
             BEGIN calldemo.get_employees
                (:dept_no, :array_size, :num_ret, :done_flag,
                 :emp_name, :job, :salary);
             END;
          END-EXEC;

          print_rows(num_ret);

          if (done_flag)
             break;
       }

    /* Disconnect from the database. */
       EXEC SQL COMMIT WORK RELEASE;
       exit(0);
    }
    void
    print_rows(n)
    int n;
    {
       int i;

        if (n == 0)
        {
            printf("No rows retrieved.\n");
            return;
        }

        for (i = 0; i < n; i++)
            printf("%10.10s%10.10s%6.2f\n",
                   emp_name[i], job[i], salary[i]);
    }

    /* Handle errors. Exit on any error. */
    void
    sql_error()
    {
       char msg[512];
       int buf_len, msg_len;

       EXEC SQL WHENEVER SQLERROR CONTINUE;

       buf_len = sizeof(msg);
       sqlglm(msg, &buf_len, &msg_len);

       printf("\nORACLE error detected:");
       printf("\n%.*s \n", msg_len, msg);

       EXEC SQL ROLLBACK WORK RELEASE;
       exit(1);
    }

Remember, the datatype of each actual parameter must be convertible to the datatype of its corresponding formal parameter. Also, before a stored procedure is exited, all OUT formal parameters must be assigned values. Otherwise, the values of corresponding actual parameters are indeterminate.

SQLCHECK=SEMANTICS is required when using an anonymous PL/SQL block.

**Related Topics**

- About Creating Stored Subprograms

##### 7.7.2.2 Remote Access

PL/SQL lets you access remote databases using database links. Typically, database links are established by your DBA and stored in the Oracle data dictionary. A database link tells Oracle where the remote database is located, the path to it, and what Oracle username and password to use. In the following example, you use the database link dallas to call the raise_salary procedure:

    EXEC SQL EXECUTE
    BEGIN
        raise_salary@dallas(:emp_id, :increase);
    END;
    END-EXEC;

You can create synonyms to provide location transparency for remote subprograms, as the following example shows:

    CREATE PUBLIC SYNONYM raise_salary
    FOR raise_salary@dallas;

##### 7.7.2.3 The CALL Statement

The concepts presented earlier for the embedded PL/SQL block also hold true for the CALL statement. The CALL embedded SQL statement has the form:

    EXEC SQL
       CALL [schema.] [package.]stored_proc[@db_link](arg1, ...)
       [INTO :ret_var [[INDICATOR]:ret_ind]] ;

where

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

You can use either SQLCHECK=SYNTAX, or SEMANTICS with the CALL statement.

##### 7.7.2.4 CALL Example

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

then to use` fact` in a Pro\*C/C++ application using the CALL statement:

     ...
    int num, fact;
    ...
    EXEC SQL CALL mathpkge.fact(:num) INTO :fact ;
    ...

**See Also:**

- "[CALL (Executable Embedded SQL)](embedded-SQL-statements-and-directives.md)" for more information about the CALL statement.

- [Oracle Database Advanced Application Developer's Guide](../adfns/index.md), for a complete explanation of passing arguments and other issues.

#### 7.7.3 About Getting Information about Stored Subprograms

**Note:**

The Logon Data Area (LDA) is no longer supported in Oracle. The ability to embed OCI Release 7 calls in your Pro\*C/C++ program will be phased out by the next major Oracle release.

[Datatypes and Host Variables](datatypes-and-host-variables.md) described how to embed OCI calls in your host program. After calling the library routine SQLLDA to set up the LDA, use the OCI call odessp to get useful information about a stored subprogram. When you call odessp, you must pass it a valid LDA and the name of the subprogram. For packaged subprograms, you must also pass the name of the package. odessp returns information about each subprogram parameter such as its datatype, size, position, and so on.

You can also use the DESCRIBE_PROCEDURE stored procedure, in the DBMS_DESCRIBE package.

### 7.8 External Procedures

PL/SQL can call C functions which are external procedures. External procedures (also known as external procedures) are stored in dynamic link libraries (DLL) or, for example, in .so libraries under Solaris.

If the external procedure executes on the server-side, it can call back into the server to execute SQL and PL/SQL in the same transaction. External procedures on the server execute faster than on the client and can interface the database server with external systems and data sources.

In order to execute a server-side external C function, the REGISTER CONNECT embedded SQL statement must be used inside that function. The syntax of the statement is:

    EXEC SQL REGISTER CONNECT USING :epctx [RETURNING :host_context] ;

where `epctx` is the external procedure context (of type pointer to `OCIExtProcContext`). `epctx` is passed to the procedure by PL/SQL.

`host_context` is a runtime context returned by the external procedure. Currently, it is the default (global) context.

The REGISTER CONNECT statement will return the set of OCI handles (OCIEnv, OCISvcCtx, and OCIError) that are associated with the current Oracle connection and transaction. These handles are then used to define the Pro\*C/C++ default unnamed connection for the global SQLLIB runtime context. The REGISTER CONNECT statement is therefore used instead of a CONNECT statement.

Subsequent embedded SQL statements will use this set of OCI handles. They execute against the global SQLLIB runtime context and the unnamed connection, even those that are in separately precompiled units. Uncommitted changes are not seen. In the future, a (nondefault) runtime context can be returned in the optional RETURNING clause.

There cannot already be any active default connection for the global runtime context. A runtime error is returned if you try to use REGISTER CONNECT when a connection already exists.

In real-world cases, the external procedure should be one that you can reuse from many different applications.

**Related Topics**

- [Oracle Call Interface Programmer's Guide](../lnoci/index.md)

#### 7.8.1 Restrictions on External Procedures

Follow these rules for external procedures:

- External procedures can only be in C. C++ external procedures are not supported.

- When you are connected to the external procedure context, any additional connection is not permitted and results in a runtime error.

- Multithreaded external procedures are not supported. Executing an EXEC SQL ENABLE THREADS statement is not permitted and will return a runtime error. Pro\*C/C++ does support multithreading in an application not using the external procedure method we are describing.

- You cannot use DDL statements. They result in runtime errors.

- You cannot use transaction control statements, such as EXEC SQL COMMIT, and EXEC SQL ROLLBACK.

- You cannot use object navigation statements such as EXEC SQL OBJECT ... .

- You cannot use polling EXEC SQL LOB statements.

- You cannot use EXEC TOOLS statements. They will result in runtime errors.

#### 7.8.2 About Creating the External Procedure

Here is a simple example to create the external procedure `extp1`.

To store an external C procedure, compile and link the code to a library such as a DLL.

Reference to NT removed user comment 9561

Then use the following SQL command once to register the external procedure `extp1`:

    CREATE OR REPLACE PROCEDURE extp1
    AS EXTERNAL NAME "extp1"
    LIBRARY mylib
    WITH CONTEXT
    PARAMETERS(CONTEXT) ;

Where mylib is the name of the library storing procedure extp1. WITH CONTEXT means to implicitly call this procedure with argument of type` OCIExtProcContext*`. The context is omitted in your call, but is passed to the procedure anyway. The keyword CONTEXT appears in the CREATE statement, however, as a place marker.

This context parameter is the one referenced in the EXEC SQL REGISTER CONNECT statement inside `extp1`.

The external procedure is called from SQL\*Plus this way:

    SQL>
    BEGIN
      INSERT INTO emp VALUES(9999,'JOHNSON','SALESMAN',7782, sysdate, 1200,150,10);
      extp1;
    END;

Here is the listing of `extp1.pc`:

    void extp1 (epctx)
    OCIExtProcContext *epctx;
    {
    char name[15];
            EXEC SQL REGISTER CONNECT USING :epctx;
            EXEC SQL WHENEVER SQLERROR goto err;
            EXEC SQL SELECT ename INTO :name FROM emp WHERE empno = 9999;
            return;
    err: SQLExtProcError(SQL_SINGLE_RCTX,sqlca.sqlerrm.sqlerrmc,sqlca.sqlerrm.sqlerrml);
            return;
    }

**Related Topics**

- [External Subprograms](../lnpls/external-subprograms.md)

#### 7.8.3 SQLExtProcError()

The SQLLIB function `SQLExtProcError()` provides the ability to return control to PL/SQL when an error occurs in an external C procedure. The function and its arguments are:

SQLExtProcError (ctx, msg, msglen)

where:

ctx (IN) sql_context \*

This is the target SQLLIB runtime context of the REGISTER CONNECT statement, which has to be executed before this function is invoked. Only the global runtime context is supported now.

msg (OUT) char \*

The text of the error message.

msglen (OUT) size_t

The length in bytes of the message.

SQLLIB calls the OCI service function OCIExtProcRaiseExcpWithMsg when this function is executed.

The message is from the structure `sqlerrm` in the SQLCA.

Here is an example showing use of `SQLExtProcError()`:

    void extp1 (epctx)
    OCIExtProcContext *epctx;
    {
       char name[15];
       EXEC SQL REGISTER CONNECT USING :epctx;
       EXEC SQL WHENEVER SQLERROR goto err;
       EXEC SQL SELECT ename INTO :name FROM emp WHERE smpno = 9999;
       return;
     err:
       SQLExtProcError (SQL_SINGLE_RCTX, sqlca.sqlerrm.sqlerrmc,
          sqlca.sqlerrm.sqlerrml);
       printf("\n%*s\n", sqlca.sqlerrm.sqlerrml, sqlca.sqlerrm.sqlerrmc);
       return;
    }

**Related Topics**

- [SQLCA Structure](handling-run-time-errors.md)

### 7.9 About Using Dynamic SQL

Recall that the precompiler treats an entire PL/SQL block like a single SQL statement. Therefore, you can store a PL/SQL block in a string host variable. Then, if the block contains no host variables, you can use dynamic SQL Method 1 to EXECUTE the PL/SQL string. Or, if the block contains a known number of host variables, you can use dynamic SQL Method 2 to PREPARE and EXECUTE the PL/SQL string. If the block contains an unknown number of host variables, you must use dynamic SQL Method 4.

**Note:**

In dynamic SQL Method 4, you cannot bind a host array to a PL/SQL procedure with a parameter of type "table."

**Related Topics**

- [ANSI Dynamic SQL](ANSI-dynamic-SQL.md)
- [Oracle Dynamic SQL](Oracle-dynamic-SQL.md)
- [Oracle Dynamic SQL: Method 4](Oracle-dynamic-SQL-method-4.md)
- [Using Method 4](Oracle-dynamic-SQL.md)
