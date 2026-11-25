## 13  LOB Storage with Applications

Applications that contain tables with LOB columns may use both `SECUREFILE` and `BASICFILE` LOBs. If a feature applies to only one kind of LOB, this is stated.

Topics:

- Tables That Contain LOBs

- Data Types for LOB Columns

- LOB Storage Parameters

- LOB Columns Indexing

- LOB Manipulation in Partitioned Tables

- LOBs in Index Organized Tables

- Restrictions on Index Organized Tables with LOB Columns

- Restrictions for LOBs in Partitioned Index-Organized Tables

- Updating LOBs in Nested Tables

<!-- -->

- Tables That Contain LOBs
- Data Types for LOB Columns
- LOB Storage Parameters
- LOB Columns Indexing
- LOB Manipulation in Partitioned Tables
- LOBs in Index Organized Tables
- Restrictions on Index Organized Tables with LOB Columns
  The ALTER TABLE MOVE operation cannot be performed on an index organized table with a LOB column in parallel.
- Restrictions for LOBs in Partitioned Index-Organized Tables
- Updating LOBs in Nested Tables

**Parent topic:** [Application Design with LOBs](application-design-with-LOBs.md)

### 13.1 Tables That Contain LOBs

When creating tables that contain LOBs, use these guidelines:

Topics:

- Persistent LOBs Initialized to NULL or Empty

- Initializing LOBs

- Initializing Persistent LOB Columns and Attributes to a Value

- Initializing BFILEs to NULL or a File Name

<!-- -->

- Persistent LOBs Initialized to NULL or Empty
- Initializing LOBs
- Initializing Persistent LOB Columns and Attributes to a Value
- Initializing BFILEs to NULL or a File Name
- Restriction on First Extent of a LOB Segment

**Parent topic:** LOB Storage with Applications

#### 13.1.1 Persistent LOBs Initialized to NULL or Empty

You can set a persistent LOB — ­that is, a LOB column in a table, or a LOB attribute in an object type that you defined— to be `NULL` or empty:

- Set a Persistent LOB to NULL: A LOB set to `NULL` has no locator. A `NULL` value is stored in the row in the table, not a locator. This is the same process as for all other data types.

- Set a Persistent LOB to Empty: By contrast, an empty LOB stored in a table is a LOB of zero length that has a locator. So, if you `SELECT` from an empty LOB column or attribute, then you get back a locator which you can use to populate the LOB with data using supported programmatic environments, such as OCI or `PL/SQL(DBMS_LOB`).

<!-- -->

- Setting a Persistent LOB to NULL
- Setting a Persistent LOB to Empty

**See Also:**

[Overview of Supplied LOB APIs](overview-of-supplied-LOB-APIs.md) for more information on supported environments

**Parent topic:** Tables That Contain LOBs

##### 13.1.1.1 Setting a Persistent LOB to NULL

You may want to set a persistent LOB value to `NULL` upon inserting the row.

These are possible situations where this is useful:

- In cases where you do not have the LOB data at the time of the `INSERT`.

- If you want to use a `SELECT` statement, such as the following, to determine whether or not the LOB holds a `NULL` value:

      SELECT COUNT (*) FROM print_media WHERE ad_graphic IS NOT NULL;

      SELECT COUNT (*) FROM print_media WHERE ad_graphic IS NULL;

Note that you cannot call OCI or `DBMS_LOB` functions on a `NULL` LOB, so you must then use an SQL `UPDATE` statement to reset the LOB column to a non-`NULL` (or empty) value.

The point is that you cannot make a function call from the supported programmatic environments on a LOB that is `NULL.` These functions only work with a locator, and if the LOB column is `NULL`, then there is no locator in the row.

**Parent topic:** Persistent LOBs Initialized to NULL or Empty

##### 13.1.1.2 Setting a Persistent LOB to Empty

You can initialize a persistent LOB to `EMPTY` rather that `NULL`. Doing so, enables you to obtain a locator for the LOB instance without populating the LOB with data.

- You set a persistent LOB to `EMPTY`, using the SQL function `EMPTY_BLOB()` or `EMPTY_CLOB()` in the `INSERT` statement, as follows.

      INSERT INTO a_table VALUES (EMPTY_BLOB());

As an alternative, you can use the `RETURNING` clause to obtain the LOB locator in one operation rather than calling a subsequent `SELECT` statement:

    DECLARE
       Lob_loc  BLOB;
    BEGIN
       INSERT INTO a_table VALUES (EMPTY_BLOB()) RETURNING blob_col INTO Lob_loc;
       /* Now use the locator Lob_loc to populate the BLOB with data */
    END;

**Parent topic:** Persistent LOBs Initialized to NULL or Empty

#### 13.1.2 Initializing LOBs

You can initialize the LOBs in `print_media` by using the following `INSERT` statement:

    INSERT INTO print_media VALUES (1001, EMPTY_CLOB(), EMPTY_CLOB(), NULL,
        EMPTY_BLOB(), EMPTY_BLOB(), NULL, NULL, NULL, NULL);

This sets the value of `ad_sourcetext`, `ad_fltextn`, `ad_composite`, and `ad_photo` to an empty value, and sets `ad_graphic` to `NULL`.

**See Also:**

[Table for LOB Examples: The PM Schema print_media Table](working-with-LOBs.md) for the `print_media` table.

**Parent topic:** Tables That Contain LOBs

#### 13.1.3 Initializing Persistent LOB Columns and Attributes to a Value

You can initialize the LOB column or LOB attributes to a value that contains more than 4G bytes of data, the limit before release 10.2.

**See Also:**

[Data Interface for Persistent LOBs](data-interface-for-persistent-LOBs.md)

**Parent topic:** Tables That Contain LOBs

#### 13.1.4 Initializing BFILEs to NULL or a File Name

A `BFILE` can be initialized to `NULL` or to a filename. To do so, you can use the `BFILENAME()` function.

**See Also:**

"[BFILENAME and Initialization](LOB-APIs-for-BFILE-operations.md)".

**Parent topic:** Tables That Contain LOBs

#### 13.1.5 Restriction on First Extent of a LOB Segment

The first extent of any segment requires at least 2 blocks (if `FREELIST GROUPS` was 0). That is, the initial extent size of the segment should be at least 2 blocks. LOBs segments are different because they need at least 3 blocks in the first extent if the LOB is a BasicFiles LOB and 16 blocks if the LOB is a SecureFiles LOB.

