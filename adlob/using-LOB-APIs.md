## 12  Using LOB APIs

APIs that perform operations on `BLOB`, `CLOB`, and `NCLOB` data types appear in Table 12-1. These operations can be used with either persistent or temporary LOB instances. Note that these do not apply to `BFILE`s.

**See Also:**

- [Operations Specific to Persistent and Temporary LOBs](operations-specific-to-persistent-and-temporary-LOBs.md) for information on how to create temporary and persistent LOB instances and other operations specific to temporary or persistent LOBs.

- [LOB APIs for BFILE Operations](LOB-APIs-for-BFILE-operations.md) for information on operations specific to `BFILE` instances.

This information is given for each of these operations:

- Preconditions describe dependencies that must be met and conditions that must exist before calling each operation.

- Usage Notes provide implementation guidelines such as information specific to a given programmatic environment or data type.

- Syntax refers you to the syntax reference documentation for each supported programmatic environment.

- Examples describe any setup tasks necessary to run the examples given. Demonstration files listed are available in subdirectories under `$ORACLE_HOME/rdbms/demo/lobs/` named `plsql`, `oci`, `vb`, and `java`. The driver program `lobdemo.sql` is in `/plsql` and the driver program `lobdemo.c` is in `/oci`.

Topics:

- Supported Environments

- About Appending One LOB to Another

- About Determining Character Set Form

- About Determining Character Set ID

- Loading a LOB with Data from a BFILE

- About Loading a BLOB with Data from a BFILE

- Loading a CLOB or NCLOB with Data from a BFILE

- Determining Whether a LOB is Open

- About Displaying LOB Data

- About Reading Data from a LOB

- About LOB Array Read

- Reading a Portion of a LOB (SUBSTR)

- Comparing All or Part of Two LOBs

- Patterns: Checking for Patterns in a LOB Using INSTR

- Length: Determining the Length of a LOB

- Copying All or Part of One LOB to Another LOB

- Copying a LOB Locator

- Equality: Checking If One LOB Locator Is Equal to Another

- About Determining Whether LOB Locator Is Initialized

- About Appending to a LOB

- About Writing Data to a LOB

- LOB Array Write

- About Trimming LOB Data

- About Erasing Part of a LOB

- Determining Whether a LOB instance Is Temporary

- Converting a BLOB to a CLOB

- Converting a CLOB to a BLOB

- Ensuring Read Consistency

<!-- -->

- Supported Environments
- About Appending One LOB to Another
- About Determining Character Set Form
- About Determining Character Set ID
- Loading a LOB with Data from a BFILE
- About Loading a BLOB with Data from a BFILE
- Loading a CLOB or NCLOB with Data from a BFILE
- Determining Whether a LOB is Open
- About Displaying LOB Data
- About Reading Data from a LOB
- About LOB Array Read
- Reading a Portion of a LOB (SUBSTR)
- Comparing All or Part of Two LOBs
- Patterns: Checking for Patterns in a LOB Using INSTR
- Length: Determining the Length of a LOB
- Copying All or Part of One LOB to Another LOB
- Copying a LOB Locator
- Equality: Checking If One LOB Locator Is Equal to Another
- About Determining Whether LOB Locator Is Initialized
- About Appending to a LOB
- About Writing Data to a LOB
- LOB Array Write
- About Trimming LOB Data
- About Erasing Part of a LOB
- Determining Whether a LOB instance Is Temporary
- Converting a BLOB to a CLOB
  You can convert a `BLOB` instance to a `CLOB` using the PL/SQL procedure `DBMS_LOB.CONVERTTOCLOB`.
- Converting a CLOB to a BLOB
- Ensuring Read Consistency

**Parent topic:** [Reference Semantics LOBs](reference-semantics-LOBs.md)

### 12.1 Supported Environments

Table 12-1 indicates which programmatic environments are supported for the APIs discussed in this chapter. The first column describes the operation that the API performs. The remaining columns indicate with Yes or No whether the API is supported in PL/SQL, OCI, OCCI, COBOL, Pro\*C/C++, and JDBC.

Table 12-1 Environments Supported for LOB APIs

| Operation                                                                                                     | PL/SQL | OCI | OCCI | COBOL | Pro\*C/C++ | JDBC |
|:--------------------------------------------------------------------------------------------------------------|:-------|:----|:-----|:------|:-----------|:-----|
| About Appending One LOB to Another                                                                            | Yes    | Yes | No   | Yes   | Yes        | Yes  |
| About Determining Character Set Form                                                                          | No     | Yes | No   | No    | No         | No   |
| About Determining Character Set ID                                                                            | No     | Yes | No   | No    | No         | No   |
| Determining Chunk Size, See: About Writing Data to a LOB                                                      | Yes    | Yes | Yes  | Yes   | Yes        | Yes  |
| Comparing All or Part of Two LOBs                                                                             | Yes    | No  | No   | Yes   | Yes        | Yes  |
| Converting a BLOB to a CLOB                                                                                   | Yes    | No  | No   | No    | No         | No   |
| Converting a CLOB to a BLOB                                                                                   | Yes    | No  | No   | No    | No         | No   |
| Copying a LOB Locator                                                                                         | Yes    | Yes | No   | Yes   | Yes        | Yes  |
| Copying All or Part of One LOB to Another LOB                                                                 | Yes    | Yes | No   | Yes   | Yes        | Yes  |
| About Displaying LOB Data                                                                                     | Yes    | Yes | No   | Yes   | Yes        | Yes  |
| Equality: Checking If One LOB Locator Is Equal to Another                                                     | No     | Yes | No   | No    | Yes        | Yes  |
| About Erasing Part of a LOB                                                                                   | Yes    | Yes | No   | Yes   | Yes        | Yes  |
| About Determining Whether LOB Locator Is Initialized                                                          | No     | Yes | No   | No    | Yes        | No   |
| Length: Determining the Length of a LOB                                                                       | Yes    | Yes | No   | Yes   | Yes        | Yes  |
| Loading a LOB with Data from a BFILE                                                                          | Yes    | Yes | No   | Yes   | Yes        | Yes  |
| About Loading a BLOB with Data from a BFILE                                                                   | Yes    | No  | No   | No    | No         | No   |
| Loading a CLOB or NCLOB with Data from a BFILE                                                                | Yes    | No  | No   | No    | No         | No   |
| About LOB Array Read                                                                                          | No     | Yes | No   | No    | No         | No   |
| LOB Array Write                                                                                               | No     | Yes | No   | No    | No         | No   |
| [Opening Persistent LOBs with the OPEN and CLOSE Interfaces](advanced-design-considerations.md)               | Yes    | Yes | Yes  | Yes   | Yes        | Yes  |
| Open: Determining Whether a LOB is Open                                                                       | Yes    | Yes | Yes  | Yes   | Yes        | Yes  |
| Patterns: Checking for Patterns in a LOB Using INSTR                                                          | Yes    | No  | No   | Yes   | Yes        | Yes  |
| Reading a Portion of a LOB (SUBSTR)                                                                           | Yes    | No  | No   | Yes   | Yes        | Yes  |
| About Reading Data from a LOB                                                                                 | Yes    | Yes | No   | Yes   | Yes        | Yes  |
| Storage Limit, Determining: [Maximum Storage Limit for Terabyte-Size LOBs](advanced-design-considerations.md) | Yes    | No  | No   | No    | No         | No   |
| About Trimming LOB Data                                                                                       | Yes    | Yes | No   | Yes   | Yes        | Yes  |
| WriteNoAppend, see About Appending to a LOB .                                                                 | No     | No  | No   | No    | No         | No   |
| About Writing Data to a LOB                                                                                   | Yes    | Yes | Yes  | Yes   | Yes        | Yes  |

**Parent topic:** Using LOB APIs

### 12.2 About Appending One LOB to Another

This operation appends one LOB instance to another.

#### Preconditions

Before you can append one LOB to another, the following conditions must be met:

- Two LOB instances must exist.

- Both instances must be of the same type, for example both `BLOB` or both `CLOB` types.

- You can pass any combination of persistent or temporary LOB instances to this operation.

#### Usage Notes

Persistent LOBs: You must lock the row you are selecting the LOB from prior to updating a LOB value if you are using the PL/SQL `DBMS_LOB` Package or OCI. While the SQL `INSERT` and `UPDATE` statements implicitly lock the row, locking the row can be done explicitly using the SQL `SELECT` `FOR` `UPDATE` statement in SQL and PL/SQL programs, or by using an OCI `pin` or `lock` function in OCI programs.

#### Syntax

See the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — APPEND

