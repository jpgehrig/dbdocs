Table 26-2 lists the LOB functions that use the LOB locator that are described in this section. Use functions that end in "2" for all new applications.

Beginning with Oracle Database 12`c` Release 2 (12.2), most LOB functions support Application Continuity (see [When Application Continuity in OCI Can Fail Over](high-availability-in-oci.md) for a complete list). This support also includes some deprecated LOB functions for compatibility listed in [Deprecated Lob Functions](deprecated-oci-functions.md).

Beginning with Oracle Database 12`c` Release 2 (12.2), OCI LOB functions support distributed operations on remote LOBs (CLOB, BLOB) except for OCI LOB functions for BFILES. This includes support for certain queries that select a remote LOB locator that in previous releases returned an error. The only restriction is that all LOB functions that take in two locators should have both LOBs collocated at one database. The following LOB functions throw an error when a remote locator is passed to it: `OCILobAssign()`, `OCILobLocatorAssign()`, `OCILobEnableBuffering()`, `OCILobDisableBuffering()`, `OCILobFlushBuffer()`, `OCILobArrayRead()`, `OCILobArrayWrite()`, and `OCILobLoadFromFile2()`.

**Note:**

There is another way of accessing LOBs -- using the data interface for LOBs. You can bind or define character data for a `CLOB` column or `RAW` data for a `BLOB` column, as described in these locations:

- [About Binding LOB Data](binding-and-defining-in-oci.md) for usage and examples for both `INSERT` and `UPDATE` statements

- [About Defining LOB Data](binding-and-defining-in-oci.md) for usage and examples of `SELECT` statements

- [LOB and BFILE Operations](lobs-and-bfile-operations.md)

Table 26-2 LOB Functions 

| Function                                                | Purpose                                                                                                  |
|:--------------------------------------------------------|:---------------------------------------------------------------------------------------------------------|
| OCIDurationBegin()                                      | Start user duration for temporary LOB                                                                    |
| OCIDurationEnd()                                        | End user duration for temporary LOB                                                                      |
| OCILobAppend()                                          | Append one LOB to another                                                                                |
| OCILobArrayRead()                                       | Read LOB data for multiple locators                                                                      |
| OCILobArrayWrite()                                      | Write LOB data for multiple locators                                                                     |
| OCILobAssign()                                          | Assign one LOB locator to another                                                                        |
| OCILobCharSetForm()                                     | Get character set form from LOB locator                                                                  |
| OCILobCharSetId()                                       | Get character set ID from LOB locator                                                                    |
| OCILobClose()                                           | Close a previously opened LOB                                                                            |
| OCILobCopy2()                                           | Copy all or part of one LOB to another. This function must be used for LOBs of size greater than 4 GB.   |
| OCILobCreateTemporary()                                 | Create a temporary LOB                                                                                   |
| [OCILobDisableBuffering()](deprecated-oci-functions.md) | Turn LOB buffering off                                                                                   |
| [OCILobEnableBuffering()](deprecated-oci-functions.md)  | Turn LOB buffering on                                                                                    |
| OCILobErase2()                                          | Erase a portion of a LOB. This function must be used for LOBs of size greater than 4 GB.                 |
| OCILobFileClose()                                       | Close a previously opened `BFILE`                                                                        |
| OCILobFileCloseAll()                                    | Close all previously opened files                                                                        |
| OCILobFileExists()                                      | Check if a file exists on the server                                                                     |
| OCILobFileGetName()                                     | Get directory object and file name from the LOB locator                                                  |
| OCILobFileIsOpen()                                      | Check if file on server is open using this locator                                                       |
| OCILobFileOpen()                                        | Open a `BFILE`                                                                                           |
| OCILobFileSetName()                                     | Set directory object and file name in the LOB locator                                                    |
| [OCILobFlushBuffer()](deprecated-oci-functions.md)      | Flush the LOB buffer                                                                                     |
| OCILobFreeTemporary()                                   | Free a temporary LOB                                                                                     |
| OCILobGetChunkSize()                                    | Get the chunk size of a LOB                                                                              |
| OCILobGetContentType()                                  | Retrieve the user-specified content type string (a file format identifier) for a SecureFile              |
| OCILobGetLength2()                                      | Get length of a LOB. This function must be used for LOBs of size greater than 4 GB.                      |
| OCILobGetOptions()                                      | Get option settings of a SecureFile                                                                      |
| OCILobGetStorageLimit()                                 | Get the maximum length of an internal LOB (BLOB, CLOB, or NCLOB) in bytes                                |
| OCILobIsEqual()                                         | Compare two LOB locators for Equality                                                                    |
| OCILobIsOpen()                                          | Check to see if a LOB is open                                                                            |
| OCILobIsTemporary()                                     | Determine if a given LOB is temporary                                                                    |
| OCILobLoadFromFile2()                                   | Load a LOB from a `BFILE`. This function must be used for LOBs of size greater than 4 GB.                |
| OCILobLocatorAssign()                                   | Assign one LOB locator to another                                                                        |
| OCILobLocatorIsInit()                                   | Check to see if a LOB locator is initialized                                                             |
| OCILobOpen()                                            | Open a LOB                                                                                               |
| OCILobRead2()                                           | Read a portion of a LOB. This function must be used for LOBs of size greater than 4 GB.                  |
| OCILobSetContentType()                                  | Store the user-specified content type string of the SecureFile                                           |
| OCILobSetOptions()                                      | Enable option settings for existing and newly created SecureFiles                                        |
| OCILobTrim2()                                           | Truncate a LOB. This function must be used for LOBs of size greater than 4 GB.                           |
| OCILobWrite2()                                          | Write into a LOB. This function must be used for LOBs of size greater than 4 GB.                         |
| OCILobWriteAppend2()                                    | Write data beginning at the end of a LOB. This function must be used for LOBs of size greater than 4 GB. |

Note the following for parameters in the OCI LOB calls:

- For fixed-width client-side character sets, the offset and amount parameters are always in characters for `CLOB`s and `NCLOB`s, and in bytes for `BLOB`s and `BFILE`s.

- For varying-width client-side character sets, these rules generally apply:

  - Amount (`amtp`) parameter - When the amount parameter refers to the server-side LOB, the amount is in characters. When the amount parameter refers to the client-side buffer, the amount is in bytes.

    For more information, see individual LOB calls, such as `OCILobGetLength()` (deprecated), `OCILobGetLength2()`, `OCILobRead()` (deprecated), `OCILobRead2()`, `OCILobWrite()` (deprecated), and `OCILobWrite2()`.

  - Offset (`offset`) parameter - Regardless of whether the client-side character set is varying-width, the offset parameter is always in characters for `CLOB`s and `NCLOB`s and in bytes for `BLOB`s and `BFILE`s.

- For many of the LOB operations, regardless of the client-side character set, the amount parameter is in characters for `CLOB`s and `NCLOB`s. These LOB operations include `OCILobCopy2()`, `OCILobErase2()`, `OCILobGetLength2()`, `OCILobLoadFromFile2()`, and `OCILobTrim2()`. All these operations refer to the amount of LOB data on the server.

A streaming operation means that the LOB is read or written in pieces. Streaming can be implemented using a polling mechanism or by registering a user-defined callback.

### 26.3.1 OCIDurationBegin()

Starts a user duration for a temporary LOB.

#### Purpose

Starts a user duration for a temporary LOB.

#### Syntax

    sword OCIDurationBegin ( OCIEnv              *env,
                             OCIError            *err,
                             const OCISvcCtx     *svc,
                             OCIDuration          parent,
                             OCIDuration         *duration );

#### Parameters

env (IN/OUT)
Pass as a `NULL` pointer.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

svc (IN)
An OCI service context handle. Must be non-`NULL`.

parent (IN)
The duration number of the parent duration. It is one of these:

- `OCI_DURATION_STATEMENT`

- `OCI_DURATION_SESSION`

duration (OUT)
An identifier unique to the newly created user duration.

#### Comments

This function starts a user duration. In release 8.1 or later, user durations can be used when creating temporary LOBs. A user can have multiple active user durations simultaneously. The user durations do not have to be nested. The `duration` parameter is used to return a number that uniquely identifies the duration created by this call.

**Related Topics**

- [Temporary LOB Durations](lobs-and-bfile-operations.md)

### 26.3.2 OCIDurationEnd()

Terminates a user duration for a temporary LOB.

#### Purpose

Terminates a user duration for a temporary LOB.

#### Syntax

    sword OCIDurationEnd ( OCIEnv             *env,
                           OCIError           *err,
                           const OCISvcCtx    *svc,
                           OCIDuration         duration );

#### Parameters

env (IN/OUT)
Pass as a `NULL` pointer.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

svc (IN)
OCI service context. This should be passed as `NULL` for cartridge services.

duration (IN)
A number to identify the user duration.

#### Comments

This function terminates a user duration. Temporary LOBs that are allocated for the user duration are freed.

**Related Topics**

- OCIDurationBegin()
- [OCIErrorGet()](miscellaneous-functions.md)
- [Temporary LOB Durations](lobs-and-bfile-operations.md)
- [OCIDurationBegin()](cartridge-services-memory-services.md)

### 26.3.3 OCILobAppend()

Appends a LOB value at the end of another LOB as specified.

#### Purpose

Appends a LOB value at the end of another LOB as specified.

#### Syntax

    sword OCILobAppend ( OCISvcCtx        *svchp,
                         OCIError         *errhp,
                         OCILobLocator    *dst_locp,
                         OCILobLocator    *src_locp );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

dst_locp (IN/OUT)
An internal LOB locator uniquely referencing the destination LOB. This locator must have been a locator that was obtained from the server specified by `svchp`.

src_locp (IN)
An internal LOB locator uniquely referencing the source LOB. This locator must have been a locator that was obtained from the server specified by `svchp`.

#### Comments

Appends a LOB value at the end of another LOB as specified. The data is copied from the source to the end of the destination. The source and destination LOBs must exist. The destination LOB is extended to accommodate the newly written data. It is an error to extend the destination LOB beyond the maximum length allowed (4 Gigabytes (GB)) or to try to copy from a `NULL` LOB.

The source and the destination LOB locators must be of the same type (that is, they must both be `BLOB`s or both be `CLOB`s). LOB buffering must not be enabled for either type of locator. This function does not accept a `BFILE` locator as the source or the destination.

It is not mandatory that you wrap this LOB operation inside the open or close calls. If you did not open the LOB before performing this operation, then the functional and domain indexes on the LOB column are updated during this call. However, if you did open the LOB before performing this operation, then you must close it before you commit your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance. If you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- OCILobTrim2()
- OCILobWrite2()
- OCILobCopy2()
- OCILobWriteAppend2()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.4 OCILobArrayRead()

Reads LOB data for multiple locators in one round-trip.

#### Purpose

This function can be used for LOBs of size greater than or less than 4 GB.

#### Syntax

    sword OCILobArrayRead ( OCISvcCtx                *svchp,
                            OCIError                 *errhp,
                            ub4                      *array_iter,
                            OCILobLocator           **locp_arr,
                            oraub8                   *byte_amt_arr,
                            oraub8                   *char_amt_arr,
                            oraub8                   *offset_arr,
                            void                    **bufp_arr,
                            oraub8                    bufl_arr,
                            ub1                       piece,
                            void                     *ctxp,
                            OCICallbackLobArrayRead  (cbfp)
                                            (
                                             void          *ctxp,
                                             ub4            array_iter,
                                             const void    *bufp,
                                             oraub8         lenp,
                                             ub1            piecep
                                             void         **changed_bufpp,
                                             oraub8        *changed_lenp
                                            )
                            ub2                       csid,
                            ub1                       csfrm );

#### Parameters

svchp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

