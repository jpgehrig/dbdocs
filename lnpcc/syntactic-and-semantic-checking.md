By checking the syntax and semantics of embedded SQL statements and PL/SQL blocks, the Pro\*C/C++ Precompiler helps you quickly find and fix coding mistakes. This appendix shows you how to use the SQLCHECK option to control the type and extent of checking. This appendix contains the following topics:

- What Is Syntactic and Semantic Checking?

  About Controlling the Type and Extent of Checking

- About Specifying SQLCHECK=SEMANTICS

- About Specifying SQLCHECK=SYNTAX

- About Entering the SQLCHECK Option

### C.1 What Is Syntactic and Semantic Checking?

Rules of syntax specify how language elements are sequenced to form valid statements. Thus, syntactic checking verifies that keywords, object names, operators, delimiters, and so on are placed correctly in your SQL statement. For example, the following embedded SQL statements contain syntax errors:

    EXEC SQL DELETE FROM EMP WHER DEPTNO = 20;
        -- misspelled keyword WHERE
    EXEC SQL INSERT INTO EMP COMM, SAL VALUES (NULL, 1500);
        -- missing parentheses around column names COMM and SAL

Rules of semantics specify how valid external references are made. Thus, semantic checking verifies that references to database objects and host variables are valid and that host variable datatypes are correct. For example, the following embedded SQL statements contain semantic errors:

    EXEC SQL DELETE FROM empp WHERE deptno = 20;
        -- nonexistent table, EMPP
    EXEC SQL SELECT * FROM emp WHERE ename = :emp_name;
        -- undeclared host variable, emp_name

The rules of SQL syntax and semantics are defined in[ Oracle Database SQL Language Reference](../sqlrf/index.md).

### C.2 About Controlling the Type and Extent of Checking

You control the type and extent of checking by specifying the SQLCHECK option on the command line. With SQLCHECK, the type of checking can be syntactic, semantic, or both. The extent of checking can include the following:

- Data definition statements (such as CREATE and GRANT)

- Data manipulation statements (such as SELECT and INSERT)

- PL/SQL blocks

However, SQLCHECK cannot check dynamic SQL statements because they are not fully defined until run time.

You can specify the following values for SQLCHECK:

- SEMANTICS or FULL

- SYNTAX

The default value is SYNTAX.

The use of SQLCHECK does not affect the normal syntax checking done on data control, cursor control, and dynamic SQL statements.

### C.3 About Specifying SQLCHECK=SEMANTICS

When SQLCHECK=SEMANTICS, the precompiler checks the syntax and semantics of

- Data manipulation statements (INSERT, UPDATE, and so on)

- PL/SQL blocks

- Host variable datatypes

as well as the syntax of

- Data definition statements (CREATE, ALTER, and so on)

However, only syntactic checking is done on data manipulation statements that use the AT db_name clause.

When SQLCHECK=SEMANTICS, the precompiler gets information needed for a semantic check by using embedded DECLARE TABLE statements or if you specify the USERID option on the command line, by connecting to the Oracle server and accessing the data dictionary. You need not connect to the Oracle server if every table referenced in a data manipulation statement or PL/SQL block is defined in a DECLARE TABLE statement.

If you connect to the Oracle server, but some needed information cannot be found in the data dictionary, you must use DECLARE TABLE statements to supply the missing information. A DECLARE TABLE definition overrides a data dictionary definition if they conflict.

If you embed PL/SQL blocks in a host program, you must specify SQLCHECK=SEMANTICS.

When checking data manipulation statements, the precompiler uses the syntax rules found in the[ Oracle Database SQL Language Reference,](../sqlrf/index.md) but uses a stricter set of semantic rules. In particular, stricter datatype checking is done. As a result, existing applications written for earlier versions of Oracle might not precompile successfully when SQLCHECK=SEMANTICS.

Specify SQLCHECK=SEMANTICS when you precompile new programs or want stricter datatype checking.

#### C.3.1 About Enabling a Semantic Check

