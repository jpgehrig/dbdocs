Deprecated OCI features and functions are those that may become obsolete in a future release. Replacement OCI functions are mentioned where applicable.

Beginning with Oracle Database release 18c, version 18.1, the result set descriptor `OCI_DTYPE_RSET`.

OCI release 7.3 API beginning with Oracle Database 12c Release 1 (12.1).

Table E-1 lists the OCI functions that were deprecated in releases previous to Oracle 11g R2 (11.2) unless otherwise noted. In a future release, these functions may become obsolete.

Table E-1 Deprecated OCI Functions

| Function Group                      | Deprecated Functions                                                                                                                                                                                                                                               |
|:------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Initialize                          | OCIEnvInit(), OCIInitialize()                                                                                                                                                                                                                                      |
| Statement                           | OCIStmtFetch()<br>Beginning with Oracle Database 12c Release 2 (12.2): OCIStmtPrepare()                                                                                                                                                                            |
| Lob                                 | OCILobCopy(), OCILobErase(), OCILobGetLength(), OCILobLoadFromFile(), OCILobRead(), OCILobTrim(), OCILobWrite(), OCILobWriteAppend()<br>Beginning with Oracle Database 12c Release 2 (12.2): OCILobDisableBuffering(),OCILobEnableBuffering(), OCILobFlushBuffer() |
| Database Advanced Queuing functions | OCIAQListen()                                                                                                                                                                                                                                                      |

This section includes the following topics:

- Deprecated Initialize Functions

- Deprecated Statement Functions

- Deprecated Lob Functions

- Deprecated Database Advanced Queuing Functions

### E.1 Deprecated Initialize Functions

Describes the deprecated initialize functions.

Table E-2 lists the deprecated Initialize functions that are described in this section.

Table E-2 Deprecated Initialize Functions

| Function        | Purpose                             |
|:----------------|:------------------------------------|
| OCIEnvInit()    | Initialize an environment handle.   |
| OCIInitialize() | Initialize OCI process environment. |

#### E.1.1 OCIEnvInit()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Allocates and initializes an OCI environment handle. This function is deprecated.

##### Syntax

    sword OCIEnvInit ( OCIEnv    **envhpp,
                       ub4         mode,
                       size_t      xtramemsz,
                       void      **usrmempp );

##### Parameters

envhpp (OUT)
A pointer to a handle to the environment.

mode (IN)
Specifies initialization of an environment mode. Valid modes are:

- `OCI_DEFAULT`

- `OCI_ENV_NO_UCB`

In `OCI_DEFAULT` mode, the OCI library always mutexes handles.

The `OCI_ENV_NO_UCB` mode is used to suppress the calling of the dynamic callback routine `OCIEnvCallback()` at environment initialization time. The default behavior is to allow such a call to be made.

**See Also:**

[Dynamic Callback Registrations](user-defined-callback-functions.md)

xtramemsz (IN)
Specifies the amount of user memory to be allocated for the duration of the environment.

usrmempp (OUT)
Returns a pointer to the user memory of size `xtramemsz` allocated by the call for the user for the duration of the environment.

##### Comments

**Note:**

Use [OCIEnvCreate()](connect-authorize-and-initialize-functions.md) instead of the `OCIInitialize()` and `OCIEnvInit()` calls. `OCIInitialize()` and `OCIEnvInit()` calls are supported for backward compatibility.

This call allocates and initializes an OCI environment handle. No changes are made to an initialized handle. If `OCI_ERROR` or `OCI_SUCCESS_WITH_INFO` is returned, you can use the environment handle to obtain Oracle-specific errors and diagnostics.

This call is processed locally, without a server round-trip.

The environment handle can be freed using `OCIHandleFree()`.

**Related Topics**

- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- [OCIHandleFree()](handle-and-descriptor-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCITerminate()](connect-authorize-and-initialize-functions.md)

**See Also:**

[User Memory Allocation](oci-programming-basics.md) for more information about the `xtramemsz` parameter and user memory allocation

#### E.1.2 OCIInitialize()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Initializes the OCI process environment. This function is deprecated.

##### Syntax

    sword OCIInitialize ( ub4            mode,
                          const void    *ctxp,
                          const void    *(*malocfp)
                                         ( void   *ctxp,
                                            size_t size ),
                          const void    *(*ralocfp)
                                         ( void  *ctxp,
                                           void  *memptr,
                                           size_t newsize ),
                          const void    (*mfreefp)
                                         ( void  *ctxp,
                                           void  *memptr ));

##### Parameters

mode (IN)
Specifies initialization of the mode. The valid modes are:

- `OCI_DEFAULT` - Default mode.

- `OCI_THREADED` - Threaded environment. In this mode, internal data structures not exposed to the user are protected from concurrent accesses by multiple threads.

- `OCI_OBJECT` - Uses object features.

- `OCI_EVENTS` - Uses publish-subscribe notifications.

ctxp (IN)
User-defined context for the memory callback routines.

malocfp (IN)
User-defined memory allocation function. If `mode` is `OCI_THREADED`, this memory allocation routine must be thread-safe.

ctxp (IN/OUT)
Context pointer for the user-defined memory allocation function.

size (IN)
Size of memory to be allocated by the user-defined memory allocation function.

ralocfp (IN)
User-defined memory reallocation function. If `mode` is `OCI_THREADED`, this memory allocation routine must be thread-safe.

