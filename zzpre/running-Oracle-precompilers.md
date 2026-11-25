This chapter contains the following:

- The Precompiler Command

- What Occurs during Precompilation?

- Precompiler Options

- Entering Options

- Scope of Options

- Quick Reference

- About Using the Precompiler Options

- Conditional Precompilations

- Separate Precompilations

- Compiling and Linking

This chapter details the requirements for running the Oracle Precompilers. You learn what occurs during precompilation, how to issue the precompiler command, how to specify the many useful precompiler options, and how to do conditional and separate precompilations.

### 6.1 The Precompiler Command

To run an Oracle Precompiler, you issue one of the language-specific commands shown in Table 6-1.

Table 6-1 Precompiler Run Commands

| Host Language | Precompiler Command |
|:--------------|:--------------------|
| COBOL         | `procob`            |
| FORTRAN       | `profor`            |

The location of the precompiler differs from system to system. Typically, your system manager or DBA defines environment variables, logicals, or aliases or uses other operating system-specific means to make the precompiler executable accessible.

The INAME option specifies the source file to be precompiled. For example, the Pro\*COBOL command

    procob INAME=test

precompiles the file test.pco in the current directory, since the precompiler assumes that the filename extension is .pco. You need not use a file extension when specifying INAME unless the extension is nonstandard.

Input and output filenames need not be accompanied by their respective option names, INAME and ONAME. When the option names are not specified, the precompiler assumes that the first filename specified on the command line is the input filename and that the second filename is the output filename.

Thus, the Pro\*FORTRAN command

    profor MODE=ANSI myfile.pfo DBMS=V7 myfile.f

is equivalent to

    profor MODE=ANSI INAME=myfile.pfo DBMS=V7 ONAME=myfile.f

**Note:**

Option names and option values that do not name specific operating system objects, such as filenames, are not case-sensitive. In the examples in this guide, option names are written in upper case, and option values are usually in lowercase. Filenames, including the name of the precompiler executable itself, always follow the case conventions used by the operating system on which it is executed.

### 6.2 What Occurs during Precompilation?

During precompilation, an Oracle Precompiler generates host-language code that replaces the SQL statements embedded in your host program. The generated code includes data structures that contain the datatype, length, and address of each host variable, and other information required by the Oracle run-time library, SQLLIB. The generated code also contains the calls to SQLLIB routines that perform the embedded SQL operations.

The generated code also includes calls to the SQLLIB routines that perform embedded SQL operations. Note that the precompiler does not generate calls to Oracle Call Interface (OCI) routines.

The precompiler does not generate calls to Oracle Call Interface (OCI) routines.

The precompiler can issue warnings and error messages. These messages have the prefix PCC-, and are described in Oracle Database Error Messages.

### 6.3 Precompiler Options

Many useful options are available at precompile time. They let you control how resources are used, how errors are reported, how input and output are formatted, and how cursors are managed. To specify a precompiler option, use the following syntax:

    <option_name>=<value>

The value of an option is a string literal, which represents text or numeric values. For example, for the option

    ... INAME=my_test

the value is a string literal that specifies a filename, but for the option

    ... MAXOPENCURSORS=20

the value is numeric.

Some options take Boolean values, which you can represent with the strings YES or NO, TRUE or FALSE, or with the integer literals 1 or 0, respectively. For example, the option

    ... SELECT_ERROR=YES

is equivalent to

    ... SELECT_ERROR=TRUE

or

    ... SELECT_ERROR=1

The option value is always separated from the option name by an equal sign, leave no whitespace around the equal sign, because spaces delimit individual options. For example, you might specify the option `AUTO_CONNECT` on the command line as follows:

    ... AUTO_CONNECT=YES

You can abbreviate the names of options if the abbreviation is unambiguous. For example, you cannot use the abbreviation MAX because it might stand for MAXLITERAL or MAXOPENCURSORS.

A handy reference to the precompiler options is available online. To see the online display, enter the precompiler command with no arguments at your operating system prompt. The display gives the name, syntax, default value, and purpose of each option. Options marked with an asterisk (\*) can be specified inline and on the command line.

#### 6.3.1 Default Values

Many of the options have default values, which are determined by:

- A value built in to the precompiler

- A value set in the system configuration file

- A value set in a user configuration file

- A value set in an inline specification

For example, the option MAXOPENCURSORS specifies the maximum number of cached open cursors. The built-in precompiler default value for this option is 10. However, if MAXOPENCURSORS=32 is specified in the system configuration file, the default becomes 32. The user configuration file could set it to yet another value, which then overrides the system configuration value.

Then, if this option is set on the command line, the new command-line value takes precedence. Finally, an inline specification takes precedence over all preceding defaults. For more information, refer to Configuration Files".

#### 6.3.2 Determining Current Values

You can interactively determine the current value for one or more options by using a question mark on the command line. For example, if you issue the Pro\*COBOL command

    procob ?

the complete option set, along with current values, is displayed on your terminal. In this case, the values are those built into the precompiler, overridden by any values in the system configuration file. But if you issue the following command

    procob CONFIG=my_config_file.cfg ?

and there is a file named my_config_file.cfg in the current directory, the options from the my_config_file.cfg file are listed with the other default values. Values in the user configuration file supply missing values, and they supersede values built into the precompiler or values specified in the system configuration file.

You can also determine the current value of a single option by simply specifying the option name followed by "=?" as in

    procob MAXOPENCURSORS=?

**Note:**