If you try to create a LOB segment in a permanent dictionary managed tablespace with initial = 2 blocks, then it still works because it is possible for segments in permanent dictionary-managed tablespaces to override the default storage setting of the tablespaces.

But if uniform, locally managed tablespaces or dictionary managed tablespaces of the temporary type, or locally managed temporary tablespaces have an extent size of 2 blocks, then LOB segments cannot be created in these tablespaces. This is because in these tablespace types, extent sizes are fixed and the default storage setting of the tablespaces is not ignored.

**Parent topic:** Tables That Contain LOBs

### 13.2 Data Types for LOB Columns

When selecting a data type, consider the following three topics:

- LOBs Compared to LONG and LONG RAW Types

- Varying-Width Character Data Storage in LOBs

- Converting Character Sets Implicitly with LOBs

<!-- -->

- LOBs Compared to LONG and LONG RAW Types
- Varying-Width Character Data Storage in LOBs
- Converting Character Sets Implicitly with LOBs

**Parent topic:** LOB Storage with Applications

#### 13.2.1 LOBs Compared to LONG and LONG RAW Types

Table 13-1 lists the similarities and differences between LOBs, LONGs, and LONG RAW types.

Table 13-1 LOBs Vs. LONG RAW

| LOB Data Type                                                                                                                                                                                                                                                                          | LONG and LONG RAW Data Type                                                                                                                                              |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| You can store multiple LOBs in a single row                                                                                                                                                                                                                                            | You can store only one `LONG` or `LONG` `RAW` in each row.                                                                                                               |
| `LOB`s can be attributes of a user-defined data type                                                                                                                                                                                                                                   | This is not possible with either a `LONG` or `LONG` `RAW`                                                                                                                |
| Only the LOB locator is stored in the table column; `BLOB` and `CLOB` data can be stored in separate tablespaces and `BFILE` data is stored as an external file.<br>For inline LOBs, the database stores LOBs that are less than approximately 4000 bytes of data in the table column. | In the case of a `LONG` or `LONG` `RAW` the entire value is stored in the table column.                                                                                  |
| When you access a LOB column, you can choose to fetch the locator or the data.                                                                                                                                                                                                         | When you access a `LONG` or `LONG` `RAW,` the entire value is returned.                                                                                                  |
| A LOB can be up to 128 terabytes or more in size depending on your block size.                                                                                                                                                                                                         | A `LONG` or `LONG` `RAW` instance is limited to 2 gigabytes in size.                                                                                                     |
| There is greater flexibility in manipulating data in a random, piece-wise manner with LOBs. LOBs can be accessed at random offsets.                                                                                                                                                    | Less flexibility in manipulating data in a random, piece-wise manner with `LONG or LONG RAW data.``LONG`s must be accessed from the beginning to the desired location`.` |
| You can use Oracle Golden Gate to replicate LOBs.                                                                                                                                                                                                                                      | Replication is not possible with LONG or LONG RAW.                                                                                                                       |

**Parent topic:** Data Types for LOB Columns

#### 13.2.2 Varying-Width Character Data Storage in LOBs

Varying-width character data in `CLOB` and `NCLOB` data types is stored in an internal format that is compatible with UCS2 Unicode character set format. This ensures that there is no storage loss of character data in a varying-width format. Also note the following if you are using LOBs to store varying-width character data:

- You can create tables containing `CLOB` and `NCLOB` columns even if you use a varying-width `CHAR` or `NCHAR` database character set.

- You can create a table containing a data type that has a `CLOB` attribute regardless of whether you use a varying-width `CHAR` database character set.

**Parent topic:** Data Types for LOB Columns

#### 13.2.3 Converting Character Sets Implicitly with LOBs

For `CLOB` and `NCLOB` instances used in OCI (Oracle Call Interface), or any of the programmatic environments that access OCI functionality, character set conversions are implicitly performed when translating from one character set to another.

- Use the `DBMS_LOB.LOADCLOBFROMFILE` API to perform an implicit conversion from binary data to character data when loading to a `CLOB` or `NCLOB`.

With the exception of `DBMS_LOB.LOADCLOBFROMFILE`, LOB APIs do not perform implicit conversions from binary data to character data.

For example, when you use the `DBMS_LOB.LOADFROMFILE` API to populate a `CLOB` or `NCLOB`, you are populating the LOB with binary data from a `BFILE`. In this case, you must perform character set conversions on the `BFILE` data before calling `DBMS_LOB.LOADFROMFILE`.

**See Also:**

[Oracle Database Globalization Support Guide ](../nlspg/choosing-character-set.md)for more detail on character set conversions.

**Note:**

The database character set cannot be changed from a single-byte to a multibyte character set if there are populated user-defined `CLOB` columns in the database tables. The national character set cannot be changed between `AL16UTF16` and `UTF8` if there are populated user-defined `NCLOB` columns in the database tables.

**Note:**

LOBs are not supported when the Container Database root and Pluggable Databases are in different character sets. For more information, refer to [Relocating a PDB Using CREATE PLUGGABLE DATABASE](../multi/relocating-a-pdb.md).

**Parent topic:** Data Types for LOB Columns

### 13.3 LOB Storage Parameters

You should consider certain LOB storage characteristics when designing tables with LOB storage. For a discussion of `SECUREFILE` parameters:

**See Also:**

- "[CREATE TABLE with LOB Storage](using-oracle-LOBs-storage.md)"

- "[ALTER TABLE with LOB Storage](using-oracle-LOBs-storage.md)"

Topics:

- Inline and Out-of-Line LOB Storage

- Defining Tablespace and Storage Characteristics for Persistent LOBs

<!-- -->

- Inline and Out-of-Line LOB Storage
- Defining Tablespace and Storage Characteristics for Persistent LOBs
- LOB Storage Characteristics for LOB Column or Attribute
- TABLESPACE and LOB Index
- PCTVERSION
- RETENTION Parameter for BasicFiles LOBs
- RETENTION Parameter for SecureFiles LOBs
- CACHE / NOCACHE / CACHE READS
- LOGGING / NOLOGGING Parameter for BasicFiles LOBs
- LOGGING/FILESYSTEM_LIKE_LOGGING for SecureFiles LOBs
- CHUNK
- ENABLE or DISABLE STORAGE IN ROW Clause
- Guidelines for ENABLE or DISABLE STORAGE IN ROW

**Parent topic:** LOB Storage with Applications

#### 13.3.1 Inline and Out-of-Line LOB Storage

LOB columns store locators that reference the location of the actual LOB value.