- C (OCI): [Oracle Call Interface Programmer's Guide](../lnoci/more-database-access-c-api.md) "LOB Functions" — OCILobAppend()

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB Statements, and LOB APPEND executable embedded SQL extension

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)for information on embedded SQL statements and directives — LOB APPEND

- Java (JDBC):[Oracle Database JDBC Developer’s Guide](../jjdbc/overview-of-JDBC.md)for information on creating and populating LOB columns in Java.

#### Examples

To run the following examples, you must create two LOB instances and pass them when you call the given append operation.

Examples for this use case are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lappend.sql`

- OCI: `lappend.c`

- Java (JDBC): `lappend.java`

**See Also:**

- [Example of Updating LOBs Through Updated Locators](advanced-design-considerations.md) for more details on the state of the locator after an update

- [Operations Specific to Persistent and Temporary LOBs](operations-specific-to-persistent-and-temporary-LOBs.md) for more information about Creating a LOB instance

**Parent topic:** Using LOB APIs

### 12.3 About Determining Character Set Form

This section describes how to get the character set form of a LOB instance.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): There is no applicable syntax reference for this operation.

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — OCILobCharSetForm()

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL): There is no applicable syntax reference for this operation

- C/C++ (Pro\*C/C++): There is no applicable syntax reference for this operation.

- Java (JDBC): There is no applicable syntax reference for this operation.

#### Example

The example demonstrates how to determine the character set form of the foreign language text (`ad_fltextn`).

This functionality is currently available only in OCI:

- OCI: ` lgetchfm.c`

**Parent topic:** Using LOB APIs

### 12.4 About Determining Character Set ID

This section describes how to determine the character set ID.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package):There is no applicable syntax reference for this operation.

- C (OCI): [Oracle Call Interface Programmer's Guide](../lnoci/more-database-access-c-api.md) "Relational Functions" — LOB Functions, OCILobCharSetId()

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL): There is no applicable syntax reference for this operation.

- C/C++ (Pro\*C/C++): There is no applicable syntax reference for this operation

- Java (JDBC): There is no applicable syntax reference for this operation.

#### Example

This functionality is currently available only in OCI:

- OCI: `lgetchar.c`

**Parent topic:** Using LOB APIs

### 12.5 Loading a LOB with Data from a BFILE

This operation loads a LOB with data from a `BFILE`. This procedure can be used to load data into any persistent or temporary LOB instance of any LOB data type.

#### Preconditions

Before you can load a LOB with data from a `BFILE`, the following conditions must be met:

- The `BFILE` must exist.

- The target LOB instance must exist.

#### Usage Notes

Note the following issues regarding this operation.

#### Use LOADCLOBFROMFILE When Loading Character Data

When you use the `DBMS_LOB.LOADFROMFILE` procedure to load a `CLOB` or `NCLOB` instance, you are loading the LOB with binary data from the `BFILE` and no implicit character set conversion is performed. For this reason, using the `DBMS_LOB.LOADCLOBFROMFILE` procedure is recommended when loading character data.

#### Specifying Amount of BFILE Data to Load

The value you pass for the amount parameter to functions listed in Table 12-2 must be one of the following:

- An amount less than or equal to the actual size (in bytes) of the `BFILE` you are loading.

- The maximum allowable LOB size (in bytes). Passing this value, loads the entire `BFILE`. You can use this technique to load the entire `BFILE` without determining the size of the `BFILE` before loading. To get the maximum allowable LOB size, use the technique described in Table 12-2.

Table 12-2 Maximum LOB Size for Load from File Operations

| Environment | Function                                                         | To pass maximum LOB size, get value of: |
|:------------|:-----------------------------------------------------------------|:----------------------------------------|
| `DBMS_LOB`  | `DBMS_LOB.LOADBLOBFROMFILE`                                      | `DBMS_LOB.LOBMAXSIZE`                   |
| `DBMS_LOB`  | `DBMS_LOB.LOADCLOBFROMFILE`                                      | `DBMS_LOB.LOBMAXSIZE`                   |
| `OCI`       | `OCILobLoadFromFile2()`                                          | `UB8MAXVAL`                             |
| `OCI`       | `OCILobLoadFromFile()` (For LOBs less than 4 gigabytes in size.) | `UB4MAXVAL`                             |

#### Syntax

See the following syntax references for details on using this operation in each programmatic environment:

- PL/SQL (DBMS_LOB Package):[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)"DBMS_LOB" — LOADFROMFILE.

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — OCILobLoadFromFile()

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB statements, and `LOB LOAD`, `LOB OPEN`, and `LOB CLOSE` executable embedded SQL extension

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md), for more information on `LOB LOAD` executable embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide ](../jjdbc/LOBs-and-BFiles.md)Chapter 7, "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lloaddat.sql`

- OCI: `lloaddat.c`

- Java (JDBC):` lloaddat.java`

**See Also:**

- The `LOADBLOBFROMFILE` and `LOADCLOBFROMFILE` procedures implement the functionality of this procedure and provide improved features for loading binary data and character data. (These improved procedures are available in the PL/SQL environment only.) When possible, using one of the improved procedures is recommended. See "About Loading a BLOB with Data from a BFILE" and "Loading a CLOB or NCLOB with Data from a BFILE" for more information.

- As an alternative to this operation, you can use SQL\*Loader to load persistent LOBs with data directly from a file in the file system. See "[About Using SQL\*Loader to Load LOBs](managing-LOBs.md)" for more information.

- Loading a CLOB or NCLOB with Data from a BFILE for more information about `DBMS_LOB.LOADCLOBFROMFILE` procedure

**Parent topic:** Using LOB APIs

### 12.6 About Loading a BLOB with Data from a BFILE

This procedure loads a `BLOB` with data from a `BFILE`. This procedure can be used to load data into any persistent or temporary `BLOB` instance.

**See Also:**

- "Loading a LOB with Data from a BFILE"

- To load character data, use `DBMS_LOB.LOADCLOBFROMFILE`. See "Loading a CLOB or NCLOB with Data from a BFILE" for more information.

- As an alternative to this operation, you can use SQL\*Loader to load persistent LOBs with data directly from a file in the file system. See "[About Using SQL\*Loader to Load LOBs](managing-LOBs.md)" for more information.

#### Preconditions

The following conditions must be met before calling this procedure:

- The target `BLOB` instance must exist.

- The source `BFILE` must exist.

- You must open the `BFILE`. (After calling this procedure, you must close the `BFILE` at some point.)

#### Usage Notes

Note the following with respect to this operation:

#### New Offsets Returned

Using `DBMS_LOB.LOADBLOBFROMFILE` to load binary data into a `BLOB` achieves the same result as using `DBMS_LOB.LOADFROMFILE`, but also returns the new offsets of BLOB.

#### Specifying Amount of BFILE Data to Load

The value you pass for the amount parameter to the `DBMS_LOB.LOADBLOBFROMFILE` function must be one of the following:

- An amount less than or equal to the actual size (in bytes) of the `BFILE` you are loading.

- The maximum allowable LOB size:` DBMS_LOB.LOBMAXSIZE``. `Passing this value causes the function to load the entire `BFILE`. This is a useful technique for loading the entire `BFILE` without introspecting the size of the `BFILE`.

  **See Also:**

  Table 12-2

#### Syntax

See [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md),"DBMS_LOB" — LOADBLOBFROMFILE procedure for syntax details on this procedure.

#### Examples

This example is available in PL/SQL only. This API is not provided in other programmatic environments. The online file is `lldblobf.sql`. This example illustrates:

- How to use `LOADBLOBFROMFILE` to load the entire `BFILE` without getting its length first.

- How to use the return value of the offsets to calculate the actual amount loaded.

**Parent topic:** Using LOB APIs

### 12.7 Loading a CLOB or NCLOB with Data from a BFILE

This procedure loads a `CLOB` or `NCLOB` with character data from a `BFILE`. This procedure can be used to load data into a persistent or temporary `CLOB` or `NCLOB` instance.

**See Also:**

- "Loading a LOB with Data from a BFILE"

- To load binary data, use `DBMS_LOB.LOADBLOBFROMFILE`. See "About Loading a BLOB with Data from a BFILE" for more information.

- As an alternative to this operation, you can use SQL\*Loader to load persistent LOBs with data directly from a file in the file system. See "[About Using SQL\*Loader to Load LOBs](managing-LOBs.md)" for more information.

#### Preconditions

The following conditions must be met before calling this procedure:

- The target `CLOB` or `NCLOB` instance must exist.

- The source `BFILE` must exist.

- You must open the `BFILE`. (After calling this procedure, you must close the `BFILE` at some point.)

#### Usage Notes

