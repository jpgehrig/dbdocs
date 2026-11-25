The `Clob` class defines the common properties of objects of type `CLOB`. A `Clob` is a large character object stored as a column value in a row of a database table. A `Clob` object contains a logical pointer to a `CLOB`, not the `CLOB` itself.

Methods of the `Clob` class enable you to perform specific tasks related to `Clob` objects, including methods for getting the length of a SQL `CLOB`, for materializing a `CLOB` on the client, and for extracting a part of the `CLOB`.

The only methods valid on a `NULL` `CLOB` object are [setName()](bfile-class.md), isNull(), and [operator=()](bfile-class.md).

Methods in the `ResultSet` and `Statement` classes, such as `getClob()` and `setClob()`, enable you to access an SQL `CLOB` value.

An uninitialized `CLOB` object can be initialized by:

- The [setEmpty()](blob-class.md) method. The `CLOB` can then be modified by inserting this `CLOB` into the table and retrieving it using `SELECT...FOR UPDATE`. The [write()](blob-class.md) method modifies the `CLOB`; however, the modified data is flushed to the table only when the transaction is committed. Note that an `insert` is not required.

- Assigning an initialized `Clob` object to it.

**See Also:**

- In-depth discussion of `LOB`s in the introductory chapter of [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md),

Table 13-10 Summary of Clob Methods

| Method                | Summary                                                                                                                               |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| Clob()                | `Clob` class constructor.                                                                                                             |
| append()              | Appends a `Clob` at the end of the current `Clob`.                                                                                    |
| close()               | Closes a previously opened `Clob`.                                                                                                    |
| closeStream()         | Closes the `Stream` object obtained from the current `Clob`.                                                                          |
| copy()                | Copies all or a portion of a `Clob` or `BFILE` into the current `Clob`.                                                               |
| getCharSetForm()      | Returns the character set form of the `Clob`.                                                                                         |
| getCharSetId()        | Returns the character set ID of the `Clob`.                                                                                           |
| getCharSetIdUString() | Retrieves the characterset name associated with the `Clob`; `UString` version.                                                        |
| getChunkSize()        | Returns the smallest data size to perform efficient writes to the `CLOB`.                                                             |
| getContentType()      | Returns the content type of the `Clob`.                                                                                               |
| getOptions()          | Returns the `CLOB`'s `LobOptionValue` for a specified `LobOptionTyp`e.                                                                |
| getStream()           | Returns data from the `CLOB` as a `Stream` object.                                                                                    |
| isInitialized()       | Tests whether the `Clob` object is initialized.                                                                                       |
| isNull()              | Tests whether the `Clob` object is atomically `NULL`.                                                                                 |
| isOpen()              | Tests whether the `Clob` is open.                                                                                                     |
| length()              | Returns the number of characters in the current `CLOB`.                                                                               |
| open()                | Opens the `CLOB` with read or read/write access.                                                                                      |
| operator=()           | Assigns a `CLOB` locator to the current `Clob` object.                                                                                |
| operator==()          | Tests whether two `Clob` objects are equal.                                                                                           |
| operator!=()          | Tests whether two `Clob` objects are not equal.                                                                                       |
| read()                | Reads a portion of the `CLOB` into a buffer.                                                                                          |
| setCharSetId()        | Sets the character set ID associated with the `Clob`.                                                                                 |
| setCharSetIdUString() | Sets the character set ID associated with the `Clob`; used when the environment character set is UTF16.                               |
| setCharSetForm()      | Sets the character set form associated with the `Clob`.                                                                               |
| setContentType()      | Sets the content type of the `Clob`.                                                                                                  |
| setEmpty()            | Sets the `Clob` object to empty.                                                                                                      |
| setNull()             | Sets the `Clob` object to atomically `NULL`.                                                                                          |
| setOptions()          | Specifies a `LobOptionValue` for a particular `LobOptionType`. Enables advanced compression, encryption and deduplication of `CLOB`s. |
| trim()                | Truncates the `Clob` to a specified length.                                                                                           |
| write()               | Writes a buffer into an unopened `CLOB`.                                                                                              |
| writeChunk()          | Writes a buffer into an open `CLOB`.                                                                                                  |

