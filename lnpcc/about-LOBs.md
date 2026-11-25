This chapter describes the support provided by embedded SQL statements for the LOB (Large Object) datatypes.

The four types of LOBs are introduced and compared to the older LONG and LONG RAW datatypes.

The embedded SQL interface in Pro\*C/C++ is shown to provide similar functionality to that of the Oracle Call Interface API and the PL/SQL language.

The LOB statements and their options and host variables are presented.

Lastly, examples of Pro\*C/C++ programs using the LOB interface are presented as simple illustrations of usage.

This chapter contains the following topics:

- What are LOBs?

- How to Use LOBs in Your Program

- Rules for LOB Statements

- LOB Statements

- LOBs and the Navigational Interface

- LOB Program Examples

### 16.1 What are LOBs?

Use LOB (large object) columns to store large amounts of data (maximum size is 4 Gigabytes) such as ASCII text, National Character text, files in various graphics formats, and sound wave forms.

#### 16.1.1 Internal LOBs

Internal LOBs (BLOBs, CLOBs, NCLOBs) are stored in database table spaces and have transactional support (Commit, Rollback, and so on. work with them) of the database server.

BLOBs (Binary LOBs) store unstructured binary (also called "raw") data, such as video clips.

CLOBs (Character LOBs) store large blocks of character data from the database character set.

NCLOBs (National Character LOBs) store large blocks of character data from the National Character Set.

#### 16.1.2 External LOBs

External LOBs are operating system files outside the database tablespaces, that have no transactional support from the database server.

`BFILEs` (Binary Files) store data in external binary files. A BFILE can be in GIF, JPEG, MPEG, MPEG2, text, or other formats.

#### 16.1.3 Security for BFILEs

The DIRECTORY object is used to access and use BFILEs. The DIRECTORY is a logical alias name (stored in the server) for the actual physical directory in the server file system containing the file. Users are permitted to access the file only if granted access privilege on the DIRECTORY object.

- The DDL (data definition language) SQL statements CREATE, REPLACE, ALTER, and DROP are used with DIRECTORY database objects.

- The DML (Data Management Language) SQL statements are used to GRANT and REVOKE the READ system and object privileges on DIRECTORY objects.

A example CREATE DIRECTORY directive is:

    EXEC SQL CREATE OR REPLACE DIRECTORY "Mydir" AS '/usr/home/mydir' ;

Other users or roles can read the directory only if you grant them permission with a DML (Data Manipulation Language) statement, such as GRANT. For example, to allow user `scott` to read BFILES in directory `/usr/home/mydir`:

    EXEC SQL GRANT READ ON DIRECTORY "Mydir" TO scott ;

Up to 10 BFILES can be opened simultaneously in one session. This default value can be changed by setting the SESSION_MAX_OPEN_FILES parameter.

**Related Topics**

- [Oracle Database Development Guide](../adfns/index.md)
- [GRANT](../sqlrf/GRANT.md)

#### 16.1.4 LOBs versus LONG and LONG RAW

LOBs are different from the older LONG and LONG RAW datatypes in many ways.

- The maximum size of a LOB is 4 Gigabytes versus 2 Gigabytes for LONG and LONG RAW.

- You can use random as well as sequential access methods on LOBs; you can only use sequential access methods on LONG and LONG RAW.

- LOBs (except NCLOBs) can be attributes of an object type that you define.

- Tables can have multiple LOB columns, but can have only one LONG or LONG RAW column.

Migration of existing LONG and LONG Raw attributes to LOBs is recommended by Oracle. Oracle plans to end support of LONG and LONG RAW in future releases. See [Oracle® Database Migration Guide](../drdaa/index.md) for more information on migration.

#### 16.1.5 LOB Locators

A LOB locator points to the actual LOB contents. The locator is returned when you retrieve the LOB, not the LOB's contents. LOB locators cannot be saved in one transaction or session and used again in a later transaction or session.

#### 16.1.6 Temporary LOBs

You can create temporary LOBs, that are like local variables, to assist your use of database LOBs. Temporary LOBs are not associated with any table, are only accessible by their creator, have locators (which is how they are accessed), and are deleted when a session ends.

There is no support for temporary BFILES. Temporary LOBs are only permitted to be input variables (IN values) in the WHERE clauses of INSERT, UPDATE, or DELETE statements. They are also permitted as values inserted by an INSERT statement, or a value in the SET clause of an UPDATE statement. Temporary LOBs have no transactional support from the database server, which means that you cannot do COMMITS or ROLLBACKs on them.

Temporary LOB locators can span transactions. They also are deleted when the server abnormally terminates, and when an error is returned from a database SQL operation.

#### 16.1.7 LOB Buffering Subsystem

The LBS (LOB Buffering Subsystem) is an area of user memory provided for use as a buffer for one or more LOBs in the client's address space.

Buffering has these advantages, especially for applications on a client that does many small reads and writes to specific regions of the LOB:

- The LBS reduces round trips to the server because you fill the buffer with multiple reads/writes to the LOBs, then write to the server when a FLUSH directive is executed.

- Buffering also reduces the total number of LOB updates on the server. This creates better LOB performance and saves disk space.

Oracle provides a simple buffer subsystem; not a cache. Oracle does not guarantee that the contents of a buffer are always synchronized with the server LOB value. Use the FLUSH statement to actually write updates in the server LOB.

Buffered read/write of a LOB are performed through its locator. A locator enabled for buffering provides a consistent read version of the LOB until you perform a write through that locator.

After being used for a buffered WRITE, a locator becomes an updated locator and provides access to the latest LOB version as seen through the buffering subsystem. All further buffered WRITEs to the LOB can only be done through this updated locator. Transactions involving buffered LOB operations cannot migrate across user sessions.

The LBS is managed by the user, who is responsible for updating server LOB values by using FLUSH statements to update them. It is single-user and single threaded. Use ROLLBACK and SAVEPOINT actions to guarantee correctness in the server LOBs. Transactional support for buffered LOB operations is not guaranteed by Oracle. To ensure transactional semantics for buffered LOB updates, you must maintain logical savepoints to perform a rollback in the event of an error.

### 16.2 How to Use LOBs in Your Program

This section describes some of the important programming issues related to the use of LOBs in your Pro\*C/C++ application.

#### 16.2.1 Three Ways to Access LOBs

The three methods available to access LOBs in Pro\*C/C++ are:

- The DBMS_LOB package inside PL/SQL blocks.

- OCI (Oracle Call Interface) function calls.

- Embedded SQL statements.

The SQL statements are designed to give users a functional equivalent to the PL/SQL interface while avoiding the complexity of the OCI interface.

The following table compares LOB access by OCI function calls in Pro\*C/C++, PL/SQL, and embedded SQL statements in Pro\*C/C++. Empty boxes indicate missing functionality.

Table 16-1 LOB Access Methods

| OCI (1)                | PL/SQL(2)         | Pro\*C/C++ Embedded SQL   |
|:-----------------------|:------------------|:--------------------------|
| \-                     | COMPARE()         | \-                        |
| \-                     | INSTR()           | \-                        |
| \-                     | SUBSTR()          | \-                        |
| OCILobAppend           | APPEND()          | APPEND                    |
| OCILobAssign           | :=                | ASSIGN                    |
| OCILobCharSetForm      | \-                | \-                        |
| OCICharSetId           | \-                | \-                        |
| OCILobClose            | CLOSE()           | CLOSE                     |
| OCILobCopy             | COPY()            | COPY                      |
| OCILobCreateTemporary  | CREATETEMPORARY() | CREATE TEMPORARY          |
| OCILobDisableBuffering | \-                | DISABLE BUFFERING         |
| OCILobEnableBuffering  | \-                | ENABLE BUFFERING          |
| OCILobErase            | ERASE()           | ERASE                     |
| OCILobGetChunkSize     | GETCHUNKSIZE()    | DESCRIBE                  |
| OCILobIsOpen           | ISOPEN()          | DESCRIBE                  |
| OCILobFileClose        | FILECLOSE()       | CLOSE                     |
| OCILobFileCloseAll     | FILECLOSEALL()    | FILE CLOSE ALL            |
| OCILobFileExists       | FILEEXISTS()      | DESCRIBE                  |
| OCILobFileGetName      | FILEGETNAME()     | DESCRIBE                  |
| OCILobFileIsOpen       | FILEISOPEN()      | DESCRIBE                  |
| OCILobFileOpen         | FILEOPEN()        | OPEN                      |
| OCILobFileSetName      | BFILENAME()       | FILE SET<sup>Foot 3</sup> |
| OCILobFlushBuffer      | \-                | FLUSH BUFFER              |
| OCILobFreeTemporary    | FREETEMPORARY()   | FREE TEMPORARY            |
| OCILobGetLength        | GETLENGTH()       | DESCRIBE                  |
| OCILobIsEqual          | =                 | \-                        |
| OCILobIsTemporary      | ISTEMPORARY()     | DESCRIBE                  |
| OCILobLoadFromFile     | LOADFROMFILE()    | LOAD FROM FILE            |
| OCILobLocatorIsInit    | \-                | \-                        |
| OCILobOpen             | OPEN()            | OPEN                      |
| OCILobRead             | READ()            | READ                      |
| OCILobTrim             | TRIM()            | TRIM                      |
| OCILobWrite            | WRITE()           | WRITE                     |
| OCILobWriteAppend      | WRITEAPPEND()     | WRITE                     |

