Lists and describes the statement functions.

Table 26-1 lists the statement functions that are described in this section. Use functions that end in "2" for all new applications.

Table 26-1 Statement Functions  

| Function               | Purpose                                                                                                                             |
|:-----------------------|:------------------------------------------------------------------------------------------------------------------------------------|
| OCIStmtExecute()       | Send statements to server for execution                                                                                             |
| OCIStmtFetch2()        | Fetch rows from a query and fetches a row from the (scrollable) result set                                                          |
| OCIStmtGetNextResult() | Returns the implicit results from an executed PL/SQL statement handle                                                               |
| OCIStmtGetPieceInfo()  | Get piece information for piecewise operations                                                                                      |
| OCIStmtPrepare2()      | Prepare a SQL or PL/SQL statement for execution. The user also has the option of using the statement cache, if it has been enabled. |
| OCIStmtRelease()       | Release the statement handle                                                                                                        |
| OCIStmtSetPieceInfo()  | Set piece information for piecewise operations                                                                                      |

### 26.2.1 OCIStmtExecute()

Associates an application request with a server.

#### Purpose

Associates an application request with a server.

#### Syntax

    sword OCIStmtExecute ( OCISvcCtx           *svchp,
                           OCIStmt             *stmtp,
                           OCIError            *errhp,
                           ub4                  iters,
                           ub4                  rowoff,
                           const OCISnapshot   *snap_in,
                           OCISnapshot         *snap_out,
                           ub4                  mode );

#### Parameters

svchp (IN/OUT)
Service context handle.

stmtp (IN/OUT)
A statement handle. It defines the statement and the associated data to be executed at the server. It is invalid to pass in a statement handle that has bind of data types only supported in release 8.x or later, when `svchp` points to an Oracle7 server.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information, when there is an error.

iters (IN)
For non-`SELECT` statements, the number of times this statement is executed equals `iters `- `rowoff`.

For `SELECT` statements, if `iters` is nonzero, then defines must have been done for the statement handle. The execution fetches `iters` rows into these predefined buffers and prefetches more rows depending upon the prefetch row count. If you do not know how many rows the `SELECT` statement retrieves, then set `iters` to zero.

This function returns an error if `iters`=0 for non-`SELECT` statements.

This function returns an error if `iters` is not 1 for DDL statements.

**Note:**

For array DML operations, set `iters` \<= 32767 to get better performance.

rowoff (IN)
The starting index from which the data in an array bind is relevant for this multiple row execution.

snap_in (IN)
This parameter is optional. If it is supplied, then it must point to a snapshot descriptor of type `OCI_DTYPE_SNAP`. The contents of this descriptor must be obtained from the `snap_out` parameter of a previous call. The descriptor is ignored if the SQL is not a `SELECT` statement. This facility allows multiple service contexts to Oracle Database to see the same consistent snapshot of the database's committed data. However, uncommitted data in one context is not visible to another context even using the same snapshot.

snap_out (OUT)
This parameter is optional. If it is supplied, then it must point to a descriptor of type `OCI_DTYPE_SNAP`. This descriptor is filled in with an opaque representation that is the current Oracle Database system change number (SCN) suitable as a `snap_in` input to a subsequent call to `OCIStmtExecute()`. To avoid "snapshot too old" errors, do not use this descriptor any longer than necessary.

mode (IN)
The modes are:

- `OCI_BATCH_ERRORS` - See [Using Batch Error Mode](using-sql_statements-in-oci.md) for information about this mode.

- `OCI_COMMIT_ON_SUCCESS` - When a statement is executed in this mode, the current transaction is committed after execution, if execution completes successfully.

- `OCI_DEFAULT` - Calling `OCIStmtExecute()` in this mode executes the statement. It also implicitly returns describe information about the select list.

- `OCI_DESCRIBE_ONLY` - This mode is for users who want to describe a query before execution. Calling `OCIStmtExecute()` in this mode does not execute the statement, but it does return the select-list description. To maximize performance, Oracle recommends that applications execute the statement in default mode and use the implicit describe that accompanies the execution.

- `OCI_EXACT_FETCH` - Used when the application knows in advance exactly how many rows it is fetching. This mode turns prefetching off for Oracle Database release 8 or later mode, and requires that defines be done before the execute call. Using this `mode` cancels the cursor after the desired rows are fetched and may result in reduced server-side resource usage.

