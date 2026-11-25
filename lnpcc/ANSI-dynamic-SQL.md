This chapter describes Oracle's implementation of ANSI dynamic SQL (also known as SQL standard dynamic SQL) which should be used for new Method 4 applications. It has enhancements over the older Oracle dynamic SQL Method 4, described in the previous chapter.

The ANSI Method 4 supports all Oracle types, while the older Oracle Method 4 does not support object types, cursor variables, arrays of structs, DML returning clauses, Unicode variables, and LOBs.

In ANSI dynamic SQL, descriptors are internally maintained by Oracle, while in the older Oracle dynamic SQL Method 4, descriptors are defined in the user's Pro\*C/C++ program. In both cases, Method 4 means that your Pro\*C/C++ program accepts or builds SQL statements that contain a varying number of host variables.

This chapter contains the following topics:

- Basics of ANSI Dynamic SQL

- Overview of ANSI SQL Statements

- Oracle Extensions

- ANSI Dynamic SQL Precompiler Options

- Full Syntax of the Dynamic SQL Statements

- Example Programs

### 14.1 Basics of ANSI Dynamic SQL

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

#### 14.1.1 Precompiler Options

Set the micro precompiler option DYNAMIC to ANSI, or set the macro option MODE to ANSI, which causes the default value of DYNAMIC to be ANSI. The other setting of DYNAMIC is ORACLE.

In order to use ANSI type codes, set the precompiler micro option TYPE_CODE to ANSI, or set the macro option MODE to ANSI which makes the default setting of TYPE_CODE to ANSI. To set TYPE_CODE to ANSI, DYNAMIC must also be ANSI.

Oracle's implementation of the ANSI SQL types in Overview of ANSI SQL Statements does not exactly match the ANSI standard. For example, a describe of a column declared as INTEGER will return the code for NUMERIC. As Oracle moves closer to the ANSI standard, small changes in behavior may be required. Use the ANSI types with precompiler option TYPE_CODE set to ANSI if you want your application to be portable across database platforms and as ANSI compliant as possible. Do not use TYPE_CODE set to ANSI if such changes are not acceptable.

### 14.2 Overview of ANSI SQL Statements

Allocate a descriptor area first before using it in a dynamic SQL statement.

The ALLOCATE DESCRIPTOR statement syntax is:

    EXEC SQL ALLOCATE DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
      [WITH MAX {:occurrences | numeric_literal}];

A global descriptor can be used in any module in the program. A local descriptor can be accessed only in the file in which it is allocated. Local is the default.

The descriptor name, `desc_nam,` can be a literal in single quotes or a character value stored in a host variable.

`occurrences` is the maximum number of bind variables or columns that the descriptor can hold. This must be a numeric literal. The default is 100.

When a descriptor is no longer needed, deallocate it to conserve memory. Otherwise, deallocation is done automatically when there are no more active database connections.

The deallocate statement is:

    EXEC SQL DEALLOCATE DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal};

Use the DESCRIBE statement to obtain information on a prepared SQL statement. DESCRIBE INPUT describes bind variables for the dynamic statement that has been prepared. DESCRIBE OUTPUT (the default) can give the number, type, and length of the output columns. The simplified syntax is:

    EXEC SQL DESCRIBE [INPUT | OUTPUT] sql_statement
        USING [SQL] DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal};

If your SQL statement has input and output values, you must allocate two descriptors: one for input and one for output values. If there are no input values, for example:

    SELECT ename, empno FROM emp ;

then the input descriptor is not needed.

Use the SET DESCRIPTOR statement to specify input values for INSERTS, UPDATES, DELETES and the WHERE clauses of SELECT statements. Use SET DESCRIPTOR to set the number of input bind variables (stored in `COUNT`) when you have not done a DESCRIBE into your input descriptor:

    EXEC SQL SET DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
       COUNT = {:kount | numeric_literal};

`kount` can be a host variable or a numeric literal, such as 5. Use a SET DESCRIPTOR statement for each host variable, giving at least the data source of the variable:

    EXEC SQL SET DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
       VALUE item_number DATA = :hv3;

You can also set the type and length of the input host variable:

**Note:**

When TYPE_CODE=ORACLE, if you do not set TYPE and LENGTH, either explicitly using the SET statement or implicitly by doing a DESCRIBE OUTPUT, the precompiler will use values for them derived from the host variable itself. When TYPE_CODE=ANSI, you must set TYPE using the values in Table 14-1. You should also set LENGTH because the ANSI default lengths may not match those of your host variables.

    EXEC SQL SET DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
       VALUE item_number TYPE = :hv1, LENGTH = :hv2, DATA = :hv3;

We use the identifiers` hv1`, `hv2`, and `hv3 `to remind us that the values must be supplied by host variables. item_number is the position of the input variable in the SQL statement.

TYPE is the Type Code selected from the following table, if TYPE_CODE is set to ANSI:

Table 14-1 ANSI SQL Datatypes

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

DATA is the value of the host variable that is to be input

You can also set other input values such as indicator, precision and scale.

The numeric values in the SET DESCRIPTOR statement must be declared as either `int` or `short int`, except for indicator and returned length values which you must declare as `short int`.

For example, in the following example, when you want to retrieve an `empno`, set these values: VALUE = 2, because `empno` is the second output host variable in the dynamic SQL statement. The host variable `empno_typ` is set to 3 (Oracle Type for integer). The length of a host integer, `empno_len`, is set to 4, which is the size of the host variable. The DATA is equated to the host variable `empno_data` which will receive the value from the database table. The code fragment is as follows:

    ...
    char *dyn_statement = "SELECT ename, empno FROM emp
       WHERE deptno = :deptno_number" ;
    int empno_data ;
    int empno_typ = 3 ;
    int empno_len = 4 ;
    ...
    EXEC SQL SET DESCRIPTOR 'out' VALUE 2  TYPE = :empno_typ, LENGTH = :empno_len,
       DATA = :empno_data ;

After setting the input values, execute or open your statement using the input descriptor. If there are output values in your statement, set them before doing a FETCH. If you have performed a DESCRIBE OUTPUT, you may have to test the actual type and length of your host variables. The DESCRIBE execution produces internal types and lengths that differ from your host variable external types and length.

After the FETCH of the output descriptor, use GET DESCRIPTOR to access the returned data. Again we show a simplified syntax with details later in this chapter:

    EXEC SQL GET DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}
       VALUE item_number :hv1 = DATA, :hv2 = INDICATOR, :hv3 = RETURNED_LENGTH ;

`desc_nam` and `item_number` can be literals or host variables. A descriptor name can be a literal such as 'out'. An item number can be a numeric literal such as 2.

`hv1, hv2, and hv3` are host variables. They must be host variables, not literals. Only three are shown in the example.

Use either long, int or short for all numeric values, except for indicator and returned length variables, which must be `short`.

**See Also:**

- [Table 15-2](Oracle-dynamic-SQL-method-4.md) for the Oracle type codes

- "SET DESCRIPTOR" for a complete discussion of all the possible descriptor item names

- Table 14-4 for a list of all possible items of returned data that you can get.

#### 14.2.1 Example Code

The following example demonstrates the use of ANSI Dynamic SQL. It allocates an input descriptor ('in') and an output descriptor ('out') to execute a SELECT statement. Input values are set using the SET DESCRIPTOR statement. The cursor is opened and fetched from and the resulting output values are retrieved using a GET DESCRIPTOR statement.

    ...
    char* dyn_statement = "SELECT ename, empno FROM emp WHERE deptno = :deptno_data" ;
    int deptno_type = 3, deptno_len = 2, deptno_data = 10 ;
    int ename_type = 97, ename_len = 30 ;
    char ename_data[31] ;
    int empno_type = 3, empno_len = 4 ;
    int empno_data ;
    long SQLCODE = 0 ;
    ...
    main ()
    {
    /* Place preliminary code, including connection, here. */
    ...
    EXEC SQL ALLOCATE DESCRIPTOR 'in' ;
    EXEC SQL ALLOCATE DESCRIPTOR 'out' ;
    EXEC SQL PREPARE s FROM :dyn_statement ;
    EXEC SQL DESCRIBE INPUT s USING DESCRIPTOR 'in' ;
    EXEC SQL SET DESCRIPTOR 'in' VALUE 1 TYPE = :deptno_type,
       LENGTH = :deptno_len, DATA = :deptno_data ;
    EXEC SQL DECLARE c CURSOR FOR s ;
    EXEC SQL OPEN c USING DESCRIPTOR 'in' ;
    EXEC SQL DESCRIBE OUTPUT s USING DESCRIPTOR 'out' ;
    EXEC SQL SET DESCRIPTOR 'out' VALUE 1 TYPE = :ename_type,
        LENGTH = :ename_len, DATA = :ename_data ;
    EXEC SQL SET DESCRIPTOR 'out' VALUE 2 TYPE = :empno_type,
        LENGTH = :empno_len, DATA = :empno_data ;

    EXEC SQL WHENEVER NOT FOUND DO BREAK ;
    while (SQLCODE == 0)
    {
       EXEC SQL FETCH c INTO DESCRIPTOR 'out' ;
       EXEC SQL GET DESCRIPTOR 'out' VALUE 1 :ename_data = DATA ;
       EXEC SQL GET DESCRIPTOR 'out' VALUE 2 :empno_data = DATA ;
       printf("\nEname = %s Empno = %s", ename_data, empno_data) ;
    }
    EXEC SQL CLOSE c ;
    EXEC SQL DEALLOCATE DESCRIPTOR 'in' ;
    EXEC SQL DEALLOCATE DESCRIPTOR 'out' ;
    ...
    }