<sup>Footnote 1</sup> For C/C++ users only. Prototypes for these functions are in ociap.h.

<sup>Footnote 2</sup> From dbmslob.sql. All routines are prefixed with 'DBMS_LOB.' except BFILENAME.

<sup>Footnote 3</sup>

The BFILENAME() built in SQL function may also be used.

**Note:**

You must explicitly lock the row before using any of the new statements that modify or change a LOB in any way. Operations that can modify a LOB value are APPEND, COPY, ERASE, LOAD FROM FILE, TRIM, and WRITE.

#### 16.2.2 LOB Locators in Your Application

To use a LOB locator in your Pro\*C/C++ application, include the oci.h header file and declare a pointer to the type OCIBlobLocator for BLOBs, OCIClobLocator for CLOBs and NCLOBs, or OCIBFileLocator for BFILEs.

For an NCLOB, you must either

- Use the clause 'CHARACTER SET IS NCHAR_CS' in the C/C++ declaration,

- Or, you must have already used an NLS_CHAR precompiler option on the command line or in a configuration file to set the NLS_NCHAR environment variable.

Here is how it is done:

    /* In your precompiler program */
    #include <oci.h>
    ...
    OCIClobLocator CHARACTER SET IS NCHAR_CS *a_nclob ;

Or, if you have already set the precompiler option NLS_CHAR this way when invoking Pro\*C/C++:

    NLS_CHAR=(a_nclob)

you can omit the CHARACTER SET clause in your code:

    #include <oci.h>
    ...
    OCIClobLocator *a_nclob ;

The other declarations are simple:

    /* In your precompiler program */
    #include <oci.h>
    ...
    OCIBlobLocator  *a_blob ;
    OCIClobLocator  *a_clob ;
    OCIBFileLocator *a_bfile ;

**Related Topics**

- [NLS_CHAR](precompiler-options.md)

#### 16.2.3 Initializing a LOB

There are different techniques which are used to intialize the different types of LOBs. Each is described in this section.

##### 16.2.3.1 Internal LOBs

To initialize a BLOB to empty, use the `EMPTY_BLOB()` function or, use the ALLOCATE SQL statement. For CLOBs and NCLOBs, use the `EMPTY_CLOB() `function. See [Oracle Database SQL Language Reference](../sqlrf/index.md) for more about `EMPTY_BLOB()` and `EMPTY_CLOB()`.

These functions are permitted only in the VALUES clause of an INSERT statement or as the source of the SET clause in an UPDATE statement.

For example:

    EXEC SQL INSERT INTO lob_table (a_blob, a_clob)
       VALUES (EMPTY_BLOB(), EMPTY_CLOB()) ;

The ALLOCATE statement allocates a LOB locator and initializes it to empty. So, the following code is equivalent to the previous example:

    #include <oci.h>
    ...
    OCIBlobLocator *blob ;
    OCIClobLocator *clob ;
    EXEC SQL ALLOCATE :blob ;
    EXEC SQL ALLOCATE :clob ;
    EXEC SQL INSERT INTO lob_table (a_blob, a_clob)
       VALUES (:blob, :clob) ;

##### 16.2.3.2 External LOBs

Use the LOB FILE SET statement to initialize the DIRECTORY alias of the BFILE and FILENAME this way:

    #include <oci.h>
    ...
    char *alias = "lob_dir" ;
    char *filename = "image.gif" ;
    OCIBFileLocator *bfile ;
    EXEC SQL ALLOCATE :bfile ;
    EXEC SQL LOB FILE SET :bfile
       DIRECTORY = :alias, FILENAME = :filename ;
    EXEC SQL INSERT INTO file_table (a_bfile) VALUES (:bfile) ;

