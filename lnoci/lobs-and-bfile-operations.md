This chapter describes LOB and BFILE operations.

This chapter contains these topics:

- About Using OCI Functions for LOBs

- About Creating and Modifying Persistent LOBs

- About Associating a BFILE in a Table with an Operating System File

- LOB Attributes of an Object

- Array Interface for LOBs

- About Using LOBs of Size Greater than 4 GB

- LOB and BFILE Functions in OCI

- Temporary LOB Support

- Prefetching of LOB Data, Length, and Chunk Size

- Options of SecureFiles LOBs

### 9.1 About Using OCI Functions for LOBs

OCI includes a set of functions for performing operations on large objects (LOBs) in a database.

Persistent LOBs (`BLOB`s, `CLOB`s, `NCLOB`s) are stored in the database tablespaces in a way that optimizes space and provides efficient access. These LOBs have the full transactional support of the Oracle database. `BFILE`s are large data objects stored in the server's operating system files outside the database tablespaces.

OCI also provides support for temporary LOBs, which can be used like local variables for operating on LOB data.

`BFILE`s are read-only. Oracle Database supports only binary `BFILE`s.

Beginning with Oracle Database 12c Release 2 (12.2), most LOB functions support Application Continuity.

Beginning with Oracle Database 12`c` Release 2 (12.2), OCI LOB APIs support distributed operations on remote LOBs (CLOB, BLOB) except for OCI LOB APIs for BFILES. This includes support for certain queries that select a remote LOB locator that in previous releases returned an error. The only restriction is that all LOB APIs that take in two locators should have both LOBs collocated at one database. The following LOB functions throw an error when a remote locator is passed to it: `OCILobAssign()`, `OCILobLocatorAssign()`, `OCILobEnableBuffering()`, `OCILobDisableBuffering()`, `OCILobFlushBuffer()`, `OCILobArrayRead()`, `OCILobArrayWrite()`, and `OCILobLoadFromFile2()`.

**See Also:**

- [OCI Demonstration Programs](oci-demo-programs.md) for code samples showing the use of LOBs

- `$ORACLE_HOME/rdbms/demo/lobs/oci/` for specific LOB code samples

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md) for the `DBMS_LOB` package

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md)

- [When Application Continuity in OCI Can Fail Over](high-availability-in-oci.md) for a complete list.

- [Deprecated Lob Functions](deprecated-oci-functions.md) for information about support for Application Continuity also includes some deprecated LOB functions for compatibility.

### 9.2 About Creating and Modifying Persistent LOBs

LOB instances can be either persistent (stored in the database) or temporary (existing only in the scope of your application).

Do not confuse the concept of a persistent LOB with a persistent object.

There are two ways of creating and modifying persistent LOBs:

- Using the data interface

  You can create a LOB by inserting character data into a `CLOB` column or `RAW` data into a `BLOB` column directly. You can also modify LOBs by using a SQL `UPDATE` statement, to bind character data into a `CLOB` column or `RAW` data into a `BLOB` column.

  Insert, update, and select of remote LOBs (over a dblink) is supported because neither the remote server nor the local server is of a release earlier than Oracle Database 10g Release 2. The data interface only supports data size up to 2 GB – 1, the maximum size of an `sb4` data type.

- Using the LOB locator

  You create a new internal LOB by initializing a new LOB locator using `OCIDescriptorAlloc()`, calling `OCIAttrSet()` to set it to empty (using the `OCI_ATTR_LOBEMPTY` attribute), and then binding the locator to a placeholder in an `INSERT` statement. Doing so inserts the empty locator into a table with a LOB column or attribute. You can then perform a `SELECT`...`FOR` `UPDATE` operation on this row to get the locator, and write to it using one of the OCI LOB functions.

  **Note:**

  To modify a LOB column or attribute (write, copy, trim, and so forth), you must lock the row containing the LOB. One way to do this is to use a `SELECT...FOR UPDATE` statement to select the locator before performing the operation.

For any LOB write command to be successful, a transaction must be open. If you commit a transaction before writing the data, you must lock the row again (by reissuing the `SELECT...FOR UPDATE` statement, for example), because the commit closes the transaction.

**See Also:**

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/data-interface-for-persistent-LOBs.md) chapter about data interface for persistent LOBs for more information and examples

- [About Binding LOB Data](binding-and-defining-in-oci.md) for usage and examples for both `INSERT` and `UPDATE`

- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)

- [OCIAttrSet()](handle-and-descriptor-functions.md)

### 9.3 About Associating a BFILE in a Table with an Operating System File

The `BFILENAME` function can be used in an `INSERT` statement to associate an external server-side (operating system) file with a `BFILE` column or attribute in a table.

Using `BFILENAME` in an `UPDATE` statement associates the `BFILE` column or attribute with a different operating system file. `OCILobFileSetName()` can also be used to associate a `BFILE` in a table with an operating system file. `BFILENAME` is usually used in an `INSERT` or `UPDATE` statement without bind variables, and `OCILobFileSetName()` is used for bind variables.

**See Also:**

- [OCILobFileSetName()](lob-functions.md)

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/working-with-LOBs.md) for more information about the `BFILENAME` function

### 9.4 LOB Attributes of an Object

An OCI application can use the `OCIObjectNew()` function to create a persistent or transient object with a LOB attribute.

This section includes the following topics:

- Writing to a LOB Attribute of an Object

- Transient Objects with LOB Attributes

**See Also:**

[OCIObjectNew()](oci-miscellaneous-object-functions.md)

#### 9.4.1 Writing to a LOB Attribute of an Object

It is possible to use OCI to create a new persistent object with a LOB attribute and write to that LOB attribute.

The application would follow these steps when using a LOB locator:

1.  Call `OCIObjectNew()` to create a persistent object with a LOB attribute.
2.  Mark the object as "dirty" (modified).
3.  Flush the object, thereby inserting a row into the table.
4.  Repin the latest version of the object (or refresh the object), thereby retrieving the object from the database and acquiring a valid locator for the LOB.
5.  Call `OCIObjectWrite2()` using the LOB locator in the object to write the data.

There is a second way of writing to a LOB attribute. When using the data interface, you can bind or define character data for a `CLOB` attribute or `RAW` data for a `BLOB` attribute.

**See Also:**

- [OCI Object-Relational Programming](oci-object-relational-programming.md) and the chapters that follow it for more information about objects

- [About Binding LOB Data](binding-and-defining-in-oci.md) for usage and examples for both `INSERT` and `UPDATE statements`

- [About Defining LOB Data](binding-and-defining-in-oci.md) for usage and examples of `SELECT` statements

- [OCIObjectNew()](oci-miscellaneous-object-functions.md)

- [OCILobWrite2()](lob-functions.md)

#### 9.4.2 Transient Objects with LOB Attributes

An application can call `OCIObjectNew()` and create a transient object with an internal LOB (`BLOB`, `CLOB`, `NCLOB`) attribute.

However, you cannot perform any operations, such as read or write, on the LOB attribute because transient objects with LOB attributes are not supported. Calling `OCIObjectNew()` to create a transient internal LOB type does not fail, but the application cannot use any LOB operations with the transient LOB.

An application can, however, create a transient object with a `BFILE` attribute and use the `BFILE` attribute to read data from a file stored in the server's file system. The application can also call `OCIObjectNew()` to create a transient `BFILE`.

**See Also:**

[OCIObjectNew()](oci-miscellaneous-object-functions.md)

### 9.5 Array Interface for LOBs

You can use the OCI array interface with LOBs, just as with any other data type.

There are two ways of using the array interface.

