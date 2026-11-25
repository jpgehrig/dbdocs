This chapter tells you how to run the Pro\*C/C++ precompiler, and describes the extensive set of precompiler options in detail. This chapter contains the following topics:

- The Precompiler Command

- Precompiler Options

- Quick Reference

- Entering Options

- About Using the Precompiler Options

### 10.1 The Precompiler Command

The location of the precompiler differs from system to system. The system or database administrator usually defines logicals or aliases, or uses other system-specific means to make the Pro\*C/C++ executable accessible.

To run the Pro\*C/C++ precompiler, you issue the following command:

    proc option=value...

**Note:**

The option value is always separated from the option name by an equals sign, with no whitespace around the equals sign.

For example, the command

    proc INAME=test_proc

precompiles the file `test_proc.pc` in the current directory, since the precompiler assumes that the filename extension is `pc`. The INAME=argument specifies the source file to be precompiled. The INAME option does not have to be the first option on the command line, but if it is, you can omit the option specification. So, the command

    proc myfile

is equivalent to

    proc INAME=myfile

**Note:**

The option names, and option values that do not name specific operating system objects, such as filenames, are not case-sensitive. In the examples in this guide, option names are written in upper case, and option values are usually in lower case. When you enter filenames, including the name of the Pro\*C/C++ precompiler executable itself, always follow the case conventions used by your operating system.

Some platforms, such as UNIX, require "escape characters" before certain characters in value strings. Consult your platform-specific documentation.

#### 10.1.1 Case Sensitivity

In general, you can use either uppercase or lowercase for precompiler option names and values. However, if your operating system is case sensitive, like UNIX, you must specify filename values, including the name of the Pro\*C/C++ executable, using the correct combination of uppercase and lowercase letters.

### 10.2 Precompiler Options

Precompiler options enable you to control how resources are used, how errors are reported, how input and output are formatted, and how cursors are managed.

The value of an option is a literal, which represents text or numeric values. For example, for the option

    ...  INAME=my_test

the value is a string literal that specifies a filename.

For the option MAXOPENCURSORS

    ...MAXOPENCURSORS=20

the value is numeric.

Some options take Boolean values, and you can represent these with the strings yes or no, true or false, or with the integer literals 1 or 0 respectively. For example, the option

    ...  SELECT_ERROR=yes

is equivalent to

    ...  SELECT_ERROR=true

or

    ...  SELECT_ERROR=1

all of which mean that SELECT errors should be flagged at run time.

#### 10.2.1 Environment Variables

You can use environment variables in SYS_INCLUDE and INCLUDE precompiler options. Environment variables like `ORACLE_HOME` can be used in SYS_INCLUDE and INCLUDE directory paths while precompiling a PROC application. SYS_INCLUDE and INCLUDE option values can also come from the config file, `pcscfg.cfg`. The following usages of environment variables are supported.

In Linux

    $ENV_VAR
    sys_include=$ORACLE_HOME/precomp/public
    include=$ORACLE_HOME/precomp/public

    $(ENV_VAR)
    sys_include=$(ORACLE_HOME)/precomp/public
    include=$(ORACLE_HOME)/precomp/public

    ${ENV_VAR}
    sys_include=${ORACLE_HOME}/precomp/public
    include=${ORACLE_HOME}/precomp/public

In Windows

    %ENV_VAR%
    sys_include=%ORACLE_HOME%\precomp\public
    include=%ORACLE_HOME%\precomp\public


#### 10.2.2 Configuration Files

A configuration file is a text file that contains precompiler options. Each record (line) in the file contains only one option, with its associated value or values. Any options entered on a line after the first option are ignored. For example, the following configuration file contains the lines:

    FIPS=YES
    MODE=ANSI
    CODE=ANSI_C

to set defaults for the FIPS, MODE, and CODE options.

There is a restriction of 300 characters per line for each entry in` pcscfg.cfg`. To set a value longer than 300 characters, for example, the SYS_INCLUDE path), create entries in multiple lines. For example,

    sys_include=/ade/aime_rdbms_9819/oracle/precomp/public
    sys_include=/usr/include,/usr/lib/gcc-lib/i486-suse-linux/2.95.3/include
    sys_include=/usr/lib/gcc-lib/i386-redhat-linux/3.2.3/include
    sys_include=/usr/lib/gcc-lib/i386-redhat-linux7/2.96/include
    sys_include=/usr/include

Do not use brackets at the end of a line. A bracket at the right hand end of a line nullifies all previous lines. For example, a bracket at the end of the third line,

    sys_include=/ade/aime_rdbms_9819/oracle/precomp/public
    sys_include=/usr/include,/usr/lib/gcc-lib/i486-suse-linux/2.95.3/include
    sys_include=/usr/lib/gcc-lib/i386-redhat-linux/3.2.3/include)
    sys_include=/usr/lib/gcc-lib/i386-redhat-linux7/2.96/include
    sys_include=/usr/include

sets SYS_INCLUDE to

    /usr/lib/gcc-lib/i386-redhat-linux/3.2.3/include, /usr/lib/gcc-lib/i386-redhat-linux7/2.96/include,/usr/include

There is a single system configuration file for each installation. The name of the system configuration file is `pcscfg.cfg`. The location of the file is system specific.

**Note:**

`pcscfg.cfg` contains default path settings for variables like `include` or `LIBPATH`. These paths may be computer or operating system dependent. You must verify that default paths are valid for your computer and operating system. If not valid, replace the path with 8dot3 notation.

In the `pcscfg.cfg` file, you cannot use spaces. For example, if the file contains the following line:

`include="D:\Program Files\Microsoft Visual Studio\VC98\include"`

the precompilation will fail. You can replace it with the following:

`include=D:\Progra~1\Microa~4\VC98\include`

Each Pro\*C/C++ user can have one or more private configuration files. The name of the configuration file must be specified using the CONFIG= precompiler option.

**Note:**

You cannot nest configuration files. This means that CONFIG= is not a valid option inside a configuration file.

**Related Topics**

- About Using the Precompiler Options

#### 10.2.3 Precedence of Option Values

The value of an option is determined, in increasing precedence, by:

- A value built in to the precompiler

- A value set in the Pro\*C/C++ system configuration file

- A value set in a Pro\*C/C++ user configuration file

- A value set in the command line

- A value set inline

For example, the option MAXOPENCURSORS specifies the maximum number of cached open cursors. The built-in precompiler default value for this option is 10. However, if MAXOPENCURSORS=32 is specified in the system configuration file, the default now becomes 32. The user configuration file could set it to yet another value, which then overrides the system configuration value. Finally, an inline specification takes precedence over all preceding defaults.

If a PROC command-line option is used a multiple number of times, the last value assigned in the last occurence is the value used by PROC for precompilation. For example,

    $ proc iname=sample.pc ... oname=output1.c ... oname=output2.c ... oname=output3.c

In the example, `output3.c` is the ONAME value used by PROC and the generated output filename is `output3.c`.

If an option is specified both inside the config file (system default or user specified) and on the command line, then the value specified in the command line takes precedence.

In the case of SYS_INCLUDE and INCLUDE options, the behavior is as defined in Environment Variables. The values are appended unless interrupted by a bracket at the end of a line.

If you specify a private configuration file with CONFIG=filename, then the first value takes precedence and subsequent occurences in the command line are ignored. This is an exception to command-line last-value precedence.

Some options, such as USERID, do not have a precompiler default value. The built-in default values for options that do have them are listed in Table 10-2.

**Note:**

Check your system-specific documentation for the precompiler default values; they may have been changed from the values in this chapter for your platform.

##### Determining Current Values

You can interactively determine the current value for one or more options by using a question mark on the command line. For example, if you issue the command

    proc ?

