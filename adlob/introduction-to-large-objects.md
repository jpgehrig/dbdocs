## 1  Introduction to Large Objects and SecureFiles

Large Objects (LOBs), SecureFiles LOBs, and Database File System (DBFS) work together with various database features to support application development.

Large Objects are used to hold large amounts of data inside Oracle Database, SecureFiles provides performance equal to or better than file system performance when using Oracle Database to store and manage Large Objects, and DBFS provides file system access to files stored in Oracle Database.

Topics:

- What Are Large Objects?

- Why Use Large Objects?

- Why Not Use LONGs?

- Different Kinds of LOBs

- LOB Locators

- Database Semantics for Internal and External LOBs

- Large Object Data Types

- About Object Data Types and LOBs

- Storage and Creation of Other Data Types with LOBs

- BasicFiles and SecureFiles LOBs

- Database File System (DBFS)

<!-- -->

- What Are Large Objects?
- Why Use Large Objects?
  Large objects allow you to store large amounts of data in several types of structures.
- Why Not Use LONGs?
  Oracle Database supports `LONG` and LOB data types. However, LOBs provide added benefits described below.
- Different Kinds of LOBs
  Different kinds of LOBs can be stored in the database or in external files.
- LOB Locators
  A LOB instance has a locator and a value.
- Database Semantics for Internal and External LOBs
  In all programmatic environments, database semantics differ between internal LOBs and external LOBs as follows:
- Large Object Data Types
  The database provides a set of large object data types as SQL data types where the term LOB generally refers to the set.
- About Object Data Types and LOBs
- Storage and Creation of Other Data Types with LOBs
  You can use LOBs to create other user-defined data types or store other data types as LOBs.
- BasicFiles and SecureFiles LOBs
  BasicFiles LOB and SecureFiles LOB are the two storage types used with Oracle Database 12c.
- Database File System (DBFS)
  Database File System (DBFS) provides a file system interface to files that are stored in an Oracle database.

**Parent topic:** [Getting Started](getting-started.md)

### 1.1 What Are Large Objects?

[Large Objects (LOBs) ](glossary.md) are a set of data types that are designed to hold large amounts of data.

The maximum size for a single LOB can range from 8 terabytes to 128 terabytes depending on how your database is configured. Storing data in LOBs enables you to access and manipulate the data efficiently in your application.

**Parent topic:** Introduction to Large Objects and SecureFiles

### 1.2 Why Use Large Objects?

Large objects allow you to store large amounts of data in several types of structures.

Topics:

- Data Types that Use Large Objects

- LOBs Used for Semistructured Data

- LOBs Used for Unstructured Data

<!-- -->

- Data Types that Use Large Objects
  Large objects are suitable for semistructured and unstructured data.
- LOBs Used for Semistructured Data
  Semistructured data include document files such as XML documents or word processor files, which contain data in a logical structure that is processed or interpreted by an application, and is not broken down into smaller logical units when stored in the database.
- LOBs Used for Unstructured Data
  Unstructured data is data that cannot be decomposed into standard components.

**Parent topic:** Introduction to Large Objects and SecureFiles

#### 1.2.1 Data Types that Use Large Objects

Large objects are suitable for semistructured and unstructured data.

Large object features allow you to store these kinds of data in the database and in operating system files that are accessed from the database.

- Semistructured data

  Semistructured data has a logical structure that is not typically interpreted by the database, for example, an XML document that your application or an external service processes. Oracle Database provides features such as Oracle XML DB, Oracle Multimedia, and Oracle Spatial and Graph to help your application work with semistructured data.

- Unstructured data

  Unstructured data is easily not broken down into smaller logical structures and is not typically interpreted by the database or your application, such as a photographic image stored as a binary file.

When you develop applications, you encounter different types of data, not all of which are suitable for large objects. For example, there is no need for the following to be created as large objects:

- Simple structured data

  Simple structured data can be organized into relational tables that are structured based on business rules.

- Complex structured data

  Complex structured data is more complex than simple structured data and is suited for the object-relational features of the Oracle database such as collections, references, and user-defined types.

With the growth of the Internet and content-rich applications, it has become imperative for Oracle Database to provide LOB support that:

- Can store unstructured and semistructured data in an efficient manner

- Is optimized for large amounts of data

- Provides a uniform way of accessing data stored within the database or outside the database

**Parent topic:** Why Use Large Objects?

#### 1.2.2 LOBs Used for Semistructured Data

Semistructured data include document files such as XML documents or word processor files, which contain data in a logical structure that is processed or interpreted by an application, and is not broken down into smaller logical units when stored in the database.

Applications that use semistructured data often use large amounts of character data. The Character Large Object (`CLOB`) and National Character Large Object (`NCLOB`) data types are ideal for storing and manipulating this kind of data.

Binary File objects (`BFILE` data types) can also store character data. You can use `BFILE`s to load read-only data from operating system files into `CLOB` or `NCLOB` instances that you then manipulate in your application.

**Parent topic:** Why Use Large Objects?

#### 1.2.3 LOBs Used for Unstructured Data

Unstructured data is data that cannot be decomposed into standard components.