- Using the data interface

  You can bind or define arrays of character data for a `CLOB` column or `RAW` data for a `BLOB` column. You can use array bind and define interfaces to insert and select multiple rows with LOBs in one round-trip to the server.

- Using the LOB locator

  When using the LOB locator you must allocate the descriptors, as shown in the following code example.

  Using the LOB Locator and Allocating the Descriptors

      /* First create an array of OCILobLocator pointers: */
      OCILobLocator *lobp[10];

      for (i=0; i < 10; i++)
      { OCIDescriptorAlloc (...,&lobp[i],...);

      /* Then bind the descriptor as follows */
        OCIBindByPos(... &lobp[i], ...);

**See Also:**

- [About Binding LOB Data](binding-and-defining-in-oci.md) for usage and examples for both `INSERT` and `UPDATE statements`

- [About Defining LOB Data](binding-and-defining-in-oci.md) for usage and examples of `SELECT` statements

### 9.6 About Using LOBs of Size Greater than 4 GB

Starting with Oracle Database 10g Release 1 of OCI, functions were introduced to support LOBs of size greater than 4 GB. These new functions can also be used in new applications for LOBs of less than 4 GB.

Oracle Database enables you to create tablespaces with block sizes different from the database block size. The maximum size of a LOB depends on the size of the tablespace blocks. The tablespace block size in which the LOB is stored controls the value of `CHUNK`, which is a parameter of LOB storage. When you create a LOB column, you specify a value for `CHUNK`, which is the number of bytes to be allocated for LOB manipulation. The value must be a multiple of the tablespace block size, or Oracle Database rounds up to the next multiple. (If the tablespace block size equals the database block size, then `CHUNK` is also a multiple of the database block size.) The default `CHUNK` size is one tablespace block, and the maximum value is 32 KB.

In this guide, 4 GB is defined as 4 gigabytes – 1, or 4,294,967,295 bytes. The maximum size of a LOB, persistent or temporary, is (4 gigabytes – 1) \* (`CHUNK`). The maximum LOB size can range from 8 terabytes (TB) to 128 TB.

For example, suppose that your database block size is 32 KB and you create a tablespace with a nonstandard block size of 8 KB. Further suppose that you create a table with a LOB column and specify a `CHUNK` size of 16 KB (which is a multiple of the 8 KB tablespace block size). Then the maximum size of a LOB in this column is (4 gigabytes – 1) \* 16 KB.

The maximum size of a `BFILE` is the maximum file size allowed in the operating system, or `UB8MAXVAL`, whichever is smaller.

Older LOB functions use `ub4` as the data types of some parameters, and the `ub4` data type can only hold up to 4 GB. The newer functions use parameters of 8-byte length, `oraub8`, which is a data type defined in `oratypes.h`. The data types `oraub8` and `orasb8` are mapped to appropriate 64-bit native data types depending on the compiler and operating system. Macros are used to not define `oraub8` and `orasb8` if compiling in 32-bit mode with strict ANSI option.

`OCILobGetChunkSize()` returns the usable chunk size in bytes for `BLOB`s, `CLOB`s, and `NCLOB`s. The number of bytes stored in a chunk is actually less than the size of the `CHUNK` parameter due to internal storage overhead. The function `OCILobGetStorageLimit()` is provided to return the maximum size in bytes of internal LOBs in the current installation.

**Note:**

Oracle Database does not support `BFILE`s larger than 4 gigabytes in any programmatic environment. An additional file size limit imposed by your operating system also applies to `BFILE`s.

This section includes the following topics:

- Functions to Use for the Increased LOB Sizes

- Compatibility and Migration

- [OCILobGetChunkSize()](lob-functions.md)

- [OCILobGetStorageLimit()](lob-functions.md)

#### 9.6.1 Functions to Use for the Increased LOB Sizes

Eight functions with names that end in "2" and that use the data type `oraub8` in place of the data type `ub4` were introduced in Oracle Database 10g Release 1.

Other changes were made in the read and write functions (`OCILobRead2()`, `OCILobWrite2()`, and `OCILobWriteAppend2()`) to solve several problems:

Problem: Before Oracle Database 10g Release 1, the parameter `amtp` assumed either byte or char length for LOBs based on the locator type and character set. It was complicated and users did not have the flexibility to use byte length or char length according to their requirements.

Solution: Read/Write calls should take both `byte_amtp` and `char_amtp` parameters as replacement for the `amtp` parameter. The `char_amtp` parameter is preferred for `CLOB` and `NCLOB`, and the `byte_amtp` parameter is only considered as input if `char_amtp` is zero. On output for `CLOB` and `NCLOB`, both `byte_amtp` and `char_amtp` parameters are filled. For `BLOB` and `BFILE`, the `char_ampt` parameter is ignored for both input and output.

Problem: For `OCILobRead2()`, there is no flag to indicate polling mode. There is no easy way for the users to say "I have a 100-byte buffer. Fill it as much as you can." Previously, they had to estimate how many characters to specify for the amount. If they guessed too much, they were forced into polling mode unintentionally. The user code thus can get trapped in the polling mode and subsequent OCI calls are all blocked.

Solution: This call should take `piece` as an input parameter and if `OCI_ONE_PIECE` is passed, it should fill the buffer as much as possible and come out even if the amount indicated by the `byte_amtp` parameter or `char_amtp` parameter is more than the buffer length. The value of `bufl` is used to specify the maximum amount of bytes to read.

Problem: After calling for a LOB write in polling mode, users do not know how many chars or bytes are actually fetched till the end of the polling.

Solution: Both the `byte_amtp` and `char_amtp` parameters must be updated after each call in polling mode.

Problem: While reading or writing data in streaming mode with callback, users must use the same buffer for each piece of data.

Solution: The callback function must have two new parameters to provide the buffer and the buffer length. Callback functions can set the buffer parameter to `NULL` to follow old behavior: to use the default buffer passed in the first call for all the pieces.

**See Also:**

- [LOB Functions](lob-functions.md)

- [OCILobRead2()](lob-functions.md)

- [OCILobWrite2()](lob-functions.md)

- [OCILobWriteAppend2()](lob-functions.md)

#### 9.6.2 Compatibility and Migration

Existing OCI programs can be enhanced to process larger amounts of LOB data that are greater than 4 GB.

Table 9-1 summarizes compatibility issues in this table, "old" refers to releases before Oracle Database 10g Release 1, and NA means not applicable.

Table 9-1 LOB Functions Compatibility and Migration

| LOB Function                                        | Old Client/New or Old Server(1)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | New Client/Old Server                                           | New Client/New Server                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:----------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [OCILobArrayRead()](lob-functions.md)               | <sup>Foot 2</sup>NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | OK until piece size and offset are \< 4 GB.                     | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobArrayWrite()](lob-functions.md)              | NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK until piece size and offset are \< 4 GB.                     | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobCopy2()](lob-functions.md)                   | NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK until LOB size, piece size (amount) and offset are \< 4 GB.  | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobCopy()](deprecated-oci-functions.md)         | OK; limit is 4 GB.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK                                                              | OK; limit is 4 GB.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobErase2()](lob-functions.md)                  | NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK until piece size and offset are \< 4 GB.                     | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobErase()](deprecated-oci-functions.md)        | OK; limit is 4 GB.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK                                                              | OK; limit is 4 GB.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobGetLength2()](lob-functions.md)              | NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK                                                              | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobGetLength()](deprecated-oci-functions.md)    | OK; limit is 4 GB.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK                                                              | OK; `OCI_ERROR` if LOB size \> 4 GB.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| [OCILobLoadFromFile2()](lob-functions.md)           | NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK until LOB size, piece size (amount), and offset are \< 4 GB. | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobLoadFromFile()](deprecated-oci-functions.md) | OK; limit is 4 GB.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK                                                              | OK; limit is 4 GB.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobRead2()](lob-functions.md)                   | NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK until LOB size, piece size (amount), and offset are \< 4 GB. | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobRead()](deprecated-oci-functions.md)         | OK; limit 4 GB.<br>With new server: `OCI_ERROR` is returned if you try to read any amount \>= 4 GB from any offset \< 4 GB. This is because when you read any amount \>= 4 GB, that results in an overflow of returned value in \*amtp, and so it is flagged as an error.<br>Note:<br>• If you read up to 4 GB – 1 from offset, that is not flagged as an error.<br>• When you use streaming mode with polling, no error is returned if no attempt is made to use piece size \> 4 GB (you can read data \> 4 GB in this case). | OK                                                              | OK.<br>`OCI_ERROR` is returned if you try to read any amount \>= 4 GB from any offset \< 4 GB. This is because when you read any amount \>= 4 GB, that results in an overflow of returned value in \*amtp, and so it is flagged as an error.<br>Note:<br>• If you read up to 4 GB – 1 from offset, that is not to be flagged as an error.<br>• When you use streaming mode with polling, no error is returned if no attempt is made to use piece size \> 4 GB. |
| [OCILobTrim2()](lob-functions.md)                   | NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK                                                              | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobTrim()](deprecated-oci-functions.md)         | OK; limit 4 GB.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | OK                                                              | OK; limit 4 GB.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| [OCILobWrite2()](lob-functions.md)                  | NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK until LOB size, piece size (amount) and offset are \< 4 GB.  | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobWrite()](deprecated-oci-functions.md)        | OK; limit 4 GB.<br>With new server:<br>`OCI_ERROR` is returned if you write any amount \>= 4 GB (from any offset \< 4 GB) because that results an in overflow of returned value in `*amtp`.<br>Note: Updating a LOB of 10 GB from any offset up to 4 GB –1 by up to 4 GB –1 amount of data is not flagged as an error.                                                                                                                                                                                                         | OK                                                              | OK.<br>`OCI_ERROR` is returned if you write any amount \> =4 GB (from any offset \< 4 GB) because that results in an overflow of returned value in \*amtp.<br>Note: Updating a LOB of 10 GB from any offset up to 4 GB –1 by up to 4 GB –1 amount of data is not flagged as an error.                                                                                                                                                                          |
| [OCILobWriteAppend2()](lob-functions.md)            | NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OK until LOB size and piece size are \<4 GB.                    | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [OCILobWriteAppend()](deprecated-oci-functions.md)  | OK; limit 4 GB.<br>With new server: `OCI_ERROR` is returned if you append any amount \>= 4 GB of data because that results in an overflow of returned value in `*amtp`.                                                                                                                                                                                                                                                                                                                                                        | OK                                                              | OK; limit 4 GB.<br>`OCI_ERROR` is returned if you append any amount \>= 4 GB of data because that results in an overflow of returned value in `*amtp`.                                                                                                                                                                                                                                                                                                         |
| [OCILobGetStorageLimit()](lob-functions.md)         | NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Error                                                           | OK                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

