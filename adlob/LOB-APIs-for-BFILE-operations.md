## 11  LOB APIs for BFILE Operations

APIs for operations that use `BFILE`s are listed in Table 11-1.

This information is given for each operation described:

- Usage Notes provide implementation guidelines such as information specific to a given programmatic environment or data type.

- Syntax refers you to the syntax reference documentation for each supported programmatic environment.

- Examples describe any setup tasks necessary to run the examples given. Demonstration files listed are available in subdirectories under `$ORACLE_HOME/rdbms/demo/lobs/` named `plsql`, `oci`, `vb`, and `java`. The driver program `lobdemo.sql` is in `/plsql` and the driver program` lobdemo.c` is in `/oci`.

  **Note:**

  LOB APIs do not support loading data into `BFILE`s.

  **See Also:**

  [About Using SQL\*Loader to Load LOBs](managing-LOBs.md) for details about techniques to load data into `BFILE`s.

Topics:

- Supported Environments for BFILE APIs

- About Accessing BFILEs

- Directory Objects

- BFILENAME and Initialization

- Characteristics of the BFILE Data Type

- BFILE Security

- About Loading a LOB with BFILE Data

- About Opening a BFILE with OPEN

- About Opening a BFILE with FILEOPEN

- About Determining Whether a BFILE Is Open Using ISOPEN

- About Determining Whether a BFILE Is Open with FILEISOPEN

- About Displaying BFILE Data

- About Reading Data from a BFILE

- About Reading a Portion of BFILE Data Using SUBSTR

- Comparing All or Parts of Two BFILES

- Checking If a Pattern Exists in a BFILE Using INSTR

- Determining Whether a BFILE Exists

- Getting the Length of a BFILE

- About Assigning a BFILE Locator

- Getting Directory Object Name and File Name of a BFILE

- About Updating a BFILE by Initializing a BFILE Locator

- Closing a BFILE with FILECLOSE

- Closing a BFILE with CLOSE

- Closing All Open BFILEs with FILECLOSEALL

- About Inserting a Row Containing a BFILE

<!-- -->

- Supported Environments for BFILE APIs
- About Accessing BFILEs
- Directory Objects
- BFILENAME and Initialization
- Characteristics of the BFILE Data Type
- BFILE Security
- About Loading a LOB with BFILE Data
- About Opening a BFILE with OPEN
- About Opening a BFILE with FILEOPEN
- About Determining Whether a BFILE Is Open Using ISOPEN
- About Determining Whether a BFILE Is Open with FILEISOPEN
- About Displaying BFILE Data
- About Reading Data from a BFILE
- About Reading a Portion of BFILE Data Using SUBSTR
- Comparing All or Parts of Two BFILES
- Checking If a Pattern Exists in a BFILE Using INSTR
  You can determine whether a pattern exists in a `BFILE` using the `INSTR`operation.
- Determining Whether a BFILE Exists
- Getting the Length of a BFILE
- About Assigning a BFILE Locator
- Getting Directory Object Name and File Name of a BFILE
- About Updating a BFILE by Initializing a BFILE Locator
- Closing a BFILE with FILECLOSE
- Closing a BFILE with CLOSE
- Closing All Open BFILEs with FILECLOSEALL
- About Inserting a Row Containing a BFILE

**Parent topic:** [Reference Semantics LOBs](reference-semantics-LOBs.md)

### 11.1 Supported Environments for BFILE APIs

Those programmatic environments that are supported for the APIs are listed in Table 11-1. The first column describes the operation that the API performs. The remaining columns indicate with Yes or No whether the API is supported in PL/SQL, OCI, COBOL, Pro\*C/C++, and JDBC.

Table 11-1 Environments Supported for BFILE APIs

| Operation                                                 | PL/SQL | OCI | COBOL | Pro\*C/C++ | JDBC |
|:----------------------------------------------------------|:-------|:----|:------|:-----------|:-----|
| About Inserting a Row Containing a BFILE                  | Yes    | Yes | Yes   | Yes        | Yes  |
| About Loading a LOB with BFILE Data                       | Yes    | Yes | Yes   | Yes        | Yes  |
| About Opening a BFILE with FILEOPEN                       | Yes    | Yes | No    | No         | Yes  |
| About Opening a BFILE with OPEN                           | Yes    | Yes | Yes   | Yes        | Yes  |
| About Determining Whether a BFILE Is Open Using ISOPEN    | Yes    | Yes | Yes   | Yes        | Yes  |
| About Determining Whether a BFILE Is Open with FILEISOPEN | Yes    | Yes | No    | No         | Yes  |
| About Displaying BFILE Data                               | Yes    | Yes | Yes   | Yes        | Yes  |
| About Reading Data from a BFILE                           | Yes    | Yes | Yes   | Yes        | Yes  |
| About Reading a Portion of BFILE Data Using SUBSTR        | Yes    | No  | Yes   | Yes        | Yes  |
| Comparing All or Parts of Two BFILES                      | Yes    | No  | Yes   | Yes        | Yes  |
| Checking If a Pattern Exists in a BFILE Using INSTR       | Yes    | No  | Yes   | Yes        | Yes  |
| Determining Whether a BFILE Exists                        | Yes    | Yes | Yes   | Yes        | Yes  |
| Getting the Length of a BFILE                             | Yes    | Yes | Yes   | Yes        | Yes  |
| About Assigning a BFILE Locator                           | Yes    | Yes | Yes   | Yes        | Yes  |
| Getting Directory Object Name and File Name of a BFILE    | Yes    | Yes | Yes   | Yes        | Yes  |
| About Updating a BFILE by Initializing a BFILE Locator    | Yes    | Yes | Yes   | Yes        | Yes  |
| Closing a BFILE with FILECLOSE                            | Yes    | Yes | No    | No         | Yes  |
| Closing a BFILE with CLOSE                                | Yes    | Yes | Yes   | Yes        | Yes  |
| Closing All Open BFILEs with FILECLOSEALL                 | Yes    | Yes | Yes   | Yes        | Yes  |

