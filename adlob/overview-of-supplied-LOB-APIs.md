## 10  Overview of Supplied LOB APIs

There are APIs supplied to support LOBs.

Topics:

- Programmatic Environments That Support LOBs

- Comparing the LOB Interfaces

- Using PL/SQL (DBMS_LOB Package) to Work With LOBs

- Using OCI to Work With LOBs

- Using C++ (OCCI) to Work With LOBs

- Using C/C++ (Pro\*C) to Work With LOBs

- Using COBOL (Pro\*COBOL) to Work With LOBs

- Using Java (JDBC) to Work With LOBs

- Oracle Provider for OLE DB (OraOLEDB)

- Overview of Oracle Data Provider for .NET (ODP.NET)

<!-- -->

- Programmatic Environments That Support LOBs
- Comparing the LOB Interfaces
- Using PL/SQL (DBMS_LOB Package) to Work With LOBs
- Using OCI to Work With LOBs
- Using C++ (OCCI) to Work With LOBs
- Using C/C++ (Pro\*C) to Work With LOBs
- Using COBOL (Pro\*COBOL) to Work With LOBs
- Using Java (JDBC) to Work With LOBs
- Oracle Provider for OLE DB (OraOLEDB)
- Overview of Oracle Data Provider for .NET (ODP.NET)

**Parent topic:** [Reference Semantics LOBs](reference-semantics-LOBs.md)

### 10.1 Programmatic Environments That Support LOBs

Table 10-1 lists the programmatic environments that support LOB functionality.

**See Also:**

APIs for supported LOB operations are described in detail in the following chapters:

- [Operations Specific to Persistent and Temporary LOBs](operations-specific-to-persistent-and-temporary-LOBs.md)

- [Using LOB APIs](using-LOB-APIs.md)

- [LOB APIs for BFILE Operations](LOB-APIs-for-BFILE-operations.md)

Table 10-1 Programmatic Environments That Support LOBs