Scrollable cursors can also be used with ANSI Dynamic SQL. In order to use ANSI dynamic SQL with scrollable cursors, we DECLARE the cursor in SCROLL mode. Use the various fetch orientation modes with the FETCH statement to access the result set.

### 14.3 Oracle Extensions

These extensions are described next:

- Reference semantics for data items in SET statements.

- Arrays for bulk operations.

- Support for object types, NCHAR columns, and LOBs.

#### 14.3.1 Reference Semantics

The ANSI standard specifies value semantics. To improve performance, Oracle has extended this standard to include reference semantics.

Value semantics makes a copy of your host variables data. Reference semantics uses the addresses of your host variables, avoiding a copy. Thus, reference semantics can provide performance improvements for large amounts of data.

To help speed up fetches, use the REF keyword before the data clauses:

    EXEC SQL SET DESCRIPTOR 'out' VALUE 1 TYPE = :ename_type,
       LENGTH = :ename_len, REF DATA = :ename_data ;
    EXEC SQL DESCRIPTOR 'out' VALUE 2 TYPE = :empno_type,
       LENGTH = :empno_len, REF DATA = :empno_data ;

Then the host variables receive the results of the retrieves. The GET statement is not needed. The retrieved data is written directly into `ename_data` and `empno_data` after each FETCH.

Use of the REF keyword is allowed only before DATA, INDICATOR and RETURNED_LENGTH items (which can vary with each row fetched) as in this fragment of code:

    int indi, returnLen ;
    ...
    EXEC SQL SET DESCRIPTOR 'out' VALUE 1 TYPE = :ename_type,
       LENGTH = :ename_len, REF DATA = :ename_data,
          REF INDICATOR = :indi, REF RETURNED_LENGTH = :returnLen ;

After each fetch, `returnLen `holds the actual retrieved length of the `ename` field, which is useful for `CHAR` or `VARCHAR2 `data.

`ename_len` will not receive the returned length. It will not be changed by the FETCH statement. Use a DESCRIBE statement, followed by a GET statement to find out the maximum column width before fetching rows of data.

REF keyword is also used for other types of SQL statements than SELECT, to speed them up. With reference semantics, the host variable is used rather than a value copied into the descriptor area. The host variable data at the time of execution of the SQL statement is used, not its data at the time of the SET. Here is an example:

    int x = 1 ;
    EXEC SQL SET DESCRIPTOR 'value' VALUE 1 DATA = :x ;
    EXEC SQL SET DESCRIPTOR 'reference' VALUE 1 REF DATA = :x ;
    x = 2 ;
    EXEC SQL EXECUTE s USING  DESCRIPTOR 'value' ;    /* Will use  x = 1 */
    EXEC SQL EXECUTE s USING DESCRIPTOR 'reference' ; /* Will use x = 2 */

**Related Topics**

- SET DESCRIPTOR

#### 14.3.2 About Using Arrays for Bulk Operations

Oracle extends ANSI dynamic SQL by providing bulk operations. To use bulk operations, use the `FOR` clause with an array size to specify the amount of input data or the number of rows you want to process.

The `FOR` clause is used in the ALLOCATE statement to give the maximum amount of data or number of rows. For example, to use a maximum array size of 100:

    EXEC SQL FOR 100 ALLOCATE DESCRIPTOR 'out' ;

or:

    int array_size = 100 ;
    ...
    EXEC SQL FOR :array_size ALLOCATE DESCRIPTOR 'out' ;

The `FOR `clause is then used in subsequent statements that access the descriptor. In an output descriptor the FETCH statement must have an array size equal to or less than the array size already used in the ALLOCATE statement:

    EXEC SQL FOR 20 FETCH c1 USING DESCRIPTOR 'out' ;

Subsequent GET statements for the same descriptor, that get DATA, INDICATOR, or RETURNED_LENGTH values, must use the same array size as the FETCH statement.

    int val_data[20] ;
    short val_indi[20] ;
    ...
    EXEC SQL FOR 20 GET DESCRIPTOR 'out' VALUE 1 :val_data = DATA,
      :val_indi = INDICATOR ;

However, GET statements that reference other items which do not vary from row to row, such as LENGTH, TYPE and COUNT, must not use the `FOR` clause:

    int cnt, len ;
    ...
    EXEC SQL GET DESCRIPTOR 'out' :cnt = COUNT ;
    EXEC SQL GET DESCRIPTOR 'out' VALUE 1 :len = LENGTH ;

The same holds true for SET statements with reference semantics. SET statements which precede the FETCH and employ reference semantics for DATA, INDICATOR, or RETURNED_LENGTH must have the same array size as the FETCH:

    int ref_data[20] ;
    short ref_indi[20] ;
    ...
    EXEC SQL FOR 20 SET DESCRIPTOR 'out' VALUE 1 REF DATA = :ref_data,
       REF INDICATOR = :ref_indi ;

Similarly, for a descriptor that is used for input, to insert a batch of rows, for instance, the EXECUTE or OPEN statement must use an array size equal to or less than the size used in the ALLOCATE statement. The SET statement, for both value and reference semantics, that accesses DATA, INDICATOR, or RETURNED_LENGTH must use the same array size as in the EXECUTE statement.

The FOR clause is never used on the DEALLOCATE or PREPARE statements.