: With some operating systems, the "?" may need to be preceded by an "escape" character, such as a back-slash (\\. For example, instead of "procob ?," you might need to use "procob \\" to list the Pro\*COBOL option settings.

#### 6.3.3 Case Sensitivity

In general, you can use either uppercase or lowercase for command-line option names and values. However, if your operating system is case-sensitive, like UNIX, you must specify filename values, including the name of the precompiler executable, using the correct combination of upper and lowercase letters.

#### 6.3.4 Configuration Files

A configuration file is a text file that contains precompiler options. Each record (line) in the file contains one option, with its associated value or values. For example, a configuration file might contain the lines

    FIPS=YES
    MODE=ANSI

to set defaults for the `FIPS` and `MODE` options.

There is a single system configuration file for each system. The name of the system configuration file is precompiler-specific and is shown in Table 6-2.

Table 6-2 System Configuration Files

| Precompiler  | Configuration File |
|:-------------|:-------------------|
| Pro\*COBOL   | `pcbcfg.cfg`       |
| Pro\*FORTRAN | `pccfor.cfg`       |

The location of the file is operating system-specific. On most UNIX systems, the Pro\*COBOL configuration file is usually located in the \$ORACLE_HOME/procob directory, and the Pro\*FORTRAN equivalent is in the \$ORACLE_HOME/profor directory, where \$ORACLE_HOME is the environment variable for the database software.

Each precompiler user can have one or more user configuration files. The name of the configuration file must be specified using the `CONFIG` command-line option. For more information, refer to Determining Current Values.

**Note:**

You cannot nest configuration files. CONFIG is not a valid option inside a configuration file.

### 6.4 Entering Options

All the precompiler options can be entered on the command line or (except `CONFIG`) from a configuration file. Many options can also be entered inline. During a given run, the precompiler can accept options from all three sources.

#### 6.4.1 On the Command Line

You enter precompiler options on the command line using the following syntax:

    ... [option_name=value] [option_name=value] ...

Separate each option with one or more spaces. For example, you might enter the following options:

    ... ERRORS=no LTYPE=short

#### 6.4.2 Inline

You enter options inline by coding `EXEC ORACLE `statements, using the following syntax:

    EXEC ORACLE OPTION (option_name=value);

For example, you might code the following statement:

    EXEC ORACLE OPTION (RELEASE_CURSOR=YES);

An option entered inline overrides the same option entered on the command line.

#### 6.4.3 Advantages

The `EXEC ORACLE` feature is especially useful for changing option values during precompilation. For example, you might want to change the `HOLD_CURSOR` and `RELEASE_CURSOR` values on a statement-by-statement basis. [Performance Tuning](performance-tuning.md) shows you how to use inline options to optimize run-time performance.

Specifying options inline is also helpful if your operating system limits the number of characters you can enter on the command line, and you can store inline options in configuration files, which are discussed in the next section.

#### 6.4.4 Scope of EXEC ORACLE

An EXEC ORACLE statement stays in effect until textually superseded by another EXEC ORACLE statement specifying the same option. In the following example, `HOLD_CURSOR=NO` stays in effect until superseded by `HOLD_CURSOR=YES:`

    EXEC SQL BEGIN DECLARE SECTION;
     emp_name CHARACTER(20);
     emp_number INTEGER;
     salary REAL;
     dept_number INTEGER;
    EXEC SQL END DECLARE SECTION;
    ...
    EXEC SQL WHENEVER NOT FOUND GOTO no_more;
    EXEC ORACLE OPTION (HOLD_CURSOR=NO);
    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT EMPNO, DEPTNO FROM EMP;
    EXEC SQL OPEN emp_cursor;
    display 'Employee Number Dept';
    display '--------------- ----';
    LOOP
     EXEC SQL FETCH emp_cursor INTO :emp_number, :dept_number;
     display emp_number, dept_number;
    ENDLOOP;
    no_more:
     EXEC SQL WHENEVER NOT FOUND CONTINUE;
     LOOP
     display 'Employee number? ';
     read emp_number;
     IF emp_number = 0 THEN
     exit loop;
     EXEC ORACLE OPTION (HOLD_CURSOR=YES);
     EXEC SQL SELECT ENAME, SAL
     INTO :emp_name, :salary
     FROM EMP
     WHERE EMPNO = :emp_number;
     display 'Salary for ', emp_name, ' is ', salary;
     ENDLOOP;
    ...

#### 6.4.5 From a Configuration File

The Oracle Precompilers can use a configuration file containing preset command-line options. By default, a text file called the system configuration file is used. However, you can specify any of several alternative files, called user configuration files, on the command line.

#### 6.4.6 Advantages

Configuration files offer several advantages. The system configuration file lets you standardize a set of options for all projects. User configuration files let you customize a set of options for each project. With configuration files, you need not enter long strings of options on the command line. Also, if your system limits the length of a command line, configuration files let you specify more options than the command line can hold.

#### 6.4.7 About Using Configuration Files

Each record (line) in a configuration file holds one command-line option. For example, a configuration file might contain the following lines, which set defaults for the `FIPS`, `MODE`, and SQLCHECK options:

    FIPS=YES
    MODE=ANSI
    SQLCHECK=SEMANTICS

Each Oracle Precompiler can have its own system configuration file. The name and location of the file are language- and system-specific. If the file is not found, you get a warning but the precompiler continues processing.

There is only one system configuration file for a given language, but you can create any number of user configuration files. You use the new command-line option CONFIG to specify the name and location of a particular user configuration file, as follows:

    ... CONFIG=<filename>

You cannot nest configuration files. Therefore, you cannot specify the `CONFIG` option in a configuration file. Also, you cannot specify `CONFIG` inline.

#### 6.4.8 About Setting Option Values

Many precompiler run-time options have built-in default values, which can be reset in a configuration file or on the command line. Command-line settings override user configuration file settings, which override system configuration file settings.

### 6.5 Scope of Options

A precompilation unit is a file containing host-language code and one or more embedded SQL statements. The options specified for a given precompilation unit affect only that unit; they have no effect on other units.

For example, if you specify `HOLD_CURSOR=YES` and `RELEASE_CURSOR=YES` for unit A but not unit B, SQL statements in unit A run with these `HOLD_CURSOR` and `RELEASE_CURSOR` values, but SQL statements in unit B run with the default values. However, the MAXOPENCURSORS setting that is in effect when you connect to Oracle stays in effect for the life of that connection.

The scope of an inline option is positional, not logical. That is, an inline option affects SQL statements that follow it in the source file, not in the flow of program logic. An option setting stays in effect until the end-of-file unless you re-specify the option.

### 6.6 Quick Reference

Table 6-3 is a quick reference to the precompiler options. The options marked with an asterisk can be entered inline.

Another handy reference is available online. To see the online display, just enter the precompiler command without options at your operating system prompt. The display provides the name, syntax, default value, and purpose of each option.

There are some platform-specific options. For example, on byte-swapped platforms that use MicroFocus COBOL, the option COMP5 governs the use of certain COMPUTATIONAL items. Check your system-specific Oracle manuals.

Table 6-3 Precompiler Options Quick Reference

| Syntax                                             | Default                 | Specifies ...                                                                                                                                                                                                                                         |
|:---------------------------------------------------|:------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ASACC={YES\|NO}                                    | NO                      | carriage control for listing                                                                                                                                                                                                                          |
| ASSUME_SQLCODE={YES\|NO}                           | NO                      | precompiler presumes that SQLCODE is declared                                                                                                                                                                                                         |
| AUTO_CONNECT={YES\|NO}                             | NO                      | automatic logon                                                                                                                                                                                                                                       |
| CHAR_MAP={VARCHAR2 \| CHARZ \| STRING \| CHARF} \* | CHARZ                   | mapping of character arrays and strings                                                                                                                                                                                                               |
| CHARSET_PICN={NCHAR_CHARSET \| DB_CHARSET }        | NCHAR_CHARSET           | the character set form used by PIC N variables                                                                                                                                                                                                        |
| CHARSET_PICX={NCHAR_CHARSET \| DB_CHARSET }        | DB_CHARSET              | the character set form used by PIC X variables                                                                                                                                                                                                        |
| CINCR                                              | 1                       | CINCR value for connection pool. Allows the application to set the next increment for physical connections to be opened to the database, if the current number of physical connections is less than CMAX                                              |
| CLOSE_ON_COMMIT={YES \| NO}                        | NO                      | close all cursors on COMMIT                                                                                                                                                                                                                           |
| CMAX                                               | 100                     | specifies the maximum number of physical connections that can be opened for the database                                                                                                                                                              |
| CMIN                                               | 2                       | specifies the minimum number of physical connections in the connection pool.                                                                                                                                                                          |
| CNOWAIT                                            | 0 (which means not set) | determines if the application must repeatedly try for a physical connection when all other physical connections in the pool are busy, and the total number of physical connections has already reached its maximum. CNOWAIT Value for connection pool |
| CODE={ANSI_C \| KR_C \| CPP}                       | KR_C                    | type of C code to be generated                                                                                                                                                                                                                        |
| COMMON_NAME=block_name \*                          |                         | name of FORTRAN COMMON blocks                                                                                                                                                                                                                         |
| COMMON_PARSER                                      | NO                      | parse using Common SQL Front End                                                                                                                                                                                                                      |
| COMP5                                              | YES                     | generate COMP-5 rather than COMP variables                                                                                                                                                                                                            |
| COMP_CHARSET={MULTI_BYTE \| SINGLE_BYTE}           | MULTI_BYTE              | the character set type the C/C++ compiler supports.                                                                                                                                                                                                   |
| CONFIG=filename                                    |                         | name of user configuration file                                                                                                                                                                                                                       |
| CPOOL                                              | NO                      | support connection pooling. Based on this option, the precompiler generates the appropriate code that directs SQLLIB to enable or disable the connection pool feature                                                                                 |
| CPP_SUFFIX=extension                               | \*none\*                | override the default C++ filename extension                                                                                                                                                                                                           |
| CTIMEOUT                                           | 0                       | physical connections that are idle for more than the specified time (in seconds) are terminated to maintain an optimum number of open physical connections                                                                                            |
| DB2_ARRAY={YES \|NO}                               | NO                      | support DB2 array insert/select syntax. Based on this option, the precompiler activates the additional array insert/select syntax                                                                                                                     |
| DBMS={NATIVE\|V7\|V8}                              | NATIVE                  | version-specific behavior of Oracle at precompile time                                                                                                                                                                                                |
| DECLARE_SECTION                                    | NO                      | if YES, DECLARE SECTION is required                                                                                                                                                                                                                   |
| DEF_SQLCODE={NO \| YES}                            | NO                      | controls whether the Pro\*C/C++ precompiler generates \#define's for SQLCODE                                                                                                                                                                          |
| DEFINE=symbol \*                                   |                         | symbol used in conditional precompilation                                                                                                                                                                                                             |
| DURATION={TRANSACTION \| SESSION}                  | TRANSACTION             | set pin duration for objects in the cache                                                                                                                                                                                                             |
| DYNAMIC={ANSI \| ORACLE}                           | ORACLE                  | specify Oracle or ANSI SQL semantics.                                                                                                                                                                                                                 |
| END_OF_FETCH                                       | 1403                    | end-of-fetch SQLCODE value                                                                                                                                                                                                                            |
| ERRORS={YES\|NO} \*                                | YES                     | whether errors are sent to the terminal                                                                                                                                                                                                               |
| ERRTYPE=filename                                   | \*none\*                | name of the list file for intype file errors                                                                                                                                                                                                          |
| EVENTS                                             | NO                      | support publish-subscribe event notifications                                                                                                                                                                                                         |
| FILE_ID                                            | 0                       | unique numeric identifier for the generated COBOL file                                                                                                                                                                                                |
| FIPS={YES\|NO}\*                                   | NO                      | whether ANSI/ISO extensions are flagged                                                                                                                                                                                                               |
| FORMAT={ANSI\|TERMINAL}                            | ANSI                    | format of COBOL or FORTRAN input line                                                                                                                                                                                                                 |
| Globalization Support_LOCAL={YES\|NO}              | YES                     | blank-padding operations to be preformed by SQLLIB                                                                                                                                                                                                    |
| HEADER=extension                                   | \*none\*                | name of the listing file for intype file error messages                                                                                                                                                                                               |
| HOLD_CURSOR={YES\|NO}\*                            | NO                      | how cursor cache handles SQL statements                                                                                                                                                                                                               |
| HOST={COBOL\|COB74}                                | COBOL                   | COBOL version of input file                                                                                                                                                                                                                           |
| IMPLICIT_SVPT                                      | NO                      | implicit savepoint before buffered insert                                                                                                                                                                                                             |
| \[INAME=\]filename                                 |                         | name of input file                                                                                                                                                                                                                                    |
| INCLUDE=path\*                                     |                         | directory path for INCLUDEd files                                                                                                                                                                                                                     |
| INTYPE=filename                                    | \*none\*                | name of the input file for type information                                                                                                                                                                                                           |
| IRECLEN=integer                                    | 80                      | record length of input file                                                                                                                                                                                                                           |
| LINES={YES \| NO}                                  | NO                      | whether \#line directives are generated                                                                                                                                                                                                               |
| LITDELIM={APOST\|QUOTE} \*                         | QUOTE                   | delimiter for COBOL strings                                                                                                                                                                                                                           |
| LNAME=filename                                     |                         | name of listing file                                                                                                                                                                                                                                  |
| LRECLEN=integer                                    | 132                     | record length of listing file                                                                                                                                                                                                                         |
| LTYPE={LONG\|SHORT\|NONE}                          | LONG                    | type of listing                                                                                                                                                                                                                                       |
| MAXLITERAL=integer \*                              | platform-specific       | maximum length of strings                                                                                                                                                                                                                             |
| MAXOPENCURSORS=integer \*                          | 10                      | maximum number of cursors cached                                                                                                                                                                                                                      |
| MAX_ROW_INSERT                                     | 0                       | maximum number of rows to buffer on insert                                                                                                                                                                                                            |
| MODE={ORACLE\|ANSI\|ANSI14\|ANSI13}                | ORACLE                  | compliance with the ANSI/ISO SQL standard                                                                                                                                                                                                             |
| MULTISUBPROG={YES\|NO}                             | YES                     | whether FORTRAN COMMON blocks are generated                                                                                                                                                                                                           |
| NATIVE_TYPES                                       | NO                      | support for native float/double                                                                                                                                                                                                                       |
| NESTED={YES \| NO}                                 | YES                     | if YES, nested programs are supported                                                                                                                                                                                                                 |
| NLS_CHAR=(var1, ..., varn)                         | \*none\*                | specify multibyte character variables                                                                                                                                                                                                                 |
| NLS_LOCAL={YES \| NO}                              | NO                      | if YES, use NCHAR semantics of previous Pro\*COBOL releases                                                                                                                                                                                           |
| OBJECTS={YES \| NO}                                | YES                     | Support of object types                                                                                                                                                                                                                               |
| OUTLINE                                            | NO                      | category in which Outlines are created                                                                                                                                                                                                                |
| OUTLNPREFIX                                        | \*none\*                | outline name prefix                                                                                                                                                                                                                                   |
| \[ONAME=\]filename                                 |                         | name of output file                                                                                                                                                                                                                                   |
| ORACA={YES\|NO}\*                                  | NO                      | whether the ORACA is used                                                                                                                                                                                                                             |
| ORECLEN=integer                                    | 80                      | record length of output file                                                                                                                                                                                                                          |
| PAGELEN=integer                                    | 66                      | lines in each page in listing                                                                                                                                                                                                                         |
| PARSE={NONE \| PARTIAL \| FULL}                    | FULL                    | whether Pro\*C/C++ parses (with a C parser) the.pc source                                                                                                                                                                                             |
| PICN_ENDIAN                                        | BIG                     | endianness in PIC N host variables                                                                                                                                                                                                                    |
| PICX                                               | CHARF                   | datatype of PIC X COBOL variables.                                                                                                                                                                                                                    |
| PREFETCH=0..65535                                  | 1                       | speed up queries by pre-fetching a given number of rows                                                                                                                                                                                               |
| RELEASE_CURSOR={YES\|NO} \*                        | NO                      | how cursor cache handles SQL statements                                                                                                                                                                                                               |
| RUNOUTLINE                                         | NO                      | create Outlines in the database                                                                                                                                                                                                                       |
| SELECT_ERROR={YES\|NO}\*                           | YES                     | how SELECT errors are handled                                                                                                                                                                                                                         |
| SQLCHECK={FULL\|SYNTAX\|LIMITED\|NONE}\*           | SYNTAX                  | extent of syntactic and semantic checking                                                                                                                                                                                                             |
| STMT_CACHE                                         | 0                       | size of statement cache                                                                                                                                                                                                                               |
| SYS_INCLUDE=pathname                               | none                    | directory where system header files, such as iostream.h, are found                                                                                                                                                                                    |
| THREADS={YES \| NO}                                | NO                      | indicates a shared server application                                                                                                                                                                                                                 |
| TYPE_CODE={ORACLE \| ANSI}                         | ORACLE                  | use of Oracle or ANSI type codes for dynamic SQL                                                                                                                                                                                                      |
| UNSAFE_NULL={YES\|NO}                              | NO                      | disables the ORA-01405 message                                                                                                                                                                                                                        |
| USERID=username/password                           |                         | valid Oracle username and password                                                                                                                                                                                                                    |
| UTF16_CHARSET={NCHAR_CHARSET \| DB_CHARSET}        | NCHAR_CHARSET           | specify the character set form used by UNICODE(UTF16)                                                                                                                                                                                                 |
| VARCHAR={YES\|NO}                                  | NO                      | recognize implicit VARCHAR group items in COBOL                                                                                                                                                                                                       |
| VERSION={ANY \| LATEST \| RECENT} \*               | RECENT                  | Which version of an object is to be returned                                                                                                                                                                                                          |
| XREF={YES\|NO}\*                                   | YES                     | cross reference section in listing                                                                                                                                                                                                                    |

### 6.7 About Using the Precompiler Options

This section is organized for easy reference. It lists the precompiler options alphabetically, and for each option provides its purpose, syntax, and default value. Usage notes that help you understand how the option works are also provided. Unless the usage notes say otherwise, the option can be entered on the command line, inline, or from a configuration file.

#### 6.7.1 ASACC

##### Purpose

Specifies whether the listing file follows the ASA convention of using the first column in each line for carriage control.

##### Syntax

`ASACC={YES|NO`}

