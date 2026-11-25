Lists and describes the bind, define, and describe functions.

Table 25-4 lists the bind, define, and describe functions that are described in this section.

Table 25-4 Bind, Define, and Describe Functions 

| Function                 | Purpose                                                                                          |
|:-------------------------|:-------------------------------------------------------------------------------------------------|
| OCIBindArrayOfStruct()   | Set skip parameters for static array bind                                                        |
| OCIBindByName()          | Bind by name                                                                                     |
| OCIBindByName2()         | Bind by name. Use when return lengths exceed `UB2MAXVAL` on the client.                          |
| OCIBindByPos()           | Bind by position                                                                                 |
| OCIBindByPos2()          | Bind by position. Use when return lengths exceed `UB2MAXVAL` on the client.                      |
| OCIBindDynamic()         | Set additional attributes after bind with `OCI_DATA_AT_EXEC` mode                                |
| OCIBindObject()          | Set additional attributes for bind of named data type                                            |
| OCIDefineArrayOfStruct() | Set additional attributes for static array define                                                |
| OCIDefineByPos()         | Define an output variable association                                                            |
| OCIDefineByPos2()        | Define an output variable association. Use when return lengths exceed `UB2MAXVAL` on the client. |
| OCIDefineDynamic()       | Set additional attributes for define in `OCI_DYNAMIC_FETCH` mode                                 |
| OCIDefineObject()        | Set additional attributes for define of named data type                                          |
| OCIDescribeAny()         | Describe existing schema objects                                                                 |
| OCIStmtGetBindInfo()     | Get bind and indicator variable names and handle                                                 |

### 25.4.1 OCIBindArrayOfStruct()

Sets up the skip parameters for a static array bind.

#### Purpose

Sets up the skip parameters for a static array bind.

#### Syntax

    sword OCIBindArrayOfStruct ( OCIBind     *bindp,
                                 OCIError    *errhp,
                                 ub4          pvskip,
                                 ub4          indskip,
                                 ub4          alskip,
                                 ub4          rcskip );

#### Parameters

bindp (IN/OUT)
The handle to a bind structure.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

pvskip (IN)
Skip parameter for the next data value.

indskip (IN)
Skip parameter for the next indicator value or structure.

alskip (IN)
Skip parameter for the next actual length value.

rcskip (IN)
Skip parameter for the next column-level return code value.

#### Comments

This call sets up the skip parameters necessary for a static array bind. It follows a call to `OCIBindByName()` or `OCIBindByPos()`. The bind handle returned by that initial bind call is used as a parameter for the `OCIBindArrayOfStruct()` call.

**Related Topics**

- OCIBindByName()
- OCIBindByName2()
- OCIBindByPos()
- OCIBindByPos2()

**See Also:**

[About Binding and Defining Arrays of Structures in OCI](binding-and-defining-in-oci.md) for information about skip parameters

### 25.4.2 OCIBindByName()

Creates an association between a program variable and a placeholder in a SQL statement or PL/SQL block.

#### Purpose

Creates an association between a program variable and a placeholder in a SQL statement or PL/SQL block.

#### Syntax

    sword OCIBindByName ( OCIStmt         *stmtp,
                          OCIBind        **bindpp,
                          OCIError        *errhp,
                          const OraText   *placeholder,
                          sb4              placeh_len,
                          void            *valuep,
                          sb4              value_sz,
                          ub2              dty,
                          void            *indp,
                          ub2             *alenp,
                          ub2             *rcodep,
                          ub4              maxarr_len,
                          ub4             *curelep,
                          ub4              mode );

#### Parameters

stmtp (IN/OUT)
The statement handle to the SQL or PL/SQL statement being processed.

bindpp (IN/OUT)
A pointer to save the pointer of a bind handle that is implicitly allocated by this call. The bind handle maintains all the bind information for this particular input value. The default encoding for the call depends on the `UTF-16` setting in `stmtp` unless the `mode` parameter has a different value. The handle is freed implicitly when the statement handle is deallocated. On input, the value of the pointer must be `NULL` or a valid bind handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

placeholder (IN)
The placeholder, specified by its name, that maps to a variable in the statement associated with the statement handle. The encoding of `placeholder` should always be consistent with that of the environment. That is, if the statement is prepared in `UTF-16`, so is the placeholder. As a string type parameter, the placeholder should be cast as `(text *)` and terminated with `NULL`.

placeh_len (IN)
The length of the name specified in `placeholder`, in number of bytes regardless of the encoding.

valuep (IN/OUT)
The pointer to a data value or an array of data values of type specified in the `dty` parameter. This data could be a `UTF-16` (formerly known as UCS-2) string, if an `OCIAttrSet()` function has been called to set `OCI_ATTR_CHARSET_ID` as `OCI_UTF16ID` or the deprecated `OCI_UCS2ID`. `OCI_UTF16ID` is the new designation for `OCI_UCS2ID`.

Furthermore, as pointed out for `OCIStmtPrepare2()` , the default encoding for the string type `valuep` is in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`, unless you call `OCIAttrSet()` to manually reset the character set for the bind handle.

**See Also:**

[Bind Handle Attributes](handle-and-descriptor-attributes.md)

An array of data values can be specified for mapping into a PL/SQL table or for providing data for SQL multiple-row operations. When an array of bind values is provided, this is called an array bind in OCI terms.

For `SQLT_NTY` or `SQLT_REF` binds, the `valuep` parameter is ignored. The pointers to OUT buffers are set in the `pgvpp` parameter initialized by `OCIBindObject()`.

When `mode` is set to `OCI_IOV`, pass the base address of the `OCIIOV` struct.

value_sz (IN)
The maximum size possible in bytes of any data value (passed using `valuep`) for this bind variable. This size is always expected to be the size in bytes. In the case of an array bind, this is the maximum size of any element possible with the actual sizes being specified in the `alenp` parameter.

For descriptors, locators, or REFs, whose size is unknown to client applications, use the size of the pointer to the specific type; for example, `sizeof` (`OCILobLocator *`).

The same applies even when mode is `OCI_IOV`.

dty (IN)
The data type of the values being bound. Named data types (`SQLT_NTY`) and `REF`s (`SQLT_REF`) are valid only if the application has been initialized in object mode. For named data types or `REF`s, additional calls must be made with the bind handle to set up the data type-specific attributes. See Comments for information about records, collections, and Booleans. For named data type `SQLT_CHR`, `OCIBindByName()` trims trailing blanks when the actual length is 0. Specify the actual length to prevent trailing blanks from being trimmed.

indp (IN/OUT)
Pointer to an indicator variable or array. For all data types except `SQLT_NTY`, this is a pointer to `sb2` or an array of `sb2`.

For `SQLT_NTY`, this pointer is ignored, and the actual pointer to the indicator structure or an array of indicator structures is initialized in a subsequent call to `OCIBindObject()`. This parameter is ignored for dynamic binds.

**See Also:**

[Indicator Variables](oci-programming-basics.md)

<!-- -->

alenp (IN/OUT)
Pointer to the array of actual lengths of array elements.

When `OCIEnvNlsCreate()` (which is the recommended OCI environment handle creation interface) is used, then `alenp` lengths are consistently expected in bytes (for IN binds) and reported in bytes for OUT binds. The same treatment consistently also holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types. There are no special exceptions for UCS2 or for NCHAR cases.

When the older OCI environment handle creation interfaces are used (either `OCIEnvCreate()`) or deprecated `OCIEnvInit()`), `alenp` lengths are in bytes in general. However, `alenp` lengths are expected in characters for IN binds and also reported in characters for OUT binds only when either the character set is OCI_UC2ID (= OCI_UTF16ID) or when `OCI_ATTR_CHAR_COUNT` attribute is set on the corresponding OCIBind handle. The same treatment holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types.

This parameter is ignored for dynamic binds.

rcodep (OUT)
Pointer to the array of column-level return codes. This parameter is ignored for dynamic binds.

maxarr_len (IN)
A maximum array length parameter (the maximum possible number of elements the user's array can accommodate). Used only for PL/SQL indexed table bindings.

curelep (IN/OUT)
Current array length parameter (a pointer to the actual number of elements in the array before or after the execute operation). Used only for PL/SQL indexed table bindings.

mode (IN)
To maintain coding consistency, theoretically this parameter can take all three possible values used by `OCIStmtPrepare2()`. Because the encoding of bind variables should always be same as that of the statement containing this variable, an error is raised if you specify an encoding other than that of the statement. So the recommended setting for `mode` is `OCI_DEFAULT`, which makes the bind variable have the same encoding as its statement.

The valid modes are:

- `OCI_DEFAULT` - The default mode. The statement handle that `stmtp` uses whatever is specified by its parent environment handle.

- `OCI_BIND_SOFT` - Soft bind mode. This mode increases the performance of the call. If this is the first bind or some input value like `dty` or `value_sz` is changed from the previous bind, this mode is ignored. An error is returned if the statement is not executed. Unexpected behavior results if the bind handle passed is not valid.

- `OCI_DATA_AT_EXEC` - When this mode is selected, the `value_sz` parameter defines the maximum size of the data that can be provided at run time. The application must be ready to provide the OCI library runtime IN data buffers at any time and any number of times. Runtime data is provided in one of these two ways:

  - Callbacks using a user-defined function that must be registered with a subsequent call to `OCIBindDynamic()`.

  - A polling mechanism using calls supplied by the OCI. This mode is assumed if no callbacks are defined.

    **See Also:**

    [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about using the `OCI_DATA_AT_EXEC` mode

  When `mode` is set to `OCI_DATA_AT_EXEC`, do not provide values for `valuep`, `indp`, `alenp`, and `rcodep` in the main call. Pass zeros (0) for `indp` and `alenp`. Provide the values through the callback function registered using `OCIBindDynamic()`.

- `OCI_IOV` - Bind noncontiguous addresses of data. The `valuep` parameter must be of the type `OCIIOV *`. This mode is intended to be used for scatter or gather binding, which allows multiple buffers to be bound or defined to a position, for example column A for the first 10 rows in one buffer, next 5 rows in one buffer, and the remaining 25 rows in another buffer. That eliminates the need to allocate and copy all of them into one big buffer while doing the array execute operation.

  **See Also:**

  [About Binding and Defining Multiple Buffers](binding-and-defining-in-oci.md)

When the allocated buffers are not required anymore, they should be freed by the client.

#### Comments

This call is used to perform a basic bind operation. The bind creates an association between the address of a program variable and a placeholder in a SQL statement or PL/SQL block. The bind call also specifies the type of data that is being bound, and may also indicate the method by which data is provided at run time.

Encoding is determined by either the bind handle using the setting in the statement handle as default, or you can override the setting by specifying the `mode` parameter explicitly.

The `OCIBindByName()` and `OCIBimdByName2()` also implicitly allocates the bind handle indicated by the `bindpp` parameter. If a non-`NULL` pointer is passed in `**bindpp`, the OCI assumes that this points to a valid handle that has been previously allocated with a call to `OCIHandleAlloc()` or `OCIBindByName()`.

Data in an OCI application can be bound to placeholders statically or dynamically. Binding is static when all the IN bind data and the OUT bind buffers are well defined just before the execute operation. Binding is dynamic when the IN bind data and the OUT bind buffers are provided by the application on demand at execution time to the client library. Dynamic binding is indicated by setting the `mode` parameter of this call to `OCI_DATA_AT_EXEC`.

**See Also:**

[Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about dynamic binding

Both `OCIBindByName()` and `OCIBindByName2()` and `OCIBindByPos()` and `OCIBindByPos2()` take as a parameter a bind handle, which is implicitly allocated by the bind call. A separate bind handle is allocated for each placeholder the application is binding.

Additional bind calls may be required to specify particular attributes necessary when binding certain data types or handling input data in certain ways:

- If arrays of structures are being used, `OCIBindArrayOfStruct()` must be called to set up the necessary skip parameters.

- If data is being provided dynamically at run time, and the application uses user-defined callback functions, `OCIBindDynamic()` must be called to register the callbacks.

- If lengths in `alenp` greater than 64 Kilobytes (KB) are required, use `OCIBindDynamic()`.

- If a named data type is being bound, `OCIBindObject()` must be called to specify additional necessary information.

- If a statement with the `RETURNING` clause is used, a call to `OCIBindDynamic()` must follow this call.

With IN binds, the values for each element of the array, the actual lengths of each element, and the actual array length must be set up before the call to `OCIStmtExecute()`.

With OUT binds, the values for each element of the array, the actual lengths of each element, and the actual array length are returned from the server after the `OCIStmtExecute()` call.

For Records
Clients must bind package record types using `SQLT_NTY` as the DTY of the bind. In the OCI client, objects and records are represented as Named Types (NTY) and must use the same `SQLT` code.

For Collections
Clients must bind all package collection types using `SQLT_NTY`. This is the DTY used to bind all schema level collection types.

For Booleans
Clients must bind Boolean types (`OCI_TYPECODE_BOOLEAN`) using `SQLT_BOL`.

**Related Topics**

- OCIBindDynamic()
- OCIBindObject()
- OCIBindArrayOfStruct()
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- [OCIStmtPrepare2()](statement-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvInit()](deprecated-oci-functions.md)
- OCIBindByName2()
- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- OCIBindByPos2()
- [OCIStmtExecute()](statement-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.4.3 OCIBindByName2()

Creates an association between a program variable and a placeholder in a SQL statement or PL/SQL block. Use this function when working with data types when actual lengths exceed `UB2MAXVAL` on the client.

#### Purpose

Creates an association between a program variable and a placeholder in a SQL statement or PL/SQL block. Use this call instead of `OCIBindByName()` when working with data types when actual lengths exceed `UB2MAXVAL` on the client.

#### Syntax

    sword OCIBindByName2 ( OCIStmt         *stmtp,
                           OCIBind        **bindpp,
                           OCIError        *errhp,
                           const OraText   *placeholder,
                           sb4              placeh_len,
                           void            *valuep,
                           sb8              value_sz,
                           ub2              dty,
                           void            *indp,
                           ub4             *alenp,
                           ub2             *rcodep,
                           ub4              maxarr_len,
                           ub4             *curelep,
                           ub4              mode );

#### Parameters

stmtp (IN/OUT)
The statement handle to the SQL or PL/SQL statement being processed.

bindpp (IN/OUT)
A pointer to save the pointer of a bind handle that is implicitly allocated by this call. The bind handle maintains all the bind information for this particular input value. The default encoding for the call depends on the `UTF-16` setting in `stmtp` unless the `mode` parameter has a different value. The handle is freed implicitly when the statement handle is deallocated. On input, the value of the pointer must be `NULL` or a valid bind handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

placeholder (IN)
The placeholder, specified by its name, that maps to a variable in the statement associated with the statement handle. The encoding of `placeholder` should always be consistent with that of the environment. That is, if the statement is prepared in `UTF-16`, so is the placeholder. As a string type parameter, the placeholder should be cast as `(text *)` and terminated with `NULL`.

placeh_len (IN)
The length of the name specified in `placeholder`, in number of bytes regardless of the encoding.

valuep (IN/OUT)
The pointer to a data value or an array of data values of type specified in the `dty` parameter. This data could be a `UTF-16` (formerly known as UCS-2) string, if an `OCIAttrSet()` function has been called to set `OCI_ATTR_CHARSET_ID` as `OCI_UTF16ID` or the deprecated `OCI_UCS2ID`. `OCI_UTF16ID` is the new designation for `OCI_UCS2ID`.

Furthermore, as pointed out for `OCIStmtPrepare2()`, the default encoding for the string type `valuep` is in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`, unless you call `OCIAttrSet()` to manually reset the character set for the bind handle.

