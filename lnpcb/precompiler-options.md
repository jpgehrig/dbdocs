This chapter describes the precompiler options of Pro\*COBOL. This chapter includes:

- The procob Command

- Actions During Precompilation

- About the Options

- Entering Precompiler Options

- Scope of Precompiler Options

- Quick Reference

- Using Pro\*COBOL Precompiler Options

### 14.1 The procob Command

The location of Pro\*COBOL differs from system to system. Typically, your system manager or DBA defines environment variables or aliases or uses other operating system-specific means to make the Pro\*COBOL executable accessible.

To run the Oracle Pro\*COBOL Precompiler, you issue the command

    procob [option_name=value] [option_name=value] ...

The option value is always separated from the option name by an equals sign (=), with no white space around the equals sign.

For example, the INAME option specifies the source file to be precompiled. The command:

    procob INAME=test

precompiles the file test.pco in the current directory, since Pro\*COBOL assumes that the filename extension is .pco.

You need not use a file extension when specifying INAME unless the extension is nonstandard.

Input and output filenames need not be accompanied by their respective option names, INAME and ONAME. When the option names are not specified, Pro\*COBOL assumes that the first filename specified on the command line is the input filename and that the second filename is the output filename.

Thus, the command

    procob MODE=ANSI myfile myfile.cob

is equivalent to

    procob MODE=ANSI INAME=myfile.pco ONAME=myfile.cob

#### 14.1.1 Case-Sensitivity

In general, you can use either uppercase or lowercase for command-line option names and values. However, if your operating system is case-sensitive (as in UNIX for example) you must specify filename values, including the name of Pro\*COBOL executable, using the correct combination of upper and lowercase letters.

Note: Option names and option values that do not name specific operating system objects, such as filenames, are not case-sensitive. In the examples in this guide, option names are written in upper case or lower case, and option values are usually in lower case. Filenames, including the name of the Pro\*COBOL executable itself, always follow the case conventions used by the operating system on which it is executed.

