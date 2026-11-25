This chapter describes the support provided by embedded SQL statements for the LOB (Large Object) datatypes. The four types of LOBs are introduced and compared to the older LONG and LONG RAW datatypes.

The embedded SQL interface in Pro\*COBOL is shown to provide similar functionality to that of the PL/SQL language.

The LOB statements and their options and host variables are presented.

Last, an example of Pro\*COBOL programming using the LOB interface.

The main sections are:

- Using LOBs

- How to Use LOBs

- Rules for LOB Statements

- LOB Statements

- LOB Sample Program: LOBDEMO1.PCO

### 13.1 Using LOBs

LOBs (large objects) are database types that are used to store large amounts of data (maximum size is 4 Gigabytes) such as ASCII text, text in National Characters, files in various graphics formats, and sound wave forms.

#### 13.1.1 Internal LOBs

Internal LOBs (BLOBs, CLOBs, NCLOBs) are stored in database table spaces and have transactional support of the database server. (COMMITT, ROLLBACK, and so forth work with them.)

BLOBs (Binary LOBs) store unstructured binary (also called "raw") data, such as video clips.

CLOBs (Character LOBs) store large blocks of character data from the database character set.

NCLOBs (National Character LOBs) store large blocks of character data from the national character set.

#### 13.1.2 External LOBs

External LOBs are operating system files outside the database tablespaces, that have no transactional support from the database server.

BFILEs (Binary Files) store data in external binary files. A BFILE can be in GIF, JPEG, MPEG, MPEG2, text, or other formats.

#### 13.1.3 Security for BFILEs

The DIRECTORY object is used to access and use BFILEs. The DIRECTORY is a logical alias name (stored in the server) for the actual physical directory in the server file system containing the file. Users are permitted to access the file only if granted access privilege on the DIRECTORY object.

Two kinds of SQL statements can be used with BFILEs:

- The DDL (data definition language) SQL statements CREATE, REPLACE, ALTER, and DROP.

- The DML (Data Management Language) SQL statements are used to GRANT and REVOKE the READ system and object privileges on DIRECTORY objects.

A sample CREATE DIRECTORY directive is:

         EXEC SQL CREATE OR REPLACE DIRECTORY "Mydir" AS '/usr/home/mydir' END-EXEC.

Other users or roles can read the directory only if you grant them permission with a DML (Data Manipulation Language) statement, such as GRANT. For example, to allow user `scott` to read BFILES in directory `/usr/home/mydir`:

         EXEC SQL GRANT READ ON DIRECTORY "Mydir" TO scott END-EXEC.

Up to 10 BFILES can be opened simultaneously in one session. This default value can be changed by setting the SESSION_MAX_OPEN_FILES parameter.

