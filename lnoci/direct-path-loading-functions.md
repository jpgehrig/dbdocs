Lists and describes the direct path loading functions.

Table 26-4 lists the direct path loading functions that are described in this section.

Table 26-4 Direct Path Loading Functions

| Function                     | Purpose                                                                      |
|:-----------------------------|:-----------------------------------------------------------------------------|
| OCIDirPathAbort()            | Terminate a direct path operation                                            |
| OCIDirPathColArrayEntryGet() | Get a specified entry in a column array                                      |
| OCIDirPathColArrayEntrySet() | Set a specified entry in a column array to a specific value                  |
| OCIDirPathColArrayReset()    | Reset the row array state                                                    |
| OCIDirPathColArrayRowGet()   | Get the base row pointers for a specified row number                         |
| OCIDirPathColArrayToStream() | Convert from a column array to a direct path stream format                   |
| OCIDirPathDataSave()         | Do a data savepoint, or commit the loaded data and finish the load operation |
| OCIDirPathFinish()           | Finish and commit the loaded data                                            |
| OCIDirPathFlushRow()         | Deprecated.                                                                  |
| OCIDirPathLoadStream()       | Load the data converted to direct path stream format                         |
| OCIDirPathPrepare()          | Prepare direct path interface to convert or load rows                        |
| OCIDirPathStreamReset()      | Reset the direct path stream state                                           |

### 26.5.1 OCIDirPathAbort()

Terminates a direct path operation.

#### Purpose

Terminates a direct path operation.

#### Syntax

    sword OCIDirPathAbort   ( OCIDirPathCtx          *dpctx,
                              OCIError               *errhp );

#### Parameters

dpctx (IN)
Direct path context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

All state that was maintained by the server on behalf of the direct path operation is destroyed by a termination. For a direct path load, the data loaded before the terminate operation is not visible to any queries. However, the data may still consume space in the segments that are being loaded. Any load completion operations, such as index maintenance operations, are not performed.

**Related Topics**

- OCIDirPathFinish()
- OCIDirPathPrepare()
- OCIDirPathLoadStream()
- OCIDirPathStreamReset()
- OCIDirPathDataSave()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.2 OCIDirPathColArrayEntryGet()

#### Purpose

Gets a specified entry in a column array.

#### Syntax

    sword OCIDirPathColArrayEntryGet ( OCIDirPathColArray   *dpca,
                                       OCIError             *errhp,
                                       ub4                   rownum,
                                       ub2                   colIdx,
                                       ub1                 **cvalpp,
                                       ub4                  *clenp,
                                       ub1                  *cflgp );

#### Parameters

dpca (IN/OUT)
Direct path column array handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

rownum (IN)
Zero-based row offset.

colIdx (IN)
The column's index used when building the column parameter list.

cvalpp (IN/OUT)
Pointer to pointer to column data.

clenp (IN/OUT)
Pointer to length of column data.

cflgp (IN/OUT)
Pointer to column flag.

One of these values is returned:

- `OCI_DIRPATH_COL_COMPLETE` - All data for the column is present.

- `OCI_DIRPATH_COL_NULL` - Column is `NULL`.

- `OCI_DIRPATH_COL_PARTIAL` - Partial column data is being supplied.

#### Comments

If `cflgp` is set to `OCI_DIRPATH_COL_NULL`, the `cvalpp` and `clenp` parameters are not set by this operation.

**Related Topics**

- OCIDirPathColArrayEntrySet()
- OCIDirPathColArrayRowGet()
- OCIDirPathColArrayReset()
- OCIDirPathColArrayToStream()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.3 OCIDirPathColArrayEntrySet()

Sets a specified entry in a column array to the supplied values.

#### Purpose

Sets a specified entry in a column array to the supplied values.

#### Syntax

    sword OCIDirPathColArrayEntrySet ( OCIDirPathColArray   *dpca,
                                       OCIError             *errhp,
                                       ub4                   rownum,
                                       ub2                   colIdx,
                                       ub1                  *cvalp,
                                       ub4                   clen,
                                       ub1                   cflg );

#### Parameters

dpca (IN/OUT)
Direct path column array handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

rownum (IN)
Zero-based row offset.

colIdx (IN)
The column's index used when building the column parameter list.

cvalp (IN)
Pointer to column data.

