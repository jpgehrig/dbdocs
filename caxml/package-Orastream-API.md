`Orastream` APIs support handling of text and binary nodes that exceed 64K in an XML document.

The data types used by `Orastream` are found in [Datatypes for C](datatypes.md); they include [oracheck](datatypes.md), [oraerr](datatypes.md), [oraprop_id](datatypes.md), [oramemctx](datatypes.md), [oraprop](datatypes.md), [oraprop_t](datatypes.md), [oraprop_v](datatypes.md), [orastream](datatypes.md), and [orastreamhdl](datatypes.md).

The error codes for the `Orastream` interfaces are described in Table 5-1.

Table 5-1 Orastream Error Codes for XML C Implementation

| Error Code                       | Description                                                               |
|:---------------------------------|:--------------------------------------------------------------------------|
| `ORASTREAM_ERR_NULL_POINTER`     | Null pointer encountered.                                                 |
| `ORASTREAM_ERR_BAD_STREAM`       | Invalid stream object.                                                    |
| `ORASTREAM_ERR_WRONG_DIRECTION`  | Stream object is defined for the opposite I/O direction.                  |
| `ORASTREAM_ERR_UNKNOWN_PROPERTY` | Unknown creation property.                                                |
| `ORASTREAM_ERR_NO_DIRECTION`     | The I/O direction of the stream is undefined.                             |
| `ORASTREAM_ERR_BI_DIRECTION`     | The stream direction is incorrectly defined as using both I/O directions. |
| `ORASTREAM_ERR_NOT_OPEN`         | The stream is not open.                                                   |
| `ORASTREAM_ERR_WRONG_MODE`       | The stream is defined for the opposite char/byte mode.                    |
| `ORASTREAM_ERR_CANT_OPEN`        | The stream cannot be opened.                                              |
| `ORASTREAM_ERR_CANT_CLOSE`       | The stream cannot be closed.                                              |

The `Orastream` methods, listed in the following table, support unidirectional streams used to move data piecewise. The direction and mode of the stream is determined by the paramters that initialize the stream in the OraStreamInit() method.

Table 5-2 Summary of OraStream Methods for XML C Implementation

| Function             | Summary                               |
|:---------------------|:--------------------------------------|
| OraStreamClose()     | Closes the stream.                    |
| OraStreamHandle()    | Returns the handle to the stream.     |
| OraStreamInit()      | Initializes the stream.               |
| OraStreamIsOpen()    | Determines if the stream is open.     |
| OraStreamOpen()      | Opens the stream.                     |
| OraStreamRead()      | Reads bytes from the stream.          |
| OraStreamReadable()  | Determines if the stream is readable. |
| OraStreamReadChar()  | Reads characters from the stream.     |
| OraStreamSid()       | Sets the SID of a stream.             |
| OraStreamTerm()      | Destroys the stream.                  |
| OraStreamWrite()     | Writes bytes to the stream.           |
| OraStreamWritable()  | Determines if the stream is writable. |
| OraStreamWriteChar() | Writes characters to the stream.      |

**See Also:**

[Oracle XML Developer's Kit Programmer's Guide](../adxdk/using-XML-parser-for-C.md)

### OraStreamClose()

Closes the `orastream` object.

The function is used to close the given stream by calling the 'close' callback function of the stream.

Returns `ORAERR_OK` for success, or the error code for failure.

#### Syntax

    oraerr OraStreamClose(
      orastream *stream);

| Parameter | In/Out | Description           |
|:----------|:-------|:----------------------|
| `stream`  | `IN`   | Stream that is closed |

### OraStreamHandle()

Returns the handle of the `orastream `object.

The handle contains the generic pointers and file descriptors.

#### Syntax

    orastreamhdl *OraStreamHandle(
      orastream *stream);

| Parameter | In/Out | Description                     |
|:----------|:-------|:--------------------------------|
| `stream`  | `IN`   | Stream whose handle is returned |