You can specify the character set id of the `BFILE` when calling this procedure. Doing so, ensures that the character set is properly converted from the `BFILE` data character set to the destination `CLOB` or `NCLOB` character set.

#### Specifying Amount of BFILE Data to Load

The value you pass for the amount parameter to the `DBMS_LOB.LOADCLOBFROMFILE` function must be one of the following:

- An amount less than or equal to the actual size (in characters) of the `BFILE` data you are loading.

- The maximum allowable LOB size: `DBMS_LOB.LOBMAXSIZE`

  Passing this value causes the function to load the entire `BFILE`. This is a useful technique for loading the entire `BFILE` without introspecting the size of the `BFILE`.

#### Syntax

See [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md),"DBMS_LOB" — `LOADCLOBFROMFILE` procedure for syntax details on this procedure.

#### Examples

The following examples illustrate different techniques for using this API:

- "About PL/SQL: Loading Character Data from a BFILE into a LOB"

- "About PL/SQL: Loading Segments of Character Data into Different LOBs"

<!-- -->

- About PL/SQL: Loading Character Data from a BFILE into a LOB
- About PL/SQL: Loading Segments of Character Data into Different LOBs

**Parent topic:** Using LOB APIs

#### 12.7.1 About PL/SQL: Loading Character Data from a BFILE into a LOB

The following example illustrates:

- How to use default csid (`0`).

- How to load the entire file without calling `getlength` for the `BFILE`.

- How to find out the actual amount loaded using return offsets.

This example assumes that `ad_source` is a `BFILE` in `UTF8` character set format and the database character set is `UTF8`. The online file is `lldclobf.sql`.

**Parent topic:** Loading a CLOB or NCLOB with Data from a BFILE

#### 12.7.2 About PL/SQL: Loading Segments of Character Data into Different LOBs

The following example illustrates:

- How to get the character set ID from the character set name using the `NLS_CHARSET_ID` function.

- How to load a stream of data from a single `BFILE` into different LOBs using the returned offset value and the language context `lang_ctx`.

- How to read a warning message.

This example assumes that `ad_file_ext_01` is a `BFILE` in `JA16TSTSET` format and the database national character set is `AL16UTF16`. The online file is `lldclobs.sql`.

**Parent topic:** Loading a CLOB or NCLOB with Data from a BFILE

### 12.8 Determining Whether a LOB is Open

This operation determines whether a LOB is open.

#### Preconditions

The LOB instance must exist before executing this procedure.

#### Usage Notes