When SQLCHECK=SEMANTICS, the precompiler can get information needed for a semantic check in either of the following ways:

- Connect to the Oracle server and access the data dictionary.

- Use embedded DECLARE TABLE and DECLARE TYPE statements.

##### C.3.1.1 About Connecting to the Oracle server

To do a semantic check, the precompiler can connect to an Oracle database that maintains definitions of tables, types, and views referenced in your host program.

After connecting to the Oracle server, the precompiler accesses the data dictionary for needed information. The data dictionary stores table and column names, table and column constraints, column lengths, column datatypes, and so on.

If some of the needed information cannot be found in the data dictionary (because your program refers to a table not yet created, for example), you must supply the missing information using the DECLARE TABLE statement (discussed later in this appendix).

To connect to the Oracle server, specify the USERID option on the command line, using the syntax:

    USERID=username/password

where username and password comprise a valid Oracle userid. If you omit the password, you are prompted for it.

If, instead of a username and password, you specify

    USERID=/

the precompiler attempts to automatically connect to the Oracle server. The attempt succeeds only if an existing Oracle username matches your operating system ID prefixed with "CLUSTER\$", or whatever value the parameter OS_AUTHENT_PREFIX is set to in the INIT.ORA file. For example, if your operating system ID is MBLAKE, an automatic connect only succeeds if CLUSTER\$MBLAKE is a valid Oracle username.

If you omit the USERID option, the precompiler must get needed information from embedded DECLARE TABLE statements.

If you try connecting to the Oracle server but cannot (because the database is unavailable, for example), an error message is issued and your program is not precompiled.

##### C.3.1.2 About Using DECLARE TABLE

The precompiler can do a semantic check without connecting to the Oracle server. To do the check, the precompiler must get information about tables and views from embedded DECLARE TABLE statements. Thus, every table referenced in a data manipulation statement or PL/SQL block must be defined in a DECLARE TABLE statement.

The syntax of the DECLARE TABLE statement is:

    EXEC SQL DECLARE table_name TABLE
        (col_name col_datatype [DEFAULT expr] [NULL|NOT NULL], ...);

where expr is an integer that can be used as a default column value in the CREATE TABLE statement.

For user-defined object datatypes, the size is optional because it is not used.

If you use DECLARE TABLE to define a database table that already exists, the precompiler uses your definition, ignoring the one in the data dictionary.

##### C.3.1.3 About Using DECLARE TYPE

Similarly, for TYPE, there is a DECLARE TYPE statement whose syntax is:

    EXEC SQL DECLARE type TYPE
    [AS OBJECT (col_name col_datatype, ...)] |
    [AS VARRAY(size) OF element_type ]|
    [AS TABLE OF object_type ] ;

This allows for better type-checking for user-defined types when SQLCHECK=SEMANTICS at precompile-time. When SQLCHECK=SYNTAX, the DECLARE TYPE statements serve as documentation only and are commented out and ignored.

### C.4 About Specifying SQLCHECK=SYNTAX

When SQLCHECK=SYNTAX, the precompiler checks the syntax of SQL statements documented in[ Oracle Database SQL Language Reference](../sqlrf/index.md):

- Data manipulation statements

- Host-variable expressions

No semantic check is done, and the following restrictions apply:

- No connection to the Oracle server is attempted and USERID becomes an invalid option. If you specify USERID, a warning message is issued.

- DECLARE TABLE and DECLARE TYPE statements are ignored; they serve only as documentation.

- PL/SQL blocks are not allowed. If the precompiler finds a PL/SQL block, an error message is issued.

When checking data manipulation statements, the precompiler uses Oracle syntax rules. These rules are downwardly compatible, so specify SQLCHECK=SYNTAX when migrating your precompiled programs.

### C.5 About Entering the SQLCHECK Option

You can enter the SQLCHECK option inline or on the command line. However, the level of checking you specify inline cannot be higher than the level you specify (or accept by default) on the command line. For example, if you specify SQLCHECK=SYNTAX on the command line, you cannot specify SQLCHECK=SEMANTICS inline.