| Language   | Precompiler or Interface Program              | Related Sections                                       | Related Books                                                                                                               |
|:-----------|:----------------------------------------------|:-------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------|
| PL/SQL     | DBMS_LOB Package                              | "Using PL/SQL (DBMS_LOB Package) to Work With LOBs".   | [Oracle Database PL/SQL Packages and Types Reference](../arpls/introduction-to-oracle-supplied-plsql-packages-and-types.md) |
| C          | Oracle Call Interface for C (OCI)             | "Using OCI to Work With LOBs".                         | [Oracle Call Interface Programmer's Guide](../lnoci/introduction.md)                                                        |
| C++        | Oracle Call Interface for C++ (OCCI)          | "Using C++ (OCCI) to Work With LOBs".                  | [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)                                            |
| C/C++      | Pro\*C/C++ Precompiler                        | "Using C/C++ (Pro\*C) to Work With LOBs".              | [Pro\*C/C++ Programmer's Guide](../lnpcc/introduction-and-concepts.md)                                                      |
| COBOL      | Pro\*COBOL Precompiler                        | "Using COBOL (Pro\*COBOL) to Work With LOBs".          | [Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)                                                      |
| Java       | JDBC Application Programmatic Interface (API) | "Using Java (JDBC) to Work With LOBs".                 | [Oracle Database JDBC Developer’s Guide](../jjdbc/overview-of-JDBC.md).                                                     |
| ADO/OLE DB | Oracle Provider for OLE DB (OraOLEDB).        | "Oracle Provider for OLE DB (OraOLEDB)"                | [Oracle Provider for OLE DB Developer's Guide for Microsoft Windows](../oledb/introduction-to-oracle-provider-for-oledb.md) |
| .NET       | Oracle Data Provider for .NET (ODP.NET)       | "Overview of Oracle Data Provider for .NET (ODP.NET) " | [Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/intro.md)                                  |

**Parent topic:** Overview of Supplied LOB APIs

### 10.2 Comparing the LOB Interfaces

Table 10-2 and Table 10-3 compare the eight LOB programmatic interfaces by listing their functions and methods used to operate on LOBs. The tables are split in two simply to accommodate all eight interfaces. The functionality of the interfaces, with regards to LOBs, is described in the following sections.

Table 10-2 Comparing the LOB Interfaces, 1 of 2

| PL/SQL: DBMS_LOB (dbmslob.sql)   | C (OCI)(ociap.h)          | C++ (OCCI) (occiData.h). Also for Clob and Bfile classes. | Pro\*C/C++ and Pro\*COBOL          |
|:---------------------------------|:--------------------------|:----------------------------------------------------------|:-----------------------------------|
| `DBMS_LOB.COMPARE`               | N/A                       | N/A                                                       | N/A                                |
| `DBMS_LOB.INSTR`                 | N/A                       | N/A                                                       | N/A                                |
| `DBMS_LOB.SUBSTR`                | N/A                       | N/A                                                       | N/A                                |
| `DBMS_LOB.APPEND`                | `OCILobAppend()`          | `Blob.append()`                                           | `APPEND`                           |
| N/A (use PL/SQL assign operator) | `OCILobAssign()`          |                                                           | `ASSIGN`                           |
| N/A                              | `OCILobCharSetForm()`     | `Clob.getCharsetForm` (`CLOB` only)                       | N/A                                |
| N/A                              | `OCILobCharSetId()`       | `Clob.getCharsetId()`<br>(`CLOB` only)                    | N/A                                |
| `DBMS_LOB.CLOSE `                | `OCILobClose()`           | `Blob.close() `                                           | `CLOSE`                            |
| N/A                              | N/A                       | `Clob.closeStream()`                                      | N/A                                |
| `DBMS_LOB.COPY `                 | `OCILobCopy2()`           | `Blob.copy()`                                             | `COPY`                             |
| `DBMS_LOB.ERASE `                | `OCILobErase2()`          | N/A                                                       | `ERASE`                            |
| `DBMS_LOB.FILECLOSE `            | `OCILobFileClose()`       | `Clob.close()`                                            | `CLOSE`                            |
| `DBMS_LOB.FILECLOSEALL `         | `OCILobFileCloseAll()`    | N/A                                                       | `FILE CLOSE ALL`                   |
| `DBMS_LOB.FILEEXISTS `           | `OCILobFileExist()`       | `Bfile.fileExists()`                                      | `DESCRIBE [FILEEXISTS]`            |
| DBMS_LOB.GETCHUNKSIZE            | OCILobGetChunkSize()      | Blob.getChunkSize()                                       | DESCRIBE \[CHUNKSIZE\]             |
| `DBMS_LOB.GET_STORAGE_LIMIT`     | `OCILobGetStorageLimit()` | N/A                                                       | N/A                                |
| `DBMS_LOB.GETOPTIONS`            | `OCILobGetOptions()`      | `Blob`/`Clob`::`getOptions`                               | N/A                                |
| `DBMS_LOB.FILEGETNAME `          | `OCILobFileGetName()`     | `Bfile.getFileName()` and `Bfile.getDirAlias()`           | `DESCRIBE` `DIRECTORY`, `FILENAME` |
| `DBMS_LOB.FILEISOPEN `           | `OCILobFileIsOpen()`      | `Bfile.isOpen()`                                          | `DESCRIBE` `ISOPEN`                |
| `DBMS_LOB.FILEOPEN `             | `OCILobFileOpen()`        | `Bfile.open()`                                            | `OPEN`                             |
| N/A (use BFILENAME operator)     | `OCILobFileSetName()`     | `Bfile.setName()`                                         | `FILE SET`                         |
| `DBMS_LOB.GETLENGTH `            | `OCILobGetLength2()`      | `Blob.length()`                                           | `DESCRIBE` `LENGTH`                |
| N/A                              | `OCILobIsEqual()`         | Use operator = ( )=/!=                                    | N/A                                |
| `DBMS_LOB.ISOPEN `               | `OCILobIsOpen()`          | `Blob.isOpen()`                                           | `DESCRIBE ISOPEN`                  |
| `DBMS_LOB.LOADFROMFILE`          | `OCILobLoadFromFile2()`   | Use `overloadedcopy()`                                    | LOAD FROM FILE                     |
| N/A                              | `OCILobLocatorIsInit()`   | `Clob.isinitialized()`                                    | N/A                                |
| `DBMS_LOB.OPEN`                  | `OCILobOpen()`            | `Blob.open`                                               | `OPEN`                             |
| `DBMS_LOB.READ `                 | `OCILobRead()`            | `Blob.read`                                               | `READ`                             |
| `DBMS_LOB.SETOPTIONS`            | `OCILobSetOptions()`      | `Blob`/`Clob`::`setOptions`                               | N/A                                |
| `DBMS_LOB.TRIM `                 | `OCILobTrim2()`           | `Blob.trim`                                               | `TRIM`                             |
| `DBMS_LOB.WRITE `                | `OCILobWrite2`            | `Blob.write`                                              | `WRITEORALOB.`                     |
| `DBMS_LOB.WRITEAPPEND`           | `OCILobWriteAppend2()`    | N/A                                                       | `WRITE APPEND`                     |
| `DBMS_LOB.CREATETEMPORARY`       | `OCILobCreateTemporary()` | N/A                                                       | N/A                                |
| `DBMS_LOB.FREETEMPORARY`         | `OCILobFreeTemporary()`   | N/A                                                       | N/A                                |
| `DBMS_LOB.ISTEMPORARY`           | `OCILobIsTemporary()`     | N/A                                                       | N/A                                |
| N/A                              | `OCILobLocatorAssign()`   | use operator = ( ) or copy constructor                    | N/A                                |

Table 10-3 Comparing the LOB Interfaces, 2 of 2

| PL/SQL: DBMS_LOB (dbmslob.sql) | Java (JDBC)                                                                                                                      | ODP.NET                                                |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------|
| `DBMS_LOB.COMPARE`             | Use `DBMS_LOB`.                                                                                                                  | `OracleClob.Compare`                                   |
| `DBMS_LOB.INSTR `              | position                                                                                                                         | `OracleClob.Search`                                    |
| `DBMS_LOB.SUBSTR `             | `getBytes` for `BLOB`s or `BFILE`s`getSubString` for `CLOB`s                                                                     | N/A                                                    |
| `DBMS_LOB.APPEND `             | Use `length` and then `putBytes() `or `PutString()`                                                                              | `OracleClob.Append`                                    |
| `OCILobAssign()`               | N/A \[use equal sign\]                                                                                                           | `OracleClob.Clone`                                     |
| `OCILobCharSetForm()`          | N/A                                                                                                                              | N/A                                                    |
| `OCILobCharSetId()`            | N/A                                                                                                                              | N/A                                                    |
| `DBMS_LOB.CLOSE `              | use `DBMS_LOB`.                                                                                                                  | `OracleClob.Close`                                     |
| `DBMS_LOB.COPY `               | Use read and write                                                                                                               | `OracleClob.CopyTo`                                    |
| `DBMS_LOB.ERASE `              | Use `DBMS_LOB`.                                                                                                                  | `OracleClob.Erase`                                     |
| `DBMS_LOB.FILECLOSE `          | `closeFile`                                                                                                                      | `OracleBFile.CloseFile`                                |
| `DBMS_LOB.FILECLOSEALL `       | Use `DBMS_LOB`.                                                                                                                  | N/A                                                    |
| `DBMS_LOB.FILEEXISTS `         | `fileExists`                                                                                                                     | `OracleBFile.FileExists`                               |
| `DBMS_LOB.GETCHUNKSIZE`        | `getChunkSize`                                                                                                                   | `OracleClob.OptimumChunkSize`                          |
| `DBMS_LOB.FILEGETNAME `        | `getDirAlias`<br>`getName`                                                                                                       | `OracleBFile.DirectoryName``Oracle.BFile.FileName`     |
| `DBMS_LOB.FILEISOPEN `         | Use `DBMS_LOB.ISOPEN`                                                                                                            | `OracleBFile.IsOpen`                                   |
| `DBMS_LOB.FILEOPEN `           | `openFile`                                                                                                                       | `OracleBFile.OpenFile`                                 |
| `OCILobFileSetName()`          | Use `BFILENAME`                                                                                                                  | `OracleBFile.DirectoryName`<br>`Oracle.BFile.FileName` |
| `OCILobFlushBuffer()`          | N/A                                                                                                                              | N/A                                                    |
| `DBMS_LOB.GETLENGTH `          | `length`                                                                                                                         | `OracleClob.Length`                                    |
| N/A                            | `equals()`                                                                                                                       | N/A                                                    |
| `DBMS_LOB.ISOPEN `             | use `DBMS_LOB.ISOPEN()`                                                                                                          | `OracleClob.IsInChunkWriteMode`                        |
| `DBMS_LOB.LOADFROMFILE`        | Use `read` and then `write`                                                                                                      | N/A                                                    |
| `DBMS_LOB.OPEN`                | Use `DBMS_LOB.OPEN()`                                                                                                            | `OracleClob.BeginChunkWrite`                           |
| `DBMS_LOB.READ `               | `BLOB` or `BFILE`: `getBytes()` and `getBinaryStream()`<br>`CLOB`: `getString()` and `getSubString()` and `getCharacterStream()` | `OracleClob.Read`                                      |
| `DBMS_LOB.TRIM `               | Use `DBMS_LOB.TRIM()`                                                                                                            | `OracleClob.SetLength`                                 |
| `DBMS_LOB.WRITE `              | `BLOB`: `setBytes()` and `setBinaryStream()`<br>`CLOB`: `setString()` and `setCharacterStream()`                                 | `OracleClob.Write`                                     |
| `DBMS_LOB.WRITEAPPEND`         | Use `length()` and then `putString()` or `putBytes()`                                                                            | `OracleClob.Append`                                    |
| `DBMS_LOB.CREATETEMPORARY`     | N/A                                                                                                                              | `OracleClob` constructors                              |
| `DBMS_LOB.FREETEMPORARY`       | N/A                                                                                                                              | `OracleClob.Dispose`                                   |
| `DBMS_LOB.ISTEMPORARY`         | N/A                                                                                                                              | `OracleClob.IsTemporary`                               |

**Parent topic:** Overview of Supplied LOB APIs

### 10.3 Using PL/SQL (DBMS_LOB Package) to Work With LOBs

The PL/SQL `DBMS_LOB` package can be used for the following operations:

- Internal persistent LOBs and Temporary LOBs: Read and modify operations, either entirely or in a piece-wise manner.

- BFILEs: Read operations

  **See Also:**

  [Oracle Database PL/SQL Packages and Types Reference ](../arpls/DBMS_LOB.md)for detailed documentation, including parameters, parameter types, return values, and example code.

<!-- -->

- Provide a LOB Locator Before Running the DBMS_LOB Routine
- Guidelines for Offset and Amount Parameters in DBMS_LOB Operations
- Determining Character Set ID
- PL/SQL Functions and Procedures for LOBs
- PL/SQL Functions and Procedures to Modify LOB Values
- PL/SQL Functions and Procedures for Introspection of LOBs
- PL/SQL Operations on Temporary LOBs
- PL/SQL Read-Only Functions and Procedures for BFILEs
- PL/SQL Functions and Procedures to Open and Close Internal and External LOBs

**Parent topic:** Overview of Supplied LOB APIs

#### 10.3.1 Provide a LOB Locator Before Running the DBMS_LOB Routine

`DBMS_LOB` routines work based on LOB locators. For the successful completion of `DBMS_LOB` routines, you must provide an input locator representing a LOB that exists in the database tablespaces or external file system, before you call the routine.

- Persistent LOBs: First use SQL to define tables that contain LOB columns, and subsequently you can use SQL to initialize or populate the locators in these LOB columns.

- External LOBs: Define a `DIRECTORY` object that maps to a valid physical directory containing the external LOBs that you intend to access. These files must exist, and have READ permission for Oracle Server to process. If your operating system uses case-sensitive path names, then specify the directory in the correct case.

Once the LOBs are defined and created, you may then `SELECT` a LOB locator into a local PL/SQL LOB variable and use this variable as an input parameter to `DBMS_LOB` for access to the LOB value.

Examples provided with each `DBMS_LOB` routine illustrate this in the following sections.

**See Also:**

[Directory Objects](LOB-APIs-for-BFILE-operations.md)

**Parent topic:** Using PL/SQL (DBMS_LOB Package) to Work With LOBs

#### 10.3.2 Guidelines for Offset and Amount Parameters in DBMS_LOB Operations

The following guidelines apply to offset and amount parameters used in procedures in the `DBMS_LOB` PL/SQL package:

- For character data—in all formats, fixed-width and varying-width—the `amount` and `offset` parameters are in characters. This applies to operations on `CLOB` and `NCLOB` data types.

- For binary data, the `offset` and `amount` parameters are in bytes. This applies to operations on `BLOB` data types.

- When using the following procedures:

  - `DBMS_LOB.LOADFROMFILE`

  - `DBMS_LOB.LOADBLOBFROMFILE`

  - `DBMS_LOB.LOADCLOBFROMFILE`

  you cannot specify an amount parameter with a value larger than the size of the `BFILE` you are loading from. To load the entire `BFILE` with these procedures, you must specify either the exact size of the `BFILE`, or the maximum allowable storage limit.

- When using `DBMS_LOB.READ`, the `amount` parameter can be larger than the size of the data. The amount should be less than or equal to the size of the buffer. The buffer size is limited to 32K.

  **See Also:**

  - [Loading a LOB with Data from a BFILE](using-LOB-APIs.md)

  - [About Loading a BLOB with Data from a BFILE](using-LOB-APIs.md)

  - [Loading a CLOB or NCLOB with Data from a BFILE](using-LOB-APIs.md)

  - [About Reading Data from a LOB](using-LOB-APIs.md)

**Parent topic:** Using PL/SQL (DBMS_LOB Package) to Work With LOBs

#### 10.3.3 Determining Character Set ID

To determine the character set ID, you must know the character set name.

A user can select from the `V$NLS_VALID_VALUES` view, which lists the names of the character sets that are valid as database and national character sets. Then call the function `NLS_CHARSET_ID` with the desired character set name as the one string argument. The character set ID is returned as an integer. `UTF16` does not work because it has no character set name. Use character set ID = 1000 for `UTF16`. Although `UTF16` is not allowed as a database or national character set, the APIs in `DBMS_LOB` support it for database conversion purposes. `DBMS_LOB.LOADCLOBFROMFILE` and other procedures in `DBMS_LOB` take character set ID, not character set name, as an input.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md) for details and supported Unicode encodings

- [Oracle Database Globalization Support Guide](../nlspg/appendix-A-locale-data.md) for supported languages

**Parent topic:** Using PL/SQL (DBMS_LOB Package) to Work With LOBs

#### 10.3.4 PL/SQL Functions and Procedures for LOBs

**See Also:**

PL/SQL functions and procedures that operate on `BLOB`s, `CLOB`s, `NCLOB`s, and `BFILE`s

- Table 10-4 to modify persistent LOB values

- Table 10-5 to read or examine LOB values

- Table 10-6 to create, free, or check on temporary LOBs

- Table 10-7 for read-only functions on external LOBs (`BFILE`s)

- Table 10-8 to open or close a LOB, or check if LOB is open

- [PL/SQL Packages for LOBs and DBFS](using-oracle-LOBs-storage.md) to perform archive management on SecureFiles

**Parent topic:** Using PL/SQL (DBMS_LOB Package) to Work With LOBs

#### 10.3.5 PL/SQL Functions and Procedures to Modify LOB Values

Here is a table of `DBMS_LOB` procedures:

Table 10-4 PL/SQL: DBMS_LOB Procedures to Modify LOB Values

| Function/Procedure | Description                                                                  |
|:-------------------|:-----------------------------------------------------------------------------|
| `APPEND`           | Appends the LOB value to another LOB                                         |
| `CONVERTTOBLOB`    | Converts a `CLOB` to a `BLOB`                                                |
| `CONVERTTOCLOB`    | Converts a `BLOB` to a `CLOB`                                                |
| `COPY`             | Copies all or part of a LOB to another LOB                                   |
| `ERASE`            | Erases part of a LOB, starting at a specified offset                         |
| `FRAGMENT_DELETE`  | Delete the data from the LOB at the given offset for the given length        |
| `FRAGMENT_INSERT`  | Insert the given data (\< 32KBytes) into the LOB at the given offset         |
| `FRAGMENT_MOVE`    | Move the given amount of bytes from the given offset to the new given offset |
| `FRAGMENT_REPLACE` | Replace the data at the given offset with the given data (\< 32kBytes)       |
| `LOADFROMFILE`     | Load `BFILE` data into a persistent LOB                                      |
| `LOADCLOBFROMFILE` | Load character data from a file into a LOB                                   |
| `LOADBLOBFROMFILE` | Load binary data from a file into a LOB                                      |
| `SETOPTIONS`       | Sets LOB features (deduplication and compression)                            |
| `TRIM`             | Trims the LOB value to the specified shorter length                          |
| `WRITE`            | Writes data to the LOB at a specified offset                                 |
| `WRITEAPPEND`      | Writes data to the end of the LOB                                            |

**Parent topic:** Using PL/SQL (DBMS_LOB Package) to Work With LOBs

#### 10.3.6 PL/SQL Functions and Procedures for Introspection of LOBs

Table 10-5 PL/SQL: DBMS_LOB Procedures to Read or Examine Internal and External LOB values

| Function/Procedure  | Description                                                                                                                             |
|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------|
| `COMPARE`           | Compares the value of two LOBs                                                                                                          |
| `GETCHUNKSIZE`      | Gets the chunk size used when reading and writing. This only works on persistent LOBs and does not apply to external LOBs (`BFILE`s).   |
| `GETLENGTH`         | Gets the length of the LOB value.                                                                                                       |
| `GETOPTIONS`        | Returns options (deduplication, compression, encryption) for SecureFiles.                                                               |
| `GET_STORAGE_LIMIT` | Gets the LOB storage limit for the database configuration.                                                                              |
| `INSTR`             | Returns the matching position of the nth occurrence of the pattern in the LOB.                                                          |
| `ISSECUREFILE`      | Returns `TRUE` if the `BLOB` or `CLOB` locator passed to it is for a SecureFiles or `FALSE` if it is not.                               |
| `READ`              | Reads data from the LOB starting at the specified offset.                                                                               |
| `SETOPTIONS`        | Sets options (deduplication and compression) for a SecureFiles, overriding the default LOB column settings. Incurs a server round trip. |
| `SUBSTR`            | Returns part of the LOB value starting at the specified offset.                                                                         |

**Parent topic:** Using PL/SQL (DBMS_LOB Package) to Work With LOBs

#### 10.3.7 PL/SQL Operations on Temporary LOBs

Table 10-6 PL/SQL: DBMS_LOB Procedures to Operate on Temporary LOBs

| Function/Procedure | Description                                       |
|:-------------------|:--------------------------------------------------|
| CREATETEMPORARY    | Creates a temporary LOB                           |
| ISTEMPORARY        | Checks if a LOB locator refers to a temporary LOB |
| FREETEMPORARY      | Frees a temporary LOB                             |

**Parent topic:** Using PL/SQL (DBMS_LOB Package) to Work With LOBs

#### 10.3.8 PL/SQL Read-Only Functions and Procedures for BFILEs

Table 10-7 PL/SQL: DBMS_LOB Read-Only Procedures for BFILEs

| Function/Procedure | Description                                                                             |
|:-------------------|:----------------------------------------------------------------------------------------|
| `FILECLOSE`        | Closes the file. Use `CLOSE()` instead.                                                 |
| `FILECLOSEALL`     | Closes all previously opened files                                                      |
| `FILEEXISTS`       | Checks if the file exists on the server                                                 |
| `FILEGETNAME`      | Gets the directory object name and file name                                            |
| `FILEISOPEN`       | `Checks if the file was opened using the input BFILE` locators. Use `ISOPEN()` instead. |
| `FILEOPEN`         | Opens a file. Use `OPEN()` instead.                                                     |

**Parent topic:** Using PL/SQL (DBMS_LOB Package) to Work With LOBs

#### 10.3.9 PL/SQL Functions and Procedures to Open and Close Internal and External LOBs

Table 10-8 PL/SQL: DBMS_LOB Procedures to Open and Close Internal and External LOBs

| Function/Procedure | Description           |
|:-------------------|:----------------------|
| `OPEN`             | Opens a LOB           |
| `ISOPEN`           | Sees if a LOB is open |
| `CLOSE`            | Closes a LOB          |

**See Also:**

[Opening Persistent LOBs with the OPEN and CLOSE Interfaces](advanced-design-considerations.md) for detailed information about these procedures for specific LOB operations, such as, `INSERT` a row containing a LOB

**Parent topic:** Using PL/SQL (DBMS_LOB Package) to Work With LOBs

### 10.4 Using OCI to Work With LOBs

Oracle Call Interface (OCI) LOB functions enable you to access and make changes to LOBs and to read data from `BFILE`s in C.

- Prefetching of LOB Data, Length, and Chunk Size
- Setting the CSID Parameter for OCI LOB APIs
- Fixed-Width and Varying-Width Character Set Rules for OCI
- OCILobLoadFromFile2() Amount Parameter
- OCILobRead2() Amount Parameter
- OCILobLocator Pointer Assignment
- LOB Locators in Defines and Out-Bind Variables in OCI
- OCI Functions That Operate on BLOBs, CLOBs, NCLOBs, and BFILEs
- OCI Functions to Modify Persistent LOB (BLOB, CLOB, and NCLOB) Values
- OCI Functions to Read or Examine Persistent LOB and External LOB (BFILE) Values
- OCI Functions for Temporary LOBs
- OCI Read-Only Functions for BFILEs
- OCI LOB Locator Functions
- OCI Functions to Open and Close Internal and External LOBs
- OCI LOB Examples
- Further Information About OCI

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/lobs-and-bfile-operations.md) chapter "LOB and BFILE Operations" for the details of all topics discussed in this section.

**Parent topic:** Overview of Supplied LOB APIs

#### 10.4.1 Prefetching of LOB Data, Length, and Chunk Size

To improve OCI access of smaller LOBs, LOB data can be prefetched and cached while also fetching the locator. This applies to internal LOBs, temporary LOBs, and `BFILE`s.

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.2 Setting the CSID Parameter for OCI LOB APIs

If you want to read or write data in 2-byte Unicode format, then set the `csid` (character set ID) parameter in `OCILobRead2()` and `OCILobWrite2()` to `OCI_UTF16ID`.

The `csid` parameter indicates the character set id for the buffer parameter. You can set the `csid` parameter to any character set ID. If the `csid` parameter is set, then it overrides the `NLS_LANG` environment variable.

**See Also:**

- [Oracle Call Interface Programmer's Guide](../lnoci/oci-character-set-conversion-functions.md)for information on the `OCIUnicodeToCharSet()` function and details on OCI syntax in general.

- [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md)for detailed information about implementing applications in different languages.

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.3 Fixed-Width and Varying-Width Character Set Rules for OCI

In OCI, for fixed-width client-side character sets, the following rules apply:

- `CLOB`s and `NCLOB`s: offset and amount parameters are always in characters

- `BLOB`s and `BFILE`s: offset and amount parameters are always in bytes

The following rules apply only to varying-width client-side character sets:

- Offset parameter:

  Regardless of whether the client-side character set is varying-width, the offset parameter is always as follows:

  - `CLOB`s and `NCLOB`s: in characters

  - `BLOB`s and `BFILE`s: in bytes

- Amount parameter:

  The amount parameter is always as follows:

  - When referring to a server-side LOB: in characters

  - When referring to a client-side buffer: in bytes

- OCILobFileGetLength():

  Regardless of whether the client-side character set is varying-width, the output length is as follows:

  - `CLOB`s and `NCLOB`s: in characters

  - `BLOB`s and `BFILE`s: in bytes

- OCILobRead2():

  With client-side character set of varying-width, `CLOB`s and `NCLOB`s:

  - Input amount is in characters. Input amount refers to the number of characters to read from the server-side `CLOB` or `NCLOB`.

  - Output amount is in bytes. Output amount indicates how many bytes were read into the buffer `bufp`.

- OCILobWrite2(): With client-side character set of varying-width, `CLOB`s and `NCLOB`s:

  - Input amount is in bytes. The input amount refers to the number of bytes of data in the input buffer `bufp`.

  - Output amount is in characters. The output amount refers to the number of characters written into the server-side `CLOB` or `NCLOB`.

<!-- -->

- Other Operations
- NCLOBs in OCI

**Parent topic:** Using OCI to Work With LOBs

##### 10.4.3.1 Other Operations

For all other LOB operations, irrespective of the client-side character set, the `amount` parameter is in characters for `CLOB`s and `NCLOB`s. These include `OCILobCopy2()`, `OCILobErase2()`, `OCILobLoadFromFile2()`, and `OCILobTrim2()`. All these operations refer to the amount of LOB data on the server.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md)

**Parent topic:** Fixed-Width and Varying-Width Character Set Rules for OCI

##### 10.4.3.2 NCLOBs in OCI

`NCLOB`s are allowed as parameters in methods.

**Parent topic:** Fixed-Width and Varying-Width Character Set Rules for OCI

#### 10.4.4 OCILobLoadFromFile2() Amount Parameter

When using `OCILobLoadFromFile2()` you cannot specify `amount` larger than the length of the `BFILE`. To load the entire `BFILE`, you can pass the value returned by `OCILobGetStorageLimit()`.

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.5 OCILobRead2() Amount Parameter

To read to the end of a LOB using `OCILobRead2()`, you specify an amount equal to the value returned by `OCILobGetStorageLimit()`.

**See Also:**

[About Reading Data from a LOB](using-LOB-APIs.md)

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.6 OCILobLocator Pointer Assignment

Special care must be taken when assigning `OCILobLocator` pointers in an OCI program—using the "=" assignment operator. Pointer assignments create a shallow copy of the LOB. After the pointer assignment, the source and target LOBs point to the same copy of data.

These semantics are different from using LOB APIs, such as `OCILobAssign()` or `OCILobLocatorAssign()` to perform assignments. When the these APIs are used, the locators logically point to independent copies of data after assignment.

For temporary LOBs, before performing pointer assignments, you must ensure that any temporary LOB in the target LOB locator is freed by calling `OCIFreeTemporary()`. In contrast, when `OCILobLocatorAssign()` is used, the original temporary LOB in the target LOB locator variable, if any, is freed automatically before the assignment happens.

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.7 LOB Locators in Defines and Out-Bind Variables in OCI

Before you reuse a LOB locator in a define or an out-bind variable in a SQL statement, you must free any temporary LOB in the existing LOB locator buffer using `OCIFreeTemporary()`.

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.8 OCI Functions That Operate on BLOBs, CLOBs, NCLOBs, and BFILEs

OCI functions that operate on `BLOB`s, `CLOB`s, `NCLOB`s, and `BFILE`s are as follows:

- To modify persistent LOBs, see \*\*INTERNAL XREF ERROR\*\*

- To read or examine LOB values, see \*\*INTERNAL XREF ERROR\*\*

- To create or free temporary LOB, or check if Temporary LOB exists, see \*\*INTERNAL XREF ERROR\*\*

- For read only functions on external LOBs (`BFILE`s), see \*\*INTERNAL XREF ERROR\*\*

- To operate on LOB locators, see \*\*INTERNAL XREF ERROR\*\*

- To open and close LOBs, see \*\*INTERNAL XREF ERROR\*\*

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.9 OCI Functions to Modify Persistent LOB (BLOB, CLOB, and NCLOB) Values

Table 10-9 OCI Functions to Modify Persistent LOB (BLOB, CLOB, and NCLOB) Values

| Function/Procedure       | Description                                                                |
|:-------------------------|:---------------------------------------------------------------------------|
| `OCILobAppend()`         | Appends LOB value to another LOB.                                          |
| `OCILobArrayWrite()`     | Writes data using multiple locators in one round trip.                     |
| `OCILobCopy2()`          | Copies all or part of a LOB to another LOB.                                |
| `OCILobErase2()`         | Erases part of a LOB, starting at a specified offset.                      |
| `OCILobLoadFromFile2()`  | Loads `BFILE` data into a persistent LOB.                                  |
| `OCILobSetContentType()` | Sets a content string in a SecureFiles.                                    |
| `OCILObSetOptions()`     | Enables option settings (deduplication and compression) for a SecureFiles. |
| `OCILobTrim2()`          | Truncates a LOB.                                                           |
| `OCILobWrite2()`         | Writes data from a buffer into a LOB, overwriting existing data.           |
| `OCILobWriteAppend2()`   | Writes data from a buffer to the end of the LOB.                           |

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.10 OCI Functions to Read or Examine Persistent LOB and External LOB (BFILE) Values

Table 10-10 OCI Functions to Read or Examine persistent LOB and external LOB (BFILE) Values

| Function/Procedure        | Description                                                                                                                      |
|:--------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `OCILobArrayRead()`       | Reads data using multiple locators in one round trip.                                                                            |
| `OCILobGetChunkSize()`    | Gets the chunk size used when reading and writing. This works on persistent LOBs and does not apply to external LOBs (`BFILE`s). |
| `OCILobGetContentType()`  | Gets the content string for a SecureFiles.                                                                                       |
| `OCILobGetLength2()`      | Returns the length of a LOB or a `BFILE`.                                                                                        |
| `OCILObGetOptions()`      | Obtains the enabled settings (deduplication, compression, encryption) for a given SecureFiles.                                   |
| `OCILobGetStorageLimit()` | Gets the maximum length of an internal LOB.                                                                                      |
| `OCILobRead2()`           | Reads a specified portion of a non-`NULL` LOB or a `BFILE` into a buffer.                                                        |

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.11 OCI Functions for Temporary LOBs

Table 10-11 OCI Functions for Temporary LOBs

| Function/Procedure        | Description                     |
|:--------------------------|:--------------------------------|
| `OCILobCreateTemporary()` | Creates a temporary LOB.        |
| `OCILobIsTemporary()`     | Sees if a temporary LOB exists. |
| `OCILobFreeTemporary()`   | Frees a temporary LOB.          |

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.12 OCI Read-Only Functions for BFILEs

Table 10-12 OCI Read-Only Functions for BFILES

| Function/Procedure     | Description                       |
|:-----------------------|:----------------------------------|
| `OCILobFileClose()`    | Closes an open `BFILE`.           |
| `OCILobFileCloseAll()` | Closes all open `BFILE`s.         |
| `OCILobFileExists()`   | Checks whether a `BFILE` exists.  |
| `OCILobFileGetName()`  | Returns the name of a `BFILE`.    |
| `OCILobFileIsOpen()`   | Checks whether a `BFILE` is open. |
| `OCILobFileOpen()`     | Opens a `BFILE`.                  |

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.13 OCI LOB Locator Functions

Table 10-13 OCI LOB-Locator Functions

| Function/Procedure      | Description                                            |
|:------------------------|:-------------------------------------------------------|
| `OCILobAssign() `       | Assigns one LOB locator to another.                    |
| `OCILobCharSetForm()`   | Returns the character set form of a LOB.               |
| `OCILobCharSetId()`     | Returns the character set ID of a LOB.                 |
| `OCILobFileSetName()`   | Sets the name of a `BFILE` in a locator.               |
| `OCILobIsEqual()`       | Checks whether two LOB locators refer to the same LOB. |
| `OCILobLocatorIsInit()` | Checks whether a LOB locator is initialized.           |

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.14 OCI Functions to Open and Close Internal and External LOBs

Table 10-14 OCI Functions to Open and Close Internal and External LOBs

| Function/Procedure | Description            |
|:-------------------|:-----------------------|
| `OCILobOpen()`     | Opens a LOB.           |
| `OCILobIsOpen()`   | Sees if a LOB is open. |
| `OCILobClose()`    | Closes a LOB.          |

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.15 OCI LOB Examples

Further OCI examples are provided in:

- [Using LOB APIs](using-LOB-APIs.md)

- [LOB APIs for BFILE Operations](LOB-APIs-for-BFILE-operations.md)

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/oci-demo-programs.md) for further OCI demonstration script listings

