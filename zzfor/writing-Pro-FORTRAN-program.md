This chapter provides basic information for writing a Pro\*FORTRAN program:

**Note:**

The Pro\*Fortran Precompiler is NOT supported in 64 bit Oracle Database installations.

The Pro\*Fortran Precompiler is only supported and available in Oracle Database 32 bit Client installations.

This chapter contains the following topics:

- Programming Guidelines

- Required Declarations and SQL Statements

- Host Variable Names

- Scope of Host Variables

- Host Variables

- About Referencing Host Variables

- Indicator Variables

- Host Arrays

- VARCHAR Host Variables

- About Handling Character Data

- The Oracle Datatypes

- Datatype Conversion

- Datatype Equivalencing

- Embedding PL/SQL

- About Declaring a Cursor Variable

- Connecting to Oracle

### 1.1 Programming Guidelines

This section deals with embedded SQL syntax, coding conventions, and FORTRAN-specific features and restrictions. Topics are arranged alphabetically.

#### 1.1.1 32 bit vs 64 bit

The Pro\*Fortran Precompiler is NOT supported in 64 bit Oracle environments.

The Pro\*Fortran Precompiler is only supported and available in Oracle Database 32 bit Client installations.

#### 1.1.2 Case-sensitivity

Though the standard FORTRAN character set excludes lowercase alpha characters, many compilers allow them in identifiers, comments, and quoted literals.

The Pro\*FORTRAN Precompiler is not case-sensitive; however, some compilers are. If your compiler is case-sensitive, you must declare and reference variables in the same uppercase/lowercase format. Check your FORTRAN compiler user's guide.

You must code EXEC SQL and EXEC ORACLE statements in columns 7 through 72 (columns 73 through 80 are ignored). The other columns are used for the following purposes:

- Column 1 can indicate a comment line or can be part of an optional statement label.

- Columns 2 through 5 can contain an optional statement label.

- Column 6 indicates continuation lines.

On some systems, terminal format is supported; that is, entry is not restricted to certain columns. In this manual, the program fragments and sample programs are in ANSI format (FORMAT=ANSI).

No more than one statement can appear on a single line.

#### 1.1.3 Comments

You can place FORTRAN comment lines within SQL statements. FORTRAN comment lines start with the letter C or an asterisk (\*) in column 1. You can place ANSI SQL-style comments (- - ...) in SQL statements at the end of a line, and you can also place C-style comments (/\* ... \*/) in SQL statements.

The following example shows all three styles of comments:

    EXEC SQL SELECT ENAME, SAL
    C Assign column values to host variables.
     1 INTO :ENAM, :ESAL -- output host variables
     2 FROM EMP
     3 /* Use input host variable in
     4 search condition */
     5 WHERE DEPTNO = :DNUM

**Note:**

You cannot nest comments. Blank lines are treated as comments, but are not allowed within a continued statement.

#### 1.1.4 Continuation Lines

You can continue SQL statements from one line to the next, according to the rules of FORTRAN. To code a continuation line, place a nonzero, non-blank character in column 6. In this manual, digits are used as continuation characters, as the following example shows:

    * Retrieve employee data.
     EXEC SQL SELECT EMPNO, ENAME, JOB, SAL
     1 INTO :ENUM, :ENAM, :EJOB, :ESAL
     2 FROM EMP
     3 WHERE DEPTNO = :DNUM

To continue a string literal from one line to the next, code the literal through column 72. On the next line, code a continuation character and the rest of the literal. An example follows:

    * Execute dynamic SQL statement.
     EXEC SQL EXECUTE IMMEDIATE 'UPDATE EMP SET COMM = 500 WHERE
     1 DEPTNO=20'

Most FORTRAN implementations allow up to 19 continuation lines. Check your FORTRAN compiler user's guide.

#### 1.1.5 Delimiters

Though FORTRAN does not require blanks to delimit keywords, you must use blanks to delimit keywords in SQL statements. FORTRAN uses apostrophes to delimit string literals, as in

    * Display employee name.
     IF (ENAM .LT. 'ZZZZZ') THEN
     PRINT *, ' Employee Name: ', ENAM
     END IF

SQL also uses apostrophes to delimit string literals, as in

    * Retrieve employee data.
     EXEC SQL SELECT ENAME, SAL
     1 INTO :ENAM, :ESAL
     2 FROM EMP
     3 WHERE JOB = 'CLERK'

SQL also uses quotation marks to delimit identifiers containing special or lowercase characters.

#### 1.1.6 Embedded SQL Syntax