See [Oracle Database Advanced Application Developer's Guide](../adfns/index.md) for more details on DIRECTORY objects and BFILE security, and the the GRANT command.

#### 13.1.4 LOBs Compared with LONG and LONG RAW

LOBs are different from the older LONG and LONG RAW datatypes in many ways.

- The maximum size of a LOB is 4 Gigabytes versus 2 Gigabytes for LONG and LONG RAW.

- You can use random as well as sequential access methods on LOBs; you can only use sequential access methods on LONG and LONG RAW.

- LOBs (except NCLOBs) can be attributes of an object type that you define.

- Tables can have multiple LOB columns, but can have only one LONG or LONG RAW column.

Migration of existing LONG and LONG Raw attributes to LOBs is recommended by Oracle. Oracle plans to end support of LONG and LONG RAW in future releases. See Also: [Oracle Database Upgrade Guide](../upgrd/index.md) for more information on migration, and [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/index.md) for more information on LOBs.

#### 13.1.5 LOB Locators

A LOB locator points to the actual LOB contents. The locator is returned when you retrieve the LOB, not the LOB's contents. LOB locators cannot be saved in one transaction or session and used again in a later transaction or session.

#### 13.1.6 Temporary LOBs

You can create temporary LOBs to assist your use of database LOBs. Temporary LOBs are like local variables and are not associated with any table. They are only accessible by their creator using their locators and are deleted when a session ends.

There is no support for temporary BFILES. Temporary LOBs are only permitted to be input variables (IN values) in the WHERE clause of an INSERT statement, in the SET clause of an UPDATE, or in the WHERE clause of a DELETE statement. Temporary LOBs have no transactional support from the database server, which means that you cannot do a COMMIT or ROLLBACK on them.

Temporary LOB locators can span transactions. They are deleted when the server abnormally terminates, and when an error is returned from a database SQL operation.

#### 13.1.7 LOB Buffering Subsystem

The LBS (LOB Buffering Subsystem) is an area of user memory provided for use as a buffer for one or more LOBs in the client's address space.

Buffering has these advantages, especially for applications on a client that does many small reads and writes to specific regions of the LOB:

- The LBS reduces round-trips to the server because you fill the buffer with multiple reads/writes to the LOBs, and then write to the server when a FLUSH directive is executed.

- Buffering also reduces the total number of LOB updates on the server. This creates better LOB performance and saves disk space.

Oracle provides a simple buffer subsystem, not a cache. Oracle does not guarantee that the contents of a buffer are always synchronized with the server LOB value. Use the FLUSH statement to actually write updates in the server LOB.

Buffered reads/writes of a LOB are performed through its locator. A locator enabled for buffering provides a consistent read version of the LOB until you perform a write through that locator.

After being used for a buffered WRITE, a locator becomes an updated locator and provides access to the latest LOB version as seen through the buffering subsystem. All further buffered WRITEs to the LOB can be done only through this updated locator. Transactions involving buffered LOB operations cannot migrate across user sessions.

The LBS is managed by the user, who is responsible for updating server LOB values by using FLUSH statements to update them. The LBS is single-user and single-threaded. Use ROLLBACK and SAVEPOINT actions to guarantee correctness in the server LOBs. Transactional support for buffered LOB operations is not guaranteed by Oracle. To ensure transactional semantics for buffered LOB updates, you must maintain logical savepoints to perform a rollback in the event of an error.

### 13.2 How to Use LOBs

There are two methods available to access LOBs in Pro\*COBOL:

- The DBMS_LOB package inside PL/SQL blocks.

- Embedded SQL statements.

The imbedded SQL statements are designed to give users a functional equivalent to the PL/SQL interface.

The following table compares LOB access in PL/SQL and embedded SQL statements in Pro\*COBOL. Dashes indicate missing functionality.

Table 13-1 LOB Access Methods

| PL/SQL(1)         | Pro\*COBOL Embedded SQL   |
|:------------------|:--------------------------|
| COMPARE()         | \-                        |
| INSTR()           | \-                        |
| SUBSTR()          | \-                        |
| APPEND()          | APPEND                    |
| :=                | ASSIGN                    |
| CLOSE()           | CLOSE                     |
| COPY()            | COPY                      |
| CREATETEMPORARY() | CREATE TEMPORARY          |
| \-                | DISABLE BUFFERING         |
| \-                | ENABLE BUFFERING          |
| ERASE()           | ERASE                     |
| GETCHUNKSIZE()    | DESCRIBE                  |
| ISOPEN()          | DESCRIBE                  |
| FILECLOSE()       | CLOSE                     |
| FILECLOSEALL()    | FILE CLOSE ALL            |
| FILEEXISTS()      | DESCRIBE                  |
| FILEGETNAME()     | DESCRIBE                  |
| FILEISOPEN()      | DESCRIBE                  |
| FILEOPEN()        | OPEN                      |
| BFILENAME()       | FILE SET<sup>Foot 2</sup> |
| \-                | FLUSH BUFFER              |
| FREETEMPORARY()   | FREE TEMPORARY            |
| GETLENGTH()       | DESCRIBE                  |
| =                 | \-                        |
| ISTEMPORARY()     | DESCRIBE                  |
| LOADFROMFILE()    | LOAD FROM FILE            |
| OPEN()            | OPEN                      |
| READ()            | READ                      |
| TRIM()            | TRIM                      |
| WRITE()           | WRITE                     |
| WRITEAPPEND()     | WRITE                     |

<sup>Footnote 1</sup> From dbmslob.sql. All routines are prefixed with 'DBMS_LOB.' except BFILENAME.

<sup>Footnote 2</sup>

The BFILENAME() built in SQL function may also be used.

**Note:**

You must explicitly lock the row before using any of the new statements that modify or change a LOB in any way. Operations that can modify a LOB value are APPEND, COPY, ERASE, LOAD FROM FILE, TRIM, and WRITE.

#### 13.2.1 LOB Locators in Your Application

To use LOB locators in your Pro\*COBOL application use these pseudo-types:

- SQL-BLOB

- SQL-CLOB

- SQL-NCLOB

- SQL-BFILE

For example, to declare an NCLOB variable called MY-NCLOB:

     01  MY-NCLOB    SQL-NCLOB.

#### 13.2.2 Initializing a LOB

This section discusses how to initialize different varieties of LOBs.

##### 13.2.2.1 Internal LOBs

To initialize a BLOB to empty, use the EMPTY_BLOB() function or use the ALLOCATE SQL statement. For CLOBs and NCLOBs, use the EMPTY_CLOB() function. See [Oracle Database SQL Language Reference](../sqlrf/index.md) for more about EMPTY_BLOB() and EMPTY_CLOB(). These functions are permitted only in the VALUES clause of an INSERT statement or as the source of the SET clause in an UPDATE statement.

For example:

         EXEC SQL INSERT INTO lob_table (a_blob, a_clob)
            VALUES (EMPTY_BLOB(), EMPTY_CLOB()) END-EXEC.

The ALLOCATE statement allocates a LOB locator and initializes it to empty, so, the following code is equivalent to the previous example:

    ...
     01  A-BLOB      SQL-BLOB.
     01  A-CLOB      SQL-CLOB.
    ...
         EXEC SQL ALLOCATE :A-BLOB END-EXEC.
         EXEC SQL ALLOCATE :A-CLOB END-EXEC.
         EXEC SQL INSERT INTO lob_table (a_blob, a_clob)
            VALUES (:A-BLOB, :A-CLOB) END-EXEC.

##### 13.2.2.2 External LOBs

Use the LOB FILE SET statement to initialize the DIRECTORY alias of the BFILE and FILENAME this way:

    ...
     01  ALIAS        PIC X(14) VARYING.
     01  FILENAME     PIC X(14) VARYING.
     01  A-BFILE      SQL-BFILE.
     ...
         MOVE "lob_dir" TO ALIAS-ARR.
         MOVE 7 TO ALIAS-LEN.
         MOVE "image.gif" TO FILENAME-ARR
         MOVE 9 TO FILENAME-LEN..
         EXEC SQL ALLOCATE :A-BFILE END-EXEC.
         EXEC SQL LOB FILE SET :A-BFILE
            DIRECTORY = :ALIAS, FILENAME = :FILENAME END-EXEC.
         EXEC SQL INSERT INTO file_table (a_bfile) VALUES (:A-BFILE) END-EXEC.

Refer to [Oracle Database Advanced Application Developer's Guide](../adfns/index.md) for a complete description of DIRECTORY object naming conventions and DIRECTORY object privileges.

Alternatively, you can use the BFILENAME('directory', 'filename') function in an INSERT or UPDATE statement to initialize a BFILE column or attribute for a particular row, and give the name of the actual physical directory and filename:

         EXEC SQL INSERT INTO file_table (a_bfile)
            VALUES (BFILENAME('lob_dir', 'image.gif'))
               RETURNING a_bfile INTO :A-BFILE END-EXEC.

**Note:**

BFILENAME() does not check permissions on the directory or filename, or whether the physical directory actually exists. Subsequent file accesses that use the BFILE locator will do those checks and return an error if the file is inaccessible.

##### 13.2.2.3 Temporary LOBs

A temporary LOB is initialized to empty when it is first created using the embedded SQL LOB CREATE TEMPORARY statement. The EMPTY_BLOB() and EMPTY_CLOB() functions cannot be used with temporary LOBs.

##### 13.2.2.4 Freeing LOBs

The FREE statement is used to free the memory used by an ALLOCATE statement:

    EXEC SQL FREE :A-BLOB END-EXEC.

### 13.3 Rules for LOB Statements

Here are the rules for using LOB statements:

#### 13.3.1 For All LOB Statements

These general restrictions and limitations apply when manipulating LOBs with the SQL LOB statements:

- The FOR clause is not allowed in embedded SQL LOB statements. Only one LOB locator can be used in those statement. However, the ALLOCATE and FREE statements do allow FOR clauses.

- Distributed LOBs are not supported. Although you may use the AT database clause in any of the new embedded SQL LOB statements, you cannot mix LOB locators that were created or allocated using different database connections in the same SQL LOB statement.

#### 13.3.2 For the LOB Buffering Subsystem

For the LBS, these rules must be followed:

- Errors in read or write accesses are reported at the next access to the server. Therefore, error recovery has to be coded by you, the user.

- When updating a LOB with buffered writes, do not update the same LOB with a method that bypasses the LOB Buffering Subsystem.

- An updated LOB locator enabled for buffering can be passed as an IN parameter to a PL/SQL procedure, but not as an IN OUT or OUT parameter. An error is returned. An error is also returned when there is an attempt to return an updated locator.

- An ASSIGN of an updated locator enabled for buffering to another locator is not allowed.

- You can append to the LOB value with buffered writes, but the starting offset must be one character after the end of the LOB. The LBS does not allow APPEND statements resulting in zero-byte fillers or spaces in LOBs in the database server.

- The character sets of the host locator bind variable and the database server CLOB must be the same.

- Only ASSIGN, READ and WRITE statements work with a locator enabled for buffering.

- The following statements result in errors when used with a locator enabled for buffering: APPEND, COPY, ERASE, DESCRIBE (LENGTH only), SELECT, and TRIM. Errors are also returned when you use these statements with a locator that is not enabled for buffering, if the LOB pointed to by the locator is being accessed in buffered mode by another locator.

**Note:**

The FLUSH statement must be used on a LOB enabled by the LOB Buffering Subsystem before

- Committing the transaction.

- Migrating from the current transaction to another.

- Disabling buffer operations on a LOB.

#### 13.3.3 For Host Variables

Use the following rules and notes for the LOB statements:

- src and dst can refer to either internal or external LOB locators, but file refers only to external locators.

- Numeric host values (`amt, src_offset, dst_offset`, and so forth.) are declared `as `a 4-byte integer variable, PIC S9(9) COMP. The values are restricted between 0 and 4 Gigabytes.

- The concept of NULL is part of a LOB locator. There is no need for indicator variables in the LOB statements. NULL cannot be used with numeric value variables such as `amt, src_offset`, and so forth and result in an error.

- The offset values `src_offset `and `dst_offset` have default values 1.

  **Note:**

  BLOB, CLOB, and NCLOB variables need to respect the alignment requirements of your platform. Refer to you platform documentation on alignment restrictions of your particular platform.

### 13.4 LOB Statements

The statements are presented alphabetically. In all the statements where it appears, database refers to a database connection

#### 13.4.1 APPEND

##### Purpose

The APPEND statement appends a LOB value at the end of another LOB.

##### Syntax

         EXEC SQL [AT [:]database] LOB APPEND :src TO :dst END-EXEC.

##### Host Variables

src (IN)
An internal LOB locator uniquely referencing the source LOB.

dsc (IN OUT)
An internal LOB locator uniquely referencing the destination LOB.

##### Usage Notes

The data is copied from the source LOB to the end of the destination LOB, extending the destination LOB up to a maximum of 4 Gigabytes. If the LOB is extended beyond 4 Gigabytes, an error will occur.

The source and destination LOBs must already exist and the destination LOB must be initialized.

Both the source and destination LOBs must be of the same internal LOB type. It is an error to have enabled LOB buffering for either type of locator.

#### 13.4.2 ASSIGN

##### Purpose

Assigns a LOB or BFILE locator to another.

##### Syntax

         EXEC SQL [AT [:]database] LOB ASSIGN :src to :dst END-EXEC.

##### Host Variables

src (IN)
LOB or BFILE locator source copied from.

dsc (IN OUT)
LOB or BFILE locator copied to.

##### Usage Notes

After the assignment, both locators refer to the same LOB value. The destination LOB locator must be a valid initialized (allocated) locator.

For internal LOBs, the source locator's LOB value is copied to the destination locator's LOB value only when the destination locator is stored in the table. For Pro\*COBOL, issuing a FLUSH of an object containing the destination locator will copy the LOB value.

An error is returned when a BFILE locator is assigned to an internal LOB locator and vice-versa. It is also an error if the src and dst LOBs are not of the same type.

If the source locator is for an internal LOB that was enabled for buffering, and the source locator has been used to modify the LOB value through the LOB Buffering Subsystem, and the buffers have not been flushed since the WRITE, then the source locator cannot be assigned to the destination locator. This is because only one locator for each LOB can modify the LOB value through the LOB Buffering Subsystem.

#### 13.4.3 CLOSE

##### Purpose

Close an open LOB or BFILE.

##### Syntax

         EXEC SQL [AT [:]database] LOB CLOSE :src END-EXEC.

##### Host Variables

src (IN OUT)
The locator of the LOB or BFILE to be closed.

##### Usage Notes

It is an error to close the same LOB twice either with different locators or with the same locator. For external LOBs, no error is produced if the BFILE exists but has not been opened.

It is an error to COMMIT a transaction before closing all previously opened LOBs. At transaction ROLLBACK time, all LOBs that are still open will be discarded without first being closed.

#### 13.4.4 COPY

##### Purpose

Copy all or part of a LOB value into a second LOB.

##### Syntax

         EXEC SQL [AT [:]database] LOB COPY :amt FROM :src [AT :src_offset]
            TO :dst [AT :dst_offset] END-EXEC.

##### Host Variables

##### amt (IN)

The maximum number of bytes for BLOBs, or characters for CLOBs and NCLOBs, to copy.

##### src (IN)

The locator of the source LOB.

##### src_offset (IN)

This is the number of characters for CLOB or NCLOB, and the number of bytes for a BLOB, starting from 1 at the beginning of the LOB.

##### dst (IN)

The locator of the destination LOB.

##### dst_offset (IN)

The destination offset. Same rules as for src_offset.

##### Usage Notes

If the data already exists at the destination's offset and beyond, it is overwritten with the source data. If the destination's offset is beyond the end of the current data, zero-byte fillers (BLOBs) or spaces (CLOBs) are written into the destination LOB from the end of the current data to the beginning of the newly written data from the source.

The destination LOB is extended to accommodate the newly written data if it extends beyond the current length of the destination LOB. It is a runtime error to extend this LOB beyond 4 Gigabytes.

It is also an error to try to copy from a LOB that is not initialized.

Both the source and destination LOBs must be of the same type. LOB buffering must not be enabled for either locator.

To make a temporary LOB permanent, the COPY statement must be used to explicitly COPY the temporary LOB into a permanent one.The `amt` variable indicates the maximum amount to copy. If the end of the source LOB is reached before the specified amount is copied, the operation terminates without an error.

#### 13.4.5 CREATE TEMPORARY

##### Purpose

Creates a temporary LOB.

##### Syntax

         EXEC SQL [AT [:]database] LOB CREATE TEMPORARY :src END-EXEC.

##### Host Variables

##### src (IN OUT)

Before execution, when IN,` src` is a LOB locator previously allocated.

After execution, when OUT, `src` is a LOB locator that will point to a new empty temporary LOB.

##### Usage Notes

After successful execution, the locator points to a newly created temporary LOB that resides on the database server independent of a table. The temporary LOB is empty and has zero length.

At the end of a session, all temporary LOBs are freed. Reads and Writes to temporary LOBs never go through the buffer cache.

#### 13.4.6 DISABLE BUFFERING

##### Purpose

Disables LOB buffering for the LOB locator.

##### Syntax

         EXEC SQL [AT [:]database] LOB DISABLE BUFFERING :src END-EXEC.

##### Host Variables

##### src (IN OUT)

An internal LOB locator.

##### Usage Notes

This statement does not support BFILEs. Subsequent reads or writes will not be done through the LBS.

Note: Use a FLUSH BUFFER command to make changes permanent, since the DISABLE BUFFERING statement does not implicitly flush the changes made in the LOB Buffering Subsystem.

#### 13.4.7 ENABLE BUFFERING

##### Purpose

Enables LOB buffering for the LOB locator.

##### Syntax

         EXEC SQL [AT [:]database] LOB ENABLE BUFFERING :src END-EXEC.

##### Host Variables

##### src (IN OUT)

An internal LOB locator.

##### Usage Notes

This statement does not support BFILEs. Subsequent reads and writes are done through the LBS.

#### 13.4.8 ERASE

##### Purpose

Erases a given amount of LOB data starting from a given offset.

##### Syntax

         EXEC SQL [AT [:]database] LOB ERASE :amt
            FROM :src [AT :src_offset] END-EXEC.

##### Host Variables

##### amt (IN OUT)

The input is the number of bytes or characters to erase. The returned output is the actual number erased.

##### src (IN OUT)

An internal LOB locator.

##### src_offset (IN)

The offset from the beginning of the LOB, starting from 1.

##### Usage Notes

This statement does not support BFILEs.

After execution, amt returns the actual number of characters/bytes that were erased. The actual number and requested number will differ if the end of the LOB value is reached before erasing the requested number of characters/bytes. If the LOB is empty, amt will indicate that 0 characters/bytes were erased.

For BLOBs, erasing means zero-byte fillers overwrite the existing LOB value. For CLOBs, erasing means that spaces overwrite the existing LOB value.

#### 13.4.9 FILE CLOSE ALL

##### Purpose

Closes all BFILES opened in the current session.

##### Syntax

         EXEC SQL [AT [:]database] LOB FILE CLOSE ALL END-EXEC.

##### Usage Notes

If there are any open files in the session whose closure has not been handled properly, you can use the FILE CLOSE ALL statement to close all files opened in the session and resume file operations from the beginning.

#### 13.4.10 FILE SET

##### Purpose

Sets DIRECTORY alias and FILENAME in a BFILE locator.

##### Syntax

         EXEC SQL [AT [:]database] LOB FILE SET :file
            DIRECTORY = :alias, FILENAME = :filename END-EXEC.

##### Host Variables

##### file (IN OUT)

BFILE locator where the DIRECTORY alias and FILENAME is set.

##### alias (IN)

DIRECTORY alias name to set.

##### filename (IN)

The FILENAME to set.

##### Usage Notes

The given BFILE locator must be first ALLOCATEd prior to its use in this statement.

Both the DIRECTORY alias name and FILENAME must be provided.

The maximum length of the DIRECTORY alias is 128 bytes. The maximum length of the FILENAME is 255 bytes.

The only external datatypes supported for use with the DIRECTORY alias name and FILENAME attributes are VARCHAR, VARCHAR2 and CHARF.

It is an error to use this statement with anything but an external LOB locator.

#### 13.4.11 FLUSH BUFFER

##### Purpose

Writes this LOB's buffers to the database server.

##### Syntax

         EXEC SQL [AT [:]database] LOB FLUSH BUFFER :src [FREE] END-EXEC.

##### Host Variables

##### src (IN OUT)

Internal LOB locator.

##### Usage Notes

Writes the buffer data to the database LOB in the server from the LOB referenced by the input locator.

LOB buffering must have already been enabled for the input LOB locator.

The FLUSH operation, by default, does not free the buffer resources for reallocation to another buffered LOB operation. However, if you want to free the buffer explicitly, you can include the optional FREE keyword to so indicate.

#### 13.4.12 FREE TEMPORARY

##### Purpose

Free the temporary space for the LOB locator.

##### Syntax

         EXEC SQL [AT [:]database] LOB FREE TEMPORARY :src END-EXEC.

##### Host Variables

##### src (IN OUT)

The LOB locator pointing to the temporary LOB.

##### Usage Notes

The input locator must point to a temporary LOB. The output locator is marked not initialized and can be used in subsequent LOB statements.

#### 13.4.13 LOAD FROM FILE

##### Purpose

Copy all or a part of a BFILE into an internal LOB.

##### Syntax

         EXEC SQL [AT [:]database] LOB LOAD :amt
            FROM FILE :file [AT :src_offset] INTO :dst [AT :dst_offset] END-EXEC.

##### Host Variables

##### amt (IN)

Maximum number of bytes to be loaded.

##### file (IN OUT)

The source BFILE locator.

##### src_offset (IN)

The number of bytes offset from the beginning of the file, starting from 1.

##### dst (IN OUT)

The destination LOB locator which can be BLOB, CLOB, be NCLOB.

##### dst_offset (IN)

The number of bytes (for BLOBs) or characters (CLOBs and NCLOBs) from the beginning of the destination LOB where writing will begin. It starts at 1.

##### Usage Notes

The data is copied from the source BFILE to the destination internal LOB. No character set conversions are performed when copying the BFILE data to a CLOB or NCLOB. Therefore, the BFILE data must already be in the same character set as the CLOB or NCLOB in the database.

The source and destination LOBs must already exist. If the data already exists at the destination's start position, it is overwritten with the source data. If the destination's start position is beyond the end of the current data, zero-byte fillers (BLOBs) or spaces (CLOBs and NCLOBs) are written into the destination LOB from the end of the data to the beginning of the newly written data from the source.

The destination LOB is extended to accommodate the newly written data if it extends beyond the current length of the destination LOB. It is an error to extend this LOB beyond 4 Gigabytes.

It is also an error to copy from a BFILE that is not initialized.

The amount parameter indicates the maximum amount to load. If the end of the source BFILE is reached before the specified amount is loaded, the operation terminates without error.

#### 13.4.14 OPEN

##### Purpose

Open a LOB or BFILE for read or read/write access.

##### Syntax

         EXEC SQL [AT [:]database] LOB OPEN :src
            [ READ ONLY | READ WRITE ] END-EXEC.

##### Host Variables

##### src (IN OUT)

LOB locator of the LOB or BFILE.

##### Usage Notes

The default mode in which a LOB or BFILE can be Opened is for READ ONLY access.

For internal LOBs, being OPEN is associated with the LOB, not with the locator. Assigning an already Opened locator to another locator does not count as OPENing a new LOB. Instead, both locators refer to the same LOB. For BFILEs, being OPEN is associated with the locator.

Only 32 LOBs can be OPEN at any one time. An error will be returned when the 33rd LOB is Opened.

There is no support for writable BFILEs. Therefore, when you OPEN a BFILE in READ WRITE mode, an error is returned.

It is also an error to open a LOB in READ ONLY mode and then attempt to WRITE to the LOB.

#### 13.4.15 READ

##### Purpose

Reads all or part of a LOB or BFILE into a buffer.

##### Syntax

         EXEC SQL [AT [:]database] LOB READ :amt FROM :src [AT :src_offset]
            INTO :buffer [WITH LENGTH :buflen] END-EXEC.

##### Host Variables

##### amt (IN OUT)

The input is the number of characters or bytes to be read. The output is the actual number of characters or bytes that were read.

If the amount of bytes to be read is larger than the buffer length it is assumed that the LOB is being READ in a polling mode. On input if this value is 0, then the data will be read in a polling mode from the input offset until the end of the LOB.

The number of bytes or characters actually read is returned in `amt.` If the data is read in pieces, `amt` will always contain the length of the last piece read.

When the end of a LOB is reached an ORA-1403: no data found error will be issued.

When reading in a polling mode, the application must invoke the LOB READ repeatedly to read more pieces of the LOB until no more data is left. Control the use of the polling mode with the NOT FOUND condition in a WHENEVER directive to catch the ORA-1403 error.

##### src (IN)

The LOB or BFILE locator.

##### src_offset (IN)

This is the absolute offset from the beginning of the LOB value from which to start reading. For character LOBs it is the number of characters from the beginning of the LOB. For binary LOBs or BFILEs it is the number of bytes. The first position is 1.

##### buffer (IN OUT)

A buffer into which the LOB data will be read. The external datatype of the buffer is restricted to only a few types depending on the type of the source LOB. The maximum length of the buffer depends on the external datatype being used to store the LOB value. The following table summarizes the legal external datatypes and their corresponding maximum lengths categorized by source LOB type:

Table 13-2 Source LOB and Precompiler Datatypes

| External LOB(3) | Internal LOB | Precompiler External Datatype            | Precompiler Maximum Length (4)             | PL/SQL Datatype | PL/SQL Maximum Length |
|:----------------|:-------------|:-----------------------------------------|:-------------------------------------------|:----------------|:----------------------|
| BFILE           | BLOB         | RAW<br>VARRAW<br>LONG RAW<br>LONG VARRAW | 65535<br>65533<br>2147483647<br>2147483643 | RAW             | 32767                 |
| \-              | CLOB         | VARCHAR2<br>VARCHAR<br>LONG VARCHAR      | 65535<br>65533<br>2147483643               | VARCHAR2        | 32767                 |
| \-              | NCLOB        | NVARCHAR2                                | 4000                                       | NVARCHAR2       | 4000                  |

<sup>Footnote 3</sup> Any of the external datatypes shown can be used with BFILES.

<sup>Footnote 4</sup> Lengths are measured in bytes, not characters.

##### buflen (IN)

Specifies the length of the given buffer when it cannot be determined otherwise.

##### Usage Notes

A BFILE must already exist on the database server and must have been opened using the input locator. The database must have permission to read the file and the user must have read permission on the directory.

It is an error to try to read from an un-initialized LOB or BFILE.

The length of the buffer is determined this way:

- From `buflen`, when the WITH LENGTH clause is present.

- In the absence of the WITH LENGTH clause, the length is determined by treating the buffer host variable in OUT mode according to the rules in “Handling Character Data”.

**Related Topics**

- [Handling Character Data](datatypes-and-host-variables.md)

#### 13.4.16 TRIM

##### Purpose

Truncates the LOB value.

##### Syntax

         EXEC SQL [AT [:]database] LOB TRIM :src TO :newlen END-EXEC.

##### Host Variables

##### src (IN OUT)

LOB locator for internal LOB.

##### newlen (IN)

The new length of the LOB value.

##### Usage Notes

This statement is not for BFILES. The new length cannot be greater than the current length, or an error is returned.

#### 13.4.17 WRITE

##### Purpose

Writes the contents of a buffer to a LOB.

##### Syntax

         EXEC SQL [AT [:]database] LOB WRITE [APPEND] [ FIRST | NEXT | LAST | ONE ]
            :amt FROM :buffer [WITH LENGTH :buflen]
               INTO :dst [AT :dst_offset] END-EXEC.

##### Host Variables

##### amt (IN OUT)

The input is the number of characters or bytes to be written.

The output is the actual number of characters or bytes that is written.

When writing using a polling method, `amt` will return the cumulative total length written for the execution of the WRITE statement after a WRITE LAST is executed. If the WRITE statement is interrupted, `amt` will be undefined.

##### buffer (IN)

A buffer from which the LOB data is written. See “READ” for the lengths of datatypes.

##### dst (IN OUT)

The LOB locator.

##### dst_offset (IN)

The offset from the beginning of the LOB (counting from 1), in characters for CLOBs and NCLOBs, in bytes for BLOBs.

##### buflen (IN)

The buffer length when it cannot be calculated in any other way.

##### Usage Notes

If LOB data already exists, it is overwritten with the data stored in the buffer. If the offset specified is beyond the end of the data currently in the LOB, zero-byte fillers or spaces are inserted into the LOB.

Specifying the keyword APPEND in the WRITE statement causes the data to automatically be written to the end of the LOB. When APPEND is specified, the destination offset is assumed to be the end of the LOB. It is an error to specify the destination offset when using the APPEND option in the WRITE statement.

The buffer can be written to the LOB in one piece (using the ONE orientation which is the default) or it can be provided piece-wise using a standard polling method.

Polling is begun by using FIRST, then NEXT to write subsequent pieces. The LAST keyword is used to write the final piece that terminates the write.

Using this piece-wise write mode, the buffer and the length can be different in each call if the pieces are of different sizes and from different locations.

If the total amount of data passed to Oracle is less than the amount specified by the `amt` parameter after doing all the writes, an error results.

The same rules apply for determining the buffer length as in the READ statement. See “READ”.

**Related Topics**

- READ

#### 13.4.18 DESCRIBE

##### Purpose

This is a statement that is equivalent to several OCI and PL/SQL statements. Use the LOB DESCRIBE SQL statement to retrieve attributes from a LOB. The LOB DESCRIBE statement has this format:

##### Syntax

         EXEC SQL [AT [:]database] LOB DESCRIBE :src GET attribute1 [{, attributeN}]
            INTO :hv1 [[INDICATOR] :hv_ind1] [{, :hvN [[INDICATOR] :hv_indN] }]
               END-EXEC.

where an attribute can be any of these choices:

    CHUNKSIZE | DIRECTORY | FILEEXISTS | FILENAME | ISOPEN | ISTEMPORARY | LENGTH

##### Host Variables

##### src (IN)

The LOB locator of an internal or external LOB.

##### hv1 ... hvN (OUT)

The host variables that receive the attribute values, in the order specified in the attribute name list.

##### hv_ind1 ... hv_indN (OUT)

Optional host variables that receive the indicator NULL status in the order of the attribute name list.

The following table describes the attributes, which LOB it is associated with, and the COBOL types into which they should be read:

Table 13-3 LOB Attributes

| LOB Attribute | Attribute Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Restrictions                 | COBOL Type           |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------|:---------------------|
| CHUNKSIZE     | The optimum amount (in bytes for BLOBs and characters for CLOBs/NCLOBs) of space of a given tablespace block, which is used to store the LOB value. Chunk sizes are not fixed and the maximum possible value based on the available chunk sizes is used for storage. If you make multiple WRITE requests on the same page or set of pages, data is written to the disk only when committed and is treated as a single modification. This allows for data being written in larger chunk sizes. | BLOBs, CLOBs and NCLOBs only | PIC S9(9) COMP       |
| DIRECTORY     | The name of the DIRECTORY alias for the BFILE. The length, n, is between 1 and 128 bytes. Use that length in the picture.                                                                                                                                                                                                                                                                                                                                                                     | FILE LOBs only               | PIC X(n) \[VARYING\] |
| FILEEXISTS    | Determines whether or not the BFILE exists on the server's operating system file system. FILEEXISTS is true when it is nonzero; false when it equals 0.                                                                                                                                                                                                                                                                                                                                       | FILE LOBs only               | PIC S9(9) COMP       |
| FILENAME      | The name of the BFILE. The length, n, is between 1 and 255 bytes. Use that length in the picture.                                                                                                                                                                                                                                                                                                                                                                                             | FILE LOBs only               | PIC X(n) \[VARYING\] |
| ISOPEN        | For BFILEs, if the input BFILE locator was never used in an OPEN statement, the BFILE is considered not to be OPENed by this locator. However, a different BFILE locator may have OPENed the BFILE. More than one OPEN can be performed on the same BFILE using different locators. For LOBs, if a different locator opened the LOB, the LOB is still considered to be OPEN by the input locator. ISOPEN is true when it is nonzero; false when it equals 0.                                  | \-                           | PIC S9(9) COMP       |
| ISTEMPORARY   | Determines whether or not the input LOB locator refers to a temporary LOB or not. ISTEMPORARY is true when it is nonzero; false when it equals 0.                                                                                                                                                                                                                                                                                                                                             | BLOBs, CLOBs and NCLOBs only | PIC S9(9) COMP       |
| LENGTH        | Length of BLOBs and BFILEs in bytes, CLOBs and NCLOBs in characters. For BFILEs, the length includes EOF if it exists. Empty internal LOBs have zero length. LOBs/BFILEs that are not initialized have undefined length.                                                                                                                                                                                                                                                                      | \-                           | PIC 9(9) COMP        |

##### Usage Notes

Indicator variables should be declared as PIC S9(4) COMP. After execution has completed, SQLERRD(3) contains the number of attributes retrieved without error. If there was an execution error, the attribute at which it occurred is one more than the contents of SQLERRD(3).

##### DESCRIBE Example

Here is a simple Pro\*COBOL example that extracts the DIRECTORY and FILENAME attributes of a given BFILE:

    ...
     01  A-BFILE      SQL-BFILE.
     01  DIRECTORY    PIC X(30) VARYING.
     01  FILENAME     PIC X(30) VARYING.
     01  D-IND        PIC S9(4) COMP.
     01  F-IND        PIC S9(4) COMP.
     01  FEXISTS      PIC S9(9) COMP.
     01  ISOPN        PIC S9(9) COMP.
    ...

Finally, select a BFILE locator from some LOB table and do the DESCRIBE:

         EXEC SQL ALLOCATE :A-BFILE END-EXEC.
         EXEC SQL INSERT INTO lob_table (a_bfile) VALUES (BFILENAME ('lob.dir',
            'image.gif')) END-EXEC.
         EXEC SQL SELECT a_bfile INTO :A-BFILE FROM lob_table WHERE ... END-EXEC.
         EXEC SQL DESCRIBE :A-BFILE GET DIRECTORY, FILENAME, FILEEXISTS, ISOPEN
            INTO :DIRECTORY:D-IND, :FILENAME:F-IND, FEXISTS, ISOPN ND-EXEC.

Indicator variables are valid for use only with the DIRECTORY and FILENAME attributes. These attributes are character strings whose values may be truncated if the host variable buffers used to hold their values are not large enough. When truncation occurs, the value of the indicator will be set to the original length of the attribute.

#### 13.4.19 READ and WRITE Using the Polling Method

Here is an outline of using READ with the polling method:

Start the read polling by setting the amount to zero in the first LOB READ (or set the amount to the size of the total data to be read). The amount is first set to zero in this case outline which omits details:

          EXEC SQL ALLOCATE :CLOB1 END-EXEC.

          EXEC SQL WHENEVER NOT FOUND GOTO END-OF-CLOB END-EXEC.

          EXEC SQL SELECT A_CLOB INTO :CLOB1 FROM LOB_TABLE WHERE ... END-EXEC.

          MOVE 0 TO AMT.
          EXEC SQL LOB READ :AMT FROM :VLOB1 AT :OFFSET INTO :BUFFER END-EXEC.

     READ-LOOP.
          EXEC SQL LOB READ :AMT FROM :CLOB1 INTO BUFFER $END-EXEC.
          GO TO READ-LOOP.

     END-OF-CLOB.
          EXEC SQL WHENEVER NOT FOUND CONTINUE END-EXEC.

          EXEC SQL FREE :CLOB1 END-EXEC.

The following code outline writes data from a buffer into an internal CLOB. The value of AMT (16 characters) in the initial write statement should be the length of the entire data you will write. The buffer is 5 characters long.

If EOF is read in the initial read, then do the LOB WRITE ONE. If not, start polling with a LOB WRITE FIRST of the buffer. Read the data, and do a LOB WRITE NEXT of the output. No offset is needed in the LOB WRITE NEXT because data is written at the end of the last write. After EOF is read, break out of the read loop and do a LOB WRITE LAST. The amount returned must equal the initial amount value (16).

         MOVE 16 TO AMT.
         PERFORM READ-NEXT-RECORD.
         MOVE INREC TO BUFFER-ARR.
         MOVE 5 TO BUFFER-LEN.
         IF (END-OF-FILE = "Y")
             EXEC SQL LOB WRITE ONE :AMT FROM :BUFFER INTO CLOB1
                AT :OFFSET END-EXEC.
             PERFORM DISPLAY-CLOB
         ELSE
             EXEC SQL LOB WRITE FIRST :AMT FROM :BUFFER INTO :CLOB1
                AT :OFFSET END-EXEC.
         PERFORM READ-NEXT-RECORD.
         PERFORM WRITE-TO-CLOB
            UNTIL END-OF-FILE = "Y".
         MOVE INREC TO BUFFER-ARR.
         MOVE 1 TO BUFFER-LEN.
         EXEC SQL LOB WRITE LAST :AMT FROM :BUFFER INTO :CLOB1 END-EXEC.
         PERFORM DISPLAY-CLOB.
         ...
     WRITE-TO-CLOB.
         MOVE INREC TO BUFFER-ARR.
         MOVE 5 TO BUFFER-LEN.
         EXEC SQL LOB WRITE NEXT :AMT FROM :BUFFER INTO :CLOB1 END-EXEC.
         PERFORM READ-NEXT RECORD.

     READ-NEXT-RECORD.
         MOVE SPACES TO INREC.
         READ INFILE NEXT RECORD
            AT END
            MOVE "Y" TO END-OF-FILE.
     ...

### 13.5 LOB Sample Program: LOBDEMO1.PCO

The LOBDEMO1.PCO program illustrates several LOB embedded SQL statements. The source code is in your `demo` directory. The application uses a table named `license_table` whose columns are social security number, name, and a CLOB containing text summarizing driving offenses. Several simplified SQL operations of a typical motor vehicle department are modeled.

The possible actions are:

- Add new records.

- List records by social security number.

- List information in a record, given a social security number.

- Append a new traffic violation to an existing CLOB's contents.

Here is the listing of LOBDEMO1.PCO:

          *********************************************************************
          * LOB Demo 1: DMV Database                                          *
          *                                                                   *
          * SCENARIO:                                                         *
          *                                                                   *
          * We consider the example of a database used to store driver's      *
          * licenses. The licenses are stored as rows of a table containing   *
          * three columns: the sss number of a person, his/her name and the   *
          * text summary of the info found in his license.                    *
          *                                                                   *
          * The sss number and the name are the unique social security number *
          * and name of an individual.  The text summary is a summary of the  *
          * information on the individual, including his driving record,      *
          * which can be arbitrarily long and may contain comments and data   *
          * regarding the person's driving ability.                           *
          *                                                                   *
          * APPLICATION OVERVIEW:                                             *
          *                                                                   *
          * This example demonstrate how a Pro*COBOL client can handle the    *
          * new LOB datatypes.  Demonstrated are the mechanisms for accessing *
          * and storing lobs to/from tables.                                  *
          *                                                                   *
          *  To run the demo:                                                 *
          *                                                                   *
          *  1. Execute the script, lobdemo1.sql in Server Manager            *
          *  2. Precompile using Pro*COBOL                                    *
          *       procob lobdemo1                                             *
          *  3. Compile/Link (This step is platform specific)                 *
          *                                                                   *
          * lobdemo1.sql contains the following SQL statements:               *
          *                                                                   *
          * connect scott/tiger;                                              *
          *                                                                   *
          * drop table license_table;                                         *
          *                                                                   *
          * create table license_table(                                       *
          * sss char(9),                                                      *
          * name varchar2(50),                                                *
          * txt_summary clob);                                                *
          *                                                                   *
          * insert into license_table                                         *
          *  values('971517006', 'Dennis Kernighan',                          *
          *  'Wearing a Bright Orange Shirt');                                *
          *                                                                   *
          * insert into license_table                                         *
          *  values('555001212', 'Eight H. Number',                           *
          *  'Driving Under the Influence');                                  *
          *                                                                   *
          * insert into license_table                                         *
          *  values('010101010', 'P. Doughboy',                               *
          *  'Impersonating An Oracle Employee');                             *
          *                                                                   *
          * insert into license_table                                         *
          *  values('555377012', 'Calvin N. Hobbes',                          *
          *  'Driving Under the Influence');                                  *
          *                                                                   *
          * The main program provides the menu of actions that can be         *
          * performed.  The program stops when the number 5 (Quit) option     *
          * is entered.  Depending on the input, this main program calls      *
          * the appropriate nested program to execute the chosen action.      *
          *                                                                   *
          *********************************************************************
           IDENTIFICATION DIVISION.
           PROGRAM-ID.  LOBDEMO1.
           DATA DIVISION.
           WORKING-STORAGE SECTION.
           01  USERNAME       PIC X(5).
           01  PASSWD         PIC X(5).
           01  CHOICE         PIC 9 VALUE 0.
           01  SSS            PIC X(9).
           01  SSSEXISTS      PIC 9 VALUE ZERO.
           01  LICENSE-TXT    SQL-CLOB .
           01  NEWCRIME       PIC X(35) VARYING.
           01  SSSCOUNT       PIC S9(4) COMP.
           01  THE-STRING    PIC X(200) VARYING.
           01  TXT-LENGTH    PIC S9(9) COMP.
           01  CRIMES.
               05 FILLER PIC X(35) VALUE "Driving Under the Influence".
               05 FILLER PIC X(35) VALUE "Grand Theft Auto".
               05 FILLER PIC X(35) VALUE "Driving Without a License".
               05 FILLER PIC X(35) VALUE
                      "Impersonating an Oracle Employee".
               05 FILLER PIC X(35) VALUE "Wearing a Bright Orange Shirt".
           01  CRIMELIST REDEFINES CRIMES.
               05 CRIME  PIC X(35) OCCURS 5 TIMES.
           01  CRIME-INDEX   PIC 9.
           01  TXT-LEN       PIC S9(9) COMP.
           01  CRIME-LEN     PIC S9(9) COMP.
           01  NAME1         PIC X(50) VARYING.
           01  NEWNAME         PIC X(50).
          *********************************************************************

               EXEC SQL INCLUDE SQLCA END-EXEC.

           PROCEDURE DIVISION.
           A000-CONTROL SECTION.
          *********************************************************************
          *  A000-CONTROL
          *     Overall control section
          *********************************************************************
           A000-CNTRL.
                  EXEC SQL
            WHENEVER SQLERROR DO PERFORM Z900-SQLERROR
              END-EXEC.
                  PERFORM B000-LOGON.
              PERFORM C000-MAIN UNTIL CHOICE = 5.
              PERFORM D000-LOGOFF.
           A000-EXIT.
              STOP RUN.

           B000-LOGON SECTION.
          *********************************************************************
          *  B000-LOGON
          *    Log on to database.
          *********************************************************************
           B000-LGN.
               DISPLAY '**************************************************'.
               DISPLAY '*            Welcome to the DMV Database         *'.
               DISPLAY '**************************************************'.
               MOVE "scott" TO USERNAME.
               MOVE "tiger" TO PASSWD.
               EXEC SQL
                  CONNECT :USERNAME IDENTIFIED BY :PASSWD
               END-EXEC.
               DISPLAY " ".
               DISPLAY "Connecting to license database account:  ",
                  USERNAME, "/", PASSWD.
               DISPLAY " ".
           B000-EXIT.
               EXIT.
           C000-MAIN SECTION.
          *********************************************************************
          *  C000-MAIN
          *    Display the main menu and action requests
          *********************************************************************
           C000-MN.

               DISPLAY " ".
               DISPLAY "License Options:".
               DISPLAY "1. List available records by SSS number".
               DISPLAY "2. Get information on a particular record".
               DISPLAY "3. Add crime to a record".
               DISPLAY "4. Insert new record to database".
               DISPLAY "5. Quit".
               DISPLAY " ".

               MOVE ZERO TO CHOICE.
               PERFORM Z300-ACCEPT-CHOICE UNTIL CHOICE < 6
                                       AND CHOICE > 0.
               IF (CHOICE = 1)
                  PERFORM C100-LIST-RECORDS.
               IF (CHOICE = 2)
                   PERFORM C200-GET-RECORD.
               IF (CHOICE = 3)
                   PERFORM C300-ADD-CRIME.
               IF (CHOICE = 4)
                   PERFORM C400-NEW-RECORD.
            C000-EXIT.
           EXIT.

            C100-LIST-RECORDS SECTION.
          *********************************************************************
          *  C100-LIST-RECORDS
          *   Select  Social Security Numbers from LICENCSE_TABLE
          *   and display the list
          *********************************************************************
            C100-LST.

               EXEC SQL DECLARE SSS_CURSOR CURSOR FOR
                SELECT SSS FROM LICENSE_TABLE
               END-EXEC.

               EXEC SQL OPEN SSS_CURSOR END-EXEC.

               DISPLAY "Available records:".

               PERFORM C110-DISPLAY-RECORDS UNTIL SQLCODE = 1403.
               EXEC SQL CLOSE SSS_CURSOR END-EXEC.
           C100-EXIT.
               EXIT.
           C110-DISPLAY-RECORDS SECTION.
          *********************************************************************
          *  C110-DISPLAY-RECORDS
          *    Fetch the next record from the cursor and display it.
          *********************************************************************
           C110-DSPLY.
                EXEC SQL FETCH SSS_CURSOR INTO :SSS END-EXEC.
                IF SQLCODE = 0 THEN
                    DISPLAY SSS.
           C110-EXIT.
                EXIT.

           C200-GET-RECORD SECTION.
          *******************************************************************
          *  C200-GET-RECORD
          *    Allocates the global clob LICENSE-TXT then selects
          *    the name and text which corresponds to the client-supplied
          *    sss.  It then calls Z200-PRINTCRIME to print the information and
          *    frees the clob.
          *******************************************************************
           C200-GTRECRD.
               PERFORM Z100-GET-SSS.
               IF (SSSEXISTS = 1)
                 EXEC SQL ALLOCATE :LICENSE-TXT END-EXEC
                 EXEC SQL SELECT NAME, TXT_SUMMARY
                      INTO :NAME1, :LICENSE-TXT FROM LICENSE_TABLE
                      WHERE SSS = :SSS END-EXEC
                 DISPLAY "==================================================
          -         "========================"
                 DISPLAY " "
                 DISPLAY "NAME:  ", NAME1-ARR, "SSS:  ", SSS
                 DISPLAY " "
                 PERFORM Z200-PRINTCRIME
                 DISPLAY " "
                 DISPLAY "==================================================
          -         "========================"
                 EXEC SQL FREE :LICENSE-TXT END-EXEC
               ELSE
                  DISPLAY "SSS Number Not Found".
           C200-EXIT.
               EXIT.
           C310-GETNEWCRIME SECTION.
          *******************************************************************
          *  C310-GETNEWCRIME
          *    Provides a list of the possible crimes to the user and
          *    stores the user's correct response in the variable
          *    NEWCRIME.
          *******************************************************************
           C310-GTNWCRM.

                EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.

                DISPLAY " ".
                DISPLAY "Select from the following:".
                PERFORM C311-DISPLAY-CRIME
                  VARYING CRIME-INDEX FROM 1 BY 1
                  UNTIL CRIME-INDEX > 5.
                MOVE ZERO TO CHOICE.
                PERFORM Z300-ACCEPT-CHOICE UNTIL CHOICE < 6
                                      AND CHOICE > 0.
                MOVE CRIME(CHOICE) TO NEWCRIME-ARR.
                MOVE 35 TO NEWCRIME-LEN.
                MOVE ZERO TO CHOICE.
           C310-EXIT.
                EXIT.
           C311-DISPLAY-CRIME SECTION.
          *******************************************************************
          *   C311-DISPLAY-CRIME
          *      Display an element of the crime table
          *******************************************************************
           C311-DSPLYCRM.
               DISPLAY "(", CRIME-INDEX, ") ", CRIME(CRIME-INDEX).
           C311-EXIT.
                EXIT.
           C320-APPENDTOCLOB SECTION.
          *******************************************************************
          * C320-APPENDTOCLOB
          *    Obtains the length of the global clob LICENSE-TXT and
          *    uses that in the LOB WRITE statement to append the NEWCRIME
          *    character buffer to the global clob LICENSE-TXT.
          *    The name corresponding the global SSS is then selected
          *    and displayed to the screen along with value of LICENSE-TXT.
          *    The caller to this function must allocate, select and later
          *    free the global clob LICENSE-TXT.
          *******************************************************************
           C320-PPNDTCLB.

               EXEC SQL
            WHENEVER SQLERROR DO PERFORM Z900-SQLERROR
           END-EXEC.

               EXEC SQL LOB DESCRIBE :LICENSE-TXT GET LENGTH
                   INTO :TXT-LEN END-EXEC.

               MOVE NEWCRIME-LEN TO CRIME-LEN.
               IF (TXT-LEN NOT = 0)
                 ADD 3 TO TXT-LEN
               ELSE
                 ADD 1 TO TXT-LEN.
               EXEC SQL LOB WRITE :CRIME-LEN FROM :NEWCRIME
                     INTO :LICENSE-TXT AT :TXT-LEN END-EXEC.

               EXEC SQL SELECT NAME INTO :NAME1 FROM LICENSE_TABLE
                   WHERE SSS = :SSS END-EXEC.
               DISPLAY " ".
               DISPLAY "NAME:  ", NAME1-ARR, "SSS:  ", SSS.
               DISPLAY " ".
               PERFORM Z200-PRINTCRIME.
               DISPLAY " ".

           C320-EXIT.
              EXIT.

           C300-ADD-CRIME SECTION.
          *******************************************************************
          * ADD-CRIME
          *    Obtains a sss and crime from the user and appends
          *    the crime to the list of crimes of the corresponding sss.
          *******************************************************************
           C300-DDCRM.

               EXEC SQL
                  WHENEVER SQLERROR DO PERFORM Z900-SQLERROR
           END-EXEC.

               PERFORM Z100-GET-SSS.
               IF (SSSEXISTS = 1)
                 EXEC SQL ALLOCATE :LICENSE-TXT END-EXEC
                 PERFORM C310-GETNEWCRIME
                 EXEC SQL SELECT TXT_SUMMARY INTO :LICENSE-TXT
                      FROM LICENSE_TABLE WHERE SSS = :SSS
                      FOR UPDATE END-EXEC
                 PERFORM C320-APPENDTOCLOB
                 EXEC SQL FREE :LICENSE-TXT END-EXEC
               ELSE
                  DISPLAY "SSS Number Not Found".
           C300-EXIT.
               EXIT.

           C400-NEW-RECORD SECTION.
          *******************************************************************
          * C400-NEW-RECORD
          *    Obtains the sss and name of a new record and inserts them
          *    along with an empty_clob() for the clob in the table.
          *******************************************************************
           C400-NWRCRD.

               PERFORM Z100-GET-SSS.
               IF (SSSEXISTS = 1)
                 DISPLAY "Record with that sss number already exists"
               ELSE
                 DISPLAY "Name? " WITH NO ADVANCING
                 ACCEPT NEWNAME
                 DISPLAY " ".
                 EXEC SQL ALLOCATE :LICENSE-TXT END-EXEC
                 EXEC SQL INSERT INTO LICENSE_TABLE
                      VALUES (:SSS, :NEWNAME, EMPTY_CLOB()) END-EXEC
                 EXEC SQL SELECT TXT_SUMMARY INTO :LICENSE-TXT
                      FROM LICENSE_TABLE WHERE SSS = :SSS END-EXEC
                 DISPLAY "==================================================
          -         "========================"
                 DISPLAY "NAME: ", NEWNAME,"SSS: ", SSS
                 PERFORM Z200-PRINTCRIME
                 DISPLAY "==================================================
          -         "========================"
                 EXEC SQL FREE :LICENSE-TXT END-EXEC.
           C400-EXIT.
              EXIT.
           D000-LOGOFF SECTION.
          *******************************************************************
          *  D000-LOGOFF
          *    Commit the work done to the database and log off
          *******************************************************************
           D000-LGFF.
               EXEC SQL COMMIT WORK RELEASE END-EXEC.
               DISPLAY " ".
               DISPLAY "HAVE A GOOD DAY!".
               DISPLAY " ".
           D000-EXIT.
               STOP RUN.
           Z100-GET-SSS SECTION.
          *******************************************************************
          *  Z100-GET-SSS
          *    Fills the global variable SSS with the client-supplied sss.
          *    Sets the global variable SSSEXISTS to 0 if the sss does not
          *    correspond to any entry in the database, else sets it to 1.
          *******************************************************************
           Z100-GTSSS.
               DISPLAY "Social Security Number? " WITH NO ADVANCING.
               ACCEPT SSS.
               DISPLAY " ".

               EXEC SQL SELECT COUNT(*) INTO :SSSCOUNT FROM LICENSE_TABLE
                   WHERE SSS = :SSS END-EXEC.

               IF (SSSCOUNT = 0)
                  MOVE 0 TO SSSEXISTS
               ELSE
                  MOVE 1 TO SSSEXISTS.
           Z100-EXIT.
              EXIT.
           Z200-PRINTCRIME SECTION.
          *******************************************************************
          *  Z200-PRINTCRIME
          *    Obtains the length of the global clob LICENSE-TXT and
          *    uses that in the LOB READ statement to read the clob
          *    into a character buffer to display the contents of the clob.
          *    The caller to this function must allocate, select and later
          *    free the global clob LICENSE-TXT.
          *******************************************************************
           Z200-PRNTCRM.
               DISPLAY "=====================".
               DISPLAY " CRIME SHEET SUMMARY ".
               DISPLAY "=====================".

               MOVE SPACE TO THE-STRING-ARR.
               EXEC SQL LOB DESCRIBE :LICENSE-TXT GET LENGTH
                   INTO :TXT-LENGTH END-EXEC.

               IF (TXT-LENGTH = 0)
                  DISPLAY "Record is clean"
                ELSE
                  EXEC SQL LOB READ :TXT-LENGTH FROM :LICENSE-TXT
                     INTO :THE-STRING END-EXEC
                  DISPLAY THE-STRING-ARR.

           Z200-EXIT.
               EXIT.
           Z300-ACCEPT-CHOICE SECTION.
          *******************************************************************
          *   Z300-ACCEPT-CHOICE
          *      Accept a choice between 1 and 5
          *******************************************************************
           Z300-CCPT.
               DISPLAY "Your Selection (1-5)? " WITH NO ADVANCING.
               ACCEPT CHOICE.
               DISPLAY " ".
               IF CHOICE >5 OR CHOICE < 1 THEN
                  DISPLAY "Invalid Selection"
                  DISPLAY "Please Choose from the indicated list".
           Z300-EXIT.
              EXIT.

           Z900-SQLERROR SECTION.
          *******************************************************************
          * Z900-SQLERROR
          *    Called whenever a SQLERROR occurs.
          *    Display the Error, Roll Back any work done and Log Off
          *******************************************************************
           Z900-SQLRRR.
               EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.
               DISPLAY " ".
               DISPLAY "ORACLE ERROR DETECTED:".
               DISPLAY " ".
               DISPLAY SQLERRMC.
               EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
           Z900-EXIT.
               STOP RUN.
