This chapter describes Oracle's implementation of ANSI dynamic SQL (that is, dynamic SQL as specified by the SQL standard) which should be used for new Method 4 applications. It has enhancements over the older Oracle dynamic SQL Method 4, which is described in “Oracle Dynamic SQL: Method 4”. The ANSI Method 4 supports all Oracle types, while the older Oracle Method 4 does not support cursor variables, tables of group items, the DML returning clause, and LOBs.

In ANSI dynamic SQL, descriptors are internally maintained by Oracle, while in the older Oracle dynamic SQL Method 4, descriptors are defined in the user's Pro\*COBOL program. In both cases, with Method 4 your Pro\*COBOL program accepts or builds SQL statements that contain a varying number of host variables.

The main sections in this chapter are:

- Basics of ANSI Dynamic SQL

- Overview of ANSI SQL Statements

- Oracle Extensions

- ANSI Dynamic SQL Precompiler Options

- Full Syntax of the Dynamic SQL Statements

- Sample Programs: SAMPLE12.PCO

**Related Topics**

- [Oracle Dynamic SQL: Method 4](Oracle-dynamic-SQL-method-4.md)

### 10.1 Basics of ANSI Dynamic SQL

Consider the SQL statement:

    SELECT ename, empno FROM emp WHERE deptno = :deptno_data

The steps you follow to use ANSI dynamic SQL are:

- Declare variables, including a string to hold the statement to be executed.

- Allocate descriptors for input and output variables.

- Prepare the statement.

- Describe input for the input descriptor.

