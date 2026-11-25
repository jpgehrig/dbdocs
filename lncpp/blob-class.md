The `Blob` class defines the common properties of objects of type `BLOB`. A `BLOB` is a large binary object stored as a column value in a row of a database table. A `Blob` object contains a logical pointer to a `BLOB`, not the `BLOB` itself.

Methods of the `Blob` class enable you to perform specific tasks related to `Blob` objects.

Methods of the `ResultSet` and `Statement` classes, such as `getBlob()` and `setBlob()`, enable you to access an SQL `BLOB` value.

The only methods valid on a `NULL` `Blob` object are [setName()](bfile-class.md), [isNull()](bfile-class.md), and [operator=()](bfile-class.md).

An uninitialized `Blob` object can be initialized by:

- The setEmpty() method. The `BLOB` can then be modified by inserting this `BLOB` into the table and then retrieving it using `SELECT...FOR UPDATE`. The write() method modifies the `BLOB`; however, the modified data is flushed to the table only when the transaction is committed. Note that an update is not required.

- Assigning an initialized `Blob` object to it.

**See Also:**

- In-depth discussion of LOBs in [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md)

Table 13-8 Summary of Blob Methods

| Method           | Summary                                                                                                                               |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| Blob()           | `Blob` class constructor.                                                                                                             |
| append()         | Appends a specified `BLOB` to the end of the current `BLOB`.                                                                          |
| close()          | Closes a previously opened `BLOB`.                                                                                                    |
| closeStream()    | Closes the `Stream` object obtained from the `BLOB`.                                                                                  |
| copy()           | Copies a specified portion of a `BFILE` or `BLOB` into the current `BLOB`.                                                            |
| getChunkSize()   | Returns the smallest data size to perform efficient writes to the `BLOB`.                                                             |
| getContentType() | Returns the content type of the `Blob`.                                                                                               |
| getOptions()     | Returns the `BLOB`'s `LobOptionValue` for a specified `LobOptionType`.                                                                |
| getStream()      | Returns data from the `BLOB` as a `Stream` object.                                                                                    |
| isInitialized()  | Tests whether the `Blob` object is initialized                                                                                        |
| isNull()         | Tests whether the `Blob` object is atomically `NULL`.                                                                                 |
| isOpen()         | Tests whether the `BLOB` is open.                                                                                                     |
| length()         | Returns the number of bytes in the `BLOB`.                                                                                            |
| open()           | Opens the `BLOB`` with read or `read/write access.                                                                                    |
| operator=()      | Assigns a `BLOB` locator to the `Blob` object.                                                                                        |
| operator==()     | Tests whether two `Blob` objects are equal.                                                                                           |
| operator!= ()    | Tests whether two `Blob` objects are not equal.                                                                                       |
| read()           | Reads a portion of the `BLOB` into a buffer.                                                                                          |
| setContentType() | Sets the content type of the `Blob`.                                                                                                  |
| setEmpty()       | Sets the `Blob` object to empty.                                                                                                      |
| setNull()        | Sets the `Blob` object to atomically `NULL`.                                                                                          |
| setOptions()     | Specifies a `LobOptionValue` for a particular `LobOptionType`. Enables advanced compression, encryption and deduplication of `BLOB`s. |
| trim()           | Truncates the `BLOB` to a specified length.                                                                                           |
| write()          | Writes a buffer into an unopened `BLOB`.                                                                                              |
| writeChunk()     | Writes a buffer into an open `BLOB`.                                                                                                  |

### 13.7.1 Blob()

`Blob` class constructor.

| Syntax                                          | Description                             |
|:------------------------------------------------|:----------------------------------------|
| `Blob();`                                       | Creates a `NULL` `Blob` object.         |
| `Blob(`<br>`   const Connection *connectionp);` | Creates an uninitialized `Blob `object. |
| `Blob(`<br>`   const Blob &srcBlob);`           | Creates a copy of a `Blob` object.      |