The following code example illustrates a bulk operation with no output descriptor (there is no output, only input to be inserted into the table `emp`). The value of `COUNT` is 2 (there are two host variables, `ename_arr` and `empno_arr`, in the INSERT statement). The data array `ename_arr` holds three character strings: "Tom", "Dick" and "Harry", in that order. The indicator array `ename_ind` has a value of -1 for the second element; so a NULL will be inserted instead of "Dick". The data array `empno_arr` contains three employee numbers. A DML returning clause could be used to confirm the actual names inserted.

    ...
    char* dyn_statement = "INSERT INTO emp (ename) VALUES (:ename_arr)" ;
    char ename_arr[3][6] = {Tom","Dick","Harry"} ;
    short ename_ind[3] = {0,-1,0} ;
    int ename_len = 6, ename_type = 97, cnt = 2 ;
    int empno_arr[3] = {8001, 8002, 8003} ;
    int empno_len = 4 ;
    int empno_type = 3 ;
    int array_size = 3 ;
    EXEC SQL FOR :array_size ALLOCATE DESCRIPTOR 'in' ;
    EXEC SQL SET DESCRIPTOR 'in' COUNT = :cnt ;
    EXEC SQL SET DESCRIPTOR 'in' VALUE 1 TYPE = :ename_type, LENGTH = :ename_len ;
    EXEC SQL SET DESCRIPTOR 'in' VALUE 2 TYPE = :empno_type, LENGTH = :empno_len ;
    EXEC SQL FOR :array_size SET DESCRIPTOR 'in' VALUE 1
       DATA = :ename_arr, INDICATOR = :ename_ind ;
    EXEC SQL FOR :array_size SET DESCRIPTOR 'in' VALUE 2
       DATA = :empno_arr ;
    EXEC SQL PREPARE s FROM :dyn_statement ;
    EXEC SQL FOR :array_size EXECUTE s USING DESCRIPTOR 'in' ;
    ...

The preceding code will insert these values:

    EMPNO   ENAME
     8001   Tom
     8002
     8003   Harry

**Related Topics**

- [The DML Returning Clause](embedded-SQL.md)
- [About Using the FOR Clause](host-arrays.md)

#### 14.3.3 Support for Arrays of Structs

You must set the HOST_STRIDE_LENGTH to the size of the struct, and the INDICATOR_STRIDE_LENGTH to the size of the indicator struct, and the RETURNED_LENGTH_STRIDE to the size of your returned length struct.

Arrays of structs are supported by ANSI dynamic SQL, but are not supported by the older Oracle dynamic SQL.

#### 14.3.4 Support for Object Types

For the object types that you have defined yourself, use Oracle TYPE equal to 108. For an object type column, use a DESCRIBE statement to obtain USER_DEFINED_TYPE_VERSION, USER_DEFINED_TYPE_NAME, USER_DEFINED_TYPE_NAME_LENGTH, USER_DEFINED_TYPE_SCHEMA, and USER_DEFINED_TYPE_SCHEMA_LENGTH.

If you do not employ the DESCRIBE statement to retrieve these values, you have to set them yourself through the SET DESCRIPTOR statement.

### 14.4 ANSI Dynamic SQL Precompiler Options

The macro option MODE sets ANSI compatibility characteristics and controls a number of functions. It can have the values ANSI or ORACLE. For individual functions there are micro options that override the MODE setting.

The precompiler micro option DYNAMIC specifies the descriptor behavior in dynamic SQL. The precompiler micro option TYPE_CODE specifies whether ANSI or Oracle datatype codes are to be used.

When the macro option MODE is set to ANSI, the micro option DYNAMIC becomes ANSI automatically. When MODE is set to ORACLE, DYNAMIC becomes ORACLE.

DYNAMIC and TYPE_CODE cannot be used inline.

This table describes functionality and how the DYNAMIC setting affects them.

Table 14-2 DYNAMIC Option Settings

| Function                   | DYNAMIC = ANSI                                                               | DYNAMIC = ORACLE                                                                |
|:---------------------------|:-----------------------------------------------------------------------------|:--------------------------------------------------------------------------------|
| Descriptor creation.       | Must use ALLOCATE statement.                                                 | Must use function SQLSQLDAAlloc().                                              |
| Descriptor destruction.    | May use DEALLOCATE statement.                                                | May use function SQLLDAFree().                                                  |
| Retrieving data.           | May use both FETCH and GET statements.                                       | Must use only FETCH statement.                                                  |
| Setting input data.        | May use DESCRIBE INPUT statement. Must use SET statement.                    | Must set descriptor values in code. Must use DESCRIBE BIND VARIABLES statement. |
| Descriptor representation. | Single quoted literal or host identifier which contains the descriptor name. | Host variable, a pointer to SQLDA.                                              |
| Data types available.      | All ANSI types except BIT and all Oracle types.                              | Oracle types except objects, LOBs, arrays of structs and cursor variables.      |

The micro option TYPE_CODE is set by the precompiler to the same setting as the macro option MODE. TYPE_CODE can only equal ANSI if DYNAMIC equals ANSI.

Here is the functionality corresponding to the TYPE_CODE settings:

Table 14-3 TYPE_CODE Option Settings

| Function                                                  | TYPE_CODE = ANSI                                                                                                                       | TYPE_CODE = ORACLE                                                            |
|:----------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------|
| Data type code numbers input and returned in dynamic SQL. | Use ANSI code numbers when ANSI type exists. Otherwise, use the negative of the Oracle code number.<br>Only valid when DYNAMIC = ANSI. | Use Oracle code numbers.<br>May be used regardless of the setting of DYNAMIC. |

**Related Topics**

- [MODE](precompiler-options.md)
- [New Names for SQLLIB Public Functions](advanced-topics.md)

### 14.5 Full Syntax of the Dynamic SQL Statements

See [Embedded SQL Statements and Directives](embedded-SQL-statements-and-directives.md) for more details on all these statements.

#### 14.5.1 ALLOCATE DESCRIPTOR

##### Purpose

Use this statement to allocate a SQL descriptor area. Supply a descriptor and the maximum number of occurrences of host bind items, and an array size. This statement is only for the ANSI dynamic SQL.

##### Syntax

    EXEC SQL [FOR [:]array_size] ALLOCATE DESCRIPTOR [GLOBAL | LOCAL]
       {:desc_nam | string_literal} [WITH MAX occurrences] ;

##### Variables

array_size

This is in an optional clause (it is an Oracle extension) that supports array processing. It tells the precompiler that the descriptor is usable for array processing.

GLOBAL \| LOCAL

The optional scope clause defaults to LOCAL if not entered. A local descriptor can be accessed only in the file in which it is allocated. A global descriptor can be used in any module in the compilation unit.

desc_nam

Descriptor name. Local descriptors must be unique in the module. A runtime error is generated if the descriptor has been allocated, but not deallocated, previously. A global descriptor must be unique for the application, or a runtime error results.

occurrences

The maximum number of host variables possible in the descriptor. It must be an integer constant between 0 and 64K, or an error is returned. Default is 100. The clause is optional. A precompiler error results if it does not conform to these rules.

##### Examples

    EXEC SQL ALLOCATE DESCRIPTOR 'SELDES' WITH MAX 50 ;

    EXEC SQL FOR :batch ALLOCATE DESCRIPTOR GLOBAL :binddes WITH MAX 25 ;

#### 14.5.2 DEALLOCATE DESCRIPTOR

##### Purpose

Use this statement to deallocate a SQL descriptor area that has been previously allocated, to free memory. This statement is only used for the ANSI dynamic SQL.

##### Syntax

    EXEC SQL DEALLOCATE DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal} ;

##### Variable

GLOBAL \| LOCAL

The optional scope clause defaults to LOCAL if not entered. A local descriptor can be accessed only in the file in which it is allocated. A global descriptor can be used in any module in the compilation unit.

desc_nam

A runtime error results when a descriptor with the same name and scope has not been allocated, or has been allocated and deallocated already.

##### Examples

    EXEC SQL DEALLOCATE DESCRIPTOR GLOBAL 'SELDES' ;

    EXEC SQL DEALLOCATE DESCRIPTOR :binddes ;

#### 14.5.3 GET DESCRIPTOR

##### Purpose

Use to obtain information from a SQL descriptor area.

##### Syntax

    EXEC SQL [FOR [:]array_size] GET DESCRIPTOR [GLOBAL | LOCAL]
       {:desc_nam | string_literal}
       { :hv0  = COUNT | VALUE item_number
          :hv1 = item_name1 [ {, :hvN = item_nameN}] } ;

##### Variables

array_size

The `FOR array_size` is an optional Oracle extension. `array_size` has to be equal to the field `array_size` in the FETCH statement.

COUNT

The total number of bind variables.

desc_nam

Descriptor name.

GLOBAL \| LOCAL

The optional scope clause defaults to LOCAL if not entered. A local descriptor can be accessed only in the file in which it is allocated. A global descriptor can be used in any module in the compilation unit.

VALUE item_number

The position of the item in the SQL statement. `item_number` can be a variable or a constant. If` item_number` is greater than `COUNT`, the "no data found" condition is returned. `item_number` must be greater than 0.

hv1 .. hvN

These are host variables to which values are transferred.

item_name1 .. item_nameN

The descriptor item names corresponding to the host variables. The possible ANSI descriptor item names are:

Table 14-4 Definitions of Descriptor Item Names for GET DESCRIPTOR

| Descriptor Item Name    | Meaning                                                                                                 |
|:------------------------|:--------------------------------------------------------------------------------------------------------|
| `TYPE`                  | Use the negative value of Oracle type code if the ANSI datatype is not in the table and TYPE_CODE=ANSI. |
| `LENGTH`                | Length of data in the column: in characters for NCHAR; in bytes otherwise. Set by the DESCRIBE OUTPUT.  |
| `OCTET_LENGTH`          | Length of data in bytes.                                                                                |
| `RETURNED_LENGTH`       | The actual data length after a FETCH.                                                                   |
| `RETURNED_OCTET_LENGTH` | Length of the returned data in bytes.                                                                   |
| `PRECISION`             | The number of digits.                                                                                   |
| `SCALE`                 | For exact numeric types, the number of digits to the right of the decimal point.                        |
| `NULLABLE`              | If 1, the column can have NULL values. If 0,the column cannot have NULL values.                         |
| `INDICATOR`             | The associated indicator value.                                                                         |
| `DATA`                  | The data value.                                                                                         |
| `NAME`                  | Column name.                                                                                            |
| `CHARACTER_SET_NAME`    | Column's character set.                                                                                 |

The Oracle additional descriptor item names are:

Table 14-5 Oracle Extensions to Definitions of Descriptor Item Names for GET DESCRIPTOR

| Descriptor Item Name              | Meaning                                                         |
|:----------------------------------|:----------------------------------------------------------------|
| `NATIONAL_CHARACTER`              | If 2, NCHAR or NVARCHAR2. If 1, character. If 0, non-character. |
| `INTERNAL_LENGTH`                 | The internal length, in bytes.                                  |
| `HOST_STRIDE_LENGTH`              | The size of the host struct in bytes.                           |
| `INDICATOR_STRIDE_LENGTH`         | The size of the indicator struct in bytes.                      |
| `RETURNED_LENGTH_STRIDE`          | The size of the returned-length struct in bytes.                |
| `USER_DEFINED_TYPE_VERSION`       | Used for character representation of object type version.       |
| `USER_DEFINED_TYPE_NAME`          | Name of object type.                                            |
| `USER_DEFINED_TYPE_NAME_LENGTH`   | Length of name of object type.                                  |
| `USER_DEFINED_TYPE_SCHEMA`        | Used for character representation of the object's schema.       |
| `USER_DEFINED_TYPE_SCHEMA_LENGTH` | Length of `USER_DEFINED_TYPE_SCHEMA`.                           |
| `NATIONAL_CHARACTER`              | If 2, NCHAR or NVARCHAR2. If 1, character. If 0, non-character. |

##### Usage Notes

Use the FOR clause in GET DESCRIPTOR statements which contain DATA, INDICATOR, and RETURNED_LENGTH items only.

The internal type is provided by the DESCRIBE OUTPUT statement. For both input and output, you must set the type to be the external type of your host variable.