When a LOB is open, it must be closed at some point later in the session.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — `OPEN`, `ISOPEN`.

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — `OCILobIsOpen()`.

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/embedded-SQL-statements-and-precompiler-directives.md)for information on LOBs, usage notes on LOB Statements, and LOB DESCRIBE executable embedded SQL extension.

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)`LOB DESCRIBE` executable embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide,](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lisopen.sql`

- OCI: `lisopen.c`

- C++ (OCCI): No example is provided with this release.

- Java (JDBC): `lisopen.java`

<!-- -->

- Java (JDBC): Checking If a LOB Is Open

**Parent topic:** Using LOB APIs

#### 12.8.1 Java (JDBC): Checking If a LOB Is Open

Here is how to check a `BLOB` or a `CLOB`.

- Checking If a CLOB Is Open
- Checking If a BLOB Is Open

**Parent topic:** Determining Whether a LOB is Open

##### 12.8.1.1 Checking If a CLOB Is Open

To see if a `CLOB` is open, your JDBC application can use the `isOpen` method defined in `oracle.sql.CLOB`. The return Boolean value indicates whether the `CLOB` has been previously opened or not. The `isOpen` method is defined as follows:

    /**
      * Check whether the CLOB is opened.
      * @return true if the LOB is opened.
      */
    public boolean isOpen () throws SQLException

The usage example is:

    CLOB clob = ...
     // See if the CLOB is opened
     boolean isOpen = clob.isOpen ();
    ...

**Parent topic:** Java (JDBC): Checking If a LOB Is Open

##### 12.8.1.2 Checking If a BLOB Is Open

To see if a `BLOB` is open, your JDBC application can use the `isOpen` method defined in `oracle.sql.BLOB`. The return Boolean value indicates whether the `BLOB` has been previously opened or not. The `isOpen` method is defined as follows:

    /**
     * Check whether the BLOB is opened.
     * @return true if the LOB is opened.
     */
     public boolean isOpen () throws SQLException

The usage example is:

    BLOB blob = ...
    // See if the BLOB is opened
    boolean isOpen = blob.isOpen ();
    ...

**Parent topic:** Java (JDBC): Checking If a LOB Is Open

### 12.9 About Displaying LOB Data

This section describes APIs that allow you to read LOB data. You can use this operation to read LOB data into a buffer. This is useful if your application requires displaying large amounts of LOB data or streaming data operations.

#### Usage Notes

Note the following when using these APIs.

#### Streaming Mechanism

The most efficient way to read large amounts of LOB data is to use `OCILobRead2`() with the streaming mechanism enabled.

#### Amount Parameter

The value you pass for the amount parameter is restricted for the APIs described in Table 12-3.

Table 12-3 Maximum LOB Size for Amount Parameter

| Environment | Function                                                    | Value of amount parameter is limited to:                     |
|:------------|:------------------------------------------------------------|:-------------------------------------------------------------|
| DBMS_LOB    | `DBMS_LOB.READ`                                             | The size of the buffer, 32Kbytes.                            |
| OCI         | `OCILobRead()`<br>(For LOBs less than 4 gigabytes in size.) | `UB4MAXVAL`<br>Specifying this amount reads the entire file. |
| OCI         | `OCILobRead2()`<br>(For LOBs of any size.)                  | `UB8MAXVAL`<br>Specifying this amount reads the entire file. |

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — OPEN, READ, CLOSE.

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" —, OCILobOpen(), OCILobRead2(), OCILobClose().

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB statements, and LOB READ executable embedded SQL extension.

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)for information on LOB READ executable embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide, ](../jjdbc/LOBs-and-BFiles.md)"Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `ldisplay.sql`

- OCI: `ldisplay.c`

- C++ (OCCI): No example is provided in this release.

- Java (JDBC): `ldisplay.java`

**Parent topic:** Using LOB APIs

### 12.10 About Reading Data from a LOB

This section describes how to read data from LOBs using `OCILobRead2()`.

#### Usage Notes

Note the following when using this operation.

#### Streaming Read in OCI

The most efficient way to read large amounts of LOB data is to use `OCILobRead2()` with the streaming mechanism enabled using polling or callback. To do so, specify the starting point of the read using the `offset` parameter as follows:

    ub8  char_amt =  0;
    ub8  byte_amt =  0;
    ub4  offset = 1000;

    OCILobRead2(svchp, errhp, locp, &byte_amt, &char_amt, offset, bufp, bufl,
                OCI_ONE_PIECE, 0, 0, 0, 0);

When using polling mode, be sure to look at the value of the `byte_amt` parameter after each `OCILobRead2()` call to see how many bytes were read into the buffer because the buffer may not be entirely full.

When using callbacks, the `lenp` parameter, which is input to the callback, indicates how many bytes are filled in the buffer. Be sure to check the `lenp` parameter during your callback processing because the entire buffer may not be filled with data.

**See Also:**

[ Oracle Call Interface Programmer's Guide](../lnoci/lobs-and-bfile-operations.md)

#### Chunk Size

A chunk is one or more Oracle blocks. You can specify the chunk size for the BasicFiles LOB when creating the table that contains the LOB. This corresponds to the data size used by Oracle Database when accessing or modifying the LOB value. Part of the chunk is used to store system-related information and the rest stores the LOB value. The API you are using has a function that returns the amount of space used in the LOB chunk to store the LOB value. In PL/SQL use `DBMS_LOB.GETCHUNKSIZE`. In OCI, use `OCILobGetChunkSize()`. For SecureFiles, `CHUNK` is an advisory size and is provided for backward compatibility purposes.

To improve performance, you may run `write` requests using a multiple of the value returned by one of these functions. The reason for this is that you are using the same unit that the Oracle database uses when reading data from disk. If it is appropriate for your application, then you should batch reads until you have enough for an entire chunk instead of issuing several LOB read calls that operate on the same LOB chunk.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — `OPEN`, `GETCHUNKSIZE`, `READ`, `CLOSE`

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — `OCILobOpen()`, `OCILobRead2()`, `OCILobClose()`.

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB statements, and LOB READ executable embedded SQL extension

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)for information about LOB READ executable embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide ](../jjdbc/LOBs-and-BFiles.md)Chapter 7, "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lread.sql`

- OCI: `lread.c`

- Java (JDBC): `lread.java`

**Parent topic:** Using LOB APIs

### 12.11 About LOB Array Read

This section describes how to read LOB data for multiple locators in one round trip, using `OCILobArrayRead()`.

#### Usage Notes

This function improves performance in reading LOBs in the size range less than about 512 Kilobytes. For an OCI application example, assume that the program has a prepared SQL statement such as:

    SELECT lob1 FROM lob_table for UPDATE;

where `lob1` is the LOB column and `lob_array` is an array of define variables corresponding to a LOB column:

    OCILobLocator * lob_array[10];

    ...
     for (i=0; i<10, i++)        /* initialize array of locators */
        lob_array[i] = OCIDescriptorAlloc(..., OCI_DTYPE_LOB, ...);

    ...

    OCIDefineByPos(..., 1, (dvoid *) lob_array, ... SQLT_CLOB, ...);

    /* Execute the statement with iters = 10 to do an array fetch of 10 locators. */
    OCIStmtExecute ( <service context>, <statement handle>, <error handle>,
                     10,    /* iters  */
                     0,     /* row offset */
                     NULL,  /* snapshot IN */
                     NULL,  /* snapshot out */
                     OCI_DEFAULT /* mode */);
    ...

      ub4 array_iter = 10;
      char  *bufp[10];
      oraub8 bufl[10];
      oraub8 char_amtp[10];
      oraub8 offset[10];

     for (i=0; i<10; i++)
      {
        bufp[i] = (char *)malloc(1000);
        bufl[i] = 1000;
        offset[i] = 1;
        char_amtp[i] = 1000;  /* Single byte fixed width char set. */
      }

    /* Read the 1st 1000 characters for all 10 locators in one
     * round trip. Note that offset and amount need not be
     * same for all the locators. */

    OCILobArrayRead(<service context>, <error handle>,
                    &array_iter, /* array size */
                    lob_array,   /* array of locators */
                    NULL,        /* array of byte amounts */
                    char_amtp,   /* array of char amounts */
                    offset,      /* array of offsets */
           (void **)bufp,        /* array of read buffers */
                    bufl,        /* array of buffer lengths */
                    OCI_ONE_PIECE,  /* piece information */
                    NULL,           /* callback context */
                    NULL,           /* callback function */
                    0,              /* character set ID - default */
                    SQLCS_IMPLICIT);/* character set form */

     ...

    for (i=0; i<10; i++)
      {
        /* Fill bufp[i] buffers with data to be written */
        strncpy (bufp[i], "Test Data------", 15);
        bufl[i] = 1000;
        offset[i] = 50;
        char_amtp[i] = 15;  /* Single byte fixed width char set. */
      }

    /* Write the 15 characters from offset 50 to all 10
     * locators in one round trip. Note that offset and
     * amount need not be same for all the locators. */
     */

    OCILobArrayWrite(<service context>, <error handle>,
                      &array_iter, /* array size */
                      lob_array,   /* array of locators */
                      NULL,        /* array of byte amounts */
                      char_amtp,   /* array of char amounts */
                      offset,      /* array of offsets */
                 (void **)bufp,    /* array of read buffers */
                      bufl,        /* array of buffer lengths */
                      OCI_ONE_PIECE,  /* piece information */
                      NULL,           /* callback context */
                      NULL,           /* callback function */
                      0,              /* character set ID - default */
                      SQLCS_IMPLICIT);/* character set form */
    ...

#### Streaming Support

LOB array APIs can be used to read/write LOB data in multiple pieces. This can be done by using polling method or a callback function.Here data is read/written in multiple pieces sequentially for the array of locators. For polling, the API would return to the application after reading/writing each piece with the `array_iter` parameter (OUT) indicating the index of the locator for which data is read/written. With a callback, the function is called after reading/writing each piece with `array_iter` as IN parameter.

Note that:

- It is possible to read/write data for a few of the locators in one piece and read/write data for other locators in multiple pieces. Data is read/written in one piece for locators which have sufficient buffer lengths to accommodate the whole data to be read/written.

- Your application can use different amount value and buffer lengths for each locator.

- Your application can pass zero as the amount value for one or more locators indicating pure streaming for those locators. In the case of reading, LOB data is read to the end for those locators. For writing, data is written until `OCI_LAST_PIECE` is specified for those locators.

#### LOB Array Read in Polling Mode

The following example reads 10Kbytes of data for each of 10 locators with 1Kbyte buffer size. Each locator needs 10 pieces to read the complete data. `OCILobArrayRead()` must be called 100 (10\*10) times to fetch all the data.First we call `OCILobArrayRead()` with `OCI_FIRST_PIECE` as `piece` parameter. This call returns the first 1K piece for the first locator.Next `OCILobArrayRead()` is called in a loop until the application finishes reading all the pieces for the locators and returns `OCI_SUCCESS`. In this example it loops 99 times returning the pieces for the locators sequentially.

    /* Fetch the locators */
    ...

         /* array_iter parameter indicates the number of locators in the array read.
          * It is an IN parameter for the 1st call in polling and is ignored as IN
          * parameter for subsequent calls. As OUT parameter it indicates the locator
          * index for which the piece is read.
          */

         ub4    array_iter = 10;
         char  *bufp[10];
         oraub8 bufl[10];
         oraub8 char_amtp[10];
         oraub8 offset[10];
         sword  st;

         for (i=0; i<10; i++)
         {
           bufp[i] = (char *)malloc(1000);
           bufl[i] = 1000;
           offset[i] = 1;
           char_amtp[i] = 10000;       /* Single byte fixed width char set. */
         }

         st =  OCILobArrayRead(<service context>, <error handle>,
                             &array_iter, /* array size */
                             lob_array, /* array of locators */
                             NULL,      /* array of byte amounts */
                             char_amtp, /* array of char amounts */
                             offset,    /* array of offsets */
                    (void **)bufp,      /* array of read buffers */
                             bufl,      /* array of buffer lengths */
                             OCI_FIRST_PIECE, /* piece information */
                             NULL,           /* callback context */
                             NULL,           /* callback function */
                             0,              /* character set ID - default */
                             SQLCS_IMPLICIT); /* character set form */

         /* First piece for the first locator is read here.
          * bufp[0]          => Buffer pointer into which data is read.
          * char_amtp[0 ]    => Number of characters read in current buffer
          *
          */

         While ( st == OCI_NEED_DATA)
         {
              st =  OCILobArrayRead(<service context>, <error handle>,
                              &array_iter, /* array size */
                              lob_array, /* array of locators */
                              NULL,      /* array of byte amounts */
                              char_amtp, /* array of char amounts */
                              offset,    /* array of offsets */
                     (void **)bufp,      /* array of read buffers */
                              bufl,      /* array of buffer lengths */
                              OCI_NEXT_PIECE, /* piece information */
                              NULL,           /* callback context */
                              NULL,           /* callback function */
                              0,              /* character set ID - default */
                              SQLCS_IMPLICIT);

           /* array_iter returns the index of the current array element for which
            * data is read. for example, aray_iter = 1 implies first locator,
            * array_iter = 2 implies second locator and so on.
            *
            * lob_array[ array_iter - 1]=> Lob locator for which data is read.
            * bufp[array_iter - 1]      => Buffer pointer into which data is read.
            * char_amtp[array_iter - 1] => Number of characters read in current buffer
            */

    ...
            /* Consume the data here */
    ...
         }

#### LOB Array Read with Callback

The following example reads 10Kbytes of data for each of 10 locators with 1Kbyte buffer size. Each locator needs 10 pieces to read all the data. The callback function is called 100 (10\*10) times to return the pieces sequentially.

    /* Fetch the locators */
    ...
         ub4    array_iter = 10;
         char  *bufp[10];
         oraub8 bufl[10];
         oraub8 char_amtp[10];
         oraub8 offset[10];
         sword  st;

         for (i=0; i<10; i++)
         {
           bufp[i] = (char *)malloc(1000);
           bufl[i] = 1000;
           offset[i] = 1;
           char_amtp[i] = 10000;       /* Single byte fixed width char set. */
          }

          st =  OCILobArrayRead(<service context>, <error handle>,
                            &array_iter, /* array size */
                            lob_array,   /* array of locators */
                            NULL,        /* array of byte amounts */
                            char_amtp,   /* array of char amounts */
                            offset,      /* array of offsets */
                   (void **)bufp,        /* array of read buffers */
                            bufl,        /* array of buffer lengths */
                            OCI_FIRST_PIECE,  /* piece information */
                            ctx,              /* callback context */
                            cbk_read_lob,     /* callback function */
                            0,                /* character set ID - default */
                            SQLCS_IMPLICIT);
    ...
    /* Callback function for LOB array read. */
    sb4 cbk_read_lob(dvoid *ctxp, ub4 array_iter, CONST dvoid *bufxp, oraub8 len,
                     ub1 piece, dvoid **changed_bufpp, oraub8 *changed_lenp)
    {
       static ub4 piece_count = 0;
       piece_count++;
       switch (piece)
       {
        case OCI_LAST_PIECE:
          /*--- buffer processing code goes here ---*/
    (void) printf("callback read the %d th piece(last piece) for %dth locator \n\n",
                    piece_count, array_iter );
          piece_count = 0;
          break;
        case OCI_FIRST_PIECE:
          /*--- buffer processing code goes here ---*/
          (void) printf("callback read the 1st piece for %dth locator\n",
                        array_iter);
        /* --Optional code to set changed_bufpp and changed_lenp if the buffer needs
             to be changed dynamically --*/
          break;
        case OCI_NEXT_PIECE:
          /*--- buffer processing code goes here ---*/
          (void) printf("callback read the %d th piece for %dth locator\n",
                        piece_count, array_iter);
          /* --Optional code to set changed_bufpp and changed_lenp if the  buffer
               must be changed dynamically --*/
          break;
          default:
          (void) printf("callback read error: unkown piece = %d.\n", piece);
          return OCI_ERROR;
       }
        return OCI_CONTINUE;
    }
    ...

#### Polling LOB Array Read

The next example is polling LOB data in `OCILobArrayRead()` with variable `amtp`, `bufl`, and `offset`.

    /* Fetch the locators */
    ...

         ub4    array_iter = 10;
         char  *bufp[10];
         oraub8 bufl[10];
         oraub8 char_amtp[10];
         oraub8 offset[10];
         sword  st;

         for (i=0; i<10; i++)
         {
           bufp[i] = (char *)malloc(1000);
           bufl[i] = 1000;
           offset[i] = 1;
           char_amtp[i] = 10000;       /* Single byte fixed width char set. */
         }

         /* For 3rd locator read data in 500 bytes piece from offset 101. Amount
          * is 2000, that is, total number of pieces is 2000/500 = 4.
          */
         offset[2] = 101; bufl[2] = 500; char_amtp[2] = 2000;

         /* For 6th locator read data in 100 bytes piece from offset 51. Amount
          * is 0 indicating pure polling, that is, data is read till the end of
          * the LOB is reached.
          */
         offset[5] = 51;  bufl[5] = 100; char_amtp[5] = 0;

         /* For 8th locator read 100 bytes of data in one piece. Note amount
          * is less than buffer length indicating single piece read.
          */
         offset[7] = 61;  bufl[7] = 200; char_amtp[7] = 100;

         st =  OCILobArrayRead(<service context>, <error handle>,
                             &array_iter, /* array size */
                             lob_array, /* array of locators */
                             NULL,      /* array of byte amounts */
                             char_amtp, /* array of char amounts */
                             offset,    /* array of offsets */
                    (void **)bufp,      /* array of read buffers */
                             bufl,      /* array of buffer lengths */
                             OCI_FIRST_PIECE, /* piece information */
                             NULL,           /* callback context */
                             NULL,           /* callback function */
                             0,              /* character set ID - default */
                             SQLCS_IMPLICIT); /* character set form */

         /* First piece for the first locator is read here.
          * bufp[0]          => Buffer pointer into which data is read.
          * char_amtp[0 ]    => Number of characters read in current buffer
          *
          */

         while ( st == OCI_NEED_DATA)
         {
              st =  OCILobArrayRead(<service context>, <error handle>,
                              &array_iter, /* array size */
                              lob_array, /* array of locators */
                              NULL,      /* array of byte amounts */
                              char_amtp, /* array of char amounts */
                              offset,    /* array of offsets */
                     (void **)bufp,      /* array of read buffers */
                              bufl,      /* array of buffer lengths */
                              OCI_NEXT_PIECE, /* piece information */
                              NULL,           /* callback context */
                              NULL,           /* callback function */
                              0,              /* character set ID - default */
                              SQLCS_IMPLICIT);

           /* array_iter returns the index of the current array element for which
            * data is read. for example, aray_iter = 1 implies first locator,
            * array_iter = 2 implies second locator and so on.
            *
            * lob_array[ array_iter - 1]=> Lob locator for which data is read.
            * bufp[array_iter - 1]      => Buffer pointer into which data is read.
            * char_amtp[array_iter - 1]=>Number of characters read in current buffer
            */

    ...
            /* Consume the data here */
    ...
         }

#### Syntax

Use the following syntax references for the OCI programmatic environment:

C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — `OCILobArrayRead()`.

#### Example

An example is provided in the following programmatic environment:

OCI: lreadarr.c

**Parent topic:** Using LOB APIs

### 12.12 Reading a Portion of a LOB (SUBSTR)

This section describes how to read a portion of a LOB using SUBSTR.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — SUBSTR, OPEN, CLOSE

- C (OCI): There is no applicable syntax reference for this use case

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md) for information on LOBs, usage notes on LOB Statements, and ALLOCATE, LOB OPEN, LOB READ, LOB CLOSE executable embedded SQL extensions

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)LOB READ executable embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide,](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lsubstr.sql`

- OCI: No example is provided with this release.

- C++ (OCCI): No example is provided with this release.

- Java (JDBC): `lsubstr.java`

**Parent topic:** Using LOB APIs

### 12.13 Comparing All or Part of Two LOBs

This section describes how to compare all or part of two LOBs.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — COMPARE.

- C (OCI): There is no applicable syntax reference for this use case.

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)or information on LOBs, usage notes on LOB Statements, and EXECUTE executed embedded SQL

  C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)for more information on EXECUTE executed embedded SQL

- Java (JDBC):[ Oracle Database JDBC Developer's Guide,](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lcompare.sql`

- C (OCI): No example is provided with this release.

- C++ (OCCI): No example is provided with this release.

- Java (JDBC): `lcompare.java`

**Parent topic:** Using LOB APIs

### 12.14 Patterns: Checking for Patterns in a LOB Using INSTR

This section describes how to see if a pattern exists in a LOB using `INSTR`.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — INSTR

- C (OCI): There is no applicable syntax reference for this use case.

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB Statements, and EXECUTE executed embedded SQL

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)for more information on EXECUTE executed embedded SQL