| Parameter     | Description               |
|:--------------|:--------------------------|
| `connectionp` | The connection pointer    |
| `srcBlob`     | The source `Blob` object. |

### 13.7.2 append()

Appends a `BLOB` to the end of the current `BLOB`.

#### Syntax

    void append(
       const Blob &srcBlob);

| Parameter | Description                                                    |
|:----------|:---------------------------------------------------------------|
| `srcBlob` | The `BLOB` object to be appended to the current `BLOB` object. |

### 13.7.3 close()

Closes a `BLOB`.

#### Syntax

    void close();

### 13.7.4 closeStream()

Closes the Stream object obtained from the `BLOB`.

#### Syntax

    void closeStream(
       Stream *stream);

| Parameter | Description                |
|:----------|:---------------------------|
| `stream`  | The `Stream` to be closed. |

### 13.7.5 copy()

Copies a part or all of a `BFILE` or `BLOB` into the current `BLOB`.

| Syntax                                                                                                                                              | Description                                                                                                                                                                                                                                                                                                                                                                     |
|:----------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `void copy(`<br>`   const Bfile &srcBfile,`<br>`   unsigned int numBytes,`<br>`   unsigned int dstOffset = 1,`<br>`   unsigned int srcOffset = 1);` | Copies a part of a `BFILE` into the current `BLOB`.                                                                                                                                                                                                                                                                                                                             |
| `void copy(`<br>`   const Blob &srcBlob,`<br>`   unsigned int numBytes,`<br>`   unsigned int dstOffset = 1,`<br>`   unsigned int srcOffset = 1);`   | Copies a part of a `BLOB` into the current `BLOB`.<br>If the destination `BLOB` has deduplication enabled, and the source and destination `BLOB`s are in the same column, the new `BLOB` is created as copy-on-write. All other settings are inherited from the source `BLOB`. If the destination `BLOB` has deduplication disabled, it is a completely new copy of the `BLOB`. |

| Parameter   | Description                                                                                                                                  |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| `srcBfile`  | The `BFILE` from which the data is to be copied.                                                                                             |
| `srcBlob`   | The `BLOB` from which the data is to be copied.                                                                                              |
| `numBytes`  | The number of bytes to be copied from the source `BFILE` or `BLOB`. Valid values are numbers greater than 0.                                 |
| `dstOffset` | The starting position at which to begin writing data into the current `BLOB`. Valid values are numbers greater than or equal to 1.           |
| `srcOffset` | The starting position at which to begin reading data from the source `BFILE` or `BLOB`. Valid values are numbers greater than or equal to 1. |

### 13.7.6 getChunkSize()

Returns the smallest data size to perform efficient writes to the `BLOB`.

#### Syntax

    unsigned int getChunkSize() const;

### 13.7.7 getContentType()

Returns the content type of the `Blob`. If a content type has not been assigned, returns a `NULL` string.

#### Syntax

    string getContentType();

### 13.7.8 getOptions()

Returns the `BLOB`'s `LobOptionValue` for a specified `LobOptionType`.

Throws an exception if attempting to retrieve a value for an option that is not configured on the database column or partition that stores the `BLOB`.

#### Syntax

    LobOptionValue getOptions(
       LobOptionType optType);

| Parameter | Description                                                                                                                                                                                            |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `optType` | The `LobOptionType` setting requested. These may be combined using bitwise `or` (`|`) to avoid server round trips. See [Table 7-1](programming-with-lobs.md) and [Table 7-2](programming-with-lobs.md) |

### 13.7.9 getStream()

Returns a `Stream` object from the `BLOB`. If a stream is open, it is disallowed to open another stream on `Blob object`, so the user must always close the stream before performing any `Blob` object operations.

#### Syntax

    Stream* getStream(
       unsigned int offset = 1,
       unsigned int amount = 0);