Actual LOB values are stored either in the table row (inline) or outside of the table row (out-of-line), depending on the column properties you specify when you create the table, and depending the size of the LOB.

LOB values are stored out-of-line when any of the following situations apply:

- If you explicitly specify `DISABLE` `STORAGE` `IN` `ROW` for the LOB storage clause when you create the table.

- If the size of the LOB is greater than approximately 4000 bytes (4000 minus system control information), regardless of the LOB storage properties for the column.

  In case of multibyte character sets, such as AL32UTF8, LOBs stored as CLOB may take up more space than when stored as single-byte character sets. The limit of 4000 bytes refers to the amount of storage needed to store the characters in a CLOB and not to the number of characters in a CLOB.

LOB values are stored inline when any of the following conditions apply:

- When the size of the LOB stored in the given row is small, approximately 4000 bytes or less, and you either explicitly specify `ENABLE` `STORAGE` `IN` `ROW` or the LOB storage clause when you create the table, or when you do not specify this parameter (which is the default).

- When the LOB value is `NULL` (regardless of the LOB storage properties for the column).

Using the default LOB storage properties (inline storage) can allow for better database performance; it avoids the overhead of creating and managing out-of-line storage for smaller LOB values. If LOB values stored in your database are frequently small in size, then using inline storage is recommended.

**Note:**

- LOB locators are always stored in the row.

- A LOB locator always exists for any LOB instance regardless of the LOB storage properties or LOB value - `NULL`, empty, or otherwise.

- If the LOB is created with `DISABLE STORAGE IN ROW` properties and the BasicFiles LOB holds any data, then a minimum of one `CHUNK` of out-of-line storage space is used; even when the size of the LOB is less than the `CHUNK` size.

- If a LOB column is initialized with `EMPTY_CLOB() `or `EMPTY_BLOB()`, then no LOB value exists, not even `NULL`. The row holds a LOB locator only. No additional LOB storage is used.

- LOB storage properties do not affect `BFILE` columns. `BFILE` data is always stored in operating system files outside the database.

**Parent topic:** LOB Storage Parameters

#### 13.3.2 Defining Tablespace and Storage Characteristics for Persistent LOBs

When defining LOBs in a table, you can explicitly indicate the tablespace and storage characteristics for each persistent LOB column.

To create a BasicFiles LOB, the `BASICFILE` keyword is optional but is recommended for clarity, as shown in the following example:

    CREATE TABLE ContainsLOB_tab (n NUMBER, c CLOB)
          lob (c) STORE AS BASICFILE segname (TABLESPACE lobtbs1 CHUNK 4096
                            PCTVERSION 5
                            NOCACHE LOGGING
                            STORAGE (MAXEXTENTS 5)
                           );

For SecureFiles, the `SECUREFILE` keyword is necessary, as shown in the following example (assuming `TABLESPACE lobtbs1` is `ASSM`):

    CREATE TABLE ContainsLOB_tab1 (n NUMBER, c CLOB)
          lob (c) STORE AS SECUREFILE sfsegname (TABLESPACE lobtbs1
                           RETENTION AUTO
                           CACHE LOGGING
                           STORAGE (MAXEXTENTS 5)
                         );

**Note:**

There are no tablespace or storage characteristics that you can specify for external LOBs (`BFILE`s) as they are not stored in the database.

If you must modify the LOB storage parameters on an existing LOB column, then use the `ALTER` `TABLE` `... MOVE` statement. You can change the `RETENTION`, `PCTVERSION`, `CACHE`, `NOCACHE` `LOGGING`, `NOLOGGING`, or `STORAGE` settings. You can also change the `TABLESPACE` using the `ALTER TABLE ... MOVE` statement.

- Assigning a LOB Data Segment Name

**Parent topic:** LOB Storage Parameters

##### 13.3.2.1 Assigning a LOB Data Segment Name

As shown in the previous example, specifying a name for the LOB data segment makes for a much more intuitive working environment. When querying the LOB data dictionary views `USER_LOBS`, `ALL_LOBS`, `DBA_LOBS` , you see the LOB data segment that you chose instead of system-generated names.

**See Also:**

[Oracle Database Reference](../refrn/initialization-parameters.md) for more information about initialization parameters

**Parent topic:** Defining Tablespace and Storage Characteristics for Persistent LOBs

#### 13.3.3 LOB Storage Characteristics for LOB Column or Attribute

LOB storage characteristics that can be specified for a LOB column or a LOB attribute include the following:

- `TABLESPACE`

- `PCTVERSION` or `RETENTION`

  Note that you can specify either `PCTVERSION` or `RETENTION` for BasicFiles LOBs, but not both. For SecureFiles, only the `RETENTION` parameter can be specified.

- `CACHE`/`NOCACHE/CACHE READS`

- `LOGGING/NOLOGGING`

- `CHUNK`

- `ENABLE`/`DISABLE` `STORAGE` `IN` `ROW`

- `STORAGE `

For most users, defaults for these storage characteristics are sufficient. If you want to fine-tune LOB storage, then consider the following guidelines.

**See Also:**

- `STORAGE` clause in [Oracle Database SQL Language Reference ](../sqlrf/storage_clause.md)

- `RETENTION` parameter in [Oracle Database SQL Language Reference ](../sqlrf/CREATE-TABLE.md)

**Parent topic:** LOB Storage Parameters

#### 13.3.4 TABLESPACE and LOB Index

The LOB index is an internal structure that is strongly associated with LOB storage. This implies that a user may not drop the LOB index and rebuild it.

**Note:**

The` `LOB index cannot be altered.

The system determines which tablespace to use for LOB data and LOB index depending on your specification in the LOB storage clause:

- If you do not specify a tablespace for the LOB data, then the tablespace of the table is used for the LOB data and index.

- If you specify a tablespace for the LOB data, then both the LOB data and index use the tablespace that was specified.

<!-- -->

- Tablespace for LOB Index in Non-Partitioned Table

**Parent topic:** LOB Storage Parameters

##### 13.3.4.1 Tablespace for LOB Index in Non-Partitioned Table

When creating a table, if you specify a tablespace for the LOB index for a non-partitioned table, then your specification of the tablespace is ignored and the LOB index is co-located with the LOB data. Partitioned LOBs do not include the LOB index syntax.

Specifying a separate tablespace for the LOB storage segments enables a decrease in contention on the tablespace of the table.

**Parent topic:** TABLESPACE and LOB Index