This is in contrast to structured data, such as data about an employee typically containing these components: a name, stored as a string; an identifier, such as an ID number; a salary; and so on.

Unstructured data, such as a photograph, consists of a long stream of 1s and 0s. These bits are used to switch pixels on or off so that you can see the picture on a display, but the bits are not broken down into any standard components for database storage.

Also, unstructured data such as text, graphic images, still video clips, full motion video, and sound waveforms tends to be large in size. A typical employee record may be a few hundred bytes, while even small amounts of multimedia data can be thousands of times larger.

SQL data types that are ideal for large amounts of unstructured binary data include the `BLOB` data type (Binary Large Object) and the `BFILE` data type (Binary File object).

**Parent topic:** Why Use Large Objects?

### 1.3 Why Not Use LONGs?

Oracle Database supports `LONG` and LOB data types. However, LOBs provide added benefits described below.

Using LOB data types is recommended for storing large amounts of structured and semistructured data (from Oracle8i and on). Applications developed for use with Oracle7 and earlier used the `LONG` or `LONG` `RAW` data type to store large amounts of unstructured data.

You can use `LONG`-to-LOB migration to easily migrate your existing applications that access `LONG` columns, to use LOB columns.

Advantages of LOB data types over `LONG` and `LONG` `RAW` types:

- LOB Capacity: LOBs can store much larger amounts of data. LOBs can store 4 GB of data or more depending on your system configuration. `LONG` and `LONG` `RAW` types are limited to 2 GB of data.

- Number of LOB columns in a table: A table can have multiple LOB columns. LOB columns in a table can be of any LOB type. In Oracle7 Release 7.3 and higher, tables are limited to a single `LONG` or `LONG` `RAW` column.

- Random piece-wise access: LOBs support random access to data, but `LONG`s support only sequential access.

- LOBs can also be object attributes.

**See Also:**

[Migrating Columns from LONGs to LOBs](migrating-columns-from-LONGs-to-LOBs.md)

**Parent topic:** Introduction to Large Objects and SecureFiles

### 1.4 Different Kinds of LOBs

Different kinds of LOBs can be stored in the database or in external files.

LOBs in the database are sometimes also referred to as internal LOBs or internal persistent LOBs.

LOBs can be internal or external:

- Internal LOBs

- External LOBs and the BFILE Data Type

<!-- -->

- Internal LOBs
- External LOBs and the BFILE Data Type

**Parent topic:** Introduction to Large Objects and SecureFiles

#### 1.4.1 Internal LOBs

LOBs in the database are stored inside database tablespaces in a way that optimizes space and provides efficient access.

##### SQL Data Types for Internal LOBs

The following SQL data types are supported for declaring internal LOBs: `BLOB`, `CLOB`, and `NCLOB`.

**See Also:**

Large Object Data Types

##### Persistent and Temporary LOBs

Persistent and temporary LOBs are both internal LOBs (LOBs in the database).

- A persistent LOB is a LOB instance that exists in a table row in the database.

- A temporary LOB instance is created when you instantiate a LOB only within the scope of your local application.

A temporary instance becomes a persistent instance when you insert the instance into a table row.

Persistent LOBs use copy semantics and participate in database transactions. You can recover persistent LOBs in the event of transaction or media failure, and any changes to a persistent LOB value can be committed or rolled back. In other words, all the Atomicity, Consistency, Isolation, and Durability (ACID) properties that apply to database objects apply to persistent LOBs.

**Parent topic:** Different Kinds of LOBs

#### 1.4.2 External LOBs and the BFILE Data Type

External LOBs are data objects stored in operating system files, outside the database tablespaces.

`BFILE` is the SQL data type that the database uses to access external LOBs and is the only SQL data type available for external LOBs.

`BFILE`s are read-only data types. The database allows read-only byte stream access to data stored in `BFILE`s. You cannot write to or update a `BFILE` from within your application.

The database uses reference semantics with `BFILE` columns. Data stored in a table column of type `BFILE` is physically located in an operating system file, not in the database.

You typically use `BFILE`s to hold:

- Binary data that does not change while your application is running, such as graphics

- Data that is loaded into other large object types, such as a `BLOB` or `CLOB`, where the data can then be manipulated

- Data that is appropriate for byte-stream access, such as multimedia

Any storage device accessed by your operating system can hold `BFILE` data, including hard disk drives, CD-ROMs, PhotoCDs, and DVDs. The database can access `BFILE`s provided the operating system supports stream-mode access to the operating system files.

**Note:**

External LOBs do not participate in transactions. Any support for integrity and durability must be provided by the underlying file system as governed by the operating system.

**Parent topic:** Different Kinds of LOBs

### 1.5 LOB Locators

A LOB instance has a locator and a value.

A LOB locator is a reference to where the LOB value is physically stored. The LOB value is the data stored in the LOB.

When you use a LOB in an operation such as passing a LOB as a parameter, you are actually passing a LOB locator. For the most part, you can work with a LOB instance in your application without being concerned with the semantics of LOB locators. There is no requirement to dereference LOB locators, as is required with pointers in some programming languages.

**See Also:**