array_iter (IN/OUT)
IN - This parameter indicates the size of the LOB locator array. For polling this is relevant only for the first call and is ignored in subsequent calls.

OUT - In polling mode, this parameter indicates the array index of the element read from.

locp_arr (IN)
An array of LOB or `BFILE` locators.

byte_amt_arr (IN/OUT)
An array of `oraub8` variables. The array size must be the same as the locator array size. The entries correspond to the amount in bytes for the locators.

IN - The number of bytes to read from the database. Used for `BLOB` and `BFILE` always. For `CLOB` and `NCLOB`, it is used only when the corresponding value in `char_amt_arr` is zero.

OUT - The number of bytes read into the user buffer.

char_amt_arr (IN/OUT)
An array of `oraub8` variables. The array size must be the same as the locator array size. The entries correspond to the amount in characters for the locators.

IN - The maximum number of characters to read into the user buffer. Ignored for `BLOB` and `BFILE`.

OUT - The number of characters read into the user buffer. Undefined for `BLOB` and `BFILE`.

offset\_arr (IN)
An array of `oraub8` variables. The array size must be the same as the locator array size. For character LOBs (`CLOB`s, `NCLOB`s) it is the number of characters from the beginning of the LOB; for binary LOBs or `BFILE`s, it is the number of bytes. The first position is 1.

bufp \_arr (IN/OUT)
An array of pointers to buffers into which the piece is read. The array size must be the same as the locator array size.

bufl\_arr (IN)
An array of `oraub8` variables indicating the buffer lengths for the buffer array. The array size must be the same as the locator array size.

piece (IN)
`OCI_ONE_PIECE` - The call never assumes polling. If the amount indicated is more than the buffer length, then the buffer is filled as much as possible.

For polling, pass `OCI_FIRST_PIECE` the first time and `OCI_NEXT_PIECE` in subsequent calls. `OCI_FIRST_PIECE` should be passed while using the callback.

ctxp (IN)
The context pointer for the callback function. Can be `NULL`.

cbfp (IN)
A callback that can be registered to be called for each piece. If this is `NULL`, then `OCI_NEED_DATA` is returned for each piece.

The callback function must return `OCI_CONTINUE` for the read to continue. If any other error code is returned, the LOB read is terminated.

ctxp (IN)
The context for the callback function. Can be `NULL`.

array_iter (IN)
The index of the element read from.

bufp (IN/OUT)
A buffer pointer for the piece.

lenp (IN)
The length in bytes of the current piece in `bufp`.

piecep (IN)
Which piece: `OCI_FIRST_PIECE`, `OCI_NEXT_PIECE`, or `OCI_LAST_PIECE`.

changed_bufpp (OUT)
The callback function can put the address of a new buffer if it prefers to use a new buffer for the next piece to read. The default old buffer `bufp` is used if this parameter is set to `NULL`.

changed_lenp (OUT)
Length of the new buffer, if provided.

<!-- -->

csid (IN)
The character set ID of the buffer data. If this value is 0, then `csid` is set to the client's `NLS_LANG` or `NLS_CHAR` value, depending on the value of `csfrm`. It is never assumed to be the server character set, unless the server and client have the same settings.

csfrm (IN)
The character set form of the buffer data. The `csfrm` parameter must be consistent with the type of the LOB.

The `csfrm` parameter has two possible nonzero values:

- `SQLCS_IMPLICIT` - database character set ID

- `SQLCS_NCHAR` - NCHAR character set ID

The default value is `SQLCS_IMPLICIT`. If `csfrm` is not specified, the default is assumed.

#### Comments

It is an error to try to read from a `NULL` LOB or `BFILE`.

**Note:**

When reading or writing LOBs, the character set form (`csfrm`) specified should match the form of the locator itself.

`OCILobArrayRead()` throws an error when a remote locator is passed to it.

For `BFILE`s, the operating system file must exist on the server, and it must have been opened by `OCILobFileOpen()` or `OCILobOpen()` using the input locator. The Oracle Database must have permission to read the operating system file, and the user must have read permission on the directory object.

When you use the polling mode for `OCILobArrayRead()`, the first call must specify values for `offset_arr` and `amt_arr`, but on subsequent polling calls to `OCILobArrayRead()`, you need not specify these values.

If the LOB is a `BLOB`, the `csid` and `csfrm` parameters are ignored.

**Note:**

To terminate an `OCILobArrayRead()` operation and free the statement handle, use the `OCIBreak()` call.

The following points apply to reading LOB data in streaming mode:

- When you use polling mode, be sure to specify the `char_amt_arr` and `byte_amt_arr` and `offset_arr` parameters only in the first call to `OCILobArrayRead()`. On subsequent polling calls, these parameters are ignored. If both `byte_amt_arr` and `char_amt_arr` are set to point to zero and `OCI_FIRST_PIECE` is passed, then polling mode is assumed and data is read to the end of the LOB. On output, `byte_amt_arr` gives the number of bytes read in the current piece. For `CLOB`s and `NCLOB`s, `char_amt_arr` gives the number of characters read in the current piece.

- When you use callbacks, the `lenp` parameter, which is input to the callback, indicates how many bytes are filled in the buffer. Check the `lenp` parameter during your callback processing, because the entire buffer may not be filled with data.

- When you use polling, examine the `byte_amt_arr` parameter to see how much the buffer is filled for the current piece. For `CLOB`s and `NCLOB`s, `char_amt_arr` returns the number of characters read in the buffer as well.

To read data in UTF-16 format, set the `csid` parameter to `OCI_UTF16ID`. If the c`sid` parameter is set, it overrides the `NLS_LANG` environment variable.

**Related Topics**

- OCILobFileOpen()
- OCILobOpen()
- OCILobWrite2()
- OCILobFileSetName()
- OCILobWriteAppend2()
- OCILobArrayWrite()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

- [PL/SQL REF CURSORs and Nested Tables in OCI](binding-and-defining-in-oci.md) for additional information on Unicode format

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-APIs-for-BFILE-operations.md) for a description of `BFILE`s

- The demonstration programs included with your Oracle Database installation for a code sample showing the use of LOB reads and writes.

- [OCI Demonstration Programs](oci-demo-programs.md)

