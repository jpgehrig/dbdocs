This chapter provides an overview of LOBs and their use in OCCI.

This chapter contains these topics:

- Overview of LOBs

- Creating LOBs in OCCI Applications

- Restricting the Opening and Closing of LOBs

- About Reading and Writing LOBs

- Using Objects with LOB Attributes

- About Using SecureFiles

**See also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md) for extensive information about LOBs

### 7.1 Overview of LOBs

Oracle C++ Call Interface includes classes and methods for performing operations on large objects, LOBs. LOBs are either internal or external depending on their location with respect to the database.

This section includes the following topics:

- Introducing Internal LOBs

- Introducing External LOBs

- About Storing LOBs

#### 7.1.1 Introducing Internal LOBs

Internal LOBs are stored inside database tablespaces in a way that optimizes space and enables efficient access. Internal LOBs use copy semantics and participate in the transactional model of the server. You can recover internal LOBs after transaction or media failure, and any changes to an internal LOB value can be committed or rolled back. There are three SQL data types for defining instances of internal LOBs:

- `BLOB`: A LOB whose value is composed of unstructured binary (raw) data

- `CLOB`: A LOB whose value is composed of character data that corresponds to the database character set defined for the Oracle database

- `NCLOB`: A LOB whose value is composed of character data that corresponds to the national character set defined for the Oracle database

The copy semantics for LOBs dictate that when you insert or update a LOB with a LOB from another row in the same table, both the LOB locator and the LOB value are copied. In other words, each row has a copy of the LOB value.

#### 7.1.2 Introducing External LOBs

`BFILE`s are large binary (raw) data objects data stored in operating system files outside database tablespaces; therefore, they are referred to as external LOBs. These files use reference semantics, where only the locator for the LOB is reproduced when inserting or updating in the same table. Apart from conventional secondary storage devices such as hard disks, `BFILE`s may also be located on tertiary block storage devices such as CD-ROMs, PhotoCDs and DVDs. The `BFILE` data type allows read-only byte stream access to large files on the file system of the database server. Oracle can access `BFILE`s if the underlying server operating system supports stream mode access to these files.

External LOBs do not participate in transactions. Any support for integrity and durability must be provided by the underlying file and operating systems. An external LOB must reside on a single device; it may not be striped across a disk array.

#### 7.1.3 About Storing LOBs

The size of the LOB value, among other things, dictates where it is stored. The LOB value is either stored inline with the row data or outside the row.

- Locator storage: a LOB locator, a pointer to the actual location of the LOB value, is stored inline with the row data and indicates where the LOB value is stored.

  For internal LOBs, the LOB column stores a locator to the LOB value stored in a database tablespace. Each internal LOB column and attribute for a particular row has its own unique LOB locator and a distinct copy of the LOB value stored in the database tablespace.

  For external LOBs, the LOB column stores a locator to the external operating system file that houses the `BFILE`. Each external LOB column and attribute for a given row has its own `BFILE` locator. However, two different rows can contain a `BFILE` locator that points to the same operating system file.

- Inline storage: Data stored in a LOB is termed the LOB value. The value of an internal LOB may or may not be stored inline with the other row data. If you do not set `DISABLE STORAGE IN ROW`, and if the internal LOB value is less than approximately `4,000` bytes, then the value is stored inline.Otherwise, it is stored outside the row.

  Since LOBs are intended to be large objects, inline storage is only relevant if your application mixes small and large LOBs.The LOB value is automatically moved out of the row once it extends beyond approximately `4,000` bytes.

### 7.2 Creating LOBs in OCCI Applications

Follow these steps to use LOBs in your application:

- Initialize a new LOB locator in the database.

- Assign a value to the LOB. In case of `BFILE`s, assign a reference to a valid external file.

- To access and manipulate LOBs, see the OCCI classes that implement the methods for using LOBs in an application. All are detailed in [OCCI Application Programming Interface](occi-application-programing-interface.md):

  - [Bfile Class](bfile-class.md) contains the APIs for `BFILE`s, as summarized in [Table 13-7](bfile-class.md).

  - [Blob Class](blob-class.md) contains the APIs for `BLOB`s, as summarized in [Table 13-8](blob-class.md).

  - [Clob Class](clob-class.md) contains the APIs for `CLOB`s and `NCLOB`s, as summarized in [Table 13-10](clob-class.md).