clen (IN)
Length of column data.

cflg (IN)
Column flag. One of these values is returned:

- `OCI_DIRPATH_COL_COMPLETE` - All data for the column is present.

- `OCI_DIRPATH_COL_NULL` - Column is `NULL`.

- `OCI_DIRPATH_COL_PARTIAL` - Partial column data is being supplied.

#### Comments

If `cflg` is set to `OCI_DIRPATH_COL_NULL`, the `cvalp` and `clen` parameters are not used.

#### Example

This example sets the source of data for the first row in a column array to `addr`, with a length of `len`. In this example, the column is identified by `colId`.

    err = OCIDirPathColArrayEntrySet(dpca, errhp, (ub2)0, colId, addr, len,
              OCI_DIRPATH_COL_COMPLETE);

**Related Topics**

- OCIDirPathColArrayEntryGet()
- OCIDirPathColArrayRowGet()
- OCIDirPathColArrayReset()
- OCIDirPathColArrayToStream()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.4 OCIDirPathColArrayReset()

Resets the column array state.

#### Purpose

Resets the column array state.

#### Syntax

    sword OCIDirPathColArrayReset ( OCIDirPathColArray   *dpca,
                                    OCIError             *errhp );

#### Parameters

dpca (IN)
Direct path column array handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

Resetting the column array state is necessary when piecing in a large column and an error occurs in the middle of loading the column. Do not reset the column array if the last `OCIDirPathColArrayReset()` call returned `OCI_NEED_DATA` or `OCI_CONTINUE`. That is, you are in the middle of a row conversion. Use OCI_DIRPATH_COL_ERROR to purge the current row for `OCI_NEED_DATA`.

**Related Topics**

- OCIDirPathColArrayEntryGet()
- OCIDirPathColArrayEntrySet()
- OCIDirPathColArrayRowGet()
- OCIDirPathColArrayToStream()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.5 OCIDirPathColArrayRowGet()

Gets the column array row pointers for a given row number.

#### Purpose

Gets the column array row pointers for a given row number.

#### Syntax

    sword OCIDirPathColArrayRowGet ( OCIDirPathColArray     *dpca,
                                     OCIError               *errhp,
                                     ub4                     rownum,
                                     ub1                  ***cvalppp,
                                     ub4                   **clenpp,
                                     ub1                   **cflgpp );

#### Parameters

dpca (IN/OUT)
Direct path column array handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

rownum (IN)
Zero-based row offset

cvalppp (IN/OUT)
Pointer to vector of pointers to column data

clenpp (IN/OUT)
Pointer to vector of column data lengths

cflgpp (IN/OUT)
Pointer to vector of column flags

#### Comments

Returns pointers to column array entries for the given row. This allows the application to do simple pointer arithmetic to iterate across the columns of the specific row. You can use this interface to efficiently get or set the column array entries of a row, as opposed to calling `OCIDirPathColArrayEntrySet()` for every column. The application is also responsible for not dereferencing memory beyond the column array boundaries. The dimensions of the column array are available as attributes of the column array.

**Related Topics**

- OCIDirPathColArrayEntryGet()
- OCIDirPathColArrayEntrySet()
- OCIDirPathColArrayReset()
- OCIDirPathColArrayToStream()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.6 OCIDirPathColArrayToStream()

Converts from column array format to a direct path stream format.

#### Purpose

Converts from column array format to a direct path stream format.

#### Syntax

    sword OCIDirPathColArrayToStream ( OCIDirPathColArray     *dpca,
                                       OCIDirPathCtx  const   *dpctx,
                                       OCIDirPathStream       *dpstr,
                                       OCIError               *errhp,
                                       ub4                     rowcnt,
                                       ub4                     rowoff );

#### Parameters

dpca (IN)
Direct path column array handle.

dpctx (IN)
Direct path context handle for the object being loaded.

dpstr (IN/OUT)
Direct path stream handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

rowcnt (IN)
Number of rows in the column array.

rowoff (IN)
Starting index in the column array.

#### Comments

This interface is used to convert a column array representation of data in its external format to a direct path stream format. The converted format is suitable for loading with `OCIDirPathLoadStream()`.

The column data in direct path stream format is converted to its Oracle Database internal representation. All conversions are done on the client side of the two-task interface; all conversion errors occur synchronously with the call to this interface. Information concerning which row and column an error occurred on is available as an attribute of the column array handle.