<sup>Footnote 1</sup> The term "old" refers to releases before Oracle Database 10g Release 1.

<sup>Footnote 2</sup>

NA means not applicable.

Use the functions that end in "2" when using the current server and current client. Mixing deprecated functions with functions that end in "2" can result in unexpected situations, such as data written using `OCILobWrite2()` being greater than 4 GB if the application tries to read it with `OCILobRead()` and gets only partial data (if a callback function is not used). In most cases, the application gets an error message when the size crosses 4 GB and the deprecated functions are used. However, there is no issue if you use those deprecated functions for LOBs of size smaller than 4 GB.

### 9.7 LOB and BFILE Functions in OCI

In all LOB operations that involve offsets into the data, the offset begins at 1. For LOB operations, such as `OCILobCopy2()`, `OCILobErase2()`, `OCILobLoadFromFile2()`, and `OCILobTrim2()`, the `amount` parameter is in characters for `CLOB`s and `NCLOB`s, regardless of the client-side character set.

These LOB operations refer to the amount of LOB data on the server. When the client-side character set is of varying width, the following general rules apply to the `amount` and `offset` parameters in LOB calls:

- `amount` - When the amount parameter refers to the server-side LOB, the amount is in characters. When the amount parameter refers to the client-side buffer, the amount is in bytes.

- `offset` - Regardless of whether the client-side character set is varying-width, the offset parameter is always in characters for `CLOB`s or `NCLOB`s and in bytes for `BLOB`s or `BFILE`s.

Exceptions to these general rules are noted in the description of the specific LOB call.

This section includes the following topics:

- About Improving LOB Read/Write Performance

- LOB Buffering Functions

- Functions for Opening and Closing LOBs

- LOB Read and Write Callbacks

**See Also:**

- [LOB Functions](lob-functions.md)

- [Buffer Expansion During OCI Binding](binding-and-defining-in-oci.md)

- [OCILobCopy2()](lob-functions.md)

- [OCILobErase2()](lob-functions.md)

- [OCILobLoadFromFile2()](lob-functions.md)

- [OCILobTrim2()](lob-functions.md)

#### 9.7.1 About Improving LOB Read/Write Performance

How to improve LOB Read/Write performance.

Here are some hints to improve performance:

- About Using Data Interface for LOBs

- About Using OCILobGetChunkSize()

- About Using OCILobWriteAppend2()

- About Using OCILobArrayRead() and OCILobArrayWrite()

##### 9.7.1.1 About Using Data Interface for LOBs

You can bind or define character data for a `CLOB` column or `RAW` data for a `BLOB` column.

This requires only one round-trip for inserting or selecting a LOB, as opposed to the traditional LOB interface that requires multiple round-trips.

**See Also:**

- [About Binding LOB Data](binding-and-defining-in-oci.md) for usage and examples for both `INSERT` and `UPDATE` statements

- [About Defining LOB Data](binding-and-defining-in-oci.md) for usage and examples of `SELECT` statements

##### 9.7.1.2 About Using OCILobGetChunkSize()

`OCILobGetChunkSize()` returns the usable chunk size in bytes for `BLOB`s, `CLOB`s, and `NCLOB`s.

You can use the `OCILobGetChunkSize()` call to improve the performance of LOB read and write operations for BasicFile LOBs. When a read or write is done on BasicFile LOB data whose size is a multiple of the usable chunk size and the operation starts on a chunk boundary, performance is improved. There is no requirement for SecureFile LOBs to be written or read with `OCILobGetChunkSize()` alignment.

Calling `OCILobGetChunkSize()` returns the usable chunk size of the LOB, so that an application can batch a series of write operations for the entire chunk, rather than issuing multiple LOB write calls for the same chunk.

**See Also:**

- Options of SecureFiles LOBs

- [OCILobGetChunkSize()](lob-functions.md)

##### 9.7.1.3 About Using OCILobWriteAppend2()

OCI provides a shortcut for more efficient writing of data to the end of a LOB.

The `OCILobWriteAppend2()` call appends data to the end of a LOB without first requiring a call to `OCILobGetLength2()` to determine the starting point for an `OCILobWrite2()` operation. `OCILobWriteAppend2()` does both steps.

**See Also:**

- [OCILobWriteAppend2()](lob-functions.md)

- [OCILobGetLength2()](lob-functions.md)

- [OCILobWrite2()](lob-functions.md)

##### 9.7.1.4 About Using OCILobArrayRead() and OCILobArrayWrite()

You can improve performance by using by using `OCILobArrayRead()` to read LOB data for multiple LOB locators and `OCILobArrayWrite()` to write LOB data for multiple LOB locators.