- `OCI_PARSE_ONLY` - This mode allows the user to parse the query before execution. Executing in this mode parses the query and returns parse errors in the SQL, if any. Users must note that this involves an additional round-trip to the server. To maximize performance, Oracle recommends that the user execute the statement in the default mode, which, parses the statement as part of the bundled operation.

- `OCI_STMT_SCROLLABLE_READONLY` - Required for the result set to be scrollable. The result set cannot be updated. See [About Fetching Results](using-sql_statements-in-oci.md) for more information about this mode. This mode cannot be used with any other mode.

  `OCI_RETURN_ROW_COUNT_ARRAY` - This mode allows the user to get DML rowcounts per iteration. It is an error to pass this mode for statements that are not DMLs. See [Statement Handle Attributes](handle-and-descriptor-attributes.md) for more information. This mode can be used along with `OCI_BATCH_ERRORS`.

The modes are not mutually exclusive; you can use them together, except for `OCI_STMT_SCROLLABLE_READONLY`.

#### Comments

This function is used to execute a prepared SQL statement. Using an execute call, the application associates a request with a server.

If a `SELECT` statement is executed, then the description of the select list is available implicitly as a response. This description is buffered on the client side for describes, fetches, and define type conversions. Hence it is optimal to describe a select list only after an execute.

**See Also:**

[About Describing Select-List Items](using-sql_statements-in-oci.md)

Also for `SELECT` statements, some results are available implicitly. Rows are received and buffered at the end of the execute. For queries with small row count, a prefetch causes memory to be released in the server if the end of fetch is reached, an optimization that may result in memory usage reduction. The set attribute call has been defined to set the number of rows to be prefetched for each result set.

For `SELECT` statements, at the end of the execute, the statement handle implicitly maintains a reference to the service context on which it is executed. It is the developer's responsibility to maintain the integrity of the service context. The implicit reference is maintained until the statement handle is freed or the fetch is canceled or an end of fetch condition is reached.

To reexecute a DDL statement, you must prepare the statement again using `OCIStmtPrepare2()`.

**Note:**

If output variables are defined for a `SELECT` statement before a call to `OCIStmtExecute()`, the number of rows specified by `iters` are fetched directly into the defined output buffers and additional rows equivalent to the prefetch count are prefetched. If there are no additional rows, then the fetch is complete without calling OCIStmtFetch2() or deprecated [OCIStmtFetch()](deprecated-oci-functions.md).

**Related Topics**

- OCIStmtPrepare2()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Polling Mode Operations in OCI](oci-programming-basics.md)

### 26.2.2 OCIStmtFetch2()

Fetches a row from the (scrollable) result set.

#### Purpose

Fetches a row from the (scrollable) result set. You are encouraged to use this fetch call instead of the deprecated call `OCIStmtFetch()`.

#### Syntax

    sword OCIStmtFetch2 ( OCIStmt     *stmthp,
                          OCIError    *errhp,
                          ub4          nrows,
                          ub2          orientation,
                          sb4          fetchOffset,
                          ub4          mode );

#### Parameters

stmthp (IN/OUT)
This is the statement handle of the (scrollable) result set.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information if an error occurs.

nrows (IN)
Number of rows to be fetched from the current position.

orientation (IN)
The acceptable values are:

- `OCI_DEFAULT` - Has the same effect as `OCI_FETCH_NEXT`

- `OCI_FETCH_CURRENT` - Gets the current row.

- `OCI_FETCH_NEXT` - Gets the next row from the current position. It is the default (has the same effect as `OCI_DEFAULT`). Use for a nonscrollable statement handle.

- `OCI_FETCH_FIRST` - Gets the first row in the result set.

- `OCI_FETCH_LAST` - Gets the last row in the result set.

- `OCI_FETCH_PRIOR` - Positions the result set on the previous row from the current row in the result set. You can fetch multiple rows using this mode, from the "previous row" also.

- `OCI_FETCH_ABSOLUTE` - Fetches the row number (specified by `fetchOffset` parameter) in the result set using absolute positioning.

- `OCI_FETCH_RELATIVE` - Fetches the row number (specified by `fetchOffset` parameter) in the result set using relative positioning.

fetchOffset (IN)
The offset to be used with the orientation parameter for changing the current row position.

mode (IN)
Pass in `OCI_DEFAULT`.

#### Comments