- "[LOB Locator and LOB Value](working-with-LOBs.md)"

- "[LOB Locators and BFILE Locators](working-with-LOBs.md)"

- "[LOB Storage Parameters](LOB-storage-with-applications.md)"

**Parent topic:** Introduction to Large Objects and SecureFiles

### 1.6 Database Semantics for Internal and External LOBs

In all programmatic environments, database semantics differ between internal LOBs and external LOBs as follows:

- Internal LOBs use copy semantics

  With copy semantics, both the LOB locator and LOB value are logically copied during insert, update, or assignment operations. This ensures that each table cell or each variable containing a LOB, holds a unique LOB instance.

- External LOBs use reference semantics

  With reference semantics, only the LOB locator is copied during insert operations. Note that update operations do not apply to external LOBs because external LOBs are read-only.
  **See Also:**

  External LOBs and the BFILE Data Type

**Parent topic:** Introduction to Large Objects and SecureFiles

### 1.7 Large Object Data Types

The database provides a set of large object data types as SQL data types where the term LOB generally refers to the set.

In general, the descriptions given for the data types in this table and related sections also apply to the corresponding data types provided for other programmatic environments.

Table 1-1 describes each large object data type that the database supports and describes the kind of data that uses it.

Table 1-1 Large Object Data Types

| SQL Data Type | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CLOB `       | Character Large Object<br>Stores string data in the database character set format. Used for large strings or documents that use the database character set exclusively. Characters in the database character set are in a fixed width format.                                                                                                                                                                                                                                                                                                                 |
| `NCLOB `      | National Character Set Large Object<br>Stores string data in National Character Set format, typically large strings or documents. Supports characters of varying width format.                                                                                                                                                                                                                                                                                                                                                                                |
| `BFILE `      | External Binary File<br>A binary file stored outside of the database in the host operating system file system, but accessible from database tables. `BFILE`s can be accessed from your application on a read-only basis. Use `BFILE`s to store static data, such as image data, that is not manipulated in applications.<br>Any kind of data, that is, any operating system file, can be stored in a `BFILE`. For example, you can store character data in a `BFILE` and then load the `BFILE` data into a `CLOB,` specifying the character set upon loading. |

**Parent topic:** Introduction to Large Objects and SecureFiles

### 1.8 About Object Data Types and LOBs

In general, there is no difference in the use of a LOB instance in a LOB column or as a member of an object data type. When used in this guide, the term LOB attribute refers to a LOB instance that is a member of an object data type. Unless otherwise specified, discussions that apply to LOB columns also apply to LOB attributes.

**Parent topic:** Introduction to Large Objects and SecureFiles

### 1.9 Storage and Creation of Other Data Types with LOBs

You can use LOBs to create other user-defined data types or store other data types as LOBs.

These are examples of data types provided with the database that are stored or created with LOB types.

Topics:

- VARRAYs Stored as LOBs

<!-- -->

- VARRAYs Stored as LOBs
  An instance of type `VARRAY` in the database is stored as an array of LOBs when you create a table in the following scenarios:

**Parent topic:** Introduction to Large Objects and SecureFiles

#### 1.9.1 VARRAYs Stored as LOBs

An instance of type `VARRAY` in the database is stored as an array of LOBs when you create a table in the following scenarios:

- If the `VARRAY` storage clause is not specified, and the declared size of varray data is more than 4000 bytes: `VARRAY varray_item STORE AS`

- If the `VARRAY` column properties are specified using the `STORE` `AS` `LOB` clause: `VARRAY varray_item STORE AS LOB ...`

**Parent topic:** Storage and Creation of Other Data Types with LOBs

### 1.10 BasicFiles and SecureFiles LOBs

BasicFiles LOB and SecureFiles LOB are the two storage types used with Oracle Database 12c.

Certain advanced features can be applied to SecureFiles LOBs, including compression and deduplication (part of the Advanced Compression Option), and encryption (part of the Advanced Security Option).

SecureFiles LOBs can only be created in a tablespace managed with Automatic Segment Space Management (ASSM).

SecureFiles is the default storage mechanism for LOBs starting with Oracle Database 12c, and Oracle strongly recommends SecureFiles for storing and managing LOBs, rather then BasicFiles. BasicFiles will be deprecated in a future release.

**See Also:**

[Using Oracle LOB Storage](using-oracle-LOBs-storage.md) for a discussion of both storage types

**Parent topic:** Introduction to Large Objects and SecureFiles

### 1.11 Database File System (DBFS)

Database File System (DBFS) provides a file system interface to files that are stored in an Oracle database.

Files stored in an Oracle database are usually stored as SecureFiles LOBs, and pathnames, directories, and other filesystem information is stored in database tables. SecureFiles LOBs is the default storage method for DBFS, but BasicFiles LOBs can be used in some situations.

**See Also:**

[What Is Database File System (DBFS)?](introducing-database-file-system.md)

With DBFS, you can make references from SecureFiles LOB locators to files stored outside the database. These references are called DBFS Links or Database File System Links.

**See Also:**

[Database File System Links](DBFS-hierarchical-store.md)

**Parent topic:** Introduction to Large Objects and SecureFiles