- [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for general information about piecewise OCI operations

### 26.3.5 OCILobArrayWrite()

#### Purpose

Writes LOB data for multiple locators in one round-trip. This function can be used for LOBs of size greater than or less than 4 GB.

#### Syntax

    sword OCILobArrayWrite ( OCISvcCtx             *svchp,
                             OCIError              *errhp,
                             ub4                   *array_iter,
                             OCILobLocator         **locp_arr,
                             oraub8                *byte_amt_arr,
                             oraub8                *char_amt_arr,
                             oraub8                *offset_arr,
                             void                 **bufp_arr,
                             oraub8                *bufl_arr,
                             ub1                    piece,
                             void                  *ctxp,
                             OCICallbackLobArrayWrite (cbfp)
                                              (
                                                void     *ctxp,
                                                ub4       array_iter,
                                                void     *bufp,
                                                oraub8   *lenp,
                                                ub1      *piecep
                                                void    **changed_bufpp,
                                                oraub8   *changed_lenp
                                              )
                             ub2                    csid,
                             ub1                    csfrm );

#### Parameters

svchp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

array_iter (IN/OUT)
IN - This parameter indicates the size of the LOB locator array. For polling this is relevant only for the first call and is ignored in subsequent calls.

OUT - In polling mode this parameter indicates the array index of the element just written to.

locp_arr (IN/OUT)
An array of LOB locators.

byte_amt\_arr (IN/OUT)
An array of pointers to `oraub8` variables. The array size must be the same as the locator array size. The entries correspond to the amount in bytes for the locators.

IN - The number of bytes to write to the database. Always used for `BLOB`. For `CLOB` and `NCLOB` it is used only when `char_amt_arr` is zero.

OUT - The number of bytes written to the database.

char_amt (IN/OUT)
An array of pointers to `oraub8` variables. The array size must be the same as the locator array size. The entries correspond to the amount in characters for the locators.

IN - The maximum number of characters to write to the database. Ignored for `BLOB`.

OUT - The number of characters written to the database. Undefined for `BLOB`.

offset\_arr (IN)
An array of pointers to `oraub8` variables. The array size must be the same as the locator array size. Each entry in the array is the absolute offset from the beginning of the LOB value. For character LOBs (`CLOB`s, `NCLOB`s), it is the number of characters from the beginning of the LOB; for `BLOB`s, it is the number of bytes. The first position is 1.

bufp_arr (IN/OUT)
An array of pointers to buffers into which the pieces for the locators are written. The array size must be the same as the locator array size.

bufl_arr (IN)
An array of `oraub8` variables indicating the buffer lengths for the buffer array. The array size must be the same as the locator array size.

**Note:**

This parameter assumes an 8-bit byte. If your operating system uses a longer byte, you must adjust the value of `bufl_arr` accordingly.

piece (IN)
Which piece of the buffer is being written. The default value for this parameter is `OCI_ONE_PIECE`, indicating that the buffer is written in a single piece.

The following other values are also possible for piecewise or callback mode: `OCI_FIRST_PIECE`, `OCI_NEXT_PIECE`, and `OCI_LAST_PIECE`.

ctxp (IN)
The context for the callback function. Can be `NULL`.

cbfp (IN)
A callback that can be registered to be called for each piece. If this is `NULL`, then `OCI_NEED_DATA` is returned for each piece. The callback function must return `OCI_CONTINUE` for the write to continue. If any other error code is returned, the LOB write is terminated.

The callback takes the following parameters:

ctxp (IN)
The context for the callback function. Can be `NULL`.

array_iter (IN)
The index of the element written to.

bufp (IN/OUT)
A buffer pointer for the piece. This is the same as the `bufp` passed as an input to the `OCILobArrayWrite()` routine.

lenp (IN/OUT)
The length (in bytes) of the data in the buffer (IN), and the length (in bytes) of the current piece in `bufp` (OUT).

piecep (OUT)
Which piece: `OCI_NEXT_PIECE` or `OCI_LAST_PIECE`.

changed_bufpp (OUT)
The callback function can put the address of a new buffer if it prefers to use a new buffer for the next piece to read. The default old buffer `bufp` is used if this parameter is set to `NULL`.

changed_lenp (OUT)
Length of the new buffer, if provided.

csid (IN)
The character set ID of the data in the buffer. If this value is 0, then `csid` is set to the client's `NLS_LANG` or `NLS_CHAR` value, depending on the value of `csfrm`.

csfrm (IN)
The character set form of the buffer data. The `csfrm` parameter must be consistent with the type of the LOB.

The `csfrm` parameter has two possible nonzero values:

- `SQLCS_IMPLICIT` - Database character set ID

- `SQLCS_NCHAR` - NCHAR character set ID

The default value is `SQLCS_IMPLICIT`.

#### Comments

If LOB data exists, it is overwritten with the data stored in the buffer. The buffers can be written to the LOBs in a single piece with this call, or the buffers can be provided piecewise using callbacks or a standard polling method.

`OCILobArrayWrite()` throws an error when a remote locator is passed to it.

**Note:**

When you read or write LOBs, specify a character set form (`csfrm`) that matches the form of the locator itself.

The parameters `piece`, `csid`, and `csfrm` are the same for all locators of the array.

When you use the polling mode for `OCILobArrayWrite()`, the first call must specify values for `offset_arr`, `byte_amt_arr`, and `char_amt_arr`, but on subsequent polling calls to `OCILobArrayWrite()`, you need not specify these values.

If the value of the `piece` parameter is `OCI_FIRST_PIECE`, data may need to be provided through callbacks or polling.

If a callback function is defined in the `cbfp` parameter, then this callback function is invoked to get the next piece after a piece is written to the pipe. Each piece is written from `bufp_arr`. If no callback function is defined, then `OCILobArrayWrite()` returns the `OCI_NEED_DATA` error code. The application must call `OCILobArrayWrite()` again to write more pieces of the LOBs. In this mode, the buffer pointer and the length can be different in each call if the pieces are of different sizes and from different locations.

A `piece` value of `OCI_LAST_PIECE` terminates the piecewise write, regardless of whether the polling or callback method is used.

If the amount of data passed to the database (through either input mechanism) is less than the amount specified by the `byte_amt_arr` or the `char_amt_arr` parameter, an ORA-22993 error is returned.

This function is valid for internal LOBs only. `BFILE`s are not valid, because they are read-only. If the LOB is a `BLOB`, the `csid` and `csfrm` parameters are ignored.

If both `byte_amt_arr` and `char_amt_arr` are set to point to zero amount and `OCI_FIRST_PIECE` is given as input, then polling mode is assumed and data is written until you specify `OCI_LAST_PIECE`. For `CLOB`s and `NCLOB`s, `byte_amt_arr` and `char_amt_arr` return the data written by each piece in terms of number of bytes and number of characters respectively. For `BLOB`s, `byte_amt_arr` returns the number of bytes written by each piece, whereas `char_amt_arr` is undefined on output.

To write data in UTF-16 format, set the `csid` parameter to `OCI_UTF16ID`. If the `csid` parameter is set, it overrides the `NLS_LANG` environment variable.

It is not mandatory that you wrap this LOB operation inside the open or close calls. If you did not open the LOB before performing this operation, then the functional and domain indexes on the LOB column are updated during this call. However, if you did open the LOB before performing this operation, then you must close it before you commit your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance. If you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- OCILobRead2()
- OCILobAppend()
- OCILobCopy2()
- OCILobWriteAppend2()
- OCILobArrayRead()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

- [PL/SQL REF CURSORs and Nested Tables in OCI](binding-and-defining-in-oci.md) for additional information on Unicode format

- The demonstration programs included with your Oracle Database installation for a code sample showing the use of LOB reads and writes.

- [OCI Demonstration Programs](oci-demo-programs.md)

- [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for general information about piecewise OCI operations

### 26.3.6 OCILobAssign()

Assigns one LOB or `BFILE` locator to another

#### Purpose

Assigns one LOB or `BFILE` locator to another.

#### Syntax

    sword OCILobAssign ( OCIEnv                *envhp,
                         OCIError              *errhp,
                         const OCILobLocator   *src_locp,
                         OCILobLocator        **dst_locpp );

#### Parameters

envhp (IN/OUT)
OCI environment handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

src_locp (IN)
LOB or `BFILE` locator to copy from.

dst_locpp (IN/OUT)
LOB or `BFILE` locator to copy to. The caller must have allocated space for the destination locator by calling `OCIDescriptorAlloc()`.

#### Comments

Assign source locator to destination locator. After the assignment, both locators refer to the same LOB value. For internal LOBs, the source locator's LOB value gets copied to the destination locator's LOB value only when the destination locator gets stored in the table. Therefore, issuing a flush of the object containing the destination locator copies the LOB value.

`OCILobAssign()` throws an error when a remote locator is passed to it.

`OCILobAssign()` cannot be used for temporary LOBs; it generates an `OCI_INVALID_HANDLE` error. For temporary LOBs, use `OCILobLocatorAssign()`.

For `BFILE`s, only the locator that refers to the file is copied to the table. The operating system file itself is not copied.

It is an error to assign a `BFILE` locator to an internal LOB locator, and vice versa.

If the source locator is for an internal LOB that was enabled for buffering, and the source locator has been used to modify the LOB data through the LOB buffering subsystem, and the buffers have not been flushed since the write, then the source locator may not be assigned to the destination locator. This is because only one locator for each LOB can modify the LOB data through the LOB buffering subsystem.

The value of the input destination locator must have been allocated with a call to `OCIDescriptorAlloc()`. For example, assume the following declarations:

    OCILobLocator     *source_loc = (OCILobLocator *) 0;
    OCILobLocator     *dest_loc = (OCILobLocator *) 0;

The following code example shows how an application could allocate the `source_loc` locator.

Allocating a source_loc Source Locator

    if (OCIDescriptorAlloc((void  *) envhp, (void  **) &source_loc,
        (ub4) OCI_DTYPE_LOB, (size_t) 0, (void  **) 0))
        handle_error;

Assume that it then selects a LOB from a table into the `source_loc` to initialize it. The application must allocate the destination locator, `dest_loc`, before issuing the `OCILobAssign()` call to assign the value of `source_loc` to `dest_loc`, as shown in the following code example.

Allocating a dest_loc Destination Locator

    if (OCIDescriptorAlloc((void  *) envhp, (void  **) &dest_loc,
        (ub4)OCI_DTYPE_LOB, (size_t) 0, (void  **) 0))
        handle_error;
    if (OCILobAssign(envhp, errhp, source_loc, &dest_loc))
        handle_error

**Related Topics**

- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)
- OCILobIsEqual()
- OCILobLocatorAssign()
- OCILobLocatorIsInit()
- [OCILobEnableBuffering()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.7 OCILobCharSetForm()

Gets the character set form of the LOB locator, if any.

#### Purpose

Gets the character set form of the LOB locator, if any.

#### Syntax

    sword OCILobCharSetForm ( OCIEnv                *envhp,
                              OCIError              *errhp,
                              const OCILobLocator   *locp,
                              ub1                   *csfrm );

#### Parameters

envhp (IN/OUT)
OCI environment handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN)
LOB locator for which to get the character set form.

csfrm (OUT)
Character set form of the input LOB locator. If the input locator, `locp,` is for a `BLOB` or a `BFILE`,` csfrm `is set to 0 because there is no concept of a character set for binary LOBs and `BFILE`s. The caller must allocate space for `csfrm` (a`ub1`).

The `csfrm` parameter has two possible nonzero values:

- `SQLCS_IMPLICIT` - Database character set ID, the default

- `SQLCS_NCHAR` - NCHAR character set ID

#### Comments

Returns the character set form of the input `CLOB` or `NCLOB` locator in the `csfrm `output parameter.

**Related Topics**

- OCILobCharSetId()
- OCILobLocatorIsInit()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.8 OCILobCharSetId()

Gets the LOB locator's database character set ID of the LOB locator, if any.

#### Purpose

Gets the LOB locator's database character set ID of the LOB locator, if any.

#### Syntax

    sword OCILobCharSetId ( OCIEnv                  *envhp,
                            OCIError                *errhp,
                            const OCILobLocator     *locp,
                            ub2                     *csid );

#### Parameters

envhp (IN/OUT)
OCI environment handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN)
LOB locator for which to get the character set ID.

csid (OUT)
Database character set ID of the input LOB locator. If the input locator is for a `BLOB` or a `BFILE`, `csid` is set to 0 because there is no concept of a character set for binary LOBs or binary files. The caller must allocate space for the `csid` `ub2`.

#### Comments

Returns the character set ID of the input `CLOB` or `NCLOB` locator in the `csid` output parameter.

**Related Topics**

- OCILobCharSetForm()
- OCILobLocatorIsInit()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.9 OCILobClose()

Closes a previously opened LOB or `BFILE`.

#### Purpose

Closes a previously opened LOB or `BFILE`.

#### Syntax

    sword OCILobClose ( OCISvcCtx      *svchp,
                        OCIError       *errhp,
                        OCILobLocator  *locp );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
The LOB to close. The locator can refer to an internal or external LOB.

#### Comments

Closes a previously opened internal or external LOB. No error is returned if the `BFILE` exists but is not opened. An error is returned if the internal LOB is not open.

Closing a LOB requires a round-trip to the server for both internal and external LOBs. For internal LOBs, close triggers other code that relies on the close call and for external LOBs (`BFILEs`), close actually closes the server-side operating system file.

It is not mandatory that you wrap all LOB operations inside the open or close calls. However, if you open a LOB, then you must close it before you commit your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column. It is an error to commit the transaction before closing all opened LOBs that were opened by the transaction.

When the error is returned, the LOB is no longer marked as open, but the transaction is successfully committed. Hence, all the changes made to the LOB and non-LOB data in the transaction are committed, but the domain and function-based indexing are not updated. If this happens, rebuild your functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance, so if you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- OCILobOpen()
- OCILobIsOpen()
- [OCIErrorGet()](miscellaneous-functions.md)
- [Functions for Opening and Closing LOBs](lobs-and-bfile-operations.md)

### 26.3.10 OCILobCopy2()

Copies all or a portion of a LOB value into another LOB value.

#### Purpose

Copies all or a portion of a LOB value into another LOB value. This function must be used for LOBs of size greater than 4 GB. You can also use this function for LOBs smaller than 4 GB.

#### Syntax

    sword OCILobCopy2 ( OCISvcCtx        *svchp,
                        OCIError         *errhp,
                        OCILobLocator    *dst_locp,
                        OCILobLocator    *src_locp,
                        oraub8            amount,
                        oraub8            dst_offset,
                        oraub8            src_offset );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

dst_locp (IN/OUT)
An internal LOB locator uniquely referencing the destination LOB. This locator must have been a locator that was obtained from the server specified by `svchp`.

src_locp (IN)
An internal LOB locator uniquely referencing the source LOB. This locator must have been a locator that was obtained from the server specified by `svchp`.

amount (IN)
The number of characters for `CLOB`s or `NCLOB`s or the number of bytes for `BLOB`s to be copied from the source LOB to the destination LOB. The maximum value accepted by this parameter is `UB8MAXVAL` (18446744073709551615). Specifying `UB8MAXVAL` also indicates that the entire source LOB will be copied to the destination LOB using the specified source and destination offsets.

dst_offset (IN)
This is the absolute offset for the destination LOB. For character LOBs, it is the number of characters from the beginning of the LOB at which to begin writing. For binary LOBs, it is the number of bytes from the beginning of the LOB from which to begin writing. The offset starts at 1.

src_offset (IN)
This is the absolute offset for the source LOB. For character LOBs, it is the number of characters from the beginning of the LOB. For binary LOBs, it is the number of bytes. Starts at 1.

#### Comments

Copies all or a portion of an internal LOB value into another internal LOB as specified. The data is copied from the source to the destination. The source (`src_locp`) and the destination (`dst_locp`) LOBs must exist.

Copying a complete SecureFile in a column or partition with deduplicate enabled, to a LOB in the same column or partition, causes the copy to be deduplicated.

If the data exists at the destination's start position, it is overwritten with the source data. If the destination's start position is beyond the end of the current data, zero-byte fillers (for `BLOBs`) or spaces (for `CLOBs`) are written into the destination LOB from the end of the current data to the beginning of the newly written data from the source. The destination LOB is extended to accommodate the newly written data if it extends beyond the current length of the destination LOB. It is an error to extend the destination LOB beyond the maximum length allowed (that is, 4 gigabytes) or to try to copy from a `NULL` LOB. Use OCILobCopy2() for LOBs of size greater than 4 GB.

Both the source and the destination LOB locators must be of the same type (that is, they must both be `BLOBs` or both be `CLOBs`). LOB buffering must not be enabled for either locator.

This function does not accept a `BFILE` locator as the source or the destination.

It is not mandatory that you wrap this LOB operation inside the open or close calls. If you did not open the LOB before performing this operation, then the functional and domain indexes on the LOB column are updated during this call. However, if you did open the LOB before performing this operation, then you must close it before you commit your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance. If you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Note:**

You can call OCILobGetLength2() to determine the length of the source LOB.

**Related Topics**

- OCILobRead2()
- OCILobAppend()
- OCILobWrite2()
- OCILobWriteAppend2()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.11 OCILobCreateTemporary()