These functions, which were introduced in Oracle Database 10g Release 2, reduce the number of round-trips for these operations.

**See Also:**

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/using-LOB-APIs.md) sections "LOB Array Read" and "LOB Array Write" for more information and code examples that show how to use these functions with callback functions and in piecewise mode

- [OCILobArrayRead()](lob-functions.md)

- [OCILobArrayWrite()](lob-functions.md)

#### 9.7.2 LOB Buffering Functions

These LOB functions are deprecated. Use the LOB prefetch feature in place of these LOB buffering functions.

OCI provides several calls for controlling LOB buffering for small reads and writes of internal LOB values:

- `OCILobEnableBuffering()`

- `OCILobDisableBuffering()`

- `OCILobFlushBuffer()`

These functions enable applications that are using internal LOBs (`BLOB`, `CLOB`, `NCLOB`) to buffer small reads and writes in client-side buffers. This reduces the number of network round-trips and LOB versions, thereby improving LOB performance significantly.

**See Also:**

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/index.md) for more information on LOB buffering, see the chapter about using LOB APIs.

- [LOB Function Round-Trips](oci-function-server-round-trips.md) for a list of the server round-trips required for each function

- Prefetching of LOB Data, Length, and Chunk Size

- [OCILobEnableBuffering()](deprecated-oci-functions.md)

- [OCILobDisableBuffering()](deprecated-oci-functions.md)

- [OCILobFlushBuffer()](deprecated-oci-functions.md)

#### 9.7.3 Functions for Opening and Closing LOBs

OCI provides functions to explicitly open a LOB, `OCILobOpen()`, to close a LOB, `OCILobClose()`, and to test whether a LOB is open, `OCILobIsOpen()`.

These functions mark the beginning and end of a series of LOB operations so that specific processing, such as updating indexes, can be performed when a LOB is closed.

For internal LOBs, the concept of openness is associated with a LOB and not its locator. The locator does not store any information about the state of the LOB. It is possible for more than one locator to point to the same open LOB. However, for `BFILE`s, being open is associated with a specific locator. Hence, more than one open call can be performed on the same `BFILE` by using different locators.

If an application does not wrap LOB operations within a set of `OCILobOpen()` and `OCILobClose()` calls, then each modification to the LOB implicitly opens and closes the LOB, thereby firing any triggers associated with changes to the LOB.

If LOB operations are not wrapped within open and close calls, any extensible indexes on the LOB are updated as LOB modifications are made, and thus are always valid and may be used at any time. If the LOB is modified within a set of `OCILobOpen()` and `OCILobClose()` calls, triggers are not fired for individual LOB modifications. Triggers are only fired after the `OCILobClose()` call, so indexes are not updated until after the close call and thus are not valid within the open and close calls. `OCILobIsOpen()` can be used with internal LOBs and `BFILEs`.

An error is returned when you commit the transaction before closing all opened LOBs that were opened by the transaction. When the error is returned, the LOB is no longer marked as open, but the transaction is successfully committed. Hence, all the changes made to the LOB and non-LOB data in the transaction are committed, but the domain and functional indexing are not updated. If this happens, rebuild your functional and domain indexes on the LOB column.

A LOB opened when there is no transaction must be closed before the end of the session. If there are LOBs open at the end of session, the LOB is no longer marked as open and the domain and functional indexing is not updated. If this happens, rebuild your functional and domain indexes on the LOB column.

This section includes the following topic: Restrictions on Opening and Closing LOBs.

**See Also:**

- [OCILobOpen()](lob-functions.md)

- [OCILobClose()](lob-functions.md)

- [OCILobIsOpen()](lob-functions.md)

##### 9.7.3.1 Restrictions on Opening and Closing LOBs

What are the restrictions on opening and closing LOBs.

The LOB opening and closing mechanism has the following restrictions:

- An application must close all previously opened LOBs before committing a transaction. Failing to do so results in an error. If a transaction is rolled back, all open LOBs are discarded along with the changes made. Because the LOBs are not closed, so the associated triggers are not fired.

- Although there is no limit to the number of open internal LOBs, there is a limit on the number of open files as determined by the `SESSION_MAX_OPEN_FILES` parameter. Assigning an already opened locator to another locator does not count as opening a new LOB.

- It is an error to open or close the same internal LOB twice within the same transaction, either with different locators or the same locator.

- It is an error to close a LOB that has not been opened.

  **Note:**

  The definition of a transaction within which an open LOB value must be closed is one of the following:

  - Between `SET TRANSACTION` and `COMMIT`

  - Between `DATA` `MODIFYING` `DML` or `SELECT`` ... FOR UPDATE` and `COMMIT`.

  - Within an autonomous transaction block

**See Also:**

- `SESSION_MAX_OPEN_FILES` parameter in [Oracle Database Reference](../refrn/SESSION_MAX_OPEN_FILES.md)

- [OCI Demonstration Programs](oci-demo-programs.md) for examples of the use of the [OCILobOpen()](lob-functions.md) and [OCILobClose()](lob-functions.md) calls in the online demonstration programs

- [Table C-2](oci-function-server-round-trips.md)

#### 9.7.4 LOB Read and Write Callbacks

OCI supports read and write callback functions.

The following sections describe the use of callbacks in more detail:

- Callback Interface for Streaming

- Reading LOBs by Using Callbacks

- Writing LOBs by Using Callbacks

##### 9.7.4.1 Callback Interface for Streaming

User-defined read and write callback functions for inserting or retrieving data provide an alternative to the polling methods for streaming LOBs.

These functions are implemented by you and registered with OCI through the `OCILobRead2()`, `OCILobWriteAppend2()`, and `OCILobWrite2()` calls. These callback functions are called by OCI whenever they are required.

**See Also:**

- [OCILobRead2()](lob-functions.md)

- [OCILobWriteAppend2()](lob-functions.md)

- [OCILobWrite2()](lob-functions.md)

##### 9.7.4.2 Reading LOBs by Using Callbacks

The user-defined read callback function is registered through the `OCILobRead2()` function.

The callback function should have the following prototype:

    CallbackFunctionName ( void *ctxp, CONST void *bufp, oraub8 len, ub1 piece,
                           void **changed_bufpp, oraub8 *changed_lenp);

The first parameter, `ctxp`, is the context of the callback that is passed to OCI in the `OCILobRead2()` function call. When the callback function is called, the information provided by you in `ctxp` is passed back to you (OCI does not use this information on the way IN). The `bufp` parameter in `OCILobRead2()`) is the pointer to the storage where the LOB data is returned and `bufl` is the length of this buffer. It tells you how much data has been read into the buffer provided.

If the buffer length provided in the original `OCILobRead2()` call is insufficient to store all the data returned by the server, then the user-defined callback is called. In this case, the `piece` parameter indicates whether the information returned in the buffer is the first, next, or last piece.

The parameters `changed_bufpp` and `changed_lenp` can be used inside the callback function to change the buffer dynamically. The `changed_bufpp` parameter should point to the address of the changed buffer and the `changed_lenp` parameter should point to the length of the changed buffer. The `changed_bufpp` and `changed_lenp` parameters need not be used inside the callback function if the application does not change the buffer dynamically.

Example 9-1 shows a code fragment that implements read callback functions using `OCILobRead2()`. Assume that `lobl` is a valid locator that has been previously selected, `svchp` is a valid service handle, and `errhp` is a valid error handle. In the example, the user-defined function `cbk_read_lob()` is repeatedly called until all the LOB data has been read.