TYPE is the ANSI SQL Datatype code. Use the negative value of the Oracle type code if the ANSI type is not in the table.

LENGTH contains the column length in characters for fields that have fixed-width National Character Sets. It is in bytes for other character columns. It is set in DESCRIBE OUTPUT.

RETURNED_LENGTH is the actual data length set by the FETCH statement. It is in bytes or characters as described for LENGTH. The fields OCTET_LENGTH and RETURNED_OCTET_LENGTH are the lengths in bytes.

NULLABLE = 1 means that the column can have NULLS; NULLABLE = 0 means it cannot.

CHARACTER_SET_NAME only has meaning for character columns. For other types, it is undefined. The DESCRIBE OUTPUT statement obtains the value.

DATA and INDICATOR are the data value and the indicator status for that column. If data = NULL, but the indicator was not requested, an error is generated at runtime ("DATA EXCEPTION, NULL VALUE, NO INDICATOR PARAMETER").

##### Oracle-Specific Descriptor Item Names

NATIONAL_CHARACTER = 2 if the column is an NCHAR or NVARCHAR2 column. If the column is a character (but not National Character) column, this item is set to 1. If a non-character column, this item becomes 0 after DESCRIBE OUTPUT is executed.

INTERNAL_LENGTH is for compatibility with Oracle dynamic Method 4. It has the same value as the length member of the Oracle SQL descriptor area.

The following three items are not returned by a DESCRIBE OUTPUT statement.

- HOST_STRIDE_LENGTH is the size of the struct of host variables.

- INDICATOR_STRIDE_LENGTH is the size of the struct of indicator variables.

- RETURNED_LENGTH_STRIDE is the size of the struct of returned-length variables

The following items apply only to object types when the precompiler option OBJECTS has been set to YES.

- USER_DEFINED_TYPE_VERSION contains the character representation of the type version.

- USER_DEFINED_TYPE_NAME is the character representation of the name of the type.

- USER_DEFINED_TYPE_NAME_LENGTH is the length of the type name in bytes.

- USER_DEFINED_TYPE_SCHEMA is the character representation of the schema name of the type.

- USER_DEFINED_TYPE_SCHEMA_LENGTH is the length in characters of the type's schema name.

##### Examples

    EXEC SQL GET DESCRIPTOR :binddes :n = COUNT ;

    EXEC SQL GET DESCRIPTOR 'SELDES' VALUE 1 :t = TYPE, :l = LENGTH ;

    EXEC SQL FOR :batch GET DESCRIPTOR LOCAL 'SELDES'
       VALUE :sel_item_no :i = INDICATOR, :v = DATA ;

**See Also:**

- Table 14-1 for the ANSI type codes

- "[Table 15-2](Oracle-dynamic-SQL-method-4.md)" for the Oracle type codes

- [Oracle Dynamic SQL: Method 4](Oracle-dynamic-SQL-method-4.md)

#### 14.5.4 SET DESCRIPTOR

##### Purpose

Use this statement to set information in the descriptor area from host variables. The SET DESCRIPTOR statement supports only host variables for the item names.

##### Syntax

    EXEC SQL [FOR array_size] SET DESCRIPTOR [GLOBAL | LOCAL]
       {:desc_nam | string_literal} {COUNT = :hv0 |
       VALUE item_number
       [REF] item_name1 = :hv1
       [{, [REF] item_nameN = :hvN}]} ;

##### Variables

array_size

This optional Oracle clause permits using arrays when setting the descriptor items DATA, INDICATOR, and RETURNED_LENGTH only. You cannot use other items in a SET DESCRIPTOR that contains the FOR clause. All host variable array sizes must match. Use the same array size for the SET statement that you use for the FETCH statement.

GLOBAL \| LOCAL

The optional scope clause defaults to LOCAL if not entered. A local descriptor can be accessed only in the file in which it is allocated. A global descriptor can be used in any module in the compilation unit.

desc_nam

The descriptor name. It follows the rules in ALLOCATE DESCRIPTOR.

COUNT

The number of bind (input) or define (output) variables.

VALUE item_number

Position in the dynamic SQL statement of a host variable.

hv1 .. hvN

The host variables (not constants) that you set.

item_nameI

In a similar way to the GET DESCRIPTOR syntax `desc_item_name` can take on these values.

Table 14-6 Descriptor Item Names for SET DESCRIPTOR

| Descriptor Item Name | Meaning                                                                       |
|:---------------------|:------------------------------------------------------------------------------|
| `TYPE`               | Use negative value of the Oracle type if there is no corresponding ANSI type. |
| `LENGTH`             | Maximum length of data in the column.                                         |
| `INDICATOR`          | The associated indicator value. Set for reference semantics.                  |
| `DATA`               | Value of the data to be set. Set for reference semantics.                     |
| `CHARACTER_SET_NAME` | Column's character set.                                                       |
| `TYPE`               | Use negative value of the Oracle type if there is no corresponding ANSI type. |

See Table 14-1 for the ANSI type codes and see "[Table 15-2](Oracle-dynamic-SQL-method-4.md)" for the Oracle type codes.

The Oracle extensions to the descriptor item names are:

Table 14-7 Oracle Extensions to Descriptor Item Names for SET DESCRIPTOR

| Descriptor Item Name              | Meaning                                                                                                                        |
|:----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `RETURNED_LENGTH`                 | Length returned after a FETCH. Set if reference semantics is being used.                                                       |
| `NATIONAL_CHARACTER`              | Set to 2 when the input host variable is an NCHAR or NVARCHAR2 type.<br>Set to 0 when the National Character setting is clear. |
| `HOST_STRIDE_LENGTH`              | Size of the host variable struct in bytes.                                                                                     |
| `INDICATOR_STRIDE_LENGTH`         | Size of the indicator variable in bytes.                                                                                       |
| `RETURNED_LENGTH_STRIDE`          | Size of the returned-length struct in bytes.                                                                                   |
| `USER_DEFINED_TYPE_NAME`          | Name of object type.                                                                                                           |
| `USER_DEFINED_TYPE_NAME_LENGTH`   | Length of name of object type.                                                                                                 |
| `USER_DEFINED_TYPE_SCHEMA`        | Used for character representation of the object's schema.                                                                      |
| `USER_DEFINED_TYPE_SCHEMA_LENGTH` | Length of `USER_DEFINED_TYPE_SCHEMA`.                                                                                          |

##### Usage Notes

Reference semantics is another optional Oracle extension that speeds performance. Use the keyword REF before these descriptor items names only: DATA, INDICATOR, RETURNED_LENGTH. When you use the REF keyword you do not need to use a GET statement. Complex data types (object and collection types, arrays of structs, and the DML returning clause) all require the REF form of SET DESCRIPTOR.

If the program reuses DESCRIPTOR for another SQL, the old values of DESCRIPTOR remain.

When REF is used the associated host variable itself is used in the SET. The GET is not needed in this case. The RETURNED_LENGTH can only be set when you use the REF semantics, not the value semantics.

Use the same array size for the SET or GET statements that you use in the FETCH.

Set the NATIONAL_CHAR field to 2 for NCHAR host input values.

Set the NATIONAL_CHARACTER field to 0 when DESCRIPTOR is used for NCHAR host input values in the old SQL.

When setting an object type's characteristics, you must set USER_DEFINED_TYPE_NAME and USER_DEFINED_TYPE_NAME_LENGTH.

If omitted, USER_DEFINED_TYPE_SCHEMA and USER_DEFINED_TYPE_SCHEMA_LENGTH default to the current connection.

Set CHARACTER_SET_NAME to UTF16 for client-side Unicode support. The data will be in UCS2 encoding and the RETURNED_LENGTH is in CHARS.

##### Example

    int bindno = 2 ;
    short indi = -1 ;
    char data = "ignore" ;
    int batch = 1 ;

    EXEC SQL FOR :batch ALLOCATE DESCRIPTOR 'binddes' ;
    EXEC SQL SET DESCRIPTOR GLOBAL :binddes COUNT = 3 ;
    EXEC SQL FOR :batch SET DESCRIPTOR :bindes
       VALUE :bindno INDICATOR = :indi, DATA = :data ;
    ...

**Related Topics**

- GET DESCRIPTOR
- [The DML Returning Clause](embedded-SQL.md)
- About Using Arrays for Bulk Operations

**See Also:**

#### 14.5.5 Use of PREPARE

##### Purpose

The PREPARE statement used in this method is the same as the PREPARE statement used in the other dynamic SQL methods. An Oracle extension allows a quoted string for the SQL statement, as well as a variable.

##### Syntax

    EXEC SQL PREPARE statement_id FROM :sql_statement ;

##### Variables

statement_id

This must not be declared; it is a undeclared SQL identifier.

sql_statement

A character string (a constant or a variable) holding the embedded SQL statement.

##### Example

    char* statement = "SELECT ENAME FROM emp WHERE deptno = :d" ;
    EXEC SQL PREPARE S1 FROM :statement ;

#### 14.5.6 DESCRIBE INPUT

##### Purpose

This statement returns information about the bind variables.