- Set the input descriptor (in our example the one input host bind variable, `deptno_data)`.

- Declare and open a dynamic cursor.

- Set the output descriptors (in our example, the output host variables `ename `and `empno)`.

- Repeatedly fetch data, using GET DESCRIPTOR to retrieve the `ename` and `empno` data fields from each row.

- Do something with the data retrieved (output it, for instance).

- Close the dynamic cursor and deallocate the input and output descriptors.

#### 10.1.1 Precompiler Options

Normally, if you are using ANSI dynamic SQL you will be writing to the ANSI standard for precompilers and will therefore be using the macro command line option `MODE=ANSI`. If you wish to use this method and do not wish to use MODE=ANSI, then the functionality is controlled by the micro command line option: `DYNAMIC=ANSI`.

You can either set the micro precompiler option DYNAMIC to ANSI, or set the macro option MODE to ANSI. This causes the default value of DYNAMIC to be ANSI. The other setting of DYNAMIC is `ORACLE`. For more about micro options, see “Macro and Micro Options” and “`DYNAMIC`”.

In order to use ANSI type codes, set the precompiler micro option `TYPE_CODE` to ANSI, or set the macro option `MODE` to `ANSI`. This changes the default setting of `TYPE_CODE` to ANSI. To set `TYPE_CODE` to `ANSI`, `DYNAMIC` must also be `ANSI`.

For a list of the `ANSI SQL `types see “ANSI SQL Datatypes”. Use the `ANSI` types with precompiler option `TYPE_CODE` set to ANSI if you want your application to be portable across database platforms and be as compliant to `ANSI` as possible.

For more details, see “`MODE`” and “`TYPE_CODE`”.

**Related Topics**

- [Macro and Micro Options](precompiler-options.md)
- [DYNAMIC](precompiler-options.md)
- [MODE](precompiler-options.md)
- [TYPE_CODE](precompiler-options.md)

### 10.2 Overview of ANSI SQL Statements

Allocate a descriptor area before using it in a dynamic SQL statement.

The ALLOCATE DESCRIPTOR statement syntax is:

         EXEC SQL ALLOCATE DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
            [WITH MAX {:occurrences | numeric_literal}]
         END-EXEC.

A global descriptor can be used in any module in the program. A local descriptor can be accessed only in the file in which it is allocated. Local is the default.

The descriptor name, `desc_nam`, is a host variable. A string literal can be used instead.

`occurrences` is the maximum number of bind variables or columns that the descriptor can hold, with a default of 100.

When a descriptor is no longer needed, deallocate it to conserve memory.

The deallocate statement is:

         EXEC SQL DEALLOCATE DESCRIPTOR [GLOBAL | LOCAL]
            {:desc_nam | string_literal}
    END-EXEC.

Use the DESCRIBE statement to obtain information on a prepared SQL statement. DESCRIBE INPUT describes bind variables for the dynamic statement that has been prepared. DESCRIBE OUTPUT (the default) can give the number, type, and length of the output columns. The simplified syntax is:

         EXEC SQL DESCRIBE [INPUT | OUTPUT] sql_statement
            USING [SQL] DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
         END-EXEC.

If your SQL statement has input and output values, you must allocate two descriptors: one for input and one for output values. If there are no input values, for example:

    SELECT ename, empno FROM emp

then the input descriptor is not needed.

Use the SET DESCRIPTOR statement to specify input values for INSERTS, UPDATES, DELETES and the WHERE clauses of SELECT statements. Use SET DESCRIPTOR to set the number of input bind variables (stored in COUNT) when you have not done a DESCRIBE into your input descriptor:

         EXEC SQL SET DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
            COUNT = {:kount | numeric_literal}
         END-EXEC.

`kount` can be a host variable or a numeric literal, such as 5. Use a SET DESCRIPTOR statement for each host variable, giving at least the data value of the variable:

         EXEC SQL SET DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
            VALUE item_number DATA = :hv3
    END-EXEC.

You can also set the type and length of the input host variable:

Note: If you do not set the type and length, either explicitly, through the SET DESCRIPTOR statement, or implicitly by doing a DESCRIBE OUTPUT, when TYPE_CODE=ORACLE, the precompiler will use values for these derived from the host variable itself. When TYPE_CODE=ANSI, you must set the type using the values in Table 10-1. You should also set the length because the ANSI default lengths may not match those of your host variable.

         EXEC SQL SET DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
            VALUE item_number TYPE = :hv1, LENGTH = :hv2, DATA = :hv3
    END-EXEC.

We use the identifiers` hv1`, `hv2`, and `hv3 `to remind us that the values must be supplied by host variables. item_number is the position of the input variable in the SQL statement. It can be a host variable or an integer number.

TYPE is the Type Code selected from the following table, if TYPE_CODE is set to ANSI:

Table 10-1 ANSI SQL Datatypes

| Datatype          | Type Code |
|:------------------|:----------|
| CHARACTER         | 1         |
| CHARACTER VARYING | 12        |
| DATE              | 9         |
| DECIMAL           | 3         |
| DOUBLE PRECISION  | 8         |
| FLOAT             | 6         |
| INTEGER           | 4         |
| NUMERIC           | 2         |
| REAL              | 7         |
| SMALLINT          | 5         |

See Table 11-2 for the Oracle type codes. Use the negative value of the Oracle code if the ANSI datatype is not in the table, and TYPE_CODE = ANSI.

DATA is the host variable value which is input.

You can also set other input values such as indicator, precision and scale. See the more complete discussion of “SET_DESCRIPTOR” for a list of all the possible descriptor item names.

The numeric values in the SET DESCRIPTOR statement must be declared as either `PIC S9(9) COMP `or `PIC S9(4) COMP` except for indicator and returned length values which you must declare as `PIC S9(4)COMP`.

In the following example, when you want to retrieve empno, set these values: VALUE=2, because `empno` is the second output host variable in the dynamic SQL statement. The host variable `EMPNO-TYP` is set to 3 (Oracle Type for integer). The length of a host integer, `EMPNO-LEN`, is set to 4, which is the size of the host variable. The DATA is equated to the host variable EMPNO-DATA which will receive the value from the database table. The code fragment is as follows:

     ...
     01  DYN-STATEMENT PIC X(58)
         VALUE "SELECT ename, empno FROM emp WHERE deptno =:deptno_number".
     01  EMPNO-DATA PIC S9(9) COMP.
     01  EMPNO-TYP  PIC S9(9) COMP   VALUE 3.
     01  EMPNO-LEN  PIC S9(9) COMP   VALUE 4.
     ...
         EXEC SQL SET DESCRIPTOR 'out' VALUE 2  TYPE=:EMPNO-TYP, LENGTH=:EMPNO-LEN,
            DATA=:EMPNO-DATA END-EXEC.


After setting the input values, execute or open your statement using the input descriptor. If there are output values in your statement, set them before doing a FETCH. If you have done a DESCRIBE OUTPUT, you may have to reset the actual types and lengths of your host variables because the DESCRIBE execution will produce internal types and lengths which differ from your host variable external types and length.

After the FETCH of the output descriptor, use GET DESCRIPTOR to access the returned data. Again we show a simplified syntax with details later in this chapter:

         EXEC SQL GET DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
            VALUE item_number
    :hv1 = DATA, :hv2 = INDICATOR, :hv3 = RETURNED_LENGTH
         END-EXEC.

`desc_nam` and `item_number` can be literals or host variables. A descriptor name can be a literal such as 'out'. An item number can be a numeric literal such as 2.

`hv1, hv2, and hv3` are host variables. They must be host variables, not literals. Only three are shown in the example. See Table 10-4 for a list of all possible items of returned data that you can get.

Use either` PIC S9(n) COMP `where n is the platform-dependent upper limit, `PIC S9(9)COMP `or `PIC S9(4)COMP`for all numeric values, except for indicator and returned length variables, which must be `PIC S9(4) COMP`.

**Related Topics**

- SET DESCRIPTOR

### 10.3 Sample Code

The following example demonstrates the use of ANSI Dynamic SQL. It allocates an input descriptor `in` and an output descriptor `out` to execute a SELECT statement. Input values are set through the SET DESCRIPTOR statement. The cursor is opened and fetched from and the resulting output values are retrieved through a GET DESCRIPTOR statement.

     ...
     01  DYN-STATEMENT PIC X(58)
         VALUE "SELECT ENAME, EMPNO FROM EMP WHERE DEPTNO =:DEPTNO-DAT".
     01  EMPNO-DAT  PIC S9(9) COMP.
     01  EMPNO-TYP  PIC S9(9) COMP   VALUE 3.
     01  EMPNO-LEN  PIC S9(9) COMP   VALUE 4.
     01  DEPTNO-TYP PIC S9(9) COMP   VALUE 3.
     01  DEPTNO-LEN PIC S9(9) COMP   VALUE 4.
     01  DEPTNO-DAT PIC S9(9) COMP   VALUE 10.
     01  ENAME-TYP  PIC S9(9) COMP   VALUE 3.
     01  ENAME-LEN  PIC S9(9) COMP   VALUE 30.
     01  ENAME-DAT  PIC X(30).
     01  SQLCODE PIC S9(9)    COMP   VALUE 0.
     ...
    * Place preliminary code, including connection, here
    ...
         EXEC SQL ALLOCATE DESCRIPTOR 'in' END-EXEC.
         EXEC SQL ALLOCATE DESCRIPTOR 'out' END-EXEC.
         EXEC SQL PREPARE s FROM :DYN-STATEMENT END-EXEC.
         EXEC SQL DESCRIBE INPUT s USING DESCRIPTOR 'in' END-EXEC.
         EXEC SQL SET DESCRIPTOR 'in' VALUE 1 TYPE=:DEPTNO-TYP,
            LENGTH=:DEPTNO-LEN, DATA=:DEPTNO-DAT END-EXEC.
         EXEC SQL DECLARE c CURSOR FOR s END-EXEC.
         EXEC SQL OPEN c USING DESCRIPTOR 'in' END-EXEC.
         EXEC SQL DESCRIBE OUTPUT s USING DESCRIPTOR 'out' END-EXEC.
         EXEC SQL SET DESCRIPTOR 'out' VALUE 1 TYPE=:ENAME-TYP,
            LENGTH=:ENAME-LEN, DATA=:ENAME-DAT END-EXEC.
         EXEC SQL SET DESCRIPTOR 'out' VALUE 2 TYPE=:EMPNO-TYP,
            LENGTH=:EMPNO-LEN, DATA=:EMPNO-DAT END-EXEC.

         EXEC SQL WHENEVER NOT FOUND GOTO BREAK END-EXEC.
     LOOP.
         IF SQLCODE NOT = 0
            GOTO BREAK.
         EXEC SQL FETCH c INTO DESCRIPTOR 'out' END-EXEC.
         EXEC SQL GET DESCRIPTOR 'OUT' VALUE 1 :ENAME-DAT = DATA END-EXEC.
         EXEC SQL GET DESCRIPTOR 'OUT' VALUE 2 :EMPNO-DAT = DATA END-EXEC.
         DISPLAY "ENAME = " WITH NO ADVANCING
         DISPLAY ENAME-DAT  WITH NO ADVANCING
         DISPLAY "EMPNO = " WITH NO ADVANCING
         DISPLAY EMPNO-DAT.
         GOTO LOOP.
     BREAK:
         EXEC SQL CLOSE c END-EXEC.
         EXEC SQL DEALLOCATE DESCRIPTOR 'in' END-EXEC.
         EXEC SQL DEALLOCATE DESCRIPTOR 'out' END-EXEC.

### 10.4 Oracle Extensions

These extensions are described next:

- Reference semantics for data items in SET statements.

- Arrays for bulk operations.

- Support for object types, NCHAR columns, and LOBs.

#### 10.4.1 Reference Semantics

The ANSI standard specifies value semantics. To improve performance, Oracle has extended this standard to include reference semantics.

Value semantics makes a copy of your host variables data. Reference semantics uses the addresses of your host variables, avoiding a copy. Thus, reference semantics can provide performance improvements for large amounts of data.

To help speed up fetches, use the REF keyword before the data clauses:

         EXEC SQL SET DESCRIPTOR 'out' VALUE 1 TYPE=:ENAME-TYP,
            LENGTH=:ENAME-LEN, REF DATA=:ENAME-DAT END-EXEC.
         EXEC SQL DESCRIPTOR 'out' VALUE 2 TYPE=:EMPNO-TYP,
            LENGTH=:EMPNO-LEN, REF DATA=:EMPNO-DAT END-EXEC.

Then the host variables receive the results of the retrieves. The GET statement is not needed. The retrieved data is written directly into `ename_data` and `empno_data` after each FETCH.

Use of the REF keyword is allowed only before DATA, INDICATOR and RETURNED_LENGTH items (which can vary with each row fetched) as in this fragment of code:

     01   INDI       PIC S9(4) COMP.
     01   RETRN-LEN  PIC S9(9) COMP.
     ...
          EXEC SQL SET DESCRIPTOR 'out' VALUE 1 TYPE=:ENAME-TYP,
             LENGTH=:ENAME-LEN, REF DATA=:ENAME-DAT,
             REF INDICATOR=:INDI, REF RETURNED_LENGTH =:RETRN-LEN END-EXEC.

After each fetch, `RETRN-LEN `holds the actual retrieved length of the `ename` field, which is useful for `CHAR` or `VARCHAR2 `data.

`ENAME-LEN` will not receive the returned length. It will not be changed by the FETCH statement. Use a DESCRIBE statement, followed by a GET statement to find out the maximum column width before fetching rows of data.

REF keyword is also used for other types of SQL statements than SELECT, to speed them up. Note that with reference semantics, the host variable is used rather than a value copied into the descriptor area. The host variable data at the time of execution of the SQL statement is used, not its data at the time of the SET. Here is an example:

     ...
         MOVE 1 to VAL.
     ...
         EXEC SQL SET DESCRIPTOR 'value' VALUE 1 DATA = :VAL END-EXEC.
         EXEC SQL SET DESCRIPTOR 'reference' VALUE 1 REF DATA = :VAL END-EXEC.
         MOVE 2 to VAL.
    * Will use  VAL = 1
         EXEC SQL EXECUTE s USING  DESCRIPTOR 'value' END-EXEC.
    *Will use VAL = 2
         EXEC SQL EXECUTE s USING DESCRIPTOR 'reference' END-EXEC.

See “SET_DESCRIPTOR” for many more details on the differences.

**Related Topics**

- SET DESCRIPTOR

#### 10.4.2 Using Tables for Bulk Operations

Oracle's implementation of ANSI dynamic SQL extends the SQL standard's dynamic SQL by providing bulk operations. To use bulk operations, use the `FOR` clause with an array size to specify the amount of input data or the number of rows you want to process.

The `FOR` clause is used in the ALLOCATE statement to give the maximum amount of data or number of rows. For example, to use a maximum array size of 100:

         EXEC SQL FOR 100 ALLOCATE DESCRIPTOR 'out' END-EXEC.

or:

         MOVE 100 TO INT-ARR-SIZE.
         EXEC SQL FOR :INT-ARR-SIZE ALLOCATE DESCRIPTOR 'out' END-EXEC.

The `FOR `clause is then used in subsequent statements that access the descriptor. In an output descriptor the FETCH statement must have an array size equal to or less than the array size already used in the ALLOCATE statement:

         EXEC SQL FOR 20 FETCH c1 USING DESCRIPTOR 'out' END-EXEC.

Subsequent GET statements for the same descriptor, that get DATA, INDICATOR, or RETURNED_LENGTH values, must use the same array size as the FETCH statement.

     01  VAL-DATA   OCCURS 20 TIMES  PIC S9(9) COMP.
     01  VAL-INDI   OCCURS 20 TIMES  PIC S9(4) COMP.
    ...
         EXEC SQL FOR 20 GET DESCRIPTOR 'out' VALUE 1 :VAL-DATA = DATA,
           :VAL-INDI = INDICATOR
         END-EXEC.

However, GET statements that reference other items which do not vary from row to row, such as LENGTH, TYPE and COUNT, must not use the `FOR` clause:

     01  CNT  PIC S9(9) COMP.
     01  LEN  PIC S9(9) COMP.
    ...
         EXEC SQL GET DESCRIPTOR 'out'   :CNT = COUNT END-EXEC.
         EXEC SQL GET DESCRIPTOR 'out' VALUE 1 :LEN = LENGTH END-EXEC.

The same holds true for SET statements with reference semantics. SET statements which precede the FETCH and employ reference semantics for DATA, INDICATOR, or RETURNED_LENGTH must have the same array size as the FETCH:

     ...
     01  REF-DATA   OCCURS 20 TIMES  PIC S9(9) COMP.
     01  REF-INDI   OCCURS 20 TIMES  PIC S9(4) COMP.
    ...
         EXEC SQL FOR 20 SET DESCRIPTOR 'out' VALUE 1 REF DATA = :REF-DATA,
            REF INDICATOR = :REF-INDI END-EXEC.

Similarly, for a descriptor that is used for input, to insert a batch of rows, for instance, the EXECUTE or OPEN statement must use an array size equal to or less than the size used in the ALLOCATE statement. The SET statement, for both value and reference semantics, that accesses DATA, INDICATOR, or RETURNED_LENGTH must use the same array size as in the EXECUTE statement.

The FOR clause is never used on the DEALLOCATE or PREPARE statements.

The following code sample illustrates a bulk operation with no output descriptor (there is no output, only input to be inserted into the table `emp`). The value of `CNT` is 2 (there are two host variables, `ENAME and EMPNO`, in the INSERT statement). The data table `ENAME-TABLE` holds three character strings: `Tom`, `Dick` and `Harry`, in that order. Their employee numbers are in the table `EMPNO-TABLE`. The indicator table `ENAME-IND` has a value of -1 for the second element; so a `NULL` will be inserted instead of `Dick`.

     01  DYN-STATEMENT  PIC X(240) value
             "INSERT INTO EMP(ENAME, EMPNO) VALUES (:ENAME,:EMPNO)".
     01  ARRAY-SIZE PIC S9(9) COMP   VALUE 3.
     01  ENAME-VALUES.
          05 FILLER PIC X(6)   VALUE "Tom   ".
          05 FILLER PIC X(6)   VALUE "Dick  ".
          05 FILLER PIC X(6)   VALUE "Harry ".
     01  ENAME-TABLE REDEFINES ENAME-VALUES.
          05 ENAME  PIC X(6)OCCURS 3 TIMES.
     01  ENAME-IND  PIC S9(4) COMPOCCURS 3 TIMES.
     01  ENAME-LEN  PIC S9(9) COMP   VALUE   6.
     01  ENAME-TYP  PIC S9(9) COMP   VALUE  96.
     01  EMPNO-VALUES.
          05 FILLER PIC S9(9) COMP   VALUE 8001.
          05 FILLER PIC S9(9) COMP   VALUE 8002.
          05 FILLER PIC S9(9) COMP   VALUE 8003.
     01  EMPNO-TABLE REDEFINES EMPNO-VALUES.
          05 EMPNO  PIC S9(9) DISPLAY SIGN LEADING  OCCURS 3 TIMES.
     01  EMPNO-LEN  PIC S9(9) COMP   VALUE   4.
     01  EMPNO-TYP  PIC S9(9) COMP   VALUE   3.
     01  CNT        PIC S9(9) COMP   VALUE   2.
    ........
         EXEC SQL FOR :ARRAY-SIZE ALLOCATE DESCRIPTOR 'in' END-EXEC.
         EXEC SQL PREPARE S FROM :DYN-STATEMENT  END-EXEC.
         MOVE 0 TO ENAME-IND(1).
         MOVE -1 TO ENAME-IND(2).
         MOVE 0 TO ENAME-IND(3).
         EXEC SQL SET DESCRIPTOR 'in' COUNT = :CNT END-EXEC.
         EXEC SQL SET DESCRIPTOR 'in' VALUE 1
            TYPE = :ENAME-TYP, LENGTH =:ENAME-LEN
         END-EXEC.
         EXEC SQL FOR :ARRAY-SIZE  SET DESCRIPTOR 'in' VALUE 1
            DATA = :ENAME, INDICATOR = :ENAME-IND
         END-EXEC.
         EXEC SQL SET DESCRIPTOR 'in' VALUE 2
            TYPE = :EMPNO-TYP, LENGTH =:EMPNO-LEN
         END-EXEC.
         EXEC SQL FOR :ARRAY-SIZE  SET DESCRIPTOR 'in' VALUE 2
            DATA = :EMPNO
         END-EXEC.
         EXEC SQL FOR :ARRAY-SIZE EXECUTE S
            USING DESCRIPTOR 'in' END-EXEC.
      ...

The preceding code inserts these values into the table:

          EMPNO   ENAME
          8001    Tom
          8002
          8003    Harry

See the discussion in “The FOR Clause” for restrictions and cautions.

**Related Topics**

- [The FOR Clause](host-tables.md)

### 10.5 ANSI Dynamic SQL Precompiler Options

The macro option MODE (See “MODE”) sets ANSI compatibility characteristics and controls a number of functions. It can have the values ANSI or ORACLE. For individual functions there are micro options that override the MODE setting.

The precompiler micro option DYNAMIC specifies the descriptor behavior in dynamic SQL. The precompiler micro option TYPE_CODE specifies whether ANSI or Oracle datatype codes are to be used.

When the macro option MODE is set to ANSI, the micro option DYNAMIC becomes ANSI automatically. When MODE is set to ORACLE, DYNAMIC becomes ORACLE.

DYNAMIC and TYPE_CODE cannot be used inline.

The following table describes how the DYNAMIC setting affects various functionality:

Table 10-2 DYNAMIC Option Settings

| Function                   | DYNAMIC=ANSI                                                                 | DYNAMIC=ORACLE                                                                  |
|:---------------------------|:-----------------------------------------------------------------------------|:--------------------------------------------------------------------------------|
| Descriptor creation.       | Must use ALLOCATE statement.                                                 | Must use an Oracle format descriptor.                                           |
| Descriptor destruction.    | May use DEALLOCATE statement.                                                | N/A                                                                             |
| Retrieving data.           | May use both FETCH and GET statements.                                       | Must use only FETCH statement.                                                  |
| Setting input data.        | May use DESCRIBE INPUT statement. Must use SET statement.                    | Must set descriptor values in code. Must use DESCRIBE BIND VARIABLES statement. |
| Descriptor representation. | Single quoted literal or host identifier which contains the descriptor name. | Host variable, a pointer to SQLDA.                                              |
| Data types available.      | All ANSI types except BIT and all Oracle types.                              | Oracle types except objects, LOBs, and cursor variables.                        |

The micro option TYPE_CODE is set by the precompiler to the same setting as the macro option MODE. TYPE_CODE can only equal ANSI if DYNAMIC equals ANSI.

The following table shows the functionality corresponding to the TYPE_CODE settings.

Table 10-3 TYPE_CODE Option Settings

| Function                                                  | TYPE_CODE=ANSI                                                                                                                       | TYPE_CODE=ORACLE                                                              |
|:----------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------|
| Data type code numbers input and returned in dynamic SQL. | Use ANSI code numbers when ANSI type exists. Otherwise, use the negative of the Oracle code number.<br>Only valid when DYNAMIC=ANSI. | Use Oracle code numbers.<br>May be used regardless of the setting of DYNAMIC. |

**Related Topics**

- [MODE](precompiler-options.md)

### 10.6 Full Syntax of the Dynamic SQL Statements

For more details on all these statements, see the alphabetical listing in the appendix “Embedded SQL Statements and Precompiler Directives”.

**Related Topics**

- [Embedded SQL Statements and Precompiler Directives](embedded-SQL-statements-and-precompiler-directives.md)

#### 10.6.1 ALLOCATE DESCRIPTOR

This statement is used only for ANSI dynamic SQL.

##### Purpose

Use this statement to allocate a SQL descriptor area. Supply a descriptor, the maximum number of occurrences of host bind items, and an array size.

##### Syntax

         EXEC SQL [FOR [:]array_size] ALLOCATE DESCRIPTOR [GLOBAL | LOCAL]
            {:desc_nam | string_literal} [WITH MAX occurrences]
         END-EXEC.

##### 10.6.1.1 Variables

A number of variables can be used with the ALLOCATE descriptor. These include: array_size, desc_nam, and occurrences.

array_size
The optional array_size clause (an Oracle extension) supports table processing. It tells the precompiler that the descriptor is usable for table processing.

     GLOBAL | LOCAL

The optional scope clause defaults to LOCAL if not entered. A local descriptor can be accessed only in the file in which it is allocated. A global descriptor can be used in any module in the compilation unit.

desc_nam
The desc_nam variable defines the local descriptors that must be unique in the module. A runtime error is generated if the descriptor has been previously allocated, but not deallocated. A global descriptor must be unique for the application or a runtime error results.

occurrences
The optional occurrences clause is the maximum number of host variables possible in the descriptor. The occurrences variable must be an integer constant between 0 and 64K, or an error is returned. The default is 100. A precompiler error results if it does not conform to these rules.

##### 10.6.1.2  Examples

         EXEC SQL ALLOCATE DESCRIPTOR 'SELDES' WITH MAX 50 END-EXEC.

         EXEC SQL FOR :BATCH ALLOCATE DESCRIPTOR GLOBAL :BINDDES WITH MAX 25
            END-EXEC.

#### 10.6.2 DEALLOCATE DESCRIPTOR

##### Purpose

To free memory, use the deallocate statement. This statement deallocates a previously allocated SQL descriptor area.

##### Syntax

         EXEC SQL DEALLOCATE DESCRIPTOR [GLOBAL | LOCAL]
            {:desc_nam | string_literal}
         END-EXEC.

##### Variables

desc_nam
The only variable available with the deallocate descriptor is desc_nam (for descriptor name.) A runtime error results when a descriptor with the same name and scope has not been allocated, or has already been allocated and deallocated.

##### Examples

         EXEC SQL DEALLOCATE DESCRIPTOR GLOBAL 'SELDES' END-EXEC.

         EXEC SQL DEALLOCATE DESCRIPTOR :BINDDES END-EXEC.

#### 10.6.3 GET DESCRIPTOR

##### Purpose

Use to obtain information from a SQL descriptor area.

##### Syntax

         EXEC SQL [FOR [:]array_size] GET DESCRIPTOR [GLOBAL | LOCAL]
         {:desc_nam | string_literal}
            {:hv0  = COUNT | VALUE item_number :hv1 = item_name1
            [{, :hvN = item_nameN }]}
         END-EXEC.

##### Variables

array_size
The `FOR array_size` variable is an optional Oracle extension.` FOR array_size` has to be equal to the `array_size` field in the FETCH statement.

desc_nam
The descriptor name.

GLOBAL \| LOCAL
GLOBAL means that the descriptor name is known to all program files. LOCAL means that it is known only in the file in which it is allocated. LOCAL is the default.

COUNT
The total number of bind variables.

VALUE item_number
The position of the item in the SQL statement. `item_number` can be a variable or a constant. If` item_number` is greater than `COUNT`, the "no data found" condition is returned. `item_number` must be greater than 0.

hv1 .. hvN
These are host variables to which values are transferred.

item_name1 .. item_nameN
The descriptor item names corresponding to the host variables. The possible ANSI descriptor item names` `are listed in the following table.

Table 10-4 Definitions of Descriptor Item Names

| Descriptor Item Name    | Meaning                                                                                                                                                                                     |
|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TYPE`                  | See Table 10-1 for the ANSI type codes. See Table 11-2 for the Oracle type codes. Use the negative value of the Oracle code if the ANSI datatype is not in the table, and TYPE_CODE = ANSI. |
| `LENGTH`                | Length of data in the column. In characters for NCHAR, and otherwise in bytes. Set by the DESCRIBE OUTPUT.                                                                                  |
| `OCTET_LENGTH`          | Length of data in bytes.                                                                                                                                                                    |
| `RETURNED_LENGTH`       | The actual data length after a FETCH. It is undefined for fixed-length character types.                                                                                                     |
| `RETURNED_OCTET_LENGTH` | Length of the returned data in bytes.                                                                                                                                                       |
| `PRECISION`             | The number of digits.                                                                                                                                                                       |
| `SCALE`                 | For exact numeric types, the number of digits to the right of the decimal point.                                                                                                            |
| `NULLABLE`              | If 1, the column can have NULL values. If 0, the column cannot have NULL values.                                                                                                            |
| `INDICATOR`             | The associated indicator value.                                                                                                                                                             |
| `DATA`                  | The data value.                                                                                                                                                                             |
| `NAME`                  | Column name.                                                                                                                                                                                |
| `CHARACTER_SET_NAME`    | Column's character set.                                                                                                                                                                     |

The following table lists the Oracle extensions to the descriptor item names.

Table 10-5 Oracle Extensions to Definitions of Descriptor Item Names

| Descriptor Item Name | Meaning                                                         |
|:---------------------|:----------------------------------------------------------------|
| `NATIONAL_CHARACTER` | If 2, NCHAR or NVARCHAR2. If 1, character. If 0, non-character. |
| `INTERNAL_LENGTH`    | The internal length, in bytes.                                  |

##### Usage Notes

Use the FOR clause in GET DESCRIPTOR statements which contain DATA, INDICATOR, and RETURNED_LENGTH items only.

The internal type is provided by the DESCRIBE OUTPUT statement. For both input and output, you must set the type to be the external type of your host variable. TYPE is the Oracle or ANSI code in Table 10-1. You will receive the negative value of the Oracle type code if the ANSI type is not in the table.

LENGTH contains the column length in characters for fields that have fixed-width National Language character sets. It is in bytes for other character columns. It is set in DESCRIBE OUTPUT.

RETURNED_LENGTH is the actual data length set by the FETCH statement. It is in bytes or characters as described for LENGTH. The fields OCTET_LENGTH and RETURNED_OCTET_LENGTH are the lengths in bytes.

NULLABLE = 1 means that the column can have NULLS; NULLABLE = 0 means it cannot.

CHARACTER_SET_NAME only has meaning for character columns. For other types, it is undefined. The DESCRIBE OUTPUT statement obtains the value.

DATA and INDICATOR are the data value and the indicator status for that column. If data = NULL, but the indicator was not requested, an error is generated at runtime ("DATA EXCEPTION, NULL VALUE, NO INDICATOR PARAMETER").

##### Oracle-specific Descriptor Item Names

NATIONAL_CHARACTER = 2 if the column is an NCHAR or NVARCHAR2 column. If the column is a character (but not National Character) column, this item is set to 1. If a non-character column, this item becomes 0 after DESCRIBE OUTPUT is executed.

INTERNAL_LENGTH is for compatibility with Oracle dynamic Method 4. It has the same value as the length member of the Oracle descriptor area. See “Oracle Dynamic SQL: Method 4”.

##### Examples

         EXEC SQL GET DESCRIPTOR :BINDDES :COUNT = COUNT END-EXEC.

         EXEC SQL GET DESCRIPTOR 'SELDES' VALUE 1 :TYP = TYPE, :LEN = LENGTH
            END-EXEC.

         EXEC SQL FOR :BATCH GET DESCRIPTOR LOCAL 'SELDES'
            VALUE :SEL-ITEM-NO :IND = INDICATOR, :DAT = DATA END-EXEC.

**Related Topics**

- [Oracle Dynamic SQL: Method 4](Oracle-dynamic-SQL-method-4.md)

#### 10.6.4 SET DESCRIPTOR

##### Purpose

Use this statement to set information in the descriptor area from host variables. The SET DESCRIPTOR statement supports only host variables for the item names.

##### Syntax

         EXEC SQL [FOR [:]array_size] SET DESCRIPTOR [GLOBAL | LOCAL]
            {:desc_nam | string_literal}
            {COUNT = :hv0 | VALUE item_number
            [REF] item_name1 = :hv1
            [{, [REF] item_nameN = :hvN}]}
         END-EXEC.

##### Variables

array_size
This optional Oracle clause permits using arrays when setting the descriptor items DATA, INDICATOR, and RETURNED_LENGTH only. You cannot use other items in a SET DESCRIPTOR that contains the FOR clause. All host variable table sizes must match. Use the same array size for the SET statement that you use for the FETCH statement.

desc_nam
The descriptor name. It follows the rules in ALLOCATE DESCRIPTOR.

COUNT
The number of bind (input) or define (output) variables.

VALUE item_number
Position in the dynamic SQL statement of a host variable.

hv1 .. hvN
The host variables (not constants) that you set.

item_name1 .. item_nameN
In a similar way to the GET DESCRIPTOR syntax (see “GET DESCRIPTOR”), `item_name` can take on these values:

Table 10-6 Descriptor Item Names for SET DESCRIPTOR

| Descriptor Item Name | Meaning                                                                                                                                                                                        |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| TYPE                 | See Table 10-1 for the ANSI type codes. See Table 11-2 for the Oracle type codes. Use the negative value of the Oracle type code if the Oracle type is not in the table, and TYPE_CODE = ANSI. |
| LENGTH               | Maximum length of data in the column.                                                                                                                                                          |
| PRECISION            | The number of digits.                                                                                                                                                                          |
| SCALE                | For exact numeric types, the number of bytes to the right of the decimal point.                                                                                                                |
| INDICATOR            | The associated indicator value. Set for reference semantics.                                                                                                                                   |
| DATA                 | Value of the data to be set. Set for reference semantics.                                                                                                                                      |
| CHARACTER_SET_NAME   | Column's character set.                                                                                                                                                                        |

The Oracle extensions to the descriptor item names are listed in the following table.

Table 10-7 Extensions to Descriptor Item Names for SET DESCRIPTOR

| Descriptor Item Name | Meaning                                                                  |
|:---------------------|:-------------------------------------------------------------------------|
| RETURNED_LENGTH      | Length returned after a FETCH. Set if reference semantics is being used. |
| NATIONAL_CHARACTER   | Set to 2 when the input host variable is an NCHAR or NVARCHAR2 type.     |

##### Usage Notes

Reference semantics is another optional Oracle extension that speeds performance. Use the keyword REF before these descriptor items names only: DATA, INDICATOR, RETURNED_LENGTH. When you use the REF keyword you do not need to use a GET statement. Complex data types and DML returning clauses require the REF form of SET DESCRIPTOR. See “DML Returning Clause”.

When REF is used the associated host variable itself is used in the SET. The GET is not needed in this case. The RETURNED_LENGTH can only be set when you use the REF semantics, not the value semantics.

Use the same array size for the SET or GET statements that you use in the FETCH.

Set the NATIONAL_CHAR field to 2 for NCHAR host input values.

When setting an object type's characteristics, you must set USER_DEFINED_TYPE_NAME and USER_DEFINED_TYPE_NAME_LENGTH.

If omitted, USER_DEFINED_TYPE_SCHEMA and USER_DEFINED_TYPE_SCHEMA_LENGTH default to the current connection.

**Related Topics**

- [DML Returning Clause](embedded-SQL.md)
- GET DESCRIPTOR

##### 10.6.4.1 Example

Bulk table examples are found in "Using Tables for Bulk Operations".

     ...
     O1  BINDNO  PIC S9(9) COMP  VALUE 2.
     01  INDI    PIC S9(4) COMP  VALUE -1.
     01  DATA    PIC X(6)  COMP  VALUE "ignore".
     01  BATCH   PIC S9(9) COMP  VALUE 1.
     ...
         EXEC SQL FOR :batch ALLOCATE DESCRIPTOR :BINDDES END-EXEC.
         EXEC SQL SET DESCRIPTOR GLOBAL :BINDDES COUNT = 3 END-EXEC.
         EXEC SQL FOR :batch SET DESCRIPTOR :BINDDES
            VALUE :BINDNO INDICATOR = :INDI, DATA = :DATA END-EXEC.
    ...

#### 10.6.5 Use of PREPARE

##### Purpose

The PREPARE statement used in this method is the same as the PREPARE statement used in the Oracle dynamic SQL methods. An Oracle extension allows a quoted string for the SQL statement, as well as a variable.

##### Syntax

         EXEC SQL PREPARE statement_id FROM :sql_statement END-EXEC.

##### Variables

statement_id
This must not be declared; it is an undeclared SQL identifier associated with the prepared SQL statement.

sql_statement
A character string (a constant or a variable) holding the embedded SQL statement.

##### Examples

     ...
     01  STATEMENT    PIC X(255)
            VALUE "SELECT ENAME FROM emp WHERE deptno = :d".
     ...
         EXEC SQL PREPARE S1 FROM :STATEMENT END-EXEC.

#### 10.6.6 DESCRIBE INPUT

##### Purpose

This statement returns information about the input bind variables.

##### Syntax

         EXEC SQL DESCRIBE INPUT statement_id USING [SQL] DESCRIPTOR
            [GLOBAL | LOCAL] {:desc_nam | string_literal}
    END-EXEC.

##### Variables

statement_id
The same as used in PREPARE and DESCRIBE OUTPUT. This must not be declared; it is a SQL identifier.

GLOBAL \| LOCAL
GLOBAL means that the descriptor name is known to all program files. LOCAL means that it is known only in the file in which it is allocated. LOCAL is the default.

desc_nam
The descriptor name.

Usage Notes
Only COUNT and NAME are implemented for bind variables in this version.

##### Examples

         EXEC SQL DESCRIBE INPUT S1 USING SQL DESCRIPTOR GLOBAL :BINDDES END-EXEC.
         EXEC SQL DESCRIBE INPUT S2 USING DESCRIPTOR 'input' END-EXEC.

#### 10.6.7 DESCRIBE OUTPUT

##### Purpose

The DESCRIBE INPUT statement is used to obtain information about the columns in a PREPARE statement. The ANSI syntax differs from the older syntax. The information which is stored in the SQL descriptor area is the number of values returned and associated information such as type, length, and name.

##### Syntax

         EXEC SQL DESCRIBE [OUTPUT] statement_id USING [SQL] DESCRIPTOR
            [GLOBAL | LOCAL] {:desc_nam | string_literal}
    END-EXEC.

##### Variables

statement_id
The statement_id is a SQL identifier. It must not be declared.

GLOBAL \| LOCAL
GLOBAL means that the descriptor name is known to all program files. LOCAL means that it is known only in the file in which it is allocated. LOCAL is the default.

desc_nam
The descriptor name. Either a host variable preceded by a ':', or a single-quoted string. OUTPUT is the default and can be omitted.

##### Examples

     ...
     01  DESNAME   PIC X(10) VALUE "SELDES".
     ...
         EXEC SQL DESCRIBE S1 USING SQL DESCRIPTOR 'SELDES' END-EXEC.
    * Or:
         EXEC SQL DESCRIBE OUTPUT S1 USING DESCRIPTOR :DESNAME END-EXEC.

#### 10.6.8 EXECUTE

##### Purpose

EXECUTE matches input and output variables in a prepared SQL statement and then executes the statement. This ANSI version of EXECUTE differs from the older EXECUTE statement by allowing two descriptors in one statement to support DML RETURNING.

##### Syntax

         EXEC SQL [FOR [:]array_size] EXECUTE statement_id
            [USING [SQL] DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}]
            [INTO [SQL] DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}]
         END-EXEC.

##### Variables

array_size
The number of rows the statement will process.

statement_id
The same as used in PREPARE. This must not be declared; it is a SQL identifier. It can be a literal.

GLOBAL \| LOCAL
GLOBAL means that the descriptor name is known to all program files. LOCAL means that it is known only in the file in which it is allocated. LOCAL is the default.

desc_nam
The descriptor name. Either a host variable preceded by a ':', or a single-quoted string.

##### Usage Notes

The INTO clause implements the RETURNING clause for INSERT, UPDATE and DELETE (See “Inserting Rows” and succeeding pages).

##### Examples

         EXEC SQL EXECUTE S1 USING SQL DESCRIPTOR GLOBAL :BINDDES END-EXEC.

         EXEC SQL EXECUTE S2 USING DESCRIPTOR :bv1 INTO DESCRIPTOR 'SELDES'
            END-EXEC.

**Related Topics**

- [Inserting Rows](embedded-SQL.md)

#### 10.6.9 Use of EXECUTE IMMEDIATE

##### Purpose

The EXECUTE IMMEDIATE statement executes a literal or host variable character string containing the SQL statement.The ANSI SQL form of this statement is the same as in the older dynamic SQL:

##### Syntax

         EXEC SQL EXECUTE IMMEDIATE [:]sql_statement END-EXEC.

##### Variables

Only one variable is available with the EXECUTE IMMEDIATE statement.

sql_statement
The sql_statement variable is the SQL statement or PL/SQL block in a character string. It can be a host variable or a literal.

##### Examples

         EXEC SQL EXECUTE IMMEDIATE :statement END-EXEC.

#### 10.6.10 Use of DYNAMIC DECLARE CURSOR

##### Purpose

The DYNAMIC DECLARE CURSOR statement declares a cursor that is associated with a statement which is a query. This is a form of the generic Declare Cursor statement.

##### Syntax

         EXEC SQL DECLARE cursor_name CURSOR FOR statement_id END-EXEC.

##### Variables

cursor_name
A cursor variable (a SQL identifier, not a host variable).

statement_id
An undeclared SQL identifier (the same as the one used in the PREPARE statement).

##### Examples

         EXEC SQL DECLARE C1 CURSOR FOR S1 END-EXEC.

#### 10.6.11 OPEN Cursor

##### Purpose

The OPEN statement associates input parameters with a cursor and then opens the cursor.

##### Syntax

         EXEC SQL [FOR [:]array_size] OPEN dyn_cursor
            [[USING [SQL] DESCRIPTOR [GLOBAL | LOCAL] desc_nam1]
            [INTO [SQL] DESCRIPTOR [GLOBAL | LOCAL] desc_nam2] ]
         END-EXEC.

##### Variables

array_size
This limit is less than or equal to number specified when the descriptor was allocated.

GLOBAL \| LOCAL
GLOBAL means that the descriptor name is known to all program files. LOCAL means that it is known only in the file in which it is allocated. LOCAL is the default.

dyn_cursor
The cursor variable.

desc_nam1, desc_nam2
The optional descriptor names.

##### Usage Notes

If the prepared statement associated with the cursor contains colons or question marks, a USING clause must be specified, or an error results at runtime. The INTO clause supports DML RETURNING (See “Inserting Rows” and succeeding sections on DELETE and UPDATE).

##### Examples

         EXEC SQL OPEN C1 USING SQL DESCRIPTOR :BINDDES END-EXEC.

         EXEC SQL FOR :LIMIT OPEN C2 USING DESCRIPTOR :B1, :B2
           INTO SQL DESCRIPTOR :SELDES
         END-EXEC.

**Related Topics**

- [Inserting Rows](embedded-SQL.md)

#### 10.6.12 FETCH

##### Purpose

The FETCH statement fetches a row for a cursor declared with a dynamic DECLARE statement.

##### Syntax

         EXEC SQL [FOR [:]array_size] FETCH cursor INTO [SQL] DESCRIPTOR
           [GLOBAL | LOCAL] {:desc_nam | string_literal}
         END-EXEC.

##### Variables

array_size
The number of rows the statement will process.

cursor
The dynamic cursor that was previously declared.

GLOBAL \| LOCAL
GLOBAL means that the descriptor name is known to all program files. LOCAL means that it is known only in the file in which it is allocated. LOCAL is the default.

desc_nam
Descriptor name.

##### Usage Notes

The optional `array_size `in the FOR clause must be less than or equal to the number specified in the ALLOCATE DESCRIPTOR statement.

RETURNED_LENGTH is undefined for fixed-length character types.

##### Examples

         EXEC SQL FETCH FROM C1 INTO DESCRIPTOR 'SELDES' END-EXEC.

         EXEC SQL FOR :ARSZ FETCH C2 INTO DESCRIPTOR :DESC END-EXEC.

#### 10.6.13 CLOSE a Dynamic Cursor

##### Purpose

The CLOSE statement closes a dynamic cursor. Its syntax is identical to the Oracle Method 4.

##### Syntax

         EXEC SQL CLOSE cursor END-EXEC.

##### Variables

Only one variable is available with the CLOSE statement.

cursor
The cursor variable describes the previously declared dynamic cursor.

##### Examples

         EXEC SQL CLOSE C1 END-EXEC.

#### 10.6.14 Differences From Oracle Dynamic Method 4

The ANSI dynamic SQL interface supports all the features supported by the Oracle dynamic Method 4, with these additions:

- All datatypes, including cursor variables, and LOB types are supported by ANSI Dynamic SQL.

- The ANSI mode uses an internal SQL descriptor area which is an expansion of the external SQLDA used in Oracle older dynamic Method 4 to store its input and output information.

- New embedded SQL statements are introduced: ALLOCATE DESCRIPTOR, DEALLOCATE DESCRIPTOR, DESCRIBE, GET DESCRIPTOR, and SET DESCRIPTOR.

- The DESCRIBE statement does not return the names of indicator variables in ANSI Dynamic SQL.

- ANSI Dynamic SQL does not allow you to specify the maximum size of the returned column name or expression. The default size is set at 128.

- The descriptor name must be either an identifier in single-quotes or a host variable preceded by a colon.

- For output, the optional SELECT LIST FOR clause in the DESCRIBE is replaced by the optional keyword OUTPUT. The INTO clause is replaced by the USING DESCRIPTOR clause, which can contain the optional keyword SQL.

- For input, the optional BIND VARIABLES FOR clause of the DESCRIBE can be replaced by the keyword INPUT. The INTO clause is replaced by the USING DESCRIPTOR clause, which can contain the optional keyword SQL.

- The optional keyword SQL can come before the keyword DESCRIPTOR in the USING clause of the EXECUTE, FETCH and OPEN statements.

#### 10.6.15 Restrictions

Restrictions in effect on ANSI dynamic SQL are:

- You cannot mix the two dynamic methods in the same module.

- The precompiler option DYNAMIC must be set to ANSI. The precompiler option TYPE_CODE can be set to ANSI only if DYNAMIC is set to ANSI.

- The SET statement supports only host variables as item names.

### 10.7 Sample Programs: SAMPLE12.PCO

The following ANSI SQL dynamic Method 4 program, SAMPLE12.PCO, is found in the demo directory. SAMPLE12 mimics SQL\*Plus by prompting for SQL statements to be input by the user. Read the comments at the beginning for details of the program flow.

          ******************************************************************
          * Sample Program 12: Dynamic SQL Method 4 using ANSI Dynamic SQL *
          *                                                                *
          * This program shows the basic steps required to use dynamic     *
          * SQL Method 4 with ANSI Dynamic SQL.  After logging on to       *
          * ORACLE, the program prompts the user for a SQL statement,      *
          * PREPAREs the statement, DECLAREs a cursor, checks for any      *
          * bind variables using DESCRIBE INPUT, OPENs the cursor, and     *
          * DESCRIBEs any select-list variables.  If the input SQL         *
          * statement is a query, the program FETCHes each row of data,    *
          * then CLOSEs the cursor.                                        *
          * use option dynamic=ansi when precompiling this sample.         *
          ******************************************************************

           IDENTIFICATION DIVISION.
           PROGRAM-ID.  ANSIDYNSQL4.
           ENVIRONMENT DIVISION.
           DATA DIVISION.
           WORKING-STORAGE SECTION.

           01  USERNAME       PIC X(20).
           01  PASSWD         PIC X(20).
           01  BDSC           PIC X(6) VALUE "BNDDSC".
           01  SDSC           PIC X(6) VALUE "SELDSC".
           01  BNDCNT         PIC S9(9) COMP.
           01  SELCNT         PIC S9(9) COMP.
           01  BNDNAME        PIC X(80).
           01  BNDVAL         PIC X(80).
           01  SELNAME        PIC X(80) VARYING.
           01  SELDATA        PIC X(80).
           01  SELTYP         PIC S9(4) COMP.
           01  SELPREC        PIC S9(4) COMP.
           01  SELLEN         PIC S9(4) COMP.
           01  SELIND         PIC S9(4) COMP.
           01  DYN-STATEMENT  PIC X(80).
           01  BND-INDEX      PIC S9(9) COMP.
           01  SEL-INDEX      PIC S9(9) COMP.
           01  VARCHAR2-TYP   PIC S9(4) COMP VALUE 1.
           01  VAR-COUNT      PIC 9(2).
           01  ROW-COUNT      PIC 9(4).
           01  NO-MORE-DATA   PIC X(1) VALUE "N".
           01  TMPLEN         PIC S9(9) COMP.
           01  MAX-LENGTH     PIC S9(9) COMP VALUE 80.

               EXEC SQL INCLUDE SQLCA         END-EXEC.

           PROCEDURE DIVISION.
           START-MAIN.

               EXEC SQL WHENEVER SQLERROR GOTO SQL-ERROR END-EXEC.

               DISPLAY "USERNAME: " WITH NO ADVANCING.
               ACCEPT USERNAME.
               DISPLAY "PASSWORD: " WITH NO ADVANCING.
               ACCEPT PASSWD.
               EXEC SQL CONNECT :USERNAME IDENTIFIED BY :PASSWD END-EXEC.
               DISPLAY "CONNECTED TO ORACLE AS USER: ", USERNAME.

          *    ALLOCATE THE BIND AND SELECT DESCRIPTORS.

               EXEC SQL ALLOCATE DESCRIPTOR :BDSC WITH MAX 20 END-EXEC.
               EXEC SQL ALLOCATE DESCRIPTOR :SDSC WITH MAX 20 END-EXEC.

          *    GET A SQL STATEMENT FROM THE OPERATOR.

               DISPLAY "ENTER SQL STATEMENT WITHOUT TERMINATOR:".
               DISPLAY ">" WITH NO ADVANCING.
               ACCEPT DYN-STATEMENT.
               DISPLAY " ".

          *    PREPARE THE SQL STATEMENT AND DECLARE A CURSOR.

               EXEC SQL  PREPARE S1 FROM :DYN-STATEMENT  END-EXEC.
               EXEC SQL  DECLARE C1 CURSOR FOR S1        END-EXEC.

          *    DESCRIBE BIND VARIABLES.

               EXEC SQL DESCRIBE INPUT S1 USING DESCRIPTOR :BDSC END-EXEC.

               EXEC SQL GET DESCRIPTOR :BDSC :BNDCNT = COUNT END-EXEC.

               IF BNDCNT < 0
                   DISPLAY "TOO MANY BIND VARIABLES."
                   GO TO END-SQL
               ELSE
                   DISPLAY "NUMBER OF BIND VARIABLES: " WITH NO ADVANCING
                   MOVE BNDCNT TO VAR-COUNT
                   DISPLAY VAR-COUNT
          *        EXEC SQL SET DESCRIPTOR :BDSC COUNT = :BNDCNT END-EXEC
               END-IF.

               IF BNDCNT = 0
                   GO TO DESCRIBE-ITEMS.
               PERFORM SET-BND-DSC
                       VARYING BND-INDEX FROM 1 BY 1
                       UNTIL BND-INDEX > BNDCNT.

          *    OPEN THE CURSOR AND DESCRIBE THE SELECT-LIST ITEMS.

           DESCRIBE-ITEMS.
               EXEC SQL  OPEN C1 USING DESCRIPTOR :BDSC END-EXEC.

               EXEC SQL  DESCRIBE OUTPUT S1 USING DESCRIPTOR :SDSC  END-EXEC.

               EXEC SQL GET DESCRIPTOR :SDSC :SELCNT = COUNT END-EXEC.

               IF SELCNT < 0
                   DISPLAY "TOO MANY SELECT-LIST ITEMS."
                   GO TO END-SQL
               ELSE
                   DISPLAY "NUMBER OF SELECT-LIST ITEMS: "
                       WITH NO ADVANCING
                   MOVE SELCNT TO VAR-COUNT
                   DISPLAY VAR-COUNT
                   DISPLAY " "
          *        EXEC SQL SET DESCRIPTOR :SDSC COUNT = :SELCNT END-EXEC
               END-IF.

          *    SET THE INPUT DESCRIPTOR

               IF SELCNT > 0
                   PERFORM SET-SEL-DSC
                       VARYING SEL-INDEX FROM 1 BY 1
                       UNTIL SEL-INDEX > SELCNT
                   DISPLAY " ".

          *    FETCH EACH ROW AND PRINT EACH SELECT-LIST VALUE.

               IF SELCNT > 0
                   PERFORM FETCH-ROWS UNTIL NO-MORE-DATA = "Y".

               DISPLAY " "
               DISPLAY "NUMBER OF ROWS PROCESSED: " WITH NO ADVANCING.
               MOVE SQLERRD(3) TO ROW-COUNT.
               DISPLAY ROW-COUNT.

          *    CLEAN UP AND TERMINATE.

               EXEC SQL CLOSE C1 END-EXEC.
               EXEC SQL DEALLOCATE DESCRIPTOR :BDSC END-EXEC.
               EXEC SQL DEALLOCATE DESCRIPTOR :SDSC END-EXEC.
               EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
               DISPLAY " ".
               DISPLAY "HAVE A GOOD DAY!".
               DISPLAY " ".
               STOP RUN.

          *    DISPLAY ORACLE ERROR MESSAGE AND CODE.

           SQL-ERROR.
               DISPLAY " ".
               DISPLAY SQLERRMC.
           END-SQL.
               EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.
               EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
               STOP RUN.

          *    PERFORMED SUBROUTINES BEGIN HERE:

          *    SET A BIND-LIST ELEMENT'S ATTRIBUTE
          *    LET THE USER FILL IN THE BIND VARIABLES AND
          *    REPLACE THE 0S DESCRIBED INTO THE DATATYPE FIELDS OF THE
          *    BIND DESCRIPTOR WITH 1S TO AVOID AN "INVALID DATATYPE"
          *    ORACLE ERROR
           SET-BND-DSC.
                   EXEC SQL GET DESCRIPTOR :BDSC VALUE
                          :BND-INDEX :BNDNAME = NAME END-EXEC.
                   DISPLAY "ENTER VALUE FOR ", BNDNAME.
                   ACCEPT BNDVAL.
                   EXEC SQL SET DESCRIPTOR :BDSC VALUE :BND-INDEX
                     TYPE = :VARCHAR2-TYP, LENGTH = :MAX-LENGTH,
                     DATA = :BNDVAL END-EXEC.

          * SET A SELECT-LIST ELEMENT'S ATTRIBUTES
           SET-SEL-DSC.
               MOVE SPACES TO SELNAME-ARR.
               EXEC SQL GET DESCRIPTOR :SDSC VALUE :SEL-INDEX
                     :SELNAME = NAME, :SELTYP = TYPE,
                     :SELPREC = PRECISION, :SELLEN = LENGTH END-EXEC.

          *    IF DATATYPE IS DATE, LENGTHEN TO 9 CHARACTERS.
               IF SELTYP = 12
                   MOVE 9 TO SELLEN.

          *    IF DATATYPE IS NUMBER, SET LENGTH TO PRECISION.
               MOVE 0 TO TMPLEN.
               IF SELTYP = 2 AND SELPREC = 0
                   MOVE 40 TO TMPLEN.
               IF SELTYP = 2 AND SELPREC > 0
                   ADD 2 TO SELPREC
                   MOVE SELPREC TO TMPLEN.

               IF SELTYP = 2
                   IF TMPLEN > MAX-LENGTH
                       DISPLAY "COLUMN VALUE TOO LARGE FOR DATA BUFFER."
                       GO TO END-SQL
                   ELSE
                       MOVE TMPLEN TO SELLEN.

          * COERCE DATATYPES TO VARCHAR2.
               MOVE 1 TO SELTYP.

          *    DISPLAY COLUMN HEADING.
               DISPLAY "  ", SELNAME-ARR(1:SELLEN) WITH NO ADVANCING.

               EXEC SQL SET DESCRIPTOR :SDSC VALUE :SEL-INDEX
                  TYPE = :SELTYP, LENGTH = :SELLEN END-EXEC.

          * FETCH A ROW AND PRINT THE SELECT-LIST VALUE.

           FETCH-ROWS.
               EXEC SQL  FETCH C1 INTO DESCRIPTOR :SDSC END-EXEC.
               IF SQLCODE NOT = 0
                   MOVE "Y" TO NO-MORE-DATA.
               IF SQLCODE = 0
                   PERFORM PRINT-COLUMN-VALUES
                       VARYING SEL-INDEX FROM 1 BY 1
                       UNTIL SEL-INDEX > SELCNT
                   DISPLAY " ".

          * PRINT A SELECT-LIST VALUE.

           PRINT-COLUMN-VALUES.
               MOVE SPACES TO SELDATA.
          *    returned length is not set for blank padded types
               IF SELTYP EQUALS 1
                  EXEC SQL GET DESCRIPTOR :SDSC VALUE :SEL-INDEX
                    :SELDATA = DATA, :SELIND = INDICATOR,
                    :SELLEN = LENGTH END-EXEC
               ELSE
                  EXEC SQL GET DESCRIPTOR :SDSC VALUE :SEL-INDEX
                     :SELDATA = DATA, :SELIND = INDICATOR,
                     :SELLEN = RETURNED_LENGTH END-EXEC.
               IF (SELIND = -1)
                  move "  NULL" to SELDATA.

               DISPLAY SELDATA(1:SELLEN), "  "
                     WITH NO ADVANCING.