Note that in a threaded environment, concurrent `OCIDirPathColArrayToStream()` operations can be referencing the same direct path context handle. However, the direct path context handle is not modified by this interface.

The return codes for this call are:

- `OCI_SUCCESS` - All data in the column array was successfully converted to stream format. The column array attribute `OCI_ATTR_ROW_COUNT` is the number of rows processed.

- `OCI_ERROR` - An error occurred during conversion; the error handle contains the error information. The column array attribute `OCI_ATTR_ROW_COUNT` is the number of rows successfully converted in the last call. The attribute `OCI_ATTR_COL_COUNT` contains the column index into the column array for the column that caused the error. A stream must always be loaded after column array to stream conversion returns `OCI_ERROR`. It cannot be reset or converted to until it is loaded.

- `OCI_CONTINUE` - Not all of the data in the column array could be converted to stream format. The stream buffer is not large enough to contain all of the column array data. The caller should either load the data, save the data to a file, or use another stream and call `OCIDirPathColArrayToStream()` again to convert the remainder of the column array data. The column array attribute `OCI_ATTR_ROW_COUNT` is the number of rows successfully converted in the last call. The row offset must be updated for the next conversion; internal state does keep track of the column to continue conversion from. The `OCI_ATTR_ROW_COUNT` value must be added to the previous row offset by the caller.

- `OCI_NEED_DATA` - All of the data in the column array was successfully converted, but a partial column was encountered. The caller should load the resulting stream, and supply the remainder of the row, iteratively if necessary. The column array attribute `OCI_ATTR_ROW_COUNT` is the number of rows successfully converted in the last call. The attribute `OCI_ATTR_COL_COUNT` contains the column index into the column array for the column that is marked partial.

**Related Topics**

- OCIDirPathLoadStream()
- OCIDirPathColArrayEntryGet()
- OCIDirPathColArrayEntrySet()
- OCIDirPathColArrayReset()
- OCIDirPathColArrayRowGet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.7 OCIDirPathDataSave()

Depending on the action requested, does a data savepoint, or commits the loaded data and finishes the direct path load operation.

#### Purpose

Depending on the action requested, does a data savepoint, or commits the loaded data and finishes the direct path load operation.

#### Syntax

    sword OCIDirPathDataSave ( OCIDirPathCtx          *dpctx,
                               OCIError               *errhp,
                               ub4                     action  );

#### Parameters

dpctx (IN)
Direct path context handle for the object loaded.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

action (IN)
Values for action parameter to `OCIDirPathDataSave()` are as follows:

- `OCI_DIRPATH_DATASAVE_SAVEONLY` - To execute a data savepoint only

- `OCI_DIRPATH_DATASAVE_FINISH` - To commit the loaded data and call the direct finishing function

#### Comments

A return value of `OCI_SUCCESS` indicates that the backend has properly executed a data savepoint or executed the finishing logic.

Executing a data savepoint is not allowed for LOBs.

Executing the finishing logic is different from properly terminating the load, because resources allocated are not freed.

**Related Topics**

- OCIDirPathAbort()
- OCIDirPathFinish()
- OCIDirPathPrepare()
- OCIDirPathStreamReset()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.8 OCIDirPathFinish()

Finishes the direct path load operation.

#### Purpose

Finishes the direct path load operation.

#### Syntax

    sword OCIDirPathFinish (   OCIDirPathCtx          *dpctx,
                               OCIError               *errhp );

#### Parameters

dpctx (IN)
Direct path context handle for the object loaded.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

After the load has completed, and the loaded data is to be committed, the direct path finishing function is called. Finish is not allowed until all streams have been loaded, and there is not a partially loaded row.

A return value of `OCI_SUCCESS` indicates that the backend has properly terminated the load.

**Related Topics**

- OCIDirPathAbort()
- OCIDirPathDataSave()
- OCIDirPathPrepare()
- OCIDirPathStreamReset()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.9 OCIDirPathFlushRow()

Flushes a partially loaded row from the server. This function is deprecated.

#### Purpose

Flushes a partially loaded row from the server. This function is deprecated.

#### Syntax

    sword OCIDirPathFlushRow (   OCIDirPathCtx          *dpctx,
                                 OCIError               *errhp );