##### Syntax

    EXEC SQL DESCRIBE INPUT statement_id USING [SQL] DESCRIPTOR
       [GLOBAL | LOCAL] {:desc_nam | string_literal} ;

##### Variables

statement_id

The same as used in PREPARE and DESCRIBE OUTPUT. This must not be declared; it is an undeclared SQL identifier.

GLOBAL \| LOCAL

The optional scope clause defaults to LOCAL if not entered. A local descriptor can be accessed only in the file in which it is allocated. A global descriptor can be used in any module in the compilation unit.

desc_nam

The descriptor name.

##### Usage Notes

DESCRIBE INPUT only sets COUNT and NAME items.

##### Examples

    EXEC SQL DESCRIBE INPUT S1 USING SQL DESCRIPTOR GLOBAL :binddes ;
    EXEC SQL DESCRIBE INPUT S2 USING DESCRIPTOR 'input' ;

#### 14.5.7 DESCRIBE OUTPUT

##### Purpose

Use this statement to obtain information about the output columns in a PREPAREd statement. The ANSI syntax differs from the older Oracle syntax. The information which is stored in the SQL descriptor area is the number of values returned and associated information such as type, length, and name.

##### Syntax

    EXEC SQL DESCRIBE [OUTPUT] statement_id USING [SQL] DESCRIPTOR
       [GLOBAL | LOCAL] {:desc_nam | string_literal} ;

##### Variables

statement_id

The same as used in PREPARE. This must not be declared; it is an undeclared SQL identifier.

GLOBAL \| LOCAL

The optional scope clause defaults to LOCAL if not entered. A local descriptor can be accessed only in the file in which it is allocated. A global descriptor can be used in any module in the compilation unit.

desc_nam

The descriptor name.

OUTPUT is the default and can be omitted.

##### Examples

    char* desname = "SELDES" ;
    EXEC SQL DESCRIBE S1 USING SQL DESCRIPTOR 'SELDES' ; /* Or, */
    EXEC SQL DESCRIBE OUTPUT S1 USING DESCRIPTOR :desname ;

#### 14.5.8 EXECUTE

##### Purpose

EXECUTE matches input and output variables in a prepared SQL statement and then executes the statement. This ANSI version of EXECUTE differs from the older EXECUTE statement by allowing two descriptors in one statement to support DML returning clause.

##### Syntax

    EXEC SQL [FOR :array_size] EXECUTE statement_id
        [USING [SQL] DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}]
            [INTO [SQL] DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam | string_literal}] ;

##### Variables

array_size

The number of rows the statement will process.

statement_id

The same as used in PREPARE. This must not be declared; it is an undeclared SQL identifier. It can be a literal.

GLOBAL \| LOCAL

The optional scope clause defaults to LOCAL if not entered. A local descriptor can be accessed only in the file in which it is allocated. A global descriptor can be used in any module in the compilation unit.

desc_nam

The descriptor name.

##### Usage Notes

The INTO clause implements the DML returning clause for INSERT, UPDATE and DELETE.

##### Examples

    EXEC SQL EXECUTE S1 USING SQL DESCRIPTOR GLOBAL :binddes ;

    EXEC SQL EXECUTE S2 USING DESCRIPTOR :bv1 INTO DESCRIPTOR 'SELDES' ;

**Related Topics**

- [The DML Returning Clause](embedded-SQL.md)

#### 14.5.9 Use of EXECUTE IMMEDIATE

##### Purpose

Executes a literal or host variable character string containing the SQL statement.The ANSI SQL form of this statement is the same as in the older Oracle dynamic SQL:

##### Syntax

    EXEC SQL EXECUTE IMMEDIATE {:sql_statement | string_literal}

##### Variable

sql_statement

The SQL statement or PL/SQL block in a character string.

##### Example

    EXEC SQL EXECUTE IMMEDIATE :statement ;

#### 14.5.10 Use of DYNAMIC DECLARE CURSOR

##### Purpose

Declares a cursor that is associated with a statement which is a query. This is a form of the generic Declare Cursor statement.

##### Syntax

    EXEC SQL DECLARE cursor_name CURSOR FOR statement_id;

##### Variables

cursor_name

A cursor variable (a SQL identifier, not a host variable).

statement_id

An undeclared SQL identifier.

##### Example

    EXEC SQL DECLARE C1 CURSOR FOR S1 ;

#### 14.5.11 OPEN Cursor

##### Purpose

The OPEN statement associates input parameters with a cursor and then opens the cursor.

##### Syntax

    EXEC SQL [FOR :array_size] OPEN dyn_cursor
        [[USING [SQL] DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam1 | string_literal}]
        [INTO [SQL] DESCRIPTOR [GLOBAL | LOCAL] {:desc_nam2 | string_literal}]] ;

##### Variables

array_size

This limit is less than or equal to number specified when the descriptor was allocated.

dyn_cursor

The cursor variable.

GLOBAL \| LOCAL

The optional scope clause defaults to LOCAL if not entered. A local descriptor can be accessed only in the file in which it is allocated. A global descriptor can be used in any module in the compilation unit.

desc_nam

The descriptor name.

##### Usage Notes

If the prepared statement associated with the cursor contains colons or question marks, a USING clause must be specified, or an error results at runtime. The DML returning clause is supported.

##### Examples

    EXEC SQL OPEN C1 USING SQL DESCRIPTOR :binddes ;

    EXEC SQL FOR :limit OPEN C2 USING DESCRIPTOR :b1, :b2
       INTO SQL DESCRIPTOR :seldes ;

**Related Topics**

- [The DML Returning Clause](embedded-SQL.md)

#### 14.5.12 FETCH

##### Purpose

Fetches a row for a cursor declared with a dynamic DECLARE statement.

##### Syntax

    EXEC SQL [FOR :array_size] FETCH cursor INTO [SQL] DESCRIPTOR
       [GLOBAL | LOCAL] {:desc_nam | string_literal} ;

##### Variables

array_size

The number of rows the statement will process.

cursor

The dynamic cursor that was previously declared.

GLOBAL \| LOCAL

The optional scope clause defaults to LOCAL if not entered. A local descriptor can be accessed only in the file in which it is allocated. A global descriptor can be used in any module in the compilation unit.

desc_nam

Descriptor name.

##### Usage Notes

The optional `array_size `in the FOR clause must be less than or equal to the number specified in the ALLOCATE DESCRIPTOR statement.

##### Examples

    EXEC SQL FETCH FROM C1 INTO DESCRIPTOR 'SELDES' ;

    EXEC SQL FOR :arsz FETCH C2 INTO DESCRIPTOR :desc ;

#### 14.5.13 CLOSE a Dynamic Cursor

##### Purpose

Closes a dynamic cursor. Syntax has not changed from the older Oracle Method 4:

##### Syntax

    EXEC SQL CLOSE cursor ;

##### Variable

cursor

The dynamic cursor that was previously declared.

##### Example

    EXEC SQL CLOSE C1 ;

#### 14.5.14 Differences From Oracle Dynamic Method 4

The ANSI dynamic SQL interface supports all the datatypes supported by the Oracle dynamic Method 4, with these additions:

- All datatypes, including object types, result sets, and LOB types are supported by ANSI Dynamic SQL.

- The ANSI mode uses an internal SQL descriptor area which is an expansion of the external SQLDA used in Oracle older dynamic Method 4 to store its input and output information.

- New embedded SQL statements are introduced: ALLOCATE DESCRIPTOR, DEALLOCATE DESCRIPTOR, DESCRIBE, GET DESCRIPTOR, and SET DESCRIPTOR.

- The DESCRIBE statement does not return the names of indicator variables in ANSI Dynamic SQL.

- ANSI Dynamic SQL does not allow you to specify the maximum size of the returned column name or expression. The default size is set at 128.

- The descriptor name must be either an identifier in single-quotes or a host variable preceded by a colon.

- For output, the optional SELECT LIST FOR clause in the DESCRIBE is replaced by the optional keyword OUTPUT. The INTO clause is replaced by the USING DESCRIPTOR clause, which can contain the optional keyword SQL.

- For input, the optional BIND VARIABLES FOR clause of the DESCRIBE can be replaced by the keyword INPUT. The INTO clause is replaced by the USING DESCRIPTOR clause, which can contain the optional keyword SQL.

- The optional keyword SQL can come before the keyword DESCRIPTOR in the USING clause of the EXECUTE, FETCH and OPEN statements.

#### 14.5.15 Restrictions (ANSI Dynamic SQL)

Restrictions in effect on ANSI dynamic SQL are:

- You cannot mix ANSI and Oracle dynamic SQL methods in the same module.

- The precompiler option DYNAMIC must be set to ANSI. The precompiler option TYPE_CODE can be set to ANSI only if DYNAMIC is set to ANSI.

- The SET statement supports only host variables as item names.

### 14.6 Example Programs

The following two programs are in the demo directory.

#### 14.6.1 ansidyn1.pc

This program demonstrates using ANSI Dynamic SQL to process SQL statements which are not known until runtime. It is intended to demonstrate the simplest (though not the most efficient) approach to using ANSI Dynamic SQL. It uses ANSI compatible value semantics and ANSI type codes. ANSI SQLSTATE is used for error numbers. Descriptor names are literals. All input and output is through ANSI varying character type.