- Whenever you want to modify an internal LOB column or attribute using write, copy, trim, and similar operations, you must lock the row that contains the target LOB. Use a `SELECT...FOR UPDATE` statement to select the LOB locator.

- A transaction must be open before a LOB write command succeeds. Therefore, you must write the data before committing a transaction (since `COMMIT` closes the transaction). Otherwise, you must lock the row again by reissuing the `SELECT...FOR UPDATE` statement. Each of the LOB class implementations in OCCI have `open()` and `close()` methods. To check whether a LOB is open, call the `isOpen()` method of the class.

- The methods `open()`, `close()` and `isOpen()` should also be used to mark the beginning and end of a series of LOB operations. Whenever a LOB modification is made, it triggers updates on extensible indexes. If these modifications are made within `open()...close()` code blocks, the individual triggers are disabled until after the `close()` call, and then all are issued at the same time. This implementation enables the efficient processing of maintenance operations, such as updating indexes, when the LOBs are closed. However, this also means that extensive indexes are not valid during the execution of the `open()...close()` code block.

  Note that for internal LOBs, the concept of openness is associated with the LOB and not the LOB locator. The LOB locator does not store any information about whether the LOB to which it refers is open. It is possible for multiple LOB locators to point to the same open LOB. However, for external LOBs, openness is associated with a specific external LOB locator. Therefore, multiple `open()` calls can be made on the same `BFILE` using different external LOB locators.

### 7.3 Restricting the Opening and Closing of LOBs

The definition of a transaction within which an open LOB value must be closed is one of the following:

- Between `SET TRANSACTION` and `COMMIT`

- Between `DATA MODIFYING DML` and `COMMIT`

- Between `SELECT...FOR UPDATE` and `COMMIT`

- Within an autonomous transaction block

The LOB opening and closing mechanism has the following restrictions:

- An application must close all previously opened LOBs before committing a transaction. Failing to do so results in an error. If a transaction is rolled back, then all open LOBs are discarded along with the changes made, so associated triggers are not fired.

- While there is no limit to the number of open internal LOBs, there is a limit on the number of open files. Note that assigning an opened locator to another locator does not count as opening a new LOB.

- It is an error to open or close the same internal LOB twice within the same transaction, either with different locators or with the same locator.

- It is an error to close a LOB that has not been opened.

### 7.4 About Reading and Writing LOBs

There are two general methods for reading and writing LOBs: non-streamed, and streamed.

This section includes the following topics:

- Reading LOBs

- Writing LOBs

- About Enhancing the Performance of LOB Reads and Writes

- Updating LOBs

- About Reading and Writing Multiple LOBs

#### 7.4.1 Reading LOBs

Example 7-1 illustrates how to get data from a non-`NULL` internal LOB, using a non-streamed method. This method requires that you keep track of the read offset and the amount remaining to be read, and pass these values to the `read()` method.

Example 7-2 is similar as it demonstrates how to read data from a `BFILE`, where the `BFILE` locator is not `NULL`, by using a non-streamed read.

In contrast to Example 7-1 and Example 7-2, the streamed reading demonstrated in Example 7-3 on a non-`NULL` `BLOB` does not require keeping track of the offset.

