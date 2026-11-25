## 15  Performance Guidelines

There are performance guidelines for applications that use LOB data types.

- LOB Performance Guidelines

- Moving Data to LOBs in a Threaded Environment

- LOB Access Statistics

<!-- -->

- LOB Performance Guidelines
- Moving Data to LOBs in a Threaded Environment
- LOB Access Statistics

**Parent topic:** [Application Design with LOBs](application-design-with-LOBs.md)

### 15.1 LOB Performance Guidelines

There are various performance guidelines that apply to applications that use LOB data types.

- All LOBs
- Persistent LOBs
- Temporary LOBs

**Related Topics**

- All LOBs
- Persistent LOBs
- Temporary LOBs

**Parent topic:** Performance Guidelines

#### 15.1.1 All LOBs

This section explains guidelines for using LOBs.

- Chunk Size
- LOB Pre-fetching
  LOB pre-fetching allows to preview initial part of the data or use LOB locator interface to access the stored data
- Small LOBs
  Oracle Database allow LOBs to use Data Interface for read and write operations provided the LOB size is smaller than the available buffer size.
- Large LOBs

**Related Topics**

- Chunk Size
- LOB Pre-fetching
- Small LOBs
- Large LOBs

**Parent topic:** LOB Performance Guidelines

##### 15.1.1.1 Chunk Size

A chunk is one or more Oracle blocks. You can specify the chunk size for the LOB when creating the table that contains the LOB.

This corresponds to the data size used by Oracle Database when accessing or modifying the LOB value. Part of the chunk is used to store system-related information and the rest stores the LOB value. The API you are using has a function that returns the amount of space used in the LOB chunk to store the LOB value. In PL/SQL use `DBMS_LOB.GETCHUNKSIZE`. In OCI, use `OCILobGetChunkSize()`. For SecureFiles, the usable data area of the tablespace block size is returned.

**Parent topic:** All LOBs

##### 15.1.1.2 LOB Pre-fetching

LOB pre-fetching allows to preview initial part of the data or use LOB locator interface to access the stored data

LOB pre-fetching allows to perform the following operations:

- Preview the initial part of the data

- Use the locator interface to access the stored data

**Related Topics**

- [Prefetching of LOB Data, Length, and Chunk Size](overview-of-supplied-LOB-APIs.md)
- [Prefetching LOBs to Improve Performance](overview-of-supplied-LOB-APIs.md)

**Parent topic:** All LOBs

##### 15.1.1.3 Small LOBs

Oracle Database allow LOBs to use Data Interface for read and write operations provided the LOB size is smaller than the available buffer size.

Oracle Database allow LOBs to use Data Interface for data read and write operations if the LOB size is smaller than the available buffer size.

**Related Topics**

- [Data Interface for Persistent LOBs](data-interface-for-persistent-LOBs.md)

**Parent topic:** All LOBs

##### 15.1.1.4 Large LOBs

Starting from Oracle Database 19c release, piecewise or callback mechanism can be used for OCILobRead and OCILobWrite operations.

**Parent topic:** All LOBs

#### 15.1.2 Persistent LOBs

- Performance Guidelines for Small BasicFiles LOBs
- General Performance Guidelines for BasicFiles LOBs

**Related Topics**

- Performance Guidelines for Small BasicFiles LOBs
- General Performance Guidelines for BasicFiles LOBs

**Parent topic:** LOB Performance Guidelines

##### 15.1.2.1 Performance Guidelines for Small BasicFiles LOBs

If most LOBs in your database tables are small in size, use these guidelines.

For LOBs in your database tables that are 8K bytes or less, with only a few rows containing LOBs larger than 8K bytes, then use these guidelines to maximize database performance:

- Use `ENABLE STORAGE IN ROW`.

- Set the `DB_BLOCK_SIZE` initialization parameter to 8K bytes and use a chunk size of 8K bytes.

- **See Also:**

  [LOB Storage Parameters](LOB-storage-with-applications.md) for more information on tuning other parameters such as `CACHE,` `PCTVERSION`, and `CHUNK` for the LOB segment

**Parent topic:** Persistent LOBs

##### 15.1.2.2 General Performance Guidelines for BasicFiles LOBs

You can achieve maximum performance with BasicFiles LOBs.

Use these guidelines for maximum performance with BasicFiles LOBs:

- When Possible, Read/Write Large Data Chunks at a Time:

  Because LOBs are big, you can obtain the best performance by reading and writing large pieces of a LOB value at a time. This helps in several respects:

  1.  If accessing the LOB from the client side and the client is at a different node than the server, then large reads/writes reduce network overhead.

  2.  If using the `NOCACHE` option, then each small read/write incurs an I/O. Reading/writing large quantities of data reduces the I/O.

  3.  Writing to the LOB creates a new version of the LOB chunk. Therefore, writing small amounts at a time incurs the cost of a new version for each small write. If logging is on, then the chunk is also stored in the redo log.