#### Parameters

dpctx (IN)
Direct path context handle for the object loaded.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

This function is necessary when part of a row is loaded, but a conversion error occurs on the next piece being processed by the application. Only the row currently in partial state is discarded. If the server is not currently processing a partial row for the object associated with the direct path context, this function does nothing.

**Related Topics**

- OCIDirPathAbort()
- OCIDirPathFinish()
- OCIDirPathPrepare()
- OCIDirPathLoadStream()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.10 OCIDirPathLoadStream()

Loads the data converted to direct path stream format.

#### Purpose

Loads the data converted to direct path stream format.

#### Syntax

    sword OCIDirPathLoadStream (   OCIDirPathCtx          *dpctx,
                                   OCIDirPathStream       *dpstr,
                                   OCIError               *errhp );

#### Parameters

dpctx (IN)
Direct path context handle for the object loaded.

dpstr (IN)
Direct path stream handle for the stream to load.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

When the interface returns an error, information concerning the row in the column array that sourced the stream can be obtained as an attribute of the direct path stream. Also, the offset into the stream where the error occurred can be obtained as an attribute of the stream.

Return codes for this function are:

- `OCI_SUCCESS` - All data in the stream was successfully loaded.

- `OCI_ERROR` - An error occurred while loading the data. The problem could be a partition mapping error, a `NULL` constraint violation, a function-based index evaluation error, or an out of space condition, such as cannot allocate extent. `OCI_ATTR_ROW_COUNT` is the number of rows successfully loaded in the last call.

- `OCI_NEED_DATA` - Last row was not complete. The caller must supply another row piece. If the stream was sourced from a column array, the attribute `OCI_ATTR_ROW_COUNT` is the number of complete rows successfully loaded in the last call.

- `OCI_NO_DATA` - Attempt to load an empty stream or a stream that has been completely processed.

A stream must be repeatedly loaded until `OCI_SUCCESS`, `OCI_NEED_DATA`, or `OCI_NO_DATA` is returned. For example, a stream cannot be reset if `OCI_ERROR` is returned from `OCIDirPathLoadStream()`.

**Related Topics**

- OCIDirPathAbort()
- OCIDirPathDataSave()
- OCIDirPathFinish()
- OCIDirPathPrepare()
- OCIDirPathStreamReset()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.11 OCIDirPathPrepare()

#### Purpose

Prepares the direct path load interface before any rows can be converted or loaded.

#### Syntax

    sword OCIDirPathPrepare (   OCIDirPathCtx          *dpctx,
                                OCISvcCtx              *svchp,
                                OCIError               *errhp );

#### Parameters

dpctx (IN)
Direct path context handle for the object loaded.

svchp (IN)
Service context.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

After the name of the object to be operated on is set, the external attributes of the column data are set, and all load options are set, the direct path interface must be prepared with `OCIDirPathPrepare()` before any rows can be converted or loaded.

A return value of `OCI_SUCCESS` indicates that the backend has been properly initialized for a direct path load operation. A nonzero return indicates an error. Possible errors are:

- Invalid context

- Not connected to a server

- Object name not set

- Already prepared (cannot prepare twice)

- Object not suitable for a direct path operation

**Related Topics**

- OCIDirPathAbort()
- OCIDirPathDataSave()
- OCIDirPathFinish()
- OCIDirPathStreamReset()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.5.12 OCIDirPathStreamReset()

Resets the direct path stream state.

#### Purpose

Resets the direct path stream state.

#### Syntax

    sword OCIDirPathStreamReset ( OCIDirPathStream       *dpstr,
                                  OCIError               *errhp );

#### Parameters

dpstr (IN)
Direct path stream handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

A direct path stream maintains the state that indicates where the next `OCIDirPathColArrayToStream()` call should start writing into the stream. Normally, data is appended to the end of the stream. A stream cannot be reset until it is successfully loaded (the loading returned `OCI_SUCCESS`, `OCI_NEED_DATA`, or `OCI_NO_DATA`).

**Related Topics**

- OCIDirPathAbort()
- OCIDirPathDataSave()
- OCIDirPathFinish()
- OCIDirPathPrepare()
- OCIDirPathColArrayToStream()
- [OCIErrorGet()](miscellaneous-functions.md)