##### Default

`NO`

##### Usage Notes

Cannot be entered inline.

#### 6.7.2 ASSUME_SQLCODE

##### Purpose

Instructs the Oracle Precompiler to presume that SQLCODE is declared irrespective of whether it is declared in the Declare Section or of the proper type. ASSUME_SQLCODE=YES causes Releases 1.6 and later of the Oracle Precompilers to behave similarly to Release 1.5 in this respect.

##### Syntax

`ASSUME_SQLCODE={YES|NO`}

##### Default

NO

##### Usage Notes

Cannot be entered inline.

When `ASSUME_SQLCODE=NO`, `SQLCODE` is recognized as a status variable if and only if at least one of the following criteria is satisfied:

- It is declared in a Declare Section with exactly the right datatype.

- The precompiler finds no other status variable.

If the precompiler finds a SQLSTATE declaration (of exactly the right type of course) in a Declare Section or finds an `INCLUDE` of the SQLCA, it will not presume SQLCODE is declared.

When `ASSUME_SQLCODE=YES`, and when SQLSTATE and SQLCA (Pro\*FORTRAN only) are declared as status variables, the precompiler presumes SQLCODE is declared whether it is declared in a Declare Section or of the proper type. This causes Releases 1.6.7 and later to behave like Release 1.5 in this regard.

#### 6.7.3 AUTO_CONNECT

##### Purpose

Specifies whether your program connects automatically to the default user account.

##### Syntax

`AUTO_CONNECT={YES|NO}`

##### Default

`NO`

##### Usage Note

Cannot be entered inline.

When `AUTO_CONNECT=YES`, as soon as the precompiler encounters an executable SQL statement, your program tries to log on to Oracle automatically with the userid

    <prefix><username>

where prefix is the value of the Oracle initialization parameter` OS_AUTHENT_PREFIX` (the default value is null) and username is your operating system user or task name. In this case, you cannot override the default value for MAXOPENCURORS (10), even if you specify a different value on the command line.

When `AUTO_CONNECT=NO` (the default), you must use the `CONNECT` statement to log on to Oracle.

#### 6.7.4 CHAR_MAP

##### Purpose

Specifies the default mapping of C host variables of type char or char\[n\], and pointers to them, into SQL.

##### Syntax

CHAR_MAP={VARCHAR2 \| CHARZ \| STRING \| CHARF}

##### Default

CHARZ

##### Usage Note

In earlier releases, you had to declare char or char\[n\] host variables as CHAR, using the SQL DECLARE statement. The external datatypes VARCHAR2 and CHARZ were the default character mappings of Oracle Database version 7.

#### 6.7.5 CINCR

##### Purpose

Allows the application to set the next increment for physical connections to be opened to the database.

##### Syntax

CINCR = Range is 1 to (CMAX-CMIN).

##### Default

1

##### Usage Notes

Initially, all physical connections as specified through CMIN are opened to the server. Subsequently, physical connections are opened only when necessary. Users should set CMIN to the total number of planned or expected concurrent statements to be run by the application to get optimum performance. The default value is set to 2.

#### 6.7.6 CLOSE_ON_COMMIT

##### Purpose

Specifies whether to close cursors on a commit statement.

##### Syntax

CLOSE_ON_COMMIT={YES \| NO}

##### Default

NO

##### Usage Notes

Can be used only on the command line or in a configuration file.

If MODE is specified at a higher level than CLOSE_ON_COMMIT, then MODE takes precedence. For example, the defaults are MODE=ORACLE and CLOSE_ON_COMMIT=NO. If the user specifies MODE=ANSI on the command line, then any cursors will be closed on commit.

When CLOSE_ON_COMMIT=NO (when MODE=ORACLE), issuing a COMMIT or ROLLBACK will close only cursors that are declared using the FOR UPDATE clause or are referenced in a CURRENT OF clause. Other cursors that are not affected by the COMMIT or ROLLBACK statement, remain open, if they are open already. However, when CLOSE_ON_COMMIT=YES (when MODE=ANSI), issuing a COMMIT or ROLLBACK closes all cursors.

#### 6.7.7 CMAX

##### Purpose

Specifies the maximum number of physical connections that can be opened for the database.

##### Syntax

CINCR = Range is 1 to 65535

##### Default

100

##### Usage Notes

CMAX value must be at least CMIN+CINCR.After this value is reached, more physical connections cannot be opened.In a typical application, running 100 concurrent database operations is more than sufficient. The user can set an appropriate value.

#### 6.7.8 CMIN

##### Purpose

Specifies the minimum number of physical connections that can be opened for the database.

##### Syntax

CINCR = Range is 1 to (CMAX-CINCR).

##### Default

2

##### Usage Notes

CMAX value must be at least CMIN+CINCR.After this value is reached, more physical connections cannot be opened.In a typical application, running 100 concurrent database operations is more than sufficient. The user can set an appropriate value.

#### 6.7.9 CNOWAIT

##### Purpose

This attribute determines if the application must repeatedly try for a physical connection when all other physical connections in the pool are busy, and the total number of physical connections has already reached its maximum.

##### Syntax

CNOWAIT = Range is 1 to 65535.

##### Default

0 which means not set.

##### Usage Notes

If physical connections are not available and no more physical connections can be opened, an error is thrown when this attribute is set. Otherwise, the call waits until it acquires another connection. By default, CNOWAIT is not to be set so a thread will wait until it can acquire a free connection, instead of returning an error.

#### 6.7.10 CODE

##### Purpose

Specifies the format of C function prototypes generated by the Pro\*C/C++ precompiler. (A function prototype declares a function and the datatypes of its arguments.) The precompiler generates function prototypes for SQL library routines, so that your C compiler can resolve external references. The CODE option lets you control the prototyping.

##### Syntax

CODE={ANSI_C \| KR_C \| CPP}

##### Default

KR_C

##### Usage Notes

Can be entered on the command line, but not inline.

ANSI C standard X3.159-1989 provides for function prototyping. When CODE=ANSI_C, Pro\*C/C++ generates full function prototypes, which conform to the ANSI C standard. An example follows:

    extern void sqlora(long *, void *);

The precompiler can also generate other ANSI-approved constructs such as the const type qualifier.

When CODE=KR_C (the default), the precompiler comments out the argument lists of generated function prototypes, as shown here:

    extern void sqlora(/*_ long *, void * _*/);

Specify CODE=KR_C if your C compiler is not compliant with the X3.159 standard.

When CODE=CPP, the precompiler generates C++ compatible code.

#### 6.7.11 COMMON_NAME

##### Purpose

For Pro\*FORTRAN only, the `COMMON_NAME` option specifies a prefix used to name internal FORTRAN `COMMON` blocks. Your host program does not access the `COMMON` blocks directly. But, they allow two or more program units in the same precompilation unit to contain SQL statements.

##### Syntax

`COMMON_NAME=``blockname`

##### Default

First five characters in name of input file

##### Usage Notes

The Pro\*FORTRAN Precompiler uses a special program file called a block data subprogram to establish `COMMON` blocks for all the SQL variables in an input file. The block data subprogram defines two COMMON blocks -- one for CHARACTER variables, the other for non-CHARACTER variables -- and uses DATA statements to initialize the variables.

The format of a block data subprogram follows:

    BLOCK DATA <subprogram_name>
    variable declarations
    COMMON statements
    DATA statements
    END

Your host program does not access the `COMMON` blocks directly. But, they allow two or more program files in the same precompilation file to contain SQL statements.

To name the `COMMON` blocks, the precompiler uses the name of the input file and the suffixes C, D, and I. At most, the first five characters of the filename are used. For example, if the name of the input file is `ACCTSPAY`, the precompiler names the `COMMON` blocks `ACCTSC`, `ACCTSD`, and `ACCTSI`.

The precompiler, however, can give `COMMON` blocks defined in different output files the same name, as the following schematic shows:

    ACCTSPAY.PFO ===> ACCTSC, ACCTSD, ACCTSI in ACCTSPAY.FOR
    ACCTSREC.PFO ===> ACCTSC, ACCTSD, ACCTSI in ACCTSREC.FOR

If you were to link `ACCTSPAY` and `ACCTSREC` into an executable program, the linker would see three, not six, `COMMON` blocks.

To solve the problem, you can rename the input files, or you can override the default `COMMON` block names by specifying `COMMON_NAME` inline or on the command line as follows:

    COMMON_NAME=<block_name>