The fetch call works similarly to the deprecated `OCIStmtFetch()` call, but with the addition of the `fetchOffset` parameter. It can be used on any statement handle, whether it is scrollable or not. For a nonscrollable statement handle, the only acceptable value of `orientation` is `OCI_FETCH_NEXT`, and the `fetchOffset` parameter is ignored.

For new applications you are encouraged to use this call, `OCIStmtFetch2()`.

A `fetchOffset` with `orientation` set to `OCI_FETCH_RELATIVE` is equivalent to all of the following:

- `OCI_FETCH_CURRENT` with a value of `fetchOffset` equal to 0

- `OCI_FETCH_NEXT` with a value of `fetchOffset` equal to 1

- `OCI_FETCH_PRIOR` with a value of `fetchOffset` equal to -1

`OCI_ATTR_UB8_ROW_COUNT` contains the highest absolute row value that was fetched.

All other orientation modes besides `OCI_FETCH_ABSOLUTE` and `OCI_FETCH_RELATIVE` ignore the `fetchOffset` value.

This call can also be used to determine the number of rows in the result set by using `OCI_FETCH_LAST` and then calling `OCIAttrGet()` on `OCI_ATTR_CURRENT_POSITION`. But the response time of this call can be high. If `nrows` is set to be greater than 1 with `OCI_FETCH_LAST` orientation, nrows is considered to be 1.

The return codes are the same as for deprecated `OCIStmtFetch()`, except that `OER(1403)` with return code `OCI_NO_DATA` is returned every time a fetch on a scrollable statement handle (or execute) is made and not all rows requested by the application could be fetched.

If you call `OCIStmtFetch2()` with the `nrows` parameter set to 0, this cancels the cursor.

The scrollable statement handle must be explicitly canceled (that is, fetch with 0 rows) or freed to release server-side resources for the scrollable cursor. A nonscrollable statement handle is implicitly canceled on receiving the `OER(1403)`.

Use `OCI_ATTR_ROWS_FETCHED` to find the number of rows that were successfully fetched into the user's buffers in the last fetch call.

**Related Topics**