- Java (JDBC):[ Oracle Database JDBC Developer's Guide ](../jjdbc/LOBs-and-BFiles.md)Chapter 7, "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `linstr.sql`

- C (OCI): No example is provided with this release.

- C++ (OCCI): No example is provided with this release.

- Java (JDBC): `linstr.java`

**Parent topic:** Using LOB APIs

### 12.15 Length: Determining the Length of a LOB

This section describes how to determine the length of a LOB.

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — GETLENGTH

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — `OCILobGetLength2()`

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/embedded-SQL-statements-and-precompiler-directives.md)for information on LOBs, usage notes on LOB Statements, and LOB DESCRIBE executable embedded SQL extension

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)for more information on LOB DESCRIBE executable embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide,](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package) `llength.sql`

- OCI: `llength.c`

- C++ (OCCI): No example is provided with this release.

- Java (JDBC): `llength.java`

**Parent topic:** Using LOB APIs

### 12.16 Copying All or Part of One LOB to Another LOB

This section describes how to copy all or part of a LOB to another LOB. These APIs copy an amount of data you specify from a source LOB to a destination LOB.

#### Usage Notes

Note the following issues when using this API.

#### Specifying Amount of Data to Copy

The value you pass for the `amount` parameter to the `DBMS_LOB.COPY` function must be one of the following:

- An amount less than or equal to the actual size of the data you are loading.

- The maximum allowable LOB size: `DBMS_LOB.LOBMAXSIZE``.`Passing this value causes the function to read the entire LOB. This is a useful technique for reading the entire LOB without introspecting the size of the LOB.

Note that for character data, the amount is specified in characters, while for binary data, the amount is specified in bytes.

#### Locking the Row Prior to Updating

If you plan to update a LOB value, then you must lock the row containing the LOB prior to updating. While the SQL `INSERT` and `UPDATE` statements implicitly lock the row, locking is done explicitly by means of a SQL `SELECT` `FOR` `UPDATE` statement in SQL and PL/SQL programs, or by using an `OCI` `pin` or `lock` function in OCI programs.

**See Also:**

[Example of Updating LOBs Through Updated Locators](advanced-design-considerations.md) for more details on the state of the locator after an update

#### Syntax