### OraStreamInit()

Creates and initializes a `orastream` object.

#### Syntax

    orastream *OraStreamInit(
      void *sctx,
      void *sid,
      oraerr *err,
      list);

| Parameter | In/Out | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:----------|:-------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sctx`    | `IN`   | The input context; may be `NULL`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `sid`     | `IN`   | The user-defined stream context identifier                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `err`     | `OUT`  | The error, if any. `ORAERR_OK` for success, or the error code for failure.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `list`    | `IN`   | `NULL`-terminated list of name-value pairs of arguments that specify the properties of the new `orastream` oject. These are:<br>• The `open` property name is for the open function, and its value follows.<br>`ORASTREAM_OPEN_F((*), sctx, sid, hdl, length)`<br>• The `close` property name is for the close function, and its value follows.<br>`ORASTREAM_CLOSE_F((*), sctx, sid, hdl)`<br>• The `read` property name is for reading byte data from the stream to the buffer. Note that `nread` returns the number of bytes actually read.<br>`ORASTREAM_READ_F((*), sctx, sid, hdl, dest,`<br>`  size, start, nread, eoi)`<br>• The `write` property name is for writing byte data from the buffer to the stream. Note that `written` returns the number of bytes actually written.<br>`ORASTREAM_WRITE_F((*), sctx, sid, hdl, src,`<br>`  size, written)`<br>• The `read_char` property name is for reading character data from the stream to the buffer. Note that `nread` returns the number of characters actually read.<br>`ORASTREAM_READ_F((*), sctx, sid, hdl, dest,`<br>`  size, start, nread, eoi)`<br>• The `write_char` property name is for writing character data from the buffer to the stream. Note that `written` returns the number of characters actually written.<br>`ORASTREAM_WRITE_F((*), sctx, sid, hdl, src,`<br>`  size, written)` |

### OraStreamIsOpen()

Determines if the `orastream` is open. Returns `TRUE` or `FALSE`.

Note that the stream must be open to perform read and write operations.

#### Syntax

    boolean OraStreamIsOpen(
      orastream *stream);

| Parameter | In/Out | Description                                         |
|:----------|:-------|:----------------------------------------------------|
| `stream`  | `IN`   | The stream that should be open for reads or writes. |

### OraStreamOpen()

Opens the `orastream` object.

The function opens the stream by calling the 'open' callback function of the stream.

Returns `ORAERR_OK` for success, or the error code for failure.

#### Syntax

    oraerr OraStreamOpen(
      orastream *stream,
      ubig_ora *length)

| Parameter | In/Out | Description                  |
|:----------|:-------|:-----------------------------|
| `stream`  | `IN`   | The stream that is open      |
| `length`  | `OUT`  | Optional parameter; not used |

### OraStreamRead()

Reads `byte`s from the `orastream` object.

The function is used to read the data from the stream into the specified buffer. It also returns `TRUE` for the `eoi` parameter if the end of stream is reached.

Returns `ORAERR_OK` for success, or the error code for failure.

#### Syntax

    oraerr OraStreamRead(
      orastream *stream,
      oratext *dest,
      ubig_ora size,
      oratext **start,
      ubig_ora *nread,
      ub1 *eoi);

| Parameter | In/Out | Description                                                       |
|:----------|:-------|:------------------------------------------------------------------|
| `stream`  | `IN`   | Stream that is being read                                         |
| `dest`    | `IN`   | The destination buffer                                            |
| `size`    | `IN`   | The size of the data to be read                                   |
| `start`   | `OUT`  | Pointer to the start of data being read                           |
| `nread`   | `OUT`  | Number of bytes actually read from the stream                     |
| `eoi`     | `OUT`  | Returns `TRUE` if end of the stream is reached; `FALSE` otherwise |

### OraStreamReadable()

Determines if an existing `orastream` object is readable.

Returns `TRUE` or `FALSE`.

#### Syntax

    boolean OraStreamReadable(
      orastream *stream);

| Parameter | In/Out | Description                            |
|:----------|:-------|:---------------------------------------|
| `stream`  | `IN`   | Stream that is checked for readability |

### OraStreamReadChar()

Reads `char`s from the `orastream` object.

The function is used to read the data from the stream into the specified buffer. It also returns `TRUE` for the `eoi` parameter if the end of stream is reached.

Returns `ORAERR_OK` for success, or the error code for failure.

#### Syntax

    oraerr OraStreamReadChar(
      orastream *stream,
      oratext *dest,
      ubig_ora size,
      oratext **start,
      ubig_ora *nread,
      ub1 *eoi);

| Parameter | In/Out | Description                                                       |
|:----------|:-------|:------------------------------------------------------------------|
| `stream`  | `IN`   | Stream that is being read                                         |
| `dest`    | `IN`   | The destination buffer                                            |
| `size`    | `IN`   | The size of the data to be read                                   |
| `start`   | `OUT`  | Pointer to the start of data being read                           |
| `nread`   | `OUT`  | Number of characters actually read from the stream                |
| `eoi`     | `OUT`  | Returns `TRUE` if end of the stream is reached; `FALSE` otherwise |

### OraStreamSid()

Assigns an SID to an existing `orastream` object. Returns the old SID through the `OUT` parameter `osid`.

Returns `ORAERR_OK` for success, or the error code for failure.

#### Syntax

    oraerr OraStreamSid(
      orastream *stream,
      void *sid,
      void **osid);

| Parameter | In/Out | Description                     |
|:----------|:-------|:--------------------------------|
| `stream`  | `IN`   | The stream whose SID is changed |
| `sid`     | `IN`   | The new SID                     |
| `osid`    | `OUT`  | The previous SID of the stream  |

### OraStreamTerm()

Destroys a `orastream` object and frees its associated memory.

Returns `ORAERR_OK` for success, or the error code for failure.

#### Syntax

    oraerr OraStreamTerm(
      orastream *stream);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `stream`  | `IN`   | Stream that is destroyed |

### OraStreamWrite()

Writes `byte`s to the `orastream` object.

The number of bytes actually read are stored by the `OUT` parameter `nwrote`.

Returns `ORAERR_OK` for success, or the error code for failure.

#### Syntax

    oraerr OraStreamWrite(
      orastream *stream,
      oratext *src,
      ubig_ora size,
      ubig_ora *nwrote);

| Parameter | In/Out | Description                           |
|:----------|:-------|:--------------------------------------|
| `stream`  | `IN`   | Stream where the data is written      |
| `src`     | `IN`   | Buffer from which the data is written |
| `size`    | `IN`   | Size of data to be written            |
| nwrote    | `OUT`  | Number of bytes written to the stream |

### OraStreamWritable()

Determines if an existing `orastream` object is writable.

Returns `TRUE` or `FALSE`.

#### Syntax

    boolean OraStreamWritable(
      orastream *stream);

| Parameter | In/Out | Description                             |
|:----------|:-------|:----------------------------------------|
| `stream`  | `IN`   | Stream that is checked for writability. |

### OraStreamWriteChar()

Writes `char`s to the `orastream` object.

The number of characters actually written are stored by the `OUT` parameter `nwrote`.

Returns `ORAERR_OK` for success, or the error code for failure.

#### Syntax

    oraerr OraStreamWriteChar(
      orastream *stream,
      oratext *src,
      ubig_ora size,
      ubig_ora *nwrote);

| Parameter | In/Out | Description                                |
|:----------|:-------|:-------------------------------------------|
| `stream`  | `IN`   | Stream where the data is written           |
| `src`     | `IN`   | Buffer from which the data is written      |
| `size`    | `IN`   | Size of data to be written                 |
| nwrote    | `OUT`  | Number of characters written to the stream |
