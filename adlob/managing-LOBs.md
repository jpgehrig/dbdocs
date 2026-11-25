## 16  Managing LOBs: Database Administration

You must perform various administrative tasks to set up, maintain, and use a database that contains LOBs.

Topics:

- Database Utilities for Loading Data into LOBs

- Temporary LOB Management

- BFILEs Management

- Changing Tablespace Storage for a LOB

- Managing LOB Signatures

**Note:**

LOBs are not supported when the Container Database root and Pluggable Databases are in different character sets. For more information, refer to [Relocating a PDB Using CREATE PLUGGABLE DATABASE](../multi/relocating-a-pdb.md).

- Database Utilities for Loading Data into LOBs
  Certain utilities are recommended for bulk loading data into LOB columns as part of database setup or maintenance tasks.
- Temporary LOB Management
  The database keeps track of temporary LOBs in each session, and the application can determine which user owns the temporary LOB by using the session ID.
- BFILEs Management
  You need to perform various administrative tasks to manage databases that contain `BFILE`s.
- Changing Tablespace Storage for a LOB
  Database administrators use certain techniques to change the default storage for a LOB.
- Managing LOB Signatures

**Parent topic:** [LOB Administration](LOB-administration.md)

### 16.1 Database Utilities for Loading Data into LOBs

Certain utilities are recommended for bulk loading data into LOB columns as part of database setup or maintenance tasks.

The following utilities are recommended for bulk loading data into LOB columns as part of database setup or maintenance tasks:

- SQL\*Loader

- Oracle Data Pump

**Note:**

Application Developers: If you are loading data into a LOB in your application, then using the LOB APIs is recommended. See [Using LOB APIs](using-LOB-APIs.md) .

- About Using SQL\*Loader to Load LOBs
  There are two general techniques for using SQL\*Loader to load data into LOBs
- About Using SQL\*Loader to Populate a BFILE Column
  You can load data from files in the file system into a `BFILE` column.
- About Using Oracle Data Pump to Transfer LOB Data
  You can use Oracle Data Pump to transfer LOB data from one database to another.

**Parent topic:** Managing LOBs: Database Administration

#### 16.1.1 About Using SQL\*Loader to Load LOBs

There are two general techniques for using SQL\*Loader to load data into LOBs

You can use SQL\*Loader to load data into LOBs in these ways:

- Loading data from a primary data file

- Loading from a secondary data file using LOB files

Consider the following issues when loading LOBs with SQL\*Loader:

- For SQL\*Loader conventional path loads, failure to load a particular LOB does not result in the rejection of the record containing that LOB; instead, the record ends up containing an empty LOB.

  For SQL\*Loader direct-path loads, the LOB could be empty or truncated. LOBs are sent in pieces to the server for loading. If there is an error, then the LOB piece with the error is discarded and the rest of that LOB is not loaded. In other words, if the entire LOB with the error is contained in the first piece, then that LOB column is either empty or truncated.

- When loading from `LOB file`s, specify the maximum length of the field corresponding to a LOB-type column. If the maximum length is specified, then it is taken as a hint to help optimize memory usage. It is important that the maximum length specification does not underestimate the true maximum length.

- When using SQL\*Loader direct-path load, loading LOBs can take up substantial memory. If the message "SQL\*Loader 700 (out of memory)" appears when loading LOBs, then internal code is probably batching up more rows in each load call than can be supported by your operating system and process memory. A work-around is to use the ROWS option to read a smaller number of rows in each data save.

- You can also use the Direct Path API to load LOBs.

- Using `LOB file`s is recommended when loading columns containing XML data in `CLOB`s or `XMLType` columns. Consider the following validation criteria for XML documents in determining whether to use direct-path load or conventional path load with SQL\*Loader:

  - If the XML document must be validated upon loading, then use conventional path load.

  - If it is not necessary to ensure that the XML document is valid, or if you can safely assume that the XML document is valid, then you can perform a direct-path load. Direct-path load performs better because you avoid the overhead of XML validation.

  A conventional path load executes SQL `INSERT` statements to populate tables in an Oracle database.

  A direct-path load eliminates much of the Oracle database overhead by formatting Oracle data blocks and writing the data blocks directly to the database files. Additionally, it does not compete with other users for database resources, so it can usually load data at near disk speed. Considerations inherent to direct path loads, such as restrictions, security, and backup implications, are discussed in [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md).

- Tables to be loaded must already exist in the database. SQL\*Loader never creates tables. It loads existing tables that either contain data or are empty.