See the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — COPY

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — OCILobCopy2

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/embedded-SQL-statements-and-precompiler-directives.md)for information on LOBs, usage notes on LOB Statements, and LOB COPY executable embedded SQL extension

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)for information on LOB COPY executable embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide,](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lcopy.sql`

- OCI: `lcopy.c`

- Java (JDBC): `lcopy.java`

**Parent topic:** Using LOB APIs

### 12.17 Copying a LOB Locator

This section describes how to copy a LOB locator. Note that different locators may point to the same or different data, or to current or outdated data.

**See Also:**

[Read-Consistent Locators](advanced-design-considerations.md) for more details about how to assign one LOB to another using PL/SQL using the `:=` operator

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): Refer to "[Read-Consistent Locators](advanced-design-considerations.md)" for information on assigning one lob locator to another

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — ` OCILobAssign()`, `OCILobIsEqual()`

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/embedded-SQL-statements-and-precompiler-directives.md)for information on LOBs, usage notes on LOB Statements, and ALLOCATE and LOB ASSIGN executable embedded SQL extensions

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)SELECT, LOB ASSIGN executable embedded SQL extensions

- Java (JDBC):[ Oracle Database JDBC Developer's Guide ](../jjdbc/LOBs-and-BFiles.md)Chapter 7, "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lcopyloc.sql`

- OCI: `lcopyloc.c`

- C++ (OCCI): No example is provided with this release.

- Java (JDBC): `lcopyloc.java`

**Parent topic:** Using LOB APIs

### 12.18 Equality: Checking If One LOB Locator Is Equal to Another

This section describes how to determine whether one LOB locator is equal to another. If two locators are equal, then this means that they refer to the same version of the LOB data.

**See Also:**

- Environments Supported for LOB APIs

- "[Read-Consistent Locators](advanced-design-considerations.md)"

#### Syntax

Use the following syntax references for each programmatic environment:

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — `OCILobAssign()`, `OCILobIsEqual()`

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL): There is no applicable syntax reference for this use case.

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)LOB ASSIGN executable embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide,](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL: No example is provided with this release.

- OCI: `lequal.c`

- C++ (OCCI): No example is provided with this release.

- Java (JDBC): `lequal.java`

**Parent topic:** Using LOB APIs

### 12.19 About Determining Whether LOB Locator Is Initialized

This section describes how to determine whether a LOB locator is initialized.

**See Also:**

Table 12-1

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): There is no applicable syntax reference for this use case.

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — `OCILobLocatorIsInit()`

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL): There is no applicable syntax reference for this use case.

- C/C++ (Pro\*C/C++)[Pro\*C/C++ Programmer's Guide](../lnpcc/introduction.md)

- Java (JDBC): There is no applicable syntax reference for this use case.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): No example is provided with this release.

- OCI: `linit.c`

- C (OCCI)): No example is provided with this release.

- Java (JDBC): No example is provided with this release.

**Parent topic:** Using LOB APIs

### 12.20 About Appending to a LOB

This section describes how to write-append the contents of a buffer to a LOB.

**See Also:**

Table 12-1

#### Usage Notes

Note the following issues regarding usage of this API.

#### Writing Singly or Piecewise

The `writeappend` operation writes a buffer to the end of a LOB.

For OCI, the buffer can be written to the LOB in a single piece with this call; alternatively, it can be rendered piecewise using callbacks or a standard polling method.

#### Writing Piecewise: When to Use Callbacks or Polling

If the value of the piece parameter is `OCI_FIRST_PIECE`, then data must be provided through callbacks or polling.

- If a callback function is defined in the `cbfp` parameter, then this callback function is called to get the next piece after a piece is written to the pipe. Each piece is written from `bufp`.

- If no callback function is defined, then `OCILobWriteAppend2`() returns the `OCI_NEED_DATA` error code. The application must call `OCILobWriteAppend2`() again to write more pieces of the LOB. In this mode, the buffer pointer and the length can be different in each call if the pieces are of different sizes and from different locations. A piece value of `OCI_LAST_PIECE` terminates the piecewise write.

#### Locking the Row Prior to Updating

Prior to updating a LOB value using the PL/SQL `DBMS_LOB` package or the OCI, you must lock the row containing the LOB. While the SQL `INSERT` and `UPDATE` statements implicitly lock the row, locking is done explicitly by means of an SQL `SELECT` `FOR` `UPDATE` statement in SQL and PL/SQL programs, or by using an `OCI` `pin` or `lock` function in OCI programs.

**See Also:**

[Example of Updating LOBs Through Updated Locators](advanced-design-considerations.md) for more details on the state of the locator after an update

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — `WRITEAPPEND`

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — `OCILobWriteAppend2`()

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB statements

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)for more information on Embedded SQL Statements and Directives

- Java (JDBC):[ Oracle Database JDBC Developer's Guide ](../jjdbc/LOBs-and-BFiles.md)Chapter 7, "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lwriteap.sql`

- OCI: `lwriteap.c`

- C++ (OCCI): No example is provided with this release.

- Java (JDBC): `lwriteap.java`

**Parent topic:** Using LOB APIs

### 12.21 About Writing Data to a LOB

This section describes how to write the contents of a buffer to a LOB.

**See Also:**

- Table 12-1

- About Reading Data from a LOB

#### Usage Notes

Note the following issues regarding usage of this API.

#### Stream Write

The most efficient way to write large amounts of LOB data is to use `OCILobWrite2`() with the streaming mechanism enabled, and using polling or a callback. If you know how much data is written to the LOB, then specify that amount when calling `OCILobWrite2()`. This ensures that LOB data on the disk is contiguous. Apart from being spatially efficient, the contiguous structure of the LOB data makes reads and writes in subsequent operations faster.

#### Chunk Size

A chunk is one or more Oracle blocks. You can specify the chunk size for the LOB when creating the table that contains the LOB. This corresponds to the data size used by Oracle Database when accessing or modifying the LOB value. Part of the chunk is used to store system-related information and the rest stores the LOB value. The API you are using has a function that returns the amount of space used in the LOB chunk to store the LOB value. In PL/SQL use `DBMS_LOB.GETCHUNKSIZE`. In OCI, use `OCILobGetChunkSize()`.

#### Use a Multiple of the Returned Value to Improve Write Performance

To improve performance, run write requests using a multiple of the value returned by one of these functions. The reason for this is that the LOB chunk is versioned for every `write` operation. If all `writes` are done on a chunk basis, then no extra or excess versioning is incurred or duplicated. If it is appropriate for your application, then you should batch writes until you have enough for an entire chunk instead of issuing several LOB write calls that operate on the same LOB chunk.

#### Locking the Row Prior to Updating

Prior to updating a LOB value using the PL/SQL `DBMS_LOB` Package or OCI, you must lock the row containing the LOB. While the SQL `INSERT` and `UPDATE` statements implicitly lock the row, locking is done explicitly by means of a SQL `SELECT` `FOR` `UPDATE` statement in SQL and PL/SQL programs, or by using an `OCI` `pin` or `lock` function in OCI programs.

**See Also:**

[Example of Updating LOBs Through Updated Locators](advanced-design-considerations.md) for more details on the state of the locator after an update

#### Using DBMS_LOB.WRITE to Write Data to a BLOB

When you are passing a hexadecimal string to DBMS_LOB.WRITE() to write data to a BLOB, use the following guidelines:

- The `amount` parameter should be \<= the buffer `length` parameter

- The `length` of the buffer should be ((`amount`\*2) - 1). This guideline exists because the two characters of the string are seen as one hexadecimal character (and an implicit hexadecimal-to-raw conversion takes place), that is, every two bytes of the string are converted to one raw byte.

The following example is correct:

    declare
       blob_loc  BLOB;
       rawbuf RAW(10);
       an_offset INTEGER := 1;
       an_amount BINARY_INTEGER := 10;
    BEGIN
       select blob_col into blob_loc from a_table
    where id = 1;
       rawbuf := '1234567890123456789';
       dbms_lob.write(blob_loc, an_amount, an_offset,
    rawbuf);
       commit;
    END;

Replacing the value for `an_amount` in the previous example with the following values, yields error message, ora_21560:

        an_amount BINARY_INTEGER := 11;

or

        an_amount BINARY_INTEGER := 19;

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB"— WRITE

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — OCILobWrite2().

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB statements, and LOB WRITE executable embedded SQL extension

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)LOB WRITE executable embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide ](../jjdbc/LOBs-and-BFiles.md)Chapter 7, "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lwrite.sql`

- OCI: `lwrite.c`

- Java (JDBC): `lwrite.java`

**Parent topic:** Using LOB APIs

### 12.22 LOB Array Write

This section describes how to write LOB data for multiple locators in one round trip, using `OCILobArrayWrite()`.