where block_name is a legal `COMMON` block name. For example, if you specify `COMMON_NAME=PAY`, the precompiler names its `COMMON` blocks `PAYC` and `PAYI`. At most, the first five characters in block_name are used.

For example, if you specify `COMMON_NAME=PAY`, the precompiler names its COMMON blocks `PAYC` and `PAYI`. At most, the first 5 characters in block_name are used.

If you specify COMMON_NAME inline, its `EXEC ORACLE OPTION` statement must precede the FORTRAN PROGRAM, `SUBROUTINE`, or `FUNCTION` statement.

You might want to override the default `COMMON` block names if they conflict with your user-defined `COMMON` block names. However, the preferred practice is to rename the user-defined `COMMON` blocks.

`COMMON_NAME` is not needed if you specify MULTISUBPROG.

#### 6.7.12 COMMON_PARSER

##### Purpose

Specifies that the SQL99 syntax for SELECT, INSERT, DELETE, UPDATE and body of the cursor in a DECLARE CURSOR statement will be supported.

##### Syntax

COMMON_PARSER={YES \| NO}

##### Default

NO

##### Usage Notes

Can be entered in the command line.

#### 6.7.13 COMP_CHARSET

##### Purpose

Indicates to the Pro\*C/C++ Precompiler whether multibyte character sets are (or are not) supported by the compiler to be used. It is intended for use by developers working in a multibyte client-side environment (for example, when NLS_LANG is set to a multibyte character set).

##### Syntax

COMP_CHARSET={MULTI_BYTE \| SINGLE_BYTE}

##### Default

MULTI_BYTE

##### Usage Notes

Can be entered only on the command line.

With COMP_CHARSET=MULTI_BYTE (default), Pro\*C/C++ generates C code that is to be compiled by a compiler that supports multibyte character sets.