To use a SQL statement in your host program, precede the SQL statement with the EXEC SQL clause. Embedded SQL syntax is described in the [Pro\*C/C++ Programmer's Guide](../lnpcc/introduction.md). The precompiler translates all EXEC SQL statements into calls to the runtime library SQLLIB.

#### 1.1.7 File Length

The Pro\*FORTRAN Precompiler cannot process arbitrarily long source files. Some of the variables used internally limit the size of the generated file. There is no absolute limit to the number of lines allowed, but the following aspects of the source files are contributing factors to the file-size constraint:

- complexity of the embedded SQL statements (for example, the number of bind and define variables)

- whether a database name is used (for example, connecting to a database with an AT clause)

- number of embedded SQL statements

To prevent problems related to this limitation, use multiple program units to reduce the size of the source files as required.

#### 1.1.8 File Naming Restrictions

Avoid using filenames starting with "sql," because errors might occur. For example, if you name a file SQLERROR.PFO, some linkers return name conflicts because there will be an array named SQLERD and a common block named SQLERD.

#### 1.1.9 FORTRAN Versions

The Pro\*FORTRAN Precompiler supports the standard implementation of FORTRAN for your operating system (usually FORTRAN 77). For more information, see your Oracle system-specific documentation.

### 1.2 Required Declarations and SQL Statements

Passing data between Oracle and your application program requires host variables and event handling. This section shows you how to meet these requirements.

#### 1.2.1 The Declare Section

You must declare all program variables to be used in SQL statements in the Declare Section, which begins with the statement

    EXEC SQL BEGIN DECLARE SECTION

and ends with the statement

    EXEC SQL END DECLARE SECTION

Between these two statements only the following are allowed:

- host variable and indicator variable declarations

- EXEC SQL DECLARE statements

- EXEC SQL INCLUDE statements

- EXEC SQL VAR statements

- EXEC ORACLE statements

- FORTRAN comments

In a Pro\*FORTRAN source file, multiple program units can contain SQL statements. So, multiple Declare Sections are allowed for each precompiled unit. Furthermore, a Pro\*FORTRAN program can contain multiple files.

#### 1.2.2 Using the INCLUDE Statement

FORTRAN INCLUDEs are processed by the FORTRAN compiler, while EXEC SQL INCLUDE statements are processed by Pro\*FORTRAN to copy files into your host program, as illustrated in the following example:

    * Copy in the SQL Communications Area (SQLCA)
    * and the Oracle Communications Area (ORACA).
     EXEC SQL INCLUDE SQLCA
     EXEC SQL INCLUDE ORACA

You can INCLUDE any file. When you precompile a Pro\*FORTRAN program, each EXEC SQL INCLUDE statement is replaced by a copy of the file named in the statement.

#### 1.2.3 Filename Extensions

If your system uses file extensions but you do not specify one, the Pro\*FORTRAN Precompiler assumes the default extension for source files (usually FOR or F). The default extension is system dependent. For more information, see your Oracle system-specific documentation.

#### 1.2.4 Search Paths

If your system uses directories, you can set a search path for INCLUDE files using the INCLUDE precompiler option, as follows:

    INCLUDE=path

where path defaults to the current directory.

The precompiler first searches the current directory, then the directory specified by the INCLUDE option, and finally the directory for standard INCLUDE files. You need not specify a path for standard files such as the SQLCA and ORACA. However, a path is required for nonstandard files unless they are stored in the current directory.

You can also specify multiple paths on the command line, as follows:

    ... INCLUDE=<path1> INCLUDE=<path2> ...

When multiple paths are specified, the precompiler searches the current directory first, then the path1 directory, then the path2 directory, and so on. The directory containing standard INCLUDE files is searched last. The path syntax is system specific. Check the Oracle installation or user's guide for your system.

#### 1.2.5 Caution

Remember, the precompiler searches for a file in the current directory first even if you specify a search path. If the file you want to INCLUDE is in another directory, make sure no file with the same name is in the current directory or any other directory that precedes it in the search path. Also, if your operating system is case-sensitive, you must specify the same upper or lower case filename under which the file is stored.

#### 1.2.6 Event and Error Handling

Pro\*FORTRAN provides forward and backward compatibility when checking the outcome of executing SQL statements. However, there are restrictions on using SQLCA, SQLCODE, and SQLSTATE depending on the MODE and DBMS option settings. For more information, see [Error Handling and Diagnostics](../zzpre/error-handling-diagnostics.md).

### 1.3 Host Variable Names

Host variable names must consist only of letters and digits, and must begin with a letter. They can be of any length, but only the first 31 characters are significant. Some compilers prohibit variable names longer than six characters, or ignore characters after the sixth. Check your FORTRAN compiler user's guide.

#### 1.3.1 Logical and Relational Operators

Logical and relational operators are different for FORTRAN and SQL, as shown in the following tables, respectively. For example, the SQL operators do not have leading and trailing periods, as shown in table 1-1 and table 1-2.

Table 1-1 Logical Operators

| SQL Operators | FORTRAN Operators |
|:--------------|:------------------|
| NOT           | .NOT.             |
| AND           | .AND.             |
| OR            | .OR.              |
| --            | .EQV.             |
| --            | .NEQV.            |

Table 1-2 Relational Operator

| SQL Operators | FORTRAN operators |
|:--------------|:------------------|
| =             | .EQ.              |
| \<\>, !=, ^=  | .NE.              |
| \>            | .GT.              |
| \<            | .LT.              |
| \>=           | .GE.              |
| \<=           | .LE.              |

Logical and relational FORTRAN operators are not allowed in SQL statements.

#### 1.3.2 MAXLITERAL Default

With the MAXLITERAL precompiler option, you can specify the maximum length of string literals generated by the precompiler, so that compiler limits are not exceeded. For Pro\*FORTRAN, the default value is 1000, but you might need to specify a lower value.

For example, if your FORTRAN compiler cannot handle string literals longer than 512 characters, specify MAXLITERAL=512. Check your FORTRAN compiler user's guide.

#### 1.3.3 Nulls

In SQL, a null represents a missing, unknown, or inapplicable column value; it equates neither to zero nor to a blank. Use the NVL function to convert nulls to non-null values, use the IS \[NOT\] NULL comparison operator to search for nulls, and use indicator variables to insert and test for nulls.

#### 1.3.4 Program Units

In FORTRAN, a program unit is a function, subroutine, or main program. In Pro\*FORTRAN, an input file contains one or more program units.

If a program unit contains SQL statements, it must

- define all local host variables in its Declare Section

- INCLUDE the SQLCA when MODE={ORACLE\|ANSI13}

- declare a variable named SQLATA or SQLCOD inside or outside the Declare Section when MODE={ANSI\|ANSI14}

- INCLUDE the ORACA if you specify ORACA=YES

Multiple program units can contain SQL statements. For example, you can DECLARE a cursor in one program unit, OPEN it in another, FETCH from it in yet another, and CLOSE it in still another as long as they are in the same file.

### 1.4 Scope of Host Variables

The scoping rules for FORTRAN identifiers apply to host variables. Host variables declared in a program unit are local to that unit, and host variables declared in the main program are not global. So, all host variables used in a program unit must be declared in that unit in the Declare Section.

#### 1.4.1 Statement Labels

You can associate FORTRAN numeric statement labels (1 - 99999) with SQL statements, as shown in the following example:

    * Insert row into employee table.
     500 EXEC SQL INSERT INTO EMP (EMPNO, ENAME, JOB, DEPTNO)
     1 VALUES (:ENUM, :ENAM, :EJOB, :DNUM)

And, you can reference statement labels in a WHENEVER DO or WHENEVER GOTO statement, as this example shows:

    * Handle SQL execution errors.
     EXEC SQL WHENEVER SQLERROR GOTO 900
     ...
    * SQLEMC stores the Oracle error code and message.
     900 WRITE (*, 8500) SQLEMC
     8500 FORMAT (1X, 70A1)
     ...

Statement labels must be coded in columns 1 through 5, and must not appear in continuation lines. Statement labels may consist of alphanumeric characters, only; the special characters, underscore ( \_ ), hyphen (-), and dollar sign (\$) are not allowed.

The Pro\*FORTRAN Precompiler does not use statement labels in generated code. Therefore, the BEGLABEL and ENDLABEL options that were available in earlier Pro\*FORTRAN versions are not supported in this version and will return an informational message if found.

#### 1.4.2 Statement Terminator

Embedded SQL statements are terminated by an end-of-line, as the following example shows:

    * Delete employee.
     EXEC SQL DELETE FROM EMP WHERE EMPNO = :ENUM

However, a continuation character on the next line overrides an end-of-line.

### 1.5 Host Variables

Host variables are the key to communication between your host program and Oracle. Typically, a host program inputs data to Oracle, and Oracle outputs data to the program. Oracle stores input data in database columns and stores output data in program host variables.

#### 1.5.1 Declaring Host Variables

Host variables are declared according to FORTRAN rules, using the FORTRAN datatypes that are supported by Oracle. FORTRAN datatypes must be compatible with the source/target database column. The supported FORTRAN datatypes are shown in the following table. One-dimensional arrays of FORTRAN types are also supported.

| Variable Declaration                                     | Description                                                      |
|:---------------------------------------------------------|:-----------------------------------------------------------------|
| BYTE var CHARACTER var                                   | single character                                                 |
| CHARACTER var\*n CHARACTER\*n var                        | n-byte character string                                          |
| CHARACTER(\*) var                                        | character string                                                 |
| INTEGER var INTEGER\*2 var INTEGER\*4 var                | default-length integer 2-byte integer 4-byte integer             |
| LOGICAL var LOGICAL\*1 var LOGICAL\*2 var LOGICAL\*4 var | single character 2-byte character string 4-byte character string |
| REAL var REAL\*4 var REAL\*8 var DOUBLE PRECISION var    | 4-byte real number 8-byte real number                            |
| VARCHAR\*n                                               | \<= 32765-byte, variable length character string (3)             |
| SQLCURSOR                                                | cursor variable                                                  |

Notes:

1.  The size of FORTRAN numeric types is implementation-dependent. The sizes given in the table are typical but not universal. Check your FORTRAN compiler user's guide.

2.  CHARACTER(\*) variables have no predetermined length. They are used to specify dummy arguments in a subroutine declaration. The maximum length of an actual argument is returned by the LEN intrinsic function.

3.  Variables declared with VARCHAR\*n (not native to FORTRAN) are assigned the VARCHAR external datatype. See "Declaring VARCHAR Variables" for more information.

The following table lists the compatible Oracle internal datatypes.

| Internal Type                                      | FORTRAN Type                                                                                                                                                                                           | Description                                                                                                                                                                                                                                                                       |
|:---------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CHAR(x) (1)VARCHAR2(y) (1)                         | BYTE CHARACTER CHARACTER\*n VARCHAR\*n var1, var2, var3                                                                                                                                                | single character variable-length string variable-length string variable-length string                                                                                                                                                                                             |
| NUMBER NUMBER (p,s) (2)                            | CHARACTER\*nvar CHARACTER var \*n CHARACTER(\*) DOUBLE PRECISION INTEGER INTEGER\*2 INTEGER\*4 LOGICAL var LOGICAL\*1 var LOGICAL\*2 var LOGICAL\*4 varREAL REAL\*4 REAL\*8 VARCHAR\*nvar1, var2, var3 | n-byte character string (3) character string (as parameter) 8-byte float number integer (default size) 2-byte integer 4-byte integer single character 2-byte character string 4-byte character string float number 4-byte float number 8-byte float number variable-length string |
| DATE (4)LONG RAW (1)LONG RAW ROWID (5)MLSLABEL (6) | CHARACTER\*n var CHARACTER\*n var VARCHAR\*n var1, var2, var3                                                                                                                                          | n-byte character string n-byte variable-length string variable-length string                                                                                                                                                                                                      |
| CURSOR                                             | SQLCURSOR                                                                                                                                                                                              | cursor variable                                                                                                                                                                                                                                                                   |

Notes:

1.  x ranges from 1 to 255, and 1 is the default. y ranges from 1 to 2000.

2.  p ranges from 2 to 38. s ranges from -84 to 127.

3.  Strings can be converted to NUMBERs only if they consist of convertible characters -- 0 to 9, period (.), +, -, E, e. The NLS settings for your system might change the decimal point from a period (.) to a comma (,).

4.  When converted to a string type, the default size of a DATE depends on the NLS settings in effect on your system. When converted to a binary value, the length is 7 bytes.

5.  When converted to a string type, a ROWID requires from 18 to 256 bytes.

#### 1.5.2 Example Declarations

In the following example, several host variables are declared to be used later in a Pro\*FORTRAN program:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM
     CHARACTER*10 ENAM
     REAL*4 ESAL
     INTEGER*2 DNUM
     CHARACTER*15 DNAM
     EXEC SQL END DECLARE SECTION

You can also declare one-dimensional arrays of FORTRAN types, as the next example shows:

    * Declare host arrays.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM(100)
     CHARACTER*10 ENAM(100)
     REAL*4 ESAL(100)
     EXEC SQL END DECLARE SECTION

#### 1.5.3 Repeating Definitions

You can use repeating definitions for datatypes, as in the following example:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     ...
     REAL*4 ESAL, ECOM, EBON
     EXEC SQL END DECLARE SECTION

which is equivalent to

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     ...
     REAL*4 ESAL
     REAL*4 ECOM
     REAL*4 EBON
     EXEC SQL END DECLARE SECTION

#### 1.5.4 Initialization

While it is not necessary to initialize host variables inside the Declare Section, you can use the FORTRAN DATA statement to initialize host variables, as shown in the following example:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     ...
     REAL*4 MINSAL
     REAL*4 MAXSAL
     DATA MINSAL, MAXSAL /1000.00, 5000.00/
     EXEC SQL END DECLARE SECTION

DATA statements must come before the first executable FORTRAN statement but after any variable and PARAMETER declarations. Later in your program, you can change the values of variables initialized by a DATA statement. You cannot, however, reuse a DATA statement to reset the changed values.

#### 1.5.5 Constants

You can use the FORTRAN PARAMETER statement inside or outside the Declare Section to assign constant values to host variables, as the following example shows:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     CHARACTER*5 UID
     CHARACTER*5 PWD
     PARAMETER (UID = 'AAAAA', PWD = 'BBBBB')
     EXEC SQL END DECLARE SECTION

#### 1.5.6 COMMON Blocks

Using the FORTRAN COMMON statement, you can keep host variables and arrays in a common storage area as if they were globally defined, so that you can use their values in different program units. The COMMON statement must appear outside the Declare Section, and before the first executable FORTRAN statement but after variable declarations. An example follows:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM
     CHARACTER*10 ENAM
     REAL*4 ESAL
     REAL*4 ECOM
     EXEC SQL END DECLARE SECTION
    * Define COMMON block.
     COMMON /EMPBLK/ ENUM, ESAL, ECOM

In this example, EMPBLK is the COMMON block name. The names of COMMON blocks, subroutines, and functions are the only globally defined identifiers in a FORTRAN program. You should avoid using blank COMMON blocks.

You can make a COMMON block available to other program units by redefining it in those units. You must repeat the type declarations for variables in a COMMON block in all units where the block is used.

Only the order and datatypes of variables in the COMMON block matter, not their names. Therefore, the variable names can differ from unit to unit. However, it is good programming practice to use the same names for corresponding variables in each occurrence of a COMMON block.

The following restrictions apply to COMMON blocks:

- You cannot put VARCHAR variables in a COMMON block.

- Host arrays cannot be dimensioned in a COMMON statement.

- You cannot use a DATA statement to initialize variables in a blank COMMON block.

- With most compilers, CHARACTER variables must appear in their own COMMON blocks; that is, they cannot be mixed with other variables in a COMMON block.

#### 1.5.7 EQUIVALENCE Statement

With the FORTRAN EQUIVALENCE statement, you can use two or more host variable names for the same storage location. The EQUIVALENCE statement must appear before the first executable FORTRAN statement.

You can equivalence CHARACTER variables only to other CHARACTER variables. You cannot equivalence VARCHAR variables.

#### 1.5.8 Special Requirements for Subroutines

You must explicitly declare host variables in the Declare Section of the program unit that uses them in SQL statements. Thus, variables passed to a subroutine and used in SQL statements within the subroutine must be declared in the subroutine Declare Section, as illustrated in the following example:

    ...
     CALL LOGON (UID, PWD)
     ...
     SUBROUTINE LOGON (UID, PWD)
    * Declare host variables in subroutine.
     EXEC SQL BEGIN DECLARE SECTION
     CHARACTER*10 UID
     CHARACTER*10 PWD
     EXEC SQL END DECLARE SECTION
     ...
     EXEC SQL CONNECT :UID IDENTIFIED BY :PWD
     WRITE(*, 1000) UID
     1000 FORMAT(/,' Connected to Oracle as user: ', A10, /)
     RETURN
     END

#### 1.5.9 Restrictions

The following restrictions apply with respect to Declarations:

##### Implicit Declarations

FORTRAN allows implicit declaration of INTEGER and REAL variables. Unless explicitly declared otherwise, identifiers starting with I, J, K, L, M, or N are assumed to be of type INTEGER, and other identifiers are assumed to be of type REAL.

However, implicit declaration of host variables is not allowed; it triggers an "undeclared host variable" error message at precompile time. Every variable referenced in a SQL statement must be defined in the Declare Section.

##### Complex Numbers

These are numbers including a real and an imaginary part. In FORTRAN, complex numbers are represented using the datatype COMPLEX. Pro\*FORTRAN, however, does not support the use of COMPLEX host variables in SQL statements.

### 1.6 About Referencing Host Variables

You use host variables in SQL data manipulation statements. A host variable must be prefixed with a colon (:) in SQL statements but must not be prefixed with a colon in FORTRAN statements, as shown in the following example:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM
     CHARACTER*10 ENAM
     REAL*4 ESAL
     CHARACTER*10 EJOB
     EXEC SQL END DECLARE SECTION
     ...
     WRITE (*, 3100)
     3100 FORMAT (' Enter employee number: ')
     READ (*, 3200) ENUM
     3200 FORMAT (I4)
     EXEC SQL SELECT ENAME, SAL, JOB
     1 INTO :ENAM, :ESAL, :EJOB
     2 FROM EMP
     3 WHERE EMPNO = :ENUM
     BONUS = ESAL / 10
     ...

Though it might be confusing, you can provide the same name to a host variable as that of an Oracle table or column, as the following example shows:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM
     CHARACTER*10 ENAM
     REAL*4 ESAL
     EXEC SQL END DECLARE SECTION
     ...
     EXEC SQL SELECT ENAME, SAL
     1 INTO :ENAM, :ESAL
     2 FROM EMP
     3 WHERE EMPNO = :ENUM

#### 1.6.1 Restrictions

A host variable cannot substitute for a column, table, or other Oracle objects in a SQL statement and must not be an Oracle reserved word. See [Oracle Reserved Words, Keywords, and Namespaces](../zzpre/Oracle-reserved-words-keywords-namespaces.md) for a list of Oracle reserved words and keywords.

### 1.7 Indicator Variables

You use indicator variables to provide information to Oracle about the status of a host variable, or to monitor the status of data returned from Oracle. An indicator variable is always associated with a host variable.

You use indicator variables in the VALUES or SET clauses to assign nulls to input host variables and in the INTO clause to detect nulls or truncated values in output host variables.

#### 1.7.1 Declaring Indicator Variables

An indicator variable must be explicitly declared in the Declare Section as a 2-byte integer (INTEGER\*2) and must not be an Oracle reserved word. In the following example, you declare two indicator variables (the names IESAL and IECOM are arbitrary):

    * Declare host and indicator variables.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM
     CHARACTER*10 ENAM
     REAL*4 ESAL
     REAL*4 ECOM
     INTEGER*2 IESAL
     INTEGER*2 IECOM
     EXEC SQL END DECLARE SECTION

You can define an indicator variable anywhere in the Declare Section. It need not follow its associated host variable.

#### 1.7.2 About Referencing Indicator Variables

In SQL statements, an indicator variable must be prefixed with a colon and appended to its associated host variable. In FORTRAN statements, an indicator variable must not be prefixed with a colon or appended to its associated host variable. An example follows:

    * Retrieve employee data.
     EXEC SQL SELECT SAL, COMM
     1 INTO :ESAL, :ECOM:IECOM
     2 FROM EMP
     3 WHERE EMPNO = :ENUM
    * When an indicator variable equals -1, its associated
    * host variable is null.
     IF (IECOM .EQ. -1) THEN
     PAY = ESAL
     ELSE
     PAY = ESAL + ECOM
     END IF

To improve readability, you can precede any indicator variable with the optional keyword INDICATOR. You must still prefix the indicator variable with a colon. The correct syntax is

    :<host_variable> INDICATOR :<indicator_variable>

, which is equivalent to

    :<host_variable>:<indicator_variable>

You can use both forms of the expression in your host program.

#### 1.7.3 Restrictions

Indicator variables cannot be used in the WHERE clause to search for nulls. For example, the following DELETE statement triggers an Oracle error at run time:

    * Set indicator variable.
     IECOM = -1
     EXEC SQL DELETE FROM EMP WHERE COMM = :ECOM:IECOM

The correct syntax follows:

    EXEC SQL DELETE FROM EMP WHERE COMM IS NULL

#### 1.7.4 Oracle Restrictions

When DBMS=V6, Oracle does not issue an error if you SELECT or FETCH a null into a host variable not associated with an indicator variable. However, when DBMS=V7, if you SELECT or FETCH a null into a host variable that has no indicator, Oracle issues the following error message:

    ORA-01405: fetched column value is NULL

When precompiling with MODE=ORACLE and DBMS=V7, you can disable the ORA-01405 message by also specifying UNSAFE_NULL=YES on the command line. For more information, see [UNSAFE_NULL](../zzpre/running-Oracle-precompilers.md).

#### 1.7.5 ANSI Requirements

When MODE=ORACLE, if you SELECT or FETCH a truncated column value into a host variable not associated with an indicator variable, Oracle issues the following error message:

    ORA-01406: fetched column value was truncated

However, when MODE={ANSI\|ANSI14\|ANSI13}, no error is generated. Values for indicator variables are discussed in [Meeting Program Requirements](../zzpre/meeting-program-requirements.md).

### 1.8 Host Arrays

Host arrays can boost performance by letting you manipulate an entire collection of data items with a single SQL statement. With few exceptions, you can use host arrays wherever scalar host variables are allowed. And, you can associate an indicator array with any host array.

#### 1.8.1 About Declaring Host Arrays

You declare and dimension host arrays in the Declare Section. In the following example, three host arrays are declared, each with an upper dimension bound of 50 (the lower bound defaults to 1):

    * Declare and dimension host arrays.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM(50)
     CHARACTER*10 ENAM(50)
     REAL*4 ESAL(50)
     EXEC SQL END DECLARE SECTION

#### 1.8.2 Restrictions

You cannot specify a lower dimension bound for host arrays. For example, the following declaration is invalid:

    * Invalid dimensioning of host array
     EXEC SQL BEGIN DECLARE SECTION
     ...
     REAL*4 VECTOR(0:10)
     EXEC SQL END DECLARE SECTION

Multi-dimensional host arrays are not allowed. Therefore, the two-dimensional host array declared in the following example is invalid:

    * Invalid declaration of host array
     EXEC SQL BEGIN DECLARE SECTION
     ...
     REAL*4 MATRIX(50, 100)
     EXEC SQL END DECLARE SECTION

You cannot dimension host arrays using the FORTRAN DIMENSION statement. For example, the following usage is invalid:

    * Invalid use of DIMENSION statement
     EXEC SQL BEGIN DECLARE SECTION
     REAL*4 ESAL
     REAL*4 ECOM
     DIMENSION ESAL(50), ECOM(50)
     EXEC SQL END DECLARE SECTION

Also, you cannot dimension a host array in a COMMON statement.

#### 1.8.3 About Referencing Host Arrays

If you use multiple host arrays in a single SQL statement, their dimensions should be the same. However, this is not a requirement because the Pro\*FORTRAN Precompiler always uses the smallest dimension for the SQL operation. In the following example, only 50 rows are INSERTed:

    * Declare host arrays.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM(100)
     CHARACTER*10 ENAM(100)
     INTEGER*4 DNUM(100)
     REAL*4 ECOM(50)
     EXEC SQL END DECLARE SECTION
     ...
    * Populate host arrays here.
     ...
     EXEC SQL INSERT INTO EMP (EMPNO, ENAME, COMM, DEPTNO)
     1 VALUES (:ENUM, :ENAM, :ECOM, :DNUM)

Host arrays must not be subscripted in SQL statements. For example, the following INSERT statement is invalid:

    * Declare host arrays.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM(50)
     REAL*4 ESAL(50)
     INTEGER*4 DNUM(50)
     EXEC SQL END DECLARE SECTION
     ...
     DO 200 J = 1, 50
    * Invalid use of host arrays
     EXEC SQL INSERT INTO EMP (EMPNO, SAL, DEPTNO)
     1 VALUES (:ENUM(J), :ESAL(J), :DNUM(J))
     200 CONTINUE

You need not process host arrays in a loop. Instead, use unsubscripted array names in your SQL statement. Oracle treats a SQL statement containing host arrays of dimension n like the same statement executed n times with n different scalar variables. For more information, see [Using Host Arrays](../zzpre/using-host-arrays.md).

#### 1.8.4 About Using Indicator Arrays

You can use indicator arrays to assign nulls to input host arrays and to detect nulls or truncated values in output host arrays. The following example shows how to INSERT with indicator arrays:

    * Declare host and indicator arrays.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM(50)
     INTEGER*4 DNUM(50)
     REAL*4 ECOM(50)
     INTEGER*2 IECOM(50) -- indicator array
     EXEC SQL END DECLARE SECTION
     ...
    * Populate the host and indicator arrays. To insert
    * a null into the COMM column, assign -1 to the
    * appropriate element in the indicator array.
     ...
     EXEC SQL INSERT INTO EMP (EMPNO, DEPTNO, COMM)
     1 VALUES (:ENUM, :DNUM, :ECOM:IECOM)

The dimension of the indicator array must be greater than, or equal to, the dimension of the host array.

### 1.9 VARCHAR Host Variables

FORTRAN string datatypes are of fixed length. However, Pro\*FORTRAN lets you declare a variable-length string pseudotype called VARCHAR.

#### 1.9.1 About Declaring VARCHAR Variables

A VARCHAR is a set of three variables declared using the syntax

    * Declare a VARCHAR.
     EXEC SQL BEGIN DECLARE SECTION
     VARCHAR*<n> <VARNAM>, <VARLEN>, <VARARR>
     EXEC SQL END DECLARE SECTION

where:

    n

Is the maximum length of the VARCHAR; n must be in the range 1 through 32765.

    VARNAM

Is the name used to reference the VARCHAR in SQL statements; it is called an aggregate name because it identifies a set of variables.

    VARLEN

Is a 2-byte signed integer variable that stores the actual length of the string variable.

    VARARR

Is the string variable used in FORTRAN statements.

The advantage of using VARCHAR variables is that you can explicitly set and reference VARLEN. With input host variables, Oracle reads the value of VARLEN and uses the same number of characters of VARARR. With output host variables, Oracle sets VARLEN to the length of the character string stored in VARARR.

You can declare a VARCHAR only in the Declare Section. In the following example, you declare a VARCHAR named EJOB with a maximum length of 15 characters:

    * Declare a VARCHAR.
     EXEC SQL BEGIN DECLARE SECTION
     ...
     VARCHAR*15 EJOB, EJOBL, EJOBA
     EXEC SQL END DECLARE SECTION

The precompiler expands this declaration to

    * Expanded VARCHAR declaration
     INTEGER*2 EJOBL
     LOGICAL*1 EJOBA(15)
     INTEGER*2 SQXXX(2)
     EQUIVALENCE (SQXXX(1), EJOBL), (SQXXX(2), EJOBA(1))

where SQXXX is an array generated by the precompiler and XXX denotes three arbitrary characters. Notice that the aggregate name EJOB is not declared. The EQUIVALENCE statement forces the compiler to store EJOBL and EJOBA contiguously.

#### 1.9.2 About Referencing VARCHAR Variables

In SQL statements, you can reference a VARCHAR variable by using the aggregate name prefixed with a colon, as the following example shows:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     ...
     INTEGER*4 ENUM
     VARCHAR*15 EJOB, EJOBL, EJOBA
     EXEC SQL END DECLARE SECTION
     ...
     EXEC SQL SELECT JOB
     1 INTO :EJOB
     2 FROM EMP
     3 WHERE EMPNO = :ENUM

After the query executes, EJOBL holds the actual length of the character string retrieved from the database and stored in EJOBA. In FORTRAN statements, you reference VARCHAR variables using the length variable and string variable names, as this example shows:

    * Display job title.
     WRITE (*, 5200) (EJOBA(J), J = 1, EJOBL)
     5200 FORMAT (15A1)
     ...

#### 1.9.3 About Overcoming the Length Limit

Recall that the length variable of a VARCHAR must be a 2-byte integer. FORTRAN provides a 2-byte signed integer datatype, which can represent numbers in the range -32768 through 32767. However, FORTRAN lacks a 2-byte unsigned integer datatype, which can represent numbers in the range 0 through 65535. Therefore, the maximum length of a VARCHAR character string is 32765 bytes (32767 minus 2 for the length variable).

With other host languages, the maximum length of a VARCHAR character string is 65533 bytes. If you want to use 65533-byte VARCHAR variables, try the technique shown in the following example:

    * Declare a VARCHAR.
     EXEC SQL BEGIN DECLARE SECTION
     ...
     VARCHAR*65533 BUF, BUFL, BUFA
     EXEC SQL END DECLARE SECTION
     ...
    * Equivalence two 2-byte integers to one 4-byte integer.
     INTEGER*2 INT2(2)
     INTEGER*4 INT4
     EQUIVALENCE (INT2(1), INT4)
     INTEGER*4 I
     ...
     INT4 = 65533
    * Set the VARCHAR length variable equal to the
    * equivalenced value of INT4.
     BUFL = INT2(1)
     DO 100 I = 1, 65533
     BUFA(I) = 32
     100 CONTINUE
     EXEC SQL INSERT INTO LONG_TABLE VALUES (:BUF)
     ...
     BUFL = 0
     EXEC SQL SELECT COL1 INTO :BUF FROM LONG_TABLE
     INT2(1) = BUFL
     ...

**Note:**

The way integers are stored varies from system to system. On some systems, the least significant digits are stored at the low address; on other systems they are stored at the high address. In the last example, this determines whether the length is stored in INT2(1) or INT2(2).

### 1.10 About Handling Character Data

This section explains how the Pro\*FORTRAN Precompiler handles character host variables. There are two types of character host variables:

- CHARACTER\*n

- VARCHAR

Do not confuse VARCHAR, which is a host variable data structure supplied by the precompiler, with VARCHAR2, which is an Oracle column datatype for variable-length character strings.

#### 1.10.1 Effects of the MODE Option

The MODE option has the following effects:

- It determines how the Pro\*FORTRAN Precompiler treats data in character arrays and strings. The MODE option allows the program to use ANSI fixed-length strings or to maintain compatibility with previous versions of the Oracle Server and the Pro\*FORTRAN Precompiler.

- With respect to character handling, MODE={ANSI14\|ANSI13} is equivalent to MODE=ORACLE. The MODE option affects character data on input (from host variables to Oracle) and on output (from Oracle to host variables).

**Note:**

The MODE option does not affect the way Pro\*FORTRAN handles VARCHAR host variables.

#### 1.10.2 CHARACTER\*n

Character variables are declared using the CHARACTER\*n datatype. These types of variables handle character data based on their roles as input or output variables.

#### 1.10.3 On Input

When MODE=ORACLE, the program interface strips trailing blanks before sending the value to the database. If you insert into a fixed-length CHAR column, Oracle re-appends trailing blanks up to the length of the database column. However, if you insert into a variable-length VARCHAR2 column, Oracle never appends blanks.

When MODE=ANSI, trailing blanks are never stripped.

Make sure that the input value is not trailed by extraneous characters. For example, nulls are not stripped and are inserted into the database. Normally, this is not a problem because when a value is READ into or assigned to a CHARACTER\*n variable, FORTRAN appends blanks up to the length of the variable.

The following example illustrates the point:

    * Declare host variables
     EXEC SQL BEGIN DECLARE SECTION
     CHARACTER ENAM *10, EJOB *8
     ...
     EXEC SQL END DECLARE SECTION
     ...
     WRITE (*, 300)
     300 FORMAT (/, '$Employee name? ')
    * Assume the name 'MILLER' is entered
     READ (*, 400)
     400 FORMAT (A10)
     EJOB = 'SALES'
     EXEC SQL INSERT INTO emp (empno, ename, deptno, job)
     VALUES (1234, :ENAM, 20, :EJOB)

If you precompile the last example with MODE=ORACLE and the target database columns are VARCHAR2, the program interface strips the trailing blanks on input and inserts just the 6-character string "MILLER" and the 5-character string "SALES" into the database. However, if the target database columns are CHAR, the strings are blank-padded to the width of the columns.

If you precompile the last example with MODE=ANSI and the JOB column is defined as CHAR(10), the value inserted into that column is "SALES#####" (five trailing blanks). However, if the JOB column is defined as VARCHAR2(10), the value inserted is "SALES###" (three trailing blanks) because the host variable is a CHARACTER\*8. This might not be what you want, so be careful.

#### 1.10.4 On Output

The MODE option has no effect on output to character variables. When you use a CHARACTER\*n variable as an output host variable, Oracle blank-pads it. In our example, when your program fetches the string "MILLER" from the database, ENAM contains the value "MILLER####" (with four trailing blanks). This character string can be used without change as input to another SQL statement.

#### 1.10.5 VARCHAR Variables

VARCHAR variables handle character data based on their roles as input or output variables

#### 1.10.6 On Input

When you use a VARCHAR variable as an input host variable, your program must assign values to the length and string variables, as shown in the following example:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM
     VARCHAR*15 EJOB, EJOBL, EJOBA
     INTEGER*2 IEJOB
     INTEGER*4 DNUM
     EXEC SQL END DECLARE SECTION
     ...
     WRITE (*, 4300)
     4300 FORMAT (/, ' Enter job title: ')
     READ (*, 4400) EJOBA
     4400 FORMAT (15A1)
    * Scan backward for last non-blank character, then
    * set length to that position. If input is all blank,
    * set indicator variable to -1 to indicate a null.
     DO 5000 J = 15, 1, -1
     IF (EJOBA(J) .NE. ' ') GOTO 5100
     5000 CONTINUE
     J = 0
     5100 IF (J .EQ. 0) THEN
     IEJOB = -1
     ELSE
     IEJOB = 0
     END IF
     EJOBL = J
     EXEC SQL INSERT INTO EMP (EMPNO, JOB, DEPTNO)
     1 VALUES (:ENUM, :EJOB:IEJOB, :DNUM)

#### 1.10.7 On Output

When you use a VARCHAR variable as an output host variable, Oracle sets the length variable. An example follows:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM
     VARCHAR*15 EJOB, EJOBL, EJOBA
     INTEGER*4 ESAL
     EXEC SQL END DECLARE SECTION
     ...
     EXEC SQL SELECT JOB, SAL INTO :EJOB, :ESAL FROM EMP
     1 WHERE EMPNO = :ENUM
     ...
     IF (EJOBL .EQ. 0) GOTO ...
     ...

An advantage of VARCHAR variables over fixed-length strings is that the length of the value returned by Oracle is available immediately. With fixed-length strings, to get the length of the value, your program must count the number of characters. (The intrinsic function LEN returns the length of a string including blanks, not its current length.)

### 1.11 The Oracle Datatypes

Oracle recognizes two kinds of datatypes: internal and external. Internal datatypes specify how Oracle stores data in database columns. Oracle also uses internal datatypes to represent database pseudocolumns. An external datatype specifies how data is stored in a host variable. For descriptions of the Oracle datatypes, see [Oracle Datatypes](../zzpre/meeting-program-requirements.md).

#### 1.11.1 Internal Datatypes

For values stored in database columns, Oracle uses the following internal datatypes:

| Name     | Code | Description                                      |
|:---------|:-----|:-------------------------------------------------|
| CHAR     | 96   | \<= 255-byte, fixed-length string                |
| DATE     | 12   | 7-byte, fixed-length date/time value             |
| LONG     | 8    | \<= 2147483647-byte, variable-length string      |
| LONG RAW | 24   | \<= 2147483647-byte, variable-length binary data |
| MLSLABEL | 105  | \<= 5-byte, variable-length binary label         |
| NUMBER   | 2    | fixed or floating point number                   |
| RAW      | 23   | \<= 255-byte, variable-length binary data        |
| ROWID    | 11   | fixed-length binary value                        |
| VARCHAR2 | 1    | \<= 2000-byte, variable-length string            |

Table 1 - 5. Internal Datatypes

These internal datatypes can be quite different from FORTRAN datatypes. For example, FORTRAN has no equivalent to the NUMBER datatype, which was specially designed for portability and high precision.

#### 1.11.2 External Datatypes

As the following table shows, the external datatypes include all the internal datatypes plus several datatypes found in other supported host languages. For example, the STRING external datatype refers to a C null-terminated string. You use the datatype names in datatype equivalencing, and you use the datatype codes in dynamic SQL Method 4.

| Name         | Code | Description                                                                                           |
|:-------------|:-----|:------------------------------------------------------------------------------------------------------|
| CHAR         | 1 96 | \<= 65535-byte, variable-length character string (1)\<= 65535-byte, fixed-length character string (1) |
| CHARF        | 96   | \<= 65535-byte, fixed-length character string                                                         |
| CHARZ        | 97   | \<= 65535-byte, fixed-length, null-terminated string (2)                                              |
| DATE         | 12   | 7-byte, fixed-length date/time value                                                                  |
| DECIMAL      | 7    | COBOL packed decimal                                                                                  |
| DISPLAY      | 91   | COBOL numeric character string                                                                        |
| FLOAT        | 4    | 4-byte or 8-byte floating-point number                                                                |
| INTEGER      | 3    | 2-byte or 4-byte signed integer                                                                       |
| LONG         | 8    | \<= 2147483647-byte, fixed-length string                                                              |
| LONG RAW     | 24   | \<= 217483647-byte, fixed-length binary data                                                          |
| LONG VARCHAR | 94   | \<= 217483643-byte, variable-length string                                                            |
| LONG VARRAW  | 95   | \<= 217483643-byte, variable-length binary data                                                       |
| MLSLABEL     | 106  | 2..5-byte, variable-length binary data                                                                |
| NUMBER       | 2    | integer or floating-point number                                                                      |
| RAW          | 23   | \<= 65535-byte, fixed-length binary data (2)                                                          |
| ROWID        | 11   | (typically) 13-byte, fixed-length binary value                                                        |
| STRING       | 5    | \<= 65535-byte, null-terminated character string (2)                                                  |
| UNSIGNED     | 68   | 2-byte or 4-byte unsigned integer                                                                     |
| VARCHAR      | 9    | \<= 65533-byte, variable-length character string                                                      |
| VARCHAR2     | 1    | \<= 65535-byte, variable-length character string (2)                                                  |
| VARNUM       | 6    | variable-length binary number                                                                         |
| VARRAW       | 15   | \<= 65533-byte, variable-length binary data                                                           |

Notes:

1.  CHAR is datatype 1 when MODE={ORACLE\|ANSI13\|ANSI14} and datatype 96 when MODE=ANSI.

2.  Maximum size is 32767 (32K) on some platforms.

### 1.12 Datatype Conversion

At precompile time, an external datatype is assigned to each host variable in the Declare Section. For example, the precompiler assigns the FLOAT external datatype to host variables of type REAL. At run time, the datatype code of every host variable used in a SQL statement is passed to Oracle. Oracle uses the codes to convert between internal and external datatypes.

Before assigning a SELECTed column value to an output host variable, Oracle must convert the internal datatype of the source column to the datatype of the host variable. Likewise, before assigning or comparing the value of an input host variable to a column, Oracle must convert the external datatype of the host variable to the internal datatype of the target column.

Conversions between internal and external datatypes follow the usual data conversion rules. For example, you can convert a CHAR value of "1234" to a INTEGER\*2 value. You cannot, however, convert a CHAR value of "65543" (number too large) or "10F" (number not decimal) to a INTEGER\*2 value. Likewise, you cannot convert a CHARACTER\*n value that contains alphabetic characters to a NUMBER value.

For more information about datatype conversion, see [Meeting Program Requirements](../zzpre/meeting-program-requirements.md).

### 1.13 Datatype Equivalencing

Datatype equivalencing lets you control the way Oracle interprets input data and the way Oracle formats output data. You can equivalence supported FORTRAN datatypes to Oracle external datatypes on a variable-by-variable basis.

#### 1.13.1 Host Variable Equivalencing

By default, the Pro\*FORTRAN Precompiler assigns a specific external datatype to every host variable. The default assignments are shown in the following table. For more information about datatype equivalencing, see [Datatype Equivalencing](../zzpre/learning-basics.md).

| Host Type                                                                                                                           | External Type  | Code                                      |
|:------------------------------------------------------------------------------------------------------------------------------------|:---------------|:------------------------------------------|
| BYTE var LOGICAL var LOGICAL\*1 var LOGICAL\*2 var LOGICAL\*4 var CHARACTER var CHARACTER var\*n CHARACTER\*n var CHARACTER(\*) var | VARCHAR2 CHARF | 1 (when MODE != ANSI) 96 (when MODE=ANSI) |
| VARCHAR\*n                                                                                                                          | VARCHAR        | 9                                         |
| INTEGER var INTEGER\*2 var INTEGER\*4 var                                                                                           | INTEGER        | 3                                         |
| REAL var REAL\*4 var REAL\*8 var DOUBLE PRECISION var                                                                               | FLOAT          | 4                                         |

With the VAR statement, you can override the default assignments by equivalencing host variables to Oracle external datatypes in the Declare Section. The syntax you use is

    EXEC SQL
     VAR <host_variable>
     IS <ext_type_name> [({<length> | <precision>,<scale>})]

where host_variable is an input or output host variable (or host array) declared earlier in the Declare Section, ext_type_name is the name of a valid external datatype, and length is an integer literal specifying a valid length in bytes.

When ext_type_name is FLOAT, use length; when ext_type_name is DECIMAL, you must specify precision and scale instead of length.

Host variable equivalencing is useful in several ways. For example, you can use it when you want Oracle to store but not interpret data. Suppose you want to store a host array of 4-byte integers in a RAW database column. Simply equivalence the host array to the RAW external datatype, as follows:

    EXEC SQL BEGIN DECLARE SECTION
     INTEGER*4 ENUM(50)
     ...
    * Reset default datatype (INTEGER) to RAW.
     EXEC SQL VAR ENUM IS RAW (200);
     EXEC SQL END DECLARE SECTION
     ...

With host arrays, the length you specify must match the buffer size required to hold the array. In the last example, you specified a length of 200, which is the buffer size required to hold 50 4-byte integers.

For more information about datatype equivalencing, see [Datatype Equivalencing](../zzpre/learning-basics.md).

### 1.14 Embedding PL/SQL

The Pro\*FORTRAN Precompiler treats a PL/SQL block like a single embedded SQL statement. As a result, you can place a PL/SQL block anywhere in a host program that you can place a SQL statement.

To embed a PL/SQL block in your host program, declare the variables to be shared with PL/SQL and bracket the PL/SQL block with the EXEC SQL EXECUTE and END-EXEC keywords.

#### 1.14.1 Host Variables

Inside a PL/SQL block, host variables are global to the entire block and can be used anywhere a PL/SQL variable is allowed. Like host variables in a SQL statement, host variables in a PL/SQL block must be prefixed with a colon. The colon sets host variables apart from PL/SQL variables and database objects.

#### 1.14.2 VARCHAR Variables

When entering a PL/SQL block, Oracle automatically checks the length fields of VARCHAR host variables. So, you must set the length fields before the block is entered. For input variables, set the length field to the length of the value stored in the string field. For output variables, set the length field to the maximum length allowed by the string field.

#### 1.14.3 Indicator Variables

In a PL/SQL block, you cannot refer to an indicator variable by itself; it must be appended to its associated host variable. In addition, if you refer to a host variable with its indicator variable, you must always refer to it the same way within the same block.

#### 1.14.4 About Handling Nulls

When entering a block, if an indicator variable has a value of -1, PL/SQL automatically assigns a null to the host variable. When exiting the block, if a host variable is null, PL/SQL automatically assigns a value of -1 to the indicator variable.

#### 1.14.5 About Handling Truncated Values

PL/SQL does not raise an exception when a truncated string value is assigned to a host variable. However, if you use an indicator variable, PL/SQL sets it to the original length of the string.

#### 1.14.6 SQLCHECK

You must specify SQLCHECK=SEMANTICS when precompiling a program with an embedded PL/SQL block. You must also use the USERID option. For more information, see [SQLCHECK](../zzpre/running-Oracle-precompilers.md).

#### 1.14.7 Cursor Variables

Starting with Release 1.7 of the Pro\*FORTRAN Precompiler, you can use cursor variables in your Pro\*FORTRAN programs to process multi-row queries using static embedded SQL. A cursor variable identifies a cursor reference that is defined and opened on the Oracle Database Server, using PL/SQL. See the Oracle Database PL/SQL Language Reference for complete information about cursor variables.

The advantages of cursor variables are:

- Encapsulation: queries are centralized in the stored procedure that opens the cursor variable.

- Ease of maintenance: only the stored procedure needs to be changed if the table changes.

- Security: the user of the application (the username when the Pro\*FORTRAN application connected to the database) must have execute permission on the stored procedure that opens the cursor. This user, however, does not need to have read permission on the tables used in the query. This capability can be used to limit access to the columns in the table.

### 1.15 About Declaring a Cursor Variable

You declare a Pro\*FORTRAN cursor variable using the SQLCURSOR pseudotype. For example:

    EXEC SQL BEGIN DECLARE SECTION
     ...
     SQLCURSOR CURVAR
     ...
     EXEC SQL END DECLARE SECTION

A SQLCURSOR variable is implemented using a FORTRAN INTEGER\*4 array in the code that Pro\*FORTRAN generates. A cursor variable is just like any other Pro\*FORTRAN host variable.

#### 1.15.1 About Allocating a Cursor Variable

Before you can OPEN or FETCH a cursor variable, you must allocate it by using the Pro\*FORTRAN ALLOCATE command. For example, to allocate the cursor variable CURVAR that was declared in the previous section, write the following statement:

    EXEC SQL ALLOCATE :CURVAR

Allocating a cursor variable does not require a call to the server, either at precompile time or at run time.

**Caution:**

Allocating a cursor variable does cause heap memory to be used. For this reason, avoid allocating a cursor variable in a program loop.

#### 1.15.2 About Opening a Cursor Variable

You must use an embedded anonymous PL/SQL block to open a cursor variable on the Oracle Server. The anonymous PL/SQL block may open the cursor either indirectly by calling a PL/SQL stored procedure that opens the cursor (and defines it in the same statement) or directly from the Pro\*FORTRAN program.

#### 1.15.3 About Opening Indirectly through a Stored PL/SQL Procedure

Consider the following PL/SQL package stored in the database:

    CREATE PACKAGE demo_cur_pkg AS
     TYPE EmpName IS RECORD (name VARCHAR2(10));
     TYPE cur_type IS REF CURSOR RETURN EmpName;
     PROCEDURE open_emp_cur (
     curs IN OUT curtype,
     dept_num IN NUMBER);
    END;
    CREATE PACKAGE BODY demo_cur_pkg AS
     CREATE PROCEDURE open_emp_cur (
     curs IN OUT curtype,
     dept_num IN NUMBER) IS
     BEGIN
     OPEN curs FOR
     SELECT ename FROM emp
     WHERE deptno = dept_num
     ORDER BY ename ASC;
     END;
    END;

After this package has been stored, you can open the variable curs by calling the open_emp_cur stored procedure from your Pro\*FORTRAN program, and FETCH from the cursor variable ECUR in the program. For example:

    EXEC SQL BEGIN DECLARE SECTION
     SQLCURSOR ECUR
     INTEGER*4 DNUM
     VARCHAR*10 ENAM, ENAML, ENAMA
     EXEC SQL END DECLARE SECTION
     ...
    * Allocate the cursor variable.
     EXEC SQL ALLOCATE :ECUR
     ...
     DNUM=30
    * Open the cursor on the Oracle Database Server.
     EXEC SQL EXECUTE
     1 BEGIN
     2 demo_cur_pkg.open_emp_cur(:ECUR, :DNUM);
     3 END;
     4 END-EXEC
     EXEC SQL WHENEVER NOTFOUND DO CALL SIGNOFF
    *
     1000 EXEC SQL FETCH :ECUR INTO :ENAM
     PRINT *, "Employee Name: ", ENAM
     GOTO 1000
     ...

#### 1.15.4 About Opening Directly from Your Pro\*FORTRAN Application

To open a cursor by using a PL/SQL anonymous block in a Pro\*FORTRAN program, define the cursor in the anonymous block. Consider the following example:

    EXEC SQL EXECUTE
     1 BEGIN
     2 OPEN :ECUR FOR SELECT ENAME FROM EMP
     3 WHERE DEPTNO = :DNUM;
     4 END;
     5 END-EXEC
     ...

#### 1.15.5 Return Types

When you define a reference cursor (REF CURSOR) in a PL/SQL stored procedure, you must declare the type that the cursor returns. The return types allowed for reference cursors are described in the [PL/SQL User's Guide and Reference](../lnpls/overview.md).

#### 1.15.6 About Fetching from a Cursor Variable

Use the embedded SQL FETCH .... INTO command to retrieve the rows SELECTed when you opened the cursor variable. For example:

    EXEC SQL FETCH :ECUR INTO :EINFO:IEINFO

Before you can FETCH from a cursor variable, the variable must be initialized and opened. You cannot FETCH from an unopened cursor variable.

#### 1.15.7 About Closing a Cursor Variable

Use the embedded SQL CLOSE command to close a cursor variable. For example:

    EXEC SQL BEGIN DECLARE SECTION
    * Declare the cursor variable.
     SQLCURSOR ECUR
     ...
     EXEC SQL END DECLARE SECTION
    * Allocate and open the cursor variable, then
    * fetch one or more rows.
     ...
    * Close the cursor variable.
     EXEC SQL CLOSE :ECUR

#### 1.15.8 Restrictions

The following restrictions apply to the use of cursor variables:

- You can only use cursor variables with the ALLOCATE, FETCH, and CLOSE commands. The DECLARE CURSOR command does not apply to cursor variables.

- You cannot FETCH from a CLOSEd or unALLOCATEd cursor variable.

- If you precompile with MODE=ANSI, it is an error to close a cursor variable that is already closed.

- You cannot use the AT clause with the ALLOCATE command.

#### 1.15.9 Error Conditions

Do not perform any of the following operations:

- FETCH from a closed cursor variable

- use a cursor variable that is not ALLOCATEd

- CLOSE a cursor variable that is not open

These operations on cursor variables result in errors.

#### 1.15.10 Sample Programs

The following sample programs -- a SQL script (SAMPLE11.SQL) and a Pro\*FORTRAN program (SAMPLE11.PFO) -- demonstrate how you can use cursor variables in Pro\*FORTRAN.

**Note:**

For simplicity in demonstrating this feature, this example does not perform the password management techniques that a deployed system normally uses. In a production environment, follow the Oracle Database password management guidelines, and disable any sample accounts. See [Oracle Database Security Guide](../dbseg/managing-security-for-application-developers.md) for password management guidelines and other security recommendations.

#### 1.15.11 SAMPLE11.SQL

Following is the PL/SQL source code for a creating a package that declares and opens a cursor variable:

    CONNECT AAAAA/BBBBB
    CREATE OR REPLACE PACKAGE emp_demo_pkg AS
     TYPE emp_cur_type IS REF CURSOR RETURN emp%ROWTYPE;
     PROCEDURE open_cur (
     cursor IN OUT emp_cur_type,
     dept_num IN number);
    END emp_demo_pkg;
    /
    CREATE OR REPLACE PACKAGE BODY emp_demo_pkg AS
     PROCEDURE open_cur (
     cursor IN OUT emp_cur_type,
     dept_num IN number) IS
     BEGIN
     OPEN cursor FOR SELECT * FROM emp
     WHERE deptno = dept_num
     ORDER BY ename ASC;
     END;
    END emp_demo_pkg;
    /

#### 1.15.12 SAMPLE11.PFO

Following is a Pro\*FORTRAN sample program that uses the cursor declared in the SAMPLE11.SQL example to fetch employee names, salaries, and commissions from the EMP table.

    PROGRAM SAMPLE11
     EXEC SQL BEGIN DECLARE SECTION
    * Declare the cursor variable.
     SQLCURSOR ECUR
    * EMPINFO
     INTEGER ENUM
     CHARACTER*10 ENAM
     VARCHAR*9 EJOB, EJOBL, EJOBA
     INTEGER EMGR
     VARCHAR*10 EDAT, EDATL, EDATA
     REAL ESAL
     REAL ECOM
     INTEGER EDEP
    * EMPINFO INDICATORS
     INTEGER*2 IENUM
     INTEGER*2 IENAM
     INTEGER*2 IEJOB
     INTEGER*2 IEMGR
     INTEGER*2 IEDAT
     INTEGER*2 IESAL
     INTEGER*2 IECOM
     INTEGER*2 IEDEP
     EXEC SQL END DECLARE SECTION
     EXEC SQL INCLUDE SQLCA
     COMMON /CURSOR/ ECUR
     EXEC SQL WHENEVER SQLERROR DO CALL SQLERR

    * LOG ON TO ORACLE.
     CALL LOGON

    * Initialize the cursor variable.
     EXEC SQL ALLOCATE :ECUR
     TYPE 1000
     1000 FORMAT (/, 'Enter department number (0 to exit): ', $)
     ACCEPT 1100, EDEP
     1100 FORMAT (I10)
     IF (EDEP .LE. 0) THEN
     CALL SIGNOFF
     ENDIF

    * Open the cursor by calling a PL/SQL stored procedure.
     EXEC SQL EXECUTE
     1 BEGIN
     2 emp_demo_pkg.open_cur (:ECUR, :EDEP);
     3 END;
     4 END-EXEC
     PRINT 1200, EDEP
     1200 FORMAT (/, 'For department ', I, ':',/)
     PRINT 1300
     1300 FORMAT (/, 'EMPLOYEE SALARY COMMISSION',
     + /, '---------- ---------- ----------')

    * Fetch data from the cursor into the host variables.
     2000 EXEC SQL WHENEVER NOT FOUND DO CALL SIGNOFF
     EXEC SQL FETCH :ECUR
     1 INTO :ENUM:IENUM,
     2 :ENAM:IENAM,
     3 :EJOB:IEJOB,
     4 :EMGR:IEMGR,
     5 :EDAT:IEDAT,
     6 :ESAL:IESAL,
     7 :ECOM:IECOM,
     8 :EDEP:IEDEP

    * Check for commission and print results.
     IF (IECOM .EQ. 0) THEN
     PRINT 2100, ENAM, ESAL, ECOM
     2100 FORMAT (A10, 2X, F10.2, 2X, F10.2)
     ELSE
     PRINT 2200, ENAM, ESAL
     2200 FORMAT (A10, 2X, F10.2, 2X, ' N/A')
     ENDIF
     GOTO 2000
     END

    * LOG ON TO ORACLE.
     SUBROUTINE LOGON
     EXEC SQL BEGIN DECLARE SECTION
     CHARACTER*10 UID
     CHARACTER*10 PWD
     EXEC SQL END DECLARE SECTION
     EXEC SQL INCLUDE SQLCA
     UID = 'AAAAA'
     PWD = 'BBBBB'
     EXEC SQL CONNECT :UID IDENTIFIED BY :PWD
     PRINT 3000, UID
     3000 FORMAT (/, 'CONNECTED TO ORACLE AS USER: ', A)
     END
    * Close the cursor variable.
     SUBROUTINE SIGNOFF
     EXEC SQL BEGIN DECLARE SECTION
     SQLCURSOR ECUR
     EXEC SQL END DECLARE SECTION
     EXEC SQL INCLUDE SQLCA
     COMMON /CURSOR/ ECUR
     EXEC SQL CLOSE :ECUR
     PRINT 4100
     4100 FORMAT (/, 'HAVE A GOOD DAY.', /)
     EXEC SQL COMMIT WORK RELEASE
     STOP
     END

     SUBROUTINE SQLERR
     EXEC SQL INCLUDE SQLCA
     EXEC SQL WHENEVER SQLERROR CONTINUE
     PRINT*, ' '
     PRINT *, 'ORACLE ERROR DETECTED: '
     PRINT '(70A1)', SQLEMC
     PRINT*, ' '
     EXEC SQL ROLLBACK WORK RELEASE
     STOP
     END

### 1.16 Connecting to Oracle

Your Pro\*FORTRAN program must log on to Oracle before querying or manipulating data. To log on, you use the CONNECT statement, as in

    * Log on to Oracle.
     EXEC SQL CONNECT :UID IDENTIFIED BY :PWD

where UID and PWD are CHARACTER or VARCHAR host variables. Alternatively, you can use the statement

    * Log on to Oracle.
     EXEC SQL CONNECT :UIDPWD

where the host variable UIDPWD contains your username and password separated by a slash (/).

The CONNECT statement must be the first SQL statement executed by the program. That is, other executable SQL statements can positionally, but not logically, precede the CONNECT statement.

To supply the Oracle username and password separately, you define two host variables in the Declare Section as character strings or VARCHAR variables. If you supply a userid containing both username and password, only one host variable is needed.

Make sure to set the username and password variables before the CONNECT is executed or it will fail. Your program can prompt for the values or you can hard code them as follows:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     CHARACTER*5 UID
     CHARACTER*5 PWD
     ...
     EXEC SQL END DECLARE SECTION
     UID = 'AAAAA'
     PWD = 'BBBBB'
    * Handle logon errors.
     EXEC SQL WHENEVER SQLERROR GOTO ...
     EXEC SQL CONNECT :UID IDENTIFIED BY :PWD

However, you cannot hard code a username and password into the CONNECT statement or use quoted literals. For example, both of the following statements are invalid:

    * Invalid CONNECT statements
     EXEC SQL CONNECT AAAAA IDENTIFIED BY BBBBB
     EXEC SQL CONNECT 'AAAAA' IDENTIFIED BY 'BBBBB'

#### 1.16.1 Automatic Logons

You can automatically log on to the Oracle using the following userid:

    <prefix><username>

where prefix is the value of the Oracle initialization parameter OS_AUTHENT_PREFIX (the default value is OPS\$) and username is your operating system user or task name. For example, if the prefix is OPS\$, your user name is TBARNES, and OPS\$TBARNES is a valid Oracle userid, you log on to Oracle as user OPS\$TBARNES.

To take advantage of the automatic logon feature, you simply pass a slash (/) character to the precompiler, as follows:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     ...
     CHARACTER*1 ORAID
     EXEC SQL END DECLARE SECTION
     ORAID = '/'
     EXEC SQL CONNECT :ORAID

This automatically connects you as user OPS\$username. For example, if your operating system username is RHILL, and OPS\$RHILL is a valid Oracle username, connecting with a slash (/) automatically logs you on to Oracle as user OPS\$RHILL.

You can also pass a character string to the precompiler. However, the string cannot contain trailing blanks. For example, the following CONNECT statement will fail:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     ...
     CHARACTER*5 ORAID
     EXEC SQL END DECLARE SECTION
     ORAID = '/ '
     EXEC SQL CONNECT :ORAID

For more information about operating system authentication, see the Oracle Database Administrator's Guide.

#### 1.16.2 Concurrent Logons

Your application can use Oracle Net Services to access any combination of remote and local databases concurrently or make multiple connections to the same database. In the following example, you connect to two nondefault databases concurrently:

    * Declare host variables.
     EXEC SQL BEGIN DECLARE SECTION
     CHARACTER*5 UID
     CHARACTER*5 PWD
     CHARACTER*12 DBSTR1
     CHARACTER*12 DBSTR2
     EXEC SQL END DECLARE SECTION
     UID = 'AAAAA'
     PWD = 'BBBBB'
     DBSTR1 = 'NEWYORK'
     DBSTR2 = 'BOSTON'
    * Give each database connection a unique name.
     EXEC SQL DECLARE DBNAM1 DATABASE
     EXEC SQL DECLARE DBNAM2 DATABASE
    * Connect to the two non-default databases.
     EXEC SQL CONNECT :UID IDENTIFIED BY :PWD
     1 AT DBNAM1 USING :DBSTR1
     EXEC SQL CONNECT :UID IDENTIFIED BY :PWD
     1 AT DBNAM2 USING :DBSTR2

The string syntax in DBSTR1 and DBSTR2 depends on your network driver and how it is configured. DBNAM1 and DBNAM2 name the nondefault connections; they can be undeclared identifiers or host variables.

For step-by-step instructions on connecting to Oracle through Oracle Net Services, see [Meeting Program Requirements](../zzpre/meeting-program-requirements.md).