the complete set of options, along with their current values, is printed to your terminal. (On a UNIX system running the C shell, escape the '?' with a backslash.) In this case, the values are those built into the precompiler, overridden by any values in the system configuration file. But if you issue the command

    proc config=my_config_file.h ?


and there is a file named `my_config_file.h` in the current directory, all options are listed. Values in the user configuration file supply missing values, and supersede values built-in to the Pro\*C/C++ precompiler, or values specified in the system configuration file.

You can also determine the current value of a single option, by simply specifying that option name, followed by =?. For example:

    proc maxopencursors=?

prints the current default value for the MAXOPENCURSORS option.

Entering:

    proc

will give a short summary that resembles "Table 10-2".

**Related Topics**

- What Occurs During Precompilation?
- About Using the Precompiler Options

#### 10.2.4 Macro and Micro Options

The option MODE controls several options at once. MODE is known as a macro option. Some newer options such as CLOSE_ON_COMMIT, DYNAMIC and TYPE_CODE control only one function and are known as micro options. A macro option has precedence over micro options only if the macro option is at a higher level of precedence.

The following table lists the values of micro options set by the macro option values:

Table 10-1 How Macro Option Values Set Micro Option Values

| Macro Option     | Micro Option                                             |
|:-----------------|:---------------------------------------------------------|
| MODE=ANSI \| ISO | CLOSE_ON_COMMIT=YES<br>DYNAMIC=ANSI<br>TYPE_CODE=ANSI    |
| MODE=ORACLE      | CLOSE_ON_COMMIT=NO<br>DYNAMIC=ORACLE<br>TYPE_CODE=ORACLE |

If you specify both MODE=ANSI and CLOSE_ON_COMMIT=NO in the user configuration file, then cursors will not be closed after a COMMIT. If you specify MODE=ORACLE in your configuration file and CLOSE_ON_COMMIT=YES on the command line, then the cursors will be closed.

**Related Topics**

- Precedence of Option Values

#### 10.2.5 What Occurs During Precompilation?

During precompilation, Pro\*C/C++ generates C or C++ code that replaces the SQL statements embedded in your host program. The generated code contains data structures that indicate the datatype, length, and address of host variables, as well as other information required by the runtime library, SQLLIB. The generated code also contains the calls to SQLLIB routines that perform the embedded SQL operations.

**Note:**

The precompiler does not generate calls to Oracle Call Interface (OCI) routines.

Table 10-2 is a quick reference to the major precompiler options. The options that are accepted, but do not have any affect, are not included in this table.

**Related Topics**

- [Oracle Database Error Messages Reference](../errmg/index.md)
- About Using the Precompiler Options

#### 10.2.6 Scope of Options

A precompilation unit is a file containing C code and one or more embedded SQL statements. The options specified for a given precompilation unit affect only that unit; they have no effect on other units. For example, if you specify HOLD_CURSOR=YES and RELEASE_CURSOR=YES for unit A, but not for unit B, SQL statements in unit A run with these HOLD_CURSOR and RELEASE_CURSOR values, but SQL statements in unit B run with the default values.

#### 10.2.7 Pro\*C/C++ Precompiler Issues for Windows Platforms

This section highlights issues related to Pro\*C/C++ for Windows platforms.

##### 10.2.7.1 Configuration File