With COMP_CHARSET=SINGLE_BYTE, Pro\*C/C++ generates C code for single-byte compilers that addresses a complication that may arise from the ASCII equivalent of a backslash (\\ character in the second byte of a double-byte character in a multibyte string. In this case, the backslash (\\ character is "escaped" with another backslash character preceding it.

**Note:**

The need for this feature is common when developing in a Shift-JIS environment with older C compilers.

This option has no effect when NLS_LANG is set to a single-byte character set.

#### 6.7.14 COMP_CHARSET

##### Purpose

Indicates to the Pro\*C/C++ Precompiler whether multibyte character sets are (or are not) supported by the compiler to be used. It is intended for use by developers working in a multibyte client-side environment (for example, when NLS_LANG is set to a multibyte character set).

##### Syntax

COMP_CHARSET={MULTI_BYTE \| SINGLE_BYTE}

##### Default

MULTI_BYTE

##### Usage Notes

Can be entered only on the command line.

With COMP_CHARSET=MULTI_BYTE (default), Pro\*C/C++ generates C code that is to be compiled by a compiler that supports multibyte character sets.

With COMP_CHARSET=SINGLE_BYTE, Pro\*C/C++ generates C code for single-byte compilers that addresses a complication that may arise from the ASCII equivalent of a backslash (\\ character in the second byte of a double-byte character in a multibyte string. In this case, the backslash (\\ character is "escaped" with another backslash character preceding it.

**Note:**

The need for this feature is common when developing in a Shift-JIS environment with older C compilers.

This option has no effect when NLS_LANG is set to a single-byte character set.

#### 6.7.15 CONFIG

##### Purpose

Specifies the name of a user configuration file.

##### Syntax

`CONFIG=``filename`

##### Default

`None`

##### Usage Notes

Can be entered only on the command line.

The Oracle Precompilers can use a configuration file containing preset command-line options. By default, a text file called the system configuration file is used. However, you can specify any of several alternative files, called user configuration files.

You cannot nest configuration files. Therefore, you cannot specify the option `CONFIG` in a configuration file.

#### 6.7.16 CPOOL

##### Purpose

Based on this option, the precompiler generates the appropriate code that directs SQLLIB to enable or disable the connection pool feature.

##### Syntax

CPOOL = {YES\|NO}

##### Default

NO

##### Usage Notes

If this option is set to NO, other connection pooling options will be ignored by the precompiler.

#### 6.7.17 CPP_SUFFIX

##### Purpose

The CPP_SUFFIX option provides the ability to specify the filename extension that the precompiler appends to the C++ output file generated when the CODE=CPP option is specified.

##### Syntax

CPP_SUFFIX=filename_extension

##### Default

System-specific.

##### Usage Notes

Most C compilers expect a default extension of ".c" for their input files. Different C++ compilers, however, can expect different filename extensions. The CPP_SUFFIX option provides the ability to specify the filename extension that the precompiler generates. The value of this option is a string, without the quotes or the period. For example, CPP_SUFFIX=cc, or CPP_SUFFIX=C.

#### 6.7.18 CTIMEOUT

##### Purpose

Physical connections that are idle for more than the specified time (in seconds) are terminated to maintain an optimum number of open physical connections

##### Syntax

CTIMEOUT = Range is 1 to 65535.

##### Default

0 which means not set.

##### Usage Notes

Physical connections will not be closed until the connection pool is terminated.Creating a new physical connection will cost a round trip to the server.

#### 6.7.19 DB2_ARRAY

##### Purpose

Based on this option, the precompiler activates the additional array insert/select syntax.

##### Syntax

DB2_ARRAY={YES \|NO}

##### Default

NO

##### Usage Notes

If this option is set to NO, the Oracle precompiler syntax is supported, otherwise the DB2 insert/select array syntax is supported.

#### 6.7.20 DBMS

##### Purpose

Specifies whether Oracle follows the semantic and syntactic rules of Oracle9i, Oracle8i, Oracle8, Oracle7, or the native version of Oracle (that is, the version to which your application is connected).

##### Syntax

`DBMS={NATIVE|V7|V8}`

##### Default

`NATIVE`

##### Usage Notes

Cannot be entered inline.

Using the DBMS option, you can control the version-specific behavior of Oracle. When DBMS=NATIVE (the default), Oracle follows the semantic and syntactic rules of the native version of Oracle.

When DBMS=V8, or DBMS=V7, Oracle follows the respective rules for Oracle9i (which remain the same as for Oracle7, Oracle8, and Oracle8i).

Table 6-4 shows how the compatible `DBMS` and `MODE` settings interact. All other combinations are incompatible or not recommended.

Table 6-4 Compatible DBMS and MODE Settings

| Situation                                                                                                        | DBMS=V7/V8 MODE=ANSI           | DBMS=V7/V8 MODE=ORACLE         |
|:-----------------------------------------------------------------------------------------------------------------|:-------------------------------|:-------------------------------|
| "no data found" warning code                                                                                     | +100                           | +1403                          |
| fetch nulls without using indicator variables                                                                    | error -1405                    | error -1405                    |
| fetch truncated values without using indicator variables                                                         | no error but SQLWARN(2) is set | no error but SQLWARN(2) is set |
| cursors closed by COMMIT or ROLLBACK                                                                             | all explicit                   | CURRENT OF only                |
| open an already OPENed cursor                                                                                    | error -2117                    | no error                       |
| close an already CLOSEd cursor                                                                                   | error -2114                    | no error                       |
| SQL group function ignores nulls                                                                                 | no warning                     | no warning                     |
| when SQL group function in multirow query is called                                                              | FETCH time                     | FETCH time                     |
| declare SQLCA structure                                                                                          | optional                       | required                       |
| declare SQLCODE or SQLSTATE status variable                                                                      | required                       | optional but Oracle ignores    |
| default external datatype of character host variables external datatype used for CHAR in TYPE and VAR statements | CHARF                          | VARCHAR2                       |
| default external datatype of string literals in SQL statements                                                   | CHARF                          | CHARF                          |
| default internal datatype of CHAR variables in SQL statements                                                    | CHAR                           | CHAR                           |
| default external datatype of CHAR variables in PL/SQL blocks                                                     | CHARF                          | CHARF                          |
| default external datatype of value function USER returns                                                         | CHARF                          | CHARF                          |
| external datatype code DESCRIBE returns (dynamic SQL Method 4)                                                   | 96                             | 96                             |
| integrity constraints                                                                                            | enabled                        | enabled                        |
| PCTINCREASE for rollback segments                                                                                | not allowed                    | not allowed                    |
| MAXEXTENTS storage parameters                                                                                    | not allowed                    | not allowed                    |

#### 6.7.21 DEF_SQLCODE

##### Purpose

Controls whether the Pro\*C/C++ precompiler generates \#define's for SQLCODE.

##### Syntax

DEF_SQLCODE={NO \| YES}

##### Default

NO

##### Usage Notes

Can be used only on the command line or in a configuration file.

When DEF_SQLCODE=YES, the precompiler defines SQLCODE in the generated source code as follows:

    #define SQLCODE sqlca.sqlcode

You can then use SQLCODE to check the results of executable SQL statement. The DEF_SQLCODE option is supplied for compliance with standards that require the use of SQLCODE.

In addition, you must also include the SQLCA using one of the following entries in your source code:

    #include <sqlca.h>

or

    EXEC SQL INCLUDE SQLCA;

If the SQLCA is not included, using this option causes a precompile time error.

#### 6.7.22 DEFINE

##### Purpose

Specifies a user-defined symbol that is used to include or exclude portions of source code during a conditional precompilation.

##### Syntax

`DEFINE=``symbol`

##### Default

`None`

##### Usage Notes

If you enter `DEFINE` inline, the EXEC ORACLE statement takes the following form:

    EXEC ORACLE DEFINE <symbol>;

#### 6.7.23 DURATION

##### Purpose

Sets the pin duration used by subsequent EXEC SQL OBJECT CREATE and EXEC SQL OBJECT DEREF statements. Objects in the cache are implicitly unpinned at the end of the duration.

##### Syntax

DURATION={TRANSACTION \| SESSION}

##### Default

TRANSACTION

##### Usage Notes

Can be entered inline by use of the EXEC ORACLE OPTION statement.

TRANSACTION means that objects are implicitly unpinned when the transaction completes.

SESSION means that objects are implicitly unpinned when the connection is terminated.

#### 6.7.24 DYNAMIC

##### Purpose

This micro option specifies the descriptor behavior in dynamic SQL Method 4. The setting of MODE determines the setting of DYNAMIC.

##### Syntax

DYNAMIC={ORACLE \| ANSI}

##### Default

ORACLE

##### Usage Notes

Cannot be entered inline by use of the EXEC ORACLE OPTION statement.

#### 6.7.25 ERRORS

##### Purpose

Specifies whether precompiler error messages are sent to the terminal and listing file or only to the listing file.

##### Syntax

`ERRORS={YES|NO`}

##### Default

`YES`

##### Usage Notes

When` ERRORS=YES`, error messages are sent to the terminal and listing file.

When `ERRORS=NO`, error messages are sent only to the listing file.

#### 6.7.26 ERRTYPE

##### Purpose

Specifies an output file in which errors generated in processing type files are written. If omitted, errors are output to the screen.

##### Syntax

ERRTYPE=filename

##### Default

None

##### Usage Notes

Only one error file will be produced. If multiple values are entered, the last one is used by the precompiler.

#### 6.7.27 EVENTS

##### Purpose

Specifies that the application is interested in registering for and receiving notifications.

##### Syntax

EVENTS={YES \| NO}

##### Default

NO

##### Usage Notes

Can only be entered in the command line.

#### 6.7.28 FIPS

##### Purpose

Specifies whether extensions to ANSI/ISO SQL are flagged (by the FIPS Flagger). An extension is any SQL element that violates ANSI/ISO format or syntax rules, except privilege enforcement rules.

##### Syntax

`FIPS={YES|NO}`

##### Default

`NO`

##### Usage Notes

When `FIPS=YES`, the `FIPS` Flagger issues warning (not error) messages if you use an Oracle extension to the ANSI/ISO embedded SQL standard (SQL92) or use a SQL92 feature in a nonconforming manner.

The following extensions to ANSI/ISO SQL are flagged at precompile time:

- Array interface including the FOR clause

- SQLCA, ORACA, and SQLDA data structures

- Dynamic SQL including the `DESCRIBE` statement

- Embedded PL/SQL blocks

- Automatic datatype conversion

- DATE, COMP-3 (Pro\*COBOL only), `NUMBER`, `RAW`, `LONG` `RAW`, `VARRAW`, `ROWID`, and `VARCHAR` datatypes

- ORACLE OPTION statement for specifying run-time options

- EXEC IAF and EXEC TOOLS statements in user exits

- `CONNECT` statement

- `TYPE` and VAR datatype equivalencing statements

- AT db_name clause

- `DECLARE`...`DATABASE`, ...`STATEMENT`, and ...`TABLE` statements

- SQLWARNING condition in `WHENEVER` statement

- `DO` and `STOP` actions in `WHENEVER` statement

- `COMMENT` and `FORCE` `TRANSACTION` clauses in `COMMIT` statement

- `FORCE` `TRANSACTION` and `TO` `SAVEPOINT` clauses in `ROLLBACK` statement

- `RELEASE` parameter in `COMMIT` and `ROLLBACK` statements

- Optional colon-prefixing of `WHENEVER`...DO labels and of host variables in the `INTO` clause

#### 6.7.29 FORMAT

##### Purpose

Specifies the format of COBOL or FORTRAN input lines.

##### Syntax

`FORMAT={ANSI|TERMINAL}`

##### Default

`ANSI`

##### Usage Notes

Cannot be entered inline.

The format of input lines is system-dependent. Check your system-specific Oracle manuals.

When `FORMAT=ANSI`, the format of input lines conforms as much as possible to the current ANSI standard.

#### 6.7.30 Globalization Support_LOCAL

##### Purpose

For Pro\*COBOL only, the Globalization Support_LOCAL option determines whether Globalization Support character conversions are performed by the precompiler run-time library or by the Oracle Server.

##### Syntax

`Globalization Support_LOCAL={YES|NO}`

##### Default

`NO`

##### Usage Notes

Cannot be entered inline.

When` Globalization Support_LOCAL=YES`, the run-time library (SQLLIB) locally performs blank-padding and blank-stripping for host variables that have multibyte Globalization Support datatypes.

When Globalization `Support_LOCAL=NO`, blank-padding and blank-stripping operations are not performed locally for host variables that have multibyte Globalization Support datatypes.

Oracle does not perform any blank-padding or blank-stripping of Globalization Support variables. When Globalization Support_LOCAL=NO, the Oracle Server returns an error upon executing a SQL statement that uses multibyte Globalization Support data.

#### 6.7.31 HEADER

##### Purpose

Permits precompiled header files. Specifies the file extension for precompiled header files.

##### Syntax

HEADER=extension

##### Default

NONE

##### Usage Notes

When precompiling a header file, this option is required and is used to specify the file extension for the output file that is created by precompiling that header file.

When precompiling an ordinary Pro\*C/C++ program this option is optional. When given, it enables the use of the precompiled header mechanism during the precompilation of that Pro\*C/C++ program.

In both cases, this option also specifies the file extension to use when processing a \#include directive. If an \#include file exists with the specified extension, Pro\*C/C++ assumes the file is a precompiled header file previously generated by Pro\*C/C++. Pro\*C/C++ will then instantiate the data from that file rather than process the \#include directive and precompile the included header file.

This option is only allowed on the command line or in a configuration file. It is not allowed inline. When using this option, specify the file extension only. Do not include any file separators. For example, do not include a period '.' in the extension.

#### 6.7.32 HOLD_CURSOR

##### Purpose

Specifies how the cursors for SQL statements and PL/SQL blocks are handled in the cursor cache.

##### Syntax

`HOLD_CURSOR={YES|NO}`

##### Default

`NO`

##### Usage Notes

You can use `HOLD_CURSOR` to improve the performance of your program. For more information, refer to [Performance Tuning](performance-tuning.md)

When a SQL data manipulation statement is executed, its associated cursor is linked to an entry in the cursor cache. The cursor cache entry is in turn linked to an Oracle private SQL area, which stores information needed to process the statement. `HOLD_CURSOR` controls what happens to the link between the cursor and cursor cache.

When `HOLD_CURSOR=NO`, after Oracle executes the SQL statement and the cursor is closed, the precompiler marks the link as reusable. The link is reused as soon as the cursor cache entry to which it points is needed for another SQL statement. This frees memory allocated to the private SQL area and releases parse locks.

When `HOLD_CURSOR=YES` and `RELEASE_CURSOR=NO`, the link is maintained; the precompiler does not reuse it. This is useful for SQL statements that are executed often because it speeds up subsequent executions. There is no need to reparse the statement or allocate memory for an Oracle private SQL area.

For inline use with implicit cursors, set `HOLD_CURSOR` before executing the SQL statement. For inline use with explicit cursors, set `HOLD_CURSOR` before opening the cursor.

Note that `RELEASE_CURSOR=YES` overrides `HOLD_CURSOR=YES `and that `HOLD_CURSOR`=`NO` overrides `RELEASE_CURSOR=NO`. For information showing how these two options interact, refer to [Table C-1](performance-tuning.md).

#### 6.7.33 HOST

##### Purpose

Specifies the host language to be used.

##### Syntax

`HOST={COB74|COBOL}`

##### Default

COBOL

##### Usage Notes

Cannot be entered inline.

COB74 refers to the 1974 version of ANSI-approved COBOL. COBOL refers to 1985 version. Other values might be available on your platform.

#### 6.7.34 IMPLICIT_SVPT

##### Purpose

Controls whether an implicit savepoint is taken before the start of a new batched insert.

##### Syntax

implicit_svpt={YES\|NO}

##### Default

NO

##### Usage Notes

If implict_svpt=yes, a savepoint is taken before the start of a new batch of rows. If an error occurs on the insert, an implicit "rollback to savepoint" is executed. This option exists for DB/2 compatibility, the obvious downside being the extra round-trip.

If implict_svpt=no, there is no implicit savepoint taken. If an error occurs on the buffered insert, then it is reported back to the application, but no rollback is executed.

#### 6.7.35 INAME

##### Purpose

Specifies the name of the input file.

##### Syntax

`INAME=``filename`

##### Default

`None`

##### Usage Notes

Cannot be entered inline.

When specifying the name of your input file on the command line, the keyword INAME is optional. For example, in Pro\*COBOL, you can specify myprog.pco instead of `INAME=myprog.pco`.

The precompiler assumes the standard input file extension (refer to Table 6-5). So, you need not use a file extension when specifying INAME unless the extension is nonstandard. For example, in Pro\*FORTRAN, you can specify myprog instead of myprog.pfo.

Table 6-5 Input File Extensions

| Host Language | Standard File Extension |
|:--------------|:------------------------|
| COBOL         | `pco`                   |
| FORTRAN       | `pfo`                   |

For Pro\*COBOL only, if you use a nonstandard input file extension when specifying `INAME`, you must also specify HOST.

#### 6.7.36 INCLUDE

##### Purpose

Specifies a directory path for EXEC SQL INCLUDE files. It only applies to operating systems that use directories.

##### Syntax

`INCLUDE=path`

##### Default

Current directory

##### Usage Notes

Typically, you use `INCLUDE` to specify a directory path for the SQLCA and ORACA files. The precompiler searches first in the current directory, then in the directory specified by `INCLUDE`, and finally in a directory for standard `INCLUDE` files. Hence, you need not specify a directory path for standard files such as the SQLCA and ORACA.

You must still use `INCLUDE` to specify a directory path for nonstandard files unless they are stored in the current directory. You can specify more than one path on the command line, as follows:

    ... INCLUDE=<path1> INCLUDE=<path2> ...

The precompiler searches first in the current directory, then in the directory named by path1, then in the directory named by path2, and finally in the directory for standard `INCLUDE` files.

Remember, the precompiler searches for a file in the current directory first--even if you specify a directory path. So, if the file you want to `INCLUDE` resides in another directory, make sure no file with the same name resides in the current directory.

The syntax for specifying a directory path is system-specific. Follow the conventions of your operating system.

#### 6.7.37 IRECLEN

##### Purpose

Specifies the record length of the input file.

##### Syntax

`IRECLEN=``integer`

##### Default

`80`

##### Usage Notes

Cannot be entered inline.

The value you specify for IRECLEN should not exceed the value of ORECLEN. The maximum value allowed is system-dependent.

#### 6.7.38 INTYPE

##### Purpose

Specifies one or more OTT-generated type files (only needed if Object types are used in the application).

##### Syntax

INTYPE=(file_1,file_2,...,file_n)

##### Default

None

##### Usage Notes

There will be one type file for each Object type in the Pro\*C/C++ code.

#### 6.7.39 LINES

##### Purpose

Specifies whether the Pro\*C/C++ precompiler adds \#line preprocessor directives to its output file.

##### Syntax

LINES={YES \| NO}

##### Default

NO

##### Usage Notes

Can be entered only on the command line.

The LINES option helps with debugging.

When LINES=YES, the Pro\*C/C++ precompiler adds \#line preprocessor directives to its output file.

Normally, your C compiler increments its line count after each input line is processed. The \#line directives force the compiler to reset its input line counter so that lines of precompiler-generated code are not counted. Moreover, when the name of the input file changes, the next \#line directive specifies the new filename.

The C compiler uses the line numbers and filenames to show the location of errors. Thus, error messages issued by the C compiler always refer to your original source files, not the modified (precompiled) source file. This also enables stepping through the original source code using most debuggers.

When LINES=NO (the default), the precompiler adds no \#line directives to its output file.

**Note:**

The Pro\*C/C++ precompiler does not support the \#line directive. You cannot directly code \#line directives in the precompiler source. But you can still use the LINES= option to have the precompiler insert \#line directives for you.

#### 6.7.40 LITDELIM

##### Purpose

For Pro\*COBOL only, the LITDELIM option specifies the delimiter for string constants and literals.

##### Syntax

`LITDELIM={APOST|QUOTE}`

##### Default

`QUOTE`

##### Usage Notes

When `LITDELIM=APOST`, the precompiler uses apostrophes when generating COBOL code. If you specify `LITDELIM=QUOTE`, quotation marks are used, as in

    CALL "SQLROL" USING SQL-TMP0.

In SQL statements, you must use quotation marks to delimit identifiers containing special or lowercase characters, as in

    EXEC SQL CREATE TABLE "Emp2" END-EXEC.

but you must use apostrophes to delimit string constants, as in

    EXEC SQL SELECT ENAME FROM EMP WHERE JOB = 'CLERK' END-EXEC.

Regardless of which delimiter is used in the Pro\*COBOL source file, the precompiler generates the delimiter specified by the LITDELIM value.

#### 6.7.41 LNAME

##### Purpose

Specifies a nondefault name for the listing file.

##### Syntax

`LNAME=filename`

##### Default

input.LIS, where input is the base name of the input file.

##### Usage Notes

Cannot be entered inline.

By default, the listing file is written to the current directory.

#### 6.7.42 LRECLEN

##### Purpose

Specifies the record length of the listing file.

##### Syntax

`LRECLEN=``integer`

##### Default

`132`

##### Usage Notes

Cannot be entered inline.

The value of LRECLEN can range from 80 through 255. If you specify a value the range, 80 is used instead. If you specify a value earlier the range, 255 is used instead. LRECLEN should exceed IRECLEN by at least 8 to allow for the insertion of line numbers.

#### 6.7.43 LTYPE

##### Purpose

Specifies the listing type.

##### Syntax

`LTYPE={LONG|SHORT|NONE}`

##### Default

`LONG`

##### Usage Notes

Cannot be entered inline.

When `LTYPE=LONG`, input lines appear in the listing file. When `LTYPE=SHORT`, input lines do not appear in the listing file. When `LTYPE=NONE`, no listing file is created.

#### 6.7.44 MAXLITERAL

##### Purpose

Specifies the maximum length of string literals generated by the precompiler so that compiler limits are not exceeded. For example, if your compiler cannot handle string literals longer than 132 characters, you can specify MAXLITERAL=132 on the command line.

##### Syntax

`MAXLITERAL=``integer`

##### Default

The default is precompiler-specific as shown here:

| Precompiler  | Default |
|:-------------|:--------|
| Pro\*COBOL   | 256     |
| Pro\*FORTRAN | 1000    |

##### Usage Notes

The maximum value of `MAXLITERAL` is compiler-dependent. The default value is language-dependent, but you might have to specify a lower value. For example, some COBOL compilers cannot handle string literals longer than 132 characters, so you would specify `MAXLITERAL=132.`

Strings that exceed the length specified by `MAXLITERAL` are divided during precompilation, then recombined (concatenated) at run time.

You can enter `MAXLITERAL` inline but your program can set its value just once, and the EXEC ORACLE statement must precede the first EXEC SQL statement. Otherwise, the precompiler issues a warning message, ignores the extra or misplaced EXEC ORACLE statement, and continues processing.

#### 6.7.45 MAXOPENCURSORS

##### Purpose

Specifies the number of concurrently open cursors that the precompiler tries to keep cached.

##### Syntax

`MAXOPENCURSORS=``integer`

##### Default

10

##### Usage Notes

You can use MAXOPENCURSORS to improve the performance of your program. For more information, refer to [Performance Tuning](performance-tuning.md)

When precompiling separately, use MAXOPENCURSORS as described in "Separate Precompilations".

MAXOPENCURSORS specifies the initial size of the SQLLIB cursor cache. If a new cursor is needed, and there are no free cache entries, Oracle tries to reuse an entry. Its success depends on the values of HOLD_CURSOR and RELEASE_CURSOR, and, for explicit cursors, on the status of the cursor itself. Oracle allocates an additional cache entry if it cannot find one to reuse. If necessary, Oracle keeps allocating additional cache entries until it runs out of memory or reaches the limit set by OPEN_CURSORS. To avoid a "maximum open cursors exceeded" Oracle error, MAXOPENCURSORS must be lower than OPEN_CURSORS by at least 6.

As your program's need for concurrently open cursors grows, you might want to re-specify MAXOPENCURSORS to match the need. A value of 45 to 50 is not uncommon, but remember that each cursor requires another private SQL area in the user process memory space. The default value of 10 is adequate for most programs.

#### 6.7.46 MAX_ROW_INSERT

##### Purpose

Controls the number of rows that need to be buffered before executing the INSERT statement.

##### Syntax

max_row_insert={number of rows to be buffered}

##### Default

0

##### Usage Notes

Any number greater than zero enables buffered insert feature and buffers that many rows before executing the INSERT statement.

#### 6.7.47 MODE

##### Purpose

Specifies whether your program observes Oracle practices or complies with the current ANSI SQL standard.

##### Syntax

`MODE={ANSI|ISO|ANSI14|ISO14|ANSI13|ISO13|ORACLE}`

##### Default

`ORACLE`

##### Usage Notes

Cannot be entered inline.

The following pairs of `MODE` values are equivalent: ANSI and ISO, ANSI14 and ISO14, ANSI13 and ISO13.

When `MODE=ORACLE `(the default), your embedded SQL program observes Oracle practices.

When `MODE={ANSI14|ANSI13}`, your program complies closely with the current ANSI SQL standard.

When` MODE=ANSI`, your program complies fully with the ANSI standard and the following changes go into effect:

- CHAR column values, `USER` pseudocolumn values, character host values, and quoted literals are treated like ANSI fixed-length character strings. And, ANSI-compliant blank-padding semantics are used when you assign, compare, `INSERT`, `UPDATE`, `SELECT`, or `FETCH` such values.

- Issuing a `COMMIT` or `ROLLBACK` closes all explicit cursors. (When `MODE={ANSI13|ORACLE}`, a commit or rollback closes only cursors referenced in a `CURRENT OF` clause.)

- You cannot OPEN a cursor that is already open or `CLOSE` a cursor that is already closed. (When `MODE=ORACLE`, you can reOPEN an open cursor to avoid reparsing.)

- The "no data found" Oracle warning code returned to SQLCODE becomes +100 instead of +1403. The error message text does not change.

- No error message is issued if Oracle assigns a truncated column value to an output host variable.

When `MODE={ANSI|ANSI14},` a 4-byte integer variable named SQLCODE (SQLCOD in FORTRAN) or a 5-byte character variable named SQLSTATE (SQLSTA in FORTRAN) must be declared. For more information, refer to "[Error Handling Alternatives](error-handling-diagnostics.md)".

Table 6-4 shows how the MODE and DBMS settings interact. Other combinations are incompatible or are not recommended.

#### 6.7.48 MULTISUBPROG

##### Purpose

For Pro\*FORTRAN only, the MULTISUBPROG option specifies whether the Pro\*FORTRAN precompiler generates `COMMON` statements and `BLOCK DATA` subprograms.

**Note:**

This option allows Pro\*FORTRAN release 1.3 applications to migrate to later releases. You can ignore the MUTISUBPROG option if you are not migrating Pro\*FORTRAN release 1.3 source code.

##### Syntax

`MULTISUBPROG={YES|NO}`

##### Default

`YES`

##### Usage Notes

Cannot be entered inline.

When `MULTISUBPROG=YES`, the precompiler generates `COMMON` statements and `BLOCK DATA` subprograms. Your host program does not access the `COMMON` blocks directly, but it allows two or more program units in the same precompilation unit to contain SQL statements.

However, the precompiler can give `COMMON` blocks defined in different output files the same name. If you link the files into an executable program, you get a link-time or run-time error. To solve this problem, you can rename the input files or override the default COMMON block names by specifying the option `COMMON_NAME`. To avoid the problem, specify `MULTISUBPROG=NO`.

Specify `MULTISUBPROG=NO` if your Pro\*FORTRAN source code has only a single subprogram in each source file (this was the restriction in release 1.3). When `MULTISUBPROG=NO`, the `COMMON_BLOCK` option is ignored and the precompiler generates no `COMMON` statements or `BLOCK DATA` subprograms. Every program unit that contains executable SQL statements must have a Declare Section. Otherwise, you get a precompilation error. For input files that contain more than one embedded SQL program unit, the precompiler generates the same declarations in each unit.

#### 6.7.49 NATIVE_TYPES

##### Purpose

Support for native float/double.

##### Syntax

NATIVE_TYPES = {YES\|NO}

##### Default

NO

##### Usage Notes

The native float and native double datatypes represent the single-precision and double-precision floating point values. They are represented natively, that is, in the host system's floating point format.

#### 6.7.50 NLS_CHAR

##### Purpose

Specifies which C host character variables are treated by the precompiler as multibyte character variables.

##### Syntax

NLS_CHAR=varname or NLS_CHAR=(var_1,var_2,...,var_n)

##### Default

None.

##### Usage Notes

Can be entered only on the command line, or in a configuration file.

This option provides the ability to specify at precompile time a list of the names of one or more host variables that the precompiler must treat as multibyte character variables. You can specify only C char variables or Pro\*C/C++ VARCHARs using this option.

If you specify in the option list a variable that is not declared in your program, then the precompiler generates no error.

#### 6.7.51 NLS_LOCAL

##### Purpose

Determines whether multibyte character set conversions are performed by the precompiler run-time library, SQLLIB, or by the database server.

##### Syntax

NLS_LOCAL={NO \| YES}

##### Default

NO

##### Usage Notes

When set to YES, local multibyte support is provided by Pro\*C/C++ and the SQLLIB library. The option NLS_CHAR must be used to indicate which C host variables are multibyte.

When set to NO, Pro\*C/C++ will use the database server support for multibyte objects. Set NLS_LOCAL to NO for all new applications.

Environment variable NLS_NCHAR must be set to a valid fixed-width National Character Set. Variable-width National Character Sets are not supported.

Can be entered only on the command line, or in a configuration file.

#### 6.7.52 OBJECTS

##### Purpose

Requests support for object types.

##### Syntax

OBJECTS={YES \| NO}

##### Default

YES

##### Usage Notes

Can only be entered in the command line.

#### 6.7.53 ONAME

##### Purpose

Specifies the name of the output file.

##### Syntax

`ONAME=``filename`

##### Default

`System-dependent`

##### Usage Notes

Cannot be entered inline.

Use this option to specify the name of the output file, where the name differs from that of the input file. For example, if you issue

    procob INAME=my_test

the default output filename is my_test.cob. If you want the output filename to be my_test_1.cob, issue the command

    procob INAME=my_test ONAME=my_test_1.cob

Note that you should add the .cob extension to files specified using ONAME. There is no default extension with the ONAME option.

Oracle recommends that you not let the output filename default, but rather name it explicitly using ONAME.

#### 6.7.54 ORACA

##### Purpose

Specifies whether a program can use the Oracle Communications Area (ORACA).

##### Syntax

`ORACA={YES|NO}`

##### Default

`NO`

##### Usage Notes

When `ORACA=YE`S, you must place the `INCLUDE` ORACA statement in your program.

#### 6.7.55 ORECLEN

##### Purpose

Specifies the record length of the output file.

##### Syntax

`ORECLEN=``integer`

##### Default

80

##### Usage Notes

Cannot be entered inline.

The value you specify for ORECLEN should equal or exceed the value of IRECLEN. The maximum value allowed is system-dependent.

#### 6.7.56 OUTLINE

##### Purpose

Indicates that the outline SQL file must be generated for the SQL statements.

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

#### 6.7.57 OUTLNPREFIX

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

If the length of the outline name exceeds 30 bytes, then this option is helpful for the user who can just specify the prefix name.

If outlnprefix=none, then the outline names are generated by the system. The generated format is

    <category_name>_<filename>_<filetype>_<sequence_no>

Semantic check should be full when this option is turned on, which means option sqlcheck=full/semantics. If sqlcheck=syntax/limited/none, or outline=false, or both, then an error will be generated.

#### 6.7.58 PAGELEN

##### Purpose

Specifies the number of lines in each physical page of the listing file.

##### Syntax

`PAGELEN=``integer`

##### Default

`66`

##### Usage Notes

Cannot be entered inline.

The maximum value allowed is system-dependent.

#### 6.7.59 PARSE

##### Purpose

Specifies the way that the Pro\*C/C++ precompiler parses the source file.

##### Syntax

PARSE={FULL \| PARTIAL \| NONE}

##### Default

FULL

##### Usage Notes

To generate C++ compatible code, the PARSE option must be either NONE or PARTIAL.

If PARSE=NONE or PARSE=PARTIAL, all host variables must be declared inside a Declare Section.

The variable SQLCODE must also be declared inside a declare section, or it cannot be relied on to detect errors. Check the default value of PARSE for your platform.

If PARSE=FULL, the C parser is used, and it does not understand C++ constructs, such as classes, in your code.

With PARSE=FULL or PARSE=PARTIAL Pro\*C/C++ fully supports C preprocessor directives, such as \#define, \#ifdef, and so on. However, with PARSE=NONE conditional preprocessing is supported by EXEC ORACLE statements.

**Note:**

Some platforms have the default value of PARSE as other than FULL. See your system-dependent documentation.

#### 6.7.60 PREFETCH

##### Purpose

Use this option to speed up queries by pre-fetching several rows.

##### Syntax

PREFETCH=integer

##### Default

1

##### Usage Notes

Can be used in a configuration file or on the command-line. The value of the integer is used for execution of all queries using explicit cursors, subject to the rules of precedence.

When used inline it must placed before OPEN statements with explicit cursors. Then the number of rows pre-fetched when that OPEN is done is determined by the last inline PREFETCH option in effect.

The value range allowed is 0.. 65535.

#### 6.7.61 RELEASE_CURSOR

##### Purpose

Specifies how the cursors for SQL statements and PL/SQL blocks are handled in the cursor cache.

##### Syntax

`RELEASE_CURSOR={YES|NO}`

##### Default

`NO`

##### Usage Notes

You can use `RELEASE_CURSOR` to improve the performance of your program. For more information, refer to [Performance Tuning](performance-tuning.md).

When a SQL data manipulation statement is executed, its associated cursor is linked to an entry in the cursor cache. The cursor cache entry is in turn linked to an Oracle private SQL area, which stores information needed to process the statement. `RELEASE_CURSOR` controls what happens to the link between the cursor cache and private SQL area.

When `RELEASE_CURSOR=YES`, after Oracle executes the SQL statement and the cursor is closed, the precompiler immediately removes the link. This frees memory allocated to the private SQL area and releases parse locks. To make sure that associated resources are freed when you CLOSE a cursor, you must specify `RELEASE_CURSOR=YES`.

When `RELEASE_CURSOR=NO` and `HOLD_CURSOR=YES`, the link is maintained. The precompiler does not reuse the link unless the number of open cursors exceeds the value of MAXOPENCURSORS. This is useful for SQL statements that are executed often because it speeds up subsequent executions. There is no need to reparse the statement or allocate memory for an Oracle private SQL area.

For inline use with implicit cursors, set `RELEASE_CURSOR` before executing the SQL statement. For inline use with explicit cursors, set `RELEASE_CURSOR` before opening the cursor.

Note that R`ELEASE_CURSOR=YES` overrides `HOLD_CURSOR=YES` and that `HOLD_CURSOR=NO` overrides `RELEASE_CURSOR=NO`. For information showing how these two options interact, refer to [Table C-1](performance-tuning.md)

#### 6.7.62 RUNOUTLINE

##### Purpose

Provides the developer with the option of executing "create outline" statements either by using precompiler or by the developer manually at a later time.

##### Syntax

runoutline={yes \| no}

##### Default

no

##### Usage Notes

If runoutline=yes, then the generated 'create outline' statements are executed by the precompiler/translator at the end of a successful precompilation.

The outline option should be set to true or category_name when runoutline is used. Semantic check should be full when this option is turned on, which means option sqlcheck=full/semantics. If sqlcheck=syntax/limited/none, then error will be generated.

#### 6.7.63 SELECT_ERROR

##### Purpose

Specifies whether your program generates an error when a single-row `SELECT` statement returns more than one row or more rows than a host array can accommodate.

##### Syntax

`SELECT_ERROR={YES|NO}`

##### Default

`YES`

##### Usage Notes

When SELECT_ERROR=YES, an error is generated if a single-row select returns too many rows or an array select returns more rows than the host array can accommodate.

When SELECT_ERROR=NO, no error is generated when a single-row select returns too many rows or when an array select returns more rows than the host array can accommodate.

Whether you specify YES or NO, a random row is selected from the table. To ensure a specific ordering of rows, use the ORDER BY clause in your `SELECT` statement. When `SELECT_ERROR=NO` and you use `ORDER BY`, Oracle returns the first row, or the first n rows if you are selecting into an array. When `SELECT_ERROR=YES`, whether you use `ORDER BY`, an error is generated if too many rows are returned.

#### 6.7.64 SQLCHECK

##### Purpose

Specifies the type and extent of syntactic and semantic checking.

##### Syntax

`SQLCHECK={SEMANTICS|FULL|SYNTAX|LIMITED|NONE}`

##### Default

`SYNTAX`

##### Usage Notes

The values `SEMANTICS` and `FULL` are equivalent, as are the values `SYNTAX` and `LIMITED.`

The Oracle Precompilers can help you debug a program by checking the syntax and semantics of embedded SQL statements and PL/SQL blocks. Any errors found are reported at precompile time.

You control the level of checking by entering the SQLCHECK option inline and on the command line, inline and on the command line. However, the level of checking you specify inline cannot be higher than the level you specify (or accept by default) on the command line. For example, if you specify `SQLCHECK=NONE` on the command line, you cannot specify `SQLCHECK=SYNTAX` inline.

If `SQLCHECK=SYNTAX|SEMANTICS`, the precompiler generates an error when PL/SQL reserved words are used in SQL statements, even though the SQL statements are not themselves PL/SQL. If a PL/SQL reserved word must be used as an identifier, you can enclose it in double-quotes.

When` SQLCHECK=SEMANTICS`, the precompiler checks the syntax and semantics of

- Data manipulation statements such as `INSERT` and `UPDATE`

- PL/SQL blocks

However, the precompiler checks only the syntax of remote data manipulation statements (those using the AT db_name clause).

The precompiler gets the information for a semantic check from embedded `DECLARE` `TABLE` statements or, if you specify the option `USERID`, by connecting to Oracle and accessing the data dictionary. You need not connect to Oracle if every table referenced in a data manipulation statement or PL/SQL block is defined in a `DECLARE TABLE` statement.

If you connect to Oracle but some information cannot be found in the data dictionary, you must use` DECLARE TABLE` statements to supply the missing information. During precompilation, a `DECLARE TABLE` definition overrides a data dictionary definition if they conflict.

Specify `SQLCHECK=SEMANTICS` when precompiling new programs. If you embed PL/SQL blocks in a host program, you must specify `SQLCHECK=SEMANTICS` and the option `USERID`.

When `SQLCHECK=SYNTAX`, the precompiler checks the syntax of

- Data manipulation statements

- PL/SQL blocks

No semantic checking is done. `DECLARE TABLE` statements are ignored and PL/SQL blocks are not allowed. When checking data manipulation statements, the precompiler uses Oracle database version 7 syntax rules, which are downwardly compatible. Specify `SQLCHECK=SYNTAX` when migrating your precompiled programs.

When` SQLCHECK=NONE`, no syntactic or semantic checking is done. DECLARE TABLE statements are ignored and PL/SQL blocks are not allowed. Specify `SQLCHECK=NONE` if your program

- Contains non-Oracle SQL (for example, because it will connect to a non-Oracle server through Open Gateway)

- References tables not yet created and lacks `DECLARE TABLE` statements for them

The following table summarizes the checking done by SQLCHECK. For more information about syntactic and semantic checking, refer to [Syntactic and Semantic Checking](syntactic-and-semantic-checking.md).

| Statement  | SQLCHECK=SEMANTIC — Syntax | SQLCHECK=SEMANTIC — Semantic | SQLCHECK=SYNTAX — Syntax | SQLCHECK=SYNTAX — Semantic | SQLCHECK=NONE — Syntax | SQLCHECK=NONE — Semantic |
|:-----------|:---------------------------|:-----------------------------|:-------------------------|:---------------------------|:-----------------------|:-------------------------|
| DML        | Y                          | Y                            | Y                        | na                         | na                     | na                       |
| Remote DML | Y                          | na                           | Y                        | na                         | na                     | na                       |
| PL/SQL     | Y                          | Y                            | na                       | na                         | na                     | na                       |

#### 6.7.65 STMT_CACHE

##### Purpose

Denotes the Statement cache size for the dynamic SQL statements.

##### Syntax

STMT_CACHE = Range is 0 to 65535

##### Default

0

##### Usage Notes

The stmt_cache option can be set to hold the anticipated number of distinct dynamic SQL statements in the application.

#### 6.7.66 SQLCHECK

##### Purpose

Specifies the type and extent of syntactic and semantic checking. By checking the syntax and semantics of embedded SQL statements and PL/SQL blocks, the Pro\*C/C++ Precompiler helps you quickly find and fix coding mistakes. Rules of syntax specify how language elements are sequenced to form valid statements. Thus, you can verify that keywords, object names, operators, delimiters, and similar objects are placed correctly in your SQL statement.

##### Syntax

SQLCHECK={SEMANTICS \| FULL \| SYNTAX}

##### Default

SYNTAX

##### Functionality

When

`SQLCHECK=SYNTAX`,

you will only check the syntax of the SQL statements by using the client side SQL interface.

When

`SQLCHECK=SEMANTICS` or `FULL`,

the SQL statements will be packaged/bundled into an IDL object by using a generic grammar during parsing. The generic grammar does not understand the SQL syntax, it can only identify the host variables, indicator variables, and the possible SQL identifiers. During the semantic phase, the validity of the host and indicator variables will be checked in the same manner it is currently done for SQL. The same will be done for semantics like the table names, column names, and types.

##### Usage Notes

SEMANTICS is the same as FULL.

Can be entered inline or on the command line.

**See Also:**

"What Is Syntactic and Semantic Checking?" on page D‐1 for complete details. (Pro\*C Programmer's Guide)

#### 6.7.67 THREADS

##### Purpose

When THREADS=YES, the precompiler searches for context declarations.

##### Syntax

THREADS={YES \| NO}

##### Default

NO

##### Usage Notes

Cannot be entered inline.

This precompiler option is required for any program that requires multithreading support.

With THREADS=YES, the precompiler generates an error if no EXEC SQL CONTEXT USE directive is encountered before the first context is visible and an executable SQL statement is found.

#### 6.7.68 TYPE_CODE

##### Purpose

This micro option specifies whether ANSI or Oracle datatype codes are used in dynamic SQL Method 4. Its setting is the same as the setting of MODE option.

##### Syntax

TYPE_CODE={ORACLE \| ANSI}

##### Default

ORACLE

##### Usage Notes

Cannot be entered inline.

#### 6.7.69 UNSAFE_NULL

##### Purpose

Specifying `UNSAFE_NULL=YES` prevents generation of `ORA-01405` messages when fetching `NULLs` without using indicator variables.

##### Syntax

`UNSAFE_NULL={YES|NO}`

##### Default

`NO`

##### Usage Notes

Cannot be entered inline.

The `UNSAFE_NULL=YES` is allowed only when `MODE=ORACLE `and DBMS=V7.

The `UNSAFE_NULL` option has no effect on host variables in an embedded PL/SQL block. You must use indicator variables to avoid `ORA-01405` errors.

#### 6.7.70 USERID

##### Purpose

Specifies an Oracle username and password.

##### Syntax

`USERID=``username``/``password`

##### Default

`None`

##### Usage Notes

Cannot be entered inline.

Do not specify this option when using the automatic logon feature, which accepts your Oracle username prefixed with the value of the Oracle initialization parameter `OS_AUTHENT_PREFIX`.

When `SQLCHECK=SEMANTICS,` if you want the precompiler to get needed information by connecting to Oracle and accessing the data dictionary, you must also specify USERID.

#### 6.7.71 UTF16_CHARSET

##### Purpose

Specify the character set form used by UNICODE(UTF16) variables.

##### Syntax

    UTF16_CHARSET={NCHAR_CHARSET | DB_CHARSET}

##### Default

    NCHAR_CHARSET

##### Usage Notes

Can be used only on the command line or in a configuration file, but not inline.

If UTF16_CHARSET=NCHAR_CHARSET (the default), the UNICODE(UTF16) bind / define buffer is converted according to the server side National Character Set. There may be a performance impact when the target column is CHAR.

If UTF16_CHAR=DB_CHARSET, the UNICODE(UTF16) bind / define buffer is converted according to the database character set.

**WARNING:**

There may be data loss when the target column is NCHAR.

#### 6.7.72 VARCHAR

##### Purpose

For Pro\*COBOL only, the `VARCHAR` option instructs the precompiler to treat the COBOL group item described in [Introduction](../lnpcb/introduction.md)as a `VARCHAR` datatype.

##### Syntax

`VARCHAR={YES|NO}`

##### Default

`NO`

##### Usage Notes

Cannot be entered inline.

When `VARCHAR=YES`, the implicit group item described in [Introduction](../lnpcb/introduction.md) is accepted as an Oracle VARCHAR external datatype with a length field and a string field.

When `VARCHAR=NO,` the Pro\*COBOL Precompiler does not accept the implicit group items as `VARCHAR` external datatypes.

#### 6.7.73 VERSION

##### Purpose

Determines which version of the object will be returned by the EXEC SQL OBJECT DEREF statement.

##### Syntax

VERSION={RECENT \| LATEST \| ANY}

##### Default

RECENT

##### Usage Notes

Can be entered inline using the EXEC ORACLE OPTION statement.

RECENT means that if the object has been selected into the object cache in the current transaction, then that object is returned. For transactions running in serializable mode, this option has the same effect as LATEST without incurring as many network round trips. Most applications should use RECENT.

LATEST means that if the object does not reside in the object cache, it is retrieved from the database. If It does reside in the object cache, it is refreshed from the server. Use LATEST with caution because it incurs the greatest number of network round trips. Use LATEST only when it is imperative that the object cache is kept as coherent as possible with the server buffer cache

ANY means that if the object already resides in the object cache, return that object. If not, retrieve the object from the server. ANY incurs the fewest network round trips. Use in applications that access read-only objects or when a user will have exclusive access to the objects.

#### 6.7.74 XREF

##### Purpose

Specifies whether a cross-reference section is included in the listing file.

##### Syntax

`XREF={YES|NO}`

##### Default

`YES`

##### Usage Notes

When `XREF=YES`, cross references are included for host variables, cursor names, and statement names. The cross references show where each object is defined and referenced in your program.

When `XREF=NO`, the cross-reference section is not included.

### 6.8 Conditional Precompilations

Conditional precompilation includes (or excludes) sections of code in your host program based on certain conditions. For example, you might want to include one section of code when precompiling under UNIX and another section when precompiling under VMS. Conditional precompilation lets you write programs that can run in different environments.

Conditional sections of code are marked by statements that define the environment and actions to take. You can code host-language statements and EXEC SQL statements in these sections. The following statements let you exercise conditional control over precompilation:

    EXEC ORACLE DEFINE symbol; -- define a symbol
    EXEC ORACLE IFDEF symbol; -- if symbol is defined
    EXEC ORACLE IFNDEF symbol; -- if symbol is not defined
    EXEC ORACLE ELSE; -- otherwise
    EXEC ORACLE ENDIF; -- end this control block

All EXEC ORACLE statements must be terminated with the statement terminator for your host language. For example, in Pro\*COBOL, a conditional statement must be terminated with "`END-EXEC`." and in Pro\*FORTRAN it must be terminated by a return character.

#### 6.8.1 An Example

In the following example, the `SELECT` statement is precompiled only when the symbol site2 is defined:

    EXEC ORACLE IFDEF site2;
     EXEC SQL SELECT DNAME
     INTO :dept_name
     FROM DEPT
     WHERE DEPTNO = :dept_number;
    EXEC ORACLE ENDIF;

Blocks of conditions can be nested as shown in the following example:

    EXEC ORACLE IFDEF outer;
     EXEC ORACLE IFDEF inner;
     ...
     EXEC ORACLE ENDIF;
    EXEC ORACLE ENDIF;

You can "comment out" host-language or embedded SQL code by placing it between IFDEF and ENDIF and not defining the symbol.

#### 6.8.2 Defining Symbols

You can define a symbol in two ways. Either include the statement

    EXEC ORACLE DEFINE symbol;

in your host program or define the symbol on the command line using the syntax

    ... INAME=filename ... DEFINE=symbol

where symbol is not case-sensitive.

Some port-specific symbols are predefined for you when the Oracle Precompilers are installed on your system. For example, predefined operating system symbols include CMS, MVS, MS-DOS, UNIX, and VMS.

### 6.9 Separate Precompilations

With the Oracle Precompilers, you can precompile several host program modules separately, then link them into one executable program. This supports modular programming, which is required when the functional components of a program are written and debugged by different programmers. The individual program modules need not be written in the same language.

#### 6.9.1 Guidelines

The following guidelines will help you avoid some common problems.

##### Referencing Cursors

Cursor names are SQL identifiers, whose scope is the precompilation unit. Hence, cursor operations cannot span precompilation units (files). That is, you cannot declare a cursor in one file and open or fetch from it in another file. So, when doing a separate precompilation, make sure all definitions and references to a given cursor are in one file.

##### Specifying MAXOPENCURSORS

When you precompile the program module that connects to Oracle, specify a value for MAXOPENCURSORS that is high enough for any of the program modules. If you use it for another program module, MAXOPENCURSORS is ignored. Only the value in effect for the connect is used at run time.

##### Using a Single SQLCA

If you want to use just one SQLCA, you must declare it globally in one of the program modules.

#### 6.9.2 Restrictions

All references to an explicit cursor must be in the same program file. You cannot perform operations on a cursor that was DECLAREd in a different module. Refer to [ Using Embedded SQL](using-embedded-SQL.md) for more information about cursors.

Also, any program file that contains SQL statements must have a SQLCA that is in the scope of the local SQL statements.

### 6.10 Compiling and Linking

To get an executable program, you must compile the source file(s) produced by the precompiler, then link the resulting object module with any modules needed from SQLLIB and system-specific Oracle libraries. Also, if you are embedding OCI calls, make sure to link in the OCI run-time library (OCILIB).

The linker resolves symbolic references in the object modules. If these references conflict, the link fails. This can happen when you try to link third party software into a precompiled program. Not all third-party software is compatible with Oracle, so you might have problems. Check with Oracle Customer Services to see if the software is supported.

Compiling and linking are system-dependent. For instructions, see your system-specific Oracle manuals.

For more information about OCI handle and descriptor attributes, see Handle and Descriptor Attributes.

#### 6.10.1 System-Dependent

Compiling and linking are system-dependent. For example, on some systems, you must turn off compiler optimization when compiling a host language program. For instructions, refer to your system-specific Oracle documentation.

#### 6.10.2 Multibyte Globalization Support Compatibility

When using multibyte Globalization Support features, you must link your object files to the current version of the SQLLIB run-time library. The multibyte Globalization Support features in this release are supported by the SQLLIB run-time library and not by the Oracle Server. The resulting application can then be executed with any release of the Oracle database.