**Parent topic:** LOB APIs for BFILE Operations

### 11.2 About Accessing BFILEs

To access `BFILE`s use one of the following interfaces:

- OCI (Oracle Call Interface)

- PL/SQL (DBMS_LOB package)

- Precompilers, such as Pro\*C/C++ and Pro\*COBOL

- Java (JDBC)

**See Also:**

[Overview of Supplied LOB APIs](overview-of-supplied-LOB-APIs.md) for information about supported environments for accessing `BFILE`s.

**Parent topic:** LOB APIs for BFILE Operations

### 11.3 Directory Objects

The `DIRECTORY` object facilitates administering access and usage of `BFILE` data types.

A `DIRECTORY` object specifies a logical alias name for a physical directory on the database server file system under which the file to be accessed is located. You can access a file in the server file system only if granted the required access privilege on `DIRECTORY` object. You can also use Oracle Enterprise Manager Cloud Control to manage `DIRECTORY` objects.

- Initializing a BFILE Locator
- How to Associate Operating System Files with a BFILE

**See Also:**

- `CREATE` `DIRECTORY` in [Oracle Database SQL Language Reference](../sqlrf/CREATE-DIRECTORY.md)

- See [Oracle Database Administrator's Guide](../admin/distributed-database-concepts.md) for the description of Oracle Enterprise Manager Cloud Control

**Parent topic:** LOB APIs for BFILE Operations

#### 11.3.1 Initializing a BFILE Locator

The `DIRECTORY` object provides the flexibility to manage the locations of the files, instead of forcing you to hard-code the absolute path names of physical files in your applications.

A directory object name is used in conjunction with the `BFILENAME` function, in SQL and PL/SQL, or the `OCILobFileSetName()` in OCI, for initializing a `BFILE` locator.

**WARNING:**

The database does not verify that the directory and path name you specify actually exist. You should take care to specify a valid directory in your operating system. If your operating system uses case-sensitive path names, then be sure you specify the directory in the correct format. There is no requirement to specify a terminating slash (for example, `/tmp/` is not necessary, simply use `/tmp`).

Directory specifications cannot contain ".." anywhere in the path (for example, `/abc/def/hij..`).

**Parent topic:** Directory Objects

#### 11.3.2 How to Associate Operating System Files with a BFILE

To associate an operating system file to a `BFILE`, first create a `DIRECTORY` object which is an alias for the full path name to the operating system file.

To associate existing operating system files with relevant database records of a particular table use Oracle SQL DML (Data Manipulation Language). For example:

- Use `INSERT` to initialize a `BFILE` column to point to an existing file in the server file system.

- Use `UPDATE` to change the reference target of the `BFILE`.

- Initialize a `BFILE` to `NULL` and then update it later to refer to an operating system file using the `BFILENAME` function.

- OCI users can also use `OCILobFileSetName()` to initialize a `BFILE` locator variable that is then used in the `VALUES` clause of an `INSERT` statement.

##### Directory Example

The following statements associate the files `Image1.gif`and`image2.gif`with records having `key_value` of 21 and 22 respectively. '`IMG`' is a `DIRECTORY` object that represents the physical directory under which `Image1.gif` and `image2.gif `are stored.

You may be required to set up data structures similar to the following for certain examples to work:

    CREATE TABLE Lob_table (
       Key_value NUMBER NOT NULL,
       F_lob BFILE)
    INSERT INTO Lob_table VALUES
          (21,  BFILENAME('IMG', 'Image1.gif'));
       INSERT INTO Lob_table VALUES
          (22, BFILENAME('IMG', 'image2.gif'));

The following `UPDATE` statement changes the target file to`image3.gif `for the row with `key_value` of 22.

     UPDATE Lob_table SET f_lob = BFILENAME('IMG', 'image3.gif')
           WHERE Key_value = 22;

**WARNING:**

The database does not expand environment variables specified in the `DIRECTORY` object or file name of a `BFILE` locator. For example, specifying:

    BFILENAME('WORK_DIR', '$MY_FILE')

where `MY_FILE`, an environment variable defined in the operating system, is not valid.

**Parent topic:** Directory Objects

### 11.4 BFILENAME and Initialization

`BFILENAME` is a built-in function that you use to initialize a `BFILE` column to point to an external file.

Once physical files are associated with records using SQL DML, subsequent read operations on the `BFILE` can be performed using PL/SQL `DBMS_LOB` package and OCI. However, these files are read-only when accessed through `BFILE`s, and so they cannot be updated or deleted through `BFILE`s.

As a consequence of the reference-based semantics for `BFILEs`, it is possible to have multiple `BFILE` columns in the same record or different records referring to the same file. For example, the following `UPDATE` statements set the `BFILE` column of the row with`key_value` = 21 in `lob_table`to point to the same file as the row with `key_value` = 22.

    UPDATE lob_table
       SET f_lob = (SELECT f_lob FROM lob_table WHERE key_value = 22)
          WHERE key_value = 21;

Think of `BFILENAME` in terms of initialization — it can initialize the value for the following:

- `BFILE` column

- `BFILE` (automatic) variable declared inside a PL/SQL module

**Parent topic:** LOB APIs for BFILE Operations

### 11.5 Characteristics of the BFILE Data Type

Using the `BFILE` data type has the following advantages:

- If your need for a particular `BFILE` is temporary and limited within the module on which you are working, then you can use the `BFILE` related APIs on the variable without ever having to associate this with a column in the database.

- Because you are not forced to create a `BFILE` column in a server side table, initialize this column value, and then retrieve this column value using a `SELECT`, you save a round-trip to the server.

About Loading a LOB with BFILE Data for examples related to`DBMS_LOB`.`LOADFROMFILE` .

The OCI counterpart for `BFILENAME` is `OCILobFileSetName()`, which can be used in a similar fashion.

- DIRECTORY Name Specification

**Parent topic:** LOB APIs for BFILE Operations

#### 11.5.1 DIRECTORY Name Specification

You must have `CREATE ANY DIRECTORY` system privilege to create directories.

Path names cannot contain two dots (".."). The naming convention for `DIRECTORY` objects is the same as that for tables and indexes. That is, normal identifiers are interpreted in uppercase, but delimited identifiers are interpreted as is. For example, the following statement:

    CREATE OR REPLACE DIRECTORY scott_dir AS '/usr/home/scott';

creates or redefines a `DIRECTORY` object whose name is '`SCOTT_DIR`' (in uppercase). But if a delimited identifier is used for the `DIRECTORY` name, as shown in the following statement

    CREATE DIRECTORY "Mary_Dir" AS '/usr/home/mary';

then the directory object name is '`Mary_Dir`'. Use '`SCOTT_DIR`' and '`Mary_Dir`' when calling `BFILENAME`. For example:

    BFILENAME('SCOTT_DIR', 'afile')
    BFILENAME('Mary_Dir', 'afile')

- On Windows Platforms

**Parent topic:** Characteristics of the BFILE Data Type

##### 11.5.1.1 On Windows Platforms

On Windows platforms the directory names are case-insensitive. Therefore the following two statements refer to the same directory:

    CREATE DIRECTORY "big_cap_dir" AS "g:\data\source";

    CREATE DIRECTORY "small_cap_dir" AS "G:\DATA\SOURCE";

**Parent topic:** DIRECTORY Name Specification

### 11.6 BFILE Security

`BEFILE` security concerns the `BFILE` security model and associated SQL statements. The main SQL statements associated with `BFILE` security are:

- SQL DDL: `CREATE` and `REPLACE` or `ALTER` a `DIRECTORY` object

- SQL DML: `GRANT` and `REVOKE` the `READ` system and object privileges on `DIRECTORY` objects

<!-- -->

- Ownership and Privileges
- Read Permission on a DIRECTORY Object
- SQL DDL for BFILE Security
- SQL DML for BFILE Security
- Catalog Views on Directories
- Guidelines for DIRECTORY Usage
- BFILEs in Shared Server (Multithreaded Server) Mode
- External LOB (BFILE) Locators

**Parent topic:** LOB APIs for BFILE Operations

#### 11.6.1 Ownership and Privileges

The `DIRECTORY` object is a system owned object.

For more information on system owned objects, see [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md). Oracle Database supports two new system privileges, which are granted only to DBA:

- `CREATE` `ANY` `DIRECTORY`: For creating or altering the `DIRECTORY` object creation

- `DROP` `ANY` `DIRECTORY`: For deleting the `DIRECTORY` object

**Parent topic:** BFILE Security

#### 11.6.2 Read Permission on a DIRECTORY Object

`READ` permission on the `DIRECTORY` object enables you to read files located under that directory. The creator of the `DIRECTORY` object automatically earns the `READ` privilege.

If you have been granted the `READ` permission with `GRANT` option, then you may in turn grant this privilege to other users/roles and add them to your privilege domains.

**Note:**

The `READ` permission is defined only on the `DIRECTORY` object, not on individual files. Hence there is no way to assign different privileges to files in the same directory.

The physical directory that it represents may or may not have the corresponding operating system privileges (read in this case) for the Oracle Server process.

It is the responsibility of the DBA to ensure the following:

- That the physical directory exists

- Read permission for the Oracle Server process is enabled on the file, the directory, and the path leading to it

- The directory remains available, and read permission remains enabled, for the entire duration of file access by database users

The privilege just implies that as far as the Oracle Server is concerned, you may read from files in the directory. These privileges are checked and enforced by the PL/SQL `DBMS_LOB` package and OCI APIs at the time of the actual file operations.

**WARNING:**

Because `CREATE` `ANY` `DIRECTORY` and `DROP` `ANY` `DIRECTORY` privileges potentially expose the server file system to all database users, the DBA should be prudent in granting these privileges to normal database users to prevent security breach.

**Parent topic:** BFILE Security

#### 11.6.3 SQL DDL for BFILE Security

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md) for information about the following SQL DDL statements that create, replace, and drop `DIRECTORY` objects:

- `CREATE` `DIRECTORY`

- `DROP` `DIRECTORY`

**Parent topic:** BFILE Security

#### 11.6.4 SQL DML for BFILE Security

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md) for information about the following SQL DML statements that provide security for `BFILE`s:

- `GRANT` (system privilege)

- `GRANT` (object privilege)

- `REVOKE` (system privilege)

- `REVOKE` (object privilege)

- `AUDIT` (new statements)

- `AUDIT` (schema objects)

**Parent topic:** BFILE Security

#### 11.6.5 Catalog Views on Directories

Catalog views are provided for DIRECTORY objects to enable users to view object names and corresponding paths and privileges. Supported views are:

- `ALL_DIRECTORIES` (`OWNER`, `DIRECTORY_NAME`, `DIRECTORY_PATH`)

  This view describes all directories accessible to the user.

- `DBA_DIRECTORIES`(`OWNER`, `DIRECTORY_NAME`, `DIRECTORY_PATH`)

  This view describes all directories specified for the entire database.

**Parent topic:** BFILE Security

#### 11.6.6 Guidelines for DIRECTORY Usage

The main goal of the `DIRECTORY` feature is to enable a simple, flexible, non-intrusive, yet secure mechanism for the DBA to manage access to large files in the server file system. But to realize this goal, it is very important that the DBA follow these guidelines when using `DIRECTORY` objects:

- Do not map a `DIRECTORY` object to a data file directory. A `DIRECTORY` object should not be mapped to physical directories that contain Oracle data files, control files, log files, and other system files. Tampering with these files (accidental or otherwise) could corrupt the database or the server operating system.

- Only the DBA should have system privileges. The system privileges such as `CREATE` `ANY` `DIRECTORY` (granted to the DBA initially) should be used carefully and not granted to other users indiscriminately. In most cases, only the database administrator should have these privileges.

- Use caution when granting the DIRECTORY privilege. Privileges on `DIRECTORY` objects should be granted to different users carefully. The same holds for the use of the `WITH` `GRANT` `OPTION` clause when granting privileges to users.

- Do not drop or replace `DIRECTORY` objects when database is in operation. `DIRECTORY` objects should not be arbitrarily dropped or replaced when the database is in operation. If this were to happen, then operations from all sessions on all files associated with this `DIRECTORY` object fail. Further, if a `DROP` or `REPLACE` command is executed before these files could be successfully closed, then the references to these files are lost in the programs, and system resources associated with these files are not be released until the session(s) is shut down.

  The only recourse left to PL/SQL users, for example, is to either run a program block that calls `DBMS_LOB`.`FILECLOSEALL` and restart their file operations, or exit their sessions altogether. Hence, it is imperative that you use these commands with prudence, and preferably during maintenance downtimes.

- Use caution when revoking a user's privilege on `DIRECTORY` objects. Revoking a user's privilege on a `DIRECTORY` object using the `REVOKE` statement causes all subsequent operations on dependent files from the user's session to fail. Either you must re-acquire the privileges to close the file, or run a `FILECLOSEALL` in the session and restart the file operations.

In general, using `DIRECTORY` objects for managing file access is an extension of system administration work at the operating system level. With some planning, files can be logically organized into suitable directories that have READ privileges for the Oracle process.

`DIRECTORY` objects can be created with `READ` privileges that map to these physical directories, and specific database users granted access to these directories.

**Parent topic:** BFILE Security

#### 11.6.7 BFILEs in Shared Server (Multithreaded Server) Mode

The database does not support session migration for `BFILE` data types in shared server (multithreaded server) mode. This implies that operations on open `BFILE` instances can persist beyond the end of a call to a shared server.

In shared server sessions, `BFILE` operations are bound to one shared server, they cannot migrate from one server to another.

**Parent topic:** BFILE Security

#### 11.6.8 External LOB (BFILE) Locators

For `BFILE`s, the value is stored in a server-side operating system file; in other words, external to the database. The `BFILE` locator that refers to that file is stored in the row.

- When Two Rows in a BFILE Table Refer to the Same File
- BFILE Locator Variable
- Guidelines for BFILEs

**Parent topic:** BFILE Security

##### 11.6.8.1 When Two Rows in a BFILE Table Refer to the Same File

If a `BFILE` locator variable that is used in a `DBMS_LOB`.`FILEOPEN` (for example L1) is assigned to another locator variable, (for example L2), then both L1 and L2 point to the same file.

This means that two rows in a table with a `BFILE` column can refer to the same file or to two distinct files — a fact that the canny developer might turn to advantage, but which could well be a pitfall for the unwary.

**Parent topic:** External LOB (BFILE) Locators

##### 11.6.8.2 BFILE Locator Variable

`A BFILE` locator variable operates like any other automatic variable. With respect to file operations, it operates like a file descriptor available as part of the standard input/output library of most conventional programming languages.

This implies that once you define and initialize a `BFILE` locator, and open the file pointed to by this locator, all subsequent operations until the closure of this file must be done from within the same program block using this locator or local copies of this locator.

**Parent topic:** External LOB (BFILE) Locators

##### 11.6.8.3 Guidelines for BFILEs

Note the following guidelines when working with `BFILE`s:

- Open and close a file from the same program block at same nesting level. The `BFILE` locator variable can be used, just as any scalar, as a parameter to other procedures, member methods, or external function callouts. However, it is recommended that you open and close a file from the same program block at the same nesting level.

- Set the `BFILE` value before flushing the object to the database. If an object contains a `BFILE`, then you must set the `BFILE` value before flushing the object to the database, thereby inserting a new row. In other words, you must call `OCILobFileSetName()` after `OCIObjectNew()` and before `OCIObjectFlush()`.

- Indicate the `DIRECTORY` object name and file name before inserting or updating of a `BFILE`. It is an error to insert or update a `BFILE` without indicating a `DIRECTORY` object name and file name.

  This rule also applies to users using an OCI bind variable for a `BFILE` in an insert or update statement. The OCI bind variable must be initialized with a `DIRECTORY` object name and file name before issuing the insert or update statement.

- Initialize `BFILE` Before insert or update

  **Note:**

  `OCISetAttr()` does not allow the user to set a `BFILE` locator to `NULL`.

- Before using SQL to insert or update a row with a `BFILE`, you must initialize the `BFILE` to one of the following:

  - `NULL` (not possible if using an OCI bind variable)

  - A `DIRECTORY` object name and file name

- A path name cannot contain two dots ("..") anywhere in its specification. A file name cannot start with two dots.

**Parent topic:** External LOB (BFILE) Locators

### 11.7  About Loading a LOB with BFILE Data

You can load a LOB with data from a `BFILE`.

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

[Oracle Database JDBC Developer’s Guide](../jjdbc/introducing-JDBC.md) for details of working with `BFILE` functions in this chapter.

#### Preconditions

The following preconditions must exist before calling this procedure:

- The source `BFILE` instance must exist.

- The destination LOB instance must exist.

#### Usage Notes

**Note:**

The `LOADBLOBFROMFILE` and `LOADCLOBFROMFILE` procedures implement the functionality of this procedure and provide improved features for loading binary data and character data. The improved procedures are available in the PL/SQL environment only. When possible, using one of the improved procedures is recommended.

**See Also:**

- [About Loading a BLOB with Data from a BFILE](using-LOB-APIs.md)

- [Loading a CLOB or NCLOB with Data from a BFILE](using-LOB-APIs.md)

#### Character Set Conversion

In using OCI, or any of the programmatic environments that access OCI functionality, character set conversions are implicitly performed when translating from one character set to another.

#### BFILE to CLOB or NCLOB: Converting From Binary Data to a Character Set

When you use the `DBMS_LOB.LOADFROMFILE` procedure to populate a `CLOB` or `NCLOB`, you are populating the LOB with binary data from the `BFILE`. No implicit translation is performed from binary data to a character set. For this reason, you should use the `LOADCLOBFROMFILE` procedure when loading text.

**See Also:**

- [Loading a CLOB or NCLOB with Data from a BFILE](using-LOB-APIs.md)

- [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md) for character set conversion issues.

#### Amount Parameter

Note the following with respect to the `amount` parameter:

- `DBMS_LOB.LOADFROMFILE`

  If you want to load the entire `BFILE`, then pass the constant `DBMS_LOB.LOBMAXSIZE`. If you pass any other value, then it must be less than or equal to the size of the `BFILE`.

- `OCILobLoadFromFile()`

  If you want to load the entire `BFILE`, then you can pass the constant `UB4MAXVAL`. If you pass any other value, then it must be less than or equal to the size of the `BFILE`.

- `OCILobLoadFromFile2() `

  If you want to load the entire `BFILE`, then you can pass the constant `UB8MAXVAL`. If you pass any other value, then it must be less than or equal to the size of the `BFILE`.

  **See Also:**

  [Table 12-2](using-LOB-APIs.md) for details on the maximum value of the amount parameter.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB" — LOADFROMFILE