### 13.9.1 Clob()

`Clob` class constructor.

| Syntax                                          | Description                             |
|:------------------------------------------------|:----------------------------------------|
| `Clob();`                                       | Creates a `NULL` `Clob` object.         |
| `Clob(`<br>`   const Connection *connectionp);` | Creates an uninitialized `Clob` object. |
| `Clob(`<br>`   const Clob *srcClob);`           | Creates a copy of a `Clob` object.      |

| Parameter     | Description              |
|:--------------|:-------------------------|
| `connectionp` | Connection pointer       |
| `srcClob`     | The source `Clob` object |

### 13.9.2 append()

Appends a `CLOB` to the end of the current `CLOB`.

#### Syntax

    void append(
       const Clob &srcClob);

| Parameter | Description                                      |
|:----------|:-------------------------------------------------|
| `srcClob` | The `CLOB` to be appended to the current `CLOB`. |

### 13.9.3 close()

Closes a `CLOB`.

#### Syntax

    void close();

### 13.9.4 closeStream()

Closes the `Stream` object obtained from the `CLOB`.

#### Syntax

    void closeStream(
       Stream *stream);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `stream`  | The Stream object to be closed. |

### 13.9.5 copy()

Copies a part or all of a `BFILE` or `CLOB` into the current `CLOB`.

OCCI does not perform any characterset conversions when loading data from a `Bfile` into a `Clob`; therefore, ensure that the contents of the `Bfile` are character data in the server's `Clob` storage characterset.

| Syntax                                                                                                                                              | Description                                                                                                                                                                                                                                                                                                                                                           |
|:----------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `void copy(`<br>`   const Bfile &srcBfile,`<br>`   unsigned int numBytes,`<br>`   unsigned int dstOffset = 1,`<br>`   unsigned int srcOffset = 1);` | Copies a `BFILE` into the current `CLOB`.                                                                                                                                                                                                                                                                                                                             |
| `void copy(`<br>`   const Clob &srcClob,`<br>`   unsigned int numBytes,`<br>`   unsigned int dstOffset = 1,`<br>`   unsigned int srcOffset = 1);`   | Copies a `CLOB` into the current `CLOB`.<br>If the destination `CLOB` has deduplication enabled, and the source and destination `CLOB`s are in the same column, the new `CLOB` is created as copy-on-write. All other settings are inherited from the source `CLOB`. If the destination `CLOB` has deduplication disabled, it is a completely new copy of the `CLOB`. |

| Parameter   | Description                                                                                                                                                                                                                                                  |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `srcBfile`  | The `BFILE` from which the data is to be copied.                                                                                                                                                                                                             |
| `srcClob`   | The `CLOB` from which the data is to be copied.                                                                                                                                                                                                              |
| `numBytes`  | The number of bytes to be copied from the source `BFILE`` or ``CLOB``. `Valid values are numbers greater than 0.                                                                                                                                             |
| `dstOffset` | The starting position at which data is to be is at 0.<br>The starting position at which to begin writing data into the current `CLOB` Valid values are numbers greater than or equal to 1 written in the destination buffer; the position of the first byte. |
| `srcOffset` | The starting position at which to begin reading data from the source `BFILE` or `CLOB`. Valid values are numbers greater than or equal to 1.                                                                                                                 |

### 13.9.6 getCharSetForm()

Returns the character set form of the `CLOB`.

#### Syntax

    CharSetForm getCharSetForm() const;

### 13.9.7 getCharSetId()

Returns the character set ID of the `CLOB`, in string form.

#### Syntax

    string getCharSetId() const;

### 13.9.8 getCharSetIdUString()

Retrieves the characterset name associated with the `Clob`; `UString` version.

#### Syntax

    UString getCharSetIdUString() const;

### 13.9.9 getChunkSize()

Returns the smallest data size to perform efficient writes to the `CLOB`.

#### Syntax

    unsigned int getChunkSize() const;

### 13.9.10 getContentType()

Returns the content type of the `Clob`. If a content type has not been assigned, returns a `NULL` string.

#### Syntax

    string getContentType();

### 13.9.11 getOptions()

Returns the `CLOB`'s `LobOptionValue` for a specified `LobOptionType`.