- Use `OCILobRead2()` and `OCILobWrite2()` with Callback:

  So that data is streamed to and from the LOB. Ensure the length of the entire write is set in the `amount` parameter on input. Whenever possible, read and write in multiples of the LOB chunk size.

- Use a Checkout/Check-in Model for LOBs:

  LOBs are optimized for the following operations:

  - SQL `UPDATE` which replaces the entire LOB value

  - Copy the entire LOB data to the client, modify the LOB data on the client side, copy the entire LOB data back to the database. This can be done using `OCILobRead2`() and `OCILobWrite2`() with streaming.

- Commit changes frequently.

**Parent topic:** Persistent LOBs

#### 15.1.3 Temporary LOBs

In addition to the guidelines described in "LOB Performance Guidelines" on LOB performance in general, here are some guidelines for using temporary LOBs:

- Use PGA memory to store temporary LOBs for improved performance.

- Use a separate temporary tablespace for temporary LOB storage instead of the default system tablespace

  This avoids device contention when copying data from persistent LOBs to temporary LOBs.

  If you use the newly provided enhanced SQL semantics functionality in your applications, then there are many more temporary LOBs created silently in SQL and PL/SQL than before. Ensure that temporary tablespace for storing these temporary LOBs is large enough for your applications. In particular, these temporary LOBs are silently created when you use the following:

  - SQL functions on LOBs

  - PL/SQL built-in character functions on LOBs

  - Variable assignments from `VARCHAR2`/`RAW` to `CLOB`s/`BLOB`s, respectively.

  - Perform a `LONG`-to-`LOB` migration

- If SQL operators are used on LOBs, the PGA memory and temporary tablespace must be large enough to accommodate the temporary LOBs generated by SQL operators.

- Free up temporary LOBs returned from SQL queries and PL/SQL programs

  In PL/SQL, C (OCI), Java and other programmatic interfaces, SQL query results or PL/SQL program executions return temporary LOBs for operation/function calls on LOBs. For example:

      SELECT substr(CLOB_Column, 4001, 32000) FROM ...

  If the query is executed in PL/SQL, then the returned temporary LOBs are automatically freed at the end of a PL/SQL program block. You can also explicitly free the temporary LOBs at any time. In OCI and Java, the returned temporary LOB must be explicitly freed.

  Without proper deallocation of the temporary LOBs returned from SQL queries, temporary tablespace is filled and you may observe performance degradation.

- In PL/SQL, use NOCOPY to pass temporary LOB parameters by reference whenever possible.

  **See Also:**

  [Oracle Database PL/SQL Language Reference](../lnpls/overview.md)for more information on passing parameters by reference and parameter aliasing

- Take advantage of buffer cache on temporary LOBs.

  Temporary LOBs created with the CACHE parameter set to true move through the buffer cache. Otherwise temporary LOBs are read directly from, and written directly to, disk.

- For optimal performance, temporary LOBs use reference on read, copy on write semantics. When a temporary LOB locator is assigned to another locator, the physical LOB data is not copied. Subsequent READ operations using either of the LOB locators refer to the same physical LOB data. On the first WRITE operation after the assignment, the physical LOB data is copied in order to preserve LOB value semantics, that is, to ensure that each locator points to a unique LOB value. This performance consideration mainly applies to the PL/SQL and OCI environments.

  In PL/SQL, reference on read, copy on write semantics are illustrated as follows:

      LOCATOR1 BLOB;
      LOCATOR2 BLOB;
      DBMS_LOB.CREATETEMPORARY (LOCATOR1,TRUE,DBMS_LOB.SESSION);

      -- LOB data is not copied in this assignment operation:
      LOCATOR2 := LOCATOR;
      -- These read operations refer to the same physical LOB copy:
      DBMS_LOB.READ(LOCATOR1, ...);
      DBMS_LOB.GETLENGTH(LOCATOR2, ...);

      -- A physical copy of the LOB data is made on WRITE:
      DBMS_LOB.WRITE(LOCATOR2, ...);

  In OCI, to ensure value semantics of LOB locators and data, `OCILobLocatorAssign()` is used to copy temporary LOB locators and the LOB Data. `OCILobLocatorAssign()` does not make a round trip to the server. The physical temporary LOB copy is made when LOB updates happen in the same round trip as the LOB update API as illustrated in the following:

      OCILobLocator *LOC1;
      OCILobLocator *LOC2;
      OCILobCreateTemporary(... LOC1, ... TRUE,OCI_DURATION_SESSION);

      /* No round-trip is incurred in the following call. */
      OCILobLocatorAssign(... LOC1, LOC2);

      /* Read operations refer to the same physical LOB copy. */
      OCILobRead2(... LOC1 ...)

      /* One round-trip is incurred to make a new copy of the
       * LOB data and to write to the new LOB copy.
       */
      OCILobWrite2(... LOC1 ...)

      /* LOC2 does not see the same LOB data as LOC1. */
      OCILobRead2(... LOC2 ...)

  If LOB value semantics are not intended, then you can use C pointers to achieve reference semantics as illustrated in the following:

      OCILobLocator *LOC1;
      OCILobLocator *LOC2;
      OCILobCreateTemporary(... LOC1, ... TRUE,OCI_DURATION_SESSION);

      /* Pointer is copied. LOC1 and LOC2 refer to the same LOB data. */
      LOC2 = LOC1;

      /* Write to LOC2. */
      OCILobWrite2(...LOC2...)

      /* LOC1 sees the change made to LOC2. */
      OCILobRead2(...LOC1...)

