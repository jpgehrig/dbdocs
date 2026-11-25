The `Bfile` class defines the common properties of objects of type `BFILE`. A `BFILE` is a large binary file stored in an operating system file outside of the Oracle database. A `Bfile` object contains a logical pointer to a `BFILE`, not the `BFILE` itself.

Methods of the `Bfile` class enable you to perform specific tasks related to `Bfile` objects.

Methods of the `ResultSet` and `Statement` classes, such as `getBfile()` and `setBfile()`, enable you to access an SQL `BFILE` value.

The only methods valid on a `NULL` `Bfile` object are setName(), isNull(), and operator=().

A `Bfile` object can be initialized by:

- The setName() method. The `BFILE` can then be modified by inserting this `BFILE` into the table and then retrieving it using `SELECT...FOR UPDATE`. The `write()` method modifies the `BFILE`; however, the modified data is flushed to the table only when the transaction is committed. Note that an `INSERT` operation is not required.

- Assigning an initialized `Bfile` object to it.

  **See Also:**

  In-depth discussion of LOBs in the introductory chapter of [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md),

Table 13-7 Summary of Bfile Methods

| Method               | Summary                                                                          |
|:---------------------|:---------------------------------------------------------------------------------|
| Bfile()              | `Bfile` class constructor.                                                       |
| close()              | Closes a previously opened `BFILE`.                                              |
| closeStream()        | Closes the stream obtained from the `BFILE`.                                     |
| fileExists()         | Tests whether the `BFILE `exists.                                                |
| getDirAlias()        | Returns the directory object of the `BFILE`.                                     |
| getFileName()        | Returns the name of the `BFILE`.                                                 |
| getStream()          | Returns data from the `BFILE` as a `Stream` object.                              |
| getUStringDirAlias() | Returns a `UString` containing the directory object associated with the `BFILE`. |
| getUStringFileName() | Returns a `UString` containing the file name associated with the `BFILE`.        |
| isInitialized()      | Tests whether the `Bfile` object is initialized.                                 |
| isNull()             | Tests whether the `Bfile` object is atomically `NULL`.                           |
| isOpen()             | Tests whether the `BFILE `is open.                                               |
| length()             | Returns the number of bytes in the `BFILE`.                                      |
| open()               | Opens the `BFILE` with read-only access.                                         |
| operator=()          | Assigns a `BFILE` locator to the `Bfile` object.                                 |
| operator==()         | Tests whether two `Bfile` objects are equal.                                     |
| operator!=()         | Tests whether two `Bfile` objects are not equal.                                 |
| operator==()         | Reads a specified portion of the `BFILE` into a buffer.                          |
| setName()            | Sets the directory object and file name of the `BFILE`.                          |
| setNull()            | Sets the `Bfile` object to atomically `NULL`.                                    |

### 13.6.1 Bfile()

`Bfile` class constructor.

| Syntax                                           | Description                              |
|:-------------------------------------------------|:-----------------------------------------|
| `Bfile();`                                       | Creates a `NULL` `Bfile` object.         |
| `Bfile(`<br>`   const Connection *connectionp);` | Creates an uninitialized `Bfile `object. |
| `Bfile(`<br>`   const Bfile &srcBfile);`         | Creates a copy of a `Bfile` object.      |

| Parameter     | Description               |
|:--------------|:--------------------------|
| `connectionp` | The connection pointer    |
| `srcBfile`    | The source `Bfile` object |

### 13.6.2 close()

Closes a previously opened `Bfile`.

#### Syntax

    void close();

### 13.6.3 closeStream()

Closes the stream obtained from the `Bfile`.

#### Syntax

    void closeStream(
       Stream *stream);

| Parameter | Description              |
|:----------|:-------------------------|
| `stream`  | The stream to be closed. |

### 13.6.4 fileExists()

Tests whether the `BFILE` exists. If the `BFILE` exists, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool fileExists() const;

### 13.6.5 getDirAlias()

Returns a string containing the directory object associated with the `BFILE`.

#### Syntax

    string getDirAlias() const;

### 13.6.6 getFileName()

Returns a string containing the file name associated with the `BFILE`.

#### Syntax

    string getFileName() const;

### 13.6.7 getStream()

Returns a `Stream `object read from the `BFILE`. If a stream is open, it is disallowed to open another stream on the `Bfile` object. The stream must be closed before performing any `Bfile` object operations.

#### Syntax

    Stream* getStream(
       unsigned int offset = 1,
       unsigned int amount = 0);

| Parameter | Description                                                                                                                                                                                                       |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `offset`  | The starting position at which to begin reading data from the `BFILE`. If `offset` is not specified, the data is written from the beginning of the `BLOB`. Valid values are numbers greater than or equal to `1`. |
| `amount`  | The total number of bytes to be read from the `BFILE`; if `amount` is `0`, the data is read in a streamed mode from input `offset` until the end of the `BFILE`.                                                  |