#### 13.3.5 PCTVERSION

When a BasicFiles LOB is modified, a new version of the BasicFiles LOB page is produced in order to support consistent read of prior versions of the BasicFiles LOB value.

`PCTVERSION` is the percentage of all used BasicFiles LOB data space that can be occupied by old versions of BasicFiles LOB data pages. As soon as old versions of BasicFiles LOB data pages start to occupy more than the `PCTVERSION` amount of used BasicFiles LOB space, Oracle Database tries to reclaim the old versions and reuse them. In other words, `PCTVERSION` is the percent of used BasicFiles LOB data blocks that is available for versioning old BasicFiles LOB data.

`PCTVERSION` has a default of 10 (%), a minimum of 0, and a maximum of 100.

To decide what value `PCTVERSION` should be set to, consider the following:

- How often BasicFiles LOBs are updated?

- How often the updated BasicFiles LOBs are read?

Table 13-2 provides some guidelines for determining a suitable `PCTVERSION` value given an update percentage of 'X'.

Table 13-2 Recommended PCTVERSION Settings

| BasicFiles LOB Update Pattern | BasicFiles LOB Read Pattern             | PCTVERSION |
|:------------------------------|:----------------------------------------|:-----------|
| Updates X% of LOB data        | Reads updated LOBs                      | X%         |
| Updates X% of LOB data        | Reads LOBs but not the updated LOBs     | 0%         |
| Updates X% of LOB data        | Reads both updated and non-updated LOBs | 2X%        |
| Never updates LOB             | Reads LOBs                              | 0%         |

If your application requires several BasicFiles LOB updates concurrent with heavy reads of BasicFiles LOB columns, then consider using a higher value for `PCTVERSION`, such as 20%.

Setting `PCTVERSION` to twice the default value allows more free pages to be used for old versions of data pages. Because large queries may require consistent reads of BasicFiles LOB columns, it may be useful to retain old versions of BasicFiles LOB pages. In this case, BasicFiles LOB storage may grow because the database does not reuse free pages aggressively.

If persistent BasicFiles LOB instances in your application are created and written just once and are primarily read-only afterward, then updates are infrequent. In this case, consider using a lower value for `PCTVERSION`, such as 5% or lower.

The more infrequent and smaller the BasicFiles LOB updates are, the less space must be reserved for old copies of BasicFiles LOB data. If existing BasicFiles LOBs are known to be read-only, then you could safely set `PCTVERSION` to 0% because there would never be any pages needed for old versions of data.

**Parent topic:** LOB Storage Parameters

#### 13.3.6 RETENTION Parameter for BasicFiles LOBs

You can specify the `RETENTION` parameter in the LOB storage clause of the `CREATE TABLE` or `ALTER TABLE` statement as an alternative to the `PCTVERSION` parameter,. Doing so, configures the LOB column to store old versions of LOB data for a period of time, rather than using a percentage of the table space. For example:

    CREATE TABLE ContainsLOB_tab (n NUMBER, c CLOB)
          lob (c) STORE AS BASICFILE segname (TABLESPACE lobtbs1 CHUNK 4096
                            RETENTION
                            NOCACHE LOGGING
                            STORAGE (MAXEXTENTS 5)
                           );

The `RETENTION` parameter is designed for use with `UNDO` features of the database, such as Flashback Versions Query. When a LOB column has the `RETENTION` property set, old versions of the LOB data are retained for the amount of time specified by the `UNDO_RETENTION` parameter.

Note the following with respect to the `RETENTION` parameter:

- `UNDO` SQL is not enabled for LOB columns as it is with other data types. You must set the `RETENTION` property on a LOB column to use Undo SQL on LOB data.

- You cannot set the value of the `RETENTION` parameter explicitly. The amount of time for retention of LOB versions in determined by the `UNDO_RETENTION` parameter.

- Usage of the `RETENTION` parameter is only supported in Automatic Undo Management mode. You must configure your table for use with Automatic Undo Management before you can set `RETENTION` on a LOB column. ASSM is required for LOB `RETENTION` to be in effect for BasicFiles LOBs. The `RETENTION` parameter of the SQL (in the `STORE` `AS` clause) is silently ignored if the BasicFiles LOB resides in an MSSM tablespace.

- The LOB storage clause can specify `RETENTION` or `PCTVERSION`, but not both.

  **See Also:**

  - [Oracle Database Development Guide](../adfns/flashback.md) for more information on using flashback features of the database.

  - [Oracle Database SQL Language Reference](../sqlrf/storage_clause.md) for details on LOB storage clause syntax.

**Parent topic:** LOB Storage Parameters

#### 13.3.7 RETENTION Parameter for SecureFiles LOBs

Specifying the `RETENTION` parameter for SecureFiles indicates that the database manages consistent read data for the SecureFiles storage dynamically, taking into account factors such as the `UNDO` mode of the database.

- Specify `MAX` if the database is in `FLASHBACK` mode to limit the size of the LOB `UNDO` retention in bytes. If you specify `MAX`, then you must also specify the `MAXSIZE` clause in the `storage_clause`.

- Specify `AUTO` if you want to retain `UNDO` sufficient for consistent read purposes only. This is the default.

- Specify `NONE` if no `UNDO` is required for either consistent read or flashback purposes.

The default `RETENTION` for SecureFiles is `AUTO`.

**Parent topic:** LOB Storage Parameters

#### 13.3.8 CACHE / NOCACHE / CACHE READS

When creating tables that contain LOBs, use the cache options according to the guidelines in Table 13-3:

Table 13-3 When to Use CACHE, NOCACHE, and CACHE READS

| Cache Mode          | Read                 | Write                |
|:--------------------|:---------------------|:---------------------|
| `CACHE READS`       | Frequently           | Once or occasionally |
| `CACHE`             | Frequently           | Frequently           |
| `NOCACHE `(default) | Once or occasionally | Never                |

- CACHE / NOCACHE / CACHE READS: LOB Values and Buffer Cache

**Parent topic:** LOB Storage Parameters

##### 13.3.8.1 CACHE / NOCACHE / CACHE READS: LOB Values and Buffer Cache

- CACHE: LOB pages are placed in the buffer cache for faster access.

- NOCACHE: As a parameter in the `STORE AS` clause, `NOCACHE` specifies that LOB values are not brought into the buffer cache.

- CACHE READS: LOB values are brought into the buffer cache only during read and not during write operations.

`NOCACHE` is the default for both SecureFiles and BasicFiles LOBs.