- Use OCI_OBJECT mode for temporary LOBs

  To improve the performance of temporary LOBs on LOB assignment, use `OCI_OBJECT` mode for `OCILobLocatorAssign()`. In `OCI_OBJECT` mode, the database tries to minimize the number of deep copies to be done. Hence, after `OCILobLocatorAssign()` is done on a source temporary LOB in `OCI_OBJECT` mode, the source and the destination locators point to the same LOB until any modification is made through either LOB locator.

**Parent topic:** LOB Performance Guidelines

### 15.2 Moving Data to LOBs in a Threaded Environment

There are two possible procedures that you can use to move data to LOBs in a threaded environment, one of which should be avoided.

#### Recommended Procedure

**Note:**

- There is no requirement to create an empty LOB in this procedure.

- You can use the `RETURNING` clause as part of the `INSERT/UPDATE` statement to return a locked LOB locator. This eliminates the need for doing a `SELECT-FOR-UPDATE`, as mentioned in step 3.

The recommended procedure is as follows:

1.  `INSERT` an empty LOB, `RETURNING` the LOB locator.

2.  Move data into the LOB using this locator.

3.  `COMMIT`. This releases the ROW locks and makes the LOB data persistent.

Alternatively, you can insert more than 4000 bytes of data directly for the LOB columns or LOB attributes.

#### Procedure to Avoid

The following sequence requires a new connection when using a threaded environment, adversely affects performance, and is not recommended:

1.  Create an empty (non-`NULL`) LOB

2.  Perform `INSERT` using the empty LOB

3.  `SELECT-FOR-UPDATE` of the row just entered

4.  Move data into the LOB

5.  `COMMIT`. This releases the `ROW` locks and makes the LOB data persistent.

**Parent topic:** Performance Guidelines

### 15.3 LOB Access Statistics

After Oracle Database 10g Release 2, three session-level statistics specific to LOBs are available to users: LOB reads, LOB writes, and LOB writes unaligned.

Session statistics are accessible through the `V$MYSTAT`, `V$SESSTAT`, and `V$SYSSTAT` dynamic performance views. To query these views, the user must be granted the privileges `SELECT_CATALOG_ROLE`, `SELECT ON SYS.V_$MYSTAT` view, and `SELECT ON SYS.V_$STATNAME` view.

LOB reads is defined as the number of LOB API read operations performed in the session/system. A single LOB API read may correspond to multiple physical/logical disk block reads.

LOB writes is defined as the number of LOB API write operations performed in the session/system. A single LOB API write may correspond to multiple physical/logical disk block writes.

LOB writes unaligned is defined as the number of LOB API write operations whose start offset or buffer size is not aligned to the internal chunk size of the LOB. Writes aligned to chunk boundaries are the most efficient write operations. The internal chunk size of a LOB is available through the LOB API (for example, using PL/SQL, by `DBMS_LOB.GETCHUNKSIZE()`).

The following simple example demonstrates how LOB session statistics are updated as the user performs read/write operations on LOBs.

It is important to note that session statistics are aggregated across operations to all LOBs accessed in a session; the statistics are not separated or categorized by objects (that is, table, column, segment, object numbers, and so on).

In these examples, you reconnect to the database for each demonstration to clear the `V$MYSTAT`. This enables you to see how the lob statistics change for the specific operation you are testing, without the potentially obscuring effect of past LOB operations within the same session.

**See also:**

[Oracle Database Reference](../refrn/statistics-descriptions.md), appendix E, "Statistics Descriptions"

- Example of Retrieving LOB Access Statistics

**Parent topic:** Performance Guidelines

#### 15.3.1 Example of Retrieving LOB Access Statistics