**See Also:**

[Bind Handle Attributes](handle-and-descriptor-attributes.md)

An array of data values can be specified for mapping into a PL/SQL table or for providing data for SQL multiple-row operations. When an array of bind values is provided, this is called an array bind in OCI terms.

For `SQLT_NTY` or `SQLT_REF` binds, the `valuep` parameter is ignored. The pointers to OUT buffers are set in the `pgvpp` parameter initialized by `OCIBindObject()`.

When `mode` is set to `OCI_IOV`, pass the base address of the `OCIIOV` struct.

value_sz (IN)
The maximum size possible in bytes of any data value (passed using `valuep`) for this bind variable. This size is always expected to be the size in bytes. In the case of an array bind, this is the maximum size of any element possible with the actual sizes being specified in the `alenp` parameter.

If the value of `value_sz` \> `SB4MAXVAL`, an `ORA-24452` error will be issued, meaning that values \> `SB4MAXVAL` are not supported in Release 12.1 or later.

For descriptors, locators, or REFs, whose size is unknown to client applications, use the size of the pointer to the specific type; for example, `sizeof` (`OCILobLocator *`).

The same applies even when mode is `OCI_IOV`.

dty (IN)
The data type of the values being bound. Named data types (`SQLT_NTY`) and `REF`s (`SQLT_REF`) are valid only if the application has been initialized in object mode. For named data types or `REF`s, additional calls must be made with the bind handle to set up the data type-specific attributes. See Comments for information about records, collections, and Booleans. For named data type `SQLT_CHR`, `OCIBindByName2()` trims trailing blanks when the actual length is 0. Specify the actual length to prevent trailing blanks from being trimmed.

indp (IN/OUT)
Pointer to an indicator variable or array. For all data types except `SQLT_NTY`, this is a pointer to `sb2` or an array of `sb2`.

For `SQLT_NTY`, this pointer is ignored, and the actual pointer to the indicator structure or an array of indicator structures is initialized in a subsequent call to `OCIBindObject()`. This parameter is ignored for dynamic binds.

**See Also:**

[Indicator Variables](oci-programming-basics.md)

<!-- -->

alenp (IN/OUT)
Pointer to the array of actual lengths of array elements.

When `OCIEnvNlsCreate()` (which is the recommended OCI environment handle creation interface) is used, then `alenp` lengths are consistently expected in bytes (for IN binds) and reported in bytes for OUT binds. The same treatment consistently also holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types. There are no special exceptions for UCS2 or for NCHAR cases.

When the older OCI environment handle creation interfaces are used (either `OCIEnvCreate()`) or deprecated `OCIEnvInit()`), `alenp` lengths are in bytes in general. However, `alenp` lengths are expected in characters for IN binds and also reported in characters for OUT binds only when either the character set is OCI_UC2ID (= OCI_UTF16ID) or when `OCI_ATTR_CHAR_COUNT` attribute is set on the corresponding OCIBind handle. The same treatment holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types.

This parameter is ignored for dynamic binds.

rcodep (OUT)
Pointer to the array of column-level return codes. This parameter is ignored for dynamic binds.