**Note:**

Using the `CACHE` option results in improved performance when reading and writing data from the LOB column. However, it can potentially age other non-LOB pages out of the buffer cache prematurely.

**Parent topic:** CACHE / NOCACHE / CACHE READS

#### 13.3.9 LOGGING / NOLOGGING Parameter for BasicFiles LOBs

The \[`NO`\]`LOGGING` parameter is applied to using LOBs in the same manner as for other table operations. In the usual case, if the \[`NO`\]`LOGGING` clause is omitted, then this means that neither `NO``LOGGING` nor `LOGGING` is specified and the logging attribute of the table or table partition defaults to the logging attribute of the tablespace in which it resides.

For LOBs, there is a further alternative depending on how `CACHE` is stipulated.

- CACHE is specified and \[`NO`\]`LOGGING` clause is omitted. `LOGGING` is automatically implemented (because you cannot have `CACHE` `NOLOGGING`).

- CACHE is not specified and \[`NO`\]`LOGGING` clause is omitted. The process defaults in the same way as it does for tables and partitioned tables. That is, the \[`NO`\]`LOGGING` value is obtained from the tablespace in which the LOB segment resides.

The following issues should also be kept in mind.

- LOBs Always Generate Undo for LOB Index Pages
- When LOGGING is Set Oracle Generates Full Redo for LOB Data Pages

**Parent topic:** LOB Storage Parameters

##### 13.3.9.1 LOBs Always Generate Undo for LOB Index Pages

Regardless of whether `LOGGING` or `NOLOGGING` is set, LOBs never generate rollback information (undo) for LOB data pages because old LOB data is stored in versions.

Rollback information that is created for LOBs tends to be small because it is only for the LOB index page changes.

**Parent topic:** LOGGING / NOLOGGING Parameter for BasicFiles LOBs

##### 13.3.9.2 When LOGGING is Set Oracle Generates Full Redo for LOB Data Pages

`NOLOGGING` is intended to be used when a customer does not care about media recovery.

Thus, if the disk/tape/storage media fails, then you cannot recover your changes from the log because the changes were never logged.

- NOLOGGING is Useful for Bulk Loads or Inserts.

**Parent topic:** LOGGING / NOLOGGING Parameter for BasicFiles LOBs

###### 13.3.9.2.1 NOLOGGING is Useful for Bulk Loads or Inserts.

For instance, when loading data into the LOB, if you do not care about redo and can just start the load over if it fails, set the LOB data segment storage characteristics to `NOCACHE` `NOLOGGING`. This provides good performance for the initial load of data.

Once you have completed loading data, if necessary, use `ALTER` `TABLE` to modify the LOB storage characteristics for the LOB data segment for normal LOB operations, for example, to `CACHE` or `NOCACHE` `LOGGING`.

**Note:**

`CACHE` implies that you also get `LOGGING`.

**Parent topic:** When LOGGING is Set Oracle Generates Full Redo for LOB Data Pages

#### 13.3.10 LOGGING/FILESYSTEM_LIKE_LOGGING for SecureFiles LOBs

The `NOLOGGING` and `LOGGING` parameters are applied to using LOBs in the same manner as for other table operations.

In the usual case, if the `logging_clause` is omitted, then the SecureFiles inherits its logging attribute from the tablespace in which it resides. In this case, if `NOLOGGING` is the default value, the SecureFiles defaults to `FILESYSTEM_LIKE_LOGGING`.

**Note:**

Using the `CACHE` option results in improved performance when reading and writing data from the LOB column. However, it can potentially age other non-LOB pages out of the buffer cache prematurely.

- CACHE Implies LOGGING
- SecureFiles and an Efficient Method of Generating REDO and UNDO
- FILESYSTEM_LIKE_LOGGING is Useful for Bulk Loads or Inserts

**Parent topic:** LOB Storage Parameters

##### 13.3.10.1 CACHE Implies LOGGING

For SecureFiles, there is a further alternative depending on how `CACHE` is specified:

- If `CACHE` is specified and the `LOGGING` clause is omitted, then `LOGGING` is used.

- If `CACHE` is not specified and the logging_clause is omitted. Then the process defaults in the same way as it does for tables and partitioned tables. That is, the `LOGGING` value is obtained from the tablespace in which the LOB value resides. If the tablespace is `NOLOGGING`, then the SecureFiles defaults to `FILESYSTEM_LIKE_LOGGING`.

Keep the following issues in mind.

**Parent topic:** LOGGING/FILESYSTEM_LIKE_LOGGING for SecureFiles LOBs

##### 13.3.10.2 SecureFiles and an Efficient Method of Generating REDO and UNDO

This means that Oracle Database determines if it is more efficient to generate `REDO` and `UNDO` for the change to a block, similar to heap blocks, or if it generates a version and full `REDO` of the new block similar to BasicFiles LOBs.

**Parent topic:** LOGGING/FILESYSTEM_LIKE_LOGGING for SecureFiles LOBs

##### 13.3.10.3 FILESYSTEM_LIKE_LOGGING is Useful for Bulk Loads or Inserts

For instance, when loading data into the LOB, if you do not care about `REDO` and can just start the load over if it fails, set the LOB data segment storage characteristics to `FILESYSTEM_LIKE_LOGGING`. This provides good performance for the initial load of data.

Once you have completed loading data, if necessary, use `ALTER` `TABLE` to modify the LOB storage characteristics for the LOB data segment for normal LOB operations. For example, to `CACHE` or `NOCACHE` `LOGGING`.

**Parent topic:** LOGGING/FILESYSTEM_LIKE_LOGGING for SecureFiles LOBs

#### 13.3.11 CHUNK

A chunk is one or more Oracle blocks.

You can specify the chunk size for the BasicFiles LOB when creating the table that contains the LOB. This corresponds to the data size used by Oracle Database when accessing or modifying the LOB value. Part of the chunk is used to store system-related information and the rest stores the LOB value. The API you are using has a function that returns the amount of space used in the LOB chunk to store the LOB value. In PL/SQL use `DBMS_LOB.GETCHUNKSIZE`. In OCI, use `OCILobGetChunkSize()`.

**Note:**

If the tablespace block size is the same as the database block size, then `CHUNK` is also a multiple of the database block size. The default `CHUNK` size is equal to the size of one tablespace block, and the maximum value is 32K.

- The Value of CHUNK
- Set INITIAL and NEXT to Larger than CHUNK

**See Also:**