ctxp (IN/OUT)
Context pointer for the user-defined memory reallocation function.

memptr (IN/OUT)
Pointer to memory block.

newsize (IN)
New size of memory to be allocated.

mfreefp (IN)
User-defined memory free function. If `mode` is `OCI_THREADED`, this memory free routine must be thread-safe.

ctxp (IN/OUT)
Context pointer for the user-defined memory free function.

memptr (IN/OUT)
Pointer to memory to be freed.

##### Comments

**Note:**

Use [OCIEnvCreate()](connect-authorize-and-initialize-functions.md) instead of the deprecated OCIInitialize() call. The `OCIInitialize()` call is supported for backward compatibility.

This call initializes the OCI process environment. `OCIInitialize()` must be invoked before any other OCI call.

This function provides the ability for the application to define its own memory management functions through callbacks. If the application has defined such functions (that is, memory allocation, memory reallocation, memory free), they should be registered using the callback parameters in this function.

These memory callbacks are optional. If the application passes `NULL` values for the memory callbacks in this function, the default process memory allocation mechanism is used.

**See Also:**

- [Overview of OCI Multithreaded Development](managing-scalable-platforms.md) for information about using the OCI to write multithreaded applications

- [OCI Object-Relational Programming](oci-object-relational-programming.md) for information about OCI programming with objects

##### Example

The following statement shows an example of how to call `OCIInitialize()` in both threaded and object mode, with no user-defined memory functions:

    OCIInitialize((ub4) OCI_THREADED | OCI_OBJECT, (void  *)0,
         (void  * (*)()) 0, (void  * (*)()) 0,  (void (*)()) 0 );

**Related Topics**

- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- [OCIHandleFree()](handle-and-descriptor-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCITerminate()](connect-authorize-and-initialize-functions.md)

### E.2 Deprecated Statement Functions

Describes the deprecated statement functions.

Table E-3 lists the deprecated Statement functions that are described in this section.

Table E-3 Deprecated Statement Functions

| Function         | Purpose                                           |
|:-----------------|:--------------------------------------------------|
| OCIStmtFetch()   | Fetch rows from a query.                          |
| OCIStmtPrepare() | Prepares a SQL or PL/SQL statement for execution. |

#### E.2.1 OCIStmtFetch()

This function was deprecated in a release previous to Oracle 11g R2 (11.2).

##### Purpose

Fetches rows from a query. This function is deprecated. Use [OCIStmtFetch2()](statement-functions.md).

##### Syntax

    sword OCIStmtFetch ( OCIStmt     *stmtp,
                         OCIError    *errhp,
                         ub4          nrows,
                         ub2          orientation,
                         ub4          mode );

##### Parameters

stmtp (IN)
A statement (application request) handle.

errhp (IN)
An error handle that you can pass to [OCIErrorGet()](miscellaneous-functions.md) for diagnostic information when there is an error.

nrows (IN)
Number of rows to be fetched from the current position.

orientation (IN)
Before release 9.0, the only acceptable value is `OCI_FETCH_NEXT`, which is also the default value.

mode (IN)
Pass as `OCI_DEFAULT`.

##### Comments

The fetch call is a local call, if prefetched rows suffice. However, this is transparent to the application.

If LOB columns are being read, LOB locators are fetched for subsequent LOB operations to be performed on these locators. Prefetching is turned off if `LONG` columns are involved.

This function can return `OCI_NO_DATA` on `EOF` and `OCI_SUCCESS_WITH_INFO` when one of these errors occurs:

- ORA-24344 - Success with compilation error

- ORA-24345 - A truncation or `NULL` fetch error occurred

- ORA-24347 - Warning of a `NULL` column in an aggregate function

If you call `OCIStmtFetch()` with the `nrows` parameter set to 0, this cancels the cursor.

Use `OCI_ATTR_ROWS_FETCHED` to find the number of rows that were successfully fetched into the user's buffers in the last fetch call.

**Related Topics**

- [OCIStmtFetch2()](statement-functions.md)

#### E.2.2 OCIStmtPrepare()

This function was deprecated beginning with Oracle Database 12c Release 2 (12.2).

##### Purpose

Prepares a SQL or PL/SQL statement for execution. This function is deprecated. Use [OCIStmtPrepare2()](statement-functions.md).

##### Syntax

    sword OCIStmtPrepare ( OCIStmt       *stmtp,
                           OCIError      *errhp,
                           const OraText *stmt,
                           ub4            stmt_len,
                           ub4            language,
                           ub4            mode );

##### Parameters

stmtp (IN)
A statement handle associated with the statement to be executed. By default, it contains the encoding setting in the environment handle from which it is derived. A statement can be prepared in UTF-16 encoding only in a UTF-16 environment.

errhp (IN)
An error handle that you can pass to [OCIErrorGet()](miscellaneous-functions.md) for diagnostic information when there is an error.

stmt (IN)
SQL or PL/SQL statement to be executed. Must be a `NULL`-terminated string. That is, the ending character is a number of `NULL` bytes, depending on the encoding. The statement must be in the encoding specified by the `charset` parameter of a previous call to [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md).