- C (OCI): [Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations", for usage notes and examples. Chapter 16, "LOB Functions" — `OCILobLoadFromFile2()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB Statements, and LOB LOAD (executable embedded SQL extension).

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements" "Embedded SQL Statements and Directives"— LOB LOAD.

- Java (JDBC)[ Oracle Database JDBC Developer's Guide)](../jjdbc/LOBs-and-BFiles.md): "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB): `floaddat.sql`

- OCI: `floaddat.c`

- Java (JDBC): No example.

**Parent topic:** LOB APIs for BFILE Operations

### 11.8 About Opening a BFILE with OPEN

You can open a `BFILE` using the OPEN function.

**Note:**

You can also open a `BFILE` using the `FILEOPEN` function; however, using the `OPEN` function is recommended for new development.

**See Also:**

- About Opening a BFILE with FILEOPEN for more information about `FILEOPEN` function

- Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL(DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): "DBMS_LOB" —](../arpls/DBMS_LOB.md) OPEN

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations", for usage notes. Chapter 16, section "LOB Functions" — `OCILobOpen()`, `OCILobClose()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB statements, and LOB OPEN executable embedded SQL extension.

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB OPEN.

- Java (JDBC) [(Oracle Database JDBC Developer's Guide):](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs and BFILEs" — Working with BFILEs.

#### Scenario

These examples open an image in operating system file `ADPHOTO_DIR`.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL(DBMS_LOB): `fopen.sql`

- OCI: `fopen.c`

- Java (JDBC): `fopen.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.9 About Opening a BFILE with FILEOPEN

You can open a `BFILE` using the `FILEOPEN` function.

**Note:**

The `FILEOPEN` function is not recommended for new application development. The `OPEN` function is recommended for new development.

**See Also:**

- About Opening a BFILE with OPEN

- Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Usage Notes for Opening a BFILE

While you can continue to use the older `FILEOPEN` form, Oracle strongly recommends that you switch to using `OPEN`, because this facilitates future extensibility.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB" — FILEOPEN, FILECLOSE

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations, for usage notes. Chapter 16, section "LOB Functions" — `OCILobFileOpen()`, `OCILobFileClose()`, `OCILobFileSetName()`.

- COBOL (Pro\*COBOL): A syntax reference is not applicable in this release.

- C/C++ (Pro\*C/C++): A syntax reference is not applicable in this release.

- Java (JDBC) ([Oracle Database JDBC Developer's Guide](../jjdbc/LOBs-and-BFiles.md)): "Working With LOBs and BFILEs" — Working with BFILEs.

#### Scenario for Opening a BFILE

These examples open `keyboard_logo.jpg` in `DIRECTORY` object `MEDIA_DIR`.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB): `ffilopen.sql`

- OCI: `ffilopen.c`

- Java (JDBC): `ffilopen.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.10 About Determining Whether a BFILE Is Open Using ISOPEN

You can determine whether a `BFILE` is open using `ISOPEN`.

**Note:**

This function (`ISOPEN`) is recommended for new application development. The older `FILEISOPEN` function, is not recommended for new development.

**See Also:**

- About Determining Whether a BFILE Is Open with FILEISOPEN

- Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB"— ISOPEN

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobFileIsOpen()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB statements, and LOB DESCRIBE executable embedded SQL extension.

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB DESCRIBE

- Java (JDBC) [(Oracle Database JDBC Developer's Guide):](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB): `fisopen.sql`

- OCI: `fisopen.c`

- Java (JDBC): `fisopen.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.11 About Determining Whether a BFILE Is Open with FILEISOPEN

You can determine whether a `BFILE` is `OPEN` using the `FILEISOPEN` function.

**Note:**

The `FILEISOPEN` function is not recommended for new application development. The `ISOPEN` function is recommended for new development.

**See Also:**

- About Determining Whether a BFILE Is Open Using ISOPEN

- Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Usage Notes

While you can continue to use the older `FILEISOPEN` form, Oracle strongly recommends that you switch to using `ISOPEN`, because this facilitates future extensibility.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL(DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB" — FILEISOPEN

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobFileIsOpen()`.

- COBOL (Pro\*COBOL): A syntax reference is not applicable in this release.

- C/C++ (Pro\*C/C++): A syntax reference is not applicable in this release.

- Java (JDBC) ([Oracle Database JDBC Developer's Guide](../jjdbc/LOBs-and-BFiles.md)): "Working With LOBs and BFILEs" — Working with BFILEs.

#### Scenario

These examples query whether a `BFILE` associated with `ad_graphic` is open.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL(DBMS_LOB): `ffisopen.sql`

- OCI: `ffisopen.c`

- Java (JDBC): `ffisopen.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.12 About Displaying BFILE Data

You can display `BFILE` data using various operations that differ by programmatic environment..

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB"— READ. Chapter 29, "DBMS_OUTPUT" - PUT_LINE

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobFileOpen()`, `OCILobRead2()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB statements, and LOB READ executable embedded SQL extension.

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements" — READ

- Java (JDBC) ([Oracle Database JDBC Developer's Guide](../jjdbc/LOBs-and-BFiles.md)): Chapter 7, "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

Examples are provided in these programmatic environments:

- PL/SQL (DBMS_LOB): `fdisplay.sql`

- OCI: `fdisplay.c`

- Java (JDBC): `fdisplay.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.13 About Reading Data from a BFILE

You can read data from a `BFILE`.

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Usage Notes

Note the following when using this operation.

#### Streaming Read in OCI

The most efficient way to read large amounts of `BFILE` data is by `OCILobRead2()` with the streaming mechanism enabled, and using polling or callback. To do so, specify the starting point of the read using the `offset` parameter as follows:

    ub8  char_amt =  0;
    ub8  byte_amt =  0;
    ub4  offset = 1000;

    OCILobRead2(svchp, errhp, locp, &byte_amt, &char_amt, offset, bufp, bufl,
                OCI_ONE_PIECE, 0, 0, 0, 0);

When using polling mode, be sure to look at the value of the `byte_amt` parameter after each `OCILobRead2()` call to see how many bytes were read into the buffer, because the buffer may not be entirely full.

When using callbacks, the `lenp` parameter, which is input to the callback, indicates how many bytes are filled in the buffer. Be sure to check the `lenp` parameter during your callback processing because the entire buffer may not be filled with data.

#### Amount Parameter

- When calling `DBMS_LOB.READ`, the amount parameter can be larger than the size of the data; however, the amount parameter should be less than or equal to the size of the buffer. In PL/SQL, the buffer size is limited to 32K.

- When calling `OCILobRead2()`, you can pass a value of 0 (zero) for the `byte_amt` parameter to read to the end of the `BFILE`.

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/lobs-and-bfile-operations.md)

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB" — READ

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobRead2()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB statements, and LOB READ executable embedded SQL extension.

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB READ

- Java (JDBC)[ (Oracle Database JDBC Developer's Guide):](../jjdbc/LOBs-and-BFiles.md) Chapter 7, "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB): `fread.sql`

- OCI: `fread.c`

- Java (JDBC): `fread.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.14 About Reading a Portion of BFILE Data Using SUBSTR

You can read a portion of `BFILE` data using `SUBSTR`.

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB"— SUBSTR

- OCI: A syntax reference is not applicable in this release.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB statements, and LOB CLOSE executable embedded SQL extension.

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB OPEN.

- Java (JDBC)[ (Oracle Database JDBC Developer's Guide)](../jjdbc/LOBs-and-BFiles.md): Chapter 7, "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

Examples are provided in these programmatic environments:

- PL/SQL (DBMS_LOB): `freadprt.sql`

- C (OCI): No example is provided with this release.

- Java (JDBC): `freadprt.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.15 Comparing All or Parts of Two BFILES

You can compare all or parts of two `BFILE`s.

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL(DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB"— COMPARE

- C (OCI): A syntax reference is not applicable in this release.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB statements, and LOB OPEN executable embedded SQL extension.

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB OPEN.

- Java (JDBC) [(Oracle Database JDBC Developer's Guide):](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

Examples are provided in these programmatic environments:

- PL/SQL(DBMS_LOB): `fcompare.sql`

- OCI: No example is provided with this release.

- Java (JDBC): `fcompare.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.16 Checking If a Pattern Exists in a BFILE Using INSTR

You can determine whether a pattern exists in a `BFILE` using the `INSTR`operation.

**See Also:**

Table 11-1for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB" — INSTR

- C (OCI): A syntax reference is not applicable in this release.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB statements, and LOB OPEN executable embedded SQL extension.

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB OPEN.

- Java (JDBC) [(Oracle Database JDBC Developer's Guide):](../jjdbc/LOBs-and-BFiles.md)"Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

These examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB): `fpattern.sql`

- OCI: No example is provided with this release.

- Java (JDBC): `fpattern.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.17 Determining Whether a BFILE Exists

This procedure determines whether a `BFILE` locator points to a valid `BFILE` instance.

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB" — FILEEXISTS

- C (OCI) [Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobFileExists()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB statements, and LOB DESCRIBE executable embedded SQL extension.

- C/C++ (Pro\*C/C++) [Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB DESCRIBE.

- Java (JDBC)[ Oracle Database JDBC Developer's Guide:](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

The examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB): `fexists.sql`

- OCI: `fexists.c`

- Java (JDBC): `fexists.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.18 Getting the Length of a BFILE

You can get the length of a `BFILE`.

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB" — GETLENGTH

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations". Chapter 16, section "LOB Functions" — `OCILobGetLength2()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB statements, and LOB DESCRIBE executable embedded SQL extension.

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB DESCRIBE

- Java (JDBC)[ Oracle Database JDBC Developer's Guide](../jjdbc/LOBs-and-BFiles.md): "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

The examples are provided in these programmatic environments:

- PL/SQL (DBMS_LOB): `flength.sql`

- OCI: `flength.c`

- Java (JDBC): `flength.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.19 About Assigning a BFILE Locator

You can assign one `BFILE` locator to another.

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- SQL [(Oracle Database SQL Language Reference): ](../sqlrf/SQL-Statements-CREATE-SEQUENCE-to-DROP-CLUSTER.md)Chapter 7, "SQL Statements" — CREATE PROCEDURE

- PL/SQL (DBMS_LOB): Refer to [Advanced Design Considerations](advanced-design-considerations.md) of this manual for information on assigning one lob locator to another.

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobLocatorAssign()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/large-objects-LOBs.md)for information on LOBs, usage notes on LOB statements, and LOB ASSIGN executable embedded SQL extension.

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB ASSIGN

- Java (JDBC[) Oracle Database JDBC Developer's Guide:](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

The examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB): `fcopyloc.sql`

- OCI: `fcopyloc.c`

- Java (JDBC): `fcopyloc.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.20 Getting Directory Object Name and File Name of a BFILE

You can get the `DIRECTORY` object name and file name of a `BFILE`.

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB" — FILEGETNAME

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobFileGetName()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB Statements, and LOB DESCRIBE executable embedded SQL extension.

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB DESCRIBE ... GET DIRECTORY ...

- Java (JDBC)[ Oracle Database JDBC Developer's Guide:](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

Examples of this procedure are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB): `fgetdir.sql`

- OCI: `fgetdir.c`

- Java (JDBC): `fgetdir.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.21 About Updating a BFILE by Initializing a BFILE Locator

You can update a `BFILE` by initializing a `BFILE` locator.

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB): See the [(Oracle Database SQL Language Reference), ](../sqlrf/SQL-Statements-MERGE-to-UPDATE.md)Chapter 7, "SQL Statements" — UPDATE

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobFileSetName()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB Statements, and ALLOCATE executable embedded SQL extension. See also [Oracle Database PL/SQL Packages and Types Reference](../arpls/introduction-to-oracle-supplied-plsql-packages-and-types.md) for more information on SQL UPDATE statement

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives"

- Java (JDBC)[ Oracle Database JDBC Developer's Guide:](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

- PL/SQL (DBMS_LOB): `fupdate.sql`

- OCI: `fupdate.c`

- Java (JDBC): `fupdate.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.22 Closing a BFILE with FILECLOSE

You can close a `BFILE` with `FILECLOSE`.

**Note:**

This function (`FILECLOSE`) is not recommended for new development. For new development, use the `CLOSE` function instead.

**See Also:**

Closing a BFILE with CLOSE

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB)[(Oracle Database PL/SQL Packages and Types Reference):](../arpls/DBMS_LOB.md) "DBMS_LOB" — FILEOPEN, FILECLOSE

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobFileClose()`.

- COBOL (Pro\*COBOL): A syntax reference is not applicable in this release.

- C/C++ (Pro\*C/C++): A syntax reference is not applicable in this release.

- Java (JDBC[) Oracle Database JDBC Developer's Guide:](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

- PL/SQL (DBMS_LOB): `fclose_f.sql`

- OCI: `fclose_f.c`

- Java (JDBC): `fclose_f.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.23 Closing a BFILE with CLOSE

You can close a `BFILE` with the `CLOSE` function.

**Note:**

This function (`CLOSE`) is recommended for new application development. The older `FILECLOSE` function, is not recommended for new development.

**See Also:**

Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Usage Notes

Opening and closing a `BFILE` is mandatory. You must close the instance later in the session.

**See Also:**

- About Opening a BFILE with OPEN

- About Determining Whether a BFILE Is Open Using ISOPEN

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB"— CLOSE

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobClose()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB Statements, and LOB CLOSE executable embedded SQL extension

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB CLOSE

- Java (JDBC)[ Oracle Database JDBC Developer's Guide:](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

- PL/SQL (DBMS_LOB): `fclose_c.sql`

- OCI: `fclose_c.c`

- Java (JDBC): `fclose_c.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.24 Closing All Open BFILEs with FILECLOSEALL

You can close all open `BFILE`s.

You are responsible for closing any `BFILE` instances before your program terminates. For example, you must close any open `BFILE` instance before the termination of a PL/SQL block or OCI program.

You must close open BFILE instances even in cases where an exception or unexpected termination of your application occurs. In these cases, if a `BFILE` instance is not closed, then it is still considered open by the database. Ensure that your exception handling strategy does not allow BFILE instances to remain open in these situations.

**See Also:**

- Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

- "[Setting Maximum Number of Open BFILEs](managing-LOBs.md) "

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB) [(Oracle Database PL/SQL Packages and Types Reference): ](../arpls/DBMS_LOB.md)"DBMS_LOB" — FILECLOSEALL

- C (OCI) ([Oracle Call Interface Programmer's Guide)](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations" for usage notes. Chapter 16, section "LOB Functions" — `OCILobFileCloseAll()`.

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB Statements, and LOB FILE CLOSE ALL executable embedded SQL extension

- C/C++ (Pro\*C/C++) ([Pro\*C/C++ Programmer's Guide)](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB FILE CLOSE ALL

- Java (JDBC)[ Oracle Database JDBC Developer's Guide:](../jjdbc/LOBs-and-BFiles.md) Chapter 7, "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

- PL/SQL (DBMS_LOB): `fclosea.sql`

- OCI: `fclosea.c`

- Java (JDBC): `fclosea.java`

**Parent topic:** LOB APIs for BFILE Operations

### 11.25 About Inserting a Row Containing a BFILE

You can insert a row containing a `BFILE` by initializing a `BFILE` locator.

**See Also:**

- Table 11-1, for a list of operations on `BFILE`s and APIs provided for each programmatic environment.

#### Usage Notes

You must initialize the `BFILE` locator bind variable to `NULL` or a `DIRECTORY` object and file name before issuing the `INSERT` statement.

#### Syntax

See the following syntax references for each programmatic environment:

- SQL([Oracle Database SQL Language Reference](../sqlrf/SQL-Statements-DROP-TABLE-to-LOCK-TABLE.md), Chapter 7 "SQL Statements" — INSERT

- C (OCI) [Oracle Call Interface Programmer's Guide](../lnoci/lobs-and-bfile-operations.md): Chapter 7, "LOB and File Operations".

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction.md)for information on LOBs, usage notes on LOB Statements, embedded SQL, and precompiler directives. See also [Oracle Database SQL Language Reference](../sqlrf/SQL-Statements-DROP-TABLE-to-LOCK-TABLE.md), for related information on the SQL INSERT statement.

- C/C++ (Pro\*C/C++) [Pro\*C/C++ Programmer's Guide](../lnpcc/about-Objects.md): "Large Objects (LOBs)", "LOB Statements", "Embedded SQL Statements and Directives" — LOB FILE SET. See also ([Oracle Database SQL Language Reference](../sqlrf/SQL-Statements-DROP-TABLE-to-LOCK-TABLE.md)), Chapter 7 "SQL Statements" — INSERT

- Java (JDBC) [Oracle Database JDBC Developer's Guide](../jjdbc/LOBs-and-BFiles.md): "Working With LOBs and BFILEs" — Working with BFILEs.

#### Examples

- PL/SQL (DBMS_LOB): `finsert.sql`

- OCI: `finsert.c`

- Java (JDBC): `finsert.java`

**Parent topic:** LOB APIs for BFILE Operations