**Parent topic:** Using OCI to Work With LOBs

#### 10.4.16 Further Information About OCI

**See Also:**

[`http://www.oracle.com/technology/`](http://www.oracle.com/technology/) for more information about OCI features and frequently asked questions.

**Parent topic:** Using OCI to Work With LOBs

### 10.5 Using C++ (OCCI) to Work With LOBs

Oracle C++ Call Interface (OCCI) is a C++ API for manipulating data in an Oracle database. OCCI is organized as an easy-to-use set of C++ classes that enable a C++ program to connect to a database, run SQL statements, insert/update values in database tables, retrieve results of a query, run stored procedures in the database, and access metadata of database schema objects. OCCI also provides a seamless interface to manipulate objects of user-defined types as C++ class instances.

Oracle C++ Call Interface (OCCI) is designed so that you can use OCI and OCCI together to build applications.

The OCCI API provides the following advantages over JDBC and ODBC:

- OCCI encompasses more Oracle functionality than JDBC. OCCI provides all the functionality of OCI that JDBC does not provide.

- OCCI provides compiled performance. With compiled programs, the source code is written as close to the computer as possible. Because JDBC is an interpreted API, it cannot provide the performance of a compiled API. With an interpreted program, performance degrades as each line of code must be interpreted individually into code that is close to the computer.

- OCCI provides memory management with smart pointers. You do not have to be concerned about managing memory for OCCI objects. This results in robust higher performance application code.

- Navigational access of OCCI enables you to intuitively access objects and call methods. Changes to objects persist without writing corresponding SQL statements. If you use the client side cache, then the navigational interface performs better than the object interface.

- With respect to ODBC, the OCCI API is simpler to use. Because ODBC is built on the C language, OCCI has all the advantages C++ provides over C. Moreover, ODBC has a reputation as being difficult to learn. The OCCI, by contrast, is designed for ease of use.

You can use OCCI to make changes to an entire persistent LOB, or to pieces of the beginning, middle, or end of it, as follows:

- For reading from internal and external LOBs (`BFILE`s)

- For writing to persistent LOBs

<!-- -->

- OCCI Classes for LOBs
- Fixed-Width Character Set Rules
- Varying-Width Character Set Rules
- Offset and Amount Parameters for Other OCCI Operations
- Amount Parameter for OCCI LOB copy() Methods
- Amount Parameter for OCCI read() Operations
- Further Information About OCCI
- OCCI Methods That Operate on BLOBs, BLOBs, NCLOBs, and BFILEs
- OCCI Methods to Modify Persistent LOB (BLOB, CLOB, and NCLOB) Values
- OCCI Methods to Read or Examine Persistent LOB and BFILE Values
- OCCI Read-Only Methods for BFILEs
- Other OCCI LOB Methods
- OCCI Methods to Open and Close Internal and External LOBs

**Parent topic:** Overview of Supplied LOB APIs

#### 10.5.1 OCCI Classes for LOBs

OCCI provides these classes that allow you to use different types of LOB instances as objects in your C++ application:

- `Clob` class to access and modify data stored in internal `CLOB`s and `NCLOB`s

- `Blob` class to access and modify data stored in internal `BLOB`s

- `Bfile` class to access and read data stored in external LOBs (`BFILE`s)

  **See Also:**

  Syntax information on these classes and details on OCCI in general is available in the[Oracle C++ Call Interface Programmer's Guide](../lncpp/programming-with-lobs.md).

<!-- -->

- Clob Class
- Blob Class
- Bfile Class

**Parent topic:** Using C++ (OCCI) to Work With LOBs

##### 10.5.1.1 Clob Class

The Clob driver implements a `CLOB` object using an SQL LOB locator. This means that a CLOB object contains a logical pointer to the SQL `CLOB` data rather than the data itself.

The `CLOB` interface provides methods for getting the length of an SQL `CLOB` value, for materializing a `CLOB` value on the client, and getting a substring. Methods in the `ResultSet` and `Statement` interfaces such as `getClob()` and `setClob()` allow you to access SQL `CLOB` values.

**See Also:**

[Oracle C++ Call Interface Programmer's Guide](../lncpp/clob-class.md) for detailed information on the Clob class.

**Parent topic:** OCCI Classes for LOBs

##### 10.5.1.2 Blob Class

Methods in the `ResultSet` and `Statement` interfaces, such as `getBlob()` and `setBlob()`, allow you to access SQL `BLOB` values. The `Blob` interface provides methods for getting the length of a SQL `BLOB` value, for materializing a `BLOB` value on the client, and for extracting a part of the `BLOB`.

**See Also:**

- [Oracle C++ Call Interface Programmer's Guide](../lncpp/blob-class.md) for detailed information on the Blob class methods and details on instantiating and initializing a Blob object in your C++ application.

- [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md)for detailed information about implementing applications in different languages.

**Parent topic:** OCCI Classes for LOBs

##### 10.5.1.3 Bfile Class

The `Bfile` class enables you to instantiate a `Bfile` object in your C++ application. You must then use methods of the `Bfile` class, such as the` setName()` method, to initialize the `Bfile` object which associates the object properties with an object of type `BFILE` in a `BFILE` column of the database.

**See Also:**

[Oracle C++ Call Interface Programmer's Guide](../lncpp/bfile-class.md) for detailed information on the `Bfile` class methods and details on instantiating and initializing an `Bfile` object in your C++ application.

**Parent topic:** OCCI Classes for LOBs

#### 10.5.2 Fixed-Width Character Set Rules

In OCCI, for fixed-width client-side character sets, these rules apply:

- `Clob`: offset and amount parameters are always in characters

- `Blob`: offset and amount parameters are always in bytes

- `Bfile`: offset and amount parameters are always in bytes

**Parent topic:** Using C++ (OCCI) to Work With LOBs

#### 10.5.3 Varying-Width Character Set Rules

The following rules apply only to varying-width client-side character sets:

- Offset parameter: Regardless of whether the client-side character set is varying-width, the offset parameter is always as follows:

  - `Clob()`: in characters

  - `Blob()`: in bytes

  - `Bfile()`: in bytes

- Amount parameter: The amount parameter is always as indicated:

  - `Clob`: in characters, when referring to a server-side LOB

  - `Blob`: in bytes, when referring to a client-side buffer

  - `Bfile`: in bytes, when referring to a client-side buffer

- length(): Regardless of whether the client-side character set is varying-width, the output length is as follows:

  - `Clob.length()`: in characters

  - `Blob.length()`: in bytes

  - `Bfile.length()`: in bytes

- Clob.read() and Blob.read(): With client-side character set of varying-width, `CLOB`s and `NCLOB`s:

  - Input amount is in characters. Input amount refers to the number of characters to read from the server-side `CLOB` or `NCLOB`.

  - Output amount is in bytes. Output amount indicates how many bytes were read into the OCCI buffer parameter, `buffer`.

- Clob.write() and Blob.write(): With client-side character set of varying-width, `CLOB`s and `NCLOB`s:

  - Input amount is in bytes. Input amount refers to the number of bytes of data in the OCCI input buffer, `buffer`.

  - Output amount is in characters. Output amount refers to the number of characters written into the server-side `CLOB` or `NCLOB`.

**Parent topic:** Using C++ (OCCI) to Work With LOBs

#### 10.5.4 Offset and Amount Parameters for Other OCCI Operations

For all other OCCI LOB operations, irrespective of the client-side character set, the amount parameter is in characters for `CLOB`s and `NCLOB`s. These include the following:

- `Clob.copy()`

- `Clob.erase()`

- `Clob.trim()`

- For `LoadFromFile` functionality, overloaded `Clob.copy()`

All these operations refer to the amount of LOB data on the server.

**See also:**

[Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md)

- NCLOBs in OCCI

**Parent topic:** Using C++ (OCCI) to Work With LOBs

##### 10.5.4.1 NCLOBs in OCCI

- `NCLOB` instances are allowed as parameters in methods

- `NCLOB` instances are allowed as attributes in object types.

**Parent topic:** Offset and Amount Parameters for Other OCCI Operations

#### 10.5.5 Amount Parameter for OCCI LOB copy() Methods

The `copy()` method on `Clob` and `Blob` enables you to load data from a `BFILE`. You can pass one of the following values for the `amount` parameter to this method:

- An amount smaller than the size of the `BFILE` to load a portion of the data

- An amount equal to the size of the `BFILE` to load all of the data

- The `UB8MAXVAL `constant to load all of the `BFILE` data

You cannot specify an amount larger than the length of the `BFILE`.

**Parent topic:** Using C++ (OCCI) to Work With LOBs

#### 10.5.6 Amount Parameter for OCCI read() Operations

The `read()` method on an `Clob`, `Blob`, or `Bfile` object, reads data from a `BFILE`. You can pass one of these values for the amount parameter to specify the amount of data to read:

- An amount smaller than the size of the `BFILE` to load a portion of the data

- An amount equal to the size of the `BFILE` to load all of the data

- `0` (zero) to read until the end of the `BFILE` in streaming mode

You cannot specify an amount larger than the length of the `BFILE`.

**Parent topic:** Using C++ (OCCI) to Work With LOBs

#### 10.5.7 Further Information About OCCI

**See Also:**

- [Oracle C++ Call Interface Programmer's Guide](../lncpp/blob-class.md)

- [`http://www.oracle.com/`](http://www.oracle.com/) search for articles and product information featuring OCCI.

**Parent topic:** Using C++ (OCCI) to Work With LOBs

#### 10.5.8 OCCI Methods That Operate on BLOBs, BLOBs, NCLOBs, and BFILEs

OCCI methods that operate on `BLOB`s, `CLOB`s, `NCLOB`s, and `BFILE`s are as follows:

- To modify persistent LOBs, see Table 10-15

- To read or examine LOB values, see Table 10-16

- For read only methods on external LOBs (`BFILE`s), see Table 10-17

- Other LOB OCCI methods are described in Table 10-18

- To open and close LOBs, see Table 10-19

**Parent topic:** Using C++ (OCCI) to Work With LOBs

#### 10.5.9 OCCI Methods to Modify Persistent LOB (BLOB, CLOB, and NCLOB) Values

Table 10-15 OCCI Clob and Blob Methods to Modify Persistent LOB (BLOB, CLOB, and NCLOB) Values

| Function/Procedure   | Description                                                      |
|:---------------------|:-----------------------------------------------------------------|
| `Blob/Clob.append()` | Appends `CLOB or BLOB` value to another LOB.                     |
| `Blob/Clob.copy()`   | Copies all or part of a `CLOB` or `BLOB` to another LOB.         |
| `Blob/Clob.copy()`   | Loads `BFILE` data into a persistent LOB.                        |
| `Blob/Clob.trim() `  | Truncates a `CLOB or BLOB`.                                      |
| `Blob/Clob.write()`  | Writes data from a buffer into a LOB, overwriting existing data. |

**Parent topic:** Using C++ (OCCI) to Work With LOBs

#### 10.5.10 OCCI Methods to Read or Examine Persistent LOB and BFILE Values

Table 10-16 OCCI Blob/Clob/Bfile Methods to Read or Examine persistent LOB and BFILE Values

| Function/Procedure         | Description                                                                                                                      |
|:---------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `Blob/Clob.getChunkSize()` | Gets the chunk size used when reading and writing. This works on persistent LOBs and does not apply to external LOBs (`BFILE`s). |
| `Blob/Clob.getOptions()`   | Obtains settings for existing and newly created LOBs.                                                                            |
| `Blob/Clob.length() `      | Returns the length of a LOB or a `BFILE`.                                                                                        |
| `Blob/Clob.read() `        | Reads a specified portion of a non-`NULL` LOB or a `BFILE` into a buffer.                                                        |
| `Blob/Clob.setOptions()`   | Enables LOB settings for existing and newly created LOBs.                                                                        |

**Parent topic:** Using C++ (OCCI) to Work With LOBs

#### 10.5.11 OCCI Read-Only Methods for BFILEs

Table 10-17 OCCI Read-Only Methods for BFILES

| Function/Procedure     | Description                       |
|:-----------------------|:----------------------------------|
| `Bfile.close()`        | Closes an open `BFILE`.           |
| `Bfile.fileExists()`   | Checks whether a `BFILE` exists.  |
| `Bfile.getFileName() ` | Returns the name of a `BFILE`.    |
| `Bfile.getDirAlias()`  | Gets the directory object name.   |
| `Bfile.isOpen()`       | Checks whether a `BFILE` is open. |
| `Bfile.open()`         | Opens a `BFILE`.                  |

**Parent topic:** Using C++ (OCCI) to Work With LOBs

#### 10.5.12 Other OCCI LOB Methods

Table 10-18 Other OCCI LOB Methods

| Methods                            | Description                                                        |
|:-----------------------------------|:-------------------------------------------------------------------|
| `Clob/Blob/Bfile.operator=()`      | Assigns one LOB locator to another. Use = or the copy constructor. |
| `Clob.getCharSetForm() `           | Returns the character set form of a LOB.                           |
| `Clob.getCharSetId()`              | Returns the character set ID of a LOB.                             |
| `Bfile.setName() `                 | Sets the name of a `BFILE`.                                        |
| `Clob/Blob/Bfile.operator==()`     | Checks whether two LOB refer to the same LOB.                      |
| `Clob/Blob/Bfile.isInitialized() ` | Checks whether a LOB is initialized.                               |

**Parent topic:** Using C++ (OCCI) to Work With LOBs

#### 10.5.13 OCCI Methods to Open and Close Internal and External LOBs

Table 10-19 OCCI Methods to Open and Close Internal and External LOBs

| Function/Procedure         | Description           |
|:---------------------------|:----------------------|
| `Clob/Blob/Bfile.Open()`   | Opens a LOB           |
| `Clob/Blob/Bfile.isOpen()` | Sees if a LOB is open |
| `Clob/Blob/Bfile.Close() ` | Closes a LOB          |

**Parent topic:** Using C++ (OCCI) to Work With LOBs

### 10.6 Using C/C++ (Pro\*C) to Work With LOBs

You can make changes to an entire persistent LOB, or to pieces of the beginning, middle or end of a LOB by using embedded SQL. You can access both internal and external LOBs for read purposes, and you can write to persistent LOBs.

Embedded SQL statements allow you to access data stored in `BLOB`s, `CLOB`s, `NCLOB`s, and `BFILE`s. These statements are listed in the following tables, and are discussed in greater detail later in the chapter.

- Providing an Allocated Input Locator Pointer That Represents LOB
- Pro\*C/C++ Statements That Operate on BLOBs, CLOBs, NCLOBs, and BFILEs
- Pro\*C/C++ Embedded SQL Statements to Modify Persistent LOB Values
- Pro\*C/C++ Embedded SQL Statements for Introspection of LOBs
- Pro\*C/C++ Embedded SQL Statements for Temporary LOBs
- Pro\*C/C++ Embedded SQL Statements for BFILEs
- Pro\*C/C++ Embedded SQL Statements for LOB Locators
- Pro\*C/C++ Embedded SQL Statements to Open and Close LOBs

**See Also:**

[Pro\*C/C++ Programmer's Guide](../lnpcc/introduction-and-concepts.md)for detailed documentation, including syntax, host variables, host variable types and example code.

**Parent topic:** Overview of Supplied LOB APIs

#### 10.6.1 Providing an Allocated Input Locator Pointer That Represents LOB

Unlike locators in PL/SQL, locators in Pro\*C/C++ are mapped to locator pointers which are then used to refer to the LOB or BFILE value.

To successfully complete an embedded SQL LOB statement you must do the following:

1.  Provide an allocated input locator pointer that represents a LOB that exists in the database tablespaces or external file system before you run the statement.
2.  SELECT a LOB locator into a LOB locator pointer variable.
3.  Use this variable in the embedded SQL LOB statement to access and manipulate the LOB value.
    **See Also:**

    APIs for supported LOB operations are described in detail in:

    - [Operations Specific to Persistent and Temporary LOBs](operations-specific-to-persistent-and-temporary-LOBs.md)

    - [Using LOB APIs](using-LOB-APIs.md)

    - [LOB APIs for BFILE Operations](LOB-APIs-for-BFILE-operations.md)

**Parent topic:** Using C/C++ (Pro\*C) to Work With LOBs

#### 10.6.2 Pro\*C/C++ Statements That Operate on BLOBs, CLOBs, NCLOBs, and BFILEs

Pro\*C/C++ statements that operate on BLOBs, CLOBs, and NCLOBs are listed in the following tables:

- To modify persistent LOBs, see \*\*INTERNAL XREF ERROR\*\*

- To read or examine LOB values, see \*\*INTERNAL XREF ERROR\*\*

- To create or free temporary LOB, or check if Temporary LOB exists, see \*\*INTERNAL XREF ERROR\*\*

- To operate close and 'see if file exists' functions on BFILEs, see \*\*INTERNAL XREF ERROR\*\*

- To operate on LOB locators, see \*\*INTERNAL XREF ERROR\*\*

- To open or close LOBs or `BFILE`s, see \*\*INTERNAL XREF ERROR\*\*

**Parent topic:** Using C/C++ (Pro\*C) to Work With LOBs

#### 10.6.3 Pro\*C/C++ Embedded SQL Statements to Modify Persistent LOB Values

Table 10-20 Pro\*C/C++: Embedded SQL Statements to Modify Persistent LOB Values

| Statement            | Description                                                     |
|:---------------------|:----------------------------------------------------------------|
| `APPEND`             | Appends a LOB` `value to another LOB.                           |
| `COPY`               | Copies all or a part of a LOB into another LOB.                 |
| `ERASE`              | Erases part of a LOB, starting at a specified offset.           |
| `LOAD` `FROM` `FILE` | Loads `BFILE` data into a persistent LOB at a specified offset. |
| `TRIM`               | Truncates a LOB.                                                |
| `WRITE`              | Writes data from a buffer into a LOB at a specified offset.     |
| `WRITE` `APPEND`     | Writes data from a buffer into a LOB at the end of the LOB.     |

**Parent topic:** Using C/C++ (Pro\*C) to Work With LOBs

#### 10.6.4 Pro\*C/C++ Embedded SQL Statements for Introspection of LOBs

Table 10-21 Pro\*C/C++: Embedded SQL Statements for Introspection of LOBs

| Statement                 | Description                                                                                                                |
|:--------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| `DESCRIBE` `[CHUNKSIZE`\] | Gets the chunk size used when writing. This works for persistent LOBs only. It does not apply to external LOBs (`BFILE`s). |
| `DESCRIBE [LENGTH]`       | Returns the length of a LOB or a `BFILE`.                                                                                  |
| `READ`                    | reads a specified portion of a non-`NULL` LOB or a `BFILE` into a buffer.                                                  |

**Parent topic:** Using C/C++ (Pro\*C) to Work With LOBs

#### 10.6.5 Pro\*C/C++ Embedded SQL Statements for Temporary LOBs

Table 10-22 Pro\*C/C++: Embedded SQL Statements for Temporary LOBs

| Statement                  | Description                                      |
|:---------------------------|:-------------------------------------------------|
| `CREATE` `TEMPORARY`       | Creates a temporary LOB.                         |
| `DESCRIBE` `[ISTEMPORARY]` | Sees if a LOB locator refers to a temporary LOB. |
| `FREE` `TEMPORARY`         | Frees a temporary LOB.                           |

**Parent topic:** Using C/C++ (Pro\*C) to Work With LOBs

#### 10.6.6 Pro\*C/C++ Embedded SQL Statements for BFILEs

Table 10-23 Pro\*C/C++: Embedded SQL Statements for BFILES

| Statement                         | Description                                                  |
|:----------------------------------|:-------------------------------------------------------------|
| `FILE` `CLOSE` `ALL`              | Closes all open `BFILE`s.                                    |
| `DESCRIBE` `[FILEEXISTS]`         | Checks whether a `BFILE` exists.                             |
| `DESCRIBE` `[DIRECTORY,FILENAME]` | Returns the directory object name and filename of a `BFILE`. |

**Parent topic:** Using C/C++ (Pro\*C) to Work With LOBs

#### 10.6.7 Pro\*C/C++ Embedded SQL Statements for LOB Locators

Table 10-24 Pro\*C/C++ Embedded SQL Statements for LOB Locators

| Statement    | Description                                                            |
|:-------------|:-----------------------------------------------------------------------|
| `ASSIGN`     | Assigns one LOB locator to another.                                    |
| `FILE` `SET` | Sets the directory object name and filename of a `BFILE` in a locator. |

**Parent topic:** Using C/C++ (Pro\*C) to Work With LOBs

#### 10.6.8 Pro\*C/C++ Embedded SQL Statements to Open and Close LOBs

Table 10-25 Pro\*C/C++ Embedded SQL Statements to Open and Close Persistent LOBs and External LOBs (BFILEs)

| Statement              | Description                       |
|:-----------------------|:----------------------------------|
| `OPEN`                 | Opens a LOB or `BFILE`.           |
| `DESCRIBE` `[ISOPEN`\] | Sees if a LOB or `BFILE` is open. |
| `CLOSE`                | Closes a LOB or `BFILE`.          |

**Parent topic:** Using C/C++ (Pro\*C) to Work With LOBs

### 10.7 Using COBOL (Pro\*COBOL) to Work With LOBs

You can make changes to an entire persistent LOB, or to pieces of the beginning, middle or end of it by using embedded SQL. You can access both internal and external LOBs for read purposes, and you can also write to persistent LOBs.

Embedded SQL statements allow you to access data stored in `BLOB`s, `CLOB`s, `NCLOB`s, and `BFILE`s. These statements are listed in the following tables, and are discussed in greater detail later in the manual.

- Providing an Allocated Input Locator Pointer That Represents LOB
- Pro\*COBOL Statements That Operate on BLOBs, CLOBs, NCLOBs, and BFILEs
- Pro\*COBOL Embedded SQL Statements to Modify Persistent LOB Values
- Pro\*COBOL Embedded SQL Statements for Introspection of LOBs
- Pro\*COBOL Embedded SQL Statements for Temporary LOBs
- Pro\*COBOL Embedded SQL Statements for BFILEs
- Pro\*COBOL Embedded SQL Statements for LOB Locators
- Pro\*COBOL Embedded SQL Statements for Opening and Closing LOBs and BFILEs

**Parent topic:** Overview of Supplied LOB APIs

#### 10.7.1 Providing an Allocated Input Locator Pointer That Represents LOB

Unlike locators in PL/SQL, locators in Pro\*COBOL are mapped to locator pointers which are then used to refer to the LOB or BFILE value. For the successful completion of an embedded SQL LOB statement you must perform the following:

1.  Provide an allocated input locator pointer that represents a LOB that exists in the database tablespaces or external file system before you run the statement.
2.  SELECT a LOB locator into a LOB locator pointer variable
3.  Use this variable in an embedded SQL LOB statement to access and manipulate the LOB value.
    **See Also:**

    APIs for supported LOB operations are described in detail in:

    - [Operations Specific to Persistent and Temporary LOBs](operations-specific-to-persistent-and-temporary-LOBs.md)

    - [Using LOB APIs](using-LOB-APIs.md)

    - [LOB APIs for BFILE Operations](LOB-APIs-for-BFILE-operations.md)

Where the Pro\*COBOL interface does not supply the required functionality, you can call OCI using C. Such an example is not provided here because such programs are operating system dependent.

**See Also:**

[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for detailed documentation, including syntax, host variables, host variable types, and example code.

**Parent topic:** Using COBOL (Pro\*COBOL) to Work With LOBs

#### 10.7.2 Pro\*COBOL Statements That Operate on BLOBs, CLOBs, NCLOBs, and BFILEs

The following Pro\*COBOL statements operate on BLOBs, CLOBs, NCLOBs, and BFILEs:

- To modify persistent LOBs, see \*\*INTERNAL XREF ERROR\*\*

- To read or examine internal and external LOB values, see \*\*INTERNAL XREF ERROR\*\*

- To create or free temporary LOB, or check LOB locator, see \*\*INTERNAL XREF ERROR\*\*

- To operate close and 'see if file exists' functions on `BFILE`s, see \*\*INTERNAL XREF ERROR\*\*

- To operate on LOB locators, see \*\*INTERNAL XREF ERROR\*\*

- To open or close persistent LOBs or `BFILE`s, see \*\*INTERNAL XREF ERROR\*\*

**Parent topic:** Using COBOL (Pro\*COBOL) to Work With LOBs

#### 10.7.3 Pro\*COBOL Embedded SQL Statements to Modify Persistent LOB Values

Table 10-26 Pro\*COBOL Embedded SQL Statements to Modify LOB Values

| Statement            | Description                                                     |
|:---------------------|:----------------------------------------------------------------|
| `APPEND`             | Appends a LOB` `value to another LOB.                           |
| `COPY`               | Copies all or part of a LOB into another LOB.                   |
| `ERASE`              | Erases part of a LOB, starting at a specified offset.           |
| `LOAD` `FROM` `FILE` | Loads `BFILE` data into a persistent LOB at a specified offset. |
| `TRIM`               | Truncates a LOB.                                                |
| `WRITE`              | Writes data from a buffer into a LOB at a specified offset      |
| `WRITE` `APPEND`     | Writes data from a buffer into a LOB at the end of the LOB.     |

**Parent topic:** Using COBOL (Pro\*COBOL) to Work With LOBs

#### 10.7.4 Pro\*COBOL Embedded SQL Statements for Introspection of LOBs

Table 10-27 Pro\*COBOL Embedded SQL Statements for Introspection of LOBs

| Statement                | Description                                                               |
|:-------------------------|:--------------------------------------------------------------------------|
| `DESCRIBE` `[CHUNKSIZE]` | Gets the Chunk size used when writing.                                    |
| `DESCRIBE` `[LENGTH]`    | Returns the length of a LOB or a `BFILE`.                                 |
| `READ`                   | Reads a specified portion of a non-`NULL` LOB or a `BFILE` into a buffer. |

**Parent topic:** Using COBOL (Pro\*COBOL) to Work With LOBs

#### 10.7.5 Pro\*COBOL Embedded SQL Statements for Temporary LOBs

Table 10-28 Pro\*COBOL Embedded SQL Statements for Temporary LOBs

| Statement                  | Description                                      |
|:---------------------------|:-------------------------------------------------|
| `CREATE` `TEMPORARY`       | Creates a temporary LOB.                         |
| `DESCRIBE` `[ISTEMPORARY]` | Sees if a LOB locator refers to a temporary LOB. |
| `FREE` `TEMPORARY`         | Frees a temporary LOB.                           |

**Parent topic:** Using COBOL (Pro\*COBOL) to Work With LOBs

#### 10.7.6 Pro\*COBOL Embedded SQL Statements for BFILEs

Table 10-29 Pro\*COBOL Embedded SQL Statements for BFILES

| Statement                          | Description                                                  |
|:-----------------------------------|:-------------------------------------------------------------|
| `FILE` `CLOSE` `ALL`               | Closes all open `BFILE`s.                                    |
| `DESCRIBE` `[FILEEXISTS]`          | Checks whether a `BFILE` exists.                             |
| `DESCRIBE` `[DIRECTORY, FILENAME]` | Returns the directory object name and filename of a `BFILE`. |

**Parent topic:** Using COBOL (Pro\*COBOL) to Work With LOBs

#### 10.7.7 Pro\*COBOL Embedded SQL Statements for LOB Locators

Table 10-30 Pro\*COBOL Embedded SQL Statements for LOB Locator Statements

| Statement    | Description                                                            |
|:-------------|:-----------------------------------------------------------------------|
| `ASSIGN`     | Assigns one LOB locator to another.                                    |
| `FILE` `SET` | Sets the directory object name and filename of a `BFILE` in a locator. |

**Parent topic:** Using COBOL (Pro\*COBOL) to Work With LOBs

#### 10.7.8 Pro\*COBOL Embedded SQL Statements for Opening and Closing LOBs and BFILEs

Table 10-31 Pro\*COBOL Embedded SQL Statements for Opening and Closing Persistent LOBs and BFILEs

| Statement             | Description                       |
|:----------------------|:----------------------------------|
| `OPEN`                | Opens a LOB or `BFILE`.           |
| `DESCRIBE` `[ISOPEN]` | Sees if a LOB or `BFILE` is open. |
| `CLOSE`               | Closes a LOB or `BFILE`.          |

**Parent topic:** Using COBOL (Pro\*COBOL) to Work With LOBs

### 10.8 Using Java (JDBC) to Work With LOBs

You can perform the following tasks on LOBs with Java (JDBC):

- Modifying Internal Persistent LOBs Using Java

- Reading Internal Persistent LOBs and External LOBs (BFILEs) With Java

- Calling DBMS_LOB Package from Java (JDBC)

- Referencing LOBs Using Java (JDBC)

- Create and Manipulate Temporary LOBs and Store Them in Tables as Permanent LOBs. See JDBC Temporary LOB APIs

<!-- -->

- Modifying Internal Persistent LOBs Using Java
- Reading Internal Persistent LOBs and External LOBs (BFILEs) With Java
- Calling DBMS_LOB Package from Java (JDBC)
- Prefetching LOBs to Improve Performance
- Zero-Copy Input/Output for SecureFiles to Improve Performance
- Referencing LOBs Using Java (JDBC)
- JDBC Syntax References and Further Information
- JDBC Methods for Operating on LOBs
- JDBC oracle.sql.BLOB Methods to Modify BLOB Values
- JDBC oracle.sql.BLOB Methods to Read or Examine BLOB Values
- JDBC oracle.sql.BLOB Methods and Properties for Streaming BLOB Data
- JDBC oracle.sql.CLOB Methods to Modify CLOB Values
- JDBC oracle.sql.CLOB Methods to Read or Examine CLOB Value
- JDBC oracle.sql.CLOB Methods and Properties for Streaming CLOB Data
- JDBC oracle.sql.BFILE Methods to Read or Examine External LOB (BFILE) Values
- JDBC oracle.sql.BFILE Methods and Properties for Streaming BFILE Data
- JDBC Temporary LOB APIs
- JDBC: Opening and Closing LOBs
- JDBC: Opening and Closing BLOBs
- JDBC: Opening and Closing CLOBs
- JDBC: Opening and Closing BFILEs
- Truncating LOBs Using JDBC
- JDBC BLOB Streaming APIs
- JDBC CLOB Streaming APIs
- BFILE Streaming APIs
- JDBC and Empty LOBs

**Parent topic:** Overview of Supplied LOB APIs

#### 10.8.1 Modifying Internal Persistent LOBs Using Java

You can make changes to an entire persistent LOB, or to pieces of the beginning, middle, or end of a persistent LOB in Java by means of the JDBC API using the classes:

- `oracle`.`sql`.`BLOB`

- `oracle`.`sql`.`CLOB`

These classes implement `java.sql.Blob` and `java.sql.Clob` interfaces according to the JDBC 3.0 specification, which has methods for LOB modification. They also include legacy Oracle proprietary methods for LOB modification. These legacy methods are marked as deprecated.

Starting in Oracle Database Release 11.1, the minimum supported version of the JDK is JDK5. To use JDK5, place `ojdbc5.jar` in your `CLASSPATH`. To use JDK6, place `ojdbc6.jar` in your `CLASSPATH`. `ojdbc5.jar` supports the JDBC 3.0 specification and `ojdbc6.jar` supports the JDBC4.0 specification which is new with JDK6.

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.2 Reading Internal Persistent LOBs and External LOBs (BFILEs) With Java

With JDBC you can use Java to read both internal persistent LOBs and external LOBs (`BFILE`s).

- BLOB, CLOB, and BFILE Classes

**Parent topic:** Using Java (JDBC) to Work With LOBs

##### 10.8.2.1 BLOB, CLOB, and BFILE Classes

- `BLOB` and `CLOB` Classes: In JDBC theses classes provide methods for performing operations on large objects in the database including `BLOB` and `CLOB` data types.

- `BFILE` Class: In JDBC this class provides methods for performing operations on `BFILE` data in the database.

The `BLOB`, `CLOB`, and `BFILE` classes encapsulate LOB locators, so you do not deal with locators but instead use methods and properties provided to perform operations and get state information.

**Parent topic:** Reading Internal Persistent LOBs and External LOBs (BFILEs) With Java

#### 10.8.3 Calling DBMS_LOB Package from Java (JDBC)

Any LOB functionality not provided by these classes can be accessed by a call to the` `PL/SQL `DBMS_LOB` package. This technique is used repeatedly in the examples throughout this manual.

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.4 Prefetching LOBs to Improve Performance

The number of server round trips can be reduced by prefetching part of the data and metadata (length and chunk size) along with the LOB locator during the fetch.

The `SELECT` parse, execution, and fetch occurs in one round trip. For large LOBs (larger than five times the prefetch size) less improvement is seen.

To configure the prefetch size, a connection property, `oracle.jdbc.defaultLobPrefetchSize`, defined as a constant in `oracle.jdbc.OracleConnection` can be used. Values can be -1 to disable prefetching, 0 to enable prefetching for metadata only, or any value greater than 0 which represents the number of bytes for `BLOB`s and characters for `CLOB`s, to be prefetched along with the locator during fetch operations.

You can change the prefetch size for a particular statement by using a method defined in `oracle.jdbc.OracleStatement`:

    void setLobPrefetchSize(int size) throws SQLException;

The statement level setting overrides the setting at the connection level. This setting can also be overriden at the column level through the extended `defineColumnType` method, where the size represents the number of bytes (or characters for `CLOB`) to prefetch. The possible values are the same as for the connection property. The type must be set to `OracleTypes.CLOB` for a `CLOB` column and `OracleTypes.BLOB` for a `BLOB` column. This method throws `SQLException` if the value is less than -1. To complement the statement there is in `oracle.jdbc.OracleStatement`:

    int getLobPrefetchSize();

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.5 Zero-Copy Input/Output for SecureFiles to Improve Performance

To improve the performance of SecureFiles, there is a Zero-copy Input/Output protocol on the server that is only available to network clients that support the new Net NS Data transfer protocol.

To determine if a LOB is a SecureFiles or not, use the method

    public boolean isSecureFile() throws SQLException

If it is a SecureFiles, `TRUE` is returned.

Use this thin connection property to disable (by setting to `FALSE`) the Zero-copy Input/Output protocol:

    oracle.net.useZeroCopyIO

- Zero-Copy Input/Output on the Server
- Zero-Copy Input/Output in the JDBC Thin Driver
- JDBC-OCI Driver Considerations

**Parent topic:** Using Java (JDBC) to Work With LOBs

##### 10.8.5.1 Zero-Copy Input/Output on the Server

Oracle Net Services is now able to use data buffers provided by the users of Oracle Net Services without transferring the data into or out of its local buffers.

The network buffers (at the NS layer) are bypassed and internal lob buffers are directly written on the network. The same applies to buffer reads.

This feature is only available to network clients that support the new NS Data packet (this is negotiated during the NS handshake). The thin driver supports the new NS protocol so that the server can use the zero-copy protocol and JavaNet exposes the zero-copy IO mechanism to the upper layer so that data copies are no longer required in the thin driver code.

**Parent topic:** Zero-Copy Input/Output for SecureFiles to Improve Performance

##### 10.8.5.2 Zero-Copy Input/Output in the JDBC Thin Driver

When you call the `BLOB.getBytes(long pos, int length, byte[] buffer)` API, the buffer provided is used at the JavaNet layer to read the bytes from the socket.

The data is retrieved in one single round trip. Similarly, during a write operation, when you call `BLOB.setBytes(long pos, byte[] bytes)`, the buffer is directly written on the network at the JavaNet layer. So the data is written in one single round trip. The user buffer is sent as a whole.

**Parent topic:** Zero-Copy Input/Output for SecureFiles to Improve Performance

##### 10.8.5.3 JDBC-OCI Driver Considerations

The JDBC-OCI driver supports Zero-copy Input/Output in the server and in the network layer.

**Parent topic:** Zero-Copy Input/Output for SecureFiles to Improve Performance

#### 10.8.6 Referencing LOBs Using Java (JDBC)

You can get a reference to any of the preceding LOBs in the following two ways:

- As a column of an `OracleResultSet`

- As an `OUT` type PL/SQL parameter from an `OraclePreparedStatement`

<!-- -->

- Using OracleResultSet: BLOB and CLOB Objects Retrieved

**Parent topic:** Using Java (JDBC) to Work With LOBs

##### 10.8.6.1 Using OracleResultSet: BLOB and CLOB Objects Retrieved

When `BLOB` and `CLOB` objects are retrieved as a part of an `OracleResultSet`, these objects represent LOB locators of the currently selected row.

If the current row changes due to a move operation, for example, `rset`.`next`(), then the retrieved locator still refers to the original LOB row.

To retrieve the locator for the most current row, you must call `getBLOB()`, `getCLOB()`, or `getBFILE()` on the `OracleResultSet` each time a move operation is made depending on whether the instance is a `BLOB`, `CLOB` or `BFILE`.

**Parent topic:** Referencing LOBs Using Java (JDBC)

#### 10.8.7 JDBC Syntax References and Further Information

For further JDBC syntax and information about using JDBC with LOBs:

**See Also:**

- [Oracle Database JDBC Developer's Guide,](../jjdbc/LOBs-and-BFiles.md)for detailed documentation, including parameters, parameter types, return values, and example code.

- [`http://www.oracle.com/technology/`](http://www.oracle.com/technology/)

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.8 JDBC Methods for Operating on LOBs

The following JDBC methods operate on `BLOB`s, `CLOB`s, and `BFILE`s:

- `BLOB`s:

  - To modify `BLOB` values, see \*\*INTERNAL XREF ERROR\*\*

  - To read or examine `BLOB` values, see \*\*INTERNAL XREF ERROR\*\*

  - For streaming `BLOB` data, see Table 10-34

  - Temporary `BLOB`s: Creating, checking if `BLOB` is open, and freeing. See \*\*INTERNAL XREF ERROR\*\*

  - Opening, closing, and checking if `BLOB` is open, see \*\*INTERNAL XREF ERROR\*\*

  - Truncating `BLOB`s, see \*\*INTERNAL XREF ERROR\*\*

  - `BLOB` streaming API, see \*\*INTERNAL XREF ERROR\*\*

- `CLOB`s:

  - To read or examine `CLOB` values, see \*\*INTERNAL XREF ERROR\*\*

  - For streaming `CLOB` data, see Table 10-37

  - To modify `CLOB`s, see \*\*INTERNAL XREF ERROR\*\*

- Temporary `CLOB`s:

  - Opening, closing, and checking if `CLOB` is open, see \*\*INTERNAL XREF ERROR\*\*

  - Truncating `CLOB`s, see \*\*INTERNAL XREF ERROR\*\*

  - `CLOB` streaming API, see \*\*INTERNAL XREF ERROR\*\*

- `BFILE`s:

  - To read or examine `BFILE`s, see \*\*INTERNAL XREF ERROR\*\*

  - For streaming `BFILE` data, see Table 10-39

  - Opening, closing, and checking if `BFILE` is open, see \*\*INTERNAL XREF ERROR\*\*

  - BFILE streaming API, see \*\*INTERNAL XREF ERROR\*\*

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.9 JDBC oracle.sql.BLOB Methods to Modify BLOB Values

Table 10-32 JDBC oracle.sql.BLOB Methods To Modify BLOB Values

| Method                       | Description                                                          |
|:-----------------------------|:---------------------------------------------------------------------|
| `int setBytes(long, byte[])` | Inserts the byte array into the `BLOB`, starting at the given offset |

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.10 JDBC oracle.sql.BLOB Methods to Read or Examine BLOB Values

Table 10-33 JDBC oracle.sql.BLOB Methods to Read or Examine BLOB Values

| Method                                    | Description                                                        |
|:------------------------------------------|:-------------------------------------------------------------------|
| `byte[] getBytes(long, int)`              | Gets the contents of the LOB as an array of bytes, given an offset |
| `long position(byte[],long)`              | Finds the given byte array within the LOB, given an offset         |
| `long position(Blob,long)`                | Finds the given `BLOB` within the LOB                              |
| `public boolean equals(java.lang.Object)` | Compares this LOB with another. Compares the LOB locators.         |
| `public long length()`                    | Returns the length of the LOB                                      |
| `public int getChunkSize()`               | Returns the `ChunkSize` of the LOB                                 |

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.11 JDBC oracle.sql.BLOB Methods and Properties for Streaming BLOB Data

Table 10-34 JDBC oracle.sql.BLOB Methods and Properties for Streaming BLOB Data

| Method                                          | Description                                                                                         |
|:------------------------------------------------|:----------------------------------------------------------------------------------------------------|
| `public java.io.InputStream getBinaryStream())` | Streams the LOB as a binary stream                                                                  |
| `public java.io.OutputStream setBinaryStream()` | Retrieves a stream that can be used to write to the `BLOB` value that this `Blob` object represents |

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.12 JDBC oracle.sql.CLOB Methods to Modify CLOB Values

Table 10-35 JDBC oracle.sql.CLOB Methods to Modify CLOB Values

| Method                                  | Description                                                                                                          |
|:----------------------------------------|:---------------------------------------------------------------------------------------------------------------------|
| `int setString(long, java.lang.String)` | JDBC 3.0: Writes the given Java String to the `CLOB` value that this `Clob` object designates at the position `pos`. |
| `int putChars(long, char[])`            | Inserts the character array into the LOB, starting at the given offset                                               |

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.13 JDBC oracle.sql.CLOB Methods to Read or Examine CLOB Value

Table 10-36 JDBC oracle.sql.CLOB Methods to Read or Examine CLOB Values

| Method                                     | Description                                            |
|:-------------------------------------------|:-------------------------------------------------------|
| `java.lang.String getSubString(long, int)` | Returns a substring of the LOB as a string             |
| `int getChars(long, int, char[])`          | Reads a subset of the LOB into a character array       |
| `long position(java.lang.String, long)`    | Finds the given String within the LOB, given an offset |
| `long position(oracle.jdbc2.Clob, long)`   | Finds the given `CLOB` within the LOB, given an offset |
| `long length()`                            | Returns the length of the LOB                          |
| `int getChunkSize()`                       | R`eturns the ChunkSize` of the LOB                     |

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.14 JDBC oracle.sql.CLOB Methods and Properties for Streaming CLOB Data

Table 10-37 JDBC oracle.sql.CLOB Methods and Properties for Streaming CLOB Data

| Method                                          | Description                                                                                                                                            |
|:------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `java.io.InputStream getAsciiStream()`          | Implements the `Clob` interface method. Gets the `CLOB` value designated by this `Clob` object as a stream of ASCII bytes                              |
| `java.io.OutputStream setAsciiStream(long pos)` | JDBC 3.0: Retrieves a stream to be used to write ASCII characters to the `CLOB` value that this `Clob` object represents, starting at position `pos`   |
| `java.io.Reader getCharacterStream()`           | Reads the `CLOB` as a character stream                                                                                                                 |
| `java.io.Writer setCharacterStream(long pos)`   | JDBC 3.0: Retrieves a stream to be used to write Unicode characters to the `CLOB` value that this `Clob` object represents, starting at position `pos` |

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.15 JDBC oracle.sql.BFILE Methods to Read or Examine External LOB (BFILE) Values

Table 10-38 JDBC oracle.sql.BFILE Methods to Read or Examine External LOB (BFILE) Values

| Method                                  | Description                                                                                    |
|:----------------------------------------|:-----------------------------------------------------------------------------------------------|
| `byte[] getBytes(long, int)`            | `G`ets the contents of the `BFILE` as an array of bytes, given an offset                       |
| `int getBytes(long, int, byte[])`       | Reads a subset of the `BFILE` into a byte array                                                |
| `long position(oracle.sql.BFILE, long)` | Finds the first appearance of the given `BFILE` contents within the LOB, from the given offset |
| `long position(byte[], long)`           | Finds the first appearance of the given byte array within the `BFILE`, from the given offset   |
| `long length()`                         | R`eturns the length of the BFILE`                                                              |
| `boolean fileExists()`                  | Checks if the operating system file referenced by this `BFILE` exists                          |
| `public void openFile()`                | Opens the operating system file referenced by this `BFILE`                                     |
| `public void closeFile()`               | C`loses the operating system file referenced by this BFILE`                                    |
| `public boolean isFileOpen()`           | Checks if this `BFILE` is open                                                                 |
| `public java.lang.String getDirAlias()` | G`ets the directory object name for this BFILE`                                                |
| `public java.lang.String getName()`     | G`ets the file name referenced by this BFILE`                                                  |

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.16 JDBC oracle.sql.BFILE Methods and Properties for Streaming BFILE Data

Table 10-39 JDBC oracle.sql.BFILE Methods and Properties for Streaming BFILE Data

| Method                                         | Description                          |
|:-----------------------------------------------|:-------------------------------------|
| `public java.io.InputStream getBinaryStream()` | Reads` the BFILE` as a binary stream |

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.17 JDBC Temporary LOB APIs

Oracle Database JDBC drivers contain APIs to create and close temporary LOBs. These APIs can replace workarounds that use the following procedures from the `DBMS_LOB` PL/SQL package in prior releases:

- `DBMS_LOB.createTemporary()`

- `DBMS_LOB.isTemporary()`

- `DBMS_LOB.freeTemporary()`

Table 10-40 JDBC: Temporary BLOB APIs

| Methods                                                                                                     | Description                                                         |
|:------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------|
| `public static BLOB createTemporary(Connection conn,`<br>`boolean cache, int duration) throws SQLException` | Creates a temporary `BLOB`                                          |
| `public static boolean isTemporary(BLOB blob) `<br>`throws SQLException`                                    | Checks if the specified `BLOB` locator refers to a temporary `BLOB` |
| `public boolean isTemporary() throws SQLException`                                                          | Checks if the current `BLOB` locator refers to a temporary `BLOB`   |
| `public static void freeTemporary(BLOB temp_blob)`<br>`throws SQLException`                                 | Frees the specified temporary `BLOB`                                |
| `public void freeTemporary() throws SQLException`                                                           | Frees the temporary `BLOB`                                          |

Table 10-41 JDBC: Temporary CLOB APIs

| Methods                                                                                                     | Description                                                         |
|:------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------|
| `public static CLOB createTemporary(Connection conn,`<br>`boolean cache, int duration) throws SQLException` | Creates a temporary `CLOB`                                          |
| `public static boolean isTemporary(CLOB clob)`<br>`throws SQLException`                                     | Checks if the specified `CLOB` locator refers to a temporary `CLOB` |
| `public boolean isTemporary() throws SQLException`                                                          | Checks if the current `CLOB` locator refers to a temporary `CLOB`   |
| `public static void freeTemporary(CLOB temp_clob)`<br>`throws SQLException`                                 | Frees the specified temporary `CLOB`                                |
| `public void freeTemporary() throws SQLException`                                                           | Frees the temporary `CLOB`                                          |

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.18 JDBC: Opening and Closing LOBs

`oracle.sql.CLOB` class is the Oracle JDBC driver implementation of standard JDBC `java.sql.Clob` interface. Table 10-41 lists the Oracle extension APIs in `oracle.sql.CLOB` for accessing temporary CLOBs.

Oracle Database JDBC drivers contain APIs to explicitly open and close LOBs. These APIs replace previous techniques that use `DBMS_LOB.open()` and `DBMS_LOB.close()`.

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.19 JDBC: Opening and Closing BLOBs

`oracle.sql.BLOB` class is the Oracle JDBC driver implementation of standard JDBC java.sql.Blob interface. Table 10-42 lists the Oracle extension APIs in `oracle.sql.BLOB` that open and close BLOBs.

Table 10-42 JDBC: Opening and Closing BLOBs

| Methods                                          | Description                |
|:-------------------------------------------------|:---------------------------|
| `public void open(int mode) throws SQLException` | Opens the `BLOB`           |
| `public boolean isOpen() throws SQLException`    | Sees if the `BLOB` is open |
| `public void close() throws SQLException`        | Closes the `BLOB`          |

- Opening the BLOB Using JDBC
- Checking If the BLOB Is Open Using JDBC
- Closing the BLOB Using JDBC

**Parent topic:** Using Java (JDBC) to Work With LOBs

##### 10.8.19.1 Opening the BLOB Using JDBC

To open a `BLOB`, your JDBC application can use the open method as defined in `oracle.sql.BLOB` class as follows:

    /**
     * Open a BLOB in the indicated mode. Valid modes include MODE_READONLY,
     * and MODE_READWRITE. It is an error to open the same LOB twice.
     */
    public void open (int mode) throws SQLException

Possible values of the mode parameter are:

    public static final int MODE_READONLY
    public static final int MODE_READWRITE

Each call to open opens the BLOB. For example:

    BLOB blob = ...
    blob.open (BLOB.MODE_READWRITE);

**Parent topic:** JDBC: Opening and Closing BLOBs

##### 10.8.19.2 Checking If the BLOB Is Open Using JDBC

To see if a `BLOB` is opened, your JDBC application can use the `isOpen` method defined in oracle.sql.BLOB. The return Boolean value indicates whether the `BLOB` has been previously opened or not. The `isOpen` method is defined as follows:

    /**
     * Check whether the BLOB is opened.
     * @return true if the LOB is opened.
     */
     public boolean isOpen () throws SQLException

The usage example is:

    BLOB blob = ...
    // See if the BLOB is opened
    boolean isOpen = blob.isOpen ();

**Parent topic:** JDBC: Opening and Closing BLOBs

##### 10.8.19.3 Closing the BLOB Using JDBC

To close a BLOB, your JDBC application can use the close method defined in `oracle.sql.BLOB`. The close API is defined as follows:

    /**
      * Close a previously opened BLOB.
      */
    public void close () throws SQLException

The usage example is:

    BLOB blob = ...
    // close the BLOB
    blob.close ();

**Parent topic:** JDBC: Opening and Closing BLOBs

#### 10.8.20 JDBC: Opening and Closing CLOBs

Class `oracle.sql.CLOB` is the Oracle JDBC driver implementation of the standard JDBC `java.sql.Clob` interface. Table 10-43 lists the Oracle extension APIs in `oracle.sql.CLOB` to open and close `CLOB`s.

Table 10-43 JDBC: Opening and Closing CLOBs

| Methods                                          | Description                 |
|:-------------------------------------------------|:----------------------------|
| `public void open(int mode) throws SQLException` | Open the `CLOB`             |
| `public boolean isOpen() throws SQLExceptio`n    | See if the `CLOB` is opened |
| `public void close() throws SQLException`        | Close the `CLOB`            |

- Opening the CLOB Using JDBC
- Checking If the CLOB Is Open Using JDBC
- Closing the CLOB Using JDBC

**Parent topic:** Using Java (JDBC) to Work With LOBs

##### 10.8.20.1 Opening the CLOB Using JDBC

To open a `CLOB`, your JDBC application can use the open method defined in `oracle.sql.CLOB` class as follows:

    /**
     * Open a CLOB in the indicated mode. Valid modes include MODE_READONLY,
     * and MODE_READWRITE. It is an error to open the same LOB twice.
     */
    public void open (int mode) throws SQLException

The possible values of the mode parameter are:

    public static final int MODE_READONLY
    public static final int MODE_READWRITE

Each call to open opens the `CLOB`. For example,

    CLOB clob = ...
    clob.open (CLOB.MODE_READWRITE);

**Parent topic:** JDBC: Opening and Closing CLOBs

##### 10.8.20.2 Checking If the CLOB Is Open Using JDBC

To see if a `CLOB` is opened, your JDBC application can use the `isOpen` method defined in oracle.sql.CLOB. The return Boolean value indicates whether the `CLOB` has been previously opened or not. The `isOpen` method is defined as follows:

    /**
      * Check whether the CLOB is opened.
      * @return true if the LOB is opened.
      */
    public boolean isOpen () throws SQLException

The usage example is:

    CLOB clob = ...
     // See if the CLOB is opened
     boolean isOpen = clob.isOpen ();

**Parent topic:** JDBC: Opening and Closing CLOBs

##### 10.8.20.3 Closing the CLOB Using JDBC

To close a `CLOB`, the JDBC application can use the close method defined in `oracle.sql.CLOB`. The close API is defined as follows:

    /**
    * Close a previously opened CLOB.
    */
    public void close () throws SQLException

The usage example is:

    CLOB clob = ...
    // close the CLOB
    clob.close ();

**Parent topic:** JDBC: Opening and Closing CLOBs

#### 10.8.21 JDBC: Opening and Closing BFILEs

`oracle.sql.BFILE` class wraps the database `BFILE` object. Table 10-44 lists the Oracle extension APIs in `oracle.sql.BFILE` for opening and closing `BFILE`s.

Table 10-44 JDBC API Extensions for Opening and Closing BFILEs

| Methods                                          | Description                   |
|:-------------------------------------------------|:------------------------------|
| `public void open() throws SQLException`         | Opens the `BFILE`             |
| `public void open(int mode) throws SQLException` | Opens the `BFILE`             |
| `public boolean isOpen() throws SQLException`    | Checks if the `BFILE` is open |
| `public void close() throws SQLException`        | Closes the `BFILE`            |

- Opening BFILEs
- Checking If the BFILE Is Open
- Closing the BFILE
- Usage Example (OpenCloseLob.java)

**Parent topic:** Using Java (JDBC) to Work With LOBs

##### 10.8.21.1 Opening BFILEs

To open a `BFILE`, your JDBC application can use the `OPEN` method defined in `oracle.sql.BFILE` class as follows:

    /**
     * Open a external LOB in the read-only mode. It is an error
     * to open the same LOB twice.
     */
    public void open () throws SQLException

    /**
     * Open a external LOB in the indicated mode. Valid modes include
     * MODE_READONLY only. It is an error to open the same
     * LOB twice.
     */
    public void open (int mode) throws SQLException

The only possible value of the mode parameter is:

    public static final int MODE_READONLY

Each call to open opens the `BFILE`. For example,

    BFILE bfile = ...
    bfile.open ();

**Parent topic:** JDBC: Opening and Closing BFILEs

##### 10.8.21.2 Checking If the BFILE Is Open

To see if a `BFILE` is opened, your JDBC application can use the `isOpen` method defined in `oracle.sql.BFILE`. The return Boolean value indicates whether the BFILE has been previously opened or not. The `isOpen` method is defined as follows:

    /**
     * Check whether the BFILE is opened.
     * @return true if the LOB is opened.
     */
    public boolean isOpen () throws SQLException

The usage example is:

    BFILE bfile = ...
    // See if the BFILE is opened
    boolean isOpen = bfile.isOpen ();

**Parent topic:** JDBC: Opening and Closing BFILEs

##### 10.8.21.3 Closing the BFILE

To close a `BFILE`, your JDBC application can use the `close` method defined in `oracle.sql.BFILE`. The `close` API is defined as follows:

    /**
     * Close a previously opened BFILE.
    */
    public void close () throws SQLException

The usage example is --

    BFILE bfile = ...
    // close the BFILE
    bfile.close ();

**Parent topic:** JDBC: Opening and Closing BFILEs

##### 10.8.21.4 Usage Example (OpenCloseLob.java)

    /*
     * This sample shows how to open/close BLOB and CLOB.
     */

    // You must import the java.sql package to use JDBC
    import java.sql.*;

    // You must import the oracle.sql package to use oracle.sql.BLOB
    import oracle.sql.*;

    class OpenCloseLob
    {
      public static void main (String args [])
           throws SQLException
      {
        // Load the Oracle JDBC driver
        DriverManager.registerDriver(new oracle.jdbc.driver.OracleDriver());

        String url = "jdbc:oracle:oci8:@";
        try {
          String url1 = System.getProperty("JDBC_URL");
          if (url1 != null)
            url = url1;
        } catch (Exception e) {
          // If there is any security exception, ignore it
          // and use the default
        }

        // Connect to the database
        Connection conn =
          DriverManager.getConnection (url, "scott", "password");
        // It is faster when auto commit is off
        conn.setAutoCommit (false);

        // Create a Statement
        Statement stmt = conn.createStatement ();

        try
        {
          stmt.execute ("drop table basic_lob_table");
        }
        catch (SQLException e)
        {
          // An exception could be raised here if the table did not exist.
        }

    // Create a table containing a BLOB and a CLOB
    stmt.execute ("create table basic_lob_table (x varchar2 (30), b blob, c clob)");

    // Populate the table
    stmt.execute (
        "insert into basic_lob_table values"
        + " ('one', '010101010101010101010101010101', 'onetwothreefour')");

        // Select the lobs
        ResultSet rset = stmt.executeQuery ("select * from basic_lob_table");
        while (rset.next ())
        {
          // Get the lobs
          BLOB blob = (BLOB) rset.getObject (2);
          CLOB clob = (CLOB) rset.getObject (3);

          // Open the lobs
          System.out.println ("Open the lobs");
          blob.open (BLOB.MODE_READWRITE);
          clob.open (CLOB.MODE_READWRITE);

          // Check if the lobs are opened
          System.out.println ("blob.isOpen()="+blob.isOpen());
          System.out.println ("clob.isOpen()="+clob.isOpen());

          // Close the lobs
          System.out.println ("Close the lobs");
          blob.close ();
          clob.close ();

          // Check if the lobs are opened
          System.out.println ("blob.isOpen()="+blob.isOpen());
          System.out.println ("clob.isOpen()="+clob.isOpen());
        }

        // Close the ResultSet
        rset.close ();

        // Close the Statement
        stmt.close ();

        // Close the connection
        conn.close ();
      }
    }

**Parent topic:** JDBC: Opening and Closing BFILEs

#### 10.8.22 Truncating LOBs Using JDBC

Oracle Database JDBC drivers contain APIs to truncate persistent LOBs. These APIs replace previous techniques that used `DBMS_LOB.trim()`.

- JDBC: Truncating BLOBs
- JDBC: Truncating CLOBs

**Parent topic:** Using Java (JDBC) to Work With LOBs

##### 10.8.22.1 JDBC: Truncating BLOBs

`oracle.sql.BLOB` class is Oracle JDBC driver implementation of the standard JDBC `java.sql.Blob` interface. Table 10-45 lists the Oracle extension API in `oracle.sql.BLOB` that truncates BLOBs.

Table 10-45 JDBC: Truncating BLOBs

| Methods                                                 | Description          |
|:--------------------------------------------------------|:---------------------|
| `public void truncate(long newlen) throws SQLException` | Truncates the `BLOB` |

The truncate API is defined as follows:

    /**
    *Truncate the value of the BLOB to the length you specify in the newlen parameter.
     * @param newlen the new length of the BLOB.
     */
    public void truncate (long newlen) throws SQLException

The `newlen` parameter specifies the new length of the `BLOB`.

**Parent topic:** Truncating LOBs Using JDBC

##### 10.8.22.2 JDBC: Truncating CLOBs

`oracle.sql.CLOB` class is the Oracle JDBC driver implementation of standard JDBC `java.sql.Clob` interface. Table 10-46 lists the Oracle extension API in `oracle.sql.CLOB` that truncates `CLOB`s.

Table 10-46 JDBC: Truncating CLOBs

| Methods                                                 | Description          |
|:--------------------------------------------------------|:---------------------|
| `public void truncate(long newlen) throws SQLException` | Truncates the `CLOB` |

The truncate API is defined as follows:

    /**
    *Truncate the value of the CLOB to the length you specify in the newlen parameter.
     * @param newlen the new length of the CLOB.
     */
    public void truncate (long newlen) throws SQLException

The `newlen` parameter specifies the new length of the `CLOB`.

**See:**

"[About Trimming LOB Data](using-LOB-APIs.md)", for an example.

**Parent topic:** Truncating LOBs Using JDBC

#### 10.8.23 JDBC BLOB Streaming APIs

The JDBC interface provided with the database includes LOB streaming APIs that enable you to read from or write to a LOB at the requested position from a Java stream.

The `oracle.sql.BLOB` class implements the standard JDBC `java.sql.Blob` interface. Table 10-47 lists BLOB Streaming APIs.

Table 10-47 JDBC: BLOB Streaming APIs

| Methods                                                                              | Description                                                                                                                                   |
|:-------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `public java.io.OutputStream`<br>` setBinaryStream (long pos) ``throws SQLException` | JDBC 3.0: Retrieves a stream that can be used to write to the `BLOB` value that this `Blob` object represents, starting at position `pos`     |
| `public java.io.InputStream `<br>` getBinaryStream()` `throws SQLException`          | JDBC 3.0: Retrieves a stream that can be used to read the `BLOB` value that this `Blob` object represents, starting at the beginning          |
| `public java.io.InputStream `<br>` getBinaryStream(long pos)` `throws SQLException`  | Oracle extension: Retrieves a stream that can be used to read the `BLOB` value that this `Blob` object represents, starting at position `pos` |

These APIs are defined as follows:

    /**
     * Write to the BLOB from a stream at the requested position.
     *
     * @param pos is the position data to be put.
     * @return a output stream to write data to the BLOB
     */
    public java.io.OutputStream setBinaryStream(long pos) throws SQLException

    /**
     * Read from the BLOB as a stream at the requested position.
     *
     * @param pos is the position data to be read.
     * @return a output stream to write data to the BLOB
     */
    public java.io.InputStream getBinaryStream(long pos) throws SQLException

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.24 JDBC CLOB Streaming APIs

The `oracle.sql.CLOB` class is the Oracle JDBC driver implementation of standard JDBC `java.sql.Clob` interface. Table 10-48 lists the `CLOB` streaming APIs.

Table 10-48 JDBC: CLOB Streaming APIs

| Methods                                                                           | Description                                                                                                                                                           |
|:----------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `public java.io.OutputStream`<br>` setAsciiStream (long pos) throws SQLException` | JDBC 3.0: Retrieves a stream to be used to write ASCII characters to the `CLOB` value that this `Clob` object represents, starting at position `pos`                  |
| `public java.io.Writer`<br>` setCharacterStream (long pos) throws SQLException`   | JDBC 3.0: Retrieves a stream to be used to write Unicode characters to the `CLOB` value that this `Clob` object represents, starting, at position `pos`               |
| `public java.io.InputStream`<br>` getAsciiStream() throws SQLException`           | JDBC 3.0: Retrieves a stream that can be used to read ASCII characters from the `CLOB` value that this `Clob` object represents, starting at the beginning            |
| `public java.io.InputStream `<br>`getAsciiStream(long pos)` `throws SQLException` | Oracle extension: Retrieves a stream that can be used to read ASCII characters from the `CLOB` value that this `Clob` object represents, starting at position `pos`   |
| `public java.io.Reader`<br>` getCharacterStream() throws SQLException`            | JDBC 3.0: Retrieves a stream that can be used to read Unicode characters from the `CLOB` value that this `Clob` object represents, starting at the beginning          |
| `public java.io.Reader`<br>` getCharacterStream(long pos) throws SQLException`    | Oracle extension: Retrieves a stream that can be used to read Unicode characters from the `CLOB` value that this `Clob` object represents, starting at position `pos` |

These APIs are defined as follows:

    /**
      * Write to the CLOB from a stream at the requested position.
      * @param pos is the position data to be put.
      * @return a output stream to write data to the CLOB
      */
    public java.io.OutputStream setAsciiStream(long pos) throws SQLException

    /**

         * Write to the CLOB from a stream at the requested position.
         * @param pos is the position data to be put.
         * @return a output stream to write data to the CLOB
         */
      public java.io.Writer setCharacterStream(long pos) throws SQLException

        /**
         * Read from the CLOB as a stream at the requested position.
         * @param pos is the position data to be put.
         * @return a output stream to write data to the CLOB
         */
      public java.io.InputStream getAsciiStream(long pos) throws SQLException

       /**
        * Read from the CLOB as a stream at the requested position.
        * @param pos is the position data to be put.
        * @return a output stream to write data to the CLOB
        */
       public java.io.Reader getCharacterStream(long pos) throws SQLException

**Parent topic:** Using Java (JDBC) to Work With LOBs

#### 10.8.25 BFILE Streaming APIs

`oracle.sql.BFILE `class wraps the database `BFILE`s. Table 10-49 lists the Oracle extension APIs in `oracle.sql.BFILE` that reads `BFILE` content from the requested position.

Table 10-49 JDBC: BFILE Streaming APIs

| Methods                                                                          | Description                        |
|:---------------------------------------------------------------------------------|:-----------------------------------|
| `public java.io.InputStream `<br>`getBinaryStream(long pos) throws SQLException` | Reads from the `BFILE` as a stream |

These APIs are defined as follows:

    /**
     * Read from the BLOB as a stream at the requested position.
     *
     * @param pos is the position data to be read.
     * @return a output stream to write data to the BLOB
     */
    public java.io.InputStream getBinaryStream(long pos) throws SQLException

- JDBC BFILE Streaming Example (NewStreamLob.java)

**Parent topic:** Using Java (JDBC) to Work With LOBs

##### 10.8.25.1 JDBC BFILE Streaming Example (NewStreamLob.java)

    /*
     * This sample shows how to read/write BLOB and CLOB as streams.
     */

    import java.io.*;

    // You must import the java.sql package to use JDBC
    import java.sql.*;

    // You must import the oracle.sql package to use oracle.sql.BLOB
    import oracle.sql.*;

    class NewStreamLob
    {
      public static void main (String args [])  throws Exception
      {
        // Load the Oracle JDBC driver
        DriverManager.registerDriver(new oracle.jdbc.driver.OracleDriver());

        String url = "jdbc:oracle:oci8:@";
        try {
          String url1 = System.getProperty("JDBC_URL");
          if (url1 != null)
            url = url1;
        } catch (Exception e) {
          // If there is any security exception, ignore it
          // and use the default
        }

        // Connect to the database
        Connection conn =
          DriverManager.getConnection (url, "scott", "password");
        // It is faster when auto commit is off
        conn.setAutoCommit (false);

        // Create a Statement
        Statement stmt = conn.createStatement ();

        try
        {
          stmt.execute ("drop table basic_lob_table");
        }
        catch (SQLException e)
        {
          // An exception could be raised here if the table did not exist.
        }

        // Create a table containing a BLOB and a CLOB
        stmt.execute (
             "create table basic_lob_table"
             + "(x varchar2 (30), b blob, c clob)");

        // Populate the table
        stmt.execute (
             "insert into basic_lob_table values"
             + "('one', '010101010101010101010101010101', 'onetwothreefour')");

        System.out.println ("Dumping lobs");

        // Select the lobs
        ResultSet rset = stmt.executeQuery ("select * from basic_lob_table");
        while (rset.next ())
        {
          // Get the lobs
          BLOB blob = (BLOB) rset.getObject (2);
          CLOB clob = (CLOB) rset.getObject (3);

          // Print the lob contents
          dumpBlob (conn, blob, 1);
          dumpClob (conn, clob, 1);

          // Change the lob contents
          fillClob (conn, clob, 11, 50);
          fillBlob (conn, blob, 11, 50);
        }
        rset.close ();

        System.out.println ("Dumping lobs again");

        rset = stmt.executeQuery ("select * from basic_lob_table");
        while (rset.next ())
        {
          // Get the lobs
          BLOB blob = (BLOB) rset.getObject (2);
          CLOB clob = (CLOB) rset.getObject (3);

          // Print the lobs contents
          dumpBlob (conn, blob, 11);
          dumpClob (conn, clob, 11);
        }
        // Close all resources
        rset.close();
        stmt.close();
        conn.close();
      }

      // Utility function to dump Clob contents
      static void dumpClob (Connection conn, CLOB clob, long offset)
        throws Exception
      {
        // get character stream to retrieve clob data
        Reader instream = clob.getCharacterStream(offset);

        // create temporary buffer for read
        char[] buffer = new char[10];

        // length of characters read
        int length = 0;

        // fetch data
        while ((length = instream.read(buffer)) != -1)
        {
          System.out.print("Read " + length + " chars: ");

          for (int i=0; i<length; i++)
            System.out.print(buffer[i]);
          System.out.println();
        }

        // Close input stream
        instream.close();
      }

      // Utility function to dump Blob contents
      static void dumpBlob (Connection conn, BLOB blob, long offset)
        throws Exception
      {
        // Get binary output stream to retrieve blob data
        InputStream instream = blob.getBinaryStream(offset);
        // Create temporary buffer for read
        byte[] buffer = new byte[10];
        // length of bytes read
        int length = 0;
        // Fetch data
        while ((length = instream.read(buffer)) != -1)
        {
          System.out.print("Read " + length + " bytes: ");

          for (int i=0; i<length; i++)
            System.out.print(buffer[i]+" ");
          System.out.println();
        }

        // Close input stream
        instream.close();
      }

      // Utility function to put data in a Clob
      static void fillClob (Connection conn, CLOB clob, long offset, long length)
        throws Exception
      {
        Writer outstream = clob.setCharacterStream(offset);

        int i = 0;
        int chunk = 10;

        while (i < length)
        {
          outstream.write("aaaaaaaaaa", 0, chunk);

          i += chunk;
          if (length - i < chunk)
             chunk = (int) length - i;
        }
        outstream.close();
      }

      // Utility function to put data in a Blob
      static void fillBlob (Connection conn, BLOB blob, long offset, long length)
        throws Exception
      {
        OutputStream outstream = blob.setBinaryStream(offset);

        int i = 0;
        int chunk = 10;

        byte [] data = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 };

        while (i < length)
        {
          outstream.write(data, 0, chunk);

          i += chunk;
          if (length - i < chunk)
             chunk = (int) length - i;
        }
        outstream.close();
      }
    }

**Parent topic:** BFILE Streaming APIs

#### 10.8.26 JDBC and Empty LOBs

An empty `BLOB` can be created from the following API from `oracle.sql.BLOB`:

    public static BLOB empty_lob () throws SQLException

Similarly, the following API from `oracle.sql.CLOB` creates an empty `CLOB`:

    public static CLOB empty_lob () throws SQLException

Empty LOB instances are created by JDBC drivers without making database round trips. Empty LOBs can be used in the following cases:

- set APIs of `PreparedStatement`

- update APIs of updatable result set

- attribute value of STRUCTs

- element value of ARRAYs

  **Note:**

  Empty LOBs are special marker LOBs but not real LOB values.

JDBC applications cannot read or write to empty LOBs created from the preceding APIs. An ORA-17098 "Invalid empty lob operation" results if your application attempts to read/write to an empty LOB.

**Parent topic:** Using Java (JDBC) to Work With LOBs

### 10.9 Oracle Provider for OLE DB (OraOLEDB)

Oracle Provider for OLE DB (OraOLEDB) offers high performance and efficient access to Oracle data for OLE DB and ADO developers.

Developers programming with COM, C++, or any COM client can use OraOLEDB to access Oracle databases.

OraOLEDB is an OLE DB provider for Oracle. It offers high performance and efficient access to Oracle data including LOBs, and also allows updates to certain LOB types.

The following LOB types are supported by OraOLEDB:

- For Persistent LOBs:

  `READ`/`WRITE` through the rowset.

- For BFILEs:

  READ-ONLY through the rowset.

- Temporary LOBs:

  Are not supported through the rowset.

  **See Also:**

  [Oracle Provider for OLE DB Developer's Guide for Microsoft Windows](../oledb/introduction-to-oracle-provider-for-oledb.md)

**Parent topic:** Overview of Supplied LOB APIs

### 10.10 Overview of Oracle Data Provider for .NET (ODP.NET)

Oracle Data Provider for .NET (ODP.NET) is an implementation of a data provider for the Oracle database.

ODP.NET uses Oracle native APIs to offer fast and reliable access to Oracle data and features from any .NET application. ODP.NET also uses and inherits classes and interfaces available in the Microsoft .NET Framework Class Library. The ODP.NET supports the following LOBs as native data types with .NET: `BLOB`, `CLOB`, `NCLOB`, and `BFILE`.

COM and .NET are complementary development technologies. Microsoft recommends that developers use the .NET Framework rather than COM for new development.

**See Also:**

[Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/intro.md)

**Parent topic:** Overview of Supplied LOB APIs