"[Terabyte-Size LOB Support](advanced-design-considerations.md)" for information about maximum LOB sizes

**Parent topic:** LOB Storage Parameters

##### 13.3.11.1 The Value of CHUNK

Once the value of `CHUNK` is chosen (when the LOB column is created), it cannot be changed.

Because you cannot change the value `CHUNK`, it is important that you choose a value which optimizes your storage and performance requirements. For SecureFiles, `CHUNK` is an advisory size and is provided for backward compatibility purposes.

- Space Considerations
- Performance Considerations

**Parent topic:** CHUNK

###### 13.3.11.1.1 Space Considerations

The value of `CHUNK` does not matter for LOBs that are stored inline.

Inline storage occurs when `ENABLE` `STORAGE` `IN` `ROW` is set, and the size of the LOB locator and the LOB data is less than approximately 4000 bytes. However, when the LOB data is stored out-of-line, it always takes up space in multiples of the `CHUNK` parameter. This can lead to a large waste of space if your data is small, but the `CHUNK` is set to a large number. Table 13-4 illustrates this point:

Table 13-4 Data Size and CHUNK Size

| Data Size                   | CHUNK Size | Disk Space Used to Store the LOB | Space Utilization (Percent) |
|:----------------------------|:-----------|:---------------------------------|:----------------------------|
| 3500 enable storage in row  | irrelevant | 3500 in row                      | 100                         |
| 3500 disable storage in row | 32 KB      | 32 KB                            | 10                          |
| 3500 disable storage in row | 4 KB       | 4 KB                             | 90                          |
| 33 KB                       | 32 KB      | 64 KB                            | 51                          |
| 2 GB +10                    | 32 KB      | 2 GB + 32 KB                     | 99+                         |

**Parent topic:** The Value of CHUNK

###### 13.3.11.1.2 Performance Considerations

It is more efficient to access LOBs in big chunks.

You can set `CHUNK` to the data size most frequently accessed or written. For example, if only one block of LOB data is accessed at a time, then set `CHUNK` to the size of one block. If you have big LOBs, and read or write big amounts of data, then choose a large value for `CHUNK`.

**Parent topic:** The Value of CHUNK

##### 13.3.11.2 Set INITIAL and NEXT to Larger than CHUNK

If you explicitly specify storage characteristics for the LOB, then make sure that `INITIAL` and `NEXT` for the LOB data segment storage are set to a size that is larger than the `CHUNK` size.

For example, if the database block size is 2KB and you specify a `CHUNK` of 8KB, then make sure that `INITIAL` and `NEXT` are bigger than 8KB and preferably considerably bigger (for example, at least 16KB).

Put another way: If you specify a value for `INITIAL,` `NEXT`, or the LOB `CHUNK `size, then make sure they are set in the following manner:

- `CHUNK` \<= `NEXT`

- `CHUNK` \<= `INITIAL`

**Parent topic:** CHUNK

#### 13.3.12 ENABLE or DISABLE STORAGE IN ROW Clause

The `ENABLE` \| `DISABLE` `STORAGE` `IN` `ROW` clause is used to indicate whether the LOB should be stored inline (in the row) or out-of-line. If the LOB is saved `IN` `ROW`,

- Exadata pushdown is enabled for LOBs without compression and encryption, and LOBs with securefile compression

- In-Memory is enabled for LOBs without compression and encryption

**Note:**

You may not alter this specification once you have made it: if you `ENABLE STORAGE IN ROW`, then you cannot alter it to `DISABLE STORAGE IN ROW` and vice versa.

The default is `ENABLE` `STORAGE` `IN` `ROW`.

**Parent topic:** LOB Storage Parameters

#### 13.3.13 Guidelines for ENABLE or DISABLE STORAGE IN ROW

The maximum amount of LOB data stored in the row is the maximum `VARCHAR2` size (4000). This includes the control information and the LOB value. If you indicate that the LOB should be stored in the row, once the LOB value and control information is larger than approximately 4000, then the LOB value is automatically moved out of the row.

This suggests the following guidelines:

The default, ENABLE STORAGE IN ROW, is usually the best choice for the following reasons:

- Small LOBs: If the LOB is small (less than approximately 4000 bytes), then the whole LOB can be read while reading the row without extra disk I/O.

- Large LOBs: If the LOB is big (greater than approximately 4000 bytes), then the control information is still stored in the row if ENABLE STORAGE IN ROW is set, even after moving the LOB data out of the row. This control information could enable us to read the out-of-line LOB data faster.

However, in some cases `DISABLE STORAGE IN ROW` is a better choice. This is because storing the LOB in the row increases the size of the row. This impacts performance if you are doing a lot of base table processing, such as full table scans, multi-row accesses (range scans), or many `UPDATE`/`SELECT` to columns other than the LOB columns.

**Parent topic:** LOB Storage Parameters

### 13.4 LOB Columns Indexing

There are different techniques you can use to index LOB columns.

**Note:**

After you move a LOB column any existing table indexes must be rebuilt.

Topics:

- Domain Indexing on LOB Columns

- Text Indexes on LOB Columns

- Function-Based Indexes on LOBs

- Extensible Indexing on LOB Columns

- Oracle Text Indexing Support for XML

<!-- -->

- Domain Indexing on LOB Columns
- Text Indexes on LOB Columns
- Function-Based Indexes on LOBs
- Extensible Indexing on LOB Columns
- Oracle Text Indexing Support for XML

**Parent topic:** LOB Storage with Applications

#### 13.4.1 Domain Indexing on LOB Columns

You might be able to improve the performance of queries by building indexes specifically attuned to your domain. Extensibility interfaces provided with the database allow for domain indexing, a framework for implementing such domain specific indexes.

**Note:**

You cannot build a B-tree or bitmap index on a LOB column.

**See Also:**

[Oracle Database Data Cartridge Developer's Guide ](../addci/building-domain-indexes.md)for information on building domain specific indexes.

**Parent topic:** LOB Columns Indexing

#### 13.4.2 Text Indexes on LOB Columns

Depending on the nature of the contents of the LOB column, one of the Oracle Text options could also be used for building indexes.

For example, if a text document is stored in a `CLOB` column, then you can build a text index to speed up the performance of text-based queries over the `CLOB` column.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/index.md) for an example of using a `CLOB` column to store text data

**Parent topic:** LOB Columns Indexing

#### 13.4.3 Function-Based Indexes on LOBs

A function-based index is an index built on an expression. It extends your indexing capabilities beyond indexing on a column. A function-based index increases the variety of ways in which you can access data.