Throws an exception if attempting to retrieve a value for an option that is not configured on the database column or partition that stores the `CLOB`.

#### Syntax

    LobOptionValue getOptions(
       LobOptionType optType);

| Parameter | Description                                                                                                                                                                                            |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `optType` | The `LobOptionType` setting requested. These may be combined using bitwise `or` (`|`) to avoid server round trips. See [Table 7-1](programming-with-lobs.md) and [Table 7-2](programming-with-lobs.md) |

### 13.9.12 getStream()

Returns a `Stream` object from the `CLOB`. If a stream is open, it is disallowed to open another stream on `CLOB` object, so the user must always close the stream before performing any `Clob` object operations. The client's character set id and form is used by default, unless they are explicitly set through setCharSetId() and [setEmpty()](blob-class.md) calls.

#### Syntax

    Stream* getStream(
       unsigned int offset = 1,
       unsigned int amount = 0);

| Parameter | Description                                                                                                                                                                                                    |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `offset`  | The starting position at which to begin reading data from the `CLOB`. If `offset` is not specified, the data is written from the beginning of the `CLOB`. Valid values are numbers greater than or equal to 1. |
| `amount`  | The total number of consecutive characters to be read. If `amount` is 0, the data is read from the` offset` value until the end of the `CLOB`.                                                                 |

### 13.9.13 isInitialized()

Tests whether the `Clob object` is initialized. If the `Clob` object is initialized, `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isInitialized() const;

### 13.9.14 isNull()

Tests whether the `Clob` object is atomically `NULL`. If the `Clob` object is atomically `NULL`, `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.9.15 isOpen()