Creates a temporary LOB.

#### Purpose

Creates a temporary LOB.

#### Syntax

    sword OCILobCreateTemporary(OCISvcCtx          *svchp,
                                OCIError           *errhp,
                                OCILobLocator      *locp,
                                ub2                 csid,
                                ub1                 csfrm,
                                ub1                 lobtype,
                                boolean             cache,
                                OCIDuration         duration);

#### Parameters

svchp (IN)
The OCI service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
A locator that points to the temporary LOB. You must allocate the locator using `OCIDescriptorAlloc()` before passing it to this function. It does not matter whether this locator points to a LOB; the temporary LOB gets overwritten either way.

csid (IN)
The LOB character set ID. For Oracle8i or later, pass as `OCI_DEFAULT`.

csfrm (IN)
The LOB character set form of the buffer data. The `csfrm` parameter has two possible nonzero values:

- `SQLCS_IMPLICIT` - Database character set ID, to create a `CLOB`. `OCI_DEFAULT` can also be used to implicitly create a `CLOB`.

- `SQLCS_NCHAR` - `NCHAR` character set ID, to create an `NCLOB`.

The default value is `SQLCS_IMPLICIT`.

lobtype (IN)
The type of LOB to create. Valid values include:

- `OCI_TEMP_BLOB` - For a temporary `BLOB`

- `OCI_TEMP_CLOB` - For a temporary `CLOB` or `NCLOB`

cache (IN)
Pass `TRUE` if the temporary LOB should be read into the cache; pass `FALSE` if it should not. The default is `FALSE` for `NOCACHE` functionality.

duration (IN)
The duration of the temporary LOB. The following are valid values:

- `OCI_DURATION_SESSION`

- `OCI_DURATION_CALL`

#### Comments

This function creates a temporary LOB and its corresponding index in the user's temporary tablespace.

When this function is complete, the `locp` parameter points to an empty temporary LOB whose length is zero.

The lifetime of the temporary LOB is determined by the `duration` parameter. At the end of its duration the temporary LOB is freed. An application can free a temporary LOB sooner with the `OCILobFreeTemporary()` call.

If the LOB is a `BLOB`, the `csid` and `csfrm` parameters are ignored.

**Related Topics**

- OCILobFreeTemporary()
- OCILobIsTemporary()
- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Temporary LOB Support](lobs-and-bfile-operations.md) for more information about temporary LOBs and their durations

### 26.3.12 OCILobErase2()

Erases a specified portion of the internal LOB data starting at a specified offset.

#### Purpose

Erases a specified portion of the internal LOB data starting at a specified offset. This function must be used for LOBs of size greater than 4 GB. You can also use this function for LOBs smaller than 4 GB.

#### Syntax

    sword OCILobErase2 ( OCISvcCtx       *svchp,
                         OCIError        *errhp,
                         OCILobLocator   *locp,
                         oraub8          *amount,
                         oraub8           offset );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
An internal LOB locator that uniquely references the LOB. This locator must have been a locator that was obtained from the server specified by `svchp`.

amount (IN/OUT)
The number of characters for `CLOB`s or `NCLOB`s, or bytes for `BLOB`s, to erase. On IN, the value signifies the number of characters or bytes to erase. On OUT, the value identifies the actual number of characters or bytes erased.

offset (IN)
Absolute offset in characters for `CLOB`s or `NCLOB`s, or bytes for `BLOB`s, from the beginning of the LOB value from which to start erasing data. Starts at 1.

#### Comments

The actual number of characters or bytes erased is returned. For `BLOB`s, erasing means that zero-byte fillers overwrite the existing LOB value. For `CLOB`s, erasing means that spaces overwrite the existing LOB value.

This function is valid only for internal LOBs; `BFILE`s are not allowed.

It is not mandatory that you wrap this LOB operation inside the open or close calls. If you did not open the LOB before performing this operation, then the functional and domain indexes on the LOB column are updated during this call. However, if you did open the LOB before performing this operation, then you must close it before you commit your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance. If you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- OCILobRead2()
- OCILobAppend()
- OCILobCopy2()
- OCILobWrite2()
- OCILobWriteAppend2()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.13 OCILobFileClose()

Closes a previously opened `BFILE`.

#### Purpose

Closes a previously opened `BFILE`.

#### Syntax

    sword OCILobFileClose ( OCISvcCtx            *svchp,
                            OCIError             *errhp,
                            OCILobLocator        *filep );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

filep (IN/OUT)
A pointer to a `BFILE` locator that refers to the `BFILE` to be closed.

#### Comments

Closes a previously opened `BFILE`. It is an error if this function is called for an internal LOB. No error is returned if the `BFILE` exists but is not opened.

This function is only meaningful the first time it is called for a particular `BFILE` locator. Subsequent calls to this function using the same `BFILE` locator have no effect.

**Related Topics**

- OCILobClose()
- OCILobFileCloseAll()
- OCILobFileExists()
- OCILobFileIsOpen()
- OCILobFileOpen()
- OCILobOpen()
- OCILobIsOpen()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-APIs-for-BFILE-operations.md) for a description of `BFILE`s

### 26.3.14 OCILobFileCloseAll()

Closes all open `BFILE`s on a given service context.

#### Purpose

Closes all open `BFILE`s on a given service context.

#### Syntax

    sword OCILobFileCLoseAll ( OCISvcCtx   *svchp,
                               OCIError    *errhp );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

Closes all open `BFILE`s on a given service context.

**Related Topics**

- OCILobFileClose()
- OCILobFileExists()
- OCILobFileIsOpen()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-APIs-for-BFILE-operations.md) for a description of `BFILE`s

### 26.3.15 OCILobFileExists()

Tests to see if the `BFILE` exists on the server's operating system.

#### Purpose

Tests to see if the `BFILE` exists on the server's operating system.

#### Syntax

    sword OCILobFileExists ( OCISvcCtx        *svchp,
                             OCIError         *errhp,
                             OCILobLocator    *filep,
                             boolean          *flag );

#### Parameters

svchp (IN)
The OCI service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

filep (IN)
Pointer to the `BFILE` locator that refers to the file.

flag (OUT)
Returns `TRUE` if the `BFILE` exists on the server; `FALSE` if it does not.

#### Comments

Checks to see if the `BFILE` exists on the server's file system. It is an error to call this function for an internal LOB.

**Related Topics**

- OCILobFileClose()
- OCILobFileCloseAll()
- OCILobFileIsOpen()
- OCILobOpen()
- OCILobIsOpen()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-APIs-for-BFILE-operations.md) for a description of `BFILE`s

### 26.3.16 OCILobFileGetName()

Gets the `BFILE` locator's directory object and file name.

#### Purpose

Gets the `BFILE` locator's directory object and file name.

#### Syntax

    sword OCILobFileGetName ( OCIEnv                   *envhp,
                              OCIError                 *errhp,
                              const OCILobLocator      *filep,
                              OraText                  *dir_alias,
                              ub2                      *d_length,
                              OraText                  *filename,
                              ub2                      *f_length );

#### Parameters

envhp (IN/OUT)
OCI environment handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

filep (IN)
`BFILE` locator for which to get the directory object and file name.

dir_alias (OUT)
Buffer into which the directory object name is placed. This can be in UTF-16. You must allocate enough space for the directory object name. The maximum length for the directory object is 30 bytes.

d_length (IN/OUT)
Serves the following purposes (can be in code point for Unicode, or bytes):

- IN: length of the input `dir_alias `string

- OUT: length of the returned` dir_alias `string

filename (OUT)
Buffer into which the file name is placed. You must allocate enough space for the file name. The maximum length for the file name is 255 bytes.

f_length (IN/OUT)
Serves the following purposes (in number of bytes):

- IN: length of the input `filename` buffer

- OUT: length of the returned `filename `string

#### Comments

Returns the directory object and file name associated with this `BFILE` locator. The environment handle determines whether it is in Unicode. It is an error to call this function for an internal LOB.

**Related Topics**

- OCILobFileSetName()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-APIs-for-BFILE-operations.md) for a description of `BFILE`s

### 26.3.17 OCILobFileIsOpen()

Tests to see if the `BFILE` is open.

#### Purpose

Tests to see if the `BFILE` is open.

#### Syntax

    sword OCILobFileIsOpen ( OCISvcCtx        *svchp,
                             OCIError         *errhp,
                             OCILobLocator    *filep,
                             boolean          *flag );

#### Parameters

svchp (IN)
The OCI service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

filep (IN)
Pointer to the `BFILE` locator being examined.

flag (OUT)
Returns `TRUE` if the `BFILE` was opened using this particular locator; returns `FALSE` if it was not.

#### Comments

Checks to see if a file on the server was opened with the `filep` `BFILE` locator. It is an error to call this function for an internal LOB.

If the input `BFILE` locator was never passed to the `OCILobFileOpen()` or `OCILobOpen()` command, the file is considered not to be opened by this locator. However, a different locator may have the file open. Openness is associated with a particular locator.

**Related Topics**

- OCILobClose()
- OCILobFileCloseAll()
- OCILobFileExists()
- OCILobFileClose()
- OCILobFileIsOpen()
- OCILobFileOpen()
- OCILobOpen()
- OCILobIsOpen()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-APIs-for-BFILE-operations.md) for a description of `BFILE`s

### 26.3.18  OCILobFileOpen()

Opens a `BFILE` on the file system of the server for read-only access.

#### Purpose

Opens a `BFILE` on the file system of the server for read-only access.

#### Syntax

    sword OCILobFileOpen ( OCISvcCtx            *svchp,
                           OCIError             *errhp,
                           OCILobLocator        *filep,
                           ub1                   mode );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

filep (IN/OUT)
The `BFILE` to open. It is an error if the locator does not refer to a `BFILE`.

mode (IN)
Mode in which to open the file. The only valid mode is `OCI_FILE_READONLY`.

#### Comments

Opens a `BFILE` on the file system of the server. The `BFILE` can be opened for read-only access. `BFILE`s can not be written through Oracle Database. It is an error to call this function for an internal LOB.

This function is only meaningful the first time it is called for a particular `BFILE` locator. Subsequent calls to this function using the same `BFILE` locator have no effect.

**Related Topics**

- OCILobClose()
- OCILobFileCloseAll()
- OCILobFileExists()
- OCILobFileClose()
- OCILobFileIsOpen()
- OCILobFileOpen()
- OCILobOpen()
- OCILobIsOpen()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-APIs-for-BFILE-operations.md) for a description of `BFILE`s

### 26.3.19 OCILobFileSetName()

Sets the directory object and file name in the `BFILE` locator.

#### Purpose

Sets the directory object and file name in the `BFILE` locator.

#### Syntax

    sword OCILobFileSetName ( OCIEnv             *envhp,
                              OCIError           *errhp,
                              OCILobLocator     **filepp,
                              const OraText      *dir_alias,
                              ub2                 d_length,
                              const OraText      *filename,
                              ub2                 f_length );

#### Parameters

envhp (IN/OUT)
OCI environment handle. Contains the UTF-16 setting.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

filepp (IN/OUT)
Pointer to the `BFILE` locator for which to set the directory object and file name.