Refer to [Oracle Database Advanced Application Developer's Guide](../adfns/index.md) for a complete description of DIRECTORY object naming conventions and DIRECTORY object privileges.

Alternatively, you can use the BFILENAME('directory', 'filename') function in an INSERT or UPDATE statement to initialize a BFILE column or attribute for a particular row, and give the name of the actual physical directory and filename:

    EXEC SQL INSERT INTO file_table (a_bfile)
       VALUES (BFILENAME('lob_dir', 'image.gif'))
          RETURNING a_bfile INTO :bfile ;

**Note:**

BFILENAME() does not check permissions on the directory or filename, or whether the physical directory actually exists. Subsequent file accesses that use the BFILE locator will do those checks and return an error if the file is inaccessible.

##### 16.2.3.3 Temporary LOBs

A temporary LOB is initialized to empty when it is first created using the embedded SQL LOB CREATE TEMPORARY statement. The EMPTY_BLOB() and EMPTY_CLOB() functions cannot be used with temporary LOBs.

##### 16.2.3.4 Freeing LOBs

The FREE statement is used to free the memory reserved by an ALLOCATE statement:

    EXEC SQL FREE :a_blob;

### 16.3 Rules for LOB Statements

Here are the rules for using LOB statements:

#### 16.3.1 For All LOB Statements

These general restrictions and limitations apply when manipulating LOBs with the SQL LOB statements:

- The FOR clause is not allowed in EXEC SQL LOB statements since only one LOB locator can be used in those statements.

- Distributed LOBs are not supported. Although you may use the AT database clause in any of the new embedded SQL LOB statements, you cannot mix LOB locators that were created or ALLOCATEd using different database connections in the same SQL LOB statement.

- For the LOB READ and WRITE operations, OCI provides a callback mechanism whereby the client can specify a callback function that will be executed each time a piece of the LOB value is either read or written. The embedded SQL LOB approach does not support this capability.

- OCI provides a mechanism that allows users to create and specify their own durations that can be used when creating temporary LOBs. There is also a mechanism for specifying that the buffer cache be used for READ and WRITE operations on temporary LOBs. This interface does not support these capabilities.

#### 16.3.2 For the LOB Buffering Subsystem

For the LBS, these rules must be followed:

- Errors in read or write accesses are reported at the next access to the server. Therefore, error recovery has to be coded by you, the user.

- When updating a LOB with buffered writes, do not update the same LOB with a method that bypasses the LOB Buffering Subsystem.

- An updated LOB locator enabled for buffering can be passed as an IN parameter to a PL/SQL procedure, but not as an IN OUT or OUT parameter. An error is returned, An error also is returned when there is an attempt to return an updated locator.

- An ASSIGN of an updated locator enabled for buffering to another locator is not allowed.

- You can append to the LOB value with buffered writes, but the starting offset must be one character after the end of the LOB. The LBS does not allow APPEND statements resulting in zero-byte fillers or spaces in LOBs in the database server.

- The character sets of the host locator bind variable and the database server CLOB must be the same.

- Only ASSIGN, READ and WRITE statements work with a locator enabled for buffering.

- The following statements result in errors when used with a locator enabled for buffering: APPEND, COPY, ERASE, DESCRIBE (LENGTH only), and TRIM. Errors are also returned when you use these statements with a locator that is not enabled for buffering, if the LOB pointed to by the locator is being accessed in buffered mode by another locator.

  **Note:**

  The FLUSH statement must be used on a LOB enabled by the LOB Buffering Subsystem before.

- Committing the transaction.

- Migrating from the current transaction to another.

- Disabling buffer operations on a LOB.

- Returning from an external procedure execution back to the PL/SQL routine.

  **Note:**

  If an external callout is called from a PL/SQL block with a locator parameter, then all buffering, including the ENABLE statement should be done inside the external procedure.

Follow this recipe:

- Call the external callout.

- ENABLE the locator for buffering.

- READ or WRITE using the locator.

- FLUSH the LOB (LOBs are never implicitly flushed).

- Disable the locator for buffering.

- Return to the function/procedure/method in PL/SQL.

You have to explicitly FLUSH a LOB.

#### 16.3.3 For Host Variables

Use the following rules and notes for the LOB statements:

- src and dst can refer to either internal or external LOB locators, but file refers only to external locators.

- Numeric host values (`amt, src_offset, dst_offset`, and so on) are declared `as `a 4-byte unsigned integer variable. The values are restricted between 0 and 4 Gigabytes.

- The concept of NULL is part of a LOB locator. There is no need for indicator variables in the LOB statements. NULL cannot be used with numeric value variables such as `amt, src_offset`, and so on and result in an error.

- The offset values `src_offset `and `dst_offset` have default values 1.

### 16.4 LOB Statements

The statements are presented alphabetically. In all the statements where it appears, database refers to a database connection

#### 16.4.1 APPEND

##### Purpose

This statement appends a LOB value at the end of another LOB.

##### Syntax

    EXEC SQL [AT [:]database] LOB APPEND :src TO :dst ;

##### Host Variables

src (IN)

An internal LOB locator uniquely referencing the source LOB.

dst (IN OUT)

An internal LOB locator uniquely referencing the destination LOB.

##### Usage Notes

The data is copied from the source LOB to the end of the destination LOB, extending the destination LOB up to a maximum of 4 Gigabytes. If the LOB is extended beyond 4 Gigabytes, an error will occur.

The source and destination LOBs must already exist and the destination LOB must be initialized.

Both the source and destination LOBs must be of the same internal LOB type. It is an error to have enabled LOB buffering for either type of locator.

#### 16.4.2 ASSIGN

##### Purpose

Assigns a LOB or BFILE locator to another.

##### Syntax

    EXEC SQL [AT [:]database] LOB ASSIGN :src to :dst ;

##### Host Variables

src (IN)

LOB or BFILE locator source copied from.

dst (IN OUT)

LOB or BFILE locator copied to.

##### Usage Notes

After the assignment, both locators refer to the same LOB value. The destination LOB locator must be a valid initialized (ALLOCATEd) locator.

For internal LOBs, the source locator's LOB value is copied to the destination locator's LOB value only when the destination locator is stored in the table. For Pro\*C/C++, issuing a FLUSH of an object containing the destination locator will copy the LOB value.

An error is returned when a BFILE locator is assigned to an internal LOB locator and vice-versa. It is also an error if the src and dst LOBs are not of the same type.

If the source locator is for an internal LOB that was enabled for buffering, and the source locator has been used to modify the LOB value through the LOB Buffering Subsystem, and the buffers have not been FLUSHed since the WRITE, then the source locator cannot be assigned to the destination locator. This is because only one locator for each LOB can modify the LOB value through the LOB Buffering Subsystem.

#### 16.4.3 CLOSE (for LOBs)

##### Purpose

Close an open LOB or BFILE.

##### Syntax

    EXEC SQL [AT [:]database] LOB CLOSE :src ;

##### Host Variables

src (IN OUT)

The locator of the LOB or BFILE to be closed.

##### Usage Notes

It is an error to close the same LOB twice either with different locators or with the same locator. For external LOBs, no error is produced if the BFILE exists but has not been opened.

It is an error to COMMIT a transaction before closing all previously opened LOBs. At transaction ROLLBACK time, all LOBs that are still open will be discarded without first being closed.

#### 16.4.4 COPY

##### Purpose

Copy all or part of a LOB value into a second LOB.

##### Syntax

    EXEC SQL [AT [:]database] LOB COPY :amt FROM :src [AT :src_offset]
       TO :dst [AT :dst_offset] ;

##### Host Variables

amt (IN)

The maximum number of bytes for BLOBs, or characters for CLOBs and NCLOBs, to copy.

src (IN)

The locator of the source LOB.

src_offset (IN)

This is the number of characters for CLOB or NCLOB, and the number of bytes for a BLOB, starting from 1 at the beginning of the LOB.

dst (IN)

The locator of the destination LOB.

dst_offset (IN)

The destination offset. Same rules as for src_offset.

##### Usage Notes

If the data already exists at the destination's offset and beyond, it is overwritten with the source data. If the destination's offset is beyond the end of the current data, zero-byte fillers (BLOBs) or spaces (CLOBs) are written into the destination LOB from the end of the current data to the beginning of the newly written data from the source.

The destination LOB is extended to accommodate the newly written data if it extends beyond the current length of the destination LOB. It is a runtime error to extend this LOB beyond 4 Gigabytes.

It is also an error to try to copy from a LOB that is not initialized.

Both the source and destination LOBs must be of the same type. LOB buffering must not be enabled for either locator.

The `amt` variable indicates the maximum amount to copy. If the end of the source LOB is reached before the specified amount is copied, the operation terminates with `ORA-22993` error.

To make a temporary LOB permanent, the COPY statement must be used to explicitly COPY the temporary LOB into a permanent one.

#### 16.4.5 CREATE TEMPORARY

##### Purpose

Creates a temporary LOB.

##### Syntax

    EXEC SQL [AT [:]database] LOB CREATE TEMPORARY :src ;

##### Host Variables

src (IN OUT)

Before execution, when IN,` src` is a LOB locator previously ALLOCATEd.

After execution, when OUT, `src` is a LOB locator that will point to a new empty temporary LOB.

##### Usage Notes

After successful execution, the locator points to a newly created temporary LOB that resides on the database server independent of a table. The temporary LOB is empty and has zero length.

At the end of a session, all temporary LOBs are freed. READs and WRITEs to temporary LOBs never go through the buffer cache.

#### 16.4.6 DISABLE BUFFERING

##### Purpose

Disables LOB buffering for the LOB locator.

##### Syntax

    EXEC SQL [AT [:]database] LOB DISABLE BUFFERING :src ;

##### Host Variable

src (IN OUT)

An internal LOB locator.

##### Usage Notes

This statement does not support BFILEs. Subsequent reads or writes will not be done through the LBS.

**Note:**

Use a FLUSH BUFFER command to make changes permanent, since this statement does not implicitly flush the changes made in the LOB Buffering Subsystem.

#### 16.4.7 ENABLE BUFFERING

##### Purpose

Enables LOB buffering for the LOB locator.

##### Syntax

    EXEC SQL [AT [:]database] LOB ENABLE BUFFERING :src ;

##### Host Variable

src (IN OUT)

An internal LOB locator.

##### Usage Notes

This statement does not support BFILEs. Subsequent reads and writes are done through the LBS.

#### 16.4.8 ERASE

##### Purpose

Erases a given amount of LOB data starting from a given offset.

##### Syntax

    EXEC SQL [AT [:]database] LOB ERASE :amt FROM :src [AT :src_offset] ;

##### Host Variables

amt (IN OUT)

The input is the number of bytes or characters to erase. The returned output is the actual number erased.

src (IN OUT)

An internal LOB locator.

src_offset (IN)

The offset from the beginning of the LOB, starting from 1.

##### Usage Notes

This statement does not support BFILEs.

After execution, `amt` returns the actual number of characters/bytes that were erased. The actual number and requested number will differ if the end of the LOB value is reached before erasing the requested number of characters/bytes. If the LOB is empty, `amt` will indicate that 0 characters/bytes were erased.

For BLOBs, erasing means zero-byte fillers overwrite the existing LOB value. For CLOBs, erasing means that spaces overwrite the existing LOB value.

#### 16.4.9 FILE CLOSE ALL

##### Purpose

Closes all BFILES opened in the current session.

##### Syntax

    EXEC SQL [AT [:]database] LOB FILE CLOSE ALL ;

##### Usage Notes

If there are any open files in the session whose closure has not been handled properly, you can use the FILE CLOSE ALL statement to close all files opened in the session, and resume file operations from the beginning.

#### 16.4.10 FILE SET

##### Purpose

Sets DIRECTORY alias and FILENAME in a BFILE locator.

##### Syntax

    EXEC SQL [AT [:]database] LOB FILE SET :file
        DIRECTORY = :alias, FILENAME = :filename ;

##### Host Variables

file (IN OUT)

BFILE locator where the DIRECTORY alias and FILENAME is set.

alias (IN)

DIRECTORY alias name to set.

filename (IN)

The FILENAME to set.

##### Usage Notes

The given BFILE locator must be first ALLOCATEd prior to its use in this statement.

Both the DIRECTORY alias name and FILENAME must be provided.

The maximum length of the DIRECTORY alias is 128 bytes. The maximum length of the FILENAME is 255 bytes.

The only external datatypes supported for use with the DIRECTORY alias name and FILENAME attributes are CHARZ, STRING, VARCHAR, VARCHAR2 and CHARF.

It is an error to use this statement with anything but an external LOB locator.

#### 16.4.11 FLUSH BUFFER

##### Purpose

Writes this LOB's buffers to the database server.

##### Syntax

    EXEC SQL [AT [:]database] LOB FLUSH BUFFER :src [FREE] ;

##### Host Variables

src (IN OUT)

Internal LOB locator.

##### Usage Notes

Writes the buffer data to the database LOB in the server from the LOB referenced by the input locator.

LOB buffering must have already been enabled for the input LOB locator.

The FLUSH operation, by default, does not free the buffer resources for reallocation to another buffered LOB operation. However, if you want to free the buffer explicitly, you can include the optional FREE keyword to so indicate.

#### 16.4.12 FREE TEMPORARY

##### Purpose

Free the temporary space for the LOB locator.

##### Syntax

    EXEC SQL [AT [:]database] LOB FREE TEMPORARY :src ;

##### Host Variable

src (IN OUT)

The LOB locator pointing to the temporary LOB.

##### Usage Notes

The input locator must point to a temporary LOB. The output locator is marked not initialized and can be used in subsequent LOB statements.

#### 16.4.13 LOAD FROM FILE

##### Purpose

Copy all or a part of a BFILE into an internal LOB.

##### Syntax

    EXEC SQL [AT [:]database] LOB LOAD :amt FROM FILE :file [AT :src_offset] INTO
        :dst [AT :dst_offset] ;

##### Host Variables

amt (IN)

Maximum number of bytes to be loaded.

file (IN OUT)

The source BFILE locator.

src_offset (IN)

The number of bytes offset from the beginning of the file, starting from 1.

dst (IN OUT)

The destination LOB locator which can be BLOB, CLOB, be NCLOB.

dst_offset (IN)

The number of bytes (for BLOBs) or characters (CLOBs and NCLOBs) from the beginning of the destination LOB where writing will begin. It starts at 1.

##### Usage Notes

The data is copied from the source BFILE to the destination internal LOB. No character set conversions are performed when copying the BFILE data to a CLOB or NCLOB. Therefore, the BFILE data must already be in the same character set as the CLOB or NCLOB in the database.

The source and destination LOBs must already exist. If the data already exists at the destination's start position, it is overwritten with the source data. If the destination's start position is beyond the end of the current data, zero-byte fillers (BLOBs) or spaces (CLOBs and NCLOBs) are written into the destination LOB. The fillers are written to the destination LOB from the end of the data to the beginning of the newly written data from the source.

The destination LOB is extended to accommodate the newly written data if it extends beyond the current length of the destination LOB. It is an error to extend this LOB beyond 4 Gigabytes.

It is also an error to copy from a BFILE that is not initialized.

The amount parameter indicates the maximum amount to load. If the end of the source BFILE is reached before the specified amount is loaded, the operation terminates with `ORA-22993` error.

#### 16.4.14 OPEN (for LOBs)

##### Purpose

Open a LOB or BFILE for read or read/write access.

##### Syntax

    EXEC SQL [AT [:]database] LOB OPEN :src [ READ ONLY | READ WRITE ] ;

##### Host Variables

src (IN OUT)

LOB locator of the LOB or BFILE.

##### Usage Notes

The default mode in which a LOB or BFILE can be OPENed is for READ ONLY access.

For internal LOBs, being OPEN is associated with the LOB, not the locator. Assigning an already OPENed locator to another locator does not count as OPENing a new LOB. Instead, both locators refer to the same LOB. For BFILEs, being OPEN is associated with the locator.

Only 32 LOBs can be OPEN at any one time. An error will be returned when the 33rd LOB is OPENed.

There is no support for writable BFILEs. Therefore, when you OPEN a BFILE in READ WRITE mode, an error is returned.

It is also an error to open a LOB in READ ONLY mode and then attempt to WRITE to the LOB.

#### 16.4.15 READ

##### Purpose

Reads all or part of a LOB or BFILE into a buffer.

##### Syntax

    EXEC SQL [AT [:]database] LOB READ :amt FROM :src [AT :src_offset]
       INTO :buffer [WITH LENGTH :buflen] ;

##### Host Variables

amt (IN OUT)

The input is the number of characters or bytes to be read. The output is the actual number of characters or bytes that were read.

If the amount of bytes to be read is larger than the buffer length it is assumed that the LOB is being READ in a polling mode. On input if this value is 0, then the data will be read in a polling mode from the input offset until the end of the LOB.

The number of bytes or characters actually read is returned in `amt.` If the data is read in pieces, `amt` will always contain the length of the last piece read.

When the end of a LOB is reached an `ORA-1403: no data found` error will be issued.

When reading in a polling mode, the application must invoke the LOB READ repeatedly to read more pieces of the LOB until no more data is left. Control the use of the polling mode with the NOT FOUND condition in a WHENEVER directive to catch the `ORA-1403` error.

src (IN)

The LOB or BFILE locator.

src_offset (IN)

This is the absolute offset from the beginning of the LOB value from which to start reading. For character LOBs it is the number of characters from the beginning of the LOB. For binary LOBs or BFILEs it is the number of bytes. The first position is 1.

buffer (IN/OUT)

A buffer into which the LOB data will be read. The external datatype of the buffer is restricted to only a few types depending on the type of the source LOB. The maximum length of the buffer depends on the external datatype being used to store the LOB value. The following table summarizes the legal external datatypes and their corresponding maximum lengths categorized by source LOB type:

Table 16-2 Source LOB and Precompiler Datatypes

| External LOB(4) | Internal LOB | Precompiler External Datatype            | Precompiler Maximum Length (5)             | PL/SQL Datatype | PL/SQL Maximum Length |
|:----------------|:-------------|:-----------------------------------------|:-------------------------------------------|:----------------|:----------------------|
| BFILE           | BLOB         | RAW<br>VARRAW<br>LONG RAW<br>LONG VARRAW | 65535<br>65533<br>2147483647<br>2147483643 | RAW             | 32767                 |
| BFILE           | CLOB         | VARCHAR2<br>VARCHAR<br>LONG VARCHAR      | 65535<br>65533<br>2147483643               | VARCHAR2        | 32767                 |
| BFILE           | NCLOB        | NVARCHAR2                                | 4000                                       | NVARCHAR2       | 4000                  |

<sup>Footnote 4</sup> Any of the external datatypes shown can be used with BFILES.

<sup>Footnote 5</sup> Lengths are measured in bytes, not characters.

buflen (IN)

Specifies the length of the given buffer when it cannot be determined otherwise.

##### Usage Notes

A BFILE must already exist on the database server and it must have been opened using the input locator. The database must have permission to read the file and you, the user, must have read permission on the directory.

It is an error to try to read from an un-initialized LOB or BFILE.

The length of the buffer is determined this way:

- From `buflen`, when the WITH LENGTH clause is present.

- In the absence of the WITH LENGTH clause, the length is determined by treating the buffer host variable in OUT mode.

**Related Topics**

- [Globalization Support](datatypes-and-host-variables.md)
- READ a BLOB, Write a File Example

#### 16.4.16 TRIM

##### Purpose

Truncates the LOB value.

##### Syntax

    EXEC SQL [AT [:]database] LOB TRIM :src TO :newlen ;

##### Host Variables

src (IN OUT)

LOB locator for internal LOB.

newlen (IN)

The new length of the LOB value.

##### Usage Notes

This statement is not for BFILES. The new length cannot be greater than the current length, or an error is returned.

#### 16.4.17 WRITE

##### Purpose

Writes the contents of a buffer to a LOB.

##### Syntax

    EXEC SQL [AT [:]database] LOB WRITE [APPEND] [ FIRST | NEXT | LAST | ONE ]
        :amt FROM :buffer [WITH LENGTH :buflen] INTO :dst [AT :dst_offset] ;

##### Host Variables

amt (IN OUT)
The input is the number of characters or bytes to be written.

The output is the actual number of characters or bytes that is written.

When writing using a polling method, `amt` will return the cumulative total length written for the execution of the WRITE statement after a WRITE LAST is executed. If the WRITE statement is interrupted, `amt` will be undefined.

buffer (IN)
A buffer from which the LOB data is written.

dst (IN OUT)
The LOB locator.

dst_offset (IN)
The offset from the beginning of the LOB (counting from 1), in characters for CLOBs and NCLOBs, in bytes for BLOBs.

buflen (IN)
The buffer length when it cannot be calculated in any other way.

##### Usage Notes

If LOB data already exists, it is overwritten with the data stored in the buffer. If the offset specified is beyond the end of the data currently in the LOB, zero-byte fillers or spaces are inserted into the LOB.

Specifying the keyword APPEND in the WRITE statement causes the data to automatically be written to the end of the LOB. When APPEND is specified, the destination offset is assumed to be the end of the LOB. It is an error to specify the destination offset when using the APPEND option in the WRITE statement.

The buffer can be written to the LOB in one piece (using the ONE orientation which is the default) or it can be provided piece-wise using a standard polling method.

Polling is begun by using FIRST, then NEXT to write subsequent pieces. The LAST keyword is used to write the final piece that terminates the write.

Using this piece-wise write mode, the buffer and the length can be different in each call if the pieces are of different sizes and from different locations.

If the total amount of data passed to Oracle is less than the amount specified by the `amt` parameter after doing all the writes, an error results.

The same rules apply for determining the buffer length as in the READ statement.

**Related Topics**

- READ
- READ a BLOB, Write a File Example

#### 16.4.18 DESCRIBE

##### Purpose

This is a statement that is equivalent to several OCI and PL/SQL statements (which is why it is saved for last). Use the LOB DESCRIBE SQL statement to retrieve attributes from a LOB. This capability is similar to OCI and PL/SQL procedures. The LOB DESCRIBE statement has this format:

##### Syntax

    EXEC SQL [AT [:]database] LOB DESCRIBE :src GET attribute1 [{, attributeN}]
       INTO :hv1 [[INDICATOR] :hv_ind1] [{, :hvN [[INDICATOR] :hv_indN] }] ;

where an attribute can be any of these choices:

    CHUNKSIZE | DIRECTORY | FILEEXISTS | FILENAME | ISOPEN | ISTEMPORARY | LENGTH

##### Host variables

src (IN)

The LOB locator of an internal or external LOB.

hv1 ... hvN ... (OUT)

The host variables that receive the attribute values, in the order specified in the attribute name list.

hv_ind1 ... hv_indN ... (OUT)

Optional host variables that receive the indicator NULL status in the order of the attribute name list.

This table describes the attributes, which LOB it is associated with, and the C types into which they should be read:

Table 16-3 LOB Attributes

| LOB Attribute | Attribute Description                                                                                                                                                                                                                                                                                                                                                                                                                                        | Restrictions                  | C Type                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------|:--------------------------|
| CHUNKSIZE     | The amount (in bytes for BLOBs and characters for CLOBs/NCLOBs) of space used in the LOB chunk to store the LOB value. You speed up performance if you issue READ/WRITE requests using a multiple of this chunk size. If all WRITEs are done on a chunk basis, no extra/excess versioning is done nor duplicated. Users could batch up the WRITE until they have enough for a chunk instead of issuing several WRITE calls for the same CHUNK.               | BLOBs, CLOBs, and NCLOBs only | unsigned int              |
| DIRECTORY     | The name of the DIRECTORY alias for the BFILE. The maximum length is 128 bytes.                                                                                                                                                                                                                                                                                                                                                                              | FILE LOBs only                | char \* <sup>Foot 6</sup> |
| FILEEXISTS    | Determines whether or not the BFILE exists on the server's operating system's file system. FILEEXISTS is true when it is nonzero; false when it equals 0.                                                                                                                                                                                                                                                                                                    | FILE LOBs only                | signed int                |
| FILENAME      | The name of the BFILE. The maximum length is 255 bytes.                                                                                                                                                                                                                                                                                                                                                                                                      | FILE LOBs only                | char \*                   |
| ISOPEN        | For BFILEs, if the input BFILE locator was never used in an OPEN statement, the BFILE is considered not to be OPENed by this locator. However, a different BFILE locator may have OPENed the BFILE. More than one OPEN can be performed on the same BFILE using different locators. For LOBs, if a different locator OPENed the LOB, the LOB is still considered to be OPEN by the input locator. ISOPEN is true when it is nonzero; false when it equals 0. | \-                            | signed int                |
| ISTEMPORARY   | Determines whether or not the input LOB locator refers to a temporary LOB or not. ISTEMPORARY is true when it is nonzero; false when it equals 0.                                                                                                                                                                                                                                                                                                            | BLOBs, CLOBs, and NCLOBs only | signed int                |
| LENGTH        | Length of BLOBs and BFILEs in bytes, CLOBs and NCLOBs in characters. For BFILEs, the length includes EOF if it exists. Empty internal LOBs have zero length. LOBs/BFILEs that are not initialized have undefined length.                                                                                                                                                                                                                                     | \-                            | unsigned int              |

<sup>Footnote 6</sup>

For DIRECTORY and FILENAME attributes, the only external datatypes that will be supported are CHARZ, STRING, VARCHAR, VARCHAR2 and CHARF.

##### Usage Notes

Indicator variables should be declared short. After execution has completed, sqlca.sqlerrd\[2\] contains the number of attributes retrieved without error. If there was an execution error, the attribute at which it occurred is one more than the contents of sqlca.sqlerrd\[2\].

##### DESCRIBE Example

Here is a simple Pro\*C/C++ example that extracts the DIRECTORY and FILENAME attributes of a given BFILE:

The oci.h header file is needed for the proper type resolution and compilation of the following OCIBFileLocator declaration:

    #include <oci.h>
    ...
    OCIBFileLocator *bfile ;
    char directory[31], filename[256] ;
    short d_ind, f_ind ;

Finally, select a BFILE locator from some LOB table and perform the DESCRIBE:

    EXEC SQL ALLOCATE :bfile ;
    EXEC SQL SELECT a_bfile INTO :bfile FROM lob_table WHERE ... ;
    EXEC SQL LOB DESCRIBE :bfile
       GET DIRECTORY, FILENAME INTO :directory:d_ind, :filename:f_ind ;

Indicator variables are only valid for use with the DIRECTORY and FILENAME attributes. These attributes are character strings whose values may be truncated if the host variable buffers used to hold their values aren't large enough. When truncation occurs, the value of the indicator will be set to the original length of the attribute.

### 16.5 LOBs and the Navigational Interface

The navigational interface can also be used to work with object types that contain LOBs as attributes.

**Related Topics**

- [Navigational Access to Objects](about-Objects.md)

#### 16.5.1 Transient Objects

Use the OBJECT CREATE statement to create transient and persistent objects with LOB attributes. You can ASSIGN a temporary LOB to the LOB attribute of a transient object, then copy the value to a permanent LOB or a LOB attribute of a persistent object to save the data. Or, ASSIGN the temporary LOB to the LOB attribute and use FLUSH to write the value to the database.

You can create a transient object with a BFILE attribute and read data from the BFILE on disk. Remember, temporary BFILEs are not supported.

#### 16.5.2 Persistent Objects

When you create a persistent object in the object cache that contains an internal LOB attribute, the LOB attribute is implicitly set to empty. You must first flush this object using the OBJECT FLUSH statement, thereby inserting a row into the table and creating an empty LOB. Once the object is refreshed in the object cache (using the VERSION=LATEST option), the real locator is read into the attribute.

When creating an object with a BFILE attribute, the BFILE is set to NULL. It must be updated with a valid directory alias and filename before the BFILE can be read.

A temporary LOB may be ASSIGNed to a LOB attribute of a persistent object. The actual LOB value will be copied when the object is flushed. A user may also explicitly copy a temporary LOB's value to a LOB attribute of a persistent object using the temporary LOB locator and a locator for the LOB attribute in a COPY statement.

#### 16.5.3 Navigational Interface Example

Use the OBJECT GET and SET statements to handle LOBs through the navigational interface.

You can retrieve a LOB locator that is an attribute of an object type and use it in any of the new embedded SQL LOB statements. Place LOB locators back into object types as attributes using the OBJECT SET statement.

Doing so is the same as a direct LOB ASSIGN operation. The same rules apply to an OBJECT GET or SET of a LOB attribute from or to an object type that would apply if a LOB ASSIGN had been performed instead, including type enforcement.

For example, suppose we had this simple type definition

    CREATE TYPE lob_type AS OBJECT (a_blob BLOB) ;

This example assumes that the type is a column in the database with a valid (and initialized) BLOB attribute.

The OTT-generated C structure usable by Pro\*C/C++ looks like this:

    struct lob_type
    {
       OCIBlobLocator *a_blob ;
    } ;
    typedef struct lob_type lob_type ;

You can write a Pro\*C/C++ program to extract the BLOB attribute and retrieve the BLOB's current length in a DESCRIBE statement. You can then TRIM the BLOB to half its size, setting the attribute back with a SET OBJECT and then make the change permanent with an OBJECT FLUSH.

First include oci.h and make some local variable declarations:

    #include <oci.h>
    lob_type *lob_type_p ;
    OCIBlobLocator *blob = (OCIBlobLocator *)0 ;
    unsigned int length ;

Select the BLOB attribute from the object, do an OBJECT GET, and do a DESCRIBE to get the current length of the BLOB:

    EXEC SQL ALLOCATE :blob ;
    EXEC SQL SELECT a_column
       INTO :lob_type_p FROM a_table WHERE ... FOR UPDATE ;
    EXEC SQL OBJECT GET a_blob FROM :lob_type_p INTO :blob ;
    EXEC SQL LOB DESCRIBE :blob GET LENGTH INTO :length ;

Cut the length in half and TRIM the BLOB to that new length:

    length = (unsigned int)(length / 2) ;
    EXEC SQL LOB TRIM :blob TO :length ;

Once the BLOB has been changed, set the BLOB attribute back into the object, FLUSH the change back to the server, and commit:

    EXEC SQL OBJECT SET a_blob OF :lob_type_p TO :blob ;
    EXEC SQL OBJECT FLUSH :lob_type_p ;
    EXEC SQL FREE :blob ;
    EXEC SQL COMMIT WORK ;

**See Also:**

[The Object Type Translator](the-Object-type.md) for information on creating an INTYPE file for OTT and running OTT.

### 16.6 LOB Program Examples

Here are two examples which show how to read and write BFILEs and BLOBs.

#### 16.6.1 READ a BLOB, Write a File Example

In this example we will be reading data from a BLOB with an unknown arbitrary length into a buffer and then writing the data from the buffer into an external file. Our buffer is small, so depending on the size of the BLOB we are reading, we may be able to read the BLOB value into the buffer in a single READ statement or we may be required to utilize a standard polling method instead.

First we start off with oci.h and some simple local variable declarations

    #include <oci.h>
    OCIBlobLocator *blob ;
    FILE *fp ;
    unsigned int amt, offset = 1 ;

Now we need a buffer to store the BLOB value and then write to the file from:

    #define MAXBUFLEN 5000
    unsigned char buffer[MAXBUFLEN] ;
    EXEC SQL VAR buffer IS RAW(MAXBUFLEN) ;

Allocate the BLOB host variable and select a BLOB which we will READ:

    EXEC SQL ALLOCATE :blob ;
    EXEC SQL SELECT a_blob INTO :blob FROM lob_table WHERE ... ;

We can then open the external file to which we will write the BLOB value:

    fp = fopen((const char *)"image.gif", (const char *)"w") ;

If the buffer can hold the entire LOB value in a single READ we need to catch the NOT FOUND condition to signal LOB READ termination:

    EXEC SQL WHENEVER NOT FOUND GOTO end_of_lob ;

Now do our first READ. We set the amount to the maximum value of 4 Gigabytes. It is larger than our buffer so if the LOB doesn't fit we will READ using a polling mode:

    amt = 4294967295 ;
    EXEC SQL LOB READ :amt FROM :blob AT :offset INTO :buffer ;

If we get here then it means that the buffer was not large enough to hold the entire LOB value, so we must write what we have using binary I/O and continue reading:

    (void) fwrite((void *)buffer, (size_t)MAXBUFLEN, (size_t)1, fp) ;

We use a standard polling method to continue reading with the LOB READ inside of an infinite loop. We can set up the NOT FOUND condition to terminate the loop:

    EXEC SQL WHENEVER NOT FOUND DO break ;
    while (TRUE)
      {

During polling, the offset is not used so we can omit it in subsequent LOB READs. We need the amount, however, because it will tell us how much was READ in the last READ invocation

        EXEC SQL LOB READ :amt FROM :blob INTO :buffer ;
        (void) fwrite((void *)buffer, (size_t)MAXBUFLEN, (size_t)1, fp) ;
      }

Here, we have reached the end of the LOB value. The amount holds the amount of the last piece that was READ. During polling, the amount for each interim piece was set to MAXBUFLEN, or the maximum size of our buffer:

    end_of_lob:
    (void) fwrite((void *)buffer, (size_t)amt, (size_t)1, fp) ;

The basic structure of this code should allow internal LOBs of arbitrary length to be READ into local buffers and then written to external files. It has been modeled after OCI and PL/SQL.

#### 16.6.2 Read a File, WRITE a BLOB Example

In this example we will be reading data from a file with a known arbitrary length into a buffer and then writing the data from the buffer into an internal BLOB. Our buffer is small, so depending on the size of the file we are reading, we may be able to write the file data into the LOB in a single WRITE or we may be required to utilize a standard polling method instead.

First we start off with oci.h and some simple local variable declarations

    #include <oci.h>
    OCIBlobLocator *blob ;
    FILE *fp ;
    unsigned int amt, offset = 1 ;
    unsigned filelen, remainder, nbytes ;
    boolean last ;

We need a buffer to store the file data and then write to the LOB:

    #define MAXBUFLEN 5000
    unsigned char buffer[MAXBUFLEN] ;
    EXEC SQL VAR buffer IS RAW(MAXBUFLEN) ;

We initialize an empty BLOB in an empty table and retrieve that BLOB into an ALLOCATEd locator and then fill it with the data from the file:

    EXEC SQL ALLOCATE :blob ;
    EXEC SQL INSERT INTO lob_table (a_blob) VALUES (EMPTY_BLOB())
       RETURNING a_blob INTO :blob ;

Open the binary file and determine its length. The total amount we write to our BLOB is the actual length of the binary file:

    fp = fopen((const char *)"image.gif", (const char *)"r") ;
    (void) fseek(fp, 0L, SEEK_END) ;
    filelen = (unsigned int)ftell(fp) ;
    amt = filelen ;

Set up our initial read of the file, determining the number of bytes to read based on our buffer size:

    if (filelen > MAXBUFLEN)
        nbytes = MAXBUFLEN ;
    else
        nbytes = filelen ;

Issue a file I/O operation to read `n` bytes of data from our file, `fp`, into our buffer and determine how much is left to read. Start reading from the beginning of the file:

    (void) fseek(fp, 0L, SEEK_SET) ;
    (void) fread((void *)buffer, (size_t)nbytes, (size_t)1, fp) ;
    remainder = filelen - nbytes ;

Based on what is left, either write the buffer in a single piece or initiate polling to write the data from the file in several smaller pieces:

         if (remainder == 0)
         {

In this case we can write the data in a single piece:

            EXEC SQL LOB WRITE ONE :amt
               FROM :buffer INTO :blob AT :offset ;
          }
         else
          {

Initiate the polling method for writing the data piece-wise into the LOB. First, to initiate the polling method, we use the FIRST orientation on the initial WRITE:

            EXEC SQL LOB WRITE FIRST :amt
               FROM :buffer INTO :blob AT :offset ;

Set up a simple loop to implement the polling method:

            last = FALSE ;
            EXEC SQL WHENEVER SQLERROR DO break ;
            do
              {

Calculate the number of bytes to read from the file and subsequently to WRITE into the destination LOB. Also determine if this will be our LAST piece:

                if (remainder > MAXBUFLEN)
                    nbytes = MAXBUFLEN ;
                else
                    {
                        nbytes = remainder ;
                        last = TRUE ;
                    }

Again read the next `nbytes` from the file on the file system into our buffer. If any error occurs during a file read, we automatically set the next WRITE to be the LAST one:

                if  fread((void *)buffer, (size_t)nbytes, (size_t)1, fp) != 1)
                   last = TRUE ;

At this point, either WRITE the LAST piece or an interim NEXT piece which would indicate that there is still data left to be processed from the file:

               if (last)
                 {
                   EXEC SQL LOB WRITE LAST :amt
                      FROM :buffer INTO :blob  ;
                 }

               else
                 {
                   EXEC SQL LOB WRITE NEXT :amt
                      FROM :buffer INTO :blob  ;
                 }
               remainder -= nbytes ;
              }
    while (!last && !feof(fp)) ;

This code example allows files of arbitrary length to be read into a local buffer and then written to a LOB. It has been modeled after OCI examples.

#### 16.6.3 lobdemo1.pc

This program, `lobdemo1.pc`, illustrates several LOB embedded SQL statements. The source code is in the `demo` directory. The application uses a table named `license_table` whose columns are social security number, name, and a CLOB containing text summarizing driving offenses. Several simplified SQL operations of a typical motor vehicle department are modeled.

The possible actions are:

- Add new records.

- List records by social security number.

- List information in a record, given a social security number.

- Append a new traffic violation to an existing CLOB's contents.

<!-- -->

    /***************************************************************************

      SCENARIO:

      We consider the example of a database used to store driver's
      licenses. The licenses are stored as rows of a table containing
      three columns: the sss number of a person, his name in text and the
      text summary of the info found in his license.

      The sss number is the driver's unique social security number.

      The name is the driver's given name as found on his ID card.

      The text summary is a summary of the information on the driver,
      including his driving record, which can be arbitrarily long and may
      contain comments and data regarding the person's driving ability.

      APPLICATION OVERVIEW:

      This example demonstrate how a Pro*C client can handle the new LOB
      datatypes through PL/SQL routines. Demonstrated are mechanisms for
      accessing and storing lobs to tables and manipulating LOBs through
      the stored procedures available through the dbms_lob package.

    ****************************************************************************/

    /***************************************************************************

       To run the demo:

       1. Execute the script, lobdemo1c.sql in SQL*Plus
       2. Precompile using Pro*C/C++
            proc lobdemo1 user=scott/tiger sqlcheck=full
       3. Compile/Link (This step is platform specific)

    ****************************************************************************/

    /*** The following will be added to the creation script for this example ***
     *** This code can be found in lobdemo1c.sql                 ***

    connect scott/tiger;

    set serveroutput on;

    Rem Make sure database has no license_table floating around

    drop table license_table;

    Rem ABSTRACTION:
    Rem A license table reduces the notion of a driver's license into three
    Rem distinct components - a unique social security number (sss),
    Rem a name (name), and a text summary of miscellaneous information.

    Rem IMPLEMENTATION:
    Rem Our implementation follows this abstraction

    create table license_table(
      sss char(9),
      name varchar2(50),
      txt_summary clob);

    insert into license_table
        values('971517006', 'Dennis Kernighan',
        'Wearing a Bright Orange Shirt - 31 Oct 1996');

    insert into license_table
        values('555001212', 'Eight H. Number',
        'Driving Under the Influence - 1 Jan 1997');

    insert into license_table
        values('010101010', 'P. Doughboy',
        'Impersonating An Oracle Employee - 10 Jan 1997');

    insert into license_table
        values('555377012', 'Calvin N. Hobbes',
        'Driving Under the Influence - 30 Nov 1996');

    select count(*) from license_table;

    Rem Commit to save
    commit;

    ****************************************************************************/

    /**************************
     * Begin lobdemo1.pc code *
     **************************/

    #define EX_SUCCESS       0
    #define EX_FAILURE       1

    #ifndef STDIO
    # include <stdio.h>
    #endif /* STDIO */

    #ifndef SQLCA_ORACLE
    # include <sqlca.h>
    #endif /* SQLCA_ORACLE */

    #ifndef OCI_ORACLE
    # include <oci.h>
    #endif /* OCI_ORACLE */

    #include <time.h>
    #include <string.h>
    #include <stdlib.h>
    #include <ctype.h>

    #ifndef LOBDEMO1_ORACLE
    # include "lobdemo1.h"
    #endif /* LOBDEMO1_ORACLE */

    /***********
     * Defines *
     ***********/
    #define SSS_LENGTH 12
    #define NAME_LENGTH 50 /* corresponds with max length of name in table */
    #define BUFLEN 1024
    #define MAXCRIME 5
    #define DATELENGTH 12

    /***********
     * Globals *
     ***********/

    char *CrimeList[MAXCRIME]={ "Driving Under the Influence",
                    "Grand Theft Auto",
                    "Driving Without a License",
                    "Impersonating an Oracle Employee",
                    "Wearing a Bright Orange Shirt" };

    char curdate[DATELENGTH];

    /***********************
     * Function prototypes *
     ***********************/

    #if defined(__STDC__)
      void GetDate( void );
      void PrintSQLError( void );
      void Driver( void );
      void ListRecords( void );
      void PrintCrime( OCIClobLocator *a_clob );
      void GetRecord( void );
      void NewRecord( void );
      char *NewCrime( void );
      void GetName( char *name_holder );
      void AppendToClob( OCIClobLocator *a_clob, char *charbuf );
      void AddCrime( void );
      void ReadClob( OCIClobLocator *a_clob );
      boolean GetSSS( char *suggested_sss );
    #else
      void GetDate();
      void PrintSQLError( );
      void Driver( );
      void ListRecords( );
      void PrintCrime(/* OCIClobLocator *a_clob */);
      void GetRecord( );
      void NewRecord( );
      char *NewCrime( );
      void GetName(/* char *name_holder */);
      void AppendToClob(/* OCIClobLocator *a_clob, char *charbuf */);
      void AddCrime();
      boolean GetSSS(/* char *suggested_sss */);
    #endif

    /*
     * NAME
     *   GetDate
     * DESCRIPTION
     *   Get date from user
     * LOB FEATURES
     *   none
     */

    void GetDate()
    {
      time_t now;

      now = time(NULL);
      strftime(curdate, 100, " - %d %b %Y", localtime(&now));
    }

    main()
    {
      char * uid = "scott/tiger";

      EXEC SQL WHENEVER SQLERROR DO PrintSQLError();

      printf("Connecting to license database account: %s \n", uid);
      EXEC SQL CONNECT :uid;

      GetDate();

      printf("\t*******************************\n");
      printf("\t* Welcome to the DMV Database *\n");
      printf("\t*******************************\n\n");
      printf("Today's Date is%s\n", curdate);

      Driver();

      EXEC SQL COMMIT RELEASE;

      return (EX_SUCCESS);
    }

    /*
     * NAME
     *   Driver
     * DESCRIPTION
     *   Command Dispatch Routine
     * LOB FEATURES
     *   none
     */

    void Driver()
    {
      char choice[20];
      boolean done = FALSE;

      while (!done)
      {
        printf("\nLicense Options:\n");
        printf("\t(L)ist available records by SSS number\n");
        printf("\t(G)et information on a particular record\n");
        printf("\t(A)dd crime to a record\n");
        printf("\t(I)nsert new record to database\n");
        printf("\t(Q)uit\n");
        printf("Enter your choice: ");

        fgets(choice, 20, stdin);
        switch(toupper(choice[0]))
        {
        case 'L':
          ListRecords();
          break;
        case 'G':
          GetRecord();
          break;
        case 'A':
          AddCrime();
          break;
        case 'I':
          NewRecord();
          break;
        case 'Q':
          done = TRUE;
          break;
        default:
          break;
        }
      }
    }

    /*
     * NAME
     *   ListRecords
     * DESCRIPTION
     *   List available records by sss number
     * LOB FEATURES
     *   none
     */

    void ListRecords()
    {
      char *select_sss = "SELECT SSS FROM LICENSE_TABLE";
      char sss[10];

      EXEC SQL PREPARE sss_exec FROM :select_sss;
      EXEC SQL DECLARE sss_cursor CURSOR FOR sss_exec;
      EXEC SQL OPEN sss_cursor;

      printf("Available records:\n");

      EXEC SQL WHENEVER NOT FOUND DO break;
      while (TRUE)
        {
          EXEC SQL FETCH sss_cursor INTO :sss;
          printf("\t%s\n", sss);
        }
      EXEC SQL WHENEVER NOT FOUND CONTINUE;

      EXEC SQL CLOSE sss_cursor;
    }

    /*
     * NAME
     *   PrintCrime
     * DESCRIPTION
     *   Tests correctness of clob
     * LOB FEATURES
     *   OCIlobRead and OCILobGetLength
     */

    void PrintCrime(a_clob)
      OCIClobLocator *a_clob;
    {
      ub4 lenp;

      printf("\n");
      printf("=====================\n");
      printf(" CRIME SHEET SUMMARY \n");
      printf("=====================\n\n");

      EXEC SQL LOB DESCRIBE :a_clob GET LENGTH INTO :lenp;

      if(lenp == 0) /* No crime on file */
        {
          printf("Record is clean\n");
        }
      else
        {
          ub4 amt = lenp;
          varchar *the_string = (varchar *)malloc(2 + lenp);

          the_string->len = (ub2)lenp;

          EXEC SQL WHENEVER NOT FOUND CONTINUE;
          EXEC SQL LOB READ :amt
            FROM :a_clob INTO :the_string WITH LENGTH :lenp;

          printf("%.*s\n", the_string->len, the_string->arr);
          free(the_string);
        }
    }

    /*
     * NAME
     *   GetRecord
     * DESCRIPTION
     *   Get license of single individual
     * LOB FEATURES
     *   allocate and select of blob and clob
     */

    void GetRecord()
    {
      char sss[SSS_LENGTH];

      if(GetSSS(sss) == TRUE)
        {
          OCIClobLocator *license_txt;
          char name[NAME_LENGTH]={'\0'};

          EXEC SQL ALLOCATE :license_txt;

          EXEC SQL SELECT name, txt_summary INTO :name, :license_txt
        FROM license_table WHERE sss = :sss;

          printf("========================================================\n\n");
          printf("NAME: %s\tSSS: %s\n", name, sss);
          PrintCrime(license_txt);
          printf("\n\n========================================================\n");

          EXEC SQL FREE :license_txt;
        }
      else
        {
          printf("SSS Number Not Found\n");
        }
    }

    /*
     * NAME
     *   NewRecord
     * DESCRIPTION
     *   Create new record in database
     * LOB FEATURES
     *   EMPTY_CLOB() and OCILobWrite
     */

    void NewRecord()
    {
      char sss[SSS_LENGTH], name[NAME_LENGTH] = {'\0'};

      if(GetSSS(sss) == TRUE)
        {
          printf("Record with that sss number already exists.\n");
          return;
        }
      else
        {
          OCIClobLocator *license_txt;

          EXEC SQL ALLOCATE :license_txt;

          GetName(name);

          EXEC SQL INSERT INTO license_table
        VALUES (:sss, :name, empty_clob());

          EXEC SQL SELECT TXT_SUMMARY INTO :license_txt FROM LICENSE_TABLE
        WHERE SSS = :sss;

          printf("========================================================\n\n");
          printf("NAME: %s\tSSS: %s\n", name, sss);
          PrintCrime(license_txt);
          printf("\n\n========================================================\n");

          EXEC SQL FREE :license_txt;
        }
    }

    /*
     * NAME
     *   NewCrime
     * DESCRIPTION
     *   Query user for new crime
     * LOB FEATURES
     *   None
     */

    char *NewCrime()
    {
      int  SuggestedCrimeNo;
      int  i;
      char crime[10];

      printf("Select from the following:\n");
      for(i = 1; i <= MAXCRIME; i++)
        printf("(%d) %s\n", i, CrimeList[i-1]);

      printf("Crime (1-5): ");
      fgets(crime, 10, stdin);
      SuggestedCrimeNo = atoi(crime);

      while((SuggestedCrimeNo < 1) || (SuggestedCrimeNo > MAXCRIME))
        {
          printf("Invalid selection\n");
          printf("Crime (1-5): ");
          fgets(crime, 10, stdin);
          SuggestedCrimeNo = atoi(crime);
        }

      return CrimeList[SuggestedCrimeNo-1];
    }

    /*
     * NAME
     *   AppendToClob
     * DESCRIPTION
     *   Append String charbuf to a Clob in the following way:
     *   if the contents of the clob a_clob were <foo> and the
     *   contents of charbuf were <bar>, after the append a_clob
     *   will contain: <foo>\n<bar> - <curdate>
     *   where <curdate> is today's date as obtained by the
     *   GetDate procedure.
     * LOB FEATURES
     *   OCILobWrite
     * NOTE
     *   Potentially, charbuf can be a very large string buffer.
     *   Furthermore, it should be noted that lobs and lob
     *   performance were designed for large data. Therefore,
     *   users are encouraged to read and write large chunks of
     *   data to lobs.
     */

    void AppendToClob(a_clob, charbuf)
      OCIClobLocator *a_clob;
      char *charbuf;
    {
      ub4 ClobLen, WriteAmt, Offset;
      int CharLen = strlen(charbuf);
      int NewCharbufLen = CharLen + DATELENGTH + 4;
      varchar *NewCharbuf;

      NewCharbuf = (varchar *)malloc(2 + NewCharbufLen);

      NewCharbuf->arr[0] = '\n';
      NewCharbuf->arr[1] = '\0';
      strcat((char *)NewCharbuf->arr, charbuf);
      NewCharbuf->arr[CharLen + 1] = '\0';
      strcat((char *)NewCharbuf->arr, curdate);

      NewCharbuf->len = NewCharbufLen;

      EXEC SQL LOB DESCRIBE :a_clob GET LENGTH INTO :ClobLen;

      WriteAmt = NewCharbufLen;
      Offset = ClobLen + 1;

      EXEC SQL LOB WRITE ONE :WriteAmt FROM :NewCharbuf
        WITH LENGTH :NewCharbufLen INTO :a_clob AT :Offset;

      free(NewCharbuf);
    }

    /*
     * NAME
     *   AddCrime
     * DESCRIPTION
     *   Add a crime to a citizen's crime file
     * LOB FEATURES
     *   OCILobWrite
     */

    void AddCrime()
    {
      char sss[SSS_LENGTH];

      if (GetSSS(sss) == TRUE)
        {
          OCIClobLocator *license_txt;
          char *crimebuf;
          char  name[NAME_LENGTH] = {'\0'};

          EXEC SQL ALLOCATE :license_txt;

          EXEC SQL SELECT txt_summary INTO :license_txt FROM license_table
        WHERE sss = :sss FOR UPDATE;

          crimebuf = NewCrime();

          printf("Added %s to CrimeList\n", crimebuf);
          AppendToClob(license_txt, crimebuf);

          EXEC SQL SELECT name INTO :name FROM license_table WHERE sss = :sss;

          printf("NAME: %s SSS: %s\n", name, sss);
          PrintCrime(license_txt);

          EXEC SQL COMMIT;
          EXEC SQL FREE :license_txt;
        }
      else
        {
          printf("SSS Number Not Found\n");
        }
    }

    /*
     * NAME
     *   GetSSS
     * DESCRIPTION
     *   Fills the passed buffer with a client-supplied social security number
     *   Returns FALSE if sss does not correspond to any entry in the database,
     *   else returns TRUE
     * LOB FEATURES
     *   none
     */

    boolean GetSSS(suggested_sss)
      char *suggested_sss;
    {
      int count = 0;
      int i;

      printf("Social Security Number: ");
      fgets(suggested_sss, SSS_LENGTH, stdin);

      for(i = 0; ((suggested_sss[i] != '\0') && (i < SSS_LENGTH)); i++)
        {
          if(suggested_sss[i] == '\n')
        suggested_sss[i]='\0';
        }

      EXEC SQL SELECT COUNT(*) INTO :count FROM license_table
        WHERE sss = :suggested_sss;

      return (count != 0);
    }

    /*
     * NAME
     *   GetName
     * DESCRIPTION
     *   Get name from user.
     *
     * LOB FEATURES
     *   none
     */

    void GetName(name_holder)
      char *name_holder;
    {
      int count=0;
      int i;

      printf("Enter Name: ");
      fgets(name_holder, NAME_LENGTH + 1, stdin);

      for(i = 0; name_holder[i] != '\0'; i++)
        {
          if(name_holder[i] == '\n')
        name_holder[i]='\0';
        }

      return;
    }

    /*
     * NAME
     *   PrintSQLError
     * DESCRIPTION
     *   Prints an error message using info in sqlca and calls exit.
     * COLLECTION FEATURES
     *   none
     */

    void PrintSQLError()
    {
      EXEC SQL WHENEVER SQLERROR CONTINUE;
      printf("SQL error occurred...\n");
      printf("%.*s\n", (int)sqlca.sqlerrm.sqlerrml,
             (CONST char *)sqlca.sqlerrm.sqlerrmc);
      EXEC SQL ROLLBACK RELEASE;
      exit(EX_FAILURE);
    }