The program connects you to ORACLE using your username and password, then prompts you for a SQL statement. Enter legal SQL or PL/SQL statements using regular, not embedded, SQL syntax and terminate each statement with a semicolon. Your statement will be processed. If it is a query, the fetched rows are displayed.

You can enter multiline statements. The limit is 1023 characters. There is a limit on the size of the variables, MAX_VAR_LEN, defined as 255. This program processes up to 40 bind variables and 40 select-list items. DML returning clauses and user defined types are not supported with value semantics.

Precompile the program with mode = ansi, for example:

    proc mode=ansi ansidyn1

Using `mode=ansi` will set dynamic and `type_code` to ansi.

    /*******************************************************************
    ANSI Dynamic Demo 1:  ANSI Dynamic SQL with value semantics,
                                       literal descriptor names
                                       and ANSI type codes

    This program demonstates using ANSI Dynamic SQL to process SQL
    statements which are not known until runtime.  It is intended to
    demonstrate the simplest (though not the most efficient) approach
    to using ANSI Dynamic SQL.  It uses ANSI compatible value semantics
    and ANSI type codes. ANSI Sqlstate is used for error numbers.
    Descriptor names are literals. All input and output is through ANSI the
    varying character type.

    The program connects you to ORACLE using your username and password,
    then prompts you for a SQL statement.  Enter legal SQL or PL/SQL
    statements using regular, not embedded, SQL syntax and terminate each
    statement with a seimcolon.  Your statement will be processed.  If it
    is a query, the fetched rows are displayed.

    You can enter multiline statements.  The limit is 1023 characters.
    There is a limit on the size of the variables, MAX_VAR_LEN, defined as 255.
    This program processes up to 40 bind variables and 40 select-list items.
    DML returning statments and user defined types are not supported with
    value semantics.

    Precompile the program with mode=ansi, for example:

    proc mode=ansi ansidyn1

    Using mode=ansi will set dynamic and type_code to ansi.

    *******************************************************************/

    #include <stdio.h>
    #include <string.h>
    #include <setjmp.h>
    #include <stdlib.h>
    #include <sqlcpr.h>

    #define MAX_OCCURENCES 40
    #define MAX_VAR_LEN    255
    #define MAX_NAME_LEN   31

    #ifndef NULL
    #define NULL  0
    #endif

    /* Prototypes */
    #if defined(__STDC__)
      void sql_error(void);
      int oracle_connect(void);
      int get_dyn_statement(void);
      int process_input(void);
      int process_output(void);
      void help(void);
    #else
      void sql_error(/*_ void _*/);
      int oracle_connect(/*_ void _*/);
      int get_dyn_statement(/* void _*/);
      int process_input(/*_ void _*/);
      int process_output(/*_ void _*/);
      void help(/*_ void _*/);
    #endif

    EXEC SQL INCLUDE sqlca;

    char SQLSTATE[6];

    /* global variables */
    EXEC SQL BEGIN DECLARE SECTION;
     char    dyn_statement[1024];
     char SQLSTATE[6];
    EXEC SQL END DECLARE SECTION;

    /* Define a buffer to hold longjmp state info. */
    jmp_buf jmp_continue;

    /* A global flag for the error routine. */
    int parse_flag = 0;
    /* A global flag to indicate statement is a select */
    int select_found;

    void main()
    {

        /* Connect to the database. */
        if (oracle_connect() != 0)
            exit(1);

        EXEC SQL WHENEVER SQLERROR DO sql_error();

        /* Allocate the input and output descriptors. */
        EXEC SQL ALLOCATE DESCRIPTOR 'input_descriptor';
        EXEC SQL ALLOCATE DESCRIPTOR 'output_descriptor';

        /* Process SQL statements. */
        for (;;)
        {
            (void) setjmp(jmp_continue);

            /* Get the statement.  Break on "exit". */
            if (get_dyn_statement() != 0)
                break;

            /* Prepare the statement and declare a cursor. */
            parse_flag = 1;     /* Set a flag for sql_error(). */
            EXEC SQL PREPARE S FROM :dyn_statement;
            parse_flag = 0;     /* Unset the flag. */

            EXEC SQL DECLARE C CURSOR FOR S;

            /* Call the function that processes the input. */
            if (process_input())
                exit(1);

            /* Open the cursor and execute the statement. */
            EXEC SQL OPEN C USING DESCRIPTOR 'input_descriptor';

            /* Call the function that processes the output. */
            if (process_output())
                exit(1);

            /* Close the cursor. */
            EXEC SQL CLOSE C;

        }   /* end of for(;;) statement-processing loop */

        /* Deallocate the descriptors */
        EXEC SQL DEALLOCATE DESCRIPTOR 'input_descriptor';
        EXEC SQL DEALLOCATE DESCRIPTOR 'output_descriptor';

        EXEC SQL WHENEVER SQLERROR CONTINUE;
        EXEC SQL COMMIT WORK;
        puts("\nHave a good day!\n");

        EXEC SQL WHENEVER SQLERROR DO sql_error();
        return;
    }

    int get_dyn_statement()
    {
        char *cp, linebuf[256];
        int iter, plsql;

        for (plsql = 0, iter = 1; ;)
        {
            if (iter == 1)
            {
                printf("\nSQL> ");
                dyn_statement[0] = '\0';
                select_found = 0;
            }

            fgets(linebuf, sizeof linebuf, stdin);

            cp = strrchr(linebuf, '\n');
            if (cp && cp != linebuf)
                *cp = ' ';
            else if (cp == linebuf)
                continue;

            if ((strncmp(linebuf, "SELECT", 6) == 0) ||
                (strncmp(linebuf, "select", 6) == 0))
            {
                select_found=1;;
            }

            if ((strncmp(linebuf, "EXIT", 4) == 0) ||
                (strncmp(linebuf, "exit", 4) == 0))
            {
                return -1;
            }

            else if (linebuf[0] == '?' ||
                (strncmp(linebuf, "HELP", 4) == 0) ||
                (strncmp(linebuf, "help", 4) == 0))
            {
                help();
                iter = 1;
                continue;
            }

            if (strstr(linebuf, "BEGIN") ||
                (strstr(linebuf, "begin")))
            {
                plsql = 1;
            }

            strcat(dyn_statement, linebuf);

            if ((plsql && (cp = strrchr(dyn_statement, '/'))) ||
                (!plsql && (cp = strrchr(dyn_statement, ';'))))
            {
                *cp = '\0';
                break;
            }
            else
            {
                iter++;
                printf("%3d  ", iter);
            }
        }
        return 0;
    }

    int process_input()
    {
        int i;
        EXEC SQL BEGIN DECLARE SECTION;
          char name[31];
          int  input_count, input_len, occurs, ANSI_varchar_type;
          char input_buf[MAX_VAR_LEN];
        EXEC SQL END DECLARE SECTION;

        EXEC SQL DESCRIBE INPUT S USING DESCRIPTOR 'input_descriptor';
        EXEC SQL GET DESCRIPTOR 'input_descriptor' :input_count = COUNT;

        ANSI_varchar_type=12;
        for (i=0; i < input_count; i++)
        {
            occurs = i +1;                       /* occurence is 1 based */
            EXEC SQL GET DESCRIPTOR 'input_descriptor'
                     VALUE :occurs :name = NAME;
            printf ("\nEnter value for input variable %*.*s:  ", 10,31, name);
            fgets(input_buf, sizeof(input_buf), stdin);
            input_len = strlen(input_buf) - 1;  /* get rid of new line */
            input_buf[input_len] = '\0';        /* null terminate */
            EXEC SQL SET DESCRIPTOR 'input_descriptor'
                     VALUE :occurs TYPE = :ANSI_varchar_type,
                                   LENGTH = :input_len,
                                   DATA = :input_buf;
        }
        return(sqlca.sqlcode);
    }

    int process_output()
    {
       int i, j;
       EXEC SQL BEGIN DECLARE SECTION;
         int output_count, occurs, type, len, col_len;
         short indi;
         char data[MAX_VAR_LEN], name[MAX_NAME_LEN];
       EXEC SQL END DECLARE SECTION;
       if (!select_found)
           return(0);

       EXEC SQL DESCRIBE OUTPUT S USING DESCRIPTOR 'output_descriptor';

       EXEC SQL GET DESCRIPTOR 'output_descriptor' :output_count = COUNT;

       printf ("\n");
       type = 12;            /* ANSI VARYING character type */
       len = MAX_VAR_LEN;    /* use the max allocated length */
       for (i = 0; i < output_count; i++)
        {
            occurs = i + 1;
            EXEC SQL GET DESCRIPTOR 'output_descriptor' VALUE :occurs
                     :name = NAME;
            printf("%-*.*s ", 9,9, name);
            EXEC SQL SET DESCRIPTOR 'output_descriptor' VALUE :occurs
                     TYPE = :type, LENGTH = :len;
        }
        printf("\n");

        /* FETCH each row selected and print the column values. */
        EXEC SQL WHENEVER NOT FOUND GOTO end_select_loop;

        for (;;)
        {
            EXEC SQL FETCH C INTO DESCRIPTOR 'output_descriptor';
            for (i=0; i < output_count; i++)
              {
                occurs = i + 1;
                EXEC SQL GET DESCRIPTOR 'output_descriptor' VALUE :occurs
                     :data = DATA, :indi = INDICATOR;
                if (indi == -1)
                  printf("%-*.*s ", 9,9, "NULL");
                else
                  printf("%-*.*s ", 9,9, data);  /* simplified output formatting */
                              /* truncation will occur, but columns will line up */
              }
             printf ("\n");
        }
    end_select_loop:
        return(0);
    }

    void help()
    {
        puts("\n\nEnter a SQL statement or a PL/SQL block at the SQL> prompt.");
        puts("Statements can be continued over several lines, except");
        puts("within string literals.");
        puts("Terminate a SQL statement with a semicolon.");
        puts("Terminate a PL/SQL block (which can contain embedded semicolons)");
        puts("with a slash (/).");
        puts("Typing \"exit\" (no semicolon needed) exits the program.");
        puts("You typed \"?\" or \"help\" to get this message.\n\n");
    }

    void sql_error()
    {
        /* ORACLE error handler */
        printf("\n\nANSI sqlstate: %s: ", SQLSTATE);
        printf ("\n\n%.70s\n",sqlca.sqlerrm.sqlerrmc);
        if (parse_flag)
            printf
            ("Parse error at character offset %d in SQL statement.\n",
               sqlca.sqlerrd[4]);

        EXEC SQL WHENEVER SQLERROR CONTINUE;
        EXEC SQL ROLLBACK WORK;
        longjmp(jmp_continue, 1);
    }

    int oracle_connect()
    {
        EXEC SQL BEGIN DECLARE SECTION;
            VARCHAR  username[128];
            VARCHAR  password[32];
        EXEC SQL END DECLARE SECTION;

        printf("\nusername: ");
        fgets((char *) username.arr, sizeof username.arr, stdin);
        username.arr[strlen((char *) username.arr)-1] = '\0';
        username.len = (unsigned short)strlen((char *) username.arr);

        printf("password: ");
        fgets((char *) password.arr, sizeof password.arr, stdin);
        password.arr[strlen((char *) password.arr) - 1] = '\0';
        password.len = (unsigned short)strlen((char *) password.arr);

        EXEC SQL WHENEVER SQLERROR GOTO connect_error;

        EXEC SQL CONNECT :username IDENTIFIED BY :password;

        printf("\nConnected to ORACLE as user %s.\n", username.arr);

        return 0;

    connect_error:
        fprintf(stderr, "Cannot connect to ORACLE as user %s\n", username.arr);
        return -1;
    }