Function-based indexes cannot be built on nested tables or LOB columns. However, you can build function-based indexes on VARRAYs.

Like extensible indexes and domain indexes on LOB columns, function-based indexes are also automatically updated when a DML operation is performed on the LOB column. Function-based indexes are also updated when any extensible index is updated.

**See Also:**

[Oracle Database Development Guide ](../adfns/indexes.md)for more information on using function-based indexes.

**Parent topic:** LOB Columns Indexing

#### 13.4.4 Extensible Indexing on LOB Columns

The database provides extensible indexing, a feature which enables you to define new index types as required. This is based on the concept of cooperative indexing where a data cartridge and the database build and maintain indexes for data types such as text and spatial for example, for On-line-Analytical Processing (OLAP).

The cartridge is responsible for defining the index structure, maintaining the index content during load and update operations, and searching the index during query processing. The index structure can be stored in Oracle as heap-organized, or an index-organized table, or externally as an operating system file.

To support this structure, the database provides an indextype. The purpose of an indextype is to enable efficient search and retrieval functions for complex domains such as text, spatial, image, and OLAP by means of a data cartridge. An indextype is analogous to the sorted or bit-mapped index types that are built-in within the Oracle Server. The difference is that an indextype is implemented by the data cartridge developer, whereas the Oracle kernel implements built-in indexes. Once a new indextype has been implemented by a data cartridge developer, end users of the data cartridge can use it just as they would built-in indextypes.

When the database system handles the physical storage of domain indexes, data cartridges

- Define the format and content of an index. This enables cartridges to define an index structure that can accommodate a complex data object.

- Build, delete, and update a domain index. The cartridge handles building and maintaining the index structures. Note that this is a significant departure from the medicine indexing features provided for simple SQL data types. Also, because an index is modeled as a collection of tuples, in-place updating is directly supported.

- Access and interpret the content of an index. This capability enables the data cartridge to become an integral component of query processing. That is, the content-related clauses for database queries are handled by the data cartridge.

By supporting extensible indexes, the database significantly reduces the effort needed to develop high-performance solutions that access complex data types such as LOBs.

- Extensible Optimizer

**Parent topic:** LOB Columns Indexing

##### 13.4.4.1 Extensible Optimizer

The extensible optimizer functionality allows authors of user-defined functions and indexes to create statistics collections, selectivity, and cost functions. This information is used by the optimizer in choosing a query plan. The cost-based optimizer is thus extended to use the user-supplied information.

Extensible indexing functionality enables you to define new operators, index types, and domain indexes. For such user-defined operators and domain indexes, the extensible optimizer functionality allows users to control the three main components used by the optimizer to select an execution plan: statistics, selectivity, and cost.

**See Also:**