| Parameter | Description                                                                                                                                                                                                      |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `offset`  | The starting position at which to begin reading data from the `BLOB`. If `offset` is not specified, the data is written from the beginning of the `BLOB`. Valid values are numbers greater than or equal to `1`. |
| `amount`  | The total number of bytes to be read from the `BLOB`; if `amount` is `0`, the data is read in a streamed mode from input `offset` until the end of the `BLOB`.                                                   |

### 13.7.10 isInitialized()

Tests whether the `Blob` object is initialized. If the `Blob` object is initialized, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isInitialized() const;

### 13.7.11 isNull()

Tests whether the `Blob` object is atomically `NULL`. If the `Blob` object is atomically `NULL`, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.7.12 isOpen()

Tests whether the `BLOB` is open. If the `BLOB` is open, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isOpen() const;

### 13.7.13 length()

Returns the number of bytes in the `BLOB`.

#### Syntax

    unsigned int length() const;

### 13.7.14 open()

Opens the `BLOB` in read/write or read-only mode.

#### Syntax

    void open(
       LobOpenMode mode = OCCI_LOB_READWRITE);

| Parameter | Description                                                                                                  |
|:----------|:-------------------------------------------------------------------------------------------------------------|
| `mode`    | The mode the `BLOB` is to be opened in. Valid values are:<br>• `OCCI_LOB_READWRITE`<br>• `OCCI_LOB_READONLY` |

### 13.7.15 operator=()

Assigns a `BLOB` to the current `BLOB`. The source `BLOB` gets copied to the destination `BLOB` only when the destination `BLOB` gets stored in the table.

#### Syntax

    Blob& operator=(
       const Blob &srcBlob);

| Parameter | Description                                |
|:----------|:-------------------------------------------|
| `srcBlob` | The source `BLOB` from which to copy data. |

### 13.7.16 operator==()

Compares two `Blob objects` for equality. Two `Blob objects` are equal if they both refer to the same `BLOB`. Two `NULL` `Blob objects` are not considered equal. If the `Blob` objects are equal, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator==(
       const Blob &srcBlob) const;

| Parameter | Description                                               |
|:----------|:----------------------------------------------------------|
| `srcBlob` | The source `BLOB` to be compared with the current `BLOB`. |

### 13.7.17 operator!= ()

Compares two `Blob objects` for inequality. Two `Blob objects` are equal if they both refer to the same `BLOB`. Two `NULL` `Blob` objects are not considered equal. If the `Blob` objects are not equal, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator!=(
       const Blob &srcBlob) const;

| Parameter | Description                                               |
|:----------|:----------------------------------------------------------|
| `srcBlob` | The source `BLOB` to be compared with the current `BLOB`. |

### 13.7.18 read()

Reads a part or all of the `BLOB` into a buffer. The actual number of bytes read is returned.

#### Syntax

    unsigned int read(
       unsigned int amt,
       unsigned char *buffer,
       unsigned int bufsize,
       unsigned int offset = 1) const;

| Parameter  | Description                                                                                                                                               |
|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `amt`      | The number of bytes to be read. Valid values are numbers greater than or equal to `1`.                                                                    |
| `buffer`   | The buffer that the `BLOB `data is to be read into. Valid values are numbers greater than or equal to `amt`.                                              |
| `buffsize` | The size of the buffer that the `BLOB` data is to be read into. Valid values are numbers greater than or equal to `amt`.                                  |
| `offset`   | The starting position at which to begin reading data from the `BLOB`. If `offset` is not specified, the data is written from the beginning of the `BLOB`. |

### 13.7.19 setContentType()

Sets the content type of the `Blob`. If the `Blob` is not a SecureFile, throws an exception.

#### Syntax

    void setContentType(
       const string contenttype);

| Parameter     | Description                                                     |
|:--------------|:----------------------------------------------------------------|
| `contenttype` | The content type of the `Blob`; an ASCII Mime compliant string. |