maxarr_len (IN)
A maximum array length parameter (the maximum possible number of elements the user's array can accommodate). Used only for PL/SQL indexed table bindings.

curelep (IN/OUT)
Current array length parameter (a pointer to the actual number of elements in the array before or after the execute operation). Used only for PL/SQL indexed table bindings.

mode (IN)
To maintain coding consistency, theoretically this parameter can take all three possible values used by `OCIStmtPrepare2()`. Because the encoding of bind variables should always be same as that of the statement containing this variable, an error is raised if you specify an encoding other than that of the statement. So the recommended setting for `mode` is `OCI_DEFAULT`, which makes the bind variable have the same encoding as its statement.

The valid modes are:

- `OCI_DEFAULT` - The default mode. The statement handle that `stmtp` uses whatever is specified by its parent environment handle.

- `OCI_BIND_SOFT` - Soft bind mode. This mode increases the performance of the call. If this is the first bind or some input value like `dty` or `value_sz` is changed from the previous bind, this mode is ignored. An error is returned if the statement is not executed. Unexpected behavior results if the bind handle passed is not valid.

- `OCI_DATA_AT_EXEC` - When this mode is selected, the `value_sz` parameter defines the maximum size of the data that can be provided at run time. The application must be ready to provide the OCI library runtime IN data buffers at any time and any number of times. Runtime data is provided in one of these two ways:

  - Callbacks using a user-defined function that must be registered with a subsequent call to `OCIBindDynamic()`.

  - A polling mechanism using calls supplied by the OCI. This mode is assumed if no callbacks are defined.

    **See Also:**

    [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about using the `OCI_DATA_AT_EXEC` mode

  When `mode` is set to `OCI_DATA_AT_EXEC`, do not provide values for `valuep`, `indp`, `alenp`, and `rcodep` in the main call. Pass zeros (0) for `indp` and `alenp`. Provide the values through the callback function registered using `OCIBindDynamic()`.

- `OCI_IOV` - Bind noncontiguous addresses of data. The `valuep` parameter must be of the type `OCIIOV *`. This mode is intended to be used for scatter or gather binding, which allows multiple buffers to be bound or defined to a position, for example column A for the first 10 rows in one buffer, next 5 rows in one buffer, and the remaining 25 rows in another buffer. That eliminates the need to allocate and copy all of them into one big buffer while doing the array execute operation.

  **See Also:**

  [About Binding and Defining Multiple Buffers](binding-and-defining-in-oci.md)

When the allocated buffers are not required anymore, they should be freed by the client.

#### Comments

This call is used to perform a basic bind operation. The bind creates an association between the address of a program variable and a placeholder in a SQL statement or PL/SQL block. The bind call also specifies the type of data that is being bound, and may also indicate the method by which data is provided at run time.

Encoding is determined by either the bind handle using the setting in the statement handle as default, or you can override the setting by specifying the `mode` parameter explicitly.

The `OCIBindByName2()` also implicitly allocates the bind handle indicated by the `bindpp` parameter. If a non-`NULL` pointer is passed in `**bindpp`, the OCI assumes that this points to a valid handle that has been previously allocated with a call to `OCIHandleAlloc()` or `OCIBindByName2()`.

Data in an OCI application can be bound to placeholders statically or dynamically. Binding is static when all the IN bind data and the OUT bind buffers are well defined just before the execute operation. Binding is dynamic when the IN bind data and the OUT bind buffers are provided by the application on demand at execution time to the client library. Dynamic binding is indicated by setting the `mode` parameter of this call to `OCI_DATA_AT_EXEC`.

**See Also:**

[Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about dynamic binding

Both `OCIBindByName2()` and `OCIBindByPos2()` take as a parameter a bind handle, which is implicitly allocated by the bind call. A separate bind handle is allocated for each placeholder the application is binding.

Additional bind calls may be required to specify particular attributes necessary when binding certain data types or handling input data in certain ways:

- If arrays of structures are being used, `OCIBindArrayOfStruct()` must be called to set up the necessary skip parameters.

- If data is being provided dynamically at run time, and the application uses user-defined callback functions, `OCIBindDynamic()` must be called to register the callbacks.

- If lengths in `alenp` greater than 64 Kilobytes (KB) are required, use `OCIBindDynamic()`.

- If a named data type is being bound, `OCIBindObject()` must be called to specify additional necessary information.

- If a statement with the `RETURNING` clause is used, a call to `OCIBindDynamic()` must follow this call.

With IN binds, the values for each element of the array, the actual lengths of each element, and the actual array length must be set up before the call to `OCIStmtExecute()`.

With OUT binds, the values for each element of the array, the actual lengths of each element, and the actual array length are returned from the server after the `OCIStmtExecute()` call.

For Records
Clients must bind package record types using `SQLT_NTY` as the DTY of the bind. In the OCI client, objects and records are represented as Named Types (NTY) and must use the same `SQLT` code.

For Collections
Clients must bind all package collection types using `SQLT_NTY`. This is the DTY used to bind all schema level collection types.

For Booleans
Clients must bind Boolean types (`OCI_TYPECODE_BOOLEAN`) using `SQLT_BOL`.

**Related Topics**

- OCIBindDynamic()
- OCIBindObject()
- OCIBindArrayOfStruct()
- OCIBindByName()
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- [OCIStmtPrepare2()](statement-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvInit()](deprecated-oci-functions.md)
- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- OCIBindByPos2()
- [OCIStmtExecute()](statement-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.4.4 OCIBindByPos()

Creates an association between a program variable and a placeholder in a SQL statement or PL/SQL block.

#### Purpose

Creates an association between a program variable and a placeholder in a SQL statement or PL/SQL block.

#### Syntax

    sword OCIBindByPos ( OCIStmt       *stmtp,
                         OCIBind      **bindpp,
                         OCIError      *errhp,
                         ub4            position,
                         void          *valuep,
                         sb4            value_sz,
                         ub2            dty,
                         void          *indp,
                         ub2           *alenp,
                         ub2           *rcodep,
                         ub4            maxarr_len,
                         ub4           *curelep,
                         ub4            mode );

#### Parameters

stmtp (IN/OUT)
The statement handle to the SQL or PL/SQL statement being processed.

bindpp (IN/OUT)
An address of a bind handle that is implicitly allocated by this call. The bind handle maintains all the bind information for this particular input value. The handle is freed implicitly when the statement handle is deallocated. On input, the value of the pointer must be `NULL` or a valid bind handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

position (IN)
The placeholder attributes are specified by position if `OCIBindByPos()` is being called. Positions are 1-based.

valuep (IN/OUT)
An address of a data value or an array of data values of the type specified in the `dty` parameter. An array of data values can be specified for mapping into a PL/SQL table or for providing data for SQL multiple-row operations. When an array of bind values is provided, this is called an array bind in OCI terms.

For a LOB, the buffer pointer must be a pointer to a LOB locator of type `OCILobLocator`. Give the address of the pointer.

For SQLT_NTY or SQLT_REF binds, the `valuep` parameter is ignored. The pointers to OUT buffers are set in the `pgvpp` parameter initialized by `OCIBindObject()`.

If the `OCI_ATTR_CHARSET_ID` attribute is set to `OCI_UTF16ID` (replaces the deprecated `OCI_UCS2ID`, which is retained for backward compatibility), all data passed to and received with the corresponding bind call is assumed to be in `UTF-16` encoding.

When `mode` is set to `OCI_IOV`, pass the base address of the `OCIIOV` struct.

**See Also:**

[Bind Handle Attributes](handle-and-descriptor-attributes.md)

value_sz (IN)
The maximum size possible in bytes of any data value (passed using `valuep`) for this bind variable. This size is always expected to be the size in bytes. In the case of an array bind, this is the maximum size of any element possible with the actual sizes being specified in the `alenp` parameter.

For descriptors, locators, or `REF`s, whose size is unknown to client applications, use the size of the pointer to the specific type; for example, `sizeof` (`OCILobLocator *`).

The same applies even when mode is `OCI_IOV`.

dty (IN)
The data type of the values being bound. Named data types (SQLT_NTY) and `REF`s (SQLT_REF) are valid only if the application has been initialized in object mode. For named data types or `REF`s, additional calls must be made with the bind handle to set up the attributes specific to the data type. See Comments for information about records, collections, and Booleans. For named data type `SQLT_CHR`, `OCIBindByPos()` trims trailing blanks when the actual length is 0. Specify the actual length to prevent trailing blanks from being trimmed.

indp (IN/OUT)
Pointer to an indicator variable or array. For all data types, this is a pointer to `sb2` or an array of `sb2` values. The only exception is SQLT_NTY, where this pointer is ignored and the actual pointer to the indicator structure or an array of indicator structures is initialized by `OCIBindObject()`. The `indp` parameter is ignored for dynamic binds. If `valuep` is an `OUT` parameter, then you must set `indp` to point to `OCI_IND_NULL`.

**See Also:**

[Indicator Variables](oci-programming-basics.md)

alenp (IN/OUT)
Pointer to an array of actual lengths of array elements.

When `OCIEnvNlsCreate()` (which is the recommended OCI environment handle creation interface) is used, then `alenp` lengths are consistently expected in bytes (for IN binds) and reported in bytes for OUT binds. The same treatment consistently also holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types. There are no special exceptions for UCS2 or for NCHAR cases.

When the older OCI environment handle creation interfaces are used (either `OCIEnvCreate()` or deprecated `OCIEnvInit()`), `alenp` lengths are in bytes in general. However, `alenp` lengths are expected in characters for IN binds and also reported in characters for OUT binds only when either the character set is OCI_UC2ID (= OCI_UTF16ID) or when `OCI_ATTR_CHAR_COUNT` attribute is set on the corresponding OCIBind handle. The same treatment holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types.

This parameter is ignored for dynamic binds.

rcodep (OUT)
Pointer to an array of column-level return codes. This parameter is ignored for dynamic binds.

maxarr_len (IN)
A maximum array length parameter (the maximum possible number of elements that the user's array can accommodate). Used only for PL/SQL indexed table bindings.

curelep (IN/OUT)
Current array length parameter (a pointer to the actual number of elements in the array before or after the execute operation). Used only for PL/SQL indexed table bindings.

mode (IN)
The valid modes for this parameter are:

- `OCI_DEFAULT` - This is default mode.

- `OCI_BIND_SOFT` - Soft bind mode. This mode increases the performance of the call. If this is the first bind or some input value like `dty` or `value_sz` is changed from the previous bind, this mode is ignored. An error is returned if the statement is not executed. Unexpected behavior results if the bind handle passed is not valid.

- `OCI_DATA_AT_EXEC` - When this mode is selected, the `value_sz` parameter defines the maximum size of the data that can be provided at run time. The application must be ready to provide the OCI library runtime IN data buffers at any time and any number of times. Runtime data is provided in one of the following ways:

  - Callbacks using a user-defined function that must be registered with a subsequent call to `OCIBindDynamic()`.

  - A polling mechanism using calls supplied by OCI. This mode is assumed if no callbacks are defined.

    **See Also:**

    [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about using the `OCI_DATA_AT_EXEC` mode

    When `mode` is set to `OCI_DATA_AT_EXEC`, do not provide values for `valuep`, `indp`, `alenp`, and `rcodep` in the main call. Pass zeros (0) for `indp` and `alenp`. Provide the values through the callback function registered using `OCIBindDynamic()`.

- `OCI_IOV` - Bind noncontiguous addresses of data. The `valuep` parameter must be of the type `OCIIOV *`. This mode is intended to be used for scatter or gather binding, which allows multiple buffers to be bound or defined to a position, for example column A for the first 10 rows in one buffer, next 5 rows in one buffer, and the remaining 25 rows in another buffer. That eliminates the need to allocate and copy all of them into one big buffer while doing the array execute operation.

  **See Also:**

  [About Binding and Defining Multiple Buffers](binding-and-defining-in-oci.md)

When the allocated buffers are not required anymore, they should be freed by the client.

#### Comments

This call is used to perform a basic bind operation. The bind creates an association between the address of a program variable and a placeholder in a SQL statement or PL/SQL block. The bind call also specifies the type of data that is being bound, and may also indicate the method by which data is to be provided at run time.

This function also implicitly allocates the bind handle indicated by the `bindpp` parameter. If a non-`NULL` pointer is passed in `**bindpp`, OCI assumes that this points to a valid handle that has been previously allocated with a call to `OCIHandleAlloc()` or `OCIBindByPos()`.

Data in an OCI application can be bound to placeholders statically or dynamically. Binding is static when all the IN bind data and the OUT bind buffers are well defined just before the execute operation. Binding is dynamic when the IN bind data and the OUT bind buffers are provided by the application on demand at execution time to the client library. Dynamic binding is indicated by setting the `mode` parameter of this call to `OCI_DATA_AT_EXEC`.

**See Also:**

[Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about dynamic binding

Both `OCIBindByName()` and `OCIBindByPos()` take as a parameter a bind handle, which is implicitly allocated by the bind call. A separate bind handle is allocated for each placeholder the application is binding.

Additional bind calls may be required to specify particular attributes necessary when binding certain data types or handling input data in certain ways:

- If arrays of structures are being used, `OCIBindArrayOfStruct()` must be called to set up the necessary skip parameters.

- If data is being provided dynamically at run time, and the application uses user-defined callback functions, `OCIBindDynamic()` must be called to register the callbacks.

- If lengths in `alenp` greater than 64 KB are required, use `OCIBindDynamic()`.

- If a named data type is being bound, `OCIBindObject()` must be called to specify additional necessary information.

- If a statement with the `RETURNING` clause is used, a call to `OCIBindDynamic()` must follow this call.

With IN binds, the values for each element of the array, the actual lengths of each element, and the actual array length must be set up before the call to `OCIStmtExecute()`.

With OUT binds, the values for each element of the array, the actual lengths of each element, and the actual array length are returned from the server after the`OCIStmtExecute()` call.

For Records
Clients must bind package record types using `SQLT_NTY` as the DTY of the bind. In the OCI client, objects and records are represented as Named Types (NTY) and must use the same `SQLT` code.

For Collections
Clients must bind all package collection types using `SQLT_NTY`. This is the DTY used to bind all schema level collection types.

For Booleans
Clients must bind Boolean types (`OCI_TYPECODE_BOOLEAN`) using `SQLT_BOL`.

**Related Topics**

- OCIBindDynamic()
- OCIBindObject()
- OCIBindArrayOfStruct()
- OCIBindByPos2()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvInit()](deprecated-oci-functions.md)
- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- OCIBindByName()
- [OCIStmtExecute()](statement-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.4.5 OCIBindByPos2()

Creates an association between a program variable and a placeholder in a SQL statement or PL/SQL block. Use this call when working with data types when actual lengths exceed `UB2MAXVAL` on the client.

#### Purpose

Creates an association between a program variable and a placeholder in a SQL statement or PL/SQL block. Use this call instead of `OCIBindByPos()` when working with data types when actual lengths exceed `UB2MAXVAL` on the client.

#### Syntax

    sword OCIBindByPos2 ( OCIStmt      *stmtp,
                          OCIBind     **bindpp,
                          OCIError     *errhp,
                          ub4           position,
                          void         *valuep,
                          sb8           value_sz,
                          ub2           dty,
                          void         *indp,
                          ub4          *alenp,
                          ub2          *rcodep,
                          ub4           maxarr_len,
                          ub4          *curelep,
                          ub4           mode );

#### Parameters

stmtp (IN/OUT)
The statement handle to the SQL or PL/SQL statement being processed.

bindpp (IN/OUT)
An address of a bind handle that is implicitly allocated by this call. The bind handle maintains all the bind information for this particular input value. The handle is freed implicitly when the statement handle is deallocated. On input, the value of the pointer must be `NULL` or a valid bind handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

position (IN)
The placeholder attributes are specified by position if `OCIBindByPos()` is being called. Positions are 1-based.

valuep (IN/OUT)
An address of a data value or an array of data values of the type specified in the `dty` parameter. An array of data values can be specified for mapping into a PL/SQL table or for providing data for SQL multiple-row operations. When an array of bind values is provided, this is called an array bind in OCI terms.

For a LOB, the buffer pointer must be a pointer to a LOB locator of type `OCILobLocator`. Give the address of the pointer.

For SQLT_NTY or SQLT_REF binds, the `valuep` parameter is ignored. The pointers to OUT buffers are set in the `pgvpp` parameter initialized by `OCIBindObject()`.

If the `OCI_ATTR_CHARSET_ID` attribute is set to `OCI_UTF16ID` (replaces the deprecated `OCI_UCS2ID`, which is retained for backward compatibility), all data passed to and received with the corresponding bind call is assumed to be in `UTF-16` encoding.

When `mode` is set to `OCI_IOV`, pass the base address of the `OCIIOV` struct.

**See Also:**

[Bind Handle Attributes](handle-and-descriptor-attributes.md)

value_sz (IN)
The maximum size possible in bytes of any data value (passed using `valuep`) for this bind variable. This size is always expected to be the size in bytes. In the case of an array bind, this is the maximum size of any element possible with the actual sizes being specified in the `alenp` parameter.

If the value of `value_sz` \> `SB4MAXVAL`, an `ORA-24452` error will be issued, meaning that values \> `SB4MAXVAL` are not supported in Release 12.1 or later.

For descriptors, locators, or `REF`s, whose size is unknown to client applications, use the size of the pointer to the specific type; for example, `sizeof` (`OCILobLocator *`).

The same applies even when mode is `OCI_IOV`.

dty (IN)
The data type of the values being bound. Named data types (SQLT_NTY) and `REF`s (SQLT_REF) are valid only if the application has been initialized in object mode. For named data types or `REF`s, additional calls must be made with the bind handle to set up the attributes specific to the data type. See Comments for information about records, collections, and Booleans. For named data type `SQLT_CHR`, `OCIBindByPos2()` trims trailing blanks when the actual length is 0. Specify the actual length to prevent trailing blanks from being trimmed.

indp (IN/OUT)
Pointer to an indicator variable or array. For all data types, this is a pointer to `sb2` or an array of `sb2` values. The only exception is SQLT_NTY, where this pointer is ignored and the actual pointer to the indicator structure or an array of indicator structures is initialized by `OCIBindObject()`. The `indp` parameter is ignored for dynamic binds. If `valuep` is an `OUT` parameter, then you must set `indp` to point to `OCI_IND_NULL`.

**See Also:**

[Indicator Variables](oci-programming-basics.md)

alenp (IN/OUT)
Pointer to an array of actual lengths of array elements.

When `OCIEnvNlsCreate()` (which is the recommended OCI environment handle creation interface) is used, then `alenp` lengths are consistently expected in bytes (for IN binds) and reported in bytes for OUT binds. The same treatment consistently also holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types. There are no special exceptions for UCS2 or for NCHAR cases.

When the older OCI environment handle creation interfaces are used (either `OCIEnvCreate()` or deprecated `OCIEnvInit()`), `alenp` lengths are in bytes in general. However, `alenp` lengths are expected in characters for IN binds and also reported in characters for OUT binds only when either the character set is OCI_UC2ID (= OCI_UTF16ID) or when `OCI_ATTR_CHAR_COUNT` attribute is set on the corresponding OCIBind handle. The same treatment holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types.

This parameter is ignored for dynamic binds.

rcodep (OUT)
Pointer to an array of column-level return codes. This parameter is ignored for dynamic binds.

maxarr_len (IN)
A maximum array length parameter (the maximum possible number of elements that the user's array can accommodate). Used only for PL/SQL indexed table bindings.

curelep (IN/OUT)
Current array length parameter (a pointer to the actual number of elements in the array before or after the execute operation). Used only for PL/SQL indexed table bindings.

mode (IN)
The valid modes for this parameter are:

- `OCI_DEFAULT` - This is default mode.

- `OCI_BIND_SOFT` - Soft bind mode. This mode increases the performance of the call. If this is the first bind or some input value like `dty` or `value_sz` is changed from the previous bind, this mode is ignored. An error is returned if the statement is not executed. Unexpected behavior results if the bind handle passed is not valid.

- `OCI_DATA_AT_EXEC` - When this mode is selected, the `value_sz` parameter defines the maximum size of the data that can be provided at run time. The application must be ready to provide the OCI library runtime IN data buffers at any time and any number of times. Runtime data is provided in one of the following ways:

  - Callbacks using a user-defined function that must be registered with a subsequent call to `OCIBindDynamic()`.

  - A polling mechanism using calls supplied by OCI. This mode is assumed if no callbacks are defined.

    **See Also:**

    [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about using the `OCI_DATA_AT_EXEC` mode

    When `mode` is set to `OCI_DATA_AT_EXEC`, do not provide values for `valuep`, `indp`, `alenp`, and `rcodep` in the main call. Pass zeros (0) for `indp` and `alenp`. Provide the values through the callback function registered using `OCIBindDynamic()`.

- `OCI_IOV` - Bind noncontiguous addresses of data. The `valuep` parameter must be of the type `OCIIOV *` . This mode is intended to be used for scatter or gather binding, which allows multiple buffers to be bound or defined to a position, for example column A for the first 10 rows in one buffer, next 5 rows in one buffer, and the remaining 25 rows in another buffer. That eliminates the need to allocate and copy all of them into one big buffer while doing the array execute operation.

  **See Also:**

  [About Binding and Defining Multiple Buffers](binding-and-defining-in-oci.md)

When the allocated buffers are not required anymore, they should be freed by the client.

#### Comments

This call is used to perform a basic bind operation. The bind creates an association between the address of a program variable and a placeholder in a SQL statement or PL/SQL block. The bind call also specifies the type of data that is being bound, and may also indicate the method by which data is to be provided at run time.

This function also implicitly allocates the bind handle indicated by the `bindpp` parameter. If a non-`NULL` pointer is passed in `**bindpp`, OCI assumes that this points to a valid handle that has been previously allocated with a call to `OCIHandleAlloc()` or `OCIBindByPos2()`.

Data in an OCI application can be bound to placeholders statically or dynamically. Binding is static when all the IN bind data and the OUT bind buffers are well defined just before the execute operation. Binding is dynamic when the IN bind data and the OUT bind buffers are provided by the application on demand at execution time to the client library. Dynamic binding is indicated by setting the `mode` parameter of this call to `OCI_DATA_AT_EXEC`.

**See Also:**

[Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about dynamic binding

Both `OCIBindByName2()` and `OCIBindByPos2()` take as a parameter a bind handle, which is implicitly allocated by the bind call. A separate bind handle is allocated for each placeholder the application is binding.

Additional bind calls may be required to specify particular attributes necessary when binding certain data types or handling input data in certain ways:

- If arrays of structures are being used, `OCIBindArrayOfStruct()` must be called to set up the necessary skip parameters.

- If data is being provided dynamically at run time, and the application uses user-defined callback functions, `OCIBindDynamic()` must be called to register the callbacks.

- If lengths in `alenp` greater than 64 KB are required, use `OCIBindDynamic()`.

- If a named data type is being bound, `OCIBindObject()` must be called to specify additional necessary information.

- If a statement with the `RETURNING` clause is used, a call to `OCIBindDynamic()` must follow this call.

With IN binds, the values for each element of the array, the actual lengths of each element, and the actual array length must be set up before the call to `OCIStmtExecute()` .

With OUT binds, the values for each element of the array, the actual lengths of each element, and the actual array length are returned from the server after the `OCIStmtExecute()` call.

For Records
Clients must bind package record types using `SQLT_NTY` as the DTY of the bind. In the OCI client, objects and records are represented as Named Types (NTY) and must use the same `SQLT` code.

For Collections
Clients must bind all package collection types using `SQLT_NTY`. This is the DTY used to bind all schema level collection types.

For Booleans
Clients must bind Boolean types (`OCI_TYPECODE_BOOLEAN`) using `SQLT_BOL`.

**Related Topics**

- OCIBindDynamic()
- OCIBindObject()
- OCIBindArrayOfStruct()
- OCIBindByPos()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvInit()](deprecated-oci-functions.md)
- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- OCIBindByName2()
- [OCIStmtExecute()](statement-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.4.6 OCIBindDynamic()

Registers user callbacks for dynamic data allocation.

#### Purpose

Registers user callbacks for dynamic data allocation.

#### Syntax

    sword OCIBindDynamic ( OCIBind     *bindp,
                           OCIError    *errhp,
                           void        *ictxp,
                           OCICallbackInBind         (icbfp)(
                                    void             *ictxp,
                                    OCIBind          *bindp,
                                    ub4               iter,
                                    ub4               index,
                                    void            **bufpp,
                                    ub4              *alenp,
                                    ub1              *piecep,
                                    void            **indpp ),
                                    void             *octxp,
                           OCICallbackOutBind        (ocbfp)(
                                    void             *octxp,
                                    OCIBind          *bindp,
                                    ub4               iter,
                                    ub4               index,
                                    void            **bufpp,
                                    ub4             **alenpp,
                                    ub1              *piecep,
                                    void            **indpp,
                                    ub2             **rcodepp ) );

#### Parameters

bindp (IN/OUT)
A bind handle returned by a call to `OCIBindByName()` or `OCIBindByPos()`.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

ictxp (IN)
The context pointer required by the callback function `icbfp`.

icbfp (IN)
The callback function that returns a pointer to the IN bind value or piece at run time. The callback takes in the following parameters:

ictxp (IN/OUT)
The context pointer for this callback function.

bindp (IN)
The bind handle passed in to uniquely identify this bind variable.

iter (IN)
A 0-based execute iteration value.

index (IN)
Index of the current array, for an array bind in PL/SQL. For SQL it is the row index. The value is 0-based and not greater than the `curelep` parameter of the bind call.

bufpp (OUT)
The pointer to the buffer or storage. For descriptors, `*bufpp` contains a pointer to the descriptor. For example, if you define the following parameter, then you set `*bufpp` to `lobp`, not `*lobp`.

    OCILobLocator    *lobp;

For `REF`s, pass the address of the ref; that is, pass `&my_ref` for `*bufpp`.

If the `OCI_ATTR_CHARSET_ID` attribute is set to `OCI_UTF16ID` (replaces the deprecated `OCI_UCS2ID`, which is retained for backward compatibility), all data passed to and received with the corresponding bind call is assumed to be in `UTF-16` encoding.

**See Also:**

[Bind Handle Attributes](handle-and-descriptor-attributes.md)

alenp (OUT)
A pointer to storage for OCI to fill in the size of the bind value or piece after it has been read. For descriptors, pass the size of the pointer to the descriptor; for example, `sizeof(OCILobLocator *)`.

piecep (OUT)
A piece of the bind value. This can be one of the following values: `OCI_ONE_PIECE`, `OCI_FIRST_PIECE`, `OCI_NEXT_PIECE`, and `OCI_LAST_PIECE`. For data types that do not support piecewise operations, you must pass `OCI_ONE_PIECE` or an error is generated.

indpp (OUT)
Contains the indicator value. This is either a pointer to an sb2 value or a pointer to an indicator structure for binding named data types.

octxp (IN)
The context pointer required by the callback function `ocbfp()`.

ocbfp (IN)
The callback function that returns a pointer to the OUT bind value or piece at run time. The callback takes in the following parameters:

octxp (IN/OUT)
The context pointer for this callback function.

bindp (IN)
The bind handle passed in to uniquely identify this bind variable.

iter (IN)
A 0-based execute iteration value.

index (IN)
For PL/SQL, the index of the current array for an array bind. For SQL, the index is the row number in the current iteration. It is 0-based, and must not be greater than the `curelep` parameter of the bind call.

bufpp (OUT)
A pointer to a buffer to write the bind value or piece in.

If the `OCI_ATTR_CHARSET_ID` attribute is set to `OCI_UTF16ID` (replaces the deprecated `OCI_UCS2ID`, which is retained for backward compatibility), all data passed to and received with the corresponding bind call is assumed to be in `UTF-16` encoding. For more information, see "[Bind Handle Attributes](handle-and-descriptor-attributes.md)".

alenpp (IN/OUT)
A pointer to storage for OCI to fill in the size of the bind value or piece after it has been read. It is in bytes except for Unicode encoding (if the `OCI_ATTR_CHARSET_ID` attribute is set to `OCI_UTF16ID`), when it is in code points.

piecep (IN/OUT)
Returns a piece value from the callback (application) to the Oracle Database, as follows:

- `IN` - The value can be `OCI_ONE_PIECE` or `OCI_NEXT_PIECE`.

- `OUT` - Depends on the IN value:

  - If IN value is `OCI_ONE_PIECE`, then OUT value can be `OCI_ONE_PIECE` or `OCI_FIRST_PIECE`.

  - If IN value is `OCI_NEXT_PIECE`, then OUT value can be `OCI_NEXT_PIECE` or `OCI_LAST_PIECE`.

indpp (OUT)
Contains the indicator value. This is either a pointer to an `sb2` value, or a pointer to an indicator structure for binding named data types.

rcodepp (OUT)
Returns a pointer to the return code.

#### Comments

This call is used to register user-defined callback functions for providing or receiving data if `OCI_DATA_AT_EXEC` mode was specified in a previous call to `OCIBindByName()` or `OCIBindByPos()`.

The callback function pointers must return `OCI_CONTINUE` if the call is successful. Any return code other than `OCI_CONTINUE` signals that the client wants to terminate processing immediately.

**See Also:**

[Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about the `OCI_DATA_AT_EXEC` mode

When passing the address of a storage area, ensure that the storage area exists even after the application returns from the callback. This means that you should not allocate such storage on the stack.

**Note:**

After you use `OCIEnvNlsCreate()` to create the environment handle, the actual lengths and returned lengths of bind and define handles are always in number of bytes.

**Related Topics**

- OCIBindByName()
- OCIBindByName2()
- OCIBindByPos()
- OCIBindByPos2()
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.4.7 OCIBindObject()

Sets up additional attributes that are required for a named data type (object) bind.

#### Purpose

Sets up additional attributes that are required for a named data type (object) bind.

#### Syntax

    sword OCIBindObject ( OCIBind          *bindp,
                          OCIError         *errhp,
                          const OCIType    *type,
                          void            **pgvpp,
                          ub4              *pvszsp,
                          void            **indpp,
                          ub4              *indszp, );

#### Parameters

bindp (IN/OUT)
The bind handle returned by the call to `OCIBindByName()` or `OCIBindByName2()` or `OCIBindByPos()` or `OCIBindByPos2()`.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

type (IN)
Points to the TDO that describes the type of program variable being bound. Retrieved by calling `OCITypeByName()`. Optional for `REF`s in SQL, but required for `REF`s in PL/SQL.

pgvpp (IN/OUT)
Address of the program variable buffer. For an array, `pgvpp` points to an array of addresses. When the bind variable is also an OUT variable, the OUT named data type value or `REF` is allocated in the Object Cache, and a `REF` is returned.

`pgvpp` is ignored if the `OCI_DATA_AT_EXEC` mode is set. Then the named data type buffers are requested at run time. For static array binds, skip factors may be specified using the `OCIBindArrayOfStruct()` call. The skip factors are used to compute the address of the next pointer to the value, the indicator structure, and their sizes.

pvszsp (OUT) \[optional\]
Points to the size of the program variable. The size of the named data type is not required on input. For an array, `pvszsp` is an array of `ub4`s. On return, for OUT bind variables, this points to sizes of the named data types and `REF`s received. `pvszsp` is ignored if the `OCI_DATA_AT_EXEC` mode is set. Then the size of the buffer is taken at run time.

indpp (IN/OUT) \[optional\]
Address of the program variable buffer containing the parallel indicator structure. For an array, `indpp` points to an array of pointers. When the bind variable is also an OUT bind variable, memory is allocated in the object cache, to store the OUT indicator values. At the end of the execute operation when all OUT values have been received, `indpp` points to the pointers of these newly allocated indicator structures. Required only for SQLT_NTY binds. The `indpp` parameter is ignored if the `OCI_DATA_AT_EXEC` mode is set. Then the indicator is requested at run time.

indszp (IN/OUT)
Points to the size of the IN indicator structure program variable. For an array, it is an array of `sb2`s. On return for OUT bind variables, this points to sizes of the received OUT indicator structures. `indszp` is ignored if the `OCI_DATA_AT_EXEC` mode is set. Then the indicator size is requested at run time.

#### Comments

This function sets up additional attributes for binding a named data type or a `REF`. An error is returned if this function is called when the OCI environment has been initialized in non-object mode.

This call takes as a parameter a type descriptor object (TDO) of data type `OCIType` for the named data type being defined. The TDO can be retrieved with a call to `OCITypeByName()`.

If the `OCI_DATA_AT_EXEC` mode was specified in `OCIBindByName()` or `OCIBindByName2()` or `OCIBindByPos()` or `OCIBindByPos2()`, the pointers to the IN buffers are obtained either using the callback `icbfp` registered in the `OCIBindDynamic()` call or by the `OCIStmtSetPieceInfo()` call.

The buffers are dynamically allocated for the OUT data. The pointers to these buffers are returned either by:

- Calling `ocbfp()` registered by the `OCIBindDynamic()`

- Setting the pointer to the buffer in the buffer passed in by `OCIStmtSetPieceInfo()` called when `OCIStmtExecute()` returned `OCI_NEED_DATA`

The memory of these client library-allocated buffers must be freed when not in use anymore by using the `OCIObjectFree()` call.

**Related Topics**

- OCIBindByName()
- OCIBindByName2()
- OCIBindByPos()
- OCIBindByPos2()
- OCIBindArrayOfStruct()
- [OCITypeByName()](oci-type-information-accessor-functions.md)
- [OCIStmtSetPieceInfo()](statement-functions.md)
- [OCIStmtExecute()](statement-functions.md)
- [OCIObjectFree()](oci-pin-unpin-and-free-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.4.8 OCIDefineArrayOfStruct()

Specifies additional attributes necessary for a static array define, used in an array of structures (multirow, multicolumn) fetch.

#### Purpose

Specifies additional attributes necessary for a static array define, used in an array of structures (multirow, multicolumn) fetch.

#### Syntax

    sword OCIDefineArrayOfStruct ( OCIDefine   *defnp,
                                   OCIError    *errhp,
                                   ub4          pvskip,
                                   ub4          indskip,
                                   ub4          rlskip,
                                   ub4          rcskip );

#### Parameters

defnp (IN/OUT)
The handle to the define structure that was returned by a call to `OCIDefineByPos()` or `OCIDefineByPos2()`.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

pvskip (IN)
Skip parameter for the next data value.

indskip (IN)
Skip parameter for the next indicator location.

rlskip (IN)
Skip parameter for the next return length value.

rcskip (IN)
Skip parameter for the next return code.

#### Comments

This call follows a call to `OCIDefineByPos()` or `OCIDefineByPos2()`. If the application is binding an array of structures involving objects, it must call `OCIDefineObject()` first, and then call `OCIDefineArrayOfStruct()`.

**Related Topics**

- OCIDefineByPos()
- OCIDefineByPos2()
- OCIDefineObject()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Skip Parameters](binding-and-defining-in-oci.md)

### 25.4.9 OCIDefineByPos()

Associates an item in a select list with the type and output data buffer.

#### Purpose

Associates an item in a select list with the type and output data buffer.

#### Syntax

    sword OCIDefineByPos ( OCIStmt     *stmtp,
                           OCIDefine  **defnpp,
                           OCIError    *errhp,
                           ub4          position,
                           void        *valuep,
                           sb4          value_sz,
                           ub2          dty,
                           void        *indp,
                           ub2         *rlenp,
                           ub2         *rcodep,
                           ub4          mode );

#### Parameters

stmtp (IN/OUT)
A handle to the requested SQL query operation.

defnpp (IN/OUT)
A pointer to a pointer to a define handle. If this parameter is passed as `NULL`, this call implicitly allocates the define handle. For a redefine, a non-`NULL` handle can be passed in this parameter. This handle is used to store the define information for this column.

**Note:**

You must keep track of this pointer. If a second call to `OCIDefineByPos()` is made for the same column position, there is no guarantee that the same pointer will be returned.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

position (IN)
The position of this value in the select list. Positions are 1-based and are numbered from left to right. The value 0 selects `ROWID`s (the globally unique identifier for a row in a table).

valuep (IN/OUT)
A pointer to a buffer or an array of buffers of the type specified in the `dty` parameter. A number of buffers can be specified when results for more than one row are desired in a single fetch call.

For a LOB, the buffer pointer must be a pointer to a LOB locator of type `OCILobLocator`. Give the address of the pointer.

When `mode` is set to `OCI_IOV`, pass the base address of the `OCIIOV` struct.

value_sz (IN)
The size of each `valuep` buffer in bytes. If the data is stored internally in VARCHAR2 format, the number of characters desired, if different from the buffer size in bytes, can be specified by using `OCIAttrSet()`.

In a multibyte conversion environment, a truncation error is generated if the number of bytes specified is insufficient to handle the number of characters needed.

If the `OCI_ATTR_CHARSET_ID` attribute is set to `OCI_UTF16ID` (replaces the deprecated `OCI_UCS2ID`, which is retained for backward compatibility), all data passed to and received with the corresponding define call is assumed to be in `UTF-16` encoding.

When `mode` is set to `OCI_IOV`, pass the size of the data value.

**See Also:**

[Bind Handle Attributes](handle-and-descriptor-attributes.md)

<!-- -->

dty (IN)
The data type. Named data type (SQLT_NTY) and `REF` (SQLT_REF) are valid only if the environment has been initialized in object mode.

SQLT_CHR and SQLT_LNG can be specified for `CLOB` columns, and SQLT_BIN and SQLT_LBI can be specified for `BLOB` columns.

**See Also:**

[Data Types](data-types.md) for a listing of data type codes and values

<!-- -->

indp (IN)
Pointer to an indicator variable or array. For scalar data types, pointer to `sb2` or an array of `sb2`s. Ignored for SQLT_NTY defines. For SQLT_NTY defines, a pointer to a named data type indicator structure or an array of named data type indicator structures is associated by a subsequent `OCIDefineObject()` call.

**See Also:**

[Indicator Variables](oci-programming-basics.md)

<!-- -->

rlenp (IN/OUT)
Pointer to array of length of data fetched.

When `OCIEnvNlsCreate()` (which is the recommended OCI environment handle creation interface) is used, then `rlenp` lengths are consistently reported in bytes. The same treatment consistently also holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types. There are no special exceptions for UCS2 or for NCHAR cases.

When the older OCI environment handle creation interfaces are used (either `OCIEnvCreate()` or deprecated `OCIEnvInit()`), `rlenp` lengths are in bytes in general. However, `rlenp` lengths are reported in characters when either the character set is OCI_UC2ID (= OCI_UTF16ID) or when `OCI_ATTR_CHAR_COUNT` attribute is set on the corresponding OCIBind handle. The same treatment holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types.

rcodep (OUT)
Pointer to array of column-level return codes.

mode (IN)
The valid modes are:

- `OCI_DEFAULT` - This is the default mode.

- `OCI_DEFINE_SOFT` - Soft define mode. This mode increases the performance of the call. If this is the first define, or some input parameter such as `dty` or `value_sz` is changed from the previous define, this mode is ignored. Unexpected behavior results if an invalid define handle is passed. An error is returned if the statement is not executed.

- `OCI_DYNAMIC_FETCH` - For applications requiring dynamically allocated data at the time of fetch, this mode must be used. You can define a callback using the `OCIDefineDynamic()` call. The `value_sz` parameter defines the maximum size of the data that is to be provided at run time. When the client library needs a buffer to return the fetched data, the callback is invoked to provide a runtime buffer into which a piece or all the data is returned.

  **See Also:**

  [Implicit Fetching of ROWIDs](performance-topics.md)

- `OCI_IOV` - Define noncontiguous addresses of data. The `valuep` parameter must be of the type `OCIIOV *`. This mode is intended to be used for scatter or gather binding, which allows multiple buffers to be bound or defined to a position, for example column A for the first 10 rows in one buffer, next 5 rows in one buffer, and the remaining 25 rows in another buffer. That eliminates the need to allocate and copy all of them into one big buffer while doing the array execute operation.

  **See Also:**

  [About Binding and Defining Multiple Buffers](binding-and-defining-in-oci.md)

#### Comments

This call defines an output buffer that receives data retrieved from Oracle Database. The define is a local step that is necessary when a `SELECT` statement returns data to your OCI application.

This call also implicitly allocates the define handle for the select-list item. If a non-`NULL` pointer is passed in `*defnpp`, OCI assumes that this points to a valid handle that has been previously allocated with a call to `OCIHandleAlloc()` or `OCIDefineByPos()` or `OCIDefineByPos2()`. This would be true for an application that is redefining a handle to a different address so that it can reuse the same define handle for multiple fetches.

Defining attributes of a column for a fetch is done in one or more calls. The first call is to `OCIDefineByPos()` or `OCIDefineByPos2()`, which defines the minimal attributes required to specify the fetch.

Following the call to `OCIDefineByPos()` or `OCIDefineByPos2()` additional define calls may be necessary for certain data types or fetch modes:

- A call to `OCIDefineArrayOfStruct()` is necessary to set up skip parameters for an array fetch of multiple columns.

- A call to `OCIDefineObject()` is necessary to set up the appropriate attributes of a named data type (that is, object or collection) or `REF` fetch. In this case, the data buffer pointer in `OCIDefineByPos()` or `OCIDefineByPos2()` is ignored.

- Both `OCIDefineArrayOfStruct()` and `OCIDefineObject()` must be called after `OCIDefineByPos()` or `OCIDefineByPos2()` to fetch multiple rows with a column of named data types.

For a LOB define, the buffer pointer must be a pointer to a LOB locator of type `OCILobLocator`, allocated by the `OCIDescriptorAlloc()` call. LOB locators, and not LOB values, are always returned for a LOB column. LOB values can then be fetched using OCI LOB calls on the fetched locator. This same mechanism applies for all descriptor data types.

For NCHAR (fixed and varying length), the buffer pointer must point to an array of bytes sufficient for holding the required NCHAR characters.

Nested table columns are defined and fetched like any other named data type.

When defining an array of descriptors or locators, you should pass in an array of pointers to descriptors or locators.

When doing an array define for character columns, you should pass in an array of character buffers.

If the `mode` parameter in this call is set to `OCI_DYNAMIC_FETCH`, the client application can fetch data dynamically at run time. Runtime data can be provided in one of two ways:

- Callbacks using a user-defined function that must be registered with a subsequent call to `OCIDefineDynamic()`. When the client library needs a buffer to return the fetched data, the callback is invoked and the runtime buffers provided return a piece or all of the data.

- A polling mechanism using calls supplied by OCI. This mode is assumed if no callbacks are defined. In this case, the fetch call returns the `OCI_NEED_DATA` error code, and a piecewise polling method is used to provide the data.

  **See Also:**

  - [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about using the `OCI_DYNAMIC_FETCH` mode

  - [Overview of Defining in OCI](binding-and-defining-in-oci.md) for more information about defines

  - [Implicit Fetching of ROWIDs](performance-topics.md)

**Related Topics**

- OCIDefineArrayOfStruct()
- OCIDefineDynamic()
- OCIDefineObject()
- OCIDefineByPos2()
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvInit()](deprecated-oci-functions.md)
- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.4.10 OCIDefineByPos2()

Associates an item in a select list with the type and output data buffer. Use this call when working with data types when actual lengths exceed `UB2MAXVAL` on the client.

#### Purpose

Associates an item in a select list with the type and output data buffer. Use this call instead of `OCIDefineByPos()` when working with data types when actual lengths exceed `UB2MAXVAL` on the client.

#### Syntax

    sword OCIDefineByPos2 ( OCIStmt     *stmtp,
                            OCIDefine  **defnpp,
                            OCIError    *errhp,
                            ub4          position,
                            void        *valuep,
                            sb8          value_sz,
                            ub2          dty,
                            void        *indp,
                            ub4         *rlenp,
                            ub2         *rcodep,
                            ub4          mode );

#### Parameters

stmtp (IN/OUT)
A handle to the requested SQL query operation.

defnpp (IN/OUT)
A pointer to a pointer to a define handle. If this parameter is passed as `NULL`, this call implicitly allocates the define handle. For a redefine, a non-`NULL` handle can be passed in this parameter. This handle is used to store the define information for this column.

**Note:**

You must keep track of this pointer. If a second call to `OCIDefineByPos()` is made for the same column position, there is no guarantee that the same pointer will be returned.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

position (IN)
The position of this value in the select list. Positions are 1-based and are numbered from left to right. The value 0 selects `ROWID`s (the globally unique identifier for a row in a table).

valuep (IN/OUT)
A pointer to a buffer or an array of buffers of the type specified in the `dty` parameter. A number of buffers can be specified when results for more than one row are desired in a single fetch call.

For a LOB, the buffer pointer must be a pointer to a LOB locator of type `OCILobLocator`. Give the address of the pointer.

When `mode` is set to `OCI_IOV`, pass the base address of the `OCIIOV` struct.

value_sz (IN)
The size of each `valuep` buffer in bytes. If the data is stored internally in `VARCHAR2` format, the number of characters desired, if different from the buffer size in bytes, can be specified as additional bytes by using `OCIAttrSet()`.

If the value of `value_sz` \> `SB4MAXVAL`, an `ORA-24452` error will be issued, meaning that values \> `SB4MAXVAL` are not supported in Release 12.1 or later.

In a multibyte conversion environment, a truncation error is generated if the number of bytes specified is insufficient to handle the number of characters needed.

If the `OCI_ATTR_CHARSET_ID` attribute is set to `OCI_UTF16ID` (replaces the deprecated `OCI_UCS2ID`, which is retained for backward compatibility), all data passed to and received with the corresponding define call is assumed to be in `UTF-16` encoding.

When `mode` is set to `OCI_IOV`, pass the size of the data value.

**See Also:**

[Bind Handle Attributes](handle-and-descriptor-attributes.md)

<!-- -->

dty (IN)
The data type. Named data type (SQLT_NTY) and `REF` (SQLT_REF) are valid only if the environment has been initialized in object mode.

SQLT_CHR and SQLT_LNG can be specified for `CLOB` columns, and SQLT_BIN and SQLT_LBI can be specified for `BLOB` columns.

**See Also:**

[Data Types](data-types.md) for a listing of data type codes and values

<!-- -->

indp (IN)
Pointer to an indicator variable or array. For scalar data types, pointer to `sb2` or an array of `sb2`s. Ignored for SQLT_NTY defines. For SQLT_NTY defines, a pointer to a named data type indicator structure or an array of named data type indicator structures is associated by a subsequent `OCIDefineObject()` call.

**See Also:**

[Indicator Variables](oci-programming-basics.md)

<!-- -->

rlenp (IN/OUT)
Pointer to array of length of data fetched.

When `OCIEnvNlsCreate()` (which is the recommended OCI environment handle creation interface) is used, then `rlenp` lengths are consistently reported in bytes. The same treatment consistently also holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types. There are no special exceptions for UCS2 or for NCHAR cases.

When the older OCI environment handle creation interfaces are used (either `OCIEnvCreate()` or deprecated `OCIEnvInit()`), `rlenp` lengths are in bytes in general. However, `rlenp` lengths are reported in characters when either the character set is OCI_UC2ID (= OCI_UTF16ID) or when `OCI_ATTR_CHAR_COUNT` attribute is set on the corresponding OCIBind handle. The same treatment holds for the length prefix in `SQLT_VCS` (2-byte length prefix) and `SQLT_LVC` (4-byte length prefix) types.

rcodep (OUT)
Pointer to array of column-level return codes.

mode (IN)
The valid modes are:

- `OCI_DEFAULT` - This is the default mode.

- `OCI_DEFINE_SOFT` - Soft define mode. This mode increases the performance of the call. If this is the first define, or some input parameter such as `dty` or `value_sz` is changed from the previous define, this mode is ignored. Unexpected behavior results if an invalid define handle is passed. An error is returned if the statement is not executed.

- `OCI_DYNAMIC_FETCH` - For applications requiring dynamically allocated data at the time of fetch, this mode must be used. You can define a callback using the `OCIDefineDynamic()` call. The `value_sz` parameter defines the maximum size of the data that is to be provided at run time. When the client library needs a buffer to return the fetched data, the callback is invoked to provide a runtime buffer into which a piece or all the data is returned.

  **See Also:**

  [Implicit Fetching of ROWIDs](performance-topics.md)

- `OCI_IOV` - Define noncontiguous addresses of data. The `valuep` parameter must be of the type `OCIIOV *`. This mode is intended to be used for scatter or gather binding, which allows multiple buffers to be bound or defined to a position, for example column A for the first 10 rows in one buffer, next 5 rows in one buffer, and the remaining 25 rows in another buffer. That eliminates the need to allocate and copy all of them into one big buffer while doing the array execute operation.

  **See Also:**

  [About Binding and Defining Multiple Buffers](binding-and-defining-in-oci.md)

#### Comments

This call defines an output buffer that receives data retrieved from Oracle Database. The define is a local step that is necessary when a `SELECT` statement returns data to your OCI application.

This call also implicitly allocates the define handle for the select-list item. If a non-`NULL` pointer is passed in `*defnpp`, OCI assumes that this points to a valid handle that has been previously allocated with a call to `OCIHandleAlloc()` or `OCIDefineByPos2()`. This would be true for an application that is redefining a handle to a different address so that it can reuse the same define handle for multiple fetches.

Defining attributes of a column for a fetch is done in one or more calls. The first call is to `OCIDefineByPos2()`, which defines the minimal attributes required to specify the fetch.

Following the call to `OCIDefineByPos2()` additional define calls may be necessary for certain data types or fetch modes:

- A call to `OCIDefineArrayOfStruct()` is necessary to set up skip parameters for an array fetch of multiple columns.

- A call to `OCIDefineObject()` is necessary to set up the appropriate attributes of a named data type (that is, object or collection) or `REF` fetch. In this case, the data buffer pointer in `OCIDefineByPos2()` is ignored.

- Both `OCIDefineArrayOfStruct()` and `OCIDefineObject()` must be called after `OCIDefineByPos2()` to fetch multiple rows with a column of named data types.

For a LOB define, the buffer pointer must be a pointer to a LOB locator of type `OCILobLocator`, allocated by the `OCIDescriptorAlloc()` call. LOB locators, and not LOB values, are always returned for a LOB column. LOB values can then be fetched using OCI LOB calls on the fetched locator. This same mechanism applies for all descriptor data types.

For NCHAR (fixed and varying length), the buffer pointer must point to an array of bytes sufficient for holding the required NCHAR characters.

Nested table columns are defined and fetched like any other named data type.

When defining an array of descriptors or locators, you should pass in an array of pointers to descriptors or locators.

When doing an array define for character columns, you should pass in an array of character buffers.

If the `mode` parameter in this call is set to `OCI_DYNAMIC_FETCH`, the client application can fetch data dynamically at run time. Runtime data can be provided in one of two ways:

- Callbacks using a user-defined function that must be registered with a subsequent call to `OCIDefineDynamic()`. When the client library needs a buffer to return the fetched data, the callback is invoked and the runtime buffers provided return a piece or all of the data.

- A polling mechanism using calls supplied by OCI. This mode is assumed if no callbacks are defined. In this case, the fetch call returns the `OCI_NEED_DATA` error code, and a piecewise polling method is used to provide the data.

  **See Also:**

  - [Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about using the `OCI_DYNAMIC_FETCH` mode

  - [Overview of Defining in OCI](binding-and-defining-in-oci.md) for more information about defines

  - [Implicit Fetching of ROWIDs](performance-topics.md)

**Related Topics**

- OCIDefineArrayOfStruct()
- OCIDefineDynamic()
- OCIDefineObject()
- OCIDefineByPos()
- [OCIAttrSet()](handle-and-descriptor-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvInit()](deprecated-oci-functions.md)
- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.4.11 OCIDefineDynamic()

Sets the additional attributes required if the `OCI_DYNAMIC_FETCH` mode was selected in `OCIDefineByPos()` or `OCIDefineByPos2()`.

#### Purpose

Sets the additional attributes required if the `OCI_DYNAMIC_FETCH` mode was selected in `OCIDefineByPos()` or `OCIDefineByPos2()`.

#### Syntax

    sword OCIDefineDynamic ( OCIDefine   *defnp,
                             OCIError    *errhp,
                             void        *octxp,
                             OCICallbackDefine      (ocbfp)(
                                      void          *octxp,
                                      OCIDefine     *defnp,
                                      ub4            iter,
                                      void         **bufpp,
                                      ub4          **alenpp,
                                      ub1           *piecep,
                                      void         **indpp,
                                      ub2          **rcodep );

#### Parameters

defnp (IN/OUT)
The handle to a define structure returned by a call to `OCIDefineByPos()`.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

octxp (IN)
Points to a context for the callback function.

ocbfp (IN)
Points to a callback function. This is invoked at run time to get a pointer to the buffer into which the fetched data or a piece of it is to be retrieved. The callback also specifies the indicator, the return code, and the lengths of the data piece and indicator.

**Note:**

Normally, in an OCI function, an `IN` parameter refers to data being passed to OCI, and an `OUT` parameter refers to data coming back from OCI. For callbacks, this is reversed. `IN` means that data is coming from OCI into the callback, and `OUT` means that data is coming out of the callback and going to OCI.

The callback parameters are:

octxp (IN/OUT)
A context pointer passed as an argument to all the callback functions. When the client library needs a buffer to return the fetched data, the callback is invoked and the runtime buffers provided return a piece or all of the data.

defnp (IN)
The define handle.

iter (IN)
Specifies which row of this current fetch; 0-based.

bufpp (OUT)
Returns a pointer to a buffer to store the column value; that is, `*bufpp` points to some appropriate storage for the column value.

alenpp (IN/OUT)
Used by the application to set the size of the storage it is providing in `*bufpp`. After data is fetched into the buffer, `alenpp` indicates the actual size of the data in bytes. If the buffer length provided in the first call is insufficient to store all the data returned by the server, then the callback is called again, and so on.

piecep (IN/OUT)
Returns a piece value from the callback (application) to OCI, as follows:

The `piecep` parameter indicates whether the piece to be fetched is the first piece, `OCI_FIRST_PIECE`, a subsequent piece, `OCI_NEXT_PIECE`, or the last piece, `OCI_LAST_PIECE`. The program can process the piece the next time the callback is called, or after the series of callbacks is over.

- `IN` - The value can be `OCI_ONE_PIECE`, `OCI_FIRST_PIECE`, or `OCI_NEXT_PIECE`.

- `OUT` - Depends on the IN value:

  - The `OUT` value can be `OCI_ONE_PIECE` if the `IN` value was `OCI_ONE_PIECE`.

  - The `OUT` value can be `OCI_ONE_PIECE` or `OCI_FIRST_PIECE` if the `IN` value was `OCI_FIRST_PIECE`.

  - The `OUT` value can be `OCI_NEXT_PIECE` or `OCI_LAST_PIECE` if the `IN` value was `OCI_NEXT_PIECE`.

indpp (IN)
Indicator variable pointer.

rcodep (IN)
Return code variable pointer.

#### Comments

This call is used to set the additional attributes required if the `OCI_DYNAMIC_FETCH` mode has been selected in a call to `OCIDefineByPos()` or `OCIDefineByPos2()`. If `OCI_DYNAMIC_FETCH` mode was selected, and the call to `OCIDefineDynamic()` is skipped, then the application can fetch data piecewise using OCI calls (`OCIStmtGetPieceInfo()` and `OCIStmtSetPieceInfo()`).

**Note:**

After you use `OCIEnvNlsCreate()` to create the environment handle, the actual lengths and returned lengths of bind and define handles are always in number of bytes.

**Related Topics**

- OCIDefineObject()
- OCIBindDynamic()
- OCIDefineByPos()
- OCIDefineByPos2()
- [OCIStmtGetPieceInfo()](statement-functions.md)
- [OCIStmtSetPieceInfo()](statement-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

**See Also:**

[Runtime Data Allocation and Piecewise Operations in OCI](binding-and-defining-in-oci.md) for more information about `OCI_DYNAMIC_FETCH` mode

### 25.4.12 OCIDefineObject()

Sets up additional attributes necessary for a named data type or `REF` define.

#### Purpose

Sets up additional attributes necessary for a named data type or `REF` define.

#### Syntax

    sword OCIDefineObject ( OCIDefine       *defnp,
                            OCIError        *errhp,
                            const OCIType   *type,
                            void           **pgvpp,
                            ub4             *pvszsp,
                            void           **indpp,
                            ub4             *indszp );

#### Parameters

defnp (IN/OUT)
A define handle previously allocated in a call to `OCIDefineByPos()` or `OCIDefineByPos2()`.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

type (IN) \[optional\]
Points to the type descriptor object (TDO) that describes the type of the program variable. This parameter is optional for variables of type `SQLT_REF`, and may be passed as `NULL` if it is not being used.

pgvpp (IN/OUT)
Points to a pointer to a program variable buffer. For an array, `pgvpp` points to an array of pointers. Memory for the fetched named data type instances is dynamically allocated in the object cache. At the end of the fetch when all the values have been received, `pgvpp` points to the pointers to these newly allocated named data type instances. The application must call `OCIObjectFree()` to deallocate the named data type instances when they are no longer needed.

**Note:**

If the application wants the buffer to be implicitly allocated in the cache, `*pgvpp` should be passed in as `NULL`.

pvszsp (IN/OUT)
Points to the size of the program variable. For an array, it is an array of `ub4`.

indpp (IN/OUT)
Points to a pointer to the program variable buffer containing the parallel indicator structure. For an array, points to an array of pointers. Memory is allocated to store the indicator structures in the object cache. At the end of the fetch when all values have been received, `indpp` points to the pointers to these newly allocated indicator structures.

indszp (IN/OUT)
Points to the sizes of the indicator structure program variable. For an array, it is an array of `ub4`s.

#### Comments

This function follows a call to `OCIDefineByPos()` or `OCIDefineByPos2()` to set initial define information. This call sets up additional attributes necessary for a named data type define. An error is returned if this function is called when the OCI environment has been initialized in non-object mode.

This call takes as a parameter a type descriptor object (TDO) of data type `OCIType` for the named data type being defined. The TDO can be retrieved with a call to `OCIDescribeAny()`.

**Related Topics**

- OCIDefineByPos()
- OCIDefineByPos2()
- [OCIObjectFree()](oci-pin-unpin-and-free-functions.md)
- OCIDescribeAny()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

- `OCIEnvCreate()`, and `OCIEnvNlsCreate()` for more information about initializing the OCI process environment

- [About Binding and Defining Multiple Buffers](binding-and-defining-in-oci.md) for an example of using multiple buffers

### 25.4.13 OCIDescribeAny()

Describes existing schema and subschema objects.

#### Purpose

Describes existing schema and subschema objects.

#### Syntax

    sword OCIDescribeAny ( OCISvcCtx       *svchp,
                           OCIError        *errhp,
                           void            *objptr,
                           ub4              objptr_len,
                           ub1              objptr_typ,
                           ub1              info_level,
                           ub1              objtyp,
                           OCIDescribe     *dschp );

#### Parameters

svchp (IN)
A service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

objptr (IN)
This parameter can be:

1.  A string containing the name of the object to be described. Must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

2.  A pointer to a `REF` to the TDO (for a type).

3.  A pointer to a TDO (for a type).

These cases are distinguished by passing the appropriate value for `objptr_typ`. This parameter must be non-`NULL`.

In case 1, the string containing the object name should be in the format `name1[.name2 ...][@linkname]`, such as `hr.employees.employee_id@mydb`. Database links are only allowed to Oracle8i or later databases. The object name is interpreted by the following SQL rules:

- If only `name1` is entered and `objtyp` is equal to `OCI_PTYPE_SCHEMA`, then the name refers to the named schema. The Oracle Database must be release 8.1 or later.

- If only `name1` is entered and `objtyp` is equal to `OCI_PTYPE_DATABASE`, then the name refers to the named database. When describing a remote database with `database_name@db_link_name`, the remote Oracle Database must be release 8.1 or later.

- If only `name1` is entered and `objtyp` is not equal to `OCI_PTYPE_SCHEMA` or `OCI_PTYPE_DATABASE`, then the name refers to the named object (of type table, view, procedure, function, package, type, synonym, sequence) in the current schema of the current user. When connected to an Oracle7 Server, the only valid types are procedure and function.

- If `name1.name2.name3 ...` is entered, the object name refers to a schema or subschema object in the schema named `name1`. For example, in the string `hr.employees.department_id`, `hr` is the name of the schema, `employees` is the name of a table in the schema, and `department_id` is the name of a column in the table.

objnm_len (IN)
The length of the name string pointed to by `objptr`. Must be nonzero if a name is passed. Can be zero if `objptr` is a pointer to a TDO or its `REF`.

objptr_typ (IN)
The type of object passed in `objptr`. Valid values are:

- `OCI_OTYPE_NAME`, if `objptr` points to the name of a schema object

- `OCI_OTYPE_REF`, if `objptr` is a pointer to a `REF` to a TDO

- `OCI_OTYPE_PTR`, if `objptr` is a pointer to a TDO

info_level (IN)
Reserved for future extensions. Pass `OCI_DEFAULT`.

objtyp (IN)
The type of schema object being described. Valid values are:

- `OCI_PTYPE_TABLE`, for tables

- `OCI_PTYPE_VIEW`, for views

- `OCI_PTYPE_PROC`, for procedures

- `OCI_PTYPE_FUNC`, for functions

- `OCI_PTYPE_PKG`, for packages

- `OCI_PTYPE_TYPE`, for types

- `OCI_PTYPE_SYN`, for synonyms

- `OCI_PTYPE_SEQ`, for sequences

- `OCI_PTYPE_SCHEMA`, for schemas

- `OCI_PTYPE_DATABASE`, for databases

- `OCI_PTYPE_UNK`, for unknown schema objects

dschp (IN/OUT)
A describe handle that is populated with describe information about the object after the call. Must be non-`NULL`.

#### Comments

This is a generic describe call that describes existing schema objects: tables, views, synonyms, procedures, functions, packages, sequences, types, schemas, and databases. In addition, the `OCIDescribeAny()` call describes all package types and package type attributes contained in the package. This call also describes subschema objects, such as a column in a table. This call populates the describe handle with the object-specific attributes that can be obtained through an `OCIAttrGet()` call.

An `OCIParamGet()` on the describe handle returns a parameter descriptor for a specified position. Parameter positions begin with 1. Calling `OCIAttrGet()` on the parameter descriptor returns the specific attributes of a stored procedure or function parameter, or a table column descriptor. These subsequent calls do not need an extra round-trip to the server because the entire schema object description is cached on the client side by `OCIDescribeAny()`. Calling `OCIAttrGet()` on the describe handle also returns the total number of positions.

If the `OCI_ATTR_DESC_PUBLIC` attribute is set on the describe handle, then the object named is looked up as a public synonym when the object does not exist in the current schema and only `name1` is specified.

By default, explicit describe (`OCIDescribeAny()`) does not list the invisible columns. To get the user defined invisible column's metadata, you must set the describe handle attribute `OCI_ATTR_SHOW_INVISIBLE_COLUMNS` before calling `OCIDescribeAny()`. To know whether the column is of an invisible type, you can get the column attribute `OCI_ATTR_INVISIBLE_COL` using `OCIAttrGet()`.

The property whether a column is visible or not can be controlled by the user. Invisible columns are not seen unless specified explicitly in the `SELECT` list. Any generic access of a table, such as a `SELECT * FROM` `table-name` statement or a `DESCRIBE` statement, will not show invisible columns.

**Related Topics**

- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)
- [OCIParamGet()](handle-and-descriptor-functions.md)
- [OCIAttrGet()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Describing Schema Metadata](describing-schema-metadata.md) for more information about describe operations

### 25.4.14 OCIStmtGetBindInfo()

Gets the bind and indicator variable names.

#### Purpose

Gets the bind and indicator variable names.

#### Syntax

    sword OCIStmtGetBindInfo ( OCIStmt      *stmtp,
                               OCIError     *errhp,
                               ub4           size,
                               ub4           startloc,
                               sb4          *found,
                               OraText      *bvnp[],
                               ub1           bvnl[],
                               OraText      *invp[],
                               ub1           inpl[],
                               ub1           dupl[],
                               OCIBind      *hndl[] );

#### Parameters

stmtp (IN)
The statement handle prepared by `OCIStmtPrepare2()`.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

size (IN)
The number of elements in each array.

startloc (IN)
Position of the bind variable at which to start getting bind information.

found (IN)
The expression `abs`(`found`) gives the total number of bind variables in the statement irrespective of the start position. Positive value if the number of bind variables returned is less than the size provided, otherwise negative.

bvnp (OUT)
Array of pointers to hold bind variable names. Is in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

bvnl (OUT)
Array to hold the length of the each `bvnp` element. The length is in bytes.

invp (OUT)
Array of pointers to hold indicator variable names. Must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

inpl (OUT)
Array of pointers to hold the length of the each `invp` element. In number of bytes.

dupl (OUT)
An array whose element value is 0 or 1 depending on whether the bind position is a duplicate of another.

hndl (OUT)
An array that returns the bind handle if binds have been done for the bind position. No handle is returned for duplicates.

#### Comments

This call returns information about bind variables after a statement has been prepared. This includes bind names, indicator names, and whether binds are duplicate binds. This call also returns an associated bind handle if there is one. The call sets the `found` parameter to the total number of bind variables and not just the number of distinct bind variables.

`OCI_NO_DATA` is returned if the statement has no bind variables or if the starting bind position specified in the invocation does not exist in the statement.

This function does not include `SELECT INTO` list variables, because they are not considered to be binds.

The statement must have been prepared with a call to `OCIStmtPrepare2()` prior to this call. The encoding setting in the statement handle determines whether Unicode strings are retrieved.

This call is processed locally.

**Related Topics**

- [OCIStmtPrepare2()](statement-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