Example 9-1 Implementing Read Callback Functions Using OCILobRead2()

    ...
    oraub8   offset = 1;
    oraub8   loblen = 0;
    oraub8   byte_amt = 0;
    oraub8   char_amt = 0
    ub1      bufp[MAXBUFLEN];

    sword retval;
    byte_amtp = 4294967297;     /* 4 gigabytes plus 1 */

    if (retval = OCILobRead2(svchp, errhp, lobl, &byte_amt, &char_amt, offset,
      (void *) bufp, (oraub8) MAXBUFLEN, (void *) 0, OCI_FIRST_PIECE,
      cbk_read_lob, (ub2) 0, (ub1) SQLCS_IMPLICIT))
    {
         (void) printf("ERROR: OCILobRead2() LOB.\n");
         report_error();
    }
    ...
    sb4 cbk_read_lob(ctxp, bufxp, len, piece, changed_bufpp, changed_lenp)
    void       *ctxp;
    CONST void *bufxp;
    oraub8      len;
    ub1         piece;
    void       **changed_bufpp;
    oraub8      *changed_lenp;
    {
        static ub4 piece_count = 0;
        piece_count++;

        switch (piece)
       {
          case OCI_LAST_PIECE:     /*--- buffer processing code goes here ---*/
              (void) printf("callback read the %d th piece\n\n", piece_count);
              piece_count = 0;
              break;
          case OCI_FIRST_PIECE:   /*--- buffer processing code goes here ---*/
              (void) printf("callback read the %d th piece\n", piece_count);
              /* --Optional code to set changed_bufpp and changed_lenp if the
                  buffer must be changed dynamically --*/
              break;
          case OCI_NEXT_PIECE:   /*--- buffer processing code goes here ---*/
              (void) printf("callback read the %d th piece\n", piece_count);
             /* --Optional code to set changed_bufpp and changed_lenp if the
                 buffer must be changed dynamically --*/
              break;
          default:
              (void) printf("callback read error: unknown piece = %d.\n", piece);
               return OCI_ERROR;
         }
        return OCI_CONTINUE;
    }

**See Also:**

[OCILobRead2()](lob-functions.md)

##### 9.7.4.3 Writing LOBs by Using Callbacks

Similar to read callbacks, the user-defined write callback function is registered through the `OCILobWrite2()` function.

The callback function should have the following prototype:

    CallbackFunctionName ( void *ctxp, void *bufp, oraub8 *lenp, ub1 *piecep,
                            void **changed_bufpp, oraub8 *changed_lenp);

The first parameter, `ctxp`, is the context of the callback that is passed to OCI in the `OCILobWrite2()` function call. The information provided by you in `ctxp` is passed back to you when the callback function is called by OCI (OCI does not use this information on the way IN). The `bufp` parameter is the pointer to a storage area; you provide this pointer in the call to `OCILobWrite2()`.

After inserting the data provided in the call to `OCILobWrite2()` any data remaining is inserted by the user-defined callback. In the callback, provide the data to insert in the storage indicated by `bufp` and also specify the length in `lenp`. You also indicate whether it is the next (`OCI_NEXT_PIECE`) or the last (`OCI_LAST_PIECE`) piece using the `piecep` parameter. You must ensure that the storage pointer that is provided by the application does not write more than the allocated size of the storage.

The parameters `changed_bufpp` and `changed_lenp` can be used inside the callback function to change the buffer dynamically. The `changed_bufpp` parameter should point to the address of the changed buffer and the `changed_lenp` parameter should point to the length of the changed buffer. The `changed_bufpp` and `changed_lenp` parameters need not be used inside the callback function if the application does not change the buffer dynamically.

Example 9-2 shows a code fragment that implements write callback functions using `OCILobWrite2()`. Assume that `lobl` is a valid locator that has been locked for updating, `svchp` is a valid service handle, and `errhp` is a valid error handle. The user-defined function `cbk_write_lob()` is repeatedly called until the `piecep` parameter indicates that the application is providing the last piece.

Example 9-2 Implementing Write Callback Functions Using OCILobWrite2()

    ...

    ub1      bufp[MAXBUFLEN];
    oraub8   byte_amt = MAXBUFLEN * 20;
    oraub8   char_amt = 0;
    oraub8   offset = 1;
    oraub8   nbytes = MAXBUFLEN;

    /*-- code to fill bufp with data goes here. nbytes should reflect the size and
     should be less than or equal to MAXBUFLEN --*/
    if (retval = OCILobWrite2(svchp, errhp, lobl, &byte_amt, &char_amt, offset,
        (void*)bufp, (ub4)nbytes, OCI_FIRST_PIECE, (void *)0, cbk_write_lob,
        (ub2) 0, (ub1) SQLCS_IMPLICIT))
    {
       (void) printf("ERROR: OCILobWrite2().\n");
       report_error();
       return;
    }
    ...
    sb4 cbk_write_lob(ctxp, bufxp, lenp,  piecep, changed_bufpp, changed_lenp)
    void    *ctxp;
    void    *bufxp;
    oraub8  *lenp;
    ub1       *piecep;
    void  **changed_bufpp;
    oraub8  *changed_lenp;
    {
        /*-- code to fill bufxp with data goes here. *lenp should reflect the
            size and should be less than or equal to MAXBUFLEN -- */
        /* --Optional code to set changed_bufpp and changed_lenp if the
            buffer must be changed dynamically --*/
        if (this is the last data buffer)
            *piecep = OCI_LAST_PIECE;
        else
            *piecep = OCI_NEXT_PIECE;
        return OCI_CONTINUE;
    }

**See Also:**

[OCILobWrite2()](lob-functions.md)

### 9.8 Temporary LOB Support

OCI provides functions for creating and freeing temporary LOBs, `OCILobCreateTemporary()` and `OCILobFreeTemporary()`, and a function for determining whether a LOB is temporary, `OCILobIsTemporary()`.

Temporary LOBs are not permanently stored in the database, but act like local variables for operating on LOB data. OCI functions that operate on standard (persistent) LOBs can also be used on temporary LOBs.

As with persistent LOBs, all functions operate on the locator for the temporary LOB, and the actual LOB data is accessed through the locator.

Temporary LOB locators can be used as arguments to the following types of SQL statements:

- `UPDATE` - The temporary LOB locator can be used as a value in a `WHERE` clause when testing for nullity or as a parameter to a function. The locator can also be used in a `SET` clause.

- `DELETE` - The temporary LOB locator can be used in a `WHERE` clause when testing for nullity or as a parameter to a function.

- `SELECT` - The temporary LOB locator can be used in a `WHERE` clause when testing for nullity or as a parameter to a function. The temporary LOB can also be used as a return variable in a `SELECT...INTO` statement when selecting the return value of a function.

**Note:**

If you select a permanent locator into a temporary locator, the temporary locator is overwritten with the permanent locator. In this case, the temporary LOB is not implicitly freed. You must explicitly free the temporary LOB before the `SELECT...INTO` operation. If the temporary LOB is not freed explicitly, it is not freed until the end of its specified `duration`. Unless you have another temporary locator pointing to the same LOB, you no longer have a locator pointing to the temporary LOB, because the original locator was overwritten by the `SELECT...INTO` operation.

This section includes the following topics:

- Creating and Freeing Temporary LOBs

- Temporary LOB Durations

- About Freeing Temporary LOBs

- Take Care When Assigning Pointers

- Temporary LOB Example

**See Also:**

- [OCILobCreateTemporary()](lob-functions.md)

- [OCILobFreeTemporary()](lob-functions.md)

- [OCILobIsTemporary()](lob-functions.md)

#### 9.8.1 Creating and Freeing Temporary LOBs

You create a temporary LOB with the `OCILobCreateTemporary()` function.