dir_alias (IN)
Buffer that contains the directory object name (must be in the encoding specified by the `charset` parameter of a previous call to [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md) to set in the `BFILE` locator.

d_length (IN)
Length (in bytes) of the input `dir_alias` parameter.

filename (IN)
Buffer that contains the file name (must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()` to set in the `BFILE` locator.

f_length (IN)
Length (in bytes) of the input `filename `parameter.

#### Comments

It is an error to call this function for an internal LOB.

**Related Topics**

- OCILobFileGetName()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-APIs-for-BFILE-operations.md) for a description of `BFILE`s

### 26.3.20 OCILobFreeTemporary()

Frees a temporary LOB.

#### Purpose

Frees a temporary LOB.

#### Syntax

    sword OCILobFreeTemporary( OCISvcCtx          *svchp,
                               OCIError           *errhp,
                               OCILobLocator      *locp);

#### Parameters

svchp (IN/OUT)
The OCI service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
A locator uniquely referencing the LOB to be freed.

#### Comments

This function frees the contents of the temporary LOB to which this locator points. Note that the locator itself is not freed until `OCIDescriptorFree()` is called. You must always call `OCILobFreeTemporary()` before calling `OCIDescriptorFree()` or `OCIArrayDescriptorFree()` to free the contents of the temporary LOB. See [About Freeing Temporary LOBs](lobs-and-bfile-operations.md) for more information.

This function returns an error if the LOB locator passed in the `locp` parameter does not point to a temporary LOB, possibly because the LOB locator:

- Points to a permanent LOB

- Pointed to a temporary LOB that has been freed

- Has never pointed to anything

**Related Topics**

- OCILobCreateTemporary()
- OCILobIsTemporary()
- [OCIDescriptorFree()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.21 OCILobGetChunkSize()

Gets the chunk size of a LOB.

#### Purpose

Gets the chunk size of a LOB.

#### Syntax

    sword OCILobGetChunkSize ( OCISvcCtx       *svchp,
                               OCIError        *errhp,
                               OCILobLocator   *locp,
                               ub4             *chunk_size );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
The internal LOB for which to get the usable chunk size.

chunk_size (OUT)
For LOBs with storage parameter `BASICFILE`, the amount of a chunk's space that is used to store the internal LOB value. This is the amount that users should use when reading or writing the LOB value. If possible, users should start their writes at chunk boundaries, such as the beginning of a chunk, and write a chunk at a time.

The `chunk_size` parameter is returned in terms of bytes for `BLOB`s, `CLOB`s, and `NCLOB`s.

For LOBs with storage parameter `SECUREFILE`, `chunk_size` is an advisory size and is provided for backward compatibility.

#### Comments

When creating a table that contains an internal LOB, the user can specify the chunking factor, which can be a multiple of Oracle Database blocks. This corresponds to the chunk size used by the LOB data layer when accessing and modifying the LOB value. Part of the chunk is used to store system-related information, and the rest stores the LOB value. This function returns the amount of space used in the LOB chunk to store the LOB value. Performance is improved if the application issues read or write requests using a multiple of this chunk size. For writes, there is an added benefit because LOB chunks are versioned and, if all writes are done on a chunk basis, no extra versioning is done or duplicated. Users could batch up the write until they have enough for a chunk instead of issuing several write calls for the same chunk.

**Related Topics**

- OCILobGetStorageLimit()
- OCILobRead2()
- OCILobAppend()
- OCILobCopy2()
- OCILobWrite2()
- OCILobWriteAppend2()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[About Improving LOB Read/Write Performance](lobs-and-bfile-operations.md)

### 26.3.22 OCILobGetContentType()

Gets the user-specified content type string for the data in a SecureFile, if set.

#### Purpose

Gets the user-specified content type string for the data in a SecureFile, if set.

#### Syntax

    sword OCILobGetContentType ( OCIEnv         *envhp,
                                 OCISvcCtx      *svchp,
                                 OCIError       *errhp,
                                 OCILobLocator  *lobp,
                                 oratext        *contenttypep,
                                 ub4            *contenttypelenp,
                                 ub4             mode );

#### Parameters

envhp (IN)
The environment handle.

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that can be passed to `OCIErrorGet()` for diagnostic information when there is an error.

lobp (IN)
A LOB locator that uniquely references a LOB.

contenttypep (IN/OUT)
Pointer to the buffer where the content type is stored after successful execution. You must allocate the buffer before calling this function. The size of the allocated buffer must be `>= OCI_LOB_CONTENTTYPE_MAXSIZE`.

contenttypelenp (IN/OUT)
Set this field to the size of `contenttypep` buffer. After the call successfully executes, this field holds the size of the `contenttypep` returned.

mode (IN)
For future use. Pass zero now.

#### Comments

This function only works on SecureFiles. If `lobp` is not a SecureFile, then the error `SECUREFILE_WRONGTYPE` is returned. If `lobp` is buffered, a temporary LOB, or an abstract LOB, then the error `SECUREFILE_BADLOB` is returned.

If the SecureFile does not have a `contenttype` associated with it, the `contenttype` length (`contenttypelenp`) is returned as 0 without modifying the buffer `contenttypep`.

The maximum possible size of the `ContentType` string is defined as:

    #define OCI_LOB_CONTENTTYPE_MAXSIZE 128

The `ContentType` is ASCII (that is, 1-byte/7-bit UTF8).

**Related Topics**

- OCILobSetContentType()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.23 OCILobGetLength2()

Gets the length of a LOB. This function must be used for LOBs of size greater than 4 GB.

#### Purpose

You can also use this function for LOBs smaller than 4 GB.

#### Syntax

    sword OCILobGetLength2 ( OCISvcCtx      *svchp,
                             OCIError       *errhp,
                             OCILobLocator  *locp,
                             oraub8         *lenp );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN)
A LOB locator that uniquely references the LOB. For internal LOBs, this locator must have been a locator that was obtained from the server specified by `svchp`. For `BFILE`s, the locator can be set by `OCILobFileSetName()`, by a `SELECT` statement, or by `OCIObjectPin()`.

lenp (OUT)
On output, it is the length of the LOB if the LOB is not `NULL`. For character LOBs, it is the number of characters; for binary LOBs and `BFILE`s, it is the number of bytes in the LOB.

#### Comments

Gets the length of a LOB. If the LOB is `NULL`, the length is undefined. The length of a `BFILE` includes the EOF, if it exists. The length of an empty internal LOB is zero.

Regardless of whether the client-side character set is varying-width, the output length is in characters for `CLOB`s and `NCLOB`s, and in bytes for `BLOB`s and `BFILE`s.

**Note:**

Any zero-byte or space fillers in the LOB written by previous calls to `OCILobErase2()` or `OCILobWrite2()` are also included in the length count.

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- OCILobFileSetName()
- OCILobRead2()
- OCILobWrite2()
- OCILobCopy2()
- OCILobAppend()
- OCILobLoadFromFile2()
- OCILobWriteAppend2()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.24 OCILobGetOptions()

Obtains the enabled settings corresponding to the given input option types for a given SecureFile LOB.

#### Purpose

Obtains the enabled settings corresponding to the given input option types for a given SecureFile LOB.

#### Syntax

    sword OCILobGetOptions ( OCISvcCtx         *svchp,
                             OCIError          *errhp,
                             OCILobLocator     *locp,
                             ub4                option_types,
                             void              *optionsp,
                             ub4                optionslenp,
                             ub4                mode );

#### Parameters

svchp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
The LOB locator or `BFILE` locator that uniquely references the LOB or `BFILE`. This locator must have been obtained from the server specified by `svchp`.

option_types (IN)
The given option types that can be combined by a bit-wise inclusive `OR` (symbol "\|"):

- Compression - `OCI_LOB_OPT_COMPRESS`

- Encryption - `OCI_LOB_OPT_ENCRYPT`

- Deduplication - `OCI_LOB_OPT_DEDUPLICATE`

optionsp (OUT)
The current settings for each of the option types given. Possible values are:

- `OCI_LOB_OPT_COMPRESS_ON`

- `OCI_LOB_OPT_ENCRYPT_ON`

- `OCI_LOB_OPT_DEDUPLICATE_ON`

optionslenp (OUT)
The length of the value in `optionsp`.

mode (IN)
Reserved for future use. Pass in 0.

#### Comments

You can only specify option types that have been enabled on the column. An error is returned when an attempt is made to get the value of an option type that is not enabled on the column. For example, if you have a LOB column with compression enabled, and you call `OCILobGetOptions()` with `OCI_LOB_OPT_ENCRYPT` set in the `option_types` parameter, an error occurs.

Note that the returned value is a `ub4` pointer cast as a `void` pointer to allow for future expansion of option types and values. The `optionslenp` returned should be equal to `sizeof(ub4)`.

**Related Topics**

- OCILobSetOptions()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.25 OCILobGetStorageLimit()

Gets the maximum length of an internal LOB (`BLOB`, `CLOB`, or `NCLOB`) in bytes.

#### Purpose

Gets the maximum length of an internal LOB (`BLOB`, `CLOB`, or `NCLOB`) in bytes.

#### Syntax

    sword OCILobGetStorageLimit ( OCISvcCtx      *svchp,
                                  OCIError       *errhp,
                                  OCILobLocator  *locp,
                                  oraub8         *limitp );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN)
A LOB locator that uniquely references the LOB. The locator must have been one that was obtained from the server specified by `svchp`.

limitp (OUT)
The maximum length of the LOB (in bytes) that can be stored in the database.

#### Comments

Because block size ranges from 2 KB to 32 KB, the maximum LOB size ranges from 8 terabytes to 128 terabytes (TB) for LOBs.

**Related Topics**

- OCILobGetChunkSize()
- [OCIErrorGet()](miscellaneous-functions.md)
- [About Using LOBs of Size Greater than 4 GB](lobs-and-bfile-operations.md)

### 26.3.26 OCILobIsEqual()

Compares two LOB or `BFILE` locators for equality.

#### Purpose

Compares two LOB or `BFILE` locators for equality.

#### Syntax

    sword OCILobIsEqual ( OCIEnv                  *envhp,
                          const OCILobLocator     *x,
                          const OCILobLocator     *y,
                          boolean                 *is_equal );

#### Parameters

envhp (IN)
The OCI environment handle.

x (IN)
LOB locator to compare.

y (IN)
LOB locator to compare.

is_equal (OUT)
`TRUE`, if the LOB locators are equal; `FALSE` if they are not.

#### Comments

Compares the given LOB or `BFILE` locators for equality. Two LOB or `BFILE` locators are equal if and only if they both refer to the same LOB or `BFILE` value.

Two `NULL` locators are considered not equal by this function.

**Related Topics**

- OCILobAssign()
- OCILobLocatorIsInit()

### 26.3.27 OCILobIsOpen()

Tests whether a LOB or `BFILE` is open.

#### Purpose

Tests whether a LOB or `BFILE` is open.

#### Syntax

    sword OCILobIsOpen ( OCISvcCtx        *svchp,
                         OCIError         *errhp,
                         OCILobLocator    *locp,
                         boolean          *flag );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that can be passed to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN)
Pointer to the LOB locator being examined. The locator can refer to an internal or external LOB.

flag (OUT)
Returns `TRUE` if the internal LOB is open or if the `BFILE` was opened using the input locator. Returns `FALSE` if it was not.

#### Comments

Checks to see if the internal LOB is open or if the `BFILE` was opened using the input locator.

For BFILEs
If the input `BFILE` locator was never passed to `OCILobOpen()` or `OCILobFileOpen()`, the `BFILE` is considered not to be opened by this `BFILE` locator. However, a different `BFILE` locator may have opened the `BFILE`. Multiple opens can be performed on the same `BFILE` using different locators. In other words, openness is associated with a specific locator for `BFILEs`.

For internal LOBs
Openness is associated with the LOB, not with the locator. If `locator1` opened the LOB, then `locator2` also sees the LOB as open.

For internal LOBs, this call requires a server round-trip because it checks the state on the server to see if the LOB is open. For external LOBs (`BFILEs`), this call also requires a round-trip because the operating system file on the server side must be checked to see if it is open.

**Related Topics**

- OCILobClose()
- OCILobFileCloseAll()
- OCILobFileExists()
- OCILobFileClose()
- OCILobFileIsOpen()
- OCILobFileOpen()
- OCILobOpen()
- [OCIErrorGet()](miscellaneous-functions.md)
- [Functions for Opening and Closing LOBs](lobs-and-bfile-operations.md)

### 26.3.28 OCILobIsTemporary()

Tests if a locator points to a temporary LOB.

#### Purpose

Tests if a locator points to a temporary LOB.

#### Syntax

    sword OCILobIsTemporary(OCIEnv            *envhp,
                            OCIError          *errhp,
                            OCILobLocator     *locp,
                            boolean           *is_temporary);

#### Parameters

envhp (IN)
The OCI environment handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN)
The locator to test.

is_temporary (OUT)
Returns `TRUE` if the LOB locator points to a temporary LOB; `FALSE` if it does not.

#### Comments

This function tests a locator to determine if it points to a temporary LOB. If so, `is_temporary` is set to `TRUE`. If not, `is_temporary` is set to `FALSE`.

**Related Topics**

- OCILobCreateTemporary()
- OCILobFreeTemporary()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.29 OCILobLoadFromFile2()

Loads and copies all or a portion of the file into an internal LOB. This function must be used for LOBs of size greater than 4 GB.

#### Purpose

You can also use this function for LOBs smaller than 4 GB.

#### Syntax

    sword OCILobLoadFromFile2 ( OCISvcCtx        *svchp,
                                OCIError         *errhp,
                                OCILobLocator    *dst_locp,
                                OCILobLocator    *src_locp,
                                oraub8            amount,
                                oraub8            dst_offset,
                                oraub8            src_offset );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

dst_locp (IN/OUT)
A locator uniquely referencing the destination internal LOB, that may be of type `BLOB`, `CLOB`, or `NCLOB`.

src_locp (IN/OUT)
A locator uniquely referencing the source `BFILE`.

amount (IN)
The number of bytes to be loaded.

dst_offset (IN)
This is the absolute offset for the destination LOB. For character LOBs, it is the number of characters from the beginning of the LOB at which to begin writing. For binary LOBs, it is the number of bytes from the beginning of the LOB from which to begin reading. The offset starts at 1.

src_offset (IN)
This is the absolute offset for the source `BFILE`. It is the number of bytes from the beginning of the `BFILE`. The offset starts at 1.

#### Comments

Loads and copies a portion or all of a `BFILE` value into an internal LOB as specified. The data is copied from the source `BFILE` to the destination internal LOB (`BLOB` or `CLOB`). No character set conversions are performed when copying the `BFILE` data to a `CLOB` or `NCLOB`. Also, when binary data is loaded into a `BLOB`, no character set conversions are performed. Therefore, the `BFILE` data must be in the same character set as the LOB in the database. No error checking is performed to verify this.

`OCILobLoadFromFile2()` throws an error when a remote locator is passed to it.

The source (`src_locp`) and the destination (`dst_locp`) LOBs must exist. If the data exists at the destination's start position, it is overwritten with the source data. If the destination's start position is beyond the end of the current data, zero-byte fillers (for `BLOB`s) or spaces (for `CLOB`s) are written into the destination LOB from the end of the data to the beginning of the newly written data from the source. The destination LOB is extended to accommodate the newly written data if it extends beyond the current length of the destination LOB.

It is an error to extend the destination LOB beyond the maximum length allowed (4 gigabytes) (see `OCILobLoadFromFile2()` to use for LOBs of size greater than 4 GB) or to try to copy from a NULL `BFILE`.

It is not mandatory that you wrap this LOB operation inside the open or close calls. If you did not open the LOB before performing this operation, then the functional and domain indexes on the LOB column are updated during this call. However, if you did open the LOB before performing this operation, then you must close it before you commit your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance. If you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- OCILobAppend()
- OCILobWrite2()
- OCILobTrim2()
- OCILobCopy2()
- OCILobGetLength2()
- OCILobWriteAppend2()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.30 OCILobLocatorAssign()

Assigns one LOB or `BFILE` locator to another.

#### Purpose

Assigns one LOB or `BFILE` locator to another.

#### Syntax

    sword OCILobLocatorAssign ( OCISvcCtx              *svchp,
                                OCIError               *errhp,
                                const OCILobLocator    *src_locp,
                                OCILobLocator         **dst_locpp );

#### Parameters

svchp (IN/OUT)
The OCI service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

src_locp (IN)
The LOB or `BFILE` locator to copy from.

dst_locpp (IN/OUT)
The LOB or `BFILE` locator to copy to. The caller must allocate space for the `OCILobLocator` by calling `OCIDescriptorAlloc()`.

#### Comments

This call assigns the source locator to the destination locator. After the assignment, both locators refer to the same LOB data. For internal LOBs, the source locator's LOB data gets copied to the destination locator's LOB data only when the destination locator gets stored in the table. Therefore, issuing a flush of the object containing the destination locator copies the LOB data. For `BFILE`s, only the locator that refers to the operating system file is copied to the table; the operating system file is not copied.

`OCILobLocatorAssign()` throws an error when a remote locator is passed to it.

Note that this call is similar to `OCILobAssign()`, but `OCILobLocatorAssign()` takes an OCI service handle pointer instead of an OCI environment handle pointer. Also, `OCILobLocatorAssign()` can be used for temporary LOBs, but `OCILobAssign()` cannot be used for temporary LOBs.

**Note:**

If the `OCILobLocatorAssign()` function fails, the target locator is not restored to its previous state. The target locator should not be used in subsequent operations unless it is reinitialized.

If the destination locator is for a temporary LOB, the destination temporary LOB is freed before the source LOB locator is assigned to it.

If the source LOB locator refers to a temporary LOB, the destination is made into a temporary LOB too. The source and the destination are conceptually different temporary LOBs. In the `OCI_DEFAULT` mode, the source temporary LOB is deep copied, and a destination locator is created to refer to the new deep copy of the temporary LOB. Hence `OCILobIsEqual()` returns `FALSE` after the `OCILobLocatorAssign()` call. However, in the `OCI_OBJECT` mode, an optimization is made to minimize the number of deep copies, so the source and destination locators point to the same LOB until any modification is made through either LOB locator. Hence `OCILobIsEqual()` returns `TRUE` right after `OCILobLocatorAssign()` until the first modification. In both these cases, after the `OCILobLocatorAssign()`, any changes to the source or the destination do not reflect in the other (that is, destination or source) LOB. If you want the source and the destination to point to the same LOB and want your changes to reflect in the other, then you must use the equal sign to ensure that the two LOB locator pointers refer to the same LOB locator.

**Related Topics**

- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)
- OCILobAssign()
- OCILobIsEqual()
- OCILobLocatorIsInit()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.31 OCILobLocatorIsInit()

Tests to see if a given LOB or `BFILE` locator is initialized.

#### Purpose

Tests to see if a given LOB or `BFILE` locator is initialized.

#### Syntax

    sword OCILobLocatorIsInit ( OCIEnv               *envhp,
                                OCIError             *errhp,
                                const OCILobLocator  *locp,
                                boolean              *is_initialized );

#### Parameters

envhp (IN/OUT)
OCI environment handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN)
The LOB or `BFILE` locator being tested.

is_initialized (OUT)
Returns `TRUE` if the given LOB or `BFILE` locator is initialized; returns `FALSE` if it is not.

#### Comments

Tests to see if a given LOB or `BFILE` locator is initialized.

Internal LOB locators can be initialized by one of these methods:

- Selecting a non-`NULL` LOB into the locator

- Pinning an object that contains a non-`NULL` LOB attribute by `OCIObjectPin()`

- Setting the locator to empty by `OCIAttrSet()`

  **See Also:**

  [LOB Descriptor and LOB Locator Attributes](handle-and-descriptor-attributes.md)

`BFILE` locators can be initialized by one of these methods:

- Selecting a non-`NULL` `BFILE` into the locator

- Pinning an object that contains a non-`NULL` `BFILE` attribute by `OCIObjectPin()`

- Calling OCILobFileSetName()

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- OCILobIsEqual()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.32 OCILobOpen()

Opens a LOB, internal or external, in the indicated mode.

#### Purpose

Opens a LOB, internal or external, in the indicated mode.

#### Syntax

    sword OCILobOpen ( OCISvcCtx        *svchp,
                       OCIError         *errhp,
                       OCILobLocator    *locp,
                       ub1               mode );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
The LOB to open. The locator can refer to an internal or external LOB.

mode (IN)
The mode in which to open the LOB or `BFILE`. In Oracle8i or later, valid modes for LOBs are `OCI_LOB_READONLY` and `OCI_LOB_READWRITE`. Note that `OCI_FILE_READONLY` exists as input to `OCILobFileOpen()`. `OCI_FILE_READONLY` can be used with `OCILobOpen()` if the input locator is for a `BFILE`.

#### Comments

It is an error to open the same LOB twice. `BFILE`s cannot be opened in read/write mode. If a user tries to write to a LOB or `BFILE` that was opened in read-only mode, an error is returned.

Opening a LOB requires a round-trip to the server for both internal and external LOBs. For internal LOBs, the open triggers other code that relies on the open call. For external LOBs (`BFILE`s), open requires a round-trip because the actual operating system file on the server side is being opened.

It is not necessary to open a LOB to perform operations on it. When using function-based indexes, extensible indexes or context, and making multiple calls to update or write to the LOB, you should first call `OCILobOpen()`, then update the LOB as many times as you want, and finally call `OCILobClose()`. This sequence of operations ensures that the indexes are only updated once at the end of all the write operations instead of once for each write operation.

It is not mandatory that you wrap all LOB operations inside the open and close calls. However, if you open a LOB, then you must close it before you commit your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column. It is an error to commit the transaction before closing all opened LOBs that were opened by the transaction.

When the error is returned, the LOB is no longer marked as open, but the transaction is successfully committed. Hence, all the changes made to the LOB and non-LOB data in the transaction are committed, but the domain and function-based indexing are not updated. If this happens, rebuild your functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance, so if you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- OCILobClose()
- OCILobFileCloseAll()
- OCILobFileExists()
- OCILobFileClose()
- OCILobFileIsOpen()
- OCILobFileOpen()
- OCILobIsOpen()
- [OCIErrorGet()](miscellaneous-functions.md)
- [Functions for Opening and Closing LOBs](lobs-and-bfile-operations.md)

### 26.3.33 OCILobRead2()

Reads a portion of a LOB or `BFILE`, as specified by the call, into a buffer. This function must be used for LOBs of size greater than 4 GB.

#### Purpose

You can also use this function for LOBs smaller than 4 GB.

#### Syntax

    sword OCILobRead2 ( OCISvcCtx           *svchp,
                        OCIError            *errhp,
                        OCILobLocator       *locp,
                        oraub8              *byte_amtp,
                        oraub8              *char_amtp,
                        oraub8               offset,
                        void                *bufp,
                        oraub8               bufl,
                        ub1                  piece,
                        void                *ctxp,
                        OCICallbackLobRead2 (cbfp)
                                            ( void          *ctxp,
                                              const void    *bufp,
                                              oraub8         lenp,
                                              ub1            piecep
                                              void         **changed_bufpp,
                                              oraub8        *changed_lenp
                                            )
                        ub2                  csid,
                        ub1                  csfrm );

#### Parameters

svchp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN)
A LOB or `BFILE` locator that uniquely references the LOB or `BFILE`. This locator must have been a locator that was obtained from the server specified by `svchp`.

byte_amtp (IN/OUT)
IN - The number of bytes to read from the database. Used for `BLOB` and `BFILE` always. For `CLOB` and `NCLOB`, it is used only when `char_amtp` is zero.

OUT - The number of bytes read into the user buffer.

char_amtp (IN/OUT)
IN - The maximum number of characters to read into the user buffer. Ignored for `BLOB` and `BFILE`.

OUT - The number of characters read into the user buffer. Undefined for `BLOB` and `BFILE`.

offset (IN)
On input, this is the absolute offset from the beginning of the LOB value. For character LOBs (`CLOB`s, `NCLOB`s), it is the number of characters from the beginning of the LOB; for binary LOBs or `BFILE`s, it is the number of bytes. The first position is 1.

If you use streaming (by polling or a callback), specify the offset in the first call; in subsequent polling calls, the offset parameter is ignored. When you use a callback, there is no offset parameter.

bufp (IN/OUT)
The pointer to a buffer into which the piece is read. The length of the allocated memory is assumed to be `bufl`.

bufl (IN)
The length of the buffer in octets. This value differs from the `amtp` value for `CLOB`s and for `NCLOB`s (`csfrm`=`SQLCS_NCHAR`) when the `amtp` parameter is specified in terms of characters, and the `bufl` parameter is specified in terms of bytes.

piece (IN)
`OCI_ONE_PIECE` - The call never assumes polling. If the amount indicated is more than the buffer length, then the buffer is filled as much as possible.

For polling, pass `OCI_FIRST_PIECE` the first time and `OCI_NEXT_PIECE` in subsequent calls. `OCI_FIRST_PIECE` should be passed while using the callback.

ctxp (IN)
The context pointer for the callback function. Can be `NULL`.

cbfp (IN)
A callback that can be registered to be called for each piece. If this is `NULL`, then `OCI_NEED_DATA` is returned for each piece.

The callback function must return `OCI_CONTINUE` for the read to continue. If any other error code is returned, the LOB read is terminated.

ctxp (IN)
The context for the callback function. Can be `NULL`.

bufp (IN/OUT)
A buffer pointer for the piece.

lenp (IN)
The length in bytes of the current piece in `bufp`.

piecep (IN)
Which piece: `OCI_FIRST_PIECE`, `OCI_NEXT_PIECE`, or `OCI_LAST_PIECE`.

changed_bufpp (OUT)
The callback function can put the address of a new buffer if it prefers to use a new buffer for the next piece to read. The default old buffer `bufp` is used if this parameter is set to `NULL`.

changed_lenp (OUT)
Length of the new buffer, if provided.

<!-- -->

csid (IN)
The character set ID of the buffer data. If this value is 0, then `csid` is set to the client's `NLS_LANG` or `NLS_CHAR` value, depending on the value of `csfrm`. It is never assumed to be the server character set, unless the server and client have the same settings.

csfrm (IN)
The character set form of the buffer data. The `csfrm` parameter must be consistent with the type of the LOB.

The `csfrm` parameter has two possible nonzero values:

- `SQLCS_IMPLICIT` - Database character set ID

- `SQLCS_NCHAR` - NCHAR character set ID

The default value is `SQLCS_IMPLICIT`. If `csfrm` is not specified, the default is assumed.

#### Comments

Reads a portion of a LOB or `BFILE` as specified by the call into a buffer. It is an error to try to read from a `NULL` LOB or `BFILE`.

**Note:**

When you read or write LOBs, specify a character set form (`csfrm`) that matches the form of the locator itself.

For `BFILE`s, the operating system file must exist on the server, and it must have been opened by `OCILobFileOpen()` or `OCILobOpen()` using the input locator. Oracle Database must have permission to read the operating system file, and the user must have read permission on the directory object.

When you use the polling mode for `OCILobRead2()`, the first call must specify values for `offset` and `amtp`, but on subsequent polling calls to `OCILobRead2()`, you need not specify these values.

If the LOB is a `BLOB`, the `csid` and `csfrm` parameters are ignored.

**Note:**

To terminate an `OCILobRead2()` operation and free the statement handle, use the `OCIBreak()` call.

The following points apply to reading LOB data in streaming mode:

- When you use polling mode, be sure to specify the `char_amtp` and `byte_amtp` and offset parameters only in the first call to `OCILobRead2()`. On subsequent polling calls these parameters are ignored. If both `byte_amtp` and `char_amtp` are set to point to zero and `OCI_FIRST_PIECE` is passed, then polling mode is assumed and data is read till the end of the LOB. On output, `byte_amtp` gives the number of bytes read in the current piece.

  For `CLOB`s and `NCLOB`s, `char_amtp` gives the number of characters read in the current piece.

  For `CLOB`s and `NCLOB`s, if you do not pass `char_amtp`, then `char_amtp` is calculated internally as `byte_amtp`/`max char width`, so if `max char width` is 4, `char_amtp` is calculated as `byte_amtp`/4. Thus, `OCILobRead2()` does not calculate how many bytes are required for each character. Instead, `OCILobRead2()` fetches in the worst case the number of characters that can fit in `byte_amtp`. To fill the buffer, check the `byte_amtp` parameter to see how much of the buffer is filled, then call `OCILobRead2()` again to fetch the remaining bytes.

- When you use callbacks, the `len` parameter, which is input to the callback, indicates how many bytes are filled in the buffer. Check the `len` parameter during your callback processing, because the entire buffer cannot be filled with data.

- When you use polling, look at the `byte_amtp` parameter to see how much the buffer is filled for the current piece. For `CLOB`s and `NCLOB`s, `char_amtp` returns the number of characters read in the buffer as well.

To read data in UTF-16 format, set the `csid` parameter to `OCI_UTF16ID`. If the c`sid` parameter is set, it overrides the `NLS_LANG` environment variable.

**Related Topics**

- OCILobFileOpen()
- OCILobOpen()
- [OCIBreak()](miscellaneous-functions.md)
- OCILobWrite2()
- OCILobFileSetName()
- OCILobWriteAppend2()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

- [PL/SQL REF CURSORs and Nested Tables in OCI](binding-and-defining-in-oci.md) for additional information about Unicode format

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-APIs-for-BFILE-operations.md) for a description of `BFILE`s

- The demonstration programs included with your Oracle Database installation for a code sample showing the use of LOB reads and writes.

- [OCI Demonstration Programs](oci-demo-programs.md)

- [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for general information about piecewise OCI operations

- [Polling Mode Operations in OCI](oci-programming-basics.md)

### 26.3.34 OCILobSetContentType()

Sets a content type string for the data in the SecureFile to something that can be used by an application.

#### Purpose

Sets a content type string for the data in the SecureFile to something that can be used by an application.

#### Syntax

    sword OCILobSetContentType ( OCIEnv        *envhp,
                                 OCISvcCtx     *svchp,
                                 OCIError      *errhp,
                                 OCILobLocator *lobp,
                                 const oratext *contenttypep,
                                 ub4            contenttypelen,
                                 ub4            mode);

#### Parameters

envhp (IN)
The environment handle.

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that can be passed to `OCIErrorGet()` for diagnostic information when there is an error.

lobp (IN)
A LOB locator that uniquely references a LOB.

contenttypep (IN)
The `contenttype` to be set for the given LOB.

contenttypelen (IN)
The size of `contenttype` in bytes. The size must be less than or equal to `OCI_LOB_CONTENTTYPE_MAXSIZE` bytes.

mode (IN)
For future use. Pass zero now.

#### Comments

This function only works on SecureFiles. If `lobp` is not a SecureFile, then the error `SECUREFILE_WRONGTYPE` is returned. If `lobp` is buffered, a temporary LOB, or an abstract LOB, then the error `SECUREFILE_BADLOB` is returned.

The maximum possible size of the `ContentType` string is defined as:

    #define OCI_LOB_CONTENTTYPE_MAXSIZE 128

The `ContentType` is ASCII (that is, 1-byte/7-bit UTF8).

To clear an existing `contenttype` set on a SecureFile, invoke `OCILobSetContentType()` with `contenttypep` set to (`oratext *)0` and `contenttypelen` set to `0`.

**Related Topics**

- OCILobGetContentType()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.35 OCILobSetOptions()

Enables option settings for a SecureFile LOB.

#### Purpose

Enables option settings for a SecureFile LOB.

#### Syntax

    sword OCILobSetOptions ( OCISvcCtx       *svchp,
                             OCIError        *errhp,
                             OCILobLocator   *locp,
                             ub4              option_types,
                             void            *optionsp,
                             ub4              optionslen,
                             ub4              mode );

#### Parameters

svchp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
The LOB locator that uniquely references the LOB. This locator must have been a locator that was obtained from the server specified by `svchp`.

option_types (IN)
You can specify multiple option types and values by using the bit-wise inclusive OR ("\|"). An error results if you specify an `option_types` value that is not enabled on the LOB column.

- Compression —`OCI_LOB_OPT_COMPRESS`

- Encryption — `OCI_LOB_OPT_ENCRYPT`

- Deduplication —`OCI_LOB_OPT_DEDUPLICATE`

- Allocation size — `OCI_LOB_OPT_ALLOCSIZE`

- Content type — `OCI_LOB_OPT_CONTENTTYPE`

- Modification time — `OCI_LOB_OPT_MODTIME`

optionsp (IN)
The possible settings are:

- `OCI_LOB_OPT_COMPRESS_OFF`

- `OCI_LOB_OPT_COMPRESS_ON`

- `OCI_LOB_ENCRYPT_OFF`

- `OCI_LOB_ENCRYPT_ON`

- `OCI_LOB_OPT_DEDUPLICATE_OFF`

- `OCI_LOB_OPT_DEDUPLICATE_ON`

optionslen (IN)
The length of the value in `optionsp`. Note that the only valid length at this time is `sizeof(ub4)`.

mode (IN)
Reserved for future use. Pass in 0.

**Related Topics**

- OCILobGetOptions()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.36 OCILobTrim2()

Truncates the LOB value to a shorter length. This function must be used for LOBs of size greater than 4 GB.

#### Purpose

You can also use this function for LOBs smaller than 4 GB.

#### Syntax

    sword OCILobTrim2 ( OCISvcCtx       *svchp,
                        OCIError        *errhp,
                        OCILobLocator   *locp,
                        oraub8           newlen );

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
An internal LOB locator that uniquely references the LOB. This locator must have been a locator that was obtained from the server specified by `svchp`.

newlen (IN)
The new length of the LOB value, which must be less than or equal to the current length. For character LOBs, it is the number of characters; for binary LOBs and `BFILE`s, it is the number of bytes in the LOB.

#### Comments

This function trims the LOB data to a specified shorter length. The function returns an error if `newlen` is greater than the current LOB length. This function is valid only for internal LOBs. `BFILE`s are not allowed.

It is not mandatory that you wrap this LOB operation inside the open or close calls. If you did not open the LOB before performing this operation, then the functional and domain indexes on the LOB column are updated during this call. However, if you did open the LOB before performing this operation, then you must close it before you commit your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance. If you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- OCILobRead2()
- OCILobAppend()
- OCILobCopy2()
- OCILobErase2()
- OCILobWrite2()
- OCILobWriteAppend2()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.3.37 OCILobWrite2()

Writes a buffer into a LOB. This function must be used for LOBs of size greater than 4 GB.

#### Purpose

You can also use this function for LOBs smaller than 4 GB.

#### Syntax

    sword OCILobWrite2 ( OCISvcCtx       *svchp,
                         OCIError        *errhp,
                         OCILobLocator   *locp,
                         oraub8          *byte_amtp,
                         oraub8          *char_amtp,
                         oraub8           offset,
                         void            *bufp,
                         oraub8           buflen,
                         ub1              piece,
                         void            *ctxp,
                         OCICallbackLobWrite2 (cbfp)
                                         (
                                           void     *ctxp,
                                           void     *bufp,
                                           oraub8   *lenp,
                                           ub1      *piecep
                                           void    **changed_bufpp,
                                           oraub8   *changed_lenp
                                         )
                         ub2              csid,
                         ub1              csfrm );

#### Parameters

svchp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
An internal LOB locator that uniquely references the LOB. This locator must have been a locator that was obtained from the server specified by `svchp`.

byte_amtp (IN/OUT)
IN - The number of bytes to write to the database. Always used for `BLOB`. For `CLOB` and `NCLOB` it is used only when `char_amtp` is zero.

OUT - The number of bytes written to the database. In polling mode, it is the length of the piece, in bytes, just written.

char_amtp (IN/OUT)
IN - The maximum number of characters to write to the database. Ignored for `BLOB`.

OUT - The number of characters written to the database. Undefined for `BLOB`. In polling mode, it is the length of the piece, in characters, just written.

offset (IN)
On input, it is the absolute offset from the beginning of the LOB value. For character LOBs, it is the number of characters from the beginning of the LOB; for binary LOBs, it is the number of bytes. The first position is 1.

If you use streaming (by polling or a callback), specify the offset in the first call; in subsequent polling calls, the offset parameter is ignored. When you use a callback, there is no offset parameter.

bufp (IN)
The pointer to a buffer from which the piece is written. The length of the data in the buffer is assumed to be the value passed in `buflen`. Even if the data is being written in pieces using the polling method, `bufp` must contain the first piece of the LOB when this call is invoked. If a callback is provided, `bufp` must not be used to provide data or an error results.

buflen (IN)
The length, in bytes, of the data in the buffer. This value differs from the `char_amtp` value for `CLOB`s and `NCLOB`s when the amount is specified in terms of characters using the `char_amtp` parameter, and the `buflen` parameter is specified in terms of bytes.

**Note:**

This parameter assumes an 8-bit byte. If your operating system uses a longer byte, you must adjust the value of `buflen` accordingly.

piece (IN)
Which piece of the buffer is being written. The default value for this parameter is `OCI_ONE_PIECE`, indicating that the buffer is written in a single piece.

The following other values are also possible for piecewise or callback mode: `OCI_FIRST_PIECE`, `OCI_NEXT_PIECE`, and `OCI_LAST_PIECE`.

ctxp (IN)
The context for the callback function. Can be `NULL`.

cbfp (IN)
A callback that can be registered to be called for each piece in a piecewise write. If this is `NULL`, the standard polling method is used.

The callback function must return `OCI_CONTINUE` for the write to continue. If any other error code is returned, the LOB write is terminated. The callback takes the following parameters:

ctxp (IN)
The context for the callback function. Can be `NULL`.

bufp (IN/OUT)
A buffer pointer for the piece. This is the same as the `bufp` passed as an input to the `OCILobWrite()` routine.

lenp (IN/OUT)
The length (in bytes) of the data in the buffer (IN), and the length (in bytes) of the current piece in `bufp` (OUT).

piecep (OUT)
Which piece: `OCI_NEXT_PIECE` or `OCI_LAST_PIECE`.

changed_bufpp (OUT)
The callback function can put the address of a new buffer if it prefers to use a new buffer for next piece to read. The default old buffer `bufp` is used if this parameter is set to `NULL`.

changed_lenp (OUT)
Length of the new buffer, if provided.

csid (IN)
The character set ID of the data in the buffer. If this value is 0, then `csid` is set to the client's `NLS_LANG` or `NLS_CHAR` value, depending on the value of `csfrm`.

csfrm (IN)
The character set form of the buffer data. The `csfrm` parameter must be consistent with the type of the LOB.

The `csfrm` parameter has two possible nonzero values:

- `SQLCS_IMPLICIT` - Database character set ID

- `SQLCS_NCHAR` - NCHAR character set ID

The default value is `SQLCS_IMPLICIT`.

#### Comments

Writes a buffer into an internal LOB as specified. If LOB data exists, it is overwritten with the data stored in the buffer. The buffer can be written to the LOB in a single piece with this call, or it can be provided piecewise using callbacks or a standard polling method.

**Note:**

When you read or write LOBs, specify a character set form (`csfrm`) that matches the form of the locator itself.

When you use the polling mode for `OCILobWrite2()`, the first call must specify values for `offset`, `byte_amtp`, and `char_amtp`, but on subsequent polling calls to `OCILobWrite2()`, you need not specify these values.

If the value of the `piece` parameter is `OCI_FIRST_PIECE`, data may need to be provided through callbacks or polling.

If a callback function is defined in the `cbfp` parameter, then this callback function is invoked to get the next piece after a piece is written to the pipe. Each piece is written from `bufp`. If no callback function is defined, then `OCILobWrite2()` returns the `OCI_NEED_DATA` error code. The application must call `OCILobWrite2()` again to write more pieces of the LOB. In this mode, the buffer pointer and the length can be different in each call if the pieces are of different sizes and from different locations.

A `piece` value of `OCI_LAST_PIECE` terminates the piecewise write, regardless of whether the polling or callback method is used.

If the amount of data passed to the database (through either input mechanism) is less than the amount specified by the `byte_amtp` or the `char_amtp` parameter, an ORA-22993 error is returned.

This function is valid for internal LOBs only. `BFILE`s are not allowed, because they are read-only. If the LOB is a `BLOB`, the `csid` and `csfrm` parameters are ignored.

If both `byte_amtp` and `char_amtp` are set to point to zero amount, and `OCI_FIRST_PIECE` is given as input, then polling mode is assumed and data is written until you specify `OCI_LAST_PIECE`. For `CLOB`s and `NCLOB`s, `byte_amtp` and `char_amtp` return the data written by each piece in terms of number of bytes and number of characters respectively. For `BLOB`s, `byte_amtp` returns the number of bytes written by each piece, whereas `char_amtp` is undefined on output.

To write data in UTF-16 format, set the `csid` parameter to `OCI_UTF16ID`. If the `csid` parameter is set, it overrides the `NLS_LANG` environment variable.

It is not mandatory that you wrap this LOB operation inside the open or close calls. If you did not open the LOB before performing this operation, then the functional and domain indexes on the LOB column are updated during this call. However, if you did open the LOB before performing this operation, then you must close it before you commit your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance. If you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- OCILobRead2()
- OCILobAppend()
- OCILobCopy2()
- OCILobWriteAppend2()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

- [PL/SQL REF CURSORs and Nested Tables in OCI](binding-and-defining-in-oci.md) for additional information about Unicode format

- The demonstration programs included with your Oracle Database installation for a code sample showing the use of LOB reads and writes.

- [OCI Demonstration Programs](oci-demo-programs.md)

- [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for general information about piecewise OCI operations

- [Polling Mode Operations in OCI](oci-programming-basics.md)

### 26.3.38 OCILobWriteAppend2()

Writes data starting at the end of a LOB. This function must be used for LOBs of size greater than 4 GB.

#### Purpose

You can also use this function for LOBs smaller than 4 GB.

#### Syntax

    sword OCILobWriteAppend2 ( OCISvcCtx            *svchp,
                               OCIError             *errhp,
                               OCILobLocator        *locp,
                               oraub8               *byte_amtp,
                               oraub8               *char_amtp,
                               void                 *bufp,
                               oraub8                buflen,
                               ub1                   piece,
                               void                 *ctxp,
                               OCICallbackLobWrite2 (cbfp)
                                             (
                                               void     *ctxp,
                                               void     *bufp,
                                               oraub8   *lenp,
                                               ub1      *piecep
                                               void    **changed_bufpp,
                                               oraub8   *changed_lenp
                                              )
                               ub2                   csid,
                               ub1                   csfrm);

#### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
An internal LOB locator that uniquely references a LOB.

byte_amtp (IN/OUT)
IN - The number of bytes to write to the database. Used for `BLOB`. For `CLOB` and `NCLOB` it is used only when `char_amtp` is zero.

OUT - The number of bytes written to the database.

char_amtp (IN/OUT)
IN - The maximum number of characters to write to the database. Ignored for `BLOB`.

OUT - The number of characters written to the database. Undefined for `BLOB`.

bufp (IN)
The pointer to a buffer from which the piece is written. The length of the data in the buffer is assumed to be the value passed in `buflen`. Even if the data is being written in pieces, `bufp` must contain the first piece of the LOB when this call is invoked. If a callback is provided, `bufp` must not be used to provide data or an error results.

buflen (IN)
The length, in bytes, of the data in the buffer. Note that this parameter assumes an 8-bit byte. If your operating system uses a longer byte, the value of `buflen` must be adjusted accordingly.

piece (IN)
Which piece of the buffer is being written. The default value for this parameter is `OCI_ONE_PIECE`, indicating that the buffer is written in a single piece. The following other values are also possible for piecewise or callback mode: `OCI_FIRST_PIECE`, `OCI_NEXT_PIECE`, and `OCI_LAST_PIECE`.

ctxp (IN)
The context for the callback function. Can be `NULL`.

cbfp (IN)
A callback that can be registered to be called for each piece in a piecewise write. If this is `NULL`, the standard polling method is used. The callback function must return `OCI_CONTINUE` for the write to continue. If any other error code is returned, the LOB write is terminated. The callback takes the following parameters:

ctxp (IN)
The context for the callback function. Can be `NULL`.

bufp (IN/OUT)
A buffer pointer for the piece.

lenp (IN/OUT)
The length (in bytes) of the data in the buffer (IN), and the length (in bytes) of the current piece in `bufp` (OUT).

piecep (OUT)
Which piece: `OCI_NEXT_PIECE` or `OCI_LAST_PIECE`.

changed_bufpp (OUT)
The callback function can put the address of a new buffer if it prefers to use a new buffer for next piece to be written. The default old buffer `bufp` is used if this parameter is set to `NULL`.

changed_lenp (OUT)
Length of the new buffer, if provided.

csid (IN)
The character set ID of the buffer data.

csfrm (IN)
The character set form of the buffer data.

The `csfrm` parameter has two possible nonzero values:

- `SQLCS_IMPLICIT` - Database character set ID

- `SQLCS_NCHAR` - NCHAR character set ID

The default value is `SQLCS_IMPLICIT`.

#### Comments

The buffer can be written to the LOB in a single piece with this call, or it can be provided piecewise using callbacks or a standard polling method. If the value of the piece parameter is `OCI_FIRST_PIECE`, data must be provided through callbacks or polling. If a callback function is defined in the `cbfp` parameter, then this callback function is invoked to get the next piece after a piece is written to the pipe. Each piece is written from `bufp`. If no callback function is defined, then `OCILobWriteAppend2()` returns the `OCI_NEED_DATA` error code.

The application must call `OCILobWriteAppend2()` again to write more pieces of the LOB. In this mode, the buffer pointer and the length can be different in each call if the pieces are of different sizes and from different locations. A piece value of `OCI_LAST_PIECE` terminates the piecewise write.

The `OCILobWriteAppend2()` function is not supported if LOB buffering is enabled.

If the LOB is a `BLOB`, the `csid` and `csfrm` parameters are ignored.

If both `byte_amtp` and `char_amtp` are set to point to zero amount and `OCI_FIRST_PIECE` is given as input, then polling mode is assumed and data is written until you specify `OCI_LAST_PIECE`. For `CLOB`s and `NCLOB`s, `byte_amtp` and `char_amtp` return the data written by each piece in terms of number of bytes and number of characters respectively. For `BLOB`s, `byte_amtp` returns the number of bytes written by each piece whereas `char_amtp` is undefined on output.

It is not mandatory that you wrap this LOB operation inside the open or close calls. If you did not open the LOB before performing this operation, then the functional and domain indexes on the LOB column are updated during this call. However, if you did open the LOB before performing this operation, then you must close it before you commit your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance. If you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- OCILobRead2()
- OCILobAppend()
- OCILobCopy2()
- OCILobWrite2()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[About Improving LOB Read/Write Performance](lobs-and-bfile-operations.md)