#### Usage Notes

**See Also:**

"About LOB Array Read" for examples of array read/write.

#### LOB Array Write in Polling Mode

The following example writes 10Kbytes of data for each of `10` locators with a 1K buffer size. `OCILobArrayWrite()` has to be called `100` (`10` times `10`) times to write all the data. The function is used in a similar manner to `OCILobWrite2()`.

    /* Fetch the locators */
    ...

    /* array_iter parameter indicates the number of locators in the array read.
     * It is an IN parameter for the 1st call in polling and is ignored as IN
     * parameter for subsequent calls. As an OUT parameter it indicates the locator
     * index for which the piece is written.
     */

    ub4    array_iter = 10;
    char  *bufp[10];
    oraub8 bufl[10];
    oraub8 char_amtp[10];
    oraub8 offset[10];
    sword  st;
    int    i, j;

    for (i=0; i<10; i++)
    {
      bufp[i] = (char *)malloc(1000);
      bufl[i] = 1000;
      /* Fill bufp here. */
    ...
      offset[i] = 1;
      char_amtp[i] = 10000;       /* Single byte fixed width char set. */
    }

    for (i  = 1; i <= 10; i++)
    {
     /* Fill up bufp[i-1] here.  The first piece for ith locator would be written from
        bufp[i-1] */
    ...
        st =  OCILobArrayWrite(<service context>, <error handle>,
                          &array_iter, /* array size */
                          lob_array,   /* array of locators */
                          NULL,        /* array of byte amounts */
                          char_amtp,   /* array of char amounts */
                          offset,      /* array of offsets */
                 (void **)bufp,        /* array of write buffers */
                          bufl,        /* array of buffer lengths */
                          OCI_FIRST_PIECE, /* piece information */
                          NULL,            /* callback context */
                          NULL,            /* callback function */
                          0,               /* character set ID - default */
                          SQLCS_IMPLICIT); /* character set form */

     for ( j = 2; j < 10; j++)
     {
     /* Fill up bufp[i-1] here.  The jth piece for ith locator would be written from
        bufp[i-1] */
    ...
     st =  OCILobArrayWrite(<service context>, <error handle>,
                            &array_iter, /* array size */
                            lob_array,   /* array of locators */
                            NULL,        /* array of byte amounts */
                            char_amtp,   /* array of char amounts */
                            offset,      /* array of offsets */
                   (void **)bufp,        /* array of write buffers */
                            bufl,        /* array of buffer lengths */
                            OCI_NEXT_PIECE, /* piece information */
                            NULL,           /* callback context */
                            NULL,           /* callback function */
                            0,              /* character set ID - default */
                            SQLCS_IMPLICIT);

        /* array_iter returns the index of the current array element for which
         * data is being written. for example, aray_iter = 1 implies first locator,
         * array_iter = 2 implies second locator and so on. Here i = array_iter.
         *
         * lob_array[ array_iter - 1] => Lob locator for which data is written.
         * bufp[array_iter - 1]       => Buffer pointer from which data is written.
         * char_amtp[ array_iter - 1] => Number of characters written in
         * the piece just written
         */
    }

    /* Fill up bufp[i-1] here.  The last piece for ith locator would be written from
       bufp[i -1] */
    ...
     st =  OCILobArrayWrite(<service context>, <error handle>,
                            &array_iter, /* array size */
                            lob_array,   /* array of locators */
                            NULL,        /* array of byte amounts */
                            char_amtp,   /* array of char amounts */
                            offset,      /* array of offsets */
                   (void **)bufp,        /* array of write buffers */
                            bufl,        /* array of buffer lengths */
                            OCI_LAST_PIECE,  /* piece information */
                            NULL,            /* callback context */
                            NULL,            /* callback function */
                            0,               /* character set ID - default */
                            SQLCS_IMPLICIT);
    }

    ...

#### LOB Array Write with Callback

The following example writes 10Kbytes of data for each of 10 locators with a 1K buffer size. A total of 100 pieces must be written (10 pieces for each locator). The first piece is provided by the `OCILobArrayWrite()` call. The callback function is called 99 times to get the data for subsequent pieces to be written.

    /* Fetch the locators */
    ...

        ub4    array_iter = 10;
        char  *bufp[10];
        oraub8 bufl[10];
        oraub8 char_amtp[10];
        oraub8 offset[10];
        sword  st;

        for (i=0; i<10; i++)
        {
          bufp[i] = (char *)malloc(1000);
          bufl[i] = 1000;
          offset[i] = 1;
          char_amtp[i] = 10000;       /* Single byte fixed width char set. */
        }

     st =  OCILobArrayWrite(<service context>, <error handle>,
                            &array_iter, /* array size */
                            lob_array,   /* array of locators */
                            NULL,        /* array of byte amounts */
                            char_amtp,   /* array of char amounts */
                            offset,      /* array of offsets */
                   (void **)bufp,        /* array of write buffers */
                            bufl,        /* array of buffer lengths */
                            OCI_FIRST_PIECE,  /* piece information */
                            ctx,              /* callback context */
                            cbk_write_lob     /* callback function */
                            0,                /* character set ID - default */
                            SQLCS_IMPLICIT);

    ...

    /* Callback function for LOB array write. */
    sb4 cbk_write_lob(dvoid *ctxp, ub4 array_iter, dvoid *bufxp, oraub8 *lenp,
                      ub1 *piecep, ub1 *changed_bufpp, oraub8 *changed_lenp)
    {
     static ub4 piece_count = 0;
     piece_count++;

     printf (" %dth piece written  for %dth locator \n\n", piece_count, array_iter);

     /*-- code to fill bufxp with data goes here. *lenp should reflect the  size and
      *   should be less than or equal to MAXBUFLEN -- */
     /* --Optional code to set changed_bufpp and changed_lenp if the buffer must
      *   be changed dynamically --*/

      if (this is the last data buffer for current locator)
         *piecep = OCI_LAST_PIECE;
      else if (this is the first data buffer for the next locator)
         *piecep = OCI_FIRST_PIECE;
         piece_count = 0;
      else
         *piecep = OCI_NEXT_PIECE;

         return OCI_CONTINUE;
        }
    ...

#### Polling LOB Data in Array Write

The next example is polling LOB data in `OCILobArrayWrite()` with variable `amtp`, `bufl`, and `offset`.

    /* Fetch the locators */
    ...

    ub4    array_iter = 10;
    char  *bufp[10];
    oraub8 bufl[10];
    oraub8 char_amtp[10];
    oraub8 offset[10];
    sword  st;
    int    i, j;
    int piece_count;

    for (i=0; i<10; i++)
    {
      bufp[i] = (char *)malloc(1000);
      bufl[i] = 1000;
      /* Fill bufp here. */
    ...
      offset[i] = 1;
      char_amtp[i] = 10000;       /* Single byte fixed width char set. */
    }

         /* For 3rd locator write data in 500 bytes piece from offset 101. Amount
          * is 2000, that is, total number of pieces is 2000/500 = 4.
          */
         offset[2] = 101; bufl[2] = 500; char_amtp[2] = 2000;

         /* For 6th locator write data in 100 bytes piece from offset 51. Amount
          * is 0 indicating pure polling, that is, data is written
          * till OCI_LAST_PIECE
          */
         offset[5] = 51;  bufl[5] = 100; char_amtp[5] = 0;

         /* For 8th locator write 100 bytes of data in one piece. Note amount
          * is less than buffer length indicating single piece write.
          */
         offset[7] = 61;  bufl[7] = 200; char_amtp[7] = 100;

    for (i  = 1; i <= 10; i++)
    {
     /* Fill up bufp[i-1] here.  The first piece for ith locator would be written from
        bufp[i-1] */
    ...
        /* Calculate number of pieces that must be written */
        piece_count = char_amtp[i-1]/bufl[i-1];

        /* Single piece case */
        if (char_amtp[i-1] <= bufl[i-1])
          piece_count = 1;

        /* Zero amount indicates pure polling. So we can write as many
         * pieces as needed. Let us write 50 pieces.
         */
        if (char_amtp[i-1] == 0)
          piece_count = 50;

        st =  OCILobArrayWrite(<service context>, <error handle>,
                          &array_iter, /* array size */
                          lob_array,   /* array of locators */
                          NULL,        /* array of byte amounts */
                          char_amtp,   /* array of char amounts */
                          offset,      /* array of offsets */
                 (void **)bufp,        /* array of write buffers */
                          bufl,        /* array of buffer lengths */
                          OCI_FIRST_PIECE, /* piece information */
                          NULL,            /* callback context */
                          NULL,            /* callback function */
                          0,               /* character set ID - default */
                          SQLCS_IMPLICIT); /* character set form */

     for ( j = 2; j < piece_count; j++)
     {
       /* Fill up bufp[i-1] here. The jth piece for ith locator would be written
        * from bufp[i-1] */
    ...
       st =  OCILobArrayWrite(<service context>, <error handle>,
                              &array_iter, /* array size */
                              lob_array,   /* array of locators */
                              NULL,        /* array of byte amounts */
                              char_amtp,   /* array of char amounts */
                              offset,      /* array of offsets */
                     (void **)bufp,        /* array of write buffers */
                              bufl,        /* array of buffer lengths */
                              OCI_NEXT_PIECE, /* piece information */
                              NULL,           /* callback context */
                              NULL,           /* callback function */
                              0,              /* character set ID - default */
                              SQLCS_IMPLICIT);

        /* array_iter returns the index of the current array element for which
         * data is being written. for example, aray_iter = 1 implies first locator,
         * array_iter = 2 implies second locator and so on. Here i = array_iter.
         *
         * lob_array[ array_iter - 1] => Lob locator for which data is written.
         * bufp[array_iter - 1]       => Buffer pointer from which data is written.
         * char_amtp[ array_iter - 1] => Number of characters written in
         * the piece just written
         */
    }

    /* Fill up bufp[i-1] here.  The last piece for ith locator would be written from
     * bufp[i -1] */
    ...

    /* If piece_count is 1 it is a single piece write. */
    if (piece_count[i] != 1)
      st =  OCILobArrayWrite(<service context>, <error handle>,
                              &array_iter, /* array size */
                              lob_array,   /* array of locators */
                              NULL,        /* array of byte amounts */
                              char_amtp,   /* array of char amounts */
                              offset,      /* array of offsets */
                     (void **)bufp,        /* array of write buffers */
                              bufl,        /* array of buffer lengths */
                              OCI_LAST_PIECE,  /* piece information */
                              NULL,            /* callback context */
                              NULL,            /* callback function */
                              0,               /* character set ID - default */
                              SQLCS_IMPLICIT);
    }

    ...