The parameters passed to this function include a value for the duration of the LOB. The default duration is for the length of the current session. All temporary LOBs are deleted at the end of the duration. Users can reclaim temporary LOB space by explicitly freeing the temporary LOB with the `OCILobFreeTemporary()` function. A temporary LOB is empty when it is created.

When creating a temporary LOB, you can also specify whether the temporary LOB is read into the server's buffer cache.

To make a temporary LOB permanent, use `OCILobCopy2()` to copy the data from the temporary LOB into a permanent one. You can also use the temporary LOB in the `VALUES` clause of an `INSERT` statement, as the source of the assignment in an `UPDATE` statement, or assign it to a persistent LOB attribute and then flush the object. Temporary LOBs can be modified using the same functions that are used for standard LOBs.

**Note:**

The most efficient way to insert an empty LOB is to bind a temporary LOB with no value assigned to it. This uses less resources than the following method.

    INSERT INTO tab1 VALUES(EMPTY_CLOB())

**See Also:**

- [OCILobCreateTemporary()](lob-functions.md)

- [OCILobFreeTemporary()](lob-functions.md)

- [OCILobCopy2()](lob-functions.md)

#### 9.8.2 Temporary LOB Durations

OCI supports several predefined durations for temporary LOBs, and a set of functions that the application can use to define application-specific durations.

The predefined durations and their associated attributes are:

- Call, `OCI_DURATION_CALL`, only on the server side

- Session, `OCI_DURATION_SESSION`

The session duration expires when the containing session or connection ends. The call duration expires at the end of the current OCI call.

When you run in object mode, you can also define application-specific durations. An application-specific duration, also referred to as a user duration, is defined by specifying the start of a duration using `OCIDurationBegin()` and the end of the duration using `OCIDurationEnd()`.

**Note:**

User-defined durations are only available if an application has been initialized in object mode.

Each application-specific duration has a duration identifier that is returned by `OCIDurationBegin()` and is guaranteed to be unique until `OCIDurationEnd()` is called. An application-specific duration can be as long as a session duration.

At the end of a duration, all temporary LOBs associated with that duration are freed. The descriptor associated with the temporary LOB must be freed explicitly with the `OCIDescriptorFree()` call.

User-defined durations can be nested; one duration can be defined as a child duration of another user duration. It is possible for a parent duration to have child durations that have their own child durations.

**Note:**

When a duration is started with `OCIDurationBegin()`, one of the parameters is the identifier of a parent duration. When a parent duration is ended, all child durations are also ended.

**See Also:**

- [OCIDurationBegin()](cartridge-services-memory-services.md)

- [OCIDurationEnd()](cartridge-services-memory-services.md)

- [OCIDescriptorFree()](handle-and-descriptor-functions.md)

#### 9.8.3 About Freeing Temporary LOBs

Any time that your OCI program obtains a LOB locator from SQL or PL/SQL, use the `OCILobIsTemporary()` function to check that the locator is temporary.

If it is, then free the locator when your application is finished with it by using the `OCILobFreeTemporary()` call. The locator can be from a define during a select or an out bind. A temporary LOB duration is always upgraded to a session duration when it is shipped to the client side. The application must do the following before the locator is overwritten by the locator of the next row:

    OCILobIsTemporary(env, err, locator, is_temporary);
    if(is_temporary)
        OCILobFreeTemporary(svc, err, locator);

**See Also:**

- [OCILobIsTemporary()](lob-functions.md)

- [OCILobFreeTemporary()](lob-functions.md)

#### 9.8.4 Take Care When Assigning Pointers

Special care must be taken when assigning `OCILobLocator` pointers.

Pointer assignments create a shallow copy of the LOB. After the pointer assignment, source and target LOBs point to the same copy of data. This behavior is different from using LOB APIs, such as `OCILobAssign()` or `OCILobLocatorAssign()`, to perform assignments. When the APIs are used, the locators logically point to independent copies of data after assignment.

For temporary LOBs, before pointer assignments, you must ensure that any temporary LOB in the target LOB locator is freed by `OCILobFreeTemporary()`. When `OCILobLocatorAssign()` is used, the original temporary LOB in the target LOB locator variable, if any, is freed before the assignment happens.

Before an out-bind variable is reused in executing a SQL statement, you must free any temporary LOB in the existing out-bind LOB locator buffer by using the `OCILobFreeTemporary()` call.

**See Also:**

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/performance-guidelines.md) for information in the section about temporary LOB performance guidelines

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/performance-guidelines.md) for a discussion of optimal performance of temporary LOBs

- [OCILobAssign()](lob-functions.md)

- [OCILobLocatorAssign()](lob-functions.md)

- [OCILobFreeTemporary()](lob-functions.md)

- [OCILobLocatorAssign()](lob-functions.md)

#### 9.8.5 Temporary LOB Example

Shows how temporary LOBs can be used.

Example 9-3 shows how temporary LOBs can be used.

