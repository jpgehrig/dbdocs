You use a `Stream` to read or write streamed data (usually `LONG`).

- A read-able `Stream` is used to obtain streamed data from a result set or `OUT` bind variable from a stored procedure call. A read-able `Stream` must be read completely until the end of data is reached or it should be closed to discard any unwanted data.

- A write-able `Stream` is used to provide streamed data (usually `LONG`) to parameterized statements including callable statements.

Table 13-45 Enumerated Values Used by Stream Class

| Attribute | Options                                                                                                                                                                                                                                                 |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Status`  | • `READY_FOR_READ` indicates that the `Stream` is ready for read operations<br>• `READY_FOR_WRITE` indicates that the `Stream` is ready for write operations<br>• `INACTIVE` indicates that the `Stream` is not available for ready or write operations |

Table 13-46 Summary of Stream Methods

| Method            | Summary                                                                      |
|:------------------|:-----------------------------------------------------------------------------|
| readBuffer()      | Reads the stream and returns the amount of data read from the Stream object. |
| readLastBuffer()  | Reads last buffer from Stream.                                               |
| writeBuffer()     | Writes data from buffer to the stream.                                       |
| writeLastBuffer() | Writes the last data from buffer to the stream.                              |
| status()          | Returns the current status of the stream.                                    |

### 13.31.1 readBuffer()

Reads data from `Stream`. The size parameter specifies the maximum number of byte characters to read. Returns the amount of data read from the `Stream` object. -1 means end of data on the stream.

#### Syntax

    virtual int readBuffer(
       char *buffer,
       unsigned int size) = 0;

| Parameter | Description                                                    |
|:----------|:---------------------------------------------------------------|
| `buffer`  | Pointer to data buffer; must be allocated and freed by caller. |
| `size`    | Specifies the number of bytes to be read.                      |

### 13.31.2 readLastBuffer()

Reads the last buffer from the `Stream`. It can also be called top discard unread data. The size parameter specifies the maximum number of byte characters to read. Returns the amount of data read from the `Stream` object; `-1` means end of data on the stream.

#### Syntax

    virtual int readLastBuffer(
       char *buffer,
       unsigned int size) = 0;

| Parameter | Description                                                    |
|:----------|:---------------------------------------------------------------|
| `buffer`  | Pointer to data buffer; must be allocated and freed by caller. |
| `size`    | Specifies the number of bytes to be read.                      |

### 13.31.3 writeBuffer()

Writes data from buffer to the stream. The amount of data is determined by `size`.

#### Syntax

    virtual void writeBuffer(
       char *buffer,
       unsigned int size) = 0;

| Parameter | Description                                    |
|:----------|:-----------------------------------------------|
| `buffer`  | Pointer to data buffer.                        |
| `size`    | Specifies the number of `chars` to be written. |

### 13.31.4 writeLastBuffer()

This method writes the last data buffer to the stream. It can also be called to write the last chunk of data. The amount of data written is determined by size.

#### Syntax

    virtual void writeLastBuffer(
       char *buffer,
       unsigned int size) = 0;

| Parameter | Description                                  |
|:----------|:---------------------------------------------|
| `buffer`  | Pointer to data buffer.                      |
| `size`    | Specifies the number of bytes to be written. |

### 13.31.5 status()

Returns the current `Status`, as defined in Table 13-45 .

#### Syntax

    virtual Status status() const;
