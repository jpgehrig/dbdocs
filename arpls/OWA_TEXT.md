## 233  OWA_TEXT

The `OWA_TEXT` package contains subprograms used by `OWA_PATTERN` for manipulating strings. They are externalized so you can use them directly.

**See Also:**

For more information about implementation of this package:

- [Oracle Fusion Middleware Administrator's Guide for Oracle HTTP Server](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=HSADM)

- [Oracle Fusion Middleware User's Guide for mod_plsql](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=YPMOD)

The chapter contains the following topics:

- Types

- Summary of OWA_TEXT Subprograms

### 233.1 OWA_OPT_LOCK Types

There are three OWA_OPT_LOCK lock types.

- MULTI_LINE DATA TYPE

- ROW_LIST DATA TYPE

- VC_ARR DATA TYPE

#### 233.1.1 MULTI_LINE DATA TYPE

This datatype is a PL/SQL record that holds large amounts of text. The rows field, of type `OWA_TEXT`.`VC_ARR` `DATA` `TYPE`, contains the text data in the record.

    TYPE multi_line IS RECORD (
       rows           vc_arr,
       num_rows       INTEGER,
       partial_row    BOOLEAN);

#### 233.1.2 ROW_LIST DATA TYPE

This is the datatype for holding data to be processed.

    TYPE row_list IS RECORD (
       rows           int_arr,
       num_rows       INTEGER);

    int_arr IS DEFINED AS:

    TYPE int_arr IS TABLE OF INTEGER INDEX BY BINARY_INTEGER;

#### 233.1.3 VC_ARR DATA TYPE

This is a component of the MULTI_LINE DATA TYPE and is used for holding large amounts of text.

    TYPE vc_arr IS TABLE OF VARCHAR2(32767) INDEX BY BINARY_INTEGER;

**Related Topics**

- MULTI_LINE DATA TYPE

### 233.2 Summary of OWA_TEXT Subprograms

This table lists the `OWA_TEXT` subprograms and briefly describes them.

Table 233-1 OWA_TEXT Package Subprograms

| Subprogram                          | Description                                |
|:------------------------------------|:-------------------------------------------|
| ADD2MULTI Procedure                 | Adds text to an existing `multi_line` type |
| NEW_ROW_LIST Function and Procedure | Creates a new `row_list`                   |
| PRINT_MULTI Procedure               | Prints out the contents of a `multi_list`  |
| PRINT_ROW_LIST Procedure            | Prints out the contents of a `row_list`    |
| STREAM2MULTI Procedure              | Converts a varchar2 to a `multi_line` type |

#### 233.2.1 ADD2MULTI Procedure

This procedure adds content to an existing Multi_Line Data Type

##### Syntax

    OWA_TEXT.ADD2MULTI(
       stream         IN       VARCHAR2,
       mline          IN OUT   multi_line,

   continue       IN       BOOLEAN   DEFAULT TRUE);

##### Parameters

Table 233-2 ADD2MULTI Procedure Parameters

| Parameter  | Description                                                                                                                                                 |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `stream`   | The text to add.                                                                                                                                            |
| `mline`    | The `OWA_TEXT.MULTI_LINE DATA TYPE`. The output of this parameter contains stream.                                                                          |
| `continue` | If `TRUE`, the procedure appends stream within the previous final row (assuming it is less than 32K). If `FALSE`, the procedure places stream in a new row. |

#### 233.2.2 NEW_ROW_LIST Function and Procedure

This function or procedure creates a new `OWA_TEX.ROW_LIST DATA TYPE`.

The function version uses no parameters and returns a new empty `row_list`. The procedure version creates the `row_list` datatype as an output parameter.

##### Syntax

    OWA_TEXT.NEW_ROW_LIST
      RETURN ROW_LIST;

    OWA_TEXT.NEW_ROW_LIST(
      rlist    OUT     row_list);

##### Parameters

Table 233-3 NEW_ROW_LIST Procedure Parameters

| Parameter | Description                                                        |
|:----------|:-------------------------------------------------------------------|
| `rlist`   | This is an output parameter containing the new `row_list` datatype |

##### Return Values

The function version returns the new `row_list` datatype.

#### 233.2.3 PRINT_MULTI Procedure

This procedure uses the PRINT Procedures or the PRN Procedures to print the "rows" field of the `OWA_TEXT`.`MULTI_LINE` `DATA` `TYPE`.

##### Syntax

    OWA_TEXT.PRINT_MULTI(
       mline       IN       multi_line);

##### Parameters

Table 233-4 PRINT_MULTI` `Procedure Parameters

| Parameter | Description                       |
|:----------|:----------------------------------|
| `mline`   | The multi_line datatype to print. |

##### Return Values

The contents of the `multi_line`.

**Related Topics**

- [PRINT Procedures](HTP.md)
- [PRN Procedures](HTP.md)

#### 233.2.4 PRINT_ROW_LIST Procedure

This procedure uses the PRINT Procedures or the PRN Procedures to print the "rows" field of the `OWA_TEXT`.`ROW_LIST` `DATA` `TYPE`.

##### Syntax

    OWA_TEXT.PRINT_ROW_LIST(
       rlist       IN       multi_line);

##### Parameters

Table 233-5 PRINT_ROW_LIST Procedure Parameters

| Parameter | Description                     |
|:----------|:--------------------------------|
| `rlist`   | The row_list datatype to print. |

##### Return Values

The contents of the `row_list`.

**Related Topics**

- [PRINT Procedures](HTP.md)
- [PRN Procedures](HTP.md)

#### 233.2.5 STREAM2MULTI Procedure

This procedure converts a string to a `multi_line` datatype.

##### Syntax

    OWA_TEXT.STREAM2MULTI(
       stream         IN       VARCHAR2
       mline          OUT      multi_line);

##### Parameters

Table 233-6 STREAM2MULTI Procedure Parameters

| Parameter | Description                                          |
|:----------|:-----------------------------------------------------|
| `stream`  | The string to convert.                               |
| `mline`   | The stream in `OWA_TEXT.MULTI_LINE DATA TYPE` format |