Example 9-3 Using Temporary LOBs

    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    #include <oci.h>

    /* Function Prototype */
    static void checkerr (/*_ OCIError *errhp, sword status _*/);
    sb4 select_and_createtemp (OCILobLocator *lob_loc,
                               OCIError      *errhp,
                               OCISvcCtx     *svchp,
                               OCIStmt       *stmthp,
                               OCIEnv        *envhp);
    /* This function reads in a single video frame from the print_media table.
    Then it creates a temporary LOB. The temporary LOB that is created is read
    through the CACHE, and is automatically cleaned up at the end of the user's
    session, if it is not explicitly freed sooner. This function returns OCI_SUCCESS
    if it completes successfully or OCI_ERROR if it fails. */

    sb4 select_and_createtemp (OCILobLocator *lob_loc,
                               OCIError      *errhp,
                               OCISvcCtx     *svchp,
                               OCIStmt       *stmthp,
                               OCIEnv        *envhp)
    {
      OCIDefine     *defnp1;
      OCIBind       *bndhp;
      text          *sqlstmt;
      int rowind =1;
      ub4 loblen = 0;
      OCILobLocator *tblob;
      printf ("in select_and_createtemp \n");
        if(OCIDescriptorAlloc((void*)envhp, (void **)&tblob,
                              (ub4)OCI_DTYPE_LOB, (size_t)0, (void**)0))
      {
        printf("failed in OCIDescriptor Alloc in select_and_createtemp \n");
        return OCI_ERROR;
     }
      /* arbitrarily select where Clip_ID =1 */
      sqlstmt=(text *)"SELECT Frame FROM print_media WHERE product_ID = 1 FOR UPDATE";
      if (OCIStmtPrepare2(svchp, stmthp, errhp, sqlstmt, (ub4) strlen((char *)sqlstmt),
                         NULL, 0, (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT))
      {
          (void) printf("FAILED: OCIStmtPrepare() sqlstmt\n");
          return OCI_ERROR;
      }
      /* Define for BLOB */
      if (OCIDefineByPos(stmthp, &defnp1, errhp, (ub4)1, (void *) &lob_loc, (sb4)0,
                 (ub2) SQLT_BLOB, (void *)0, (ub2 *)0, (ub2 *)0, (ub4) OCI_DEFAULT))
      {
        (void) printf("FAILED: Select locator: OCIDefineByPos()\n");
        return OCI_ERROR;
      }
      /* Execute the select and fetch one row */
      if (OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4) 0,
                       (CONST OCISnapshot*) 0, (OCISnapshot*) 0, (ub4) OCI_DEFAULT))
      {
        (void) printf("FAILED: OCIStmtExecute() sqlstmt\n");
        return OCI_ERROR;
      }
      if(OCILobCreateTemporary(svchp, errhp, tblob, (ub2)0, SQLCS_IMPLICIT,
                             OCI_TEMP_BLOB, OCI_ATTR_NOCACHE, OCI_DURATION_SESSION))
      {
        (void) printf("FAILED: CreateTemporary() \n");
        return OCI_ERROR;
      }
      if (OCILobGetLength(svchp, errhp, lob_loc, &loblen) != OCI_SUCCESS)
      {
        printf("OCILobGetLength FAILED\n");
        return OCI_ERROR;
      }
      if (OCILobCopy(svchp, errhp, tblob,lob_loc,(ub4)loblen, (ub4) 1, (ub4) 1))
      {
        printf( "OCILobCopy FAILED \n");
      }
      if(OCILobFreeTemporary(svchp,errhp,tblob))
      {
        printf ("FAILED: OCILobFreeTemporary call \n");
        return OCI_ERROR;
      }
         return OCI_SUCCESS;
    }
    int main(char *argv, int argc)
    {
      /* OCI Handles */
      OCIEnv        *envhp;
      OCIServer     *srvhp;
      OCISvcCtx     *svchp;
      OCIError      *errhp;
      OCISession    *authp;
      OCIStmt       *stmthp;
      OCILobLocator *clob, *blob;
      OCILobLocator *lob_loc;
      int type =1;
      /* Initialize and Log on */
      OCIEnvCreate(&envhp, OCI_DEFAULT, (void *)0, 0, 0, 0,
            (size_t)0, (void *)0);
      (void) OCIHandleAlloc( (void *) envhp, (void **) &errhp, OCI_HTYPE_ERROR,
                              (size_t) 0, (void **) 0);
      /* server contexts */
      (void) OCIHandleAlloc( (void *) envhp, (void **) &srvhp, OCI_HTYPE_SERVER,
                             (size_t) 0, (void **) 0);
       /* service context */
      (void) OCIHandleAlloc( (void *) envhp, (void **) &svchp, OCI_HTYPE_SVCCTX,
                             (size_t) 0, (void **) 0);
        /* attach to Oracle Database */
      (void) OCIServerAttach( srvhp, errhp, (text *)"", strlen(""), 0);
        /* set attribute server context in the service context */
      (void) OCIAttrSet ((void *) svchp, OCI_HTYPE_SVCCTX,
                         (void *)srvhp, (ub4) 0,
                         OCI_ATTR_SERVER, (OCIError *) errhp);
       (void) OCIHandleAlloc((void *) envhp,
                            (void **)&authp, (ub4) OCI_HTYPE_SESSION,
                            (size_t) 0, (void **) 0);
       (void) OCIAttrSet((void *) authp, (ub4) OCI_HTYPE_SESSION,
                        (void *) "scott", (ub4)5,
                        (ub4) OCI_ATTR_USERNAME, errhp);
      (void) OCIAttrSet((void *) authp, (ub4) OCI_HTYPE_SESSION,
                        (void *) "password", (ub4) 5,
                        (ub4) OCI_ATTR_PASSWORD, errhp);
      /* Begin a User Session */
      checkerr(errhp, OCISessionBegin ( svchp,  errhp, authp, OCI_CRED_RDBMS,
                                        (ub4) OCI_DEFAULT));
      (void) OCIAttrSet((void *) svchp, (ub4) OCI_HTYPE_SVCCTX,
                        (void *) authp, (ub4) 0,
                        (ub4) OCI_ATTR_SESSION, errhp);
      /* ------- Done logging in ----------------------------------*/
       /* allocate a statement handle */
      checkerr(errhp, OCIHandleAlloc( (void *) envhp, (void **) &stmthp,
                                 OCI_HTYPE_STMT, (size_t) 0, (void **) 0));
      checkerr(errhp, OCIDescriptorAlloc((void *)envhp, (void **)&lob_loc,
                       (ub4) OCI_DTYPE_LOB, (size_t) 0, (void **) 0));
      /* Subroutine calls begin here */
      printf("calling select_and_createtemp\n");
      select_and_createtemp (lob_loc, errhp, svchp,stmthp,envhp);
      return 0;
    }
    void checkerr(errhp, status)
    OCIError *errhp;
    sword status;
    {
      text errbuf[512];
      sb4 errcode = 0;
      switch (status)
      {
      case OCI_SUCCESS:
        break;
      case OCI_SUCCESS_WITH_INFO:
        (void) printf("Error - OCI_SUCCESS_WITH_INFO\n");
        break;
      case OCI_NEED_DATA:
        (void) printf("Error - OCI_NEED_DATA\n");
        break;
      case OCI_NO_DATA:
        (void) printf("Error - OCI_NODATA\n");
        break;
      case OCI_ERROR:
        (void) OCIErrorGet((void *)errhp, (ub4) 1, (text *) NULL, &errcode,
                            errbuf, (ub4) sizeof(errbuf), OCI_HTYPE_ERROR);
        (void) printf("Error - %.*s\n", 512, errbuf);
        break;
      case OCI_INVALID_HANDLE:
        (void) printf("Error - OCI_INVALID_HANDLE\n");
        break;
      case OCI_STILL_EXECUTING:
        (void) printf("Error - OCI_STILL_EXECUTE\n");
        break;
      case OCI_CONTINUE:
        (void) printf("Error - OCI_CONTINUE\n");
        break;
      default:
        break;
      }
    }

### 9.9 Prefetching of LOB Data, Length, and Chunk Size

To improve OCI access of smaller LOBs, LOB data can be prefetched and cached while also fetching the locator.

This applies to internal LOBs, temporary LOBs, and `BFILE`s. Take the following steps to prepare your application:

1.  Set the `OCI_ATTR_DEFAULT_LOBPREFETCH_SIZE` attribute for the session handle. The value of this attribute indicates the default prefetch data size for a LOB locator. This attribute value enables prefetching for all the LOB locators fetched in the session. The default value for this attribute is zero (no prefetch of LOB data). This option relieves the application developer from setting the prefetch LOB size for each define handle. You can either set this attribute or set (in Step 3) `OCI_ATTR_LOBPREFETCH_SIZE`.
2.  Perform the prepare and define steps for the statement to be executed.
3.  You can override the default prefetch size, if required, for the LOB locators to be fetched, by setting `OCI_ATTR_LOBPREFETCH_SIZE` attribute for the define handle. This optional attribute provides control of the prefetch size for the locators fetched from a particular column.
4.  Set the `OCI_ATTR_LOBPREFETCH_LENGTH` attribute to the prefetch LOB length and chunk size. This is mandatory to be set to `TRUE` for the attribute (`OCI_ATTR_LOBPREFETCH_SIZE`) described in item 1 to work.
5.  Execute the statement.
6.  Call [OCILobRead2()](lob-functions.md) or [OCILobArrayRead()](lob-functions.md) with individual LOB locators; OCI takes the data from the prefetch buffer, does the necessary character conversion, and copies the data into the LOB read buffer (no change in LOB semantic). If the data requested is bigger than the prefetch buffer, then it will require additional round-trips.
7.  Call [OCILobGetLength2()](lob-functions.md) and [OCILobGetChunkSize()](lob-functions.md) to obtain the length and chunk size without making round-trips to the server.