Always cast the parameter to (`text *)`. After a statement has been prepared in UTF-16, the character set for the bind and define buffers default to UTF-16.

stmt_len (IN)
Length of the statement in characters or in number of bytes, depending on the encoding. Must not be zero.

language (IN)
Specifies V7, or native syntax. Possible values are as follows:

- `OCI_V7_SYNTAX` - V7 ORACLE parsing syntax.

- `OCI_NTV_SYNTAX` - Syntax depends upon the version of the server.

  `OCI_FOREIGN_SYNTAX` - Specifies the statement to be translated according to the SQL translation profile set in the session.

mode (IN)
Similar to the `mode` in the [OCIEnvCreate()](connect-authorize-and-initialize-functions.md) call, but this one has higher priority because it can override the "naturally" inherited mode setting.

The possible values are `OCI_DEFAULT` (default mode) or `OCI_PREP2_IMPL_RESULTS_CLIENT`. The mode should be passed as `OCI_PREP2_IMPL_RESULTS_CLIENT` when this call is made in an external procedure and implicit results need to be processed. See [OCI Support for Implicit Results](performance-topics.md) for more details. The statement handle `stmtp` uses whatever is specified by its parent environment handle.

##### Comments

An OCI application uses this call to prepare a SQL or PL/SQL statement for execution. The `OCIStmtPrepare()` call defines an application request.

The `mode` parameter determines whether the statement content is encoded as UTF-16 or not. The statement length is in number of code points or in number of bytes, depending on the encoding.

Although the statement handle inherits the encoding setting from the parent environment handle, the `mode` for this call can also change the encoding setting for the statement handle itself.

Data values for this statement initialized in subsequent bind calls are stored in a bind handle that uses settings in this statement handle as the default.

This call does not create an association between this statement handle and any particular server.

Before reexecuting a DDL statement, call this function a second time.

This call does not support Application Continuity and if this call is used, it returns the following error: `Error - ORA-25412: transaction replay disabled by call to OCIStmtPrepare`. Use the `OCIStmtPrepare2()` call to support the use of Application Continuity in an HA infrastructure.

**Related Topics**

- [OCIStmtPrepare2()](statement-functions.md)

**See Also:**

[About Preparing Statements](using-sql_statements-in-oci.md) for more information about using this call

### E.3 Deprecated Lob Functions

Describes the deprecated LOB functions.

Table E-4 lists the deprecated LOB functions that are described in this section.

Beginning with Oracle Database 12`c` Release 2 (12.2), most LOB functions including some deprecated LOB functions as indicated in the following table support Application Continuity (see [When Application Continuity in OCI Can Fail Over](high-availability-in-oci.md) for a complete list).

Table E-4 Deprecated LOB Functions

| Function                 | Purpose                                                                  |
|:-------------------------|:-------------------------------------------------------------------------|
| OCILobCopy()             | Copy all or part of one LOB to another. Supports Application Continuity. |
| OCILobDisableBuffering() | Disables LOB buffering for the input locator.                            |
| OCILobEnableBuffering()  | Enables LOB buffering for the input locator.                             |
| OCILobErase()            | Erase a portion of a LOB. Supports Application Continuity.               |
| OCILobFlushBuffer()      | Flushes or write s all buffers for this LOB to the server.               |
| OCILobGetLength()        | Get length of a LOB.                                                     |
| OCILobLoadFromFile()     | Load a LOB from a `BFILE`. Supports Application Continuity.              |
| OCILobRead()             | Read a portion of a LOB. Supports Application Continuity.                |
| OCILobTrim()             | Truncate a LOB. Supports Application Continuity.                         |
| OCILobWrite()            | Write into a LOB. Supports Application Continuity.                       |
| OCILobWriteAppend()      | Write data beginning at the end of a LOB.                                |

#### E.3.1 OCILobCopy()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Copies all or a portion of a LOB value into another LOB value. This function is deprecated. Use [OCILobCopy2()](lob-functions.md).

##### Syntax

    sword OCILobCopy ( OCISvcCtx        *svchp,
                       OCIError         *errhp,
                       OCILobLocator    *dst_locp,
                       OCILobLocator    *src_locp,
                       ub4               amount,
                       ub4               dst_offset,
                       ub4               src_offset );

##### Parameters

**Related Topics**

- [OCILobCopy2()](lob-functions.md)

#### E.3.2 OCILobDisableBuffering()

This function was deprecated beginning with Oracle Database 12c Release 2 (12.2).

##### Purpose

Disables LOB buffering for the input locator. This function is deprecated.

##### Syntax

    sword OCILobDisableBuffering ( OCISvcCtx      *svchp,
                                   OCIError       *errhp,
                                   OCILobLocator  *locp );

##### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to [OCIErrorGet()](miscellaneous-functions.md) or diagnostic information when there is an error.

locp (IN/OUT)
An internal LOB locator uniquely referencing the LOB.

##### Comments

Disables LOB buffering for the input internal LOB locator. The next time data is read from or written to the LOB through the input locator, the LOB buffering subsystem is not used. Note that this call does not implicitly flush the changes made in the buffering subsystem. The user must explicitly call OCILobFlushBuffer() to do this.

`OCILobDisableBuffering()` throws an error when a remote locator is passed to it.

This function does not accept a `BFILE` locator.

**Related Topics**

- OCILobEnableBuffering()
- [OCIErrorGet()](miscellaneous-functions.md)
- OCILobFlushBuffer()

#### E.3.3 OCILobEnableBuffering()

This function was deprecated beginning with Oracle Database 12c Release 2 (12.2).

##### Purpose

Enables LOB buffering for the input locator. This function is deprecated.

##### Syntax

    sword OCILobEnableBuffering ( OCISvcCtx      *svchp,
                                  OCIError       *errhp,
                                  OCILobLocator  *locp );

##### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to [OCIErrorGet()](miscellaneous-functions.md) for diagnostic information when there is an error.

locp (IN/OUT)
An internal LOB locator uniquely referencing the LOB.

##### Comments

Enables LOB buffering for the input internal LOB locator. The next time data is read from or written to the LOB through the input locator, the LOB buffering subsystem is used.

`OCILobEnableBuffering()` throws an error when a remote locator is passed to it.

If LOB buffering is enabled for a locator and that locator is passed to one of these routines, an error is returned: [OCILobAppend()](lob-functions.md), OCILobCopy() (deprecated), [OCILobCopy2()](lob-functions.md), OCILobErase() (deprecated), [OCILobErase2()](lob-functions.md), OCILobGetLength() (deprecated), [OCILobGetLength2()](lob-functions.md), OCILobLoadFromFile() (deprecated), [OCILobLoadFromFile2()](lob-functions.md), OCILobTrim() (deprecated), [OCILobTrim2()](lob-functions.md), OCILobWriteAppend() (deprecated), or [OCILobWriteAppend2()](lob-functions.md).

This function does not accept a `BFILE` locator.

**Related Topics**

- OCILobDisableBuffering()
- [OCIErrorGet()](miscellaneous-functions.md)
- OCILobWrite()
- [OCILobWrite2()](lob-functions.md)
- OCILobRead()
- [OCILobRead2()](lob-functions.md)
- OCILobFlushBuffer()
- OCILobWriteAppend()
- [OCILobWriteAppend2()](lob-functions.md)

#### E.3.4 OCILobErase()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Erases a specified portion of the internal LOB data starting at a specified offset. This function is deprecated. Use `OCILobErase2()`.

##### Syntax

    sword OCILobErase ( OCISvcCtx       *svchp,
                        OCIError        *errhp,
                        OCILobLocator   *locp,
                        ub4             *amount,
                        ub4              offset );

##### Parameters

**Related Topics**

- [OCILobErase2()](lob-functions.md)

#### E.3.5 OCILobFlushBuffer()

This function was deprecated beginning with Oracle Database 12c Release 2 (12.2).

##### Purpose

Flushes or write s all buffers for this LOB to the server. This function is deprecated.

##### Syntax

    sword OCILobFlushBuffer ( OCISvcCtx       *svchp,
                              OCIError        *errhp,
                              OCILobLocator   *locp
                              ub4              flag );

##### Parameters

svchp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

locp (IN/OUT)
An internal locator uniquely referencing the LOB.

flag (IN)
When this flag is set to `OCI_LOB_BUFFER_FREE`, the buffer resources for the LOB are freed after the flush. See the Comments section.

##### Comments

Flushes to the server changes made to the buffering subsystem that are associated with the LOB referenced by the input locator. This routine actually writes the data in the buffer to the LOB in the database. LOB buffering must have been enabled for the input LOB locator.

`OCILobFlushBuffer()` throws an error when a remote locator is passed to it.

The flush operation, by default, does not free the buffer resources for reallocation to another buffered LOB operation. To free the buffer explicitly, you can set the flag parameter to `OCI_LOB_BUFFER_FREE`.

If the client application intends to read the buffer value after the flush and knows in advance that the current value in the buffer is the desired value, there is no need to reread the data from the server.

The effects of freeing the buffer are mostly transparent to the user, except that the next access to the same range in the LOB involves a round-trip to the server, and there is an added cost for acquiring buffer resources and initializing the buffer with the data read from the LOB. This option is intended for client environments that have low on-board memory.

**Related Topics**

- OCILobEnableBuffering()
- [OCIErrorGet()](miscellaneous-functions.md)
- OCILobWrite()
- [OCILobWrite2()](lob-functions.md)
- OCILobRead()
- [OCILobRead2()](lob-functions.md)
- OCILobDisableBuffering()
- OCILobWriteAppend()
- [OCILobWriteAppend2()](lob-functions.md)

#### E.3.6 OCILobGetLength()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Gets the length of a LOB. This function is deprecated. Use `OCILobGetLength2()`.

##### Syntax

    sword OCILobGetLength ( OCISvcCtx      *svchp,
                            OCIError       *errhp,
                            OCILobLocator  *locp,
                            ub4            *lenp );

##### Parameters

**Related Topics**

- [OCILobGetLength2()](lob-functions.md)

#### E.3.7 OCILobLoadFromFile()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Loads and copies all or a portion of the file into an internal LOB. This function is deprecated. Use `OCILobLoadFromFile2()`.

##### Syntax

    sword OCILobLoadFromFile ( OCISvcCtx        *svchp,
                               OCIError         *errhp,
                               OCILobLocator    *dst_locp,
                               OCILobLocator    *src_locp,
                               ub4               amount,
                               ub4               dst_offset,
                               ub4               src_offset );

##### Parameters

**Related Topics**

- [OCILobLoadFromFile2()](lob-functions.md)

#### E.3.8 OCILobRead()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Reads a portion of a LOB or `BFILE`, as specified by the call, into a buffer. This function is deprecated. Use `OCILobRead2()`.

##### Syntax

    sword OCILobRead ( OCISvcCtx          *svchp,
                       OCIError           *errhp,
                       OCILobLocator      *locp,
                       ub4                *amtp,
                       ub4                 offset,
                       void               *bufp,
                       ub4                 bufl,
                       void               *ctxp,
                       OCICallbackLobRead (cbfp)
                                          ( void          *ctxp,
                                            const void    *bufp,
                                            ub4            len,
                                            ub1            piece
                                          )
                       ub2                 csid,
                       ub1                 csfrm );

##### Parameters

svchp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to [OCIErrorGet()](miscellaneous-functions.md) for diagnostic information when there is an error.

locp (IN)
A LOB or `BFILE` locator that uniquely references the LOB or `BFILE`. This locator must have been a locator that was obtained from the server specified by `svchp`.

amtp (IN/OUT)
The value in `amtp` is the amount in either bytes or characters, as shown in Table E-5.

Table E-5 Characters or Bytes in amtp for OCILobRead()

| LOB or BFILE         | Input      | Output with Fixed-Width Client-Side Character Set | Output with Varying-Width Client-Side Character Set |
|:---------------------|:-----------|:--------------------------------------------------|:----------------------------------------------------|
| `BLOB`s and `BFILE`s | bytes      | bytes                                             | bytes                                               |
| `CLOB`s and `NCLOB`s | characters | characters                                        | bytes <sup>Foot 1</sup>                             |

<sup>Footnote 1</sup>

The input amount refers to the number of characters to be read from the server-side `CLOB` or `NCLOB`. The output amount indicates how many bytes were read into the buffer `bufp`.

The parameter `amtp` is the total amount of data read if:

- Data is not read in streamed mode (only one piece is read and there is no polling or callback)

- Data is read in streamed mode with a callback

The parameter `amtp` is the length of the last piece read if the data is read in streamed mode using polling.

If the amount to be read is larger than the buffer length, it is assumed that the LOB is being read in a streamed mode from the input offset until the end of the LOB, or until the specified number of bytes have been read, whichever comes first. On input, if this value is 0, then the data is read in streamed mode from the input offset until the end of the LOB.

The streamed mode (implemented with either polling or callbacks) reads the LOB value sequentially from the input offset.

If the data is read in pieces, the `amtp` parameter always contains the length of the piece just read.

If a callback function is defined, then this callback function is invoked each time `bufl` bytes are read off the pipe. Each piece is written into `bufp`.

If the callback function is not defined, then the `OCI_NEED_DATA` error code is returned. The application must call `OCILobRead()` over and over again to read more pieces of the LOB until the `OCI_NEED_DATA` error code is not returned. The buffer pointer and the length can be different in each call if the pieces are being read into different sizes and locations.

offset (IN)
On input, this is the absolute offset from the beginning of the LOB value. For character LOBs (`CLOB`s, `NCLOB`s) it is the number of characters from the beginning of the LOB, for binary LOBs or `BFILE`s it is the number of bytes. The first position is 1.

If you use streaming (by polling or a callback), specify the offset in the first call; in subsequent polling calls, the offset parameter is ignored. When you use a callback, there is no offset parameter.

bufp (IN/OUT)
The pointer to a buffer into which the piece is read. The length of the allocated memory is assumed to be `bufl`.

bufl (IN)
The length of the buffer in octets. This value differs from the `amtp` value for `CLOB`s and for `NCLOB`s (`csfrm`=`SQLCS_NCHAR`) when the `amtp` parameter is specified in terms of characters, and the `bufl` parameter is specified in terms of bytes.

ctxp (IN)
The context pointer for the callback function. Can be `NULL`.

cbfp (IN)
A callback that can be registered to be called for each piece. If this is `NULL`, then `OCI_NEED_DATA` is returned for each piece.

The callback function must return `OCI_CONTINUE` for the read to continue. If any other error code is returned, the LOB read is terminated.

ctxp (IN)
The context for the callback function. Can be `NULL`.

bufp (IN/OUT)
A buffer pointer for the piece.

len (IN)
The length in bytes of the current piece in `bufp`.

piece (IN)
Which piece: `OCI_FIRST_PIECE`, `OCI_NEXT_PIECE`, or `OCI_LAST_PIECE`.

csid (IN)
The character set ID of the buffer data. If this value is 0, then `csid` is set to the client's `NLS_LANG` or `NLS_CHAR` value, depending on the value of `csfrm`. It is never assumed to be the server's character set, unless the server and client have the same settings.

csfrm (IN)
The character set form of the buffer data. The `csfrm` parameter must be consistent with the type of the LOB.

The `csfrm` parameter has two possible nonzero values:

- `SQLCS_IMPLICIT` - Database character set ID

- `SQLCS_NCHAR` - NCHAR character set ID

The default value is `SQLCS_IMPLICIT`. If `csfrm` is not specified, the default is assumed.

##### Comments

Reads a portion of a LOB or `BFILE` as specified by the call into a buffer. It is an error to try to read from a `NULL` LOB or `BFILE`.

**Note:**

When you read or write LOBs, specify a character set form (`csfrm`) that matches the form of the locator itself.

For `BFILE`s, the operating system file must exist on the server, and it must have been opened by [OCILobFileOpen()](lob-functions.md) or [OCILobOpen()](lob-functions.md) using the input locator. Oracle Database must have permission to read the operating system file, and the user must have read permission on the directory object.

When you use the polling mode for `OCILobRead()`, the first call must specify values for `offset` and `amtp`, but on subsequent polling calls to `OCILobRead()`, you need not specify these values.

If the LOB is a `BLOB`, the `csid` and `csfrm` parameters are ignored.

**Note:**

To terminate an `OCILobRead()` operation and free the statement handle, use the [OCIBreak()](miscellaneous-functions.md) call.

The following apply to client-side varying-width character sets for `CLOB`s and `NCLOB`s:

- When you use polling mode, be sure to specify the `amtp` and `offset` parameters only in the first call to `OCILobRead()`. On subsequent polling calls, these parameters are ignored.

- When you use callbacks, the `len` parameter, which is input to the callback, indicates how many bytes are filled in the buffer. Check the `len` parameter during your callback processing because the entire buffer cannot be filled with data.

The following applies to client-side fixed-width character sets and server-side varying-width character sets for `CLOB`s and `NCLOB`s:

- When reading a `CLOB` or `NCLOB` value, look at the `amtp` parameter after every call to `OCILobRead()` to see how much of the buffer is filled. When the return value is in characters (as when the client-side character set is fixed-width), then convert this value to bytes and determine how much of the buffer is filled. When you use callbacks, always check the `len` parameter to see how much of the buffer is filled. This value is always in bytes.

To read data in UTF-16 format, set the `csid` parameter to `OCI_UTF16ID`. If the `csid` parameter is set, it overrides the `NLS_LANG` environment variable.

**Related Topics**

- [OCILobRead2()](lob-functions.md)

**See Also:**

- [PL/SQL REF CURSORs and Nested Tables in OCI](binding-and-defining-in-oci.md) for additional information about Unicode format

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-APIs-for-BFILE-operations.md) for a description of `BFILE`s