- [OCIStmtFetch()](deprecated-oci-functions.md)
- OCIStmtExecute()
- [OCIBindByPos()](bind-define-describe-functions.md)
- [OCIBindByPos2()](bind-define-describe-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
- [About Using Scrollable Cursors in OCI](using-sql_statements-in-oci.md)
- [Polling Mode Operations in OCI](oci-programming-basics.md)

### 26.2.3 OCIStmtGetNextResult()

Returns the implicit results from an executed PL/SQL statement handle.

#### Purpose

Returns the implicit results from an executed PL/SQL statement handle.

#### Syntax

    sword OCIStmtGetNextResult (OCIStmt   *stmthp,
                                OCIError  *errhp,
                                void     **result,
                                ub4       *rtype,
                                ub4        mode)

#### Parameters

stmthp (IN)
The executed statement handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

result (OUT)
The next implicit result from the executed PL/SQL statement.

rtype (OUT)
The type of the implicit result. The only possible value is `OCI_RESULT_TYPE_SELECT`.

mode (IN)
The only possible value is `OCI_DEFAULT` (default mode).

#### Comments

Each call to `OCIStmtGetNextResult()` retrieves a single implicit result in the order in which they were returned from the PL/SQL procedure or block. If no more results are available, then `OCI_NO_DATA` is returned. If `rtype` is `OCI_RESULT_TYPE_SELECT`, then the returned result can be cast as an OCI statement handle, and is allocated by OCI. Applications can do normal OCI define and fetch calls to fetch rows from the implicit result sets. The returned OCI statement handle cannot be freed explicitly. All implicit result sets are automatically closed and freed when the top-level statement handle is freed or released.

See [OCI_ATTR_IMPLICIT_RESULT_COUNT](handle-and-descriptor-attributes.md) for information about this statement handle attribute, which returns the total number of implicit results available on the top-level OCI statement handle.

#### Returns

Returns one of the following:

- `OCI_ERROR`

- `OCI_SUCCESS`

- `OCI_NO_DATA` - When all implicit result sets have been retrieved from the top-level statement handle

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 26.2.4 OCIStmtGetPieceInfo()

Returns piece information for a piecewise operation.

#### Purpose

Returns piece information for a piecewise operation.

#### Syntax

    sword OCIStmtGetPieceInfo( const OCIStmt  *stmtp,
                               OCIError       *errhp,
                               void          **hndlpp,
                               ub4            *typep,
                               ub1            *in_outp,
                               ub4            *iterp,
                               ub4            *idxp,
                               ub1            *piecep );

#### Parameters

stmtp (IN)
The statement that when executed returned `OCI_NEED_DATA`.

errhp (OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

hndlpp (OUT)
Returns a pointer to the bind or define handle of the bind or define whose run-time data is required or is being provided.

typep (OUT)
The type of the handle pointed to by `hndlpp`: `OCI_HTYPE_BIND` (for a bind handle) or `OCI_HTYPE_DEFINE` (for a define handle).

in_outp (OUT)
Returns `OCI_PARAM_IN` if the data is required for an IN bind value. Returns `OCI_PARAM_OUT` if the data is available as an OUT bind variable or a define position value.

iterp (OUT)
Returns the row number of a multiple row operation.

idxp (OUT)
The index of an array element of a PL/SQL array bind operation.

piecep (OUT)
Returns one of these defined values: `OCI_ONE_PIECE`, `OCI_FIRST_PIECE`, `OCI_NEXT_PIECE`, or `OCI_LAST_PIECE`.

#### Comments

When an execute or fetch call returns `OCI_NEED_DATA` to get or return a dynamic bind, define value, or piece, `OCIStmtGetPieceInfo()` returns the relevant information: bind or define handle, iteration, index number, and which piece.

**Related Topics**

- [OCIArrayDescriptorAlloc()](handle-and-descriptor-functions.md)
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- OCIStmtExecute()
- OCIStmtFetch2()
- OCIStmtSetPieceInfo()
- [OCIErrorGet()](miscellaneous-functions.md)
- [Polling Mode Operations in OCI](oci-programming-basics.md)

**See Also:**

- [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about using `OCIStmtGetPieceInfo()`

### 26.2.5 OCIStmtPrepare2()

Prepares a SQL or PL/SQL statement for execution.

#### Purpose

Prepares a SQL or PL/SQL statement for execution. The user has the option of using the statement cache, if it has been enabled.

Oracle strongly encourages use of `OCIStmtPrepare2()` in all OCI applications instead of the deprecated call `OCIStmtPrepare()`.

#### Syntax

    sword OCIStmtPrepare2 ( OCISvcCtx      *svchp,
                            OCIStmt       **stmthp,
                            OCIError       *errhp,
                            const OraText  *stmttext,
                            ub4             stmt_len,
                            const OraText  *key,
                            ub4             keylen,
                            ub4             language,
                            ub4             mode );

#### Parameters

svchp (IN)
The service context to be associated with the statement.

stmthp (OUT)
Pointer to the statement handle returned.

errhp (IN)
A pointer to the error handle for diagnostics.

stmttext (IN)
The statement text. The semantics of the `stmttext` are same as those of `OCIStmtPrepare()`; that is, the string must be `NULL`-terminated.

stmt_len (IN)
The statement text length.

key (IN)
For statement caching only. The key to be used for searching the statement in the statement cache. If the key is passed in, then the statement text and other parameters are ignored and the search is solely based on the key.

keylen (IN)
For statement caching only. The length of the key.

language (IN)
Specifies V7, or native syntax. Possible values are as follows:

- `OCI_V7_SYNTAX` - V7 ORACLE parsing syntax.

- `OCI_NTV_SYNTAX` - Syntax depends upon the version of the server.

  `OCI_FOREIGN_SYNTAX` - Specifies the statement to be translated according to the SQL translation profile set in the session.

<!-- -->

mode (IN)
This function can be used with and without statement caching. This is determined at the time of connection or session pool creation. If caching is enabled for a session, then all statements in the session have caching enabled, and if caching is not enabled, then all statements are not cached.

The valid modes are as follows:

- `OCI_DEFAULT` - Caching is not enabled. If the statement is not found in the cache, this mode allocates a new statement handle and prepares the statement handle for execution. If the statement is not found in the cache and one of the following circumstances applies, then the subsequent actions follow:

  - Only the text has been supplied: a new statement is allocated and prepared and returned. The tag `NULL`. `OCI_SUCCESS` is returned.

  - Only the tag has been supplied: `stmthp` is `NULL`. `OCI_ERROR` is returned.

  - Both text and key were supplied: a new statement is allocated and prepared and returned. The tag `NULL`. `OCI_SUCCESS_WITH_INFO` is returned, as the returned statement differs from the requested statement in that the tag is `NULL`.

- `OCI_PREP2_CACHE_SEARCHONLY` - In this case, if the statement is not found (a `NULL` statement handle is returned), you must take further action. If the statement is found, `OCI_SUCCESS` is returned. Otherwise, `OCI_ERROR` is returned.

- `OCI_PREP2_GET_PLSQL_WARNINGS` - If warnings are enabled in the session and the PL/SQL program is compiled with warnings, then `OCI_SUCCESS_WITH_INFO` is the return status from the execution. Use `OCIErrorGet()` to find the new error number corresponding to the warnings.

- `OCI_PREP2_IMPL_RESULTS_CLIENT` - The mode should be passed as `OCI_PREP2_IMPL_RESULTS_CLIENT` when this call is made in an external procedure and implicit results need to be processed. See [OCI Support for Implicit Results](performance-topics.md) for more details.

**Related Topics**

- [OCIStmtPrepare()](deprecated-oci-functions.md)
- OCIStmtRelease()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.2.6 OCIStmtRelease()

Releases the statement handle obtained by a call to `OCIStmtPrepare2()`.

#### Purpose

Releases the statement handle obtained by a call to `OCIStmtPrepare2()`.

#### Syntax

    sword OCIStmtRelease ( OCIStmt        *stmthp,
                           OCIError       *errhp,
                           const OraText  *key,
                           ub4             keylen,
                           ub4             mode );

#### Parameters

stmthp (IN/OUT)
The statement handle returned by `OCIStmtPrepare2()`.

errhp (IN)
The error handle used for diagnostics.

key (IN)
Only valid for statement caching. The key to be associated with the statement in the cache. This is a SQL string passed in by the caller. If a `NULL` key is passed in, the statement is not tagged.

keylen (IN)
Only valid for statement caching. The length of the key.

mode (IN)
The valid modes are:

- `OCI_DEFAULT`

- `OCI_STRLS_CACHE_DELETE` - Only valid for statement caching. The statement is not kept in the cache anymore.

**Related Topics**

- OCIStmtPrepare2()

### 26.2.7 OCIStmtSetPieceInfo()

Sets piece information for a piecewise operation.

#### Purpose

Sets piece information for a piecewise operation.

#### Syntax

    sword OCIStmtSetPieceInfo ( void              *hndlp,
                                ub4                type,
                                OCIError          *errhp,
                                const void        *bufp,
                                ub4               *alenp,
                                ub1                piece,
                                const void        *indp,
                                ub2               *rcodep );

#### Parameters

hndlp (IN/OUT)
The bind or define handle.

type (IN)
Type of the handle.

errhp (OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

bufp (IN/OUT)
A pointer to storage containing the data value or the piece when it is an IN bind variable; otherwise, `bufp` is a pointer to storage for getting a piece or a value for OUT binds and define variables. For named data types or `REF`s, a pointer to the object or `REF` is returned.

alenp (IN/OUT)
The length of the piece or the value. Do not change this parameter between executions of the same SQL statement.

piece (IN)
The piece parameter. Valid values are:

- `OCI_ONE_PIECE`

- `OCI_FIRST_PIECE`

- `OCI_NEXT_PIECE`

- `OCI_LAST_PIECE`

This parameter is used for IN bind variables only.

indp (IN/OUT)
Indicator. A pointer to an `sb2` value or pointer to an indicator structure for named data types (SQLT_NTY) and `REF`s (SQLT_REF), that is, depending upon the data type, `*indp` is either an `sb2` or a `void `\*.

rcodep (IN/OUT)
Return code.

#### Comments

When an execute call returns `OCI_NEED_DATA` to get a dynamic IN/OUT bind value or piece, `OCIStmtSetPieceInfo()` sets the piece information: the buffer, the length, which piece is currently being processed, the indicator, and the return code for this column.

**Related Topics**

- [OCIArrayDescriptorAlloc()](handle-and-descriptor-functions.md)
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- OCIStmtExecute()
- OCIStmtFetch2()
- OCIStmtGetPieceInfo()
- [OCIErrorGet()](miscellaneous-functions.md)
- [Polling Mode Operations in OCI](oci-programming-basics.md)

**See Also:**

- [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about using `OCIStmtSetPieceInfo()`