This example demonstrates retrieving LOB access statistics.

    rem
    rem Set up the user
    rem

    CONNECT / AS SYSDBA;
    SET ECHO ON;
    GRANT SELECT_CATALOG_ROLE TO pm;
    GRANT SELECT ON sys.v_$mystat TO pm;
    GRANT SELECT ON sys.v_$statname TO pm;

    rem
    rem Create a simplified view for statistics queries
    rem

    CONNECT pm;
    SET ECHO ON;

    DROP VIEW mylobstats;
    CREATE VIEW mylobstats
    AS
    SELECT  SUBSTR(n.name,1,20) name,
            m.value             value
    FROM    v$mystat    m,
            v$statname  n
    WHERE   m.statistic# = n.statistic#
        AND n.name LIKE 'lob%';

    rem
    rem Create a test table
    rem

    DROP TABLE t;
    CREATE TABLE t (i NUMBER, c CLOB)
        lob(c) STORE AS (DISABLE STORAGE IN ROW);

    rem
    rem Populate some data
    rem
    rem This should result in unaligned writes, one for
    rem each row/lob populated.
    rem

    CONNECT pm
    SELECT * FROM mylobstats;
    INSERT INTO t VALUES (1, 'a');
    INSERT INTO t VALUES (2, rpad('a',4000,'a'));
    COMMIT;
    SELECT * FROM mylobstats;

    rem
    rem Get the lob length
    rem
    rem Computing lob length does not read lob data, no change
    rem in read/write stats.
    rem

    CONNECT pm;
    SELECT * FROM mylobstats;
    SELECT LENGTH(c) FROM t;
    SELECT * FROM mylobstats;

    rem
    rem Read the lobs
    rem
    rem Lob reads are performed, one for each lob in the table.
    rem

    CONNECT pm;
    SELECT * FROM mylobstats;
    SELECT * FROM t;
    SELECT * FROM mylobstats;

    rem
    rem Read and manipulate the lobs (through temporary lobs)
    rem
    rem The use of complex operators like "substr()" results in
    rem the implicit creation and use of temporary lobs. operations
    rem on temporary lobs also update lob statistics.
    rem

    CONNECT pm;
    SELECT * FROM mylobstats;
    SELECT substr(c, length(c), 1) FROM t;
    SELECT substr(c, 1, 1) FROM t;
    SELECT * FROM mylobstats;

    rem
    rem Perform some aligned overwrites
    rem
    rem Only lob write statistics are updated because both the
    rem byte offset of the write, and the size of the buffer
    rem being written are aligned on the lob chunksize.
    rem

    CONNECT pm;
    SELECT * FROM mylobstats;
    DECLARE
        loc     CLOB;
        buf     LONG;
        chunk   NUMBER;
    BEGIN
        SELECT c INTO loc FROM t WHERE i = 1
            FOR UPDATE;

        chunk := DBMS_LOB.GETCHUNKSIZE(loc);
        buf   := rpad('b', chunk, 'b');

        -- aligned buffer length and offset
        DBMS_LOB.WRITE(loc, chunk, 1, buf);
        DBMS_LOB.WRITE(loc, chunk, 1+chunk, buf);
        COMMIT;
    END;
    /
    SELECT * FROM mylobstats;

    rem
    rem Perform some unaligned overwrites
    rem
    rem Both lob write and lob unaligned write statistics are
    rem updated because either one or both of the write byte offset
    rem and buffer size are unaligned with the lob's chunksize.
    rem

    CONNECT pm;
    SELECT * FROM mylobstats;
    DECLARE
        loc CLOB;
        buf LONG;
    BEGIN
        SELECT c INTO loc FROM t WHERE i = 1
            FOR UPDATE;

        buf := rpad('b', DBMS_LOB.GETCHUNKSIZE(loc), 'b');

        -- unaligned buffer length
        DBMS_LOB.WRITE(loc, DBMS_LOB.GETCHUNKSIZE(loc)-1, 1, buf);

        -- unaligned start offset
        DBMS_LOB.WRITE(loc, DBMS_LOB.GETCHUNKSIZE(loc), 2, buf);

        -- unaligned buffer length and start offset
        DBMS_LOB.WRITE(loc, DBMS_LOB.GETCHUNKSIZE(loc)-1, 2, buf);

        COMMIT;
    END;
    /
    SELECT * FROM mylobstats;
    DROP TABLE t;
    DROP VIEW mylobstats;

    CONNECT / AS SYSDBA
    REVOKE SELECT_CATALOG_ROLE FROM pm;
    REVOKE SELECT ON sys.v_$mystat FROM pm;
    REVOKE SELECT ON sys.v_$statname FROM pm;

    QUIT;

**Parent topic:** LOB Access Statistics