### 13.7.20 setEmpty()

Sets the `Blob` object to empty.

| Syntax                                                   | Description                                                                                     |
|:---------------------------------------------------------|:------------------------------------------------------------------------------------------------|
| `void setEmpty();`                                       | Sets the `Blob` object to empty.                                                                |
| `void setEmpty(`<br>`   const Connection* connectionp);` | Sets the `Blob` object to empty and initializes the connection pointer to the passed parameter. |

| Parameter     | Description                                       |
|:--------------|:--------------------------------------------------|
| `connectionp` | The new connection pointer for the `BLOB` object. |

### 13.7.21 setNull()

Sets the `Blob` object to atomically `NULL`.

#### Syntax

    void setNull();

### 13.7.22 setOptions()

Specifies a `LobOptionValue` for a particular `LobOptionType`. Enables advanced compression, encryption and deduplication of `BLOB`s. See [Table 7-1](programming-with-lobs.md) and [Table 7-2](programming-with-lobs.md).

Throws an exception if attempting to set or un-set an option that is not configured on the database column or partition that stores the `BLOB`.

Throws an exception if attempting to turn off encryption in an encrypted `BLOB` column.

#### Syntax

    void setOptions(
       LobOptionType optType,
       LobOptionValue optValue);

| Parameter  | Description                                                                                                              |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------|
| `optType`  | The `LobOptionType` setting being specified. These may be combined using bitwise `or` (`|`) to avoid server round trips. |
| `optValue` | The `LobOptionValue` setting for the `LobOptionType` specified by the `optType` parameter                                |

### 13.7.23 trim()

Truncates the `BLOB` to the new length specified.

#### Syntax

    void trim(
       unsigned int newlen);

| Parameter | Description                                                                                                    |
|:----------|:---------------------------------------------------------------------------------------------------------------|
| `newlen`  | The new length of the `BLOB`. Valid values are numbers less than or equal to the current length of the `BLOB`. |

### 13.7.24 write()

Writes data from a buffer into a `BLOB`. This method implicitly opens the `BLOB`, copies the buffer into the `BLOB`, and implicitly closes the `BLOB`. If the `BLOB` is open, use writeChunk() instead. The actual number of bytes written is returned.

#### Syntax

    unsigned int write(
       unsigned int amt,
       unsigned char *buffer,
       unsigned int bufsize,
       unsigned int offset = 1);

| Parameter  | Description                                                                                                                                                                                                    |
|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `amt`      | The number of bytes to be written to the `BLOB`.                                                                                                                                                               |
| `buffer`   | The buffer containing the data to be written to the `BLOB`.                                                                                                                                                    |
| `buffsize` | The size of the `buffer containing the data to be written to the ``BLOB``. `Valid values are numbers greater than or equal to `amt`.                                                                           |
| `offset`   | The starting position at which to begin writing data into the `BLOB`. If `offset` is not specified, the data is written from the beginning of the `BLOB`. Valid values are numbers greater than or equal to 1. |

### 13.7.25 writeChunk()

Writes data from a buffer into a previously opened `BLOB`. The actual number of bytes written is returned.

#### Syntax

    unsigned int writeChunk(
       unsigned int amount,
       unsigned char *buffer,
       unsigned int bufsize,
       unsigned int offset = 1);

| Parameter  | Description                                                                                                                                                                                                      |
|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `amt`      | The number of bytes to be written to the `BLOB`.                                                                                                                                                                 |
| `buffer`   | The buffer containing the data to be written to the `BLOB`.                                                                                                                                                      |
| `buffsize` | The size of the buffer containing the data to be written to the `BLOB`. Valid values are numbers greater than or equal to `amt`.                                                                                 |
| `offset`   | The starting position at which to begin writing data into the `BLOB`. If `offset` is not specified, the data is written from the beginning of the `BLOB`. Valid values are numbers greater than or equal to `1`. |