- The following privileges are required for a load:

  - You must have `INSERT` privileges on the table to be loaded.

  - You must have `DELETE` privileges on the table to be loaded, when using the `REPLACE` or `TRUNCATE` option to empty out the old data before loading the new data in its place.

    **See Also:**

    - [ Oracle Call Interface Programmer's Guide](../lnoci/direct-path-load-interface.md) for more information about Direct Path API

    - [Oracle Database Utilities](../sutil/loading-objects-oracle-sql-loader.md) for more information about using SQL\*Loader to load LOBs

**Parent topic:** Database Utilities for Loading Data into LOBs

#### 16.1.2 About Using SQL\*Loader to Populate a BFILE Column

You can load data from files in the file system into a `BFILE` column.

You can load data from files in the file system into a `BFILE` column.

**See Also:**

"[Supported Environments for BFILE APIs](LOB-APIs-for-BFILE-operations.md)"

Note that the `BFILE` data type stores unstructured binary data in operating system files outside the database. A `BFILE` column or attribute stores a file locator that points to a server-side external file containing the data.

**Note:**

A particular file to be loaded as a `BFILE` does not have to actually exist at the time of loading.

SQL\*Loader assumes that the necessary `DIRECTORY` objects have been created.

**See Also:**

See "[Directory Objects](LOB-APIs-for-BFILE-operations.md)" and the sections following it for more information on creating directory objects

A control file field corresponding to a `BFILE` column consists of the column name followed by the `BFILE` directive.

The `BFILE` directive takes as arguments a `DIRECTORY` object name followed by a `BFILE` name. Both of these can be provided as string constants, or they can be dynamically sourced through some other field.

**See Also:**

[Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for details on SQL\*Loader syntax

The following two examples illustrate the loading of `BFILE`s.

**Note:**

You may be required to set up the following data structures for certain examples to work (you are prompted for the password):

    CONNECT system
    Enter password:
    Connected.
    GRANT CREATE ANY DIRECTORY to samp;
    CONNECT samp
    Enter password:
    Connected.
    CREATE OR REPLACE DIRECTORY adgraphic_photo as '/tmp';
    CREATE OR REPLACE DIRECTORY adgraphic_dir as '/tmp';

In the following example based on the "[Table for LOB Examples: The PM Schema print_media Table](working-with-LOBs.md)", only the file name is specified dynamically.

Control file:

    LOAD DATA
    INFILE sample9.dat
    INTO TABLE Print_media
    FIELDS TERMINATED BY ','
    (product_id  INTEGER EXTERNAL(6),
     FileName    FILLER CHAR(30),
     ad_graphic  BFILE(CONSTANT "modem_graphic_2268_21001", FileName))

Data file:

    007, modem_2268.jpg,
    008, monitor_3060.jpg,
    009, keyboard_2056.jpg,

**Note:**

`product_ID` defaults to (255) if a size is not specified. It is mapped to the file names in the data file. `ADGRAPHIC_PHOTO` is the directory where all files are stored. `ADGRAPHIC_DIR` is a `DIRECTORY` object created previously.

In the following example, the `BFILE` and the `DIRECTORY` objects are specified dynamically.

Control file:

    LOAD DATA
    INFILE sample10.dat
    INTO TABLE Print_media
    FIELDS TERMINATED BY ','
    (
     product_id INTEGER EXTERNAL(6),
     ad_graphic BFILE (DirName, FileName),
     FileName  FILLER CHAR(30),
     DirName   FILLER CHAR(30)
    )

Data file:

    007,monitor_3060.jpg,ADGRAPHIC_PHOTO,
    008,modem_2268.jpg,ADGRAPHIC_PHOTO,
    009,keyboard_2056.jpg,ADGRAPHIC_DIR,

**Note:**

`DirName` `FILLER` `CHAR` `(30)` is mapped to the data file field containing the directory name corresponding to the file being loaded.

**Parent topic:** Database Utilities for Loading Data into LOBs

#### 16.1.3 About Using Oracle Data Pump to Transfer LOB Data

You can use Oracle Data Pump to transfer LOB data from one database to another.

Oracle Data Pump can transfer LOB data from one database to another.

Beginning with Oracle Database 12c, Data Pump has an option to create all LOB columns as SecureFiles LOBs.

**See Also:**

"[SecureFiles LOB Storage](using-oracle-LOBs-storage.md)" for an introduction to SecureFiles LOBs

When Data Pump recreates tables, however, it recreates them as they existed in the source database, by default. Therefore, if a LOB column was a BasicFiles LOB in the source database, Data Pump attempts to recreate it as a BasicFiles LOB in the imported database. You can force creation of LOBs as SecureFiles LOBs in the tables being recreated using a `TRANSFORM` parameter for the command line or a `LOB_STORAGE` parameter for the `DBMS_DATAPUMP` and `DBMS_METADATA` packages.

**Note:**

The transform name is not valid in transportable import.

**See Also:**

- [Oracle Database Utilities](../sutil/datapump-import-utility.md) for specific table syntax used with SecureFiles LOBs

- [Oracle Database Utilities](../sutil/oracle-data-pump.md) for details on using Oracle Data Pump

**Parent topic:** Database Utilities for Loading Data into LOBs

### 16.2 Temporary LOB Management

The database keeps track of temporary LOBs in each session, and the application can determine which user owns the temporary LOB by using the session ID.

The database provides a `v$` view called `v$temporary_lobs`. As a database administrator, you can use this view to monitor and guide any emergency cleanup of temporary space used by temporary LOBs.

Temporary LOB data is stored in temporary tablespaces. As a database administrator, you control data storage resources for temporary LOB data by controlling user access to temporary tablespaces and by the creation of different temporary tablespaces.

**See Also:**

[Oracle Database Administrator's Guide](../admin/managing-tablespaces.md) for details on managing temporary tablespaces

**Parent topic:** Managing LOBs: Database Administration

### 16.3 BFILEs Management

You need to perform various administrative tasks to manage databases that contain `BFILE`s.

Topics:

- Rules for Using Directory Objects and BFILEs

- Setting Maximum Number of Open BFILEs

<!-- -->

- Rules for Using Directory Objects and BFILEs
  You can create a directory object or `BFILE` objects if these conditions are met.
- Setting Maximum Number of Open BFILEs
  A limited number of `BFILE`s can be open simultaneously in each session.

**Parent topic:** Managing LOBs: Database Administration

#### 16.3.1 Rules for Using Directory Objects and BFILEs

You can create a directory object or `BFILE` objects if these conditions are met.

When you create a directory object or `BFILE` objects, ensure that the following conditions are met:

- The operating system file must not be a symbolic or hard link.

- The operating system directory path named in the Oracle DIRECTORY object must be an existing operating system directory path.

- The operating system directory path named in the Oracle DIRECTORY object should not contain any symbolic links in its components.

**Parent topic:** BFILEs Management

#### 16.3.2 Setting Maximum Number of Open BFILEs

A limited number of `BFILE`s can be open simultaneously in each session.

The initialization parameter, `SESSION_MAX_OPEN_FILES`, defines an upper limit on the number of simultaneously open files in a session.

The default value for this parameter is 10. Using this default, you can open a maximum of 10 files at the same time in each session. To alter this limit, the database administrator must change the parameter value in the `init.ora` file. For example:

    SESSION_MAX_OPEN_FILES=20

If the number of unclosed files reaches the `SESSION_MAX_OPEN_FILES` value, then you cannot open additional files in the session. To close all open files, use the `DBMS_LOB.FILECLOSEALL` call.

**Parent topic:** BFILEs Management

### 16.4 Changing Tablespace Storage for a LOB

Database administrators use certain techniques to change the default storage for a LOB.

As the database administrator, you can use the following techniques to change the default storage for a LOB after the table has been created:

- Using ALTER TABLE... MODIFY: You can change LOB tablespace storage as follows:

<!-- -->

    ALTER TABLE test MODIFY
      LOB (lob1)
        STORAGE  (
        NEXT         4M
        MAXEXTENTS   100
        PCTINCREASE  50
                )

**Note:**

The `ALTER TABLE` syntax for modifying an existing LOB column uses the `MODIFY LOB` clause, not the `LOB...STORE AS` clause. The `LOB...STORE AS` clause is only for newly added LOB columns.

There are two kinds of LOB storage clauses: `LOB_storage_clause` and `modify_LOB_storage_clause. `In the `ALTER TABLE MODIFY LOB` statement, you can only specify the `modify_LOB_storage_clause`.

- Using ALTER TABLE... MOVE: You can also use the `MOVE` clause of the `ALTER` `TABLE` statement to change LOB tablespace storage. For example:

<!-- -->

    ALTER TABLE test MOVE
        TABLESPACE tbs1
        LOB (lob1, lob2)
        STORE AS (
              TABLESPACE tbs2
              DISABLE STORAGE IN ROW);

**Parent topic:** Managing LOBs: Database Administration

### 16.5 Managing LOB Signatures

Starting from Oracle Database 19c release, you can configure signature-based security for large object (`LOB`) locators using the `LOB_SIGNATURE_ENABLE` initialization parameter.

- To enable signature, set the `LOB_SIGNATURE_ENABLE` initialization parameter at `init.ora`, or using the following `ALTER SYSTEM` command. Also ensure that you have set the compatibility to 12.2.0.2 or above.

  `ALTER SYSTEM SET LOB_SIGNATURE_ENABLE = [TRUE|FALSE];`

- The following `ALTER` statement helps to encrypt, re-key, and delete the signature keys.

  `ALTER DATABASE DICTIONARY [ENCRYPT|REKEY|DELETE] CREDENTIALS;`

For more information, refer to the Oracle Database Security Guide.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/managing-security-for-application-developers.md)

**Parent topic:** Managing LOBs: Database Administration