For this release, the system configuration file is called `pcscfg.cfg`. This file is located in the `ORACLE_HOME\``precomp\admin` directory.

##### 10.2.7.2 CODE

The `CODE` option has a default setting of `ANSI_C`. Pro\*C/C++ for other operating systems may have a default setting of `KR_C`.

##### 10.2.7.3 DBMS

`DBMS=V6_CHAR` is not supported when using `CHAR_MAP=VARCHAR2`. Instead, use `DBMS=V7`.

##### 10.2.7.4 INCLUDE

For sample programs that precompile with `PARSE=PARTIAL` or `PARSE=FULL`, an include path of `c:\program files\devstudio\vc\include` has been added. If Microsoft Visual Studio has been installed in a different location, modify the Include Directories field accordingly for the sample programs to precompile correctly.

##### 10.2.7.5 PARSE

The `PARSE` option has a default setting of `NONE`. Pro\*C/C++ for other operating systems may have a default setting of `FULL`.

### 10.3 Quick Reference

Table 10-2 is a quick reference to the Pro\*C/C++ options. Options marked with an asterisk can be entered inline.

Table 10-2 Precompiler Options

| Syntax                                             | Default                | Specifics                                                                                                                                                                                                                          |
|:---------------------------------------------------|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AUTO_CONNECT={YES \| NO}                           | NO                     | Automatic CLUSTER\$ account connection before the first executable statement.                                                                                                                                                      |
| CHAR_MAP={VARCHAR2 \| CHARZ \| STRING \| CHARF} \* | CHARZ                  | Mapping of character arrays and strings.                                                                                                                                                                                           |
| CINCR                                              | 1                      | Allows the application to set the next increment for physical connections to be opened to the database, if the current number of physical connections is less than CMAX.                                                           |
| CLOSE_ON_COMMIT={YES \| NO}                        | NO                     | Close all cursors on COMMIT.                                                                                                                                                                                                       |
| CODE={ANSI_C \| KR_C \| CPP}                       | KR_C                   | Kind of C code generated.                                                                                                                                                                                                          |
| COMP_CHARSET={MULTI_BYTE \| SINGLE_BYTE}           | MULTI_BYTE             | The character set type the C/C++ compiler supports.                                                                                                                                                                                |
| CONFIG=filename                                    | none                   | User's private configuration file.                                                                                                                                                                                                 |
| CMIN                                               | 2                      | Specifies the minimum number of physical connections in the connection pool.                                                                                                                                                       |
| CMAX                                               | 100                    | Specifies the maximum number of physical connections that can be opened for the database.                                                                                                                                          |
| CNOWAIT                                            | 0 which means not set. | This attribute determines if the application must repeatedly try for a physical connection when all other physical connections in the pool are busy, and the total number of physical connections has already reached its maximum. |
| CPOOL                                              | NO                     | Based on this option, the precompiler generates the appropriate code that directs SQLLIB to enable or disable the connection pool feature.                                                                                         |
| CPP_SUFFIX=extension                               | none                   | Specify the default filename extension for C++ output files.                                                                                                                                                                       |
| CTIMEOUT                                           | 0 which means not set. | Physical connections that are idle for more than the specified time (in seconds) are terminated to maintain an optimum number of open physical connections.                                                                        |
| DBMS={V7 \| NATIVE \| V8}                          | NATIVE                 | Compatibility (Oracle7, Oracle8, Oracle8i, Oracle9i, or the database version to which you are connected at precompile time).                                                                                                       |
| DEF_SQLCODE={YES \| NO}                            | NO                     | Generate a macro to \#define SQLCODE.                                                                                                                                                                                              |
| DEFINE=name \*                                     | none                   | Define a name for use by the Pro\*C/C++ precompiler.                                                                                                                                                                               |
| DURATION={TRANSACTION \| SESSION}                  | TRANSACTION            | Set pin duration for objects in the cache.                                                                                                                                                                                         |
| DYNAMIC={ANSI \| ORACLE}                           | ORACLE                 | Specifies Oracle or ANSI SQL semantics.                                                                                                                                                                                            |
| ERRORS={YES \| NO}                                 | YES                    | Where to direct error messages (NO means only to listing file, and not to terminal).                                                                                                                                               |
| ERRTYPE=filename                                   | none                   | Name of the listing file for intype file error messages.                                                                                                                                                                           |
| FIPS={NO \| SQL89 \| SQL2 \| YES} \*               | none                   | Whether to flag ANSI/ISO non-compliance.                                                                                                                                                                                           |
| HEADER=extension                                   | none                   | Specify file extension for precompiled header files.                                                                                                                                                                               |
| HOLD_CURSOR={YES \| NO} \*                         | NO                     | How cursor cache handles SQL statement.                                                                                                                                                                                            |
| INAME=\]filename                                   | none                   | Name of the input file.                                                                                                                                                                                                            |
| INCLUDE=pathname \*                                | none                   | Directory path for EXEC SQL INCLUDE or \#include statements.                                                                                                                                                                       |
| INTYPE=filename                                    | none                   | Name of the input file for type information.                                                                                                                                                                                       |
| LINES={YES \| NO}                                  | NO                     | Whether \#line directives are generated.                                                                                                                                                                                           |
| LNAME=filename                                     | none                   | Name of listing file.                                                                                                                                                                                                              |
| LTYPE={NONE \| SHORT \| LONG}                      | none                   | Type of listing file to be generated, if any.                                                                                                                                                                                      |
| MAXLITERAL=10..1024                                | 1024                   | Maximum length (bytes) of string literals in generated C code.                                                                                                                                                                     |
| MAXOPENCURSORS=5..255 \*                           | 10                     | Maximum number of concurrent cached open cursors.                                                                                                                                                                                  |
| MODE={ANSI \| ISO \| ORACLE}                       | ORACLE                 | ANSI/ISO or Oracle behavior.                                                                                                                                                                                                       |
| NATIVE_TYPES                                       | NO                     | Support for native float/double.                                                                                                                                                                                                   |
| NLS_CHAR=(var1, ..., varn)                         | none                   | Specify multibyte character variables.                                                                                                                                                                                             |
| NLS_LOCAL={YES \| NO}                              | NO                     | Control multibyte character semantics.                                                                                                                                                                                             |
| OBJECTS={YES \| NO}                                | YES                    | Support of object types.                                                                                                                                                                                                           |
| ONAME=\]filename                                   | iname.c                | Name of the output (code) file.                                                                                                                                                                                                    |
| ORACA={YES \| NO} \*                               | NO                     | Whether to use the ORACA.                                                                                                                                                                                                          |
| PAGELEN=30..256                                    | 80                     | Page length of the listing file.                                                                                                                                                                                                   |
| PARSE={NONE \| PARTIAL \| FULL}                    | FULL                   | Whether Pro\*C/C++ parses (with a C parser) the.pc source.                                                                                                                                                                         |
| PLAN_BASELINE={module_name \|YES \|NO}             | NO                     | Specify a module name to create a SQL Plan Baseline.                                                                                                                                                                               |
| PLAN_PREFIX={prefix_name \| none}                  | none                   | Ensures that the plan name does not exceed 128 bytes.                                                                                                                                                                              |
| PLAN_RUN={YES \| NO}                               | NO                     | Executes the generated SQL file                                                                                                                                                                                                    |
| PLAN_FIXED={YES \| NO}                             | YES                    | Specifies whether or not the created plan baseline is fixed or non-fixed                                                                                                                                                           |
| PLAN_ENABLED={YES \| NO}                           | YES                    | Enables the Plan Baseline that is created.                                                                                                                                                                                         |
| MEMFORPREFETCH=0..4294967294                       | none                   | Speed up queries by pre-fetching rows that fill the specified memory.                                                                                                                                                              |
| PREFETCH=0..65535                                  | 1                      | Speed up queries by pre-fetching a given number of rows.                                                                                                                                                                           |
| RELEASE_CURSOR={YES \| NO} \*                      | NO                     | Control release of cursors from cursor cache.                                                                                                                                                                                      |
| SELECT_ERROR={YES \| NO} \*                        | YES                    | Flagging of SELECT errors.                                                                                                                                                                                                         |
| SQLCHECK={SEMANTICS \| SYNTAX} \*                  | SYNTAX                 | Amount of precompile time SQL checking.                                                                                                                                                                                            |
| SYS_INCLUDE=pathname                               | none                   | Directory where system header files, such as iostream.h, are found.                                                                                                                                                                |
| THREADS={YES \| NO}                                | NO                     | Indicates a shared server application.                                                                                                                                                                                             |
| TYPE_CODE={ORACLE \| ANSI}                         | ORACLE                 | Use of Oracle or ANSI type codes for dynamic SQL.                                                                                                                                                                                  |
| UNSAFE_NULL={YES \| NO}                            | NO                     | UNSAFE_NULL=YES disables the ORA-01405 message.                                                                                                                                                                                    |
| USERID=username/password\[@dbname\]                | none                   | Username/password\[@dbname\] connect string.                                                                                                                                                                                       |
| UTF16_CHARSET={NCHAR_CHARSET \| DB_CHARSET}        | NCHAR_CHARSET          | Specify the character set form used by UNICODE(UTF16).                                                                                                                                                                             |
| VARCHAR={YES \| NO}                                | NO                     | Allow the use of implicit VARCHAR structures.                                                                                                                                                                                      |
| VERSION={ANY \| LATEST \| RECENT} \*               | RECENT                 | Which version of an object is to be returned.                                                                                                                                                                                      |

### 10.4 Entering Options

You can enter any precompiler option in the command line. Many can also be entered inline in the precompiler program source file, using the EXEC ORACLE OPTION statement.

#### 10.4.1 On the Command Line

You enter precompiler options in the command line using the following syntax:

    ... [OPTION_NAME=value] [OPTION_NAME=value] ...

Separate each option=value specification with one or more spaces. For example, you might enter the following:

    ... CODE=ANSI_C MODE=ANSI

#### 10.4.2 Inline

You enter options inline by coding EXEC ORACLE statements, using the following syntax:

    EXEC ORACLE OPTION (OPTION_NAME=value);

For example, you might code the following:

    EXEC ORACLE OPTION (RELEASE_CURSOR=yes);

##### 10.4.2.1 Uses for EXEC ORACLE

The EXEC ORACLE feature is especially useful for changing option values during precompilation. For example, you might want to change HOLD_CURSOR and RELEASE_CURSOR on a statement-by-statement basis.

Specifying options inline or in a configuration file is also helpful if your operating system limits the number of characters you can enter on the command line.

**See Also:**

[Performance Tuning](performance-tuning.md) shows you how to optimize runtime performance using inline options.

##### 10.4.2.2 Scope of EXEC ORACLE

An EXEC ORACLE statement stays in effect until textually superseded by another EXEC ORACLE statement specifying the same option. In the following example, HOLD_CURSOR=NO stays in effect until superseded by HOLD_CURSOR=YES:

    char emp_name[20];
    int  emp_number, dept_number;
    float salary;

    EXEC SQL WHENEVER NOT FOUND DO break;
    EXEC ORACLE OPTION (HOLD_CURSOR=NO);

    EXEC SQL DECLARE emp_cursor CURSOR FOR
    SELECT empno, deptno FROM emp;

    EXEC SQL OPEN emp_cursor;
    printf(
    "Employee Number  Department\n--------------------------\n");
    for (;;)
    {
       EXEC SQL FETCH emp_cursor INTO :emp_number, :dept_number;
       printf("%d\t%d\n", emp_number, dept_number);
    }

    EXEC SQL WHENEVER NOT FOUND CONTINUE;
    for (;;)
    {
       printf("Employee number: ");
       scanf("%d", &emp_number);
       if (emp_number == 0)
          break;
       EXEC ORACLE OPTION (HOLD_CURSOR=YES);
       EXEC SQL SELECT ename, sal
          INTO :emp_name, :salary
          FROM emp WHERE empno = :emp_number;
       printf("Salary for %s is %6.2f.\n", emp_name, salary);

#### 10.4.3 Column Properties Support

Column properties are returned in an 8 byte value where each bit indicates a column property. Three column properties are supported:

      +---------------------------------------------------+
      ! 32 |..............| 10 | 9 | 8 |......| 3 | 2 | 1 |
      +---------------------------------------------------+
                                               |    |   |
                                               |    |   |-> auto-increment column
                                               |    |-> auto value always generated
                                               |-> if generated by default when null

You can get the Column Properties through dynamic statements using the new SQLDA member (`sqlda->CP[]`).

    struct SQLDA {
      /* ub4    */ int        N; /* Descriptor size in number of entries        */
      ..........
      ..........
      ..........
      ..........
      /* ub2*   */ short     *Z; /* Ptr to Arr of cur lengths of ind. var. names*/
      /* ub8*   */ long long *CP; /* Ptr to Arr of column properties            */
      };

This member is updated as part of a meta data DESCRIBE.

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

### 10.5 About Using the Precompiler Options

This section is organized for easy reference. It lists precompiler options alphabetically, and for each option gives its purpose, syntax, and default value. Usage notes help you understand how the option works.

#### 10.5.1 AUTO_CONNECT

##### Purpose

Allows automatic connection to the CLUSTER\$ account.

##### Syntax

AUTO_CONNECT={YES \| NO}

##### Default

NO

##### Usage Notes

Can be entered only on the command line or in a configuration file.

If AUTO_CONNECT=YES, and the application is not already connected to a database when it processes the first executable SQL statement, it attempts to connect using the userid

    CLUSTER$username

where username is your current operating system user or task name and CLUSTER\$username is a valid Oracle userid.

When AUTO_CONNECT=NO, you must use the CONNECT statement in your program to connect to Oracle.

#### 10.5.2 CHAR_MAP

##### Purpose

Specifies the default mapping of C host variables of type char or char\[n\], and pointers to them, into SQL.

##### Syntax

CHAR_MAP={VARCHAR2 \| CHARZ \| STRING \| CHARF}

##### Default

CHARZ

##### Usage Note

Before release 8.0, you had to declare char or char\[n\] host variables as CHAR, using the SQL DECLARE statement. The external datatypes VARCHAR2 and CHARZ were the default character mappings of Oracle7.

**See Also:**

- "[VARCHAR Variables](datatypes-and-host-variables.md) " for a table of CHAR_MAP settings, descriptions of the datatype, and where they are the default.

- "[Inline Usage of the CHAR_MAP Option](advanced-topics.md)" for an example of usage of CHAR_MAP in Pro\*C/C++.

#### 10.5.3 CINCR

##### Purpose

Allows the application to set the next increment for physical connections to be opened to the database.

##### Syntax

CINCR = Range is 1 to (CMAX-CMIN).

##### Default

1

##### Usage Notes

Initially, all physical connections as specified through CMIN are opened to the server. Subsequently, physical connections are opened only when necessary. Users should set CMIN to the total number of planned or expected concurrent statements to be run by the application to get optimum performance. The default value is set to 2.

#### 10.5.4 CLOSE_ON_COMMIT

##### Purpose

Specifies whether or not all cursors declared without the WITH HOLD clause are closed on commit.

##### Syntax

CLOSE_ON_COMMIT={YES \| NO}

##### Default

NO

##### Usage Notes

Can be used only on the command line or in a configuration file.

This option will only have an effect when a cursor is not coded using the WITH HOLD clause in a DECLARE CURSOR statement, since that will override both the new option and the existing behavior which is associated with the MODE option. If MODE is specified at a higher level than CLOSE_ON_COMMIT, then MODE takes precedence. For example, the defaults are MODE=ORACLE and CLOSE_ON_COMMIT=NO. If the user specifies MODE=ANSI on the command line, then any cursors not using the WITH HOLD clause will be closed on commit.

When CLOSE_ON_COMMIT=NO (when MODE=ORACLE), issuing a COMMIT or ROLLBACK will close only cursors that are declared using the FOR UPDATE clause or are referenced in a CURRENT OF clause. Other cursors that are not affected by the COMMIT or ROLLBACK statement, remain open, if they are open already. However, when CLOSE_ON_COMMIT=YES (when MODE=ANSI), issuing a COMMIT or ROLLBACK closes all cursors.

**Related Topics**

- [Scrollable Cursors](embedded-SQL.md)
- Macro and Micro Options

#### 10.5.5 CMAX

##### Purpose

Specifies the maximum number of physical connections that can be opened for the database.

##### Syntax

CINCR = Range is 1 to 65535

##### Default

100

##### Usage Notes

CMAX value must be at least CMIN+CINCR.Once this value is reached, more physical connections cannot be opened.In a typical application, running 100 concurrent database operations is more than sufficient. The user can set an appropriate value.

#### 10.5.6 CMIN

##### Purpose

Specifies the minimum number of physical connections that can be opened for the database.

##### Syntax

CINCR = Range is 1 to (CMAX-CINCR).

##### Default

2

##### Usage Notes

CMAX value must be at least CMIN+CINCR.Once this value is reached, more physical connections cannot be opened.In a typical application, running 100 concurrent database operations is more than sufficient. The user can set an appropriate value.

#### 10.5.7 CNOWAIT

##### Purpose

This attribute determines if the application must repeatedly try for a physical connection when all other physical connections in the pool are busy, and the total number of physical connections has already reached its maximum.

##### Syntax

CNOWAIT = Range is 1 to 65535.

##### Default

0 which means not set.

##### Usage Notes

If physical connections are not available and no more physical connections can be opened, an error is thrown when this attribute is set. Otherwise, the call waits until it acquires another connection. By default, CNOWAIT is not to be set so a thread will wait until it can acquire a free connection, instead of returning an error.

#### 10.5.8 CODE

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

**See Also:**

"[Code Generation](C-Plus-Plus-Applications.md)" for all of the consequences of using this option value.

#### 10.5.9 COMMON_PARSER

##### Purpose

Specifies that the SQL99 syntax for SELECT, INSERT, DELETE, UPDATE and body of the cursor in a DECLARE CURSOR statement will be supported.

##### Syntax

COMMON_PARSER={YES \| NO}

##### Default

NO

##### Usage Notes

Can be entered in the command line.

#### 10.5.10 COMP_CHARSET

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

#### 10.5.11 CONFIG

##### Purpose

Specifies the name of a user configuration file.

##### Syntax

CONFIG=filename

##### Default

None

##### Usage Notes

Can be entered only on the command line.

This option is the only way you can inform Pro\*C/C++ of the name and location of user configuration files.

#### 10.5.12 CPOOL

##### Purpose

Based on this option, the precompiler generates the appropriate code that directs SQLLIB to enable or disable the connection pool feature.

##### Syntax

CPOOL = {YES\|NO}

##### Default

NO

##### Usage Notes

If this option is set to NO, other connection pooling options will be ignored by the precompiler.

#### 10.5.13 CPP_SUFFIX

##### Purpose

The CPP_SUFFIX option provides the ability to specify the filename extension that the precompiler appends to the C++ output file generated when the CODE=CPP option is specified.

##### Syntax

CPP_SUFFIX=filename_extension

##### Default

System-specific.

##### Usage Notes

Most C compilers expect a default extension of ".c" for their input files. Different C++ compilers, however, can expect different filename extensions. The CPP_SUFFIX option provides the ability to specify the filename extension that the precompiler generates. The value of this option is a string, without the quotes or the period. For example, CPP_SUFFIX=cc, or CPP_SUFFIX=C.

#### 10.5.14 CTIMEOUT

##### Purpose

Physical connections that are idle for more than the specified time (in seconds) are terminated to maintain an optimum number of open physical connections

##### Syntax

CTIMEOUT = Range is 1 to 65535.

##### Default

0 which means not set.

##### Usage Notes

Physical connections will not be closed until the connection pool is terminated.Creating a new physical connection will cost a round trip to the server.

#### 10.5.15 DB2_ARRAY

##### Purpose

Based on this option, the precompiler activates the additional array insert/select syntax.

##### Syntax

DB2_ARRAY={YES \|NO}

##### Default

NO

##### Usage Notes

If this option is set to NO, the Oracle precompiler syntax is supported, otherwise the DB2 insert/select array syntax is supported.

#### 10.5.16 DBMS

##### Purpose

Specifies whether Oracle follows the semantic and syntactic rules of Oracle9i, Oracle8i, Oracle8, Oracle7, or the native version of Oracle (that is, the version to which the application is connected).

##### Syntax

DBMS={NATIVE \| V7 \| V8}

##### Default

NATIVE

##### Usage Notes

Can be entered only on the command line, or in a configuration file.

The DBMS option lets you control the version-specific behavior of Oracle. When DBMS=NATIVE (the default), Oracle follows the semantic and syntactic rules of the database version to which the application is connected.

When DBMS=V8, or DBMS=V7, Oracle follows the respective rules for Oracle9i (which remain the same as for Oracle7, Oracle8, and Oracle8i).

V6_CHAR is not supported in Oracle and its functionality is provided by the precompiler option CHAR_MAP.

Table 10-3 DBMS and MODE Interaction

| Situation                                                | DBMS=V7 \| V8MODE=ANSI           | DBMS=V7 \| V8MODE=ORACLE          |
|:---------------------------------------------------------|:---------------------------------|:----------------------------------|
| "no data found" warning code                             | +100                             | +1403                             |
| fetch NULLs without using indicator variables            | error -1405                      | error -1405                       |
| fetch truncated values without using indicator variables | no error but sqlwarn\[1\] is set | no error but sqlwarn\[1\]) is set |
| cursors closed by COMMIT or ROLLBACK                     | all explicit                     | CURRENT OF only                   |
| open an already OPENed cursor                            | error -2117                      | no error                          |
| close an already CLOSEd cursor                           | error -2114                      | no error                          |
| SQL group function ignores NULLs                         | no warning                       | no warning                        |
| when SQL group function in multirow query is called      | FETCH time                       | FETCH time                        |
| declare SQLCA structure                                  | optional                         | required                          |
| declare SQLCODE or SQLSTATE status variable              | required                         | optional, but Oracle ignores      |
| integrity constraints                                    | enabled                          | enabled                           |
| PCTINCREASE for rollback segments                        | not allowed                      | not allowed                       |
| MAXEXTENTS storage parameters                            | not allowed                      | not allowed                       |

**Related Topics**

- CHAR_MAP

#### 10.5.17 DEF_SQLCODE

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

#### 10.5.18 DEFINE

##### Purpose

Defines a name that can be used in \#ifdef and \#ifndef Pro\*C/C++ precompiler directives. The defined name can also be used by the EXEC ORACLE IFDEF and EXEC ORACLE IFNDEF statements.

##### Syntax

DEFINE=name

##### Default

None

##### Usage Notes

Can be entered on the command line or inline. You can only use DEFINE to define a name—you cannot define macros with it. For example, the following use of define is not valid:

    proc my_prog DEFINE=LEN=20

Using DEFINE in the correct way, you could do

    proc my_prog DEFINE=XYZZY

And then in my_prog.pc, code

    #ifdef XYZZY
    ...
    #else
    ...
    #endif

Or, you could just as well code

    EXEC ORACLE IFDEF XYZZY;
    ...
    EXEC ORACLE ELSE;
    ...
    EXEC ORACLE ENDIF;

The following example is invalid:

    #define XYZZY
    ...
    EXEC ORACLE IFDEF XYZZY
    ...
    EXEC ORACLE ENDIF;

EXEC ORACLE conditional statements are valid only if the macro is defined using EXEC ORACLE DEFINE or the DEFINE option.

If you define a name using DEFINE=, and then conditionally include (or exclude) a code section using the Pro\*C/C++ precompiler \#ifdef (or \#ifndef) directives, you must also make sure that the name is defined when you run the C compiler. For example, for UNIX `cc`, you must use the -D option to define the name.

#### 10.5.19 DURATION

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

#### 10.5.20 DYNAMIC

##### Purpose

This micro option specifies the descriptor behavior in dynamic SQL Method 4. The setting of MODE determines the setting of DYNAMIC.

##### Syntax

DYNAMIC={ORACLE \| ANSI}

##### Default

ORACLE

##### Usage Notes

Cannot be entered inline by use of the EXEC ORACLE OPTION statement.

See the DYNAMIC option settings in [ANSI Dynamic SQL Precompiler Options](ANSI-dynamic-SQL.md).

#### 10.5.21 ERRORS

##### Purpose

Specifies whether error messages are sent to the terminal as well as the listing file (YES), or just to the listing file (NO).

##### Syntax

ERRORS={YES \| NO}

##### Default

YES

##### Usage Notes

Can be entered only on the command line, or in a configuration file.

#### 10.5.22 ERRTYPE

##### Purpose

Specifies an output file in which errors generated in processing type files are written. If omitted, errors are output to the screen.

##### Syntax

ERRTYPE=filename

##### Default

None

##### Usage Notes

Only one error file will be produced. If multiple values are entered, the last one is used by the precompiler.

**Related Topics**

- INTYPE

#### 10.5.23 EVENTS

##### Purpose

Specifies that the application is interested in registering for and receiving notifications.

##### Syntax

EVENTS={YES \| NO}

##### Default

NO

##### Usage Notes

Can only be entered in the command line.

#### 10.5.24 FIPS

##### Purpose

Specifies whether extensions to ANSI SQL are flagged (by the FIPS Flagger). An extension is any SQL element that violates ANSI format or syntax rules, except privilege enforcement rules.

##### Syntax

FIPS={SQL89 \| SQL2 \| YES \| NO}

##### Default

None

##### Usage Notes

Can be entered inline or on the command line.

When FIPS=YES, the FIPS Flagger is enabled, and warning (not error) messages are issued if you use an Oracle extension to ANSI SQL, or use an ANSI SQL feature in a nonconforming manner. Extensions to ANSI SQL that are flagged at precompile time include the following:

- Array interface including the FOR clause

- SQLCA, ORACA, and SQLDA data structures

- Dynamic SQL including the DESCRIBE statement

- Embedded PL/SQL blocks

- Automatic datatype conversion

- DATE, NUMBER, RAW, LONGRAW, VARRAW, ROWID, VARCHAR2, and VARCHAR datatypes

- Pointer host variables

- Oracle OPTION statement for specifying runtime options

- TOOLS statements in user exits

- CONNECT statement

- TYPE and VAR datatype equivalence statements

- AT db_name clause

- DECLARE...DATABASE, ...STATEMENT, and ...TABLE statements

- SQLWARNING condition in WHENEVER statement

- DO function_name() and "do break" and "do continue"actions in WHENEVER statement

- COMMENT and FORCE TRANSACTION clauses in COMMIT statement

- FORCE TRANSACTION and TO SAVEPOINT clauses in ROLLBACK statement

- RELEASE parameter in COMMIT and ROLLBACK statements

- Optional colon-prefixing of WHENEVER...GOTO labels, and of host variables in the INTO clause

#### 10.5.25 HEADER

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

**Related Topics**

- [Precompiled Header Files](advanced-topics.md)

#### 10.5.26 HOLD_CURSOR

##### Purpose

Specifies how the cursors for SQL statements and PL/SQL blocks are handled in the cursor cache.

##### Syntax

HOLD_CURSOR={YES \| NO}

##### Default

NO

##### Usage Notes

Can be entered inline or on the command line.

You can use HOLD_CURSOR to improve the performance of your program.

When a SQL data manipulation statement is executed, its associated cursor is linked to an entry in the cursor cache. The cursor cache entry is in turn linked to an Oracle private SQL area, which stores information needed to process the statement. HOLD_CURSOR controls what happens to the link between the cursor and cursor cache.

When HOLD_CURSOR=NO, after Oracle executes the SQL statement and the cursor is closed, the precompiler marks the link as reusable. The link is reused as soon as the cursor cache entry to which it points is needed for another SQL statement. This frees memory allocated to the private SQL area and releases parse locks.

When HOLD_CURSOR=YES, the link is maintained; the precompiler does not reuse it. This is useful for SQL statements that are often executed because it speeds up subsequent executions and there is no need to re-parse the statement or allocate memory for an Oracle private SQL area.

For inline use with implicit cursors, set HOLD_CURSOR before executing the SQL statement. For inline use with explicit cursors, set HOLD_CURSOR before CLOSEing the cursor.

RELEASE_CURSOR=YES overrides HOLD_CURSOR=YES and HOLD_CURSOR=NO overrides RELEASE_CURSOR=NO. For information showing how these two options interact, see [Table B-1](performance-tuning.md).

**Related Topics**

- [Performance Tuning](performance-tuning.md)

#### 10.5.27 IMPLICIT_SVPT

##### Purpose

Controls whether an implicit savepoint is taken prior to the start of a new batched insert.

##### Syntax

implicit_svpt={YES\|NO}

##### Default

NO

##### Usage Notes

If implict_svpt=yes, a savepoint is taken prior to the start of a new batch of rows. If an error occurs on the insert, an implicit "rollback to savepoint" is executed. This option exists for DB2 compatibility, the obvious downside being the extra round-trip.

If implict_svpt=no, there is no implicit savepoint taken. If an error occurs on the buffered insert, then it is reported back to the application, but no rollback is executed.

#### 10.5.28 INAME

##### Purpose

Specifies the name of the input file.

##### Syntax

INAME=path_and_filename

##### Default

None

##### Usage Notes

Can be entered only on the command line.

All input file names must be unique at precompilation time.

You can omit the filename extension if it is `.pc`. If the input filename is the first option on the command line, you can omit the INAME= part of the option. For example:

    proc sample1 MODE=ansi

to precompile the file `sample1.pc`, using ANSI mode. This command is the same as

    proc INAME=sample1 MODE=ansi

**Note:**

The `sqlctx` hash value is generated based on the `INAME` parameter passed to the Pro\*C/C++ command. This can cause issues in the applications where files having the same name are stored in different directories containing different functions and the build scripts are sent to the physical directory to precompile the program. As a result, there is no need to place the makefiles at a higher level and precompile files using their pathnames.

#### 10.5.29 INCLUDE

##### Purpose

Specifies a directory path for files included using the \#include or EXEC SQL INCLUDE directives.

##### Syntax

INCLUDE=pathname or INCLUDE=(path_1,path_2,...,path_n)

##### Default

Current directory and paths built into Pro\*C/C++.

##### Usage Notes

Can be entered inline or on the command line.

You use INCLUDE to specify a directory path for included files. The precompiler searches directories in the following order:

1.  the current directory

2.  the system directory specified in a SYS_INCLUDE precompiler option

3.  the directories specified by the INCLUDE option, in the order they are entered

4.  the built-in directories for standard header files

You normally do not need to specify a directory path for Oracle-specific header files such as `sqlca.h` and `sqlda.h`.

**Note:**

If you specify an Oracle-specific filename without an extension for inclusion, Pro\*C/C++ assumes an extension of `.h`. So, included files should have an extension, even if it is not `.h`.

For all other header files, the precompiler does not assume a `.h `extension.

You must still use INCLUDE to specify directory paths for non-standard files, unless they are stored in the current directory. You can specify more than one path on the command line, as follows:

    ... INCLUDE=path_1 INCLUDE=path_2 ...

**Note:**

 If the file you want to include resides in another directory, make sure that there is no file with the same name in the current directory.

The syntax for specifying a directory path using the INCLUDE option is system specific. Follow the conventions used for your operating system

**Note:**

For the INCLUDE option, the precedence of option values gets reversed. Unlike other options in which the values get overwritten, INCLUDE appends all the directory files that are mentioned in:

- Precompiler

- Pro\*C/C++ system configuration file

- Pro\*C/C++ user configuration file

- Command line

- Inline

However, there is a difference between passing values within or without brackets. If you pass a single value or directory list within brackets, then the existing value of INCLUDE is overwritten. If you pass the list as a simple value without brackets, it will supplement any existing value.

#### 10.5.30 INTYPE

##### Purpose

Specifies one or more OTT-generated type files (only needed if Object types are used in the application).

##### Syntax

INTYPE=(file_1,file_2,...,file_n)

##### Default

None

##### Usage Notes

There will be one type file for each Object type in the Pro\*C/C++ code.

#### 10.5.31 LINES

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

The Pro\*C/C++ precompiler does not support the \#line directive. This means that you cannot directly code \#line directives in the precompiler source. But you can still use the LINES= option to have the precompiler insert \#line directives for you.

**Related Topics**

- [Directives Ignored](advanced-topics.md)

#### 10.5.32 LNAME

##### Purpose

Specifies the name of the listing file.

##### Syntax

LNAME=filename

##### Default

None

##### Usage Notes

Can be entered only on the command line.

The default filename extension for the listing file is `.lis`.

#### 10.5.33 LTYPE

##### Purpose

Specifies the type of listing file generated.

##### Syntax

LTYPE={NONE \| SHORT \| LONG}

##### Default

SHORT

##### Usage Notes

Can be entered on the command line or in a configuration file.

When a listing file is generated, the LONG format is the default. With LTYPE=LONG specified, all of the source code is listed as it is parsed and messages listed as they are generated. In addition, the Pro\*C/C++ options currently in effect are listed.

With LTYPE=SHORT specified, only the generated messages are listed—no source code—with line references to the source file to help you locate the code that generated the message condition.

With LTYPE=NONE specified, no list file is produced unless the LNAME option explicitly specifies a name for a list file. Under the latter condition, the list file is generated with LTYPE=LONG assumed.

#### 10.5.34 MAX_ROW_INSERT

##### Purpose

Controls the number of rows that need to be buffered before executing the INSERT statement.

##### Syntax

max_row_insert={0...1000}

##### Default

0

##### Usage Notes

Any number greater than zero enables buffered insert feature and buffers that many rows before executing the INSERT statement.

#### 10.5.35 MAXLITERAL

##### Purpose

Specifies the maximum length of string literals generated by the precompiler, so that compiler limits are not exceeded.

##### Syntax

MAXLITERAL=integer, range is 10 to 1024

##### Default

1024

##### Usage Notes

Cannot be entered inline.

The maximum value of MAXLITERAL is compiler dependent. For example, some C compilers cannot handle string literals longer than 512 characters, so you would specify MAXLITERAL=512.

Strings that exceed the length specified by MAXLITERAL are divided during precompilation, then recombined (concatenated) at run time.

You can enter MAXLITERAL inline but your program can set its value only once, and the EXEC ORACLE statement must precede the first EXEC SQL statement. Otherwise, Pro\*C/C++ issues a warning message, ignores the extra or misplaced EXEC ORACLE statement, and continues processing.

#### 10.5.36 MAXOPENCURSORS

##### Purpose

Specifies the number of concurrently open cursors that the precompiler tries to keep cached.

##### Syntax

MAXOPENCURSORS=integer

##### Default

10

##### Usage Notes

Can be entered inline or on the command line.

You can use MAXOPENCURSORS to improve the performance of your program. When precompiling separately, use MAXOPENCURSORS. MAXOPENCURSORS specifies the initial size of the SQLLIB cursor cache.

When an implicit statement is executed and HOLD_CURSOR=NO, or an explicit cursor is closed, the cursor entry is marked as reusable. If this statement is issued again and the cursor entry has not been used for another statement, it is reused.

If a new cursor is needed and the number of cursors allocated is less than MAXOPENCURSORS, then the next one in the cache is allocated. Once MAXOPENCCURSORS has been exceeded Oracle first tries to reuse a previous entry. If there are no free entries, then an additional cache entry will be allocated. Oracle will continue to do this until the program runs out of memory or the database parameter OPEN_CURSORS is exceeded.

During normal processing, when using HOLD_CURSOR=NO and RELEASE_CURSOR=NO (the default), it is advisable to set MAXOPENCURSORS to no more than 6 less than the database parameter OPEN_CURSORS to allow for the cursors used by the data dictionary to process statements.

As your program's need for concurrently open cursors grows, you might want to respecify MAXOPENCURSORS to match the need. A value of 45 to 50 is not uncommon, but remember that each cursor requires another private SQL area in the user process memory space. The default value of 10 is adequate for most programs.

**Related Topics**

- [Performance Tuning](performance-tuning.md)
- [Guidelines for Programming](precompiler-concepts.md)

#### 10.5.37 MODE

##### Purpose

Specifies whether your program observes Oracle practices or complies with the current ANSI/ISO SQL standards.

##### Syntax

MODE={ANSI \| ISO \| ORACLE}

##### Default

ORACLE

##### Usage Notes

Can be entered only on the command line or in a configuration file.

In the context of this option ISO is equivalent to ANSI.

When MODE=ORACLE (the default), your embedded SQL program observes Oracle practices. For example, a Declare Section is optional, and blanks are stripped.

When MODE=ANSI, your program complies fully with the ANSI SQL standard, and the following changes go into effect:

- Issuing a COMMIT or ROLLBACK closes all explicit cursors.

- You cannot OPEN an already open cursor or CLOSE an already closed cursor. (When MODE=ORACLE, you can reOPEN an open cursor to avoid re-parsing.)

- You must declare a either a long variable named SQLCODE or a char SQLSTATE\[6\]variable (uppercase is required for both variables) that is in the scope of every EXEC SQL statement. The same SQLCODE or SQLSTATE variable need not be used in each case; that is, the variable need not be global.

- Declaring the SQLCA is optional. You need not include the SQLCA.

- The "no data found" Oracle warning code returned to SQLCODE becomes +100 instead of +1403. The message text does not change.

- You must have a Declare Section for host variables.

#### 10.5.38 NATIVE_TYPES

##### Purpose

Support for native float/double.

##### Syntax

NATIVE_TYPES = {YES\|NO}

##### Default

NO

##### Usage Notes

The native float and native double datatypes represent the single-precision and double-precision floating point values. They are represented natively, that is, in the host system's floating point format.

#### 10.5.39 NLS_CHAR

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

#### 10.5.40 NLS_LOCAL

##### Purpose

Determines whether multibyte character set conversions are performed by the precompiler runtime library, SQLLIB, or by the database server.

##### Syntax

NLS_LOCAL={NO \| YES}

##### Default

NO

##### Usage Notes

When set to YES, local multibyte support is provided by Pro\*C/C++ and the SQLLIB library. The option NLS_CHAR must be used to indicate which C host variables are multibyte.

When set to NO, Pro\*C/C++ will use the database server support for multibyte objects. Set NLS_LOCAL to NO for all new applications.

Environment variable NLS_NCHAR must be set to a valid fixed-width National Character Set. Variable-width National Character Sets are not supported.

Can be entered only on the command line, or in a configuration file.

#### 10.5.41 OBJECTS

##### Purpose

Requests support for object types.

##### Syntax

OBJECTS={YES \| NO}

##### Default

YES

##### Usage Notes

Can only be entered in the command line.

#### 10.5.42 ONAME

##### Purpose

Specifies the name of the output file. The output file is the C code file that the precompiler generates.

##### Syntax

ONAME=path_and_filename

##### Default

INAME with a .c extension.

##### Usage Notes

Can be entered only on the command line. Use this option to specify the full path name of the output file, where the path name differs from that of the input (`.pc`) file. For example, if you issue the command:

    proc iname=my_test

the default output filename is `my_test.c`. If you want the output filename to be `my_test_1.c`, issue the command

    proc iname=my_test oname=my_test_1.c

You should add the `.c` extension to files specified using ONAME because one is not added by default.

**Note:**

Oracle recommends that you not let the output filename default, but rather name it explicitly using ONAME. If you specify an ONAME value without an extension, the name of the generated file will not have one.

#### 10.5.43 ORACA

##### Purpose

Specifies whether a program can use the Oracle Communications Area (ORACA).

##### Syntax

ORACA={YES \| NO}

##### Default

NO

##### Usage Notes

Can be entered inline or on the command line.

When ORACA=YES, you must place either the EXEC SQL INCLUDE ORACA or \#include `oraca.h` statement in your program.

#### 10.5.44 OUTLINE

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

#### 10.5.45 OUTLNPREFIX

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

#### 10.5.46 PAGELEN

##### Purpose

Specifies the number of lines for each physical page of the listing file.

##### Syntax

PAGELEN=integer

##### Default

80

##### Usage Notes

Cannot be entered inline. The value range allowed is 30..256..

#### 10.5.47 PARSE

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

**Related Topics**

- [About Parsing Code](C-Plus-Plus-Applications.md)
- [Declare Section](precompiler-concepts.md)
- [Conditional Precompilation](precompiler-concepts.md)

#### 10.5.48 PLAN_BASELINE

##### Purpose

Creates a SQL Plan Baseline by specifying the module name.

##### Syntax

PLAN_BASELINE={module_name \| YES \| NO}

##### Default

NO

##### Usage Notes

The module name will become a part of the unique plan name generated by appending the filename, file type, and sequence number.

#### 10.5.49 PLAN_PREFIX

##### Purpose

Ensures that the plan name does not exceed 128 bytes.

##### Syntax

PLAN_PREFIX={prefix_name \| none}

##### Default

none

##### Usage Notes

It is an optional command. The default is none which means that no prefix name is used, and if the plan name exceeds 128 bytes an error message is generated.

#### 10.5.50 PLAN_RUN

##### Purpose

Executes the generated SQL file.

##### Syntax

PLAN_RUN={YES \| NO}

##### Default

NO

##### Usage Notes

If the PLAN_RUN option is not set then the generated SQL file is not executed.

#### 10.5.51 PLAN_FIXED

##### Purpose

Specifies whether or not the created plan baseline is fixed or non-fixed.

##### Syntax

PLAN_FIXED={ YES \| NO }

##### Default

YES

##### Usage Notes

When set to NO, a non-fixed Plan Baseline is created.

#### 10.5.52 PLAN_ENABLED

##### Purpose

Enables the use of the Plan Baseline that is created.

##### Syntax

PLAN_ENABLED={ YES \| NO }

##### Default

YES

##### Usage Notes

When set to the default, YES, the created Plan Baseline is used for plan selection. When set to NO, the Plan Baseline is created, but is not used until enabled manually.

#### 10.5.53 MEMFORPREFETCH

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

#### 10.5.54 PREFETCH

##### Purpose

Use this option to speed up queries by pre-fetching a number of rows.

##### Syntax

PREFETCH=integer

##### Default

1

##### Usage Notes

Can be used in a configuration file or on the command-line. The value of the integer is used for execution of all queries using explicit cursors, subject to the rules of precedence.

When used in-line it must placed before OPEN statements with explicit cursors. Then the number of rows pre-fetched when that OPEN is done is determined by the last in-line PREFETCH option in effect.

The value range allowed is 0.. 65535.

#### 10.5.55 RELEASE_CURSOR

##### Purpose

Specifies how the cursors for SQL statements and PL/SQL blocks are handled in the cursor cache.

##### Syntax

RELEASE_CURSOR={YES \| NO}

##### Default

NO

##### Usage Notes

Can be entered inline or on the command line.

You can use RELEASE_CURSOR to improve the performance of your program.

When a SQL data manipulation statement is executed, its associated cursor is linked to an entry in the cursor cache. The cursor cache entry is in turn linked to an Oracle private SQL area, which stores information needed to process the statement. RELEASE_CURSOR controls what happens to the link between the cursor cache and private SQL area.

When RELEASE_CURSOR=YES, after Oracle executes the SQL statement and the cursor is closed, the precompiler immediately removes the link. This frees memory allocated to the private SQL area and releases parse locks. To make sure that associated resources are freed when you CLOSE a cursor, you must specify RELEASE_CURSOR=YES.

When RELEASE_CURSOR=NO, the link is maintained. The precompiler does not reuse the link unless the number of open cursors exceeds the value of MAXOPENCURSORS. This is useful for SQL statements that are often executed because it speeds up subsequent executions. There is no need to re-parse the statement or allocate memory for an Oracle private SQL area.

For inline use with implicit cursors, set RELEASE_CURSOR before executing the SQL statement. For inline use with explicit cursors, set RELEASE_CURSOR before CLOSEing the cursor.

RELEASE_CURSOR=YES overrides HOLD_CURSOR=YES.

**Related Topics**

- [Performance Tuning](performance-tuning.md)

#### 10.5.56 RUNOUTLINE

##### Purpose

Provides the developer with the option of executing "create outline" statements either by using precompiler or by the developer manually at a later time.

##### Syntax

runoutline={yes \| no}

##### Default

no

##### Usage Notes

If runoutline=yes, then the generated 'create outline' statements are executed by the precompiler/translator at the end of a successful precompilation.

The outline option should be set to true or category_name when runoutline is used. Semantic check should be full when this option is turned on, which means option sqlcheck=full/semantics. If sqlcheck=syntax/limited/none, then error will be generated.

#### 10.5.57 SELECT_ERROR

##### Purpose

Specifies whether your program generates an error when a SELECT statement returns more than one row, or more rows than a host array can accommodate.

##### Syntax

SELECT_ERROR={YES \| NO}

##### Default

YES

##### Usage Notes

Can be entered inline or on the command line.

When SELECT_ERROR=YES, an error is generated when a single-row SELECT returns too many rows, or when an array SELECT returns more rows than the host array can accommodate. The result of the SELECT is indeterminate.

When SELECT_ERROR=NO, no error is generated when a single-row SELECT returns too many rows, or when an array SELECT returns more rows than the host array can accommodate.

Whether you specify YES or NO, a random row is selected from the table. The only way to ensure a specific ordering of rows is to use the ORDER BY clause in your SELECT statement. When SELECT_ERROR=NO and you use ORDER BY, Oracle returns the first row, or the first n rows when you are SELECTing into an array. When SELECT_ERROR=YES, whether or not you use ORDER BY, an error is generated when too many rows are returned.

#### 10.5.58 STMT_CACHE

##### Purpose

Denotes the Statement cache size for the dynamic SQL statements.

##### Syntax

STMT_CACHE = Range is 0 to 65535

##### Default

0

##### Usage Notes

The stmt_cache option can be set to hold the anticipated number of distinct dynamic SQL statements in the application.

#### 10.5.59 SYS_INCLUDE

##### Purpose

Specifies the location of system header files.

##### Syntax

SYS_INCLUDE=pathname \| (path1, ..., pathn`)`

##### Default

System-specific.

##### Usage Notes

Pro\*C/C++ searches for standard system header files, such as `stdio.h`, in standard locations that are platform specific. For example, on almost all UNIX systems, the file `stdio.h` has the full path name `/usr/include/stdio.h.`

But C++ compilers can have system header files, such as `stdio.h`, that are not in the standard system locations. You can use the SYS_INCLUDE command line option to specify a list of directory paths that Pro\*C/C++ searches to look for system header files. For example:

    SYS_INCLUDE=(/usr/lang/SC2.0.1/include,/usr/lang/SC2.1.1/include)

The search path that you specify using SYS_INCLUDE overrides the default header location.

If PARSE=NONE, the value specified in SYS_INCLUDE is irrelevant for the precompilation, since there is no need for Pro\*C/C++ to include system header files in the precompilation. (You must, of course, still include Oracle-specific headers, such as `sqlca.h`. and system header files, with \#include directives for pre-processing by the compiler.)

The precompiler searches directories in the following order:

1.  The current directory

2.  The system directory specified in the SYS_INCLUDE precompiler option

3.  The directories specified by the INCLUDE option, in the order entered

4.  The built-in directory for standard header files

Because of step 3, you normally do not need to specify a directory path for standard header files such as `sqlca.h` and `sqlda.h`.

The syntax for specifying a directory path using the SYS_INCLUDE option is system specific. Follow the conventions used for your operating system

**Note:**

For the SYS_INCLUDE option, the precedence of option values gets reversed. Unlike other options in which the values get overwritten, SYS_INCLUDE appends all the directory files that are mentioned in:

- Precompiler

- Pro\*C/C++ system configuration file

- Pro\*C/C++ user configuration file

- Command line

- Inline

However, there is a difference between passing values within or without brackets. If you pass a single value or directory list within brackets, then the existing value of SYS_INCLUDE is overwritten. If you pass the list as a simple value without brackets, it will supplement any existing value.

#### 10.5.60 THREADS

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

**Related Topics**

- [Multithreaded Applications](multithreaded-applications.md)

#### 10.5.61 TYPE_CODE

##### Purpose

This micro option specifies whether ANSI or Oracle datatype codes are used in dynamic SQL Method 4. Its setting is the same as the setting of MODE option.

##### Syntax

TYPE_CODE={ORACLE \| ANSI}

##### Default

ORACLE

##### Usage Notes

Cannot be entered inline.

See the possible option settings in [Table 14-3](ANSI-dynamic-SQL.md).

#### 10.5.62 UNSAFE_NULL

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

#### 10.5.63 USERID

##### Purpose

Specifies an Oracle username and password.

##### Syntax

USERID=username/password\[@dbname\]

##### Default

None

##### Usage Notes

Can be entered only on the command line.

Do not specify this option when using the automatic connect feature, which accepts your Oracle username prefixed with CLUSTER\$. The actual value of the "CLUSTER\$" string is set as a parameter in the INIT.ORA file.

When SQLCHECK=SEMANTICS, if you want the precompiler to get needed information by connecting to Oracle and accessing the data dictionary, you must also specify USERID.

#### 10.5.64 UTF16_CHARSET

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

#### 10.5.65 VARCHAR

##### Purpose

Instructs the Pro\*C/C++ precompiler to interpret some structs as VARCHAR host variables.

##### Syntax

VARCHAR={NO \| YES}

##### Default

NO

##### Usage Notes

Can be entered only on the command line.

When VARCHAR=YES, a C struct that you code as

    struct {
        short len;
        char  arr[n];
    } name;

is interpreted by the precompiler as a VARCHAR\[n\] host variable.

VARCHAR can be used in conjunction with the NLS_CHAR option to designate a multibyte character variable.

#### 10.5.66 VERSION

##### Purpose

Determines which version of the object will be returned by the EXEC SQL OBJECT DEREF statement.

##### Syntax

VERSION={RECENT \| LATEST \| ANY}

##### Default

RECENT

##### Usage Notes

Can be entered inline by use of the EXEC ORACLE OPTION statement.

RECENT means that if the object has been selected into the object cache in the current transaction, then that object is returned. For transactions running in serializable mode, this option has the same effect as LATEST without incurring as many network round trips. Most applications should use RECENT.

LATEST means that if the object does not reside in the object cache, it is retrieved from the database. If It does reside in the object cache, it is refreshed from the server. Use LATEST with caution because it incurs the greatest number of network round trips. Use LATEST only when it is imperative that the object cache is kept as coherent as possible with the server buffer cache

ANY means that if the object already resides in the object cache, return that object. If not, retrieve the object from the server. ANY incurs the fewest network round trips. Use in applications that access read-only objects or when a user will have exclusive access to the objects.