Tests whether the `CLOB` is open. If the `CLOB` is open, `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isOpen() const;

### 13.9.16 length()

Returns the number of characters in the `CLOB`.

#### Syntax

    unsigned int length() const;

### 13.9.17 open()

Opens the `CLOB` in `read/write` or read-only mode.

#### Syntax

    void open(
       LObOpenMode mode = OCCI_LOB_READWRITE);

| Parameter | Description                                                                                                      |
|:----------|:-----------------------------------------------------------------------------------------------------------------|
| `mode`    | `The mode the ``CLOB`` is to be opened in. Valid values are:`<br>• `OCCI_LOB_READWRITE`<br>• `OCCI_LOB_READONLY` |

### 13.9.18 operator=()

Assigns a `CLOB` to the current `CLOB`. The source `CLOB` gets copied to the destination `CLOB` only when the destination `CLOB` gets stored in the table.

#### Syntax

    Clob& operator=(
       const Clob &srcClob);

| Parameter | Description                                    |
|:----------|:-----------------------------------------------|
| `srcClob` | The `Clob` from which the data must be copied. |

### 13.9.19 operator==()

Compares two `Clob` objects for equality. Two `Clob` objects are equal if they both refer to the same `CLOB`. Two `NULL` `Clob` objects are not considered equal. If the `Blob` objects are equal, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator==(
       const Clob &srcClob) const;

| Parameter | Description                                                      |
|:----------|:-----------------------------------------------------------------|
| `srcClob` | The `Clob` object to be compared with the current `Clob` object. |

### 13.9.20 operator!=()

Compares two `Clob objects` for inequality. Two `Clob` objects are equal if they both refer to the same `CLOB`. Two `NULL` `Clob` objects are not considered equal. If the `Clob` objects are not equal, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator!=(
       const Clob &srcClob) const;

| Parameter | Description                                                      |
|:----------|:-----------------------------------------------------------------|
| `srcClob` | The `Clob` object to be compared with the current `Clob` object. |

### 13.9.21 read()

Reads a part or all of the `CLOB` into a buffer.

Returns the actual number of characters read for fixed-width charactersets, such as UTF16, or the number of bytes read for multibyte charactersets, including UTF8.

The client's character set id and form is used by default, unless they are explicitly set through setCharSetId(), setCharSetIdUString() and setCharSetForm() calls.

Note that for the second version of the method, the return value represents either the number of characters read for fixed-width charactersets (UTF16), or the number of bytes read for multibyte charactersets (including UTF8).

| Syntax                                                                                                                                             | Description                                                                                                                                                      |
|:---------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `unsigned int read(`<br>`   unsigned int amt,`<br>`   unsigned char *buffer,`<br>`   unsigned int bufsize,`<br>`   unsigned int offset=1) const;`  | Reads a part or all of the `CLOB` into a buffer.                                                                                                                 |
| `unsigned int read(`<br>`   unsigned int amt,`<br>`   unsigned utext *buffer,`<br>`   unsigned int bufsize,`<br>`   unsigned int offset=1) const;` | Reads a part or all of the `CLOB` into a buffer; globalization enabled. Should be called after setting character set to OCCIUTF16 using `setCharSetId()` method. |

| Parameter  | Description                                                                                                                                                                                                    |
|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `amt`      | The number of bytes to be read. from the `CLOB`.                                                                                                                                                               |
| `buffer`   | The buffer that the `CLOB `data is to be read into.                                                                                                                                                            |
| `buffsize` | The size of the buffer. Valid values are numbers greater than or equal to `amt`.                                                                                                                               |
| `offset`   | The starting position at which to begin reading data from the `CLOB`. If `offset` is not specified, the data is written from the beginning of the `CLOB`. Valid values are numbers greater than or equal to 1. |

### 13.9.22 setCharSetId()

Sets the Character set Id associated with `Clob`. The characterset id set is used for read/write and getStream() operations. If no value is set explicitly, the default client's character set id is used. List of character sets supported is given in Globalization Support Guide Appendix A.

#### Syntax

    void setCharSetId(
       const string &charset);

| Parameter | Description                                                                       |
|:----------|:----------------------------------------------------------------------------------|
| `charset` | Oracle supported characterset name, such as `E8DEC`, `ZHT16BIG5`, or `OCCIUTF16`. |

### 13.9.23 setCharSetIdUString()

Sets the characterset id associated with `Clob`; used when the environment's characterset is `UTF16`. The `charset` id set is used for read, write and getStream() operations.

#### Syntax

    void setCharSetIdUSString(
       const string &charset);

| Parameter | Description                                                                                                          |
|:----------|:---------------------------------------------------------------------------------------------------------------------|
| `charset` | Oracle supported characterset name, such as `WE8DEC`, `ZHT16BIG5`, or` OCCIUTF16` in `UString` (UTF16 characterset). |

### 13.9.24 setCharSetForm()

Sets the character set form associated with the `CLOB`. The charset form set is used for read, write and getStream() operations. If no value is set explicitly, by default, `OCCI_SQLCS_IMPLICIT` is used.

#### Syntax

    void setCharSetForm(
       CharSetForm csfrm );

| Parameter | Description                  |
|:----------|:-----------------------------|
| `csfrm`   | The charset form for `Clob`. |

### 13.9.25 setContentType()

Sets the content type of the `Clob`. If the `Clob` is not a SecureFile, throws an exception.

#### Syntax

    void setContentType(
       const string contenttype);

| Parameter     | Description                                                     |
|:--------------|:----------------------------------------------------------------|
| `contenttype` | The content type of the `Clob`; an ASCII Mime compliant string. |

### 13.9.26 setEmpty()

Sets the `Clob` object to empty.

| Syntax                                                   | Description                                                                                     |
|:---------------------------------------------------------|:------------------------------------------------------------------------------------------------|
| `void setEmpty();`                                       | Sets the `Clob` object to empty.                                                                |
| `void setEmpty(`<br>`   const Connection* connectionp);` | Sets the `Clob` object to empty and initializes the connection pointer to the passed parameter. |

| Parameter     | Description                                       |
|:--------------|:--------------------------------------------------|
| `connectionp` | The new connection pointer for the `Clob` object. |

### 13.9.27 setNull()

Sets the `Clob` object to atomically `NULL`.

#### Syntax

    void setNull();

### 13.9.28 setOptions()

Specifies a `LobOptionValue` for a particular `LobOptionType`. Enables advanced compression, encryption and deduplication of CLOBs. See [Table 7-1](programming-with-lobs.md) and [Table 7-2](programming-with-lobs.md).

Throws an exception if attempting to set or un-set an option that is not configured on the database column or partition that stores the `CLOB`.

Throws an exception if attempting to turn off encryption in an encrypted `CLOB` column.

#### Syntax

    void setOptions(
       LobOptionType optType,
       LobOptionValue optValue);

| Parameter  | Description                                                                                                              |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------|
| `optType`  | The `LobOptionType` setting being specified. These may be combined using bitwise `or` (`|`) to avoid server round trips. |
| `optValue` | The `LobOptionValue` setting for the `LobOptionType` specified by the `optType` parameter                                |

### 13.9.29 trim()

Truncates the `CLOB`` to the new length specified.`

#### Syntax

    void trim(
       unsigned int newlen);

| Parameter | Description                                                                                                    |
|:----------|:---------------------------------------------------------------------------------------------------------------|
| `newlen`  | The new length of the `CLOB`. Valid values are numbers less than or equal to the current length of the `CLOB`. |

### 13.9.30 write()

Writes data from a buffer into a `CLOB`.

This method implicitly opens the `CLOB`, copies the buffer into the `CLOB`, and implicitly closes the `CLOB`. If the `CLOB` is open, use writeChunk() instead. The actual number of characters written is returned. The client's character set id and form is used by default, unless they are explicitly set through setCharSetId() and setCharSetForm() calls.

| Syntax                                                                                                                                       | Description                                                                                                                                                         |
|:---------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `unsigned int write(`<br>`   unsigned int amt,`<br>`   unsigned char *buffer,`<br>`   unsigned int bufsize,`<br>`   unsigned int offset=1);` | Writes data from a buffer into a `CLOB`.                                                                                                                            |
| `unsigned int write(`<br>`   unsigned int amt,`<br>`   utext *buffer,`<br>`   unsigned int bufsize,`<br>`   unsigned int offset=1);`         | Writes data from a UTF16 buffer into a `CLOB`; globalization enabled. Should be called after setting character set to OCCIUTF16 using setCharSetIdUString() method. |

| Parameter  | Description                                                                                                                                                                                                    |
|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `amt`      | The amount parameter represents:<br>• number of characters written for fixed-width charactersets (UTF16)<br>• number of bytes written for multibyte charactersets (including UTF8)                             |
| `buffer`   | The buffer containing the data to be written to the `CLOB`.                                                                                                                                                    |
| `buffsize` | The size of the buffer containing the data to be written to the `CLOB``. `Valid values are numbers greater than or equal to `amt`.                                                                             |
| `offset`   | The starting position at which to begin writing data into the `CLOB`. If `offset` is not specified, the data is written from the beginning of the `CLOB`. Valid values are numbers greater than or equal to 1. |

### 13.9.31 writeChunk()

Writes data from a buffer into a previously opened `CLOB`. Returns the actual number of characters. The client's character set id and form is used by default, unless they are explicitly set through setCharSetId() and setCharSetForm() calls.

| Syntax                                                                                                                                            | Description                                                                                                                                                          |
|:--------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `unsigned int writeChunk(`<br>`   unsigned int amt,`<br>`   unsigned char *buffer,`<br>`   unsigned int bufsize,`<br>`   unsigned int offset=1);` | Writes data from a buffer into a previously opened `CLOB`.                                                                                                           |
| `unsigned int writeChunk(`<br>`   unsigned int amt,`<br>`   utext *buffer,`<br>`   unsigned int bufsize,`<br>`   unsigned int offset=1);`         | Writes data from a UTF16 buffer into a `CLOB`; globalization enabled. Should be called after setting characterset to `OCCIUTF16` using setCharSetIdUString() method. |

| Parameter  | Description                                                                                                                                                                                                    |
|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `amt`      | The amount parameter represents either a number of characters written for fixed-width charactersets (UTF16) or a number of bytes written for multibyte charactersets (including UTF8)                          |
| `buffer`   | The buffer containing the data to be written to the `CLOB`.                                                                                                                                                    |
| `buffsize` | The size of the buffer containing the data to be written to the `CLOB``. `Valid values are numbers greater than or equal to `amt`.                                                                             |
| `offset`   | The starting position at which to begin writing data into the `CLOB`. If `offset` is not specified, the data is written from the beginning of the `CLOB`. Valid values are numbers greater than or equal to 1. |