With some operating systems and user shells, such as UNIX C shell, the `?` may need to be preceded by an "escape" character, such as a back-slash (\\. For example, instead of `procob ?`, you might need to use `procob \?` to list the Pro\*COBOL option settings.

Consult your platform-specific documentation.

### 14.2 Actions During Precompilation

During precompilation, Pro\*COBOL generates COBOL code that replaces the SQL statements embedded in your host program. The generated code includes data structures that contain the datatype, length, and address of each host variable, as well as other information required by the Oracle runtime library, SQLLIB. The generated code also contains the calls to SQLLIB routines that perform the embedded SQL operations.

Pro\*COBOL can issue warnings and error messages. These messages are described in [Oracle Database Error Messages](../errmg/index.md).

### 14.3 About the Options

Many useful options are available at precompile time. They let you control how resources are used, how errors are reported, how input and output are formatted, and how cursors are managed.

The value of an option is a literal, which represents text or numeric values. For example, for the option

    ... INAME=my_test

the value is a string literal that specifies a filename.

For the option

    ... PREFETCH=100

the value is numeric.

Some options take Boolean values, which you can represent with the strings YES or NO, TRUE or FALSE, or with the integer literals 1 or 0, respectively. For example, the option

    ... SELECT_ERROR=YES

is equivalent to

    ... SELECT_ERROR=TRUE

or

    ... SELECT_ERROR=1

You leave no white space around the equals (=) sign. This is because spaces delimit individual options. For example, you might specify the option AUTO_CONNECT on the command line as follows:

    ... AUTO_CONNECT=YES

You can abbreviate the names of options unless the abbreviation is ambiguous. For example, you cannot use the abbreviation MAX because it might stand for MAXLITERAL or MAXOPENCURSORS.

A handy reference to the Pro\*COBOL options is available online. To see the online display, enter the Pro\*COBOL command, with no arguments, at your operating system prompt:

    procob

The display gives the name, syntax, default value, and purpose of each option. Options marked with an asterisk (\*) can be specified inline as well as on the command line.

#### 14.3.1 Precedence of Option Values

Option values are determined by the following, in order of increasing precedence:

- A default built in to Pro\*COBOL

- A value set in the systemconfiguration file

- A value set in a userconfiguration file

- A value entered in the command line

- A value set in an inline specification

For example, the option MAXOPENCURSORS specifies the maximum number of cached open cursors. The built-in Pro\*COBOL default value for this option is 10. However, if MAXOPENCURSORS=32 is specified in the system configuration file, the value becomes 32. The user configuration file could set it to yet another value, which then overrides the system configuration value.

If the MAXOPNCURSORS option is set on the command line, the new command-line value takes precedence. Finally, an inline specification takes precedence over all preceding defaults. For more information, see “Entering Precompiler Options”.

**Related Topics**

- Entering Precompiler Options

#### 14.3.2 Macro and Micro Options

Option MODE is known as a macro option. Some newer options, such as END_OF_FETCH, control only one function and are known as micro options. When setting a macro and a micro option, you must remember that the macro option has precedence over micro options. This is the case if, and only if, the macro option is at a higher level of precedence than the micro option. (As described in the section “Precedence of Option Values”.) This behavior is a change from releases of Pro\*COBOL prior to 8.0.

For example, the default for MODE is ORACLE, and for END_OF_FETCH is 1403. If you specify MODE=ANSI in the user configuration file, Pro\*COBOL will return a value of 100 at the end of fetch, overriding the default END_OF_FETCH value of 1403. If you specify both MODE=ANSI and END_OF_FETCH=1403 in the configuration file, then 1403 will be returned. If you specify END_OF_FETCH=1403 in your configuration file and MODE=ANSI on the command line, then 100 will be returned.

The following table lists the values of micro options set by the macro option values:

Table 14-1 How Macro Option Values Set Micro Option Values

| Macro Option                            | Micro Option                                                                                        |
|:----------------------------------------|:----------------------------------------------------------------------------------------------------|
| MODE=ANSI \| ISO                        | CLOSE_ON_COMMIT=YES<br>DECLARE_SECTION=YES<br>END_OF_FETCH=100<br>DYNAMIC=ANSI<br>TYPE_CODE=ANSI    |
| MODE=ANSI14 \| ANSI13 \| ISO14 \| ISO13 | CLOSE_ON_COMMIT=NO<br>DECLARE_SECTION=YES<br>END_OF_FETCH=100                                       |
| MODE=ORACLE                             | CLOSE_ON_COMMIT=NO<br>DECLARE_SECTION=NO<br>END_OF_FETCH=1403<br>DYNAMIC=ORACLE<br>TYPE_CODE=ORACLE |

**Related Topics**

- Precedence of Option Values

#### 14.3.3 Determining Current Values

You can interactively determine the current value for one or more options by using a question mark on the command line. For example, if you issue the command

    procob ?

the complete option set, along with current values, is displayed on your terminal. In this case, the values are those built into Pro\*COBOL, overridden by any values in the system configuration file. But if you issue the following command

    procob CONFIG=my_config_file.cfg ?

and there is a file named `my_config_file.cfg` in the current directory, the options from the `my_config_file.cfg` file are listed with the other default values. Values in the user configuration file supply missing values, and they supersede values built into Pro\*COBOL and values specified in the system configuration file.

You can also determine the current value of a single option by simply specifying the option name followed by `=?` as in

    procob MAXOPENCURSORS=?

### 14.4 Entering Precompiler Options

All Pro\*COBOL options (except CONFIG) can be entered on the command line or from a configuration file. Many options can also be entered inline. During a given run, Pro\*COBOL can accept options from all three sources.

#### 14.4.1 On the Command Line

You enter precompiler options on the command line using `... [option_name=value] [option_name=value] ...`

Separate each option with one or more spaces. For example, you might enter the following options:

    ... ERRORS=no LTYPE=short

#### 14.4.2 Inline

Enter options inline by coding EXEC ORACLE OPTION statements, using the following syntax:

         EXEC ORACLE OPTION (option_name=value) END-EXEC.

For example, you might code the following statement:

         EXEC ORACLE OPTION (RELEASE_CURSOR=YES) END-EXEC.

An option entered inline overrides the same option entered on the command line.

##### 14.4.2.1 Advantages

The EXEC ORACLE feature is especially useful for changing option values during precompilation. For example, you might want to change the HOLD_CURSOR and RELEASE_CURSOR values on a statement-by-statement basis. “Performance Tuning” shows you how to use inline options to optimize runtime performance.

Specifying options inline is also helpful if your operating system limits the number of characters you can enter on the command line, and you can store inline options in configuration files. These are discussed in the next section.

**Related Topics**

- [Performance Tuning](performance-tuning.md)

##### 14.4.2.2 Scope of EXEC ORACLE

An EXEC ORACLE statement stays in effect until textually superseded by another EXEC ORACLE statement specifying the same option. In the following example, HOLD_CURSOR=NO stays in effect until superseded by HOLD_CURSOR=YES:

         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
     01  EMP-NAME    PIC X(20) VARYING.
     01  EMP-NUMBER  PIC S9(4) COMP VALUE ZERO.
     01  SALARY      PIC S9(5)V99 COMP-3 VALUE ZERO.
     01  DEPT-NUMBER PIC S9(4) COMP VALUE ZERO.
         EXEC SQL END DECLARE SECTION END-EXEC.
         ...
         EXEC SQL WHENEVER NOT FOUND GOTO NO-MORE END-EXEC.
         ...
         EXEC ORACLE OPTION (HOLD_CURSOR=NO)END-EXEC.
         ...
         EXEC SQL DECLARE emp_cursor CURSOR FOR
    SELECT EMPNO, DEPTNO FROM EMP
         END-EXEC.
         EXEC SQL OPEN emp_cursor END-EXEC.

         DISPLAY 'Employee Number  Dept'.
         DISPLAY '---------------  ----'.
         PERFORM
             EXEC SQL
               FETCH emp_cursor INTO :EMP-NUMBER, :DEPT-NUMBER
             END-EXEC
             DISPLAY EMP-NUMBER, DEPT-NUMBER END-EXEC
         END-PERFORM.

     NO-MORE.
             EXEC SQL WHENEVER NOT FOUND CONTINUE END-EXEC.
         PERFORM
             DISPLAY 'Employee number? '
             ACCEPT EMP-NUMBER
             IF EMP-NUMBER IS NOT = 0
                 EXEC ORACLE OPTION (HOLD_CURSOR=YES) END-EXEC
                 EXEC SQL SELECT ENAME, SAL
                     INTO :EMP-NAME, :SALARY
                     FROM EMP
                     WHERE EMPNO = :EMP-NUMBER
                     DISPLAY 'Salary for ', EMP-NAME, ' is ', SALARY
                 END-EXEC
             END-IF
         END-PERFORM.
      NEXT-PARA.
         ...

#### 14.4.3 Configuration Files

A configuration file is a text file that contains precompiler options. Each record (line) in the file contains one option, with its associated value or values. For example, a configuration file might contain the lines

    FIPS=YES
    MODE=ANSI

to set values for the FIPS and MODE options.

There is a single system configuration file for each system. The name of the system configuration file is

    pcbcfg.cfg

The location of the file is operating system-specific. On most UNIX systems, the Pro\*COBOL configuration file is usually located in the \$ORACLE_HOME/precomp/admin directory, where \$ORACLE_HOME is the environment variable for the database software.

Note that before release 8.0 of Pro\*COBOL, the configuration file was called pccob.cfg.

The Pro\*COBOL user can have one or more user configuration files. The name of the configuration file must be specified using the CONFIG command-line option. For more information, see “Determining Current Values”.

Note: You cannot nest configuration files. This means that CONFIG is not a valid option inside a configuration file.

**Related Topics**

- Determining Current Values

#### 14.4.4 Column Properties Support

Column properties are returned in an 8 byte value where each bit indicates a column property. Three column properties are supported:

      +---------------------------------------------------+
      ! 32 |..............| 10 | 9 | 8 |......| 3 | 2 | 1 |
      +---------------------------------------------------+
                                               |    |   |
                                               |    |   |-> auto-increment column
                                               |    |-> auto value always generated
                                               |-> if generated by default when null

You can get the Column Properties through dynamic statements using the new SQLDA member (`sqlda->CP[]`).

    01  SELDSC.
         02  SQLDNUM             PIC S9(9) COMP VALUE 20.
         02  SQLDFND             PIC S9(9) COMP.
         02  SELDVAR             OCCURS 20 TIMES.
             03 SELDV            PIC S9(9) COMP.
             03 SELDFMT          PIC S9(9) COMP.
             03 SELDVLN          PIC S9(9) COMP.
             03 SELDFMTL         PIC S9(4) COMP.
             03 SELDVTYP         PIC S9(4) COMP.
             03 SELDI            PIC S9(9) COMP.
             03 SELDH-VNAME      PIC S9(9) COMP.
             03 SELDH-MAX-VNAMEL PIC S9(4) COMP.
             03 SELDH-CUR-VNAMEL PIC S9(4) COMP.
             03 SELDI-VNAME      PIC S9(9) COMP.
             03 SELDI-MAX-VNAMEL PIC S9(4) COMP.
             03 SELDI-CUR-VNAMEL PIC S9(4) COMP.
             03 SELDFCLP         PIC S9(9) COMP.
             03 SELDFCRCP        PIC S9(9) COMP.
         02  SQLDSCCP            OCCURS 20 TIMES PIC S9(18) COMP-5.

This member `SQLDSCCP` is updated as part of a meta data DESCRIBE.

You can get the Column Properties through static statements using the new function `SQLGetColProp()` which gets the column properties from the last executed statement.

    void SQLGetColProp(
       void  *uga,    --> IN -- run time context
       text *coln,    --> IN -- column name
       ub2  *colatr,  --> IN -- column attributes
       ub8  *colprop  --> IN/OUT -- column attribute/ub8 value that holds column properties
                       )

`SQLGetColProp()` returns values determined by the column attribute `colatr`.

- SQL_ATTR_COL_PROPERTIES: Returns an 8 byte value (`colprop`) containing the column properties of the named column

- SQL_ATTR_COL_PROPERTY_IS_IDENTITY `colprop` is true if the named column is an identity column

- SQL_ATTR_COL_PROPERTY_IS_GEN_ALWAYS `colprop` is true if the named column always generates an auto increment value

- SQL_ATTR_COL_PROPERTY_IS_GEN_BY_DEF_ON_NULL `colprop` is true if the named column generates an auto increment value in the case of a default-null column constraint.

### 14.5 Scope of Precompiler Options

A precompilation unit is a file containing COBOL code and one or more embedded SQL statements. The options specified for a given precompilation unit affect only that unit; they have no effect on other units.

For example, if you specify HOLD_CURSOR=YES and RELEASE_CURSOR=YES for unit A but not unit B, SQL statements in unit A run with these HOLD_CURSOR and RELEASE_CURSOR values, but SQL statements in unit B run with the default values. However, the MAXOPENCURSORS setting that is in effect when you connect to Oracle stays in effect for the life of that connection.

The scope of an inline option is positional, not logical. That is, an inline option affects SQL statements that follow it in the source file, not in the flow of program logic. An option setting stays in effect until the end-of-file unless you re-specify the option.

### 14.6 Quick Reference

The following table is a quick reference to the Pro\*COBOL options. Options marked with an asterisk can be entered inline.

Another handy reference is available online. To see the online display, just enter the Pro\*COBOL command without options at your operating system prompt. The display gives the name, syntax, default value, and purpose of each option.

**Note:**

There are some platform-specific options. For example, on byte-swapped platforms the option COMP5 governs the use of certain COMPUTATIONAL items. Check your system-specific Oracle manuals.

COMP5 is not supported on SPARC Solaris 64 bit Computers. Use COMP instead.

Added CWH_SQL99 option for feature 25546?

Table 14-2 Option List

| Syntax                                   | Default   | Specifies                                                                                |
|:-----------------------------------------|:----------|:-----------------------------------------------------------------------------------------|
| ASACC={YES \| NO}                        | NO        | If YES, use ASA carriage control for listing.                                            |
| ASSUME_SQLCODE={YES \| NO}               | NO        | If YES, assume SQLCODE variable exists.                                                  |
| AUTO_CONNECT={YES \| NO}                 | NO        | If YES, allow automatic connect to ops\$ accounts before the first executable statement. |
| CLOSE_ON_COMMIT\*                        | NO        | If YES, close all cursors on COMMIT.                                                     |
| CONFIG=filename                          | (none)    | Specifies name of user-defined configuration file.                                       |
| CWH_SQL99={YES \| NO}                    | YES       | If YES, close held cursors on ROLLBACK (SQL standard behavior.)                          |
| DATE_FORMAT                              | LOCAL     | Specifies date string format.                                                            |
| DBMS={NATIVE \| V7 \| V8}                | NATIVE    | Version-specific behavior of Oracle at precompile time.                                  |
| DECLARE_SECTION                          | NO        | If YES, DECLARE SECTION is required.                                                     |
| DEFINE=symbol \*                         | (none)    | Define a symbol used in conditional precompilation.                                      |
| DYNAMIC                                  | ORACLE    | Specifies Oracle or ANSI dynamic semantics in SQL Method 4.                              |
| END_OF_FETCH                             | 1403      | End-of-fetch SQLCODE value.                                                              |
| ERRORS={YES \| NO} \*                    | YES       | If YES, display errors on the terminal.                                                  |
| FIPS={YES \| NO}                         | NO        | If YES, ANSI/ISO extensions are flagged.                                                 |
| FORMAT={ANSI \| TERMINAL \| VARIABLE}    | ANSI      | Format of input file COBOL statements.                                                   |
| HOLD_CURSOR={YES \| NO}\*                | NO        | If YES, hold OraCursor (do not re-assign).                                               |
| HOST={COBOL \| COB74}                    | COBOL     | COBOL version used in input file (COBOL 85 or COBOL 74).                                 |
| \[INAME=\]filename                       | (none)    | Name of input file.                                                                      |
| INCLUDE=path\*                           | (none)    | Pathname for EXEC SQL INCLUDE files.                                                     |
| IRECLEN=integer                          | 80        | Record length of input file.                                                             |
| LITDELIM={APOST \| QUOTE}                | QUOTE     | Delimiters for COBOL strings.                                                            |
| LNAME=filename                           | (none)    | Name of listing file.                                                                    |
| LRECLEN=integer                          | 132       | Record length of listing file.                                                           |
| LTYPE={LONG \| SHORT \| NONE} \*         | LONG      | Type of listing.                                                                         |
| MAXLITERAL=integer \*                    | 256       | Maximum length of strings. (120 on IBM-proprietary S370 OS)                              |
| MAXOPENCURSORS=integer \*                | 10        | Maximum number of OraCursors cached (1).                                                 |
| MODE={ORACLE \| ANSI}                    | ORACLE    | If ANSI, follow the ANSI/ISO SQL standard.                                               |
| NESTED={YES \| NO}                       | YES       | If YES, nested programs are supported.                                                   |
| NLS_LOCAL={YES \| NO}                    | NO        | If YES, use NCHAR semantics of previous Pro\*COBOL releases.                             |
| \[ONAME=\]filename                       | iname.cob | Name of output file.                                                                     |
| ORACA={YES \| NO}\*                      | NO        | If YES, use ORACA communications area.                                                   |
| ORECLEN=integer                          | 80        | Record length of output file.                                                            |
| PAGELEN=integer                          | 66        | Lines for each page in listing.                                                          |
| PICX                                     | CHARF     | Datatype of PIC X COBOL variables.                                                       |
| PLAN_BASELINE={module_name \| YES \| NO} | NO        | Specify a module name to create a SQL Plan Baseline.                                     |
| PLAN_PREFIX={prefix_name\| none}         | none      | Ensures that the plan name does not exceed 128 bytes.                                    |
| PLAN_RUN={YES \| NO}                     | NO        | Executes the generated SQL file                                                          |
| PLAN_FIXED={YES \| NO}                   | YES       | Specifies whether or not the created plan baseline is fixed or non-fixed                 |
| PLAN_ENABLED={YES \| NO}                 | YES       | Enables the Plan Baseline that is created.                                               |
| MEMFORPREFETCH=0..4294967294             | none      | Speed up queries by pre-fetching rows that fill the specified memory.                    |
| PREFETCH                                 | 1         | Speed up queries by pre-fetching a given number of rows.                                 |
| RELEASE_CURSOR={YES \| NO} \*            | NO        | If YES, release OraCursor after execute.                                                 |
| SELECT_ERROR={YES \| NO}\*               | YES       | If YES, generate FOUND error on SELECT.                                                  |
| SQLCHECK={SEMANTICS \| SYNTAX}\*         | SYNTAX    | SQL checking level.                                                                      |
| THREADS={YES \| NO}                      | NO        | Indicates a multithreaded application.                                                   |
| TYPE_CODE                                | ORACLE    | Use Oracle or ANSI type codes for dynamic SQL method 4.                                  |
| UNSAFE_NULL={YES \| NO}                  | NO        | If YES, unsafe null fetches are allowed (disables the ORA-01405 message).                |
| USERID=username/password\[@dbname\]      | (none)    | Oracle username, password, and optional database.                                        |
| VARCHAR={YES \| NO}                      | NO        | If YES, accept user-defined VARCHAR group items.                                         |
| XREF={YES \| NO}\*                       | YES       | If YES, generate symbol cross references in listing.                                     |

### 14.7 Using Pro\*COBOL Precompiler Options

This section is organized for easy reference. It lists the Pro\*COBOL precompiler options alphabetically and for each option gives its purpose, syntax, and default value. Usage notes that help you understand how the option works are also provided. Unless the usage notes say otherwise, the option can be entered on the command line, inline, or from a configuration file.

#### 14.7.1 ASACC

##### Purpose

Specifies whether the listing file follows the ASA convention of using the first column in each line for carriage control.

##### Syntax

ASACC={YES \| NO}

##### Default

NO

##### Usage Notes

Cannot be entered inline.

#### 14.7.2 ASSUME_SQLCODE

##### Purpose

Instructs Pro\*COBOL to presume that SQLCODE is declared whether or not it is declared in the program, or of the proper type.

##### Syntax

ASSUME_SQLCODE={YES \| NO}

##### Default

NO

##### Usage Notes

Cannot be entered inline.

When DECLARE_SECTION=YES and ASSUME_SQLCODE=YES, SQLCODE can be declared outside a Declare Section.

When DECLARE_SECTION=YES and ASSUME_SQLCODE=NO, SQLCODE is recognized as the status variable if and only if at least one of the following criteria is satisfied:

- It is declared with exactly the right datatype.

- Pro\*COBOL finds no other status variable. If Pro\*COBOL finds a SQLSTATE declaration (of exactly the right type of course), or finds an include of a SQLCA, then it will not presume SQLCODE is declared.

When ASSUME_SQLCODE=YES, and when SQLSTATE and/or SQLCA are declared as status variables, Pro\*COBOL presumes SQLCODE is declared whether or not it is declared or of the proper type.

#### 14.7.3 AUTO_CONNECT

##### Purpose

Specifies whether your program connects automatically to the default user account.

##### Syntax

AUTO_CONNECT={YES \| NO}

##### Default

NO

##### Usage Notes

Cannot be entered inline.

When AUTO_CONNECT=YES, as soon as Pro\*COBOL encounters an executable SQL statement, your program tries to log on to Oracle automatically with the userid

    <prefix><username>

where \<prefix\> is the value of the Oracle initialization parameter OS_AUTHENT_PREFIX (the default value is OPS\$) and \<username\> is your operating system user or task name. In this case, you cannot override the default value for MAXOPENCURORS (10), even if you specify a different value on the command line.

When AUTO_CONNECT=NO (the default), you must use the CONNECT statement to logon to Oracle.

#### 14.7.4 CHARSET_PICX

##### Purpose

Specifies the character set form used by PIC X variables used in select, insert, or update statements.

##### Syntax

CHARSET_PICX={NCHAR_CHARSET \| DB_CHARSET }

##### Default

DB_CHARSET

##### Usage Notes

Can be used on the command line or in a configuration file, but not inline.

If CHARSET_PICX = NCHAR_CHARSET, the PIC X bind or define buffer is converted according to the server-side National Character Set. Possible performance impact might be seen when target column is CHAR. Similarly, if CHARSET_PICX = DB_CHARSET, the PIC X bind or define buffer is converted according to server-side Database Character Set. There can be some data loss when target column is NCHAR.

#### 14.7.5 CHARSET_PICN

##### Purpose

Specifies the character set form used by PIC N variables used in select, insert, or update statements.

##### Syntax

CHARSET_PICN={NCHAR_CHARSET \| DB_CHARSET }

##### Default

NCHAR_CHARSET

##### Usage Notes

Can be used on the command line or in a configuration file, but not inline.

If CHARSET_PICN = DB_CHARSET, the PIC N bind or define buffer is converted according to the server-side Database Character Set. There can be some data loss when target column is NCHAR. Similarly, if CHARSET_PICN = NCHAR_CHARSET, the PIC N bind or define buffer is converted according to server-side National Character Set. Possible performance impact might be seen when target column is CHAR.

#### 14.7.6 CLOSE_ON_COMMIT

##### Purpose

Specifies whether or not all cursors declared without the WITH HOLD clause are closed on commit.

##### Syntax

CLOSE_ON_COMMIT={YES \| NO}

##### Default

NO

##### Usage Notes

Can be used only on the command line or in a configuration file.

This option will only have an effect when a cursor is not coded using the WITH HOLD clause in a DECLARE CURSOR statement, since that will override both the new option and the existing behavior which is associated with the MODE option. If MODE is specified at a higher level than CLOSE_ON_COMMIT, then MODE takes precedence. For example, the defaults are MODE=ORACLE and CLOSE_ON_COMMIT=NO. If the user specifies MODE=ANSI on the command line, then any cursors not using the WITH HOLD clause will be closed on commit.

When CLOSE_ON_COMMIT=NO (when MODE=ORACLE), issuing a COMMIT or ROLLBACK will close only cursors that are declared using the FOR UPDATE clause or are referenced in a CURRENT OF clause. Other cursors are not affected by the COMMIT or ROLLBACK statement, remain open, if they are open already. However, when CLOSE_ON_COMMIT=YES (when MODE=ANSI), issuing a COMMIT or ROLLBACK closes all cursors.

For a further discussion of the precedence of this option see “Macro and Micro Options”.

**Related Topics**

- Macro and Micro Options

#### 14.7.7 COMMON_PARSER

##### Purpose

Specifies that the SQL99 syntax for SELECT, INSERT, DELETE, UPDATE and body of the cursor in a DECLARE CURSOR statement will be supported.

##### Syntax

COMMON_PARSER={YES \| NO}

##### Default

NO

##### Usage Notes

Can be entered in the command line.

#### 14.7.8 CONFIG

##### Purpose

Specifies the name of a user configuration file.

##### Syntax

CONFIG=filename

##### Default

None

##### Usage Notes

Can be entered only on the command line.

Pro\*COBOL can use a configuration file containing preset command-line options. However, you can specify any of several alternative files, called user configuration files. For more information, see “Entering Precompiler Options”.

You cannot nest configuration files. Therefore, you cannot specify the option CONFIG in a configuration file.

**Related Topics**

- Entering Precompiler Options

#### 14.7.9 DATE_FORMAT

##### Purpose

Species the string format in which dates are returned.

##### Syntax

DATE_FORMAT={ISO \| USA \| EUR \| JIS \| LOCAL \| 'fmt' (default LOCAL)

##### Default

LOCAL

##### Usage Notes

Can only be entered on the command line or in a configuration file. The date strings are shown in the following table:

Table 14-3 Formats for Date Strings

| Format Name                          | Abbreviation | Date Format                    |
|:-------------------------------------|:-------------|:-------------------------------|
| International Standards Organization | ISO          | yyyy-mm-dd                     |
| USA standard                         | USA          | mm/dd/yyyy                     |
| European standard                    | EUR          | dd.mm.yyyy                     |
| Japanese Industrial Standard         | JIS          | yyyy-mm-dd                     |
| installation-defined                 | LOCAL        | Any installation-defined form. |

'fmt' is a date format model, such as "Month dd, yyyy". See “Datetime Format Elements” for the list of date format model elements.

There is one restriction on the use of the DATE_FORMAT option: All compilation units to be linked together must use the same DATE_FORMAT value. An error occurs when there is a mismatch in the values of DATE_FORMAT across compilation units

#### 14.7.10 DB2_ARRAY

##### Purpose

Based on this option, the precompiler activates the additional array insert/select syntax.

##### Syntax

DB2_ARRAY={YES \|NO}

##### Default

NO

##### Usage Notes

If this option is set to NO, the Oracle precompiler syntax is supported, otherwise the DB2 insert/select array syntax is supported.

#### 14.7.11 DBMS

##### Purpose

Specifies whether Oracle follows the semantic and syntactic rules of Oracle7 Database, Oracle8i, or the native version of Oracle (that is, the version to which your application is connected).

##### Syntax

DBMS={V7 \| V8 \| NATIVE}

##### Default

NATIVE

##### Usage Notes

Cannot be entered inline.

With the DBMS option you control the version-specific behavior of Oracle. When DBMS=NATIVE (the default), Oracle follows the semantic and syntactic rules of the native version of Oracle.

#### 14.7.12 DECLARE_SECTION

##### Purpose

Specifies whether or not only declarations in a Declare Section are allowed as host variables.

##### Syntax

DECLARE_SECTION={YES \| NO}

##### Default

NO

##### Usage Notes

Can be entered only on the command line or in a configuration file.

When MODE=ORACLE, use of the BEGIN DECLARE SECTION and END DECLARE SECTION statements are optional, starting with release 8.0 of Pro\*COBOL. The DECLARE_SECTION option is provided for backward compatibility with previous releases. DECLARE_SECTION is a micro option of MODE.

This option allows the user to specify MODE=ORACLE together with DECLARE_SECTION=YES to get the same effect that previous releases provided when using MODE=ORACLE alone. (Only variables declared inside the DECLARE statements are allowed as host variables.) For a discussion of precedence of this option, see “Precedence of Option Values”.

**Related Topics**

- Precedence of Option Values

#### 14.7.13 DEFINE

##### Purpose

Specifies a user-defined symbol that is used to include or exclude portions of source code during a conditional precompilation. For more information, see “Conditional Precompilations”

##### Syntax

DEFINE=symbol

##### Default

None

##### Usage Notes

If you enter DEFINE inline, the EXEC ORACLE statement takes the following form:

    EXEC ORACLE DEFINE symbol END-EXEC.

**Related Topics**

- [Conditional Precompilations](precompiler-concepts.md)

#### 14.7.14 DYNAMIC

##### Purpose

This micro option of MODE specifies the descriptor behavior in dynamic SQL Method 4.

##### Syntax

DYNAMIC={ORACLE \| ANSI}

##### Default

ORACLE

##### Usage Notes

Cannot be entered inline by use of the EXEC ORACLE OPTION statement.

See the DYNAMIC option settings in “ANSI Dynamic SQL Precompiler Options”.

**Related Topics**

- [ANSI Dynamic SQL Precompiler Options](ANSI-dynamic-SQL.md)

#### 14.7.15 END_OF_FETCH

##### Purpose

This micro option of MODE specifies which SQLCODE value is returned when an END-OF-FETCH condition occurs after execution of a SQL statement.

##### Syntax

END_OF_FETCH={100 \| 1403}

##### Default

1403

##### Usage Notes

Can be entered only on the command line or in a configuration file.

END_OF_FETCH is a micro option of MODE. For further discussion, see “Macro and Micro Options”.

If you specify MODE=ANSI in a configuration file, Pro\*COBOL returns the SQLCODE value 100 at the END_OF_FETCH, overriding the default END_OF_FETCH=1403.

If you specify MODE=ANSI and END_OF_FETCH=1403 in the configuration file, then Pro\*COBOL will return the SQLCODE value 1403 at the END_OF_FETCH.

If you specify MODE=ANSI in the configuration file and END_OF_FETCH=1403 on the command line, which has a higher precedence than your configuration file, Pro\*COBOL will again return the SQLCODE value 1403 at the END_OF_FETCH.

**Related Topics**

- Macro and Micro Options

#### 14.7.16 ERRORS

##### Purpose

Specifies whether Pro\*COBOL error messages are sent to the terminal and listing file or only to the listing file.

##### Syntax

ERRORS={YES \| NO}

##### Default

YES

##### Usage Notes

When ERRORS=YES, error messages are sent to the terminal and listing file.

When ERRORS=NO, error messages are sent only to the listing file.

#### 14.7.17 File_ID

##### Purpose

Denotes the unique identifier for the generated Cobol file. The generated files contain a unique number associated with the "SQLCTX" variable. The file_id option can be used to set the value of the SQLCTX variable. The option is useful while precompiling multiple source files, so that the user can ensure unique SQLCTX values associated with the different generated files.

##### Syntax

FILE_ID=Range is 0 to 65535

##### Default

0

##### Usage Notes

The file_id option can be used to directly assign values to "SQLCTX" variable in the generated Cobol file.

#### 14.7.18 FIPS

##### Purpose

Specifies whether extensions to ANSI/ISO SQL are flagged (by the FIPS Flagger). An extension is any SQL element that violates ANSI/ISO format or syntax rules, except privilege enforcement rules.

##### Syntax

FIPS={YES \| NO}

##### Default

NO

##### Usage Notes

When FIPS=YES, the FIPS Flagger issues warning (not error) messages if you use an Oracle extension to the Entry level of SQL-92 or use a feature of Entry level SQL-92 in a nonconforming manner.

The following extensions to ANSI/ISO SQL are flagged at precompile time:

- Array interface including the FOR clause

- SQLCA, ORACA, and SQLDA data structures

- Dynamic SQL including the DESCRIBE statement

- Embedded PL/SQL blocks

- Automatic datatype conversion

- DATE, COMP-3, NUMBER, RAW, LONG RAW, VARRAW, ROWID, and VARCHAR datatypes

- ORACLE OPTION statement for specifying runtime options

- EXEC TOOLS statements in user exits

- CONNECT statement

- TYPE and VAR datatype equivalencing statements

- AT db_name clause

- DECLARE...DATABASE, ...STATEMENT, and ...TABLE statements

- SQLWARNING condition in WHENEVER statement

- DO and STOP actions in WHENEVER statement

- COMMENT and FORCE TRANSACTION clauses in COMMIT statement

- FORCE TRANSACTION and TO SAVEPOINT clauses in ROLLBACK statement

- RELEASE parameter in COMMIT and ROLLBACK statements

- Optional colon-prefixing of WHENEVER...DO labels and of host variables in the INTO clause

#### 14.7.19 FORMAT

##### Purpose

Specifies the format of COBOL statements.

##### Syntax

FORMAT={ANSI \| TERMINAL \| VARIABLE}

##### Default

ANSI

##### Usage Notes

Cannot be entered inline.

The format of input lines is system-dependent. Check your system-specific Oracle manuals, or your COBOL compiler.

When FORMAT=ANSI, the format of input lines conforms as much as possible to the current ANSI standard for COBOL. When FORMAT=TERMINAL, input lines can start in column 1. Example code in this book is in TERMINAL format. Use FORMAT=VARIABLE to allow Flexible B Area Length. See “Coding Areas” for a more complete description.

**Related Topics**

- [Coding Areas](precompiler-concepts.md)

#### 14.7.20 HOLD_CURSOR

##### Purpose

Specifies how the cursors for SQL statements and PL/SQL blocks are handled in the cursor cache.

##### Syntax

HOLD_CURSOR={YES \| NO}

##### Default

NO

##### Usage Notes

You can use HOLD_CURSOR to improve the performance of your program. For more information, see “Performance Tuning”.

When a SQL data manipulation statement is executed, its associated cursor is linked to an entry in the cursor cache. The cursor cache entry is in turn linked to an Oracle private SQL area, which stores information needed to process the statement. HOLD_CURSOR controls what happens to the link between the cursor and cursor cache.

When HOLD_CURSOR=NO, after Oracle executes the SQL statement and the cursor is closed, Pro\*COBOL marks the link as reusable. The link is reused as soon as the cursor cache entry to which it points is needed for another SQL statement. This frees memory allocated to the private SQL area and releases parse locks.

When HOLD_CURSOR=YES, the link is maintained; Pro\*COBOL does not reuse it. This is useful for SQL statements that are executed often because it speeds up subsequent executions and there is no need to re-parse the statement or allocate memory for an Oracle private SQL area.

For inline use with implicit cursors, set HOLD_CURSOR before executing the SQL statement. For inline use with explicit cursors, set HOLD_CURSOR before opening the cursor.

For information showing how the HOLD_CURSOR and RELEASE_CURSOR options interact, see “Performance Tuning”.

**Related Topics**

- [Performance Tuning](performance-tuning.md)

#### 14.7.21 HOST

##### Purpose

Specifies the host language to be used.

##### Syntax

HOST={COB74 \| COBOL}

##### Default

COBOL

##### Usage Notes

Cannot be entered inline.

COB74 refers to the 1974 version of ANSI-approved COBOL. COBOL refers to the 1985 version. Other values might be available on your platform.

#### 14.7.22 IMPLICIT_SVPT

##### Purpose

Controls whether an implicit savepoint is taken prior to the start of a new batched insert.

##### Syntax

implicit_svpt={YES\|NO}

##### Default

NO

##### Usage Notes

If yes, a savepoint is taken prior to the start of a new batch of rows. If an error occurs on the insert, an implicit "rollback to savepoint" is executed. This option exists for DB2 compatibility, the obvious downside being the extra round-trip.

If no, there is no implicit savepoint taken. If an error occurs on the buffered insert, then it is reported back to the application, but no rollback is executed.

#### 14.7.23 INAME

##### Purpose

Specifies the name of the input file.

##### Syntax

INAME=filename

##### Default

None

##### Usage Notes

Cannot be entered inline.

All input file names must be unique at precompilation time.

When specifying the name of your input file on the command line, the keyword INAME is optional. For example, in Pro\*COBOL, you can specify myprog.pco instead of INAME=myprog.pco.

You need not use a file extension when specifying INAME unless the extension is nonstandard. On the UNIX platform, Pro\*COBOL assumes the default input file extension pco.

#### 14.7.24 INCLUDE

##### Purpose

Specifies a directory path for EXEC SQL INCLUDE files. It only applies to operating systems that use directories.

##### Syntax

INCLUDE=path

##### Default

Current directory

##### Usage Notes

Pro\*COBOL searches first in the current directory, then in the directory specified by INCLUDE, and finally in a directory for standard INCLUDE files. Hence, you need not specify a directory path for standard files.

You must still use INCLUDE to specify a directory path for nonstandard files unless they are stored in the current directory. You can specify more than one path on the command line, as follows:

    ... INCLUDE=path1 INCLUDE=path2 ...

Pro\*COBOL searches first in the current directory, then in the directory named by path1, then in the directory named by path2, and finally in the directory for standard INCLUDE files.

Note: Pro\*COBOL looks for a file in the current directory first—even if you specify a directory path. Therefore, if the file you want to INCLUDE resides in another directory, make sure no file with the same name resides in the current directory.

The syntax for specifying a directory path is system-specific. Follow the conventions of your operating system.

#### 14.7.25 IRECLEN

##### Purpose

Specifies the record length of the input file.

##### Syntax

IRECLEN=integer

##### Default

80

##### Usage Notes

Cannot be entered inline.

The value you specify for IRECLEN should not exceed the value of ORECLEN. The maximum value allowed is system-dependent.

#### 14.7.26 LITDELIM

##### Purpose

The LITDELIM option specifies the delimiters for string constants and literals in the COBOL code generated by Pro\*COBOL.

##### Syntax

LITDELIM={APOST \| QUOTE}

##### Default

QUOTE

##### Usage Notes

When LITDELIM=APOST, Pro\*COBOL uses apostrophes when generating COBOL code. If you specify LITDELIM=QUOTE, quotation marks are used, as in

         CALL "SQLROL" USING SQL-TMP0.

In SQL statements, you must use quotation marks to delimit identifiers containing special or lowercase characters, as in

         EXEC SQL CREATE TABLE "Emp2" END-EXEC.

but you must use apostrophes to delimit string constants, as in

         EXEC SQL SELECT ENAME FROM EMP WHERE JOB = 'CLERK' END-EXEC.

Regardless of which delimiters are used in the Pro\*COBOL source file, Pro\*COBOL generates the delimiters specified by the LITDELIM value.

#### 14.7.27 LNAME

##### Purpose

Specifies a nondefault name for the listing file.

##### Syntax

LNAME=filename

##### Default

Input

##### Usage Notes

Cannot be entered inline.

By default, the listing file is written to the current directory.

#### 14.7.28 LRECLEN

##### Purpose

Specifies the record length of the listing file.

##### Syntax

LRECLEN=integer

##### Default

132

##### Usage Notes

Cannot be entered inline.

The value of LRECLEN can range from 80 through 132. If you specify a value below the range, 80 is used instead. If you specify a value above the range, an error occurs. LRECLEN should exceed IRECLEN by at least 8 to allow for the insertion of line numbers.

#### 14.7.29 LTYPE

##### Purpose

Specifies the listing type.

##### Syntax

LTYPE={LONG \| SHORT \| NONE}

##### Default

LONG

##### Usage Notes

Cannot be entered inline.

Table 14-4 Types of Listings

| Listing Types | Description                                    |
|:--------------|:-----------------------------------------------|
| LTYPE=LONG    | input lines appear in the listing file.        |
| LTYPE=SHORT   | input lines do not appear in the listing file. |
| LTYPE=NONE    | no listing file is created.                    |

#### 14.7.30 MAX_ROW_INSERT

##### Purpose

Controls the number of rows that need to be buffered before executing the INSERT statement.

##### Syntax

max_row_insert={0...1000}

##### Default

0

##### Usage Notes

Any number greater than zero enables buffered insert feature and buffers that many rows before executing the INSERT statement.

#### 14.7.31 MAXLITERAL

##### Purpose

Specifies the maximum length of string literals generated by Pro\*COBOL so that compiler limits are not exceeded. For example, if your compiler cannot handle string literals longer than 132 characters, you can specify MAXLITERAL=132 on the command line.

##### Syntax

MAXLITERAL=integer

##### Default

1024

##### Usage Notes

The maximum value of MAXLITERAL is compiler-dependent. The default value is language-dependent, but you may have to specify a lower value. For example, some COBOL compilers cannot handle string literals longer than 132 characters, so you would specify MAXLITERAL=132.

Strings that exceed the length specified by MAXLITERAL are divided during precompilation, then recombined (concatenated) at run time.

You can enter MAXLITERAL inline but your program can set its value just once, and the EXEC ORACLE statement must precede the first EXEC SQL statement. Otherwise, Pro\*COBOL issues a warning message, ignores the extra or misplaced EXEC ORACLE statement, and continues processing.

#### 14.7.32 MAXOPENCURSORS

##### Purpose

Specifies the number of concurrently open cursors that Pro\*COBOL tries to keep cached.

##### Syntax

MAXOPENCURSORS=integer

##### Default

10

##### Usage Notes

You can use MAXOPENCURSORS to improve the performance of your program. For more information, see “Performance Tuning”.

When precompiling separately, use MAXOPENCURSORS as described in “Separate Precompilations”.

MAXOPENCURSORS specifies the initial size of the SQLLIB cursor cache.

When an implicit statement is executed and HOLD_CURSOR=NO, or an explicit cursor is closed, the cursor entry is marked as reusable. If this statement is issued again and the cursor entry has not been used for another statement, it is reused.

If a new cursor is needed and the number of cursors allocated is less than MAXOPENCURSORS, then the next one in the cache is allocated. Once MAXOPENCCURSORS has been exceeded, Oracle first tries to reuse a previous entry. If there are no free entries, then an additional cache entry is allocated. Oracle continues to do this until the program runs out of memory or the database parameter OPEN_CURSORS is exceeded.

During normal processing, when using HOLD_CURSOR=NO and RELEASE_CURSOR=NO (the default), it is advisable to set MAXOPENCURSORS to no more than 6 less than the database parameter OPEN_CURSORS to allow for the cursors used by the data dictionary to process statements.

As your program's need for concurrently open cursors grows, you might want to re-specify MAXOPENCURSORS to match the need. A value of 45 to 50 is not uncommon, but remember that each cursor requires another private SQL area in the user process memory space. The default value of 10 is adequate for most programs.

**Related Topics**

- [Performance Tuning](performance-tuning.md)
- [Separate Precompilations](precompiler-concepts.md)

#### 14.7.33 MODE

##### Purpose

This macro option specifies whether your program observes Oracle practices or complies with the current ANSI SQL standard.

##### Syntax

MODE={ANSI \| ISO \| ANSI14 \| ISO14 \| ANSI13 \| ISO13 \| ORACLE}

##### Default

ORACLE

##### Usage Notes

Cannot be entered inline.

The following pairs of MODE values are equivalent: ANSI and ISO, ANSI14 and ISO14, ANSI13 and ISO13.

When MODE=ORACLE (the default), your embedded SQL program observes Oracle practices.

When MODE={ANSI14 \| ANSI13}, your program complies closely with the current ANSI SQL standard.

When MODE=ANSI, your program complies fully with the ANSI standard and the following changes go into effect:

- You cannot open a cursor that is already open or CLOSE a cursor that is already closed. (When MODE=ORACLE, you can reOPEN an open cursor to avoid re-parsing.)

- No error message is issued if Oracle assigns a truncated column value to an output host variable.

When MODE={ANSI \| ANSI14}, a 4-byte integer variable named SQLCODE or a 5-byte character variable named SQLSTATE must be declared. For more information, see “Error Handling Alternatives”.

**Related Topics**

- [Error Handling Alternatives](error-handling-and-diagnostics.md)

#### 14.7.34 NESTED

##### Purpose

Indicates whether GLOBAL clauses in nested programs are to be generated. If the compiler supports nested programs, use YES as the value of NESTED.

##### Syntax

NESTED={YES \| NO}

##### Default

YES

##### Usage Notes

Cannot be entered inline.

#### 14.7.35 NLS_LOCAL

##### Purpose

The NLS_LOCAL option determines whether Globalization Support (formerly called NLS) character conversions are performed by the Pro\*COBOL runtime library or by the Oracle Server.

##### Syntax

NLS_LOCAL={YES \| NO}

##### Default

NO

##### Usage Notes

Cannot be entered inline.

This option is for use when passing National Character Set variables to and from the server.

When NLS_LOCAL=YES, the runtime library (SQLLIB) locally performs blank-padding and blank-stripping for host variables that have multibyte Globalization Support datatypes. Continue to use this value only for Pro\*COBOL applications written for releases before releases 8.0.

When NLS_LOCAL=YES, because dynamic SQL statements are not processed at precompile time, this option has no effect on dynamic SQL statements.

Also, when NLS_LOCAL=YES, columns storing multibyte Globalization Support data cannot be used in embedded data definition language (DDL) statements. This restriction cannot be enforced when precompiling, so the use of these column types within embedded DDL statements results in an execution error rather than a precompile error.

When NLS_LOCAL=NO, blank-padding and blank-stripping operations are performed by the Oracle Server for host variables that have multibyte Globalization Support datatypes. Use for all new release 8.0, or later, applications.

The environment variable NLS_NCHAR specifies the character set used for National Character Set data. (NCHAR, NVARCHAR2, NCLOB). If it is not specified, the character set defined or defined indirectly by NLS_LANG will be used. See “Setting Up a Globalization Support Environment” for details.

#### 14.7.36 ONAME

##### Purpose

Specifies the name of the output file.

##### Syntax

ONAME=filename

##### Default

System dependent

##### Usage Notes

Cannot be entered inline.

Use this option to specify the name of the output file, where the name differs from that of the input file. For example, if you issue

    procob INAME=my_test

the default output filename is `my_test.cob`. If you want the output filename to be `my_test_1.cob`, issue the command

    procob INAME=my_test ONAME=my_test_1.cob

Note that you should add the .cob extension to files specified using ONAME. There is no default extension with the ONAME option.

Attention: Oracle recommends that you not let the output filename default, but rather name it explicitly using ONAME.

#### 14.7.37 ORACA

##### Purpose

Specifies whether a program can use the Oracle Communications Area (ORACA).

##### Syntax

ORACA={YES \| NO}

##### Default

NO

##### Usage Notes

When ORACA=YES, you must place the INCLUDE ORACA statement in your program.

#### 14.7.38 ORECLEN

##### Purpose

Specifies the record length of the output file.

##### Syntax

ORECLEN=integer

##### Default

80

##### Usage Notes

Cannot be entered inline.

The value you specify for ORECLEN should equal or exceed the value of IRECLEN. The maximum value allowed is system-dependent.

#### 14.7.39 OUTLINE

##### Purpose

Indicates that the outline SQL file needs to be generated for the SQL statements.

##### Syntax

outline={yes \| no \| category_name}

##### Default

no

##### Usage Notes

The outline SQL file should be in the DEFAULT category if the value is `yes` and the generated outline format is

    DEFAULT_<filename>_<filetype>_<sequence_no>

If the category name is mentioned, then the SQL file should be generated in the category mentioned. The generated outline format for this is

    <category_name>_<filename>_<filetype>_<sequence_no>

The outline SQL file is not generated if the value is `no`.

Semantic check should be full when this option is turned on, which means option sqlcheck=full/semantics. If sqlcheck=syntax/limited/none, then error will be generated.

#### 14.7.40 OUTLNPREFIX

##### Purpose

Controls the generation of the outline names.

##### Syntax

outlnprefix={none \| prefix_name}

##### Default

no

##### Usage Notes

If outlnprefix=prefix_name, then the outline format

    <category_name>_<filename>_<filetype>

is replaced with `<prefix_name>` for the outline names.

If the length of the outline name exceeds 128 bytes, then this option is helpful for the user who can just specify the prefix name.

If outlnprefix=none, then the outline names are generated by the system. The generated format is

    <category_name>_<filename>_<filetype>_<sequence_no>

Semantic check should be full when this option is turned on, which means option sqlcheck=full/semantics. If sqlcheck=syntax/limited/none, and/or outline=false, then error will be generated.

#### 14.7.41 PAGELEN

##### Purpose

Specifies the number of lines for each physical page of the listing file.

##### Syntax

PAGELEN=integer

##### Default

66

##### Usage Notes

Cannot be entered inline. The maximum value allowed is system-dependent.

#### 14.7.42 PICN_ENDIAN

##### Purpose

Maintains platform endianness (little endian for Linux and Windows; big endian for Solaris) in PIC N variables.

##### Syntax

picn_endian={BIG \| OS}

##### Default

BIG

##### Usage Notes

If picn_endian=big, then PIC N variables are bound with character set ID AL16UTF16.

If picn_endian=os then PIC N variables are bound with character set ID UCS2.

The default value for this option is "big" to preserve the current behavior. This option is ignored if NLS_NCHAR is not AL16UTF16.

Character set form for PIC N variables can be set by using the existing Pro\*Cobol command line option: charset_picn={nchar_charset \| db_charset}

#### 14.7.43 PICX

##### Purpose

Specifies the default datatype of PIC X variables.

##### Syntax

PICX={CHARF \| VARCHAR2}

##### Default

CHARF

##### Usage Notes

Can be entered only on the command line or in a configuration file.

Starting in Pro\*COBOL 8.0, the default datatype of PIC X, N, or G variables was changed from VARCHAR2 to CHARF. PICX is provided for backward compatibility.

This new default behavior is consistent with the normal COBOL move semantics. Note that this is a change in behavior for the case where you are inserting a PIC X variable (with MODE=ORACLE) into a VARCHAR2 column. Any trailing blanks which had formerly been trimmed will be preserved. Note also, that the new default lessens the occurrence of the following anomaly: Using a PIC X bind variable initialized with trailing blanks in a WHERE clause would never match a value with the same number of trailing blanks which was stored in a char column because the bind variable's trailing blanks were stripped before the comparison.

When PICX=VARCHAR2, Oracle treats local CHAR variables in a PL/SQL block like variable-length character values. When PICX=CHARF, however, Oracle treats the CHAR variables like ANSI-compliant, fixed-length character values. See “Default for PIC X” for an extensive discussion.

**Related Topics**

- [Default for PIC X](datatypes-and-host-variables.md)

#### 14.7.44 PLAN_BASELINE

##### Purpose

Creates a SQL Plan Baseline by specifying the module name.

##### Syntax

PLAN_BASELINE={module_name \| YES \| NO}

##### Default

NO

##### Usage Notes

The module name will become a part of the unique plan name generated by appending the filename, file type, and sequence number.

#### 14.7.45 PLAN_PREFIX

##### Purpose

Ensures that the plan name does not exceed 128 bytes.

##### Syntax

PLAN_PREFIX={prefix_name \| none}

##### Default

none

##### Usage Notes

It is an optional command. The default is none which means that no prefix name is used, and if the plan name exceeds 128 bytes an error message is generated.

#### 14.7.46 PLAN_RUN

##### Purpose

Executes the generated SQL file.

##### Syntax

PLAN_RUN={YES \| NO}

##### Default

NO

##### Usage Notes

If the PLAN_RUN option is not set then the generated SQL file is not executed.

#### 14.7.47 PLAN_FIXED

##### Purpose

Specifies whether or not the created plan baseline is fixed or non-fixed.

##### Syntax

PLAN_FIXED={ YES \| NO }

##### Default

YES

##### Usage Notes

When set to NO, a non-fixed Plan Baseline is created.

#### 14.7.48 PLAN_ENABLED

##### Purpose

Enables the use of the Plan Baseline that is created.

##### Syntax

PLAN_ENABLED={ YES \| NO }

##### Default

YES

##### Usage Notes

When set to the default, YES, the created Plan Baseline is used for plan selection. When set to NO, the Plan Baseline is created, but is not used until enabled manually.

#### 14.7.49 MEMFORPREFETCH

##### Purpose

Use this option to speed up queries by pre-fetching the number of rows that can be accommodated in the specified memory.

##### Syntax

MEMFORPREFETCH=integer

##### Default

No value set.

##### Usage Notes

This option can be used in configuration file or on the command line. The value of the integer is used for execution of all queries using explicit cursors, subject to the rules of precedence.

When used inline it must be placed before OPEN statements with explicit cursors. Then the number of rows pre-fetched when that OPEN is done is determined by the last in-line MEMFORPREFETCH option in effect.

The MEMFORPREFETCH default is no-value-is-set. To turn off prefetching, use MEMFORPREFETCH=0 on the command line.

Prefetching is turned off when LONG or LOB columns are being accessed. MEMFORPREFETCH is used to enhance the performance of single row fetches. MEMFORPREFETCH values have no effect when doing array fetches, regardless of which value is assigned.

There is no single perfect prefetch memory value that can be used to assist all the fetches in an application.

Therefore, when using the MEMFORPREFETCH option, you should test different values to give a general improvement across all statements in the program. Note that if certain statements need to be tuned individually, the MEMFORPREFETCH option can be specified inline using EXEC ORACLE OPTION. Note that this will affect all fetch statements that follow the command in your program. Select the appropriate prefetch memory to enhance the performance of any particular FETCH statement. To achieve this individual prefetch count, you should use the inline prefetch option rather than from the command line.

#### 14.7.50 PREFETCH

##### Purpose

Use this option to speed up queries by pre-fetching a given number of rows.

##### Syntax

PREFETCH=integer

##### Default

1

##### Usage Notes

Can be used in a configuration file or on the command-line. The value of the integer is used for execution of all queries using explicit cursors, subject to the rules of precedence.

When used in-line it must be placed before OPEN statements with explicit cursors. Then the number of rows pre-fetched when that OPEN is done is determined by the last in-line PREFETCH option in effect.

The PREFETCH default is 1. To turn off prefetching, use PREFETCH=0 on the command line.

Prefetching is turned off when LONG or LOB columns are being accessed. PREFETCH is used to enhance the performance of single row fetches. PREFETCH values have no effect when doing array fetches, regardless of which value is assigned.

There is no single perfect prefetch number that can be used to assist all the fetches in an application.

Therefore, when using the PREFETCH option, you should test different values to give a general improvement across all statements in the program. Note that if certain statements need to be tuned individually, the PREFETCH option can be specified in line using EXEC ORACLE OPTION. Note that this will affect all fetch statements that follow the command in your program. Select the appropriate prefetch number to enhance the performance of any particular FETCH statement. To achieve this individual prefetch count, you should use the inline prefetch option. (Rather than from the command line.)

The maximum value is 9999. See “The PREFETCH Precompiler Option” for further discussion.

**Related Topics**

- [The PREFETCH Precompiler Option](embedded-SQL.md)

#### 14.7.51 RELEASE_CURSOR

##### Purpose

Specifies how the cursors for SQL statements and PL/SQL blocks are handled in the cursor cache.

##### Syntax

RELEASE_CURSOR={YES \| NO}

##### Default

NO

##### Usage Notes

You can use RELEASE_CURSOR to improve the performance of your program. For more information, see .

When a SQL data manipulation statement is executed, its associated cursor is linked to an entry in the cursor cache. The cursor cache entry is in turn linked to an Oracle private SQL area, which stores information needed to process the statement. RELEASE_CURSOR controls what happens to the link between the cursor cache and private SQL area.

When RELEASE_CURSOR=YES, after Oracle executes the SQL statement and the cursor is closed, Pro\*COBOL immediately removes the link. This frees memory allocated to the private SQL area and releases parse locks. To make sure that associated resources are freed when you CLOSE a cursor, you must specify RELEASE_CURSOR=YES.

When RELEASE_CURSOR=NO, the link is maintained. Pro\*COBOL does not reuse the link unless the number of open cursors exceeds the value of MAXOPENCURSORS. This is useful for SQL statements that are executed often because it speeds up subsequent executions. There is no need to re-parse the statement or allocate memory for an Oracle private SQL area.

For inline use with implicit cursors, set RELEASE_CURSOR before executing the SQL statement. For inline use with explicit cursors, set RELEASE_CURSOR before opening the cursor.

Note that RELEASE_CURSOR=YES overrides HOLD_CURSOR=YES. For information showing how these two options interact, see “Performance Tuning”.

**Related Topics**

- [Precompiler Options](ANSI-dynamic-SQL.md)

#### 14.7.52 RUNOUTLINE

##### Purpose

Provides the developer with the option of executing "create outline" statements either by using precompiler or by the developer manually at a later time.

##### Syntax

runoutline={yes \| no}

##### Default

no

##### Usage Notes

If runoutline=yes, then the generated 'create outline' statements are executed by the precompiler/translator at the end of a successful precompilation.

The outline option should be set to true or category_name when runoutline is used. Semantic check should be full when this option is turned on, which means option sqlcheck=full/semantics. If sqlcheck=syntax/limited/none, then error will be generated.

#### 14.7.53 SELECT_ERROR

##### Purpose

Specifies whether your program generates an error when a SELECT statement returns more than one row or more rows than a host array can accommodate.

##### Syntax

SELECT_ERROR={YES \| NO}

##### Default

YES

##### Usage Notes

When SELECT_ERROR=YES, an error is generated if a single-row select returns too many rows or an array select returns more rows than the host array can accommodate.

When SELECT_ERROR=NO, no error is generated when a single-row select returns too many rows or when an array select returns more rows than the host array can accommodate.

Whether you specify YES or NO, a random row is selected from the table. To ensure a specific ordering of rows, use the ORDER BY clause in your SELECT statement. When SELECT_ERROR=NO and you use ORDER BY, Oracle returns the first row, or the first n rows if you are selecting into an array. When SELECT_ERROR=YES, whether or not you use ORDER BY, an error is generated if too many rows are returned.

#### 14.7.54 SQLCHECK

##### Purpose

Specifies the type and extent of syntactic and semantic checking..

When SQLCHECK=SEMANTICS or FULL, the SQL statements are packaged/bundled into an IDL objects using a generic grammar during parsing. The generic grammar will not try to understand the SQL syntax, it can only identify the host variables, indicator variables, and the possible SQL identifiers. During the semantic phase, the validity of the host and indicator variables are checked in the same manner it is now being done for SQL. The semantics like the table name ,column names,types will be checked in the same way it is now being handled for SQL.

The new unified parser:

1.  Precompiles all the existing precompiler applications.

2.  Supports the following SQL statements completely (all clauses of these SQL statements):

    1.  SELELCT statement

    2.  INSERT statement

    3.  DELETE statement

    4.  UPDATE statement

    5.  Body of the cursor in a DECLARE CURSOR statement

##### Syntax

SQLCHECK={SEMANTICS \| FULL \| SYNTAX \| LIMITED}

##### Default

SYNTAX

##### Usage Notes

The values SEMANTICS and FULL are equivalent, as are the values SYNTAX and LIMITED.

Pro\*COBOL can help you debug a program by checking the syntax and semantics of embedded SQL statements and PL/SQL blocks. Any errors found are reported at precompile time.

You control the level of checking by entering the SQLCHECK option inline or on the command line, or both inline and on the command line. However, the level of checking you specify inline cannot be higher than the level you specify (or accept by default) on the command line.

Pro\*COBOL generates an error when PL/SQL reserved words are used in SQL statements, even though the SQL statements are not themselves PL/SQL. If a PL/SQL reserved word must be used as an identifier, you can enclose it in double-quotes (").

When SQLCHECK=SEMANTICS, Pro\*COBOL checks the syntax and semantics of

- Data manipulation statements such as INSERT and UPDATE

- PL/SQL blocks

However, Pro\*COBOL checks only the syntax of remote data manipulation statements (those using the AT db_name clause).

Pro\*COBOL gets the information for a semantic check from embedded DECLARE TABLE statements or, if you specify the option USERID, by connecting to Oracle and accessing the data dictionary. You need not connect to Oracle if every table referenced in a data manipulation statement or PL/SQL block is defined in a DECLARE TABLE statement.

If you connect to Oracle but some information cannot be found in the data dictionary, you must use DECLARE TABLE statements to supply the missing information. During precompilation, a DECLARE TABLE definition overrides a data dictionary definition if they conflict.

Specify SQLCHECK=SEMANTICS when precompiling new programs. If you embed PL/SQL blocks in a host program, you must specify SQLCHECK=SEMANTICS and the option USERID.

When SQLCHECK=SEMANTICS or FULL, the SQL statements are first locally parsed. The verification of the host and indicator variables, and checking for the validity of SQL identifiers is done by using embedded DECLARE TABLE statement or by connecting to server when userid is specified in command line. Now the parsing is done twice when SQLCHECK = SEMANTICS or FULL once by the precompiler and once by the PL/SQL. When a new syntax is made available by SQL, the precompiler fails on the new syntax before calling PL/SQL interfaces if the local SQL grammar is not updated to accept the new syntax.

When SQLCHECK=SYNTAX, Pro\*COBOL checks the syntax of data manipulation statements. The SQL statements are locally parsed. With this command line option, the precompiler does not verify the table name or column names. When SQLCHECK=SYNTAX, the syntax of the SQL statements is checked by using the client side SQL interface.

No semantic checking is done. DECLARE TABLE statements are ignored and PL/SQL blocks are not allowed. When checking data manipulation statements, Pro\*COBOL uses Oracle syntax rules, which are downwardly compatible. Specify SQLCHECK=SYNTAX when migrating your precompiled programs.

Table 14-5 summarizes the checking done by SQLCHECK. For more information about syntactic and semantic checking, see “Syntactic and Semantic Checking”.

Table 14-5 Checking Done by SQLCHECK

| \-         | SQLCHECK= SEMANTICS | \-        | SQLCHECK=SYNTAX | \-        |
|:-----------|:--------------------|:----------|:----------------|:----------|
| \-         | Syntax              | Semantics | Syntax          | Semantics |
| DML        | X                   | X         | X               | \-        |
| Remote DML | X                   | \-        | X               | \-        |
| PL/SQL     | X                   | X         | \-              | \-        |

##### Restrictions of Unified Parser

The restrictions of unified parser for Pro\*COBOL are:

- Pro\*COBOL does not support variables without a ':' (colon).

- Define tables cannot be used. In CSF mode, plsql fails when `declare table` statement is passed to plsql.

- The following example fails if `sqlcheck=syntax` and `common_parser=yes` is used:

      select ename into :empname from emp@dblink;

  In earlier versions, only local parsing is done when sqlcheck=syntax is used. But now when `sqlcheck=syntax` and `common_parser=yes`, the statement is just bundled and sent to pcisyn(). PLSQL fails if connection is not there when dblinks are used.

  The above statement can be precompiled with:

      sqlcheck=full userid=<userid> common_parser=yes

- Error handling for insert does not follow the usual sequence. Consider the following statement where XYZ is a group item.

      insert into emp (empno, ename) values (:XYZ)

  PLSQL does not allow group items or structures while doing syntax check for insert statements (restriction from PLSQL.). It expects that the group item be broken into the individual elements for inserts. So the precompiler should expand the above statement to `insert into emp (empno, ename) values (:b1,:b2)` in the syntax phase itself.

  This expansion is not possible in syntax phase. Therefore, `pcisyn()` is not called in syntax phase of precompiler the way it is done for other statements. The statement is deferred till semantic phase of precompiler for insert statement only. The net effect is that the error messages might not be following the usual sequence. For example:

      EXEC SQL insert into emp (empno, ename) alues (:XYZ) END-EXEC.
                                               ^^^^^ syntax error at 'alues'
       EXEC SQL select ename into :empname fro emp END-EXEC.
                                           ^^^ syntax error at 'fro'

  Ideally error sequence should be as follows:

      syntax error at 'alues' in INSERT
      syntax error at 'fro' in SELECT

  Because of the restrictions discussed earlier, the error sequence will be:

      syntax error at 'fro' in SELECT
      syntax error at 'alues' in INSERT

  **Note:**

  The line numbers will be there in the reported errors. Therefore, Pro\*Cobol programmers can identify the line very easily, even though it is not in the order used in the program.

**Related Topics**

- [Syntactic and Semantic Checking Basics](syntactic-and-semantic-checking.md)

#### 14.7.55 STMT_CACHE

##### Purpose

Denotes the Statement cache size for the dynamic SQL statements.

##### Syntax

STMT_CACHE = Range is 0 to 65535

##### Default

0

##### Usage Notes

The stmt_cache option can be set to hold the anticipated number of distinct dynamic SQL statements in the application.

#### 14.7.56 TYPE_CODE

##### Purpose

This micro option of MODE specifies whether ANSI or Oracle datatype codes are used in ANSI dynamic SQL method 4. Its setting is the same as the setting of MODE option.

##### Syntax

TYPE_CODE={ORACLE \| ANSI}

##### Default

ORACLE

##### Usage Notes

Cannot be entered inline.

See the possible option settings in “TYPE_CODE Option Settings”.

#### 14.7.57 UNSAFE_NULL

##### Purpose

Specifying UNSAFE_NULL=YES prevents generation of ORA-01405 messages when fetching NULLs without using indicator variables.

##### Syntax

UNSAFE_NULL={YES \| NO}

##### Default

NO

##### Usage Notes

Cannot be entered inline.

The UNSAFE_NULL=YES is allowed only when MODE=ORACLE.

The UNSAFE_NULL option has no effect on host variables in an embedded PL/SQL block. You must use indicator variables to avoid ORA-01405 errors.

When UNSAFE_NULL=YES, no error is returned if a SELECT or FETCH statement selects a NULL, and there is no indicator variable associated with the output host variable. When UNSAFE_NULL=NO, selecting or fetching a NULL column or expression into a host variable that has no associated indicator variable causes an error (SQLSTATE is `22002`; SQLCODE is ORA-01405).

#### 14.7.58 USERID

##### Purpose

Specifies an Oracle username and password.

##### Syntax

USERID=username/password\[@dbname\]

##### Default

None

##### Usage Notes

Cannot be entered inline.

When SQLCHECK=SEMANTICS, if you want Pro\*COBOL to get needed information by connecting to Oracle and accessing the data dictionary, you must also specify USERID. The database alias is optional. Do not enter the brackets.

#### 14.7.59 VARCHAR

##### Purpose

The VARCHAR option instructs Pro\*COBOL to treat the COBOL group item described in “Embedded SQL” as a VARCHAR datatype.

##### Syntax

VARCHAR={YES \| NO}

##### Default

NO

##### Usage Notes

Cannot be entered inline.

When VARCHAR=YES, the implicit group item described in “Embedded SQL” is accepted as a VARCHAR external datatype with a length field and a string field.

When VARCHAR=NO, Pro\*COBOL does not accept the implicit group items as VARCHAR external datatypes.

**Related Topics**

- [Embedded SQL](embedded-SQL.md)

#### 14.7.60 XREF

##### Purpose

Specifies whether a cross-reference section is included in the listing file.

##### Syntax

XREF={YES \| NO}

##### Default

YES

##### Usage Notes

When XREF=YES, cross references are included for host variables, cursor names, and statement names. The cross references show where each object is defined and referenced in your program.

When XREF=NO, the cross-reference section is not included.