[Oracle Database Data Cartridge Developer's Guide](../addci/introduction-to-data-cartridges.md)

**Parent topic:** Extensible Indexing on LOB Columns

#### 13.4.5 Oracle Text Indexing Support for XML

You can create Oracle Text indexes on `CLOB` columns and perform queries on XML data.

**See Also:**

- [Oracle XML Developer's Kit Programmer's Guide](../adxdk/introduction-to-XDK.md)

- [Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md)

- [Oracle Text Application Developer's Guide](../ccapp/understanding-oracle-text-application-development.md)

**Parent topic:** LOB Columns Indexing

### 13.5 LOB Manipulation in Partitioned Tables

You can partition tables that contain LOB columns.

Topics:

- About Manipulating LOBs in Partitioned Tables

- Partitioning a Table Containing LOB Columns

- Creating an Index on a Table Containing Partitioned LOB Columns

- Moving Partitions Containing LOBs

- Splitting Partitions Containing LOBs

- Merging Partitions Containing LOBs

<!-- -->

- About Manipulating LOBs in Partitioned Tables
- Partitioning a Table Containing LOB Columns
- Creating an Index on a Table Containing Partitioned LOB Columns
- Moving Partitions Containing LOBs
- Splitting Partitions Containing LOBs
- Merging Partitions Containing LOBs

**Parent topic:** LOB Storage with Applications

#### 13.5.1 About Manipulating LOBs in Partitioned Tables

As a result, LOBs can take advantage of all of the benefits of partitioning including the following:

- LOB segments can be spread between several tablespaces to balance I/O load and to make backup and recovery more manageable.

- LOBs in a partitioned table become easier to maintain.

- LOBs can be partitioned into logical groups to speed up operations on LOBs that are accessed as a group.

This section describes some of the ways you can manipulate LOBs in partitioned tables.

**Parent topic:** LOB Manipulation in Partitioned Tables

#### 13.5.2 Partitioning a Table Containing LOB Columns

LOBs are supported in RANGE partitioned, LIST partitioned, and HASH partitioned tables. Composite heap-organized tables can also have LOBs.

You can partition a table containing LOB columns using the following techniques:

- When the table is created using the `PARTITION BY ...` clause of the `CREATE TABLE` statement.

- Adding a partition to an existing table using the `ALTER TABLE ... ADD PARTITION` clause.

- Exchanging partitions with a table that has partitioned LOB columns using the `ALTER TABLE ... EXCHANGE PARTITION` clause. Note that `EXCHANGE PARTITION` can only be used when both tables have the same storage attributes, for example, both tables store LOBs out-of-line.

Creating LOB partitions at the same time you create the table (in the `CREATE TABLE` statement) is recommended. If you create partitions on a LOB column when the table is created, then the column can hold LOBs stored either inline or out-of-line LOBs.

After a table is created, new LOB partitions can only be created on LOB columns that are stored out-of-line. Also, partition maintenance operations, `SPLIT PARTITION` and `MERGE PARTITIONS`, only work on LOB columns that store LOBs out-of-line.

**Note:**

Once a table is created, storage attributes cannot be changed

**See Also:**

- LOB Storage Parameters for more information about LOB storage attributes

- Restrictions for LOBs in Partitioned Index-Organized Tables for additional information on LOB restrictions

**Parent topic:** LOB Manipulation in Partitioned Tables

#### 13.5.3 Creating an Index on a Table Containing Partitioned LOB Columns

To improve the performance of queries, you can create indexes on partitioned LOB columns. For example:

    CREATE INDEX index_name
       ON table_name (LOB_column_1, LOB_column_2, ...) LOCAL;

Note that only domain and function-based indexes are supported on LOB columns. Other types of indexes, such as unique indexes are not supported with LOBs.

**Parent topic:** LOB Manipulation in Partitioned Tables

#### 13.5.4 Moving Partitions Containing LOBs

You can move a LOB partition into a different tablespace. This is useful if the tablespace is no longer large enough to hold the partition. To do so, use the `ALTER TABLE ... MOVE PARTITION` clause. For example:

    ALTER TABLE current_table MOVE PARTITION partition_name
       TABLESPACE destination_table_space
       LOB (column_name) STORE AS (TABLESPACE current_tablespace);

**Parent topic:** LOB Manipulation in Partitioned Tables

#### 13.5.5 Splitting Partitions Containing LOBs

You can split a partition containing LOBs into two equally sized partitions using the `ALTER TABLE ... SPLIT PARTITION` clause. Doing so permits you to place one or both new partitions in a new tablespace. For example:

    ALTER TABLE table_name SPLIT PARTITION partition_name
       AT (partition_range_upper_bound)
       INTO (PARTITION partition_name,
          PARTITION new_partition_name TABLESPACE new_tablespace_name
             LOB (column_name) STORE AS (TABLESPACE tablespace_name)
             ... ;

**Parent topic:** LOB Manipulation in Partitioned Tables

#### 13.5.6 Merging Partitions Containing LOBs

You can merge partitions that contain LOB columns using the `ALTER TABLE ... MERGE PARTITIONS` clause.

This technique is useful for reclaiming unused partition space. For example:

    ALTER TABLE table_name
       MERGE PARTITIONS partition_1, partition_2
       INTO PARTITION new_partition TABLESPACE new_tablespace_name
          LOB (column_name) store as (TABLESPACE tablespace_name)
         ... ;

**Parent topic:** LOB Manipulation in Partitioned Tables

### 13.6 LOBs in Index Organized Tables

Index Organized Tables (IOTs) support internal and external LOB columns. For the most part, SQL DDL, DML, and piece wise operations on LOBs in IOTs produce the same results as those for normal tables. The only exception is the default semantics of LOBs during creation. The main differences are:

- Tablespace Mapping: By default, or unless specified otherwise, the LOB data and index segments are created in the tablespace in which the primary key index segments of the index organized table are created.

- Inline as Compared to Out-of-Line Storage: By default, all LOBs in an index organized table created without an overflow segment are stored out of line. In other words, if an index organized table is created without an overflow segment, then the LOBs in this table have their default storage attributes as `DISABLE` `STORAGE` `IN` `ROW`. If you forcibly try to specify an `ENABLE` `STORAGE` `IN` `ROW` clause for such LOBs, then SQL raises an error.

  On the other hand, if an overflow segment has been specified, then LOBs in index organized tables exactly mimic their semantics in conventional tables.

**See Also:**

Defining Tablespace and Storage Characteristics for Persistent LOBs

#### Example of Index Organized Table (IOT) with LOB Columns

Consider the following example:

    CREATE TABLE iotlob_tab (c1 INTEGER PRIMARY KEY, c2 BLOB, c3 CLOB, c4
    VARCHAR2(20))
      ORGANIZATION INDEX
        TABLESPACE iot_ts
        PCTFREE 10 PCTUSED 10 INITRANS 1 MAXTRANS 1 STORAGE (INITIAL 4K)
        PCTTHRESHOLD 50 INCLUDING c2
      OVERFLOW
        TABLESPACE ioto_ts
        PCTFREE 10 PCTUSED 10 INITRANS 1 MAXTRANS 1 STORAGE (INITIAL 8K) LOB (c2)
        STORE AS lobseg (TABLESPACE lob_ts DISABLE STORAGE IN ROW
                         CHUNK 16384 PCTVERSION 10 CACHE STORAGE (INITIAL 2M)
                         INDEX lobidx_c1 (TABLESPACE lobidx_ts STORAGE (INITIAL 4K)));

Executing these statements results in the creation of an index organized table `iotlob_tab` with the following elements:

- A primary key index segment in the tablespace `iot_ts`,

- An overflow data segment in tablespace `ioto_ts`

- Columns starting from column `C3` being explicitly stored in the overflow data segment

- `BLOB` (column `C2`) data segments in the tablespace `lob_ts`

- `BLOB` (column `C2`) index segments in the tablespace `lobidx_ts`

- `CLOB` (column `C3`) data segments in the tablespace `iot_ts`

- `CLOB` (column `C3`) index segments in the tablespace `iot_ts`

- `CLOB` (column `C3`) stored in line by virtue of the IOT having an overflow segment

- `BLOB` (column `C2`) explicitly forced to be stored out of line

  **Note:**

  If no overflow had been specified, then both C2 and C3 would have been stored out of line by default.

Other LOB features, such as `BFILE`s and varying character width LOBs, are also supported in index organized tables, and their usage is the same as for conventional tables.

**Parent topic:** LOB Storage with Applications

### 13.7 Restrictions on Index Organized Tables with LOB Columns

The ALTER TABLE MOVE operation cannot be performed on an index organized table with a LOB column in parallel.

Instead, use the `NOPARALLEL` clause to move the LOB column for such tables. For example:

    ALTER TABLE t1 MOVE LOB(a) STORE AS (<tablespace users>) NOPARALLEL;

**Parent topic:** LOB Storage with Applications

### 13.8 Restrictions for LOBs in Partitioned Index-Organized Tables

LOB columns are supported in range-, list-, and hash-partitioned index-organized tables with the following restrictions:

- Composite partitioned index-organized tables are not supported.

- Relational and object partitioned index-organized tables (partitioned by range, hash, or list) can hold LOBs stored as follows; however, partition maintenance operations, such as `MOVE`, `SPLIT`, and `MERGE` are not supported with:

  - VARRAY data types stored as LOB data types

  - Abstract data types with LOB attributes

  - Nested tables with LOB types

    **See Also:**

    Additional restrictions for LOB columns in general are given in "[LOB Rules and Restrictions](working-with-LOBs.md)".

**Parent topic:** LOB Storage with Applications

### 13.9 Updating LOBs in Nested Tables

To update LOBs in a nested table, you must lock the row containing the LOB explicitly. To do so, you must specify the FOR UPDATE clause in the subquery prior to updating the LOB value.

Note that locking the row of a parent table does not lock the row of a nested table containing LOB columns.

**Note:**

Nested tables containing LOB columns are the only data structures supported for creating collections of LOBs. You cannot create a `VARRAY` of any LOB data type.

**Parent topic:** LOB Storage with Applications