### 13.6.8 getUStringDirAlias()

Returns a `UString` containing the directory object associated with the `BFILE`. Note the `UString` object is in UTF16 character set. The environment associated with `BFILE` should be associated with UTF16 characterset.

#### Syntax

    UString getUStringDirAlias() const;

### 13.6.9 getUStringFileName()

Returns a `UString` containing the file name associated with the `BFILE`. Note the `UString` object is in UTF16 characterset. The environment associated with `BFILE` should be associated with UTF16 characterset.

#### Syntax

    UString getUStringFileName() const;

### 13.6.10 isInitialized()

Tests whether the `Bfile` object has been initialized. If the `Bfile` object has been initialized, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isInitialized() const;

### 13.6.11 isNull()

Tests whether the `Bfile` object is atomically `NULL`. If the `Bfile` object is atomically `NULL`, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.6.12 isOpen()

Tests whether the `BFILE` is open. The `BFILE` is considered to be open only if it was opened by a call on this `Bfile` object. (A different `Bfile` object could have opened this file as multiple `open()` calls can be performed on the same file by associating the file with different `Bfile` objects). If the `BFILE` is open, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isOpen() const;

### 13.6.13 length()

Returns the number of bytes (inclusive of the end of file marker) in the `BFILE`.

#### Syntax

    unsigned int length() const;

### 13.6.14 open()

Opens an existing `BFILE `for read-only access. This function is meaningful the first time it is called for a `Bfile` object.

#### Syntax

    void open();

### 13.6.15 operator=()

Assigns a `Bfile` object to the current `Bfile` object. The source `Bfile` object is assigned to this `Bfile` object only when this `Bfile` object gets stored in the database.

#### Syntax

    Bfile& operator=(
       const Bfile &srcBfile);

| Parameter  | Description                                                      |
|:-----------|:-----------------------------------------------------------------|
| `srcBfile` | The `Bfile` object to be assigned to the current `Bfile` object. |

### 13.6.16 operator==()

Compares two `Bfile` objects for equality. The `Bfile` objects are equal if they both refer to the same `BFILE`. If the `Bfile` objects are `NULL`, then `FALSE` is returned. If the `Bfile` objects are equal, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator==(
       const Bfile &srcBfile) const;

| Parameter  | Description                                                        |
|:-----------|:-------------------------------------------------------------------|
| `srcBfile` | The `Bfile` object to be compared with the current `Bfile` object. |

### 13.6.17 operator!=()

Compares two `Bfile objects` for inequality. The `Bfile` objects are equal if they both refer to the same `BFILE`. If the `Bfile` objects are not equal, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator!=(
       const Bfile &srcBfile) const;

| Parameter  | Description                                                        |
|:-----------|:-------------------------------------------------------------------|
| `srcBfile` | The `Bfile` object to be compared with the current `Bfile` object. |

### 13.6.18 read()

Reads a part or all of the `BFILE` into the buffer specified, and returns the number of bytes read.

#### Syntax

    unsigned int read(
       unsigned int amt,
       unsigned char *buffer,
       unsigned int bufsize,
       unsigned int offset = 1) const;

| Parameter  | Description                                                                                                                                                 |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `amt`      | The number of bytes to be read. Valid values are numbers greater than or equal to `1`.                                                                      |
| `buffer`   | The buffer that the `BFILE `data is to be read into. Valid values are numbers greater than or equal to `amt`.                                               |
| `buffsize` | The size of the buffer that the `BFILE` data is to be read into. Valid values are numbers greater than or equal to `amt`.                                   |
| `offset`   | The starting position at which to begin reading data from the `BFILE`. If `offset` is not specified, the data is written from the beginning of the `BFILE`. |

### 13.6.19 setName()

Sets the directory object and file name of the `BFILE`.

| Syntax                                                                             | Description                                                                                                                                  |
|:-----------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| `void setName(`<br>`   const string &dirAlias,`<br>`   const string &fileName);`   | Sets the directory object and file name of the `BFILE`.                                                                                      |
| `void setName(`<br>`   const UString &dirAlias,`<br>`   const UString &fileName);` | Sets the directory object and file name of the `BFILE` (Unicode support). The client `Environment` should be initialized in OCCIUTIF16 mode. |

| Parameter  | Description                                             |
|:-----------|:--------------------------------------------------------|
| `dirAlias` | The directory object to be associated with the `BFILE`. |
| `fileName` | The file name to be associated with the `BFILE`.        |

### 13.6.20 setNull()

Sets the `Bfile object` to atomically `NULL`.

#### Syntax

    void setNull();