#### Syntax

Use the following syntax references for the OCI programmatic environment:

C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — `OCILobArrayWrite()`.

#### Example

An example is provided in the following programmatic environment:

OCI: lwritearr.c

**Parent topic:** Using LOB APIs

### 12.23 About Trimming LOB Data

This section describes how to trim a LOB to the size you specify.

**See Also:**

Table 12-1

#### Usage Notes

Note the following issues regarding usage of this API.

#### Locking the Row Prior to Updating

Prior to updating a LOB value using the PL/SQL `DBMS_LOB` Package, or OCI, you must lock the row containing the LOB. While the SQL `INSERT` and `UPDATE` statements implicitly lock the row, locking is done explicitly by means of:

- A `SELECT` `FOR` `UPDATE` statement in SQL and PL/SQL programs.

- An `OCI` `pin` or `lock` function in OCI programs.

**See Also:**

[Example of Updating LOBs Through Updated Locators](advanced-design-considerations.md) for more details on the state of the locator after an update

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — `TRIM`

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — OCILobTrim2().

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB statements, and LOB TRIM executed embedded SQL extension

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md) for more information on LOB TRIM executed embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide ](../jjdbc/LOBs-and-BFiles.md)Chapter 7, "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `ltrim.sql`

- OCI: `ltrim.c`

- C++ (OCCI): No example is provided with this release.

- Java (JDBC): `ltrim.java`

**Parent topic:** Using LOB APIs

### 12.24 About Erasing Part of a LOB

This section describes how to erase part of a LOB.

**See Also:**

Table 12-1

#### Usage Notes

Note the following issues regarding usage of this API.

#### Locking the Row Prior to Updating

Prior to updating a LOB value using the PL/SQL `DBMS_LOB` Package or OCI, you must lock the row containing the LOB. While `INSERT` and `UPDATE` statements implicitly lock the row, locking is done explicitly by means of a `SELECT` `FOR` `UPDATE` statement in SQL and PL/SQL programs, or by using the `OCI` `pin` or `lock` function in OCI programs.

**See Also:**

[Example of Updating LOBs Through Updated Locators](advanced-design-considerations.md) f or more details on the state of the locator after an update

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB Package): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — ERASE

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — `OCILobErase2()`.

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB statements, and LOB ERASE executable embedded SQL extension.

- C/C++ (Pro\*C/C++):[Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)for more information on LOB ERASE executable embedded SQL extension

- Java (JDBC):[ Oracle Database JDBC Developer's Guide,](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `lerase.sql`

- OCI: `lerase.c`

- C++ (OCCI): No example is provided with this release.

- Java (JDBC): `lerase.java`

**Parent topic:** Using LOB APIs

### 12.25 Determining Whether a LOB instance Is Temporary

This section describes how to determine whether a LOB instance is temporary.

**See Also:**

Table 12-1

#### Syntax

Use the following syntax references for each programmatic environment:

- PL/SQL (DBMS_LOB): [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)"DBMS_LOB" — ISTEMPORARY, FREETEMPORARY

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/more-database-access-c-api.md)"LOB Functions" — OCILobIsTemporary().

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB statements, and embedded SQL and LOB DESCRIBE executable embedded SQL extension

- C/C++ (Pro\*C/C++): [Pro\*C/C++ Programmer's Guide](../lnpcc/embedded-SQL-statements-and-directives.md)for more information on LOB DESCRIBE executable embedded SQL extension

- Java (JDBC): [Oracle Database JDBC Developer's Guide](../jjdbc/LOBs-and-BFiles.md), "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Column.

#### Examples

Examples are provided in the following programmatic environments:

- PL/SQL (DBMS_LOB Package): `listemp.sql`

- OCI: `listemp.c`

<!-- -->

- Java (JDBC): Determining Whether a BLOB Is Temporary

**Parent topic:** Using LOB APIs

#### 12.25.1 Java (JDBC): Determining Whether a BLOB Is Temporary

To see if a `BLOB` is temporary, the JDBC application can either use the `isTemporary` instance method to determine whether the current `BLOB` object is temporary, or pass the `BLOB` object to the static `isTemporary` method to determine whether the specified `BLOB` object is temporary. These two methods are defined in`listempb.java`.

This JDBC API replaces previous work-arounds that use `DBMS_LOB.isTemporary().`

To determine whether a `CLOB` is temporary, the JDBC application can either use the `isTemporary` instance method to determine whether the current `CLOB` object is temporary, or pass the `CLOB` object to the static `isTemporary` method. These two methods are defined in `listempc.java`.

**Parent topic:** Determining Whether a LOB instance Is Temporary

### 12.26 Converting a BLOB to a CLOB

You can convert a `BLOB` instance to a `CLOB` using the PL/SQL procedure `DBMS_LOB.CONVERTTOCLOB`.

This technique is convenient if you have character data stored in binary format that you want to store in a `CLOB`. You specify the character set of the binary data when calling this procedure.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md) for details on syntax and usage of this procedure

**Parent topic:** Using LOB APIs

### 12.27 Converting a CLOB to a BLOB

You can convert a `CLOB` instance to a `BLOB` instance using the PL/SQL procedure `DBMS_LOB.CONVERTTOBLOB`. This technique is a convenient way to convert character data to binary data using LOB APIs. See

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md) for details on syntax and usage of this procedure

**Parent topic:** Using LOB APIs

### 12.28 Ensuring Read Consistency

This script can be used to ensure that hot backups can be taken of tables that have `NOLOGGING` or `FILESYSTEM_LIKE_LOGGING` LOBs and have a known recovery point with no read inconsistencies:

    ALTER DATABASE FORCE LOGGING;
    SELECT CHECKPOINT_CHANGE# FROM V$DATABASE;  --Start SCN

SCN (System Change Number) is a stamp that defines a version of the database at the time that a transaction is committed.

Perform the backup.

Run the next script:

    ALTER SYSTEM CHECKPOINT GLOBAL;
    SELECT CHECKPOINT_CHANGE# FROM V$DATABASE;  --End SCN
    ALTER DATABASE NO FORCE LOGGING;

Back up the archive logs generated by the database. At the minimum, archive logs between start SCN and end SCN (including both SCN points) must be backed up.

To restore to a point with no read inconsistency, restore to end SCN as your incomplete recovery point. If recovery is done to an SCN after end SCN, there can be read inconsistency in the `NOLOGGING` LOBs.

For SecureFiles, if a read inconsistency is found during media recovery, the database treats the inconsistent blocks as holes and fills `BLOB`s with `0`'s and `CLOB`s with fill characters.

**Parent topic:** Using LOB APIs