Example 9-4 Prefetching of LOB Data, Length, and Chunk Size

    ...
    ub4 default_lobprefetch_size = 2000;                  /* Set default size to 2K */
    ...
    /* set LOB prefetch attribute to session */
    OCIAttrSet (sesshp, (ub4) OCI_HTYPE_SESSION,
                (void *)&default_lobprefetch_size,               /* attribute value */
                0,                      /* attribute size; not required to specify; */
                (ub4) OCI_ATTR_DEFAULT_LOBPREFETCH_SIZE,
                errhp);
    ...
    /* select statement */
    char *stmt = "SELECT lob1 FROM lob_table";
    ...
    /* declare and allocate LOB locator */
    OCILobLocator * lob_locator;
    lob_locator = OCIDescriptorAlloc(..., OCI_DTYPE_LOB, ...);

    OCIDefineByPos(..., 1, (void *) &lob_locator, ..., SQLT_CLOB, ...);
    ...
    /* Override the default prefetch size to 4KB */
    ub4 prefetch_size = 4000;
    OCIAttrSet (defhp,  OCI_HTYPE_DEFINE,
                (void *) &prefetch_size                             /* attr value */,
                0                  /* restricting prefetch size to be ub4 max val */,
                OCI_ATTR_LOBPREFETCH_SIZE                            /* attr type */,
                errhp);
    ...
    /* Set prefetch length attribute */
    boolean prefetch_length = TRUE;
    OCIAttrSet( defhp,  OCI_HTYPE_DEFINE,
                (dvoid *) &prefetch_length  /* attr value */,
                0,
                OCI_ATTR_LOBPREFETCH_LENGTH  /* attr type */,
                errhp );
    ...
    /* execute the statement. 4KB of data for the LOB is read and
     * cached in descriptor cache buffer.
     */
    OCIStmtExecute (svchp, stmthp, errhp,
                    1,               /* iters */
                    0,               /* row offset */
                    NULL,            /* snapshot IN */
                    NULL,            /* snapshot out */
                    OCI_DEFAULT);    /* mode */
    ...
    oraub8 char_amtp = 4000;
    oraub8 lob_len;
    ub4 chunk_size;

    /* LOB chunk size, length, and data are read from cache. No round-trip. */

    OCILobGetChunkSize (svchp, errhp, lob_locator, &chunk_size);

    OCILobGetLength2(svchp, errhp, lob_locator, &lob_len );

    OCILobRead2(svchp, errhp, lob_locator, NULL, &char_amtp, ...);
    ...

Note that the prefetch size is in number of bytes for `BLOB`s and `BFILE`s and in number of characters for `CLOB`s.

Example 9-4 shows a code fragment illustrating these steps.

Prefetch cache allocation: The prefetch cache buffer for a descriptor is allocated while fetching a LOB locator. The allocated buffer size is determined by the `OCI_ATTR_LOBPREFETCH_SIZE` attribute for the define handle; the default value of this attribute is indicated by the `OCI_ATTR_DEFAULT_LOBPREFETCH_SIZE` attribute value of the session handle. If the cache buffer is already allocated, then it is resized if required.

For the following two LOB APIs, if the source locator has cached data, then the destination locator cache is allocated or resized and cached data is copied from source to destination.

- [OCILobAssign()](lob-functions.md)

- [OCILobLocatorAssign()](lob-functions.md)

Once allocated, the cache buffer memory for a descriptor is released when the descriptor itself is freed.

Prefetch cache invalidation: The cache for a descriptor gets invalidated when LOB data is updated using the locator. Meaning the cache is no longer used for reading data and the next [OCILobRead2()](lob-functions.md) call on the locator makes a round-trip.

The following LOB APIs invalidate the prefetch cache for the descriptor used:

- [OCILobErase()](deprecated-oci-functions.md) (deprecated)

- [OCILobErase2()](lob-functions.md)

- [OCILobTrim()](deprecated-oci-functions.md) (deprecated)

- [OCILobTrim2()](lob-functions.md)

- [OCILobWrite()](deprecated-oci-functions.md) (deprecated)

- [OCILobWrite2()](lob-functions.md)

- [OCILobWriteAppend()](deprecated-oci-functions.md) (deprecated)

- [OCILobWriteAppend2()](lob-functions.md)

- [OCILobArrayWrite()](lob-functions.md)

The following LOB APIs invalidate the cache for the destination LOB locator:

- [OCILobAppend()](lob-functions.md)

- [OCILobCopy()](deprecated-oci-functions.md) (deprecated)

- [OCILobCopy2()](lob-functions.md)

- [OCILobLoadFromFile()](deprecated-oci-functions.md) (deprecated)

- [OCILobLoadFromFile2()](lob-functions.md)

Performance Tuning: The prefetch buffer size must be decided upon based on average LOB size and client-side memory. If a large amount of data is prefetched, you must ensure the memory availability. Performance gain may not be significant for prefetching large LOBs, because the cost of fetching data is much higher compared to the cost of a round-trip to the server.

You must have a fair idea of the LOB data size to be able to make best use of this LOB prefetch feature. Because the parameters are part of application design, the application must be rebuilt if any parameter value must be modified.

Upgrading: LOB prefetching cannot be used against a pre-11.1 release server or in a pre-11.1 client against an 11.1 or later server. When you use a pre-11.1 server with an 11.1 or later client, [OCIAttrSet()](handle-and-descriptor-functions.md) returns an error or an error-with-information saying that "server does not support this functionality."

**See Also:**

- [OCI_ATTR_DEFAULT_LOBPREFETCH_SIZE](handle-and-descriptor-attributes.md)

- [OCI_ATTR_LOBPREFETCH_LENGTH](handle-and-descriptor-attributes.md)

- [OCI_ATTR_LOBPREFETCH_SIZE](handle-and-descriptor-attributes.md)

### 9.10 Options of SecureFiles LOBs

For SecureFiles (LOBs with the `STORE AS SECUREFILE` option, which were introduced in Oracle Database 11g Release 1) you can specify the SQL parameter `DEDUPLICATE` in `CREATE` `TABLE` and `ALTER` `TABLE` statements.

**Note:**

The deprecated algorithms for `DBMS_CRYPTO` and native network encryption include MD4, MD5, DES, 3DES, and RC4-related algorithms as well as 3DES for Transparent Data Encryption (TDE). Removing older, less secure cryptography algorithms prevents accidental use of these algorithms. To meet your security requirements, Oracle recommends that you use more modern cryptography algorithms, such as the Advanced Encryption Standard (AES).

As a consequence of this deprecation, Oracle recommends that you review your network encryption configuration to see if you have specified use of any of the deprecated algorithms. If any are found, then switch to using a more modern cipher, such as AES. Also, if you are currently using 3DES encryption for your TDE deployment, then you should plan to migrate to a more modern algorithm such as AES. For more information, refer to Oracle Database Security Guide

This parameter value enables you to specify that LOB data that is identical in two or more rows in a LOB column shares the same data blocks, thus saving disk space. `KEEP_DUPLICATES` turns off this capability. The following options are also used with `SECUREFILE`:

The parameter `COMPRESS` turns on LOB compression. `NOCOMPRESS` turns LOB compression off.

The parameter `ENCRYPT` turns on LOB encryption and optionally selects an encryption algorithm. `NOENCRYPT` turns off LOB encryption. Each LOB column can have its own encryption specification, independent of the encryption of other LOB or non-LOB columns. Valid algorithms are `3DES168`, `AES128`, `AES192`, and `AES256`.

The paradigm used before release 11.1 is the default. This default LOBs paradigm is also now explicitly set by the option `STORE AS BASICFILE`.

The following OCI functions are used with the `SECUREFILE` features:

- `OCILobGetOptions()`

- `OCILobSetOptions()`

- `OCILobGetContentType()`

- `OCILobSetContentType()`

**See Also:**

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/using-oracle-LOBs-storage.md) for complete details of relevant SQL functions and cross-references to PL/SQL packages and information about migrating to SecureFiles

- [OCILobGetOptions()](lob-functions.md)

- [OCILobSetOptions()](lob-functions.md)

- [OCILobGetContentType()](lob-functions.md)

- [OCILobSetContentType()](lob-functions.md)