- The demonstration programs included with your Oracle Database installation for a code sample showing the use of LOB reads and writes.

- [OCI Demonstration Programs](oci-demo-programs.md)

- [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for general information about piecewise OCI operations

- [Polling Mode Operations in OCI](oci-programming-basics.md)

#### E.3.9 OCILobTrim()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Truncates the LOB value to a shorter length. This function is deprecated. Use [OCILobTrim2()](lob-functions.md).

##### Syntax

    sword OCILobTrim ( OCISvcCtx       *svchp,
                       OCIError        *errhp,
                       OCILobLocator   *locp,
                       ub4              newlen );

##### Parameters

**Related Topics**

- [OCILobTrim2()](lob-functions.md)

#### E.3.10 OCILobWrite()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Writes a buffer into a LOB. This function is deprecated. Use `OCILobWrite2()`.

##### Syntax

    sword OCILobWrite ( OCISvcCtx       *svchp,
                        OCIError        *errhp,
                        OCILobLocator   *locp,
                        ub4             *amtp,
                        ub4              offset,
                        void            *bufp,
                        ub4              buflen,
                        ub1              piece,
                        void            *ctxp,
                        OCICallbackLobWrite      (cbfp)
                                        (
                                          void     *ctxp,
                                          void     *bufp,
                                          ub4      *lenp,
                                          ub1      *piecep
                                        )
                        ub2              csid,
                        ub1              csfrm );

##### Parameters

svchp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to [OCIErrorGet()](miscellaneous-functions.md) for diagnostic information when there is an error.

locp (IN/OUT)
An internal LOB locator that uniquely references the LOB. This locator must have been a locator that was obtained from the server specified by `svchp`.

amtp (IN/OUT)
The value in `amtp` is the amount in either bytes or characters, as shown in Table E-6.

Table E-6 Characters or Bytes in amtp for OCILobWrite()

| LOB or BFILE         | Input with Fixed-Width Client-Side Character Set | Input with Varying-Width Client-Side Character Set | Output     |
|:---------------------|:-------------------------------------------------|:---------------------------------------------------|:-----------|
| `BLOB`s and `BFILE`s | bytes                                            | bytes                                              | bytes      |
| `CLOB`s and `NCLOB`s | characters                                       | bytes <sup>Foot 2</sup>                            | characters |

<sup>Footnote 2</sup>

The input amount refers to the number of bytes of data that the user wants to write into the LOB and not the number of bytes in the `bufp`, which is specified by `buflen`. If data is written in pieces, the amount of bytes to write may be larger than the `buflen`. The output amount refers to the number of characters written into the server-side `CLOB` or `NCLOB`.

This should always be a non-`NULL` pointer. If you want to specify write-until-end-of-file, then you must declare a variable, set it equal to zero, and pass its address for this parameter.

If the amount is specified on input, and the data is written in pieces, the parameter `amtp` contains the total length of the pieces written at the end of the call (last piece written) and is undefined in between. Note that it is different from the piecewise read case. An error is returned if that amount is not sent to the server.

If `amtp` is zero, then streaming mode is assumed, and data is written until the user specifies `OCI_LAST_PIECE`.

offset (IN)
On input, it is the absolute offset from the beginning of the LOB value. For character LOBs, it is the number of characters from the beginning of the LOB; for binary LOBs, it is the number of bytes. The first position is 1.

If you use streaming (by polling or a callback), specify the offset in the first call; in subsequent polling calls, the offset parameter is ignored. When you use a callback, there is no offset parameter.

bufp (IN)
The pointer to a buffer from which the piece is written. The length of the data in the buffer is assumed to be the value passed in `buflen`. Even if the data is being written in pieces using the polling method, `bufp` must contain the first piece of the LOB when this call is invoked. If a callback is provided, `bufp` must not be used to provide data or an error results.

buflen (IN)
The length, in bytes, of the data in the buffer. This value differs from the `amtp` value for `CLOB`s and `NCLOB`s when the `amtp` parameter is specified in terms of characters, and the `buflen` parameter is specified in terms of bytes.

**Note:**

This parameter assumes an 8-bit byte. If your operating system uses a longer byte, you must adjust the value of `buflen` accordingly.

piece (IN)
Which piece of the buffer is being written. The default value for this parameter is `OCI_ONE_PIECE`, indicating that the buffer is written in a single piece. The following other values are also possible for piecewise or callback mode: `OCI_FIRST_PIECE`, `OCI_NEXT_PIECE`, and `OCI_LAST_PIECE`.

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

csid (IN)
The character set ID of the data in the buffer. If this value is 0, then `csid` is set to the client's `NLS_LANG` or `NLS_CHAR` value, depending on the value of `csfrm`.

csfrm (IN)
The character set form of the buffer data. The `csfrm` parameter must be consistent with the type of the LOB.

The `csfrm` parameter has two possible nonzero values:

- `SQLCS_IMPLICIT` - Database character set ID

- `SQLCS_NCHAR` - `NCHAR` character set ID

The default value is `SQLCS_IMPLICIT`.

##### Comments

Writes a buffer into an internal LOB as specified. If LOB data exists, it is overwritten with the data stored in the buffer. The buffer can be written to the LOB in a single piece with this call, or it can be provided piecewise using callbacks or a standard polling method.

**Note:**

When you read or write LOBs, specify a character set form (`csfrm`) that matches the form of the locator itself.

When you use the polling mode for `OCILobWrite()`, the first call must specify values for `offset` and `amtp`, but on subsequent polling calls to `OCILobWrite()`, you need not specify these values.

If the value of the `piece` parameter is `OCI_FIRST_PIECE`, data may need to be provided through callbacks or polling.

If a callback function is defined in the `cbfp` parameter, then this callback function is invoked to get the next piece after a piece is written to the pipe. Each piece is written from `bufp`. If no callback function is defined, then `OCILobWrite()` returns the `OCI_NEED_DATA` error code. The application must call `OCILobWrite()` again to write more pieces of the LOB. In this mode, the buffer pointer and the length can be different in each call if the pieces are of different sizes and from different locations.

A `piece` value of `OCI_LAST_PIECE` terminates the piecewise write, regardless of whether the polling or callback method is used.

If the amount of data passed to Oracle Database (through either input mechanism) is less than the amount specified by the `amtp` parameter, an ORA-22993 error is returned.

This function is valid for internal LOBs only. `BFILE`s are not allowed, because they are read-only. If the LOB is a `BLOB`, the `csid` and `csfrm` parameters are ignored.

If the client-side character set is varying-width, then the input amount is in bytes and the output amount is in characters for `CLOB`s and `NCLOB`s. The input amount refers to the number of bytes of data that the user wants to write into the LOB and not the number of bytes in the `bufp`, which is specified by `buflen`. If data is written in pieces, the amount of bytes to write may be larger than the `buflen`. The output amount refers to the number of characters written into the server-side `CLOB` or `NCLOB`.

To write data in UTF-16 format, set the `csid` parameter to `OCI_UTF16ID`. If the `csid` parameter is set, it overrides the `NLS_LANG` environment variable.

It is not mandatory that you wrap this LOB operation inside the open or close calls. If you did not open the LOB before performing this operation, then the functional and domain indexes on the LOB column are updated during this call. However, if you did open the LOB before performing this operation, then you must close it before you commit or roll back your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance. If you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- [OCILobWrite2()](lob-functions.md)

**See Also:**

- [PL/SQL REF CURSORs and Nested Tables in OCI](binding-and-defining-in-oci.md) for additional information about Unicode format

- The demonstration programs included with your Oracle Database installation for a code sample showing the use of LOB reads and writes.

- [OCI Demonstration Programs](oci-demo-programs.md)

- [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for general information about piecewise OCI operations

- [Polling Mode Operations in OCI](oci-programming-basics.md)

#### E.3.11 OCILobWriteAppend()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Writes data starting at the end of a LOB. This function is deprecated. Use [OCILobWriteAppend2()](lob-functions.md).

##### Syntax

    sword OCILobWriteAppend ( OCISvcCtx     *svchp,
                              OCIError      *errhp,
                              OCILobLocator *locp,
                              ub4           *amtp,
                              void          *bufp,
                              ub4            buflen,
                              ub1            piece,
                              void          *ctxp,
                              OCICallbackLobWrite       (cbfp)
                                             (
                                               void     *ctxp,
                                               void     *bufp,
                                               ub4      *lenp,
                                               ub1      *piecep
                                             )
                              ub2            csid,
                              ub1            csfrm );

##### Parameters

svchp (IN)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to [OCIErrorGet()](miscellaneous-functions.md) for diagnostic information when there is an error.

locp (IN/OUT)
An internal LOB locator that uniquely references a LOB.

amtp (IN/OUT)
The value in `amtp` is the amount in either bytes or characters, as shown in Table E-7.

Table E-7 Characters or Bytes in amtp for OCILobWriteAppend()

| LOB or BFILE         | Input with Fixed-Width Client-Side Character Set | Input with Varying-Width Client-Side Character Set | Output     |
|:---------------------|:-------------------------------------------------|:---------------------------------------------------|:-----------|
| `BLOB`s and `BFILE`s | bytes                                            | bytes                                              | bytes      |
| `CLOB`s and `NCLOB`s | characters                                       | bytes <sup>Foot 3</sup>                            | characters |

<sup>Footnote 3</sup>

The input amount refers to the number of bytes of data that the user wants to write into the LOB and not the number of bytes in the `bufp,` which is specified by `buflen`. If data is written in pieces, the amount of bytes to write may be larger than the `buflen`. The output amount refers to the number of characters written into the server-side `CLOB` or `NCLOB`.

If the amount is specified on input, and the data is written in pieces, the parameter `amtp` contains the total length of the pieces written at the end of the call (last piece written) and is undefined in between. (Note it is different from the piecewise read case). An error is returned if that amount is not sent to the server. If `amtp` is zero, then streaming mode is assumed, and data is written until the user specifies `OCI_LAST_PIECE`.

If the client-side character set is varying-width, then the input amount is in bytes, not characters, for `CLOB`s or `NCLOB`s.

bufp (IN)
The pointer to a buffer from which the piece is written. The length of the data in the buffer is assumed to be the value passed in `buflen`. Even if the data is being written in pieces, `bufp` must contain the first piece of the LOB when this call is invoked. If a callback is provided, bufp must not be used to provide data or an error results.

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

csid (IN)
The character set ID of the buffer data.

csfrm (IN)
The character set form of the buffer data.

The `csfrm` parameter has two possible nonzero values:

- `SQLCS_IMPLICIT` - Database character set ID

- `SQLCS_NCHAR` - `NCHAR` character set ID

The default value is `SQLCS_IMPLICIT`.

##### Comments

The buffer can be written to the LOB in a single piece with this call, or it can be provided piecewise using callbacks or a standard polling method. If the value of the piece parameter is `OCI_FIRST_PIECE`, data must be provided through callbacks or polling. If a callback function is defined in the `cbfp` parameter, then this callback function is invoked to get the next piece after a piece is written to the pipe. Each piece is written from `bufp`. If no callback function is defined, then `OCILobWriteAppend()` returns the `OCI_NEED_DATA` error code.

The application must call `OCILobWriteAppend()` again to write more pieces of the LOB. In this mode, the buffer pointer and the length can be different in each call if the pieces are of different sizes and from different locations. A piece value of `OCI_LAST_PIECE` terminates the piecewise write.

`OCILobWriteAppend()` is not supported if LOB buffering is enabled.

If the LOB is a `BLOB`, the `csid` and `csfrm` parameters are ignored.

If the client-side character set is varying-width, then the input amount is in bytes, not characters, for `CLOB`s or `NCLOB`s.

It is not mandatory that you wrap this LOB operation inside the open or close calls. If you did not open the LOB before performing this operation, then the functional and domain indexes on the LOB column are updated during this call. However, if you did open the LOB before performing this operation, then you must close it before you commit or roll back your transaction. When an internal LOB is closed, it updates the functional and domain indexes on the LOB column.

If you do not wrap your LOB operations inside the open or close API, then the functional and domain indexes are updated each time you write to the LOB. This can adversely affect performance. If you have functional or domain indexes, Oracle recommends that you enclose write operations to the LOB within the open or close statements.

**Related Topics**

- [OCILobWriteAppend2()](lob-functions.md)

**See Also:**

[About Improving LOB Read/Write Performance](lobs-and-bfile-operations.md)

### E.4 Deprecated Database Advanced Queuing Functions

Describes deprecated Oracle Database Advanced Queuing functions.

Table E-8 lists the deprecated Database Advanced Queuing functions that are described in this section.

Table E-8 Deprecated Database Advanced Queuing Functions

| Function      | Purpose                                                     |
|:--------------|:------------------------------------------------------------|
| OCIAQListen() | Listen on one or more queues on behalf of a list of agents. |

#### E.4.1 OCIAQListen()

This function was deprecated in a release previous to Oracle Database 11g Release 2 (11.2).

##### Purpose

Listens on one or more queues on behalf of a list of agents. This function is deprecated. Use`OCIAQListen2()`.

##### Syntax

    sword OCIAQListen (OCISvcCtx      *svchp,
                       OCIError       *errhp,
                       OCIAQAgent    **agent_list,
                       ub4             num_agents,
                       sb4             wait,
                       OCIAQAgent    **agent,
                       ub4             flags);

##### Parameters

svchpp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to [OCIErrorGet()](miscellaneous-functions.md) for diagnostic information when there is an error.

agent_list (IN)
List of agents for which to monitor messages.

num_agents (IN)
Number of agents in the agent list.

wait (IN)
Timeout interval for the listen call.

agent (OUT)
Agent for which there is a message. `OCIAgent` is an OCI descriptor.

flags (IN)
Not currently used; pass as `OCI_DEFAULT`.

##### Comments

This is a blocking call that returns when there is a message ready for consumption for an agent in the list. If there are no messages found when the wait time expires, an error is returned.

**Related Topics**

- [OCIAQListen2()](streams-advanced-queueing-and-publish-subscribe-functions.md)