Example 7-1 How to Read Non-Streamed BLOBs

    ResultSet *rset=stmt->executeQuery("SELECT ad_composite FROM print_media
                                        WHERE product_id=6666");
    while(rset->next())
    {
       Blob blob=rset->getBlob(1);
       if(blob.isNull())
         cerr <<"Null Blob"<<endl;
       else
       {
          blob.open(OCCI_LOB_READONLY);

          const unsigned int BUFSIZE=100;
          char buffer[BUFSIZE];
          unsigned int readAmt=BUFSIZE;
          unsigned int offset=1;

          //reading readAmt bytes from offset 1
          blob.read(readAmt,buffer,BUFSIZE,offset);

          //process information in buffer
          ...
          blob.close();
       }
    }
    stmt->closeResultSet(rset);

Example 7-2 How to Read Non-Streamed BFILESs

    ResultSet *rset=stmt->executeQuery("SELECT ad_graphic FROM print_media
                                        WHERE product_id=6666");
    while(rset->next())
    {
       Bfile file=rset->getBfile(1);
       if(bfile.isNull())
          cerr <<"Null Bfile"<<endl;
       else
       {
          //display the directory alias and the file name of the BFILE
          cout <<"File Name:"<<bfile.getFileName()<<endl;
          cout <<"Directory Alias:"<<bfile.getDirAlias()<<endl;

          if(bfile.fileExists())
          {
             unsigned int length=bfile.length();
             char *buffer=new char[length];
             bfile.read(length, buffer, length, 1);
             //read all the contents of the BFILE into buffer, then process
             ...
             delete[] buffer;
          }
          else
             cerr <<"File does not exist"<<endl;
       }
    }
    stmt->closeResultSet(rset);

Example 7-3 How to Read Streamed BLOBs

    ResultSet *rset=stmt->executeQuery("SELECT ad_composite FROM print_media
                                        WHERE product_id=6666");
    while(rset->next())
    {
       Blob blob=rset->getBlob(1);
       if(blob.isNull())
          cerr <<"Null Blob"<<endl;
       else
       {
          Stream *instream=blob.getStream(1,0);
          //reading from offset 1 to the end of the BLOB

          unsigned int size=blob.getChunkSize();
          char *buffer=new char[size];

          while((unsigned int length=instream->readBuffer(buffer,size))!=-1)
          {
             //process "length" bytes read into buffer
             ...
          }
          delete[] buffer;
          blob.closeStream(instream);
       }
    }
    stmt->closeResultSet(rset);

#### 7.4.2 Writing LOBs

Example 7-4 demonstrates how to write data to an internal non-`NULL` LOB by using a non-streamed write. The `writeChunk()` method is enclosed by the `open()` and `close()` methods; it operates on a LOB that is currently open and ensures that triggers do not fire for every chunk read. The `write()` method can be used for the `writeChunk()` method; however, the `write()` method implicitly opens and closes the LOB.

Example 7-5 demonstrates how to write data to an internal LOB that is populated by using a streamed write.

Example 7-4 How to Write Non-Streamed BLOBs

    ResultSet *rset=stmt->executeQuery("SELECT ad_composite FROM print_media
                                        WHERE product_id=6666 FOR UPDATE");
    while(rset->next())
    {
       Blob blob=rset->getBlob(1);
       if(blob.isNull())
          cerr <<"Null Blob"<<endl;
       else
       {
          blob.open(OCCI_LOB_READWRITE);

          const unsigned int BUFSIZE=100;
          char buffer[BUFSIZE];
          unsigned int writeAmt=BUFSIZE;
          unsigned int offset=1;

          //writing writeAmt bytes from offset 1
          //contents of buffer are replaced after each writeChunk(),
          //typically with an fread()
          while(<fread "BUFSIZE" bytes into buffer succeeds>)
          {
             blob.writeChunk(writeAmt, buffer, BUFSIZE, offset);
             offset += writeAmt;
          }
          blob.writeChunk(<remaining amt>, buffer, BUFSIZE, offset);

          blob.close();
       }
    }
    stmt->closeResultSet(rset);
    conn->commit();

Example 7-5 How to Write Streamed BLOBs

    ResultSet *rset=stmt->executeQuery("SELECT ad_composite FROM print_media
                                        WHERE product_id=6666 FOR UPDATE");
    while(rset->next())
    {
       Blob blob=rset->getBlob(1);
       if(blob.isNull())
          cerr <<"Null Blob"<<endl;
       else
       {
          char buffer[BUFSIZE];
          Stream *outstream=blob.getStream(1,0);

          //writing from buffer beginning at offset 1 until
          //a writeLastBuffer() method is issued.
          //contents of buffer are replaced after each writeBuffer(),
          //typically with an fread()
          while(<fread "BUFSIZE" bytes into buffer succeeds>)
             ostream->writeBuffer(buffer,BUFSIZE);
          ostream->writeLastBuffer(buffer,<remaining amt>);
          blob.closeStream(outstream);
       }
    }
    stmt->closeResultSet(rset);
    conn->commit();

#### 7.4.3 About Enhancing the Performance of LOB Reads and Writes

Reading and writing of internal LOBs can be improved by using either `getChunkSize()` method.

This section includes the following topic: About Using the getChunkSize() Method.

##### 7.4.3.1 About Using the getChunkSize() Method

The `getChunkSize()` method returns the usable chunk size in bytes for `BLOB`s, and in characters for `CLOB`s and `NCLOB`s. Performance improves when a read or a write begins on a multiple of the usable chunk size, and the request size is also a multiple of the usable chunk size. You can specify the chunk size for a LOB column when you create a table that contains the LOB.

Calling the `getChunkSize()` method returns the usable chunk size of the LOB. An application can batch a series of write operations until an entire chunk can be written, rather than issuing multiple LOB write calls that operate on the same chunk

To read through the end of a LOB, use the `read()` method with an amount of 4 GB. This avoids the round-trip involved with first calling the `getLength()` method because the `read()` method with an amount of 4 GB reads until the end of the LOB is reached.

For LOBs that store variable width characters, the `GetChunkSize()` method returns the number of Unicode characters that fit in a LOB chunk.

#### 7.4.4 Updating LOBs

To update a value of a LOB in the database, you must assign the new value to the LOB, execute a SQL `UPDATE` command in the database, and then commit the transaction. Example 7-6 demonstrates how to update an existing `CLOB` (in this case, by setting it to empty), while Example 7-7 demonstrates how to update a `BFILE`.

Example 7-6 Updating a CLOB Value

    Clob clob(conn);
    clob.setEmpty();
    stmt->setSQL("UPDATE print_media SET ad_composite = :1
                  WHERE product_id=6666");
    stmt->setClob(1, clob);
    stmt->executeUpdate();
    conn->commit();

Example 7-7 Updating a BFILE Value

    Bfile bfile(conn);
    bfile.setName("MEDIA_DIR", "img1.jpg");
    stmt->setSQL("UPDATE print_media SET ad_graphic = :1
                  WHERE product_id=6666");
    stmt->setBfile(1, bfile);
    stmt->executeUpdate();
    conn->commit();

#### 7.4.5 About Reading and Writing Multiple LOBs

As of Oracle Database 10g Release 2, OCCI has new interfaces that enhance application performance while reading and writing multiple `LOB`s, such as `Bfile`s, `Blob`s, `Clob`s and `NClob`s.

These interfaces have several advantages over the standard methods for reading and writing a single LOB at a time:

- Reading and writing multiple `LOB`s through OCCI in a single server round-trip improves performance by decreasing I/O time between the application and the back end.

- The new APIs provide support for LOBs that are larger than the previous limit of 4 GB. The new interfaces accept the `oraub8` data type for amount, offsets, buffer and length parameters. These parameters are mapped to the appropriate 64-bit native data type, which is determined by the compiler and the operating system.

- For `Clob`-related methods, the user can specify the data amount read or written in terms of character counts or byte counts.

New APIs for this features are described in [OCCI Application Programming Interface](occi-application-programing-interface.md), section on [Connection Class](connection-class.md), and include [readVectorOfBfiles()](connection-class.md), [readVectorOfBlobs()](connection-class.md), [readVectorOfClobs()](connection-class.md) (overloaded to support general charactersets, and the `UTF16` characterset in particular), [writeVectorOfBlobs()](connection-class.md), and [writeVectorOfClobs()](connection-class.md) (overloaded to support general charactersets, and the `UTF16` characterset in particular).

This section includes the following topic: About Using the Interfaces for Reading and Writing Multiple LOBs.

##### 7.4.5.1 About Using the Interfaces for Reading and Writing Multiple LOBs

Each of the `readVectorOf``xxx``()` and `writeVectorOf``xxx``()` interface uses the following parameters:

- `conn`, a `Connection` class object

- `vec`, a vector of `LOB` objects: `Bfile`, `Blob`, `Clob`, or `NClob`

- `byteAmts`, array of amounts, in bytes, for reading or writing

- `charAmts`, array of amounts, in characters, for reading or writing (only applicable for `Clob`s and `NClob`s)

- `offsets`, array of offsets, in bytes for `Bfile`s and `Blob`s, and in characters for `Clob`s and `NClob`s

- `buffers`, array of buffer pointers

- `bufferLengths`, array of buffer lengths.

If there are errors in either reading or writing of one of the LOBs in the vector, the whole operation is cancelled. The `byteAmts` or `charAmts` parameters should be checked to determine the actual number of bytes or characters read or written.

### 7.5 Using Objects with LOB Attributes

An OCCI application can use the operator `new()` to create a persistent object with a LOB attribute. By default, all LOB attributes are constructed by using the default constructor, and are initialized to `NULL`.

Example 7-8 demonstrates how to create and use persistent objects with internal LOB attributes. Example 7-9 demonstrates how to create and use persistent objects with external LOB attributes.

Example 7-8 How to Use a Persistent Object with a BLOB Attribute

1.  Create a persistent object with a `BLOB` attribute:

        Person *p=new(conn,"PERSON_TAB")Person();
        p->imgBlob = Blob(conn);

2.  Either initialize the `Blob` object to empty:

        p->imgBlob.setEmpty();

    Or set it to some existing value

3.  Mark the `Blob` object as dirty:

        p->markModified();

4.  Flush the object:

        p->flush();

5.  Repin the object after obtaining a `REF` to it, thereby retrieving a refreshed version of the object from the database and acquiring an initialized LOB:

        Ref<Person> r = p->getRef();
        delete p;
        p = r.ptr();

6.  Write the data:

        p->imgBlob.write( ... );

Example 7-9 How to Use a Persistent Object with a BFILE Attribute

1.  Create a persistent object with a `BFILE` attribute:

        Person *p=new(conn,"PERSON_TAB")Person();
        p->imgBFile = BFile(conn);

2.  Initialize the `Bfile` object:

        p->setName(directory_alias, file_name);

3.  Mark the `Bfile` object as dirty:

        p->markModified();

4.  Flush the object:

        p->flush();

5.  Read the data:

        p->imgBfile.read( ... );

### 7.6 About Using SecureFiles

Introduced with Oracle Database 11g Release 1, SecureFiles LOBs add powerful new features for LOB compression, encryption, and deduplication.

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/using-oracle-LOBs-storage.md)

This section includes the following topics:

- About Using SecureFile Compression

- About Using SecureFiles Encryption

- About Using SecureFiles Deduplication

- About Combining SecureFiles Compression, Encryption, and Deduplication

- SecureFiles LOB Types and Constants

#### 7.6.1 About Using SecureFile Compression

SecureFiles compression enables server-side compression of LOB data, transparent to the application. Using SecureFiles compression saves storage space with minimal impact on reading and updating performance for SecureFiles LOB data.

#### 7.6.2 About Using SecureFiles Encryption

SecureFiles introduce a new encryption capability for LOB data and extend Transparent Data Encryption by enabling efficient random read and write access to encrypted SecureFiles LOBs.

#### 7.6.3 About Using SecureFiles Deduplication

SecureFiles deduplication allows the Oracle Database to automatically detect duplicate LOB data, and to conserve space by storing a single copy of the SecureFiles LOB.

#### 7.6.4 About Combining SecureFiles Compression, Encryption, and Deduplication

You can combine compression, encryption and deduplication in any combination. Oracle Database applies these features according to the following rules:

- Deduplicate detection, if enabled, is performed before compression and encryption. This prevents potentially unnecessary and expensive compression and encryption operations on duplicate SecureFiles LOBs.

- Compression is performed before encryption, to allow for the highest possible compression ratios.

#### 7.6.5 SecureFiles LOB Types and Constants

The following types for SecureFiles LOBs enable additional flexibility for compression, encryption, and deduplication. Table 7-1 lists options for the `LobOptionType`, while Table 7-2 lists options for the `LobOptionValue`.

Table 7-1 Values of Type LobOptionType

| Value                      | Description             |
|:---------------------------|:------------------------|
| `OCCI_LOB_OPT_COMPRESS`    | Compression option type |
| `OCCI_LOB_OPT_ENCRYPT`     | Encryption option type  |
| `OCCI_LOB_OPT_DEDUPLICATE` | Deduplicate option type |

Table 7-2 Values of Type LobOptionValue

| Value                      | Description                         |
|:---------------------------|:------------------------------------|
| `OCCI_LOB_COMPRESS_OFF`    | Turns off SecureFiles compression   |
| `OCCI_LOB_COMPRESS_ON`     | Turns on SecureFiles compression    |
| `OCCI_LOB_ENCRYPT_OFF`     | Turns off SecureFiles encryption    |
| `OCCI_LOB_ENCRYPT_ON`      | Turns on SecureFiles encryption     |
| `OCCI_LOB_DEDUPLICATE_OFF` | Turns off SecureFiles deduplication |
| `OCCI_LOB_DEDUPLICATE_ON`  | Turns off LOB deduplication         |