#### 14.6.2 ansidyn2.pc

This program demonstrates using ANSI Dynamic SQL to process SQL statements which are not known until runtime. It uses the Oracle extensions for batch processing and reference semantics.

The program connects you to ORACLE using your username and password, then prompts you for a SQL statement. Enter legal SQL or PL/SQL statement using interactive, not embedded, SQL syntax, terminating the statement with a semicolon. Your statement will be processed. If it is a query, the fetched rows are displayed.

You can enter multiline statements. The limit is 1023 characters. There is a limit on the size of the variables, MAX_VAR_LEN, defined as 255. This program processes up to 40 bind variables and 40 select-list items.

Precompile the program with `dynamic = ansi`, for example:

    proc dynamic=ansi ansidyn2

    /*******************************************************************
    ANSI Dynamic Demo 2:  ANSI Dynamic SQL with reference semantics,
                               batch processing and global descriptor
                               names in host variables

    This program demonstates using ANSI Dynamic SQL to process SQL
    statements which are not known until runtime.  It uses the Oracle
    extensions for batch processing and reference semantics.

    The program connects you to ORACLE using your username and password,
    then prompts you for a SQL statement.  Enter legal SQL or PL/SQL
    statement using interactive, not embedded, SQL syntax, terminating the
    statement with a seimcolon.  Your statement will be processed.  If it
    is a query, the fetched rows are displayed.

    If your statement has input bind variables (other than in a where clause),
    the program will ask for an input array size and then allow you to enter
    that number of input values. If your statment has output, the program will
    ask you for an output array size and will do array fetchng using that value.
    It will also output the rows fetched in one batch together, so using a small
    value for the output array size will improve the look of the output.
    For example, connected as scott/tiger, try select empno, ename from emp
    with an output array size of 4;

    You can enter multiline statements.  The limit is 1023 characters.
    There is a limit on the size of the variables, MAX_VAR_LEN, defined as 255.
    This program processes up to 40 bind variables and 40 select-list items.

    Precompile with program with dynamic=ansi, for example:

    proc dynamic=ansi ansidyn2

    *******************************************************************/

    #include <stdio.h>
    #include <string.h>
    #include <setjmp.h>
    #include <stdlib.h>
    #include <sqlcpr.h>

    #define MAX_OCCURENCES  40
    #define MAX_ARRSZ      100
    #define MAX_VAR_LEN    255
    #define MAX_NAME_LEN    31

    #ifndef NULL
    #define NULL  0
    #endif

    /* Prototypes */
    #if defined(__STDC__)
      void sql_error(void);
      int oracle_connect(void);
      int get_dyn_statement(void);
      int process_input(void);
      int process_output(void);
      void rows_processed(void);
      void help(void);
    #else
      void sql_error(/*_ void _*/);
      int oracle_connect(/*_ void _*/);
      int get_dyn_statement(/* void _*/);
      int process_input(/*_ void _*/);
      int process_output(/*_ void _*/);
      void rows_processed(/*_ void _*/);
      void help(/*_ void _*/);
    #endif

    EXEC SQL INCLUDE sqlca;

    /* global variables */
    char    dyn_statement[1024];                      /* statement variable     */
    EXEC SQL VAR dyn_statement IS STRING(1024);

    char  indesc[]="input_descriptor";                /* descriptor names       */
    char outdesc[]="output_descriptor";
    char   input[MAX_OCCURENCES][MAX_ARRSZ][MAX_VAR_LEN +1 ],    /* data areas */
          output[MAX_OCCURENCES][MAX_ARRSZ][MAX_VAR_LEN + 1];

    short outindi[MAX_OCCURENCES][MAX_ARRSZ];        /* output indicators      */
    short *iptr;

    int   in_array_size;     /* size of input batch, that is, number of rows */
    int   out_array_size;    /* size of input batch, that is, number of rows */
    int   max_array_size=MAX_ARRSZ;   /* maximum arrays size used for allocates */

    char *dml_commands[] = {"SELECT", "select", "INSERT", "insert",
                            "UPDATE", "update", "DELETE", "delete"};

    int select_found, cursor_open = 0;

    /* Define a buffer to hold longjmp state info. */
    jmp_buf jmp_continue;

    /* A global flag for the error routine. */
    int parse_flag = 0;

    void main()
    {

        /* Connect to the database. */
        if (oracle_connect() != 0)
            exit(1);

        EXEC SQL WHENEVER SQLERROR DO sql_error();

        /* Allocate the input and output descriptors. */
        EXEC SQL FOR :max_array_size
                 ALLOCATE DESCRIPTOR GLOBAL :indesc;
        EXEC SQL FOR :max_array_size
                 ALLOCATE DESCRIPTOR GLOBAL :outdesc;

        /* Process SQL statements. */
        for (;;)
        {
            (void) setjmp(jmp_continue);

            /* Get the statement.  Break on "exit". */
            if (get_dyn_statement() != 0)
                break;

            /* Prepare the statement and declare a cursor. */
            parse_flag = 1;     /* Set a flag for sql_error(). */
            EXEC SQL PREPARE S FROM :dyn_statement;
            parse_flag = 0;     /* Unset the flag. */

            EXEC SQL DECLARE C CURSOR FOR S;

            /* Call the function that processes the input. */
            if (process_input())
                exit(1);

            /* Open the cursor and execute the statement. */
            EXEC SQL FOR :in_array_size
                OPEN C USING DESCRIPTOR GLOBAL :indesc;
            cursor_open = 1;

            /* Call the function that processes the output. */
            if (process_output())
                exit(1);

            /* Tell user how many rows were processed. */
            rows_processed();

        }   /* end of for(;;) statement-processing loop */


        /* Close the cursor. */
        if (cursor_open)
          EXEC SQL CLOSE C;

        /* Deallocate the descriptors */
        EXEC SQL DEALLOCATE DESCRIPTOR GLOBAL :indesc;
        EXEC SQL DEALLOCATE DESCRIPTOR GLOBAL :outdesc;

        EXEC SQL WHENEVER SQLERROR CONTINUE;
        EXEC SQL COMMIT WORK RELEASE;
        puts("\nHave a good day!\n");

        EXEC SQL WHENEVER SQLERROR DO sql_error();
        return;
    }

    int get_dyn_statement()
    {
        char *cp, linebuf[256];
        int iter, plsql;

        for (plsql = 0, iter = 1; ;)
        {
            if (iter == 1)
            {
                printf("\nSQL> ");
                dyn_statement[0] = '\0';
                select_found = 0;
            }

            fgets(linebuf, sizeof linebuf, stdin);

            cp = strrchr(linebuf, '\n');
            if (cp && cp != linebuf)
                *cp = ' ';
            else if (cp == linebuf)
                continue;

            if ((strncmp(linebuf, "SELECT", 6) == 0) ||
                (strncmp(linebuf, "select", 6) == 0))
            {
                select_found=1;;
            }

            if ((strncmp(linebuf, "EXIT", 4) == 0) ||
                (strncmp(linebuf, "exit", 4) == 0))
            {
                return -1;
            }

            else if (linebuf[0] == '?' ||
                (strncmp(linebuf, "HELP", 4) == 0) ||
                (strncmp(linebuf, "help", 4) == 0))
            {
                help();
                iter = 1;
                continue;
            }

            if (strstr(linebuf, "BEGIN") ||
                (strstr(linebuf, "begin")))
            {
                plsql = 1;
            }

            strcat(dyn_statement, linebuf);

            if ((plsql && (cp = strrchr(dyn_statement, '/'))) ||
                (!plsql && (cp = strrchr(dyn_statement, ';'))))
            {
                *cp = '\0';
                break;
            }
            else
            {
                iter++;
                printf("%3d  ", iter);
            }
        }
        return 0;
    }

    int process_input()
    {
        int i, j;
        char name[31];
        int  input_count, input_len= MAX_VAR_LEN;
        int  occurs, string_type = 5;
        int  string_len;
        char arr_size[3];

        EXEC SQL DESCRIBE INPUT S USING DESCRIPTOR GLOBAL :indesc;
        EXEC SQL GET DESCRIPTOR GLOBAL :indesc :input_count = COUNT;

        if (input_count > 0 && !select_found )
           {     /* get input array size */
              printf ("\nEnter value for input array size (max is %d) :  ",
                               max_array_size);
            fgets(arr_size, 4, stdin);
            in_array_size = atoi(arr_size);
           }
        else
           {
             in_array_size = 1;
           }
        for (i=0; i < input_count; i++)
        {
            occurs = i +1;                       /* occurence is 1 based */
            EXEC SQL GET DESCRIPTOR GLOBAL :indesc
                     VALUE :occurs :name = NAME;

            for (j=0; j < in_array_size; j++)
            {
              if (in_array_size == 1)
                printf ("\nEnter value for input variable %*.*s:  ",10,31, name);
              else
                printf ("\nEnter %d%s value for input variable %*.*s:  ",
                   j +1, ((j==0) ?  "st" :  (j==1) ? "nd" : (j==2) ? "rd" :"th"),
                          10,31, name);
              fgets(input[i][j], sizeof(input[i][j]), stdin);
              string_len = strlen(input[i][j]);
              input[i][j][string_len - 1 ] = '\0';   /* change \n to \0 */
            }
            EXEC SQL SET DESCRIPTOR GLOBAL :indesc
                     VALUE :occurs TYPE = :string_type, LENGTH = :input_len;
            EXEC SQL FOR :in_array_size
                     SET DESCRIPTOR GLOBAL :indesc
                         VALUE :occurs  REF DATA = :input[i];
        }

        return(sqlca.sqlcode);
    }

    int process_output()
    {
       int i, j;
       int output_count, occurs;
       int type, output_len= MAX_VAR_LEN;
       char name[MAX_OCCURENCES][MAX_NAME_LEN];
       int rows_this_fetch=0, cumulative_rows=0;
       char arr_size[3];
       if (!select_found)
          return(0);
       EXEC SQL DESCRIBE OUTPUT S USING DESCRIPTOR GLOBAL :outdesc;

       EXEC SQL GET DESCRIPTOR GLOBAL :outdesc :output_count = COUNT;

       if (output_count > 0 )
          {
            printf ("\nEnter value for output array size (max is %d) :  ",
                           max_array_size);
            fgets(arr_size, 4, stdin);
            out_array_size = atoi(arr_size);
          }
       if (out_array_size < 1)    /* must have at least one */
           out_array_size = 1;

       printf ("\n");

       for (i = 0; i < output_count; i++)
       {
          occurs = i + 1;
          EXEC SQL GET DESCRIPTOR GLOBAL :outdesc VALUE :occurs
                   :type = TYPE, :name[i] = NAME;
          occurs = i + 1;                         /* occurence is one based */
          type = 5;  /* force all data to be null terminated character */
          EXEC SQL SET DESCRIPTOR GLOBAL :outdesc VALUE :occurs
                   TYPE = :type, LENGTH = :output_len;

          iptr = (short *)&outindi[i]; /* no mult-dimension non-char host vars */
          EXEC SQL FOR :out_array_size
                   SET DESCRIPTOR GLOBAL :outdesc VALUE :occurs
                   REF DATA = :output[i], REF INDICATOR = :iptr;
       }



       EXEC SQL WHENEVER NOT FOUND GOTO end_select_loop;

       /* print the column headings */
       for (j=0; j < out_array_size; j++)
          for (i=0; i < output_count; i++)
             printf("%-*.*s ", 9,9, name[i]);
       printf("\n");

       /* FETCH each row selected and print the column values. */
       for (;;)
       {
          EXEC SQL FOR :out_array_size
                  FETCH C INTO DESCRIPTOR GLOBAL :outdesc;
          rows_this_fetch = sqlca.sqlerrd[2] - cumulative_rows;
          cumulative_rows = sqlca.sqlerrd[2];
          if (rows_this_fetch)
          for (j=0; j < out_array_size && j < rows_this_fetch; j++)
          {           /* output by columns using simplified formatting */
             for (i=0; i < output_count; i++)
               {
                    if (outindi[i][j] == -1)
                       printf("%-*.*s ", 9, 9, "NULL");
                   else
                      printf("%-*.*s ", 9, 9, output[i][j]);  /* simplified */
                                  /* output formatting may cause truncation */
                                  /* but columns will line up */
               }
          }
           printf ("\n");
       }

    end_select_loop:
       /* print any unprinted rows */
       rows_this_fetch = sqlca.sqlerrd[2] - cumulative_rows;
       cumulative_rows = sqlca.sqlerrd[2];
       if (rows_this_fetch)
         for (j=0; j < out_array_size && j < rows_this_fetch; j++)
           {           /* output by columns using simplified formatting */
             for (i=0; i < output_count; i++)
               {
                  if (outindi[i][j] == -1)
                       printf("%-*.*s ",9, 9, "NULL");
                   else
                      printf("%-*.*s ", 9, 9, output[i][j]);
                }
            }
       return(0);
    }

    void rows_processed()
    {
       int i;
       for (i = 0; i < 8; i++)
         {
           if (strncmp(dyn_statement, dml_commands[i], 6) == 0)
             {
                printf("\n\n%d row%c processed.\n", sqlca.sqlerrd[2],
                           sqlca.sqlerrd[2] == 1 ? ' ' : 's');
                break;
             }
         }
       return;
    }

    void help()
    {
        puts("\n\nEnter a SQL statement or a PL/SQL block at the SQL> prompt.");
        puts("Statements can be continued over several lines, except");
        puts("within string literals.");
        puts("Terminate a SQL statement with a semicolon.");
        puts("Terminate a PL/SQL block (which can contain embedded semicolons)");
        puts("with a slash (/).");
        puts("Typing \"exit\" (no semicolon needed) exits the program.");
        puts("You typed \"?\" or \"help\" to get this message.\n\n");
    }

    void sql_error()
    {
        /* ORACLE error handler */
        printf ("\n\n%.70s\n",sqlca.sqlerrm.sqlerrmc);
        if (parse_flag)
            printf
            ("Parse error at character offset %d in SQL statement.\n",
               sqlca.sqlerrd[4]);

        EXEC SQL WHENEVER SQLERROR CONTINUE;
        EXEC SQL ROLLBACK WORK;
        longjmp(jmp_continue, 1);
    }

    int oracle_connect()
    {
        EXEC SQL BEGIN DECLARE SECTION;
            VARCHAR  username[128];
            VARCHAR  password[32];
        EXEC SQL END DECLARE SECTION;

        printf("\nusername: ");
        fgets((char *) username.arr, sizeof username.arr, stdin);
        username.arr[strlen((char *) username.arr)-1] = '\0';
        username.len = (unsigned short)strlen((char *) username.arr);

        printf("password: ");
        fgets((char *) password.arr, sizeof password.arr, stdin);
        password.arr[strlen((char *) password.arr) - 1] = '\0';
        password.len = (unsigned short)strlen((char *) password.arr);

        EXEC SQL WHENEVER SQLERROR GOTO connect_error;

        EXEC SQL CONNECT :username IDENTIFIED BY :password;

        printf("\nConnected to ORACLE as user %s.\n", username.arr);

        return 0;

    connect_error:
        fprintf(stderr, "Cannot connect to ORACLE as user %s\n", username.arr);
        return -1;
    }
